---
title: "RTAPI error on running EMC2 in 8.04 HH on desktop"
date: 2008-06-19
forum: General Help
---

### Post by oakes3 on 2008-06-19
I'm a complete newb trying to install EMC2 into Ubuntu 8.04 Hardy Heron to control a homebuilt gantry router.

Ubuntu runs well, and installed easily on a separate hard drive on a 2.0 Ghz Sempron 3400+ Emachines desktop with 3Gb of RAM.

I tried first to install EMC2 separately, then also with the EMC2-Ubuntu Live CD ISO image burned onto a CD.

Same error both times: it seem I get a RTAPI error / segmentation error which I have no idea how to solve.

All input welcome - Thanks

error text follows:



Print file information:
RUN_IN_PLACE=no
EMC2_DIR=
EMC2_BIN_DIR=/usr/bin
EMC2_TCL_DIR=/usr/share/emc/tcl
EMC2_SCRIPT_DIR=
EMC2_RTLIB_DIR=/usr/realtime-2.6.24-16-rtai/modules/emc2
EMC2_CONFIG_DIR=
EMC2_LANG_DIR=/usr/share/emc/tcl/msgs
INIVAR=/usr/bin/inivar
HALCMD=/usr/bin/halcmd
EMC2_EMCSH=/usr/bin/emcsh
EMC2_IOSH=/usr/bin/iosh
EMC2 - 2.2.5
Machine configuration directory is '/home/david/emc2/configs/sim'
Machine configuration file is 'tkemc.ini'
INIFILE=/home/david/emc2/configs/sim/tkemc.ini
PARAMETER_FILE=sim.var
EMCMOT=motmod
EMCIO=io
TASK=milltask
HALUI=
DISPLAY=tkemc
NML_FILE=emc.nml
Starting EMC2...
Starting EMC2 server program: emcsvr
Loading Real Time OS, RTAPI, and HAL_LIB modules
Realtime system did not load
Shutting down and cleaning up EMC2...
Killing task emcsvr, PID=5226
Removing HAL_LIB, RTAPI, and Real Time OS modules
Removing NML shared memory segments
Cleanup done

Kernel message information:
[ 0.000000] Linux version 2.6.24-16-rtai (root@dana-laptop) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 Sun Apr 13 17:50:16 EEST 2008 (Ubuntu 2.6.24-12.22-generic)
[ 0.000000] BIOS-provided physical RAM map:
[ 0.000000] BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[ 0.000000] BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[ 0.000000] BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[ 0.000000] BIOS-e820: 0000000000100000 - 0000000077ee0000 (usable)
[ 0.000000] BIOS-e820: 0000000077ee0000 - 0000000077ee3000 (ACPI NVS)
[ 0.000000] BIOS-e820: 0000000077ee3000 - 0000000077ef0000 (ACPI data)
[ 0.000000] BIOS-e820: 0000000077ef0000 - 0000000077f00000 (reserved)
[ 0.000000] BIOS-e820: 0000000078000000 - 0000000080000000 (reserved)
[ 0.000000] BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[ 0.000000] BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[ 0.000000] BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
[ 0.000000] BIOS-e820: 00000000fefffc00 - 00000000ff000000 (reserved)
[ 0.000000] BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[ 0.000000] 1022MB HIGHMEM available.
[ 0.000000] 896MB LOWMEM available.
[ 0.000000] Entering add_active_range(0, 0, 491232) 0 entries of 256 used
[ 0.000000] Zone PFN ranges:
[ 0.000000] DMA 0 -> 4096
[ 0.000000] Normal 4096 -> 229376
[ 0.000000] HighMem 229376 -> 491232
[ 0.000000] Movable zone start PFN for each node
[ 0.000000] early_node_map[1] active PFN ranges
[ 0.000000] 0: 0 -> 491232
[ 0.000000] On node 0 totalpages: 491232
[ 0.000000] DMA zone: 32 pages used for memmap
[ 0.000000] DMA zone: 0 pages reserved
[ 0.000000] DMA zone: 4064 pages, LIFO batch:0
[ 0.000000] Normal zone: 1760 pages used for memmap
[ 0.000000] Normal zone: 223520 pages, LIFO batch:31
[ 0.000000] HighMem zone: 2045 pages used for memmap
[ 0.000000] HighMem zone: 259811 pages, LIFO batch:31
[ 0.000000] Movable zone: 0 pages used for memmap
[ 0.000000] DMI 2.3 present.
[ 0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
[ 0.000000] Built 1 zonelists in Zone order, mobility grouping on. Total pages: 487395
[ 0.000000] Kernel command line: root=UUID=ba0c2ae3-e944-457c-894d-be986c9198d7 ro quiet splash
[ 0.000000] Enabling fast FPU save and restore... done.
[ 0.000000] Enabling unmasked SIMD FPU exception support... done.
[ 0.000000] Initializing CPU#0
[ 0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[ 0.000000] Detected 2009.279 MHz processor.
[ 24.709411] I-pipe 2.0-04: pipeline enabled.
[ 24.709419] spurious 8259A interrupt: IRQ7.
[ 24.712453] Console: colour VGA+ 80x25
[ 24.712456] console [tty0] enabled
[ 24.712836] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[ 24.713417] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[ 24.769379] Memory: 1937804k/1964928k available (1440k kernel code, 25736k reserved, 573k data, 228k init, 1047424k highmem)
[ 24.769387] virtual kernel memory layout:
[ 24.769388] fixmap : 0xfffed000 - 0xfffff000 ( 72 kB)
[ 24.769389] pkmap : 0xff800000 - 0xffc00000 (4096 kB)
[ 24.769391] vmalloc : 0xf8800000 - 0xff7fe000 ( 111 MB)
[ 24.769392] lowmem : 0xc0000000 - 0xf8000000 ( 896 MB)
[ 24.769393] .init : 0xc02fa000 - 0xc0333000 ( 228 kB)
[ 24.769394] .data : 0xc026836d - 0xc02f77ec ( 573 kB)
[ 24.769396] .text : 0xc0100000 - 0xc026836d (1440 kB)
[ 24.769399] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[ 24.769435] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[ 24.849358] Calibrating delay using timer specific routine.. 4020.32 BogoMIPS (lpj=8040644)
[ 24.849381] Security Framework initialized
[ 24.849386] SELinux: Disabled at boot.
[ 24.849396] AppArmor: AppArmor initialized
[ 24.849400] Failure registering capabilities with primary security module.
[ 24.849406] Mount-cache hash table entries: 512
[ 24.849495] CPU: After generic identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001 00000000
[ 24.849502] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[ 24.849504] CPU: L2 Cache: 256K (64 bytes/line)
[ 24.849506] CPU: After all inits, caps: 078bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000001 00000000
[ 24.849515] Compat vDSO mapped to ffffe000.
[ 24.849523] CPU: AMD Sempron(tm) Processor 3400+ stepping 02
[ 24.849527] Checking 'hlt' instruction... OK.
[ 24.865457] Freeing SMP alternatives: 0k freed
[ 24.865592] net_namespace: 64 bytes
[ 24.865943] NET: Registered protocol family 16
[ 24.866073] EISA bus registered
[ 24.872634] PCI: PCI BIOS revision 3.00 entry at 0xfa7d0, last bus=4
[ 24.872636] PCI: Using configuration type 1
[ 24.872638] Setting up standard PCI resources
[ 24.875464] Linux Plug and Play Support v0.97 (c) Adam Belay
[ 24.875622] PCI: Probing PCI hardware
[ 24.875628] PCI: Probing PCI hardware (bus 00)
[ 24.876629] PCI: Transparent bridge - 0000:00:10.0
[ 24.965294] AppArmor: AppArmor Filesystem Enabled
[ 24.965551] PCI: Bridge: 0000:00:02.0
[ 24.965553] IO window: a000-afff
[ 24.965556] MEM window: fd700000-fd7fffff
[ 24.965558] PREFETCH window: fde00000-fdefffff
[ 24.965561] PCI: Bridge: 0000:00:03.0
[ 24.965563] IO window: 9000-9fff
[ 24.965565] MEM window: fdd00000-fddfffff
[ 24.965568] PREFETCH window: fdc00000-fdcfffff
[ 24.965570] PCI: Bridge: 0000:00:04.0
[ 24.965572] IO window: b000-bfff
[ 24.965575] MEM window: fd900000-fd9fffff
[ 24.965577] PREFETCH window: fd800000-fd8fffff
[ 24.965580] PCI: Bridge: 0000:00:10.0
[ 24.965582] IO window: c000-cfff
[ 24.965585] MEM window: fdb00000-fdbfffff
[ 24.965588] PREFETCH window: fda00000-fdafffff
[ 24.965598] PCI: Setting latency timer of device 0000:00:02.0 to 64
[ 24.965604] PCI: Setting latency timer of device 0000:00:03.0 to 64
[ 24.965610] PCI: Setting latency timer of device 0000:00:04.0 to 64
[ 24.965618] PCI: Setting latency timer of device 0000:00:10.0 to 64
[ 24.965626] NET: Registered protocol family 2
[ 24.969215] Time: tsc clocksource has been installed.
[ 25.001223] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[ 25.001465] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[ 25.002242] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[ 25.002440] TCP: Hash tables configured (established 131072 bind 65536)
[ 25.002442] TCP reno registered
[ 25.013288] checking if image is initramfs... it is
[ 25.546081] Freeing initrd memory: 6867k freed
[ 25.546414] audit: initializing netlink socket (disabled)
[ 25.546424] audit(1213788845.780:1): initialized
[ 25.546546] highmem bounce pool size: 64 pages
[ 25.547774] VFS: Disk quotas dquot_6.5.1
[ 25.547794] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[ 25.547882] io scheduler noop registered
[ 25.547884] io scheduler anticipatory registered
[ 25.547886] io scheduler deadline registered
[ 25.547894] io scheduler cfq registered (default)
[ 25.547908] Boot video device is 0000:00:05.0
[ 33.558895] 0000:00:0b.1 EHCI: BIOS handoff failed (BIOS bug ?) 01010001
[ 33.558988] PCI: Setting latency timer of device 0000:00:02.0 to 64
[ 33.559009] assign_interrupt_mode Found MSI capability
[ 33.559012] Allocate Port Service[0000:00:02.0cie00]
[ 33.559059] PCI: Setting latency timer of device 0000:00:03.0 to 64
[ 33.559079] assign_interrupt_mode Found MSI capability
[ 33.559081] Allocate Port Service[0000:00:03.0cie00]
[ 33.559125] PCI: Setting latency timer of device 0000:00:04.0 to 64
[ 33.559145] assign_interrupt_mode Found MSI capability
[ 33.559147] Allocate Port Service[0000:00:04.0cie00]
[ 33.559258] isapnp: Scanning for PnP cards...
[ 33.911811] isapnp: No Plug & Play device found
[ 33.932994] Real Time Clock Driver v1.12ac
[ 33.932997] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[ 33.933112] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[ 33.933823] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[ 33.933886] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[ 33.933976] PNP: No PS/2 controller found. Probing ports directly.
[ 33.936435] serio: i8042 KBD port at 0x60,0x64 irq 1
[ 33.936439] serio: i8042 AUX port at 0x60,0x64 irq 12
[ 33.938630] mice: PS/2 mouse device common for all mice
[ 33.938714] EISA: Probing bus 0 at eisa.0
[ 33.938720] Cannot allocate resource for EISA slot 1
[ 33.938740] EISA: Detected 0 cards.
[ 33.938809] NET: Registered protocol family 1
[ 33.938817] Using IPI Shortcut mode
[ 33.938910] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[ 33.938912] EDD information not available.
[ 33.939053] Freeing unused kernel memory: 228k freed
[ 33.966421] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[ 35.161156] fuse init (API version 7.9)
[ 35.508265] usbcore: registered new interface driver usbfs
[ 35.508285] usbcore: registered new interface driver hub
[ 35.514465] usbcore: registered new device driver usb
[ 35.515131] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[ 35.515168] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[ 35.515171] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[ 35.515377] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
[ 35.515392] ohci_hcd 0000:00:0b.0: irq 10, io mem 0xfe02f000
[ 35.555600] SCSI subsystem initialized
[ 35.570593] usb usb1: configuration #1 chosen from 1 choice
[ 35.570614] hub 1-0:1.0: USB hub found
[ 35.570622] hub 1-0:1.0: 8 ports detected
[ 35.588496] libata version 3.00 loaded.
[ 35.672648] PCI: Setting latency timer of device 0000:00:0b.1 to 64
[ 35.672652] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[ 35.672674] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 2
[ 35.672702] ehci_hcd 0000:00:0b.1: debug port 1
[ 35.672706] PCI: cache line size of 64 is not supported by device 0000:00:0b.1
[ 35.672714] ehci_hcd 0000:00:0b.1: irq 11, io mem 0xfe02e000
[ 35.684362] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[ 35.684471] usb usb2: configuration #1 chosen from 1 choice
[ 35.684489] hub 2-0:1.0: USB hub found
[ 35.684495] hub 2-0:1.0: 8 ports detected
[ 35.788422] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[ 35.788440] PCI: Setting latency timer of device 0000:00:14.0 to 64
[ 36.307993] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x50ef @ 0, addr 00:40:ca:8f:b2:12
[ 36.307998] forcedeth 0000:00:14.0: highdma pwrctl timirq lnktim desc-v3
[ 36.310318] pata_amd 0000:00:0d.0: version 0.3.10
[ 36.310364] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[ 36.311226] scsi0 : pata_amd
[ 36.312143] scsi1 : pata_amd
[ 36.312180] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf400 irq 14
[ 36.312184] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf408 irq 15
[ 36.327582] usb 1-5: new full speed USB device using ohci_hcd and address 2
[ 36.484964] ata1.00: ATA-6: WDC WD1600BB-00GUC0, 08.02D08, max UDMA/100
[ 36.484969] ata1.00: 312581808 sectors, multi 16: LBA48
[ 36.485179] ata1.01: ATA-7: Maxtor 6Y160P0, YAR41BW0, max UDMA/133
[ 36.485182] ata1.01: 320173056 sectors, multi 16: LBA48
[ 36.495412] usb 1-5: configuration #1 chosen from 1 choice
[ 36.501542] ata1.00: configured for UDMA/100
[ 36.511450] usbcore: registered new interface driver libusual
[ 36.515879] Initializing USB Mass Storage driver...
[ 36.516334] ata1.01: configured for UDMA/133
[ 36.517960] scsi2 : SCSI emulation for USB Mass Storage devices
[ 36.518464] usbcore: registered new interface driver usb-storage
[ 36.518469] USB Mass Storage support registered.
[ 36.518550] usb-storage: device found at 2
[ 36.518552] usb-storage: waiting for device to settle before scanning
[ 36.883204] ata2.00: ATAPI: TSSTcorpCD/DVDW TS-H552D, GA01, max UDMA/33
[ 36.883334] ata2.01: ATA-6: WDC WD800JB-00JJC0, 05.01C05, max UDMA/100
[ 36.883337] ata2.01: 156301488 sectors, multi 16: LBA
[ 37.094890] ata2.00: configured for UDMA/33
[ 37.102984] ata2.01: configured for UDMA/100
[ 37.103069] scsi 0:0:0:0: Direct-Access ATA WDC WD1600BB-00G 08.0 PQ: 0 ANSI: 5
[ 37.103352] scsi 0:0:1:0: Direct-Access ATA Maxtor 6Y160P0 YAR4 PQ: 0 ANSI: 5
[ 37.104468] scsi 1:0:0:0: CD-ROM TSSTcorp CD/DVDW TS-H552D GA01 PQ: 0 ANSI: 5
[ 37.104667] scsi 1:0:1:0: Direct-Access ATA WDC WD800JB-00JJ 05.0 PQ: 0 ANSI: 5
[ 37.109279] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[ 37.109284] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[ 37.109899] sata_nv 0000:00:0e.0: version 3.5
[ 37.109950] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[ 37.110808] scsi3 : sata_nv
[ 37.111302] scsi4 : sata_nv
[ 37.111335] ata3: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xe000 irq 11
[ 37.111338] ata4: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xe008 irq 11
[ 37.115323] Driver 'sd' needs updating - please use bus_type methods
[ 37.115395] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[ 37.115406] sd 0:0:0:0: [sda] Write Protect is off
[ 37.115409] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 37.115421] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 37.115457] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[ 37.115463] sd 0:0:0:0: [sda] Write Protect is off
[ 37.115466] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 37.115477] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 37.115480] sda:<4>Driver 'sr' needs updating - please use bus_type methods
[ 37.134061] sda1 sda2
[ 37.134123] sd 0:0:0:0: [sda] Attached SCSI disk
[ 37.134174] sd 0:0:1:0: [sdb] 320173056 512-byte hardware sectors (163929 MB)
[ 37.134183] sd 0:0:1:0: [sdb] Write Protect is off
[ 37.134185] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[ 37.134197] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 37.134227] sd 0:0:1:0: [sdb] 320173056 512-byte hardware sectors (163929 MB)
[ 37.134234] sd 0:0:1:0: [sdb] Write Protect is off
[ 37.134236] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[ 37.134247] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 37.134251] sdb: sdb1 sdb2 < sdb5 >
[ 37.149554] sd 0:0:1:0: [sdb] Attached SCSI disk
[ 37.151307] sd 1:0:1:0: [sdc] 156301488 512-byte hardware sectors (80026 MB)
[ 37.152217] sd 1:0:1:0: [sdc] Write Protect is off
[ 37.152220] sd 1:0:1:0: [sdc] Mode Sense: 00 3a 00 00
[ 37.154387] sd 1:0:1:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 37.161582] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[ 37.161585] Uniform CD-ROM driver Revision: 3.20
[ 37.161619] sr 1:0:0:0: Attached scsi CD-ROM sr0
[ 37.161625] sd 1:0:1:0: [sdc] 156301488 512-byte hardware sectors (80026 MB)
[ 37.161634] sd 1:0:1:0: [sdc] Write Protect is off
[ 37.161636] sd 1:0:1:0: [sdc] Mode Sense: 00 3a 00 00
[ 37.161648] sd 1:0:1:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 37.161651] sdc: sdc1 sdc2 < sdc5 >
[ 37.201544] sd 1:0:1:0: [sdc] Attached SCSI disk
[ 37.205393] sd 0:0:0:0: Attached scsi generic sg0 type 0
[ 37.205410] sd 0:0:1:0: Attached scsi generic sg1 type 0
[ 37.205424] sr 1:0:0:0: Attached scsi generic sg2 type 5
[ 37.205441] sd 1:0:1:0: Attached scsi generic sg3 type 0
[ 37.422264] ata3: SATA link down (SStatus 0 SControl 300)
[ 37.636690] kjournald starting. Commit interval 5 seconds
[ 37.636700] EXT3-fs: mounted filesystem with ordered data mode.
[ 37.741878] ata4: SATA link down (SStatus 0 SControl 300)
[ 41.521863] usb-storage: device scan complete
[ 41.527172] scsi 2:0:0:0: Direct-Access Generic USB SD Reader 1.00 PQ: 0 ANSI: 0
[ 41.534038] scsi 2:0:0:1: Direct-Access Generic USB CF Reader 1.01 PQ: 0 ANSI: 0
[ 41.541034] scsi 2:0:0:2: Direct-Access Generic USB SM Reader 1.02 PQ: 0 ANSI: 0
[ 41.548024] scsi 2:0:0:3: Direct-Access Generic USB MS Reader 1.03 PQ: 0 ANSI: 0
[ 41.559776] sd 2:0:0:0: [sdd] Attached SCSI removable disk
[ 41.559812] sd 2:0:0:0: Attached scsi generic sg4 type 0
[ 41.570032] sd 2:0:0:1: [sde] Attached SCSI removable disk
[ 41.570067] sd 2:0:0:1: Attached scsi generic sg5 type 0
[ 41.581009] sd 2:0:0:2: [sdf] Attached SCSI removable disk
[ 41.581042] sd 2:0:0:2: Attached scsi generic sg6 type 0
[ 41.600277] sd 2:0:0:3: [sdg] Attached SCSI removable disk
[ 41.601643] sd 2:0:0:3: Attached scsi generic sg7 type 0
[ 42.457354] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
[ 42.457376] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x1c40
[ 42.832494] Linux video capture interface: v2.00
[ 42.987831] saa7130/34: v4l2 driver version 0.2.14 loaded
[ 43.007585] saa7130[0]: found at 0000:04:06.0, rev: 1, irq: 10, latency: 32, mmio: 0xfdbff000
[ 43.007593] saa7130[0]: subsystem: 1461:10ff, board: AVerMedia DVD EZMaker [card=33,autodetected]
[ 43.007609] saa7130[0]: board init: gpio is 10000
[ 43.171346] saa7130[0]: i2c eeprom 00: 61 14 ff 10 ff ff ff ff ff ff ff ff ff ff ff ff
[ 43.171354] saa7130[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 43.171361] saa7130[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 43.171367] saa7130[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 43.171373] saa7130[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 43.171378] saa7130[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 43.171384] saa7130[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 43.171390] saa7130[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 43.171480] saa7130[0]: registered device video0 [v4l2]
[ 43.171507] saa7130[0]: registered device vbi0
[ 43.180251] saa7134 ALSA driver for DMA sound loaded
[ 43.180277] saa7130[0]/alsa: saa7130[0] at 0xfdbff000 irq 10 registered as card -2
[ 43.304781] PCI: Setting latency timer of device 0000:00:10.2 to 64
[ 43.515291] input: PC Speaker as /devices/platform/pcspkr/input/input2
[ 43.626853] intel8x0_measure_ac97_clock: measured 54883 usecs
[ 43.626857] intel8x0: clocking to 46903
[ 44.249647] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input3
[ 45.401206] lp: driver loaded but no devices found
[ 45.462235] Adding 3229024k swap on /dev/sdc5. Priority:-1 extents:1 across:3229024k
[ 45.993778] EXT3 FS on sdc1, internal journal
[ 47.077799] ip_tables: (C) 2000-2006 Netfilter Core Team
[ 48.276733] ppdev: user-space parallel port driver
[ 48.353682] audit(1213814069.101:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4375 profile="/usr/sbin/cupsd" namespace="default"
[ 49.440131] Bluetooth: Core ver 2.11
[ 49.441795] NET: Registered protocol family 31
[ 49.441799] Bluetooth: HCI device and connection manager initialized
[ 49.441803] Bluetooth: HCI socket layer initialized
[ 49.457387] Bluetooth: L2CAP ver 2.9
[ 49.457391] Bluetooth: L2CAP socket layer initialized
[ 49.475797] Bluetooth: RFCOMM socket layer initialized
[ 49.475812] Bluetooth: RFCOMM TTY layer initialized
[ 49.475814] Bluetooth: RFCOMM ver 1.8
[ 53.544901] NET: Registered protocol family 17
[ 56.571424] NET: Registered protocol family 10
[ 56.571591] lo: Disabled Privacy Extensions
[ 67.346277] eth0: no IPv6 routers present
[ 132.122220] BUG: unable to handle kernel NULL pointer dereference at virtual address 00000038
[ 132.122226] printing eip: f89b54d5 *pde = 00000000
[ 132.122231] Oops: 0000 [#1]
[ 132.122234] Modules linked in: ipv6 af_packet rfcomm l2cap bluetooth ppdev iptable_filter ip_tables x_tables lp parport psmouse serio_raw evdev pcspkr snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss saa7134_alsa snd_pcm saa7134 compat_ioctl32 videobuf_dma_sg videobuf_core ir_kbd_i2c snd_seq_dummy ir_common videodev v4l2_common v4l1_compat snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd soundcore snd_page_alloc i2c_nforce2 i2c_core ext3 jbd mbcache sg sr_mod cdrom sd_mod amd74xx ide_core usb_storage libusual pata_amd sata_nv ata_generic forcedeth libata scsi_mod ehci_hcd ohci_hcd usbcore fuse
[ 132.122263]
[ 132.122265] Pid: 5088, comm: pulseaudio Not tainted (2.6.24-16-rtai #1)
[ 132.122268] EIP: 0060:[] EFLAGS: 00010282 CPU: 0
[ 132.122275] EIP is at snd_card_saa7134_capture_open+0xf/0x101 [saa7134_alsa]
[ 132.122278] EAX: df9cd500 EBX: 00000000 ECX: df9e4678 EDX: f89b80ac
[ 132.122281] ESI: df9cd500 EDI: df9e4000 EBP: 00000000 ESP: f75d1e64
[ 132.122283] DS: 007b ES: 007b FS: 0000 GS: 0033 SS: 0068
[ 132.122286] Process pulseaudio (pid: 5088, ti=f75d0000 task=df931020 task.ti=f75d0000)<0>
[ 132.122289] I-pipe domain Linux
[ 132.122290] Stack: ffffffff df9e4000 00000000 f75d1eb0 df9ff200 f7fbf108 f89c6c25 f75d1e84
[ 132.122295] df9cd500 f7fbf108 f7fbf000 f89c6cf9 f75d1eb0 00000001 00000000 df931020
[ 132.122300] c010f197 f7fbf114 f7fbf114 df9ff200 f893c3e4 00000000 df9ff200 df8d51f4
[ 132.122304] Call Trace:
[ 132.122315] [] snd_pcm_open_substream+0x3c/0x76 [snd_pcm]
[ 132.122334] [] snd_pcm_open+0x9a/0x172 [snd_pcm]
[ 132.122351] [] default_wake_function+0x0/0x5
[ 132.122368] [] snd_open+0xbb/0x105 [snd]
[ 132.122386] [] chrdev_open+0xe0/0xf6
[ 132.122397] [] chrdev_open+0x0/0xf6
[ 132.122401] [] __dentry_open+0xc1/0x16d
[ 132.122413] [] nameidata_to_filp+0x24/0x33
[ 132.122421] [] do_filp_open+0x37/0x3e
[ 132.122432] [] snd_ctl_release+0xbd/0xd9 [snd]
[ 132.122460] [] get_unused_fd_flags+0x49/0xa8
[ 132.122472] [] do_sys_open+0x44/0xca
[ 132.122486] [] sys_open+0x1c/0x1e
[ 132.122490] [] sysenter_past_esp+0x6e/0x72
[ 132.122521] =======================
[ 132.122522] Code: 78 42 00 8b 50 38 74 11 c7 82 54 05 00 00 01 00 00 00 89 d0 e8 d0 5a 02 00 31 c0 c3 55 57 56 89 c6 53 83 ec 08 8b 68 08 8b 78 70 <8b> 5d 38 8d 43 48 89 44 24 04 e8 59 f1 8a c7 8b 83 b8 05 00 00
[ 132.122540] EIP: [] snd_card_saa7134_capture_open+0xf/0x101 [saa7134_alsa] SS:ESP 0068:f75d1e64
[ 132.122548] ---[ end trace bed87f0925460442 ]---
[ 199.291713] I-pipe: Domain RTAI registered.
[ 199.291718] RTAI[hal]: <3.6> mounted over IPIPE-NOTHREADS 2.0-04.
[ 199.291731] BUG: Unhandled exception over domain RTAI at 0xc013a453 - switching to ROOT
[ 199.291736] Pid: 5241, comm: insmod Tainted: G D 2.6.24-16-rtai #1
[ 199.291742] [] __ipipe_handle_exception+0x104/0x156
[ 199.291751] [] __ipipe_restore_root+0xc/0x22
[ 199.291767] [] error_code+0x6f/0x80
[ 199.291789] [] __ipipe_restore_root+0xc/0x22
[ 199.291795] [] release_console_sem+0x15f/0x1b1
[ 199.291808] [] vprintk+0x239/0x261
[ 199.291836] [] vsnprintf+0x29c/0x469
[ 199.291854] [] printk+0x4c/0xb5
[ 199.291866] [] rt_printk+0x3f/0x47 [rtai_hal]
[ 199.291901] [] md5_transform+0x3ce/0x6df
[ 199.291914] [] vt_console_print+0x0/0x249
[ 199.291920] [] __call_console_drivers+0x34/0x40
[ 199.291929] [] release_console_sem+0x198/0x1b1
[ 199.291941] [] vprintk+0x255/0x261
[ 199.291977] [] idr_get_new+0xa/0x24
[ 199.291985] [] printk+0x4c/0xb5
[ 199.291991] [] rtai_domain_entry+0x27/0x3f [rtai_hal]
[ 199.292006] [] ipipe_register_domain+0x198/0x1cb
[ 199.292016] [] __rtai_hal_init+0x1da/0x287 [rtai_hal]
[ 199.292025] [] rtai_uvec_handler+0x0/0x3a [rtai_hal]
[ 199.292038] [] sys_init_module+0x122e/0x13a6
[ 199.292054] [] rtai_domain_entry+0x0/0x3f [rtai_hal]
[ 199.292066] [] sys_init_module+0x12ee/0x13a6
[ 199.292145] [] sysenter_past_esp+0x6e/0x72
[ 199.292175] =======================
[ 199.292182] ------------[ cut here ]------------
[ 199.292184] Kernel BUG at c013a453 [verbose debug info unavailable]
[ 199.292186] invalid opcode: 0000 [#2]
[ 199.292188] Modules linked in: rtai_hal ipv6 af_packet rfcomm l2cap bluetooth ppdev iptable_filter ip_tables x_tables lp parport psmouse serio_raw evdev pcspkr snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss saa7134_alsa snd_pcm saa7134 compat_ioctl32 videobuf_dma_sg videobuf_core ir_kbd_i2c snd_seq_dummy ir_common videodev v4l2_common v4l1_compat snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd soundcore snd_page_alloc i2c_nforce2 i2c_core ext3 jbd mbcache sg sr_mod cdrom sd_mod amd74xx ide_core usb_storage libusual pata_amd sata_nv ata_generic forcedeth libata scsi_mod ehci_hcd ohci_hcd usbcore fuse
[ 199.292213]
[ 199.292215] Pid: 5241, comm: insmod Tainted: G D (2.6.24-16-rtai #1)
[ 199.292218] EIP: 0060:[] EFLAGS: 00010202 CPU: 0
[ 199.292221] EIP is at __ipipe_restore_root+0xc/0x22
[ 199.292223] EAX: 00000001 EBX: 00005ee8 ECX: ffffffff EDX: 00005f2d
[ 199.292225] ESI: 00005f2d EDI: 00005f2d EBP: 00005f2d ESP: f7743cac
[ 199.292228] DS: 007b ES: 007b FS: 0000 GS: 0033 SS: 0068
[ 199.292230] Process insmod (pid: 5241, ti=f7742000 task=f777c560 task.ti=f7742000)<0>
[ 199.292232] I-pipe domain Linux
[ 199.292233] Stack: c0112967 00000000 fffff3ad f7743d08 00000200 00000012 f7743d08 c0112d33
[ 199.292238] f7743cf6 c02a1d48 00000036 000000c7 00047386 00f585e0 00000048 c033dcd1
[ 199.292242] 66b64bc9 116345c9 363cffce 20205b3e 2e393931 37313932 205d3831 00047300
[ 199.292245] Call Trace:
[ 199.292247] [] release_console_sem+0x15f/0x1b1
[ 199.292259] [] vprintk+0x239/0x261
[ 199.292287] [] vsnprintf+0x29c/0x469
[ 199.292303] [] printk+0x4c/0xb5
[ 199.292315] [] rt_printk+0x3f/0x47 [rtai_hal]
[ 199.292347] [] md5_transform+0x3ce/0x6df
[ 199.292359] [] vt_console_print+0x0/0x249
[ 199.292364] [] __call_console_drivers+0x34/0x40
[ 199.292372] [] release_console_sem+0x198/0x1b1
[ 199.292384] [] vprintk+0x255/0x261
[ 199.292418] [] idr_get_new+0xa/0x24
[ 199.292427] [] printk+0x4c/0xb5
[ 199.292432] [] rtai_domain_entry+0x27/0x3f [rtai_hal]
[ 199.292447] [] ipipe_register_domain+0x198/0x1cb
[ 199.292458] [] __rtai_hal_init+0x1da/0x287 [rtai_hal]
[ 199.292466] [] rtai_uvec_handler+0x0/0x3a [rtai_hal]
[ 199.292479] [] sys_init_module+0x122e/0x13a6
[ 199.292496] [] rtai_domain_entry+0x0/0x3f [rtai_hal]
[ 199.292507] [] sys_init_module+0x12ee/0x13a6
[ 199.292589] [] sysenter_past_esp+0x6e/0x72
[ 199.292618] =======================
[ 199.292619] Code: 0b eb fe fa 0f ba 35 a4 14 2e c0 00 83 3d a8 14 2e c0 00 74 08 83 c8 ff e8 f4 fb ff ff fb c3 81 3d 24 19 2e c0 80 31 38 c0 74 04 <0f> 0b eb fe 85 c0 74 09 0f ba 2d a4 14 2e c0 00 c3 e9 b2 ff ff
[ 199.292635] EIP: [] __ipipe_restore_root+0xc/0x22 SS:ESP 0068:f7743cac
[ 199.292640] ---[ end trace bed87f0925460442 ]---

Debug file information:
/etc/init.d/realtime: line 148: 5241 Segmentation fault $INSMOD $MOD
5226
PID TTY STAT TIME COMMAND
Stopping realtime threads
RTAPI: ERROR: could not open shared memory (errno=2)
HAL: ERROR: rtapi init failed
halcmd: hal_init() failed: -9
NOTE: 'rtapi' kernel module must be loaded
Unloading hal components
RTAPI: ERROR: could not open shared memory (errno=2)
HAL: ERROR: rtapi init failed
halcmd: hal_init() failed: -9
NOTE: 'rtapi' kernel module must be loaded
ERROR: Module hal_lib does not exist in /proc/modules
ERROR: Module rtapi does not exist in /proc/modules
ERROR: Module rtai_math does not exist in /proc/modules
ERROR: Module rtai_sem does not exist in /proc/modules
ERROR: Module rtai_fifos does not exist in /proc/modules
ERROR: Module rtai_sched does not exist in /proc/modules
ERROR: Module rtai_hal is in use

---

### Post by alex.joni on 2008-07-20
> **oakes3 said:**
> 

Same error both times: it seem I get a RTAPI error / segmentation error which I have no idea how to solve.

All input welcome - Thanks



This is an odd place to report errors about emc2 :)
Please use the channels provided at [www.linuxcnc.org](www.linuxcnc.org)
I think you are witnessing a problem with RTAI that has been recently fixed. It would be glad if you could help us confirm it.
Please get online on #emc at irc.freenode.net, and look for me (alex_joni) or jepler for assistance.

Best regards,
Alex

---

### Post by mickymin on 2013-02-05
Now I have the same poblems on one computer, but the others are ok.
I wonder how you solve the problem?
Can I solve the problem by using the ubuntu10.04 ISO ?

---

