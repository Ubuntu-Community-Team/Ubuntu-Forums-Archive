---
title: "CD-ROM won't mount"
date: 2006-11-16
forum: General Help
---

### Post by skale on 2006-11-16
I am trying to mount the (windows) Unreal Tournament CD, and it does not like  it at all.  Here's the command:
```
sudo mount -t iso9660 /dev/hdc /media/cdrom0

```
It gives this message:
```

mount: block device /dev/hdd is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdd,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

This is the error message:
```
[17189839.972000] Unable to identify CD-ROM format.
```

I am not sure what is going on.  I believe the problem is with the type, but it could be something else.  It is not a hardware problem, and fstab has never had problems before, so I do not think it is that.  I would like to mount it, and am almost completely perplexed.  I am sure it is something silly, however.  Here's fstab for a stupid-check.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>   <options>                   <dump/pass>proc            /proc           proc    defaults                        0  0
/dev/hda3       /               ext3    defaults,errors=remount-ro      0  1
/dev/hda1       /media/hda1     ext3    defaults                        0  1
/dev/hda4       /media/hda4     ext3    defaults                        0  2
/dev/hda2       none            swap    sw                              0  0
/dev/hdc        /media/cdrom0   auto    user,noauto                     0  0
/dev/hdd        /media/cdrom1   iso9660 user,auto                       0  0
/dev/fd0        /media/floppy0  auto    rw,user,auto                    0  0
/dev/sda1       /media/usbdisk  vfat    user,auto                       0  0




```

---

### Post by taurus on 2006-11-16
Are you sure you got the right CD drive?  You tried to mount it from /dev/hdc but the error report came from /dev/hdd!!!

---

### Post by skale on 2006-11-16
Yes.  The cause of the disparity is that I tried to mount it on both my CD drives.  I simply put up the command for hdc and posted the error for hdd.  Both have the same problem.

---

### Post by taurus on 2006-11-16
And I suppose you can read that CD fine with another machine!

---

