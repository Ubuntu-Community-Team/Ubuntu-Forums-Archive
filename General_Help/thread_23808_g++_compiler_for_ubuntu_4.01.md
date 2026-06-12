---
title: "g++ compiler for ubuntu 4.01"
date: 2005-04-04
forum: General Help
---

### Post by henry on 2005-04-04
[FONT=Times New Roman]12[/FONT]

Hi:

I am new to linux. Can you guys tell me how to install g++ version 3.3 comipler step by step. 

I am using ubuntu 4.01

If posible could you send me a tutorial link for progamming in linux

Thanks

---

### Post by lao_V on 2005-04-04
I am not sure what version will be available in 4.10 but if you want to install g++ then just type sudo apt-get install g++

---

### Post by dcast on 2005-04-09
You could also go to synaptic and simply install the development base or essentials and that will give you everything you need and more for c++ and c

---

### Post by lorap on 2005-04-11
hi buddy!
as i understood you wanna study programming in linux/unix environment.
well you don't need install gcc to program in C.use unix native compiler-cc.
this's the way to compile your code:

cc -c yourcode.c

to build executable:

cc -o executable's name yourcode.c

to add a math library:

cc -o executable's name yourcode.c -lm

once you've a questions send me an email to:
[email]linuxrat@gmail.com[/email]

you're welcome friend!
have a nice day!
pavel

p.s.:
one thing you should do is to open synaptic and add documentation.
sometimes you'll need to install additional libraries.do it once you need them but don't install all at once.

---

