---
title: "OS X USB Drive not mounting"
date: 2008-01-27
forum: General Help
---

### Post by indeago on 2008-01-27
hello i just installed Ubuntu, and have all the updates completed... 

After all was done, I attempted to plug in my external USB hard disk which i previously used on my old OS X system. I believe it's formatted as NTFS or whatever is OS X's default file system... (don't remember exactly)

However, ubuntu doesn't mount the drive.

I tried "sudo fdisk -l"  and the drive is showing but it's displayed as having an invalid partition table. (although the drive is healthy with data)

I installed ubuntu with "ex3" file system

bellow is output of "sudo fdisk -l"

My internal drive is the 320 GB, 
the problem is with the external USB drive /dev/sdf 40GB

any help is appreciated, :)



Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcab10bee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2310    18555043+  83  Linux
/dev/sda2            2311        2432      979965   82  Linux swap / Solaris
/dev/sda3            2433       20668   146480670   83  Linux
/dev/sda4           20669       38913   146552962+  83  Linux

Disk /dev/sdf: 40.0 GB, 40007761920 bytes
64 heads, 32 sectors/track, 38154 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Disk identifier: 0x9cf26b0a

Disk /dev/sdf doesn't contain a valid partition table

---

### Post by ghost_ryder35 on 2008-01-27
HFS+ is the filesystem used on OS X, NTFS is Windows NT 4.0 and later.  YOu should be able to mount HFS+ out of the box with Ubuntu but in order to write to it you need to check out this web page [http://ubuntuforums.org/showthread.php?t=92141]("http://ubuntuforums.org/showthread.php?t=92141"), if it is NTFS you should do
sudo apt-get update
go to add/remove programs and search for "NTFS"
there is a program that will allow the read write of NTFS filesystems there.  
Hope this helped.

---

### Post by indeago on 2008-01-27
I figured it would mount out of the box in ubuntu considering the drive was formatted and used on my old mac OS X, but no it doesn't mount... 

i tried the NTFS configuration tool and that didn't help either, still won't mount.

I can't even view the disk drive... let alone write or read the data

I do remember using a program in windows which allowed me to mount the drive and have read access to the drive...  ( could this have caused some kind of conflict? ) 

is there anyway to manually mount the drive? 

or is possible to manually copy out data from an unmounted disk drive? 

When i installed ubuntu I had created two extra partitions. At one point i had problems writing to those mounted folders outside of root ( I resolved this issue ).

My plan was to copy the contents of my external drive to one of the partitions in my root system folder... 

But for some strange reason Ubuntu won't mount my external drive...

---

### Post by ghost_ryder35 on 2008-01-27
1. unplug all other USB devices and try to mount the drive

If #1 does not work then proceed

2. Refer to this [webpage]("http://www.linuxquestions.org/questions/ubuntu-63/manual-mount-external-usb-hard-drive-in-ubuntu-519463/") to manually mount a drive in Ubuntu

3. Good luck

---

