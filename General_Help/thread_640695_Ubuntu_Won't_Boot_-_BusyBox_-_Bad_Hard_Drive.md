---
title: "Ubuntu Won't Boot - BusyBox - Bad Hard Drive?"
date: 2007-12-14
forum: General Help
---

### Post by innocenceisdeath on 2007-12-14
Hey,
Ubuntu isn't booting, whenever I turn it on it goes to the splash screen then to busy box a second later. If I hit Alt + F1 then I get this appear on my screen. (Attached image)

I don't appear to be able to mount the hard drive wjhile running a live CD :S
I think it said something about a bad superblock?

Any ideas on anything I can do to retrieve my files, or salvage the hard drive? Or do I need to a buy a new hard drive and reinstall the whole thing?

Thanks, any help will be greatly appreciated!

---

### Post by innocenceisdeath on 2007-12-16
*Bumpeth*

---

### Post by aldenhg on 2007-12-16
Go and download DFT (Drive Fitness Test) 
[http://www.hitachigst.com/hdd/support/download.htm#DFT](http://www.hitachigst.com/hdd/support/download.htm#DFT)
Make a CD of it and boot from it. Run the long test and wait a long, long time. If it ends and you don't have any errors (besides one error at the end - that one is normal) then your hard drive is fine and you can recover your files. Otherwise you might consider picking up a IDE/SATA to USB adapter to plug your hard drive into another computer to recover the files. good luck!

---

### Post by innocenceisdeath on 2007-12-17
Thanks a lot. Seems my hard drive is fine, which is a relief.
I still have no idea what is wrong though. I can boot from a Live CD but I still cannot access the hard drive. =/

---

### Post by innocenceisdeath on 2007-12-22
Bump

---

### Post by spartan777 on 2007-12-24
i have the same exact issue. i updated ubuntu about 3 weeks ago, restart, and get busybox with similar errors before it.

BUMP

i have ubuntu 7.10, 2.6.22-14-generic

---

### Post by innocenceisdeath on 2007-12-24
I just can't think of any reason as to why this has happenned. :S

I hadnt changed any settings or installed any new hardware or software or anything...

Looks like I may have to get another HDD and try to copy the files over and then reinstall Ubuntu if no one else has any ideas. It's really starting to piss me off having to use my old slow XP machine. =[

---

### Post by Marrz on 2008-04-25
I'm running 8.04, installed with the windows utility, and I have the same issues, works fine on install and the first reboot or so then it goes wacky and does this, any new suggestions

BUMP

---

### Post by Typoh on 2008-04-25
> **Marrz said:**
> I'm running 8.04, installed with the windows utility, and I have the same issues, works fine on install and the first reboot or so then it goes wacky and does this, any new suggestions

BUMP

Same exact problem.  Except, to get mine to install, I had to use the IRQPOLL method.

BAMP

---

### Post by innocenceisdeath on 2008-04-26
The solution to my problem was a bad superblock.

Can't guarantee this is your problem though.

This fixed mine :) [http://www.brunolinux.com/04-The_File_System/Damaged_Superblock.html](http://www.brunolinux.com/04-The_File_System/Damaged_Superblock.html)

---

