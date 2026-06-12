---
title: "DVD rom/cd rw drive"
date: 2007-11-16
forum: General Help
---

### Post by alnhntr29 on 2007-11-16
I have been playing with fstab in order to get my system to see a sony dvd drive. My question is why are there 3 fstab entries and which one is it that I should have changed. The following is all 3 entries, could somebody tell me what they need to look like? I changed all 3 and I now have a dvd icon, but it still wont read from the drive, and says mount point does not exist.


fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=c5b6d265-b06e-4829-8ecc-5d30f02979f9 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=c4f681fe-ae01-459b-96b8-9e62846eec6d none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/dvd      udf,iso9660 user,noauto     0       0

(this one had only /dev/cdrom0, I changed it to /dev/hdc and added the 2nd line.the rest all I did was add the second line)

fstab.edgy

 /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=c5b6d265-b06e-4829-8ecc-5d30f02979f9 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=c4f681fe-ae01-459b-96b8-9e62846eec6d none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/dvd      udf,iso9660 user,noauto     0       0

fstab.pre-uuid

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/dvd      udf,iso9660 user,noauto     0       0

---

