---
title: "NTFS or FAT32 ?"
date: 2007-12-18
forum: General Help
---

### Post by ummaya on 2007-12-18
I am going to make a new Windows XP installation and I want to exploit this occasion to try Ubuntu. Right now my 140GB Hard Disk is partitioned into two drives : one 40GB drive (C) for Windows OS and all Program files and one 100GB drive (D).

I would like to repartitioned my hard disk into three parts :
Windows XP OS on a 40GB drive and all Windows stuffs (files ,movies, games etc...) on drive two (90GB)
Drive three : 10 GB for Ubuntu (root/ SWAP/ Home)

How should I format drive two ( in which I want to store things I would like to share with Ubuntu ) and drive three? FAT32 or NTFS?

Thanks.

---

### Post by jespdj on 2007-12-18
In Ubuntu 7.10, reading and writing from and to NTFS partitions is enabled by default. So just use NTFS.

The partition where you're going to install Ubuntu on should be formatted with a Linux file system, such as ext3. The Ubuntu installer will do this for you.

---

### Post by ummaya on 2007-12-18
Hi **jespdj**

Thank you for helping

---

### Post by mozetti on 2007-12-18
My advice - use FAT32. NTFS read/write support is now pretty good, but because MS hasn't opened up the specs for NTFS there is always the chance something could go wacky. That being said, the NTFS write support is supposed to be very good, but for me I err on the side of safety.

Just my $0.02

---

### Post by HermanAB on 2007-12-18
FAT32 is not robust.  So while it will be easier to handle, your data is likely more important than that.

Another option is to install an Ext3 file system in Windows and instead of making Linux Windows compatible, go the other way around and improve Windows so it supports Linux.

Cheers,

Herman

---

### Post by weblordpepe on 2007-12-19
NTFS is leaps and bounds ahead of FAT32, even under Linux. FAT32 is pretty much oldschool and geared at older systems. There's all kinds of redundancy & stuff in NTFS. Now that you can read/write NTFS in linux, there's no real need to touch FAT32. Not speed, not security, not  nothing.

The real problem with NTFS on linux is compression. But thats OK, just don't use compression (native filesystem compression, not file archives).
Linux will also ignore any kind of NTFS security that other Windows machines obey.

---

### Post by LaRoza on 2007-12-19
I would have in the past said "FAT32", but NTFS works fine and is much better than FAT32.

---

