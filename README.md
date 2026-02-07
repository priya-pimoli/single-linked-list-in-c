# single-linked-list-in-c
linked list whole program in c
this is a menu based program


#include <stdio.h>
#include<stdlib.h>

struct node{
    int data;
    struct node *next;
};
struct node *head=NULL;
void insertatend(int data){
   struct node*newnode;
   newnode=(struct node*)malloc(sizeof ( struct node));
   newnode->data=data;
   newnode->next=NULL;
   if(head==NULL){
       head=newnode;
       return;
   }else{
       struct node*temp=head;
       while(temp->next!=NULL){
           temp=temp->next;
       }
       temp->next=newnode;
   }
}
void display(){
    struct node*temp=head;
    if(head==NULL){
        printf("list is empty");
        return;
    }else{
        while(temp!=NULL){
            printf("%d ->",temp->data);
            temp=temp->next;
        }
        printf("null");
    }
}
void insertatbeg(int data){
    struct node*newnode=(struct node*)malloc(sizeof(struct node));
    newnode->data=data;
    newnode->next=head;
    head=newnode;
}
void deleteatbeg(){
    struct node*temp=head;
    if (head == NULL) {
        printf("List is empty\n");
        return;
    }
    head=temp->next;
    free(temp);
}
void deleteatend(){
    struct node *temp ,*prev;
      if (head == NULL) {
        printf("List is empty\n");
        return;
    }
    if(head->next==NULL){
     free(head);
     head=NULL;
     return;
    }
    
    temp=head;
   while(temp->next!=NULL){
       prev=temp;
       temp=temp->next;
       
   } 
   prev->next=NULL;
   free(temp);
}
int main() {
int choice, data, key;

    do {
        printf("\n--- MENU ---\n");
        printf("1. Insert at Beginning\n");
        printf("2. Insert at End\n");
        printf("3. Delete from Beginning\n");
        printf("4. Delete from End\n");
        printf("5. Display\n");
        printf("6. Exit\n");

        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1:
                printf("Enter data: ");
                scanf("%d", &data);
                insertatbeg(data);
                break;

            case 2:
                printf("Enter data: ");
                scanf("%d", &data);
                insertatend(data);
                break;

           

            case 3:
                deleteatbeg();
                break;

            case 4:
                deleteatend();
                break;

            case 5:
                display();
                break;

            case 6:
                printf("Exiting program\n");
                break;

            default:
                printf("Invalid choice\n");
        }
    } while (choice != 6);

    return 0;
}