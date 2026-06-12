---
title: "unmount USB"
date: 2008-05-21
forum: General Help
---

### Post by kakyoism on 2008-05-21
I tend to disconnect my usb devices without unmounting them (windows behavior).

But then when i plug them back, they become sth else in /media,
say, if the before disconnected, the USB drive is called "USB_DISK"
then after it's plugged back on, the "USB_DISK" is still there,
but the new one is named "USB_DISK_" with an underscore.

THEN all my paths related to the original USB are messed up!!!!

When I try to delete the old "USB_DISK", it says, the device is busy.
The umount command doesn't work and no way to delete it. 

How am I supposed to solve this and get my re-connected device to 
fill in the original "USB_DISK"?

Thx!

---

### Post by bingoUV on 2008-05-21
Typing the following command tells you which device are currently mounted where.
```

mount

```

Use umount to unmount these. If it says device is in use, the following command kills all processes that are using the device.
```

sudo fuser -km /path/to/where/USB/disk/is/mounted

```

The command above could kill some processes that you need, but you don't know that they are using your USB device. Hopefully not catastrophic. If so, sorry.

---

