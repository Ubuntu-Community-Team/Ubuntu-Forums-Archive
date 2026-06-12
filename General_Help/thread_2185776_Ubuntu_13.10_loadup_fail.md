---
title: "Ubuntu 13.10 loadup fail?"
date: 2013-11-04
forum: General Help
---

### Post by Christopher on 2013-11-04
When im booting into Ubuntu 13.10 im watching my screen & all things read ok, but theres one that says "fail" in red. I cant tell what it is cause my PC is booting to fast lol, is there a way to stop it and write it down so i can get whats wrong fixed? Ubuntu 13.10 seems to run flawlessly its just that "fail" when loading is all that seems to me wrong. Thanks in advance.

---

### Post by Bucky Ball on 2013-11-04
*Thread moved to **General Help**.*

If all is well I wouldn't be too bothered. You could open a terminal and check dmesg. Just type:

dmesg

... immediately after boot.

---

### Post by Christopher on 2013-11-04
> **Bucky Ball said:**
> *Thread moved to **General Help**.*

If all is well I wouldn't be too bothered. You could open a terminal and check dmesg. Just type:

dmesg

... immediately after boot.



Should i post the "dmesg" here to see IF anything is wrong?

---

### Post by Bucky Ball on 2013-11-04
> **Christopher said:**
> Should i post the "dmesg" here to see IF anything is wrong?

Yep, sure. Something might stick out. You might notice something near the end. (And please use code tags when you post it by clicking 'Go Advanced', highlight the code and hit the # icon. ;)

---

### Post by Christopher on 2013-11-04
```
[    0.128016] vgaarb: device added: PCI:0000:03:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.128017] vgaarb: loaded
[    0.128018] vgaarb: bridge control possible 0000:03:00.0
[    0.128135] SCSI subsystem initialized
[    0.128137] ACPI: bus type ATA registered
[    0.128145] libata version 3.00 loaded.
[    0.128145] ACPI: bus type USB registered
[    0.128145] usbcore: registered new interface driver usbfs
[    0.128145] usbcore: registered new interface driver hub
[    0.128145] usbcore: registered new device driver usb
[    0.128145] PCI: Using ACPI for IRQ routing
[    0.135365] PCI: pci_cache_line_size set to 64 bytes
[    0.135423] e820: reserve RAM buffer [mem 0x0009b800-0x0009ffff]
[    0.135425] e820: reserve RAM buffer [mem 0xafef0000-0xafffffff]
[    0.135485] NetLabel: Initializing
[    0.135486] NetLabel:  domain hash size = 128
[    0.135487] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.135496] NetLabel:  unlabeled traffic allowed by default
[    0.135504] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.135504] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
[    0.135504] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
[    0.137008] Switched to clocksource hpet
[    0.140277] AppArmor: AppArmor Filesystem Enabled
[    0.140301] pnp: PnP ACPI init
[    0.140311] ACPI: bus type PNP registered
[    0.140371] system 00:00: [io  0x1000-0x107f] could not be reserved
[    0.140373] system 00:00: [io  0x1080-0x10ff] has been reserved
[    0.140374] system 00:00: [io  0x1400-0x147f] has been reserved
[    0.140376] system 00:00: [io  0x1480-0x14ff] has been reserved
[    0.140377] system 00:00: [io  0x1800-0x187f] has been reserved
[    0.140379] system 00:00: [io  0x1880-0x18ff] has been reserved
[    0.140382] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.140473] system 00:01: [io  0x04d0-0x04d1] has been reserved
[    0.140475] system 00:01: [io  0x0295-0x0314] has been reserved
[    0.140476] system 00:01: [io  0x0880-0x088f] has been reserved
[    0.140478] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.140486] pnp 00:02: [dma 4]
[    0.140501] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.140554] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.140583] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.140601] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.140623] pnp 00:06: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.140701] pnp 00:07: [dma 2]
[    0.140722] pnp 00:07: Plug and Play ACPI device, IDs PNP0700 (active)
[    0.140861] pnp 00:08: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.140919] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.141313] system 00:0a: [mem 0xe0000000-0xefffffff] has been reserved
[    0.141316] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.141420] system 00:0b: [mem 0x000d0000-0x000d3fff] has been reserved
[    0.141422] system 00:0b: [mem 0x000d5800-0x000d7fff] has been reserved
[    0.141424] system 00:0b: [mem 0x000f0000-0x000fbfff] could not be reserved
[    0.141425] system 00:0b: [mem 0x000fc000-0x000fffff] could not be reserved
[    0.141427] system 00:0b: [mem 0xafef0000-0xafefffff] could not be reserved
[    0.141429] system 00:0b: [mem 0xffff0000-0xffffffff] has been reserved
[    0.141430] system 00:0b: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.141432] system 00:0b: [mem 0x00100000-0xafeeffff] could not be reserved
[    0.141434] system 00:0b: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.141435] system 00:0b: [mem 0xd0000000-0xdfffffff] has been reserved
[    0.141438] system 00:0b: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.141440] system 00:0b: [mem 0xfeff0000] has been reserved
[    0.141442] system 00:0b: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.141447] pnp: PnP ACPI: found 12 devices
[    0.141448] ACPI: bus type PNP unregistered
[    0.147773] pci 0000:03:00.0: BAR 6: assigned [mem 0xcd000000-0xcd01ffff pref]
[    0.147776] pci 0000:02:00.0: PCI bridge to [bus 03]
[    0.147778] pci 0000:02:00.0:   bridge window [io  0x9000-0x9fff]
[    0.147782] pci 0000:02:00.0:   bridge window [mem 0xca000000-0xcdffffff]
[    0.147784] pci 0000:02:00.0:   bridge window [mem 0xb0000000-0xbfffffff 64bit pref]
[    0.147788] pci 0000:02:02.0: PCI bridge to [bus 04]
[    0.147796] pci 0000:01:00.0: PCI bridge to [bus 02-04]
[    0.147798] pci 0000:01:00.0:   bridge window [io  0x9000-0x9fff]
[    0.147801] pci 0000:01:00.0:   bridge window [mem 0xca000000-0xcdffffff]
[    0.147804] pci 0000:01:00.0:   bridge window [mem 0xb0000000-0xbfffffff 64bit pref]
[    0.147808] pci 0000:00:03.0: PCI bridge to [bus 01-04]
[    0.147809] pci 0000:00:03.0:   bridge window [io  0x9000-0x9fff]
[    0.147812] pci 0000:00:03.0:   bridge window [mem 0xca000000-0xcdffffff]
[    0.147814] pci 0000:00:03.0:   bridge window [mem 0xb0000000-0xbfffffff 64bit pref]
[    0.147817] pci 0000:00:0f.0: PCI bridge to [bus 05]
[    0.147819] pci 0000:00:0f.0:   bridge window [mem 0xcfe00000-0xcfefffff]
[    0.147823] pci 0000:00:13.0: PCI bridge to [bus 06]
[    0.147841] pci 0000:00:0f.0: setting latency timer to 64
[    0.147846] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.147847] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.147849] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.147850] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000dffff]
[    0.147851] pci_bus 0000:00: resource 8 [mem 0xaff00000-0xcfffffff]
[    0.147853] pci_bus 0000:01: resource 0 [io  0x9000-0x9fff]
[    0.147855] pci_bus 0000:01: resource 1 [mem 0xca000000-0xcdffffff]
[    0.147856] pci_bus 0000:01: resource 2 [mem 0xb0000000-0xbfffffff 64bit pref]
[    0.147857] pci_bus 0000:02: resource 0 [io  0x9000-0x9fff]
[    0.147859] pci_bus 0000:02: resource 1 [mem 0xca000000-0xcdffffff]
[    0.147860] pci_bus 0000:02: resource 2 [mem 0xb0000000-0xbfffffff 64bit pref]
[    0.147862] pci_bus 0000:03: resource 0 [io  0x9000-0x9fff]
[    0.147863] pci_bus 0000:03: resource 1 [mem 0xca000000-0xcdffffff]
[    0.147865] pci_bus 0000:03: resource 2 [mem 0xb0000000-0xbfffffff 64bit pref]
[    0.147866] pci_bus 0000:05: resource 1 [mem 0xcfe00000-0xcfefffff]
[    0.147868] pci_bus 0000:05: resource 4 [io  0x0000-0x0cf7]
[    0.147869] pci_bus 0000:05: resource 5 [io  0x0d00-0xffff]
[    0.147870] pci_bus 0000:05: resource 6 [mem 0x000a0000-0x000bffff]
[    0.147872] pci_bus 0000:05: resource 7 [mem 0x000c0000-0x000dffff]
[    0.147873] pci_bus 0000:05: resource 8 [mem 0xaff00000-0xcfffffff]
[    0.147900] NET: Registered protocol family 2
[    0.148066] TCP established hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.148550] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.149003] TCP: Hash tables configured (established 65536 bind 65536)
[    0.149064] TCP: reno registered
[    0.149072] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.149131] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.149227] NET: Registered protocol family 1
[    0.149504] ACPI: PCI Interrupt Link [AUBA] enabled at IRQ 23
[    0.220269] ACPI: PCI Interrupt Link [AUS2] enabled at IRQ 22
[    0.220481] pci 0000:03:00.0: Boot video device
[    0.220485] PCI: CLS 64 bytes, default 64
[    0.220521] Trying to unpack rootfs image as initramfs...
[    0.525047] Freeing initrd memory: 24276K (ffff880035086000 - ffff88003683b000)
[    0.525057] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.525059] software IO TLB [mem 0xabef0000-0xafef0000] (64MB) mapped at [ffff8800abef0000-ffff8800afeeffff]
[    0.525215] Scanning for low memory corruption every 60 seconds
[    0.525463] Initialise module verification
[    0.525500] audit: initializing netlink socket (disabled)
[    0.525516] type=2000 audit(1383557888.524:1): initialized
[    0.545208] bounce pool size: 64 pages
[    0.545217] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.546342] zbud: loaded
[    0.546429] VFS: Disk quotas dquot_6.5.2
[    0.546459] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.546822] fuse init (API version 7.22)
[    0.546879] msgmni has been set to 15962
[    0.547289] Key type asymmetric registered
[    0.547291] Asymmetric key parser 'x509' registered
[    0.547314] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.547339] io scheduler noop registered
[    0.547341] io scheduler deadline registered (default)
[    0.547359] io scheduler cfq registered
[    0.547460] pcieport 0000:00:03.0: irq 40 for MSI/MSI-X
[    0.547505] pcieport 0000:00:13.0: irq 41 for MSI/MSI-X
[    0.547622] pcieport 0000:00:03.0: Signaling PME through PCIe PME interrupt
[    0.547624] pcieport 0000:01:00.0: Signaling PME through PCIe PME interrupt
[    0.547625] pcieport 0000:02:00.0: Signaling PME through PCIe PME interrupt
[    0.547627] pci 0000:03:00.0: Signaling PME through PCIe PME interrupt
[    0.547628] pcieport 0000:02:02.0: Signaling PME through PCIe PME interrupt
[    0.547630] pcie_pme 0000:00:03.0:pcie01: service driver pcie_pme loaded
[    0.547640] pcieport 0000:00:13.0: Signaling PME through PCIe PME interrupt
[    0.547643] pcie_pme 0000:00:13.0:pcie01: service driver pcie_pme loaded
[    0.547652] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.547662] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.547713] intel_idle: does not run on family 6 model 23
[    0.547780] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.547784] ACPI: Power Button [PWRB]
[    0.547820] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.547822] ACPI: Power Button [PWRF]
[    0.547922] GHES: HEST is not enabled!
[    0.547980] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.568366] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.569438] Linux agpgart interface v0.103
[    0.570414] brd: module loaded
[    0.570908] loop: module loaded
[    0.571148] libphy: Fixed MDIO Bus: probed
[    0.571205] tun: Universal TUN/TAP device driver, 1.6
[    0.571206] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.571236] PPP generic driver version 2.4.2
[    0.571270] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.571271] ehci-pci: EHCI PCI platform driver
[    0.571387] ehci-pci 0000:00:0b.1: setting latency timer to 64
[    0.571395] ehci-pci 0000:00:0b.1: EHCI Host Controller
[    0.571400] ehci-pci 0000:00:0b.1: new USB bus registered, assigned bus number 1
[    0.571406] ehci-pci 0000:00:0b.1: debug port 1
[    0.571425] ehci-pci 0000:00:0b.1: cache line size of 64 is not supported
[    0.571437] ehci-pci 0000:00:0b.1: irq 22, io mem 0xcfffe000
[    0.580018] ehci-pci 0000:00:0b.1: USB 2.0 started, EHCI 1.00
[    0.580046] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.580047] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.580049] usb usb1: Product: EHCI Host Controller
[    0.580050] usb usb1: Manufacturer: Linux 3.11.0-12-generic ehci_hcd
[    0.580052] usb usb1: SerialNumber: 0000:00:0b.1
[    0.580115] hub 1-0:1.0: USB hub found
[    0.580119] hub 1-0:1.0: 10 ports detected
[    0.580226] ehci-platform: EHCI generic platform driver
[    0.580231] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.580232] ohci-platform: OHCI generic platform driver
[    0.580236] uhci_hcd: USB Universal Host Controller Interface driver
[    0.580274] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    0.582867] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.582871] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.582956] mousedev: PS/2 mouse device common for all mice
[    0.583058] rtc_cmos 00:04: RTC can wake from S4
[    0.583180] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.583209] rtc_cmos 00:04: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    0.583246] device-mapper: uevent: version 1.0.3
[    0.583289] device-mapper: ioctl: 4.25.0-ioctl (2013-06-26) initialised: dm-devel@redhat.com
[    0.583294] cpuidle: using governor ladder
[    0.583295] cpuidle: using governor menu
[    0.583302] ledtrig-cpu: registered to indicate activity on CPUs
[    0.583356] TCP: cubic registered
[    0.583420] NET: Registered protocol family 10
[    0.583553] NET: Registered protocol family 17
[    0.583558] Key type dns_resolver registered
[    0.583703] PM: Hibernation image not present or could not be loaded.
[    0.583706] Loading module verification certificates
[    0.584417] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: fddf6943d8ac4f5b6eb0919a7a3ee3d9088b1bfa'
[    0.584425] registered taskstats version 1
[    0.586217] Key type trusted registered
[    0.587492] Key type encrypted registered
[    0.588721] AppArmor: AppArmor sha1 policy hashing enabled
[    0.588973]   Magic number: 5:863:625
[    0.589070] rtc_cmos 00:04: setting system clock to 2013-11-04 09:38:09 UTC (1383557889)
[    0.589113] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.589114] EDD information not available.
[    0.590161] Freeing unused kernel memory: 1364K (ffffffff81d10000 - ffffffff81e65000)
[    0.590163] Write protecting the kernel read-only data: 12288k
[    0.592136] Freeing unused kernel memory: 1040K (ffff8800016fc000 - ffff880001800000)
[    0.593583] Freeing unused kernel memory: 836K (ffff880001b2f000 - ffff880001c00000)
[    0.601702] systemd-udevd[104]: starting version 204
[    0.618227] pata_amd 0000:00:0d.0: version 0.4.1
[    0.618273] pata_amd 0000:00:0d.0: setting latency timer to 64
[    0.618693] scsi0 : pata_amd
[    0.619535] scsi1 : pata_amd
[    0.619649] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xec00 irq 14
[    0.619651] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xec08 irq 15
[    0.619773] sata_nv 0000:00:0e.0: version 3.5
[    0.619962] ACPI: PCI Interrupt Link [ASA0] enabled at IRQ 21
[    0.619973] sata_nv 0000:00:0e.0: Using SWNCQ mode
[    0.620148] sata_nv 0000:00:0e.0: setting latency timer to 64
[    0.620420] scsi2 : sata_nv
[    0.620473] scsi3 : sata_nv
[    0.620511] ata3: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd800 irq 21
[    0.620512] ata4: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd808 irq 21
[    0.620682] ACPI: PCI Interrupt Link [ASA1] enabled at IRQ 20
[    0.620688] sata_nv 0000:00:0e.1: Using SWNCQ mode
[    0.620713] sata_nv 0000:00:0e.1: setting latency timer to 64
[    0.620891] scsi4 : sata_nv
[    0.620937] scsi5 : sata_nv
[    0.620974] ata5: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xc400 irq 20
[    0.620976] ata6: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xc408 irq 20
[    0.621141] ACPI: PCI Interrupt Link [ASA2] enabled at IRQ 21
[    0.621144] sata_nv 0000:00:0e.2: Using SWNCQ mode
[    0.621166] sata_nv 0000:00:0e.2: setting latency timer to 64
[    0.621349] scsi6 : sata_nv
[    0.621394] scsi7 : sata_nv
[    0.621430] ata7: SATA max UDMA/133 cmd 0xc000 ctl 0xbc00 bmdma 0xb000 irq 21
[    0.621432] ata8: SATA max UDMA/133 cmd 0xb800 ctl 0xb400 bmdma 0xb008 irq 21
[    0.626770] floppy: module verification failed: signature and/or required key missing - tainting kernel
[    0.629467] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    0.629671] ACPI: PCI Interrupt Link [AMAC] enabled at IRQ 23
[    0.629676] forcedeth 0000:00:11.0: setting latency timer to 64
[    0.630773] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[    0.643963] FDC 0 is a post-1991 82077
[    0.692035] firewire_ohci 0000:05:07.0: added OHCI v1.10 device as card 0, 4 IR + 8 IT contexts, quirks 0x2
[    0.936026] ata5: SATA link down (SStatus 0 SControl 300)
[    0.936044] ata3: SATA link down (SStatus 0 SControl 300)
[    0.972271] ata1.01: ATAPI: LITE-ON DVDRW LH-20A1H, LL0A, max UDMA/66
[    0.972276] ata1: nv_mode_filter: 0x1f39f&0x1f39f->0x1f39f, BIOS=0x1f000 (0xc50000) ACPI=0x1f01f (600:30:0x1c)
[    0.972277] ata1.01: limited to UDMA/33 due to 40-wire cable
[    1.004198] ata1.01: configured for UDMA/33
[    1.005917] scsi 0:0:1:0: CD-ROM            LITE-ON  DVDRW LH-20A1H   LL0A PQ: 0 ANSI: 5
[    1.008603] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.008605] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.008675] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    1.008738] sr 0:0:1:0: Attached scsi generic sg0 type 5
[    1.008788] ata2: port disabled--ignoring
[    1.092024] ata7: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.114155] ata7.00: ATA-7: WDC WD3200KS-00PFB0, 21.00M21, max UDMA/133
[    1.114157] ata7.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 1)
[    1.120274] ata7.00: configured for UDMA/133
[    1.152461] forcedeth 0000:00:11.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:04:4b:15:79:5e
[    1.152463] forcedeth 0000:00:11.0: highdma csum vlan pwrctl mgmt gbit lnktim msi desc-v3
[    1.152673] ACPI: PCI Interrupt Link [AMA1] enabled at IRQ 22
[    1.152678] forcedeth 0000:00:12.0: setting latency timer to 64
[    1.192067] firewire_core 0000:05:07.0: created device fw0: GUID 5ad15c4c00044b16, S400
[    1.320026] ata4: SATA link down (SStatus 0 SControl 300)
[    1.524022] tsc: Refined TSC clocksource calibration: 3600.000 MHz
[    1.676432] forcedeth 0000:00:12.0: ifname eth1, PHY OUI 0x5043 @ 2, addr 00:04:4b:15:79:5f
[    1.676434] forcedeth 0000:00:12.0: highdma csum vlan pwrctl mgmt gbit lnktim msi desc-v3
[    1.788023] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.838912] ata6.00: ATA-7: ST3500630AS, 3.AAE, max UDMA/133
[    1.838914] ata6.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.905547] ata6.00: configured for UDMA/133
[    1.905612] scsi 5:0:0:0: Direct-Access     ATA      ST3500630AS      3.AA PQ: 0 ANSI: 5
[    1.905707] sd 5:0:0:0: Attached scsi generic sg1 type 0
[    1.905752] sd 5:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.905793] sd 5:0:0:0: [sda] Write Protect is off
[    1.905795] sd 5:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.905813] sd 5:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.906171] scsi 6:0:0:0: Direct-Access     ATA      WDC WD3200KS-00P 21.0 PQ: 0 ANSI: 5
[    1.906264] sd 6:0:0:0: [sdb] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.906306] sd 6:0:0:0: [sdb] Write Protect is off
[    1.906308] sd 6:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.906325] sd 6:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.906369] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    1.913378]  sdb: sdb1
[    1.913525] sd 6:0:0:0: [sdb] Attached SCSI disk
[    1.975363]  sda: sda1 sda2 < sda5 sda6 >
[    1.975589] sd 5:0:0:0: [sda] Attached SCSI disk
[    2.216018] ata8: SATA link down (SStatus 0 SControl 300)
[    2.524056] Switched to clocksource tsc
[    8.816996] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    8.816999] EXT4-fs (sda1): write access will be enabled during recovery
[   10.661548] EXT4-fs (sda1): recovery complete
[   10.688701] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   17.343760] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.343765] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   17.435899] systemd-udevd[319]: starting version 204
[   17.632668] lp: driver loaded but no devices found
[   17.651480] i2c i2c-0: nForce2 SMBus adapter at 0xf400
[   17.651500] i2c i2c-1: nForce2 SMBus adapter at 0xf000
[   17.652573] nv_tco: NV TCO WatchDog Timer Driver v0.01
[   17.652692] nv_tco: Watchdog reboot detected
[   17.654274] ohci-pci: OHCI PCI platform driver
[   17.654428] ohci-pci 0000:00:0b.0: setting latency timer to 64
[   17.654431] ohci-pci 0000:00:0b.0: OHCI PCI host controller
[   17.654435] ohci-pci 0000:00:0b.0: new USB bus registered, assigned bus number 2
[   17.654459] ohci-pci 0000:00:0b.0: irq 23, io mem 0xcffff000
[   17.654651] nv_tco: initialized (0x1440). heartbeat=30 sec (nowayout=0)
[   17.679770] [drm] Initialized drm 1.1.0 20060810
[   17.692522] nvidia: module license 'NVIDIA' taints kernel.
[   17.692526] Disabling lock debugging due to kernel taint
[   17.730855] type=1400 audit(1383575906.638:2): apparmor="STATUS" operation="profile_load" parent=357 profile="unconfined" name="/sbin/dhclient" pid=361 comm="apparmor_parser"
[   17.730860] type=1400 audit(1383575906.638:3): apparmor="STATUS" operation="profile_load" parent=357 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=361 comm="apparmor_parser"
[   17.730864] type=1400 audit(1383575906.638:4): apparmor="STATUS" operation="profile_load" parent=357 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=361 comm="apparmor_parser"
[   17.730870] type=1400 audit(1383575906.638:5): apparmor="STATUS" operation="profile_replace" parent=353 profile="unconfined" name="/sbin/dhclient" pid=360 comm="apparmor_parser"
[   17.730875] type=1400 audit(1383575906.638:6): apparmor="STATUS" operation="profile_replace" parent=353 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=360 comm="apparmor_parser"
[   17.730878] type=1400 audit(1383575906.638:7): apparmor="STATUS" operation="profile_replace" parent=353 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=360 comm="apparmor_parser"
[   17.731248] type=1400 audit(1383575906.638:8): apparmor="STATUS" operation="profile_replace" parent=357 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=361 comm="apparmor_parser"
[   17.731251] type=1400 audit(1383575906.638:9): apparmor="STATUS" operation="profile_replace" parent=357 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=361 comm="apparmor_parser"
[   17.731260] type=1400 audit(1383575906.638:10): apparmor="STATUS" operation="profile_replace" parent=353 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=360 comm="apparmor_parser"
[   17.731264] type=1400 audit(1383575906.638:11): apparmor="STATUS" operation="profile_replace" parent=353 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=360 comm="apparmor_parser"
[   17.734509] microcode: CPU0 sig=0x1067a, pf=0x1, revision=0xa07
[   17.737797] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[   17.737800] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[   17.737802] usb usb2: Product: OHCI PCI host controller
[   17.737803] usb usb2: Manufacturer: Linux 3.11.0-12-generic ohci_hcd
[   17.737805] usb usb2: SerialNumber: 0000:00:0b.0
[   17.737915] hub 2-0:1.0: USB hub found
[   17.737920] hub 2-0:1.0: 10 ports detected
[   17.750889] ACPI: PCI Interrupt Link [AXV5] enabled at IRQ 16
[   17.750906] vgaarb: device changed decodes: PCI:0000:03:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   17.751206] [drm] Initialized nvidia-drm 0.0.0 20130102 for 0000:03:00.0 on minor 0
[   17.751226] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  319.32  Wed Jun 19 15:51:20 PDT 2013
[   17.779014] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 23
[   17.779022] hda_intel: Disabling MSI
[   17.779049] snd_hda_intel 0000:00:0f.1: setting latency timer to 64
[   17.779052] hda-intel 0000:00:0f.1: Disabling 64bit DMA
[   17.783418] hda-intel 0000:00:0f.1: Enable delay in RIRB handling
[   18.109196] microcode: CPU1 sig=0x1067a, pf=0x1, revision=0xa07
[   18.111319] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   18.112036] usb 2-3: new full-speed USB device number 2 using ohci-pci
[   18.340491] usb 2-3: New USB device found, idVendor=046d, idProduct=c041
[   18.340494] usb 2-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[   18.340495] usb 2-3: Product: USB Gaming Mouse
[   18.340497] usb 2-3: Manufacturer: Logitech
[   18.400018] SKU: Nid=0x0 sku_cfg=0x00000175
[   18.400019] SKU: port_connectivity=0x0
[   18.400020] SKU: enable_pcbeep=0x1
[   18.400021] SKU: check_sum=0x00000000
[   18.400022] SKU: customization=0x00000000
[   18.400023] SKU: external_amp=0x6
[   18.400024] SKU: platform_type=0x1
[   18.400025] SKU: swap=0x0
[   18.400025] SKU: override=0x1
[   18.488006] autoconfig: line_outs=4 (0x14/0x15/0x16/0x17/0x0) type:line
[   18.488008]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   18.488009]    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[   18.488010]    mono: mono_out=0x0
[   18.488011]    dig-out=0x11/0x1e
[   18.488011]    inputs:
[   18.488013]      Front Mic=0x19
[   18.488014]      Rear Mic=0x18
[   18.488015]      Line=0x1a
[   18.488016]    dig-in=0x1f
[   18.488017] realtek: Enabling init ASM_ID=0x0175 CODEC_ID=10ec0888
[   18.520008] usb 2-4: new low-speed USB device number 3 using ohci-pci
[   18.750489] usb 2-4: New USB device found, idVendor=045e, idProduct=00b0
[   18.750492] usb 2-4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[   18.750493] usb 2-4: Product: Microsoft\xffffffc2\xffffffae\xffffffae Digital Media Pro Keyboard
[   18.750495] usb 2-4: Manufacturer: Microsoft
[   18.771326] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   19.493398] hidraw: raw HID events driver (C) Jiri Kosina
[   19.527756] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[   19.537533] usbcore: registered new interface driver usbhid
[   19.537535] usbhid: USB HID core driver
[   19.540367] input: Logitech USB Gaming Mouse as /devices/pci0000:00/0000:00:0b.0/usb2/2-3/2-3:1.0/input/input2
[   19.541352] hid-generic 0003:046D:C041.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Gaming Mouse] on usb-0000:00:0b.0-3/input0
[   19.544617] hid-generic 0003:046D:C041.0002: hiddev0,hidraw1: USB HID v1.11 Device [Logitech USB Gaming Mouse] on usb-0000:00:0b.0-3/input1
[   19.545277] input: Microsoft Microsoft\xffffffc2\xffffffae\xffffffae Digital Media Pro Keyboard as /devices/pci0000:00/0000:00:0b.0/usb2/2-4/2-4:1.0/input/input3
[   19.545375] hid-generic 0003:045E:00B0.0003: input,hidraw2: USB HID v1.11 Keyboard [Microsoft Microsoft\xffffffc2\xffffffae\xffffffae Digital Media Pro Keyboard] on usb-0000:00:0b.0-4/input0
[   19.549645] input: Microsoft Microsoft\xffffffc2\xffffffae\xffffffae Digital Media Pro Keyboard as /devices/pci0000:00/0000:00:0b.0/usb2/2-4/2-4:1.1/input/input4
[   19.549718] hid-generic 0003:045E:00B0.0004: input,hidraw3: USB HID v1.11 Device [Microsoft Microsoft\xffffffc2\xffffffae\xffffffae Digital Media Pro Keyboard] on usb-0000:00:0b.0-4/input1
[   19.635238] init: failsafe main process (589) killed by TERM signal
[   19.926936] Bluetooth: Core ver 2.16
[   19.926955] NET: Registered protocol family 31
[   19.926956] Bluetooth: HCI device and connection manager initialized
[   19.926964] Bluetooth: HCI socket layer initialized
[   19.926967] Bluetooth: L2CAP socket layer initialized
[   19.926971] Bluetooth: SCO socket layer initialized
[   19.929580] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.929582] Bluetooth: BNEP filters: protocol multicast
[   19.929587] Bluetooth: BNEP socket layer initialized
[   19.930810] Bluetooth: RFCOMM TTY layer initialized
[   19.930815] Bluetooth: RFCOMM socket layer initialized
[   19.930816] Bluetooth: RFCOMM ver 1.11
[   20.253738] init: avahi-cups-reload main process (726) terminated with status 1
[   20.300827] ppdev: user-space parallel port driver
[   20.384097] input: HDA NVidia Front Headphone as /devices/pci0000:00/0000:00:0f.1/sound/card0/input5
[   20.384145] input: HDA NVidia Line Out Side as /devices/pci0000:00/0000:00:0f.1/sound/card0/input6
[   20.384186] input: HDA NVidia Line Out CLFE as /devices/pci0000:00/0000:00:0f.1/sound/card0/input7
[   20.384223] input: HDA NVidia Line Out Surround as /devices/pci0000:00/0000:00:0f.1/sound/card0/input8
[   20.384263] input: HDA NVidia Line Out Front as /devices/pci0000:00/0000:00:0f.1/sound/card0/input9
[   20.384300] input: HDA NVidia Line as /devices/pci0000:00/0000:00:0f.1/sound/card0/input10
[   20.384337] input: HDA NVidia Rear Mic as /devices/pci0000:00/0000:00:0f.1/sound/card0/input11
[   20.384375] input: HDA NVidia Front Mic as /devices/pci0000:00/0000:00:0f.1/sound/card0/input12
[   22.939932] init: udev-fallback-graphics main process (995) terminated with status 1
[   22.967883] forcedeth 0000:00:11.0: irq 42 for MSI/MSI-X
[   22.967906] forcedeth 0000:00:11.0 eth0: MSI enabled
[   22.968124] forcedeth 0000:00:11.0 eth0: no link during initialization
[   22.968535] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   22.968947] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   22.971005] forcedeth 0000:00:12.0: irq 43 for MSI/MSI-X
[   22.971019] forcedeth 0000:00:12.0 eth1: MSI enabled
[   25.150656] bio: create slab <bio-1> at 1
[   25.586338] Adding 4692988k swap on /dev/mapper/cryptswap1.  Priority:-1 extents:1 across:4692988k FS
christopher@christopher-132-CK-NF78:~$ 
        
```



Here it is. :confused:

---

### Post by Bucky Ball on 2013-11-04
Couldn't spot anything, but then, I'm about to go to bed and pretty tired. ;)

Are you seeing scrolling code when you boot or when are you seeing it? It is not 'failsafe mode' is it? If so, that's fine.

---

### Post by Christopher on 2013-11-04
> **Bucky Ball said:**
> Couldn't spot anything, but then, I'm about to go to bed and pretty tired. ;)

Are you seeing scrolling code when you boot or when are you seeing it? It is not 'failsafe mode' is it? If so, that's fine.



Seeing it when i boot(right after it says Ubuntu 13.10), not sure if its fail safe mode. Is there a way to stop it so i can read it fully?

---

### Post by Bucky Ball on 2013-11-04
You could try booting the recovery kernel (should be second on the list). That might give you a better look. Drop to a shell when that give you the option and run dmesg there.

---

### Post by Christopher on 2013-11-05
> **Bucky Ball said:**
> You could try booting the recovery kernel (should be second on the list). That might give you a better look. Drop to a shell when that give you the option and run dmesg there.


Awesome thank you, i will try this.

---

