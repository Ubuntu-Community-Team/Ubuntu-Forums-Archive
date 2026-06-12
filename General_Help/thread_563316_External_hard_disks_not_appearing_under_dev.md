---
title: "External hard disks not appearing under /dev?"
date: 2007-09-29
forum: General Help
---

### Post by dgr on 2007-09-29
Hi all,

I moved my VIA Epia M10000 (Kubuntu 7.04, 2.6.12-9) box and since then, external hard disks aren't showing up under /dev/sd___. Before the move, they showed up fine.

I've tried running modprobe for usbcore, ehci_hcd, usb_storage, scsi_mod and sd_mod but to no avail.

Any ideas what is going on here? Seems like a very odd puzzle!
Many thanks,
dgr

```

[4294675.076000] usbcore: registered new driver usbfs
[4294675.076000] usbcore: registered new driver hub
[4294675.079000] USB Universal Host Controller Interface driver v2.2
[4294675.079000] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[4294675.079000] uhci_hcd 0000:00:10.0: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
[4294675.141000] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[4294675.141000] uhci_hcd 0000:00:10.0: irq 11, io base 0x0000d400
[4294675.141000] hub 1-0:1.0: USB hub found
[4294675.141000] hub 1-0:1.0: 2 ports detected
[4294675.145000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 12
[4294675.145000] PCI: setting IRQ 12 as level-triggered
[4294675.145000] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [LNKB] -> GSI 12 (level, low) -> IRQ 12
[4294675.145000] uhci_hcd 0000:00:10.1: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#2)
[4294675.207000] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[4294675.207000] uhci_hcd 0000:00:10.1: irq 12, io base 0x0000d800
[4294675.207000] hub 2-0:1.0: USB hub found
[4294675.207000] hub 2-0:1.0: 2 ports detected
[4294675.211000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
[4294675.211000] PCI: setting IRQ 10 as level-triggered
[4294675.211000] ACPI: PCI Interrupt 0000:00:10.2[C] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[4294675.211000] uhci_hcd 0000:00:10.2: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#3)
[4294675.273000] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[4294675.273000] uhci_hcd 0000:00:10.2: irq 10, io base 0x0000dc00
[4294675.273000] hub 3-0:1.0: USB hub found
[4294675.273000] hub 3-0:1.0: 2 ports detected
[4294675.353000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 5
[4294675.353000] PCI: setting IRQ 5 as level-triggered
[4294675.353000] ACPI: PCI Interrupt 0000:00:10.3[D] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5
[4294675.353000] ehci_hcd 0000:00:10.3: VIA Technologies, Inc. USB 2.0
[4294675.354000] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[4294675.354000] ehci_hcd 0000:00:10.3: irq 5, io mem 0xde001000
[4294675.354000] ehci_hcd 0000:00:10.3: USB 2.0 initialized, EHCI 1.00, driver 10 Dec 2004
[4294675.354000] hub 4-0:1.0: USB hub found
[4294675.354000] hub 4-0:1.0: 6 ports detected
[4294675.472000] via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker
[4294675.472000] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[4294675.476000] eth0: VIA Rhine II at 0x1ec00, 00:40:63:c9:cd:3b, IRQ 11.
[4294675.477000] eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 45e1.
[4294675.962000] usb 4-1: new high speed USB device using ehci_hcd and address 2
[4294676.203000] usb 4-2: new high speed USB device using ehci_hcd and address 3
[4294676.279000] hub 4-2:1.0: USB hub found
[4294676.279000] hub 4-2:1.0: 4 ports detected
[4294676.547000] usb 4-3: new high speed USB device using ehci_hcd and address 4
[4294676.777000] hub 4-0:1.0: over-current change on port 5
[4294676.798000] hub 4-0:1.0: over-current change on port 6
[4294677.193000] usb 2-2: new low speed USB device using uhci_hcd and address 2
[4294677.461000] usb 4-2.1: new high speed USB device using ehci_hcd and address 6
[4294677.626000] usb 4-2.3: new high speed USB device using ehci_hcd and address 7
[4294677.790000] usb 4-2.4: new high speed USB device using ehci_hcd and address 8
[4294677.827000] usbcore: registered new driver hiddev
[4294677.848000] input: USB HID v1.10 Keyboard [2.4G USB RF KeyBoard] on usb-0000:00:10.1-2
[4294677.867000] input: USB HID v1.10 Mouse [2.4G USB RF KeyBoard] on usb-0000:00:10.1-2
[4294677.905000] input,hiddev96: USB HID v1.10 Device [2.4G USB RF KeyBoard] on usb-0000:00:10.1-2
[4294677.905000] usbcore: registered new driver usbhid
[4294677.905000] drivers/usb/input/hid-core.c: v2.01:USB HID core driver
[4294678.037000] SCSI subsystem initialized
[4294678.041000] Initializing USB Mass Storage driver...
[4294678.041000] scsi0 : SCSI emulation for USB Mass Storage devices
[4294678.041000] usb-storage: device found at 2
[4294678.041000] usb-storage: waiting for device to settle before scanning
[4294678.042000] scsi1 : SCSI emulation for USB Mass Storage devices
[4294678.042000] usb-storage: device found at 4
[4294678.042000] usb-storage: waiting for device to settle before scanning
[4294678.042000] scsi2 : SCSI emulation for USB Mass Storage devices
[4294678.042000] usb-storage: device found at 6
[4294678.042000] usb-storage: waiting for device to settle before scanning
[4294678.042000] scsi3 : SCSI emulation for USB Mass Storage devices
[4294678.042000] usb-storage: device found at 7
[4294678.042000] usb-storage: waiting for device to settle before scanning
[4294678.042000] scsi4 : SCSI emulation for USB Mass Storage devices
[4294678.043000] usb-storage: device found at 8
[4294678.043000] usb-storage: waiting for device to settle before scanning
[4294678.043000] usbcore: registered new driver usb-storage
[4294678.043000] USB Mass Storage support registered.
[4294678.847000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[4294678.847000] ACPI: Processor [CPU0] (supports 2 throttling states)
[4294679.017000] Attempting manual resume
[4294679.059000] swsusp: Suspend partition has wrong signature?
[4294679.112000] ReiserFS: hda1: found reiserfs format "3.6" with standard journal
[4294681.125000] ReiserFS: hda1: using ordered data mode
[4294681.172000] ReiserFS: hda1: journal params: device hda1, size 8192, journal first block 18, max trans len 1024, max batch
 900, max commit age 30, max trans age 30
[4294681.179000] ReiserFS: hda1: checking transaction log (hda1)
[4294681.423000] ReiserFS: hda1: replayed 3 transactions in 0 seconds
[4294681.991000] ReiserFS: hda1: Using r5 hash to sort names
[4294683.042000]   Vendor: SEAGATE   Model: ST3200822A        Rev: 3.01
[4294683.042000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[4294683.043000]   Vendor: WD        Model: 5000AAK External  Rev: 1.06
[4294683.043000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4294683.045000]   Vendor: HDS72505  Model: 0KLAT80           Rev: 0000
[4294683.045000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4294683.045000]   Vendor: ST350084  Model: 1A                Rev: 0000
[4294683.045000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4294683.045000] usb-storage: device scan complete
[4294683.046000]   Vendor: HDS72505  Model: 0KLAT80           Rev: 0000
[4294683.046000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4294683.048000] usb-storage: device scan complete
[4294683.052000] usb-storage: device scan complete
[4294683.086000] usb-storage: device scan complete
[4294683.086000] usb-storage: device scan complete
[4294683.537000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294684.958000] Adding 827308k swap on /dev/hda5.  Priority:-1 extents:1
[4294696.193000] parport: PnPBIOS parport detected.
[4294696.193000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[4294696.275000] lp0: using parport0 (interrupt-driven).
[4294696.308000] mice: PS/2 mouse device common for all mice
[4294696.364000] ieee1394: Initialized config rom entry `ip1394'
[4294696.369000] sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
[4294697.147000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[4294702.159000] NET: Registered protocol family 10
[4294702.160000] Disabled Privacy Extensions on device c02eb280(lo)
[4294702.160000] IPv6 over IPv4 tunneling driver
[4294704.434000] ACPI: Power Button (FF) [PWRF]
[4294704.434000] ACPI: Power Button (CM) [PWRB]
[4294704.559000] ibm_acpi: ec object not found
[4294739.470000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[4294740.598000] NET: Registered protocol family 17
[4294749.600000] eth0: no IPv6 routers present

```

---

