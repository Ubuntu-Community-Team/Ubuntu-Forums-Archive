---
title: "problem with removable media"
date: 2008-01-05
forum: General Help
---

### Post by tomstaehr on 2008-01-05
I've got an external harddrive and it mounts allright on my ubuntu, but I'm unable to write on it, even though it's got it's own line in my fstab, is completely empty and formatted in ext3.

This is my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=0a9b8742-0cc1-43d6-909a-46b953a1e40b /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=5a0c36e8-80f6-4168-b853-dfbdff23d1b8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sdb1	/media/extern	ext3	rw,user,auto,exec,sync	0	0

I don't know what to do, so please help me!!

---

### Post by nick_h on 2008-01-05
It's probably just a permissions problem.  Try writing a file as root.
```
sudo touch /media/extern/testfile
ls /media/extern/testfile
```
If that works then you can change permission with *chmod* and/or owner with *chown*.

---

### Post by tomstaehr on 2008-01-07
That did it!

Thanks a lot!

---

