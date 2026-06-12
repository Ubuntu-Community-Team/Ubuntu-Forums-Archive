---
title: "Mounting CD_Rom at startup"
date: 2007-01-10
forum: General Help
---

### Post by true_friend on 2007-01-10
i have a little problem. it was ok when kubuntu installed but now i feel that when i insert cd in my cd rom it is not loaded when i checked /etc/fstab there was no command for cd rom. i have two devices one is writer which runs as primary slave and cdrom which runs as sec slave.
.......................................................................
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1     /media/hda1     ntfs-3g     defaults,locale=en_US.utf8   0    0
/dev/hda5       /media/hda5     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda8       /media/hda6     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda9       /media/hda7     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom   udf,iso9660 user,noauto     0       0
...........................................................
this is the content of fstab file. i tried to add last line manually by naming cdrom as hdb but it did not worked. plz tell what command i should use.
Regards
True_Friend

---

### Post by Topsiho on 2007-01-10
You write: "i have two devices one is writer which runs as primary slave and cdrom which runs as sec slave."

This means, I think, that the first of them is /dev/hdb and the second one is /dev/hdd

IDE0 Master is /dev/hda
IDE0 Slave is /dev/hdb   <==

IDE1 Master is /dev/hdc
IDE1 Slave is /dev/hdd   <==

So you should correct the entries in your /etc/fstab:

/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdb /media/cdrom udf,iso9660 user,noauto 0 0

for this.

Also you should check that the mountpoints /media/cdrom0 and /media/cdrom both exist and are independent from each other (not linked, I mean).

Success,

Topsiho

---

### Post by true_friend on 2007-01-10
thnx it is ok now.

---

