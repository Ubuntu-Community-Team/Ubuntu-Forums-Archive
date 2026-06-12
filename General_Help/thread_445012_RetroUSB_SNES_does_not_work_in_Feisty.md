---
title: "RetroUSB SNES does not work in Feisty"
date: 2007-05-15
forum: General Help
---

### Post by Nod51 on 2007-05-15
In Edgy I had no problem plugging my "RetroUSB.com SNES RetroPort" in and using ZSNES. I upgraded to Feisty, and now it only detects 4 of the 8 buttons (no start, select, B and Y) on my SNES controller.

- Using "jstest --normal /dev/input/js0" showed that it was not just ZSNES, but the kernel that was giving bad number of buttons back.

- dmesg after I plug it in says:

[ 7805.824000] usb 2-1: new low speed USB device using uhci_hcd and address 4
[ 7805.989000] usb 2-1: configuration #1 chosen from 1 choice
[ 7806.017000] input: RetroUSB.com SNES RetroPort as /class/input/input11
[ 7806.017000] input: USB HID v1.00 Gamepad [RetroUSB.com SNES RetroPort] on usb-0000:00:1d.1-1
[ 7806.133000] usbcore: registered new interface driver xpad
[ 7806.134000] drivers/usb/input/xpad.c: driver for Xbox controllers v0.1.6

This is not an XBox controller... Edgy does not do the XBox module loading, but the rest is the same.

- when I try to load the gamecon.ko module, I get:
FATAL: Error inserting gamecon (/lib/modules/2.6.20-15-lowlatency/kernel/drivers/input/joystick/gamecon.ko): Device or resource busy

I get the same error when I use the kernel that came with Feisty

- Tried loading analog.ko with "map=0,1,0,0,0,0" that some places suggested, no luck

Ideas, suggetsion? I am left playing FF3 using part pad, part keyboard.

Thanks!

---

### Post by prozacgod on 2007-05-15
I had a similar problem with another USB gamming device, it was supposed to be HID compatible but the xpad driver kept swallowing it up.  Not sure how to help but I suspect that the chip used in your adapter has a similar device ID to ones that the xpad driver claims to support - perhaps that chip is used on say a dance pad or a wheel or some similar device.

The only thing I can come up with would be to mv your xpad.ko  (in /lib/modules[current kernel version]/kernel/drivers/usb/input  to xpad.ko.old or something  (note: don't name it something.ko remove the .ko extension)

---

### Post by Nod51 on 2007-05-16
Thanks for the suggestion, I actually moved the module xpad.ko to my /root/ but it didn't help.

SOLUTION:
compile the 2.6.21 kernel following the how-to instructions at: [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

I use a laptop ATI 9000 so I didn't have to worry about the NVIDIA stuff, so a simple reboot and now 'everything' (so far) works including the joystick. I will have to worry about the NVIDIA stull on my desktop later this week.

Is this something that should be reported as a 'bug' for Ubuntu?

---

