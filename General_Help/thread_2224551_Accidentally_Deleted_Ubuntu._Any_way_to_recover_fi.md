---
title: "Accidentally Deleted Ubuntu. Any way to recover files?"
date: 2014-05-16
forum: General Help
---

### Post by tomizzo11 on 2014-05-16
Being the beginner I am, it appears as if I accidentally deleted my ubuntu install when I was attempting to reinstall windows. I thought I had selected to reinstall windows on the partition I seemed to have deleted both my old windows and ubuntu installs. The opening page that used to ask me to select between ubuntu and windows doesn't appear anymore and just starts up windows.

So my question is, would there be any way to recover some of the lost music files I had in ubuntu? I know windows collects all of the old files from the previous windows install and places it into a windows.old folder, so I'm curious if those ubuntu files would be placed somewhere.

I highly doubt it but I thought I might as well ask. So even though I may have potentially deleted all of my files that I had in ubuntu, atleast I learned something!

---

### Post by slickymaster on 2014-05-16
[PhotoRec]("http://www.cgsecurity.org/wiki/PhotoRec") is a file data recovery software designed to recover lost files including video, documents and archives from hard disks, CD-ROMs, and lost pictures (thus the Photo Recovery name) from digital camera memory. It ignores the file system and goes after the underlying data, so it will still work even if your media's file system has been severely damaged or reformatted.

---

### Post by coldcritter64 on 2014-05-16
> **tomizzo11 said:**
> ... _*when I was attempting to reinstall windows.*_ I thought I had selected to reinstall windows on the partition I seemed to have deleted both my old windows and ubuntu installs. The opening page that used to ask me to select between ubuntu and windows doesn't appear anymore and just starts up windows....

Installing Windows **second** will often trash an existing boot record. 

Boot to a live cd or usb of Ubuntu, you will be able to restore grub to the boot records from there; IF you haven't written Windows over Ubuntu, Ubuntu will still be on the drive just waiting for you to reinstall the grub boot loader. When grub is re-installed you then can get access to either windows or the original Ubuntu install (IF not overwritten)

From the live cd issue the terminal command
```
sudo fdisk -l
```that is a lower case "L" in the command to check your hard drive partitioning. Post results back here in [noparse]```

```[/noparse] tags for readability. Using the # symbol in an advanced editor gives the code tags.

---

### Post by steeldriver on 2014-05-16
*n/m - preceding post covers it*

---

### Post by tomizzo11 on 2014-05-16
This is what I got when I typed "sudo fdisk -l"

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe0c5913d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    45062324    22531131   1c  Hidden W95 FAT32 (LBA)
/dev/sda2   *    45062328   792451119   373694396    7  HPFS/NTFS/exFAT
/dev/sda3       792453120   874371071    40958976   82  Linux swap / Solaris
/dev/sda4       874373118   976771071    51198977    5  Extended
/dev/sda5       874373120   972027903    48827392   83  Linux
/dev/sda6       972029952   976771071     2370560   82  Linux swap / Solaris


```

---

### Post by coldcritter64 on 2014-05-17
It appears you have a Ubuntu or Linux install on /dev/sda5. If you can see the file system and files/folders from a live cd you should be able to easily fix the install and boot into either windows or linux.

Some information to help you do so from askubuntu: 
[http://askubuntu.com/questions/88384/how-can-i-repair-grub-how-to-get-ubuntu-back-after-installing-windows](http://askubuntu.com/questions/88384/how-can-i-repair-grub-how-to-get-ubuntu-back-after-installing-windows)

You can either use the live cd and terminal or a couple of answers mention the "boot repair" application from the live cd. Personally I've always used the cd and terminal method to reinstall grub. I haven't tried out "boot repair" from the live cd like that link mentions. Good luck.

Note where the link mentions
> *make sure you use the correct partition number for your system!*Appears to be /dev/sda5 you need to chroot into for those instructions to work. You seem to have 2 linux swap partitions for some reason however /dev/sda5 is the only normal Linux partition there.

You **will** need to do the "reinstall grub" step at step 7 as well, windows has well and truly trashed the bootcode by the looks of that. 

Ensure you install the grub bootloader to "/dev/sda" in step 7; that is, to the entire device "sda" and NOT a partition (a partition will have a number following the "a" in "sda", eg "sda5" ... **don't** install it to "sda5" whatever you do.)

---

### Post by HermanAB on 2014-05-17
Your Ubuntu system is probably fine, because Windows doesn't understand Linux partitions and therefore will not usually write to it.  What is more likely, is that Windows messed up the boot records.

---

