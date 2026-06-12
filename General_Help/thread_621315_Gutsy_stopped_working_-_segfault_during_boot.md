---
title: "Gutsy stopped working - segfault during boot"
date: 2007-11-23
forum: General Help
---

### Post by corbbz on 2007-11-23
Today my Gutsy (64bit) installation stopped working.
The problems is that after I rebooted the computer, Ubuntu suddenly failed to start. I didn't change any settings/software/hardware before this problem came out. It keeps repeating the same segfault error.

dmesg:

```
[    0.000000] Linux version 2.6.22-14-generic (buildd@crested) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 21:45:15 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] Command line: root=UUID=badd6811-63d1-4414-9383-20ce7085f086 ro nolapic
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fff0000 (usable)
[    0.000000]  BIOS-e820: 000000007fff0000 - 000000007fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fff3000 - 0000000080000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f8000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 524272) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F66D0 checksum 0
[    0.000000] ACPI: RSDP 000F66D0, 0014 (r0 GBT   )
[    0.000000] ACPI: RSDT 7FFF3000, 0034 (r1 GBT    NVDAACPI 42302E31 NVDA  1010101)
[    0.000000] ACPI: FACP 7FFF3040, 0074 (r1 GBT    NVDAACPI 42302E31 NVDA  1010101)
[    0.000000] ACPI: DSDT 7FFF30C0, 50C3 (r1 GBT    NVDAACPI     1000 MSFT  100000C)
[    0.000000] ACPI: FACS 7FFF0000, 0040
[    0.000000] ACPI: SSDT 7FFF8240, 028A (r1 PTLTD  POWERNOW        1  LTP        1)
[    0.000000] ACPI: MCFG 7FFF8500, 003C (r1 GBT    NVDAACPI 42302E31 NVDA  1010101)
[    0.000000] ACPI: APIC 7FFF81C0, 007C (r1 GBT    NVDAACPI 42302E31 NVDA  1010101)
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000007fff0000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 524272) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-000000007fff0000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   524272
[    0.000000] On node 0 totalpages: 524175
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1125 pages reserved
[    0.000000]   DMA zone: 2818 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 7111 pages used for memmap
[    0.000000]   DMA32 zone: 513065 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] Intel MultiProcessor Specification v1.4
[    0.000000] MPTABLE: OEM ID: OEM00000 MPTABLE: Product ID: PROD00000000 MPTABLE: APIC at: 0xFEE00000
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] Processor #1
[    0.000000] I/O APIC #2 at 0xFEC00000.
[    0.000000] Setting APIC routing to flat
[    0.000000] Processors: 2
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:70000000)
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34696 bytes of per cpu data
[    0.000000] Built 1 zonelists.  Total pages: 515883
[    0.000000] Kernel command line: root=UUID=badd6811-63d1-4414-9383-20ce7085f086 ro nolapic
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Marking TSC unstable due to TSCs unsynchronized
[   26.987902] time.c: Detected 2612.102 MHz processor.
[   26.990549] Console: colour VGA+ 80x25
[   26.994894] Checking aperture...
[   26.994967] CPU 0: aperture @ 2f14000000 size 32 MB
[   26.995047] Aperture too small (32 MB)
[   27.000554] No AGP bridge found
[   27.014418] Memory: 2056132k/2097088k available (2274k kernel code, 40568k reserved, 1181k data, 296k init)
[   27.014586] SLUB: Genslabs=23, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   27.093897] Calibrating delay using timer specific routine.. 5228.44 BogoMIPS (lpj=10456886)
[   27.094071] Security Framework v1.0.0 initialized
[   27.094153] SELinux:  Disabled at boot.
[   27.094347] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   27.095308] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   27.095866] Mount-cache hash table entries: 256
[   27.096038] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   27.096129] CPU: L2 Cache: 1024K (64 bytes/line)
[   27.096208] CPU 0/0 -> Node 0
[   27.096280] CPU: Physical Processor ID: 0
[   27.096355] CPU: Processor Core ID: 0
[   27.096441] SMP alternatives: switching to UP code
[   27.096701] Early unpacking initramfs... done
[   27.319136] ACPI: Core revision 20070126
[   27.319252] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   27.321253] ACPI: setting ELCR to 0200 (from 8ca0)
[   27.322947] ExtINT not setup in hardware but reported by MP table
[   27.363376] Using local APIC timer interrupts.
[   27.401735] result 12558175
[   27.401806] Detected 12.558 MHz APIC timer.
[   27.401939] SMP alternatives: switching to SMP code
[   27.402079] Booting processor 1/2 APIC 0x1
[   27.412224] Initializing CPU#1
[   27.489871] Calibrating delay using timer specific routine.. 5224.42 BogoMIPS (lpj=10448858)
[   27.489877] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   27.489878] CPU: L2 Cache: 1024K (64 bytes/line)
[   27.489880] CPU 1/1 -> Node 0
[   27.489882] CPU: Physical Processor ID: 0
[   27.489883] CPU: Processor Core ID: 1
[   27.489971] AMD Athlon(tm) 64 X2 Dual Core Processor 5200+ stepping 02
[   27.493898] Brought up 2 CPUs
[   28.096750] migration_cost=249
[   28.097039] NET: Registered protocol family 16
[   28.097184] ACPI: bus type pci registered
[   28.097263] PCI: Using configuration type 1
[   28.098250] ACPI: EC: Look up EC in DSDT
[   28.103497] ACPI: Interpreter enabled
[   28.103572] ACPI: (supports S0 S1 S4 S5)
[   28.103793] ACPI: Using PIC for interrupt routing
[   28.110844] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   28.110928] PCI: Probing PCI hardware (bus 00)
[   28.111586] PCI: Transparent bridge - 0000:00:0e.0
[   28.111852] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   28.112179] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   28.172083] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   28.172628] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   28.173174] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 *15)
[   28.173628] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   28.174174] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 *7 9 10 11 14 15)
[   28.174628] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   28.175171] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   28.175716] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 *10 11 14 15)
[   28.176169] ACPI: PCI Interrupt Link [LP2P] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   28.176714] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 *10 11 14 15)
[   28.177168] ACPI: PCI Interrupt Link [LMAC] (IRQs *5 7 9 10 11 14 15)
[   28.177622] ACPI: PCI Interrupt Link [LMC1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   28.178166] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   28.178708] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   28.179253] ACPI: PCI Interrupt Link [LSMB] (IRQs *5 7 9 10 11 14 15)
[   28.179708] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 10 *11 14 15)
[   28.180162] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   28.180707] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 11 14 *15)
[   28.181162] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 10 *11 14 15)
[   28.181616] ACPI: PCI Interrupt Link [LSA2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   28.182192] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[   28.182563] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[   28.182936] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[   28.183306] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[   28.183675] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
[   28.184047] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
[   28.184416] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
[   28.184787] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
[   28.185154] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0, disabled.
[   28.185605] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0, disabled.
[   28.186058] ACPI: PCI Interrupt Link [AMC1] (IRQs 20 21 22 23) *0, disabled.
[   28.186509] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
[   28.186959] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0, disabled.
[   28.187410] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0, disabled.
[   28.187862] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0, disabled.
[   28.188313] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[   28.188764] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[   28.189215] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0, disabled.
[   28.189667] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0, disabled.
[   28.190120] ACPI: PCI Interrupt Link [ASA2] (IRQs 20 21 22 23) *0, disabled.
[   28.190497] Linux Plug and Play Support v0.97 (c) Adam Belay
[   28.190587] pnp: PnP ACPI init
[   28.190663] ACPI: bus type pnp registered
[   28.193491] pnp: PnP ACPI: found 9 devices
[   28.193567] ACPI: ACPI bus type pnp unregistered
[   28.193688] PCI: Using ACPI for IRQ routing
[   28.193766] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   28.193957] NET: Registered protocol family 8
[   28.194034] NET: Registered protocol family 20
[   28.194200] pnp: 00:01: ioport range 0x1000-0x107f has been reserved
[   28.194287] pnp: 00:01: ioport range 0x1080-0x10ff has been reserved
[   28.194373] pnp: 00:01: ioport range 0x1400-0x147f has been reserved
[   28.194460] pnp: 00:01: ioport range 0x1480-0x14ff has been reserved
[   28.194547] pnp: 00:01: ioport range 0x1800-0x187f has been reserved
[   28.194633] pnp: 00:01: ioport range 0x1880-0x18ff has been reserved
[   28.194724] pnp: 00:07: iomem range 0xf0000000-0xf7ffffff could not be reserved
[   28.194847] pnp: 00:08: iomem range 0xd6c00-0xd7fff has been reserved
[   28.194934] pnp: 00:08: iomem range 0xf0000-0xf7fff could not be reserved
[   28.195022] pnp: 00:08: iomem range 0xf8000-0xfbfff could not be reserved
[   28.195111] pnp: 00:08: iomem range 0xfc000-0xfffff could not be reserved
[   28.195423] PCI: Bridge: 0000:00:04.0
[   28.195499]   IO window: 8000-8fff
[   28.195573]   MEM window: f8000000-fbffffff
[   28.195651]   PREFETCH window: e0000000-efffffff
[   28.195730] PCI: Bridge: 0000:00:0e.0
[   28.195803]   IO window: disabled.
[   28.195878]   MEM window: fc000000-fc0fffff
[   28.195955]   PREFETCH window: disabled.
[   28.197590] PCI: Bridge: 0000:00:15.0
[   28.197665]   IO window: 9000-afff
[   28.197739]   MEM window: fc100000-fc1fffff
[   28.197816]   PREFETCH window: disabled.
[   28.197868] Time: acpi_pm clocksource has been installed.
[   28.197981] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   28.197987] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   28.197993] PCI: Setting latency timer of device 0000:00:15.0 to 64
[   28.198029] NET: Registered protocol family 2
[   28.237893] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[   28.238547] TCP established hash table entries: 262144 (order: 10, 6291456 bytes)
[   28.240939] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   28.241496] TCP: Hash tables configured (established 262144 bind 65536)
[   28.241584] TCP reno registered
[   28.253934] checking if image is initramfs... it is
[   28.691236] Freeing initrd memory: 7203k freed
[   28.694815] audit: initializing netlink socket (disabled)
[   28.694908] audit(1195835163.680:1): initialized
[   28.696497] VFS: Disk quotas dquot_6.5.1
[   28.696608] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   28.696757] io scheduler noop registered
[   28.696833] io scheduler anticipatory registered
[   28.696911] io scheduler deadline registered
[   28.697053] io scheduler cfq registered (default)
[   28.738214] Boot video device is 0000:01:00.0
[   28.738326] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   28.738342] assign_interrupt_mode Found MSI capability
[   28.738426] Allocate Port Service[0000:00:04.0:pcie00]
[   28.738480] PCI: Setting latency timer of device 0000:00:15.0 to 64
[   28.738503] assign_interrupt_mode Found MSI capability
[   28.738584] Allocate Port Service[0000:00:15.0:pcie00]
[   28.756093] Real Time Clock Driver v1.12ac
[   28.756243] Linux agpgart interface v0.102 (c) Dave Jones
[   28.756325] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   28.757164] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   28.757453] input: Macintosh mouse button emulation as /class/input/input0
[   28.757619] PNP: No PS/2 controller found. Probing ports directly.
[   28.758261] serio: i8042 KBD port at 0x60,0x64 irq 1
[   28.758344] serio: i8042 AUX port at 0x60,0x64 irq 12
[   28.758525] mice: PS/2 mouse device common for all mice
[   28.758697] TCP cubic registered
[   28.758810] NET: Registered protocol family 1
[   28.759054] /build/buildd/linux-source-2.6.22-2.6.22/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   28.759191] Freeing unused kernel memory: 296k freed
[   28.907930] AppArmor: AppArmor initialized<5>audit(1195835163.892:2):  type=1505 info="AppArmor initialized" pid=1246
[   28.912976] fuse init (API version 7.8)
[   28.916653] Failure registering capabilities with primary security module.
[   29.316708] usbcore: registered new interface driver usbfs
[   29.316811] usbcore: registered new interface driver hub
[   29.316910] usbcore: registered new device driver usb
[   29.317878] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 11
[   29.317963] PCI: setting IRQ 11 as level-triggered
[   29.317967] ACPI: PCI Interrupt 0000:00:0a.1[B] -> Link [LUB2] -> GSI 11 (level, low) -> IRQ 11
[   29.318363] PCI: Setting latency timer of device 0000:00:0a.1 to 64
[   29.318368] ehci_hcd 0000:00:0a.1: EHCI Host Controller
[   29.318577] ehci_hcd 0000:00:0a.1: new USB bus registered, assigned bus number 1
[   29.318725] ehci_hcd 0000:00:0a.1: debug port 1
[   29.318807] PCI: cache line size of 64 is not supported by device 0000:00:0a.1
[   29.318817] ehci_hcd 0000:00:0a.1: irq 11, io mem 0xfc206000
[   29.318918] ehci_hcd 0000:00:0a.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   29.318912] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.60.
[   29.319246] usb usb1: configuration #1 chosen from 1 choice
[   29.319352] hub 1-0:1.0: USB hub found
[   29.319431] hub 1-0:1.0: 10 ports detected
[   29.326396] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   29.326487] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   29.335052] SCSI subsystem initialized
[   29.381692] libata version 2.21 loaded.
[   29.384323] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   29.426296] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 5
[   29.426384] PCI: setting IRQ 5 as level-triggered
[   29.426387] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [LMAC] -> GSI 5 (level, low) -> IRQ 5
[   29.426571] PCI: Setting latency timer of device 0000:00:10.0 to 64
[   29.426578] forcedeth: using HIGHDMA
[   29.673744] usb 1-1: new high speed USB device using ehci_hcd and address 2
[   29.819058] usb 1-1: configuration #1 chosen from 1 choice
[   29.819382] hub 1-1:1.0: USB hub found
[   29.819739] hub 1-1:1.0: 4 ports detected
[   29.950020] eth0: forcedeth.c: subsystem: 01458:e000 bound to 0000:00:10.0
[   29.950146] NFORCE-MCP55: IDE controller at PCI slot 0000:00:0c.0
[   29.950247] NFORCE-MCP55: chipset revision 161
[   29.950325] NFORCE-MCP55: not 100% native mode: will probe irqs later
[   29.950414] NFORCE-MCP55: 0000:00:0c.0 (rev a1) UDMA133 controller
[   29.950503] NFORCE-MCP55: neither IDE port enabled (BIOS)
[   29.952550] sata_nv 0000:00:0d.0: version 3.4
[   29.952774] ACPI: PCI Interrupt Link [LSID] enabled at IRQ 15
[   29.952859] PCI: setting IRQ 15 as level-triggered
[   29.952862] ACPI: PCI Interrupt 0000:00:0d.0[A] -> Link [LSID] -> GSI 15 (level, low) -> IRQ 15
[   29.953245] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   29.953798] scsi0 : sata_nv
[   29.953961] scsi1 : sata_nv
[   29.954091] ata1: SATA max UDMA/133 cmd 0x000000000001b400 ctl 0x000000000001b802 bmdma 0x000000000001c400 irq 15
[   29.954226] ata2: SATA max UDMA/133 cmd 0x000000000001bc00 ctl 0x000000000001c002 bmdma 0x000000000001c408 irq 15
[   30.425692] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   30.463016] ata1.00: Host Protected Area detected:
[   30.463017] 	current size: 490232639 sectors
[   30.463018] 	native size: 490234752 sectors
[   30.463408] ata1.00: native size increased to 490234752 sectors
[   30.463495] ata1.00: ATA-7: WDC WD2500YS-01SHB1, 20.06C06, max UDMA/133
[   30.463583] ata1.00: 490234752 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   30.474617] ata1.00: configured for UDMA/133
[   30.813914] usb 1-1.1: new high speed USB device using ehci_hcd and address 6
[   30.920469] usb 1-1.1: configuration #1 chosen from 1 choice
[   30.926835] usbcore: registered new interface driver libusual
[   30.929301] Initializing USB Mass Storage driver...
[   30.929434] scsi2 : SCSI emulation for USB Mass Storage devices
[   30.929560] usb-storage: device found at 6
[   30.929561] usb-storage: waiting for device to settle before scanning
[   30.929571] usbcore: registered new interface driver usb-storage
[   30.929663] USB Mass Storage support registered.
[   30.945684] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   30.965846] ata2.00: Host Protected Area detected:
[   30.965848] 	current size: 490232639 sectors
[   30.965848] 	native size: 490234752 sectors
[   30.966238] ata2.00: native size increased to 490234752 sectors
[   30.966324] ata2.00: ATA-7: WDC WD2500YS-01SHB1, 20.06C06, max UDMA/133
[   30.966412] ata2.00: 490234752 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   30.977960] ata2.00: configured for UDMA/133
[   30.978129] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500YS-01S 20.0 PQ: 0 ANSI: 5
[   30.978530] scsi 1:0:0:0: Direct-Access     ATA      WDC WD2500YS-01S 20.0 PQ: 0 ANSI: 5
[   30.978925] ACPI: PCI Interrupt Link [LFID] enabled at IRQ 11
[   30.979009] ACPI: PCI Interrupt 0000:00:0d.1[B] -> Link [LFID] -> GSI 11 (level, low) -> IRQ 11
[   30.979417] PCI: Setting latency timer of device 0000:00:0d.1 to 64
[   30.979487] scsi3 : sata_nv
[   30.979614] scsi4 : sata_nv
[   30.979742] ata3: SATA max UDMA/133 cmd 0x000000000001c800 ctl 0x000000000001cc02 bmdma 0x000000000001d800 irq 11
[   30.979878] ata4: SATA max UDMA/133 cmd 0x000000000001d000 ctl 0x000000000001d402 bmdma 0x000000000001d808 irq 11
[   31.449627] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   31.613722] ata3.00: ATAPI: ASUS    DRW-1814BLT, 1.04, max UDMA/66
[   31.789708] ata3.00: configured for UDMA/66
[   32.105571] ata4: SATA link down (SStatus 0 SControl 300)
[   32.116511] scsi 3:0:0:0: CD-ROM            ASUS     DRW-1814BLT      1.04 PQ: 0 ANSI: 5
[   32.117154] ACPI: PCI Interrupt Link [LUBA] enabled at IRQ 10
[   32.117238] PCI: setting IRQ 10 as level-triggered
[   32.117242] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LUBA] -> GSI 10 (level, low) -> IRQ 10
[   32.117590] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[   32.117595] ohci_hcd 0000:00:0a.0: OHCI Host Controller
[   32.117914] ohci_hcd 0000:00:0a.0: new USB bus registered, assigned bus number 2
[   32.118052] ohci_hcd 0000:00:0a.0: irq 10, io mem 0xfc202000
[   32.179881] usb usb2: configuration #1 chosen from 1 choice
[   32.180098] hub 2-0:1.0: USB hub found
[   32.180178] hub 2-0:1.0: 10 ports detected
[   32.286127] ACPI: PCI Interrupt Link [LNK3] enabled at IRQ 15
[   32.286214] ACPI: PCI Interrupt 0000:02:0e.0[A] -> Link [LNK3] -> GSI 15 (level, low) -> IRQ 15
[   32.336522] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[15]  MMIO=[fc004000-fc0047ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   32.336729] ahci 0000:03:00.0: version 2.2
[   32.336973] ACPI: PCI Interrupt Link [LNK8] enabled at IRQ 10
[   32.337060] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LNK8] -> GSI 10 (level, low) -> IRQ 10
[   32.601545] usb 2-7: new low speed USB device using ohci_hcd and address 2
[   32.827594] usb 2-7: configuration #1 chosen from 1 choice
[   33.137501] usb 2-9: new full speed USB device using ohci_hcd and address 3
[   33.341517] ahci 0000:03:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[   33.341646] ahci 0000:03:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[   33.341739] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   33.341850] scsi5 : ahci
[   33.342114] scsi6 : ahci
[   33.342317] ata5: SATA max UDMA/133 cmd 0xffffc20000aac100 ctl 0x0000000000000000 bmdma 0x0000000000000000 irq 10
[   33.342453] ata6: SATA max UDMA/133 cmd 0xffffc20000aac180 ctl 0x0000000000000000 bmdma 0x0000000000000000 irq 10
[   33.345556] usb 2-9: configuration #1 chosen from 1 choice
[   33.609558] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0000000000000000]
[   33.653468] usb 2-10: new full speed USB device using ohci_hcd and address 4
[   33.657471] ata5: SATA link down (SStatus 0 SControl 300)
[   33.867509] usb 2-10: configuration #1 chosen from 1 choice
[   33.873575] usbcore: registered new interface driver hiddev
[   33.880610] input: Monterey USB Keyboard as /class/input/input1
[   33.880705] input: USB HID v1.00 Keyboard [Monterey USB Keyboard] on usb-0000:00:0a.0-7
[   33.898474] input: Monterey USB Keyboard as /class/input/input2
[   33.898587] input,hiddev96: USB HID v1.00 Device [Monterey USB Keyboard] on usb-0000:00:0a.0-7
[   33.907467] input: Logitech Logitech USB Headset as /class/input/input3
[   33.907557] input: USB HID v1.00 Device [Logitech Logitech USB Headset] on usb-0000:00:0a.0-9
[   33.911546] input: Logitech USB Gaming Mouse as /class/input/input4
[   33.911646] input: USB HID v1.11 Mouse [Logitech USB Gaming Mouse] on usb-0000:00:0a.0-10
[   33.921456] hiddev97: USB HID v1.11 Device [Logitech USB Gaming Mouse] on usb-0000:00:0a.0-10
[   33.921643] usbcore: registered new interface driver usbhid
[   33.921727] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   33.969450] ata6: SATA link down (SStatus 0 SControl 300)
[   33.970111] PCI: Enabling device 0000:03:00.1 (0000 -> 0001)
[   33.970428] ACPI: PCI Interrupt Link [LNK5] enabled at IRQ 7
[   33.970512] PCI: setting IRQ 7 as level-triggered
[   33.970516] ACPI: PCI Interrupt 0000:03:00.1[B] -> Link [LNK5] -> GSI 7 (level, low) -> IRQ 7
[   33.970726] PCI: Setting latency timer of device 0000:03:00.1 to 64
[   33.970862] scsi7 : pata_jmicron
[   33.970983] scsi8 : pata_jmicron
[   33.971075] ata7: PATA max UDMA/100 cmd 0x0000000000019000 ctl 0x0000000000019402 bmdma 0x000000000001a000 irq 7
[   33.971210] ata8: PATA max UDMA/100 cmd 0x0000000000019800 ctl 0x0000000000019c02 bmdma 0x000000000001a008 irq 7
[   33.975631] sd 0:0:0:0: [sda] 490234752 512-byte hardware sectors (251000 MB)
[   33.975732] sd 0:0:0:0: [sda] Write Protect is off
[   33.975814] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   33.975825] sd 0:0:0:0: [sda] Write cache: enabled, read 000:00:0a.1[B] -> Link [LUB2] -> GSI 11 (level, low) -> IRQ 11
Nov 23 19:26:35 Corbbz-Ubuntu kernel: [   45.465294] usb usb1: root hub lost power or was reset
Nov 23 19:26:35 Corbbz-Ubuntu kernel: [   45.465299] ehci_hcd 0000:00:0a.1: debug port 1
Nov 23 19:26:35 Corbbz-Ubuntu kernel: [   45.465324] ACPI: PCI Interrupt 0000:00:0d.0[A] -> Link [LSID] -> GSI 15 (level, low) -> IRQ 15
Nov 23 19:26:35 Corbbz-Ubuntu kernel: [   45.465346] ACPI: PCI Interrupt 0000:00:0d.1[B] -> Link [LFID] -> GSI 11 (level, low) -> IRQ 11
Nov 23 19:26:35 Corbbz-Ubuntu kernel: [   45.465412] NVRM: RmPowerManagement: 4
Nov 23 19:26:35 Corbbz-Ubuntu kernel: [   45.585369] ata4: SATA link down (SStatus 0 SControl 300)
Nov 23 19:26:35 Corbbz-Ubuntu kernel: [   45.592233] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[15]  MMIO=[fc004000-fc0047ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Nov 23 19:26:35 Corbbz-Ubuntu kernel: [   45.592268] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LNK8] -> GSI 10 (level, low) -> IRQ 10
Nov 23 19:26:35 Corbbz-Ubuntu kernel: [   45.592297] ACPI: PCI Interrupt 0000:03:00.1[B] -> Link [LNK5] -> GSI 7 (level, low) -> IRQ 7
Nov 23 19:26:35 Corbbz-Ubuntu kernel: [   45.592460] sd 0:0:0:0: [sda] Starting disk
Nov 23 19:26:35 Corbbz-Ubuntu kernel: [   45.646847] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Nov 23 19:26:35 Corbbz-Ubuntu kernel: [   45.646890] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Nov 23 19:26:35 Corbbz-Ubuntu kernel: [   45.646929] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Nov 23 19:26:35 Corbbz-Ubuntu kernel: [   45.665629] ata1.00: configured for UDMA/133
Nov 23 19:26:35 Corbbz-Ubuntu kernel: [   45.668510] ata2.00: configured for UDMA/133
Nov 23 19:26:35 Corbbz-Ubuntu kernel: [   45.668885] sd 0:0:0:0: [sda] 490234752 512-byte hardware sectors (251000 MB)
Nov 23 19:26:35 Corbbz-Ubuntu kernel: [   45.668895] sd 1:0:0:0: [sdb] Starting disk
Nov 23 19:26:35 Corbbz-Ubuntu kernel: [   45.668921] sd 0:0:0:0: [sda] Write Protect is off
Nov 23 19:26:35 Corbbz-Ubuntu kernel: [   45.668934] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 23 19:26:35 Corbbz-Ubuntu kernel: [   45.680114] sd 1:0:0:0: [sdb] 490234752 512-byte hardware sectors (251000 MB)
Nov 23 19:26:35 Corbbz-Ubuntu kernel: [   45.680120] sd 1:0:0:0: [sdb] Write Protect is off
Nov 23 19:26:35 Corbbz-Ubuntu kernel: [   45.680132] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 23 19:26:35 Corbbz-Ubuntu kernel: [   45.685317] usb usb2: root hub lost power or was reset
Nov 23 19:26:35 Corbbz-Ubuntu kernel: [   45.713754] Restarting tasks ... <6>usb 1-1: USB disconnect, address 2
Nov 23 19:26:35 Corbbz-Ubuntu kernel: [   45.713842] usb 1-1.1: USB disconnect, address 6
Nov 23 19:26:35 Corbbz-Ubuntu kernel: [   45.716052] done.
Nov 23 19:26:35 Corbbz-Ubuntu kernel: [   45.716066] swsusp: Basic memory bitmaps freed
Nov 23 19:26:35 Corbbz-Ubuntu kernel: [   45.720971] ata3: failed to recover some devices, retrying in 5 secs
Nov 23 19:26:35 Corbbz-Ubuntu kernel: [   45.722228] ata7: SATA link down (SStatus 0 SControl 300)
Nov 23 19:26:35 Corbbz-Ubuntu kernel: [   45.722237] ata8: SATA link down (SStatus 0 SControl 300)
Nov 23 19:26:35 Corbbz-Ubuntu kernel: [   45.785277] modprobe[28926]: segfault at 00002ab3ba73ea3c rip 00002ab3ba726080 rsp 00007ffff0389620 error 4
Nov 23 19:26:35 Corbbz-Ubuntu kernel: [   45.786192] modprobe[28928]: segfault at 00002aff81d23a3c rip 00002aff81d0b080 rsp 00007fff28da5040 error 4
Nov 23 19:26:35 Corbbz-Ubuntu kernel: [   45.786431] laptop_mode[28919]: segfault at 00002b539613ea3c rip 00002b5396126080 rsp 00007fff14988fe0 error 4
Nov 23 19:26:35 Corbbz-Ubuntu kernel: [   45.833481] usb 1-1: new high speed USB device using ehci_hcd and address 7
Nov 23 19:26:35 Corbbz-Ubuntu kernel: [   45.851507] apport[28960]: segfault at 00002ae138758a3c rip 00002ae138740080 rsp 00007fff7236f590 error 4
Nov 23 19:26:35 Corbbz-Ubuntu kernel: [   45.851821] apport[28962]: segfault at 00002b2816c1ea3c rip 00002b2816c06080 rsp 00007fff93eac0d0 error 4
Nov 23 19:26:35 Corbbz-Ubuntu kernel: [   45.852114] apport[28967]: segfault at 00002b5230f39a3c rip 00002b5230f21080 rsp 00007fff79b90db0 error 4
Nov 23 19:26:35 Corbbz-Ubuntu kernel: [   45.852397] apport[28964]: segfault at 00002ba2d86baa3c rip 00002ba2d86a2080 rsp 00007fffd240d630 error 4
```

The strange thing is, that this really came out of nowhere.
Any ideas on how to fix this, all help appreciated!

---

### Post by corbbz on 2007-11-24
Bumb. nothing?

I guess its worth to mention that Vista still works just fine, so does Ubuntu live-CD. From the live-CD I can still access the Gutsy installation partitions without any problems.

---

### Post by Regenerate on 2007-11-26
Same problem here. I also have the "SATA link down (SStatus 0 SControl 300)" notion... :(

---

### Post by MBro on 2007-12-10
I would also like to confirm this.  I have no clue as to how to fix it either.

Gutsy, 32 bit, athalon xp, nforce2 mother board.

---

