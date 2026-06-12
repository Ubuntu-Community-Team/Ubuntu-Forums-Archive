---
title: "connecting with Nexus 7"
date: 2013-01-30
forum: General Help
---

### Post by col48 on 2013-01-30
I'd like to be able to connect a Nexus 7 tablet (running Android 4.2.1) to my Lucid Lynx desktop in order to read from (and perhaps write to) it.

I've tried to follow the instructions (despite being written for 12.04) in [www.winters.org.nz/android-hints-and-tips-stuff/working-mtp-on-ubuntu](www.winters.org.nz/android-hints-and-tips-stuff/working-mtp-on-ubuntu) without success.

It has five sections:
_Configure FUSE_ went ok
_Compile and install go_mtp_: the first 3 steps were ok but the next failed and other two fell as a result.
_Create mount points_: (I only did the two Nexus7 lines)  ok
_Setup udev rules_: I created one line (vendor 18d1 product 4e41) and the file name starts 51 not 99.
restart udev: ok
_edit /etc/fstab_: I just added the first line

but I still can't see the Nexus in the file system.
It says it can't mount it.... bad superblock.

Has anyone any idea how to complete the operation?

---

### Post by col48 on 2013-02-02
bump?

---

