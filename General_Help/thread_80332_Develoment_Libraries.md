---
title: "Develoment Libraries"
date: 2005-10-21
forum: General Help
---

### Post by ILikeLinux on 2005-10-21
Hi, 

I just can't find the appropriate development libraries for gtk. 
I have installed the following packages:

----------------------------------------
$ dpkg -l | grep dev > dev.txt
----------------------------------------
see attached file dev.txt.

But when I try to make for old project of mine (was done with Fedora Core 3), I get things missing (see missing.txt). 

-----------------------------------------
$ make 1>missing.txt 2>&1
-----------------------------------------

Could anyone tell time what development packages are to
further installed. By the way, I am in Breezy. 
I just can't get what development libraries are missing, or is it 

Thanks in advance.

---

### Post by doclivingston on 2005-10-22
It's complaing about missing "cairo.h", so searching for packages containing "cairo" should find what you need (i.e. libcairo2-dev).

Also, if you go to packages.ubuntu.com and scroll down to "Search the contents of packages", you can enter the name of the file you are looking for and it will tell you which package it is in.

---

### Post by ILikeLinux on 2005-10-22
[QUOTE=doclivingston]It's complaing about missing "cairo.h", so searching for packages containing "cairo" should find what you need (i.e. libcairo2-dev).

Also, if you go to packages.ubuntu.com and scroll down to "Search the contents of packages", you can enter the name of the file you are looking for and it will tell you which package it is in.[/QUOTE]

Thanks for your reply, doclivingston. But I have cairo installed. 
----------------------------------------------------------
$ dpkg -l | grep cairo
ii  libcairo2                                            1.0.2-0ubuntu1      The Cairo 2D vector graphics library
ii  libcairo2-dev                                      1.0.2-0ubuntu1       Development files for the Cairo 2D graphics
-----------------------------------------------------------

I will try find the file cairo.h from Ubuntu web site. 
Thanks again.

---

### Post by doclivingston on 2005-10-22
Looking closer at the compile log, the problem is that the makefile isn't telling gcc where to look for the header (via -I/usr/include/cairo).

If it's a hand-written makefile, you'll want to add "$(pkg-config --cflags cairo)" to the flags passed to gcc, if it's made by autoconf/automake, you'll need to add the necessary bits for that.

---

