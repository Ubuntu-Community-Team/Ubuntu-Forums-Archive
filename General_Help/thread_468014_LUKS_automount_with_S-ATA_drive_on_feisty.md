---
title: "LUKS automount with S-ATA drive on feisty"
date: 2007-06-08
forum: General Help
---

### Post by cody_ on 2007-06-08
Hi,

automounting luks partitions on usb drives and memory sticks works great: a password dialog pops up and the filesystem is mounted.
But when i take the harddisk out of its usb case and connect it to the serial ata slot, it does not get mounted. it shows up as /dev/sda, just like with usb, but i have call gnome-mount myself on the console to mount it.
I guess there might be something wrong with hal that doesnt notify gnome about the new device or something...

any help appreciated!

---

