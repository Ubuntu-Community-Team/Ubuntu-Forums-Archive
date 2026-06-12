---
title: "Fix boot record &amp; partitioning of disk drives for swap/mdadm"
date: 2013-12-20
forum: General Help
---

### Post by jens7 on 2013-12-20
Hi,

I've just installed Ubuntu Server 13.10 and during the installation i created a mdadm 2-disk RAID 1, with 2 partitions, one for swap and one for /, also i enabled the boot flag.
Ive acquired  more disks, first i grew to a 3-disk RAID 5, and right now its growing to a 6-disk RAID 6.

This is all good, except for when i reboot. It just hangs with a blinking "_", never boots unless i manually choose one of the 2 drives in the original RAID 1.
How can i fix the boot record on the drives ive added to the RAID after installation? And if a disk ever crashes, will mdadm be able to rebuild the boot data, or should i do this manually?

Another problem i have is that i cant figure out how to partition my drives like the 2 disks from the installation. Ive grown the RAID once and im now growing it again, using the whole disk, no partitions - when its done rebuilding i would like to correct this.

Please see the 2 attached images showing my drives and partitions.

---

### Post by jens7 on 2013-12-22
If i take a disk out of the RAID, repartition it and set both boot & raid flag on the disk (just like the disks during the ubuntu installation), would i be able to boot from that disk?

---

### Post by jens7 on 2013-12-24
I found out what to do.
Created 2 partitions, partition 1 ranging from 1 MB to 8000 MB, partition 2 ranging from 8000 MB to 2 TB
Set partition 1 with the raid flag (for md0 - swap raid) and set partition 2 with boot & raid flag (for boot and md1 raid).
Then i installed the bootdata.

sudo parted /dev/sde
parted> mklabel msdos
parted> mkpart primary ext4 1 8000
parted> mkpart primary ext4 8000 2000300
parted> toggle 1 raid
parted> toggle 2 raid
parted> toggle 2 boot
parted> quit
host# grub-install /dev/sde

Installation of grub-install should now finish without errors.

---

