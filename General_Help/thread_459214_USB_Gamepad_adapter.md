---
title: "USB Gamepad adapter"
date: 2007-05-30
forum: General Help
---

### Post by Shoeberto on 2007-05-30
I recently picked this gamepad adapter for Gamcube/PS2/Xbox controllers:
[http://www.futime.com/display/ft8d91_ps2_xbox_gc_to_pc-usb_converter.shtml](http://www.futime.com/display/ft8d91_ps2_xbox_gc_to_pc-usb_converter.shtml)
However, I don't seem to be able to get it to work.

I've looked around quite a bit.  Doing cat /dev/input/js0 returns some strange characters.

dmesg returns this following while plugging the device in:
```
[138161.344644] usb 2-2.1: new full speed USB device using uhci_hcd and address 3
[138161.454809] usb 2-2.1: configuration #1 chosen from 1 choice
[138161.463736] input: HID 19fa:8d91 as /class/input/input13
[138161.463820] input: USB HID v1.10 Joystick [HID 19fa:8d91] on usb-0000:00:10.1-2.1
[138161.469747] input: HID 19fa:8d91 as /class/input/input14
[138161.469831] input: USB HID v1.10 Joystick [HID 19fa:8d91] on usb-0000:00:10.1-2.1

```
Running jscalibrator returns no input and no programs recognize it as being there.  I've tried both PS1 and PS2 dual shock controllers.  I don't have my Gamecube controllers on hand to test with, nor do I own any Xbox controllers.

Any suggestions?

---

