---
title: "hard drive partitions naming"
date: 2014-02-17
forum: General Help
---

### Post by ieee488 on 2014-02-17
My hard drive originally had partitions for XP, Win7, and Ubuntu 12.04.
XP was /dev/sda1
Win7 was /dev/sda2
Ubuntu was /dev/sda5
swap was /dev/sda6


Can someone explain to me why there isn't a /dev/sda4?
Is it something I did when installing the OS?

I did something stupid and deleted XP partion using GParted.

Does it matter that there isn't a /dev/sda1 anymore?

---

### Post by deadflowr on 2014-02-17
> Can someone explain to me why there isn't a /dev/sda4?
Is it something I did when installing the OS?

Most likely it's an extended partition.
Or it never existed, is there a /dev/sda3?
And is that the extended partition?

If you ever have installed Ubuntu on a disk by itself, using the normal install tools( and not the something else partition tools) you would see the installer makes root /dev/sda1, then it makes /dev/sda2 an extended partition, and then swap is put into /dev/sda5.
It's always weird to see, has something to do with the first 4 partition number are set for primary partitions with extended partitions being considered primary. Partitions 5 and beyond are logical.
This of course is MBR(the old way) partitioning and not GPT(the new way).
Make sense.

Added, deleting the XP partition shouldn't affect Ubuntu, since it loads from UUID numbers and not the device number, in grub, in general.
Don't know what affect it has on Win7 though.

---

### Post by oldfred on 2014-02-17
If XP was first install and had boot flag, then all of Windows 7 boot files were in sda1, not in sda2. You have to use a Windows repair CD or flash drive to repair the Windows 7 install to add its boot files. And you have to add the boot flag first to sda2 to get Windows to know it is a bootable partition.

The partition table in the MBR only holds 4 (the primary) partitions. Any one can be the extended and all logicals start at sda5, but logicals are not in the MBR but in each partitions PBR. The PBR or partition boot sector has space for more boot code, which Windows and Lilo and maybe a few others use and space for a partition table. But logicals are just a linked list so each logical has one entry or a link to the next logical in its PBR partition table.

---

### Post by ieee488 on 2014-02-18
> **deadflowr said:**
> Most likely it's an extended partition.
Or it never existed, is there a /dev/sda3?

No, there isn't a /dev/sda3.
Not sure what happened to it.
The extended partition appears to be /dev/sda4.

I had followed a tutorial for triple-booting XP, Win7, and Ubuntu. 

I guess there doesn't need to be a /dev/sda1 for things to work.

---

