---
title: "Grub Help: Booting into Windows"
date: 2007-05-23
forum: General Help
---

### Post by anotherperson on 2007-05-23
I have installed Ubuntu Fiesty Fawn and it runs fine, but the problem is when I try to boot into Windows from the Grub menu. It allows me to select it, shows no errors, and then the screen changes to only having 
Loading ... (sorry, can't remember exactly what it is) with a blinking cursor. It then sits there and doesn't do anything. 

I am able to access the windows documents from Linux.

---

### Post by merlinus on 2007-05-23
If you re-sized your windows partition when installing Ubuntu, it is possible that your windows boot loader got lost in the process (NTLDR).

You can use your original windows cd to restore it, and then you can re-install grub using the ubuntu live cd.

A search of the forum will bring lots of information.

Good luck!

-merlin

---

### Post by theDaveTheRave on 2007-05-23
I don't know if this will be helpfull to you or not.

I can get a similar fault when i attempt to boot into Windows 98. This is due to it being a remainder of an OS on a second HDD, I just haven't removed it just in case I need it someday (not much chance of that but??)

If you want to check that you have only one version of windows available to the GRUB have a look at the respective file
(you can find it in \boot\grub\ ) called "menu.lst", if you do want to edit it, remember to save the old copy (before you bugger it up) and then just comment out the lines with hashes ##

i would recomend having a bootable CD nearby, so as if it does all go pear shaped on you then you can use it to undoo the damage!

good luck.

Dave

I would also agree with Merlin, that is probably why my windows 98 doesn't want to work,

---

