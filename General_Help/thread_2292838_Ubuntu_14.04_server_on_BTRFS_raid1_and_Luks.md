---
title: "Ubuntu 14.04 server on BTRFS raid1 and Luks"
date: 2015-08-31
forum: General Help
---

### Post by zidz on 2015-08-31
Hi,

I've installed my previous systems on a separate harddrive in the past and I've started to question myself why.
Say I have 4 harddrives and I want to install the system with only BTRFS in RAID1 setup so all drives will look like this.
First partition: /boot
Second partition: LUKS containing the root filesystem
Third partition: LUKS containing Swap.

My idea is that I'll install the system and all its filesystems with BTRFS on one harddrive and then, after the first boot, add the rest of the harddrives/paritions with 'btrfs device add' for /boot and for the LUKS encrypted root filesystem and convert to raid1.
After that I guess I have to install grub at all drives MBR and have to remember to do it on new drives when I replace drives?

Anyone that see any flaws in this setup, besides I have to write the password for the drives 8 times during boot ;-)

---

