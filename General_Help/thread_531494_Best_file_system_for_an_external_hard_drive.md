---
title: "Best file system for an external hard drive"
date: 2007-08-21
forum: General Help
---

### Post by fearevilleet on 2007-08-21
Hi,

I just got a new 500 gig hdd. I want to use this hdd on linux, mac and windows. I am sure many of my files sizes will, exceeded the limits of FAT so what is the best file system to use so all OS will be able to access the hdd.

---

### Post by reckless2k2 on 2007-08-21
Ntfs

---

### Post by fearevilleet on 2007-08-21
Ya thats what I was thinking too, but dosent linux have issues mounting ntfs?

---

### Post by capink on 2007-08-21
I am able to read/write to my ext3 partitions with no problems in windows using the driver from this site:

[http://www.fs-driver.org/]("http://www.fs-driver.org/")

and since ext3 is open source, I reckon the above mentioned driver is more reliable than any reverse engineered implementation of closed source ntfs on linux .

Look for a similar solution for Mac here:

[https://sourceforge.net/projects/ext2fsx]("https://sourceforge.net/projects/ext2fsx")

but I don't use Mac so I don't know how good it is.

---

### Post by astralsin on 2007-08-21
i've had really good luck with that ext driver for windows.  but likewise ntfs-3g is a great solution for reading/writing ntfs volumes in linux.  i've never had problems with it either.  i think the best solution would probably be for you to use ext3 and use the fs driver for windows but if you have problems, there are more ways to skin a cat, you know

---

### Post by fearevilleet on 2007-08-21
Thanks, I think I will format it as ext3 when I get home. I did not know windows had an ext3 driver available for it.

---

### Post by SQuark on 2007-09-10
I was just about to ask the same question on here. So, how did it go for you?

From [what I've read](https://sourceforge.net/forum/forum.php?forum_id=218925), ext3 write support is very experimental on OS X. Did you have any luck with this?

How is ntfs write support in OS X?

Another option seems to be hfs+ (with journaling disabled for Linux), and MacDrive (commercial software) for Windows.

---

