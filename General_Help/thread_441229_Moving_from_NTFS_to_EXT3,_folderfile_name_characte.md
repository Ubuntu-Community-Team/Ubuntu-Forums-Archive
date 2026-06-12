---
title: "Moving from NTFS to EXT3, folder/file name character encoding problem"
date: 2007-05-12
forum: General Help
---

### Post by gabng on 2007-05-12
Hi, I'm trying to migrate to Linux system, my next step is to move my files from NTFS partitions to EXT3 partitions.

However, some of my files and folders in NTFS are in Chinese.  After I transfer these files from NTFS to EXT3 under Ubuntu (which displays properly), the folder/file names don't display properly when I go back to XP (using ext2ifs driver).  So I tried to transfer them under XP (again reads properly), they don't show up properly under Ubuntu.

So my problem is if there are any way to have these files in EXT3 in which they can be displayed properly under both Ubuntu and XP?  Or am I stuck with mounting NTFS partitions in Ubuntu to get this result?  Please help!

---

### Post by tinwelint on 2007-11-25
This probably has to do with the limitations in ext2ifs.
[http://www.fs-driver.org/faq.html#not_sup_feat](http://www.fs-driver.org/faq.html#not_sup_feat)

I have a problem in the same category. Files and folders with swedish characters (like å, ä and ö) created on my ext3 drives from windows aren't correct in linux. That's because the ext2ifs driver uses the current windows codepage. And linux doesn't like it. :(

---

