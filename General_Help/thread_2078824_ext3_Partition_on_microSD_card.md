---
title: "ext3 Partition on microSD card"
date: 2012-10-31
forum: General Help
---

### Post by NJPinator on 2012-10-31
First of all, not sure if this is in the right category...

Now, my actual issue: I've got a 4GB PNY brand microSDHC card which I'm trying to put an ext3 partition on, but GParted and mkfs.ext3 keep giving me errors. In fact, the card -- for what reason, I'm not sure -- will not let me create a Linux partition of any type (ext2,ext3,ext4). However, it does let my create FAT16 and FAT32 partitions on it.

The card is being read via the microSD to SD card adapter that it came with, and that in turn is being put into my laptop's in-built 3-in-1 card reader.

If it makes any difference, the laptop's card reader is supposed to supprt SD cards, xD cards, and Sony Memory Sticks, but  will only read SD cards within Ubuntu, and fails to work in Windows 7, both issues most likely down to a lack of drivers.

Finally, the  log that GParted gave me upon the error is attached to this post, along with the output mkfs.ext3 gives upon execution. Any help would be greatly appreciated!

---

### Post by Bobhuber on 2012-10-31
> **NJPinator said:**
> First of all, not sure if this is in the right category...

Now, my actual issue: I've got a 4GB PNY brand microSDHC card which I'm trying to put an ext3 partition on, but GParted and mkfs.ext3 keep giving me errors. In fact, the card -- for what reason, I'm not sure -- will not let me create a Linux partition of any type (ext2,ext3,ext4). However, it does let my create FAT16 and FAT32 partitions on it.

The card is being read via the microSD to SD card adapter that it came with, and that in turn is being put into my laptop's in-built 3-in-1 card reader.

If it makes any difference, the laptop's card reader is supposed to supprt SD cards, xD cards, and Sony Memory Sticks, but  will only read SD cards within Ubuntu, and fails to work in Windows 7, both issues most likely down to a lack of drivers.

Finally, the  log that GParted gave me upon the error is attached to this post, along with the output mkfs.ext3 gives upon execution. Any help would be greatly appreciated!
Simply put a micro sd controller is designed for fat 16 (up to 2gig) or the high density (class 10) fat 32 file system for the larger storage cards not ext3 or ext4 .

---

### Post by NJPinator on 2012-10-31
So what's the issue? Is the task impossible? My microSD is a Class 4, and is 4GB. Also, what do you mean by the "controller"?

---

### Post by Slim Odds on 2012-10-31
> **Bobhuber said:**
> Simply put a micro sd controller is designed for fat 16 (up to 2gig) or the high density (class 10) fat 32 file system for the larger storage cards not ext3 or ext4 .
You are totally incorrect. The controller reads and writes sectors, it could care less what format you use for your file system.

I've used an ext3 partition in my Android phone in the past to extend the local program storage. It's not hard.

---

### Post by NJPinator on 2012-11-01
Correction appreciated, Slim Odds, but that doesn't really aid me in any way, it just proves that it's possible. :/ Still stuck here as to how to get the partition created.

---

### Post by LewisTM on 2012-11-01
It's possible that GParted didn't create the partition right. Try using another utility like cfdisk or sfdisk to create the partition, then mkfs to format it. You could also try to format with xfs (needs package xfsprogs) which is a fully Linux-compatible fs but does not follow the same design principles as ext2/3/4.

Cheers!

---

### Post by Slim Odds on 2012-11-01
GParted works just fine. That's what I used for the ext3 partition that I used for my Nexus One.
Just remember that you have to create the partition first (with the correct type, ext3) and then format it (mkfs.ext3). Or use whatever type that you want.

---

### Post by NJPinator on 2012-11-01
I had initially used **fdisk** to create a Linux partition on the disk, and then **mkfs.ext3** to format it. GParted was my second resort to getting this partition created. I'll post back tomorrow with a full log of the commands, if need be. For now, I'm still scratching my head over this. I really can't see what the problem is, myself.

---

### Post by LewisTM on 2012-11-01
Well by Googling a little you, especially with the error "Warning, had trouble writing out superblocks", you can find that you are not alone, others have experienced exactly the same problem. Typically it's solved by getting another brand of microSD card. Sucks :(
[http://ubuntuforums.org/showthread.php?t=1931432](http://ubuntuforums.org/showthread.php?t=1931432)

---

### Post by NJPinator on 2012-11-02
Well, that's a little annoying...so my only option is to buy another card?

---

### Post by LewisTM on 2012-11-02
Well if you absolutely want to have an ext3 partition on the drive (you still haven't told us why), you could do so by creating a large 4 GB loopfile on a FAT32 partition and formatting it as ext3.

I could go into more detail but I need to know what is the intended use. Is it for use on a single system or to carry around a lot? The reason is that loopfiles are not transparently mounted.

---

