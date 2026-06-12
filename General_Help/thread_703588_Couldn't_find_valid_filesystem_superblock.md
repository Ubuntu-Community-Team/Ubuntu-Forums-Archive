---
title: "Couldn't find valid filesystem superblock"
date: 2008-02-21
forum: General Help
---

### Post by Son of Silas on 2008-02-21
I have added a PATA IDE drive as a slave to the existing master in my Ubuntu Gutsy desktop. I used GParted to create an EXT3 partition the entire size of the disk.

After some permission issues and using chown I can now use the drive normally. I have a problem though, it appear as "74.5 GB Volume: disk"

I want to rename it to be "Media" so I tried typing

> sudo tune2fs -L Media /media/disk which then gave the error
> tune2fs: Is a directory while trying to open /media/disk
Couldn't find valid filesystem superblock."

I'm sure the learning curve with linux/ubuntu will straighten out eventually, but I really struggle with things that used to be so easy in Windows.

Thanks for any suggestions

---

### Post by nick_h on 2008-02-21
You need to use the device name not the mount point with tune2fs.  It will be something like /dev/sdb.

---

### Post by Son of Silas on 2008-02-21
OK, that would make sense. How do I find out what the device name is?

---

### Post by koenn on 2008-02-21
type ```
mount
``` in a terminal or look in /etc/fstab,and see which device is mounted to /media/disk

---

