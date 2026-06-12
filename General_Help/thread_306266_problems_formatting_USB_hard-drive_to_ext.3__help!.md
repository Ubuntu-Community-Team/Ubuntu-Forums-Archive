---
title: "problems formatting USB hard-drive to ext.3  help!"
date: 2006-11-24
forum: General Help
---

### Post by syxbit on 2006-11-24
I've been trying to use gparted with NO success.
I load it from the terminal, and the output i get is (```
automount disabled
``` which is good, yet...). I then delete the partition on my HD, create a new one, and click apply.
problem is, my HD keeps getting remounted mid-format, and gives an error.
I've tried everything I can think of.
I've tried running gparted on a different Edgy box, and even from a live-boot CD.
I got some info on another forum to just run ```
fdisk
```
and then ```
sudo mke2fs -j /dev/sda1
```
it seems to work, but then when i load up gparted, it shows the following errors.
"Status: Not mounted" (yet, i'm able to read and write to it???)
and
"dumpe2fs no such file or directory while trying to open /dev/sdsa1"

could someone guide me to fixing this (and ridding myself of M$ FS's :) )

---

### Post by procras on 2006-11-24
If you are using GNOME
- Inactivate automatic settings for removable devices in System->Preferances->Removable Drives and media
Unset Mount removable drives when hot plugged
Unset Mount removalbe media when hot plugged
Unset Browse removable media when hot plugged
- Plug in your USB device
Now run the partition manager and do what you want.

- Go back and adjust Removable dricves and media settings to your fancy

---

### Post by syxbit on 2006-11-24
you're a genius!
thanks a bunch!

---

