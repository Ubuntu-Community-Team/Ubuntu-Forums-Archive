---
title: "MBR Problem? Maybe?"
date: 2007-05-01
forum: General Help
---

### Post by scottpledger on 2007-05-01
I decided that I wanted to give 7.04 a test drive, but I didn't want to remove my entire pre-existing ubuntu installation.  I only have a 30Gb drive, so I decided to re-partition my hard disk.  I used the gparted live cd and successfully resized it and installed 7.04 in the free space that now existed on my hard disk.  I installed it successfully.
After playing with 7.04 for a while, I wanted to go back to my old system.  So, I removed the partition that the new install of 7.04 was on and resized my original partition to fill the gap left from removing the 7.04 partiton.  Now, when I boot, I get the following.
```
GRUB Loading stage1.5.


GRUB loading, please wait...
Error 22
```
I believe that my MBR may be screwed up, but I don't know for sure.

---

### Post by bernied on 2007-05-01
This is not the MBR, that is stage 1, which grub has passed in order to get to 1.5. 1.5 is on the partition that you boot to. Time to check the manual...

---

### Post by wtruong on 2007-05-01
Make sure it's booting the right hard drive, sometimes it's hd1 when it's supposed to be hd0 or vice versa.  Or maybe it's looking at the wrong partition.

---

### Post by bernied on 2007-05-01
From the [manual](http://www.gnu.org/software/grub/manual/grub.html):
```
22 : No such partition
    This error is returned if a partition is requested in the device part of a device- or full file name which isn't on the selected disk. 
```
Are you able to boot a live CD and access your ubuntu partition? 
Can you post your /boot/grub/menu.lst file here?
Can you also post the output to 
```
sudo fdisk -l
```
Also, do you have a mixed IDE/SATA hardware setup? 
How many disks do you have and are they different types?

---

### Post by mac.ryan on 2007-05-01
Your MBR is not "screwed up", but it is still pointing to the version of grub from 7.04 (that you removed). You simply need to tell the MBR to point again to the "oder version" of grub. In order to do so, you can follow a variety of methods, amongst others:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by scottpledger on 2007-05-01
I only have one hd, so if my hd is wrong, then how would i change it?  I've got the 7.04 disk that I can boot from.  Also, i noticed that under /boot/grub/device.map, it shows my hd as being /dev/hda.  I think that that is right, but how can I know for sure.  The LiveCD shows it as /dev/sda.

---

### Post by bernied on 2007-05-01
I apologise, I didn't read your first post properly. mac.ryan is right, you just need to tell the grub mbr to boot to your previous install.

---

### Post by scottpledger on 2007-05-01
> **mac.ryan said:**
> Your MBR is not "screwed up", but it is still pointing to the version of grub from 7.04 (that you removed). You simply need to tell the MBR to point again to the "oder version" of grub. In order to do so, you can follow a variety of methods, amongst others:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)


THANK YOU SOOOOO MUCH!!  This worked flawlessly!  Thanks again!
:)

---

### Post by Turellius on 2007-05-01
> I only have one hd, so if my hd is wrong, then how would i change it?
You have only one hard drive, but you have multiple partitions on that hard drive.
> Also, i noticed that under /boot/grub/device.map, it shows my hd as being /dev/hda
In Linux, your drives are arranged in order like this hda is primary drive hdb is secondary drive. If you notice something to the effect of hda0 hda1 those are both partitions on the primary drive "hda".  Hopefully this will help make a bit more sense out of your situation.  However it sounds like what happened when you installed the other version of Ubuntu, it directed GRUB to load from the new partition.  Now when the MBR tries to load GRUB files and configuration, it can't find it because the partition it is trying to load from was deleted.  Unfortunately, I don't know enough about GRUB and how it works to help you out and I am presently not at a computer with linux installed.  I will check back later today.

---

### Post by Turellius on 2007-05-01
sorry I accidentally posted twice.

---

