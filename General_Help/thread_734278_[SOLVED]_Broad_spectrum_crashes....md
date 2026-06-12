---
title: "[SOLVED] Broad spectrum crashes..."
date: 2008-03-24
forum: General Help
---

### Post by buccaneere on 2008-03-24
By 'broad-spectrum', I mean crashes that happen when many different applications load. Even Gparted takes 4-5 minutes to complete a scan. I can't even zerofill the extra disks...

I had Edgy loaded long ago, which seemed to be problem-free. I tried to put Fed8 beside it, and then the problems started. I've tried everything, I think - IDE primary/secondary swap, master/slave swap, cable swap, etc.

chucknb@chucknb-desktop:~$ sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00022288

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9447    75882996   83  Linux
/dev/hda2            9448        9729     2265165    5  Extended
/dev/hda5            9448        9729     2265133+  82  Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/hdb doesn't contain a valid partition table

Disk /dev/hdd: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00023cc6

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        9729    78148161   8e  Linux LVM

Disk /dev/sda: 30.7 GB, 30735581184 bytes
255 heads, 63 sectors/track, 3736 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006ca0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          25      200781   83  Linux
/dev/sda2              26        3736    29808607+  8e  Linux LVM

The 30G HD is on a PCI IDE controller card, which wasn't a problem with Edgy.

I am completely lost. Am I missing a bios config setting? An HD jumper? Help!

---

### Post by buccaneere on 2008-05-11
The problem was caused by my KVM switch.

It is not a faulty switch, that I know of; it did switch function properly...

???

---

