---
title: "How to find out the file system of a LVM"
date: 2016-12-22
forum: General Help
---

### Post by xiaoleil on 2016-12-22
I have a logical volume at /dev/xvdk that I'd like to programatically detect if it's unformatted.  In the past, I've run "file -s" on physical devices and it'll return "data" if device is unformatted.  But because it's a LVM (I think?), it's giving me something like this, which isn't helpful.

> sudo file -sL /dev/xvdk
/dev/xvdk: LVM2 PV (Linux Logical Volume Manager), UUID: pmk0C-FABx-LAsZxB, size: 536870912000

I've tried other commands like "fdisk", "lsblk", "parted", "lvdisplay".  They all work on physical devices but not for LVM.

Suggestions?

---

### Post by kingneutron on 2016-12-22
--Have you tried " pvdisplay "?

---

