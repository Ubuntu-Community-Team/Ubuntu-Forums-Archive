---
title: "How change a file on a read only partition?"
date: 2015-02-11
forum: General Help
---

### Post by marco84 on 2015-02-11
I have a file where is defined the 'menu boot' for example:

> label live
  menu label ^Try Ubuntu without installing
  kernel /casper/vmlinuz
  append  file=/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --
But it is into a read only partition, i can't mount (remount) it with read/write privileges

How can i edit that?
I need to change only this file. I have more partition. It is into /dev/sdb1

---

### Post by Mark Phelps on 2015-02-11
What makes you believe the partition is read-only?

---

### Post by marco84 on 2015-02-11
The output of mount is clear even the edit of file...

---

### Post by ajgreeny on 2015-02-11
Is the partition a CD or DVD with an iso on it, or perhaps a live system's grub.cfg file or similar?
Where is the partition?

Tell us in more detail exactly what you have got, where the partition and the file are, and what you're wanting to do.

---

### Post by yancek on 2015-02-11
You would need to post the information requested above to get an answer.  It looks like a standard boot entry for syslinux on a Live CD/flash drive.  That would be an iso9660 filesystem which is read-only.  If it's something else, you need to indicate so.

---

### Post by marco84 on 2015-02-12
Ok, I have an usb with 3 partitions:
> /dev/sda1
/dev/sda2
/dev/sda3

i need to edit a file > /lib/live/mount/medium/isolinux/live.cfg

through > df i saw that > /dev/sda1  is mounted in > /lib/live/mount/medium

the partition is read-only, all file are only with read privileges.

---

### Post by ajgreeny on 2015-02-12
What filesystem is the USB formatted as; fat32, ntfs, ext#?

---

### Post by marco84 on 2015-02-12
/dev/sda1 is iso9660 (ro,noatime)
/dev/sda2 is vfat
/dev/sda3 is ext3

The problem is the first...

---

