---
title: "fstab remount error?"
date: 2007-09-18
forum: General Help
---

### Post by ricardisimo on 2007-09-18
What does this error message mean? I believe it's in reference to the WinXP partition:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2 -- converted during upgrade to edgy
UUID=2ec78ab2-2fe6-4211-abbb-a22984e9648b /**[COLOR="Red"] ext3 defaults,errors=remount-ro 0 1[/COLOR]**
# /dev/hda5 -- converted during upgrade to edgy
UUID=e34f029b-7b4a-4def-badb-fa40de54314a none swap sw 0 0
UUID=bfe37834-a8da-4f43-81a7-c67928f282e0 /media/storage ext3 defaults 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```
Thanks in advance.

---

### Post by maybeway36 on 2007-09-18
That's not an error message. It's fine, actually.

---

