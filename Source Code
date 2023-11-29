#include<iostream>
#include<string>
using namespace std;

class Node
{
public:
	int data;
	Node* next;
	Node() // our defoult constructor
	{
		data = 0;
		next = nullptr;
	}
	Node(int d) // our peramertized constructor
	{
		data = d;
		next = nullptr;
	}
};
class SSL // i use sinlge linked list
{
public:
	Node* head;
	SSL() // our defoult constructor
	{
		head = nullptr;
	}
	SSL(Node* head) // our peramertized constructor
	{
		this->head = head;;
	}
	void insertAtEnd(Node* n) // insert new node at the end
	{
		if (head == nullptr)
		{
			head = n;
		}
		else
		{
			Node* curr = head;
			while (curr->next != nullptr)  // treverse to end of linked list
			{
				curr = curr->next;
			}
			curr->next = n;  // now insert at end
		}
	}

	void deleteAt(int key) // delete function 
	{
		if (head == nullptr)  // when list is empty 
		{
			cout << "Empty\n";
			return;
		}
		if (head->data == key) // if key found
		{
			head = head->next;
			return;
		}
		Node* prev = head;
		Node* current = head->next;
		while (current != nullptr)  // treverse when null is not found
		{
			if (current->data == key) // if key found
			{
				prev->next = current->next; //then point to next link 
				delete current;  // and delete current link
				return;
			}
			prev = current;
			current = current->next;
		}
		cout << "Key Not Found\n";
	}
	void display() // just display
	{
		Node* curr = head;
		while (curr != nullptr)
		{
			cout << curr->data << " -> ";
			curr = curr->next;
		}
	}
};
class Vertix
{
public:
	string vName; // vertix Name
	SSL ssl; // vertix Adjecnt in form of singlie List
	Vertix() // our defoult constructor
	{
		vName = "\0";
	}
	Vertix(string N) // our peramertized constructor
	{
		vName = N;
	}
};
class Graph
{
	int count;
	int maxSize;
	Vertix* vertex;
public:
	
	Graph(int s) // our peramertized constructor
	{
		maxSize = s;
		vertex = new Vertix[maxSize];
		count = 0;
	}
	void AddVertix(string Name) // Add new Verix name like a b c
	{
		if (count > maxSize - 1)
		{
			return;
		}
		vertex[count].vName = Name;
		count++;
	}
	void addEdge(int source, int dest) // Add new Edge a-----b
	{
		Node* E1 = new Node(dest);
		vertex[source].ssl.insertAtEnd(E1);
		Node* E2 = new Node(source);
		vertex[dest].ssl.insertAtEnd(E2);
	}
	void displayGraph()
	{
		if (count == 0)
		{
			cout << "Empty" << endl;
			return;
		}
		cout << "\n************** Adjacency List *********************** \n";
		for (int i = 0; i < count; i++)
		{
			cout << vertex[i].vName << " | ";
			vertex[i].ssl.display();
			cout << "\n\n";
		}
		cout << "\n----------------------------------------------------- \n\n\n";
	}

	int minKey(int key[], bool mstSet[]) 
	{
		int max = 9999;  // max value
		int index;  // index that we return

		for (int i = 0; i < 5; i++)
		{
			if (mstSet[i] == false && key[i] < max) // check that is visted and must be less
			{
				max = key[i];
				index = i;
			}
		}

		return index;
	}

	void printMST(int parent[], int weight[][5])  // just printing
	{
		cout << "Edge   \tWeight\n";
		for (int i = 1; i < 5; ++i)
		{
			cout << parent[i] << " --- " << i << "\t  " << weight[i][parent[i]] << "\n";
		}
			
	}

	void primMST(int weight[][5])
	{
		int predi[5];  // for MST
		int key[5];     // Key values for minimum weight edge
		bool mstSet[5]; // i make bool type array because i check it that is visited or not

		for (int i = 0; i < 5; i++) 
		{
			key[i] = 9999;  // max value
			mstSet[i] = false;  // firstly all not visited
		}

		key[0] = 0;     // Make key 0 so that this vertex is picked as the first vertex
		predi[0] = -1; // First node is always the root of MST

		for (int i = 0; i < 4; i++)
		{
			int val = minKey(key, mstSet); // here i find minimum key 
			mstSet[val] = true;   // it means visited

			for (int j = 0; j < 5; j++)
			{
				if (weight[val][j] && !mstSet[j] && weight[val][j] < key[j]) // chech the min and same alse weight is must be less
				{															// then go to that vertex
					predi[j] = val;
					key[j] = weight[val][j];   // if yes then go to that vertex
				}
			}
		}

		printMST(predi, weight);  // at the end print MST
	}
};
int main()
{
	Graph graph(5);
	graph.AddVertix("0");
	graph.AddVertix("1");
	graph.AddVertix("2");
	graph.AddVertix("3");
	graph.AddVertix("4");
	graph.addEdge(0, 1);
	graph.addEdge(0, 3);
	graph.addEdge(1, 3);
	graph.addEdge(1, 4);
	graph.addEdge(1, 2);
	graph.addEdge(2, 4);
	graph.addEdge(3, 4);

	int weight[5][5] = { { 0, 2, 0, 6, 0 },
						 { 2, 0, 3, 8, 5 },
						 { 0, 3, 0, 0, 7 },
						 { 6, 8, 0, 0, 9 },
						 { 0, 5, 7, 9, 0 } };

	graph.displayGraph();
	graph.primMST(weight);
	return 0;
}
