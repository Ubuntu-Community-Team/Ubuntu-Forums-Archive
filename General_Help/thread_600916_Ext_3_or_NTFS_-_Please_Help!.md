---
title: "Ext 3 or NTFS - Please Help!"
date: 2007-11-02
forum: General Help
---

### Post by nickdr on 2007-11-02
I want to create a share partition to use between my Windows XP install and my Ubuntu 7.10 AMD64 install. Is is better to format the shared partition using Ext3 or NTFS? Both installs need read and write access to this partition. I do no want either install to mount the other installs partition! Basically is EXt3 read and write support for Windows better than the NTFS read and write support for Linux?

Thanks!

---

### Post by hikaricore on 2007-11-02
I would say that they're both about on par.

NTFS drivers for Linux are reverse engineered so there can be minor issues from time to time.

On the other hand, the Ext2/3 access drivers for ***dows can also be a pain at times, and there are sometimes files you can not access, but it is rare.

I'd say go with whatever you feel more comfortable with to be honest.

---

### Post by rsambuca on 2007-11-02
I use both and have never had a single problem either way.

---

### Post by loganm10 on 2007-11-02
I would say fat32 ot NTFS

Ext3 requires some setup on WinXP where fat32 and NTFS work on both OS's out of the box

---

### Post by Cochise on 2007-11-02
id use ext3 personally if linux is your main os or ntfs if windows is your main os

---

### Post by rsambuca on 2007-11-02
> **loganm10 said:**
> I would say fat32 ot NTFS

Ext3 requires some setup on WinXP where fat32 and NTFS work on both OS's out of the box

FAT32 is a very poor choice.  No journaling, no permissions, lots of maintenance required.

---

### Post by hikaricore on 2007-11-02
> **rsambuca said:**
> FAT32 is a very poor choice.  No journaling, no permissions, lots of maintenance required.

And that nasty 4Gb(or so) file size limit if you're planning on making backups.

---

### Post by Matakoo on 2007-11-02
> **nickdr said:**
> I want to create a share partition to use between my Windows XP install and my Ubuntu 7.10 AMD64 install. Is is better to format the shared partition using Ext3 or NTFS? Both installs need read and write access to this partition. I do no want either install to mount the other installs partition! Basically is EXt3 read and write support for Windows better than the NTFS read and write support for Linux?

Thanks!

They're both about equal in performance and stability, as far as I can tell. A couple of things worth considering though:

1. The windows ext3 driver is a bit buggy under Vista, so if you plan on switching to Vista that is something you might want to look into. Or I should say it was when I used it under Vista a few months back - it might be better now.
2. The windows ext3 driver insists on setting owner and group of files on ext3 partitions to root whenever a file is written to disk regardless of what the ownership was beforehand.

If you intend to continue to run XP and the latter is of no importance for you, either works fine.

---

