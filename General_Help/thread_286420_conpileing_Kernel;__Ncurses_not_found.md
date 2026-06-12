---
title: "conpileing Kernel;  Ncurses not found"
date: 2006-10-27
forum: General Help
---

### Post by pk386 on 2006-10-27
Hey all. This is my first post YEA!

Ok I'm using Kubuntu 6.06 and trying to build my fist kernel.

I've got the 2.4.27 source from the ubuntu repositories and when I try

$make menuconfig 

I get "cannot find Ncurses". I did I know what your thinking... I DO have Ncurses-dev installed. 

so what now? I'm lost...](*,) 

BTW what is this xconfig I've seen once or twice?

Thanks all Morgan

---

### Post by po0f on 2006-10-27
pk386,

Why are you trying to compile such an old kernel?

`make xconfig` gives you a Qt front-end to configuring your kernel.

---

### Post by pk386 on 2006-10-27
I didn't know it was an old kernel....


it's what

$apt-get install kernel-source 

downloaded for me.


Should I be downloading it from [www.kernel.org](www.kernel.org) or something?

---

### Post by po0f on 2006-10-27
pk386,

You probably want [this](http://packages.ubuntu.com/dapper/devel/linux-source) instead, if you are using Dapper.

```
$ sudo apt-get install linux-source-`uname -r`
```
will install the source for the currently booted kernel.

---

### Post by lloyd_b on 2006-10-27
RE: The "ncurses" issue (which you will see with any kernel version).

You need to install the package "ncurses-dev" (which will install the current libncurses if you don't already have it)...

Since you're on Kubuntu, which has QT already installed, I'd go with "make xconfig" instead of "make menuconfig".  It's prettier, and easier to navigate, than the "menuconfig".

Lloyd B.

---

### Post by pk386 on 2006-10-28
It's compiling now!

Took me a while to go through the options...

Thanks

---

### Post by pk386 on 2006-10-28
When I installed Linux source 

By using as root

$apt-get install linux-source

Unzipped and un-tared it and used linux-source instead of Kernel-source then used in the linux-source dir... 

$make menuconfig 

worked just fine!

(I just felt like I should write exactly what I did... I don't like it when I read forums that the last responce is "it works!" just incase someone else runs in to this problem.)

---

