---
title: "can't boot, jfs file system"
date: 2007-01-27
forum: General Help
---

### Post by hanzomon4 on 2007-01-27
I got a problem my root jfs partition won't load grub. I had to boot into my feisty usb install to try and fix it but I've ran into a wall. 
When ever I run fsck.jfs /media/hda1 I get this error```
 sudo fsck.jfs /media/hda1/
fsck.jfs version 1.1.11, 05-Jun-2006
processing started: 1/27/2007 14.13.40
Using default parameter: -p
The current device is:  /media/hda1/
ujfs_rw_diskblocks: read 0 of 4096 bytes at offset 32768
ujfs_rw_diskblocks: read 0 of 4096 bytes at offset 61440
Superblock is corrupt and cannot be repaired 
since both primary and secondary copies are corrupt.  

 CANNOT CONTINUE.

```

This looks pretty ****** up, does anyone know how I can fix this without a reinstall?

---

### Post by hanzomon4 on 2007-01-27
Woot! Fixed it....

I booted into feisty opened a terminal and ran[FONT="Lucida Console"] mount -l[/FONT], this showed me that /dev/hda1 was actually /dev/sda1...
I ran [FONT="Lucida Console"]sudo fsck.jfs /dev/sda1[/FONT] and voilà fixed

---

### Post by mgrusin on 2007-05-09
Same here, I HATE that message from jfs.fsck!  Gives me a heart attack every time I see it.

Always jfs.fsck on the device ("/dev/md0") rather than the mount point ("media/mydisk").  Wish the code could notice that and not scare you so badly.

-MG.

---

