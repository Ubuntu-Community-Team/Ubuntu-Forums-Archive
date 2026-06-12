---
title: "I NEED a C++ program."
date: 2008-06-21
forum: General Help
---

### Post by Masterj15 on 2008-06-21
Any will do but I need one that does EVERYTHING!

Thanks :)

---

### Post by sdennie on 2008-06-21
```


#include <iostream>

int main()
{
   std::cout << "Hello World" << std::endl;

   return 0;
}

```

Doesn't quite do "EVERYTHING" though...

---

### Post by Het Irv on 2008-06-21
No Problem, give me a few minuets.

It might take a while actually, I need to learn C++ first

---

### Post by mali2297 on 2008-06-21
What do you mean by *C++ program*? Compiler, IDE or just a program written in C++?

---

### Post by Masterj15 on 2008-06-21
> **mali2297 said:**
> What do you mean by *C++ program*? Compiler, IDE or just a program written in C++?

I have anjuti ide but I don't know how to build the code or anything.

I need a compiler, and ide!

---

### Post by hessiess on 2008-06-21
> **Masterj15 said:**
> I have anjuti ide but I don't know how to build the code or anything.

I need a compiler, and ide!

see the sticky in the programming forum. quite a lot of people just use a text editor+terminal for dev.

---

### Post by mali2297 on 2008-06-21
> **Masterj15 said:**
> I have anjuti ide but I don't know how to build the code or anything.

I need a compiler, and ide!

You need to install the meta package **build-essential** from the repositories, then you will also get a  C++ compiler.

Next, try compiling vor's code. I have never used Anjuta but there should be some option to compile in the menus.

---

### Post by LunatikOwl on 2008-06-21
I'm not a C++ programmer(just a wannabe:( ) but you might want to check eclipse and kdevelop(both in the repositories). Also, although most IDE's can manage automatically the code, the de-facto standard in the free-software community is the automake and autoconf. Theres plenty of documentation on both and they appear quite ok. Also, most IDEs can rely on them to do the actual configure and compile. You also might want to check the book "Advanced Linux Programming" which covers the basic principals and API for developing robust Linux aplications, the book is avaiable for free.

Just my two cents...

---

### Post by babylon2233 on 2008-06-21
Like hessiess said, text editor + compiler is more than enough.

---

### Post by mtantawy on 2008-06-21
> **mali2297 said:**
> What do you mean by *C++ program*? Compiler, IDE or just a program written in C++?
JUST A QUESTION

what is the difference between Compiler&IDE???

Mahmoud Tantawy

---

### Post by Masterj15 on 2008-06-21
> **mtantawy said:**
> JUST A QUESTION

what is the difference between Compiler&IDE???

Mahmoud Tantawy

I don't know what ide is but a compiler is the program that builds your program into an actual program. (I think)

---

### Post by mali2297 on 2008-06-21
> **mtantawy said:**
> JUST A QUESTION

what is the difference between Compiler&IDE???

Mahmoud Tantawy

An IDE (Integrated Development Environment) provides a single environment in which you can edit, compile and debug your code. 

The compiler, in this case g++, is part of the IDEs but it can also be used by itself in a terminal. To compile the source file *foo.cc* into the executable *foo*, type
```

g++ foo.cc -o foo

```

---

