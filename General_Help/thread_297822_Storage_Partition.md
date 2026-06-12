---
title: "Storage Partition"
date: 2006-11-11
forum: General Help
---

### Post by napoelon on 2006-11-11
I am running Ubuntu Server 6.10, and I am setting up a web server. I have a spare hdd in the server, and I want to set it up as the storage for all the web files.

Quick n00b question, how would I go by partitioning this via command line, and what kinda partition would i have to make it, to have it so it is readable?

---

### Post by dcstar on 2006-11-11
> **napoelon said:**
> 
........
Quick n00b question, how would I go by partitioning this via command line, and what kinda partition would i have to make it, to have it so it is readable?

Do a "man" on the following (whatever fs you actually want):
```
jfs_mkfs (8)         - create a JFS formatted partition
mke2fs (8)           - create an ext2/ext3 filesystem
mkfs (8)             - build a Linux file system
mkfs.ext2 (8)        - create an ext2/ext3 filesystem
mkfs.ext3 (8)        - create an ext2/ext3 filesystem
mkfs.jfs (8)         - create a JFS formatted partition
mkfs.minix (8)       - make a Linux MINIX filesystem
mkfs.msdos (8)       - create an MS-DOS file system under Linux
mkfs.ntfs (8)        - create an NTFS 1.2 (Windows NT/2000/XP) file system
mkfs.reiser4 (8)     - the program for creating reiser4 filesystem.
mkfs.reiserfs (8)    - The create tool for the Linux ReiserFS filesystem.
mkfs.vfat (8)        - create an MS-DOS file system under Linux
mkfs.xfs (8)         - construct an XFS filesystem
```

---

### Post by napoelon on 2006-11-11
Would it be good to create an ext2/ext3 filesystem for storage? or should i be using a different partition type?

say i want to partition /dev/hda and have that to be a storage partition.. what would i have to type in command line.. is there a wiki i can follow?

---

### Post by iamhugeinjapan on 2006-11-11
If you have an Ubuntu live cd handy, you can boot that up and use GParted from the System - Administration menu.  You can use it to format the drive with whatever filesystem or partitions you want.

You'll most likely have to tell the real Ubuntu /etc/fstab file to mount it though. There's no shortage of instructions on doing that :)

---

