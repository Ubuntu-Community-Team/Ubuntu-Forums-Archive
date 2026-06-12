---
title: "Can't set permissions on folders, even as superuser"
date: 2007-03-10
forum: General Help
---

### Post by se2131 on 2007-03-10
I'm trying to backup a set of folders that have my pictures to an external drive.  However, I just realized that the permissions are screwy, and so I can't view or copy them without becoming the superuser.  As of right now, all the folders have the permissions:

rw-rw-----

and as the superuser, I'm unable to use chmod (666) to allow any user to read and write.  I also tried using Nautilus (as the superuser) to change the permissions, and the changes wouldn't stick.  As in, I would change the permission, and it would go right back to ---.  No error message or anything.

Any help in this matter is appreciated, thanks in advance.

---

### Post by taurus on 2007-03-10
What filesystem is that directory on?

---

### Post by se2131 on 2007-03-10
It's on a separate partition from the root filesystem, and it's also ext3 (mount point = hda3).  If you need more information, what should I give?

---

### Post by taurus on 2007-03-10
Can you give me the complete path (name) to it?  How do you mount it in /etc/fstab?

```
cat /etc/fstab
```

---

### Post by se2131 on 2007-03-10
Ah gotcha.  This is the entry in the fstab:

# /dev/hda3
UUID=4CAC-1FB2  /media/hda3     vfat    defaults,utf8,umask=007,gid=46 0       1

hm... I guess it is a fat32 partition (I forgot that I share it w/ windows), does that make file permissions difficult to change?

---

### Post by taurus on 2007-03-10
Can't change permissions for vfat or ntfs.  You can mount it with something like

```
/dev/hda3   /media/hda3   vfat   iocharset=utf8,umask=000   0   0
```
Then, you as a regular user can read and write to it.

---

### Post by se2131 on 2007-03-10
Hey thanks, that seemed to do it.

---

