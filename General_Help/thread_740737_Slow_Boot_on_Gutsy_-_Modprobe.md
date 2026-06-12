---
title: "Slow Boot on Gutsy - Modprobe?"
date: 2008-03-31
forum: General Help
---

### Post by Playa1313 on 2008-03-31
Hello, I am experiencing quite a slow boot process (compared to normal)

I decided to use a bluetooth mouse again after I became tired of it slowing down my boot process.  It seems every time it is plugged in, my computer stalls at the "Loading Hardware Drivers" section of the boot.

I attached a picture of the bootchart before and after.. could someone please help?

Edit: Also, I see this a lot in the System Log Viewer, with long delays between:

```
Mar 31 00:21:30 Inspiron kernel: [   12.480000] input: USB HID v1.11 Keyboard [HID 045e:00bf] on usb-0000:00:13.5-7.4.2
Mar 31 00:21:30 Inspiron kernel: [   12.680000] usb 6-7.4.3: new full speed USB device using ehci_hcd and address 14
Mar 31 00:21:30 Inspiron kernel: [   27.752000] usb 6-7.4.3: device descriptor read/64, error -110
Mar 31 00:21:30 Inspiron kernel: [   42.928000] usb 6-7.4.3: device descriptor read/64, error -110
Mar 31 00:21:30 Inspiron kernel: [   43.104000] usb 6-7.4.3: new full speed USB device using ehci_hcd and address 15
Mar 31 00:21:30 Inspiron kernel: [   43.584000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Mar 31 00:21:30 Inspiron kernel: [   43.588000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Mar 31 00:21:30 Inspiron kernel: [   43.744000] Linux agpgart interface v0.102 (c) Dave Jones
```

Thank you!

---

### Post by Playa1313 on 2008-03-31
please, if anyone could help?

I tried upgrading to hardy last night.  Despite everything else working ok, I still have an extremely slow boot.

---

