---
title: "fsck taking a long time"
date: 2007-12-02
forum: General Help
---

### Post by mp4215 on 2007-12-02
Everytime my filesystem is forced to do a fsck it takes forever to do that. Yesterday it took over 12 hours. I turned on my computer to do some school work at 2:30 pm and by the time I went to bed at 2:00 am it was still checking. I could deal with it taking an hour, but over 12 is pretty ridiculous. The disk is 250gb.

Here is my fstab:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=226188e0-c73d-4e3b-8f9f-6340489e5e70 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=1539b259-6619-47b3-b866-a5d17744b90e none            swap    sw              0       0
/dev/hdb1       /home           ext3    defaults,errors=remount-ro 0    1
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

---

### Post by mahiyar on 2007-12-02
Temporarily change the last bit in the fstab line
>  UUID=226188e0-c73d-4e3b-8f9f-6340489e5e70 /               ext3    defaults,errors=remount-ro 0       1 from 1 to 0, so that the next time fsck does not check at all. Boot from a live cd, run fsck from the command line and maybe you get t o know the errors and the reason for delay on observing the results.

---

