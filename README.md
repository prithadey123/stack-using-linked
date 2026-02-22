Overview
This project demonstrates the implementation of a **Stack data structure using a Linked List** in C.

A Stack follows the **LIFO (Last In, First Out)** principle:
- The last element inserted is the first one removed.

Unlike array implementation, a linked list stack:
- Does not have a fixed size.
- Grows dynamically using memory allocation.
- Handles overflow only when memory is unavailable.

---
 Source Code

```c
#include <stdio.h>
#include <stdlib.h>

// Define stack node
struct Node {
    int data;
    struct Node* next;
};

struct Node* top = NULL;

// Push operation
void push(int value) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));

    if (newNode == NULL) {
        printf("Stack Overflow! Memory not available\n");
        return;
    }

    newNode->data = value;
    newNode->next = top;
    top = newNode;

    printf("%d pushed into stack\n", value);
}

// Pop operation
void pop() {
    if (top == NULL) {
        printf("Stack Underflow! Stack is empty\n");
        return;
    }

    struct Node* temp = top;
    printf("%d popped from stack\n", top->data);
    top = top->next;
    free(temp);
}

// Display stack
void display() {
    if (top == NULL) {
        printf("Stack is empty\n");
        return;
    }

    struct Node* temp = top;
    printf("Stack elements are:\n");
    while (temp != NULL) {
        printf("%d\n", temp->data);
        temp = temp->next;
    }
}

int main() {
    push(10);
    push(20);
    push(30);

    display();

    pop();
    display();

    return 0;
}
```

---

 Explanation

 Stack Node Structure
- `struct Node` contains:
  - `data` → Stores the value.
  - `next` → Points to the next node.

 Push Operation
- Allocates memory for a new node.
- Checks for memory allocation failure.
- Inserts the node at the top of the stack.
- Updates `top`.

 Pop Operation
- Checks if stack is empty.
- Removes the top node.
- Updates `top`.
- Frees allocated memory.

 Display Operation
- Traverses from `top` to `NULL`.
- Prints stack elements.

---

 Sample Output

```
10 pushed into stack
20 pushed into stack
30 pushed into stack
Stack elements are:
30
20
10
30 popped from stack
Stack elements are:
20
10
```

---

 Time Complexity

- Push: **O(1)**
- Pop: **O(1)**
- Display: **O(n)**

---

Advantages Over Array Implementation
- No fixed size limitation
- Dynamic memory usage
- Efficient insertion and deletion

---

 How to Compile and Run

 Compile:
```
gcc stack_linkedlist.c -o stack
```

Run:
```
./stack
```

---

 Concepts Used
- Structures in C
- Pointers
- Dynamic Memory Allocation (`malloc`, `free`)
- Linked List
- Stack Data Structure
- LIFO Principle
