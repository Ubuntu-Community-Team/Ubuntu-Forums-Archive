---
title: "Strange Hard Disk Mounting Problem"
date: 2007-09-20
forum: General Help
---

### Post by bigalreturns on 2007-09-20
I have a problem with mounting a partition on one of my hard disks.  I'm using ubuntu 7.04, fully updated etc., but have installed kde3.2 to use instead of gnome.
The problem: When I initially logon, the partition isn't mounted, and through no amount of effort can I get it to mount.  The only way I can access it is to logon as root, run gnome partition editor (gparted), upon which the new drive is auto detected and mounted.  If I then log out of root and back into my usual user, the drive has appeared there as well.  I've checked the permissions of the disk, and it's all set to allow read and write, and the owner is my normal user account, not root.  Also, I tried checking the mount automatically box in the disk properties, but to no avail.  If it has any relevance the filesystem is ext3.  Any help much appreciated, as this is very annoying!

---

### Post by dcstar on 2007-09-20
> **bigalreturns said:**
> I have a problem with mounting a partition on one of my hard disks.  I'm using ubuntu 7.04, fully updated etc., but have installed kde3.2 to use instead of gnome.
The problem: When I initially logon, the partition isn't mounted, and through no amount of effort can I get it to mount.  The only way I can access it is to logon as root, run gnome partition editor (gparted), upon which the new drive is auto detected and mounted.  If I then log out of root and back into my usual user, the drive has appeared there as well.  I've checked the permissions of the disk, and it's all set to allow read and write, and the owner is my normal user account, not root.  Also, I tried checking the mount automatically box in the disk properties, but to no avail.  If it has any relevance the filesystem is ext3.  Any help much appreciated, as this is very annoying!

Your /etc/fstab file is most likely the issue, post the contents of it (or do a search for similar issues).

---

### Post by bigalreturns on 2007-09-20
[quote=/etc/fstab]
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb2
UUID=629c72a6-3c9a-4e8e-8724-e26f3112d3dd /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=717ad401-b99e-4e54-b9b2-0b200e7ef04f none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
[/quote]

The partition in question is hdb1

---

### Post by dcstar on 2007-09-20
> **bigalreturns said:**
> The partition in question is hdb1

Then you will have to manually edit your fstab file and add the appropriate entry for your hdb1 filesystem.

---

### Post by g2g591 on 2007-09-20
try using this the following as your entry, of course replacing yourmountpoint here with the actual place you wish it to be mounted (you must manually create this directory if it doesn't yet exist)
/dev/hdb1 yourmountpointhere ext3 defaults,user 0 0

---

### Post by bigalreturns on 2007-09-24
thanks to both of you, I will give this a whirl tonight.

---

