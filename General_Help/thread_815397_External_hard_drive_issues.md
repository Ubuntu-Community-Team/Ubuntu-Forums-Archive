---
title: "External hard drive issues"
date: 2008-06-01
forum: General Help
---

### Post by jake3237788 on 2008-06-01
Hello I recently switch form windows to ubuntu, before I formated I backed up all my data to an external hard drive. However ubuntu wont recognize it. It recognizes my flash drive as soon as I plug it in. I have read around on the forums and I have read some stuff about mounting a disk. I have also come across the command sudo fdisk -l. I get the same text in terminal after typing that regardless if the external is unplug or plugged in. all my stuff is backed up on that drive so I would appreciate it if some one could help. I am using ubuntu 8 if that makes any difference.

---

### Post by benerivo on 2008-06-01
Try plugging it in, and waiting several seconds. the open a terminal and type```
dmesg
```
Also try```
blkid
```adn post the outputs here

---

### Post by jake3237788 on 2008-06-01
[    0.000000] ACPI: IRQ14 used by override.

[    0.000000] ACPI: IRQ15 used by override.

[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs

[    0.000000] Using ACPI (MADT) for SMP configuration information

[    0.000000] Allocating PCI resources starting at 68000000 (gap: 60000000:80000000)

[    0.000000] swsusp: Registered nosave memory region: 000000000009c000 - 00000000000a0000

[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000

[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000

[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 373619

[    0.000000] Kernel command line: root=UUID=ed21c79b-0951-49ec-9073-a1bce6a1257a ro quiet splash

[    0.000000] mapped APIC to ffffb000 (fee00000)

[    0.000000] mapped IOAPIC to ffffa000 (fec00000)

[    0.000000] Enabling fast FPU save and restore... done.

[    0.000000] Enabling unmasked SIMD FPU exception support... done.

[    0.000000] Initializing CPU#0

[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)

[    0.000000] Detected 1808.239 MHz processor.

[   16.894883] spurious 8259A interrupt: IRQ7.

[   16.898073] Console: colour VGA+ 80x25

[   16.898077] console [tty0] enabled

[   16.898535] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)

[   16.898981] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)

[   16.952706] Memory: 1480928k/1506240k available (2176k kernel code, 23996k reserved, 1007k data, 368k init, 588736k highmem)

[   16.952715] virtual kernel memory layout:

[   16.952716]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)

[   16.952718]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)

[   16.952719]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)

[   16.952720]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)

[   16.952721]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)

[   16.952722]       .data : 0xc0320134 - 0xc041bdc4   (1007 kB)

[   16.952724]       .text : 0xc0100000 - 0xc0320134   (2176 kB)

[   16.952727] Checking if this processor honours the WP bit even in supervisor mode... Ok.

[   16.952773] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1

[   17.032762] Calibrating delay using timer specific routine.. 3619.89 BogoMIPS (lpj=7239787)

[   17.032795] Security Framework initialized

[   17.032805] SELinux:  Disabled at boot.

[   17.032823] AppArmor: AppArmor initialized

[   17.032828] Failure registering capabilities with primary security module.

[   17.032838] Mount-cache hash table entries: 512

[   17.032984] Initializing cgroup subsys ns

[   17.032988] Initializing cgroup subsys cpuacct

[   17.033000] CPU: After generic identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001 00000000

[   17.033009] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)

[   17.033012] CPU: L2 Cache: 512K (64 bytes/line)

[   17.033015] CPU: After all inits, caps: 078bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000001 00000000

[   17.033025] Compat vDSO mapped to ffffe000.

[   17.033039] Checking 'hlt' instruction... OK.

[   17.049081] SMP alternatives: switching to UP code

[   17.050286] Freeing SMP alternatives: 11k freed

[   17.050419] Early unpacking initramfs... done

[   17.387233] ACPI: Core revision 20070126

[   17.387298] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.

[   17.391556] CPU0: AMD Athlon(tm) 64 Processor 3000+ stepping 02

[   17.391581] Total of 1 processors activated (3619.89 BogoMIPS).

[   17.391881] ENABLING IO-APIC IRQs

[   17.392118] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1

[   17.536587] Brought up 1 CPUs

[   17.536636] CPU0 attaching sched-domain:

[   17.536639]  domain 0: span 01

[   17.536640]   groups: 01

[   17.536825] net_namespace: 64 bytes

[   17.536831] Booting paravirtualized kernel on bare hardware

[   17.537285] Time: 22:33:34  Date: 06/01/08

[   17.537321] NET: Registered protocol family 16

[   17.537489] EISA bus registered

[   17.537517] ACPI: bus type pci registered

[   17.544120] PCI: PCI BIOS revision 3.00 entry at 0xfa7c0, last bus=4

[   17.544122] PCI: Using configuration type 1

[   17.544124] Setting up standard PCI resources

[   17.547817] ACPI: EC: Look up EC in DSDT

[   17.553951] ACPI: Interpreter enabled

[   17.553954] ACPI: (supports S0 S1 S4 S5)

[   17.553967] ACPI: Using IOAPIC for interrupt routing

[   17.563367] ACPI: PCI Root Bridge [PCI0] (0000:00)

[   17.564411] PCI: Transparent bridge - 0000:00:10.0

[   17.564430] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]

[   17.564727] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]

[   17.661937] ACPI: PCI Interrupt Link [LNK1] (IRQs *5 7 9 10 11 14 15)

[   17.662107] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.

[   17.662276] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.

[   17.662445] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.

[   17.662614] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 11 14 15) *0, disabled.

[   17.662783] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.

[   17.662953] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 *10 11 14 15)

[   17.663121] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.

[   17.663291] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 *10 11 14 15)

[   17.663460] ACPI: PCI Interrupt Link [LUBB] (IRQs 5 7 9 10 11 14 15) *0, disabled.

[   17.663630] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 *10 11 14 15)

[   17.663808] ACPI: PCI Interrupt Link [LACI] (IRQs 5 7 9 10 *11 14 15)

[   17.663976] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 11 14 15) *0, disabled.

[   17.664147] ACPI: PCI Interrupt Link [LPMU] (IRQs *5 7 9 10 11 14 15)

[   17.664316] ACPI: PCI Interrupt Link [LMCI] (IRQs 5 7 9 10 11 14 15) *0, disabled.

[   17.664490] ACPI: PCI Interrupt Link [LSMB] (IRQs *5 7 9 10 11 14 15)

[   17.664665] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 10 *11 14 15)

[   17.664834] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.

[   17.665005] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)

[   17.665215] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0

[   17.665413] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.

[   17.665613] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.

[   17.665809] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.

[   17.666006] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.

[   17.666202] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.

[   17.666399] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0

[   17.666595] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.

[   17.666792] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0

[   17.666989] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.

[   17.667187] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0

[   17.667384] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0

[   17.667584] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0

[   17.667782] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0, disabled.

[   17.667981] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.

[   17.668179] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0

[   17.668377] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0

[   17.668581] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.

[   17.668780] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.

[   17.668978] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0

[   17.669105] Linux Plug and Play Support v0.97 (c) Adam Belay

[   17.669133] pnp: PnP ACPI init

[   17.669140] ACPI: bus type pnp registered

[   17.674114] pnpacpi: exceeded the max number of mem resources: 12

[   17.674173] pnp: PnP ACPI: found 13 devices

[   17.674175] ACPI: ACPI bus type pnp unregistered

[   17.674178] PnPBIOS: Disabled by ACPI PNP

[   17.674379] PCI: Using ACPI for IRQ routing

[   17.674383] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report

[   17.772460] NET: Registered protocol family 8

[   17.772462] NET: Registered protocol family 20

[   17.772531] AppArmor: AppArmor Filesystem Enabled

[   17.776429] Time: tsc clocksource has been installed.

[   17.784457] system 00:01: ioport range 0x1000-0x107f has been reserved

[   17.784460] system 00:01: ioport range 0x1080-0x10ff has been reserved

[   17.784462] system 00:01: ioport range 0x1400-0x147f has been reserved

[   17.784465] system 00:01: ioport range 0x1480-0x14ff has been reserved

[   17.784468] system 00:01: ioport range 0x1800-0x187f has been reserved

[   17.784470] system 00:01: ioport range 0x1880-0x18ff has been reserved

[   17.784473] system 00:01: ioport range 0x2000-0x207f has been reserved

[   17.784476] system 00:01: ioport range 0x2080-0x20ff has been reserved

[   17.784479] system 00:01: iomem range 0xfefe0000-0xfefe01ff could not be reserved

[   17.784482] system 00:01: iomem range 0x5c000000-0x5fffffff could not be reserved

[   17.784487] system 00:02: ioport range 0x4d0-0x4d1 has been reserved

[   17.784490] system 00:02: ioport range 0x800-0x87f has been reserved

[   17.784493] system 00:02: ioport range 0x290-0x29f has been reserved

[   17.784496] system 00:02: ioport range 0x290-0x297 has been reserved

[   17.784504] system 00:0b: iomem range 0xe0000000-0xefffffff could not be reserved

[   17.784507] system 00:0b: iomem range 0xbf00000-0xbffffff could not be reserved

[   17.784510] system 00:0b: iomem range 0x1bf00000-0x1bffffff could not be reserved

[   17.784512] system 00:0b: iomem range 0x2bf00000-0x2bffffff could not be reserved

[   17.784515] system 00:0b: iomem range 0x3bf00000-0x3bffffff could not be reserved

[   17.784518] system 00:0b: iomem range 0x4bf00000-0x4bffffff could not be reserved

[   17.784521] system 00:0b: iomem range 0x5bf00000-0x5bffffff has been reserved

[   17.784524] system 00:0b: iomem range 0x6bf00000-0x6bffffff has been reserved

[   17.784527] system 00:0b: iomem range 0x7bf00000-0x7bffffff has been reserved

[   17.784533] system 00:0c: iomem range 0xcde00-0xcffff has been reserved

[   17.784539] system 00:0c: iomem range 0xf0000-0xf7fff could not be reserved

[   17.784542] system 00:0c: iomem range 0xf8000-0xfbfff could not be reserved

[   17.784545] system 00:0c: iomem range 0xfc000-0xfffff could not be reserved

[   17.784548] system 00:0c: iomem range 0x5bef0000-0x5befffff could not be reserved

[   17.784551] system 00:0c: iomem range 0xffff0000-0xffffffff could not be reserved

[   17.784554] system 00:0c: iomem range 0x0-0x9ffff could not be reserved

[   17.784556] system 00:0c: iomem range 0x100000-0x5beeffff could not be reserved

[   17.784559] system 00:0c: iomem range 0x5bf00000-0x5fefffff could not be reserved

[   17.784562] system 00:0c: iomem range 0xfec00000-0xfec00fff could not be reserved

[   17.784565] system 00:0c: iomem range 0xfee00000-0xfeefffff could not be reserved

[   17.784568] system 00:0c: iomem range 0xfefff000-0xfeffffff could not be reserved

[   17.814927] PCI: Bridge: 0000:00:02.0

[   17.814929]   IO window: a000-afff

[   17.814932]   MEM window: fd700000-fd7fffff

[   17.814935]   PREFETCH window: fde00000-fdefffff

[   17.814938] PCI: Bridge: 0000:00:03.0

[   17.814939]   IO window: 9000-9fff

[   17.814942]   MEM window: fdd00000-fddfffff

[   17.814944]   PREFETCH window: fdc00000-fdcfffff

[   17.814947] PCI: Bridge: 0000:00:04.0

[   17.814949]   IO window: b000-bfff

[   17.814951]   MEM window: fd900000-fd9fffff

[   17.814953]   PREFETCH window: fd800000-fd8fffff

[   17.814956] PCI: Bridge: 0000:00:10.0

[   17.814958]   IO window: c000-cfff

[   17.814962]   MEM window: fdb00000-fdbfffff

[   17.814964]   PREFETCH window: fda00000-fdafffff

[   17.814984] PCI: Setting latency timer of device 0000:00:02.0 to 64

[   17.814991] PCI: Setting latency timer of device 0000:00:03.0 to 64

[   17.814997] PCI: Setting latency timer of device 0000:00:04.0 to 64

[   17.815005] PCI: Setting latency timer of device 0000:00:10.0 to 64

[   17.815017] NET: Registered protocol family 2

[   17.852475] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)

[   17.852788] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)

[   17.853714] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)

[   17.854167] TCP: Hash tables configured (established 131072 bind 65536)

[   17.854170] TCP reno registered

[   17.864536] checking if image is initramfs... it is

[   18.316183] Switched to high resolution mode on CPU 0

[   18.511553] Freeing initrd memory: 7271k freed

[   18.512176] audit: initializing netlink socket (disabled)

[   18.512192] audit(1212359614.460:1): initialized

[   18.512360] highmem bounce pool size: 64 pages

[   18.513968] VFS: Disk quotas dquot_6.5.1

[   18.514030] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)

[   18.514166] io scheduler noop registered

[   18.514168] io scheduler anticipatory registered

[   18.514170] io scheduler deadline registered

[   18.514180] io scheduler cfq registered (default)

[   18.514198] Boot video device is 0000:00:05.0

[   26.523333] 0000:00:0b.1 EHCI: BIOS handoff failed (BIOS bug ?) 01010001

[   26.523448] PCI: Setting latency timer of device 0000:00:02.0 to 64

[   26.523471] assign_interrupt_mode Found MSI capability

[   26.523493] Allocate Port Service[0000:00:02.0:pcie00]

[   26.523551] PCI: Setting latency timer of device 0000:00:03.0 to 64

[   26.523572] assign_interrupt_mode Found MSI capability

[   26.523588] Allocate Port Service[0000:00:03.0:pcie00]

[   26.523640] PCI: Setting latency timer of device 0000:00:04.0 to 64

[   26.523661] assign_interrupt_mode Found MSI capability

[   26.523676] Allocate Port Service[0000:00:04.0:pcie00]

[   26.523860] isapnp: Scanning for PnP cards...

[   26.876858] isapnp: No Plug & Play device found

[   26.902241] Real Time Clock Driver v1.12ac

[   26.902352] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled

[   26.902492] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A

[   26.903064] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A

[   26.904034] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize

[   26.904101] input: Macintosh mouse button emulation as /devices/virtual/input/input0

[   26.904181] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1

[   26.904184] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp

[   26.904588] serio: i8042 KBD port at 0x60,0x64 irq 1

[   26.915183] mice: PS/2 mouse device common for all mice

[   26.915285] EISA: Probing bus 0 at eisa.0

[   26.915292] Cannot allocate resource for EISA slot 1

[   26.915294] Cannot allocate resource for EISA slot 2

[   26.915313] EISA: Detected 0 cards.

[   26.915316] cpuidle: using governor ladder

[   26.915318] cpuidle: using governor menu

[   26.915410] NET: Registered protocol family 1

[   26.915433] Using IPI No-Shortcut mode

[   26.915471] registered taskstats version 1

[   26.915598]   Magic number: 12:437:602

[   26.915687]   hash matches device ptyd6

[   26.915795]   hash matches device PNP0C0F:0e

[   26.915811] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found

[   26.915813] EDD information not available.

[   26.916086] Freeing unused kernel memory: 368k freed

[   26.967094] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1

[   28.166772] fuse init (API version 7.9)

[   28.185638] ACPI: Fan [FAN] (on)

[   28.192528] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]

[   28.193922] ACPI: Thermal Zone [THRM] (40 C)

[   29.337800] usbcore: registered new interface driver usbfs

[   29.337828] usbcore: registered new interface driver hub

[   29.345771] usbcore: registered new device driver usb

[   29.361919] SCSI subsystem initialized

[   29.369772] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver

[   29.370201] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 23

[   29.370213] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [APCF] -> GSI 23 (level, low) -> IRQ 16

[   29.370229] PCI: Setting latency timer of device 0000:00:0b.0 to 64

[   29.370232] ohci_hcd 0000:00:0b.0: OHCI Host Controller

[   29.370551] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1

[   29.370571] ohci_hcd 0000:00:0b.0: irq 16, io mem 0xfe02f000

[   29.427826] usb usb1: configuration #1 chosen from 1 choice

[   29.427856] hub 1-0:1.0: USB hub found

[   29.427865] hub 1-0:1.0: 8 ports detected

[   29.433666] libata version 3.00 loaded.

[   29.530177] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22

[   29.530191] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [APCL] -> GSI 22 (level, low) -> IRQ 17

[   29.530204] PCI: Setting latency timer of device 0000:00:0b.1 to 64

[   29.530208] ehci_hcd 0000:00:0b.1: EHCI Host Controller

[   29.530237] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 2

[   29.530278] ehci_hcd 0000:00:0b.1: debug port 1

[   29.530282] PCI: cache line size of 64 is not supported by device 0000:00:0b.1

[   29.530294] ehci_hcd 0000:00:0b.1: irq 17, io mem 0xfe02e000

[   29.541629] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004

[   29.541779] usb usb2: configuration #1 chosen from 1 choice

[   29.541803] hub 2-0:1.0: USB hub found

[   29.541810] hub 2-0:1.0: 8 ports detected

[   29.585684] Floppy drive(s): fd0 is 1.44M

[   29.605428] FDC 0 is a post-1991 82077

[   29.645743] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.

[   29.646136] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 21

[   29.646148] ACPI: PCI Interrupt 0000:00:14.0[A] -> Link [APCH] -> GSI 21 (level, low) -> IRQ 18

[   29.646155] PCI: Setting latency timer of device 0000:00:14.0 to 64

[   30.057329] usb 2-1: new high speed USB device using ehci_hcd and address 2

[   30.165660] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x20 @ 1, addr 00:e0:4c:ec:41:04

[   30.165667] forcedeth 0000:00:14.0: highdma pwrctl timirq lnktim desc-v3

[   30.166064] PCI: Setting latency timer of device 0000:00:0d.0 to 64

[   30.166458] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 20

[   30.166470] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [APSI] -> GSI 20 (level, low) -> IRQ 19

[   30.166489] PCI: Setting latency timer of device 0000:00:0e.0 to 64

[   30.166497] ACPI: PCI interrupt for device 0000:00:0e.0 disabled

[   30.168327] sata_nv 0000:00:0e.0: version 3.5

[   30.168335] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [APSI] -> GSI 20 (level, low) -> IRQ 19

[   30.168363] PCI: Setting latency timer of device 0000:00:0e.0 to 64

[   30.169925] scsi0 : sata_nv

[   30.170623] scsi1 : sata_nv

[   30.170805] ata1: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xe000 irq 19

[   30.170808] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xe008 irq 19

[   30.206411] usb 2-1: configuration #1 chosen from 1 choice

[   30.389168] usbcore: registered new interface driver libusual

[   30.395015] Initializing USB Mass Storage driver...

[   30.636957] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)

[   30.645280] ata1.00: ATA-7: Maxtor 6Y080M0, YAR51HW0, max UDMA/133

[   30.645283] ata1.00: 160086528 sectors, multi 16: LBA 

[   30.661249] ata1.00: configured for UDMA/133

[   30.692913] usb 1-2: new low speed USB device using ohci_hcd and address 2

[   30.910015] usb 1-2: configuration #1 chosen from 1 choice

[   30.921098] scsi2 : SCSI emulation for USB Mass Storage devices

[   30.924837] usbcore: registered new interface driver usb-storage

[   30.924842] USB Mass Storage support registered.

[   30.924945] usb-storage: device found at 2

[   30.924947] usb-storage: waiting for device to settle before scanning

[   30.931583] usbcore: registered new interface driver hiddev

[   30.945216] input: Microsoft Microsoft Wireless Optical Mouse&#65533; 1.00 as /devices/pci0000:00/0000:00:0b.0/usb1/1-2/1-2:1.0/input/input2

[   30.956804] input,hidraw0: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Mouse&#65533; 1.00] on usb-0000:00:0b.0-2

[   30.956824] usbcore: registered new interface driver usbhid

[   30.956828] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver

[   30.972788] ata2: SATA link down (SStatus 0 SControl 300)

[   30.983386] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 6Y080M0   YAR5 PQ: 0 ANSI: 5

[   30.988229] pata_amd 0000:00:0d.0: version 0.3.10

[   30.988285] PCI: Setting latency timer of device 0000:00:0d.0 to 64

[   30.988793] scsi3 : pata_amd

[   30.994347] scsi4 : pata_amd

[   30.994968] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf400 irq 14

[   30.994971] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf408 irq 15

[   30.996749] Driver 'sd' needs updating - please use bus_type methods

[   30.996840] sd 0:0:0:0: [sda] 160086528 512-byte hardware sectors (81964 MB)

[   30.996852] sd 0:0:0:0: [sda] Write Protect is off

[   30.996855] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00

[   30.996871] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

[   30.996916] sd 0:0:0:0: [sda] 160086528 512-byte hardware sectors (81964 MB)

[   30.996925] sd 0:0:0:0: [sda] Write Protect is off

[   30.996927] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00

[   30.996941] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

[   30.996945]  sda: sda1 sda2 < sda5 >

[   31.026888] sd 0:0:0:0: [sda] Attached SCSI disk

[   31.033110] sd 0:0:0:0: Attached scsi generic sg0 type 0

[   31.294788] Attempting manual resume

[   31.294793] swsusp: Resume From Partition 8:5

[   31.294795] PM: Checking swsusp image.

[   31.295021] PM: Resume from disk failed.

[   31.336700] kjournald starting.  Commit interval 5 seconds

[   31.336715] EXT3-fs: mounted filesystem with ordered data mode.

[   31.477003] ata4.01: ATAPI: BENQ    DVD DD DW1650, BCFC, max UDMA/33

[   31.648840] ata4.01: configured for UDMA/33

[   31.650845] scsi 4:0:1:0: CD-ROM            BENQ     DVD DD DW1650    BCFC PQ: 0 ANSI: 5

[   31.650919] scsi 4:0:1:0: Attached scsi generic sg1 type 5

[   35.922133] usb-storage: device scan complete

[   35.927111] scsi 2:0:0:0: Direct-Access     GENERIC  USB Storage-SMC  I19B PQ: 0 ANSI: 0 CCS

[   35.932105] scsi 2:0:0:1: Direct-Access     GENERIC  USB Storage-CFC  I19B PQ: 0 ANSI: 0 CCS

[   35.937095] scsi 2:0:0:2: Direct-Access     GENERIC  USB Storage-SDC  I19B PQ: 0 ANSI: 0 CCS

[   35.942106] scsi 2:0:0:3: Direct-Access     GENERIC  USB Storage-MSC  I19B PQ: 0 ANSI: 0 CCS

[   35.946245] sd 2:0:0:0: [sdb] Attached SCSI removable disk

[   35.946278] sd 2:0:0:0: Attached scsi generic sg2 type 0

[   35.950229] sd 2:0:0:1: [sdc] Attached SCSI removable disk

[   35.950253] sd 2:0:0:1: Attached scsi generic sg3 type 0

[   35.954228] sd 2:0:0:2: [sdd] Attached SCSI removable disk

[   35.954252] sd 2:0:0:2: Attached scsi generic sg4 type 0

[   35.958225] sd 2:0:0:3: [sde] Attached SCSI removable disk

[   35.958251] sd 2:0:0:3: Attached scsi generic sg5 type 0

[   40.708581] input: Power Button (FF) as /devices/virtual/input/input3

[   40.723084] ACPI: Power Button (FF) [PWRF]

[   40.723228] input: Power Button (CM) as /devices/virtual/input/input4

[   40.735072] ACPI: Power Button (CM) [PWRB]

[   40.735149] input: Sleep Button (CM) as /devices/virtual/input/input5

[   40.755072] ACPI: Sleep Button (CM) [SLPB]

[   40.998993] pci_hotplug: PCI Hot Plug PCI Core version: 0.5

[   41.055021] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4

[   41.386874] Linux agpgart interface v0.102

[   41.476197] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00

[   41.476224] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x1c40

[   42.124558] nvidia: module license 'NVIDIA' taints kernel.

[   44.720924] input: PC Speaker as /devices/platform/pcspkr/input/input6

[   45.060990] ACPI: PCI Interrupt Link [APC7] enabled at IRQ 16

[   45.061004] ACPI: PCI Interrupt 0000:00:05.0[A] -> Link [APC7] -> GSI 16 (level, low) -> IRQ 20

[   45.061012] PCI: Setting latency timer of device 0000:00:05.0 to 64

[   45.061234] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008

[   45.067932] Driver 'sr' needs updating - please use bus_type methods

[   45.083918] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray

[   45.083925] Uniform CD-ROM driver Revision: 3.20

[   45.084004] sr 4:0:1:0: Attached scsi CD-ROM sr0

[   45.402316] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16

[   45.402323] ACPI: PCI Interrupt 0000:04:08.0[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 20

[   45.402350] snd-ca0106: Model 100a Rev 00000000 Serial 100a1102

[   45.976135] parport_pc 00:09: reported by Plug and Play ACPI

[   45.976189] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]

[   46.068478] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 23

[   46.068485] ACPI: PCI Interrupt 0000:00:10.2[C] -> Link [APCJ] -> GSI 23 (level, low) -> IRQ 16

[   46.068510] PCI: Setting latency timer of device 0000:00:10.2 to 64

[   46.391865] intel8x0_measure_ac97_clock: measured 54828 usecs

[   46.391871] intel8x0: clocking to 46856

[   48.512787] lp0: using parport0 (interrupt-driven).

[   48.578177] Adding 3301316k swap on /dev/sda5.  Priority:-1 extents:1 across:3301316k

[   49.137230] EXT3 FS on sda1, internal journal

[   50.908512] ip_tables: (C) 2000-2006 Netfilter Core Team

[   51.301932] No dock devices found.

[   51.665360] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3000+ processors (1 cpu cores) (version 2.20.00)

[   51.665399] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x6

[   51.665402] powernow-k8:    1 : fid 0x2 (1000 MHz), vid 0x12

[   52.569718] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)

[   52.569724] apm: overridden by ACPI.

[   52.704201] ppdev: user-space parallel port driver

[   52.830921] audit(1212359649.426:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5071 profile="/usr/sbin/cupsd" namespace="default"

[   97.016607] Marking TSC unstable due to: cpufreq changes.

[   97.023590] Time: acpi_pm clocksource has been installed.

[   97.423492] Clocksource tsc unstable (delta = -180952520 ns)

[   98.648752] Bluetooth: Core ver 2.11

[   98.649738] NET: Registered protocol family 31

[   98.649745] Bluetooth: HCI device and connection manager initialized

[   98.649751] Bluetooth: HCI socket layer initialized

[   98.739018] Bluetooth: L2CAP ver 2.9

[   98.739027] Bluetooth: L2CAP socket layer initialized

[   98.828342] Bluetooth: RFCOMM socket layer initialized

[   98.828842] Bluetooth: RFCOMM TTY layer initialized

[   98.828848] Bluetooth: RFCOMM ver 1.8

[  102.046776] NET: Registered protocol family 17

[  104.240208] NET: Registered protocol family 10

[  104.241190] lo: Disabled Privacy Extensions

[  115.828686] eth0: no IPv6 routers present

[  193.558485] usb 2-7: new high speed USB device using ehci_hcd and address 4

[  193.692441] usb 2-7: configuration #1 chosen from 1 choice

[  193.717883] scsi5 : SCSI emulation for USB Mass Storage devices

[  193.726516] usb-storage: device found at 4

[  193.726523] usb-storage: waiting for device to settle before scanning

[  198.730146] usb-storage: device scan complete

[  365.622241] usb 2-7: USB disconnect, address 4

[  365.622461] scsi 5:0:0:0: Device offlined - not ready after error recovery




and nothing come up after I enter 'blkid'

thank you for taking the time to help me.

---

### Post by cybrsaylr on 2008-06-01
I also get that "Cannot Mount Volume" at times using Ubuntu HH, when I try using my ext HHD. It's a windows problem. I have a dual boot system XP/Ubuntu and can use the ext HDD on both XP & Hardy but if the ext HDD isn't shutdown properly on Windows it won't work on Hardy till you go back into Windows shut it down by using the 'safely remove hardware' prompt on the lower right taskbar next to the clock in Windows. Once you do that it will mount properly when going back into Ubuntu. 
I used to get that "Cannot Mount Volume" in Gutsy Gibbon also at times.

I believe this holds the same for Vista as well as XP.

---

### Post by highfructose327 on 2008-06-01
Jake3237788, I have a similar issue usb stick recognized, but my Sansa Fuze is not. I plug the Sansa in, open up terminal and  run 
```
sudo modprobe -r ehci_hcd
```
 it then detects the player. I have to do this each time, but it works for now. It may work for your External HD, good luck.

---

### Post by jake3237788 on 2008-06-02
In regard to the safely remove hard drive thing, I did that in windows before formating, I safely removed the drive. Then after searching for some answer as to why ubuntu wont recognize my external I read you are supposed to shut down windows with the drive still plugged in? I tried that and ubuntu still wont recognize it. I will try the safely remove thing again and see. I hope that all it is.  

Also nothing happens when I use that modprobe command.  

Thanks for all the help guys.

---

### Post by cybrsaylr on 2008-06-02
I leave eveything plugged in.
I just click on 'safely remove hardware' prompt next to the clock in Windows, then let Windows do its thing safely shutting the ext HDD down, then restart PC and go into Ubuntu and all is well.
Ubuntu then mounts the ext HDD normally.

---

