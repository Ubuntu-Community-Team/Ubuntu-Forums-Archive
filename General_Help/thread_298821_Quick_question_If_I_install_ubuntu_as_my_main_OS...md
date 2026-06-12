---
title: "Quick question: If I install ubuntu as my main OS..."
date: 2006-11-13
forum: General Help
---

### Post by jakethesnake on 2006-11-13
If I install ubuntu as my main OS and delete windows from my system entirely will I still have the GRUB loader on my system? Just curious?

---

### Post by taurus on 2006-11-13
Yes, you need a bootloader to boot Linux so you still have to install either GRUB or LILO...

---

### Post by strabes on 2006-11-13
yeah just boot up from the live cd and delete the windows partition and mess with the partitions however you like. ubuntu installs grub automatically. if you want to dual boot then you should install windows first because it likes to be installed first for some reason.

---

### Post by jakethesnake on 2006-11-13
I'm just curious. I have read everything under the sun on how to remove the GRUB loader. But my windows recovery CD automatically deletes all my drives/partitions but this still leaves me with the GRUB loader.

---

### Post by koenn on 2006-11-13
> windows recovery CD automatically deletes all my drives/partitions
funny that a *recovery* CD should do that :-)

but seriously, 
GRUB is partially in MBR (master boot record, not really a partition), partially on whatever partition /boot is at. 
Windows can't see those partitions - that's probably whay you can't "delete" grub with a windows recovery CD. 

If you (re-)install Windows, it will overwrite the MBR and thus remove GRUB - that's also the reason why Windows has to be installed before you install Linux, or rather : GRUB - re post #3

But as you want Ubuntu as your main OS, there's no reason to get rid of GUB. You need it.

---

### Post by jakethesnake on 2006-11-14
I have been having trouble with Ubuntu, but have since ironed out all the problems and so far ubuntu has been running great!

But I have it on multiple PCs and only need it on one. 

Once I re-install windows I'm still left with the GRUB loader, and there my PC stops because GRUB is looking for I suspect a version of linux or ubuntu?

---

### Post by Bretls on 2006-11-14
Assuming you are using Windows XP, boot up recovery console with your windows cd, then run fixmbr from the command promt. That will get rid of grub.

At the "Welcome to Setup" screen, press F10 or press 'R" to repair.

---

### Post by jakethesnake on 2006-11-18
I don't even have a welcome screen once my toshiba recovery disk is in the drive and the system is rebooted. I go directly to a screen that begins to remove/delete all my old partitions and install a new windows partition in it's space.  ?

---

### Post by Bretls on 2006-11-19
You should check out Toshiba's website or contact them to find out how to get into the recovery console from there disk. I have never owned a Toshiba so I can't help you anymore than that. But if you can get into the console those commands will fix your MBR. Sorry I couldn't help you more than that.

---

