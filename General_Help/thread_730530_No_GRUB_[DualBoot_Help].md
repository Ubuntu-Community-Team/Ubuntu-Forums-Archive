---
title: "No GRUB? [DualBoot Help]"
date: 2008-03-21
forum: General Help
---

### Post by blackbinary on 2008-03-21
Okay, so heres what I've got.

1 80GB SATA HDD. This has a 20GB Partition with Ubuntu 7.10 on it. 
I then made another partition of 50GB for Windows XP. That is now installed on it. 
I have 10GB free still (think some of it may be my swap file, but I cant remember the size of it)

I also have a 320GB SATA HDD, full of all my data in NTSC for both operating systems (the swap may also be on this, again I can't remember). 

Because I installed Ubuntu, and then XP, I can't get into Ubuntu unless I use the CD.

Is there a quick way to get GRUB installed, or is there another bootloader that I can install easy?

---

### Post by nick_h on 2008-03-21
Read the following guide - [How to install Grub from a live Ubuntu cd.](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by teryowen on 2008-03-21
boot of the live CD and in terminal do this:

```

sudo grub
find /boot/grub/stage1

```
this should give you an output lookin like this (hdx,y) where x and y are numbers
x is the hard drive number and y is the parition number (0 being the 1st and 1 being the 2nd and so on)

then continue with (replace x and y with numbers)
```

root (hdx,y)
setup (hdx)
quit

```

in your case i think your X will be 0 (1st harddrive) and the Y will be 0 (1st partition)
but just trust the out put that "find /boot/grub/stage1" gives you and use those numbers.

Also in BIOS make sure that the hard drive with ubuntu has priority in booting before the other hard drive.

---

