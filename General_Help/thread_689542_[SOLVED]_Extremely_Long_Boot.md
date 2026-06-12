---
title: "[SOLVED] Extremely Long Boot"
date: 2008-02-06
forum: General Help
---

### Post by Nirevus on 2008-02-06
This has happened several times, the install is fairly fresh and hasn't been used much. There wasn't any big change before this started happening although I had recently installed Steam through WINE (it booted fine several times after this though.)

**[SIZE="4"]Boot log by time:[/SIZE]**
**0:00:** The computer shows the BIOS splash with the note "Press tab to show POST", I press this as soon as the boot shows up.
**0:38:** POST finally shows up and it appears that this is when it actually starts doing anything as it runs through all of POST now.
**0:46:** POST finishes and GRUB appears, GRUB works fine and goes through quickly
**0:49:** Ubuntu splash appears and loading bar begins to fill, it get three bars in and stops moving for the majority of the time the splash is around. This takes 1:34 seconds.
**2:23:** Ubuntu finishes loading and the login sound plays to a brown background. The desktop and bars finally appear at 2:51. 

Also, this did happen on the first two slow boot but happened on the last one, when it finally got in to the desktop I received a GNOME error about not being able to load anything, and the theme defaulted to the chunky grey theme.

**[SIZE="4"]Boot error log:[/SIZE]**
The point at which the splash bar stops moving for more than a minute the following errors are produced:
```
[   15.592000] PCI: Setting latency timer of device 0000:00:11.6 to 64
[   16.096000] ACPI: PCI interrupt for device 0000:00:11.6 disabled
[   16.096000] VIA 82xx Modem: probe of 0000:00:11.6 failed with error -13
[   16.096000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 24 (level, low) -> IRQ 22
[   16.096000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   16.096000] NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.19  Wed Sep 12 14:12:24 PDT 2007
[   16.096000] ACPI: PCI Interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 21
[   16.096000] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   22.620000] usb 5-5: device descriptor read/64, error -110
[   37.836000] usb 5-5: device descriptor read/64, error -110
[   38.052000] usb 5-5: new high speed USB device using ehci_hcd and address 6
[   53.164000] usb 5-5: device descriptor read/64, error -110
[   68.380000] usb 5-5: device descriptor read/64, error -110
[   68.596000] usb 5-5: new high speed USB device using ehci_hcd and address 7
[   73.616000] usb 5-5: device descriptor read/8, error -110
[   78.736000] usb 5-5: device descriptor read/8, error -110
[   78.952000] usb 5-5: new high speed USB device using ehci_hcd and address 8
[   83.972000] usb 5-5: device descriptor read/8, error -110
[   89.092000] usb 5-5: device descriptor read/8, error -110
[   89.436000] usbcore: registered new interface driver libusual
[   89.460000] Initializing USB Mass Storage driver...
[   89.564000] lp0: using parport0 (interrupt-driven).
```

**[SIZE="4"]Bootchart Log Image[/SIZE]**
Image attached for reference.

---

### Post by Nirevus on 2008-02-06
If anyone needs any additional information, ask and I'll post it up as soon as possible.

---

### Post by pieisgood4589 on 2008-02-06
Dunno... But I'll bump for more help!:lolflag:

---

### Post by Nirevus on 2008-02-06
Thanks, it's annoying me because I can't work out what would cause it as as far as I'm aware, nothing changed in between the time it happened and the time it didn't.

---

### Post by Nirevus on 2008-02-06
Issue was fixed by unplugging a USB flash drive.

---

