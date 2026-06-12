---
title: "How to get past 'File size limit exceeded...' error"
date: 2007-07-11
forum: General Help
---

### Post by mmathur on 2007-07-11
I am trying to back up some large files (>2GBs) from my ubuntu machine (running Feisty) and it fails on any files that are over 2GB.  I have tried to remove the limits but there is no luck.

Would anyone be able to advise on how to get past the 2GB limit?

Here is the error that I get:
File size limit exceeded (core dumped)

---

### Post by pxwpxw on 2007-07-11
If you are backing up onto FAT16 filesystem, that would be a problem

[http://support.microsoft.com/kb/310561]("http://support.microsoft.com/kb/310561")

---

### Post by rbmorse on 2007-07-11
Or, FAT32 for that matter.

---

### Post by AlexThomson_NZ on 2007-07-12
Filesystem size limits:
FAT16 - 2GB
FAT32- 4GB
NTFS- 16EB(!)
EXTx- 2TB

---

### Post by bettlebrox on 2007-07-12
Also, what does "ulimit -a" show for the "file size". If it's set to unlimited, look at /etc/security/limits.conf you can up the max file for the OS using that file, if the kernel and filesystem support it.

---

