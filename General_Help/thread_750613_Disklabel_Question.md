---
title: "Disklabel Question"
date: 2008-04-09
forum: General Help
---

### Post by Graham1 on 2008-04-09
Hi

Is there any way to recover from using the "Set Disklabel" option? By mistake, I used this option (set as msdos) thinking it would rename the partition that I was working on but discovered that the whole disk is now unusable (displaying Unallocated, when viewed in VisParted, Partition Magic, etc). Unfortunately, I have some important data (which I didn't backup) which I moved from the partition that I was working on (see 6) to my Linux partition (see 1). My setup is as follows:-

**Primary**
1. Ubuntu 7.10 (50GB, ext3)
2. openSUSE 10.3 (50GB, ext3)
3. <blank> (50GB, ext3). Previously XP

**Logical / Extended**
4. Boot (100MB, fat32)
5. Linux-Swap (2GB)
6. Data (100GB, ext3). Previously NTFS

Are there any tools that I can use to recover these partitions? (especially the Ubuntu partition which holds the data)

Thanks
Graham

---

### Post by tamoneya on 2008-04-09
i would use the Ultimate Boot CD,[http://www.ultimatebootcd.com/index.html](http://www.ultimatebootcd.com/index.html),  to recover these partitions.  It has two tool which you should test out: Active@ Partition Recovery and Partition Saving.  You may also want to clone the disk first if you have a spare.  That way if you mess up at all during the recovery process you have a backup.

P.S. stay away from the disk wiping tools like DBAN.  Then you really will lose your data.

---

### Post by Graham1 on 2008-04-09
Thanks for your advice tamoneya :) (good idea to clone to another disk).

I've been playing with TestDisk but too scared to use it (recognizes the structure / files ok). I wasn't sure how it would work, whether it would mess up when copying back to the disk and then I'll loose everything. 

I actually have a copy of UBCD 4.11 so I'll give that a try also (after making a clone first).

:)

---

### Post by Graham1 on 2008-04-15
Unfortunately, I couldn't find another 250GB drive for cloning so had to take a chance with TestDisk. Glad I did, as it recovered all partitions (OS's and data) without any problems. Got all my baby photo's back so I'm VERY happy :D. 

:)

---

