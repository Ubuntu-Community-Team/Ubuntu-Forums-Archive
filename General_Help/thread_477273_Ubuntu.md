---
title: "Ubuntu"
date: 2007-06-18
forum: General Help
---

### Post by The Wisedude on 2007-06-18
Ok well.. My Windows crashed(For the last time, trust me).

And so I Installed Linux (Ubuntu), And it is perfect, my hardrive is 189gb. And I used so 92GB for Ubuntu.

Now when I turn on the PC it says I have 2 OS's.

How can I change this? So that Ubuntu Uses the "WHOLE" Hardrive?

---

### Post by stoodleysnow on 2007-06-18
Well, congrats on choosing Ubuntu, wise dude, but if you wanted Ubuntu on the whole hard disk could you not have selected that option DURING INSTALLATION?:rolleyes:
I am assuming it is possible to stretch the Ubuntu partition after installation anyway though (for it should be):-k

---

### Post by Phixion on 2007-06-18
Yep, use gparted in Linux or Partition Magic in Windows.

---

### Post by kdarkentity on 2007-06-18
My advice to you having done this millions of times would be to format your entire drive and install Ubuntu over the entire hard drive... or you can leave it the way it is , try to fix windows and dual boot like i do

---

### Post by The Wisedude on 2007-06-19
Ok thanks everyone. But how would i use Gparted to do this operation?

---

### Post by Circus-Killer on 2007-06-19
if you dont have information that you desperately need, then i would spend the 25 minutes that it takes to do a fresh install. personally, i dont like resizing partitions. i would much rather re-install, and when it comes to the section for partitioning, select "use entire disk" option.

this is however just my opinion and preferred method, feel free to use gparted if you want, but i cant give any advice on using it (never have used it).

---

### Post by Crafty Kisses on 2007-06-19
> **The Wisedude said:**
> Ok well.. My Windows crashed(For the last time, trust me).

And so I Installed Linux (Ubuntu), And it is perfect, my hardrive is 189gb. And I used so 92GB for Ubuntu.

Now when I turn on the PC it says I have 2 OS's.

How can I change this? So that Ubuntu Uses the "WHOLE" Hardrive?

You can reformat your HDD so Ubuntu is the default OS off the LiveCD.

---

### Post by Qu4k3R on 2007-06-19
I would make windows to get "hidden"
in a terminal I would run this:

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup_2OS

Then (with GNOME)

> 
gksudo gedit /boot/grub/menu.lst


(with KDE - Kubuntu)
> 
gksudo kate /boot/grub/menu.lst


The edit the last lines, so you can get windows options commented.
If you have something like this:
> 
title		Windows XP - Home Edition
root		(hd0,2)
savedefault
makeactive
chainloader	+1


Comment (with # before the options) that "section" so it looks like:
> 
#title		Windows XP - Home Edition
#root		(hd0,2)
#savedefault
#makeactive
#chainloader	+1


Then you could install ntfs-3g drivers to use windows partitions as well.

You could also reinstall Linux, formatting everything, but you will have to reinstall everything on Ubuntu.

---

