---
title: "Need easy-to-use image backup/restore for ext4"
date: 2012-12-14
forum: General Help
---

### Post by cigtoxdoc on 2012-12-14
I didn't realize that image backups are such a problem to do until I tried to get ahead of a failing hard drive.  What is the Ubuntu equivalent of Macrium Reflect?  I am trying to get my business off of XP before support ends next April, and it appears that Ubuntu does not have a good untility that works with ext4 files systems.

John

---

### Post by ibjsb4 on 2012-12-14
There are several ext4 utilities for backup.  If you just want to create a simple clone then maybe clonezilla would work for you.

[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by CharlesA on 2012-12-14
> **ibjsb4 said:**
> There are several ext4 utilities for backup.  If you just want to create a simple clone then maybe clonezilla would work for you.

[http://clonezilla.org/](http://clonezilla.org/)

+1 to clonezilla.

If you just want to copy the data on a file level, check out rsync.

---

### Post by cigtoxdoc on 2012-12-15
Thank you for your help.  Yes, clonezilla did work in making an image of the extfs file system. Yes, it was also able to put the image on my WD Passport USB device.  Currently, I do not have another hard drive available to restore the image and make sure that it works.

JOhn

---

