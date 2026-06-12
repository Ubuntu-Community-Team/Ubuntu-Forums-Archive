---
title: "gcc segmentation fault on the following program pls help......!"
date: 2016-04-03
forum: General Help
---

### Post by Syed_Umair on 2016-04-03
PROGRAM

```
#include<stdio.h> 
#include<stdlib.h> 
#include<string.h> 
struct Listnode 
{ 
    char data[50]; 
    int leader,block,u_goto,c_goto; 
    struct Listnode *next; 
    char label[10],target[10]; 
}*temp,*cur,*first=NULL,*last=NULL,*cur1; 
 
FILE *fpr; 
void createnode(char code[50]) 
{ 
    temp=(struct Listnode *)malloc(sizeof(struct Listnode)); 
    strcpy(temp->data,code); 
    strcpy(temp->label,'\0'); 
    strcpy(temp->target,'\0'); 
 
     temp->leader=0; 
    temp->block=0; 
    temp->u_goto=0; 
    temp->c_goto=0; 
    temp->next=NULL; 
 
       if(first==NULL) 
      { 
      first=temp; 
      last=temp; 
      } 
      else 
      { 
      last->next=temp; 
      last=temp; 
      } 
} 
void printlist() 
{ 
        cur=first; 
        printf("\nMIR  code is \n\n"); 
        while(cur!=NULL) 
        { 
            printf("\ncode:%s",cur->data); 
            printf("\nleader:%d\t",cur->leader); 
            printf("block:%d\t",cur->block); 
            printf("u_goto:%d\t",cur->u_goto); 
            printf("c_goto:%d\t",cur->c_goto); 
            printf("label:%s\t",cur->label); 
            printf("target:%s\n",cur->target); 
 
              cur=cur->next; 
        } 
 
} 
 
void main() 
{ 
    char codeline[50]; 
    char c,dup[50],target[10]; 
    char *substring,*token; 
    int i=0,block,block1; 
    int j=0; 
    fpr= fopen("input.txt","r"); 
    while((c=getc(fpr))!=EOF) 
    { 
        if(c!='\n') 
        { 
            codeline[i]=c; 
            i++; 
        } 
        else 
        { 
            codeline[i]='\0'; 
            createnode(codeline); 
            i=0; 
        } 
    } 
        codeline[i]='\0'; 
    createnode(codeline); 
    fclose(fpr); 
       cur=first; 
    cur->leader=1; 
    while(cur!=NULL) 
    { 
        substring=strstr((cur->data),"if"); 
        if(substring==NULL) 
         { 
             if((strstr((cur->data),"goto"))!=NULL) 
             { 
              cur->u_goto=1; 
              (cur->next)->leader=1; 
             } 
              else 
             { 
               cur->c_goto=1; 
            (cur->next)->leader=1; 
             } 
            substring=strstr((cur->data),":"); 
        } 
        if(substring!=NULL) 
        { 
        cur->leader=1; 
        } 
           substring=strstr((cur->data),"call"); 
        if(strstr(cur->data,"return")!=NULL) 
        { 
        cur->leader=1; 
        (cur->next)->leader=1; 
        } 
        cur=cur->next; 
    } 
    cur=first; 
    while(cur!=NULL) 
    { 
        if((cur->u_goto==1)||(cur->c_goto==1)) 
           { 
               substring=strstr(cur->data,":"); 
               if(substring!=NULL) 
               { 
                   token=strstr(substring,"L" ); 
                   if(token!=NULL) 
                   strcpy(cur->target,token); 
               } 
               else 
               { 
            substring=strstr(cur->data,"L"); 
                   if(substring!=NULL) 
                   strcpy(cur->target,substring); 
               } 
           } 
           if(strstr(cur->data,":")!=NULL) 
           { 
               strcpy(dup,cur->data); 
            token=strtok(dup,":"); 
            if(token!=NULL) 
               strcpy(cur->label,token); 
           } 
        cur=cur->next; 
    } 
    cur=first; 
    while(cur!= NULL) 
    { 
     cur=cur->next; 
     if((cur->leader)==1) 
     { 
        j++; 
        cur->block=j; 
     } 
     else 
     cur->block=j; 
    } 
    printf("\n\n......Basic Blocks......\n"); 
    cur=first; 
    j=0; 
    printf("\nBlock %d:",j); 
    while(cur!=NULL) 
    { 
        if((cur->block)==j) 
        { 
            printf("%s",cur->data); 
            printf("\n\t"); 
            cur=cur->next; 
        } 
        else 
        { 
        j++; 
        printf("\nBlock %d:",j); 
        } 
    } 
    printf ("\t\t.......Control Flow.......\n\n"); 
    cur=first; 
    i=0; 
    while(cur!=NULL) 
    { 
        if((cur->block)!=(cur->next)->block) 
        { 
            block=cur->block; 
            if(cur->u_goto==1) 
            { 
                strcpy(target,cur->target); 
                cur1=first; 
                while(cur1!=NULL) 
                { 
                    if(strcmp(cur1->label,target)==0) 
                    { 
                        block1=cur1->block; 
                        printf("\t\tBlock%d---------->Block%d\n",block,block1); 
                    } 
                    cur1=cur1->next; 
                } 
            } 
            else if(cur->c_goto==1) 
            { 
                strcpy(target,cur->target); 
                cur1=first; 
                while(cur1!=NULL) 
                { 
                    if(strcmp(cur1->label,target)==0) 
                    { 
                        block1=cur1->block; 
                        printf("\t\tBlock%d---TRUE--->Block%d---FALSE--->Block%d\n",block,block1,(block+1)); 
                    } 
                    cur1=cur1->next; 
                } 
            } 
            else if(strstr(cur->data,"return")==NULL) 
            { 
                printf("\t\tBlock%d---------->Block%d\n",block,(block+1)); 
            } 
            else 
            printf("\t\tBlock%d---------->NULL\n",block); 
        } 
        cur=cur->next; 
    } 
    cur=last; 
    block=cur->block; 
    printf("\t\tBlock%d--------->NULL",block); 
}


input.txt

m <- 0

v <- 0
L1 :  if v < n goto L5
r <- v
s <- 0
return
L2 : if r >= n goto L3
v <- v + 1
goto L1
L3 :  x = a
s <- s + x
if s <= m goto L2
call P
L4 :  r <- r + 1
goto L2
L5 : return m
m <- m+10
s <- s -10
```



please help me solve this error

---

### Post by Chuck_McManis on 2016-04-06
you want to brush up on memory allocation and learn about unprotected strcpy. Basically if you have a 50 character input string you will overwrite your structures. But even better, start up gdb and put a breakpoint on your 'createnode' call, then watch what it does when you enter your text.

---

