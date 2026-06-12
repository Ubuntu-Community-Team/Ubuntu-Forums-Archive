---
title: "Which filesystem for an Ubuntu install on a thumb drive?"
date: 2012-12-13
forum: General Help
---

### Post by Asmodai on 2012-12-13
Hello,

I'd like to install Ubuntu on a flash drive, however I'm unsure which filesystem to use.
Instructions on the web almost universally say to use ext2, but that seems like poor advice to me, as those drives generally have no wear leveling and ext2 will cause frequent writes to a few areas on the drive.

I understand that some file systems optimized for flash storage such as YAFFS2, JFFS2 and UBIFS cannot be used for thumb drives, but are intended for embedded flash storage. Then there's NILFS2, which is log-structured, however it seems that it wasn't really designed for flash devices and as I understand it, may cause frequent writes to the superblocks which are not part of the log. Last there's LogFS. However, to quote the Wikipedia article:

> In contrast to JFFS2, YAFFS, and UBIFS, LogFS also provides a (very) basic, slow support for use with block devices like solid-state drives (SSDs), USB flash drives, and memory cards.
Very basic and slow? Why? In any case, that doesn't sound very good.

So what file system would be best to use?

---

### Post by oldfred on 2012-12-13
The alternative I have seen and use is ext4, but turn journalling off.

       sudo tune2fs -O ^has_journal /dev/sda1
sudo tune2fs -o discard /dev/sda1
No swap or set swapiness or install 'Dynamic Swap Space Manager' from the Ubuntu Software Center
After installing, change the fstab so that everything gets mounted with noatime.

---

### Post by ehraaron on 2012-12-14
I second ext4.. No reason why it wouldn't work well for USB storage. oldfred is spot on with his recommendation.

---

### Post by Asmodai on 2012-12-14
ext4 without journalling indeed seems like a better option than ext2, but I think the core problem remains. ext4 does not employ wear leveling, so there'll be frequent writes to a small number of blocks (some files that are frequently written to and metadata - although noatime surely will help with the latter), while most other blocks are almost never written to. Not sure how many write cycles the average thumb drive can survive, but if it as low as 10000, this might cause problems quickly.

---

