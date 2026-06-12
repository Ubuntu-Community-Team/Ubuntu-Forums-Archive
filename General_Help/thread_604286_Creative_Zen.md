---
title: "Creative Zen"
date: 2007-11-06
forum: General Help
---

### Post by PricklySponge on 2007-11-06
Would there be any way that I would be able to transfer mp3 files to and from my Creative Zen. 

The is the model I have: [http://www.amazon.com/Creative-Zen-16-GB-Black/dp/B000UVBDRS/ref=pd_bbs_sr_2/002-0559113-7727259?ie=UTF8&s=electronics&qid=1194325913&sr=8-2]("http://www.amazon.com/Creative-Zen-16-GB-Black/dp/B000UVBDRS/ref=pd_bbs_sr_2/002-0559113-7727259?ie=UTF8&s=electronics&qid=1194325913&sr=8-2")

It was just recently released so I understand if the software isn't yet available :) At his point Ubuntu doesn't recognize that it has been connected to the computer at all. 

Thanks

---

### Post by BennBuntu on 2007-11-06
I know older creatives worked with drag and drop "I've connected a Zen Vision-m", have you turned the unit on after you connected it?

---

### Post by PricklySponge on 2007-11-06
Yes, It automatically turns itself on when connected to my computer

---

### Post by BennBuntu on 2007-11-06
hmm, the ZEN vision -m just automounted as an external drive, you could try dmesg to see if it's being picked up at all. Just type dmesg in a terminal after you've plugged it in. 
Or if it shows up in /dev/ maybe try mounting manually I don't really know enough to help further. Good luck.

---

### Post by PricklySponge on 2007-11-06
This was the output of dmesg. Not really sure what I should be looking for

> 
[   33.079666] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   33.334431] usbcore: registered new interface driver usbfs
[   33.334449] usbcore: registered new interface driver hub
[   33.334463] usbcore: registered new device driver usb
[   33.399793] USB Universal Host Controller Interface driver v3.0
[   33.399839] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
[   33.399847] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[   33.399849] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[   33.399936] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[   33.399959] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000dc00
[   33.400034] usb usb1: configuration #1 chosen from 1 choice
[   33.400051] hub 1-0:1.0: USB hub found
[   33.400055] hub 1-0:1.0: 2 ports detected
[   33.404248] Floppy drive(s): fd0 is 1.44M
[   33.416129] SCSI subsystem initialized
[   33.419158] libata version 2.21 loaded.
[   33.427826] FDC 0 is a post-1991 82077
[   33.501590] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 17 (level, low) -> IRQ 18
[   33.501599] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[   33.501601] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[   33.501617] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[   33.501640] uhci_hcd 0000:00:1a.1: irq 18, io base 0x0000e000
[   33.501700] usb usb2: configuration #1 chosen from 1 choice
[   33.501717] hub 2-0:1.0: USB hub found
[   33.501720] hub 2-0:1.0: 2 ports detected
[   33.605403] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
[   33.605408] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   33.605410] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   33.605425] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
[   33.605445] uhci_hcd 0000:00:1d.0: irq 19, io base 0x0000d480
[   33.605502] usb usb3: configuration #1 chosen from 1 choice
[   33.605518] hub 3-0:1.0: USB hub found
[   33.605521] hub 3-0:1.0: 2 ports detected
[   33.709242] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
[   33.709248] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   33.709250] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   33.709264] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
[   33.709284] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000d800
[   33.709340] usb usb4: configuration #1 chosen from 1 choice
[   33.709355] hub 4-0:1.0: USB hub found
[   33.709359] hub 4-0:1.0: 2 ports detected
[   33.813073] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 20
[   33.813078] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   33.813080] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   33.813094] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
[   33.813113] uhci_hcd 0000:00:1d.2: irq 20, io base 0x0000d880
[   33.813168] usb usb5: configuration #1 chosen from 1 choice
[   33.813183] hub 5-0:1.0: USB hub found
[   33.813186] hub 5-0:1.0: 2 ports detected
[   33.918233] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 20
[   33.918240] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[   33.918243] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   33.918257] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 6
[   33.918277] ehci_hcd 0000:00:1a.7: debug port 1
[   33.918281] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[   33.918285] ehci_hcd 0000:00:1a.7: irq 20, io mem 0xfebffc00
[   33.948851] usb 3-1: new full speed USB device using uhci_hcd and address 2
[   33.948861] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   33.948929] usb usb6: configuration #1 chosen from 1 choice
[   33.948946] hub 6-0:1.0: USB hub found
[   33.948951] hub 6-0:1.0: 4 ports detected
[   34.052750] r8169 Gigabit Ethernet driver 2.2LK loaded
[   34.052775] ACPI: PCI Interrupt 0000:03:00.0[A] -> <6>ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
[   34.052779] GSI 19 (level, low) -> IRQ 17
[   34.052788] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   34.052791] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   34.052794] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   34.052809] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
[   34.052828] ehci_hcd 0000:00:1d.7: debug port 1
[   34.052833] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   34.052837] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xfebff800
[   34.052968] eth0: RTL8168b/8111b at 0xf886a000, 00:18:f3:04:c5:cb, XID 38000000 IRQ 17
[   34.064647] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   34.064699] usb usb7: configuration #1 chosen from 1 choice
[   34.064715] hub 7-0:1.0: USB hub found
[   34.064718] hub 7-0:1.0: 6 ports detected
[   34.168547] ahci 0000:02:00.0: version 2.2
[   34.168565] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   34.472012] usb 3-1: device not accepting address 2, error -71
[   35.134996] usb 7-6: new high speed USB device using ehci_hcd and address 3
[   35.170961] ahci 0000:02:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[   35.170964] ahci 0000:02:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[   35.170969] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   35.171064] scsi0 : ahci
[   35.171096] scsi1 : ahci
[   35.171135] ata1: SATA max UDMA/133 cmd 0xf88c4100 ctl 0x00000000 bmdma 0x00000000 irq 16
[   35.171138] ata2: SATA max UDMA/133 cmd 0xf88c4180 ctl 0x00000000 bmdma 0x00000000 irq 16
[   35.269366] usb 7-6: configuration #1 chosen from 1 choice
[   35.482465] ata1: SATA link down (SStatus 0 SControl 300)
[   35.506424] usb 3-1: new full speed USB device using uhci_hcd and address 4
[   35.679451] usb 3-1: configuration #1 chosen from 1 choice
[   35.682412] hub 3-1:1.0: USB hub found
[   35.685393] hub 3-1:1.0: 4 ports detected
[   35.794039] ata2: SATA link down (SStatus 0 SControl 300)
[   35.794470] PCI: Enabling device 0000:02:00.1 (0000 -> 0001)
[   35.794476] ACPI: PCI Interrupt 0000:02:00.1[B] -> GSI 17 (level, low) -> IRQ 18
[   35.794504] PCI: Setting latency timer of device 0000:02:00.1 to 64
[   35.794532] scsi2 : pata_jmicron
[   35.794559] scsi3 : pata_jmicron
[   35.794621] ata3: PATA max UDMA/100 cmd 0x0001ac00 ctl 0x0001a882 bmdma 0x0001a400 irq 18
[   35.794624] ata4: PATA max UDMA/100 cmd 0x0001a800 ctl 0x0001a482 bmdma 0x0001a408 irq 18
[   35.958313] ata3.01: ATA-6: WDC WD800BB-22JHC0, 05.01C05, max UDMA/100
[   35.958316] ata3.01: 156301488 sectors, multi 0: LBA 
[   35.966315] ata3.01: configured for UDMA/100
[   35.998929] usb 3-1.2: new full speed USB device using uhci_hcd and address 5
[   36.132843] scsi 2:0:1:0: Direct-Access     ATA      WDC WD800BB-22JH 05.0 PQ: 0 ANSI: 5
[   36.132939] ata_piix 0000:00:1f.2: version 2.11
[   36.132943] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[   36.132958] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 17
[   36.132977] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   36.132996] scsi4 : ata_piix
[   36.133019] scsi5 : ata_piix
[   36.133081] ata5: SATA max UDMA/133 cmd 0x0001ec00 ctl 0x0001e882 bmdma 0x0001e400 irq 17
[   36.133083] ata6: SATA max UDMA/133 cmd 0x0001e800 ctl 0x0001e482 bmdma 0x0001e408 irq 17
[   36.136527] sd 2:0:1:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   36.136535] sd 2:0:1:0: [sda] Write Protect is off
[   36.136536] sd 2:0:1:0: [sda] Mode Sense: 00 3a 00 00
[   36.136546] sd 2:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   36.136573] sd 2:0:1:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   36.136579] sd 2:0:1:0: [sda] Write Protect is off
[   36.136581] sd 2:0:1:0: [sda] Mode Sense: 00 3a 00 00
[   36.136590] sd 2:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   36.136592]  sda:<6>usb 3-1.2: configuration #1 chosen from 1 choice
[   36.153024]  sda1
[   36.153190] sd 2:0:1:0: [sda] Attached SCSI disk
[   36.155681] sd 2:0:1:0: Attached scsi generic sg0 type 0
[   36.293474] ata5.00: ATA-7: WDC WD1600JS-08NCB1, 10.02E01, max UDMA/133
[   36.293477] ata5.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   36.301466] ata5.00: configured for UDMA/133
[   36.362391] usb 3-1.3: new low speed USB device using uhci_hcd and address 6
[   36.603093] usb 3-1.3: configuration #1 chosen from 1 choice
[   36.610044] usbcore: registered new interface driver libusual
[   36.613998] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   36.614001] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   36.614140] usbcore: registered new interface driver hiddev
[   36.615605] Initializing USB Mass Storage driver...
[   36.615642] scsi6 : SCSI emulation for USB Mass Storage devices
[   36.615675] usb-storage: device found at 3
[   36.615676] usb-storage: waiting for device to settle before scanning
[   36.617142] input: Logitech USB Receiver as /class/input/input1
[   36.617155] input: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-1.2
[   36.617172] usbcore: registered new interface driver usb-storage
[   36.617174] USB Mass Storage support registered.
[   36.625050] input: Logitech USB Receiver as /class/input/input2
[   36.625075] input,hiddev96: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.0-1.2
[   36.674061] input: Chicony Saitek Eclipse Keyboard as /class/input/input3
[   36.674065] input: USB HID v1.11 Keyboard [Chicony Saitek Eclipse Keyboard] on usb-0000:00:1d.0-1.3
[   36.778802] input: Chicony Saitek Eclipse Keyboard as /class/input/input4
[   36.778819] input,hiddev97: USB HID v1.11 Device [Chicony Saitek Eclipse Keyboard] on usb-0000:00:1d.0-1.3
[   36.778825] usbcore: registered new interface driver usbhid
[   36.778827] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   36.792605] ata6.00: ATAPI: TSSTcorp DVD+/-RW TS-H553A, DE04, max UDMA/33
[   36.792607] ata6.00: applying bridge limits
[   36.980308] ata6.00: configured for UDMA/33
[   36.980382] scsi 4:0:0:0: Direct-Access     ATA      WDC WD1600JS-08N 10.0 PQ: 0 ANSI: 5
[   36.980426] sd 4:0:0:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[   36.980433] sd 4:0:0:0: [sdb] Write Protect is off
[   36.980434] sd 4:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   36.980444] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   36.980474] sd 4:0:0:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[   36.980481] sd 4:0:0:0: [sdb] Write Protect is off
[   36.980482] sd 4:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   36.980491] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   36.980494]  sdb: sdb1 sdb2 < sdb5 >
[   37.017991] sd 4:0:0:0: [sdb] Attached SCSI disk
[   37.018012] sd 4:0:0:0: Attached scsi generic sg1 type 0
[   37.018544] scsi 5:0:0:0: CD-ROM            TSSTcorp DVD+-RW TS-H553A DE04 PQ: 0 ANSI: 5
[   37.018573] scsi 5:0:0:0: Attached scsi generic sg2 type 5
[   37.018591] ata_piix 0000:00:1f.5: MAP [ P0 P2 P1 P3 ]
[   37.018607] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 19 (level, low) -> IRQ 17
[   37.018626] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   37.018647] scsi7 : ata_piix
[   37.018671] scsi8 : ata_piix
[   37.018733] ata7: SATA max UDMA/133 cmd 0x0001d400 ctl 0x0001d082 bmdma 0x0001c880 irq 17
[   37.018735] ata8: SATA max UDMA/133 cmd 0x0001d000 ctl 0x0001cc02 bmdma 0x0001c888 irq 17
[   37.356306] sr0: scsi3-mmc drive: 16x/48x writer cd/rw xa/form2 cdda tray
[   37.356309] Uniform CD-ROM driver Revision: 3.20
[   37.356411] sr 5:0:0:0: Attached scsi CD-ROM sr0
[   37.576184] Attempting manual resume
[   37.576186] swsusp: Resume From Partition 8:21
[   37.576187] PM: Checking swsusp image.
[   37.576300] PM: Resume from disk failed.
[   37.583971] EXT3-fs: INFO: recovery required on readonly filesystem.
[   37.583973] EXT3-fs: write access will be enabled during recovery.
[   41.605212] usb-storage: device scan complete
[   41.607834] scsi 6:0:0:0: Direct-Access     Seagate  External Drive        PQ: 0 ANSI: 0
[   41.608820] sd 6:0:0:0: [sdc] 156301488 512-byte hardware sectors (80026 MB)
[   41.609693] sd 6:0:0:0: [sdc] Write Protect is off
[   41.609695] sd 6:0:0:0: [sdc] Mode Sense: 27 00 00 00
[   41.609696] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[   41.610567] sd 6:0:0:0: [sdc] 156301488 512-byte hardware sectors (80026 MB)
[   41.611440] sd 6:0:0:0: [sdc] Write Protect is off
[   41.611441] sd 6:0:0:0: [sdc] Mode Sense: 27 00 00 00
[   41.611443] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[   41.611445]  sdc: sdc1
[   41.618090] sd 6:0:0:0: [sdc] Attached SCSI disk
[   41.618114] sd 6:0:0:0: Attached scsi generic sg3 type 0
[   42.659520] kjournald starting.  Commit interval 5 seconds
[   42.659528] EXT3-fs: recovery complete.
[   42.659880] EXT3-fs: mounted filesystem with ordered data mode.
[   48.437977] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   48.451403] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   48.506675] input: PC Speaker as /class/input/input5
[   48.630679] parport_pc 00:0a: reported by Plug and Play ACPI
[   48.630772] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   48.638100] Linux agpgart interface v0.102 (c) Dave Jones
[   48.683145] nvidia: module license 'NVIDIA' taints kernel.
[   48.932774] iTCO_vendor_support: vendor-support=0
[   48.933382] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   48.933434] iTCO_wdt: Found a ICH8 or ICH8R TCO device (Version=2, TCOBASE=0x0860)
[   48.933466] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   48.933846] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   48.933853] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   48.933920] NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.19  Wed Sep 12 14:12:24 PDT 2007
[   48.958808] usbcore: registered new interface driver xpad
[   48.958811] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: driver for Xbox controllers v0.1.6
[   49.124569] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 21
[   49.124583] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   50.486630] lp0: using parport0 (interrupt-driven).
[   50.571680] Adding 6080560k swap on /dev/sdb5.  Priority:-1 extents:1 across:6080560k
[   50.721380] EXT3 FS on sdb1, internal journal
[   51.284017] No dock devices found.
[   51.399584] input: Power Button (FF) as /class/input/input6
[   51.399597] ACPI: Power Button (FF) [PWRF]
[   51.399664] input: Power Button (CM) as /class/input/input7
[   51.399673] ACPI: Power Button (CM) [PWRB]
[   52.493172] ppdev: user-space parallel port driver
[   52.616963] audit(1194325097.827:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5315 profile="/usr/sbin/cupsd"
[   52.646339] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   52.646342] apm: disabled - APM is not SMP safe.
[   52.739119] r8169: eth0: link up
[   52.739127] r8169: eth0: link up
[   52.785229] Failure registering capabilities with primary security module.
[   52.926347] Bluetooth: Core ver 2.11
[   52.926431] NET: Registered protocol family 31
[   52.926433] Bluetooth: HCI device and connection manager initialized
[   52.926435] Bluetooth: HCI socket layer initialized
[   52.936669] Bluetooth: L2CAP ver 2.8
[   52.936672] Bluetooth: L2CAP socket layer initialized
[   52.983212] Bluetooth: RFCOMM socket layer initialized
[   52.983287] Bluetooth: RFCOMM TTY layer initialized
[   52.983289] Bluetooth: RFCOMM ver 1.8
[   57.515852] NET: Registered protocol family 17
[   66.802253] UDF-fs: No VRS found
[   66.854880] ISO 9660 Extensions: Microsoft Joliet Level 3
[   66.894620] ISOFS: changing to secondary root
[   73.768218] NET: Registered protocol family 10
[   73.768351] lo: Disabled Privacy Extensions
[   84.307068] eth0: no IPv6 routers present
[  107.703373] usb 7-5: new high speed USB device using ehci_hcd and address 4
[  107.836831] usb 7-5: configuration #1 chosen from 1 choice
[ 1559.760489] usb 7-5: USB disconnect, address 4
[ 2405.598112] usb 7-5: new high speed USB device using ehci_hcd and address 5
[ 2405.731682] usb 7-5: configuration #1 chosen from 1 choice



Thanks for your help!

I forgot to add, I know that the USB port is not the problem because the Creative Zen is able to sync in windows.

---

### Post by BennBuntu on 2007-11-06
Sounds like it uses mtp, micro$oft's media transfer protocol 

[http://libmtp.sourceforge.net/index.php?page=compatibility]("http://libmtp.sourceforge.net/index.php?page=compatibility").   Try installing libmtp6 and mpt-tools.

either search ofr libmtp in synaptic or

```
sudo apt-get install libmtp6 mpt-tools
```

Was already installed for me in Gutsy. If that's setup, open up rhythmbox and if you're lucky it will show up in the playlists.

Another option is [Gnomad2]("http://gnomad2.sourceforge.net/") 

sudo apt-get isntall gnomad2

---

### Post by PricklySponge on 2007-11-06
No luck with rhythembox, and the player still doesnt seem to be being detected by ubuntu at all.:-k

I tried Gnomad and I receive this error at start

[IMG]http://i3.photobucket.com/albums/y80/PricklySponge/Screenshot-gnomad2.png[/IMG]

---

### Post by BennBuntu on 2007-11-06
Sorry, I don't know what else to try other than hooking up with the gnomad people. your dmesg shows it picking up the usb device but not doing anything with it. If it's functional I think it should show up with.

```
lsusb
```

good luck

---

### Post by mahousaru on 2007-11-06
To get my Creative Zen V working in Gutsy with Gnomad2 I found I had to turn off the auto action using:

System, Preferences, Removable Drives and Media, Multimedia, untick portable player*

I then installed Gnomad2 which installs the mtp lib as well.  This of course is based on my personal preference for Gnomad and I have no idea will it work on your newer model.

*I can't see why you can't set Gnomad to automatically launch here.

---

### Post by SpaceFarm on 2007-11-06
I got the new 16gb Creative player too. It's doing the same thing (ie not being detected). Since it's new I'm betting there'll just be a matter of time before an update.

---

### Post by BennBuntu on 2007-11-08
Was just fiddling with rhythmbox, noticed there is a plugin in the menus for MTP.

edit > plugins > portable players - MTP

maybe worth a shot, just in case, although presumably uses the same libraries as gnomad.

---

### Post by the_real_bubba on 2007-11-27
I think the current ubuntu libraries won't recognize the new Zens, rumour has it that the version in cvs will, but I've seen one post here saying that it doesn't work, and none confirming that it does work...

---

### Post by the_real_bubba on 2007-11-27
whups by "libraries" I mean libmtp, of course...

---

### Post by peas on my plate on 2007-11-29
Creative Vision:M does use MTP, not mass storage (groan).  I got myself a Vision:M before I knew anything about Linux.  The best way to get it to work (transfer files) is to use Gnomad2.  The trick, though, is to plug in your player before you open gnomad2, otherwise it won't register.  Also, unplug your player before you close gnomad2, or the player might crash.  Keeping that in mind it works flawlessly.

Amrok will recognize it as well, but is runs slow for me since it's kde.

If only exaile would work with mtp....:)

---

### Post by JairunCaloth on 2007-11-29
Creative Zens use MTP as pointed out by other posters. Personally I couldn't stand gnomad, and other software that supports MTP should be able to access it such as Amrok, rythembox ect...

However, to get anything to work with mine, I had to download the latest MTP libraries, and compile the software using the newest MTP libraries. Also, if they can't access it, you might need to check your USB settings and make sure you have permission to use it. Don't remember off the top of my head how to do that, but it shouldn't be hard to find that information by searching the forums.

---

### Post by imdano on 2007-11-29
> **peas on my plate said:**
> If only exaile would work with mtp....:)I'm working on an MTP plugin for exaile, it's available in the development version on their Bazaar repository.  It's not completely full featured yet, but you can view/delete tracks on the device, and add tracks to the device.  Support to play tracks from the device and possibly playlist support (Exaile's playlist system isn't easily integrated with the MTP system) is forthcoming.

---

### Post by Levster on 2008-01-03
so has anyone gotten a 16gb Zen to work?

---

### Post by PinkFloyd102489 on 2008-01-03
I have a Zen Vision:M and I use Gnomad2. It works extremely well. The player only syncs up when you have Gnomad running. Otherwise, you can charge the player on the USB and listen to your music at the same time.

---

### Post by fatherdaly on 2008-02-02
Same Problem here, my Creative Zen 16gb won't work.

Loads of people seem to have got the Zen vision working, there must be a way to make mine work?

---

### Post by malcam on 2008-02-04
The version of libmtp that comes with ubuntu doesn't recognise the new Zen models. You need to compile the latest version, there's an over-the-top guide on these forums that explains how to do this but it also installs a whole load of stuff that you don't need and more than likely breaks things, so I won't link to it directly.

---

### Post by thedaylights on 2008-02-07
Malcam could you explain how to compile with the latest libmtp? And do you mean compile Gnomad2 or Rhythmbox?

thanks,
thedaylights

---

### Post by emitchlpd on 2008-02-09
The reason this isn't working for you is fairly trivial. If you run Gnomad2 as root, your Zen will be detected. Essentially there's something going on with libmtp where it doesn't make the Zen available to regular users because it doesn't know in its current version that it should (ie the Zen is newer than the latest version of libmtp in Ubuntu).

I have the 4 GB Zen -- same as yours but less flash. The stuff that applies to the Vision:M and other, older Zen devices doesn't neccessarily apply to our Zens. The common name makes it pretty difficult to find good information...

I'm going to try compiling the latest version of libmtp and I'll post back if I have any luck running Gnomad2 as a regular user.

---

### Post by nicholas mccarthy on 2008-02-10
ok, i have the old version of the Zen, the Micro one, and i dont know how to get it to be detected, any help?

---

### Post by nicholas mccarthy on 2008-02-10
never mind, i got it

---

### Post by timmyw29 on 2008-02-11
I've got a zen vision:m, and noticed it wasn't doing anything when I plugged it in (decided it was time to update the music that's on it).

Rhythmbox with the MTP plugin enabled did the trick for me. Works like a dream as far as I can tell right now. Thanks all for the info, you make things so much easier for me.

---

### Post by myolbug on 2008-02-12
Umm, I have Amarock, but it is asking me to configure my media device.  how do i do that?  Nothing is showing up on my computer with my Zen V+ connected
The rythmbox I have doesn't pick it up either.  Is this because I have Ubuntu 6.06?

---

### Post by myolbug on 2008-02-12
Bump.  Anyone?

---

### Post by Insane SandmaN on 2008-02-13
Finally i've got it! All you need to do is run your music app (supporting mtp) as root! 
For example:
sudo gnomad2 
"enter pass"
and it works!

---

### Post by fatherdaly on 2008-02-17
Bump, again. sorry.

but what do you mean? I use amorak and have libmtp6.

Nothing happens when I connect my Zen. Any suggestions?

---

### Post by lovhorror on 2008-02-17
I had this issue too, all I had to do was go into Amarok, go to settings, then configure Amarok. from there click add device, select MTP device and give it a name then click okay. Make sure that MTP device is selected, make sure the Zen is plugged in, then click connect.

---

### Post by fatherdaly on 2008-02-17
Thanks, but it didn't work.

Nothing happened when I clicked connect.

Any other Ideas?

---

### Post by growingneeds on 2008-02-23
I have the 16GB Creative Zen. I did the following in Feisty Fawn to detect the device:

1. Install Gnomad2 from Applications->Add/Remove menu.
2. From the terminal, key *sudo gnomad2*

The screen of Zen player now shows *Docked*. Thanks goes to **emitchlpd** for clarifying the technical details governing the method. I really do not have the expertise to compile software. Thanks to I**nsane SandmaN** too for listing the solution as plainly as it will ever get.

Now the question is... How do I use gnomad2 to tansfer music onto the player? Sigh. Why can't companies just make their players as simple mass storage devices...

---

