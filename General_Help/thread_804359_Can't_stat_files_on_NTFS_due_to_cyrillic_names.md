---
title: "Can't stat files on NTFS due to cyrillic names"
date: 2008-05-23
forum: General Help
---

### Post by n-alexander on 2008-05-23
Got a problem backuping.

1. I have 2 NTFS disks mounted:

/dev/sda6 on /mnt/data type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)

/dev/sdf1 on /media/disk type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)

2. do an rsync from /mnt/data to /media/disk/backup500

3. get an error: 

rsync: recv_generator: failed to stat "/media/disk/backup500/Mult/&#1025;&#1078;&#1080;&#1082; &#1074; &#1090;&#1091;&#1084;&#1072;&#1085;&#1077;.avi": Invalid or incomplete multibyte or wide character (84)

So I can access Cyrillic filenames on the first NTFS disk but not on the second. Why?

Ubuntu 8.04

Thanks,
Alex

---

### Post by sdennie on 2008-05-23
Sounds like you probably need to mount the disk with a different character encoding.  Maybe try adding utf8 as one of your mount options.

---

### Post by n-alexander on 2008-05-23
> **vor said:**
> Sounds like you probably need to mount the disk with a different character encoding.  Maybe try adding utf8 as one of your mount options.

yep, did that. The question is, how do I make the KDE automount add that option too? Somewhere in HAL?

Don't want to add a line to fstab, for then it'll only mount under root or I'll have to rebuild some NTFS utilities - at least this is what it said when I tried.

---

### Post by sdennie on 2008-05-23
> **n-alexander said:**
> yep, did that. The question is, how do I make the KDE automount add that option too? Somewhere in HAL?


I think you'll need to use udev in that case.  A decent guide can be found at [http://reactivated.net/writing_udev_rules.html](http://reactivated.net/writing_udev_rules.html) but, it's a hassle to do this.  See below...

> 
Don't want to add a line to fstab, for then it'll only mount under root or I'll have to rebuild some NTFS utilities - at least this is what it said when I tried.

Running "man mount" and looking at the ntfs section says that an ntfs partition can be mounted with an explicit uid, gid and umask.  Going the fstab route with those options is probably MUCH easier than going the udev route.

---

