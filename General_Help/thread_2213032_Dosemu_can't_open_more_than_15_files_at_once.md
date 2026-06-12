---
title: "Dosemu can't open more than 15 files at once"
date: 2014-03-24
forum: General Help
---

### Post by gonzalo6 on 2014-03-24
I'm currently trying to run a dos console application which has to open a certain number of files simultaneously ( more than 15 ). I've tried with dosbox and dosemu. Dosbox is supposed to support 127 simultaneous files, and dosemu has the config.sys file in which you can set this limit. So I tried a little C program that opens files. 

```

#include<stdio.h>
#include<stdlib.h>
#include<string.h>
#include<errno.h>


int main (void) {


 FILE *archivos[300];
 char numstr[15];
 int i=0,nmax=0;
 
 printf("\nHow many files do you want to open: ");


 scanf("%d",&nmax);
 for( i=0; i<nmax ; i++) {
   sprintf( numstr, "test%d.dat", i);


   if(!(archivos[i]=fopen( numstr ,"w")))
   {
     printf("\nCouldn't open file %s", numstr);
     printf("\nDescription: %s\r %d", strerror(errno), errno);
     printf("\nThe max open files was: %d", i);
     exit(1);
   }
 }
 
 printf("\nNo errors. The open files number is : %d\n", i);


 for( i=0; i<nmax; i++)
   fclose( archivos[i] ); 
 return( 0 );
}

```

And I got this result:
> [FONT=arial]
How many files do you want to open:  20[/FONT]
[FONT=arial][FONT=arial]Couldn't open file test15.dat[/FONT][/FONT]
[FONT=arial][FONT=arial]Description: No such file or directory 2[/FONT][/FONT]
[FONT=arial][FONT=arial]The max open files was: 15[/FONT][/FONT][FONT=arial][FONT=arial]
[/FONT][/FONT]

I'm using dosemu-1.4.0.8 in Ubuntu 12.04LTS 32-bit

The weird thing is i get the same amount of opened files in dosbox, so it seems to be a misconfiguration between this emulators and Ubuntu. Thanks for your help.

---

