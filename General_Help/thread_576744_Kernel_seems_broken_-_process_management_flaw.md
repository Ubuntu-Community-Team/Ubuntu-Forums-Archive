---
title: "Kernel seems broken - process management flaw"
date: 2007-10-15
forum: General Help
---

### Post by SeanTater on 2007-10-15
These programs all halt, becoming unresponsive, though outside of these incidents, I have never had them become unresponsive:
[LIST] [*]killall[*]pidof
[*]htop
[*]ksysguard
[*]k3b, shortly after trying to burn a cd
[/LIST]

Interestingly, "top" works. I don't know if kill works, but -9 when applied to the processes listed above had no effect.

At this same time, the kernel module bttv can no longer be removed. It seems to occur shortly after quitting  "kdetv". When rebooting or shutting down the computer following this, it does not fully turn off and a hard reboot is required.

This is what dmesg says
```

[    0.000001] CPU#0 had -182 usecs TSC skew, fixed it up.
[    0.000002] CPU#1 had 182 usecs TSC skew, fixed it up.
[    0.003993] Brought up 2 CPUs
[    0.031750] migration_cost=186
[    0.031943] Booting paravirtualized kernel on bare hardware
[    0.032005] Time:  0:09:07  Date: 09/15/107
[    0.032028] NET: Registered protocol family 16
[    0.032089] EISA bus registered
[    0.032091] ACPI: bus type pci registered
[    0.038424] PCI: PCI BIOS revision 3.00 entry at 0xf21e0, last bus=4
[    0.038426] PCI: Using configuration type 1
[    0.038427] Setting up standard PCI resources
[    0.047789] ACPI: Interpreter enabled
[    0.047791] ACPI: Using IOAPIC for interrupt routing
[    0.048326] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.048330] PCI: Probing PCI hardware (bus 00)
[    0.050871] Boot video device is 0000:03:00.0
[    0.051069] PCI: Transparent bridge - 0000:00:10.0
[    0.051098] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.136618] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.141190] ACPI: PCI Interrupt Link [LNK1] (IRQs *5 7 9 10 11 14 15)
[    0.141569] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 *10 11 14 15)
[    0.141952] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.142332] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.142709] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 *11 14 15)
[    0.143086] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.143465] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.143845] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.144222] ACPI: PCI Interrupt Link [LUBA] (IRQs *5 7 9 10 11 14 15)
[    0.144598] ACPI: PCI Interrupt Link [LUBB] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.144977] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 10 *11 14 15)
[    0.145356] ACPI: PCI Interrupt Link [LACI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.145734] ACPI: PCI Interrupt Link [LAZA] (IRQs *5 7 9 10 11 14 15)
[    0.146113] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.146495] ACPI: PCI Interrupt Link [LMCI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.146873] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 10 *11 14 15)
[    0.147250] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 *10 11 14 15)
[    0.147629] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.148010] ACPI: PCI Interrupt Link [LSID] (IRQs *5 7 9 10 11 14 15)
[    0.148389] ACPI: PCI Interrupt Link [LFID] (IRQs *5 7 9 10 11 14 15)
[    0.148829] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[    0.149261] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[    0.149693] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[    0.150124] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[    0.150555] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
[    0.150986] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
[    0.151423] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
[    0.151856] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
[    0.152287] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0, disabled.
[    0.152719] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
[    0.153152] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0, disabled.
[    0.153582] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0, disabled.
[    0.154013] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
[    0.154445] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0, disabled.
[    0.154878] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
[    0.155309] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0, disabled.
[    0.155741] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0, disabled.
[    0.156173] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[    0.156608] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[    0.157040] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0, disabled.
[    0.157472] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0, disabled.
[    0.157754] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.157761] pnp: PnP ACPI init
[    0.165350] pnp: PnP ACPI: found 14 devices
[    0.165353] PnPBIOS: Disabled by ACPI PNP
[    0.165396] PCI: Using ACPI for IRQ routing
[    0.165399] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.254866] NET: Registered protocol family 8
[    0.254867] NET: Registered protocol family 20
[    0.255344] pnp: 00:01: ioport range 0x4000-0x407f could not be reserved
[    0.255347] pnp: 00:01: ioport range 0x4080-0x40ff has been reserved
[    0.255349] pnp: 00:01: ioport range 0x4400-0x447f has been reserved
[    0.255351] pnp: 00:01: ioport range 0x4480-0x44ff could not be reserved
[    0.255353] pnp: 00:01: ioport range 0x4800-0x487f has been reserved
[    0.255355] pnp: 00:01: ioport range 0x4880-0x48ff has been reserved
[    0.255357] pnp: 00:01: ioport range 0x2000-0x207f has been reserved
[    0.255359] pnp: 00:01: ioport range 0x2080-0x20ff has been reserved
[    0.255559] PCI: Bridge: 0000:00:02.0
[    0.255561]   IO window: a000-afff
[    0.255564]   MEM window: fdd00000-fddfffff
[    0.255566]   PREFETCH window: fda00000-fdafffff
[    0.255568] PCI: Bridge: 0000:00:03.0
[    0.255569]   IO window: 8000-8fff
[    0.255572]   MEM window: fd900000-fd9fffff
[    0.255573]   PREFETCH window: fde00000-fdefffff
[    0.255576] PCI: Bridge: 0000:00:04.0
[    0.255577]   IO window: b000-bfff
[    0.255579]   MEM window: fa000000-fcffffff
[    0.255581]   PREFETCH window: d0000000-dfffffff
[    0.255584] PCI: Bridge: 0000:00:10.0
[    0.255585]   IO window: 9000-9fff
[    0.255588]   MEM window: fdc00000-fdcfffff
[    0.255590]   PREFETCH window: fdb00000-fdbfffff
[    0.255600] PCI: Setting latency timer of device 0000:00:02.0 to 64
[    0.255605] PCI: Setting latency timer of device 0000:00:03.0 to 64
[    0.255610] PCI: Setting latency timer of device 0000:00:04.0 to 64
[    0.255616] PCI: Setting latency timer of device 0000:00:10.0 to 64
[    0.255641] NET: Registered protocol family 2
[    0.303491] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.303618] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.304214] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.304473] TCP: Hash tables configured (established 131072 bind 65536)
[    0.304475] TCP reno registered
[    0.315515] checking if image is initramfs... it is
[    0.750606] Freeing initrd memory: 6774k freed
[    1.216000] audit: initializing netlink socket (disabled)
[    1.216000] audit(1192406947.400:1): initialized
[    1.216000] highmem bounce pool size: 64 pages
[    1.216000] VFS: Disk quotas dquot_6.5.1
[    1.216000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.216000] io scheduler noop registered
[    1.216000] io scheduler anticipatory registered
[    1.216000] io scheduler deadline registered
[    1.216000] io scheduler cfq registered (default)
[    1.236000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[    1.236000] assign_interrupt_mode Found MSI capability
[    1.236000] Allocate Port Service[0000:00:02.0:pcie00]
[    1.236000] PCI: Setting latency timer of device 0000:00:03.0 to 64
[    1.236000] assign_interrupt_mode Found MSI capability
[    1.236000] Allocate Port Service[0000:00:03.0:pcie00]
[    1.236000] PCI: Setting latency timer of device 0000:00:04.0 to 64
[    1.236000] assign_interrupt_mode Found MSI capability
[    1.236000] Allocate Port Service[0000:00:04.0:pcie00]
[    1.236000] isapnp: Scanning for PnP cards...
[    1.588000] isapnp: No Plug & Play device found
[    1.604000] Real Time Clock Driver v1.12ac
[    1.604000] hpet_resources: 0xfefff000 is busy
[    1.604000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.604000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.604000] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.604000] mice: PS/2 mouse device common for all mice
[    1.604000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.604000] input: Macintosh mouse button emulation as /class/input/input0
[    1.604000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    1.604000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    1.604000] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    1.604000] PNP: PS/2 controller doesn't have AUX irq; using default 12
[    1.608000] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.608000] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.608000] EISA: Probing bus 0 at eisa.0
[    1.608000] Cannot allocate resource for EISA slot 2
[    1.608000] Cannot allocate resource for EISA slot 4
[    1.608000] Cannot allocate resource for EISA slot 8
[    1.608000] EISA: Detected 0 cards.
[    1.636000] TCP cubic registered
[    1.636000] NET: Registered protocol family 1
[    1.636000] Starting balanced_irq
[    1.636000] Using IPI No-Shortcut mode
[    1.636000] ACPI: (supports S0 S1 S3 S4 S5)
[    1.636000]   Magic number: 11:762:152
[    1.636000]   hash matches device ttyp6
[    1.636000] Freeing unused kernel memory: 328k freed
[    1.640000] Time: hpet clocksource has been installed.
[    1.648000] input: AT Translated Set 2 keyboard as /class/input/input1
[    2.828000] Capability LSM initialized
[    2.856000] ACPI: Fan [FAN] (on)
[    2.860000] ACPI: Thermal Zone [THRM] (40 C)
[    3.236000] usbcore: registered new interface driver usbfs
[    3.236000] usbcore: registered new interface driver hub
[    3.236000] usbcore: registered new device driver usb
[    3.236000] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.236000] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 23
[    3.236000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [APCF] -> GSI 23 (level, low) -> IRQ 16
[    3.236000] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[    3.236000] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[    3.236000] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
[    3.236000] ohci_hcd 0000:00:0b.0: irq 16, io mem 0xfe02f000
[    3.300000] usb usb1: configuration #1 chosen from 1 choice
[    3.300000] hub 1-0:1.0: USB hub found
[    3.300000] hub 1-0:1.0: 8 ports detected
[    3.304000] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.59.
[    3.348000] Floppy drive(s): fd0 is 1.44M
[    3.368000] FDC 0 is a post-1991 82077
[    3.408000] NFORCE-MCP51: IDE controller at PCI slot 0000:00:0d.0
[    3.408000] NFORCE-MCP51: chipset revision 161
[    3.408000] NFORCE-MCP51: not 100% native mode: will probe irqs later
[    3.408000] NFORCE-MCP51: 0000:00:0d.0 (rev a1) UDMA133 controller
[    3.408000]     ide0: BM-DMA at 0xf400-0xf407, BIOS settings: hda:DMA, hdb:DMA
[    3.408000]     ide1: BM-DMA at 0xf408-0xf40f, BIOS settings: hdc:DMA, hdd:DMA
[    3.408000] Probing IDE interface ide0...
[    3.416000] SCSI subsystem initialized
[    3.420000] libata version 2.20 loaded.
[    3.704000] hda: SAMSUNG SP1604N, ATA DISK drive
[    3.712000] usb 1-2: new low speed USB device using ohci_hcd and address 2
[    3.920000] usb 1-2: configuration #1 chosen from 1 choice
[    3.932000] usbcore: registered new interface driver hiddev
[    3.936000] input: Logitech USB-PS/2 Optical Mouse as /class/input/input2
[    3.936000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:0b.0-2
[    3.936000] usbcore: registered new interface driver usbhid
[    3.936000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[    4.380000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    4.388000] Probing IDE interface ide1...
[    5.128000] hdc: LITE-ON LTR-16102B, ATAPI CD/DVD-ROM drive
[    5.916000] hdd: TOSHIBA CD/DVDW SD-R5372, ATAPI CD/DVD-ROM drive
[    5.976000] ide1 at 0x170-0x177,0x376 on irq 15
[    5.984000] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 22
[    5.984000] ACPI: PCI Interrupt 0000:00:14.0[A] -> Link [APCH] -> GSI 22 (level, low) -> IRQ 17
[    5.984000] PCI: Setting latency timer of device 0000:00:14.0 to 64
[    5.984000] forcedeth: using HIGHDMA
[    6.508000] eth0: forcedeth.c: subsystem: 01043:816a bound to 0000:00:14.0
[    6.508000] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 21
[    6.508000] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [APCL] -> GSI 21 (level, low) -> IRQ 18
[    6.508000] PCI: Setting latency timer of device 0000:00:0b.1 to 64
[    6.508000] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[    6.508000] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 2
[    6.508000] ehci_hcd 0000:00:0b.1: debug port 1
[    6.508000] PCI: cache line size of 64 is not supported by device 0000:00:0b.1
[    6.508000] ehci_hcd 0000:00:0b.1: irq 18, io mem 0xfe02e000
[    6.508000] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    6.508000] usb 1-2: USB disconnect, address 2
[    6.508000] usb usb2: configuration #1 chosen from 1 choice
[    6.508000] hub 2-0:1.0: USB hub found
[    6.508000] hub 2-0:1.0: 8 ports detected
[    6.620000] sata_nv 0000:00:0e.0: version 3.3
[    6.620000] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 20
[    6.620000] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [APSI] -> GSI 20 (level, low) -> IRQ 19
[    6.620000] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[    6.620000] ata1: SATA max UDMA/133 cmd 0x000109f0 ctl 0x00010bf2 bmdma 0x0001e000 irq 19
[    6.620000] ata2: SATA max UDMA/133 cmd 0x00010970 ctl 0x00010b72 bmdma 0x0001e008 irq 19
[    6.620000] scsi0 : sata_nv
[    7.092000] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    7.124000] usb 1-2: new low speed USB device using ohci_hcd and address 3
[    7.128000] ata1.00: ata_hpa_resize 1: sectors = 976773168, hpa_sectors = 976773168
[    7.128000] ata1.00: ATA-8: SAMSUNG HD501LJ, CR100-10, max UDMA7
[    7.128000] ata1.00: 976773168 sectors, multi 1: LBA48 NCQ (depth 0/32)
[    7.140000] ata1.00: ata_hpa_resize 1: sectors = 976773168, hpa_sectors = 976773168
[    7.140000] ata1.00: configured for UDMA/133
[    7.140000] scsi1 : sata_nv
[    7.332000] usb 1-2: configuration #1 chosen from 1 choice
[    7.344000] input: Logitech USB-PS/2 Optical Mouse as /class/input/input3
[    7.344000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:0b.0-2
[    7.452000] ata2: SATA link down (SStatus 0 SControl 300)
[    7.464000] ATA: abnormal status 0x7F on port 0x00010977
[    7.464000] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HD501LJ  CR10 PQ: 0 ANSI: 5
[    7.464000] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 23
[    7.464000] ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [APSJ] -> GSI 23 (level, low) -> IRQ 16
[    7.464000] PCI: Setting latency timer of device 0000:00:0f.0 to 64
[    7.464000] ata3: SATA max UDMA/133 cmd 0x000109e0 ctl 0x00010be2 bmdma 0x0001cc00 irq 16
[    7.464000] ata4: SATA max UDMA/133 cmd 0x00010960 ctl 0x00010b62 bmdma 0x0001cc08 irq 16
[    7.464000] scsi2 : sata_nv
[    7.776000] ata3: SATA link down (SStatus 0 SControl 300)
[    7.788000] ATA: abnormal status 0x7F on port 0x000109e7
[    7.788000] scsi3 : sata_nv
[    8.100000] ata4: SATA link down (SStatus 0 SControl 300)
[    8.112000] ATA: abnormal status 0x7F on port 0x00010967
[    8.120000] hdc: ATAPI 40X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[    8.120000] Uniform CD-ROM driver Revision: 3.20
[    8.124000] hda: max request size: 512KiB
[    8.124000] hda: 312581808 sectors (160041 MB) w/2048KiB Cache, CHS=19457/255/63, UDMA(100)
[    8.124000] hda: cache flushes supported
[    8.124000]  hda:<5>SCSI device sda: 976773168 512-byte hdwr sectors (500108 MB)
[    8.124000] sda: Write Protect is off
[    8.124000] sda: Mode Sense: 00 3a 00 00
[    8.124000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    8.124000] SCSI device sda: 976773168 512-byte hdwr sectors (500108 MB)
[    8.124000] sda: Write Protect is off
[    8.124000] sda: Mode Sense: 00 3a 00 00
[    8.124000] hdd: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[    8.128000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    8.128000]  sda: hda1 hda2 hda3 hda4
[    8.188000]  unknown partition table
[    8.188000] sd 0:0:0:0: Attached scsi disk sda
[    8.188000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    8.380000] Attempting manual resume
[    8.380000] swsusp: Resume From Partition 3:3
[    8.380000] PM: Checking swsusp image.
[    8.380000] PM: Resume from disk failed.
[    8.408000] kjournald starting.  Commit interval 5 seconds
[    8.408000] EXT3-fs: mounted filesystem with ordered data mode.
[   16.332000] eth1: no link during initialization.
[   17.256000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   17.264000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   17.608000] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x4c00
[   17.608000] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x4c40
[   17.676000] input: PC Speaker as /class/input/input4
[   17.716000] NET: Registered protocol family 17
[   17.732000] ath_hal: module license 'Proprietary' taints kernel.
[   17.736000] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   17.816000] Linux video capture interface: v2.00
[   17.900000] parport: PnPBIOS parport detected.
[   17.900000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   17.948000] Linux agpgart interface v0.102 (c) Dave Jones
[   18.012000] wlan: 0.8.4.2 (0.9.3.1)
[   18.028000] ath_pci: 0.9.4.5 (0.9.3.1)
[   18.032000] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[   18.032000] ACPI: PCI Interrupt 0000:04:08.0[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 20
[   18.660000] ath_rate_sample: 1.2 (0.9.3.1)
[   18.672000] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   18.672000] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   18.672000] wifi0: turboG rates: 6Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   18.672000] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   18.672000] wifi0: mac 7.9 phy 4.5 radio 5.6
[   18.672000] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   18.672000] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   18.672000] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   18.672000] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   18.672000] wifi0: Use hw queue 8 for CAB traffic
[   18.672000] wifi0: Use hw queue 9 for beacons
[   18.768000] wifi0: Atheros 5212: mem=0xfdcf0000, irq=20
[   19.052000] ACPI: PCI Interrupt Link [APC5] enabled at IRQ 16
[   19.052000] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [APC5] -> GSI 16 (level, low) -> IRQ 20
[   19.052000] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   19.052000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9631  Thu Nov  9 17:38:10 PST 2006
[   19.144000] bttv: driver version 0.9.16 loaded
[   19.144000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   19.144000] bttv: Bt8xx card found (0).
[   19.144000] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[   19.144000] ACPI: PCI Interrupt 0000:04:09.0[A] -> Link [APC2] -> GSI 17 (level, low) -> IRQ 21
[   19.144000] bttv0: Bt878 (rev 17) at 0000:04:09.0, irq: 21, latency: 32, mmio: 0xfdbff000
[   19.144000] bttv0: detected: Leadtek TV 2000 XP [card=34], PCI subsystem ID is 107d:6609
[   19.144000] bttv0: using: Leadtek WinFast 2000/ WinFast 2000 XP [card=34,autodetected]
[   19.144000] bttv0: gpio: en=00000000, out=00000000 in=003ff502 [init]
[   19.144000] bttv0: using tuner=5
[   19.144000] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[   19.144000] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   19.148000] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   19.148000] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[   19.192000] NET: Registered protocol family 10
[   19.192000] lo: Disabled Privacy Extensions
[   19.192000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   19.200000] tuner 2-0061: chip found @ 0xc2 (bt878 #0 [sw])
[   19.200000] tuner 2-0061: type set to 5 (Philips PAL_BG (FI1216 and compatibles))
[   19.200000] tuner 2-0061: type set to 5 (Philips PAL_BG (FI1216 and compatibles))
[   19.216000] bttv0: registered device video0
[   19.216000] bttv0: registered device vbi0
[   19.216000] bttv0: registered device radio0
[   19.216000] bttv0: PLL: 28636363 => 35468950 .. ok
[   19.256000] input: bttv IR (card=34) as /class/input/input5
[   19.316000] bt878: AUDIO driver version 0.0.0 loaded
[   19.316000] bt878: Bt878 AUDIO function found (0).
[   19.316000] ACPI: PCI Interrupt 0000:04:09.1[A] -> Link [APC2] -> GSI 17 (level, low) -> IRQ 21
[   19.316000] bt878_probe: card id=[0x6609107d], Unknown card.
[   19.316000] Exiting..
[   19.316000] ACPI: PCI interrupt for device 0000:04:09.1 disabled
[   19.316000] bt878: probe of 0000:04:09.1 failed with error -22
[   19.408000] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 22
[   19.408000] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [AAZA] -> GSI 22 (level, low) -> IRQ 17
[   19.408000] PCI: Setting latency timer of device 0000:00:10.1 to 64
[   19.848000] Adding 1052248k swap on /dev/disk/by-uuid/9784bfa9-82e2-4154-bae5-f788a62ae8b7.  Priority:-1 extents:1 across:1052248k
[   19.968000] EXT3 FS on hda1, internal journal
[   30.048000] ath0: no IPv6 routers present
[  134.228000] kjournald starting.  Commit interval 5 seconds
[  134.228000] EXT3 FS on hda2, internal journal
[  134.228000] EXT3-fs: mounted filesystem with ordered data mode.
[  134.232000] kjournald starting.  Commit interval 5 seconds
[  134.232000] EXT3 FS on hda4, internal journal
[  134.232000] EXT3-fs: mounted filesystem with ordered data mode.
[  134.280000] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
[  134.280000] SGI XFS Quota Management subsystem
[  134.292000] XFS mounting filesystem sda
[  134.364000] Starting XFS recovery on filesystem: sda (logdev: internal)
[  134.520000] Ending XFS recovery on filesystem: sda (logdev: internal)
[  139.916000] ibm_acpi: ec object not found
[  139.972000] Using specific hotkey driver
[  140.016000] input: Power Button (FF) as /class/input/input6
[  140.016000] ACPI: Power Button (FF) [PWRF]
[  140.016000] input: Power Button (CM) as /class/input/input7
[  140.016000] ACPI: Power Button (CM) [PWRB]
[  140.028000] No dock devices found.
[  140.164000] pcc_acpi: loading...
[  140.348000] powernow-k8: Found 2 AMD Athlon(tm) 64 X2 Dual Core Processor 4800+ processors (version 2.00.00)
[  140.348000] powernow-k8: MP systems not supported by PSB BIOS structure
[  140.348000] powernow-k8: MP systems not supported by PSB BIOS structure
[  144.368000] lp0: using parport0 (interrupt-driven).
[  144.388000] ppdev: user-space parallel port driver
[  147.152000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[  147.152000] apm: disabled - APM is not SMP safe.
[  148.536000] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[  148.664000] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[  148.668000] NFSD: starting 90-second grace period
[  152.168000] Bluetooth: Core ver 2.11
[  152.168000] NET: Registered protocol family 31
[  152.168000] Bluetooth: HCI device and connection manager initialized
[  152.168000] Bluetooth: HCI socket layer initialized
[  152.288000] Bluetooth: L2CAP ver 2.8
[  152.288000] Bluetooth: L2CAP socket layer initialized
[  152.304000] Bluetooth: RFCOMM socket layer initialized
[  152.304000] Bluetooth: RFCOMM TTY layer initialized
[  152.304000] Bluetooth: RFCOMM ver 1.8
[  152.928000] bttv0: PLL can sleep, using XTAL (28636363).
[  186.320000] NET: Registered protocol family 4
[  186.652000] NET: Registered protocol family 3
[  187.032000] NET: Registered protocol family 5
[  196.892000] bttv0: timeout: drop=36 irq=132/132, risc=1acc2074, bits: HSYNC FDSR
[  196.892000] bttv0: reset, reinitialize
[  196.892000] bttv0: PLL can sleep, using XTAL (28636363).
[  228.040000] bttv0: unloading
[  239.920000] bttv: driver version 0.9.16 loaded
[  239.920000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[  239.920000] bttv: Bt8xx card found (0).
[  239.920000] bttv0: Bt878 (rev 17) at 0000:04:09.0, irq: 21, latency: 32, mmio: 0xfdbff000
[  239.920000] bttv0: detected: Leadtek TV 2000 XP [card=34], PCI subsystem ID is 107d:6609
[  239.920000] bttv0: using: Leadtek WinFast 2000/ WinFast 2000 XP [card=34,insmod option]
[  239.920000] bttv0: gpio: en=00000000, out=00000000 in=003ff502 [init]
[  239.924000] tuner 2-0061: chip found @ 0xc2 (bt878 #0 [sw])
[  239.936000] bttv0: using tuner=43
[  239.936000] tuner 2-0061: type set to 43 (Philips NTSC MK3 (FM1236MK3 or FM1236/F))
[  239.936000] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[  239.936000] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[  239.936000] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[  239.936000] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[  239.944000] bttv0: registered device video0
[  239.944000] bttv0: registered device vbi0
[  239.944000] bttv0: registered device radio0
[  239.944000] bttv0: PLL: 28636363 => 35468950 .. ok
[  239.976000] input: bttv IR (card=34) as /class/input/input8
[  245.068000] bttv0: PLL can sleep, using XTAL (28636363).
[  245.292000] bttv0: SCERR @ 1a9bb014,bits: FDSR SCERR*
[  251.200000] bttv0: timeout: drop=23 irq=747/747, risc=1b20607c, bits: HSYNC FDSR
[  251.200000] bttv0: reset, reinitialize
[  251.200000] bttv0: PLL can sleep, using XTAL (28636363).
[  257.292000] bttv0: SCERR @ 1a9bb014,bits: OFLOW FDSR SCERR*
[  258.608000] bttv0: timeout: drop=38 irq=924/924, risc=1c25207c, bits: HSYNC OFLOW FDSR
[  258.608000] bttv0: reset, reinitialize
[  258.608000] bttv0: PLL can sleep, using XTAL (28636363).
[53037.624000] atkbd.c: Spurious ACK on isa0060/serio0. Some program might be trying access hardware directly.
[60077.264000] UDF-fs: Partition marked readonly; forcing readonly mount
[60077.288000] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'Bucs at Panthers', timestamp 2007/10/06 16:37 (1f10)
[60154.252000] hdd: packet command error: status=0x51 { DriveReady SeekComplete Error }
[60154.252000] hdd: packet command error: error=0x50 { LastFailedSense=0x05 }
[60154.252000] ide: failed opcode was: unknown
[60154.252000] hdd: error code: 0x70  sense_key: 0x05  asc: 0x30  ascq: 0x02
[63424.092000] UDF-fs: Partition marked readonly; forcing readonly mount
[63424.120000] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'Eagles Giants', timestamp 2007/10/07 09:14 (1f10)
[63460.696000] hdd: packet command error: status=0x51 { DriveReady SeekComplete Error }
[63460.696000] hdd: packet command error: error=0x50 { LastFailedSense=0x05 }
[63460.696000] ide: failed opcode was: unknown
[63460.696000] hdd: error code: 0x70  sense_key: 0x05  asc: 0x30  ascq: 0x02
[63477.364000] hdd: packet command error: status=0x51 { DriveReady SeekComplete Error }
[63477.364000] hdd: packet command error: error=0x50 { LastFailedSense=0x05 }
[63477.364000] ide: failed opcode was: unknown
[63477.364000] hdd: error code: 0x70  sense_key: 0x05  asc: 0x30  ascq: 0x02
[64721.396000] cdrom: This disc doesn't have any tracks I recognize!
[65000.380000] bttv0: SCERR @ 1a9bb014,bits: OFLOW FDSR SCERR*
[65116.716000] bttv0: SCERR @ 1a9bb014,bits: OFLOW FDSR SCERR*
[65131.600000] bttv0: OCERR @ 1a9bb014,bits: OFLOW OCERR*

```

And this is the last 750 lines in .xsession-errors

```

/dev/hdd is block device (64)
/dev/hdd seems to be cdrom
(K3bDevice::Device) /dev/hdd: init()
(K3bDevice::Device) /dev/hdd feature: CD Mastering
(K3bDevice::Device) /dev/hdd feature: CD Track At Once
(K3bDevice::Device) /dev/hdd feature: DVD+R
(K3bDevice::Device) /dev/hdd feature: DVD+RW
(K3bDevice::Device) /dev/hdd feature: DVD+R Double Layer
(K3bDevice::Device) /dev/hdd feature: DVD-R/-RW Write
(K3bDevice::Device) /dev/hdd feature: Rigid Restricted Overwrite
(K3bDevice::Device) /dev/hdd: dataLen: 60
(K3bDevice::Device) /dev/hdd: checking for TAO
(K3bDevice::Device) /dev/hdd: checking for SAO
(K3bDevice::Device) /dev/hdd: checking for SAO_R96P
(K3bDevice::Device) /dev/hdd: checking for SAO_R96R
(K3bDevice::Device) /dev/hdd: checking for RAW_R16
(K3bDevice::ScsiCommand) failed:
                           command:    MODE SELECT (55)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        26
                           ascq:       0
(K3bDevice::Device) /dev/hdd: checking for RAW_R96P
(K3bDevice::ScsiCommand) failed:
                           command:    MODE SELECT (55)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        26
                           ascq:       0
(K3bDevice::Device) /dev/hdd: checking for RAW_R96R
(K3bDevice::Device) /dev/hdd:  Number of supported write speeds via GET PERFORMANCE: 2
(K3bDevice::Device) /dev/hdd : 5540 KB/s
(K3bDevice::Device) /dev/hdd : 2770 KB/s
(K3bDevice::DeviceManager) setting current write speed of device /dev/hdd to 5540
/dev/hdc resolved to /dev/hdc
(K3bDevice::DeviceManager) dev /dev/hdc already found
/dev/hdd resolved to /dev/hdd
(K3bDevice::DeviceManager) dev /dev/hdd already found
(K3bDevice::DeviceManager) found config entry for devicetype: LITE-ON LTR-16102B
(K3bDevice::DeviceManager) found config entry for devicetype: TOSHIBA CD/DVDW SD-R5372
First sec data area: 43:41:33 (LBA 196608) (402653184
Last sec data area: 43:41:33 (LBA 196608) (402653184 Bytes)
Last sec layer 1: 00:00:00 (LBA 0) (0 Bytes)
Layer 1 length: 00:00:01 (LBA 1) (2048 Bytes)
Layer 2 length: 43:41:33 (LBA 196608) (402653184 Bytes)
DiskInfo:
Mediatype:       DVD-R Sequential
Current Profile: DVD-R Sequential
Disk state:      empty
Empty:           1
Rewritable:      0
Appendable:      0
Sessions:        0
Tracks:          0
Layers:          1
Capacity:        510:46:46 (LBA 2298496) (4707319808 Bytes)
Remaining size:  510:46:46 (LBA 2298496) (4707319808 Bytes)
Used Size:       00:00:00 (LBA 0) (0 Bytes)
(K3bDevice::Device) /dev/hdd:  Number of supported write speeds via GET PERFORMANCE: 2
(K3bDevice::Device) /dev/hdd : 5540 KB/s
(K3bDevice::Device) /dev/hdd : 2770 KB/s
Devices:
------------------------------
Blockdevice:    /dev/hdc
Generic device:
Vendor:         LITE-ON
Description:    LTR-16102B
Version:        OS0B
Write speed:    0
Profiles:       CD-ROM, CD-R, CD-RW
Read Cap:       CD-ROM, CD-R, CD-RW
Write Cap:      CD-R, CD-RW
Writing modes:  SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R
Reader aliases: /dev/hdc
------------------------------
Blockdevice:    /dev/hdd
Generic device:
Vendor:         TOSHIBA
Description:    CD/DVDW SD-R5372
Version:        TU31
Write speed:    22160
Profiles:       DVD-ROM, DVD-R Sequential, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW
Read Cap:       DVD-ROM, DVD-R, DVD-R Sequential, DVD-RW, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW
Write Cap:      DVD-R, DVD-R Sequential, DVD-RW, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-R, CD-RW
Writing modes:  SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R96R, Restricted Overwrite
Reader aliases: /dev/hdd
------------------------------
kdecore (KProcess): WARNING: _attachPty() 12
kdecore (KAction): WARNING: KActionCollection::operator+=(): function is severely deprecated.
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  157
  Minor opcode:  6
  Resource id:  0x137
kdetv: WARNING: V4L2Dev::enqueueBuffer(): buffer already queued: 0
V4L2Grabber::~V4L2Grabber(): wait().
V4L2Grabber::~V4L2Grabber(): deleted.
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
No battery found.
This is not a laptop, quitting ...
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  157
  Minor opcode:  6
  Resource id:  0x137
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  157
  Minor opcode:  6
  Resource id:  0x137
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  157
  Minor opcode:  6
  Resource id:  0x137
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  157
  Minor opcode:  6
  Resource id:  0x137
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  157
  Minor opcode:  6
  Resource id:  0x137
kio_sftp: ERROR: KSshProcess::version(): pclose failed.
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x14002fe
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  157
  Minor opcode:  6
  Resource id:  0x14002fe
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: PKCS7_content_free
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OpenSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OPENSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OpenSSL_add_all_algorithms_conf
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x14008c7
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  157
  Minor opcode:  6
  Resource id:  0x14008c7
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x1400912
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  157
  Minor opcode:  6
  Resource id:  0x1400912
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x1400913
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  157
  Minor opcode:  6
  Resource id:  0x1400913
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x1400914
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  157
  Minor opcode:  6
  Resource id:  0x1400914
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x1400915
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  157
  Minor opcode:  6
  Resource id:  0x1400915
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x1400916
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  157
  Minor opcode:  6
  Resource id:  0x1400916
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x1400917
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  157
  Minor opcode:  6
  Resource id:  0x1400917
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x1400918
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  157
  Minor opcode:  6
  Resource id:  0x1400918
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x1400919
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  157
  Minor opcode:  6
  Resource id:  0x1400919
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x140091a
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  157
  Minor opcode:  6
  Resource id:  0x140091a
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x1400950
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  157
  Minor opcode:  6
  Resource id:  0x1400950
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x1400951
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  157
  Minor opcode:  6
  Resource id:  0x1400951
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x1400952
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  157
  Minor opcode:  6
  Resource id:  0x1400952
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x1400955
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  157
  Minor opcode:  6
  Resource id:  0x1400955
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x1400956
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  157
  Minor opcode:  6
  Resource id:  0x1400956
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x1400957
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  157
  Minor opcode:  6
  Resource id:  0x1400957
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x1400958
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  157
  Minor opcode:  6
  Resource id:  0x1400958
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x140098e
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  157
  Minor opcode:  6
  Resource id:  0x140098e
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x140098f
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  157
  Minor opcode:  6
  Resource id:  0x140098f
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x1400990
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  157
  Minor opcode:  6
  Resource id:  0x1400990
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x1400991
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  157
  Minor opcode:  6
  Resource id:  0x1400991
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x1400992
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  157
  Minor opcode:  6
  Resource id:  0x1400992
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x1400993
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  157
  Minor opcode:  6
  Resource id:  0x1400993
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x14009ca
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  157
  Minor opcode:  6
  Resource id:  0x14009ca
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x14009cb
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  157
  Minor opcode:  6
  Resource id:  0x14009cb
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x14009cc
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  157
  Minor opcode:  6
  Resource id:  0x14009cc
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x1400a05
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  157
  Minor opcode:  6
  Resource id:  0x1400a05
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x1400a06
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  157
  Minor opcode:  6
  Resource id:  0x1400a06
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x1400a08
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  157
  Minor opcode:  6
  Resource id:  0x1400a08
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x1400a09
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  157
  Minor opcode:  6
  Resource id:  0x1400a09
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x1400a0a
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  157
  Minor opcode:  6
  Resource id:  0x1400a0a
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x1400a0b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  157
  Minor opcode:  6
  Resource id:  0x1400a0b
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x1400a41
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  157
  Minor opcode:  6
  Resource id:  0x1400a41
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x1400a42
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  157
  Minor opcode:  6
  Resource id:  0x1400a42
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x1400a43
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  157
  Minor opcode:  6
  Resource id:  0x1400a43
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x1400a7a
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  157
  Minor opcode:  6
  Resource id:  0x1400a7a
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x1400a7b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  157
  Minor opcode:  6
  Resource id:  0x1400a7b
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x1400a7c
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  157
  Minor opcode:  6
  Resource id:  0x1400a7c
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x1400ab2
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  157
  Minor opcode:  6
  Resource id:  0x1400ab2
ASSERT: "firstOption == listItems.size() || found" in /root/kdelibs/kdelibs-3.5.7/./khtml/rendering/render_form.cpp (1254)
ASSERT: "firstOption == listItems.size() || found" in /root/kdelibs/kdelibs-3.5.7/./khtml/rendering/render_form.cpp (1254)
kdetv: WARNING: V4L2Dev: VIDIOC_QBUF failed: Invalid argument
libzvbi:v4l2_stream_stop: Suspending stream.
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x1400535
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  157
  Minor opcode:  6
  Resource id:  0x1400535
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x3000007
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x3000007
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x1400ae9
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0xa00027
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x14005d4
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  157
  Minor opcode:  6
  Resource id:  0x14005d4
kio_sftp: ERROR: KSshProcess::version(): pclose failed.
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  19
  Minor opcode:  0
  Resource id:  0xc00047
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x140047b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  157
  Minor opcode:  6
  Resource id:  0x137
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  157
  Minor opcode:  6
  Resource id:  0x137
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  19
  Minor opcode:  0
  Resource id:  0x28004c4
ASSERT: "firstOption == listItems.size() || found" in /root/kdelibs/kdelibs-3.5.7/./khtml/rendering/render_form.cpp (1254)
ASSERT: "firstOption == listItems.size() || found" in /root/kdelibs/kdelibs-3.5.7/./khtml/rendering/render_form.cpp (1254)
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Creating vbi proxy client, rev.
$Id: proxy-client.c,v 1.12 2006/05/31 03:54:28 mschimek Exp $
proxy_msg: connect: error 2, No such file or directory
kdetv: WARNING: VBIDecoder: vbi_capture_proxy_new error: Connection via socket failed, server not running.
Try to open V4L2 0.20 VBI device, libzvbi interface rev.
  $Id: io-v4l2.c,v 1.33 2006/05/22 09:00:47 mschimek Exp $
Opened /dev/vbi0
libzvbi:capture_v4l2k_new: Try to open V4L2 2.6 VBI device, libzvbi interface rev.
  $Id: io-v4l2k.c,v 1.41 2006/05/31 03:54:00 mschimek Exp $.
libzvbi:capture_v4l2k_new: Opened /dev/vbi0.
libzvbi:capture_v4l2k_new: /dev/vbi0 (BT878 video (Leadtek WinFast 20) is a v4l2 vbi device,
driver bttv, version 0x00000910.
libzvbi:capture_v4l2k_new: Using streaming interface.
libzvbi:v4l2_get_videostd: Current scanning system is 525.
libzvbi:v4l2_update_services: Querying current vbi parameters...
libzvbi:v4l2_update_services: ...success.
libzvbi:print_vfmt: VBI capture parameters supported: format 59455247 [GREY], 28636363 Hz, 2048 bpl, offs 244, F1 10...25, F2 273...288, flags 00000000.
libzvbi:print_vfmt: VBI capture parameters granted: format 59455247 [GREY], 28636363 Hz, 2048 bpl, offs 244, F1 10...25, F2 273...288, flags 00000000.
libzvbi:vbi3_raw_decoder_add_services: No services to add.
libzvbi:v4l2_update_services: Nyquist check passed.
libzvbi:v4l2_update_services: Request decoding of services 0x60000c7f, strict level -1.
libzvbi:_vbi_sampling_par_permit_service: Service 0x00000001 (Teletext System B 625 Level 1.5) requires videostd_set 0x1, have 0x0.
libzvbi:_vbi_sampling_par_permit_service: Service 0x00000003 (Teletext System B, 625) requires videostd_set 0x1, have 0x0.
libzvbi:_vbi_sampling_par_permit_service: Service 0x00000001 (Teletext System B 625 Level 1.5) requires videostd_set 0x1, have 0x0.
libzvbi:_vbi_sampling_par_permit_service: Service 0x00000003 (Teletext System B, 625) requires videostd_set 0x1, have 0x0.
libzvbi:_vbi_sampling_par_permit_service: Service 0x00000004 (Video Program System) requires videostd_set 0x1, have 0x0.
libzvbi:_vbi_sampling_par_permit_service: Service 0x00000400 (Wide Screen Signalling 625) requires videostd_set 0x1, have 0x0.
libzvbi:_vbi_sampling_par_permit_service: Service 0x00000008 (Closed Caption 625, field 1) requires videostd_set 0x1, have 0x0.
libzvbi:_vbi_sampling_par_permit_service: Service 0x00000010 (Closed Caption 625, field 2) requires videostd_set 0x1, have 0x0.
libzvbi:v4l2_update_services: Will capture services 0x00000060, added 0x60 commit=1.
libzvbi:v4l2_stream_alloc: Requesting 16 streaming i/o buffers.
libzvbi:v4l2_stream_alloc: Mapping 16 streaming i/o buffers.
libzvbi:capture_v4l2k_new: Successfully opened /dev/vbi0 (BT878 video (Leadtek WinFast 20).
kdetv: WARNING: MainWindow::setupInfraRed(): Lirc not available
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  157
  Minor opcode:  6
  Resource id:  0x137
kdetv: WARNING: V4L2Dev::enqueueBuffer(): buffer already queued: 1
V4L2Grabber::~V4L2Grabber(): wait().
V4L2Grabber::~V4L2Grabber(): deleted.
kdetv: WARNING: V4L2Dev: VIDIOC_QBUF failed: Invalid argument
libzvbi:v4l2_stream_stop: Suspending stream.
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x300000a
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x300000a
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  19
  Minor opcode:  0
  Resource id:  0x300000a
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x300000a
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x300000a
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x1401d10
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x14002c5
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  157
  Minor opcode:  6
  Resource id:  0x14002c5
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x2e0039c
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x2e0039c
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x1400ba4
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  157
  Minor opcode:  6
  Resource id:  0x1400ba4
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x2c00ef8
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x2c00ef8
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x2c00ef8
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x2c00ef8
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x14003dc
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  157
  Minor opcode:  6
  Resource id:  0x14003dc
(K3bDevice::Device) /dev/hdd: GET CONFIGURATION length det failed.
(K3bDevice::Device) /dev/hdd: GET CONFIGURATION length det failed.
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x14024b4
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  157
  Minor opcode:  6
  Resource id:  0x14024b4
(K3bDevice::Device) /dev/hdd: GET CONFIGURATION length det failed.
(K3bDevice::Device) /dev/hdd:  Number of supported write speeds via GET PERFORMANCE: 2
(K3bDevice::Device) /dev/hdd : 5540 KB/s
(K3bDevice::Device) /dev/hdd : 2770 KB/s
(K3bDevice::HalConnection) lock queued for /org/freedesktop/Hal/devices/storage_serial_X44L300498
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x14004b3
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  157
  Minor opcode:  6
  Resource id:  0x14004b3
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x14021c9
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  157
  Minor opcode:  6
  Resource id:  0x14021c9
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  157
  Minor opcode:  6
  Resource id:  0x137
ASSERT: "m_frontView && m_frontView->getServer() == m_frontServer" in /build/buildd/konversation-1.0.1/./konversation/src/viewcontainer.cpp (1762)
ASSERT: "!icon.isEmpty()" in /root/kdebase/kdebase-3.5.7/./libkonq/konq_pixmapprovider.cc (81)
ASSERT: "!icon.isEmpty()" in /root/kdebase/kdebase-3.5.7/./libkonq/konq_pixmapprovider.cc (81)
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x28111af
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x28111af

```
Assuming that the kernel is perfect, what am I doing wrong?

---

