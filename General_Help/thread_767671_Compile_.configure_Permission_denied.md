---
title: "Compile ./configure Permission denied"
date: 2008-04-25
forum: General Help
---

### Post by SadaraX on 2008-04-25
I'm using a fresh install of Kubuntu 8.04 with KDE3 (though this is not a KDE/Gnome problem). I have installed libc6-dev, make, automake, autoconf, g++, gcc and other things.

Whenever I try to compile something with ./configure, I have problems. It says:

> 
bash: ./configure: /bin/sh: bad interpreter: Permission denied


I found a way around this by doing: "sh ./configure" but the configure script fails because it try to execute './a.out' at one point as a check, and gets the error:

> 
./configure: line 2827: ./a.out: Permission denied


This is a fairly serious error, since this means I cannot compile things. Anyone know of this bug and if there is a fix?

---

### Post by natrixgli on 2008-04-25
[http://azeemarif.blogspot.com/2004/09/aout-permission-denied.html](http://azeemarif.blogspot.com/2004/09/aout-permission-denied.html)

yes? no?

-n8


EDIT: May be able to work around by moving to another drive / partition and then excecuting. If the program is on a removable FAT32 drive it would make sense as I think default mount option for FAT32 includes 'noexec'

-n8

---

### Post by SadaraX on 2008-04-26
Thank you. That fixed the problem. The problem was how I had mounted my harddrive. I normally configure my /etc/fstab by hand, but this time I figured "What the hey? I'll just let KDE do it for me through their GUI." Well, the GUI set the drive with 'noexec' as an option when mounting.

I changed the option, remounted and everything was fine.

---

