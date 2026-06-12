---
title: "How do I make my partitioned SD card usable again?"
date: 2016-08-26
forum: General Help
---

### Post by Bobby_James on 2016-08-26
I have a 16GB SD card. Currently, it has three partitions (see attachment) two of which are unallocated. 

Is there a way to turn the three partitions into one partition. For example, can I format the card (I don't care about what's on it) to get one formatted partition then select my preferred file system (e.g. ext4)?

I simply could not see how to achieve this in Gparted. Happy to try with a different tool e.g. fdisk. 

Thanks for any advice and suggestions.

---

### Post by ajgreeny on 2016-08-26
You might be able to right click on the sdc2 and choose **Unmount** then simply extend the partition at both ends to fill the disk.  Gparted can not work on partitions that are mounted; unmounting it may be all that is needed.

If tghat will not work for some reason, in gparted go to **Device ->Create new partition table** which will make unallocated space of the whole disk, and then format that space to fat32 or whatever filesystem you want.

---

### Post by Jimysbil on 2016-08-26
1) Open Gparted (as root)
2) Unmount every mounted partition on the device you want to make changes.(It's better to do it before you open gparted if you don't want to wait)
3) create new partition table (msdos)
4) Create a new (probably fat32) partition to occupy the hole disk and you are done.

If you have data in some partition and you don't want to lose them you can delete the partition you don't want and resize the partition with your data to occupy the hole disk.

---

### Post by &amp;KyT$0P# on 2016-08-26
> **Jimysbil said:**
> 3) create new partition table (msdos)
If you want only one partition and want to use as much space on your SD card as possible, use **loop** partition table type

---

### Post by Bucky Ball on 2016-08-26
> **Jimysbil said:**
> 
4) Create a new (probably fat32) partition to occupy the hole disk ...

Doesn't matter. Format it to whatever you need, FAT, NTFS, EXT, whatever. :)

FAT's old, has limitations with file size, better to use NTFS if sharing with Windows or EXT if using with Linux only.

---

### Post by T2uiYKb7 on 2016-08-27
It'd doesn't make sense for a normal user to use anything other than FAT16 or FAT32 on an SD card because chances are they'll want to use it in a camera, go pro etc. at some stage and those devices definitely wont be able to read EXT3, EXT4.

---

### Post by Bucky Ball on 2016-08-27
Please take note. I said

> **Bucky Ball said:**
> Doesn't matter. Format it to whatever _you need_ ... :)

If that's FAT, great. Nothing silly about it if that's not what you need/want. 

Back to partitioning the SD. ;)

---

### Post by Bobby_James on 2016-08-27
Thank you all - I was able to resolve the issue by unmounting then extending the partition. I now have a 16GB FAT32 partition.

---

