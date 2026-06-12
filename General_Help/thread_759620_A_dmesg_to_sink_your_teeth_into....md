---
title: "A dmesg to sink your teeth into..."
date: 2008-04-19
forum: General Help
---

### Post by an0nu4nc3 on 2008-04-19
First, i've no idea if this is in the right place but i believe installing and updating has gotten me into the position i'm in now.

I've been surfing around and learning and installing and upgrading and added a module to my kernel to get a wireless USB stick working, i think... or it could have been the ov51x webcam drivers... or a USB hard drive or a multitude of other programs and things i've done to my machine over the past several months. I'm getting very lost and confused and now things are slowing down and there are more and more outputs when i start up and shut down.

I'm near the end of my patience basically. I need your direct help :) So here i am!

Here is the output when i type dmesg in the terminal:

```
[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 07:42:25 UTC 2008 (Ubuntu 2.6.22-14.52-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fff0000 (usable)
[    0.000000]  BIOS-e820: 000000003fff0000 - 000000003fff8000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003fff8000 - 0000000040000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000fb940
[    0.000000] Entering add_active_range(0, 0, 262128) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   262128
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   262128
[    0.000000] On node 0 totalpages: 262128
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 255 pages used for memmap
[    0.000000]   HighMem zone: 32497 pages, LIFO batch:7
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FA9D0 checksum 0
[    0.000000] ACPI: RSDP 000FA9D0, 0014 (r0 AMI   )
[    0.000000] ACPI: RSDT 3FFF0000, 002C (r1 AMIINT VIA_K7         10 MSFT       97)
[    0.000000] ACPI: FACP 3FFF0030, 0081 (r1 AMIINT VIA_K7         11 MSFT       97)
[    0.000000] ACPI: DSDT 3FFF0120, 31B3 (r1    VIA   VIA_K7     1000 MSFT  100000D)
[    0.000000] ACPI: FACS 3FFF8000, 0040
[    0.000000] ACPI: APIC 3FFF00C0, 0054 (r1 AMIINT VIA_K7          9 MSFT       97)
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:8 APIC version 16
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000)
[    0.000000] Built 1 zonelists.  Total pages: 260081
[    0.000000] Kernel command line: root=UUID=37f61175-e5de-4e13-b9e8-4f916c8bd55b ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2000.250 MHz processor.
[   25.432966] Console: colour VGA+ 80x25
[   25.433793] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   25.435224] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   25.471094] Memory: 1027880k/1048512k available (2015k kernel code, 19928k reserved, 915k data, 364k init, 131008k highmem)
[   25.471105] virtual kernel memory layout:
[   25.471106]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   25.471108]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   25.471109]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   25.471110]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   25.471112]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   25.471113]       .data : 0xc02f7e86 - 0xc03dce84   ( 915 kB)
[   25.471114]       .text : 0xc0100000 - 0xc02f7e86   (2015 kB)
[   25.471118] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   25.471171] SLUB: Genslabs=22, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   25.551051] Calibrating delay using timer specific routine.. 4004.87 BogoMIPS (lpj=8009758)
[   25.551093] Security Framework v1.0.0 initialized
[   25.551103] SELinux:  Disabled at boot.
[   25.551124] Mount-cache hash table entries: 512
[   25.551309] CPU: After generic identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000 00000000
[   25.551318] CPU: CLK_CTL MSR was 6003d22f. Reprogramming to 2003d22f
[   25.551323] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   25.551325] CPU: L2 Cache: 256K (64 bytes/line)
[   25.551329] CPU: After all inits, caps: 0383fbff c1c3fbff 00000000 00000420 00000000 00000000 00000000
[   25.551343] Compat vDSO mapped to ffffe000.
[   25.551359] Checking 'hlt' instruction... OK.
[   25.567198] SMP alternatives: switching to UP code
[   25.567521] Freeing SMP alternatives: 11k freed
[   25.567917] Early unpacking initramfs... done
[   25.882490] ACPI: Core revision 20070126
[   25.882590] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   25.884167] CPU0: AMD Athlon(tm) XP 2400+ stepping 01
[   25.884194] Total of 1 processors activated (4004.87 BogoMIPS).
[   25.884950] ENABLING IO-APIC IRQs
[   25.885281] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   26.030231] Brought up 1 CPUs
[   26.030410] Booting paravirtualized kernel on bare hardware
[   26.030517] Time: 11:59:44  Date: 03/19/108
[   26.030551] NET: Registered protocol family 16
[   26.030667] EISA bus registered
[   26.030686] ACPI: bus type pci registered
[   26.037594] PCI: PCI BIOS revision 2.10 entry at 0xfdaf1, last bus=1
[   26.037597] PCI: Using configuration type 1
[   26.037599] Setting up standard PCI resources
[   26.042379] ACPI: EC: Look up EC in DSDT
[   26.045756] ACPI: Interpreter enabled
[   26.045759] ACPI: (supports S0 S1 S3 S4 S5)
[   26.045775] ACPI: Using IOAPIC for interrupt routing
[   26.049852] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   26.049860] PCI: Probing PCI hardware (bus 00)
[   26.049984] PCI: Firmware left 0000:00:06.0 e100 interrupts enabled, disabling
[   26.050321] PCI quirk: region 0800-087f claimed by vt8235 PM
[   26.050325] PCI quirk: region 0400-040f claimed by vt8235 SMB
[   26.050499] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   26.062314] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   26.062400] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   26.062482] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   26.062563] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   26.062655] ACPI: Power Resource [URP1] (off)
[   26.062682] ACPI: Power Resource [URP2] (off)
[   26.062707] ACPI: Power Resource [FDDP] (off)
[   26.062732] ACPI: Power Resource [LPTP] (off)
[   26.062744] Linux Plug and Play Support v0.97 (c) Adam Belay
[   26.062765] pnp: PnP ACPI init
[   26.062775] ACPI: bus type pnp registered
[   26.065136] pnp: PnP ACPI: found 11 devices
[   26.065139] ACPI: ACPI bus type pnp unregistered
[   26.065143] PnPBIOS: Disabled by ACPI PNP
[   26.065210] PCI: Using ACPI for IRQ routing
[   26.065213] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   26.067179] NET: Registered protocol family 8
[   26.067182] NET: Registered protocol family 20
[   26.070106] Time: tsc clocksource has been installed.
[   26.097533] PCI: Bridge: 0000:00:01.0
[   26.097535]   IO window: disabled.
[   26.097540]   MEM window: dda00000-dfafffff
[   26.097544]   PREFETCH window: cd900000-dd8fffff
[   26.097561] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   26.097572] NET: Registered protocol family 2
[   26.134054] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   26.134284] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   26.137159] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   26.138183] TCP: Hash tables configured (established 131072 bind 65536)
[   26.138187] TCP reno registered
[   26.150131] checking if image is initramfs... it is
[   26.597149] Switched to high resolution mode on CPU 0
[   26.745623] Freeing initrd memory: 7063k freed
[   26.746126] audit: initializing netlink socket (disabled)
[   26.746143] audit(1208606383.996:1): initialized
[   26.746221] highmem bounce pool size: 64 pages
[   26.748171] VFS: Disk quotas dquot_6.5.1
[   26.748240] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   26.748353] io scheduler noop registered
[   26.748356] io scheduler anticipatory registered
[   26.748358] io scheduler deadline registered
[   26.748372] io scheduler cfq registered (default)
[   26.748386] PCI: VIA PCI bridge detected. Disabling DAC.
[   26.748443] Boot video device is 0000:01:00.0
[   26.748618] isapnp: Scanning for PnP cards...
[   27.101903] isapnp: No Plug & Play device found
[   27.135070] Real Time Clock Driver v1.12ac
[   27.135169] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   27.135277] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   27.135562] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   27.136408] 00:02: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   27.136805] 00:03: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   27.137699] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   27.137940] input: Macintosh mouse button emulation as /class/input/input0
[   27.138029] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   27.138412] serio: i8042 KBD port at 0x60,0x64 irq 1
[   27.138418] serio: i8042 AUX port at 0x60,0x64 irq 12
[   27.138593] mice: PS/2 mouse device common for all mice
[   27.138711] EISA: Probing bus 0 at eisa.0
[   27.138751] EISA: Detected 0 cards.
[   27.138955] TCP cubic registered
[   27.138965] NET: Registered protocol family 1
[   27.138988] Using IPI No-Shortcut mode
[   27.139168]   Magic number: 4:24:985
[   27.139886] Freeing unused kernel memory: 364k freed
[   27.180117] input: AT Translated Set 2 keyboard as /class/input/input1
[   28.350836] AppArmor: AppArmor initialized<5>audit(1208606385.496:2):  type=1505 info="AppArmor initialized" pid=1115
[   28.357959] fuse init (API version 7.8)
[   28.363158] Failure registering capabilities with primary security module.
[   28.379132] ACPI: Processor [CPU1] (supports 16 throttling states)
[   28.991994] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k4-NAPI
[   28.991999] e100: Copyright(c) 1999-2006 Intel Corporation
[   28.992047] ACPI: PCI Interrupt 0000:00:06.0[A] -> GSI 17 (level, low) -> IRQ 16
[   29.011829] e100: eth0: e100_probe: addr 0xdd9ff000, irq 16, MAC addr 00:AA:00:CA:04:1F
[   29.062041] usbcore: registered new interface driver usbfs
[   29.062081] usbcore: registered new interface driver hub
[   29.062107] usbcore: registered new device driver usb
[   29.063067] USB Universal Host Controller Interface driver v3.0
[   29.063168] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 17
[   29.063181] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   29.063372] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   29.063405] uhci_hcd 0000:00:10.0: irq 17, io base 0x0000d800
[   29.063570] usb usb1: configuration #1 chosen from 1 choice
[   29.063598] hub 1-0:1.0: USB hub found
[   29.063609] hub 1-0:1.0: 2 ports detected
[   29.112421] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   29.112429] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   29.164482] ACPI: PCI Interrupt 0000:00:10.1[B] -> GSI 21 (level, low) -> IRQ 17
[   29.164498] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   29.164526] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   29.164552] uhci_hcd 0000:00:10.1: irq 17, io base 0x0000dc00
[   29.164671] usb usb2: configuration #1 chosen from 1 choice
[   29.164699] hub 2-0:1.0: USB hub found
[   29.164709] hub 2-0:1.0: 2 ports detected
[   29.199516] Floppy drive(s): fd0 is 1.44M
[   29.227921] FDC 0 is a post-1991 82077
[   29.272213] ACPI: PCI Interrupt 0000:00:10.2[C] -> GSI 21 (level, low) -> IRQ 17
[   29.272229] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   29.272257] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[   29.272281] uhci_hcd 0000:00:10.2: irq 17, io base 0x0000e000
[   29.272398] usb usb3: configuration #1 chosen from 1 choice
[   29.272433] hub 3-0:1.0: USB hub found
[   29.272443] hub 3-0:1.0: 2 ports detected
[   29.377912] ACPI: PCI Interrupt 0000:00:10.3[D] -> GSI 21 (level, low) -> IRQ 17
[   29.377934] ehci_hcd 0000:00:10.3: EHCI Host Controller
[   29.377996] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[   29.378057] ehci_hcd 0000:00:10.3: irq 17, io mem 0xdfdfff00
[   29.378064] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   29.378184] usb usb4: configuration #1 chosen from 1 choice
[   29.378215] hub 4-0:1.0: USB hub found
[   29.378228] hub 4-0:1.0: 6 ports detected
[   29.479931] VP_IDE: IDE controller at PCI slot 0000:00:11.1
[   29.479955] ACPI: Unable to derive IRQ for device 0000:00:11.1
[   29.479957] ACPI: PCI Interrupt 0000:00:11.1[A]: no GSI
[   29.479970] VP_IDE: chipset revision 6
[   29.479972] VP_IDE: not 100% native mode: will probe irqs later
[   29.479983] VP_IDE: VIA vt8235 (rev 00) IDE UDMA133 controller on pci0000:00:11.1
[   29.479992]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:DMA, hdb:pio
[   29.480006]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:DMA, hdd:DMA
[   29.480014] Probing IDE interface ide0...
[   29.894972] hda: Maxtor 90840D5, ATA DISK drive
[   30.565926] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   30.575438] Probing IDE interface ide1...
[   31.436061] hdc: LG CD-ROM CRD-8521B, ATAPI CD/DVD-ROM drive
[   32.218582] hdd: SAMSUNG CDRW/DVD SM-348B, ATAPI CD/DVD-ROM drive
[   32.274783] ide1 at 0x170-0x177,0x376 on irq 15
[   32.282898] SCSI subsystem initialized
[   32.288875] libata version 2.21 loaded.
[   32.300089] hda: max request size: 128KiB
[   32.313593] hda: 16514064 sectors (8455 MB) w/256KiB Cache, CHS=16383/16/63, UDMA(33)
[   32.313602] hda: cache flushes not supported
[   32.313669]  hda: hda1 hda2 < hda5 >
[   32.358099] hdc: ATAPI 52X CD-ROM drive, 128kB Cache, DMA
[   32.358109] Uniform CD-ROM driver Revision: 3.20
[   32.363501] hdd: ATAPI 48X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   32.819845] Attempting manual resume
[   32.819850] swsusp: Resume From Partition 3:5
[   32.819852] PM: Checking swsusp image.
[   32.820272] PM: Resume from disk failed.
[   32.867477] kjournald starting.  Commit interval 5 seconds
[   32.867493] EXT3-fs: mounted filesystem with ordered data mode.
[   47.659933] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   47.711703] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   47.743492] Linux agpgart interface v0.102 (c) Dave Jones
[   48.037053] agpgart: Detected VIA KT400/KT400A/KT600 chipset
[   48.044941] agpgart: AGP aperture is 128M @ 0xe0000000
[   48.088371] gameport: EMU10K1 is pci0000:00:07.1/gameport0, io 0xec00, speed 1217kHz
[   48.621725] irda_init()
[   48.621754] NET: Registered protocol family 23
[   48.716577] nvidia: module license 'NVIDIA' taints kernel.
[   49.017081] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 18
[   49.017610] NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.19  Wed Sep 12 14:12:24 PDT 2007
[   49.459857] input: ImExPS/2 Logitech Wheel Mouse as /class/input/input2
[   49.463515] parport_pc 00:04: reported by Plug and Play ACPI
[   49.463621] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   49.465369] input: PC Speaker as /class/input/input3
[   49.706450] ACPI: PCI Interrupt 0000:00:07.0[A] -> GSI 18 (level, low) -> IRQ 19
[   50.847024] lp0: using parport0 (interrupt-driven).
[   50.906220] Adding 393552k swap on /dev/hda5.  Priority:-1 extents:1 across:393552k
[   51.456416] EXT3 FS on hda1, internal journal
[   52.757411] No dock devices found.
[   52.912791] input: Power Button (FF) as /class/input/input4
[   52.917641] ACPI: Power Button (FF) [PWRF]
[   52.956743] input: Power Button (CM) as /class/input/input5
[   52.961518] ACPI: Power Button (CM) [PWRB]
[   53.001107] input: Sleep Button (CM) as /class/input/input6
[   53.005890] ACPI: Sleep Button (CM) [SLPB]
[   54.935065] Failure registering capabilities with primary security module.
[   55.139424] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[   55.265111] ppdev: user-space parallel port driver
[   55.593388] audit(1208606413.853:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4568 profile="/usr/sbin/cupsd"
[   55.659701] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   55.659707] apm: overridden by ACPI.
[   59.572988] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[   59.573008] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   59.573079] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   61.156796] NET: Registered protocol family 17
[   63.053960] NET: Registered protocol family 10
[   63.054139] lo: Disabled Privacy Extensions
[   73.449349] eth0: no IPv6 routers present

```

People can select a portion that they are most familiar with and hopefully others with select other portions and all together we can reduce these outputs and speed my machine back up!

Teach me :)

---

### Post by an0nu4nc3 on 2008-04-20
Ummm... is there something wrong with my post? Wrong place? Not specific enough? Hello?

---

### Post by pointone on 2008-04-20
There's nothing wrong in your dmesg, first of all. Secondly, I don't really know what your problem is... Modules aren't loading? There's better ways to fiddle with modules:

```
man modprobe
man lsmod
```

---

### Post by Whiffle on 2008-04-20
Yeah  I don't see anything wrong with your dmesg... could you be more specific?

---

### Post by an0nu4nc3 on 2008-04-21
> pointone ```
man modprobe
man lsmod
```

Those are some useful commands for future use, thank you!

I'll address a question to each of you to keep your interest but you can answer either:

I'd like to remove the 'eth0: no IPv6 routers present' issue as i've read that the probing for DHCP addresses can slow down the start-up process by up to 30 seconds. There does not however seem to be a comprehensive and easy to understand method for disabling this.

---

### Post by an0nu4nc3 on 2008-04-21
[QUOTE=Whiffle]Yeah  I don't see anything wrong with your dmesg... could you be more specific?[/QUOTE]

I'm addressing a question to each of you to keep your interest but you can answer either:

I tried adding the 'linux-headers-2.6.22-14' modules to my linux kernel... or it may have been the ov51x-jpeg module. I did several things that day and did not notice any problems until a couple of days later. The load on my system seems to have increased unnacceptably, especially when running multiple web-applications at the same time - which i could do before without trouble but which now cause my system to pause every few seconds for a second or more. This is unacceptable and so i believe i have done something wrong.

I do not know what it is or how to find out what the problem is.

---

### Post by koenn on 2008-04-21
disable IPv6:
[http://www.ducea.com/2006/06/01/disable-ipv6-module-on-default-kernels/](http://www.ducea.com/2006/06/01/disable-ipv6-module-on-default-kernels/)

still, that's probably not the cause of your problem, because it's in the kernel and enabled by default, so you've had it all along. 

uninstall all the unnecessary stuff you installed. 
```
dpkg -l
``` will help you choose. 
use```
apt-get --purge remove <package> 
``` to get rid of config files etc. You may have  all sorts of programs running in the background or at startup because of your fiddling.

---

### Post by an0nu4nc3 on 2008-04-22
That's a massive list of everything on my computer... not entirely sure what to remove.

The IPv6 thing looks like it will work although i haven't restarted yet... as you said, it's been there all the while.

Thanks for your help though! I'll wait for HH and be more carefuly next time with what i'm trying to get working and what i install and uninstall.

---

