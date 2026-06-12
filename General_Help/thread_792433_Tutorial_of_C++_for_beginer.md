---
title: "Tutorial of C++ for beginer"
date: 2008-05-12
forum: General Help
---

### Post by jingpro on 2008-05-12
Hi,

I am a newbie of Linux. I used to use Visual studio to do C++ programming, now I want to try it under Ubuntu.

Anyone can give me some suggestions to start with? Such as: what packages for C++ shall I download? Are there more than one C++ solutions in Unbuntu, and which is best (or most popular)? 

If there is a tutorial for C++ input, edit, compile, run....that would be great for me to start with.

I searched this forum, returned useless results, so I post here. Thanks a lot for your help.

-Derek

---

### Post by sipickles on 2008-05-13
Hi Derek,

Welcome to Linux and Ubuntu!

If you are used to Visual C++ I'd recommend Code::Blocks as an alternative IDE for C++, although I'll probably start a flame-war on that front! 

Have a look here:

[Code::Blocks]("http://www.codeblocks.org/")

You'll need a compiler too, so install g++ using your Synaptic Package Manager. Code::Blocks should find this on first run.

You can always use g++ from the command line too if that is your bag! (eek, not for me!)

hth

Si

---

### Post by brethren on 2008-05-13
use synaptic and search for build-essential. this will install the g++ compiler and standard libraries

to compile a simple c++ console app from the command line

g++ helloworld.cpp -o hello

this will compile a cpp file called helloworld and output an executable call hello.out.

---

