---
title: "Live CD persistent fstab changes not working"
date: 2017-03-28
forum: General Help
---

### Post by fakr00n on 2017-03-28
Hi,
I've created a custom live CD using the tutorial in: [https://help.ubuntu.com/community/MakeALiveCD/DVD/BootableFlashFromHarddiskInstall](https://help.ubuntu.com/community/MakeALiveCD/DVD/BootableFlashFromHarddiskInstall)

I want to add some new entries to fstab on my custom CD, so I did the following methods:
--------------------------------------------------------------------------------
METHOD 1:
- Mount the iso
- Unsquashfs
- Edit fstab
- mksquashfs and remake the iso
-----------------------------------------------------------------------------------
METHOD 2:
- Mount the iso
- Unsquashfs
- Edit /usr/share/initramfs-tools/scripts/casper-bottom/12fstab
- run update-initramfs -u -k KERNEL_VERSION
- Copy vmlinuz and initrd to the boot-cathalog on the CD (/boot)
- mksquashfs
- mkiso
--------------------------------------------------------------------------------------

None of the above methods works. My fstab additions do not show up :(


Does anyone have this problem or knows how to solve it?
My custom Live CD is based on Ubuntu Server 16.10

---

### Post by cariboo on 2017-03-28
Moved to General Help, as it has nothing to do with zesty.

---

