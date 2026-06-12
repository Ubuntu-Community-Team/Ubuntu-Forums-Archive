---
title: "problems with USB connection,   disable xhci ?"
date: 2016-01-27
forum: General Help
---

### Post by todd_n on 2016-01-27
Hi all,

I'm running Ubuntu 14.04LTS on a Dell Inspiron 3647.

I've developed some problems with usb connections, like having to wait till
after I boot for my mouse to be plugged in, otherwise it won't connect.

But, recently I purchased a VPM-62489, which is an external enclosure,
to connect the drives I use with an Alesis HD24XR recorder.

The computer isn't detecting the drive, and is showing the following output in demsg:

[347141.570744] usb 3-3: Product: ViPower
[347146.566968] usb 3-3: can't set config #1, error -110
[347146.567154] usb 3-3: USB disconnect, device number 126
[347146.806301] usb 3-3: new high-speed USB device number 127 using xhci_hcd
[347151.826065] usb 3-3: unable to read config index 0 descriptor/start: -110
[347151.826071] usb 3-3: can't read configurations, error -110
[347152.121753] usb 3-3: new high-speed USB device number 4 using xhci_hcd
[347152.121772] usb 3-3: Device not responding to set address.
[347152.325735] usb 3-3: Device not responding to set address.
[347152.529423] usb 3-3: device not accepting address 4, error -71
[347152.825169] usb 3-3: new high-speed USB device number 6 using xhci_hcd
[347152.825191] usb 3-3: Device not responding to set address.
[347153.029010] usb 3-3: Device not responding to set address.
[347153.232807] usb 3-3: device not accepting address 6, error -71
[347153.528572] usb 3-3: new high-speed USB device number 9 using xhci_hcd
[347153.528590] usb 3-3: Device not responding to set address.
[347153.732426] usb 3-3: Device not responding to set address.
[347153.936239] usb 3-3: device not accepting address 9, error -71
[347154.231986] usb 3-3: new high-speed USB device number 11 using xhci_hcd
[347184.238522] usb 3-3: New USB device found, idVendor=067b, idProduct=3507
[347184.238524] usb 3-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3


After some research I think the problem may be xhci, which I should disable, and enable ehci.
But, there is no option in my BIOS to disable xhci.

Does anyone have any idea whether the direction of my solution is correct, and if so, how
I could disable xhci.

Thanks !

---

