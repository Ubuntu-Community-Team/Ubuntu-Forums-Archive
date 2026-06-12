---
title: "cannot write to XFS as normal user"
date: 2005-05-08
forum: General Help
---

### Post by mdbarton on 2005-05-08
I want to install mythtv, and have taken the advise that a large XFS partition would be needed as XFS handles large files well.
I've now re-shuffled all my partitions around and have a 82MB XFS partition (formatted using gparted).
My fstab looks like this:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda7       /boot           ext3    defaults        0       2
/dev/hda8       /mnt/bigdisk    xfs     rw,user,defaults 0 0
/dev/hdb2       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdc        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /mnt/ex-pee     ntfs    ro,defaults,umask=000   0 0
/dev/hda6       /mnt/data       vfat    rw,user,uid=1000,gid=1000,umask=0000 0 0
/dev/hdb3       /mnt/backup     vfat    rw,user,uid=1000,gid=1000,umask=0000 0 0
```
However, when logged on as a normal user I can read the XFS partition (called 'bigdisk' because I could not think of anything else!), but cannot write.
What options should I be using on the fstab entry?  Is there a particular way the partition should have been formatted that gparted may not have used?  Does the UUID of the XFS partition have any bearing on this?

---

### Post by mdbarton on 2005-05-08
fixed my own problem
ran 'nautilus computer:///' as root, changed the permissions on the drie so they are world readable, owned by group users.  Rebooted, now can access ok.

---

