---
title: "Scilab crashes on startup"
date: 2005-09-09
forum: General Help
---

### Post by rob9812 on 2005-09-09
Hey guys,

I'm new to Ubuntu and linux, about a week now.  I've heard Scilab is a good alternative to matlab, so I decided to download it from synaptic.  It seemed to install fine, but when I went to look for it in the menus it wasn't there.  I tried to run it from the terminal, and a window opened for about a second and then terminated.  I'm just wondering what I'm doing wrong?

Thanks in advance

---

### Post by amohanty on 2005-09-10
Any error messages?

AM

---

### Post by rob9812 on 2005-09-11
No error message, a window pops up for about 1 second, and then closes.

---

### Post by kleeman on 2005-09-11
Same issue here. Some sort of font issue perhaps. Here is the error:

Fontconfig error: "local.conf", line 24: not well-formed (invalid token). 

Oddly it does not exit either.

---

### Post by kleeman on 2005-09-11
Malone bug #471

[https://launchpad.net/malone/bugs/471](https://launchpad.net/malone/bugs/471)

I downloaded the binary version and it works but with lousy fonts....

---

### Post by kleeman on 2005-09-11
More wierdness:
The Ubuntu package app runs in kde but not gnome but gives the same font error message in both. Go figure....

---

