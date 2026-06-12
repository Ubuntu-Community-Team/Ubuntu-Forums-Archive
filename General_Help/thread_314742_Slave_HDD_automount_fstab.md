---
title: "Slave HDD automount fstab"
date: 2006-12-08
forum: General Help
---

### Post by Michiba on 2006-12-08
Hi all,

I have just upgraded to Edgy and can't get my hdb1 to mount on boot up. Please see fstab below.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=4e56eada-0e26-494c-b282-03e301814e20 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=8debc655-8822-4d89-93a9-9db2743c283e none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdb1       /storage      ext3    defaults        0       2


So I keep storage files on /storage and the drive still contains windows backup files and backups from breezy.

Any advice appreciated.

Michiba

---

### Post by dcstar on 2006-12-08
> **Michiba said:**
> Hi all,

I have just upgraded to Edgy and can't get my hdb1 to mount on boot up. Please see fstab below.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=4e56eada-0e26-494c-b282-03e301814e20 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=8debc655-8822-4d89-93a9-9db2743c283e none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdb1       /storage      ext3    defaults        0       2


So I keep storage files on /storage and the drive still contains windows backup files and backups from breezy.

Any advice appreciated.

Michiba

And **exactly** what happens?, and what happens if your type "mount /dev/hdb1" in a terminal?

---

### Post by Michiba on 2006-12-28
Hi David,

I did not make a folder under root for my storage mount so just oversight on my part.

thanks for replying 

Michiba

---

