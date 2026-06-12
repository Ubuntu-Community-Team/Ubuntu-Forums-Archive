---
title: "Everything seams (is) to be slow."
date: 2007-11-13
forum: General Help
---

### Post by vampire666eng on 2007-11-13
I installed uBuntu 7.10, and from the start the system isn't really responsive.
I mean the login (after I entered username and password) takes a lot of time (far more then 7.04), the programs takes a lot of time loading...even selecting options as "print" a document in OpenOffice or starting the terminal takes ages.

The hard disk is not even working hard during all this...it seams that the system is in idle and then all of a sudden (after some time), the program/process starts.

My specs are:
AMD64 3000+
2GB RAM
6600GT 128MB RAM

Summering up, my problem is that the system is slow:
- logging
- running any program and process.

Thanks a bunch.

---

### Post by taurus on 2007-11-13
Are you running x86 or x86_64 version?  Do you have compiz running in Gnome?

---

### Post by vampire666eng on 2007-11-13
I'm running x86 version (Standard personal computer (x86 architecture, PentiumTM, CeleronTM, AthlonTM, SempronTM)) and compiz (third option "3.extra") running in Gnome.

---

### Post by vampire666eng on 2007-11-13
Is there a way I can see the log (and post it here) to see if we (ehm...you guys, as I'm a linux n00b) can find out what is the problem?

EDIT: Iìm not sure if this is of any help but I just wanted to add that I have static IP and the router has DHCP disabled...

EDIT2: I wasn't effected by this on 7.04

---

### Post by vampire666eng on 2007-11-13
This is the time I hae to wait before having uBuntu ready:

- From selecting uBuntu in Grub ---> to uBuntu disaplaying login username: **1min 2sec (1:02)**

- From selecting pw login to complete desktop ---> **1min 35sec (1:35)**

Total time: **2min 37sec (2:37)** (obviously not considering the time I spend digiting username and password)

I find it a "bit" too much considering my specs.

EDIT; I tried other times and the total time is 2:50.

EDIT2: added bootchart (that should take in consideration only the things before the login)...isn't that awful? :(

---

### Post by gmaniac on 2007-11-13
Could you post the output of dmesg it could be more helpful

---

### Post by vampire666eng on 2007-11-13
Sure thing (thanks for the reply).
Here you go:

```
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 1151MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f38c0
[    0.000000] Entering add_active_range(0, 0, 524272) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   524272
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   524272
[    0.000000] On node 0 totalpages: 524272
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2303 pages used for memmap
[    0.000000]   HighMem zone: 292593 pages, LIFO batch:31
[    0.000000] DMI 2.2 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7F00 checksum 0
[    0.000000] ACPI: RSDP 000F7F00, 0014 (r0 Nvidia)
[    0.000000] ACPI: RSDT 7FFF3040, 0030 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 7FFF30C0, 0074 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 7FFF3180, 61DF (r1 NVIDIA AWRDACPI     1000 MSFT  100000E)
[    0.000000] ACPI: FACS 7FFF0000, 0040
[    0.000000] ACPI: MCFG 7FFF9480, 003C (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: APIC 7FFF93C0, 006E (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:15 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
[    0.000000] Built 1 zonelists.  Total pages: 520177
[    0.000000] Kernel command line: root=UUID=dfdd5b47-b217-41e6-be2c-bed1e6a2281e ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1809.313 MHz processor.
[   21.631021] spurious 8259A interrupt: IRQ7.
[   21.632888] Console: colour VGA+ 80x25
[   21.633231] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   21.633608] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   21.701077] Memory: 2067704k/2097088k available (2015k kernel code, 28136k reserved, 916k data, 364k init, 1179584k highmem)
[   21.701088] virtual kernel memory layout:
[   21.701089]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   21.701091]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   21.701092]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   21.701093]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   21.701095]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   21.701096]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[   21.701097]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[   21.701100] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   21.701136] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   21.781020] Calibrating delay using timer specific routine.. 3620.90 BogoMIPS (lpj=7241808)
[   21.781045] Security Framework v1.0.0 initialized
[   21.781051] SELinux:  Disabled at boot.
[   21.781064] Mount-cache hash table entries: 512
[   21.781174] CPU: After generic identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000000 00000000 00000001
[   21.781183] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   21.781185] CPU: L2 Cache: 512K (64 bytes/line)
[   21.781188] CPU: After all inits, caps: 078bfbff e3d3fbff 00000000 00000410 00000000 00000000 00000001
[   21.781198] Compat vDSO mapped to ffffe000.
[   21.781208] Checking 'hlt' instruction... OK.
[   21.797113] SMP alternatives: switching to UP code
[   21.797278] Freeing SMP alternatives: 11k freed
[   21.797531] Early unpacking initramfs... done
[   22.114468] ACPI: Core revision 20070126
[   22.114540] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   22.117723] CPU0: AMD Athlon(tm) 64 Processor 3000+ stepping 00
[   22.117739] Total of 1 processors activated (3620.90 BogoMIPS).
[   22.117875] ENABLING IO-APIC IRQs
[   22.118057] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[   22.264259] Brought up 1 CPUs
[   22.264359] Booting paravirtualized kernel on bare hardware
[   22.264398] Time: 20:41:29  Date: 10/13/107
[   22.264417] NET: Registered protocol family 16
[   22.264482] EISA bus registered
[   22.264491] ACPI: bus type pci registered
[   22.269016] PCI: PCI BIOS revision 3.00 entry at 0xfa950, last bus=5
[   22.269018] PCI: Using configuration type 1
[   22.269020] Setting up standard PCI resources
[   22.272764] ACPI: EC: Look up EC in DSDT
[   22.278418] ACPI: Interpreter enabled
[   22.278420] ACPI: (supports S0 S3 S4 S5)
[   22.278434] ACPI: Using IOAPIC for interrupt routing
[   22.287853] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   22.287858] PCI: Probing PCI hardware (bus 00)
[   22.288229] PCI: Transparent bridge - 0000:00:09.0
[   22.288472] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   22.288736] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   22.354199] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[   22.354378] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   22.354556] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[   22.354733] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   22.354910] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   22.355088] ACPI: PCI Interrupt Link [LUBA] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[   22.355264] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   22.355442] ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[   22.355620] ACPI: PCI Interrupt Link [LACI] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   22.355796] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   22.355974] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[   22.356159] ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   22.356336] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   22.356522] ACPI: PCI Interrupt Link [LSID] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[   22.356710] ACPI: PCI Interrupt Link [LFID] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   22.356897] ACPI: PCI Interrupt Link [LPCA] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   22.357093] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0
[   22.357282] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[   22.357470] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0
[   22.357658] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[   22.357785] ACPI: PCI Interrupt Link [APC5] (IRQs *16), disabled.
[   22.357979] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
[   22.358173] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
[   22.358370] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
[   22.358563] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0
[   22.358756] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
[   22.358950] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[   22.359143] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
[   22.359337] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[   22.359537] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[   22.359738] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0
[   22.359938] ACPI: PCI Interrupt Link [APCP] (IRQs 20 21 22 23) *0, disabled.
[   22.360036] Linux Plug and Play Support v0.97 (c) Adam Belay
[   22.360044] pnp: PnP ACPI init
[   22.360054] ACPI: bus type pnp registered
[   22.365280] pnp: PnP ACPI: found 15 devices
[   22.365282] ACPI: ACPI bus type pnp unregistered
[   22.365285] PnPBIOS: Disabled by ACPI PNP
[   22.365326] PCI: Using ACPI for IRQ routing
[   22.365330] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   22.365354] PCI: Cannot allocate resource region 3 of device 0000:05:00.0
[   22.416079] NET: Registered protocol family 8
[   22.416081] NET: Registered protocol family 20
[   22.416132] pnp: 00:00: ioport range 0x4000-0x407f has been reserved
[   22.416135] pnp: 00:00: ioport range 0x4080-0x40ff has been reserved
[   22.416138] pnp: 00:00: ioport range 0x4400-0x447f has been reserved
[   22.416140] pnp: 00:00: ioport range 0x4480-0x44ff has been reserved
[   22.416143] pnp: 00:00: ioport range 0x4800-0x487f has been reserved
[   22.416146] pnp: 00:00: ioport range 0x4880-0x48ff has been reserved
[   22.416157] pnp: 00:0d: iomem range 0xe0000000-0xefffffff could not be reserved
[   22.416161] pnp: 00:0e: iomem range 0xd1800-0xd3fff has been reserved
[   22.416164] pnp: 00:0e: iomem range 0xf0000-0xf7fff could not be reserved
[   22.416167] pnp: 00:0e: iomem range 0xf8000-0xfbfff could not be reserved
[   22.416170] pnp: 00:0e: iomem range 0xfc000-0xfffff could not be reserved
[   22.419973] Time: tsc clocksource has been installed.
[   22.446345] PCI: Bridge: 0000:00:09.0
[   22.446347]   IO window: a000-afff
[   22.446350]   MEM window: fe900000-fe9fffff
[   22.446353]   PREFETCH window: fea00000-feafffff
[   22.446356] PCI: Bridge: 0000:00:0b.0
[   22.446358]   IO window: 9000-9fff
[   22.446361]   MEM window: fe800000-fe8fffff
[   22.446363]   PREFETCH window: fe700000-fe7fffff
[   22.446366] PCI: Bridge: 0000:00:0c.0
[   22.446368]   IO window: 8000-8fff
[   22.446371]   MEM window: fe600000-fe6fffff
[   22.446373]   PREFETCH window: fe500000-fe5fffff
[   22.446376] PCI: Bridge: 0000:00:0d.0
[   22.446378]   IO window: 7000-7fff
[   22.446380]   MEM window: fe400000-fe4fffff
[   22.446383]   PREFETCH window: fe300000-fe3fffff
[   22.446390] PCI: Bridge: 0000:00:0e.0
[   22.446392]   IO window: 6000-6fff
[   22.446395]   MEM window: f4000000-fbffffff
[   22.446397]   PREFETCH window: d0000000-dfffffff
[   22.446404] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   22.446411] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   22.446416] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   22.446422] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   22.446427] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   22.446438] NET: Registered protocol family 2
[   22.483901] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   22.484006] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   22.485116] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   22.485507] TCP: Hash tables configured (established 131072 bind 65536)
[   22.485509] TCP reno registered
[   22.495965] checking if image is initramfs... it is
[   22.947108] Switched to high resolution mode on CPU 0
[   23.116601] Freeing initrd memory: 7055k freed
[   23.116917] audit: initializing netlink socket (disabled)
[   23.116928] audit(1194986489.120:1): initialized
[   23.116982] highmem bounce pool size: 64 pages
[   23.118417] VFS: Disk quotas dquot_6.5.1
[   23.118459] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   23.118534] io scheduler noop registered
[   23.118536] io scheduler anticipatory registered
[   23.118538] io scheduler deadline registered
[   23.118550] io scheduler cfq registered (default)
[   23.118578] PCI: Found disabled HT MSI Mapping on 0000:00:0b.0
[   23.118585] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[   23.118590] PCI: Found disabled HT MSI Mapping on 0000:00:0c.0
[   23.118597] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[   23.118602] PCI: Found disabled HT MSI Mapping on 0000:00:0d.0
[   23.118609] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[   23.118614] PCI: Found disabled HT MSI Mapping on 0000:00:0e.0
[   23.118621] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[   23.118628] Boot video device is 0000:05:00.0
[   23.118689] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   23.118706] assign_interrupt_mode Found MSI capability
[   23.118708] Allocate Port Service[0000:00:0b.0:pcie00]
[   23.118761] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   23.118777] assign_interrupt_mode Found MSI capability
[   23.118779] Allocate Port Service[0000:00:0c.0:pcie00]
[   23.118825] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   23.118841] assign_interrupt_mode Found MSI capability
[   23.118843] Allocate Port Service[0000:00:0d.0:pcie00]
[   23.118889] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   23.118904] assign_interrupt_mode Found MSI capability
[   23.118906] Allocate Port Service[0000:00:0e.0:pcie00]
[   23.118994] isapnp: Scanning for PnP cards...
[   23.470988] isapnp: No Plug & Play device found
[   23.489694] Real Time Clock Driver v1.12ac
[   23.489775] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   23.489854] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   23.489974] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   23.490374] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   23.490548] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   23.491069] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   23.491206] input: Macintosh mouse button emulation as /class/input/input0
[   23.491263] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   23.494381] serio: i8042 KBD port at 0x60,0x64 irq 1
[   23.494386] serio: i8042 AUX port at 0x60,0x64 irq 12
[   23.494520] mice: PS/2 mouse device common for all mice
[   23.494602] EISA: Probing bus 0 at eisa.0
[   23.494615] Cannot allocate resource for EISA slot 4
[   23.494620] Cannot allocate resource for EISA slot 6
[   23.494622] Cannot allocate resource for EISA slot 7
[   23.494624] Cannot allocate resource for EISA slot 8
[   23.494626] EISA: Detected 0 cards.
[   23.494704] TCP cubic registered
[   23.494715] NET: Registered protocol family 1
[   23.494733] Using IPI No-Shortcut mode
[   23.494881]   Magic number: 15:262:700
[   23.495220] Freeing unused kernel memory: 364k freed
[   23.538046] input: AT Translated Set 2 keyboard as /class/input/input1
[   24.740800] AppArmor: AppArmor initialized<5>audit(1194986490.620:2):  type=1505 info="AppArmor initialized" pid=1363
[   24.747067] fuse init (API version 7.8)
[   24.751737] Failure registering capabilities with primary security module.
[   24.755942] ACPI: Fan [FAN] (on)
[   24.760702] ACPI: Processor [CPU0] (supports 8 throttling states)
[   24.761842] ACPI: Thermal Zone [THRM] (39 C)
[   25.340841] usbcore: registered new interface driver usbfs
[   25.340862] usbcore: registered new interface driver hub
[   25.340881] usbcore: registered new device driver usb
[   25.341480] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   25.341833] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 23
[   25.341840] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 23 (level, low) -> IRQ 16
[   25.341851] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   25.341854] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   25.341969] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[   25.341983] ohci_hcd 0000:00:02.0: irq 16, io mem 0xfebff000
[   25.370519] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   25.370524] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   25.390946] SCSI subsystem initialized
[   25.395282] libata version 2.21 loaded.
[   25.402532] usb usb1: configuration #1 chosen from 1 choice
[   25.402556] hub 1-0:1.0: USB hub found
[   25.402565] hub 1-0:1.0: 10 ports detected
[   25.503070] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
[   25.503080] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCL] -> GSI 22 (level, low) -> IRQ 17
[   25.503089] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   25.503092] ehci_hcd 0000:00:02.1: EHCI Host Controller
[   25.503119] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[   25.503142] ehci_hcd 0000:00:02.1: debug port 1
[   25.503145] PCI: cache line size of 64 is not supported by device 0000:00:02.1
[   25.503154] ehci_hcd 0000:00:02.1: irq 17, io mem 0xfebfe000
[   25.503159] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   25.503218] usb usb2: configuration #1 chosen from 1 choice
[   25.503242] hub 2-0:1.0: USB hub found
[   25.503248] hub 2-0:1.0: 10 ports detected
[   25.527794] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.60.
[   25.606568] NFORCE-CK804: IDE controller at PCI slot 0000:00:06.0
[   25.606585] NFORCE-CK804: chipset revision 162
[   25.606587] NFORCE-CK804: not 100% native mode: will probe irqs later
[   25.606591] NFORCE-CK804: BIOS didn't set cable bits correctly. Enabling workaround.
[   25.606593] NFORCE-CK804: BIOS didn't set cable bits correctly. Enabling workaround.
[   25.606598] NFORCE-CK804: 0000:00:06.0 (rev a2) UDMA133 controller
[   25.606604]     ide0: BM-DMA at 0xe800-0xe807, BIOS settings: hda:DMA, hdb:DMA
[   25.606612]     ide1: BM-DMA at 0xe808-0xe80f, BIOS settings: hdc:DMA, hdd:DMA
[   25.606619] Probing IDE interface ide0...
[   25.666299] FDC 0 is a post-1991 82077
[   26.005748] hda: LITE-ON DVD SOHD-167T, ATAPI CD/DVD-ROM drive
[   26.285252] hdb: MAXTOR 6L080J4, ATA DISK drive
[   26.341478] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   26.356529] Probing IDE interface ide1...
[   27.091832] hdc: PIONEER DVD-RW DVR-111L, ATAPI CD/DVD-ROM drive
[   27.874456] hdd: HL-DT-ST DVDRAM GSA-4120B, ATAPI CD/DVD-ROM drive
[   27.931840] ide1 at 0x170-0x177,0x376 on irq 15
[   27.940988] sata_nv 0000:00:07.0: version 3.4
[   27.941381] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 21
[   27.941389] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [APSI] -> GSI 21 (level, low) -> IRQ 18
[   27.941394] sata_nv 0000:00:07.0: Using ADMA mode
[   27.941427] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   27.941517] scsi0 : sata_nv
[   27.941728] scsi1 : sata_nv
[   27.941881] ata1: SATA max UDMA/133 cmd 0xf883e480 ctl 0xf883e4a0 bmdma 0x0001d400 irq 18
[   27.941885] ata2: SATA max UDMA/133 cmd 0xf883e580 ctl 0xf883e5a0 bmdma 0x0001d408 irq 18
[   27.962711] hda: ATAPI 48X DVD-ROM drive, 512kB Cache, UDMA(33)
[   27.962718] Uniform CD-ROM driver Revision: 3.20
[   27.963839] hdb: max request size: 128KiB
[   27.963980] hdb: 156355584 sectors (80054 MB) w/1819KiB Cache, CHS=65535/16/63, UDMA(133)
[   27.964149] hdb: cache flushes supported
[   27.964172]  hdb:<6>hdc: ATAPI 40X DVD-ROM DVD-R-RAM CD-R/RW drive, 2000kB Cache, UDMA(66)
[   27.971141]  hdb1 hdb2 hdb3 hdb4 <<6>hdd: ATAPI 40X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   27.991274]  hdb5 >
[   28.348066] Attempting manual resume
[   28.348069] swsusp: Resume From Partition 3:67
[   28.348071] PM: Checking swsusp image.
[   28.356989] PM: Resume from disk failed.
[   28.385862] kjournald starting.  Commit interval 5 seconds
[   28.385872] EXT3-fs: mounted filesystem with ordered data mode.
[   28.405485] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   28.421800] ata1.00: ATA-7: HDS724040KLSA80, KFAOAC6A, max UDMA/133
[   28.421804] ata1.00: 781422768 sectors, multi 16: LBA48 
[   28.445757] ata1.00: configured for UDMA/133
[   28.912567] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   28.920752] ata2.00: ATA-6: ST3120827AS, 3.42, max UDMA/133
[   28.920755] ata2.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   28.936708] ata2.00: configured for UDMA/133
[   28.936785] scsi 0:0:0:0: Direct-Access     ATA      HDS724040KLSA80  KFAO PQ: 0 ANSI: 5
[   28.936792] ata1: bounce limit 0xFFFFFFFFFFFFFFFF, segment boundary 0xFFFFFFFF, hw segs 61
[   28.936872] scsi 1:0:0:0: Direct-Access     ATA      ST3120827AS      3.42 PQ: 0 ANSI: 5
[   28.936877] ata2: bounce limit 0xFFFFFFFFFFFFFFFF, segment boundary 0xFFFFFFFF, hw segs 61
[   28.937302] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 20
[   28.937310] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [APSJ] -> GSI 20 (level, low) -> IRQ 19
[   28.937314] sata_nv 0000:00:08.0: Using ADMA mode
[   28.937348] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   28.937415] scsi2 : sata_nv
[   28.937446] scsi3 : sata_nv
[   28.937497] ata3: SATA max UDMA/133 cmd 0xf8850480 ctl 0xf88504a0 bmdma 0x0001c000 irq 19
[   28.937500] ata4: SATA max UDMA/133 cmd 0xf8850580 ctl 0xf88505a0 bmdma 0x0001c008 irq 19
[   29.247972] ata3: SATA link down (SStatus 0 SControl 300)
[   29.559424] ata4: SATA link down (SStatus 0 SControl 300)
[   29.559865] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
[   29.559869] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [APCH] -> GSI 23 (level, low) -> IRQ 16
[   29.559875] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[   29.559881] forcedeth: using HIGHDMA
[   30.078983] eth0: forcedeth.c: subsystem: 0105b:0ca2 bound to 0000:00:0a.0
[   36.386302] NET: Registered protocol family 10
[   36.386379] lo: Disabled Privacy Extensions
[   37.493635] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x4c00
[   37.493660] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x4d00
[   37.927546] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 22
[   37.927551] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [APCJ] -> GSI 22 (level, low) -> IRQ 17
[   37.927568] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   38.248154] intel8x0_measure_ac97_clock: measured 54739 usecs
[   38.248158] intel8x0: clocking to 46919
[   38.336731] sd 0:0:0:0: [sda] 781422768 512-byte hardware sectors (400088 MB)
[   38.336743] sd 0:0:0:0: [sda] Write Protect is off
[   38.336746] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   38.336759] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   38.336807] sd 0:0:0:0: [sda] 781422768 512-byte hardware sectors (400088 MB)
[   38.336815] sd 0:0:0:0: [sda] Write Protect is off
[   38.336817] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   38.336829] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   38.336834]  sda: sda1 < sda5 >
[   38.610770] sd 0:0:0:0: [sda] Attached SCSI disk
[   38.610853] sd 1:0:0:0: [sdb] 234441648 512-byte hardware sectors (120034 MB)
[   38.610864] sd 1:0:0:0: [sdb] Write Protect is off
[   38.610866] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   38.610879] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   38.610916] sd 1:0:0:0: [sdb] 234441648 512-byte hardware sectors (120034 MB)
[   38.610924] sd 1:0:0:0: [sdb] Write Protect is off
[   38.610926] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   38.610938] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   38.610941]  sdb:<6>pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   38.626413] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   38.831161]  sdb1 sdb2 < sdb5 >
[   38.983033] sd 1:0:0:0: [sdb] Attached SCSI disk
[   39.108106] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   39.108136] sd 1:0:0:0: Attached scsi generic sg1 type 0
[   39.186399] Linux agpgart interface v0.102 (c) Dave Jones
[   39.227931] nvidia: module license 'NVIDIA' taints kernel.
[   39.546710] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[   39.546720] ACPI: PCI Interrupt 0000:05:00.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 20
[   39.546728] PCI: Setting latency timer of device 0000:05:00.0 to 64
[   39.546948] NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.19  Wed Sep 12 14:12:24 PDT 2007
[   40.019783] input: ImExPS/2 Generic Explorer Mouse as /class/input/input2
[   40.022875] parport_pc 00:0a: reported by Plug and Play ACPI
[   40.022920] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   40.024985] input: PC Speaker as /class/input/input3
[   40.944341] lp0: using parport0 (interrupt-driven).
[   40.991809] Adding 2931852k swap on /dev/hdb3.  Priority:-1 extents:1 across:2931852k
[   41.373075] EXT3 FS on hdb2, internal journal
[   41.927834] kjournald starting.  Commit interval 5 seconds
[   41.928073] EXT3 FS on hdb5, internal journal
[   41.928077] EXT3-fs: mounted filesystem with ordered data mode.
[   43.349586] No dock devices found.
[   43.424295] input: Power Button (FF) as /class/input/input4
[   43.428449] ACPI: Power Button (FF) [PWRF]
[   43.462571] input: Power Button (CM) as /class/input/input5
[   43.466687] ACPI: Power Button (CM) [PWRB]
[   43.847390] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3000+ processors (version 2.00.00)
[   43.847421] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x6
[   43.847424] powernow-k8:    1 : fid 0x2 (1000 MHz), vid 0x12
[   46.649385] eth0: no IPv6 routers present
[   54.981972] ppdev: user-space parallel port driver
[   65.157731] audit(1194982931.908:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=6751 profile="/usr/sbin/cupsd"
[   75.196486] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   75.196491] apm: overridden by ACPI.
[   75.384560] Failure registering capabilities with primary security module.
[   75.553991] Bluetooth: Core ver 2.11
[   75.554275] NET: Registered protocol family 31
[   75.554278] Bluetooth: HCI device and connection manager initialized
[   75.554281] Bluetooth: HCI socket layer initialized
[   75.565649] Bluetooth: L2CAP ver 2.8
[   75.565653] Bluetooth: L2CAP socket layer initialized
[   75.644059] Bluetooth: RFCOMM socket layer initialized
[   75.644349] Bluetooth: RFCOMM TTY layer initialized
[   75.644352] Bluetooth: RFCOMM ver 1.8
[   56.812000] Marking TSC unstable due to: cpufreq changes.
[   56.816000] Time: acpi_pm clocksource has been installed.
[   57.144000] Clocksource tsc unstable (delta = -148960904 ns)
alain@VAMPIRE666-ubuntu:~$ 

```
By the way when I select the uBuntu Op in the grub I notice a line error.....
"Cannot allocate resource region 3"....and something else, The error it's too fast and I can't read it. :-(

---

### Post by gmaniac on 2007-11-13
I have seen this message before in the forums "Clocksource tsc unstable" and people mentioning slow speeds but i don't know if there is a solution.
Search for that message. Also you could try booting with acpi disabled ( it's a grub option. Search for that also if you don't know how).

When you want to pause something when booting you can use the "dead" key scroll lock (scrLck) but probably it wont do you any good.

Hope you can find a solution

---

### Post by vampire666eng on 2007-11-26
I got it fixed.

Look here:
[http://ubuntuforums.org/showthread.php?p=3842786#post3842786](http://ubuntuforums.org/showthread.php?p=3842786#post3842786)

---

