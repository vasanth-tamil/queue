# queue
```c
# queue (c)
```c
#include <stdio.h>
#include <string.h>

#define SIZE 5
#define TRUE 1
#define FALSE 0

/*
	(init) rear = front = -1
	(isEmpty) rear = front 
	(isFull) rear = size-1
*/
struct _Queue{
	int data[SIZE];
	int front;
	int rear;
};

typedef struct _Queue Queue;

Queue queue;

// isEmpty
int isEmpty(){
	if(queue.front == queue.rear) return TRUE;
	return FALSE;
}

// isFull
int isFull(){
	if(queue.rear == SIZE-1) return TRUE;
	return FALSE;
}

// insert
void insert(int value){
	if(!isFull()){
		// rear increase value
		queue.rear++;

		// insert value
		queue.data[queue.rear] = value;
	}
	else printf("Queue Is Full Not Inserted\n");
}

// delete
int delete(){
	int value = 0;
	if(!isEmpty()){
		// increase front value
		queue.front++;

		// store remove value
		value = queue.data[queue.front];

		// detele value on queue
		queue.data[queue.front] = '\0';

		return value;
	}
	else printf("Queue Is Empty Not Delete Value\n");
}

// print value
void print(){
	if(!isEmpty()){
		printf("Queue : ");
		for(int index=queue.front+1; index<=queue.rear; index++) {
			printf("%d\t", queue.data[index]);
		}
		printf("\n");
	}
}

int main(){
	// initialize front and read default empty
	queue.front = -1;
	queue.rear = -1; 

	// printf("isEmpty() %d\n", isEmpty());
	// printf("isFull() %d\n", isFull());

	insert(10);
	insert(20);
	insert(30);
	insert(40); 
	insert(50);
	insert(60);

	printf("\n");
	print();

	delete();
	delete();
	delete();
	delete();
	delete();

	printf("\n");
	delete();

	printf("\n");
	insert(34);

	print();

	return 0;
}

```
