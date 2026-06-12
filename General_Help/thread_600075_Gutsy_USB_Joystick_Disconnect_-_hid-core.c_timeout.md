---
title: "Gutsy: USB Joystick Disconnect - hid-core.c: timeout initializing reports"
date: 2007-11-01
forum: General Help
---

### Post by Berto on 2007-11-01
Hi all,

I just installed Gutsy, and am having a problem using a joystick for more than 10 seconds.  After I begin using it, the kernel thinks it disconnects, and then gives it a new address.

See below:

```
Nov  1 19:13:37 destroyal kernel: [727551.341007] usb 1-2: USB disconnect, address 10
Nov  1 19:13:37 destroyal kernel: [727551.580613] usb 1-2: new low speed USB device using uhci_hcd and address 11
Nov  1 19:13:37 destroyal kernel: [727551.760800] usb 1-2: configuration #1 chosen from 1 choice
Nov  1 19:13:39 destroyal kernel: [727553.385285] input: Logitech Inc. WingMan Gamepad as /class/input/input22
Nov  1 19:13:39 destroyal kernel: [727553.385330] input: USB HID v1.00 Joystick [Logitech Inc. WingMan Gamepad] on usb-0000:00:1d.0-2
Nov  1 19:13:39 destroyal kernel: [727553.577617] usb 1-2: USB disconnect, address 11
Nov  1 19:13:39 destroyal kernel: [727553.817231] usb 1-2: new low speed USB device using uhci_hcd and address 12
Nov  1 19:13:39 destroyal kernel: [727553.997386] usb 1-2: configuration #1 chosen from 1 choice
Nov  1 19:13:44 destroyal kernel: [727558.741095] input: Logitech Inc. WingMan Gamepad as /class/input/input23
Nov  1 19:13:44 destroyal kernel: [727558.741141] input: USB HID v1.00 Joystick [Logitech Inc. WingMan Gamepad] on usb-0000:00:1d.0-2
Nov  1 19:13:44 destroyal kernel: [727558.965455] usb 1-2: USB disconnect, address 12
Nov  1 19:13:45 destroyal kernel: [727559.205066] usb 1-2: new low speed USB device using uhci_hcd and address 13
Nov  1 19:13:45 destroyal kernel: [727559.381142] usb 1-2: configuration #1 chosen from 1 choice
Nov  1 19:13:55 destroyal kernel: [727569.389738] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: timeout initializing reports
Nov  1 19:13:55 destroyal kernel: [727569.389808] input: Logitech Inc. WingMan Gamepad as /class/input/input24
Nov  1 19:13:55 destroyal kernel: [727569.389855] input: USB HID v1.00 Joystick [Logitech Inc. WingMan Gamepad] on usb-0000:00:1d.0-2
```

I've tried running the application (zsnes) as root, and also did ln -s /dev/input/js0 /dev/js0 which hasn't helped.

It isn't just zsnes causing this.  If I go into my system settings and mess with the keyboard/mouse/joystick stuff, the joystick dies while using it there as well.

Any ideas on this?

Thanks!
berto

---

### Post by Berto on 2007-11-05
This is still happening, I just rebooted to see if that'd help.

Is there another kernel to try?

2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007

---

### Post by Berto on 2007-11-05
Update:  This happens even faster when using 2.6.20-16-generic #2 SMP Sun Sep 23 18:31:23 UTC 2007

This never happened in Edgy

---

### Post by Berto on 2007-11-08
LOL Aww I'm sorry guys, but I tried this on Windows and the same thing happened.  The controller is busted.  I have 2 identical controllers, I finally went into my storage closet to get the other one, and it works fine.

You can close this :(

---

