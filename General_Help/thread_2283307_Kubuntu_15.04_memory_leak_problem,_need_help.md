---
title: "Kubuntu 15.04 memory leak problem, need help"
date: 2015-06-20
forum: General Help
---

### Post by zaoka on 2015-06-20
I installed Kubuntu 15.04 (64bit) with BTRFS as root partition (no separate swap space).

I have 4GB of memory. 

Problem: After surfing for a while my memory usage goes on maximum. KSysGuard does not show what is using that much of memory.

The only way to fix it is to restart the system,

I have no idea why this is happening. How can I find out what is using my memory?
Also KSysGuard says my swap usage is zero. Is this because I have only one partition or there is a problem.  By checking swapiness it is set to 60.

Please help me out fix this problem since I spent a lot of time to set everything up on this machine :lolflag:


Thanks

---

### Post by wildmanne39 on 2015-06-21
Please use normal fonts.
Thanks

---

### Post by zaoka on 2015-06-21
Anybody?

---

### Post by oldos2er on 2015-06-21
You don't have a swap partition, correct? Do you have a swap file? Naturally it's going to say swap usage is zero if you have neither.

---

### Post by zaoka on 2015-06-21
Looks like BTRFS does not support swap file and workaround could get data corruption...

---

### Post by Bucky Ball on 2015-06-21
Perhaps look in to cloning your OS partition and reformatting it to EXT4 then cloning back. Add a 2Gb /swap partition and add an entry for it to the fstab file. We can help you with that.  Unless, of course, you can find a workaround for BTRFS. I would certainly clone the partition anyway before going much further with that.

---

### Post by yetimon_64 on 2015-06-21
> **Bucky Ball said:**
> Perhaps look in to cloning your OS partition and reformatting it to EXT4 then cloning back. Add a 2Gb /swap partition and add an entry for it to the fstab file. We can help you with that.  Unless, of course, you can find a workaround for BTRFS. I would certainly clone the partition anyway before going much further with that.

Doesn't cloning actually copy the filesystem formatting as well? I am thinking that when the clone is used to reinstall, it will revert back to BTRFS.

 Maybe tarballing the files and then changing the filesystem type may work. I have seen someone here mentioning "fsarchiver", which I believe may do a "tarball" like proceedure. Though I am not entirely sure how fsarchiver actually works.  Yeti

---

