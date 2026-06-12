---
title: "odd problems"
date: 2008-06-04
forum: General Help
---

### Post by libertas on 2008-06-04
I just recently have modified my computer a lot by adding a bunch of 3d effects, alternate themes, new cursor, skydome, login screen etc. and after that and an upgrade (all done simultaneously) i was having some problems.

#1) touchpad doesn't work- it just won't work, the touch pad itself and the clicker buttons (pardon my english) don't work, 
i think the problem could possibly be the cursor i installed (Ecliz) i am rather partial to and would not like to get rid of it is there something i can do to fix the problem and keep the cursor, i have touchpad enabled by the way and it doesn't work i disabled, tried it, enabled it again and it still won't work

#2) doesn't start with power cord- when i start up the computer with the power cord in it will get to a certain point and then freeze, a chunk of the screen (which is a handprint loading screen) will move up a bit onto another bit, it doesn't move from there, computer freezes and i have to restart, take out the power cord (oh this is on a laptop by the way :P) and start it back up on battery power, it works fine like this...

never had problems like this before... i am welcome to suggestions :)

---

### Post by tamoneya on 2008-06-04
post the result of ```
dmesg |tail
```This will help us find any errors with the drivers on the touchpad.

---

### Post by libertas on 2008-06-05
[ 4174.220674] usb 1-2: USB disconnect, address 4
[37788.400922] usb 1-2: new low speed USB device using uhci_hcd and address 5
[37788.580817] usb 1-2: configuration #1 chosen from 1 choice
[37788.635201] input: Microsoft Microsoft Wireless Optical Mouse&#65533; 1.00 as /devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2:1.0/input/input10
[37788.664573] input,hidraw0: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Mouse&#65533; 1.00] on usb-0000:00:1d.0-2
[38233.626561] usb 1-2: USB disconnect, address 5
[86314.821683] usb 1-2: new low speed USB device using uhci_hcd and address 6
[86315.001567] usb 1-2: configuration #1 chosen from 1 choice
[86315.055961] input: Microsoft Microsoft Wireless Optical Mouse&#65533; 1.00 as /devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2:1.0/input/input11
[86315.085314] input,hidraw0: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Mouse&#65533; 1.00] on usb-0000:00:1d.0-2


//////
this is what i get, i think it can be told that i am using a wireless mouse, if thats any help and thank you for looking into this for me

---

### Post by libertas on 2008-06-07
that was with the touchpad ENABLED, this is the output from "dmesg |tail" when touchpad is DISABLED 

[   89.366238] usb 1-2: new low speed USB device using uhci_hcd and address 2
[   89.550440] usb 1-2: configuration #1 chosen from 1 choice
[   89.737975] usbcore: registered new interface driver hiddev
[   89.788554] input: Microsoft Microsoft Wireless Optical Mouse&#65533; 1.00 as /devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2:1.0/input/input9
[   89.809570] input,hidraw0: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Mouse&#65533; 1.00] on usb-0000:00:1d.0-2
[   89.809589] usbcore: registered new interface driver usbhid
[   89.809593] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   96.806438] ath0: no IPv6 routers present
[  100.612476] NET: Registered protocol family 17
[  120.113449] ath0: no IPv6 routers present

there are differences, i hope this helps :guitar:

---

### Post by libertas on 2008-06-12
even when i don't have the wireless mouse it it still comes up in dmesg | tail, i think that could possibly be the problem, there is nothing about my touch pad in it, is there some way that the job that the touchpad does could have been replaced by my wireless mouse? if so how could i fix this cause i would really like my touchpad back... so if anyone could suggest something?:confused:

---

