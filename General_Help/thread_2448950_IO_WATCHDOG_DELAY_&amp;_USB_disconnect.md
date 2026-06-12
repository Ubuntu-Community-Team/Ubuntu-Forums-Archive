---
title: "IO_WATCHDOG_DELAY &amp; USB disconnect"
date: 2020-08-17
forum: General Help
---

### Post by Andrew_Welham on 2020-08-17
I'm seeing USB disconnect on multiple devices (disks) on multiple systems. (so not a faulty hardware issue)


The OS is Ubuntu 20.04 (fully patched) and the card is  Inateck KTU3FR-5O2U (yes I know it not supported, but used to work ok)

Under load I see 

Aug 16 22:18:02 server kernel: [45461.281464] usb 3-3.4: USB disconnect, device number 7
Aug 16 22:18:02 server kernel: [45461.375081] usb 3-3.4: new high-speed USB device number 8 using xhci_hcd
Aug 16 22:18:02 server kernel: [45461.489887] usb 3-3.4: New USB device found, idVendor=0bc2, idProduct=ab44, bcdDevice=48.85
Aug 16 22:18:02 server kernel: [45461.489892] usb 3-3.4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Aug 16 22:18:02 server kernel: [45461.489896] usb 3-3.4: Product: Backup+ Hub
Aug 16 22:18:02 server kernel: [45461.489899] usb 3-3.4: Manufacturer: Seagate
Aug 16 22:18:02 server kernel: [45461.489902] usb 3-3.4: SerialNumber: REMOVED
Aug 16 22:18:02 server kernel: [45461.492183] hub 3-3.4:1.0: USB hub found
Aug 16 22:18:02 server kernel: [45461.492469] hub 3-3.4:1.0: 3 ports detected

on multiple devices and servers , I have read this is typically a cable issue, but this is ruled out as it on multiple systems.

I have also ready that changing 


IO_WATCHDOG_DELAY

from 200 to a higher number can help.
Typically i use syscyt to make these changes but the entry does not appear to be in there ?

How can i make this change as a test is it a kernel recompile ?, and if so how does this work with patches from ubuntu ?


Many Thanks
Andrew

---

