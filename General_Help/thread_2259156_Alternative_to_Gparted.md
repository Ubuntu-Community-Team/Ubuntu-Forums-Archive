---
title: "Alternative to Gparted"
date: 2015-01-02
forum: General Help
---

### Post by scoutdubna on 2015-01-02
I'm trying to resize an sda1 partition to its maximum to use all that is available on a 3tb disc.  

The sda2 and sda5 are in the way of using 656 Gb unallocated space.

I don't seem able using Gparted to move the sda2 and sda5 to the end of the available space.  I have managed to move it by 1.4Tb so far.

Is there a limit on the size that Gparted will handle and if so is there an alternative.

You can see the display on Gparted here.  (when moving I have turned off SWAP)  [http://dubna.co.uk/download/gparted.jpg](http://dubna.co.uk/download/gparted.jpg)

Hope someone can help.

Thanks

CHRIS

---

### Post by Dennis N on 2015-01-02
I think I would unmount sda5 and sda2, and then delete both of these partitions (there is no data there). Then you would have only unallocated space after sda1, allowing you easily resize sda1. Then recreate the others in the remaining unallocated space with gparted.

Also, If I only planned to have swap in addition to sda1, I would simply use a primary partition for swap instead of logical. You don't need both sda2 and sda5.

---

### Post by yancek on 2015-01-02
The problem is not understanding how partitioning works rather than a problem with the GParted software.  The suggestion by Dennis N above should work and might be the simplest but we don't know what your intentions are.  You have only used 2 primary partitions and so if you are using the standard MBR system, you can create 2 additional primary partitions in the unallocated space at the end of the drive if you are just looking to have the space usable.  Your system partition is almost 2TB which is more than enough.  

Another option is to just delete the swap partition and then use GParted to resize (extend) sda2 to the end of the drive and create as many logical parittions as you want.

---

### Post by Dennis N on 2015-01-03
> You have only used 2 primary partitions and so if you are using the standard MBR system, you can create 2 additional primary partitions in the unallocated space at the end of the drive if you are just looking to have the space usable. 

This was my analysis: To start, he has 1 primary partition, sda1. sda2 is indicated as an extended partition, sda5 is logical. He want to maximize sda1 to use "all that is available on a 3 TB disk", so if we take him for his word, he can indeed use it all for sda1 except for a required swap by doing as suggested.

---

### Post by oldfred on 2015-01-03
But the maximum for MBR partitioned drives is 2.2TB or 2TiB.
You have to use gpt partitioning for all drives over 2TiB.

       MBR tech details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)


 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

You may be able to convert, but be sure to have good backups.

 Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)

---

### Post by Dennis N on 2015-01-03
> But the maximum for MBR partitioned drives is 2.2TB or 2TiB.
You have to use gpt partitioning for all drives over 2TiB.

Oops! I knew that too. Should have noticed.

---

