---
title: "Ubuntu 13.10 doesn't boot into graphical mode after resizing boot partition"
date: 2013-12-16
forum: General Help
---

### Post by rrubio82 on 2013-12-16
Hello!

I had the terrible idea of shrinking my linux partition (not moving it, only shrinking it) and expanding the swap so I could hybernate my Ubuntu 13.10 machine. I made that with gparted-live without problems. After that, my ubuntu seems to boot correctly, but at the end I have my tty6 command prompt login, not my graphical greeter. I've tried everything: rescataux, the "boot-repair" utility from the Ubuntu live CD (and the result is here: [http://paste.ubuntu.com/6585186/](http://paste.ubuntu.com/6585186/)), but the same occurs. Also, when I try to do "sudo update-grub" it says "error getting canonical path" of my ubuntu partition. Please, if someone has any idea, I need help... sorry for my bad english and thanks in advance.

---

### Post by Tristan_Williams on 2013-12-16
When you boot, can you use tty1 - 6?

Also, which display manager are you using? You can usually find out by reading /etc/X11/default-display-manager
Just post the contents of that file in your next reply.

Another question, which desktop environment are you using? (Unity, Gnome, Xfce, KDE, etc...)

---

### Post by rrubio82 on 2013-12-18
Hi Tristan, thanks for your answer. Yes, I can use tty from 1 to 6, my display manager is lightdm and I'm using Unity as desktop environment. In addtion, when I try to reinstall grub, it says that grub cannot acces /boot/grub at boot time, but any boot recovering application was able to repair that... thanks a lot.

---

### Post by Tristan_Williams on 2013-12-18
You're welcome :) always glad to help

---

### Post by rrubio82 on 2013-12-20
But the problem is still there...

---

### Post by PopsTheSailor on 2013-12-24
OK, I'm just completely shooting in the dark here but when you resized  the partition, did you shrink it so much that there is no room left to  reinstall grub?

Maybe put the sizes back to what they were before you shrunk the main and expanded the swap.

One more "shot in the dark". Have you tried creating a boot repair disk and using that? Maybe it works different enough from the Live-CD to fix it. 

All long shots. Good luck!

---

### Post by monkeybrain20122 on 2013-12-24
Not that this will help your present predicament, but I learned the hard way that resizing the root  partition tends to be a bit tricky (expanding it to the right always works, but shrinking or expanding on the left may result in unbootable system sometimes, or so it seems) 

So in the future if you want to change partition size or layout use fsarchiver to clone the relevant partition. Then use gparted to reformat the old partition, and then resize, restructure the hard drive in whatever way you want and use fsarchiver to restore the clone into your new partition. It is fast and safe and I would recommend it over clonezilla (which is more commonly used judging from posts on this forum) because clonezilla has the restriction that you must restore to a partition not smaller than the one you cloned even though the cloned partition may be mostly empty. fsarchiver has no such restriction, you can restore to any partition as long as it is big enough to hold the data.

---

### Post by rrubio82 on 2013-12-26
Pops2: I shrank the partition but only from 32GB to 28GB, so I don't think is a grub space problem. The only problem I can think about is that I lost information in the shrinking operation.  				 				 					 						 	I also used several boot repair CD's (Ubuntu + boot repair tool, ultimatebootcd, etc.) and they all did the same: nothing. monkeybrain20122: Ok, I usually use clonezilla, but I will try fsarchiver, thanks.

---

