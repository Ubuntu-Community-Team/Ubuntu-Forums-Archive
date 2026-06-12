---
title: "USB Drive no longer showing on one USB port - U 18.04.1"
date: 2018-08-14
forum: General Help
---

### Post by carmichaelits on 2018-08-14
Hello,

I am having an interesting error with a USB drive I have. I have one USB 3.0 ( U3L ) port on the left side of the laptop here, and a further USB 3.0 ( U3R ) + USB 2.0 ( U2R ) on the right side.

I have 2 SanDisk Ultra ( SDU ) USB drives and One SanDisk Blade ( SDB ) USB drive.

So when I insert each SDU into U3L nothing shows up. Although, when I plug SDB into U3L it appears without any problems.

When I insert either of the two SDU's into U3R and U2R they are fine. Same result when plugging in SDB into U3R, U2R.

One SanDisk Ultra ( SDU ) is formatted for NTFS and the other is EXT4 so I don't think it is the file system...

Is there anyway to clear the 'inserted drive memory' on Ubuntu 18 - If there is such a thing?

Note: both drives have worked in the past in this slot.

Thank you in advanced,
David.

---

### Post by TheFu on 2018-08-14
Use lsusb to determine the USB device number, then use google to search for issues with that specific device number.

---

