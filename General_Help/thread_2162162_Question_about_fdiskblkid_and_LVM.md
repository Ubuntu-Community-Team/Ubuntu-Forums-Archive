---
title: "Question about fdisk/blkid and LVM"
date: 2013-07-13
forum: General Help
---

### Post by CharlesA on 2013-07-13
Hi,

I reinstalled Debian 7 (with Proxmox) on my server and noticed that the physical device name I gave it shows up in fdisk (/dev/sda1) as well as the logical device name (/dev/mapper/Thor-Array). Is that normal, or did I miss a step when I created the LVM volumes?

blkid shows /dev/sda1 as LMV2_Member, which is correct, but I have a tenancy to use fstab to see the names (and sizes) of any usb disks attached to the machine.

I followed the howto here: [https://wiki.archlinux.org/index.php/LVM](https://wiki.archlinux.org/index.php/LVM)

Which basically meant these commands were run:
```
# Create physical volume
pvcreate /dev/sda1
# Create volume group
vgcreate Thor /dev/sda1
# Create logical volume
lvcreate -l +100%FREE Thor -n Array
# Format new logical drive
mkfs.ext4 -m 0 /dev/Thor/Array
```

Any help is appreciated.

---

