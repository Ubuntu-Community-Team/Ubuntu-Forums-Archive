---
title: "USB Optical Mouse stops working after login"
date: 2016-04-27
forum: General Help
---

### Post by rockernaxo on 2016-04-27
Hi folks,

I just installed Ubuntu 16.04 two weeks ago and here it comes the first issue. Much as it is not critical, it is quite annoying.
I don't exactly know what happened in the previous days, but the mouse isn't working after login screen anymore. It could be an update or something that I installed.
In both Ubuntu's login screen and Windows, it works flawlessly, however, once Unity is loaded I can only move the pointer with the touchpad.

These are a couple of snaps from dsmeg, taken just after booting.
```

[    2.268147] usb 2-1.3: New USB device found, idVendor=15d9, idProduct=0a4c
[    2.268151] usb 2-1.3: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[    2.268153] usb 2-1.3: Product:  USB OPTICAL MOUSE
[    2.273391] hidraw: raw HID events driver (C) Jiri Kosina
[    2.277500] usbcore: registered new interface driver usbhid
[    2.277503] usbhid: USB HID core driver
[    2.279278] input:  USB OPTICAL MOUSE as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.0/0003:15D9:0A4C.0001/input/input8
[    2.279453] hid-generic 0003:15D9:0A4C.0001: input,hidraw0: USB HID v1.11 Mouse [ USB OPTICAL MOUSE] on usb-0000:00:1d.0-1.3/input0

```

As far as I can understand the USB is loaded OK and the prove is that it works momentaneously, but after a couple of seconds the following appears and it stops working.

```

[   83.465552] usb 2-1.3: input irq status -75 received
[   83.473496] usb 2-1.3: input irq status -75 received
[   83.481463] usb 2-1.3: input irq status -75 received
[   83.489548] usb 2-1.3: input irq status -75 received
[   83.545547] usb 2-1.3: input irq status -75 received
[   83.553542] usb 2-1.3: input irq status -75 received
[   83.561546] usb 2-1.3: input irq status -75 received
[   83.569400] usb 2-1.3: input irq status -75 received


```

Hope you can give some insights and help solve the problem.
Thanks in advance.

---

