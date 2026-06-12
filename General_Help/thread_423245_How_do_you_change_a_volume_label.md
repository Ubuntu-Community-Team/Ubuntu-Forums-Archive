---
title: "How do you change a volume label?"
date: 2007-04-25
forum: General Help
---

### Post by george_k on 2007-04-25
I have an external usb drive that when connected reports itself as 'disk' and gets mounted to /media/disk.

How can I change the name from 'disk' to say 'Backup'?

Thanks!

-George

---

### Post by rbmorse on 2007-04-25
What filesystem is on the drive?  If it's EXT2/3 the command is

e2label device <labelname>

---

### Post by strabes on 2007-04-25
What is the label command for a fat32 / fat16 USB thumb drive?

---

### Post by george_k on 2007-04-28
> What filesystem is on the drive? If it's EXT2/3 the command is

e2label device <labelname>


Thanks! That worked perfectly!

---

### Post by Slade Winstone on 2007-09-23
For FAT partitions, use mtools.  Check out:

[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

---

### Post by rhodry on 2007-09-23
> **rbmorse said:**
> What filesystem is on the drive?  If it's EXT2/3 the command is

e2label device <labelname>

I assume the drive should be unmounted before changing the name?

Rhodry.

---

### Post by yabbadabbadont on 2007-09-23
> **rhodry said:**
> I assume the drive should be unmounted before changing the name?

Rhodry.

Yes.

---

