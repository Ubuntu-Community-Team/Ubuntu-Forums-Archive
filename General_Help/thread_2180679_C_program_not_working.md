---
title: "C program not working"
date: 2013-10-14
forum: General Help
---

### Post by harrypotter7 on 2013-10-14
This is the exact code i have written there are no errors in the code as it compiled successfully but in the output when it asks the user to enter **"enter 1 for char blah blah......."** if i press 1 and enter it is not taking the input instead it is printing the printf statements later..........






```
#include<stdio.h>
#include<string.h>
void charstuff(char *txt,char *sdat)
 {
  int ln=strlen(txt),i,j;
  sdat[0]='\0';
  strcat(sdat,"stxdle");
  for(i=0,j=6;i<ln;i++,j++)
   {
    sdat[j]=txt[i];
    if(!strncmp(txt+i,"dle",3))
     {
      sdat[j+1]='\0';
      strcat(sdat,"ledle");
      j+=5;
      i+=2;
     }
   }
  sdat[j]='\0';
  strcat(sdat,"dleetx");
 }
void bitstuff(char *txt,char *sdat)
 {
  int ln=strlen(txt),i,j;
  sdat[0]='\0';
  strcat(sdat,"01111110");
  for(i=0,j=8;i<ln;i++,j++)
   {
    sdat[j]=txt[i];
    if(!strncmp(txt+i,"11111",5))
     {
      sdat[j+1]='\0';
      strcat(sdat,"11110");
      j+=5;
      i+=4;
     }
   }
  sdat[j]='\0';
  strcat(sdat,"01111110");
 }
void main()
 {
  int ch; 
  char txt[500],sdat[500];
  printf("\n enter 1 for character stuffing any other for bit stuffing:");
  scanf("%d",&ch);
  printf("\n enter the data to be transmitted \n");
  fflush(stdin);
  gets(txt);
  if(ch==1)
   charstuff(txt,sdat);
  else
   bitstuff(txt,sdat);
  printf("\n after framing the data to be transmitted is \n");
  puts(sdat);
 }
```

---

### Post by Dave_L on 2013-10-14
It would be helpful if you could edit your post and use [ code ] tags, so that the C source code has proper indentation.

---

### Post by spjackson on 2013-10-14
Instead of
```

  scanf("%d", &ch);

```
Try
```

  gets(txt);
  sscanf(txt, "%d", &ch);

```

---

### Post by harrypotter7 on 2013-10-14
working perfectly do u mind telling me what is the reason........

---

### Post by spjackson on 2013-10-14
fflush(stdin) does not necessarily do what you might expect. In this case, it does not cause the '\n' at the end of the first line of input to be consumed. So that's what gets read by your gets(txt), and it doesn't wait for a second line.

---

