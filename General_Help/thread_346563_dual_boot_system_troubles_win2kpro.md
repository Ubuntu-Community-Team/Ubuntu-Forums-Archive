---
title: "dual boot system troubles win2kpro"
date: 2007-01-25
forum: General Help
---

### Post by itzpapalotl on 2007-01-25
Well. I'm just baffled!
I have no idea what I'm doing, but I pretty well have to do it.
I need to get 16 identical computers to dual boot between Windows 2000 Professional, and Dapper. This sounds elementary enough, but I just can't do it.  The machines are  all early p4 gateway emachines with no real whistles or bells. 256 megs of ram, 60 gig hdd cdrw and a DVDRW drive that I use just for the install.They are in the computer lab, and they all run Windows 2kpro on a fresh install.  They run Just fine under Windows. They also run Dapper just fine if it's the only thing on the drive, but they Just will NOT dual boot. I can not get them to play nice with each-other on the same drive. 
1) I install Windows
2) I partition the drive with the Ubuntu install DVD from the The Official Ubuntu Book (disk checks out just fine).
3) I attempt the install and use the same settings that work for a clean install.
4) I wait, and  about half way through the final part of the installation, where it's copying files to the drive, The screen goes blank except for two white squares. (This is normal on the clean install as well.) The disk keeps working away, and eventually it stops.
5) Whereas during a clean install, eventually the disk gets spit out, and when I restart the machine, Ubuntu is there and working just fine, with win2k on the drive, the disk never spits out. The DVD drive does eventually quit spinning, as does the HDD, but the DVD never ejects.
6) Eventually, a few hours later and once overnight,  I restart the machine.
7) Black screen with "Error loading operating system" in white on the top.
This happens on every machine, every time. 

I assume this has to do with the grub bootloader, but here I am treading in to unfamilliar territory. I do know that Windows 2kpro has a boot loader of its own, could there be a conflict?  I have to get these machines to dual boot. Any help would be appreciated.

---

### Post by dcstar on 2007-01-26
> **itzpapalotl said:**
> 
........
I assume this has to do with the grub bootloader, but here I am treading in to unfamilliar territory. I do know that Windows 2kpro has a boot loader of its own, could there be a conflict?  I have to get these machines to dual boot. Any help would be appreciated.

There is a 6.06 install image available for "low memory installs", I have had this work better on older hardware than the standard install CD, it may be worth downloading it and trying it out on one of your machines.

Sometimes even installing the text only server system and then installing the Ubuntu-desktop package later can get a system going on hardware that falls over during the normal install process.

---

### Post by itzpapalotl on 2007-01-29
Saddly No, but thank you for the advice.
I have determined that it's not a memory issue by slapping 512 megs into the banks. Besides, when I do a clean install there are no problems, there is some conflict with Win2kPro. Like Ubuntu can't write GRUB to the boot sector. This doesn't seem to happen with XPpro

Any takers?

---

