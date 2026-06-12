---
title: "Files not displayed"
date: 2008-03-22
forum: General Help
---

### Post by bishamon on 2008-03-22
Hi

I cannot get files with filenames that contain chinese chacters to be displayed. Anyone knows why this is so? I tested in Opengeu (installed and livecd) and it works, or at least it display the file with square replacing the chinese characters.

Over, in the debian sid installation, it totally not displaying the files at all. Posted the help here, since I'm hoping someone here can shed some light on this as well. Does ubuntu support the display by default? Is it relating the mounting of the partition? The files are all on NTFS. I'm using ntfs-3g to mount the partition. Even using ntfs also wont work. This is driving me insane. Lost 70G of files because of this issue. Was going to convert the hdd from ntfs to ext3.  Hopefully I don't have to go back to windows just to resolve this.


Any information I need to provided here for some help?

This is what I have when I do a locale in shell. 

> LANG=zh_CN.GB2312
LANGUAGE=POSIX
LC_CTYPE=zh_CN.GB2312
LC_NUMERIC=POSIX
LC_TIME=POSIX
LC_COLLATE=POSIX
LC_MONETARY=POSIX
LC_MESSAGES=POSIX
LC_PAPER=POSIX
LC_NAME=POSIX
LC_ADDRESS=POSIX
LC_TELEPHONE=POSIX
LC_MEASUREMENT=POSIX
LC_IDENTIFICATION=POSIX
LC_ALL=

---

