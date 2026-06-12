---
title: "Display problems with 8.04"
date: 2008-06-13
forum: General Help
---

### Post by Theory5 on 2008-06-13
Hey. I am having display problems with ubuntu 8.04 THe login screen is too big but i know how to fix that, also when I log in most of the screen is black, except for the upper left hand conneor of the screen where I can do stuff. The rest of the screen is still responsive though.  I have an ATI HD 3870 video card and I did download the ati catalist driver for linux but that didnt help... Please help.

---

### Post by Unix_Slayer on 2008-06-13
> **Theory5 said:**
> Hey. I am having display problems with ubuntu 8.04 THe login screen is too big but i know how to fix that, also when I log in most of the screen is black, except for the upper left hand conneor of the screen where I can do stuff. The rest of the screen is still responsive though.  I have an ATI HD 3870 video card and I did download the ati catalist driver for linux but that didnt help... Please help.

In your xorg.conf, look at the screen section, and see what your virtual resolution is set at. It's in your /etc/X11 directory.

---

