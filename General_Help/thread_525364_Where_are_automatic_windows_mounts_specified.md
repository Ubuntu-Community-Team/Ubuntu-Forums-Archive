---
title: "Where are automatic windows mounts specified?"
date: 2007-08-14
forum: General Help
---

### Post by Davorian on 2007-08-14
This isn't really a problem, so much as curiosity on my part.  I'm new to Ubuntu and I've just installed Feisty.  I noticed that it automatically mounts my Windows partitions and displays them on the Gnome desktop (which is nice).  Looking at my fstab file, however, I see this:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3 
UUID=b5bb7475-2a59-4f29-8a69-6ea76329da28 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6 
UUID=c653c905-cf38-44e3-8c29-81e825e9fd25 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

Best as I can tell, the windows partitions aren't listed there, so where are the automatic mounts specified?

---

### Post by renzokuken on 2007-08-14
try running the command ```
sudo fdisk -l
``` and see what info it spits out

---

