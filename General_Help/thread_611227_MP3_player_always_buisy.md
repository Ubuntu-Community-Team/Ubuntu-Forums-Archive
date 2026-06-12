---
title: "MP3 player always buisy"
date: 2007-11-12
forum: General Help
---

### Post by a7RoX on 2007-11-12
hi my usb player is always buisy, someone has an idea why?

everytime i want to copy and unmount i tells me that data needs to be written first


patrick@patrick:~$ sudo umount -t vfat /dev/sda /media/disk
umount: /dev/sda: not found
umount: /media/disk: device is busy
umount: /media/disk: device is busy
umount: /media/disk: device is busy

---

### Post by 1337455 10534 on 2007-11-12
open up the System-Administration-System Monitor.
Shut of all music related process (gtkpod, rythmbox, amarok,).
Hint> Look for Running processes.

Then, try unmounting it using the right-click-on-the-drive-and-select-eject method

---

