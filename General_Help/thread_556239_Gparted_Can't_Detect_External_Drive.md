---
title: "Gparted Can't Detect External Drive"
date: 2007-09-21
forum: General Help
---

### Post by coarse.sand on 2007-09-21
Hello all,

I've recently started at a local college and needed to dual boot Windows on my notebook. That went without a problem, but I have an external drive that we're meant to use to transfer larger files back and forth. Since FAT32, which the drive comes formatted in, transfers slowly in my experience, and has a silly file size limit ( I just love moving DVD and CD images around in my spare time ;) ), I'm trying to partition it into ext3 with a 10gb FAT32 partition on the end to keep the Windows ext3 driver setup in, and whatever ancillary files I can think of.

I've been using Gparted to set up my notebook drive today after I got tired of using ntfs-3g on Ubuntu and switched my main data partition to ext3, but after unmounting the external drive to start patitioning it, Gparted goes into its detection mode and never stops refreshing the device listing. If someone could instruct me in forming the partition with the terminal, or better yet fixing Gparted so I don't have to start messing with cylinders, it'd be most appreciated.

---

### Post by dcstar on 2007-09-21
> **coarse.sand said:**
> 
......
I've been using Gparted to set up my notebook drive today after I got tired of using ntfs-3g on Ubuntu and switched my main data partition to ext3, but after unmounting the external drive to start patitioning it, Gparted goes into its detection mode and never stops refreshing the device listing. If someone could instruct me in forming the partition with the terminal, or better yet fixing Gparted so I don't have to start messing with cylinders, it'd be most appreciated.

There are other tools you can use in a terminal, like cfdisk, or do:

```
man -k ext3
```
to get a list of the EXT2/3 filesystem tools available on your system.

---

