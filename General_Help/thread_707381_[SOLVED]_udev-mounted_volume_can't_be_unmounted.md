---
title: "[SOLVED] udev-mounted volume can't be unmounted"
date: 2008-02-25
forum: General Help
---

### Post by DieB on 2008-02-25
hallo,

I wrote a udev-rule to mount my usb-stick to a certain point, whenever it is attached. Well after a while i found out how to write it so it works.

_Problem:_
I can't unmount it via the right-click menu anymore, error-msg tells me: "Device to mount is not in /media/.hal-mtab so it is not mounted by HAL" 

Anyone any idea how to fix it?

Before anyone asks here my udev-rule:

> #mount
BUS=="usb", ACTION=="add", KERNEL=="sd?1", SYSFS{serial}=="QTSNKJS9", SYMLINK+="usbkey", MODE="0660" RUN+="/bin/mount /dev/usbkey /home/.../drob"
#unmount
BUS=="usb", ACTION=="remove", KERNEL=="sd?1", SYSFS{serial}=="QTSNKJS9", RUN="/bin/umount -l /home/...drob"

thx

---

