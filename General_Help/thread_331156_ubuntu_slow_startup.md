---
title: "ubuntu slow startup"
date: 2007-01-04
forum: General Help
---

### Post by glendavee on 2007-01-04
My Edgy installation takes a long time to boot - approx 2 mins. The splash screen appears, but the progress bar stalls about one third of the way along, and then the black screen appears showing results of file check (which are all ok). System then sits here for about 90 secs and then login screen appears. 
How can I track the boot process to find out where it is hanging?

---

### Post by tzulberti on 2007-01-04
You should check the file: /var/log/messages...

---

### Post by glendavee on 2007-01-05
/var/log/messages contents are :

Jan  5 16:33:51 david-desktop kernel: [17179580.456000] uhci_hcd 0000:00:1d.0: irq 217, io base 0x0000ff80
Jan  5 16:33:51 david-desktop kernel: [17179580.456000] usb usb1: configuration #1 chosen from 1 choice
Jan  5 16:33:51 david-desktop kernel: [17179580.456000] hub 1-0:1.0: USB hub found
Jan  5 16:33:51 david-desktop kernel: [17179580.456000] hub 1-0:1.0: 2 ports detected
Jan  5 16:33:51 david-desktop kernel: [17179580.560000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 22 (level, low) -> IRQ 225
Jan  5 16:33:51 david-desktop kernel: [17179580.560000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Jan  5 16:33:51 david-desktop kernel: [17179580.560000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Jan  5 16:33:51 david-desktop kernel: [17179580.560000] uhci_hcd 0000:00:1d.1: irq 225, io base 0x0000ff60
Jan  5 16:33:51 david-desktop kernel: [17179580.560000] usb usb2: configuration #1 chosen from 1 choice
Jan  5 16:33:51 david-desktop kernel: [17179580.560000] hub 2-0:1.0: USB hub found
Jan  5 16:33:51 david-desktop kernel: [17179580.560000] hub 2-0:1.0: 2 ports detected
Jan  5 16:33:51 david-desktop kernel: [17179580.664000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 233
Jan  5 16:33:51 david-desktop kernel: [17179580.664000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Jan  5 16:33:51 david-desktop kernel: [17179580.664000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Jan  5 16:33:51 david-desktop kernel: [17179580.664000] uhci_hcd 0000:00:1d.2: irq 233, io base 0x0000ff40
Jan  5 16:33:51 david-desktop kernel: [17179580.664000] usb usb3: configuration #1 chosen from 1 choice
Jan  5 16:33:51 david-desktop kernel: [17179580.664000] hub 3-0:1.0: USB hub found
Jan  5 16:33:51 david-desktop kernel: [17179580.664000] hub 3-0:1.0: 2 ports detected
Jan  5 16:33:51 david-desktop kernel: [17179580.768000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 23 (level, low) -> IRQ 50
Jan  5 16:33:51 david-desktop kernel: [17179580.768000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Jan  5 16:33:51 david-desktop kernel: [17179580.768000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
Jan  5 16:33:51 david-desktop kernel: [17179580.768000] uhci_hcd 0000:00:1d.3: irq 50, io base 0x0000ff20
Jan  5 16:33:51 david-desktop kernel: [17179580.768000] usb usb4: configuration #1 chosen from 1 choice
Jan  5 16:33:51 david-desktop kernel: [17179580.768000] hub 4-0:1.0: USB hub found
Jan  5 16:33:51 david-desktop kernel: [17179580.768000] hub 4-0:1.0: 2 ports detected
Jan  5 16:33:51 david-desktop kernel: [17179580.800000] usb 1-1: new low speed USB device using uhci_hcd and address 2
Jan  5 16:33:51 david-desktop kernel: [17179580.872000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 21 (level, low) -> IRQ 217
Jan  5 16:33:51 david-desktop kernel: [17179580.872000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Jan  5 16:33:51 david-desktop kernel: [17179580.872000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
Jan  5 16:33:51 david-desktop kernel: [17179580.872000] ehci_hcd 0000:00:1d.7: debug port 1
Jan  5 16:33:51 david-desktop kernel: [17179580.872000] ehci_hcd 0000:00:1d.7: irq 217, io mem 0xffa80800
Jan  5 16:33:51 david-desktop kernel: [17179580.876000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Jan  5 16:33:51 david-desktop kernel: [17179580.876000] usb usb5: configuration #1 chosen from 1 choice
Jan  5 16:33:51 david-desktop kernel: [17179580.876000] hub 5-0:1.0: USB hub found
Jan  5 16:33:51 david-desktop kernel: [17179580.876000] hub 5-0:1.0: 8 ports detected
Jan  5 16:33:51 david-desktop kernel: [17179580.980000] ACPI: PCI Interrupt 0000:03:01.2[C] -> GSI 19 (level, low) -> IRQ 58
Jan  5 16:33:51 david-desktop kernel: [17179580.980000] ehci_hcd 0000:03:01.2: EHCI Host Controller
Jan  5 16:33:51 david-desktop kernel: [17179580.980000] ehci_hcd 0000:03:01.2: new USB bus registered, assigned bus number 6
Jan  5 16:33:51 david-desktop kernel: [17179581.004000] ehci_hcd 0000:03:01.2: irq 58, io mem 0xdfcecf00
Jan  5 16:33:51 david-desktop kernel: [17179581.004000] ehci_hcd 0000:03:01.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Jan  5 16:33:51 david-desktop kernel: [17179581.004000] usb usb6: configuration #1 chosen from 1 choice
Jan  5 16:33:51 david-desktop kernel: [17179581.004000] hub 6-0:1.0: USB hub found
Jan  5 16:33:51 david-desktop kernel: [17179581.004000] hub 6-0:1.0: 5 ports detected
Jan  5 16:33:51 david-desktop kernel: [17179581.108000] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 17 (level, low) -> IRQ 177
Jan  5 16:33:51 david-desktop kernel: [17179581.108000] ohci_hcd 0000:03:01.0: OHCI Host Controller
Jan  5 16:33:51 david-desktop kernel: [17179581.108000] ohci_hcd 0000:03:01.0: new USB bus registered, assigned bus number 7
Jan  5 16:33:51 david-desktop kernel: [17179581.108000] ohci_hcd 0000:03:01.0: irq 177, io mem 0xdfced000
Jan  5 16:33:51 david-desktop kernel: [17179581.192000] usb usb7: configuration #1 chosen from 1 choice
Jan  5 16:33:51 david-desktop kernel: [17179581.192000] hub 7-0:1.0: USB hub found
Jan  5 16:33:51 david-desktop kernel: [17179581.192000] hub 7-0:1.0: 3 ports detected
Jan  5 16:33:51 david-desktop kernel: [17179581.296000] ACPI: PCI Interrupt 0000:03:01.1[B] -> GSI 18 (level, low) -> IRQ 233
Jan  5 16:33:51 david-desktop kernel: [17179581.296000] ohci_hcd 0000:03:01.1: OHCI Host Controller
Jan  5 16:33:51 david-desktop kernel: [17179581.296000] ohci_hcd 0000:03:01.1: new USB bus registered, assigned bus number 8
Jan  5 16:33:51 david-desktop kernel: [17179581.296000] ohci_hcd 0000:03:01.1: irq 233, io mem 0xdfcee000
Jan  5 16:33:51 david-desktop kernel: [17179581.380000] usb usb8: configuration #1 chosen from 1 choice
Jan  5 16:33:51 david-desktop kernel: [17179581.380000] hub 8-0:1.0: USB hub found
Jan  5 16:33:51 david-desktop kernel: [17179581.380000] hub 8-0:1.0: 2 ports detected
Jan  5 16:33:51 david-desktop kernel: [17179581.528000] Attempting manual resume
Jan  5 16:33:51 david-desktop kernel: [17179581.568000] kjournald starting.  Commit interval 5 seconds
Jan  5 16:33:51 david-desktop kernel: [17179581.568000] EXT3-fs: mounted filesystem with ordered data mode.
Jan  5 16:33:51 david-desktop kernel: [17179582.628000] usb 5-3: new high speed USB device using ehci_hcd and address 4
Jan  5 16:33:51 david-desktop kernel: [17179583.012000] usb 5-3: configuration #1 chosen from 1 choice
Jan  5 16:33:51 david-desktop kernel: [17179583.436000] usb 5-6: new high speed USB device using ehci_hcd and address 6
Jan  5 16:33:51 david-desktop kernel: [17179583.600000] usb 5-6: configuration #1 chosen from 1 choice
Jan  5 16:33:51 david-desktop kernel: [17179583.844000] usb 5-7: new high speed USB device using ehci_hcd and address 7
Jan  5 16:33:51 david-desktop kernel: [17179584.052000] usb 5-7: configuration #1 chosen from 1 choice
Jan  5 16:33:51 david-desktop kernel: [17179584.236000] ohci_hcd 0000:03:01.0: wakeup
Jan  5 16:33:51 david-desktop kernel: [17179584.556000] usb 1-1: new low speed USB device using uhci_hcd and address 4
Jan  5 16:33:51 david-desktop kernel: [17179584.728000] usb 1-1: configuration #1 chosen from 1 choice
Jan  5 16:33:51 david-desktop kernel: [17179584.972000] usb 1-2: new low speed USB device using uhci_hcd and address 5
Jan  5 16:33:51 david-desktop kernel: [17179585.144000] usb 1-2: configuration #1 chosen from 1 choice
Jan  5 16:33:51 david-desktop kernel: [17179585.404000] usb 2-2: new full speed USB device using uhci_hcd and address 2
Jan  5 16:33:51 david-desktop kernel: [17179585.592000] usb 2-2: configuration #1 chosen from 1 choice
Jan  5 16:33:51 david-desktop kernel: [17179585.900000] usb 7-3: new full speed USB device using ohci_hcd and address 2
Jan  5 16:33:51 david-desktop kernel: [17179586.124000] usb 7-3: configuration #1 chosen from 1 choice
Jan  5 16:33:51 david-desktop kernel: [17179588.560000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jan  5 16:33:51 david-desktop kernel: [17179588.568000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jan  5 16:33:51 david-desktop kernel: [17179588.592000] hw_random: RNG not detected
Jan  5 16:33:51 david-desktop kernel: [17179588.652000] Linux agpgart interface v0.101 (c) Dave Jones
Jan  5 16:33:51 david-desktop kernel: [17179588.664000] agpgart: Detected an Intel 915G Chipset.
Jan  5 16:33:51 david-desktop kernel: [17179588.668000] agpgart: Detected 7932K stolen memory.
Jan  5 16:33:51 david-desktop kernel: [17179588.684000] agpgart: AGP aperture is 256M @ 0xc0000000
Jan  5 16:33:51 david-desktop kernel: [17179589.008000] input: PC Speaker as /class/input/input0
Jan  5 16:33:51 david-desktop kernel: [17179589.332000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 169
Jan  5 16:33:51 david-desktop kernel: [17179589.416000] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jan  5 16:33:51 david-desktop kernel: [17179589.420000] sd 2:0:0:0: Attached scsi generic sg1 type 0
Jan  5 16:33:51 david-desktop kernel: [17179589.460000] usbcore: registered new driver hiddev
Jan  5 16:33:51 david-desktop kernel: [17179589.476000] input: Dell Dell USB Mouse as /class/input/input1
Jan  5 16:33:51 david-desktop kernel: [17179589.476000] input: USB HID v1.10 Mouse [Dell Dell USB Mouse] on usb-0000:00:1d.0-1
Jan  5 16:33:51 david-desktop kernel: [17179589.492000] input: Dell Dell USB Keyboard as /class/input/input2
Jan  5 16:33:51 david-desktop kernel: [17179589.492000] input: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:1d.0-2
Jan  5 16:33:51 david-desktop kernel: [17179589.492000] usbcore: registered new driver usbhid
Jan  5 16:33:51 david-desktop kernel: [17179589.492000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
Jan  5 16:33:51 david-desktop kernel: [17179589.524000] e100: Intel(R) PRO/100 Network Driver, 3.5.10-k2-NAPI
Jan  5 16:33:51 david-desktop kernel: [17179589.524000] e100: Copyright(c) 1999-2005 Intel Corporation
Jan  5 16:33:51 david-desktop kernel: [17179589.608000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x413C pid 0x5008
Jan  5 16:33:51 david-desktop kernel: [17179589.608000] usbcore: registered new driver usblp
Jan  5 16:33:51 david-desktop kernel: [17179589.608000] usbcore: registered new driver libusual
Jan  5 16:33:51 david-desktop kernel: [17179589.608000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
Jan  5 16:33:51 david-desktop kernel: [17179589.628000] ts: Compaq touchscreen protocol output
Jan  5 16:33:51 david-desktop kernel: [17179589.680000] Initializing USB Mass Storage driver...
Jan  5 16:33:51 david-desktop kernel: [17179589.680000] scsi4 : SCSI emulation for USB Mass Storage devices
Jan  5 16:33:51 david-desktop kernel: [17179589.680000] scsi5 : SCSI emulation for USB Mass Storage devices
Jan  5 16:33:51 david-desktop kernel: [17179589.680000] usbcore: registered new driver usb-storage
Jan  5 16:33:51 david-desktop kernel: [17179589.680000] USB Mass Storage support registered.
Jan  5 16:33:51 david-desktop kernel: [17179589.816000] ACPI: PCI Interrupt 0000:03:08.0[A] -> GSI 20 (level, low) -> IRQ 209
Jan  5 16:33:51 david-desktop kernel: [17179589.844000] e100: eth0: e100_probe: addr 0xdfcef000, irq 209, MAC addr 00:13:20:AC:74:FA
Jan  5 16:33:51 david-desktop kernel: [17179590.076000] lp: driver loaded but no devices found
Jan  5 16:33:51 david-desktop kernel: [17179590.100000] ndiswrapper version 1.31 loaded (preempt=no,smp=yes)
Jan  5 16:33:51 david-desktop kernel: [17179590.256000] usb 5-3: reset high speed USB device using ehci_hcd and address 4
Jan  5 16:33:51 david-desktop kernel: [17179590.464000] ndiswrapper: driver rt73 (Belkin Corporation,11/24/2005, 1.00.02.0000) loaded
Jan  5 16:33:51 david-desktop kernel: [17179591.012000] NET: Registered protocol family 17
Jan  5 16:33:51 david-desktop kernel: [17179591.308000] wlan0: ethernet device 00:17:3f:4a:6e:5f using NDIS driver: rt73, version: 0x0, NDIS version: 0x500, vendor: 'Belkin Wireless G Plus MIMO USB ', 050D:905B.F.conf
Jan  5 16:33:51 david-desktop kernel: [17179591.308000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
Jan  5 16:33:51 david-desktop kernel: [17179591.312000] usbcore: registered new driver ndiswrapper
Jan  5 16:33:51 david-desktop kernel: [17179591.340000] Adding 3004112k swap on /dev/sdb5.  Priority:-1 extents:1 across:3004112k
Jan  5 16:33:51 david-desktop kernel: [17179591.436000] EXT3 FS on sdb1, internal journal
Jan  5 16:33:51 david-desktop kernel: [17179591.616000] NTFS driver 2.1.27 [Flags: R/O MODULE].
Jan  5 16:33:51 david-desktop kernel: [17179591.652000] NTFS volume version 3.1.
Jan  5 16:33:51 david-desktop kernel: [17179594.684000]   Vendor: JetFlash  Model: TS256MJF2A        Rev: 1.00
Jan  5 16:33:51 david-desktop kernel: [17179594.684000]   Type:   Direct-Access                      ANSI SCSI revision: 02
Jan  5 16:33:51 david-desktop kernel: [17179594.688000] SCSI device sdc: 493000 512-byte hdwr sectors (252 MB)
Jan  5 16:33:51 david-desktop kernel: [17179594.688000] sdc: Write Protect is off
Jan  5 16:33:51 david-desktop kernel: [17179594.692000]   Vendor: TEAC      Model: USB   HS-CF Card  Rev: 4.00
Jan  5 16:33:51 david-desktop kernel: [17179594.692000]   Type:   Direct-Access                      ANSI SCSI revision: 00
Jan  5 16:33:51 david-desktop kernel: [17179594.692000] SCSI device sdc: 493000 512-byte hdwr sectors (252 MB)
Jan  5 16:33:51 david-desktop kernel: [17179594.692000] sdc: Write Protect is off
Jan  5 16:33:51 david-desktop kernel: [17179594.692000]  sdc: sdc1
Jan  5 16:33:51 david-desktop kernel: [17179594.696000] sd 4:0:0:0: Attached scsi removable disk sdc
Jan  5 16:33:51 david-desktop kernel: [17179594.696000] sd 4:0:0:0: Attached scsi generic sg2 type 0
Jan  5 16:33:51 david-desktop kernel: [17179594.696000]   Vendor: TEAC      Model: USB   HS-xD/SM    Rev: 4.00
Jan  5 16:33:51 david-desktop kernel: [17179594.696000]   Type:   Direct-Access                      ANSI SCSI revision: 00
Jan  5 16:33:51 david-desktop kernel: [17179594.700000]   Vendor: TEAC      Model: USB   HS-MS Card  Rev: 4.00
Jan  5 16:33:51 david-desktop kernel: [17179594.700000]   Type:   Direct-Access                      ANSI SCSI revision: 00
Jan  5 16:33:51 david-desktop kernel: [17179594.700000]   Vendor: TEAC      Model: USB   HS-SD Card  Rev: 4.00
Jan  5 16:33:51 david-desktop kernel: [17179594.700000]   Type:   Direct-Access                      ANSI SCSI revision: 00
Jan  5 16:33:51 david-desktop kernel: [17179594.716000] sd 5:0:0:0: Attached scsi removable disk sdd
Jan  5 16:33:51 david-desktop kernel: [17179594.716000] sd 5:0:0:0: Attached scsi generic sg3 type 0
Jan  5 16:33:51 david-desktop kernel: [17179594.728000] sd 5:0:0:1: Attached scsi removable disk sde
Jan  5 16:33:51 david-desktop kernel: [17179594.728000] sd 5:0:0:1: Attached scsi generic sg4 type 0
Jan  5 16:33:51 david-desktop kernel: [17179594.744000] sd 5:0:0:2: Attached scsi removable disk sdf
Jan  5 16:33:51 david-desktop kernel: [17179594.744000] sd 5:0:0:2: Attached scsi generic sg5 type 0
Jan  5 16:33:51 david-desktop kernel: [17179594.800000] sd 5:0:0:3: Attached scsi removable disk sdg
Jan  5 16:33:51 david-desktop kernel: [17179594.800000] sd 5:0:0:3: Attached scsi generic sg6 type 0
Jan  5 16:33:51 david-desktop kernel: [17179671.196000] NET: Registered protocol family 10
Jan  5 16:33:51 david-desktop kernel: [17179671.196000] lo: Disabled Privacy Extensions
Jan  5 16:33:51 david-desktop kernel: [17179671.196000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jan  5 16:33:51 david-desktop kernel: [17179671.196000] IPv6 over IPv4 tunneling driver
Jan  5 16:33:51 david-desktop kernel: [17179672.788000] ACPI: Power Button (FF) [PWRF]
Jan  5 16:33:51 david-desktop kernel: [17179672.788000] ACPI: Power Button (CM) [VBTN]
Jan  5 16:33:51 david-desktop kernel: [17179673.020000] pcc_acpi: loading...
Jan  5 16:33:51 david-desktop kernel: [17179673.928000] Symbol usb_register_driver is being used by a non-GPL module, which will not be allowed in the future
Jan  5 16:33:51 david-desktop kernel: [17179673.928000] Please see the file Documentation/feature-removal-schedule.txt in the kernel source tree for more details.
Jan  5 16:33:51 david-desktop kernel: [17179673.932000] Symbol usb_deregister is being used by a non-GPL module, which will not be allowed in the future
Jan  5 16:33:51 david-desktop kernel: [17179673.932000] Please see the file Documentation/feature-removal-schedule.txt in the kernel source tree for more details.
Jan  5 16:33:51 david-desktop kernel: [17179674.040000] usbcore: registered new driver driverloader
Jan  5 16:33:52 david-desktop hpiod: 1.6.9 accepting connections at 2208... 
Jan  5 16:33:52 david-desktop kernel: [17179675.400000] [drm] Initialized drm 1.0.1 20051102
Jan  5 16:33:52 david-desktop kernel: [17179675.404000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 169
Jan  5 16:33:52 david-desktop kernel: [17179675.404000] [drm] Initialized i915 1.5.0 20060119 on minor 0
Jan  5 16:33:52 david-desktop kernel: [17179675.828000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Jan  5 16:33:52 david-desktop kernel: [17179675.828000] apm: disabled - APM is not SMP safe.
Jan  5 16:33:56 david-desktop kernel: [17179679.780000] ip_tables: (C) 2000-2006 Netfilter Core Team
Jan  5 16:33:56 david-desktop kernel: [17179679.868000] Netfilter messages via NETLINK v0.30.
Jan  5 16:33:56 david-desktop kernel: [17179679.876000] ip_conntrack version 2.4 (8116 buckets, 64928 max) - 224 bytes per conntrack
Jan  5 16:33:57 david-desktop kernel: [17179680.556000] Bluetooth: Core ver 2.8
Jan  5 16:33:57 david-desktop kernel: [17179680.556000] NET: Registered protocol family 31
Jan  5 16:33:57 david-desktop kernel: [17179680.556000] Bluetooth: HCI device and connection manager initialized
Jan  5 16:33:57 david-desktop kernel: [17179680.556000] Bluetooth: HCI socket layer initialized
Jan  5 16:33:57 david-desktop kernel: [17179680.616000] Bluetooth: L2CAP ver 2.8
Jan  5 16:33:57 david-desktop kernel: [17179680.616000] Bluetooth: L2CAP socket layer initialized
Jan  5 16:33:57 david-desktop kernel: [17179680.652000] Bluetooth: RFCOMM socket layer initialized
Jan  5 16:33:57 david-desktop kernel: [17179680.652000] Bluetooth: RFCOMM TTY layer initialized
Jan  5 16:33:57 david-desktop kernel: [17179680.652000] Bluetooth: RFCOMM ver 1.7
Jan  5 16:34:06 david-desktop gconfd (david-5379): starting (version 2.16.0), pid 5379 user 'david'
Jan  5 16:34:06 david-desktop gconfd (david-5379): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jan  5 16:34:06 david-desktop gconfd (david-5379): Resolved address "xml:readwrite:/home/david/.gconf" to a writable configuration source at position 1
Jan  5 16:34:06 david-desktop gconfd (david-5379): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jan  5 16:34:06 david-desktop gconfd (david-5379): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jan  5 16:34:06 david-desktop gconfd (david-5379): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jan  5 16:34:11 david-desktop gconfd (david-5379): Resolved address "xml:readwrite:/home/david/.gconf" to a writable configuration source at position 0
Jan  5 16:39:29 david-desktop exiting on signal 15
Jan  5 16:39:30 david-desktop syslogd 1.4.1#18ubuntu6: restart.
david@david-desktop:~$ 

I don't understand much of this. First line is timed at 16.33.51, and three lines from end we are at 16.34.11 ie 20 secs later.The last 2 lines are times 5 mins later - is this significant??

---

### Post by stanthecaddy22 on 2007-01-06
I was having the exact same problem, but then when I changed to using NetworkManager to manage my connections it has stopped having problems. Are you by chance using wpa_supplicant for a wireless connection?

---

### Post by glendavee on 2007-01-06
Stanthecaddy22 - don't know! When I finally got my wireless USB card working, I used System>Administration>Networking graphical interface to configure. I assume this is Network Manager (the window is called Network Settings)?

---

### Post by stanthecaddy22 on 2007-01-06
no that is actually the built int gnome-network-admin tool, the NetworkManager is a seperate applet you have to install. Does your network use WPA encryption?

---

### Post by glendavee on 2007-01-06
No, I'm not using WPA encryption. If I install Network Manager, should I remove the gnome admin tool?

---

### Post by stanthecaddy22 on 2007-01-06
No you don't have to remove the other tool you just have to allow NetworkManager to have control. Follow these instructions:

[https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

Just make sure if you change any config files that you back up the working copies! Just in case it doesn't work out you need to be able to restore the working setup.

---

### Post by glendavee on 2007-01-06
Thanks - tried it, but Network Manger couldn't find the network connection. I disabled the connection on the gnome applet, logged out and logged back in, no success. I've gone back to the original gnome network settings.

---

### Post by saxsux on 2007-08-28
Sorry to bring such an old thread up, but I'm having the exact same problems; Ubuntu always hangs on Configuring Network Interfaces, and it's because of my wireless card. It only happens if I leave my wireless card switched off, or I'm not in range of my home network.
In older versions (Dapper and Edgy) I could just comment out everything for wlan0 in /etc/network/interfaces. This would solve the boot problem, but also stop GNOME network-admin from recognising my wireless card. I could just use network-manager to manage my connections instead.

But, in Feisty, if I change my /etc/network/interfaces, my wireless card isn't recognised at all; not even by network-manager. It still solves the problem, but it also means I can't use Wifi.

Does anybody know of a proper solution to this?

---

### Post by E_K on 2007-08-28
i have the same problem but i dont use wireless at the moment so i commented everything, but tonight i go to England, where i will be using wireless, i guess i will try network manager, ill let you know how it goes....

---

### Post by UI-Freak on 2007-08-29
Same problem here. Using WPA2.

---

### Post by E_K on 2007-08-30
well made it to England, and it hangs mega time in the middle of the loading bar on boot, and im using network manager, the wireless wont work here, i think because its one of the wannado live boxes, but i managed to connect to the neighbours haha

---

### Post by saxsux on 2007-09-09
BUMP

As I'm not getting an answer here, I've been bold and submitted a question to Launchpad:
[https://answers.launchpad.net/ubuntu/+question/13073](https://answers.launchpad.net/ubuntu/+question/13073)

Maybe it will get more attention there...

---

### Post by 1337455 10534 on 2007-09-09
Try turning of Bluetooth and Braile services.
System -> Administrator -> Services

---

