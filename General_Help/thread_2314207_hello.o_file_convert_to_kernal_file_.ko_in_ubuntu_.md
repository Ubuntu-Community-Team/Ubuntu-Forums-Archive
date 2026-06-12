---
title: "hello.o file convert to kernal file .ko in ubuntu 14.5"
date: 2016-02-19
forum: General Help
---

### Post by selvamurugan on 2016-02-19
Dear All,
 I have compiled c program and created .o file in Desktop.Now I want convert to .ko file and add it to kernel.

nura@nura:~$ cd Desktop/
nura@nura:~/Desktop$ ls
hello  hello.c  hello.c~  hello.cpp~  Makefile~
nura@nura:~/Desktop$ obj-m += hello.o
obj-m: command not found
nura@nura:~/Desktop$

---

### Post by steeldriver on 2016-02-19
'obj-m += hello.o' isn't a shell command, it's an assignment that would usually go inside your Makefile - or be passed to the 'make' program as a command line argument  ```
 make "obj-m += hello.o" 
```  Are you following some kind of kernel module programming guide? AFAIK you can't usually just convert any old C program to a kernel module. What exactly are you trying to do?

---

### Post by selvamurugan on 2016-02-20
Thank you so much for your reply.Just I want add one own .ko file in kernel.I am trying doing that.I have read out the some user guide and tutorial they were given we can convert the all .o to .ko and add it on kernel.if you have any idea please share with me.

---

### Post by steeldriver on 2016-02-20
There are many tutorials on the web: try this one

[https://en.wikibooks.org/wiki/The_Linux_Kernel/Modules](https://en.wikibooks.org/wiki/The_Linux_Kernel/Modules)

---

