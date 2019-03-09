//Program to create a node, insert a node at beginning over th created node and iterating through the list to display the contents....

#include <iostream>

using namespace std;
class student{
public:
string name;
student *next;
}*start,*save,*ptr,*rear,*ins;


//function to create a new node when the linked lists is empty......
student* create(string s)
{
    ptr = new student;
    ptr->name=s;
    ptr->next=NULL;
    return ptr;
}

//function to insert a new node in the starting of the linked lists........
student* insrt(student *s, student *head)
{
    save = new student;
    save=head;
    head=s;
    s->next=save;
    return head;
}

//function to iterate through a linked list and display it............
void disp(student *iter){
while(iter!=NULL)
{
    cout<<iter->name<<"->";
    iter=iter->next;
}
cout<<endl;
}

//function to insert a new node at the end of the currently available linked list......
student* insrear(string val)
{
    int n;
    save = new student;
    student *r= new student;
    r->name = val;
    save=start;
    do{
    if(save->next!=NULL)
        save=save->next;
    else
        n=0;
    }while(n!=0);
    save->next = r;
    r->next = NULL;
    return start;

}

student* delstart(student *head)
{
    head = head->next;
    return head;
}

student* delrear(student *head)
{
    save = new student;
    save = head;
    int n=1;
    do{
        if(head->next->next!=NULL)
            head=head->next;
        else
            n=0;
    }while(n!=0);
    head->next=NULL;
    return save;
}
int main()
{
    cout<<"Enter values for the new node : ";
    string value;
    cin>>value;
    start = new student;             //"start" represents the start of the linked list.
    start = create(value);
    cout<<"Node successfully created.\n";
    cout<<"Enter values for a new node to be inserted at the start : ";
    cin>>value;
    ins = new student;
    ins->name = value;
    ins->next = NULL;
    start = insrt(ins,start);
    disp(start);
    for(int i=0; i<5; ++i)
    {
    cout<<"\nEnter a value for the node to inserted at the end : ";
    cin>>value;
    rear=new student;
    rear->name = value;
    rear->next =  NULL;
    start = insrear(value);
    }
    disp(start);
    start = delstart(start);
    disp(start);
    start = delrear(start);
    disp(start);
    delete start,ptr,rear,ins,save;
    return 0;
}
