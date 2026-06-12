---
title: "Partition problem after windows reinstall!"
date: 2006-10-12
forum: General Help
---

### Post by Flavian on 2006-10-12
Hi guys :)
I have the following problem:

Some time ago I reinstalled windows, which I found out was NOT the smartest thing to do. Since I use a hybrid system for some games that do not work in ubuntu and other stuff, I had to.
So here is the deal.
After doing that something weird happened to the partition table:
(hd0,4) changed to (hd0,2) and sda5 to sda3 which was very weird...
Now that I figured out WHAT was wrong (but not WHY it was so) I managed to change my fstab and mtab so that it worked again.
Interestingly enough, when I install a new kernel (since ubuntu writes grub menu.lst anew) I have to change them again in order to be able to boot into linux.

The main problem is that I can not access my partitions through QTparted. It only gives me the following error, if I clikc on the Hard drive:
```
Critical error during ped_disk_new!
```
It recognizes the hard drive and that it is working, but obviously not the partitions :(

What can I do to get it working again?
This is kinda annoying!
I would be glad for any help you can give me.
Flo

---

### Post by h2gofast on 2006-10-12
can you give us the output of 
sudo fdisk -l /dev/sda

sounds like a partition got moved or deleted.

---

### Post by Flavian on 2006-10-13
Sure!

Here is what **sudo fdisk -l /dev/sda** gives me:

> 
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         620     4980118+   7  HPFS/NTFS
/dev/sda2             621        9729    73168042+   f  W95 Ext'd (LBA)
/dev/sda3            8519        9673     9277506   83  Linux
/dev/sda5             621        8518    63440622    b  W95 FAT32
/dev/sda6            9674        9729      449788+  82  Linux swap / Solaris


This is my **FSTAB** before editing it (the original state it was in BEFORE the partition "crash")
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sda7       /media/sda2     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sda6       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0


This is my **FSTAB** NOW that I changed it. Note that I used different mount points ON PURPOSE, because I personally found them more descriptive then the standard ones. The /dev/sdaX section is the most important for you I guess.
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /media/Windows     ntfs    defaults,utf8,umask=007,gid=46 0       1
/dev/sda5       /media/Fat32     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sda6       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0



Thanks for any help in advance!
Flo

---

### Post by Flavian on 2006-10-16
I am still waiting for some help... would be glad if someone could help me :)

Best regards
Flo

---

### Post by h2gofast on 2006-10-20
It sounds like your partition table is borked.  The next question is if the table can be rewritten without affecting the data on each partition.  Once it's rewritten we need to tell grub to reinstall itself on the master boot record.  

I could be wrong but it is the first place I would look.  
For starters back up any data you aren't willing to loose.  Anytime you deal with a drives partitions tables, or formatting new partitions, there is always a slim chance you could lose data.  

before you give up and reinstall anything, backup data and
sudo cfdisk /dev/sda
then use arrow buttons to toggle [write] and answer yes.
sudo grub-install /dev/sda
this one might screw things up pretty well

The bottom line is that it sounds like your system isn't broken, and if it isn't broken don't fix it.  
Secondly when dual-booting, always install windows first, it's easier than reinstalling grub.  

cheers, 
h2.

---

