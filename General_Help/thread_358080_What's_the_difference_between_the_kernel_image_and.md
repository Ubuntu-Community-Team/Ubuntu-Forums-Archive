---
title: "What's the difference between the kernel image and the kernel header files?"
date: 2007-02-10
forum: General Help
---

### Post by Blofeld on 2007-02-10
In layman's terms, what's the significant difference between a kernel's image and its header files?
Why can I install one without the other?
I've looked up "header files" on Wikipedia but it didn't light a bulb.
Thanks.

---

### Post by dagnabit dang doohickey on 2007-02-10
The [Linux Dictionary]("http://www.tldp.org/LDP/Linux-Dictionary/html/index.html") describes kernel headers as:
*The header files define structures and constants that are needed for building most standard programs. The header files are also needed for rebuilding the kernel.*

Depending on how curious you may be, you'll probably find a more satisfactory answer in this freely available book:
[Linux Kernel in a Nutshell]("http://www.kroah.com/lkn/")

---

### Post by Blofeld on 2007-02-10
Thanks for the interesting links, DDD.

---

### Post by nickoli_02 on 2007-02-10
In general, header files are source files which include source code that are to be included with another source file for compilation. So, you only need these headers when you want to compile the linux kernel yourself (I believe). 

Header files just make it easy to use the same classes and functions in different programs. For instance, say you write a function which converts an integer to the string representation and want to use this function in multiple programs, you can put it in a header file and just "include" it in the source file to be compiled.

---

### Post by Blofeld on 2007-02-13
Great answer.  Thanks, Nick.

---

