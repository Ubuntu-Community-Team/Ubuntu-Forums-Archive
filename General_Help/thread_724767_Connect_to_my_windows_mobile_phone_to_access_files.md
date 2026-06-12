---
title: "Connect to my windows mobile phone to access files?"
date: 2008-03-14
forum: General Help
---

### Post by HunterK on 2008-03-14
Has anyone had luck connecting to their Windows Mobile2003 smartphone in Ubuntu? I hook it up and it begins to charge, but I do not see anything being mounted anywhere.

I do receive this in the system log which looks promising:
```

Mar 14 23:03:34 kenbuntu kernel: [ 2270.408885] usb 2-2: new full speed USB device using uhci_hcd and address 3
Mar 14 23:03:35 kenbuntu kernel: [ 2270.572595] usb 2-2: configuration #1 chosen from 3 choices
Mar 14 23:03:35 kenbuntu kernel: [ 2270.789203] usbcore: registered new interface driver usbserial
Mar 14 23:03:35 kenbuntu kernel: [ 2270.790518] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
Mar 14 23:03:35 kenbuntu kernel: [ 2270.791948] usbcore: registered new interface driver usbserial_generic
Mar 14 23:03:35 kenbuntu kernel: [ 2270.791954] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial Driver core
Mar 14 23:03:35 kenbuntu kernel: [ 2270.806546] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial support registered for PocketPC PDA
Mar 14 23:03:35 kenbuntu kernel: [ 2270.806551] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/ipaq.c: USB PocketPC PDA driver v0.5
Mar 14 23:03:35 kenbuntu kernel: [ 2270.807550] ipaq 2-2:1.0: PocketPC PDA converter detected
Mar 14 23:03:35 kenbuntu kernel: [ 2270.814393] usb 2-2: PocketPC PDA converter now attached to ttyUSB0
Mar 14 23:03:35 kenbuntu kernel: [ 2270.814806] usbcore: registered new interface driver ipaq
Mar 14 23:03:35 kenbuntu NetworkManager: <debug> [1205550215.409577] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_bb4_a51_noserial'). 
Mar 14 23:03:35 kenbuntu NetworkManager: <debug> [1205550215.410050] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_bb4_a51_noserial_if0'). 
Mar 14 23:03:35 kenbuntu NetworkManager: <debug> [1205550215.426270] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_bb4_a51_noserial_usbraw'). 
Mar 14 23:03:35 kenbuntu NetworkManager: <debug> [1205550215.437872] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_bb4_a51_noserial_if0_serial_usb_0')
```

I've seen alot of talk about synce, but honestly, I just want to access the files on it, not sync anything.  Any ideas?

Thanks!

---

### Post by HunterK on 2008-03-15
No one accesses their windows mobile cell phone in Gutsy? There's got to be a way.:confused:

---

### Post by Andre-D on 2008-05-02
you can run a Windowsmobile program called "USBdisk"
mine is v1.8 by Igor V Bozhko.

What it does, it to present your PocketPC look like a memory-stick to any computer.
Ubuntu thinks it's a memory-stick, and it works just fine.

no installation in Ubuntu /no drivers needed.

(-but I would still like Linux to talk directly to windowsmobile...)

---

### Post by beerguzzler on 2008-05-25
> **Andre-D said:**
> you can run a Windowsmobile program called "USBdisk"
mine is v1.8 by Igor V Bozhko.

What it does, it to present your PocketPC look like a memory-stick to any computer.
Ubuntu thinks it's a memory-stick, and it works just fine.

no installation in Ubuntu /no drivers needed.

(-but I would still like Linux to talk directly to windowsmobile...)

I've installed that on my HTC Hermes but Ubuntu doesn't recognise any additional memory devices when I plug it in. Can I ask how you connected yours?

---

### Post by beerguzzler on 2008-07-03
My own stupidity. I'd installed it to the phone rather than to the card.

Once I'd installed to the card Ubuntu picks up the card and you can copy files with no issues. 

Happy days!

---

