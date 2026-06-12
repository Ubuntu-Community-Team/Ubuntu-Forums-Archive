---
title: "Can't unmount my USB drive."
date: 2008-02-12
forum: General Help
---

### Post by solarwind on 2008-02-12
Hey all, I just installed Ubuntu and did some partition editing along with edits to /etc/fstab, (so this could be the problem) and I am now **unable to unmount my USB drive when I hit "safely remove" from the icon in the desktop**.

Here's the error window that pops up:
[IMG]http://img232.imageshack.us/img232/5184/snapshot1ak7.png[/IMG]

Here's my /etc/fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

# /dev/hda1 (Windows first partition)
UUID=F0B8F6B2B8F67706 /media/hda1     ntfs    defaults,umask=007,gid=46 0       1

# /dev/hda2 (Windows second partition)
/dev/hda2       /media/hda2     ntfs    defaults,umask=007,gid=46       0       0

# /dev/hdb1 (Linux first partition)
UUID=b32fdadc-f688-4871-a0ce-3ab6f3cf79cf /               ext3    defaults,errors=remount-ro 0       1

# /dev/hdb5 (Linux swap)
UUID=89cd0c9b-f1e1-4fcb-933a-3f98ce2ffcfa none            swap    sw              0       0

```

Any ideas how to fix this?

---

### Post by macogw on 2008-02-12
Well /dev/sda1 isn't listed in your /etc/fstab, so that shouldn't be making any difference.  Can you unmount it as root? ```
sudo umount /media/disk/
```  It's saying a user other than you mounted it.  Was it mounted by someone else when they were logged in, maybe?  Or maybe you mounted it as root from the command line?  It's trying to keep you from messing with whatever another user did.

---

### Post by solarwind on 2008-02-12
It let me unmount it using sudo. I was the one who plugged it in.

---

### Post by solarwind on 2008-02-12
However, it still wont let me unmount normally...

---

### Post by solarwind on 2008-02-13
Bump.

---

