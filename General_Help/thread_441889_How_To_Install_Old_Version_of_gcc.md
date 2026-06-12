---
title: "How To Install Old Version of gcc"
date: 2007-05-13
forum: General Help
---

### Post by kiaran on 2007-05-13
I was doing fine with the latest gcc compiler except that now some of the software I am working on is returning "missing symbol" errors. To clarify, I am creating plug-ins for the Maya 3d animation software package and it requires v4.0.2 of gcc. Ubuntu comes with the newer 4.1 gcc compiler.

I see that I can apt-get 4.1 and 3.4 but nothing in-between! I've tried downloading some rpms off the internet and using alien to convert to debian. With that, I've managed to get gcc 4.0.2 actually installed, but I can't find g++ to add C++ support to it! In addition to that, I think I need the gcc-base package as well. Argh!

Does anyone know a site where you can download all the old gcc packages? Or better yet a repository with the older versions so I could just use apt-get?

Any help will be greatly appreciated. Thanks.

---

### Post by kiaran on 2007-05-19
Surely it's not impossible to roll-back your version of gcc? Does nobody know how?

I'm desperate here. If I can't find a solution I'm going to have to have to go back to Edgy Eft and kiss Feisty goodbye :(

Any help is greatly appreciated. Thanks! :)

---

### Post by skaber on 2007-05-21
same here. I need gcc 4.0 but there is no package that lets me install it easily with Synaptic.
Anyone ?

---

### Post by skaber on 2007-05-22
I finally download gcc-4.0.0 from [http://gcc-ca.internet.bs/releases/](http://gcc-ca.internet.bs/releases/)
and followed the instructions in INSTALL/Readme to configure, make and install gcc-4.0.0

My success was to use the ./configure --target=xxxxx (depends on architecture) --enable-languages=x,x
e.g: ./configure --target=i686-pc-linux-gnu-gcc --enable-languages=c,c++

configure needs to be called on the root folder of the extracted .tar.gz, not in the gcc-4.0.0/gcc folder.

Good luck, this should work for any version of gcc

---

