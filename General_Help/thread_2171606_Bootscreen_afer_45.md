---
title: "Bootscreen afer 45"
date: 2013-08-31
forum: General Help
---

### Post by stefano099 on 2013-08-31
After new Installation of 12.04.3 and install the fglrx Ati driver my system is verry slow,
when i boot comes the bootscreen until 45 sec my Laptop is a Ibm Lenovo G570 with intel I3 and 6Gb Ram
hey sorry for my bad english!
Can somebody help me?


dmesg

```
[    0.313793] pci 0000:00:1c.1: PCI bridge to [bus 08]
[    0.313808] pci 0000:00:1c.1:   bridge window [mem 0xe0400000-0xe04fffff]
[    0.313852] pci_bus 0000:00: on NUMA node 0
[    0.313904] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.313944] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.314001] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEG0._PRT]
[    0.314091] \_SB_.PCI0:_OSC invalid UUID
[    0.314093] _OSC request data:1 1f 0 
[    0.314097]  pci0000:00: ACPI _OSC support notification failed, disabling PCIe ASPM
[    0.314098]  pci0000:00: Unable to request _OSC control (_OSC support mask: 0x08)
[    0.314807] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 *3 4 5 6 10 11 12 14 15)
[    0.314859] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 *10 11 12 14 15)
[    0.314909] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 10 *11 12 14 15)
[    0.314958] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 *10 11 12 14 15)
[    0.315007] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.315056] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 *10 11 12 14 15)
[    0.315105] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 10 *11 12 14 15)
[    0.315153] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 10 11 12 14 15) *7
[    0.315255] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.315261] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=none,locks=none
[    0.315263] vgaarb: loaded
[    0.315264] vgaarb: bridge control possible 0000:01:00.0
[    0.315265] vgaarb: no bridge control possible 0000:00:02.0
[    0.315466] SCSI subsystem initialized
[    0.315469] ACPI: bus type scsi registered
[    0.315510] libata version 3.00 loaded.
[    0.315527] ACPI: bus type usb registered
[    0.315546] usbcore: registered new interface driver usbfs
[    0.315554] usbcore: registered new interface driver hub
[    0.315576] usbcore: registered new device driver usb
[    0.315671] PCI: Using ACPI for IRQ routing
[    0.317331] PCI: pci_cache_line_size set to 64 bytes
[    0.317415] e820: reserve RAM buffer [mem 0x0009d800-0x0009ffff]
[    0.317417] e820: reserve RAM buffer [mem 0xbce3f000-0xbfffffff]
[    0.317420] e820: reserve RAM buffer [mem 0xbd000000-0xbfffffff]
[    0.317422] e820: reserve RAM buffer [mem 0x1bfe00000-0x1bfffffff]
[    0.317505] NetLabel: Initializing
[    0.317507] NetLabel:  domain hash size = 128
[    0.317508] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.317518] NetLabel:  unlabeled traffic allowed by default
[    0.317615] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.317622] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.320636] Switching to clocksource hpet
[    0.327096] AppArmor: AppArmor Filesystem Enabled
[    0.327117] pnp: PnP ACPI init
[    0.327129] ACPI: bus type pnp registered
[    0.327163] pnp 00:00: [dma 4]
[    0.327186] pnp 00:00: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.327208] pnp 00:01: Plug and Play ACPI device, IDs INT0800 (active)
[    0.327305] pnp 00:02: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.327337] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.327387] system 00:04: [io  0x0680-0x069f] has been reserved
[    0.327390] system 00:04: [io  0x1000-0x100f] has been reserved
[    0.327392] system 00:04: [io  0x1010-0x1013] has been reserved
[    0.327394] system 00:04: [io  0xffff] has been reserved
[    0.327397] system 00:04: [io  0x0400-0x0453] has been reserved
[    0.327399] system 00:04: [io  0x0458-0x047f] has been reserved
[    0.327401] system 00:04: [io  0x0500-0x057f] has been reserved
[    0.327404] system 00:04: [io  0x164e-0x164f] has been reserved
[    0.327406] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.327432] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.327475] system 00:06: [io  0x0454-0x0457] has been reserved
[    0.327479] system 00:06: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.384789] pnp 00:07: Plug and Play ACPI device, IDs SYN0730 SYN0700 SYN0002 PNP0f13 (active)
[    0.385002] pnp 00:08: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.385141] system 00:09: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.385144] system 00:09: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.385147] system 00:09: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.385149] system 00:09: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.385152] system 00:09: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.385154] system 00:09: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.385156] system 00:09: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.385159] system 00:09: [mem 0xff000000-0xffffffff] could not be reserved
[    0.385161] system 00:09: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.385163] system 00:09: [mem 0xbfa00000-0xbfa00fff] has been reserved
[    0.385167] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.385472] system 00:0a: [mem 0x20000000-0x201fffff] has been reserved
[    0.385475] system 00:0a: [mem 0x40000000-0x401fffff] has been reserved
[    0.385477] system 00:0a: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.385499] pnp: PnP ACPI: found 11 devices
[    0.385501] ACPI: ACPI bus type pnp unregistered
[    0.385503] PnPBIOS: Disabled by ACPI PNP
[    0.421921] pci 0000:01:00.0: no compatible bridge window for [mem 0xfffe0000-0xffffffff pref]
[    0.421955] pci 0000:01:00.0: BAR 6: assigned [mem 0xe0620000-0xe063ffff pref]
[    0.421959] pci 0000:00:01.0: PCI bridge to [bus 01-06]
[    0.421962] pci 0000:00:01.0:   bridge window [io  0x3000-0x3fff]
[    0.421965] pci 0000:00:01.0:   bridge window [mem 0xe0600000-0xe15fffff]
[    0.421968] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.421973] pci 0000:00:1c.0: PCI bridge to [bus 07]
[    0.421976] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.421982] pci 0000:00:1c.0:   bridge window [mem 0xe0500000-0xe05fffff]
[    0.421992] pci 0000:00:1c.1: PCI bridge to [bus 08]
[    0.421998] pci 0000:00:1c.1:   bridge window [mem 0xe0400000-0xe04fffff]
[    0.422034] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.422036] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.422038] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.422040] pci_bus 0000:00: resource 7 [mem 0xbfa00000-0xfeafffff]
[    0.422042] pci_bus 0000:01: resource 0 [io  0x3000-0x3fff]
[    0.422044] pci_bus 0000:01: resource 1 [mem 0xe0600000-0xe15fffff]
[    0.422046] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.422049] pci_bus 0000:07: resource 0 [io  0x2000-0x2fff]
[    0.422051] pci_bus 0000:07: resource 1 [mem 0xe0500000-0xe05fffff]
[    0.422053] pci_bus 0000:08: resource 1 [mem 0xe0400000-0xe04fffff]
[    0.422084] NET: Registered protocol family 2
[    0.422220] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    0.422238] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.422252] TCP: Hash tables configured (established 8192 bind 8192)
[    0.422265] TCP: reno registered
[    0.422267] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.422272] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.422322] NET: Registered protocol family 1
[    0.422335] pci 0000:00:02.0: Boot video device
[    0.452538] PCI: CLS 64 bytes, default 64
[    0.452610] Trying to unpack rootfs image as initramfs...
[    0.766593] Freeing initrd memory: 15492k freed
[    0.768866] Simple Boot Flag at 0x44 set to 0x1
[    0.769267] Initialise module verification
[    0.769305] audit: initializing netlink socket (disabled)
[    0.769321] type=2000 audit(1377967497.756:1): initialized
[    0.794837] bounce pool size: 64 pages
[    0.794847] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.796512] VFS: Disk quotas dquot_6.5.2
[    0.796558] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.797043] fuse init (API version 7.20)
[    0.797118] msgmni has been set to 1613
[    0.797537] Key type asymmetric registered
[    0.797539] Asymmetric key parser 'x509' registered
[    0.797569] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.797596] io scheduler noop registered
[    0.797599] io scheduler deadline registered (default)
[    0.797605] io scheduler cfq registered
[    0.797715] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.797855] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.797870] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.797920] intel_idle: MWAIT substates: 0x21120
[    0.797921] intel_idle: v0.4 model 0x2A
[    0.797923] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.798452] ACPI: AC Adapter [ACAD] (on-line)
[    0.798530] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0C:00/input/input0
[    0.798536] ACPI: Power Button [PWRB]
[    0.798714] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0E:00/input/input1
[    0.798717] ACPI: Sleep Button [SLPB]
[    0.798909] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input2
[    0.799017] ACPI: Lid Switch [LID0]
[    0.799050] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.799052] ACPI: Power Button [PWRF]
[    0.799106] ACPI: Fan [FAN0] (off)
[    0.799131] ACPI: Fan [FAN1] (off)
[    0.799179] ACPI: Requesting acpi_cpufreq
[    0.924900] thermal LNXTHERM:00: registered as thermal_zone0
[    0.924903] ACPI: Thermal Zone [TZ00] (0 C)
[    0.924933] GHES: HEST is not enabled!
[    0.925003] isapnp: Scanning for PnP cards...
[    0.925021] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.983683] ACPI: Battery Slot [BAT1] (battery absent)
[    0.983781] Linux agpgart interface v0.103
[    0.985158] brd: module loaded
[    0.985841] loop: module loaded
[    0.985936] ata_piix 0000:00:1f.2: version 2.13
[    0.985959] ata_piix 0000:00:1f.2: MAP [
[    0.985960]  P0 P2 P1 P3 ]
[    1.139462] ata_piix 0000:00:1f.2: setting latency timer to 64
[    1.139680] scsi0 : ata_piix
[    1.139764] scsi1 : ata_piix
[    1.139807] ata1: SATA max UDMA/133 cmd 0x40c8 ctl 0x40f4 bmdma 0x4090 irq 19
[    1.139813] ata2: SATA max UDMA/133 cmd 0x40c0 ctl 0x40f0 bmdma 0x4098 irq 19
[    1.139846] ata_piix 0000:00:1f.5: MAP [
[    1.139849]  P0 -- P1 -- ]
[    1.278422] isapnp: No Plug & Play device found
[    1.295241] ata_piix 0000:00:1f.5: SCR access via SIDPR is available but doesn't work
[    1.295262] ata_piix 0000:00:1f.5: setting latency timer to 64
[    1.295471] scsi2 : ata_piix
[    1.295532] scsi3 : ata_piix
[    1.295560] ata3: SATA max UDMA/133 cmd 0x40b8 ctl 0x40ec bmdma 0x4070 irq 21
[    1.295562] ata4: SATA max UDMA/133 cmd 0x40b0 ctl 0x40e8 bmdma 0x4078 irq 21
[    1.295816] libphy: Fixed MDIO Bus: probed
[    1.295877] tun: Universal TUN/TAP device driver, 1.6
[    1.295878] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.295928] PPP generic driver version 2.4.2
[    1.295982] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.295985] ehci-pci: EHCI PCI platform driver
[    1.296013] ehci-pci 0000:00:1a.0: setting latency timer to 64
[    1.296017] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    1.296022] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.296038] ehci-pci 0000:00:1a.0: debug port 2
[    1.299937] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    1.299953] ehci-pci 0000:00:1a.0: irq 16, io mem 0xe1609000
[    1.311207] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.311256] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.311262] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.311267] usb usb1: Product: EHCI Host Controller
[    1.311272] usb usb1: Manufacturer: Linux 3.8.0-29-generic ehci_hcd
[    1.311277] usb usb1: SerialNumber: 0000:00:1a.0
[    1.311425] hub 1-0:1.0: USB hub found
[    1.311430] hub 1-0:1.0: 2 ports detected
[    1.311525] ehci-pci 0000:00:1d.0: setting latency timer to 64
[    1.311528] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    1.311533] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.311546] ehci-pci 0000:00:1d.0: debug port 2
[    1.315448] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    1.315463] ehci-pci 0000:00:1d.0: irq 23, io mem 0xe1608000
[    1.327192] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.327252] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.327260] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.327265] usb usb2: Product: EHCI Host Controller
[    1.327270] usb usb2: Manufacturer: Linux 3.8.0-29-generic ehci_hcd
[    1.327275] usb usb2: SerialNumber: 0000:00:1d.0
[    1.327406] hub 2-0:1.0: USB hub found
[    1.327412] hub 2-0:1.0: 2 ports detected
[    1.327494] ehci-platform: EHCI generic platform driver
[    1.327501] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.327514] uhci_hcd: USB Universal Host Controller Interface driver
[    1.327580] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:MSS0] at 0x60,0x64 irq 1,12
[    1.372892] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.372900] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.373033] mousedev: PS/2 mouse device common for all mice
[    1.375167] rtc_cmos 00:05: RTC can wake from S4
[    1.375312] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.375342] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.375460] device-mapper: uevent: version 1.0.3
[    1.375537] device-mapper: ioctl: 4.23.1-ioctl (2012-12-18) initialised: dm-devel@redhat.com
[    1.375556] EISA: Probing bus 0 at eisa.0
[    1.375559] EISA: Cannot allocate resource for mainboard
[    1.375561] Cannot allocate resource for EISA slot 1
[    1.375562] Cannot allocate resource for EISA slot 2
[    1.375565] Cannot allocate resource for EISA slot 3
[    1.375567] Cannot allocate resource for EISA slot 4
[    1.375568] Cannot allocate resource for EISA slot 5
[    1.375570] Cannot allocate resource for EISA slot 6
[    1.375572] Cannot allocate resource for EISA slot 7
[    1.375574] Cannot allocate resource for EISA slot 8
[    1.375576] EISA: Detected 0 cards.
[    1.375584] cpufreq-nforce2: No nForce2 chipset.
[    1.375713] cpuidle: using governor ladder
[    1.376774] cpuidle: using governor menu
[    1.376779] ledtrig-cpu: registered to indicate activity on CPUs
[    1.376780] EFI Variables Facility v0.08 2004-May-17
[    1.376946] ashmem: initialized
[    1.377075] TCP: cubic registered
[    1.377168] NET: Registered protocol family 10
[    1.377353] NET: Registered protocol family 17
[    1.377364] Key type dns_resolver registered
[    1.377541] Using IPI No-Shortcut mode
[    1.377634] Loading module verification certificates
[    1.381870] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: 760b08a5a1de9684ced1bfd52640b05fe41b6ca5'
[    1.381882] registered taskstats version 1
[    1.384484] Key type trusted registered
[    1.386275] Key type encrypted registered
[    1.388773] rtc_cmos 00:05: setting system clock to 2013-08-31 16:44:59 UTC (1377967499)
[    1.389505] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.389507] EDD information not available.
[    1.421141] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.622846] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.754981] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
[    1.754993] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.755460] hub 1-1:1.0: USB hub found
[    1.755630] hub 1-1:1.0: 6 ports detected
[    1.766609] tsc: Refined TSC clocksource calibration: 2095.243 MHz
[    1.766623] Switching to clocksource tsc
[    1.866464] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    1.934504] ata1.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.934522] ata1.01: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.968292] ata1.00: ATA-8: TOSHIBA MK6465GSX, GJ005E, max UDMA/100
[    1.968303] ata1.00: 1250263728 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.968325] ata1.01: ATAPI: SlimtypeDVD A  DS8A5SH, XL63, max UDMA/100
[    1.974772] ata1.00: configured for UDMA/100
[    1.990536] ata1.01: configured for UDMA/100
[    1.992472] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK6465GS GJ00 PQ: 0 ANSI: 5
[    1.992639] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.992644] sd 0:0:0:0: [sda] 1250263728 512-byte logical blocks: (640 GB/596 GiB)
[    1.992733] sd 0:0:0:0: [sda] Write Protect is off
[    1.992738] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.998643] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
[    1.998654] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.999081] hub 2-1:1.0: USB hub found
[    1.999257] hub 2-1:1.0: 6 ports detected
[    1.999446] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.000607] scsi 0:0:1:0: CD-ROM            Slimtype DVD A  DS8A5SH   XL63 PQ: 0 ANSI: 5
[    2.006587] sr0: scsi3-mmc drive: 24x/8x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.006596] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.006730] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    2.006797] sr 0:0:1:0: Attached scsi generic sg1 type 5
[    2.070301] usb 1-1.4: new high-speed USB device number 3 using ehci-pci
[    2.083780]  sda: sda1 sda2 < sda5 >
[    2.084288] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.162902] usb 1-1.4: New USB device found, idVendor=0bda, idProduct=0139
[    2.162913] usb 1-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.162919] usb 1-1.4: Product: USB2.0-CRW
[    2.162924] usb 1-1.4: Manufacturer: Generic
[    2.162929] usb 1-1.4: SerialNumber: 20100201396000000
[    2.166005] ata2.00: failed to resume link (SControl 0)
[    2.269962] usb 2-1.1: new high-speed USB device number 3 using ehci-pci
[    2.379987] usb 2-1.1: New USB device found, idVendor=148f, idProduct=3070
[    2.379998] usb 2-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.380005] usb 2-1.1: Product: 802.11 n WLAN
[    2.380010] usb 2-1.1: Manufacturer: Ralink
[    2.380015] usb 2-1.1: SerialNumber: 1.0
[    2.453690] usb 2-1.2: new low-speed USB device number 4 using ehci-pci
[    2.553291] usb 2-1.2: New USB device found, idVendor=046d, idProduct=c504
[    2.553303] usb 2-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.553309] usb 2-1.2: Product: USB Receiver
[    2.553314] usb 2-1.2: Manufacturer: Logitech
[    2.625431] usb 2-1.3: new high-speed USB device number 5 using ehci-pci
[    2.748842] usb 2-1.3: New USB device found, idVendor=093a, idProduct=2700
[    2.748854] usb 2-1.3: New USB device strings: Mfr=16, Product=96, SerialNumber=0
[    2.748860] usb 2-1.3: Product: USB2.0_Camera
[    2.748866] usb 2-1.3: Manufacturer: PixArt Imaging Inc.
[    3.192584] ata2.01: failed to resume link (SControl 0)
[    3.204061] ata2.00: SATA link down (SStatus 4 SControl 0)
[    3.204077] ata2.01: SATA link down (SStatus 4 SControl 0)
[    3.204382] Freeing unused kernel memory: 796k freed
[    3.204543] Write protecting the kernel text: 6360k
[    3.204626] Write protecting the kernel read-only data: 2496k
[    3.204627] NX-protecting the kernel data: 3880k
[    3.220470] udevd[120]: starting version 175
[    3.255127] Disabling lock debugging due to kernel taint
[    3.277250] usbcore: registered new interface driver usbhid
[    3.277254] usbhid: USB HID core driver
[    3.286085] atl1c 0000:07:00.0: version 1.0.1.1-NAPI
[    3.313737] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input5
[    3.313830] hid-generic 0003:046D:C504.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.0-1.2/input0
[    3.314077] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.1/input/input6
[    3.314191] hid-generic 0003:046D:C504.0002: input,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-1.2/input1
[    3.731987] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    4.997912] init: ureadahead main process (312) terminated with status 5
[    6.181857] Adding 6233084k swap on /dev/sda5.  Priority:-1 extents:1 across:6233084k 
[    7.618529] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    7.915262] udevd[395]: starting version 175
[    8.946661] lp: driver loaded but no devices found
[    9.210117] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[    9.414149] ACPI Warning: 0x00000428-0x0000042f SystemIO conflicts with Region \PMIO 1 (20121018/utaddress-251)
[    9.414159] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    9.414166] ACPI Warning: 0x00000540-0x0000054f SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
[    9.414170] ACPI Warning: 0x00000540-0x0000054f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 2 (20121018/utaddress-251)
[    9.414173] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    9.414175] ACPI Warning: 0x00000530-0x0000053f SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
[    9.414180] ACPI Warning: 0x00000530-0x0000053f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 2 (20121018/utaddress-251)
[    9.414185] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    9.414187] ACPI Warning: 0x00000500-0x0000052f SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
[    9.414192] ACPI Warning: 0x00000500-0x0000052f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 2 (20121018/utaddress-251)
[    9.414196] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    9.414199] lpc_ich: Resource conflict(s) found affecting gpio_ich
[    9.425631] mei 0000:00:16.0: setting latency timer to 64
[    9.425696] mei 0000:00:16.0: irq 41 for MSI/MSI-X
[   10.132101] microcode: CPU0 sig=0x206a7, pf=0x10, revision=0x17
[   10.183439] input: Ideapad extra buttons as /devices/platform/ideapad/input/input7
[   10.596140] cfg80211: Calling CRDA to update world regulatory domain
[   10.718956] [drm] Initialized drm 1.1.0 20060810
[   10.735294] microcode: CPU1 sig=0x206a7, pf=0x10, revision=0x17
[   10.736757] microcode: CPU2 sig=0x206a7, pf=0x10, revision=0x17
[   10.738168] microcode: CPU3 sig=0x206a7, pf=0x10, revision=0x17
[   10.739553] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   11.569782] rts5139: module is from the staging directory, the quality is unknown, you have been warned.
[   11.576188] scsi4 : SCSI emulation for RTS5139 USB card reader
[   11.576359] usbcore: registered new interface driver rts5139
[   11.576413] scsi 4:0:0:0: Direct-Access     Generic- xD/SD/M.S.       1.00 PQ: 0 ANSI: 0 CCS
[   11.577246] sd 4:0:0:0: Attached scsi generic sg2 type 0
[   11.582791] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[   11.677555] [drm] Memory usable by graphics device = 2048M
[   11.677565] i915 0000:00:02.0: setting latency timer to 64
[   11.677924] i915 0000:00:02.0: irq 42 for MSI/MSI-X
[   11.677935] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   11.677937] [drm] Driver supports precise vblank timestamp query.
[   11.678094] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   11.678096] vgaarb: transferring owner from PCI:0000:00:02.0 to PCI:0000:01:00.0
[   11.890145] Linux video capture interface: v2.00
[   11.896785] fbcon: inteldrmfb (fb0) is primary device
[   11.957305] usbcore: registered new interface driver snd-usb-audio
[   12.074406] ath: phy0: ASPM enabled: 0x43
[   12.074409] ath: EEPROM regdomain: 0x65
[   12.074409] ath: EEPROM indicates we should expect a direct regpair map
[   12.074411] ath: Country alpha2 being used: 00
[   12.074411] ath: Regpair used: 0x65
[   12.261981] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04733/0xa40000/0xa0000, board id: 3655, fw id: 570026
[   12.320933] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   12.321275] ieee80211 phy0: Atheros AR9285 Rev:2 mem=0xf8e80000, irq=17
[   12.326900] Console: switching to colour frame buffer device 160x64
[   12.333469] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   12.333472] i915 0000:00:02.0: registered panic notifier
[   12.333761] [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS
[   12.334182] ACPI Error: Too many duplicates in _BCL package
[   12.334186]  (20121018/video-716)
[   12.334187] ACPI Error: Found unordered _BCL package
[   12.334189]  (20121018/video-725)
[   12.336709] acpi LNXVIDEO:02: registered as cooling_device6
[   12.336926] ACPI: Video Device [PEGP] (multi-head: yes  rom: no  post: no)
[   12.336978] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:2a/LNXVIDEO:00/input/input8
[   12.337095] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[   12.337104] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[   12.337112] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[   12.337120] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[   12.337128] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[   12.337136] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[   12.337145] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[   12.337462] ACPI Error: Too many duplicates in _BCL package
[   12.337466]  (20121018/video-716)
[   12.337467] ACPI Error: Found unordered _BCL package
[   12.337469]  (20121018/video-725)
[   12.338623] acpi device:30: registered as cooling_device7
[   12.338838] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   12.338885] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:09/input/input9
[   12.338980] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   12.340843] uvcvideo: Found UVC 1.00 device USB2.0_Camera (093a:2700)
[   12.349900] input: USB2.0_Camera as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.0/input/input10
[   12.349978] usbcore: registered new interface driver uvcvideo
[   12.349980] USB Video Class driver (1.1.1)
[   12.361844] snd_hda_intel 0000:00:1b.0: irq 43 for MSI/MSI-X
[   12.406909] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input11
[   12.521297] hda_codec: CX20590: BIOS auto-probing.
[   12.677438] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   12.677527] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   12.677594] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[   12.726306] usb 2-1.1: reset high-speed USB device number 3 using ehci-pci
[   12.778409] [drm] Enabling RC6 states: RC6 on, RC6p off, RC6pp off
[   12.844213] ieee80211 phy1: Selected rate control algorithm 'minstrel_ht'
[   12.844607] usbcore: registered new interface driver rt2800usb
[   13.961508] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   13.970511] <6>[fglrx] Maximum main memory to use for locked dma buffers: 5807 MBytes.
[   13.970724] <6>[fglrx]   vendor: 1002 device: 68e4 count: 1
[   13.971019] <6>[fglrx] ioport: bar 4, base 0x3000, size: 0x100
[   13.971028] pci 0000:01:00.0: enabling device (0000 -> 0003)
[   13.971148] <6>[fglrx] Kernel PAT support is enabled
[   13.971165] <6>[fglrx] module loaded - fglrx 13.10.10 [May 23 2013] with 1 minors
[   14.940665] type=1400 audit(1377967513.070:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=819 comm="apparmor_parser"
[   14.940681] type=1400 audit(1377967513.070:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=843 comm="apparmor_parser"
[   14.940700] type=1400 audit(1377967513.070:4): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=787 comm="apparmor_parser"
[   14.940830] type=1400 audit(1377967513.070:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=722 comm="apparmor_parser"
[   14.941250] type=1400 audit(1377967513.070:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=819 comm="apparmor_parser"
[   14.941270] type=1400 audit(1377967513.070:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=843 comm="apparmor_parser"
[   14.941419] type=1400 audit(1377967513.070:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=722 comm="apparmor_parser"
[   14.941435] type=1400 audit(1377967513.070:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=787 comm="apparmor_parser"
[   14.941584] type=1400 audit(1377967513.070:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=819 comm="apparmor_parser"
[   14.941593] type=1400 audit(1377967513.070:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=843 comm="apparmor_parser"
[   15.807753] init: failsafe main process (872) killed by TERM signal
[   17.106058] ppdev: user-space parallel port driver
[   17.937993] Bluetooth: Core ver 2.16
[   17.938017] NET: Registered protocol family 31
[   17.938019] Bluetooth: HCI device and connection manager initialized
[   17.938027] Bluetooth: HCI socket layer initialized
[   17.938031] Bluetooth: L2CAP socket layer initialized
[   17.938038] Bluetooth: SCO socket layer initialized
[   18.116154] Bluetooth: RFCOMM TTY layer initialized
[   18.116165] Bluetooth: RFCOMM socket layer initialized
[   18.116166] Bluetooth: RFCOMM ver 1.11
[   18.336645] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   18.336652] Bluetooth: BNEP filters: protocol multicast
[   18.336661] Bluetooth: BNEP socket layer initialized
[   21.748372] audit_printk_skb: 12 callbacks suppressed
[   21.748376] type=1400 audit(1377967519.882:16): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1030 comm="apparmor_parser"
[   21.748861] type=1400 audit(1377967519.886:17): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1030 comm="apparmor_parser"
[   21.749112] type=1400 audit(1377967519.886:18): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1030 comm="apparmor_parser"
[   21.752377] type=1400 audit(1377967519.886:19): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1034 comm="apparmor_parser"
[   21.752934] type=1400 audit(1377967519.890:20): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1034 comm="apparmor_parser"
[   21.827064] type=1400 audit(1377967519.966:21): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1038 comm="apparmor_parser"
[   21.886928] type=1400 audit(1377967520.026:22): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=1033 comm="apparmor_parser"
[   21.887126] type=1400 audit(1377967520.026:23): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1029 comm="apparmor_parser"
[   21.887477] type=1400 audit(1377967520.026:24): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=1029 comm="apparmor_parser"
[   21.887526] type=1400 audit(1377967520.026:25): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=1033 comm="apparmor_parser"
[   21.911726] atl1c 0000:07:00.0: irq 44 for MSI/MSI-X
[   21.926981] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.937100] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.964523] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.972979] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.414877] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   22.417748] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   26.372035] wlan1: authenticate with 00:23:08:c0:f2:ba
[   26.449160] wlan1: send auth to 00:23:08:c0:f2:ba (try 1/3)
[   26.450636] wlan1: authenticated
[   26.453889] wlan1: associate with 00:23:08:c0:f2:ba (try 1/3)
[   26.457408] wlan1: RX AssocResp from 00:23:08:c0:f2:ba (capab=0x411 status=0 aid=1)
[   26.464859] wlan1: associated
[   26.464891] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[   27.076659] fglrx_pci 0000:01:00.0: irq 45 for MSI/MSI-X
[   27.077436] <6>[fglrx] Firegl kernel thread PID: 1163
[   27.077525] <6>[fglrx] Firegl kernel thread PID: 1164
[   27.077601] <6>[fglrx] Firegl kernel thread PID: 1165
[   27.077702] <6>[fglrx] IRQ 45 Enabled
[   27.091573] <6>[fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   27.091577] <6>[fglrx] Reserved FB block: Unshared offset:f87c000, size:484000 
[   27.091579] <6>[fglrx] Reserved FB block: Unshared offset:3fff4000, size:c000 
[   74.674298] audit_printk_skb: 24 callbacks suppressed


```

```

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 IDE interface: Intel Corporation 6 Series/C200 Series Chipset Family 4 port SATA IDE Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
00:1f.5 IDE interface: Intel Corporation 6 Series/C200 Series Chipset Family 2 port SATA IDE Controller (rev 05)

01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Robson CE [Radeon HD 6370M/7370M]
07:00.0 Ethernet controller: Qualcomm Atheros AR8152 v2.0 Fast Ethernet (rev c1)
08:00.0 Network controller: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) (rev 01)



```

---

### Post by Impavidus on 2013-08-31
Having both ATI and Intel graphics sometimes give issues, but with a 5400 rpm hard disk and a few seconds to set up wifi 45 seconds doesn't sound ridiculously long.

---

### Post by stefano099 on 2013-09-01
thanks but when i
dmesg |grep -i acpi | grep -i warning
```

dmesg |grep -i acpi | grep -i warning
[   10.722788] ACPI Warning: 0x00000428-0x0000042f SystemIO conflicts with Region \PMIO 1 (20121018/utaddress-251)
[   10.722804] ACPI Warning: 0x00000540-0x0000054f SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
[   10.722811] ACPI Warning: 0x00000540-0x0000054f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 2 (20121018/utaddress-251)
[   10.722819] ACPI Warning: 0x00000530-0x0000053f SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
[   10.722824] ACPI Warning: 0x00000530-0x0000053f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 2 (20121018/utaddress-251)
[   10.722831] ACPI Warning: 0x00000500-0x0000052f SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
[   10.722835] ACPI Warning: 0x00000500-0x0000052f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 2 (20121018/utaddress-251)


```
dmesg |grep -i acpi | grep -i error
```

dmesg |grep -i acpi | grep -i error
[   13.128746] ACPI Error: Too many duplicates in _BCL package
[   13.128750] ACPI Error: Found unordered _BCL package
[   13.131547] ACPI Error: Too many duplicates in _BCL package
[   13.131555] ACPI Error: Found unordered _BCL package


```
lspci -v | perl -ne '/VGA/../^$/ and /VGA|Kern/ and print'
```

 lspci -v | perl -ne '/VGA/../^$/ and /VGA|Kern/ and print' 
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
    Kernel driver in use: i915
    Kernel modules: i915
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Robson CE [Radeon HD 6370M/7370M] (prog-if 00 [VGA controller])
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx_experimental_13, radeon


``` 

and the /dmesg is on [URL="http://paste.ubuntu.com/6050719/"]http://paste.ubuntu.com/6050719/

can sombody tell me what i can do?


[/URL]

---

