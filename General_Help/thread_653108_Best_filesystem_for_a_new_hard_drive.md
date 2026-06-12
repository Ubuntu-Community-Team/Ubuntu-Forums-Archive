---
title: "Best filesystem for a new hard drive?"
date: 2007-12-29
forum: General Help
---

### Post by teich on 2007-12-29
Hi all,

I've got a new external hard drive and was wondering about the relative pros and cons of the different filesystems I might format it as.  Any comments are appreciated.  

Thanks.
teich

---

### Post by TidusBlade on 2007-12-29
I would say if you use Linux alot, then make it ext3, mines ext3 and works flawlessly and transfer speeds are fast, the only con I know of is that it will reserve 5% of the total space availible for system needs, mostly just in case you dont have any space left but want to start up.

---

### Post by logos34 on 2007-12-29
Unless you need access from x64 windows, you can probably eliminate NTFS--there's fs-driver to read/write ext3.  So you're basically left with ext3, reiserfs, reiser4, xfs or jfs.  

Might want to take a look at these benchmarks:
[http://linuxgazette.net/122/TWDT.html#piszcz](http://linuxgazette.net/122/TWDT.html#piszcz)

> File Benchmark I Data
Conclusion

With the second round of filesystem benchmarks, I hope everyone is now satisfied with the benchmarks using the 2.6 kernel. What I gleam from these benchmarks is both EXT2 and EXT3 are now roughly the same speeds in the majority of the tests. It also appears the XFS has improved in the majority of the tests. ReiserFSv3 has slowed in many of the tests with ReiserFSv4 being the slowest in most of the tests. It is important to note that JFS has improved in some of the tests. Personally, I still choose XFS for filesystem performance and scalability.

---

### Post by disturbedite on 2007-12-29
yeah, i'd just stick to ext3 until further notice.

---

### Post by Martin Witte on 2007-12-29
i you have to share with a windows computer you could consider FAT32 - both linux and windows can read and write to this. this system is not very safe so if you have sensitive data i would recommend ext3 (windows doesn't recognize this) or ntfs (windows native, linux can read/write this, but i wouldn't recommend to use this from linux)

---

### Post by Zill on 2007-12-29
I used to use Ext3 until both file system and HDD were trashed a couple of times following power outages.  Then I moved over to ReiserFS on our three PCs and have never had any problems at all, surviving several power outages (without a UPS!).  ReiserFS does not need to run fsck at regular intervals, unlike Ext3, and also has no Lost and Found directory to worry about :-)

---

### Post by logos34 on 2007-12-29
> **Zill said:**
> I used to use Ext3 until both file system and HDD were trashed a couple of times following power outages.  Then I moved over to ReiserFS on our three PCs and have never had any problems at all, surviving several power outages (without a UPS!).  ReiserFS does not need to run fsck at regular intervals, unlike Ext3, and also has no Lost and Found directory to worry about :-)

Hmm...I've suffered at least 3 or 4 outages (no ups on linux workstation either) and ext3 hardly missed a beat...fsck only ran half the  time afterwards.   I'm amazed at it's resiliency.  That's journaling for you.  Or maybe I've just been lucky.

---

### Post by jeffus_il on 2007-12-29
Reiserfs is stable and fast, Never had a problem with it, survives the reset button without blinking. Am givng XFS a bash because I read that it may be a better performer than Reiserfs.

---

### Post by teich on 2007-12-31
Alright, thanks for the comments everyone.

---

### Post by logos34 on 2007-12-31
> **jeffus_il said:**
> Am givng XFS a bash because I read that it may be a better performer than Reiserfs.

One thing about XFS though: grub won't work on it, so you have to create a separate ext3 /boot partition.

---

### Post by Tekno_Cowboy on 2007-12-31
I'm a tinkerer, and I make my system so unstable that I have to use the reset button regularly. I also have an old house with undersize fuses for what I need to do, so the power to my computer goes out frequently. I had many problems with this with NTFS and ext2, but no problems at all with ext3. To the person who had problems wit the ext3 fs, are you sure you weren't using ext2? With ext2 I don't dare hit reset, or I lose tons of data.

---

