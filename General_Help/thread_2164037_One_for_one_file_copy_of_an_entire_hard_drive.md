---
title: "One for one file copy of an entire hard drive"
date: 2013-07-20
forum: General Help
---

### Post by cincinnatus13 on 2013-07-20
So I don't need to clone a hard drive but rather just make a straight copy of files from one to the other.
Basically, both are NTFS formatted externals.

So is there any problem with just using dd (something like dd if=/dev/sda3 of=/dev/sda4 or whatever it happens to be)? I'm not sure how Linux will handle it and if there will be like massive defragmentation like on the original or what. I only say this because NTFS is a Windows format and I know how Windows throws things around everywhere (unlike Linux IIRC.)
But anyway, all I need is basically to copy my entire media drive as a backup. I figure using the terminal might be a hair quicker than using Nautilus.

---

### Post by Cheesemill on 2013-07-20
Don't use dd as this will make a drive image rather than a file backup. I'd use rsync instead...
```
rsync -avz /path/to/source/ /path/to destination/
```
On of the best features of rsync is that you can continue the file copy from where it left off in case you need to stop the copy for any reason. Also by copying file by file instead of doing a disk image there will be no fragmentation on the destination drive.

---

### Post by dcstar on 2013-08-04
Install **Unison**.

---

