---
title: "GParted"
date: 2007-07-13
forum: General Help
---

### Post by deco57 on 2007-07-13
I currently have ubuntu installed on my hard drive i would like to dual boot ubuntu and windows.
I try to make a new partion with GParted but the option to create a new partion is disabled.

Any ideas?

---

### Post by merlinus on 2007-07-13
Use the gparted live cd.  You cannot partition the drive that you are currently using.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

-merlin

---

### Post by stchman on 2007-07-13
> **merlinus said:**
> Use the gparted live cd.  You cannot partition the drive that you are currently using.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

-merlin

he can also use gparted on the Ubuntu LiveCD.  One thing that he needs to remember is that if he installs XP or Vista that it will over write GRUB and he will have to reinstall GRUB.

---

### Post by merlinus on 2007-07-13
> 
he can also use gparted on the Ubuntu LiveCD


Yes, but it is not the latest version and has limitations in terms of resizing and moving partitions.

Good point, though, about installing windows after ubuntu and the overwriting of grub, necessitating its reinstall -- which can be done from the live cd.

-merlin

---

