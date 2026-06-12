---
title: "How to make Wubi Boot with Safe Mode GFX?"
date: 2007-07-30
forum: General Help
---

### Post by dubayou on 2007-07-30
I use Nvidia in SLI so i have to use safe mode GFX how can i tell Wubi to always boot ubuntu in safemode (or how do i fix the drivers)

---

### Post by ago on 2007-07-30
From ubuntu edit /boot/grub/menu.lst 

change the line:

```
default 0
```

to 

```
default 1
```

---

### Post by dubayou on 2007-07-30
what i tried was when it got tot he login screen i switched to term 2)ctrl-alt-f2 then edited the /boot/grub/menu.list to do that... but that just boots in term and doesnt startx at all..

what do i add to the boot params for safemode? also... how do i install the newest drive to fix this problem.

---

### Post by ago on 2007-07-30
> **dubayou said:**
> what i tried was when it got tot he login screen i switched to term 2)ctrl-alt-f2 then edited the /boot/grub/menu.list to do that... but that just boots in term and doesnt startx at all..
Yeah that's what I mean by "safe" mode. Old school... Press ctrl+d to continue with the normal boot.

If you get to the login screen you can pick some safer graphical setup within the options>session. Otherwise  you can choose the vesa driver via: sudo dpkg-reconfigure  xserver-xorg. But the console should be all you ever need ;P

> how do i install the newest drive to fix this problem.
Once in terminal you run something like:

sudo apt-get install PACKAGENAME

You have to look what package you need to serve your hardware. That assumes that your internet connection is working.

---

### Post by dubayou on 2007-07-30
whoo thanks.... thats why i love these forums.
im in linux now... all i gotta do is figure out how to get the latestest nvidia drivers

---

