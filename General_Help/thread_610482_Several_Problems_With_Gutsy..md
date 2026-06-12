---
title: "Several Problems With Gutsy."
date: 2007-11-12
forum: General Help
---

### Post by chrispche on 2007-11-12
chrispche@chrispche-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. P4M266 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:07.0 Ethernet controller: Intel Corporation 82557/8/9 Ethernet Pro 100 (rev 04)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]
chrispche@chrispche-desktop:~$ 

Sound keeps flapping. Never did in Dapper on the same machine.

There's no start up screen. The Monitor switches off.

Doesn't shut down properly some error messages. Something about the network adapters.

This does not inspire me with confidence with the next LTS.

Any ideas?

---

### Post by disturbed1 on 2007-11-12
Attach your dmesg output, this will help others with some trouble shooting. Also a lsmod could be helpful as well. Preferably after a fresh restart as it can get rather full.

```
dmesg > dmesg.log
lsmod > lsmod.log
```

---

### Post by chrispche on 2007-11-13
Ok this is the dmeg.log file:

[   43.343892] Memory: 995208k/1015744k available (2015k kernel code, 19944k reserved, 916k data, 364k init, 98240k highmem)
[   43.343907] virtual kernel memory layout:
[   43.343908]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   43.343909]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   43.343911]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   43.343912]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   43.343913]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   43.343914]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[   43.343915]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[   43.343918] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   43.343990] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   43.423989] Calibrating delay using timer specific routine.. 4937.75 BogoMIPS (lpj=9875512)
[   43.424045] Security Framework v1.0.0 initialized
[   43.424063] SELinux:  Disabled at boot.
[   43.424081] Mount-cache hash table entries: 512
[   43.424344] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[   43.424361] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   43.424365] CPU: L2 cache: 512K
[   43.424368] CPU: Hyper-Threading is disabled
[   43.424371] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b080 00004400 00000000 00000000
[   43.424390] Compat vDSO mapped to ffffe000.
[   43.424413] Checking 'hlt' instruction... OK.
[   43.440213] SMP alternatives: switching to UP code
[   43.440658] Freeing SMP alternatives: 11k freed
[   43.441047] Early unpacking initramfs... done
[   43.785251] CPU0: Intel(R) Pentium(R) 4 CPU 2.40GHz stepping 07
[   43.785300] Total of 1 processors activated (4937.75 BogoMIPS).
[   43.785570] ExtINT not setup in hardware but reported by MP table
[   43.786036] ENABLING IO-APIC IRQs
[   43.786355] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=0 pin2=0
[   44.039751] Brought up 1 CPUs
[   44.039965] Booting paravirtualized kernel on bare hardware
[   44.040064] Time:  6:22:56  Date: 10/12/107
[   44.040113] NET: Registered protocol family 16
[   44.040257] EISA bus registered
[   44.046881] PCI: PCI BIOS revision 2.10 entry at 0xfb720, last bus=1
[   44.046884] PCI: Using configuration type 1
[   44.046886] Setting up standard PCI resources
[   44.047773] ACPI: Interpreter disabled.
[   44.047780] Linux Plug and Play Support v0.97 (c) Adam Belay
[   44.047792] pnp: PnP ACPI: disabled
[   44.047795] PnPBIOS: Scanning system for PnP BIOS support...
[   44.048347] PnPBIOS: Found PnP BIOS installation structure at 0xc00fc1e0
[   44.048356] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xc210, dseg 0xf0000
[   44.049709] PnPBIOS: 15 nodes reported by PnP BIOS; 15 recorded by driver
[   44.049775] PCI: Probing PCI hardware
[   44.049780] PCI: Probing PCI hardware (bus 00)
[   44.049963] PCI: Firmware left 0000:00:07.0 e100 interrupts enabled, disabling
[   44.050306] PCI quirk: region 0400-047f claimed by vt8235 PM
[   44.050310] PCI quirk: region 0500-050f claimed by vt8235 SMB
[   44.051831] PCI: Using IRQ router VIA [1106/3177] at 0000:00:11.0
[   44.051847] PCI->APIC IRQ transform: 0000:00:07.0[A] -> IRQ 18
[   44.051851] PCI->APIC IRQ transform: 0000:00:10.0[A] -> IRQ 21
[   44.051854] PCI->APIC IRQ transform: 0000:00:10.1[B] -> IRQ 21
[   44.051858] PCI->APIC IRQ transform: 0000:00:10.2[C] -> IRQ 21
[   44.051861] PCI->APIC IRQ transform: 0000:00:10.3[D] -> IRQ 21
[   44.051867] PCI->APIC IRQ transform: 0000:00:11.1[A] -> IRQ 18
[   44.051870] PCI->APIC IRQ transform: 0000:00:11.5[C] -> IRQ 18
[   44.051874] PCI->APIC IRQ transform: 0000:00:12.0[A] -> IRQ 23
[   44.051877] PCI->APIC IRQ transform: 0000:01:00.0[A] -> IRQ 16
[   44.085917] NET: Registered protocol family 8
[   44.085919] NET: Registered protocol family 20
[   44.086019] pnp: 00:07: iomem range 0x0-0x9ffff could not be reserved
[   44.086023] pnp: 00:07: iomem range 0xfffe0000-0xffffffff could not be reserved
[   44.086027] pnp: 00:07: iomem range 0xfec00000-0xfec0ffff could not be reserved
[   44.086031] pnp: 00:07: iomem range 0xfee00000-0xfee0ffff could not be reserved
[   44.086038] pnp: 00:08: iomem range 0xf0000-0xf3fff could not be reserved
[   44.086041] pnp: 00:08: iomem range 0xf4000-0xf7fff could not be reserved
[   44.086044] pnp: 00:08: iomem range 0xf8000-0xfffff could not be reserved
[   44.086047] pnp: 00:08: iomem range 0xca000-0xcbfff has been reserved
[   44.086055] pnp: 00:0b: ioport range 0x3f0-0x3f1 has been reserved
[   44.086440] PCI: Bridge: 0000:00:01.0
[   44.086442]   IO window: disabled.
[   44.086449]   MEM window: ec000000-edffffff
[   44.086454]   PREFETCH window: e0000000-e7ffffff
[   44.086475] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   44.086490] NET: Registered protocol family 2
[   44.087678] Time: tsc clocksource has been installed.
[   44.115740] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   44.115987] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   44.118993] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   44.120059] TCP: Hash tables configured (established 131072 bind 65536)
[   44.120065] TCP reno registered
[   44.131937] checking if image is initramfs... it is
[   44.805913] Freeing initrd memory: 7332k freed
[   44.806470] audit: initializing netlink socket (disabled)
[   44.806497] audit(1194848576.140:1): initialized
[   44.806613] highmem bounce pool size: 64 pages
[   44.809023] VFS: Disk quotas dquot_6.5.1
[   44.809089] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   44.809284] io scheduler noop registered
[   44.809287] io scheduler anticipatory registered
[   44.809289] io scheduler deadline registered
[   44.809308] io scheduler cfq registered (default)
[   44.809328] PCI: VIA PCI bridge detected. Disabling DAC.
[   44.809393] Boot video device is 0000:01:00.0
[   44.809571] isapnp: Scanning for PnP cards...
[   45.163440] isapnp: No Plug & Play device found
[   45.204211] Real Time Clock Driver v1.12ac
[   45.204305] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   45.206577] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   45.206902] input: Macintosh mouse button emulation as /class/input/input0
[   45.207023] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[   45.207509] serio: i8042 KBD port at 0x60,0x64 irq 1
[   45.207517] serio: i8042 AUX port at 0x60,0x64 irq 12
[   45.207726] mice: PS/2 mouse device common for all mice
[   45.207871] EISA: Probing bus 0 at eisa.0
[   45.207909] EISA: Detected 0 cards.
[   45.208178] TCP cubic registered
[   45.208202] NET: Registered protocol family 1
[   45.208232] Using IPI No-Shortcut mode
[   45.208347]   Magic number: 15:388:367
[   45.209252] Freeing unused kernel memory: 364k freed
[   45.247257] input: AT Translated Set 2 keyboard as /class/input/input1
[   46.481436] AppArmor: AppArmor initialized<5>audit(1194848577.640:2):  type=1505 info="AppArmor initialized" pid=1123
[   46.492489] fuse init (API version 7.8)
[   46.500182] Failure registering capabilities with primary security module.
[   46.531218] thermal: Unknown symbol acpi_processor_set_thermal_limit
[   47.281255] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k4-NAPI
[   47.281259] e100: Copyright(c) 1999-2006 Intel Corporation
[   47.304384] e100: eth0: e100_probe: addr 0xef100000, irq 18, MAC addr 00:A0:C9:B7:01:26
[   47.320012] usbcore: registered new interface driver usbfs
[   47.320049] usbcore: registered new interface driver hub
[   47.320077] usbcore: registered new device driver usb
[   47.321175] USB Universal Host Controller Interface driver v3.0
[   47.321298] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   47.321535] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   47.321572] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000d400
[   47.321730] usb usb1: configuration #1 chosen from 1 choice
[   47.321765] hub 1-0:1.0: USB hub found
[   47.321776] hub 1-0:1.0: 2 ports detected
[   47.378528] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   47.378535] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   47.399720] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[   47.422266] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   47.422304] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   47.422332] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000d800
[   47.422458] usb usb2: configuration #1 chosen from 1 choice
[   47.422488] hub 2-0:1.0: USB hub found
[   47.422500] hub 2-0:1.0: 2 ports detected
[   47.526142] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   47.526175] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[   47.526206] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000dc00
[   47.526337] usb usb3: configuration #1 chosen from 1 choice
[   47.526371] hub 3-0:1.0: USB hub found
[   47.526382] hub 3-0:1.0: 2 ports detected
[   47.584569] Floppy drive(s): fd0 is 1.44M
[   47.631521] ehci_hcd 0000:00:10.3: EHCI Host Controller
[   47.631581] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[   47.631648] ehci_hcd 0000:00:10.3: irq 21, io mem 0xef101000
[   47.631656] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   47.631783] usb usb4: configuration #1 chosen from 1 choice
[   47.631819] hub 4-0:1.0: USB hub found
[   47.631834] hub 4-0:1.0: 6 ports detected
[   47.761154] eth1: VIA Rhine II at 0x1ec00, 00:0c:76:5d:c3:d0, IRQ 23.
[   47.761854] eth1: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000.
[   47.762820] VP_IDE: IDE controller at PCI slot 0000:00:11.1
[   47.762854] VP_IDE: chipset revision 6
[   47.762857] VP_IDE: not 100% native mode: will probe irqs later
[   47.762872] VP_IDE: VIA vt8235 (rev 00) IDE UDMA133 controller on pci0000:00:11.1
[   47.762884]     ide0: BM-DMA at 0xe000-0xe007, BIOS settings: hda:pio, hdb:DMA
[   47.762901]     ide1: BM-DMA at 0xe008-0xe00f, BIOS settings: hdc:DMA, hdd:DMA
[   47.762911] Probing IDE interface ide0...
[   48.401605] hdb: Maxtor 6E040L0, ATA DISK drive
[   48.457734] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   48.458076] Probing IDE interface ide1...
[   48.873352] hdc: ST3120022A, ATA DISK drive
[   49.321124] hdd: SAMSUNG CD-ROM SC-152A, ATAPI CD/DVD-ROM drive
[   49.378175] ide1 at 0x170-0x177,0x376 on irq 15
[   49.387338] SCSI subsystem initialized
[   49.396142] libata version 2.21 loaded.
[   49.410012] hdb: max request size: 128KiB
[   49.426187] hdb: 80293248 sectors (41110 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(133)
[   49.427757] hdb: cache flushes supported
[   49.427835]  hdb: hdb1 hdb2 < hdb5 >
[   49.459342] hdc: max request size: 512KiB
[   49.459765] hdc: 234441648 sectors (120034 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(100)
[   49.459912] hdc: cache flushes supported
[   49.459954]  hdc:hdc: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[   50.145816] hdc: dma_intr: error=0x84 { DriveStatusError BadCRC }
[   50.145822] ide: failed opcode was: unknown
[   50.596387] floppy0: no floppy controllers found
[   50.863652] hdc: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[   50.863660] hdc: dma_intr: error=0x84 { DriveStatusError BadCRC }
[   50.863665] ide: failed opcode was: unknown
[   51.554771] hdc: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[   51.554779] hdc: dma_intr: error=0x84 { DriveStatusError BadCRC }
[   51.554783] ide: failed opcode was: unknown
[   52.172344] hdc: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[   52.172351] hdc: dma_intr: error=0x84 { DriveStatusError BadCRC }
[   52.172356] ide: failed opcode was: unknown
[   52.172598] hdd: DMA disabled
[   52.507395] ide1: reset: success
[   52.526710]  hdc1
[   52.547251] hdd: ATAPI 52X CD-ROM drive, 128kB Cache
[   52.547263] Uniform CD-ROM driver Revision: 3.20
[   52.828852] Attempting manual resume
[   52.828857] swsusp: Resume From Partition 3:69
[   52.828859] PM: Checking swsusp image.
[   52.830611] PM: Resume from disk failed.
[   52.885825] kjournald starting.  Commit interval 5 seconds
[   52.885846] EXT3-fs: mounted filesystem with ordered data mode.
[   60.513096] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   60.515663] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   61.114405] Linux agpgart interface v0.102 (c) Dave Jones
[   61.153410] input: PC Speaker as /class/input/input2
[   61.585140] Floppy drive(s): fd0 is 1.44M
[   61.601930] agpgart: Detected VIA P4M266x/P4N266 chipset
[   61.606081] agpgart: AGP aperture is 64M @ 0xe8000000
[   61.719062] irda_init()
[   61.719091] NET: Registered protocol family 23
[   61.838702] input: ImPS/2 Logitech Wheel Mouse as /class/input/input3
[   61.842516] parport_pc 00:0f: reported by Plug and Play BIOS
[   61.842990] pnp: Device 00:0f disabled.
[   62.094598] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   64.597265] floppy0: no floppy controllers found
[   65.073210] lp: driver loaded but no devices found
[   65.138854] Adding 1694816k swap on /dev/hdb5.  Priority:-1 extents:1 across:1694816k
[   65.362822] EXT3 FS on hdb1, internal journal
[   67.055817] acpi_cpufreq: Unknown symbol acpi_processor_notify_smm
[   67.055875] acpi_cpufreq: Unknown symbol acpi_processor_unregister_performance
[   67.056050] acpi_cpufreq: Unknown symbol acpi_processor_preregister_performance
[   67.056123] acpi_cpufreq: Unknown symbol acpi_processor_register_performance
[   68.299583] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[   68.303715] ppdev: user-space parallel port driver
[   68.374060] eth1: link down
[   68.417811] audit(1194848600.146:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4353 profile="/usr/sbin/cupsd"
[   68.547983] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   68.936891] Failure registering capabilities with primary security module.
[   69.373074] Bluetooth: Core ver 2.11
[   69.373233] NET: Registered protocol family 31
[   69.373236] Bluetooth: HCI device and connection manager initialized
[   69.373241] Bluetooth: HCI socket layer initialized
[   69.392098] Bluetooth: L2CAP ver 2.8
[   69.392104] Bluetooth: L2CAP socket layer initialized
[   70.206195] Bluetooth: RFCOMM socket layer initialized
[   70.206326] Bluetooth: RFCOMM TTY layer initialized
[   70.206330] Bluetooth: RFCOMM ver 1.8
[   72.928166] [drm] Initialized drm 1.1.0 20060810
[   72.962098] [drm] Initialized savage 2.4.1 20050313 on minor 0
[   72.962737] mtrr: base(0xe2000000) is not aligned on a size(0x5000000) boundary
[   72.963402] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   72.963668] agpgart: Putting AGP V2 device at 0000:00:00.0 into 0x mode
[   72.963920] agpgart: Putting AGP V2 device at 0000:01:00.0 into 0x mode
[   73.602740] NET: Registered protocol family 17
[   75.391261] NET: Registered protocol family 10
[   75.391470] lo: Disabled Privacy Extensions
[   75.391754] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   86.098320] eth0: no IPv6 routers present
[ 3470.409993] audit(1194852004.361:4):  type=1503 operation="inode_permission" requested_mask="rw" denied_mask="rw" name="/dev/tty" pid=18623 profile="/usr/sbin/cupsd"
[ 3470.448172] audit(1194852004.361:5):  type=1503 operation="inode_permission" requested_mask="rw" denied_mask="rw" name="/dev/tty" pid=18626 profile="/usr/sbin/cupsd"
[ 4211.090965] hdc: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[ 4211.090977] hdc: dma_intr: error=0x84 { DriveStatusError BadCRC }
[ 4211.090982] ide: failed opcode was: unknown
[ 4211.245026] hdc: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[ 4211.245037] hdc: dma_intr: error=0x84 { DriveStatusError BadCRC }
[ 4211.245042] ide: failed opcode was: unknown
[ 4211.555145] hdc: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[ 4211.555157] hdc: dma_intr: error=0x84 { DriveStatusError BadCRC }
[ 4211.555162] ide: failed opcode was: unknown
[ 4211.858148] hdc: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[ 4211.858159] hdc: dma_intr: error=0x84 { DriveStatusError BadCRC }
[ 4211.858164] ide: failed opcode was: unknown
[ 4212.192526] ide1: reset: success
[ 4212.544772] hdc: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[ 4212.544783] hdc: dma_intr: error=0x84 { DriveStatusError BadCRC }
[ 4212.544788] ide: failed opcode was: unknown
[ 4212.848689] hdc: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[ 4212.848700] hdc: dma_intr: error=0x84 { DriveStatusError BadCRC }
[ 4212.848704] ide: failed opcode was: unknown
[ 4213.153101] hdc: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[ 4213.153112] hdc: dma_intr: error=0x84 { DriveStatusError BadCRC }
[ 4213.153117] ide: failed opcode was: unknown
[ 4213.306166] hdc: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[ 4213.306176] hdc: dma_intr: error=0x84 { DriveStatusError BadCRC }
[ 4213.306181] ide: failed opcode was: unknown
[ 4213.639802] ide1: reset: success
[12638.010296] audit(1194861177.383:6):  type=1503 operation="inode_permission" requested_mask="rw" denied_mask="rw" name="/dev/tty" pid=13388 profile="/usr/sbin/cupsd"
[12638.054984] audit(1194861177.383:7):  type=1503 operation="inode_permission" requested_mask="rw" denied_mask="rw" name="/dev/tty" pid=13391 profile="/usr/sbin/cupsd"

And this is the lsmod.log file:

Module                  Size  Used by
ipv6                  273892  8 
af_packet              24840  2 
savage                 34176  2 
drm                    83348  3 savage
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
apm                    22616  2 
ppdev                  10244  0 
speedstep_lib           6404  0 
cpufreq_userspace       5280  0 
cpufreq_conservative     8072  0 
cpufreq_stats           7232  0 
cpufreq_ondemand        9612  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
cpufreq_powersave       2688  0 
lp                     12580  0 
snd_via82xx            29336  3 
gameport               16776  1 snd_via82xx
snd_ac97_codec        100644  1 snd_via82xx
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  5 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         11400  2 snd_via82xx,snd_pcm
snd_mpu401_uart         9600  1 snd_via82xx
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
i2c_viapro             10004  0 
via_ircc               27668  0 
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
irda                  202300  1 via_ircc
snd                    54660  15 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             37412  0 
parport                37448  3 ppdev,lp,parport_pc
via_agp                11264  1 
soundcore               8800  1 snd
i2c_prosavage           5248  0 
i2c_algo_bit            7428  1 i2c_prosavage
i2c_core               26112  3 i2c_viapro,i2c_prosavage,i2c_algo_bit
serio_raw               8068  0 
pcspkr                  4224  0 
psmouse                39952  0 
agpgart                35016  2 drm,via_agp
crc_ccitt               3072  1 irda
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
evdev                  11136  1 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
ide_cd                 32672  0 
cdrom                  37536  1 ide_cd
ide_disk               18560  5 
ata_generic             8452  0 
libata                125168  1 ata_generic
scsi_mod              147084  1 libata
via_rhine              25992  0 
via82cxxx              10372  0 [permanent]
ide_core              116804  3 ide_cd,ide_disk,via82cxxx
ehci_hcd               36492  0 
uhci_hcd               26640  0 
usbcore               138632  3 ehci_hcd,uhci_hcd
e100                   37644  0 
mii                     6528  2 via_rhine,e100
fuse                   47124  3 
apparmor               40728  0 
commoncap               8320  1 apparmor

Meaningless to me, anyone out there have a clue?

---

### Post by disturbed1 on 2007-11-13
> **disturbed1 said:**
> **[SIZE=16]_*Attach*_[/SIZE]** your dmesg output, this will help others with some trouble shooting. Also a lsmod could be helpful as well. Preferably after a fresh restart as it can get rather full.

```
dmesg > dmesg.log
lsmod > lsmod.log
```

Attach ;) notice I even gave the commands to output the files to your home dirrectory :)

One issue you have, your hard drive has died, is dying, bad IDE cable, bad port on mother board, bad kernel driver, wrong settings in the bios, wrong/failing/bad something. Something just isn't right with your hard drive, as seen from these messages

> hdc: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[   50.863660] hdc: dma_intr: error=0x84 { DriveStatusError BadCRC }HDC is your ST3120022A, ATA DISK drive. Seagate drive, didn't feel like googling the model number, but I'm sure you know which drive that is ;). Seagate has free tools that can be used to diagnose problems with their hard drive. I'd do that to make sure all is good with the actual hard drive before looking else where, since it is the easiest of all to do.

Another issue you have is an IRQ conflict. Means two or more devices (USB, Video, IDE, floppy, ..... what ever) are attempting to share the same memory space. Which causes tons of issues. If you fiddled with the bios at all, put every thing back to where it should be. If you've added internal cards (NIC, Video, Sound, wireless......) attempt to take them all out except the Video card. Then add them back one by one until these errors (or ones similar)

> 
pnp: 00:07: iomem range 0x0-0x9ffff could not be reserved
[   44.086023] pnp: 00:07: iomem range 0xfffe0000-0xffffffff could not be reserved
[   44.086027] pnp: 00:07: iomem range 0xfec00000-0xfec0ffff could not be reserved
[   44.086031] pnp: 00:07: iomem range 0xfee00000-0xfee0ffff could not be reserved
[   44.086038] pnp: 00:08: iomem range 0xf0000-0xf3fff could not be reserved
[   44.086041] pnp: 00:08: iomem range 0xf4000-0xf7fff could not be reserved
[   44.086044] pnp: 00:08: iomem range 0xf8000-0xfffff could not be reserved
[   44.086047] pnp: 00:08: iomem range 0xca000-0xcbfff has been reserved
[   44.086055] pnp: 00:0b: ioport range 0x3f0-0x3f1 has been reservedare gone.

It goes without saying, of course, be sure the PC is powered off and unplugged, while following other common sense procedures of working with sensitive electronic equipment.

You may also want to check the support page for your Motherboard or PC Vendor to see if there is a BIOS upgrade available. Sometimes a faulty motherboard BIOS can cause errors like the above.


These are just suggestions, I don't proclaim that any of it is the absolute only cause. Only the steps I'd personally take if I where receiving the same error messages as you.

---

### Post by chrispche on 2007-11-13
Thank you. I will now reset the Bios to defaults. This is a work machine so who knows whos been fiddling.

---

### Post by disturbed1 on 2007-11-13
If you know anything about the BIOS settings, just check through them to see if anything looks funky. Perhaps pictures from a cell phone/camera for your reference in case something goes wrong, or even just jotting them down with pen and paper, can save a bit of frustration.

There's so many settings in the BIOS, one wrong setting is all it takes. I've learned this the hard way :) I was never smart enough to only change one thing at a time then test, instead I was like a kid in the candy store, *ooohhhhhh look at all the settings* with stars in my eyes, that quickly turned to tears :)

---

### Post by chrispche on 2007-11-13
No joy, well it's a work computer so none of my business. If I owned I would go out of my way a little more to fix it.

---

