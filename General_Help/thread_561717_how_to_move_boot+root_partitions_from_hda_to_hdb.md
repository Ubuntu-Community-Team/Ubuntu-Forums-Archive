---
title: "how to move boot+root partitions from hda to hdb?"
date: 2007-09-27
forum: General Help
---

### Post by kosmos on 2007-09-27
I currently have my boot and root partitions on hda, and I would like to move them to hdb, and make them a little bigger at the same time. 

This is a server machine with no CD drive and usually does not have a monitor attached to it, so it's not as simple as booting from a live CD and copying files onto a new partition.

What would be the easiest and most foolproof way of transferring those filesystems to the new disk?

For example, will the following work:

- fdisk /dev/hdb to create new partitions with desired sizes
- mark the new hdb boot partition as bootable
- mkfs.ext3 the new boot and root partitions on hdb
- mount new boot partition on /mnt and cp -rp /boot to /mnt
- edit the new /mnt/grub/menu.lst to make sure we load kernel from hdb.
- mount new root partition on /mnt and cp -rp / to /mnt (will this work correctly for /proc and /dev ...?)
- edit the new /mnt/etc/fstab to mount new the hdb partitions for boot and root
- reboot

Thanks.

---

### Post by dcstar on 2007-09-28
> **kosmos said:**
> I currently have my boot and root partitions on hda, and I would like to move them to hdb, and make them a little bigger at the same time. 

This is a server machine with no CD drive and usually does not have a monitor attached to it, so it's not as simple as booting from a live CD and copying files onto a new partition.
..........

You can telnet in and use **partimage** to copy images from one drive to another, and then use **parted** or **resize2fs** to resize each partition on the new drive.

Do them one at a time so you have contiguous disk space for the resize.

You can copy your boot info over to the new drive with (substitute dev//hd? for you own hardware):
```
dd if=/dev/hda of=/dev/hdb bs=446 count=1
```

You can then manually edit /boot/grub/menu.lst on the new drive to changes the designations of the drives so they load the right partitions if you boot off the new drive.

---

