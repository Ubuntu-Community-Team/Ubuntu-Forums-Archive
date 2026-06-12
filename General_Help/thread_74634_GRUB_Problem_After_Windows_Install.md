---
title: "GRUB Problem After Windows Install"
date: 2005-10-12
forum: General Help
---

### Post by Unit #134679 on 2005-10-12
I have Ubuntu on one harddrive and Windows on another. I just recently had to reinstall Windows so I lost GRUB. When I popped in the Ubuntu CD and performed a 'rescue', I used sudo 'grub-install /dev/hda1' and received this error:

[INDENT]Due to a bug in xfs_freeze, the following command might produce a segmentation
fault when /boot/grub is not in an XFS filesystem. This error is harmless and
can be ignored.
xfs_freeze: specified file ["/boot/grub"] is not on an XFS filesystem
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)   /dev/hda
(hd1)   /dev/hdb[/INDENT]

When I try booting my Windows drive, it just flashes this and returns back to the options:

[INDENT]title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1[/INDENT]

---

### Post by Unit #134679 on 2005-10-12
No one?

---

