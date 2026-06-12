---
title: "HP RW6828 under Ubuntu"
date: 2008-02-07
forum: General Help
---

### Post by Pug505GR on 2008-02-07
Hi all,

I have done quite a search around and can't seem to find the answers I need, either here or on the WWW. 

Has anyone had any luck running a HP RW6828 phone/PDA under Linux. It's currently running Windows Mobile v5.0. Hooking it up to the laptop seems okay, but I'm unable to mount it or examine it. DMESG gives this:

> [31520.272000] usb 2-2: new full speed USB device using uhci_hcd and address 3
[31520.456000] usb 2-2: configuration #1 chosen from 1 choice
[31520.812000] usbcore: registered new interface driver usbserial
[31520.812000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[31520.812000] usbcore: registered new interface driver usbserial_generic
[31520.812000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial Driver core
[31520.832000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial support registered for PocketPC PDA
[31520.832000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/ipaq.c: USB PocketPC PDA driver v0.5
[31520.832000] ipaq 2-2:1.0: PocketPC PDA converter detected
[31520.836000] usb 2-2: PocketPC PDA converter now attached to ttyUSB0
[31520.836000] usbcore: registered new interface driver ipaq


So it appears that things are working as it should.

Are there any pointers on how I can make this work? I'm running Gutsy 7.10.

I'm also not that precious about Windoews Mobile either, so if I need to change the OS of the phone to Linux, so be it. Will probably be better anyway.

Thanks

Matt

---

