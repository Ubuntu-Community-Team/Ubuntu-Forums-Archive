---
title: "Disable  auto startup fsct"
date: 2015-08-14
forum: General Help
---

### Post by macey on 2015-08-14
Hello,
I am running 12.04 on an Odroid U3, I want to disable the auto fsct on startup. The system is hanging on startup due to a detected file error that I can't seem to fix or even  see  by running e2fsck manually (on a different system).
Help much appreciated.

---

### Post by macey on 2015-08-14
Further to this, I have now changed the fstab to this:-
[I]UUID=e139ce78-9841-40fe-8823-96a304a09859 / ext4   errors=remount-ro,noatime 0 0
[/I]

In an effort to stop the remount=ro (read only).
Why is my / partition being mounted read-only when it shouldn't even by checking it at startup?

[I]EXT4-fs (mmcblk0p2): mounted filesystem without journal. Opts: (null)
[    3.708748] usb 1-3.2: new low-speed USB device number 5 using s5p-ehci
[    3.824120] usb 1-3.2: New USB device found, idVendor=1c4f, idProduct=0002
[    3.828480] usb 1-3.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    3.835585] usb 1-3.2: Product: USB Keykoard
[    3.839903] usb 1-3.2: Manufacturer: USB
[    3.847215] input: USB USB Keykoard as /devices/platform/s5p-ehci/usb1/1-3/1-3.2/1-3.2:1.0/input/input0
[    3.853954] hid-generic 0003:1C4F:0002.0001: input,hidraw0: USB HID v1.10 Keyboard [USB USB Keykoard] on usb-s5p-ehci-3.2/input0
[    3.867779] input: USB USB Keykoard as /devices/platform/s5p-ehci/usb1/1-3/1-3.2/1-3.2:1.1/input/input1
[    3.874890] hid-generic 0003:1C4F:0002.0002: input,hidraw1: USB HID v1.10 Device [USB USB Keykoard] on usb-s5p-ehci-3.2/input1
[    4.268376] EXT4-fs (mmcblk0p2): re-mounted. Opts: errors=remount-ro[/I]

---

