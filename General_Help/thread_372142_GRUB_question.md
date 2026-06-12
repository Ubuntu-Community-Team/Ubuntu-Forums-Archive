---
title: "GRUB question"
date: 2007-02-27
forum: General Help
---

### Post by Ubuntu Man on 2007-02-27
Hey guys, I've used Ubuntu since the Hoary Hedgehog days, then decided to give Debian a try a little while ago, but decided it wasn't for me. I pulled a little oopsy on the Debian install, installing GRUB on my master boot record (I meant to install it on my external harddrive, where I installed Linux). Now, sometimes when I boot it doesn't detect my external hdd right away so I get an "Error 21" which is because of just that, my hdd wasn't detected.

Anyways, I was wondering if I installed Ubuntu again (which I definitely want to do) and installed GRUB to my external harddrive, would I still have GRUB on my primary hard drive?

---

### Post by Quillz on 2007-02-27
It will probably remain on your primary hard drive until you reformat it, but I'm not entirely sure.

---

### Post by Ubuntu Man on 2007-02-27
> **Quillz said:**
> It will probably remain on your primary hard drive until you reformat it, but I'm not entirely sure.

How would I reformat my primary HDD?

---

### Post by tawniteamo on 2007-02-27
you can't reformat without losing all data. simply use some partitioning software or reinstall

---

### Post by Tag_yer_dead on 2007-02-27
you can remove grub how ever it is fairly complex, and you need your windows boot cd's

sorry im goin 2 have to make a double post i cant find the right links, so ill get them in 5 minutes.

---

### Post by Tag_yer_dead on 2007-02-27
once again sorry for the double post, but these two links should work

[http://support.microsoft.com/kb/307654]("http://support.microsoft.com/kb/307654")
[http://www.michaelstevenstech.com/r_c_cmds.htm]("http://www.michaelstevenstech.com/r_c_cmds.htm")

Good luck, those should work for ya

---

### Post by Ubuntu Man on 2007-02-27
My laptop came with Windows XP preinstalled.  So I don't have a boot disk. 

I'm sure I'll be able to get one somewhere, but is there a way to do it without the boot disk?

---

### Post by tawniteamo on 2007-02-27
if you don't mind wasting a cd, you don't need to install the os, you can find a windows boot cd on basically any P2P site, download, burn, run, pretty simple.

---

### Post by Ubuntu Man on 2007-02-27
> **tawniteamo said:**
> if you don't mind wasting a cd, you don't need to install the os, you can find a windows boot cd on basically any P2P site, download, burn, run, pretty simple.

Thanks man, I'll do that tomorrow.
But just to make sure, to my knowledge the command when I boot from the Windows Boot CD is:
```
fdisk /mbr
```
right?

---

### Post by tawniteamo on 2007-02-27
no, just enter the recovery console. press the number of the requested partition (they will give you options) and type FIXMBR if thats not it, then it is "FIXMBR whatever drive letter:", without quotes. if you have any more questions whilst trying, email me
I just got this from the link posted earlier by tag:

Fixmbr repairs the startup partition's master boot code. The variable device is an optional name that specifies the device that requires a new Master Boot Record. Omit this variable when the target is the startup device.
shouldn't need the drive letter.

---

