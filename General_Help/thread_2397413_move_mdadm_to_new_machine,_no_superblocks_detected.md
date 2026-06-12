---
title: "move mdadm to new machine, no superblocks detected"
date: 2018-07-29
forum: General Help
---

### Post by rob0214 on 2018-07-29
Hi all,

I'm in the process of moving from an ancient Dell (32 bit) ubuntu server to an intel NUC.

Upgraded the Dell to 16.04, everything went well.  Copied the mdadm.conf over and hooked up the drives in the RAID 6 array, and now mdadm can't find the superblocks on any device.

Re-ran update-initramfs and update-grub too.

I'm using whole drive for each, and not partitions (i.e. sda vs. sda1).

And, I have LVM on top of the RAID, which I exported prior to shutdown.

Assembling fails, even force assembling fails.

Anyone have any suggestions?

I tried re-mounting on the old Dell, and it doesn't work.

---

