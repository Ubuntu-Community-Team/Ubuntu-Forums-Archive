---
title: "USB drive Mounting ability - hosed"
date: 2007-05-08
forum: General Help
---

### Post by ctsdownloads on 2007-05-08
No @#$%ing idea how this happened, but somehow I managed to hose the ability to mount any drives using USB. This includes, hard drives, flash drives and cameras.

Here is my fdisk -l output

>  Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

  Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       36104   290005348+  83  Linux
/dev/sda2           36105       36481     3028252+   5  Extended
/dev/sda5           36105       36481     3028221   82  Linux swap / Solaris

and of course, my fstab

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=906983cb-1ed6-4722-81d7-5f1c3579a8fb /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=7194b110-ac5a-4f7e-9677-b2b23527fe1c none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

/tmp/app/1/image /tmp/app/1 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/2/image /tmp/app/2 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/3/image /tmp/app/3 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/4/image /tmp/app/4 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/5/image /tmp/app/5 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/6/image /tmp/app/6 cramfs,iso9660 user,noauto,ro,loop,exec 0 0

Please help me to get this resolved. I am running a fully patched Edgy install and have zero interest in moving to Feisty, reinstalling or anything else like that. I simply want to fix the ability to mount automatically again.

Thanks

---

### Post by ctsdownloads on 2007-05-08
Well i managed to fix it, here is what I did.

I made a back up of my fstab file.

Then edited out the mumbo-jumbo so it looked like this:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=906983cb-1ed6-4722-81d7-5f1c3579a8fb /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=7194b110-ac5a-4f7e-9677-b2b23527fe1c none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

Saved it, rebooted and from that point on, the drives now mount across the board. :guitar:

---

