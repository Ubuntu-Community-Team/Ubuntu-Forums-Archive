---
title: "How do I rename a disk?"
date: 2007-04-22
forum: General Help
---

### Post by Foxman2k on 2007-04-22
My USB External hard drive,  when plugged in,  shows up as "disk" on the desktop.

It mounts under /media/usbdisk...

How can I rename it?  Right click and rename is greyed out...

Thanks.

---

### Post by dcstar on 2007-04-22
> **Foxman2k said:**
> My USB External hard drive,  when plugged in,  shows up as "disk" on the desktop.

It mounts under /media/usbdisk...

How can I rename it?  Right click and rename is greyed out...

Thanks.

It can be done in a terminal, but the exact command depends on which filesystem type is used.

---

### Post by Foxman2k on 2007-04-23
ext3...

What tools?  mkfs?

---

### Post by Foxman2k on 2007-04-23
-L new-volume-label
              Set  the  volume  label  for the filesystem to new-volume-label.
              The maximum length of the volume label is 16 bytes.

That appears to be what I want,  but can I run the mke2fs command without wiping the disk clean?

---

### Post by dominoEfkt on 2007-06-05
I think this is what you are looking for: [https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

---

