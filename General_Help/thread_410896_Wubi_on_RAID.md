---
title: "Wubi on RAID"
date: 2007-04-16
forum: General Help
---

### Post by LoMinang on 2007-04-16
Hey guys,
I just found out about Wubi through a friend and figured it was my chance to try out Ubuntu seeing as I really don't want to mess with partitions and I'd like to keep my files too.  Short story is: I installed beta v3 and everything works fine until I reboot and choose Ubuntu.  Then, when the screen it black with grey text, it says that "Buffer I/O error on device sdal logical block 156288256" It goes through from 256-259 and also has an error for 156288320.  I did a google search on this and it seems like the problem is that my harddrives are RAIDed.

A friend built my computer and the way he explained it, he RAIDed the two 80GB harddrives so that they appear to the computer to be one 160GB harddrive.  Elsewhere on the 'net I found that if Wubi installed Ubuntu in fragments onto different harddrives that could cause the error, so I downloaded PerfectDisk and did a single-file defrag on each of the image files.  root.img wouldn't go below two fragments though.

So whenever I start up my computer, it says that it's RAIDed through FastBuild (or something) and that it has a 0+2 Stripe RAID. In another post, someone said that only RAID 0 is supported right now, but they're working on RAID 1. Does that even apply to me? I know basically nothing about hardware, but I can try to find more details if needed.

Basically: I think the problem's with my RAIDed drives, but I'm not sure how to fix it. Any advice would be appreciated.

Thanks a lot!
-L

---

### Post by LoMinang on 2007-04-16
Just thought I'd add a little more info on my computer, in case it's pertinent:
I have an ASUS K8V SE Deluxe motherboard
The RAID screen on startup says that it's with FastTrak 378 and that it's a 2+0 Stripe RAID
AMD Athelon 64-bit Processor 3200+ 2Ghz
1Gb RAM
When I look in Device Manager it says my harddrive is "Promise 2+0 Stripe/RAID0 SCSI Disk Device"

So... yeah. Any help would be appreciated.

---

### Post by GabbaGandalf on 2007-04-19
hi.

can i use wubi on this system:

bootdisk is a raid0 with 2 80gb sata drives (windows xp) 
primary master 100 gb ide drive for ubuntu.

is it possible to use this configuration and leave the windows boot manager on raid0?

thank you in advance

---

### Post by ago on 2007-04-20
New installer will have raid0 support, I cannot test it though since I have no raid0. It might be the case that additional drivers are required.

---

### Post by Spegelius on 2007-04-20
> **ago said:**
> New installer will have raid0 support, I cannot test it though since I have no raid0. It might be the case that additional drivers are required.

Is the RAID support dmraid? Or just different driver modules in the kernel? I do also have a RAID0 set and my controller is ULi M5288, which is not supported by dmraid. Drivers for M5288 exist, but they expect a specific Linux distro and Ubuntu isn't one of them.

My RAID set isn't the drive I boot from, so i can use Wubi as it is installed on a non-raid disk. But i cannot get to files on my RAID 0 set. I was thinking about compiling kernel from kernel.org sources and see if i could get the M5288 raid drivers installed somehow. Other solution might be to scrap the M5288 RAID and go for Windows sofware RAID, on dynamic disks. Does Wubi support Windows dynamic disks? There seems to be at least some solutions for getting dynamic disks to work in Linux.

---

### Post by ago on 2007-04-20
> **Spegelius said:**
> Drivers for M5288 exist, but they expect a specific Linux distro and Ubuntu isn't one of them.
We cannot support anything that is not supported by ubuntu

---

### Post by GabbaGandalf on 2007-04-20
i forget to mention that my raid is a sata fake raid (sil 3112).
this fakeraid is for my windows partition and i want to use the windows bootmanager to boot from my ide drive (no raid, just one drive).

---

### Post by Dark Legacy on 2007-04-21
> **ago said:**
> New installer will have raid0 support, I cannot test it though since I have no raid0. It might be the case that additional drivers are required.

I'm willing to test your latest build with RAID-0 and report any and all errors if you'd like.

I would give you root access to my box, but I'm afraid that it can't maintain an internet connection while booting up. :KS 

As for **what** Raid0 is: [http://en.wikipedia.org/wiki/RAID0#RAID_0](http://en.wikipedia.org/wiki/RAID0#RAID_0)

Sincerely,
Dark

---

