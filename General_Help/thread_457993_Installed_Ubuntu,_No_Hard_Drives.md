---
title: "Installed Ubuntu, No Hard Drives"
date: 2007-05-29
forum: General Help
---

### Post by roebuck86 on 2007-05-29
Hi, 
I have two hard drives in the computer. My 250GB which contains all my windows XP data and another smaller hard drive dedicated to Ubuntu.

First off im completely new to Ubuntu and Linux altogether. After an easy installation, I began installing programmes such as WINE, and GFX card drivers after restarting my machine to try and get into the windows XP side, I found I wasn't able to. To combat this problem I decided that I would disconnect the Ubuntu hard drive to solely load up the Win XP side. After this failed neither of my hard drives are now recognized and when I place the Ubuntu disc in my machine to install and the Prepare disc space/Prepare partitions doesn't detect any hard drives. 

I've reseted my CMOS to no avail, and now im completely stumped! 

Any one have any suggestions, if you need any more specific info, then please just ask.

Thanks in advance Kristian.

---

### Post by blacksadness on 2007-05-29
it could be a hardware problem, if the disks are ide check the master/slave settings or put both on cable select also check and see if windows install cd can find any disks..

---

### Post by Crafty Kisses on 2007-05-29
> **roebuck86 said:**
> Hi, 
I have two hard drives in the computer. My 250GB which contains all my windows XP data and another smaller hard drive dedicated to Ubuntu.

First off im completely new to Ubuntu and Linux altogether. After an easy installation, I began installing programmes such as WINE, and GFX card drivers after restarting my machine to try and get into the windows XP side, I found I wasn't able to. To combat this problem I decided that I would disconnect the Ubuntu hard drive to solely load up the Win XP side. After this failed neither of my hard drives are now recognized and when I place the Ubuntu disc in my machine to install and the Prepare disc space/Prepare partitions doesn't detect any hard drives. 

I've reseted my CMOS to no avail, and now im completely stumped! 

Any one have any suggestions, if you need any more specific info, then please just ask.

Thanks in advance Kristian.

You could have possibly partitoned wrong, I did this before (had 100GB of data lost) but that's besides the point, I switched to Ubuntu fully and it' s the best thing I've ever done.

I think it's VERY possible you messed up the partition, and you say it doesnt show the partition at all?

---

### Post by smoker on 2007-05-29
you may have inadvertantly formatted your windows partition. download and boot from the 'gparted live-cd' available here:  [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

this should tell you what partitions you have, what format they are, and how much data used in whatever partition. if the drives show in the bios, gparted should find them.

once you have the info about your partitions, you can go from there,

best of luck

---

