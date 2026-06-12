---
title: "Digital camera won't stay connected"
date: 2007-03-25
forum: General Help
---

### Post by jordon on 2007-03-25
I'm using Edgy. When I connect my Sony DSC-P73 digital camera and turn it on, the camera is recognized, but before I can see the images' thumbnails appear in Nautilus, the USB connection cuts out and I get the warning about safely removing hardware. If there are a few photos, I can start transferring them to the computer, but the connection still dies. This also happens with Windows XP, but only infrequently, while in Edgy it happens every time. What's up?

---

### Post by dcstar on 2007-03-26
> **jordon said:**
> I'm using Edgy. When I connect my Sony DSC-P73 digital camera and turn it on, the camera is recognized, but before I can see the images' thumbnails appear in Nautilus, the USB connection cuts out and I get the warning about safely removing hardware. If there are a few photos, I can start transferring them to the computer, but the connection still dies. This also happens with Windows XP, but only infrequently, while in Edgy it happens every time. What's up?

You may have a faulty USB port - or the camera is drawing more current from the USB port than it is capable of supplying.

In a terminal, run:
```
dmesg
```
when you plug the camera in and post any relevant output.

---

### Post by jordon on 2007-03-26
Here's what I think is relevant.

```
[17179577.584000] usb usb3: configuration #1 chosen from 1 choice
[17179577.584000] hub 3-0:1.0: USB hub found
[17179577.584000] hub 3-0:1.0: 2 ports detected
[17179577.688000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 5
[17179577.688000] PCI: setting IRQ 5 as level-triggered
[17179577.688000] ACPI: PCI Interrupt 0000:00:0b.3[A] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
[17179577.688000] ehci_hcd 0000:00:0b.3: EHCI Host Controller
[17179577.688000] ehci_hcd 0000:00:0b.3: new USB bus registered, assigned bus number 4
[17179577.688000] ehci_hcd 0000:00:0b.3: debug port 1
[17179577.712000] ehci_hcd 0000:00:0b.3: irq 5, io mem 0xef004000
[17179577.712000] ehci_hcd 0000:00:0b.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179577.712000] usb usb4: configuration #1 chosen from 1 choice
[17179577.712000] hub 4-0:1.0: USB hub found
[17179577.712000] hub 4-0:1.0: 6 ports detected
[17179577.816000] ACPI: PCI Interrupt 0000:00:11.2[D] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179577.816000] uhci_hcd 0000:00:11.2: UHCI Host Controller
[17179577.816000] uhci_hcd 0000:00:11.2: new USB bus registered, assigned bus number 5
[17179577.816000] uhci_hcd 0000:00:11.2: irq 11, io base 0x0000e000
[17179577.816000] usb usb5: configuration #1 chosen from 1 choice
[17179577.816000] hub 5-0:1.0: USB hub found
[17179577.816000] hub 5-0:1.0: 2 ports detected
[17179577.920000] ACPI: PCI Interrupt 0000:00:11.3[D] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179577.920000] uhci_hcd 0000:00:11.3: UHCI Host Controller
[17179577.920000] uhci_hcd 0000:00:11.3: new USB bus registered, assigned bus number 6
[17179577.920000] uhci_hcd 0000:00:11.3: irq 11, io base 0x0000e400
[17179577.920000] usb usb6: configuration #1 chosen from 1 choice
[17179577.920000] hub 6-0:1.0: USB hub found
[17179577.920000] hub 6-0:1.0: 2 ports detected

[17179738.076000] usb 4-4: new high speed USB device using ehci_hcd and address 3
[17179738.208000] usb 4-4: configuration #1 chosen from 1 choice
[17179738.392000] usbcore: registered new driver libusual
[17179738.492000] SCSI subsystem initialized
[17179738.504000] Initializing USB Mass Storage driver...
[17179738.504000] scsi0 : SCSI emulation for USB Mass Storage devices
[17179738.504000] usbcore: registered new driver usb-storage
[17179738.504000] USB Mass Storage support registered.
[17179738.504000] usb-storage: device found at 3
[17179738.504000] usb-storage: waiting for device to settle before scanning
[17179743.504000] usb-storage: device scan complete
[17179743.504000]   Vendor: Sony      Model: Sony DSC          Rev: 5.00
[17179743.504000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179743.600000] SCSI device sda: 253696 512-byte hdwr sectors (130 MB)
[17179743.600000] sda: Write Protect is off
[17179743.600000] sda: Mode Sense: 00 00 00 00
[17179743.600000] sda: assuming drive cache: write through
[17179743.608000] SCSI device sda: 253696 512-byte hdwr sectors (130 MB)
[17179743.612000] sda: Write Protect is off
[17179743.612000] sda: Mode Sense: 00 00 00 00
[17179743.612000] sda: assuming drive cache: write through
[17179743.612000]  sda: sda1
[17179743.620000] sd 0:0:0:0: Attached scsi removable disk sda
[17179743.704000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179757.056000] usb 4-4: USB disconnect, address 3
[17179757.060000]  0:0:0:0: SCSI error: return code = 0x10000
[17179757.060000] end_request: I/O error, dev sda, sector 41
[17179757.060000] Buffer I/O error on device sda1, logical block 8
[17179757.060000]  0:0:0:0: rejecting I/O to dead device
[17179757.060000] Buffer I/O error on device sda1, logical block 9
[17179757.060000] Buffer I/O error on device sda1, logical block 10
[17179757.060000] Buffer I/O error on device sda1, logical block 11
[17179757.060000] Buffer I/O error on device sda1, logical block 12
[17179757.060000] Buffer I/O error on device sda1, logical block 13
[17179757.060000] Buffer I/O error on device sda1, logical block 14
[17179757.060000] Buffer I/O error on device sda1, logical block 15
[17179757.060000] Buffer I/O error on device sda1, logical block 16
[17179757.060000] Buffer I/O error on device sda1, logical block 17
[17179757.060000]  0:0:0:0: rejecting I/O to dead device
[17179757.064000]  0:0:0:0: rejecting I/O to dead device
[17179757.064000]  0:0:0:0: rejecting I/O to dead device
[17179757.064000]  0:0:0:0: rejecting I/O to dead device
[17179757.064000]  0:0:0:0: rejecting I/O to dead device
[17179757.064000] sda : READ CAPACITY failed.
[17179757.064000] sda : status=0, message=00, host=1, driver=00 
[17179757.064000] sda : sense not available. 
[17179757.064000]  0:0:0:0: rejecting I/O to dead device
[17179757.064000] sda: Write Protect is off
[17179757.064000] sda: Mode Sense: 00 00 00 00
[17179757.064000] sda: assuming drive cache: write through
[17179762.016000] usb 4-4: new high speed USB device using ehci_hcd and address 4
[17179762.148000] usb 4-4: configuration #1 chosen from 1 choice
[17179762.152000] scsi1 : SCSI emulation for USB Mass Storage devices
[17179762.152000] usb-storage: device found at 4
[17179762.152000] usb-storage: waiting for device to settle before scanning
[17179767.152000] usb-storage: device scan complete
[17179767.152000]   Vendor: Sony      Model: Sony DSC          Rev: 5.00
[17179767.152000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179767.156000] SCSI device sda: 253696 512-byte hdwr sectors (130 MB)
[17179767.160000] sda: Write Protect is off
[17179767.160000] sda: Mode Sense: 00 00 00 00
[17179767.160000] sda: assuming drive cache: write through
[17179767.168000] SCSI device sda: 253696 512-byte hdwr sectors (130 MB)
[17179767.172000] sda: Write Protect is off
[17179767.172000] sda: Mode Sense: 00 00 00 00
[17179767.172000] sda: assuming drive cache: write through
[17179767.172000]  sda: sda1
[17179767.176000] sd 1:0:0:0: Attached scsi removable disk sda
[17179767.176000] sd 1:0:0:0: Attached scsi generic sg0 type 0
[17179767.528000] usb 4-4: reset high speed USB device using ehci_hcd and address 4
[17179768.444000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17179798.668000] usb 4-4: reset high speed USB device using ehci_hcd and address 4

```

---

### Post by dcstar on 2007-03-26
> **jordon said:**
> Here's what I think is relevant.
..........

It could be power management shutting down the USB port after a certain time, you may want to see if you can disable anything like that which may be affecting it.

---

### Post by jordon on 2007-04-01
> **dcstar said:**
> It could be power management shutting down the USB port after a certain time, you may want to see if you can disable anything like that which may be affecting it.

It seems that I can keep the camera plugged in for as long as I want without any problems, but the camera disconnects when I try to view/transfer the files.

---

### Post by GoPool on 2007-06-03
I have the same problem, and It does appear to be a power issue. I just remove any other devices I have in the USB ports, and it works fine.

---

### Post by jordon on 2007-06-03
Apparently I just needed to use different ports due to a bad controller. But thanks for the suggestions, guys.

---

