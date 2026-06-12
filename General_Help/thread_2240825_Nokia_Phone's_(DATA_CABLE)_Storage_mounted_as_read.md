---
title: "Nokia Phone's (DATA CABLE) Storage mounted as read only filesystem"
date: 2014-08-22
forum: General Help
---

### Post by linuxyogi on 2014-08-22
Hi, 

Today I purchased a data cable. I can read files from the SD card but cant write to it. 

I tried to chmod but I am getting read only filesystem I/O error.

This is happening both in Lubuntu and Manjaro.

How to fix this ?

---

### Post by linuxyogi on 2014-08-22
Solved !

Did 

```
sudo dd if=/dev/zero of=/dev/sdb bs=4M
```

Then created a FAT32 partition with Gparted. Now I can write to the disk but when I tried to restore data I found that a a large number of files are corrupted..

---

### Post by Impavidus on 2014-08-22
File systems are remounted read-only when the system encounters an error. Wiping the partition table and creating new partitions before remounting makes it writable for a while, until the system encounters the next error. I would suspect a hardware problem.

Related thread: [http://ubuntuforums.org/showthread.php?t=2240828](http://ubuntuforums.org/showthread.php?t=2240828)

---

