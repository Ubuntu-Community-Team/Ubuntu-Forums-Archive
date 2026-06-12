---
title: "Superblock / RAID error"
date: 2007-11-26
forum: General Help
---

### Post by dr.baltar on 2007-11-26
Hi,

I'm getting superblock errors on one of the drives in my RAID 5 array.
There are 4 drives in the SATA array
/dev/sda 
/dev/sdb 
/dev/sdc 
/dev/sdd 

hda (not on the array  ( contains boot raid 1 paritions)
hdc (not on the array   ( containts boot  raid 1 partitions  )

So I tried to "heal" sdb (the affected drive) with e2fsck -b 8193 /dev/sdb  and I even tried the other locations .  After I did this it still gave me superblock errors after I tried to reassemble the arrary.  I also tried a couple of other commands as well.

the result of the mdadm assemble is :
ubuntu@ubuntu:~$ sudo mdadm --assemble /dev/sda /dev/sdb /dev/sdc /dev/sdd 
mdadm: no recogniseable superblock on /dev/sdb
mdadm: /dev/sdb has no superblock - assembly aborted


I also have hda and hdc (raid1) which may have errors but I can mount them.  The system does not boot.   

I have formatted (fdisk) /dev/sdb hoping to create a superblock of some sort so that I can re-assemble the array but I still get "no superblock" error?  Why is this if I create a filesystem on the drive?

I am still a fair bit of a newb so bare with me :)

thanks!

---

### Post by dr.baltar on 2007-12-02
I've also tried to floor /dev/sdb with   mkfs.ext3 /dev/sdb/    (something to that effect)  hoping that it would write a new filesys / superblock and yet mdadm still reports that there is no superblock on that drive.    Should I yank SDB and format it somewhere else?  Could the drive be bad?  Should I replace it?  I'm I trying to assemble the array incorrectly?

---

### Post by bingoUV on 2007-12-02
mkfs.ext3 has an option(-c) to check the drive for bad sectors before creating filesystem. Use that.

---

### Post by dr.baltar on 2007-12-02
bingoUV:  thanks very much for the reply,

I tried that option and there were no bad blocks.   

What's odd is that gparted is now saying that my first sata disk 
/dev/sda  is unallocated 512.0B ? :(   .  I'm totally confused as to what is going on.
I think this happens intermittently.   If sda and sdb are gone,  I guess I'm hooped.

Here's the results of fdisk -l:
----------------------------
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00009410

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30401   244196001   fd  Linux raid autodetect

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001b6d2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       30401   244196001   fd  Linux raid autodetect
----------------------



is there any way to totally zero out sdb?   what would cause sdb to persistently 
have bad superblocks (according to mdadm) even after putting new filesystems on
it?

---

### Post by dr.baltar on 2007-12-02
I'm also doing all of this from a 7.10 live cd.

gparted seems to crash quite a bit and it it showing
another device called md127 with a size of 0 bytes.

thank you again.

---

