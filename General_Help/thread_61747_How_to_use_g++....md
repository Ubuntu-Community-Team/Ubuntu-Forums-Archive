---
title: "How to use g++..."
date: 2005-09-02
forum: General Help
---

### Post by veraction on 2005-09-02
Sorry this is a dumb question. I've programmed in C++ a fair amount in the past but was able to use apps/scripts that compiled/linked everything for me.

So, I have a program HelloWorld.cpp that does the obvious.

How to I make it into an executable? I can get an a.out file which shows the output by using ```
./a.out
``` but still no executable

---

### Post by amohanty on 2005-09-02
when you do a 
g++ filename.cpp

what does it return?
Typically if you dont have any syntax errors, it should generate the a.out file in the same location.

AM

---

### Post by veraction on 2005-09-02
it does generate a.out

but I want an executable.. like HelloWorld (no extension) where you can just type it and it'll run... instead of ```
./a.out
```

---

### Post by RikoW on 2005-09-02
a.out is the executable!

if you just type at your command prompt:
> ./a.out

it should print "Hello World".

If you want a different name than a.out, use the -o option

> g++ filename.C -o filename.exe   # However *.exe in windows talk :)

or just rename the file:

> mv a.out HelloWorld

Cheers,

    Riko



[QUOTE=veraction]it does generate a.out

but I want an executable.. like HelloWorld (no extension) where you can just type it and it'll run... instead of ```
./a.out
```[/QUOTE]

---

### Post by veraction on 2005-09-02
Ok, I see now sortof.

What does *./* do... as in ```
./configure
``` or ```
./a.out
``` ? Just tell the system that I'm trying to run a program? (I'm used to being able to just type ```
HelloWorld
``` and have it work (but then I had an app to make a Makefile & was on solaris)

and if I wanted to link together multiple files, i.e. classes, I'd do this: ```
g++ file1.cpp file2.cpp -o myProgram
```

thanks again & sorry for the noobishness

---

### Post by Harleen on 2005-09-02
> **veraction]
What does *./* do.
[/QUOTE]

The ./ is just the path, in which your executable is looked for. The dot is the current directory and the slash the directory divider.
If you want the current directory permanently added to your search path, so your system behaves like you used to, just add this line on the end of your .bashrc
[QUOTE]export PATH=. said:**
> 

[QUOTE=veraction]
and if I wanted to link together multiple files, i.e. classes, I'd do this: ```
g++ file1.cpp file2.cpp -o myProgram
```


Exactly. That doesn't give points for style, but it works.
If you plan to write larger programs, it might be a good idea to take a look at writing own Makefiles.

---

