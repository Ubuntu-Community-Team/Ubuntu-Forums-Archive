---
title: "dvd burner not working"
date: 2008-04-27
forum: General Help
---

### Post by oddworld on 2008-04-27
My DVD burner is not working well in Ubuntu.
I am trying to burn a knoppix DVD with a correct md5sum but it is giving me an error about an exception not baing handled.

dmesg gives this: 
```
[   22.737804] ACPI: PCI Interrupt 0000:00:0f.1[A] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 19
[   22.737850] ACPI: PCI interrupt for device 0000:00:0f.1 disabled
[   22.739802] sata_via 0000:00:0f.0: version 2.3
[   22.739818] ACPI: PCI Interrupt 0000:00:0f.0[B] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 19
[   22.739843] sata_via 0000:00:0f.0: routed to hard irq line 11
[   22.740695] scsi0 : sata_via
[   22.740754] USB Universal Host Controller Interface driver v3.0
[   22.741924] scsi1 : sata_via
[   22.741949] ata1: SATA max UDMA/133 cmd 0xe000 ctl 0xe100 bmdma 0xe400 irq 19
[   22.741951] ata2: SATA max UDMA/133 cmd 0xe200 ctl 0xe300 bmdma 0xe408 irq 19
[   22.815699] FDC 0 is a post-1991 82077
[   22.943609] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   23.108580] ata1.00: ATA-7: Maxtor 6L200M0, BANC1G10, max UDMA/133
[   23.108584] ata1.00: 398297088 sectors, multi 16: LBA48 NCQ (not used)
[   23.124557] ata1.00: configured for UDMA/133
[   23.327158] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   23.518803] ata2.00: ATA-7: WDC WD5000AAKS-75TMA0, 12.01C01, max UDMA/133
[   23.518807] ata2.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   23.535025] ata2.00: configured for UDMA/133
[   23.536035] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 6L200M0   BANC PQ: 0 ANSI: 5
[   23.536341] scsi 1:0:0:0: Direct-Access     ATA      WDC WD5000AAKS-7 12.0 PQ: 0 ANSI: 5
[   23.536650] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 20
[   23.536659] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   23.536881] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   23.536907] uhci_hcd 0000:00:10.0: irq 20, io base 0x0000e700
[   23.537003] usb usb1: configuration #1 chosen from 1 choice
[   23.537020] hub 1-0:1.0: USB hub found
[   23.537023] hub 1-0:1.0: 2 ports detected
[   23.542783] Driver 'sd' needs updating - please use bus_type methods
[   23.542858] sd 0:0:0:0: [sda] 398297088 512-byte hardware sectors (203928 MB)
[   23.542867] sd 0:0:0:0: [sda] Write Protect is off
[   23.542869] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   23.542881] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   23.542918] sd 0:0:0:0: [sda] 398297088 512-byte hardware sectors (203928 MB)
[   23.542924] sd 0:0:0:0: [sda] Write Protect is off
[   23.542925] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   23.542935] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   23.542938]  sda: sda1 sda2 < sda5 >
[   23.583916] sd 0:0:0:0: [sda] Attached SCSI disk
[   23.583945] sd 1:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[   23.583952] sd 1:0:0:0: [sdb] Write Protect is off
[   23.583954] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   23.583964] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   23.583986] sd 1:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[   23.583992] sd 1:0:0:0: [sdb] Write Protect is off
[   23.583994] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   23.584004] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   23.584006]  sdb: sdb1 < sdb5 >
[   23.595198] sd 1:0:0:0: [sdb] Attached SCSI disk
[   23.599183] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   23.599199] sd 1:0:0:0: Attached scsi generic sg1 type 0
[   23.638894] ACPI: PCI Interrupt 0000:00:10.1[A] -> GSI 21 (level, low) -> IRQ 20
[   23.638904] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   23.638922] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   23.638942] uhci_hcd 0000:00:10.1: irq 20, io base 0x0000e800
[   23.639022] usb usb2: configuration #1 chosen from 1 choice
[   23.639040] hub 2-0:1.0: USB hub found
[   23.639044] hub 2-0:1.0: 2 ports detected
[   23.742742] ACPI: PCI Interrupt 0000:00:10.2[B] -> GSI 21 (level, low) -> IRQ 20
[   23.742752] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   23.742770] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[   23.742790] uhci_hcd 0000:00:10.2: irq 20, io base 0x0000e900
[   23.742871] usb usb3: configuration #1 chosen from 1 choice
[   23.742889] hub 3-0:1.0: USB hub found
[   23.742892] hub 3-0:1.0: 2 ports detected
[   23.796360] Attempting manual resume
[   23.796363] swsusp: Resume From Partition 8:5
[   23.796365] PM: Checking swsusp image.
[   23.796501] PM: Resume from disk failed.
[   23.817901] kjournald starting.  Commit interval 5 seconds
[   23.816998] EXT3-fs: mounted filesystem with ordered data mode.
[   23.846647] ACPI: PCI Interrupt 0000:00:10.3[B] -> GSI 21 (level, low) -> IRQ 20
[   23.846657] uhci_hcd 0000:00:10.3: UHCI Host Controller
[   23.846674] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[   23.846694] uhci_hcd 0000:00:10.3: irq 20, io base 0x0000ea00
[   23.846781] usb usb4: configuration #1 chosen from 1 choice
[   23.846799] hub 4-0:1.0: USB hub found
[   23.846803] hub 4-0:1.0: 2 ports detected
[   23.878498] usb 1-1: new low speed USB device using uhci_hcd and address 2
[   23.942511] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00508d0000d41ead]
[   23.950569] pata_via 0000:00:0f.1: version 0.3.3
[   23.950591] ACPI: PCI Interrupt 0000:00:0f.1[A] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 19
[   23.951085] scsi2 : pata_via
[   23.951121] scsi3 : pata_via
[   23.952096] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe600 irq 14
[   23.952099] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe608 irq 15
[   24.051424] usb 1-1: configuration #1 chosen from 1 choice
[   24.191597] ata3.01: ATA-7: ST3400633A, 3.AAH, max UDMA/100
[   24.191600] ata3.01: 781422768 sectors, multi 16: LBA48 
[   24.191610] ata3.01: limited to UDMA/33 due to 40-wire cable
[   24.282859] ata3.01: configured for UDMA/33
[   24.293825] usb 1-2: new low speed USB device using uhci_hcd and address 3
[   24.470886] usb 1-2: configuration #1 chosen from 1 choice
[   24.713593] usb 2-1: new full speed USB device using uhci_hcd and address 2
[   24.889502] usb 2-1: configuration #1 chosen from 1 choice
[   24.933607] ata4.00: ATAPI: _NEC DVD_RW ND-3550A, 1.04, max UDMA/33
[   24.933626] ata4.01: ATAPI: SONY    CD-RW  CRX216E, PD01, max UDMA/33
[   25.109275] ata4.00: configured for UDMA/33
[   25.133090] usb 2-2: new low speed USB device using uhci_hcd and address 3
[   25.277037] ata4.01: configured for UDMA/33
[   25.277107] scsi 2:0:1:0: Direct-Access     ATA      ST3400633A       3.AA PQ: 0 ANSI: 5
[   25.277162] sd 2:0:1:0: [sdc] 781422768 512-byte hardware sectors (400088 MB)
[   25.277171] sd 2:0:1:0: [sdc] Write Protect is off
[   25.277173] sd 2:0:1:0: [sdc] Mode Sense: 00 3a 00 00
[   25.277184] sd 2:0:1:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   25.277218] sd 2:0:1:0: [sdc] 781422768 512-byte hardware sectors (400088 MB)
[   25.277224] sd 2:0:1:0: [sdc] Write Protect is off
[   25.277226] sd 2:0:1:0: [sdc] Mode Sense: 00 3a 00 00
[   25.277236] sd 2:0:1:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   25.277239]  sdc: sdc1
[   25.293361] sd 2:0:1:0: [sdc] Attached SCSI disk
[   25.293388] sd 2:0:1:0: Attached scsi generic sg2 type 0
[   25.294755] scsi 3:0:0:0: CD-ROM            _NEC     DVD_RW ND-3550A  1.04 PQ: 0 ANSI: 5
[   25.294801] scsi 3:0:0:0: Attached scsi generic sg3 type 5
[   25.305736] scsi 3:0:1:0: CD-ROM            SONY     CD-RW  CRX216E   PD01 PQ: 0 ANSI: 5
[   25.305775] scsi 3:0:1:0: Attached scsi generic sg4 type 5
[   25.306740] ACPI: PCI Interrupt 0000:00:10.4[C] -> GSI 21 (level, low) -> IRQ 20
[   25.306754] ehci_hcd 0000:00:10.4: EHCI Host Controller
[   25.306778] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[   25.306812] ehci_hcd 0000:00:10.4: irq 20, io mem 0xf302a000
[   25.316783] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   25.316859] usb usb5: configuration #1 chosen from 1 choice
[   25.316875] hub 5-0:1.0: USB hub found
[   25.316880] hub 5-0:1.0: 8 ports detected
[   25.316879] usb 2-2: unable to read config index 0 descriptor/all
[   25.316883] usb 2-2: can't read configurations, error -71
[   25.884212] usb 2-1: USB disconnect, address 2
[   26.012054] usb 1-1: USB disconnect, address 2
[   26.139901] usb 1-2: USB disconnect, address 3
[   27.298512] usb 1-1: new low speed USB device using uhci_hcd and address 4
[   27.469978] usb 1-1: configuration #1 chosen from 1 choice
[   27.709026] usb 1-2: new low speed USB device using uhci_hcd and address 5
[   27.885434] usb 1-2: configuration #1 chosen from 1 choice
[   28.124533] usb 2-1: new full speed USB device using uhci_hcd and address 5
[   28.298086] usb 2-1: configuration #1 chosen from 1 choice
[   28.541044] usb 2-2: new low speed USB device using uhci_hcd and address 6
[   28.823395] usb 2-2: configuration #1 chosen from 1 choice
[   30.147084] Linux agpgart interface v0.102
[   30.162975] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   30.183098] agpgart: Detected AGP bridge 0
[   30.191299] agpgart: AGP aperture is 256M @ 0xd0000000
[   30.201118] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   30.255093] input: Power Button (FF) as /devices/virtual/input/input1
[   30.278889] ACPI: Power Button (FF) [PWRF]
[   30.278970] input: Power Button (CM) as /devices/virtual/input/input2
[   30.310851] ACPI: Power Button (CM) [PWRB]
[   30.759477] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 18 (level, low) -> IRQ 21
[   30.787558] phy0: Selected rate control algorithm 'simple'
[   30.860066] nvidia: module license 'NVIDIA' taints kernel.
[   31.249654] udev: renamed network interface eth1 to eth0
[   31.251391] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 22
[   31.251583] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[   31.299621] udev: renamed network interface eth0_rename to eth1
[   31.514975] usblp0: USB Bidirectional printer dev 5 if 0 alt 0 proto 2 vid 0x04A9 pid 0x10A0
[   31.514993] usbcore: registered new interface driver usblp
[   31.573107] usbcore: registered new interface driver hiddev
[   31.633446] Driver 'sr' needs updating - please use bus_type methods
[   31.635192] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[   31.635197] Uniform CD-ROM driver Revision: 3.20
[   31.635241] sr 3:0:0:0: Attached scsi CD-ROM sr0
[   31.711229] sr1: scsi3-mmc drive: 24x/48x writer cd/rw xa/form2 cdda tray
[   31.711284] sr 3:0:1:0: Attached scsi CD-ROM sr1
[   31.730442] hiddev96hidraw0: USB HID v1.10 Device [CPS  CP 1500C] on usb-0000:00:10.0-1
[   31.746531] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:10.0/usb1/1-2/1-2:1.0/input/input3
[   31.773258] input,hidraw1: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:10.0-2
[   31.781797] ACPI: PCI Interrupt 0000:00:0c.0[A] -> GSI 20 (level, low) -> IRQ 19
[   31.781814] snd-ca0106: Model 100a Rev 00000000 Serial 100a1102
[   31.822623] input: Chicony Saitek Eclipse Keyboard as /devices/pci0000:00/0000:00:10.1/usb2/2-2/2-2:1.0/input/input4
[   31.833881] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   31.841176] input,hidraw2: USB HID v1.11 Keyboard [Chicony Saitek Eclipse Keyboard] on usb-0000:00:10.1-2
[   31.946348] input: Chicony Saitek Eclipse Keyboard as /devices/pci0000:00/0000:00:10.1/usb2/2-2/2-2:1.1/input/input6
[   31.969057] input,hiddev97,hidraw3: USB HID v1.11 Device [Chicony Saitek Eclipse Keyboard] on usb-0000:00:10.1-2
[   31.969073] usbcore: registered new interface driver usbhid
[   31.969076] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   32.061449] parport_pc 00:0a: reported by Plug and Play ACPI
[   32.061500] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   33.741865] lp0: using parport0 (interrupt-driven).
[   33.817286] Adding 6072528k swap on /dev/sda5.  Priority:-1 extents:1 across:6072528k
[   34.354353] EXT3 FS on sda1, internal journal
[   36.608697] ip_tables: (C) 2000-2006 Netfilter Core Team
[   36.926890] No dock devices found.
[   37.254344] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ processors (2 cpu cores) (version 2.20.00)
[   37.255168] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x8
[   37.255171] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0xa
[   37.255173] powernow-k8:    2 : fid 0x2 (1000 MHz), vid 0x12
[   38.082861] NET: Registered protocol family 10
[   38.083064] lo: Disabled Privacy Extensions
[   38.340719] apm: BIOS not found.
[   38.489655] ppdev: user-space parallel port driver
[   38.593502] audit(1209310256.923:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5071 profile="/usr/sbin/cupsd" namespace="default"
[   39.886766] cdrom: This disc doesn't have any tracks I recognize!
[   39.956004] Velocity is AUTO mode
[   39.961334] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   40.049633] Bluetooth: Core ver 2.11
[   40.050096] NET: Registered protocol family 31
[   40.050101] Bluetooth: HCI device and connection manager initialized
[   40.050105] Bluetooth: HCI socket layer initialized
[   40.062037] Bluetooth: L2CAP ver 2.9
[   40.062041] Bluetooth: L2CAP socket layer initialized
[   40.062234] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   40.100531] Bluetooth: RFCOMM socket layer initialized
[   40.100548] Bluetooth: RFCOMM TTY layer initialized
[   40.100549] Bluetooth: RFCOMM ver 1.8
[   40.105084] r8169: eth1: link down
[   40.106115] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   40.319190] Clocksource tsc unstable (delta = -213231301 ns)
[   40.900281] eth0: Link auto-negotiation speed 100M bps full duplex
[   40.901388] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   41.233446] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[   41.233455] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   41.233496] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   42.567605] NET: Registered protocol family 17
[   49.676861] eth0: no IPv6 routers present
[  152.146067] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  152.146077] ata4.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[  152.146078]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[  152.146080]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[  152.146082] ata4.00: status: { DRDY }
[  152.146095] ata4: soft resetting link
[  152.557938] ata4.00: configured for UDMA/33
[  152.643856] ata4.01: configured for UDMA/33
[  152.643865] ata4: EH complete
[  169.490989] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  169.490999] ata4.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[  169.491000]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[  169.491001]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[  169.491004] ata4.00: status: { DRDY }
[  169.491017] ata4: soft resetting link
[  170.305948] ata4.00: configured for UDMA/33
[  170.477782] ata4.01: configured for UDMA/33
[  170.477794] ata4: EH complete
[  191.049876] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  191.049888] ata4.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[  191.049890]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[  191.049891]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[  191.049894] ata4.00: status: { DRDY }
[  191.049907] ata4: soft resetting link
[  191.461758] ata4.00: configured for UDMA/33
[  191.547663] ata4.01: configured for UDMA/33
[  191.547674] ata4: EH complete
[  209.492896] ata4.00: limiting speed to UDMA/25:PIO4
[  209.492904] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  209.492912] ata4.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[  209.492913]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[  209.492914]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[  209.492917] ata4.00: status: { DRDY }
[  209.492934] ata4: soft resetting link
[  210.316585] ata4.00: configured for UDMA/25
[  210.488413] ata4.01: configured for UDMA/33
[  210.488431] ata4: EH complete
[  229.831430] ata4.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  229.831440] ata4.01: cmd a0/00:00:00:00:00/00:00:00:00:00/b0 tag 0
[  229.831442]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[  229.831443]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[  229.831446] ata4.01: status: { DRDY }
[  229.831459] ata4: soft resetting link
[  230.243307] ata4.00: configured for UDMA/25
[  230.329228] ata4.01: configured for UDMA/33
[  230.329238] ata4: EH complete
[  250.644358] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  250.644368] ata4.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[  250.644370]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[  250.644371]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[  250.644373] ata4.00: status: { DRDY }
[  250.644386] ata4: soft resetting link
[  251.056293] ata4.00: configured for UDMA/25
[  251.142163] ata4.01: configured for UDMA/33
[  251.142175] ata4: EH complete
[  268.855890] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  268.855901] ata4.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[  268.855902]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[  268.855903]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[  268.855906] ata4.00: status: { DRDY }
[  268.855920] ata4: soft resetting link
[  269.267764] ata4.00: configured for UDMA/25
[  269.353697] ata4.01: configured for UDMA/33
[  269.353708] ata4: EH complete
[  284.343302] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  284.343312] ata4.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[  284.343314]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[  284.343315]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[  284.343318] ata4.00: status: { DRDY }
[  284.343331] ata4: soft resetting link
[  284.755170] ata4.00: configured for UDMA/25
[  284.841091] ata4.01: configured for UDMA/33
[  284.841103] ata4: EH complete
[  299.830704] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  299.830714] ata4.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[  299.830715]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[  299.830716]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[  299.830719] ata4.00: status: { DRDY }
[  299.830732] ata4: soft resetting link
[  300.242582] ata4.00: configured for UDMA/25
[  300.328497] ata4.01: configured for UDMA/33
[  300.328512] ata4: EH complete
[  300.328553] sr0: CDROM (ioctl) error, command: Test Unit Ready 00 00 00 00 00 00
[  300.328560] sr: Sense Key : Aborted Command [current] [descriptor]
[  300.328564] sr: Add. Sense: No additional sense information
[  315.318107] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  315.318117] ata4.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[  315.318119]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[  315.318120]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[  315.318123] ata4.00: status: { DRDY }
[  315.318136] ata4: soft resetting link
[  315.729977] ata4.00: configured for UDMA/25
[  315.815896] ata4.01: configured for UDMA/33
[  315.815905] ata4: EH complete
[  330.805515] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  330.805526] ata4.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[  330.805527]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[  330.805528]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[  330.805531] ata4.00: status: { DRDY }
[  330.805544] ata4: soft resetting link
[  331.217389] ata4.00: configured for UDMA/25
[  331.303309] ata4.01: configured for UDMA/33
[  331.303320] ata4: EH complete
[  346.292920] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  346.292930] ata4.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[  346.292932]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[  346.292933]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[  346.292935] ata4.00: status: { DRDY }
[  346.292948] ata4: soft resetting link
[  346.704796] ata4.00: configured for UDMA/25
[  346.790718] ata4.01: configured for UDMA/33
[  346.790729] ata4: EH complete
[  361.780325] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  361.780336] ata4.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[  361.780337]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[  361.780338]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[  361.780341] ata4.00: status: { DRDY }
[  361.780354] ata4: soft resetting link
[  362.192202] ata4.00: configured for UDMA/25
[  362.278123] ata4.01: configured for UDMA/33
[  362.278138] ata4: EH complete
[  362.278170] sr0: CDROM (ioctl) error, command: Test Unit Ready 00 00 00 00 00 00
[  362.278177] sr: Sense Key : Aborted Command [current] [descriptor]
[  362.278180] sr: Add. Sense: No additional sense information
[  377.267729] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  377.267739] ata4.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[  377.267741]          cdb 1b 00 00 00 03 00 00 00  00 00 00 00 00 00 00 00
[  377.267742]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[  377.267745] ata4.00: status: { DRDY }
[  377.267757] ata4: soft resetting link
[  377.679604] ata4.00: configured for UDMA/25
[  377.765525] ata4.01: configured for UDMA/33
[  377.765537] ata4: EH complete
[  392.755133] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  392.755143] ata4.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[  392.755144]          cdb 1b 00 00 00 03 00 00 00  00 00 00 00 00 00 00 00
[  392.755145]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[  392.755150] ata4.00: status: { DRDY }
[  392.755164] ata4: soft resetting link
[  393.167008] ata4.00: configured for UDMA/25
[  393.252928] ata4.01: configured for UDMA/33
[  393.252940] ata4: EH complete
[  410.466749] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  410.466759] ata4.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[  410.466761]          cdb 1b 00 00 00 03 00 00 00  00 00 00 00 00 00 00 00
[  410.466762]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[  410.466765] ata4.00: status: { DRDY }
[  410.466778] ata4: soft resetting link
[  411.121492] ata4.00: configured for UDMA/25
[  411.293252] ata4.01: configured for UDMA/33
[  411.293264] ata4: EH complete
[  428.873793] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  428.873805] ata4.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[  428.873806]          cdb 1b 00 00 00 03 00 00 00  00 00 00 00 00 00 00 00
[  428.873807]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[  428.873810] ata4.00: status: { DRDY }
[  428.873829] ata4: soft resetting link
[  429.454761] ata4.00: configured for UDMA/25
[  429.540642] ata4.01: configured for UDMA/33
[  429.540657] ata4: EH complete
[  429.540698] sr0: CDROM (ioctl) error, command: Start/Stop Unit 1b 00 00 00 03 00
[  429.540705] sr: Sense Key : Aborted Command [current] [descriptor]
[  429.540709] sr: Add. Sense: No additional sense information
[  447.493950] ata4.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  447.493959] ata4.01: cmd a0/00:00:00:00:00/00:00:00:00:00/b0 tag 0
[  447.493961]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[  447.493962]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[  447.493965] ata4.01: status: { DRDY }
[  447.493978] ata4: soft resetting link
[  447.905617] ata4.00: configured for UDMA/25
[  447.991494] ata4.01: configured for UDMA/33
[  447.991505] ata4: EH complete
[  452.985442] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  452.985452] ata4.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[  452.985453]          cdb 1e 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[  452.985455]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[  452.985458] ata4.00: status: { DRDY }
[  452.985471] ata4: soft resetting link
[  453.397193] ata4.00: configured for UDMA/25
[  453.482989] ata4.01: configured for UDMA/33
[  453.483000] ata4: EH complete
[  458.476937] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  458.476946] ata4.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[  458.476947]          cdb 1e 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[  458.476949]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[  458.476951] ata4.00: status: { DRDY }
[  458.476964] ata4: soft resetting link
[  458.888620] ata4.00: configured for UDMA/25
[  458.974492] ata4.01: configured for UDMA/33
[  458.974502] ata4: EH complete
[  463.968432] ata4.00: limiting speed to PIO4
[  463.968438] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  463.968445] ata4.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[  463.968446]          cdb 1e 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[  463.968447]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[  463.968450] ata4.00: status: { DRDY }
[  463.968463] ata4: soft resetting link
[  464.380101] ata4.00: configured for PIO4
[  464.465978] ata4.01: configured for UDMA/33
[  464.465988] ata4: EH complete
[  469.459925] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  469.459935] ata4.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[  469.459936]          cdb 1e 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[  469.459938]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[  469.459941] ata4.00: status: { DRDY }
[  469.459954] ata4: soft resetting link
[  469.871594] ata4.00: configured for PIO4
[  469.957473] ata4.01: configured for UDMA/33
[  469.957484] ata4: EH complete
[  474.951419] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  474.951430] ata4.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[  474.951431]          cdb 1e 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[  474.951432]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[  474.951435] ata4.00: status: { DRDY }
[  474.951448] ata4: soft resetting link
[  475.363092] ata4.00: configured for PIO4
[  475.449005] ata4.01: configured for UDMA/33
[  475.449016] ata4: EH complete
[  480.442914] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  480.442923] ata4.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[  480.442925]          cdb 1e 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[  480.442926]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[  480.442929] ata4.00: status: { DRDY }
[  480.442941] ata4: soft resetting link
[  480.854632] ata4.00: configured for PIO4
[  480.940460] ata4.01: configured for UDMA/33
[  480.940474] ata4: EH complete
[  480.940517] sr 3:0:0:0: ioctl_internal_command return code = 8000002
[  480.940520]    : Sense Key : Aborted Command [current] [descriptor]
[  480.940523]    : Add. Sense: No additional sense information
[  496.542634] ata4.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  496.542643] ata4.01: cmd a0/00:00:00:00:00/00:00:00:00:00/b0 tag 0
[  496.542644]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[  496.542646]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[  496.542649] ata4.01: status: { DRDY }
[  496.542662] ata4: soft resetting link
[  496.954303] ata4.00: configured for PIO4
[  497.040180] ata4.01: configured for UDMA/33
[  497.040191] ata4: EH complete
[  502.034129] ata4.00: limiting speed to PIO3
[  502.034135] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  502.034143] ata4.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[  502.034144]          cdb 1e 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[  502.034145]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[  502.034148] ata4.00: status: { DRDY }
[  502.034161] ata4: soft resetting link
[  502.445799] ata4.00: configured for PIO3
[  502.531676] ata4.01: configured for UDMA/33
[  502.531687] ata4: EH complete
[  507.934428] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  507.934439] ata4.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[  507.934440]          cdb 1e 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[  507.934441]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[  507.934445] ata4.00: status: { DRDY }
[  507.934463] ata4: soft resetting link
[  508.717632] ata4.00: configured for PIO3
[  508.872189] ata4.01: configured for UDMA/33
[  508.872200] ata4: EH complete
[  514.130995] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  514.131004] ata4.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[  514.131005]          cdb 1e 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[  514.131006]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[  514.131009] ata4.00: status: { DRDY }
[  514.131022] ata4: soft resetting link
[  514.542667] ata4.00: configured for PIO3
[  514.628542] ata4.01: configured for UDMA/33
[  514.628553] ata4: EH complete
[  521.725696] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  521.725708] ata4.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[  521.725710]          cdb 1e 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[  521.725711]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[  521.725714] ata4.00: status: { DRDY }
[  521.725733] ata4: soft resetting link
[  522.548575] ata4.00: configured for PIO3
[  522.720311] ata4.01: configured for UDMA/33
[  522.720325] ata4: EH complete
[  529.321945] ata4.00: limiting speed to PIO0
[  529.321951] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  529.321959] ata4.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[  529.321960]          cdb 1e 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[  529.321961]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[  529.321963] ata4.00: status: { DRDY }
[  529.321977] ata4: soft resetting link
[  529.733669] ata4.00: configured for PIO0
[  529.819499] ata4.01: configured for UDMA/33
[  529.819511] ata4: EH complete
davis@davis-desktop:~$ 

```

---

### Post by oddworld on 2008-04-27
I have also just tried writing a data disc and that does not work either.
How can I find out if the drive is dead or if its a problem with my ubuntu setup?

---

### Post by oddworld on 2008-04-27
I tried k3b and it crashed.
k3b has never really worked for me
Any ideas?

---

