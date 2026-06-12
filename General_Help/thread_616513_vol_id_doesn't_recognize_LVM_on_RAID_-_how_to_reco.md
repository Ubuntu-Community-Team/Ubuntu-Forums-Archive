---
title: "vol_id doesn't recognize LVM on RAID - how to recover?"
date: 2007-11-18
forum: General Help
---

### Post by erifo on 2007-11-18
Hi!

After upgrading from 7.04 to 7.10 yesterday, my LVM LVs are not mounted during boot. Instead, boot is interrupted, and I have to run 'vgchange -a y', then 'mount -a' to get going.

The Physical Volume used in the LVM Volume Group resides on a md device (RAID1 software raid), /dev/md2. 

The problem is similar to, but not the same as the problem reported in [https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/87745](https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/87745)

I've debugged the udev scripts, and found that the cause of the problem, here:

sudo vol_id --export /dev/md2
/dev/md2: unknown volume type

For the udev scripts in the initrd to work, the output needs to contain a line on the form

ID_FS_FSTYPE=LVM1_member (or LVM2_member). As seen above, this doesn't happen on my system. For my other MD devices, ID_FS_FSTYPE is listed correctly.

As this is a system that has been around for a while, my guess is that somehow the disk labels on the md device has not been correctly written. How can I fix this?

---

