---
title: "SQUASHFS automount"
date: 2017-01-18
forum: General Help
---

### Post by Emmanuele on 2017-01-18
Dear all, I've tried an U3 usb key and now in my blkid find always such device /dev/loop0 "squashfs".

Is there any way to remove from my startup and devices once for all?

Thanks!

---

### Post by efflandt on 2017-01-19
If you are booting a live/install system from USB, I believe squashfs is the essential compressed root file system. Why do you want to remove it? I don't think the live/install system would run without it.

If you do not want to see "squashfs", do a regular installation to some storage device (a drive, 8 GB or larger USB flash memory or SD/microSD in USB reader, etc.). Although, most of the computers I have are older that use BIOS, so I am not quite sure how to set up a removable device to be bootable if you have a newer computer using UEFI.

---

