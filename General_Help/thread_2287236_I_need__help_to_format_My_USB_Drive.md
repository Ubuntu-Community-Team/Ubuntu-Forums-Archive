---
title: "I need  help to format My USB Drive"
date: 2015-07-17
forum: General Help
---

### Post by Rakesh_vijayan on 2015-07-17
Dear friends 

I am not able to format my pen drive , while use the graphical too to format this messge come up 

> Error synchronizing after formatting with type `ext4': Timed out waiting for object (udisks-error-quark, 0)

After some googleing I use this command 
I don't know what exact is ,It shows some 6.6 gb actually it was 16gb Usb 
> 
rvd@nn1:~$ sudo dd if=/dev/zero of=/dev/sdb
dd: writing to ‘/dev/sdb’: Input/output error
12854593+0 records in
12854592+0 records out
6581551104 bytes (6.6 GB) copied, 1402.62 s, 4.7 MB/s 

and I use fdisk command to delete the partition while I save the  W command it says 

> Command (m for help): w
fdisk: unable to write /dev/sdb: Bad file descriptor



when I list the file sdb it show that the ID  for bsd 5a > 
root@nn1:/home/rvd# fdisk -l /dev/sdb

Disk /dev/sdb: 16.0 GB, 16043212800 bytes
64 heads, 32 sectors/track, 15300 cylinders, total 31334400 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00039095

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32    31334399    15667184   a5  OpenBSD



, and I tried to change the file system type same message as QUOTED comes up 

any Idea to use this one again ? all the help would be appreciate my friends 

Thanks

---

### Post by Bucky Ball on 2015-07-18
Which graphical tool? Install Gparted if you don't already have it installed, launch it, click the dropdown box at the top right and head for your USB dongle. Right click and unmount it. Right click on and delete all partitions. [U][I]Make absolutely sure you are deleting partitions on the USB dongle and not the hard drive prior to deleting partitions.
[/I][/U]
Right click and create an EXT4 partition. Hit the big green 'Apply' button. What happens?

---

### Post by Rakesh_vijayan on 2015-07-18
Hi dear friend 

I  used the utility Disks in ubuntu .I am going to try with the Gparted and I will update you .... let me know the wakeuped  genius guys ,is the procedure that I did was correct to recover the drive ...

---

### Post by Rakesh_vijayan on 2015-07-18
I am able to delete the partition

 [IMG]http://s21.postimg.org/rfvh7achj/Gpart_Delete.png[/IMG]


when I try to create the new partition it say like this 

[IMG]http://s11.postimg.org/72fts3zs3/gparted.png[/IMG]

---

### Post by sudodus on 2015-07-18
> I don't know what exact is ,It shows some 6.6 gb actually it was 16gb Usb 
```

rvd@nn1:~$ sudo dd if=/dev/zero of=/dev/sdb
dd: writing to ‘/dev/sdb’: Input/output error
12854593+0 records in
12854592+0 records out
6581551104 bytes (6.6 GB) copied, 1402.62 s, 4.7 MB/s 
```


This error indicates that there is some bad block (hardware defect) on the pendrive. It might be possible to use it, if you mark the bad sector as bad, but the pendrive might be too bad (near a failure) to be possible to use beyond the bad block. What you can do is try to use ***gparted*** as suggested by Bucky Ball to create a partition table, and after that an ext4 partition. If that is successful, you can use the following command to mark the bad blocks (with a program call badblocks via a program called e2fsck).

```
sudo e2fsck -cf /dev/sdxy
```

where x is the drive letter (maybe b) and y is the partition number (probably 1).

---

### Post by Rakesh_vijayan on 2015-07-18
This the message appear by using the suggestion 
> rroot@nn1:/media# e2fsck -cf /dev/sdd1
e2fsck 1.42.9 (4-Feb-2014)
e2fsck: Read-only file system while trying to open /dev/sdd1
Disk write-protected; use the -n option to do a read-only
check of the device.
root@nn1:/media# 




and also now I am able to create the partition with the fdisk command but I can't mount the partition 
> Disk /dev/sdd: 16.0 GB, 16043212800 bytes
64 heads, 32 sectors/track, 15300 cylinders, total 31334400 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00039095

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            2048    31334399    15666176   83  Linux
root@nn1:/media# 




when I try to make file system It show that readonly message 

> root@nn1:/media# mkfs -t ext4 /dev/sdd1
mke2fs 1.42.9 (4-Feb-2014)
/dev/sdd1: Read-only file system while setting up superblock
root@nn1:/media# 



BY using Gparted I can delete the partition Is there any way to change the readonly mode ...
and let me know the cause of the problem the device became read-only system ....?

---

### Post by sudodus on 2015-07-19
It is strange that you can create the partition, but not a file system in it. Obviously the partition table is not read only. Maybe the pendrive is damaged, but it is worth trying once more.

I suggest that you again to wipe (the first part of) the pendrive with the command

```
sudo dd if=/dev/zero of=/dev/sdx
```

where x is the drive letter. In your first post x was b (the second drive), so /dev/sdb, but ***check carefully*** in order to avoid overwriting important data on other drives. If you want a safer method to wipe the pendrive, try [mkusb](https://help.ubuntu.com/community/mkusb#Wipe_the_first_megabyte_or_the_whole_device).

After that I would use the GUI program ***gparted*** and

1. create a new MSDOS partition table

2. create a partition with an ext4 file system (or another file system if you wish)

If this still fails, I'm afraid that the hardware in the pendrive is failing. Maybe it is gridlocked, or something similar. Read more at this link

[Pendrive lifetime](http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297)

---

