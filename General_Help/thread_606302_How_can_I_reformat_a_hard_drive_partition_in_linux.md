---
title: "How can I reformat a hard drive partition in linux"
date: 2007-11-07
forum: General Help
---

### Post by yinglcs2 on 2007-11-07
Hi,  

How can I reformat  a hard disk partition ? I want to reformat from ext2 and fat32.

And what is the file system which can be seen in both linux and windows?


I have tried to install and  use gparted  in ubuntu 7.10, but I get a core dump:

# gparted
======================
libparted : 1.7.1
======================
Segmentation fault (core dumped)

---

### Post by mpierce on 2007-11-07
Use qtparted and the simple gui to do it.
1) Check the "partition system id" first. Do as root-user, i.e. sudo
# fdisk -l

You should see 83 in the ID-field for the partition in question.
83 means "Linux" type of partition.

Use fdisk /dev/XXX to change the ID. Use commands: t, l , w and q, e.g.
# fdisk /dev/sdb2

2) Format the partition.
Formatting = create a filesystem on the disk/partition. Do as root-user
# mkfs[PRESS tab-key]
....
mkfs.cramfs mkfs.jfs mkfs.reiser4 mkfs.xfs
mkfs.ext2 mkfs.minix mkfs.reiserfs
....

Mkfs.ext2 - Do
# mkfs.ext2 /dev/XXXX

3) Check it
# fdisk -l

Hope this helps...

---

### Post by yinglcs2 on 2007-11-07
thanks. I tried your qtparted. But when I start  it, it just hangs there.

Any tool that I can use to partition my hard drive?

I have 100 G of an unallocated space in an existing Hard drive (capacity is 250 G).  
I just want to allocate 50 G out of this 100 G free space while keep the 150 G un-touched.

What is the easiest way to do that in Ubuntu?

---

### Post by kshane on 2007-11-08
> **yinglcs2 said:**
> thanks. I tried your qtparted. But when I start  it, it just hangs there.

Any tool that I can use to partition my hard drive?

I have 100 G of an unallocated space in an existing Hard drive (capacity is 250 G).  
I just want to allocate 50 G out of this 100 G free space while keep the 150 G un-touched.

What is the easiest way to do that in Ubuntu?

GParted has a CD you can boot to and it will do anything you need.  It boots to it's own OS so there's no screwing around with root or anything.  Very easy.  It does NTFS and other formats, too.

Kevin

---

