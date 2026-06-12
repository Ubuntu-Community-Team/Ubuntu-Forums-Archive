---
title: "Finding CD-ROM name and mounting CD-ROM drive"
date: 2015-03-07
forum: General Help
---

### Post by dora5 on 2015-03-07
I'm using Ubuntu 14.04.   From what I can see maybe I don't actually have to mount the dvd drive, though for certain I have to keep telling VLC the dvd isn't where it thinks it is.      


I guess my first question is when does one actually have to mount the dvd drive?


I have two drives on my computer; a cd-rom drive that reads CDs and does absolutely nothing else.  I did not order nor build this computer.   No clue why...   


I've run different commands and looked in the fstab file.   


The file explorer, what ever it's called, maybe Nautilus, maybe not, it has that file drawer icon and exists as the second button on the launcher, and if you type nautilus in the search thing it comes up and calls itself "Files", identifies one and only one cd/dvd drive by the name of the last DVD that was in it, such as "Anglo Saxon Times".   


The fstab file has no reference whatever to dvd drives, just a conflict or two that took place during installation, which could be part of the problem.


The command to learn what drives were found when the device booted up finds both of them, and doesn't tell me the name of either of them.  The device names are sr0 and sr1, 


 VLC can only find dvds if you tell it to play sr1, which it does not do by default, time after time after time.  Occasionally if you insert a dvd a thing comes up asking what to play it with or whatever, usually nothing at all happens. On the rare occasions that anything at all happens, I got the idea that the computer names the drive CDROM or something close.


I get the idea that the system may be calling them both "cdrom".  In fact they appear to be the same model number of hte same brand, except that they don't have anything resembling the same functionality.   


When I run a command to get more information, I learn that the DVD drive is still sr1, but the other one is now dev/cdrom.


How do I find out what the actual names of the cdrom drives are, and then will fixing fstab straighten out the issue the system seems to be having with finding the drives?

---

