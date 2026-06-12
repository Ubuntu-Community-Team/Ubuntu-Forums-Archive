---
title: "symbolic link problem"
date: 2007-02-04
forum: General Help
---

### Post by flapane on 2007-02-04
How to solve this problem?
It doesn't bother me, but I'd like to understand how to fix it
[[IMG]http://img296.imageshack.us/img296/3554/sk35uo6.th.jpg[/IMG]](http://img296.imageshack.us/img296/3554/sk35uo6.jpg)

---

### Post by dcstar on 2007-02-04
> **flapane said:**
> How to solve this problem?
It doesn't bother me, but I'd like to understand how to fix it
[[IMG]http://img296.imageshack.us/img296/3554/sk35uo6.th.jpg[/IMG]](http://img296.imageshack.us/img296/3554/sk35uo6.jpg)

It seems to be saying that the files in that directory are expected to be Symbolic links, but are actual files.

Something - or someone - seems to have installed that directory incorrectly, unless you can find out what did it you may not have much chance of fixing it.

---

### Post by flapane on 2007-02-05
I wonder it happend when I installed some 32bit packages manually (dpkg -x) but I don't know hot to fix, I have my ubuntu constantly upgraded from over 1year....

---

### Post by paparucino on 2007-02-05
> **flapane said:**
> I wonder it happend when I installed some 32bit packages manually (dpkg -x) but I don't know hot to fix, I have my ubuntu constantly upgraded from over 1year....
Did you try to run ldconfig?

---

### Post by flapane on 2007-02-05
yes I already did

---

### Post by flapane on 2007-02-12
flapane@a64:~$ sudo ldconfig
Password:
ldconfig: /usr/lib32/librsvg-2.so.2 is not a symbolic link

ldconfig: /usr/lib32/libcroco-0.6.so.3 is not a symbolic link

ldconfig: /usr/lib32/libgsf-1.so.114 is not a symbolic link

ldconfig: /usr/lib32/libglitz.so.1 is not a symbolic link

ldconfig: /usr/lib32/libgpm.so.1 is not a symbolic link

ldconfig: /usr/lib32/libslang.so.2 is not a symbolic link

ldconfig: /usr/lib32/libncurses.so.5 is not a symbolic link

ldconfig: /usr/lib32/libpanel.so.5 is not a symbolic link

ldconfig: /usr/lib32/libmenu.so.5 is not a symbolic link

ldconfig: /usr/lib32/libform.so.5 is not a symbolic link

ldconfig: /usr/lib32/libaa.so.1 is not a symbolic link

ldconfig: /usr/lib32/libSDL-1.2.so.0 is not a symbolic link

ldconfig: /usr/lib32/libXxf86dga.so.1 is not a symbolic link

ldconfig: /usr/lib32/libaudiofile.so.0 is not a symbolic link

---

