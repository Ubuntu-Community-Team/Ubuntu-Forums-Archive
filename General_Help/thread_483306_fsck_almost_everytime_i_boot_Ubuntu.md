---
title: "fsck almost everytime i boot Ubuntu"
date: 2007-06-24
forum: General Help
---

### Post by Can0n on 2007-06-24
The fsck-thing that comes up when Ubuntu boot comes up almost everytime I boot Ubuntu. I use double-boot to play on Windows. The messages I get is these:

[http://pici.se/pictures/lxdUODQkL.jpg](http://pici.se/pictures/lxdUODQkL.jpg)
[http://pici.se/pictures/SbtPdHyLj.jpg](http://pici.se/pictures/SbtPdHyLj.jpg)
[http://pici.se/pictures/tiGGZAohg.jpg](http://pici.se/pictures/tiGGZAohg.jpg)

It's almost everytime on that disk (it's one large 250Gb partition).
It may be that I use this disk in windows also, it's ext3, so I downloaded a program thats called "Ext2IFS_1_10b.exe" so that windows recognize the disk even when it's ext3. Anyway, this program, or windows, removes the drivers or something so when I try to access the harddrive it says that it's not formatted and asks if I want to do it. When it does this I run the program and tries to fix it but it doesn't work, I have to reboot the computer to make it work. Maybe this is why fsck want's to check the disk all the time?

Hope you understand my question =)

---

### Post by ss0007 on 2007-06-25
could be a compatibility issue with the WIndows program.However, if u want to 
disable the fsck checking u can edit the fstab file.
Try this in Terminal,
```
1. sudo gedit /etc/fstab
```

2. In the Sixth column (last column usually) add 0 to the drive which you want to be mounted 
without checking.
e.g To disable checking on sdb5, 
```
/dev/sdb5   /media/sdb5   vfat    iocharset=utf8,umask=000  0    **0**

```
3. Save ,exit and reboot.

let me know ur opinion.

---

### Post by max_lan on 2007-06-25
Unix format hard disks have a flag clean/dirty. If fsck finds the flag as dirty it wil fsck it.

I don't suggest you disable fsck, it does it for a reason. Basically the previous access to the disk has made some changes and hasn't neccessarily written all of them to the disk. If you don't fsck it, you will loose files/directories.
I suggest you create a small partition and get your windows driver working reliably on it, then use it on your real partition. Maybe try reformatting as per my next suggestion :

I notice that the windows program is called ext2ifs... not ext3ifs... Maybe it's trying to access it as an ext2 not an ext3 format disk. In which case, reformat (under linux) to ext2.

Max

---

### Post by Can0n on 2007-06-25
I have been recommended from another guy, and from other threads, to not disable fsck just like max_lan says so I will have it enabled. Thanks anyway ss0007 =)

About getting ext3ifs is kinda hard, it doesn't exists. But I found this on their website:

>  The Ext3 file system is the Ext2 file system which has been extended by journaling. Ext3 is backward-compatible to Ext2 - an Ext3 volume can be mounted and used as an Ext2 volume. Just as older Linux Kernels which do not know the Ext3 file system can mount Ext3 volumes (as Ext2 volumes), the Ext2 file system driver ext2fs.sys for Windows incorporated in this software package can do it without any problems, too. Of course you do not take advantage of the journaling of the Ext3 file system if you mount it as an Ext2 file system.

If you mount an Ext3 file system as an Ext2 file system and the file system is not cleanly dismounted, (e.g. due to a system crash), you have to run the e2fsck tool. (Linux does it automatically.) Running e2fsck can take several hours on large volumes. You do not benefit from journaling the Ext3 file system, because you have to run e2fsck.

I think i'm gonno try and find another driver that supports ext3.

---

