---
title: "[SOLVED] Make a media partition"
date: 2007-09-30
forum: General Help
---

### Post by PurposeOfReason on 2007-09-30
Would it be possible to make a partition where all is there, is music, pictures, and video while still being to access (read and write) them in Ubuntu? Right now, all my music is backed up onto another computer in case I do a clean install but I would prefer for these files to have their own partition.

---

### Post by x1a4 on 2007-09-30
Boot to the cd and use parted or resizefs.  Please note that not all file systems (reiserfs for instance) can be resized without data loss. And just to be on the safe side be sure to do a backup.

---

### Post by logos34 on 2007-09-30
Gparted (from livecd) would be easier:

system>admin>gnome partition editor

create a new ext3 partition in free space, or if root takes up entire disk you'll obviously have to shrink it first.

Reboot and [add partition to fstab]("http://www.psychocats.net/ubuntu/mountlinux") so it automounts at startup.

---

### Post by PurposeOfReason on 2007-09-30
Thanks, that worked better than I hoped.

---

