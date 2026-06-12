---
title: "How to change permissions on floppy drive"
date: 2008-06-24
forum: General Help
---

### Post by paddy1 on 2008-06-24
I opened properties of floppy0 in file manager, and tried to change permissions for read/write, and it says "failed to change the file group nbi31x.nlm". I am refurbishing older computers and donating to those in need. How can I change permissions so that these children can save to a floppy?

---

### Post by molotov00 on 2008-06-24
You don't change permissions on a device.

You do change permissions to files/folders that are in a device, such as the contents of a disk.

Insert a disk then mount it and you'll be good to go.

---

### Post by paddy1 on 2008-06-24
I save the Abi word file as a microsoft doc file to user, and when sending to floppy, came up as a '0' kb file. I tried to open it in XP, and it wouldn't open. I am trying to erase files on the floppy, and it locks up the computer, and will not shut down or erase anything on the floppy

---

### Post by paddy1 on 2008-06-24
:lolflag:Thanks Molotov, but it looks like a bad install. Going o install Ubuto 8.04, as I have had no probem saving to a floppy with this distro. Again, thank you

---

### Post by LinuxRocks713 on 2008-08-18
> **paddy1 said:**
> I am trying to erase files on the floppy, and it locks up the computer, and will not shut down or erase anything on the floppy

dd if=/dev/zero of=/dev/fd0
mkfs.vfat /dev/fd0

---

