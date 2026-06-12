---
title: "RadioShark on Ubuntu"
date: 2014-06-02
forum: General Help
---

### Post by deamon_knight on 2014-06-02
I'm running Lubuntu 14.04 (upgraded from 13.10). I'm trying to move completely from an older XP box to Lubuntu. I'm using a RadioShark to record some AM radio that I can't otherwise stream. This device appears to be detected, lsusb shows:

```
Bus 004 Device 002: ID 077d:627a Griffin Technology Radio SHARK
```

and dmesg | tail shows

```
[153283.372042] usb 4-1: new full-speed USB device number 2 using uhci_hcd
[153283.574035] usb 4-1: New USB device found, idVendor=077d, idProduct=627a
[153283.574042] usb 4-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[153283.574046] usb 4-1: Product: RadioSHARK
[153283.574050] usb 4-1: Manufacturer: Griffin Technology, Inc.
[153283.909110] usbcore: registered new interface driver snd-usb-audio
[153283.925910] Linux video capture interface: v2.00
[153284.026798] usbcore: registered new interface driver radioshark

```

and a new radioshark audio device appears in my controls, but I'm not sure how to control the device. The manufacturers windows software has a program for Tuning, Timeshifting, and scheduling recordings, which is what I want to do in ubuntu.

Googling has a lot of older info
[HTML]http://javier.rodriguez.org.mx/index.php/2006/06/10/griffin-radio-shark-icecast2-on-debian-gnulinux[/HTML]

but I can't seem to build the shark.c, there is a missing hid.h (library?), and running precompiled binaries error out with:

```
error while loading shared libraries: libhid.so.0: cannot open shared object file: No such file or directory

```

Ultimately, these appear to be CLI utilities though.

Can anyone suggest a good GUI driven way to control this device?

Thanks

---

