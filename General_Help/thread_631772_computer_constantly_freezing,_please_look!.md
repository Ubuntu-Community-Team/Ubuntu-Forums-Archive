---
title: "computer constantly freezing, please look!"
date: 2007-12-04
forum: General Help
---

### Post by musafirah on 2007-12-04
i am on feisty fawn and lately my computer is constantly freezing.. here is the latest part of the kern log 

> 

Dec  4 19:53:00 bokhari-desktop kernel: [   27.787417] ACPI: PCI Root Bridge [PCI0] (0000:00)
Dec  4 19:53:00 bokhari-desktop kernel: [   27.787432] PCI: Probing PCI hardware (bus 00)
Dec  4 19:53:00 bokhari-desktop kernel: [   27.787990] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
Dec  4 19:53:00 bokhari-desktop kernel: [   27.789031] PCI quirk: region ee00-eeff claimed by vt82c586 ACPI
Dec  4 19:53:00 bokhari-desktop kernel: [   27.789219] Boot video device is 0000:01:00.0
Dec  4 19:53:00 bokhari-desktop kernel: [   27.789321] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Dec  4 19:53:00 bokhari-desktop kernel: [   27.796724] Linux Plug and Play Support v0.97 (c) Adam Belay
Dec  4 19:53:00 bokhari-desktop kernel: [   27.796760] pnp: PnP ACPI init
Dec  4 19:53:00 bokhari-desktop kernel: [   27.803521] pnp: PnP ACPI: found 12 devices
Dec  4 19:53:00 bokhari-desktop kernel: [   27.803537] PnPBIOS: Disabled by ACPI PNP
Dec  4 19:53:00 bokhari-desktop kernel: [   27.803704] PCI: Using ACPI for IRQ routing
Dec  4 19:53:00 bokhari-desktop kernel: [   27.803715] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Dec  4 19:53:00 bokhari-desktop kernel: [   27.833975] NET: Registered protocol family 8
Dec  4 19:53:00 bokhari-desktop kernel: [   27.833983] NET: Registered protocol family 20
Dec  4 19:53:00 bokhari-desktop kernel: [   27.834598] pnp: 00:02: ioport range 0x4d0-0x4d1 has been reserved
Dec  4 19:53:00 bokhari-desktop kernel: [   27.834611] pnp: 00:02: ioport range 0xee00-0xee7f could not be reserved
Dec  4 19:53:00 bokhari-desktop kernel: [   27.834622] pnp: 00:02: ioport range 0xee80-0xeeff has been reserved
Dec  4 19:53:00 bokhari-desktop kernel: [   27.834639] pnp: 00:02: ioport range 0xef00-0xef5f has been reserved
Dec  4 19:53:00 bokhari-desktop kernel: [   27.835542] PCI: Bridge: 0000:00:01.0
Dec  4 19:53:00 bokhari-desktop kernel: [   27.835550]   IO window: disabled.
Dec  4 19:53:00 bokhari-desktop kernel: [   27.835561]   MEM window: 40000000-400fffff
Dec  4 19:53:00 bokhari-desktop kernel: [   27.835571]   PREFETCH window: 48000000-4fffffff
Dec  4 19:53:00 bokhari-desktop kernel: [   27.835600] PCI: Setting latency timer of device 0000:00:01.0 to 64
Dec  4 19:53:00 bokhari-desktop kernel: [   27.835676] NET: Registered protocol family 2
Dec  4 19:53:00 bokhari-desktop kernel: [   27.873438] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
Dec  4 19:53:00 bokhari-desktop kernel: [   27.873681] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
Dec  4 19:53:00 bokhari-desktop kernel: [   27.874078] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
Dec  4 19:53:00 bokhari-desktop kernel: [   27.874338] TCP: Hash tables configured (established 16384 bind 8192)
Dec  4 19:53:00 bokhari-desktop kernel: [   27.874348] TCP reno registered
Dec  4 19:53:00 bokhari-desktop kernel: [   27.885678] checking if image is initramfs... it is
Dec  4 19:53:00 bokhari-desktop kernel: [   29.793674] Freeing initrd memory: 6777k freed
Dec  4 19:53:00 bokhari-desktop kernel: [   29.794766] audit: initializing netlink socket (disabled)
Dec  4 19:53:00 bokhari-desktop kernel: [   29.794806] audit(1196815937.360:1): initialized
Dec  4 19:53:00 bokhari-desktop kernel: [   29.795191] VFS: Disk quotas dquot_6.5.1
Dec  4 19:53:00 bokhari-desktop kernel: [   29.795258] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Dec  4 19:53:00 bokhari-desktop kernel: [   29.795403] io scheduler noop registered
Dec  4 19:53:00 bokhari-desktop kernel: [   29.795412] io scheduler anticipatory registered
Dec  4 19:53:00 bokhari-desktop kernel: [   29.795420] io scheduler deadline registered
Dec  4 19:53:00 bokhari-desktop kernel: [   29.795453] io scheduler cfq registered (default)
Dec  4 19:53:00 bokhari-desktop kernel: [   29.795487] PCI: Disabling Via external APIC routing
Dec  4 19:53:00 bokhari-desktop kernel: [   29.796132] isapnp: Scanning for PnP cards...
Dec  4 19:53:00 bokhari-desktop kernel: [   30.150971] isapnp: No Plug & Play device found
Dec  4 19:53:00 bokhari-desktop kernel: [   30.236519] Real Time Clock Driver v1.12ac
Dec  4 19:53:00 bokhari-desktop kernel: [   30.236655] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Dec  4 19:53:00 bokhari-desktop kernel: [   30.236917] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Dec  4 19:53:00 bokhari-desktop kernel: [   30.239001] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Dec  4 19:53:00 bokhari-desktop kernel: [   30.239623] mice: PS/2 mouse device common for all mice
Dec  4 19:53:00 bokhari-desktop kernel: [   30.241519] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Dec  4 19:53:00 bokhari-desktop kernel: [   30.242241] input: Macintosh mouse button emulation as /class/input/input0
Dec  4 19:53:00 bokhari-desktop kernel: [   30.242351] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Dec  4 19:53:00 bokhari-desktop kernel: [   30.242364] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Dec  4 19:53:00 bokhari-desktop kernel: [   30.242859] PNP: PS/2 Controller [PNP0303:KBD,PNP0f0e:PS2M] at 0x60,0x64 irq 1,12
Dec  4 19:53:00 bokhari-desktop kernel: [   30.243474] serio: i8042 KBD port at 0x60,0x64 irq 1
Dec  4 19:53:00 bokhari-desktop kernel: [   30.243491] serio: i8042 AUX port at 0x60,0x64 irq 12
Dec  4 19:53:00 bokhari-desktop kernel: [   30.243859] EISA: Probing bus 0 at eisa.0
Dec  4 19:53:00 bokhari-desktop kernel: [   30.243880] Cannot allocate resource for EISA slot 1
Dec  4 19:53:00 bokhari-desktop kernel: [   30.243938] EISA: Detected 0 cards.
Dec  4 19:53:00 bokhari-desktop kernel: [   30.274200] TCP cubic registered
Dec  4 19:53:00 bokhari-desktop kernel: [   30.274225] NET: Registered protocol family 1
Dec  4 19:53:00 bokhari-desktop kernel: [   30.274293] Using IPI No-Shortcut mode
Dec  4 19:53:00 bokhari-desktop kernel: [   30.274496] ACPI: (supports S0 S1 S5)
Dec  4 19:53:00 bokhari-desktop kernel: [   30.274608]   Magic number: 3:746:859
Dec  4 19:53:00 bokhari-desktop kernel: [   30.274784]   hash matches device ptyse
Dec  4 19:53:00 bokhari-desktop kernel: [   30.275511] Freeing unused kernel memory: 328k freed
Dec  4 19:53:00 bokhari-desktop kernel: [   30.277057] Time: tsc clocksource has been installed.
Dec  4 19:53:00 bokhari-desktop kernel: [   30.294313] input: AT Translated Set 2 keyboard as /class/input/input1
Dec  4 19:53:00 bokhari-desktop kernel: [   32.031056] Capability LSM initialized
Dec  4 19:53:00 bokhari-desktop kernel: [   32.163543] ACPI: CPU0 (power states: C1[C1] C2[C2])
Dec  4 19:53:00 bokhari-desktop kernel: [   33.734783] ieee1394: Initialized config rom entry `ip1394'
Dec  4 19:53:00 bokhari-desktop kernel: [   33.742229] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
Dec  4 19:53:00 bokhari-desktop kernel: [   33.742243] PCI: setting IRQ 10 as level-triggered
Dec  4 19:53:00 bokhari-desktop kernel: [   33.742254] ACPI: PCI Interrupt 0000:00:0c.0[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
Dec  4 19:53:00 bokhari-desktop kernel: [   33.793493] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[10]  MMIO=[40400000-404007ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Dec  4 19:53:00 bokhari-desktop kernel: [   33.856862] SCSI subsystem initialized
Dec  4 19:53:00 bokhari-desktop kernel: [   33.887379] libata version 2.20 loaded.
Dec  4 19:53:00 bokhari-desktop kernel: [   33.901790] VP_IDE: IDE controller at PCI slot 0000:00:14.1
Dec  4 19:53:00 bokhari-desktop kernel: [   33.901822] VP_IDE: chipset revision 6
Dec  4 19:53:00 bokhari-desktop kernel: [   33.901829] VP_IDE: not 100%% native mode: will probe irqs later
Dec  4 19:53:00 bokhari-desktop kernel: [   33.901854] VP_IDE: VIA vt82c686a (rev 14) IDE UDMA66 controller on pci0000:00:14.1
Dec  4 19:53:00 bokhari-desktop kernel: [   33.901872]     ide0: BM-DMA at 0x1480-0x1487, BIOS settings: hda:DMA, hdb:pio
Dec  4 19:53:00 bokhari-desktop kernel: [   33.901899]     ide1: BM-DMA at 0x1488-0x148f, BIOS settings: hdc:DMA, hdd:DMA
Dec  4 19:53:00 bokhari-desktop kernel: [   33.901916] Probing IDE interface ide0...
Dec  4 19:53:00 bokhari-desktop kernel: [   34.028119] natsemi dp8381x driver, version 2.1, Sept 11, 2006
Dec  4 19:53:00 bokhari-desktop kernel: [   34.028126]   originally by Donald Becker <becker@scyld.com>
Dec  4 19:53:00 bokhari-desktop kernel: [   34.028132]   [http://www.scyld.com/network/natsemi.html](http://www.scyld.com/network/natsemi.html)
Dec  4 19:53:00 bokhari-desktop kernel: [   34.028136]   2.4.x kernel port by Jeff Garzik, Tjeerd Mulder
Dec  4 19:53:00 bokhari-desktop kernel: [   34.080843] usbcore: registered new interface driver usbfs
Dec  4 19:53:00 bokhari-desktop kernel: [   34.080925] usbcore: registered new interface driver hub
Dec  4 19:53:00 bokhari-desktop kernel: [   34.080995] usbcore: registered new device driver usb
Dec  4 19:53:00 bokhari-desktop kernel: [   34.085838] USB Universal Host Controller Interface driver v3.0
Dec  4 19:53:00 bokhari-desktop kernel: [   34.348859] hda: ST320430A, ATA DISK drive
Dec  4 19:53:00 bokhari-desktop kernel: [   34.463126] Floppy drive(s): fd0 is 1.44M
Dec  4 19:53:00 bokhari-desktop kernel: [   34.486199] FDC 0 is a post-1991 82077
Dec  4 19:53:00 bokhari-desktop kernel: [    7.948000] Time: acpi_pm clocksource has been installed.
Dec  4 19:53:00 bokhari-desktop kernel: [    8.404000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Dec  4 19:53:00 bokhari-desktop kernel: [    8.404000] Probing IDE interface ide1...
Dec  4 19:53:00 bokhari-desktop kernel: [    8.452000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0040d01222050665]
Dec  4 19:53:00 bokhari-desktop kernel: [    9.268000] hdc: Compaq DVD-ROM DVD-114 0114, ATAPI CD/DVD-ROM drive
Dec  4 19:53:00 bokhari-desktop kernel: [   10.052000] hdd: DVD-RW IDE1008, ATAPI CD/DVD-ROM drive
Dec  4 19:53:00 bokhari-desktop kernel: [   10.108000] ide1 at 0x170-0x177,0x376 on irq 15
Dec  4 19:53:00 bokhari-desktop kernel: [   10.108000] PCI: Enabling device 0000:00:03.0 (0004 -> 0007)
Dec  4 19:53:00 bokhari-desktop kernel: [   10.108000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 3
Dec  4 19:53:00 bokhari-desktop kernel: [   10.108000] PCI: setting IRQ 3 as level-triggered
Dec  4 19:53:00 bokhari-desktop kernel: [   10.108000] ACPI: PCI Interrupt 0000:00:03.0[A] -> Link [LNKA] -> GSI 3 (level, low) -> IRQ 3
Dec  4 19:53:00 bokhari-desktop kernel: [   10.112000] natsemi eth0: NatSemi DP8381[56] at 0x40300000 (0000:00:03.0), 00:09:5b:0b:8f:e5, IRQ 3, port TP.
Dec  4 19:53:00 bokhari-desktop kernel: [   10.112000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
Dec  4 19:53:00 bokhari-desktop kernel: [   10.112000] PCI: setting IRQ 11 as level-triggered
Dec  4 19:53:00 bokhari-desktop kernel: [   10.112000] ACPI: PCI Interrupt 0000:00:14.2[D] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Dec  4 19:53:00 bokhari-desktop kernel: [   10.112000] uhci_hcd 0000:00:14.2: UHCI Host Controller
Dec  4 19:53:00 bokhari-desktop kernel: [   10.112000] uhci_hcd 0000:00:14.2: new USB bus registered, assigned bus number 1
Dec  4 19:53:00 bokhari-desktop kernel: [   10.112000] uhci_hcd 0000:00:14.2: irq 11, io base 0x00001440
Dec  4 19:53:00 bokhari-desktop kernel: [   10.116000] usb usb1: configuration #1 chosen from 1 choice
Dec  4 19:53:00 bokhari-desktop kernel: [   10.116000] hub 1-0:1.0: USB hub found
Dec  4 19:53:00 bokhari-desktop kernel: [   10.116000] hub 1-0:1.0: 2 ports detected
Dec  4 19:53:00 bokhari-desktop kernel: [   10.140000] hda: max request size: 128KiB
Dec  4 19:53:00 bokhari-desktop kernel: [   10.140000] hda: 39102336 sectors (20020 MB) w/512KiB Cache, CHS=38792/16/63, UDMA(66)
Dec  4 19:53:00 bokhari-desktop kernel: [   10.140000] hda: cache flushes not supported
Dec  4 19:53:00 bokhari-desktop kernel: [   10.140000]  hda: hda1 hda2 < hda5 >
Dec  4 19:53:00 bokhari-desktop kernel: [   10.220000] ACPI: PCI Interrupt 0000:00:14.3[D] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Dec  4 19:53:00 bokhari-desktop kernel: [   10.220000] uhci_hcd 0000:00:14.3: UHCI Host Controller
Dec  4 19:53:00 bokhari-desktop kernel: [   10.220000] uhci_hcd 0000:00:14.3: new USB bus registered, assigned bus number 2
Dec  4 19:53:00 bokhari-desktop kernel: [   10.220000] uhci_hcd 0000:00:14.3: irq 11, io base 0x00001460
Dec  4 19:53:00 bokhari-desktop kernel: [   10.220000] usb usb2: configuration #1 chosen from 1 choice
Dec  4 19:53:00 bokhari-desktop kernel: [   10.220000] hub 2-0:1.0: USB hub found
Dec  4 19:53:00 bokhari-desktop kernel: [   10.220000] hub 2-0:1.0: 2 ports detected
Dec  4 19:53:00 bokhari-desktop kernel: [   10.264000] hdc: ATAPI DVD-ROM drive, 512kB Cache, UDMA(33)
Dec  4 19:53:00 bokhari-desktop kernel: [   10.264000] Uniform CD-ROM driver Revision: 3.20
Dec  4 19:53:00 bokhari-desktop kernel: [   10.268000] hdd: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
Dec  4 19:53:00 bokhari-desktop kernel: [   10.588000] usb 1-2: new full speed USB device using uhci_hcd and address 2
Dec  4 19:53:00 bokhari-desktop kernel: [   10.688000] Attempting manual resume
Dec  4 19:53:00 bokhari-desktop kernel: [   10.688000] swsusp: Resume From Partition 3:5
Dec  4 19:53:00 bokhari-desktop kernel: [   10.688000] PM: Checking swsusp image.
Dec  4 19:53:00 bokhari-desktop kernel: [   10.704000] PM: Resume from disk failed.
Dec  4 19:53:00 bokhari-desktop kernel: [   10.784000] kjournald starting.  Commit interval 5 seconds
Dec  4 19:53:00 bokhari-desktop kernel: [   10.784000] EXT3-fs: mounted filesystem with ordered data mode.
Dec  4 19:53:00 bokhari-desktop kernel: [   10.784000] usb 1-2: configuration #1 chosen from 1 choice
Dec  4 19:53:00 bokhari-desktop kernel: [   25.984000] eth0: DSPCFG accepted after 0 usec.
Dec  4 19:53:00 bokhari-desktop kernel: [   25.984000] eth0: link up.
Dec  4 19:53:00 bokhari-desktop kernel: [   25.984000] eth0: Setting full-duplex based on negotiated link capability.
Dec  4 19:53:00 bokhari-desktop kernel: [   27.456000] NET: Registered protocol family 17
Dec  4 19:53:00 bokhari-desktop kernel: [   29.732000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Dec  4 19:53:00 bokhari-desktop kernel: [   29.768000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Dec  4 19:53:00 bokhari-desktop kernel: [   30.824000] Linux agpgart interface v0.102 (c) Dave Jones
Dec  4 19:53:00 bokhari-desktop kernel: [   30.892000] parport_pc: VIA 686A/8231 detected
Dec  4 19:53:00 bokhari-desktop kernel: [   30.892000] parport_pc: probing current configuration
Dec  4 19:53:00 bokhari-desktop kernel: [   30.892000] parport_pc: Current parallel port base: 0x378
Dec  4 19:53:00 bokhari-desktop kernel: [   30.892000] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
Dec  4 19:53:00 bokhari-desktop kernel: [   30.912000] agpgart: Detected VIA Apollo Pro 133 chipset
Dec  4 19:53:00 bokhari-desktop kernel: [   30.916000] agpgart: AGP aperture is 64M @ 0x50000000
Dec  4 19:53:00 bokhari-desktop kernel: [   31.000000] parport_pc: VIA parallel port: io=0x378, irq=7
Dec  4 19:53:00 bokhari-desktop kernel: [   31.840000] savage4_smbus 0000:01:00.0: Using Savage4 at d8a80000
Dec  4 19:53:00 bokhari-desktop kernel: [   32.272000] input: PC Speaker as /class/input/input2
Dec  4 19:53:00 bokhari-desktop kernel: [   32.404000] via686a 0000:00:14.4: base address not set - upgrade BIOS or use force_addr=0xaddr
Dec  4 19:53:00 bokhari-desktop kernel: [   32.428000] vt596_smbus 0000:00:14.4: SMBus base address uninitialized - upgrade BIOS or use force_addr=0xaddr
Dec  4 19:53:00 bokhari-desktop kernel: [   33.008000] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
Dec  4 19:53:00 bokhari-desktop kernel: [   33.716000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x04E8 pid 0x323A
Dec  4 19:53:00 bokhari-desktop kernel: [   33.716000] usbcore: registered new interface driver usblp
Dec  4 19:53:00 bokhari-desktop kernel: [   33.716000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
Dec  4 19:53:00 bokhari-desktop kernel: [   33.844000] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
Dec  4 19:53:00 bokhari-desktop kernel: [   35.084000] fuse init (API version 7.8)
Dec  4 19:53:00 bokhari-desktop kernel: [   35.136000] lp0: using parport0 (interrupt-driven).
Dec  4 19:53:00 bokhari-desktop kernel: [   35.284000] Adding 859436k swap on /dev/disk/by-uuid/e006537a-c90b-414b-909c-33fcca742104.  Priority:-1 extents:1 across:859436k
Dec  4 19:53:00 bokhari-desktop kernel: [   35.452000] EXT3 FS on hda1, internal journal
Dec  4 19:53:00 bokhari-desktop kernel: [   35.716000] NET: Registered protocol family 10
Dec  4 19:53:00 bokhari-desktop kernel: [   35.716000] lo: Disabled Privacy Extensions
Dec  4 19:53:00 bokhari-desktop kernel: [   43.620000] No dock devices found.
Dec  4 19:53:00 bokhari-desktop kernel: [   43.908000] input: Power Button (FF) as /class/input/input4
Dec  4 19:53:00 bokhari-desktop kernel: [   43.908000] ACPI: Power Button (FF) [PWRF]
Dec  4 19:53:00 bokhari-desktop kernel: [   43.948000] input: Power Button (CM) as /class/input/input5
Dec  4 19:53:00 bokhari-desktop kernel: [   43.948000] ACPI: Power Button (CM) [PBTN]
Dec  4 19:53:00 bokhari-desktop kernel: [   44.124000] Using specific hotkey driver
Dec  4 19:53:00 bokhari-desktop kernel: [   44.220000] ibm_acpi: ec object not found
Dec  4 19:53:00 bokhari-desktop kernel: [   44.436000] pcc_acpi: loading...
Dec  4 19:53:00 bokhari-desktop kernel: [   46.376000] eth0: no IPv6 routers present
Dec  4 19:53:10 bokhari-desktop kernel: [   56.832000] ppdev: user-space parallel port driver
Dec  4 19:53:10 bokhari-desktop kernel: [   56.868000] [drm] Initialized drm 1.1.0 20060810
Dec  4 19:53:10 bokhari-desktop kernel: [   56.912000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 3 (level, low) -> IRQ 3
Dec  4 19:53:10 bokhari-desktop kernel: [   56.920000] [drm] Initialized savage 2.4.1 20050313 on minor 0
Dec  4 19:53:10 bokhari-desktop kernel: [   56.920000] mtrr: base(0x4a000000) is not aligned on a size(0x5000000) boundary
Dec  4 19:53:10 bokhari-desktop kernel: [   56.920000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Dec  4 19:53:10 bokhari-desktop kernel: [   56.920000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
Dec  4 19:53:10 bokhari-desktop kernel: [   56.924000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
Dec  4 19:53:13 bokhari-desktop kernel: [   59.140000] apm: BIOS not found.
Dec  4 19:53:25 bokhari-desktop kernel: [   71.376000] eth0: no IPv6 routers present
Dec  4 20:00:29 bokhari-desktop kernel: Inspecting /boot/System.map-2.6.20-16-generic
Dec  4 20:00:29 bokhari-desktop kernel: Loaded 24980 symbols from /boot/System.map-2.6.20-16-generic.
Dec  4 20:00:29 bokhari-desktop kernel: Symbols match kernel version 2.6.20.
Dec  4 20:00:29 bokhari-desktop kernel: No module symbols loaded - kernel modules not enabled. 
Dec  4 20:00:29 bokhari-desktop kernel: [    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Sep 23 19:50:39 UTC 2007 (Ubuntu 2.6.20-16.32-generic)
Dec  4 20:00:29 bokhari-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
Dec  4 20:00:29 bokhari-desktop kernel: [    0.000000] sanitize start
Dec  4 20:00:29 bokhari-desktop kernel: [    0.000000] sanitize end
Dec  4 20:00:29 bokhari-desktop kernel: [    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1
Dec  4 20:00:29 bokhari-desktop kernel: [    0.000000] copy_e820_map() type is E820_RAM
Dec  4 20:00:29 bokhari-desktop kernel: [    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2
Dec  4 20:00:29 bokhari-desktop kernel: [    0.000000] copy_e820_map() start: 00000000000ec000 size: 0000000000004000 end: 00000000000f0000 type: 4
Dec  4 20:00:29 bokhari-desktop kernel: [    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
Dec  4 20:00:29 bokhari-desktop kernel: [    0.000000] copy_e820_map() start: 0000000000100000 size: 0000000017f00000 end: 0000000018000000 type: 1
Dec  4 20:00:29 bokhari-desktop kernel: [    0.000000] copy_e820_map() type is E820_RAM
Dec  4 20:00:29 bokhari-desktop kernel: [    0.000000] copy_e820_map() start: 00000000fffc0000 size: 0000000000040000 end: 0000000100000000 type: 2
Dec  4 20:00:29 bokhari-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Dec  4 20:00:29 bokhari-desktop kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Dec  4 20:00:29 bokhari-desktop kernel: [    0.000000]  BIOS-e820: 00000000000ec000 - 00000000000f0000 (ACPI NVS)
Dec  4 20:00:29 bokhari-desktop kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Dec  4 20:00:29 bokhari-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 0000000018000000 (usable)
Dec  4 20:00:29 bokhari-desktop kernel: [    0.000000]  BIOS-e820: 00000000fffc0000 - 0000000100000000 (reserved)
Dec  4 20:00:29 bokhari-desktop kernel: [    0.000000] 0MB HIGHMEM available.
Dec  4 20:00:29 bokhari-desktop kernel: [    0.000000] 384MB LOWMEM available.
Dec  4 20:00:29 bokhari-desktop kernel: [    0.000000] Entering add_active_range(0, 0, 98304) 0 entries of 256 used
Dec  4 20:00:29 bokhari-desktop kernel: [    0.000000] Zone PFN ranges:
Dec  4 20:00:29 bokhari-desktop kernel: [    0.000000]   DMA             0 ->     4096
Dec  4 20:00:29 bokhari-desktop kernel: [    0.000000]   Normal       4096 ->    98304
Dec  4 20:00:29 bokhari-desktop kernel: [    0.000000]   HighMem     98304 ->    98304
Dec  4 20:00:29 bokhari-desktop kernel: [    0.000000] early_node_map[1] active PFN ranges
Dec  4 20:00:29 bokhari-desktop kernel: [    0.000000]     0:        0 ->    98304
Dec  4 20:00:29 bokhari-desktop kernel: [    0.000000] On node 0 totalpages: 98304
Dec  4 20:00:29 bokhari-desktop kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Dec  4 20:00:29 bokhari-desktop kernel: [    0.000000]   DMA zone: 0 pages reserved
Dec  4 20:00:29 bokhari-desktop kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Dec  4 20:00:29 bokhari-desktop kernel: [    0.000000]   Normal zone: 736 pages used for memmap
Dec  4 20:00:29 bokhari-desktop kernel: [    0.000000]   Normal zone: 93472 pages, LIFO batch:31
Dec  4 20:00:29 bokhari-desktop kernel: [    0.000000]   HighMem zone: 0 pages used for memmap
Dec  4 20:00:29 bokhari-desktop kernel: [    0.000000] DMI 2.1 present.
Dec  4 20:00:29 bokhari-desktop kernel: [    0.000000] ACPI: RSDP (v000 COMPAQ                                ) @ 0x000ec010
Dec  4 20:00:29 bokhari-desktop kernel: [    0.000000] ACPI: RSDT (v001 COMPAQ CARS6S6  0x00000001  0x00000000) @ 0x000ec080
Dec  4 20:00:29 bokhari-desktop kernel: [    0.000000] ACPI: FADT (v001 COMPAQ CARS6S6  0x00000001  0x00000000) @ 0x000ec0cc
Dec  4 20:00:29 bokhari-desktop kernel: [    0.000000] ACPI: SSDT (v001 COMPAQ CARS6S6  0x00000001 MSFT 0x01000007) @ 0x000ec177
Dec  4 20:00:29 bokhari-desktop kernel: [    0.000000] ACPI: DSDT (v001 COMPAQ DSDTTBL  0x00000001 MSFT 0x01000007) @ 0x00000000
Dec  4 20:00:29 bokhari-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0xee08
Dec  4 20:00:29 bokhari-desktop kernel: [    0.000000] Allocating PCI resources starting at 20000000 (gap: 18000000:e7fc0000)
Dec  4 20:00:29 bokhari-desktop kernel: [    0.000000] Detected 599.850 MHz processor.
Dec  4 20:00:29 bokhari-desktop kernel: [   27.040214] Built 1 zonelists.  Total pages: 97536
Dec  4 20:00:29 bokhari-desktop kernel: [   27.040226] Kernel command line: root=UUID=14d287f9-3c8f-4de9-a897-d8b636ce8ef1 ro quiet splash
Dec  4 20:00:29 bokhari-desktop kernel: [   27.040878] Local APIC disabled by BIOS -- you can enable it with "lapic"
Dec  4 20:00:29 bokhari-desktop kernel: [   27.040901] mapped APIC to ffffd000 (0130b000)
Dec  4 20:00:29 bokhari-desktop kernel: [   27.040914] Enabling fast FPU save and restore... done.
Dec  4 20:00:29 bokhari-desktop kernel: [   27.040923] Enabling unmasked SIMD FPU exception support... done.
Dec  4 20:00:29 bokhari-desktop kernel: [   27.040947] Initializing CPU#0
Dec  4 20:00:29 bokhari-desktop kernel: [   27.041094] PID hash table entries: 2048 (order: 11, 8192 bytes)
Dec  4 20:00:29 bokhari-desktop kernel: [   27.042733] Console: colour VGA+ 80x25
Dec  4 20:00:29 bokhari-desktop kernel: [   27.043355] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Dec  4 20:00:29 bokhari-desktop kernel: [   27.044459] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Dec  4 20:00:29 bokhari-desktop kernel: [   27.086895] Memory: 378680k/393216k available (1993k kernel code, 13956k reserved, 900k data, 328k init, 0k highmem)
Dec  4 20:00:29 bokhari-desktop kernel: [   27.086932] virtual kernel memory layout:
Dec  4 20:00:29 bokhari-desktop kernel: [   27.086936]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
Dec  4 20:00:29 bokhari-desktop kernel: [   27.086941]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Dec  4 20:00:29 bokhari-desktop kernel: [   27.086946]     vmalloc : 0xd8800000 - 0xff7fe000   ( 623 MB)
Dec  4 20:00:29 bokhari-desktop kernel: [   27.086951]     lowmem  : 0xc0000000 - 0xd8000000   ( 384 MB)
Dec  4 20:00:29 bokhari-desktop kernel: [   27.086956]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
Dec  4 20:00:29 bokhari-desktop kernel: [   27.086960]       .data : 0xc02f2429 - 0xc03d36d4   ( 900 kB)
Dec  4 20:00:29 bokhari-desktop kernel: [   27.086965]       .text : 0xc0100000 - 0xc02f2429   (1993 kB)
Dec  4 20:00:29 bokhari-desktop kernel: [   27.086976] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Dec  4 20:00:29 bokhari-desktop kernel: [   27.165092] Calibrating delay using timer specific routine.. 1201.36 BogoMIPS (lpj=2402728)
Dec  4 20:00:29 bokhari-desktop kernel: [   27.165222] Security Framework v1.0.0 initialized
Dec  4 20:00:29 bokhari-desktop kernel: [   27.165245] SELinux:  Disabled at boot.
Dec  4 20:00:29 bokhari-desktop kernel: [   27.165298] Mount-cache hash table entries: 512
Dec  4 20:00:29 bokhari-desktop kernel: [   27.165663] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
Dec  4 20:00:29 bokhari-desktop kernel: [   27.165697] CPU: L1 I cache: 16K, L1 D cache: 16K
Dec  4 20:00:29 bokhari-desktop kernel: [   27.165706] CPU: L2 cache: 256K
Dec  4 20:00:29 bokhari-desktop kernel: [   27.165716] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
Dec  4 20:00:29 bokhari-desktop kernel: [   27.165746] Compat vDSO mapped to ffffe000.
Dec  4 20:00:29 bokhari-desktop kernel: [   27.165765] Remapping vsyscall page to ffffe000
Dec  4 20:00:29 bokhari-desktop kernel: [   27.165792] Checking 'hlt' instruction... OK.
Dec  4 20:00:29 bokhari-desktop kernel: [   27.181348] SMP alternatives: switching to UP code
Dec  4 20:00:29 bokhari-desktop kernel: [   27.181823] Freeing SMP alternatives: 11k freed
Dec  4 20:00:29 bokhari-desktop kernel: [   27.182389] Early unpacking initramfs... done
Dec  4 20:00:29 bokhari-desktop kernel: [   28.183775] ACPI: Core revision 20060707
Dec  4 20:00:29 bokhari-desktop kernel: [   28.185549] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
Dec  4 20:00:29 bokhari-desktop kernel: [   28.188354] ACPI: setting ELCR to 0200 (from 0c08)
Dec  4 20:00:29 bokhari-desktop kernel: [   28.194813] CPU0: Intel Pentium III (Coppermine) stepping 01
Dec  4 20:00:29 bokhari-desktop kernel: [   28.194831] SMP motherboard not detected.
Dec  4 20:00:29 bokhari-desktop kernel: [   28.194840] Local APIC not detected. Using dummy APIC emulation.
Dec  4 20:00:29 bokhari-desktop kernel: [   28.194961] Brought up 1 CPUs
Dec  4 20:00:29 bokhari-desktop kernel: [   28.195695] Booting paravirtualized kernel on bare hardware
Dec  4 20:00:29 bokhari-desktop kernel: [   28.195887] Time:  0:59:44  Date: 11/05/107
Dec  4 20:00:29 bokhari-desktop kernel: [   28.195976] NET: Registered protocol family 16
Dec  4 20:00:29 bokhari-desktop kernel: [   28.196248] EISA bus registered
Dec  4 20:00:29 bokhari-desktop kernel: [   28.196262] ACPI: bus type pci registered
Dec  4 20:00:29 bokhari-desktop kernel: [   28.197768] PCI: PCI BIOS revision 2.10 entry at 0xfa184, last bus=1
Dec  4 20:00:29 bokhari-desktop kernel: [   28.197777] PCI: Using configuration type 1
Dec  4 20:00:29 bokhari-desktop kernel: [   28.197783] Setting up standard PCI resources
Dec  4 20:00:29 bokhari-desktop kernel: [   28.211103] ACPI: Interpreter enabled
Dec  4 20:00:29 bokhari-desktop kernel: [   28.211115] ACPI: Using PIC for interrupt routing
Dec  4 20:00:29 bokhari-desktop kernel: [   28.212656] ACPI: PCI Interrupt Link [LNKA] (IRQs *3 4 5 6 7 10 11)
Dec  4 20:00:29 bokhari-desktop kernel: [   28.213423] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Dec  4 20:00:29 bokhari-desktop kernel: [   28.214163] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *10 11)
Dec  4 20:00:29 bokhari-desktop kernel: [   28.214888] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11)
Dec  4 20:00:29 bokhari-desktop kernel: [   28.215282] ACPI: PCI Root Bridge [PCI0] (0000:00)
Dec  4 20:00:29 bokhari-desktop kernel: [   28.215297] PCI: Probing PCI hardware (bus 00)
Dec  4 20:00:29 bokhari-desktop kernel: [   28.215853] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
Dec  4 20:00:29 bokhari-desktop kernel: [   28.216893] PCI quirk: region ee00-eeff claimed by vt82c586 ACPI
Dec  4 20:00:29 bokhari-desktop kernel: [   28.217110] Boot video device is 0000:01:00.0
Dec  4 20:00:29 bokhari-desktop kernel: [   28.217183] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Dec  4 20:00:29 bokhari-desktop kernel: [   28.224585] Linux Plug and Play Support v0.97 (c) Adam Belay
Dec  4 20:00:29 bokhari-desktop kernel: [   28.224622] pnp: PnP ACPI init
Dec  4 20:00:29 bokhari-desktop kernel: [   28.231368] pnp: PnP ACPI: found 12 devices
Dec  4 20:00:29 bokhari-desktop kernel: [   28.231384] PnPBIOS: Disabled by ACPI PNP
Dec  4 20:00:29 bokhari-desktop kernel: [   28.231555] PCI: Using ACPI for IRQ routing
Dec  4 20:00:29 bokhari-desktop kernel: [   28.231566] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Dec  4 20:00:29 bokhari-desktop kernel: [   28.261823] NET: Registered protocol family 8
Dec  4 20:00:29 bokhari-desktop kernel: [   28.261831] NET: Registered protocol family 20
Dec  4 20:00:29 bokhari-desktop kernel: [   28.262452] pnp: 00:02: ioport range 0x4d0-0x4d1 has been reserved
Dec  4 20:00:29 bokhari-desktop kernel: [   28.262465] pnp: 00:02: ioport range 0xee00-0xee7f could not be reserved
Dec  4 20:00:29 bokhari-desktop kernel: [   28.262476] pnp: 00:02: ioport range 0xee80-0xeeff has been reserved
Dec  4 20:00:29 bokhari-desktop kernel: [   28.262493] pnp: 00:02: ioport range 0xef00-0xef5f has been reserved
Dec  4 20:00:29 bokhari-desktop kernel: [   28.263401] PCI: Bridge: 0000:00:01.0
Dec  4 20:00:29 bokhari-desktop kernel: [   28.263409]   IO window: disabled.
Dec  4 20:00:29 bokhari-desktop kernel: [   28.263420]   MEM window: 40000000-400fffff
Dec  4 20:00:29 bokhari-desktop kernel: [   28.263430]   PREFETCH window: 48000000-4fffffff
Dec  4 20:00:29 bokhari-desktop kernel: [   28.263459] PCI: Setting latency timer of device 0000:00:01.0 to 64
Dec  4 20:00:29 bokhari-desktop kernel: [   28.263536] NET: Registered protocol family 2
Dec  4 20:00:29 bokhari-desktop kernel: [   28.301185] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
Dec  4 20:00:29 bokhari-desktop kernel: [   28.301429] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
Dec  4 20:00:29 bokhari-desktop kernel: [   28.301826] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
Dec  4 20:00:29 bokhari-desktop kernel: [   28.302086] TCP: Hash tables configured (established 16384 bind 8192)
Dec  4 20:00:29 bokhari-desktop kernel: [   28.302095] TCP reno registered
Dec  4 20:00:29 bokhari-desktop kernel: [   28.313431] checking if image is initramfs... it is
Dec  4 20:00:29 bokhari-desktop kernel: [   30.221033] Freeing initrd memory: 6777k freed
Dec  4 20:00:29 bokhari-desktop kernel: [   30.222124] audit: initializing netlink socket (disabled)
Dec  4 20:00:29 bokhari-desktop kernel: [   30.222164] audit(1196816386.364:1): initialized
Dec  4 20:00:29 bokhari-desktop kernel: [   30.222555] VFS: Disk quotas dquot_6.5.1
Dec  4 20:00:29 bokhari-desktop kernel: [   30.222622] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Dec  4 20:00:29 bokhari-desktop kernel: [   30.222766] io scheduler noop registered
Dec  4 20:00:29 bokhari-desktop kernel: [   30.222776] io scheduler anticipatory registered
Dec  4 20:00:29 bokhari-desktop kernel: [   30.222784] io scheduler deadline registered
Dec  4 20:00:29 bokhari-desktop kernel: [   30.222818] io scheduler cfq registered (default)
Dec  4 20:00:29 bokhari-desktop kernel: [   30.222852] PCI: Disabling Via external APIC routing
Dec  4 20:00:29 bokhari-desktop kernel: [   30.223496] isapnp: Scanning for PnP cards...
Dec  4 20:00:29 bokhari-desktop kernel: [   30.578370] isapnp: No Plug & Play device found
Dec  4 20:00:29 bokhari-desktop kernel: [   30.665375] Real Time Clock Driver v1.12ac
Dec  4 20:00:29 bokhari-desktop kernel: [   30.665506] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Dec  4 20:00:29 bokhari-desktop kernel: [   30.665765] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Dec  4 20:00:29 bokhari-desktop kernel: [   30.667727] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Dec  4 20:00:29 bokhari-desktop kernel: [   30.668356] mice: PS/2 mouse device common for all mice
Dec  4 20:00:29 bokhari-desktop kernel: [   30.670221] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Dec  4 20:00:29 bokhari-desktop kernel: [   30.670942] input: Macintosh mouse button emulation as /class/input/input0
Dec  4 20:00:29 bokhari-desktop kernel: [   30.671053] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Dec  4 20:00:29 bokhari-desktop kernel: [   30.671067] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Dec  4 20:00:29 bokhari-desktop kernel: [   30.671559] PNP: PS/2 Controller [PNP0303:KBD,PNP0f0e:PS2M] at 0x60,0x64 irq 1,12
Dec  4 20:00:29 bokhari-desktop kernel: [   30.672175] serio: i8042 KBD port at 0x60,0x64 irq 1
Dec  4 20:00:29 bokhari-desktop kernel: [   30.672191] serio: i8042 AUX port at 0x60,0x64 irq 12
Dec  4 20:00:29 bokhari-desktop kernel: [   30.672555] EISA: Probing bus 0 at eisa.0
Dec  4 20:00:29 bokhari-desktop kernel: [   30.672577] Cannot allocate resource for EISA slot 1
Dec  4 20:00:29 bokhari-desktop kernel: [   30.672634] EISA: Detected 0 cards.
Dec  4 20:00:29 bokhari-desktop kernel: [   30.703067] TCP cubic registered
Dec  4 20:00:29 bokhari-desktop kernel: [   30.703096] NET: Registered protocol family 1
Dec  4 20:00:29 bokhari-desktop kernel: [   30.703164] Using IPI No-Shortcut mode
Dec  4 20:00:29 bokhari-desktop kernel: [   30.703394] ACPI: (supports S0 S1 S5)
Dec  4 20:00:29 bokhari-desktop kernel: [   30.703506]   Magic number: 3:849:960
Dec  4 20:00:29 bokhari-desktop kernel: [   30.703543]   hash matches device ttyb1
Dec  4 20:00:29 bokhari-desktop kernel: [   30.704403] Freeing unused kernel memory: 328k freed
Dec  4 20:00:29 bokhari-desktop kernel: [   30.704802] Time: tsc clocksource has been installed.
Dec  4 20:00:29 bokhari-desktop kernel: [   30.723743] input: AT Translated Set 2 keyboard as /class/input/input1
Dec  4 20:00:29 bokhari-desktop kernel: [   32.410876] Capability LSM initialized
Dec  4 20:00:29 bokhari-desktop kernel: [   32.544834] ACPI: CPU0 (power states: C1[C1] C2[C2])
Dec  4 20:00:29 bokhari-desktop kernel: [   34.033643] natsemi dp8381x driver, version 2.1, Sept 11, 2006
Dec  4 20:00:29 bokhari-desktop kernel: [   34.033650]   originally by Donald Becker <becker@scyld.com>
Dec  4 20:00:29 bokhari-desktop kernel: [   34.033655]   [http://www.scyld.com/network/natsemi.html](http://www.scyld.com/network/natsemi.html)
Dec  4 20:00:29 bokhari-desktop kernel: [   34.033660]   2.4.x kernel port by Jeff Garzik, Tjeerd Mulder
Dec  4 20:00:29 bokhari-desktop kernel: [   34.033746] PCI: Enabling device 0000:00:03.0 (0004 -> 0007)
Dec  4 20:00:29 bokhari-desktop kernel: [   34.034502] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 3
Dec  4 20:00:29 bokhari-desktop kernel: [   34.034513] PCI: setting IRQ 3 as level-triggered
Dec  4 20:00:29 bokhari-desktop kernel: [   34.034523] ACPI: PCI Interrupt 0000:00:03.0[A] -> Link [LNKA] -> GSI 3 (level, low) -> IRQ 3
Dec  4 20:00:29 bokhari-desktop kernel: [   34.036371] natsemi eth0: NatSemi DP8381[56] at 0x40300000 (0000:00:03.0), 00:09:5b:0b:8f:e5, IRQ 3, port TP.
Dec  4 20:00:29 bokhari-desktop kernel: [   34.110644] ieee1394: Initialized config rom entry `ip1394'
Dec  4 20:00:29 bokhari-desktop kernel: [   34.118122] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
Dec  4 20:00:29 bokhari-desktop kernel: [   34.118136] PCI: setting IRQ 10 as level-triggered
Dec  4 20:00:29 bokhari-desktop kernel: [   34.118147] ACPI: PCI Interrupt 0000:00:0c.0[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
Dec  4 20:00:29 bokhari-desktop kernel: [   34.169397] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[10]  MMIO=[40400000-404007ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Dec  4 20:00:29 bokhari-desktop kernel: [   34.321435] SCSI subsystem initialized
Dec  4 20:00:29 bokhari-desktop kernel: [   34.351898] libata version 2.20 loaded.
Dec  4 20:00:29 bokhari-desktop kernel: [   34.366344] VP_IDE: IDE controller at PCI slot 0000:00:14.1
Dec  4 20:00:29 bokhari-desktop kernel: [   34.366376] VP_IDE: chipset revision 6
Dec  4 20:00:29 bokhari-desktop kernel: [   34.366383] VP_IDE: not 100%% native mode: will probe irqs later
Dec  4 20:00:29 bokhari-desktop kernel: [   34.366408] VP_IDE: VIA vt82c686a (rev 14) IDE UDMA66 controller on pci0000:00:14.1
Dec  4 20:00:29 bokhari-desktop kernel: [   34.366427]     ide0: BM-DMA at 0x1480-0x1487, BIOS settings: hda:DMA, hdb:pio
Dec  4 20:00:29 bokhari-desktop kernel: [   34.366454]     ide1: BM-DMA at 0x1488-0x148f, BIOS settings: hdc:DMA, hdd:DMA
Dec  4 20:00:29 bokhari-desktop kernel: [   34.366471] Probing IDE interface ide0...
Dec  4 20:00:29 bokhari-desktop kernel: [   34.404655] usbcore: registered new interface driver usbfs
Dec  4 20:00:29 bokhari-desktop kernel: [   34.404722] usbcore: registered new interface driver hub
Dec  4 20:00:29 bokhari-desktop kernel: [   34.404796] usbcore: registered new device driver usb
Dec  4 20:00:29 bokhari-desktop kernel: [   34.409621] USB Universal Host Controller Interface driver v3.0
Dec  4 20:00:29 bokhari-desktop kernel: [   34.814398] Floppy drive(s): fd0 is 1.44M
Dec  4 20:00:29 bokhari-desktop kernel: [   34.824593] hda: ST320430A, ATA DISK drive
Dec  4 20:00:29 bokhari-desktop kernel: [   34.844757] FDC 0 is a post-1991 82077
Dec  4 20:00:29 bokhari-desktop kernel: [    7.904000] Time: acpi_pm clocksource has been installed.
Dec  4 20:00:29 bokhari-desktop kernel: [    8.404000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0040d01222050665]
Dec  4 20:00:29 bokhari-desktop kernel: [    8.456000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Dec  4 20:00:29 bokhari-desktop kernel: [    8.456000] Probing IDE interface ide1...
Dec  4 20:00:29 bokhari-desktop kernel: [    9.320000] hdc: Compaq DVD-ROM DVD-114 0114, ATAPI CD/DVD-ROM drive
Dec  4 20:00:29 bokhari-desktop kernel: [   10.104000] hdd: DVD-RW IDE1008, ATAPI CD/DVD-ROM drive
Dec  4 20:00:29 bokhari-desktop kernel: [   10.160000] ide1 at 0x170-0x177,0x376 on irq 15
Dec  4 20:00:29 bokhari-desktop kernel: [   10.160000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
Dec  4 20:00:29 bokhari-desktop kernel: [   10.160000] PCI: setting IRQ 11 as level-triggered
Dec  4 20:00:29 bokhari-desktop kernel: [   10.160000] ACPI: PCI Interrupt 0000:00:14.2[D] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Dec  4 20:00:29 bokhari-desktop kernel: [   10.160000] uhci_hcd 0000:00:14.2: UHCI Host Controller
Dec  4 20:00:29 bokhari-desktop kernel: [   10.160000] uhci_hcd 0000:00:14.2: new USB bus registered, assigned bus number 1
Dec  4 20:00:29 bokhari-desktop kernel: [   10.160000] uhci_hcd 0000:00:14.2: irq 11, io base 0x00001440
Dec  4 20:00:29 bokhari-desktop kernel: [   10.164000] usb usb1: configuration #1 chosen from 1 choice
Dec  4 20:00:29 bokhari-desktop kernel: [   10.164000] hub 1-0:1.0: USB hub found
Dec  4 20:00:29 bokhari-desktop kernel: [   10.164000] hub 1-0:1.0: 2 ports detected
Dec  4 20:00:29 bokhari-desktop kernel: [   10.184000] hda: max request size: 128KiB
Dec  4 20:00:29 bokhari-desktop kernel: [   10.184000] hda: 39102336 sectors (20020 MB) w/512KiB Cache, CHS=38792/16/63, UDMA(66)
Dec  4 20:00:29 bokhari-desktop kernel: [   10.184000] hda: cache flushes not supported
Dec  4 20:00:29 bokhari-desktop kernel: [   10.184000]  hda: hda1 hda2 < hda5 >
Dec  4 20:00:29 bokhari-desktop kernel: [   10.268000] ACPI: PCI Interrupt 0000:00:14.3[D] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Dec  4 20:00:29 bokhari-desktop kernel: [   10.268000] uhci_hcd 0000:00:14.3: UHCI Host Controller
Dec  4 20:00:29 bokhari-desktop kernel: [   10.268000] uhci_hcd 0000:00:14.3: new USB bus registered, assigned bus number 2
Dec  4 20:00:29 bokhari-desktop kernel: [   10.268000] uhci_hcd 0000:00:14.3: irq 11, io base 0x00001460
Dec  4 20:00:29 bokhari-desktop kernel: [   10.268000] usb usb2: configuration #1 chosen from 1 choice
Dec  4 20:00:29 bokhari-desktop kernel: [   10.268000] hub 2-0:1.0: USB hub found
Dec  4 20:00:29 bokhari-desktop kernel: [   10.268000] hub 2-0:1.0: 2 ports detected
Dec  4 20:00:29 bokhari-desktop kernel: [   10.284000] hdc: ATAPI DVD-ROM drive, 512kB Cache, UDMA(33)
Dec  4 20:00:29 bokhari-desktop kernel: [   10.284000] Uniform CD-ROM driver Revision: 3.20
Dec  4 20:00:29 bokhari-desktop kernel: [   10.288000] hdd: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
Dec  4 20:00:29 bokhari-desktop kernel: [   10.636000] usb 1-2: new full speed USB device using uhci_hcd and address 2
Dec  4 20:00:29 bokhari-desktop kernel: [   10.748000] Attempting manual resume
Dec  4 20:00:29 bokhari-desktop kernel: [   10.748000] swsusp: Resume From Partition 3:5
Dec  4 20:00:29 bokhari-desktop kernel: [   10.748000] PM: Checking swsusp image.
Dec  4 20:00:29 bokhari-desktop kernel: [   10.764000] PM: Resume from disk failed.
Dec  4 20:00:29 bokhari-desktop kernel: [   10.820000] EXT3-fs: INFO: recovery required on readonly filesystem.
Dec  4 20:00:29 bokhari-desktop kernel: [   10.820000] EXT3-fs: write access will be enabled during recovery.
Dec  4 20:00:29 bokhari-desktop kernel: [   10.832000] usb 1-2: configuration #1 chosen from 1 choice
Dec  4 20:00:29 bokhari-desktop kernel: [   13.172000] kjournald starting.  Commit interval 5 seconds
Dec  4 20:00:29 bokhari-desktop kernel: [   13.172000] EXT3-fs: recovery complete.
Dec  4 20:00:29 bokhari-desktop kernel: [   13.176000] EXT3-fs: mounted filesystem with ordered data mode.
Dec  4 20:00:29 bokhari-desktop kernel: [   26.912000] eth0: DSPCFG accepted after 0 usec.
Dec  4 20:00:29 bokhari-desktop kernel: [   26.912000] eth0: link up.
Dec  4 20:00:29 bokhari-desktop kernel: [   26.912000] eth0: Setting full-duplex based on negotiated link capability.
Dec  4 20:00:29 bokhari-desktop kernel: [   28.484000] NET: Registered protocol family 17
Dec  4 20:00:29 bokhari-desktop kernel: [   31.364000] Linux agpgart interface v0.102 (c) Dave Jones
Dec  4 20:00:29 bokhari-desktop kernel: [   31.404000] parport_pc: VIA 686A/8231 detected
Dec  4 20:00:29 bokhari-desktop kernel: [   31.404000] parport_pc: probing current configuration
Dec  4 20:00:29 bokhari-desktop kernel: [   31.404000] parport_pc: Current parallel port base: 0x378
Dec  4 20:00:29 bokhari-desktop kernel: [   31.404000] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
Dec  4 20:00:29 bokhari-desktop kernel: [   31.504000] parport_pc: VIA parallel port: io=0x378, irq=7
Dec  4 20:00:29 bokhari-desktop kernel: [   32.084000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Dec  4 20:00:29 bokhari-desktop kernel: [   32.128000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Dec  4 20:00:29 bokhari-desktop kernel: [   32.140000] agpgart: Detected VIA Apollo Pro 133 chipset
Dec  4 20:00:29 bokhari-desktop kernel: [   32.144000] agpgart: AGP aperture is 64M @ 0x50000000
Dec  4 20:00:29 bokhari-desktop kernel: [   32.324000] via686a 0000:00:14.4: base address not set - upgrade BIOS or use force_addr=0xaddr
Dec  4 20:00:29 bokhari-desktop kernel: [   32.344000] vt596_smbus 0000:00:14.4: SMBus base address uninitialized - upgrade BIOS or use force_addr=0xaddr
Dec  4 20:00:29 bokhari-desktop kernel: [   33.084000] input: PC Speaker as /class/input/input2
Dec  4 20:00:29 bokhari-desktop kernel: [   33.516000] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
Dec  4 20:00:29 bokhari-desktop kernel: [   34.440000] savage4_smbus 0000:01:00.0: Using Savage4 at d8b00000
Dec  4 20:00:29 bokhari-desktop kernel: [   34.780000] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
Dec  4 20:00:29 bokhari-desktop kernel: [   35.228000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x04E8 pid 0x323A
Dec  4 20:00:29 bokhari-desktop kernel: [   35.228000] usbcore: registered new interface driver usblp
Dec  4 20:00:29 bokhari-desktop kernel: [   35.228000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
Dec  4 20:00:29 bokhari-desktop kernel: [   36.028000] fuse init (API version 7.8)
Dec  4 20:00:29 bokhari-desktop kernel: [   36.068000] lp0: using parport0 (interrupt-driven).
Dec  4 20:00:29 bokhari-desktop kernel: [   36.216000] Adding 859436k swap on /dev/disk/by-uuid/e006537a-c90b-414b-909c-33fcca742104.  Priority:-1 extents:1 across:859436k
Dec  4 20:00:29 bokhari-desktop kernel: [   36.384000] EXT3 FS on hda1, internal journal
Dec  4 20:00:29 bokhari-desktop kernel: [   36.668000] NET: Registered protocol family 10
Dec  4 20:00:29 bokhari-desktop kernel: [   36.668000] lo: Disabled Privacy Extensions
Dec  4 20:00:29 bokhari-desktop kernel: [   44.436000] No dock devices found.
Dec  4 20:00:29 bokhari-desktop kernel: [   44.720000] input: Power Button (FF) as /class/input/input4
Dec  4 20:00:29 bokhari-desktop kernel: [   44.720000] ACPI: Power Button (FF) [PWRF]
Dec  4 20:00:29 bokhari-desktop kernel: [   44.760000] input: Power Button (CM) as /class/input/input5
Dec  4 20:00:29 bokhari-desktop kernel: [   44.760000] ACPI: Power Button (CM) [PBTN]
Dec  4 20:00:29 bokhari-desktop kernel: [   44.932000] Using specific hotkey driver
Dec  4 20:00:29 bokhari-desktop kernel: [   45.024000] ibm_acpi: ec object not found
Dec  4 20:00:29 bokhari-desktop kernel: [   45.236000] pcc_acpi: loading...
Dec  4 20:00:30 bokhari-desktop kernel: [   47.196000] eth0: no IPv6 routers present
Dec  4 20:00:40 bokhari-desktop kernel: [   57.180000] ppdev: user-space parallel port driver
Dec  4 20:00:40 bokhari-desktop kernel: [   57.268000] [drm] Initialized drm 1.1.0 20060810
Dec  4 20:00:40 bokhari-desktop kernel: [   57.304000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 3 (level, low) -> IRQ 3
Dec  4 20:00:40 bokhari-desktop kernel: [   57.312000] [drm] Initialized savage 2.4.1 20050313 on minor 0
Dec  4 20:00:40 bokhari-desktop kernel: [   57.316000] mtrr: base(0x4a000000) is not aligned on a size(0x5000000) boundary
Dec  4 20:00:40 bokhari-desktop kernel: [   57.316000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Dec  4 20:00:40 bokhari-desktop kernel: [   57.316000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
Dec  4 20:00:40 bokhari-desktop kernel: [   57.316000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
Dec  4 20:00:42 bokhari-desktop kernel: [   59.420000] apm: BIOS not found.
Dec  4 20:00:53 bokhari-desktop kernel: [   69.972000] eth0: no IPv6 routers present

this is pretty much what it always says. anything i can do to fix this? please give thorough explanation because i am pretty much a beginner!

---

### Post by gazj on 2007-12-04
i am no expert a kernel logs by any means, but i would try opening a terminal

entering the command

```
top
```

keep watching, the process using the most runtime will be at the top, when it freezes try to see what process is at the top, might give some pointers to the problems (thats presuming it freezes regulary of course)

let us know how you get on

---

