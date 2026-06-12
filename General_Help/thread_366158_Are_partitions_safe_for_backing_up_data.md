---
title: "Are partitions safe for backing up data?"
date: 2007-02-20
forum: General Help
---

### Post by billdotson on 2007-02-20
I have Ubuntu Edgy installed on my external HDD w/ about 25GB of ext3, 256MB of swap a 30GB FAT32, and a 249GB NTFS. When I tried to install Edgy I wanted to have all the stuff of my external drive where I could use it on Windows or Ubuntu so after the swap I made an extended partition of about 7 or 8 30GB FAT32 partitions and then a primary 25GB NTFS partition right after that. It would never work with the extended partitions so I just resorted to the partitions I have now.

Does anyone know how to make the extended partitions work? Also if I decide just to keep the drive the way I have it is it safe to keep backup files for Windows on the NTFS partition?

For some reason I am always cautious and I doubt the reliability of a partitioned HDD. Is there any reasoning behind this, is backing up data on a partition on a partioned HDD just as secure and reliable as an unpartitioned one?

Thanks

---

### Post by chggr on 2007-02-20
> **billdotson said:**
> 
For some reason I am always cautious and I doubt the reliability of a partitioned HDD. 


A partitioned HDD is more reliable than an unpartitioned one.
If you have a partitioned HDD and something happens to it (file corruption, destroyed tracks etc), this affects only the partition where the failure happened. You can still use the other partitions.
On the other hand, if your HDD is not partitioned and something happens to it, all data on the drive will be gone.

---

