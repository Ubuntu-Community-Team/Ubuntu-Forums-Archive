---
title: "Resizing a reiserfs partition"
date: 2005-10-30
forum: General Help
---

### Post by magnusbb on 2005-10-30
My notebook harddrive is only 60 GB, and it's divided into three partitions. 

1. NTFS, for the Windows XP installation
2. ReiserFS, for the Ubuntu installation
3. FAT32, for sharing files between those two

But as I've become very confident with my Ubuntu installation I want to give it some more space. Using Partition Magic in Windows, I've already scaled down the size of the NTFS partition, and now I want to equally expand the ReiserFS one.

But how do I do this. Can I do it in real-time on Ubuntu, and what methods are most secure - using what applications and so on?

It would be very good to get some assistance here, because I really want to work more on the Ubuntu system. :)

---

### Post by gorsh on 2005-10-30
I have the same situation!!
so I'mwaiting for an answer too....

thanx!

---

### Post by shamrock_uk on 2005-10-30
I've had great success with [QTParted](http://qtparted.sourceforge.net/), a partition magic clone. I always boot off the [System Rescue CD](http://www.sysresccd.org/) and do it from there to be on the safe side, but I guess that you could do it with a running system, providing the drive was unmounted of course. I would say that I've performed a resize operation on about 20 separate occasions with no problems.

---

