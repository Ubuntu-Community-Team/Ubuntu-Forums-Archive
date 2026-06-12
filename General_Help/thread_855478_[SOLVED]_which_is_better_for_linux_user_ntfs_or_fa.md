---
title: "[SOLVED] which is better for linux user ntfs or fat32"
date: 2008-07-10
forum: General Help
---

### Post by harsh1kumar on 2008-07-10
I want to format a partition so that I can store all my data on it and it can be used both in windows and ubuntu. So I wanted to know out of fat32 and ntfs, which is better. 

I am using vista and ubuntu hardy.

---

### Post by Woody1987 on 2008-07-10
FAT32 would be more stable then NTFS, but if you use FAT32 you are limited to files that can not be any bigger than 4gigabytes as files of this size or not supported. NTFS allows files of a much larger size. You could try what i do which is to use ext3 and then install an ext3 driver for windows which will allow you to browse the partition from within windows.

---

### Post by protogenesis on 2008-07-10
You'll have an easier time with FAT32 versus NTFS.  This is not to say that NTFS won't work, but you FAT32 will be an out-of-the-box non-issue.

You should be able to access NTFS from Linux, no problem, if you are only reading the files . However, if you want to write files to NTFS, you'll need a small workaround.  If you're going read-only, it doesn't matter, but for writing, it might be smarter to go with FAT32.

---

### Post by tamoneya on 2008-07-10
i will second the recommendation to use ext3 and a windows driver.  Here is the link to the driver for ext3 under windows.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

