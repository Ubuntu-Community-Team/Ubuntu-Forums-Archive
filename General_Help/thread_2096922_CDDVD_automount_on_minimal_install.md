---
title: "CD/DVD automount on minimal install"
date: 2012-12-21
forum: General Help
---

### Post by rootatgardiners on 2012-12-21
Starting with a minimalCD install, I've loaded and have nearly everything running for converting old Windows boxes to dedicated rdesktop clients that boot directly to the RDP login. I've worked out everything so far except for automounting CD and DVDs. 

What files control this behavior? fstab and mtab don't seem to be the way to go. Are there additional packages that need to be installed.

installed packages:
xorg rdesktop alsa-utils openssh-server acpid usbmount

---

### Post by Bashing-om on 2012-12-21
rootatgardiners; Hi ! Welcome to the forum.

CD and DVD devices are mounted through the gvfs-fuse-daemon. 
It is not mounted ?
```
mount
```should have this similar line:
> gvfs-fuse-daemon on /home/sysop1/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=sysop1)[INDENT][INDENT]google will provide more info <== BDQ

[/INDENT][/INDENT]

---

### Post by rootatgardiners on 2012-12-22
Installing the gvfs-fuse requires 53 packages, 25Megs. Automounting a CD should not require so much. Using fstab and mount I can get the CD to mount. But I need this to work with no intervention by the user aside from inserting the disk.

---

### Post by ibjsb4 on 2012-12-22
> **rootatgardiners said:**
> Installing the gvfs-fuse requires 53 packages, 25Megs. Automounting a CD should not require so much. Using fstab and mount I can get the CD to mount. But I need this to work with no intervention by the user aside from inserting the disk.

I have these packages installed

[ATTACH]229002[/ATTACH]

And for ease of use dconf-editor

[ATTACH]229003[/ATTACH]

And automount working

---

