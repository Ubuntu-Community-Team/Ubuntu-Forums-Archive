---
title: "Can't log in, inexpliciably"
date: 2008-04-25
forum: General Help
---

### Post by AndrewTheArt on 2008-04-25
Hey guys, I can successfully get to the login screen of my machine (Ubuntu 8.04), but after typing in my username and password, the computer does not log in - the brown/yellow background shows, but nothing else is present.

As I was restarting I did see an error about a syntax issue in the httpd.conf file (using this desktop as a web server), so I completely uninstalled apache2 to eliminate that as a confounding issue.

I logged into a failsafe xterm and got the output of dmesg uploaded to my webserver. Here it is - any ideas?

```
[    0.000000] Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e800 (usable)
[    0.000000]  BIOS-e820: 000000000009e800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fff3000 (usable)
[    0.000000]  BIOS-e820: 000000007fff3000 - 000000007fffb000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007fffb000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fed00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffc00000 - 0000000100000000 (reserved)
[    0.000000] 1151MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f4f60
[    0.000000] Entering add_active_range(0, 0, 524275) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   524275
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   524275
[    0.000000] On node 0 totalpages: 524275
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2303 pages used for memmap
[    0.000000]   HighMem zone: 292596 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F4EE0 checksum 0
[    0.000000] ACPI: RSDP 000F4EE0, 0024 (r2 HP    )
[    0.000000] ACPI: XSDT 7FFF32C0, 0044 (r1 HP     D19             2   Ò     162E)
[    0.000000] ACPI: FACP 7FFF3340, 00F4 (r3 HP     D19             2   Ò     162E)
[    0.000000] ACPI: DSDT 7FFF3440, 1F5E (r1 HP         DSDT        1 INTL 20030228)
[    0.000000] ACPI: FACS 7FFF3100, 0040
[    0.000000] ACPI: SPCR 7FFF3140, 0050 (r1 HP     SPCRRBSU        1   Ò     162E)
[    0.000000] ACPI: MCFG 7FFF31C0, 003C (r1 HP     ProLiant        1             0)
[    0.000000] ACPI: APIC 7FFF3200, 00B6 (r1 HP     00000083        2             0)
[    0.000000] ACPI: PM-Timer IO Port: 0x908
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:4 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x04] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x06] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:4 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x05] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x07] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 8, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IOAPIC (id[0x09] address[0xfec10000] gsi_base[24])
[    0.000000] IOAPIC[1]: apic_id 9, version 32, address 0xfec10000, GSI 24-47
[    0.000000] ACPI: IOAPIC (id[0x0a] address[0xfec80000] gsi_base[48])
[    0.000000] IOAPIC[2]: apic_id 10, version 32, address 0xfec80000, GSI 48-71
[    0.000000] ACPI: IOAPIC (id[0x0b] address[0xfec80400] gsi_base[72])
[    0.000000] IOAPIC[3]: apic_id 11, version 32, address 0xfec80400, GSI 72-95
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 4 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:7ec00000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009e000 - 000000000009f000
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 520180
[    0.000000] Kernel command line: root=UUID=8d96537a-52c2-4ece-9cdf-b1d27fcf2819 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] mapped IOAPIC to ffff9000 (fec10000)
[    0.000000] mapped IOAPIC to ffff8000 (fec80000)
[    0.000000] mapped IOAPIC to ffff7000 (fec80400)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 3200.271 MHz processor.
[   95.803195] Console: colour VGA+ 80x25
[   95.803199] console [tty0] enabled
[   95.803575] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   95.803938] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   95.910484] Memory: 2066708k/2097100k available (2157k kernel code, 29028k reserved, 998k data, 364k init, 1179596k highmem)
[   95.910493] virtual kernel memory layout:
[   95.910494]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   95.910495]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   95.910496]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   95.910497]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   95.910498]       .init : 0xc041b000 - 0xc0476000   ( 364 kB)
[   95.910499]       .data : 0xc031b5a4 - 0xc0414dc4   ( 998 kB)
[   95.910500]       .text : 0xc0100000 - 0xc031b5a4   (2157 kB)
[   95.910502] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   95.910546] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   95.990326] Calibrating delay using timer specific routine.. 6405.70 BogoMIPS (lpj=12811401)
[   95.990354] Security Framework initialized
[   95.990360] SELinux:  Disabled at boot.
[   95.990376] AppArmor: AppArmor initialized
[   95.990380] Failure registering capabilities with primary security module.
[   95.990388] Mount-cache hash table entries: 512
[   95.990526] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000641d 00000000 00000001 00000000
[   95.990535] monitor/mwait feature present.
[   95.990537] using mwait in idle threads.
[   95.990543] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   95.990545] CPU: L2 cache: 2048K
[   95.990548] CPU: Physical Processor ID: 0
[   95.990550] CPU: After all inits, caps: bfebfbff 20000000 00000000 0000b180 0000641d 00000000 00000001 00000000
[   95.990561] Compat vDSO mapped to ffffe000.
[   95.990577] Checking 'hlt' instruction... OK.
[   96.006725] SMP alternatives: switching to UP code
[   96.008554] Early unpacking initramfs... done
[   96.296693] ACPI: Core revision 20070126
[   96.296734] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   96.297818] CPU0: Intel(R) Xeon(TM) CPU 3.20GHz stepping 0a
[   96.297838] SMP alternatives: switching to SMP code
[   96.298592] Booting processor 1/1 eip 3000
[   96.308819] Initializing CPU#1
[   96.389111] Calibrating delay using timer specific routine.. 6400.71 BogoMIPS (lpj=12801437)
[   96.389121] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000641d 00000000 00000001 00000000
[   96.389128] monitor/mwait feature present.
[   96.389134] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   96.389137] CPU: L2 cache: 2048K
[   96.389139] CPU: Physical Processor ID: 0
[   96.389141] CPU: After all inits, caps: bfebfbff 20000000 00000000 0000b180 0000641d 00000000 00000001 00000000
[   96.389667] CPU1: Intel(R) Xeon(TM) CPU 3.20GHz stepping 0a
[   96.389708] Total of 2 processors activated (12806.41 BogoMIPS).
[   96.390032] ENABLING IO-APIC IRQs
[   96.390211] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   96.536799] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   96.556754] Brought up 2 CPUs
[   96.556783] CPU0 attaching sched-domain:
[   96.556786]  domain 0: span 03
[   96.556788]   groups: 01 02
[   96.556792]   domain 1: span 03
[   96.556794]    groups: 03
[   96.556796] CPU1 attaching sched-domain:
[   96.556798]  domain 0: span 03
[   96.556800]   groups: 02 01
[   96.556803]   domain 1: span 03
[   96.556805]    groups: 03
[   96.557058] net_namespace: 64 bytes
[   96.557065] Booting paravirtualized kernel on bare hardware
[   96.557644] Time: 15:03:09  Date: 04/25/08
[   96.557668] NET: Registered protocol family 16
[   96.557923] EISA bus registered
[   96.557929] ACPI: bus type pci registered
[   96.580649] PCI: PCI BIOS revision 2.10 entry at 0xf0096, last bus=18
[   96.580652] PCI: Using configuration type 1
[   96.580653] Setting up standard PCI resources
[   96.586161] ACPI: EC: Look up EC in DSDT
[   96.587370] ACPI: Interpreter enabled
[   96.587373] ACPI: (supports S0 S4 S5)
[   96.587386] ACPI: Using IOAPIC for interrupt routing
[   96.590141] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   96.590758] PCI quirk: region 0900-097f claimed by ICH4 ACPI/GPIO/TCO
[   96.590762] PCI quirk: region 0800-083f claimed by ICH4 GPIO
[   96.590929] PCI: PXH quirk detected, disabling MSI for SHPC device
[   96.590971] PCI: PXH quirk detected, disabling MSI for SHPC device
[   96.592055] PCI: Transparent bridge - 0000:00:1e.0
[   96.592093] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   96.592246] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.IP2P._PRT]
[   96.592337] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.IPXB._PRT]
[   96.592464] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PTA0._PRT]
[   96.592548] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PTA0.PCXA._PRT]
[   96.592656] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PTA0.PCXB._PRT]
[   96.592807] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PTB0._PRT]
[   96.592909] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PTC0._PRT]
[   96.594968] ACPI: PCI Interrupt Link [LNKA] (IRQs *5 7 10 11)
[   96.595034] ACPI: PCI Interrupt Link [LNKB] (IRQs *5 7 10 11)
[   96.595099] ACPI: PCI Interrupt Link [LNKC] (IRQs 5 7 10 *11)
[   96.595161] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 *10 11)
[   96.595224] ACPI: PCI Interrupt Link [LNKE] (IRQs 5 7 *10 11)
[   96.595286] ACPI: PCI Interrupt Link [LNKF] (IRQs 5 7 *10 11)
[   96.595348] ACPI: PCI Interrupt Link [LNKG] (IRQs 5 7 10 *11)
[   96.595410] ACPI: PCI Interrupt Link [LNKH] (IRQs 5 7 *10 11)
[   96.595535] Linux Plug and Play Support v0.97 (c) Adam Belay
[   96.595581] pnp: PnP ACPI init
[   96.595591] ACPI: bus type pnp registered
[   96.597165] pnp: PnP ACPI: found 10 devices
[   96.597168] ACPI: ACPI bus type pnp unregistered
[   96.597171] PnPBIOS: Disabled by ACPI PNP
[   96.597480] PCI: Using ACPI for IRQ routing
[   96.597483] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   96.597498] PCI: Cannot allocate resource region 4 of device 0000:00:1d.0
[   96.597503] PCI: Cannot allocate resource region 4 of device 0000:00:1d.1
[   96.597516] PCI: Cannot allocate resource region 0 of device 0000:00:1f.2
[   96.597518] PCI: Cannot allocate resource region 1 of device 0000:00:1f.2
[   96.597520] PCI: Cannot allocate resource region 2 of device 0000:00:1f.2
[   96.597522] PCI: Cannot allocate resource region 3 of device 0000:00:1f.2
[   96.597524] PCI: Cannot allocate resource region 4 of device 0000:00:1f.2
[   96.603684] PCI: Device 0000:00:00.0 not found by BIOS
[   96.764138] NET: Registered protocol family 8
[   96.764140] NET: Registered protocol family 20
[   96.764219] AppArmor: AppArmor Filesystem Enabled
[   96.767992] Time: tsc clocksource has been installed.
[   96.784126] system 00:01: ioport range 0x408-0x40f has been reserved
[   96.784130] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[   96.784133] system 00:01: ioport range 0x500-0x50f has been reserved
[   96.784136] system 00:01: ioport range 0x700-0x71f has been reserved
[   96.784138] system 00:01: ioport range 0x800-0x83f has been reserved
[   96.784141] system 00:01: ioport range 0x900-0x97f has been reserved
[   96.784144] system 00:01: ioport range 0xc80-0xc83 has been reserved
[   96.784147] system 00:01: ioport range 0xcd4-0xcd7 has been reserved
[   96.784150] system 00:01: ioport range 0xf50-0xf58 has been reserved
[   96.784152] system 00:01: ioport range 0x2f8-0x2ff has been reserved
[   96.784156] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[   96.814626] PCI: Bridge: 0000:05:00.0
[   96.814629]   IO window: disabled.
[   96.814633]   MEM window: 88000000-880fffff
[   96.814637]   PREFETCH window: f4000000-f7ffffff
[   96.814641] PCI: Bridge: 0000:05:00.2
[   96.814643]   IO window: disabled.
[   96.814647]   MEM window: disabled.
[   96.814650]   PREFETCH window: disabled.
[   96.814654] PCI: Bridge: 0000:00:02.0
[   96.814655]   IO window: disabled.
[   96.814659]   MEM window: 88000000-880fffff
[   96.814663]   PREFETCH window: f4000000-f7ffffff
[   96.814667] PCI: Bridge: 0000:00:04.0
[   96.814669]   IO window: disabled.
[   96.814673]   MEM window: disabled.
[   96.814676]   PREFETCH window: disabled.
[   96.814680] PCI: Bridge: 0000:00:06.0
[   96.814681]   IO window: disabled.
[   96.814685]   MEM window: disabled.
[   96.814688]   PREFETCH window: disabled.
[   96.814694] PCI: Bridge: 0000:00:1c.0
[   96.814698]   IO window: 4000-4fff
[   96.814703]   MEM window: fdf00000-fdffffff
[   96.814707]   PREFETCH window: 88100000-882fffff
[   96.814714] PCI: Bridge: 0000:00:1e.0
[   96.814717]   IO window: 1000-3fff
[   96.814722]   MEM window: fbf00000-fdefffff
[   96.814726]   PREFETCH window: disabled.
[   96.814745] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   96.814751] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   96.814767] PCI: Setting latency timer of device 0000:05:00.0 to 64
[   96.814782] PCI: Setting latency timer of device 0000:05:00.2 to 64
[   96.814793] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 16 (level, low) -> IRQ 16
[   96.814798] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   96.814808] ACPI: PCI Interrupt 0000:00:06.0[A] -> GSI 16 (level, low) -> IRQ 16
[   96.814812] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   96.814829] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   96.814840] NET: Registered protocol family 2
[   96.851950] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   96.852222] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   96.852747] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   96.853010] TCP: Hash tables configured (established 131072 bind 65536)
[   96.853012] TCP reno registered
[   96.864004] checking if image is initramfs... it is
[   97.314355] Switched to high resolution mode on CPU 0
[   97.314477] Switched to high resolution mode on CPU 1
[   97.431317] Freeing initrd memory: 7679k freed
[   97.432312] audit: initializing netlink socket (disabled)
[   97.432327] audit(1209135790.404:1): initialized
[   97.432570] highmem bounce pool size: 64 pages
[   97.434839] VFS: Disk quotas dquot_6.5.1
[   97.434941] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   97.435094] io scheduler noop registered
[   97.435097] io scheduler anticipatory registered
[   97.435099] io scheduler deadline registered
[   97.435110] io scheduler cfq registered (default)
[   97.435317] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   97.435346] Allocate Port Service[0000:00:02.0:pcie00]
[   97.435442] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   97.435471] Allocate Port Service[0000:00:04.0:pcie00]
[   97.435566] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   97.435595] Allocate Port Service[0000:00:06.0:pcie00]
[   97.435929] isapnp: Scanning for PnP cards...
[   97.786779] isapnp: No Plug & Play device found
[   97.821366] Real Time Clock Driver v1.12ac
[   97.821473] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   97.821593] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   97.821701] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   97.822392] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   97.823324] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   97.823400] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   97.823518] PNP: PS/2 Controller [PNP0303:KBD,PNP0f0e:PS2M] at 0x60,0x64 irq 1,12
[   97.825030] serio: i8042 KBD port at 0x60,0x64 irq 1
[   97.825036] serio: i8042 AUX port at 0x60,0x64 irq 12
[   97.844752] mice: PS/2 mouse device common for all mice
[   97.844898] EISA: Probing bus 0 at eisa.0
[   97.844902] EISA: Cannot allocate resource for mainboard
[   97.844904] Cannot allocate resource for EISA slot 1
[   97.844906] Cannot allocate resource for EISA slot 2
[   97.844908] Cannot allocate resource for EISA slot 3
[   97.844910] Cannot allocate resource for EISA slot 4
[   97.844912] Cannot allocate resource for EISA slot 5
[   97.844927] EISA: Detected 0 cards.
[   97.844931] cpuidle: using governor ladder
[   97.844933] cpuidle: using governor menu
[   97.845011] NET: Registered protocol family 1
[   97.845039] Using IPI No-Shortcut mode
[   97.845071] registered taskstats version 1
[   97.845185]   Magic number: 4:968:83
[   97.845188]   hash matches /build/buildd/linux-2.6.24/drivers/base/power/main.c:112
[   97.845253] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   97.845255] EDD information not available.
[   97.845473] Freeing unused kernel memory: 364k freed
[   97.880997] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   99.063772] fuse init (API version 7.9)
[   99.084097] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   99.084110] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   99.085284] ACPI: Thermal Zone [THM0] (8 C)
[   99.268172] usbcore: registered new interface driver usbfs
[   99.268205] usbcore: registered new interface driver hub
[   99.276266] usbcore: registered new device driver usb
[   99.296174] USB Universal Host Controller Interface driver v3.0
[   99.296241] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[   99.296255] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   99.296260] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   99.296490] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   99.296521] uhci_hcd 0000:00:1d.0: irq 16, io base 0x00005000
[   99.296703] usb usb1: configuration #1 chosen from 1 choice
[   99.296739] hub 1-0:1.0: USB hub found
[   99.296749] hub 1-0:1.0: 2 ports detected
[   99.399938] ACPI: PCI Interrupt 0000:00:1d.1[b] -> GSI 19 (level, low) -> IRQ 17
[   99.399954] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   99.399960] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   99.399994] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   99.400023] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00005020
[   99.400191] usb usb2: configuration #1 chosen from 1 choice
[   99.400228] hub 2-0:1.0: USB hub found
[   99.400236] hub 2-0:1.0: 2 ports detected
[   99.475910] SCSI subsystem initialized
[   99.504341] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 18
[   99.504359] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   99.504364] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   99.504400] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 3
[   99.508314] ehci_hcd 0000:00:1d.7: debug port 1
[   99.508322] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   99.508334] ehci_hcd 0000:00:1d.7: irq 18, io mem 0xfbee0000
[   99.519443] libata version 3.00 loaded.
[   99.524460] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   99.524624] usb usb3: configuration #1 chosen from 1 choice
[   99.524665] hub 3-0:1.0: USB hub found
[   99.524674] hub 3-0:1.0: 4 ports detected
[   99.574932] Fusion MPT base driver 3.04.06
[   99.574937] Copyright (c) 1999-2007 LSI Corporation
[   99.584282] Fusion MPT SPI Host driver 3.04.06
[   99.628335] ACPI: PCI Interrupt 0000:02:03.0[A] -> GSI 24 (level, low) -> IRQ 19
[   99.628354] mptbase: ioc0: Initiating bringup
[   99.749266] Adaptec aacraid driver 1.1-5[2449]-ms
[   99.813039] Floppy drive(s): fd0 is 1.44M
[   99.828341] FDC 0 is a National Semiconductor PC87306
[   99.902283] usb 3-4: new high speed USB device using ehci_hcd and address 2
[  100.036276] usb 3-4: configuration #1 chosen from 1 choice
[  100.036560] hub 3-4:1.0: USB hub found
[  100.036896] hub 3-4:1.0: 4 ports detected
[  100.114597] ioc0: LSI53C1030 C0: Capabilities={Initiator,Target}
[  100.618503] scsi0 : ioc0: LSI53C1030 C0, FwRev=01032700h, Ports=1, MaxQ=255, IRQ=19
[  101.501353] ACPI: PCI Interrupt 0000:02:03.1[b] -> GSI 25 (level, low) -> IRQ 20
[  101.501379] mptbase: ioc1: Initiating bringup
[  101.501392]  target0:0:0: mptspi: ioc0: mpt_config failed
[  101.988763] ioc1: LSI53C1030 C0: Capabilities={Initiator,Target}
[  102.493648] scsi1 : ioc1: LSI53C1030 C0, FwRev=01032700h, Ports=1, MaxQ=255, IRQ=20
[  103.375757] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[  103.375770] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 21
[  103.375818] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[  103.375835] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
[  103.375855] ACPI: PCI Interrupt 0000:00:1f.2[A] -> GSI 18 (level, low) -> IRQ 21
[  103.375885] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[  103.375897] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[  103.379088] tg3.c:v3.86 (November 9, 2007)
[  103.379107] ACPI: PCI Interrupt 0000:01:02.0[A] -> GSI 17 (level, low) -> IRQ 22
[  103.450979] eth0: Tigon3 [partno(349322-001) rev 3003 PHY(5705)] (PCI:33MHz:32-bit) 10/100/1000Base-T Ethernet 00:17:a4:0f:f6:cf
[  103.450987] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[0] TSOcap[1]
[  103.450990] eth0: dma_rwctrl[763f0000] dma_mask[64-bit]
[  103.451058] ACPI: PCI Interrupt 0000:06:01.0[A] -> GSI 48 (level, low) -> IRQ 23
[  103.480528] AAC0: kernel 4.2-1[7368] Mar 30 2005
[  103.480532] AAC0: monitor 4.2-1[7368]
[  103.480534] AAC0: bios 4.2-1[7368]
[  103.480537] AAC0: serial CAC1BA
[  103.481506] scsi2 : aacraid
[  103.485005] scsi 2:0:0:0: Direct-Access     Adaptec  2610SA Volume    V1.0 PQ: 0 ANSI: 2
[  103.487302] ata_piix 0000:00:1f.1: version 2.12
[  103.487320] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 21
[  103.487367] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[  103.487695] scsi3 : ata_piix
[  103.487799] scsi4 : ata_piix
[  103.487847] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x500 irq 14
[  103.487863] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x508 irq 15
[  103.492331] scsi 2:1:0:0: Direct-Access     Maxtor   6L250S0          BACE PQ: 0 ANSI: 2
[  103.493643] scsi 2:1:1:0: Direct-Access     Maxtor   6L250S0          BACE PQ: 0 ANSI: 2
[  103.494924] scsi 2:1:2:0: Direct-Access     Maxtor   6L250S0          BACE PQ: 0 ANSI: 2
[  103.496201] scsi 2:1:3:0: Direct-Access     Maxtor   6L250S0          BACE PQ: 0 ANSI: 2
[  103.522553] scsi 2:1:14:0: Enclosure         HP       SATA 01B-06D3511      PQ: 0 ANSI: 2
[  103.962031] ata2.00: ATAPI: HL-DT-STDVDRRW GWA-4166B, 2.04, max UDMA/33
[  104.137404] ata2.00: configured for UDMA/33
[  104.137432] scsi: waiting for bus probes to complete ...
[  107.125873] scsi 4:0:0:0: CD-ROM            HL-DT-ST DVDRRW GWA-4166B 2.04 PQ: 0 ANSI: 5
[  107.125978] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
[  107.126004] ACPI: PCI Interrupt 0000:00:1f.2[A] -> GSI 18 (level, low) -> IRQ 21
[  107.126058] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[  107.126114] scsi5 : ata_piix
[  107.126181] scsi6 : ata_piix
[  107.126238] ata3: SATA max UDMA/133 cmd 0x5050 ctl 0x5060 bmdma 0x5040 irq 21
[  107.126242] ata4: SATA max UDMA/133 cmd 0x5058 ctl 0x5064 bmdma 0x5048 irq 21
[  107.136620] Driver 'sd' needs updating - please use bus_type methods
[  107.136806] sd 2:0:0:0: [sda] 1953116160 512-byte hardware sectors (999995 MB)
[  107.136829] sd 2:0:0:0: [sda] Write Protect is off
[  107.136834] sd 2:0:0:0: [sda] Mode Sense: 06 00 10 00
[  107.136872] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, supports DPO and FUA
[  107.136994] sd 2:0:0:0: [sda] 1953116160 512-byte hardware sectors (999995 MB)
[  107.137030] sd 2:0:0:0: [sda] Write Protect is off
[  107.137034] sd 2:0:0:0: [sda] Mode Sense: 06 00 10 00
[  107.137067] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, supports DPO and FUA
[  107.137072]  sda: sda1 sda2 <<5>sd 2:0:0:0: Attached scsi generic sg0 type 0
[  107.139952] scsi 2:1:0:0: Attached scsi generic sg1 type 0
[  107.139985] scsi 2:1:1:0: Attached scsi generic sg2 type 0
[  107.140017] scsi 2:1:2:0: Attached scsi generic sg3 type 0
[  107.140048] scsi 2:1:3:0: Attached scsi generic sg4 type 0
[  107.140081] scsi 2:1:14:0: Attached scsi generic sg5 type 13
[  107.140114] scsi 4:0:0:0: Attached scsi generic sg6 type 5
[  107.151927]  sda5 >
[  107.152080] sd 2:0:0:0: [sda] Attached SCSI removable disk
[  107.460685] Driver 'sr' needs updating - please use bus_type methods
[  107.468399] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[  107.468406] Uniform CD-ROM driver Revision: 3.20
[  107.468505] sr 4:0:0:0: Attached scsi CD-ROM sr0
[  107.557627] Attempting manual resume
[  107.557632] swsusp: Resume From Partition 8:5
[  107.557634] PM: Checking swsusp image.
[  107.558020] PM: Resume from disk failed.
[  107.635504] kjournald starting.  Commit interval 5 seconds
[  107.635513] EXT3-fs: mounted filesystem with ordered data mode.
[  122.903884] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  123.024404] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  123.346529] iTCO_vendor_support: vendor-support=0
[  123.386380] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[  123.456045] EDAC MC: Ver: 2.1.0 Apr 10 2008
[  123.495867] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input2
[  123.527237] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[  123.527251] iTCO_wdt: No card detected
[  123.665573] parport_pc 00:07: reported by Plug and Play ACPI
[  123.665634] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[  123.761259] Contact your BIOS vendor to see if the E752x error registers can be safely un-hidden
[  123.881416] intel_rng: FWH not detected
[  124.094226] input: Power Button (FF) as /devices/virtual/input/input3
[  124.144013] ACPI: Power Button (FF) [PWRF]
[  127.672758] lp0: using parport0 (interrupt-driven).
[  127.712943] Adding 6072528k swap on /dev/sda5.  Priority:-1 extents:1 across:6072528k
[  128.259669] EXT3 FS on sda1, internal journal
[  128.360861] device-mapper: uevent: version 1.0.3
[  128.360900] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: dm-devel@redhat.com
[  129.826622] ip_tables: (C) 2000-2006 Netfilter Core Team
[  130.120116] No dock devices found.
[  133.581196] apm: BIOS not found.
[  133.779916] ppdev: user-space parallel port driver
[  134.445743] audit(1209135827.873:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5327 profile="/usr/sbin/cupsd" namespace="default"
[  135.683507] Bluetooth: Core ver 2.11
[  135.684343] NET: Registered protocol family 31
[  135.684349] Bluetooth: HCI device and connection manager initialized
[  135.684355] Bluetooth: HCI socket layer initialized
[  135.708132] Bluetooth: L2CAP ver 2.9
[  135.708139] Bluetooth: L2CAP socket layer initialized
[  135.780374] Bluetooth: RFCOMM socket layer initialized
[  135.780388] Bluetooth: RFCOMM TTY layer initialized
[  135.780392] Bluetooth: RFCOMM ver 1.8
[  137.218590] tg3: eth0: Link is up at 100 Mbps, full duplex.
[  137.218595] tg3: eth0: Flow control is off for TX and off for RX.
[  138.436998] NET: Registered protocol family 10
[  138.437364] lo: Disabled Privacy Extensions
[  139.453941] NET: Registered protocol family 17
[  152.328362] eth0: no IPv6 routers present
[  154.354525] gnome-keyring-d[6008]: segfault at 00000014 eip 080759c7 esp bfadd2a0 error 6
[  156.192505] gnome-keyring-d[6075]: segfault at 00000014 eip 080759c7 esp b7a26dc0 error 6
[  185.746703] gnome-keyring-d[6140]: segfault at 00000014 eip 080759c7 esp bf907990 error 6

```

---

### Post by Steve1961 on 2008-04-26
See this bug report:

[https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/218434](https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/218434)

---

### Post by AndrewTheArt on 2008-04-28
Thank you so much, that was exactly the bug I was experiencing and that bug report solved my issues.

For anyone interested, here is the [permalink]("https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/218434/comments/44") to the workaround. Apparently (not confirmed) either the latest version of the pam integration module or the gnome-keyring itself from SVN fixes the bug, so eventually this won't be an issue.

For now, either figure out how to install it from SVN or do this following from the link above (disable pam-gnome-keyring)

```
Workaround
---------------
This isn't really a workaround as you won't have any keyring functionality but at least you can log in.
1) Enable login by disabling the gnome keyring PAM Module:
# cp /etc/pam.d/gdm /etc/pam.d/gdm.old
* Edit /etc/pam.d/gdm and delete all lines which reference 'pam_gnome_keyring.so' (Expect to find 2 lines)
2) Restart GDM or Reboot
3) Log in and you should get in, but obviously without the Keyring features.
```Once again, thank you Steve1961.

---

### Post by Steve1961 on 2008-04-28
You're welcome

---

### Post by maiden30403 on 2008-05-11
Thanks so much guys, have this exact same problem, think I'll be switching to an IDE drive if I keep having problems with SCSI.

Just to clarify, SCSI is the issue here isn't it?

---

### Post by Steve1961 on 2008-05-11
> **maiden30403 said:**
> Thanks so much guys, have this exact same problem, think I'll be switching to an IDE drive if I keep having problems with SCSI.

Just to clarify, SCSI is the issue here isn't it?

certain scsi and flash drives seem to cause the problem.  But for information the latest fix reported on the bug report seems to resolve the issue.  Just add this line to rc.local:

hal-get-property --key block.storage_device --udi `hal-find-by-property --key volume.mount_point --string /` | xargs -l1 hal-set-property --key storage.removable --bool false --udi

---

### Post by maiden30403 on 2008-05-12
Hmm, I tried this and it doesn't solve my problem but the old fix does. There may be more to this so. I'll play around with it later and see what's going wrong.

Also I'm using an Adaptec RAID Controller 320/DC.

---

### Post by maiden30403 on 2008-05-14
> **maiden30403 said:**
> Hmm, I tried this and it doesn't solve my problem but the old fix does. There may be more to this so. I'll play around with it later and see what's going wrong.

Also I'm using an Adaptec RAID Controller 320/DC.

The solution to this if you're using an Adaptec (and possibly other) RAID controllers is setting the parent as non-removable.

You should have a line like this in rc.local:

```
hal-set-property --udi "/org/freedesktop/Hal/devices/storage_serial_SDELL_PERC_Stripe_D9427035" --key storage.removable --bool false
```

---

