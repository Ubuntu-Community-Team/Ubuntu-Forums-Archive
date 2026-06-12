---
title: "Checked, check forced?"
date: 2007-08-15
forum: General Help
---

### Post by Huesos on 2007-08-15
Once in a while during startup it says "sda1 has been mounted 30 times without being checked, check forced", then it does a scan or something and slowly boots everything up fine. This is annoying though, so how do I fix it?

---

### Post by darek1176 on 2007-08-15
Look at this tread, you will find the answer: [http://ubuntuforums.org/showthread.php?t=300477](http://ubuntuforums.org/showthread.php?t=300477)

---

### Post by ThrobbingBrain66 on 2007-08-15
Below is a copy of my fstab (/etc/fstab).  To disable the check on boot, find your root partition and go to the end of the line and change the '1' to '0'.  You can also stop it on any other partitions by doing the same thing.  That being said, it should only be happening every 30-40 boots and is a sanity check for your file system.  If it's happening more often, like very boot, you have bigger problems to worry about.
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=ab16367d-9390-4ecb-ae5c-e6b3dbf42397 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=89c4ec01-98ca-4635-959b-f3958fbd65df /home           ext3    defaults        0       2
# /dev/sda3
UUID=1a4684eb-a1ec-4188-90ad-139704ae0beb none            swap    sw              0       0
/dev/cdrom       /media/cdrom0   udf,iso9660 user,noauto     0       0
```

---

