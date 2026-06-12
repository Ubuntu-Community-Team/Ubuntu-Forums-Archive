---
title: "Does Ubuntu have support for Makefiles"
date: 2007-02-01
forum: General Help
---

### Post by tripleZero on 2007-02-01
When i type 'make' the terminal prints 
bash: make: command not found

So I used the synaptic package manager to see if I could install support for Makefiles, but I couldnt find it.  I found something called Imake (which I never heard of).  So my question is how can I get the software that will allow me to use Makefiles?

Thanx to any one who can help me out.

---

### Post by josesanders on 2007-02-01
When you run the command 'make', what you are actually doing is compiling a program from the source, so what you need is the build essentials:

$ sudo apt-get install build-essential

Most of the time, though, you shouldn't need to build anything from the source, since most programs are available from the repositories already compiled.

---

### Post by tripleZero on 2007-02-01
Cool it works!  Thank you

---

