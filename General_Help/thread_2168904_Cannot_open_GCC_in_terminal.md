---
title: "Cannot open GCC in terminal"
date: 2013-08-19
forum: General Help
---

### Post by Jorge_Diaz on 2013-08-19
I get the following error when I try to open GCC:

gcc: fatal error: no input files
compilation terminated.

I verified and according to this GCC is already installed. I'm new to Linux so please I apologize if it's something very simple.

Edit: Something  I forgot to mention is have windows 7 installed in this machine too. So I have a double partition.

---

### Post by steeldriver on 2013-08-19
Hello and welcome to the forum

You need to tell gcc the name of the file you want to compile, i.e.

```
gcc myprog.c
```

You can optionally give it an output file as well (else the results go to a default output file called 'a.out') 

```
gcc -o myprog myprog.c
```

Hope this gets you started - you can read lots more about gcc using the built in manual pages

```
man gcc
```

---

### Post by newb85 on 2013-08-19
The syntax for the gcc command requires at least one input file--the file holding the code to be compiled.  That syntax is given in the manual page for gcc, which you can view by issuing
```
man gcc
```
in the terminal.

---

### Post by Jorge_Diaz on 2013-08-19
```
gcc -o myprog myprog.c
```

Hope this gets you started - you can read lots more about gcc using the built in manual pages

```
man gcc
```[/QUOTE]

Thanks a lot for the info, I just tried the code you gave me and now I get this error: "gcc: errormyprog.c: no such file or directory

Maybe it has to do with the fact that I have installed windows 7 in this computer too?

---

### Post by steeldriver on 2013-08-19
Does the directory you are running the command in actually contain a file called 'myprog.c'?

What are you trying to do exactly? Have you written a C source code file that you wish to compile? Do you understand what the gcc command does?

---

