---
title: "Ubuntu ext3 partition read only"
date: 2007-03-01
forum: General Help
---

### Post by yerokleoh on 2007-03-01
When I try to use mkdir or create a file in my ext3 partition it won't let me. Mkdir gives me "Permission denied" and the right click -> create file for my ext3 is greyed out. My usb flash stick is also read only(It's fat16). Anyone got a solution?

EDIT: Even after NTFS support the NTFS partition of my external USB drive is also read only.
File ->properties is greyed out.

---

### Post by taurus on 2007-03-01
What is the mount point of that ext3 partition?

You can only read from ntfs filesystem and if you want to write to it, then you need to install ntfs-3g driver first.

[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

---

