---
title: "problem with compiz stopping randomly"
date: 2008-07-06
forum: General Help
---

### Post by nyxtwilight on 2008-07-06
finally got effects working with my graphics card

got awn dock...all happy and then a while later...compiz turns itself to normal and the dock disappears =/

does it all the time. im not sure what the problem is, weather its my driver for my graphics card (which is in beta) or compiz, or my computer being retarded =/

had a look at the system log and it says this:

```
Jul  5 21:39:53 nyxtwilight-laptop syslogd 1.5.0#1ubuntu1: restart.
Jul  5 21:47:16 nyxtwilight-laptop pulseaudio[15698]: main.c: This program is not intended to be run as root (unless --system is specified).
Jul  5 21:47:16 nyxtwilight-laptop pulseaudio[15698]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Jul  5 21:47:16 nyxtwilight-laptop pulseaudio[15698]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Jul  5 21:47:16 nyxtwilight-laptop pulseaudio[15698]: alsa-util.c: Cannot find fallback mixer control "Mic".
Jul  5 22:05:11 nyxtwilight-laptop syslogd 1.5.0#1ubuntu1: restart.
Jul  5 22:05:11 nyxtwilight-laptop kernel: Inspecting /boot/System.map-2.6.24-16-generic
Jul  5 22:05:11 nyxtwilight-laptop kernel: Loaded 27704 symbols from /boot/System.map-2.6.24-16-generic.
Jul  5 22:05:11 nyxtwilight-laptop kernel: Symbols match kernel version 2.6.24.
Jul  5 22:05:11 nyxtwilight-laptop kernel: Loaded 16772 symbols from 81 modules.
Jul  5 22:05:11 nyxtwilight-laptop kernel: [    0.000000] Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
Jul  5 22:05:11 nyxtwilight-laptop kernel: [    0.000000] BIOS-provided physical RAM map:
Jul  5 22:05:11 nyxtwilight-laptop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
Jul  5 22:05:11 nyxtwilight-laptop kernel: [    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
Jul  5 22:05:11 nyxtwilight-laptop kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Jul  5 22:05:11 nyxtwilight-laptop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000001be90000 (usable)
Jul  5 22:05:11 nyxtwilight-laptop kernel: [    0.000000]  BIOS-e820: 000000001be90000 - 000000001be9f000 (ACPI data)
Jul  5 22:05:11 nyxtwilight-laptop kernel: [    0.000000]  BIOS-e820: 000000001be9f000 - 000000001bf00000 (ACPI NVS)
Jul  5 22:05:11 nyxtwilight-laptop kernel: [    0.000000]  BIOS-e820: 000000001bf00000 - 0000000020000000 (reserved)
Jul  5 22:05:11 nyxtwilight-laptop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Jul  5 22:05:11 nyxtwilight-laptop kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Jul  5 22:05:11 nyxtwilight-laptop kernel: [    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
Jul  5 22:05:11 nyxtwilight-laptop kernel: [    0.000000] 0MB HIGHMEM available.
Jul  5 22:05:11 nyxtwilight-laptop kernel: [    0.000000] 446MB LOWMEM available.
Jul  5 22:05:11 nyxtwilight-laptop kernel: [    0.000000] found SMP MP-table at 000f7480
Jul  5 22:05:11 nyxtwilight-laptop kernel: [    0.000000] Zone PFN ranges:
Jul  5 22:05:11 nyxtwilight-laptop kernel: [    0.000000]   DMA             0 ->     4096
Jul  5 22:05:11 nyxtwilight-laptop kernel: [    0.000000]   Normal       4096 ->   114320
Jul  5 22:05:11 nyxtwilight-laptop kernel: [    0.000000]   HighMem    114320 ->   114320
Jul  5 22:05:11 nyxtwilight-laptop kernel: [    0.000000] Movable zone start PFN for each node
Jul  5 22:05:11 nyxtwilight-laptop kernel: [    0.000000] early_node_map[1] active PFN ranges
Jul  5 22:05:11 nyxtwilight-laptop kernel: [    0.000000]     0:        0 ->   114320
Jul  5 22:05:11 nyxtwilight-laptop kernel: [    0.000000] DMI present.
Jul  5 22:05:11 nyxtwilight-laptop kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F73D0 checksum 0
Jul  5 22:05:11 nyxtwilight-laptop kernel: [    0.000000] ACPI: RSDP 000F73D0, 0014 (r0 PTLTD )
Jul  5 22:05:11 nyxtwilight-laptop kernel: [    0.000000] ACPI: RSDT 1BE992D9, 0038 (r1 FSC    PC        6040000  LTP        0)
Jul  5 22:05:11 nyxtwilight-laptop kernel: [    0.000000] ACPI: FACP 1BE9ED70, 0074 (r1 VN896  PTLTW     6040000 PTL_    F4240)
Jul  5 22:05:11 nyxtwilight-laptop kernel: [    0.000000] ACPI: DSDT 1BE99D0E, 5062 (r1  FIC   LM10W     6040000 MSFT  100000E)
Jul  5 22:05:11 nyxtwilight-laptop kernel: [    0.000000] ACPI: FACS 1BE9FFC0, 0040
Jul  5 22:05:11 nyxtwilight-laptop kernel: [    0.000000] ACPI: APIC 1BE9EDE4, 006A (r1 PTLTD  ^I APIC    6040000  LTP        0)
Jul  5 22:05:11 nyxtwilight-laptop kernel: [    0.000000] ACPI: MCFG 1BE9EE4E, 003C (r1 PTLTD    MCFG    6040000  LTP        0)
Jul  5 22:05:11 nyxtwilight-laptop kernel: [    0.000000] ACPI: SLIC 1BE9EE8A, 0176 (r1 FSC    PC        6040000             0)
Jul  5 22:05:11 nyxtwilight-laptop kernel: [    0.000000] ACPI: SSDT 1BE99311, 0519 (r1  PmRef    CpuPm     3000 INTL 20050228)
Jul  5 22:05:11 nyxtwilight-laptop kernel: [    0.000000] ACPI: DMI detected: Fujitsu Siemens
Jul  5 22:05:11 nyxtwilight-laptop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x4008
Jul  5 22:05:11 nyxtwilight-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jul  5 22:05:11 nyxtwilight-laptop kernel: [    0.000000] Processor #0 6:14 APIC version 20
Jul  5 22:05:11 nyxtwilight-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Jul  5 22:05:11 nyxtwilight-laptop kernel: [    0.000000] Processor #1 6:14 APIC version 20
Jul  5 22:05:11 nyxtwilight-laptop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Jul  5 22:05:11 nyxtwilight-laptop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Jul  5 22:05:11 nyxtwilight-laptop kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Jul  5 22:05:11 nyxtwilight-laptop kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
Jul  5 22:05:11 nyxtwilight-laptop kernel: [    0.000000] ACPI: IOAPIC (id[0x03] address[0xfecc0000] gsi_base[24])
Jul  5 22:05:11 nyxtwilight-laptop kernel: [    0.000000] IOAPIC[1]: apic_id 3, version 3, address 0xfecc0000, GSI 24-47
Jul  5 22:05:11 nyxtwilight-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jul  5 22:05:11 nyxtwilight-laptop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 2 I/O APICs
Jul  5 22:05:11 nyxtwilight-laptop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jul  5 22:05:11 nyxtwilight-laptop kernel: [    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
Jul  5 22:05:11 nyxtwilight-laptop kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009d000 - 000000000009e000
Jul  5 22:05:11 nyxtwilight-laptop kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009e000 - 00000000000a0000
Jul  5 22:05:11 nyxtwilight-laptop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
Jul  5 22:05:11 nyxtwilight-laptop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
Jul  5 22:05:11 nyxtwilight-laptop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 113427
Jul  5 22:05:11 nyxtwilight-laptop kernel: [    0.000000] Kernel command line: root=UUID=270f4baf-9a32-4ebc-af92-f1e8eb400da6 ro quiet splash
Jul  5 22:05:11 nyxtwilight-laptop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Jul  5 22:05:11 nyxtwilight-laptop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Jul  5 22:05:11 nyxtwilight-laptop kernel: [    0.000000] Initializing CPU#0
Jul  5 22:05:11 nyxtwilight-laptop kernel: [    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
Jul  5 22:05:11 nyxtwilight-laptop kernel: [    0.000000] Detected 1596.034 MHz processor.
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   21.391480] Console: colour VGA+ 80x25
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   21.391489] console [tty0] enabled
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   21.391795] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   21.392167] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   21.410432] Memory: 440860k/457280k available (2157k kernel code, 15836k reserved, 998k data, 364k init, 0k highmem)
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   21.410448] virtual kernel memory layout:
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   21.410451]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   21.410453]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   21.410456]     vmalloc : 0xdc800000 - 0xff7fe000   ( 559 MB)
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   21.410459]     lowmem  : 0xc0000000 - 0xdbe90000   ( 446 MB)
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   21.410462]       .init : 0xc041b000 - 0xc0476000   ( 364 kB)
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   21.410464]       .data : 0xc031b5a4 - 0xc0414dc4   ( 998 kB)
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   21.410467]       .text : 0xc0100000 - 0xc031b5a4   (2157 kB)
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   21.410475] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   21.410541] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   21.490506] Calibrating delay using timer specific routine.. 3195.61 BogoMIPS (lpj=6391227)
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   21.490554] Security Framework initialized
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   21.490567] SELinux:  Disabled at boot.
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   21.490593] AppArmor: AppArmor initialized
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   21.490602] Failure registering capabilities with primary security module.
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   21.490618] Mount-cache hash table entries: 512
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   21.490866] monitor/mwait feature present.
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   21.490870] using mwait in idle threads.
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   21.490878] CPU: L1 I cache: 32K, L1 D cache: 32K
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   21.490884] CPU: L2 cache: 1024K
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   21.490889] CPU: Physical Processor ID: 0
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   21.490893] CPU: Processor Core ID: 0
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   21.490915] Compat vDSO mapped to ffffe000.
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   21.490938] Checking 'hlt' instruction... OK.
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   21.507255] SMP alternatives: switching to UP code
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   21.510903] Early unpacking initramfs... done
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.309734] ACPI: Core revision 20070126
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.309869] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.425593] CPU0: Intel Genuine Intel(R) CPU           T2060  @ 1.60GHz stepping 0c
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.425628] SMP alternatives: switching to SMP code
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.426974] Booting processor 1/1 eip 3000
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.437206] Initializing CPU#1
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.517592] Calibrating delay using timer specific routine.. 3192.36 BogoMIPS (lpj=6384721)
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.517618] monitor/mwait feature present.
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.517625] CPU: L1 I cache: 32K, L1 D cache: 32K
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.517629] CPU: L2 cache: 1024K
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.517634] CPU: Physical Processor ID: 0
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.517637] CPU: Processor Core ID: 1
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.518375] CPU1: Intel Genuine Intel(R) CPU           T1060  @ 1.60GHz stepping 0c
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.518420] Total of 2 processors activated (6387.97 BogoMIPS).
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.518794] ENABLING IO-APIC IRQs
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.519019] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.665697] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.685710] Brought up 2 CPUs
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.686259] net_namespace: 64 bytes
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.686277] Booting paravirtualized kernel on bare hardware
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.687293] Time: 21:04:26  Date: 07/05/08
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.687350] NET: Registered protocol family 16
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.687758] EISA bus registered
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.687768] ACPI: bus type pci registered
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.688188] PCI: Using configuration type 1
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.688192] Setting up standard PCI resources
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.901585] ACPI: Interpreter enabled
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.901592] ACPI: (supports S0 S3 S4 S5)
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.901616] ACPI: Using IOAPIC for interrupt routing
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.912552] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.915988] PCI: Transparent bridge - 0000:00:13.1
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.947770] ACPI: PCI Interrupt Link [ALKA] (IRQs 16 17 18 19 20 21 22 23) *9, disabled.
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.947938] ACPI: PCI Interrupt Link [ALKB] (IRQs 16 17 18 19 20 21 22 23) *10, disabled.
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.948100] ACPI: PCI Interrupt Link [ALKC] (IRQs 22) *11, disabled.
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.948255] ACPI: PCI Interrupt Link [ALKD] (IRQs 21) *3, disabled.
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.948465] ACPI: PCI Interrupt Link [LNKA] (IRQs *9 10 11 12)
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.948667] ACPI: PCI Interrupt Link [LNKB] (IRQs 9 *10 11 12)
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.948867] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 *11 12)
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.949066] ACPI: PCI Interrupt Link [LNKD] (IRQs 9 10 11 12) *3
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.949311] ACPI: Power Resource [PFAN] (off)
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.949403] Linux Plug and Play Support v0.97 (c) Adam Belay
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.949479] pnp: PnP ACPI init
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.949495] ACPI: bus type pnp registered
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.951568] pnpacpi: exceeded the max number of mem resources: 12
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.953786] pnp: PnP ACPI: found 10 devices
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.953792] ACPI: ACPI bus type pnp unregistered
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.953801] PnPBIOS: Disabled by ACPI PNP
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.954290] PCI: Using ACPI for IRQ routing
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.954296] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.954309] PCI: Cannot allocate resource region 8 of bridge 0000:00:13.1
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.954380] PCI: Cannot allocate resource region 0 of device 0000:05:01.0
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.977228] NET: Registered protocol family 8
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.977233] NET: Registered protocol family 20
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.977369] AppArmor: AppArmor Filesystem Enabled
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.981198] Time: tsc clocksource has been installed.
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.997259] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.997266] system 00:01: iomem range 0xf0012000-0xf0012fff has been reserved
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.997273] system 00:01: iomem range 0xf0013000-0xf0013fff has been reserved
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.997292] system 00:06: iomem range 0x0-0x9ffff could not be reserved
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.997299] system 00:06: iomem range 0xc0000-0xcffff could not be reserved
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.997306] system 00:06: iomem range 0xe0000-0xfffff could not be reserved
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.997312] system 00:06: iomem range 0xe0000000-0xe01010ff has been reserved
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.997319] system 00:06: iomem range 0xe00100ff-0xe00190fe has been reserved
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.997326] system 00:06: iomem range 0xe00700ff-0xe007a0fe has been reserved
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.997333] system 00:06: iomem range 0xe00800ff-0xe00a00fe has been reserved
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.997340] system 00:06: iomem range 0xe01000ff-0xe06000fe could not be reserved
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.997347] system 00:06: iomem range 0xf00120ff-0xf00140fe could not be reserved
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.997354] system 00:06: iomem range 0xffb80000-0xffc7ffff has been reserved
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.997361] system 00:06: iomem range 0xfff00000-0xffffffff could not be reserved
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.997367] system 00:06: iomem range 0xffee0000-0xffefffff has been reserved
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.997380] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.997387] system 00:07: ioport range 0xfe10-0xfe11 has been reserved
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.997393] system 00:07: ioport range 0xfe00-0xfe00 has been reserved
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.997399] system 00:07: ioport range 0x4000-0x407f has been reserved
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   22.997406] system 00:07: ioport range 0x4100-0x411f has been reserved
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   23.028271] PCI: Failed to allocate mem resource #6:10000@c0000000 for 0000:01:00.0
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   23.028277] PCI: Bridge: 0000:00:01.0
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   23.028280]   IO window: disabled.
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   23.028289]   MEM window: c8000000-c8ffffff
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   23.028296]   PREFETCH window: a0000000-bfffffff
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   23.028304] PCI: Bridge: 0000:00:02.0
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   23.028308]   IO window: disabled.
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   23.028315]   MEM window: disabled.
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   23.028321]   PREFETCH window: disabled.
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   23.028329] PCI: Bridge: 0000:00:03.0
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   23.028334]   IO window: 7000-7fff
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   23.028343]   MEM window: c9000000-c90fffff
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   23.028349]   PREFETCH window: disabled.
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   23.028358] PCI: Bridge: 0000:00:13.0
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   23.028361]   IO window: disabled.
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   23.028369]   MEM window: c9100000-c91fffff
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   23.028375]   PREFETCH window: disabled.
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   23.028388] PCI: Bridge: 0000:00:13.1
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   23.028391]   IO window: disabled.
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   23.028399]   MEM window: disabled.
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   23.028405]   PREFETCH window: disabled.
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   23.028469] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 27 (level, low) -> IRQ 16
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   23.028505] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 31 (level, low) -> IRQ 17
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   23.028582] NET: Registered protocol family 2
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   23.069248] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   23.069663] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   23.069872] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   23.070071] TCP: Hash tables configured (established 16384 bind 16384)
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   23.070076] TCP reno registered
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   23.081376] checking if image is initramfs...<7>Switched to high resolution mode on CPU 1
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   23.847247]  it is
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   24.656117] Freeing initrd memory: 7704k freed
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   24.657967] audit: initializing netlink socket (disabled)
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   24.658000] audit(1215291867.024:1): initialized
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   24.662558] VFS: Disk quotas dquot_6.5.1
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   24.662730] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   24.663018] io scheduler noop registered
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   24.663023] io scheduler anticipatory registered
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   24.663028] io scheduler deadline registered
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   24.663053] io scheduler cfq registered (default)
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   24.663083] PCI: VIA PCI bridge detected. Disabling DAC.
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   32.651701] 0000:00:10.4 EHCI: BIOS handoff failed (BIOS bug ?) 01010001
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   32.652066] assign_interrupt_mode Found MSI capability
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   32.652449] assign_interrupt_mode Found MSI capability
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   32.653118] isapnp: Scanning for PnP cards...
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   33.007813] isapnp: No Plug & Play device found
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   33.068858] Real Time Clock Driver v1.12ac
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   33.069090] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   33.071760] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   33.071908] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   33.072120] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   33.074651] i8042.c: Detected active multiplexing controller, rev 1.1.
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   33.075857] serio: i8042 KBD port at 0x60,0x64 irq 1
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   33.075868] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   33.075874] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   33.075880] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   33.075886] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   33.099457] mice: PS/2 mouse device common for all mice
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   33.099706] EISA: Probing bus 0 at eisa.0
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   33.099736] Cannot allocate resource for EISA slot 4
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   33.099747] Cannot allocate resource for EISA slot 6
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   33.099753] Cannot allocate resource for EISA slot 7
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   33.099763] EISA: Detected 0 cards.
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   33.099770] cpuidle: using governor ladder
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   33.099774] cpuidle: using governor menu
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   33.099975] NET: Registered protocol family 1
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   33.100035] Using IPI No-Shortcut mode
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   33.100103] registered taskstats version 1
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   33.100328]   Magic number: 0:123:95
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   33.100525] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   33.100529] EDD information not available.
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   33.100835] Freeing unused kernel memory: 364k freed
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   33.127622] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   34.553037] fuse init (API version 7.9)
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   34.614188] ACPI: Fan [FAN] (on)
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   34.633204] ACPI: SSDT 1BE99A9F, 01E8 (r1  PmRef  Cpu0Ist     3000 INTL 20050228)
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   34.633875] ACPI: SSDT 1BE9982A, 01F0 (r1  PmRef  Cpu0Cst     3001 INTL 20050228)
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   34.634704] ACPI: CPU0 (power states: C1[C1] C2[C2])
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   34.634715] ACPI: Processor [CPU0] (supports 16 throttling states)
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   34.635193] ACPI: SSDT 1BE99C87, 0087 (r1  PmRef  Cpu1Ist     3000 INTL 20050228)
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   34.635524] ACPI: SSDT 1BE99A1A, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050228)
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   34.636236] ACPI: CPU1 (power states: C1[C1] C2[C2])
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   34.636247] ACPI: Processor [CPU1] (supports 16 throttling states)
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   34.636278] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   34.636305] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   35.376102] ACPI: Thermal Zone [THRM] (64 C)
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   36.285767] SCSI subsystem initialized
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   36.356704] usbcore: registered new interface driver usbfs
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   36.356755] usbcore: registered new interface driver hub
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   36.360783] usbcore: registered new device driver usb
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   36.376184] USB Universal Host Controller Interface driver v3.0
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   36.376425] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 20 (level, low) -> IRQ 18
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   36.376458] uhci_hcd 0000:00:10.0: UHCI Host Controller
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   36.377047] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   36.377097] uhci_hcd 0000:00:10.0: irq 18, io base 0x00006020
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   36.377401] usb usb1: configuration #1 chosen from 1 choice
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   36.377455] hub 1-0:1.0: USB hub found
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   36.377468] hub 1-0:1.0: 2 ports detected
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   36.424344] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   36.480298] ACPI: PCI Interrupt 0000:00:10.1[B] -> GSI 22 (level, low) -> IRQ 19
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   36.480332] uhci_hcd 0000:00:10.1: UHCI Host Controller
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   36.480389] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   36.480437] uhci_hcd 0000:00:10.1: irq 19, io base 0x00006040
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   36.480691] usb usb2: configuration #1 chosen from 1 choice
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   36.480743] hub 2-0:1.0: USB hub found
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   36.480755] hub 2-0:1.0: 2 ports detected
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   36.584134] ACPI: PCI Interrupt 0000:00:10.2[C] -> GSI 21 (level, low) -> IRQ 20
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   36.584168] uhci_hcd 0000:00:10.2: UHCI Host Controller
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   36.584226] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   36.584266] uhci_hcd 0000:00:10.2: irq 20, io base 0x00006060
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   36.584501] usb usb3: configuration #1 chosen from 1 choice
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   36.584552] hub 3-0:1.0: USB hub found
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   36.584564] hub 3-0:1.0: 2 ports detected
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   36.688034] ACPI: PCI Interrupt 0000:00:10.3[D] -> GSI 23 (level, low) -> IRQ 21
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   36.688072] uhci_hcd 0000:00:10.3: UHCI Host Controller
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   36.688127] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   36.688172] uhci_hcd 0000:00:10.3: irq 21, io base 0x00006080
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   36.688427] usb usb4: configuration #1 chosen from 1 choice
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   36.688480] hub 4-0:1.0: USB hub found
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   36.688493] hub 4-0:1.0: 2 ports detected
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   36.792012] ACPI: PCI Interrupt 0000:00:0f.0[B] -> GSI 21 (level, low) -> IRQ 20
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   36.792085] sata_via 0000:00:0f.0: routed to hard irq line 10
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   36.793826] scsi0 : sata_via
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   36.793965] scsi1 : sata_via
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   36.794318] ata1: SATA max UDMA/133 cmd 0x60b8 ctl 0x60b0 bmdma 0x6010 irq 20
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   36.794325] ata2: SATA max UDMA/133 cmd 0x6008 ctl 0x6004 bmdma 0x6018 irq 20
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   36.995478] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   37.160769] ata1.00: ATA-8: FUJITSU MHW2080BH, 00000012, max UDMA/100
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   37.160780] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   37.175799] ata1.00: configured for UDMA/100
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   37.380085] ata2: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   37.391475] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHW2080B 0000 PQ: 0 ANSI: 5
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   37.391751] ACPI: PCI Interrupt 0000:00:10.4[C] -> GSI 21 (level, low) -> IRQ 20
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   37.391789] ehci_hcd 0000:00:10.4: EHCI Host Controller
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   37.391854] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   37.391917] ehci_hcd 0000:00:10.4: irq 20, io mem 0xc9400000
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   37.403072] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   37.403324] usb usb5: configuration #1 chosen from 1 choice
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   37.403379] hub 5-0:1.0: USB hub found
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   37.403393] hub 5-0:1.0: 8 ports detected
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   37.507764] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 23 (level, low) -> IRQ 21
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   37.512205] eth0: VIA Rhine II at 0xc9400400, 00:14:0b:0b:74:0e, IRQ 21.
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   37.512923] eth0: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000.
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   37.513766] scsi2 : pata_via
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   37.513875] scsi3 : pata_via
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   37.515213] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x60a0 irq 14
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   37.515220] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x60a8 irq 15
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   37.537666] Driver 'sd' needs updating - please use bus_type methods
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   37.537843] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   37.537872] sd 0:0:0:0: [sda] Write Protect is off
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   37.537918] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   37.538032] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   37.538055] sd 0:0:0:0: [sda] Write Protect is off
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   37.538097] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   37.538104]  sda: sda1 sda2 <<6>ata4.00: ATAPI: HL-DT-ST DVDRAM GSA-T10N, PW02, max UDMA/33
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   37.870419]  sda5 >
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   37.870665] sd 0:0:0:0: [sda] Attached SCSI disk
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   37.882887] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   38.006817] ata4.00: configured for UDMA/33
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   38.010691] scsi 3:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T10N  PW02 PQ: 0 ANSI: 5
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   38.010895] scsi 3:0:0:0: Attached scsi generic sg1 type 5
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   38.027021] Driver 'sr' needs updating - please use bus_type methods
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   38.045205] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   38.045215] Uniform CD-ROM driver Revision: 3.20
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   38.300455] Attempting manual resume
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   38.329752] EXT3-fs: INFO: recovery required on readonly filesystem.
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   38.329761] EXT3-fs: write access will be enabled during recovery.
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   41.745398] kjournald starting.  Commit interval 5 seconds
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   41.745427] EXT3-fs: sda1: orphan cleanup on readonly fs
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   41.745535] EXT3-fs: sda1: 2 orphan inodes deleted
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   41.745539] EXT3-fs: recovery complete.
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   41.750417] EXT3-fs: mounted filesystem with ordered data mode.
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   50.631331] Linux agpgart interface v0.102
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   50.701255] agpgart: Detected VIA P4M900 chipset
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   50.723033] agpgart: AGP aperture is 128M @ 0xc0000000
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   50.895152] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   50.964271] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   51.523714] input: Power Button (FF) as /devices/virtual/input/input2
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   51.546235] ACPI: Power Button (FF) [PWRF]
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   51.546486] input: Power Button (CM) as /devices/virtual/input/input3
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   51.574206] ACPI: Power Button (CM) [PWRB]
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   51.574442] input: Lid Switch as /devices/virtual/input/input4
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   51.574550] ACPI: Lid Switch [LID]
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   51.639547] ACPI: AC Adapter [ACAD] (on-line)
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   51.786079] ACPI: Battery Slot [BAT0] (battery present)
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   53.940827] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:1a/LNXVIDEO:00/input/input5
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   53.971861] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   54.011474] input: PC Speaker as /devices/platform/pcspkr/input/input6
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   54.951263] ath_hal: module license 'Proprietary' taints kernel.
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   54.978405] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   55.079317] wlan: 0.9.4
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   55.112263] ath_pci: 0.9.4
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   55.112403] ACPI: PCI Interrupt 0000:05:01.0[A] -> GSI 18 (level, low) -> IRQ 22
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   55.743784] input: PS/2 Mouse as /devices/virtual/input/input7
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   55.816593] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio4/input/input8
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   55.850917] ath_rate_sample: 1.2 (0.9.4)
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   55.851897] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   55.851910] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   55.851931] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   55.851940] wifi0: mac 7.8 phy 4.5 radio 5.6
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   55.851951] wifi0: Use hw queue 1 for WME_AC_BE traffic
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   55.851956] wifi0: Use hw queue 0 for WME_AC_BK traffic
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   55.851960] wifi0: Use hw queue 2 for WME_AC_VI traffic
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   55.851965] wifi0: Use hw queue 3 for WME_AC_VO traffic
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   55.851970] wifi0: Use hw queue 8 for CAB traffic
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   55.851974] wifi0: Use hw queue 9 for beacons
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   55.952278] wifi0: Atheros 5212: mem=0x30000000, irq=22
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   56.017237] ACPI: PCI Interrupt 0000:04:01.0[A] -> GSI 17 (level, low) -> IRQ 23
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   58.470423] lp: driver loaded but no devices found
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   58.696845] Adding 1309256k swap on /dev/sda5.  Priority:-1 extents:1 across:1309256k
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   59.272285] EXT3 FS on sda1, internal journal
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   60.850328] ip_tables: (C) 2000-2006 Netfilter Core Team
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   66.423476] Clocksource tsc unstable (delta = 4687184193 ns)
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   66.426687] Time: acpi_pm clocksource has been installed.
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   66.633397] No dock devices found.
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   67.836250] apm: BIOS not found.
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   67.997995] ppdev: user-space parallel port driver
Jul  5 22:05:11 nyxtwilight-laptop kernel: [   68.092719] audit(1215291911.822:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5092 profile="/usr/sbin/cupsd" namespace="default"
Jul  5 22:05:11 nyxtwilight-laptop dhcdbd: Started up.
Jul  5 22:05:12 nyxtwilight-laptop kernel: [   69.193824] eth0: link down
Jul  5 22:05:13 nyxtwilight-laptop kernel: [   69.343158] Bluetooth: Core ver 2.11
Jul  5 22:05:13 nyxtwilight-laptop kernel: [   69.344024] NET: Registered protocol family 31
Jul  5 22:05:13 nyxtwilight-laptop kernel: [   69.344031] Bluetooth: HCI device and connection manager initialized
Jul  5 22:05:13 nyxtwilight-laptop kernel: [   69.344040] Bluetooth: HCI socket layer initialized
Jul  5 22:05:13 nyxtwilight-laptop kernel: [   69.403179] Bluetooth: L2CAP ver 2.9
Jul  5 22:05:13 nyxtwilight-laptop kernel: [   69.403191] Bluetooth: L2CAP socket layer initialized
Jul  5 22:05:13 nyxtwilight-laptop kernel: [   69.474901] Bluetooth: RFCOMM socket layer initialized
Jul  5 22:05:13 nyxtwilight-laptop kernel: [   69.474935] Bluetooth: RFCOMM TTY layer initialized
Jul  5 22:05:13 nyxtwilight-laptop kernel: [   69.474937] Bluetooth: RFCOMM ver 1.8
Jul  5 22:05:17 nyxtwilight-laptop kernel: [   73.540510] [drm] Initialized drm 1.0.1 20051102
Jul  5 22:05:17 nyxtwilight-laptop kernel: [   73.574761] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 24
Jul  5 22:05:17 nyxtwilight-laptop kernel: [   73.576687] [drm] Initialized via_chrome9 1.1.2 Thu, 14 Apr 2006 10:00:00 +0800 on minor 0: 
Jul  5 22:05:17 nyxtwilight-laptop kernel: [   73.578916] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
Jul  5 22:05:17 nyxtwilight-laptop kernel: [   73.579857] agpgart: Xorg tried to set rate=x12. Setting to AGP3 x8 mode.
Jul  5 22:05:17 nyxtwilight-laptop kernel: [   73.580783] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
Jul  5 22:05:17 nyxtwilight-laptop kernel: [   73.581853] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
Jul  5 22:05:18 nyxtwilight-laptop kernel: [   74.308818] [drm] pci_driver->suspend is set by  SaveAGPRegisters
Jul  5 22:05:18 nyxtwilight-laptop kernel: [   74.308843] [drm] pci_driver->resume is set by  RestoreAGPRegisters
Jul  5 22:05:18 nyxtwilight-laptop kernel: [   74.308845] [drm] the pci_driver have already been associated with pci_device
Jul  5 22:05:18 nyxtwilight-laptop kernel: [   74.308853] [drm] DMA buffer initialized finished. Use AGP Ring Buffer type!
Jul  5 22:05:18 nyxtwilight-laptop kernel: [   74.308856] [drm] Total AGP DMA buffer size = 16777216 bytes. 
Jul  5 22:05:24 nyxtwilight-laptop kernel: [   80.716448] hda-intel: Invalid position buffer, using LPIB read method instead.
Jul  5 22:09:27 nyxtwilight-laptop kernel: [  323.690697] gdm[5748]: segfault at 23fd6e74 eip b7888635 esp bfa319c0 error 4
Jul  5 22:09:27 nyxtwilight-laptop kernel: [  323.691295] gdm[5406]: segfault at 085733e8 eip b7888635 esp bfa31d80 error 4
Jul  5 22:09:28 nyxtwilight-laptop exiting on signal 15
Jul  5 22:10:43 nyxtwilight-laptop syslogd 1.5.0#1ubuntu1: restart.
Jul  5 22:10:43 nyxtwilight-laptop kernel: Inspecting /boot/System.map-2.6.24-16-generic
Jul  5 22:10:43 nyxtwilight-laptop kernel: Loaded 27704 symbols from /boot/System.map-2.6.24-16-generic.
Jul  5 22:10:43 nyxtwilight-laptop kernel: Symbols match kernel version 2.6.24.
Jul  5 22:10:43 nyxtwilight-laptop kernel: Loaded 16772 symbols from 81 modules.
Jul  5 22:10:43 nyxtwilight-laptop kernel: [    0.000000] Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
Jul  5 22:10:43 nyxtwilight-laptop kernel: [    0.000000] BIOS-provided physical RAM map:
Jul  5 22:10:43 nyxtwilight-laptop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
Jul  5 22:10:43 nyxtwilight-laptop kernel: [    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
Jul  5 22:10:43 nyxtwilight-laptop kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Jul  5 22:10:43 nyxtwilight-laptop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000001be90000 (usable)
Jul  5 22:10:43 nyxtwilight-laptop kernel: [    0.000000]  BIOS-e820: 000000001be90000 - 000000001be9f000 (ACPI data)
Jul  5 22:10:43 nyxtwilight-laptop kernel: [    0.000000]  BIOS-e820: 000000001be9f000 - 000000001bf00000 (ACPI NVS)
Jul  5 22:10:43 nyxtwilight-laptop kernel: [    0.000000]  BIOS-e820: 000000001bf00000 - 0000000020000000 (reserved)
Jul  5 22:10:43 nyxtwilight-laptop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Jul  5 22:10:43 nyxtwilight-laptop kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Jul  5 22:10:43 nyxtwilight-laptop kernel: [    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
Jul  5 22:10:43 nyxtwilight-laptop kernel: [    0.000000] 0MB HIGHMEM available.
Jul  5 22:10:43 nyxtwilight-laptop kernel: [    0.000000] 446MB LOWMEM available.
Jul  5 22:10:43 nyxtwilight-laptop kernel: [    0.000000] found SMP MP-table at 000f7480
Jul  5 22:10:43 nyxtwilight-laptop kernel: [    0.000000] Zone PFN ranges:
Jul  5 22:10:43 nyxtwilight-laptop kernel: [    0.000000]   DMA             0 ->     4096
Jul  5 22:10:43 nyxtwilight-laptop kernel: [    0.000000]   Normal       4096 ->   114320
Jul  5 22:10:43 nyxtwilight-laptop kernel: [    0.000000]   HighMem    114320 ->   114320
Jul  5 22:10:43 nyxtwilight-laptop kernel: [    0.000000] Movable zone start PFN for each node
Jul  5 22:10:43 nyxtwilight-laptop kernel: [    0.000000] early_node_map[1] active PFN ranges
Jul  5 22:10:43 nyxtwilight-laptop kernel: [    0.000000]     0:        0 ->   114320
Jul  5 22:10:43 nyxtwilight-laptop kernel: [    0.000000] DMI present.
Jul  5 22:10:43 nyxtwilight-laptop kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F73D0 checksum 0
Jul  5 22:10:43 nyxtwilight-laptop kernel: [    0.000000] ACPI: RSDP 000F73D0, 0014 (r0 PTLTD )
Jul  5 22:10:43 nyxtwilight-laptop kernel: [    0.000000] ACPI: RSDT 1BE992D9, 0038 (r1 FSC    PC        6040000  LTP        0)
Jul  5 22:10:43 nyxtwilight-laptop kernel: [    0.000000] ACPI: FACP 1BE9ED70, 0074 (r1 VN896  PTLTW     6040000 PTL_    F4240)
Jul  5 22:10:43 nyxtwilight-laptop kernel: [    0.000000] ACPI: DSDT 1BE99D0E, 5062 (r1  FIC   LM10W     6040000 MSFT  100000E)
Jul  5 22:10:43 nyxtwilight-laptop kernel: [    0.000000] ACPI: FACS 1BE9FFC0, 0040
Jul  5 22:10:43 nyxtwilight-laptop kernel: [    0.000000] ACPI: APIC 1BE9EDE4, 006A (r1 PTLTD  ^I APIC    6040000  LTP        0)
Jul  5 22:10:43 nyxtwilight-laptop kernel: [    0.000000] ACPI: MCFG 1BE9EE4E, 003C (r1 PTLTD    MCFG    6040000  LTP        0)
Jul  5 22:10:43 nyxtwilight-laptop kernel: [    0.000000] ACPI: SLIC 1BE9EE8A, 0176 (r1 FSC    PC        6040000             0)
Jul  5 22:10:43 nyxtwilight-laptop kernel: [    0.000000] ACPI: SSDT 1BE99311, 0519 (r1  PmRef    CpuPm     3000 INTL 20050228)
Jul  5 22:10:43 nyxtwilight-laptop kernel: [    0.000000] ACPI: DMI detected: Fujitsu Siemens
Jul  5 22:10:43 nyxtwilight-laptop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x4008
Jul  5 22:10:43 nyxtwilight-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jul  5 22:10:43 nyxtwilight-laptop kernel: [    0.000000] Processor #0 6:14 APIC version 20
Jul  5 22:10:43 nyxtwilight-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Jul  5 22:10:43 nyxtwilight-laptop kernel: [    0.000000] Processor #1 6:14 APIC version 20
Jul  5 22:10:43 nyxtwilight-laptop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Jul  5 22:10:43 nyxtwilight-laptop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Jul  5 22:10:43 nyxtwilight-laptop kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Jul  5 22:10:43 nyxtwilight-laptop kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
Jul  5 22:10:43 nyxtwilight-laptop kernel: [    0.000000] ACPI: IOAPIC (id[0x03] address[0xfecc0000] gsi_base[24])
Jul  5 22:10:43 nyxtwilight-laptop kernel: [    0.000000] IOAPIC[1]: apic_id 3, version 3, address 0xfecc0000, GSI 24-47
Jul  5 22:10:43 nyxtwilight-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jul  5 22:10:43 nyxtwilight-laptop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 2 I/O APICs
Jul  5 22:10:43 nyxtwilight-laptop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jul  5 22:10:43 nyxtwilight-laptop kernel: [    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
Jul  5 22:10:43 nyxtwilight-laptop kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009d000 - 000000000009e000
Jul  5 22:10:43 nyxtwilight-laptop kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009e000 - 00000000000a0000
Jul  5 22:10:43 nyxtwilight-laptop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
Jul  5 22:10:43 nyxtwilight-laptop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
Jul  5 22:10:43 nyxtwilight-laptop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 113427
Jul  5 22:10:43 nyxtwilight-laptop kernel: [    0.000000] Kernel command line: root=UUID=270f4baf-9a32-4ebc-af92-f1e8eb400da6 ro quiet splash
Jul  5 22:10:43 nyxtwilight-laptop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Jul  5 22:10:43 nyxtwilight-laptop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Jul  5 22:10:43 nyxtwilight-laptop kernel: [    0.000000] Initializing CPU#0
Jul  5 22:10:43 nyxtwilight-laptop kernel: [    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
Jul  5 22:10:43 nyxtwilight-laptop kernel: [    0.000000] Detected 1596.029 MHz processor.
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   23.788515] Console: colour VGA+ 80x25
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   23.788523] console [tty0] enabled
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   23.788827] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   23.789201] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   23.807473] Memory: 440860k/457280k available (2157k kernel code, 15836k reserved, 998k data, 364k init, 0k highmem)
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   23.807490] virtual kernel memory layout:
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   23.807492]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   23.807495]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   23.807498]     vmalloc : 0xdc800000 - 0xff7fe000   ( 559 MB)
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   23.807501]     lowmem  : 0xc0000000 - 0xdbe90000   ( 446 MB)
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   23.807504]       .init : 0xc041b000 - 0xc0476000   ( 364 kB)
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   23.807506]       .data : 0xc031b5a4 - 0xc0414dc4   ( 998 kB)
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   23.807509]       .text : 0xc0100000 - 0xc031b5a4   (2157 kB)
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   23.807517] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   23.807582] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   23.887546] Calibrating delay using timer specific routine.. 3195.69 BogoMIPS (lpj=6391389)
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   23.887596] Security Framework initialized
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   23.887608] SELinux:  Disabled at boot.
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   23.887635] AppArmor: AppArmor initialized
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   23.887643] Failure registering capabilities with primary security module.
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   23.887660] Mount-cache hash table entries: 512
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   23.887908] monitor/mwait feature present.
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   23.887912] using mwait in idle threads.
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   23.887920] CPU: L1 I cache: 32K, L1 D cache: 32K
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   23.887925] CPU: L2 cache: 1024K
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   23.887931] CPU: Physical Processor ID: 0
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   23.887934] CPU: Processor Core ID: 0
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   23.887957] Compat vDSO mapped to ffffe000.
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   23.887981] Checking 'hlt' instruction... OK.
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   23.904295] SMP alternatives: switching to UP code
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   23.907941] Early unpacking initramfs... done
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   24.706627] ACPI: Core revision 20070126
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   24.706746] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   24.822463] CPU0: Intel Genuine Intel(R) CPU           T2060  @ 1.60GHz stepping 0c
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   24.822498] SMP alternatives: switching to SMP code
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   24.823848] Booting processor 1/1 eip 3000
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   24.834081] Initializing CPU#1
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   24.914633] Calibrating delay using timer specific routine.. 3192.35 BogoMIPS (lpj=6384704)
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   24.914659] monitor/mwait feature present.
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   24.914665] CPU: L1 I cache: 32K, L1 D cache: 32K
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   24.914669] CPU: L2 cache: 1024K
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   24.914674] CPU: Physical Processor ID: 0
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   24.914677] CPU: Processor Core ID: 1
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   24.915450] CPU1: Intel Genuine Intel(R) CPU           T1060  @ 1.60GHz stepping 0c
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   24.915494] Total of 2 processors activated (6388.04 BogoMIPS).
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   24.915869] ENABLING IO-APIC IRQs
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   24.916094] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.062740] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.082757] Brought up 2 CPUs
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.083305] net_namespace: 64 bytes
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.083323] Booting paravirtualized kernel on bare hardware
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.084340] Time: 21:10:01  Date: 07/05/08
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.084397] NET: Registered protocol family 16
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.084805] EISA bus registered
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.084814] ACPI: bus type pci registered
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.085233] PCI: Using configuration type 1
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.085237] Setting up standard PCI resources
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.298628] ACPI: Interpreter enabled
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.298635] ACPI: (supports S0 S3 S4 S5)
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.298660] ACPI: Using IOAPIC for interrupt routing
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.309597] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.313031] PCI: Transparent bridge - 0000:00:13.1
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.344807] ACPI: PCI Interrupt Link [ALKA] (IRQs 16 17 18 19 20 21 22 23) *9, disabled.
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.344975] ACPI: PCI Interrupt Link [ALKB] (IRQs 16 17 18 19 20 21 22 23) *10, disabled.
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.345137] ACPI: PCI Interrupt Link [ALKC] (IRQs 22) *11, disabled.
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.345292] ACPI: PCI Interrupt Link [ALKD] (IRQs 21) *3, disabled.
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.345503] ACPI: PCI Interrupt Link [LNKA] (IRQs *9 10 11 12)
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.345705] ACPI: PCI Interrupt Link [LNKB] (IRQs 9 *10 11 12)
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.345905] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 *11 12)
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.346104] ACPI: PCI Interrupt Link [LNKD] (IRQs 9 10 11 12) *3
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.346348] ACPI: Power Resource [PFAN] (off)
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.346438] Linux Plug and Play Support v0.97 (c) Adam Belay
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.346512] pnp: PnP ACPI init
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.346528] ACPI: bus type pnp registered
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.348606] pnpacpi: exceeded the max number of mem resources: 12
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.350826] pnp: PnP ACPI: found 10 devices
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.350831] ACPI: ACPI bus type pnp unregistered
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.350840] PnPBIOS: Disabled by ACPI PNP
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.351330] PCI: Using ACPI for IRQ routing
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.351337] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.351350] PCI: Cannot allocate resource region 8 of bridge 0000:00:13.1
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.351422] PCI: Cannot allocate resource region 0 of device 0000:05:01.0
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.374268] NET: Registered protocol family 8
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.374273] NET: Registered protocol family 20
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.374409] AppArmor: AppArmor Filesystem Enabled
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.378239] Time: tsc clocksource has been installed.
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.394299] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.394306] system 00:01: iomem range 0xf0012000-0xf0012fff has been reserved
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.394313] system 00:01: iomem range 0xf0013000-0xf0013fff has been reserved
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.394333] system 00:06: iomem range 0x0-0x9ffff could not be reserved
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.394339] system 00:06: iomem range 0xc0000-0xcffff could not be reserved
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.394346] system 00:06: iomem range 0xe0000-0xfffff could not be reserved
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.394353] system 00:06: iomem range 0xe0000000-0xe01010ff has been reserved
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.394359] system 00:06: iomem range 0xe00100ff-0xe00190fe has been reserved
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.394366] system 00:06: iomem range 0xe00700ff-0xe007a0fe has been reserved
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.394373] system 00:06: iomem range 0xe00800ff-0xe00a00fe has been reserved
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.394380] system 00:06: iomem range 0xe01000ff-0xe06000fe could not be reserved
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.394387] system 00:06: iomem range 0xf00120ff-0xf00140fe could not be reserved
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.394394] system 00:06: iomem range 0xffb80000-0xffc7ffff has been reserved
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.394401] system 00:06: iomem range 0xfff00000-0xffffffff could not be reserved
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.394408] system 00:06: iomem range 0xffee0000-0xffefffff has been reserved
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.394420] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.394427] system 00:07: ioport range 0xfe10-0xfe11 has been reserved
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.394433] system 00:07: ioport range 0xfe00-0xfe00 has been reserved
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.394440] system 00:07: ioport range 0x4000-0x407f has been reserved
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.394446] system 00:07: ioport range 0x4100-0x411f has been reserved
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.425311] PCI: Failed to allocate mem resource #6:10000@c0000000 for 0000:01:00.0
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.425317] PCI: Bridge: 0000:00:01.0
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.425320]   IO window: disabled.
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.425329]   MEM window: c8000000-c8ffffff
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.425336]   PREFETCH window: a0000000-bfffffff
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.425344] PCI: Bridge: 0000:00:02.0
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.425347]   IO window: disabled.
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.425355]   MEM window: disabled.
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.425361]   PREFETCH window: disabled.
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.425368] PCI: Bridge: 0000:00:03.0
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.425374]   IO window: 7000-7fff
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.425383]   MEM window: c9000000-c90fffff
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.425389]   PREFETCH window: disabled.
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.425398] PCI: Bridge: 0000:00:13.0
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.425401]   IO window: disabled.
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.425409]   MEM window: c9100000-c91fffff
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.425415]   PREFETCH window: disabled.
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.425428] PCI: Bridge: 0000:00:13.1
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.425432]   IO window: disabled.
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.425439]   MEM window: disabled.
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.425445]   PREFETCH window: disabled.
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.425509] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 27 (level, low) -> IRQ 16
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.425545] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 31 (level, low) -> IRQ 17
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.425621] NET: Registered protocol family 2
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.466290] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.466707] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.466915] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.467114] TCP: Hash tables configured (established 16384 bind 16384)
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.467120] TCP reno registered
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   25.478417] checking if image is initramfs...<7>Switched to high resolution mode on CPU 1
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   26.244312]  it is
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   27.053096] Freeing initrd memory: 7704k freed
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   27.054950] audit: initializing netlink socket (disabled)
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   27.054983] audit(1215292203.020:1): initialized
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   27.059543] VFS: Disk quotas dquot_6.5.1
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   27.059716] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   27.060004] io scheduler noop registered
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   27.060009] io scheduler anticipatory registered
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   27.060013] io scheduler deadline registered
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   27.060038] io scheduler cfq registered (default)
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   27.060067] PCI: VIA PCI bridge detected. Disabling DAC.
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   35.048713] 0000:00:10.4 EHCI: BIOS handoff failed (BIOS bug ?) 01010001
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   35.049079] assign_interrupt_mode Found MSI capability
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   35.049461] assign_interrupt_mode Found MSI capability
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   35.050127] isapnp: Scanning for PnP cards...
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   35.404823] isapnp: No Plug & Play device found
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   35.466567] Real Time Clock Driver v1.12ac
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   35.466806] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   35.469408] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   35.469559] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   35.469769] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   35.472191] i8042.c: Detected active multiplexing controller, rev 1.1.
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   35.473400] serio: i8042 KBD port at 0x60,0x64 irq 1
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   35.473410] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   35.473416] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   35.473422] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   35.473428] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   35.492631] mice: PS/2 mouse device common for all mice
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   35.492873] EISA: Probing bus 0 at eisa.0
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   35.492904] Cannot allocate resource for EISA slot 4
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   35.492915] Cannot allocate resource for EISA slot 6
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   35.492921] Cannot allocate resource for EISA slot 7
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   35.492932] EISA: Detected 0 cards.
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   35.492938] cpuidle: using governor ladder
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   35.492942] cpuidle: using governor menu
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   35.493148] NET: Registered protocol family 1
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   35.493207] Using IPI No-Shortcut mode
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   35.493285] registered taskstats version 1
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   35.493523]   Magic number: 0:226:196
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   35.493617]   hash matches device ttys8
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   35.493641]   hash matches device ttypb
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   35.493843] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   35.493848] EDD information not available.
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   35.494150] Freeing unused kernel memory: 364k freed
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   35.520725] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   36.959040] fuse init (API version 7.9)
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   37.041856] ACPI: Fan [FAN] (on)
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   37.056862] ACPI: SSDT 1BE99A9F, 01E8 (r1  PmRef  Cpu0Ist     3000 INTL 20050228)
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   37.057540] ACPI: SSDT 1BE9982A, 01F0 (r1  PmRef  Cpu0Cst     3001 INTL 20050228)
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   37.058387] ACPI: CPU0 (power states: C1[C1] C2[C2])
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   37.058398] ACPI: Processor [CPU0] (supports 16 throttling states)
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   37.058896] ACPI: SSDT 1BE99C87, 0087 (r1  PmRef  Cpu1Ist     3000 INTL 20050228)
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   37.059227] ACPI: SSDT 1BE99A1A, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050228)
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   37.059954] ACPI: CPU1 (power states: C1[C1] C2[C2])
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   37.059966] ACPI: Processor [CPU1] (supports 16 throttling states)
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   37.059997] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   37.060021] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   37.801084] ACPI: Thermal Zone [THRM] (64 C)
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   38.665980] SCSI subsystem initialized
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   38.764083] ACPI: PCI Interrupt 0000:00:0f.0[B] -> GSI 21 (level, low) -> IRQ 18
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   38.764200] ACPI: PCI interrupt for device 0000:00:0f.0 disabled
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   38.802091] scsi0 : pata_via
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   38.815131] scsi1 : pata_via
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   38.816491] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x60a0 irq 14
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   38.816498] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x60a8 irq 15
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   38.831104] usbcore: registered new interface driver usbfs
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   38.831158] usbcore: registered new interface driver hub
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   38.841059] usbcore: registered new device driver usb
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   38.859454] USB Universal Host Controller Interface driver v3.0
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   38.934519] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   39.133186] ata2.00: ATAPI: HL-DT-ST DVDRAM GSA-T10N, PW02, max UDMA/33
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   39.304880] ata2.00: configured for UDMA/33
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   39.308791] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T10N  PW02 PQ: 0 ANSI: 5
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   39.309112] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 23 (level, low) -> IRQ 19
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   39.313691] eth0: VIA Rhine II at 0xc9400400, 00:14:0b:0b:74:0e, IRQ 19.
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   39.314409] eth0: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000.
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   39.314505] ACPI: PCI Interrupt 0000:00:0f.0[B] -> GSI 21 (level, low) -> IRQ 18
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   39.314582] sata_via 0000:00:0f.0: routed to hard irq line 10
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   39.314987] scsi2 : sata_via
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   39.316304] scsi3 : sata_via
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   39.316718] ata3: SATA max UDMA/133 cmd 0x60b8 ctl 0x60b0 bmdma 0x6010 irq 18
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   39.316725] ata4: SATA max UDMA/133 cmd 0x6008 ctl 0x6004 bmdma 0x6018 irq 18
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   39.520349] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   39.684661] ata3.00: ATA-8: FUJITSU MHW2080BH, 00000012, max UDMA/100
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   39.684671] ata3.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   39.701660] ata3.00: configured for UDMA/100
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   39.807501] Driver 'sr' needs updating - please use bus_type methods
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   39.826181] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   39.826192] Uniform CD-ROM driver Revision: 3.20
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   39.838477] sr 1:0:0:0: Attached scsi generic sg0 type 5
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   39.904980] ata4: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   39.916321] scsi 2:0:0:0: Direct-Access     ATA      FUJITSU MHW2080B 0000 PQ: 0 ANSI: 5
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   39.916494] scsi 2:0:0:0: Attached scsi generic sg1 type 0
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   39.917223] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 20 (level, low) -> IRQ 20
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   39.917252] uhci_hcd 0000:00:10.0: UHCI Host Controller
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   39.917765] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   39.917816] uhci_hcd 0000:00:10.0: irq 20, io base 0x00006020
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   39.918126] usb usb1: configuration #1 chosen from 1 choice
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   39.918180] hub 1-0:1.0: USB hub found
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   39.918193] hub 1-0:1.0: 2 ports detected
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   39.934250] Driver 'sd' needs updating - please use bus_type methods
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   39.934435] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   39.934466] sd 2:0:0:0: [sda] Write Protect is off
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   39.934512] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   39.934616] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   39.934639] sd 2:0:0:0: [sda] Write Protect is off
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   39.934694] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   39.934703]  sda: sda1 sda2 <<6>ACPI: PCI Interrupt 0000:00:10.1[B] -> GSI 22 (level, low) -> IRQ 21
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   40.020131] uhci_hcd 0000:00:10.1: UHCI Host Controller
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   40.020183] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   40.020224] uhci_hcd 0000:00:10.1: irq 21, io base 0x00006040
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   40.020473] usb usb2: configuration #1 chosen from 1 choice
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   40.020527] hub 2-0:1.0: USB hub found
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   40.020539] hub 2-0:1.0: 2 ports detected
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   40.124958] ACPI: PCI Interrupt 0000:00:10.2[C] -> GSI 21 (level, low) -> IRQ 18
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   40.124989] uhci_hcd 0000:00:10.2: UHCI Host Controller
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   40.125044] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   40.125078] uhci_hcd 0000:00:10.2: irq 18, io base 0x00006060
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   40.125306] usb usb3: configuration #1 chosen from 1 choice
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   40.125357] hub 3-0:1.0: USB hub found
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   40.125369] hub 3-0:1.0: 2 ports detected
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   40.228843] ACPI: PCI Interrupt 0000:00:10.3[D] -> GSI 23 (level, low) -> IRQ 19
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   40.228873] uhci_hcd 0000:00:10.3: UHCI Host Controller
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   40.228925] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   40.228965] uhci_hcd 0000:00:10.3: irq 19, io base 0x00006080
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   40.229199] usb usb4: configuration #1 chosen from 1 choice
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   40.229250] hub 4-0:1.0: USB hub found
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   40.229262] hub 4-0:1.0: 2 ports detected
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   40.266937]  sda5 >
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   40.267151] sd 2:0:0:0: [sda] Attached SCSI disk
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   40.333177] ACPI: PCI Interrupt 0000:00:10.4[C] -> GSI 21 (level, low) -> IRQ 18
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   40.333213] ehci_hcd 0000:00:10.4: EHCI Host Controller
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   40.333269] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   40.333338] ehci_hcd 0000:00:10.4: irq 18, io mem 0xc9400000
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   40.344693] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   40.344982] usb usb5: configuration #1 chosen from 1 choice
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   40.345043] hub 5-0:1.0: USB hub found
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   40.345057] hub 5-0:1.0: 8 ports detected
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   40.576774] Attempting manual resume
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   40.603193] kjournald starting.  Commit interval 5 seconds
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   40.603227] EXT3-fs: mounted filesystem with ordered data mode.
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   49.579587] Linux agpgart interface v0.102
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   49.702223] agpgart: Detected VIA P4M900 chipset
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   49.722532] agpgart: AGP aperture is 128M @ 0xc0000000
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   49.841570] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   49.943469] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   50.465895] input: Power Button (FF) as /devices/virtual/input/input2
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   50.493673] ACPI: Power Button (FF) [PWRF]
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   50.493833] input: Power Button (CM) as /devices/virtual/input/input3
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   50.517565] ACPI: Power Button (CM) [PWRB]
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   50.517739] input: Lid Switch as /devices/virtual/input/input4
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   50.517866] ACPI: Lid Switch [LID]
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   50.618695] ACPI: Battery Slot [BAT0] (battery present)
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   50.627877] ACPI: AC Adapter [ACAD] (on-line)
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   52.568435] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:1a/LNXVIDEO:00/input/input5
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   52.591526] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   52.851764] input: PC Speaker as /devices/platform/pcspkr/input/input6
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   53.754924] ath_hal: module license 'Proprietary' taints kernel.
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   53.769273] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   53.875462] wlan: 0.9.4
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   53.921056] ath_pci: 0.9.4
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   53.921197] ACPI: PCI Interrupt 0000:05:01.0[A] -> GSI 18 (level, low) -> IRQ 22
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   54.649415] ath_rate_sample: 1.2 (0.9.4)
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   54.650418] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   54.650430] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   54.650452] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   54.650461] wifi0: mac 7.8 phy 4.5 radio 5.6
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   54.650471] wifi0: Use hw queue 1 for WME_AC_BE traffic
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   54.650476] wifi0: Use hw queue 0 for WME_AC_BK traffic
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   54.650489] wifi0: Use hw queue 2 for WME_AC_VI traffic
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   54.650494] wifi0: Use hw queue 3 for WME_AC_VO traffic
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   54.650498] wifi0: Use hw queue 8 for CAB traffic
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   54.650502] wifi0: Use hw queue 9 for beacons
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   54.694223] input: PS/2 Mouse as /devices/virtual/input/input7
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   54.730158] wifi0: Atheros 5212: mem=0x30000000, irq=22
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   54.731238] ACPI: PCI Interrupt 0000:04:01.0[A] -> GSI 17 (level, low) -> IRQ 23
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   54.797596] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio4/input/input8
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   57.314480] lp: driver loaded but no devices found
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   57.551744] Adding 1309256k swap on /dev/sda5.  Priority:-1 extents:1 across:1309256k
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   58.126096] EXT3 FS on sda1, internal journal
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   59.660874] ip_tables: (C) 2000-2006 Netfilter Core Team
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   65.228686] Clocksource tsc unstable (delta = 4687192695 ns)
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   65.231144] Time: acpi_pm clocksource has been installed.
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   65.462835] No dock devices found.
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   66.742504] apm: BIOS not found.
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   66.897309] ppdev: user-space parallel port driver
Jul  5 22:10:43 nyxtwilight-laptop kernel: [   66.992069] audit(1215292243.888:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4954 profile="/usr/sbin/cupsd" namespace="default"
Jul  5 22:10:44 nyxtwilight-laptop dhcdbd: Started up.
Jul  5 22:10:44 nyxtwilight-laptop kernel: [   68.087386] eth0: link down
Jul  5 22:10:45 nyxtwilight-laptop kernel: [   68.184600] Bluetooth: Core ver 2.11
Jul  5 22:10:45 nyxtwilight-laptop kernel: [   68.184800] NET: Registered protocol family 31
Jul  5 22:10:45 nyxtwilight-laptop kernel: [   68.184804] Bluetooth: HCI device and connection manager initialized
Jul  5 22:10:45 nyxtwilight-laptop kernel: [   68.184810] Bluetooth: HCI socket layer initialized
Jul  5 22:10:45 nyxtwilight-laptop kernel: [   68.233126] Bluetooth: L2CAP ver 2.9
Jul  5 22:10:45 nyxtwilight-laptop kernel: [   68.233136] Bluetooth: L2CAP socket layer initialized
Jul  5 22:10:45 nyxtwilight-laptop kernel: [   68.301045] Bluetooth: RFCOMM socket layer initialized
Jul  5 22:10:45 nyxtwilight-laptop kernel: [   68.301642] Bluetooth: RFCOMM TTY layer initialized
Jul  5 22:10:45 nyxtwilight-laptop kernel: [   68.301646] Bluetooth: RFCOMM ver 1.8
Jul  5 22:10:49 nyxtwilight-laptop kernel: [   72.603035] [drm] Initialized drm 1.0.1 20051102
Jul  5 22:10:49 nyxtwilight-laptop kernel: [   72.629560] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 24
Jul  5 22:10:49 nyxtwilight-laptop kernel: [   72.631655] [drm] Initialized via_chrome9 1.1.2 Thu, 14 Apr 2006 10:00:00 +0800 on minor 0: 
Jul  5 22:10:49 nyxtwilight-laptop kernel: [   72.634095] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
Jul  5 22:10:49 nyxtwilight-laptop kernel: [   72.634137] agpgart: Xorg tried to set rate=x12. Setting to AGP3 x8 mode.
Jul  5 22:10:49 nyxtwilight-laptop kernel: [   72.634154] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
Jul  5 22:10:49 nyxtwilight-laptop kernel: [   72.634327] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
Jul  5 22:10:50 nyxtwilight-laptop kernel: [   73.386569] [drm] pci_driver->suspend is set by  SaveAGPRegisters
Jul  5 22:10:50 nyxtwilight-laptop kernel: [   73.386594] [drm] pci_driver->resume is set by  RestoreAGPRegisters
Jul  5 22:10:50 nyxtwilight-laptop kernel: [   73.386596] [drm] the pci_driver have already been associated with pci_device
Jul  5 22:10:50 nyxtwilight-laptop kernel: [   73.386604] [drm] DMA buffer initialized finished. Use AGP Ring Buffer type!
Jul  5 22:10:50 nyxtwilight-laptop kernel: [   73.386607] [drm] Total AGP DMA buffer size = 16777216 bytes. 
Jul  5 22:10:56 nyxtwilight-laptop kernel: [   79.804880] hda-intel: Invalid position buffer, using LPIB read method instead.
Jul  5 22:25:01 nyxtwilight-laptop kernel: [  924.512119] NET: Registered protocol family 10
Jul  5 22:25:01 nyxtwilight-laptop kernel: [  924.512755] lo: Disabled Privacy Extensions
Jul  5 22:25:01 nyxtwilight-laptop kernel: [  924.513746] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jul  5 22:25:02 nyxtwilight-laptop pulseaudio[5568]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Jul  5 22:25:02 nyxtwilight-laptop pulseaudio[5568]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Jul  5 22:25:02 nyxtwilight-laptop pulseaudio[5568]: alsa-util.c: Cannot find fallback mixer control "Mic".
Jul  5 22:25:10 nyxtwilight-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.reason
Jul  5 22:25:13 nyxtwilight-laptop kernel: [  936.332798] NET: Registered protocol family 17
Jul  5 22:25:23 nyxtwilight-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.host_name
Jul  5 22:25:23 nyxtwilight-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.domain_name
Jul  5 22:25:23 nyxtwilight-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.nis_domain
Jul  5 22:25:23 nyxtwilight-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.nis_servers
Jul  5 22:25:23 nyxtwilight-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.interface_mtu
Jul  5 22:52:32 nyxtwilight-laptop -- MARK --
Jul  5 23:12:32 nyxtwilight-laptop -- MARK --
Jul  5 23:21:47 nyxtwilight-laptop kernel: [ 4217.485984] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
Jul  5 23:21:47 nyxtwilight-laptop kernel: [ 4217.486018] agpgart: Xorg tried to set rate=x12. Setting to AGP3 x8 mode.
Jul  5 23:21:47 nyxtwilight-laptop kernel: [ 4217.486031] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
Jul  5 23:21:47 nyxtwilight-laptop kernel: [ 4217.486183] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
Jul  5 23:21:48 nyxtwilight-laptop kernel: [ 4218.191247] [drm] the pci_driver have already been associated with pci_device
Jul  5 23:21:48 nyxtwilight-laptop kernel: [ 4218.191273] [drm] DMA buffer initialized finished. Use AGP Ring Buffer type!
Jul  5 23:21:48 nyxtwilight-laptop kernel: [ 4218.191276] [drm] Total AGP DMA buffer size = 16777216 bytes. 
Jul  5 23:22:28 nyxtwilight-laptop pulseaudio[6787]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Jul  5 23:22:28 nyxtwilight-laptop pulseaudio[6787]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Jul  5 23:22:28 nyxtwilight-laptop pulseaudio[6787]: alsa-util.c: Cannot find fallback mixer control "Mic".
Jul  5 23:22:38 nyxtwilight-laptop gnome-power-manager: (nyxtwilight) Power Manager is already running in this session.
Jul  5 23:22:39 nyxtwilight-laptop kernel: [ 4269.011515] awn-applet-acti[6925]: segfault at 000001f4 eip b7afeab6 esp bff5dee0 error 4
Jul  5 23:24:10 nyxtwilight-laptop kernel: [ 4360.423241] python[6933]: segfault at 00000000 eip b6daf206 esp bf93bef0 error 4
Jul  5 23:36:03 nyxtwilight-laptop kernel: [ 5063.530277] compiz.real[6898]: segfault at 00000000 eip 00000000 esp bfd014cc error 4
Jul  5 23:38:32 nyxtwilight-laptop kernel: [ 5220.685564] awn-applet-acti[7142]: segfault at 00000004 eip b76adad7 esp bfae5a5c error 4
Jul  5 23:40:43 nyxtwilight-laptop kernel: [ 5351.153376] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
Jul  5 23:40:43 nyxtwilight-laptop kernel: [ 5351.153411] agpgart: Xorg tried to set rate=x12. Setting to AGP3 x8 mode.
Jul  5 23:40:45 nyxtwilight-laptop kernel: [ 5351.153422] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
Jul  5 23:40:45 nyxtwilight-laptop kernel: [ 5351.153554] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
Jul  5 23:40:45 nyxtwilight-laptop kernel: [ 5352.381481] [drm] the pci_driver have already been associated with pci_device
Jul  5 23:40:45 nyxtwilight-laptop kernel: [ 5352.381510] [drm] DMA buffer initialized finished. Use AGP Ring Buffer type!
Jul  5 23:40:45 nyxtwilight-laptop kernel: [ 5352.381513] [drm] Total AGP DMA buffer size = 16777216 bytes. 
Jul  5 23:41:12 nyxtwilight-laptop pulseaudio[7433]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Jul  5 23:41:12 nyxtwilight-laptop pulseaudio[7433]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Jul  5 23:41:12 nyxtwilight-laptop pulseaudio[7433]: alsa-util.c: Cannot find fallback mixer control "Mic".
Jul  5 23:42:06 nyxtwilight-laptop kernel: [ 5435.295884] awn-applet-acti[7575]: segfault at 00000000 eip b7a8e206 esp bf809140 error 4
Jul  5 23:44:38 nyxtwilight-laptop kernel: [ 5587.174464] compiz.real[7538]: segfault at 00000000 eip 00000000 esp bfac2d7c error 4
Jul  5 23:54:08 nyxtwilight-laptop kernel: [ 6156.794045] python[7594]: segfault at 00000000 eip b6ddd206 esp bfdedba0 error 4
Jul  5 23:54:08 nyxtwilight-laptop kernel: [ 6156.885513] python[7598]: segfault at 00000000 eip b6c40206 esp bf98ef40 error 4
Jul  5 23:54:08 nyxtwilight-laptop kernel: [ 6156.924657] python[7596]: segfault at 00000000 eip b6de7206 esp bf82ade0 error 4
Jul  5 23:54:08 nyxtwilight-laptop kernel: [ 6156.944933] python[7571]: segfault at 00000000 eip b6d93206 esp bf807db0 error 4
Jul  6 00:13:19 nyxtwilight-laptop -- MARK --
Jul  6 00:21:19 nyxtwilight-laptop kernel: [ 7786.408821] compiz.real[7990]: segfault at 00000000 eip 00000000 esp bfd44dec error 4
Jul  6 00:24:20 nyxtwilight-laptop kernel: [ 7967.044749] compiz.real[8604]: segfault at 00000000 eip 00000000 esp bff7c20c error 4
Jul  6 00:29:50 nyxtwilight-laptop syslogd 1.5.0#1ubuntu1: restart.
Jul  6 00:33:11 nyxtwilight-laptop pulseaudio[7433]: pstream.c: Failed to import memory block.
Jul  6 00:53:19 nyxtwilight-laptop -- MARK --
Jul  6 01:02:08 nyxtwilight-laptop kernel: [10233.552903] compiz.real[8850]: segfault at 00000000 eip 00000000 esp bfb7be1c error 4
Jul  6 01:03:56 nyxtwilight-laptop kernel: [10341.311317] compiz.real[9969]: segfault at 00000000 eip 00000000 esp bffcee7c error 4
Jul  6 01:04:31 nyxtwilight-laptop kernel: [10376.379975] compiz.real[10062]: segfault at 00000000 eip 00000000 esp bfaf19cc error 4
Jul  6 01:05:07 nyxtwilight-laptop kernel: [10411.834424] compiz.real[10147]: segfault at 00000000 eip 00000000 esp bfd71c4c error 4
Jul  6 01:05:27 nyxtwilight-laptop kernel: [10432.552170] avant-window-na[7992]: segfault at 0000001c eip b7b21447 esp bfd9f800 error 4
Jul  6 01:07:24 nyxtwilight-laptop gnome-power-manager: (nyxtwilight) GNOME interactive logout. Reason: The power button has been pressed.
Jul  6 01:07:27 nyxtwilight-laptop last message repeated 2 times
Jul  6 01:07:52 nyxtwilight-laptop kernel: [10577.138322] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
Jul  6 01:07:52 nyxtwilight-laptop kernel: [10577.138360] agpgart: Xorg tried to set rate=x12. Setting to AGP3 x8 mode.
Jul  6 01:07:52 nyxtwilight-laptop kernel: [10577.138377] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
Jul  6 01:07:52 nyxtwilight-laptop kernel: [10577.138550] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
Jul  6 01:07:53 nyxtwilight-laptop kernel: [10577.921875] [drm] the pci_driver have already been associated with pci_device
Jul  6 01:07:53 nyxtwilight-laptop kernel: [10577.921905] [drm] DMA buffer initialized finished. Use AGP Ring Buffer type!
Jul  6 01:07:53 nyxtwilight-laptop kernel: [10577.921910] [drm] Total AGP DMA buffer size = 16777216 bytes. 
Jul  6 01:08:33 nyxtwilight-laptop pulseaudio[10629]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Jul  6 01:08:33 nyxtwilight-laptop pulseaudio[10629]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Jul  6 01:08:33 nyxtwilight-laptop pulseaudio[10629]: alsa-util.c: Cannot find fallback mixer control "Mic".
Jul  6 01:09:58 nyxtwilight-laptop kernel: [10702.866218] compiz.real[10719]: segfault at 00000000 eip 00000000 esp bfdff49c error 4
Jul  6 01:21:29 nyxtwilight-laptop kernel: [11393.751820] ip6_tables: (C) 2000-2006 Netfilter Core Team
Jul  6 01:21:31 nyxtwilight-laptop exiting on signal 15
Jul  6 21:28:56 nyxtwilight-laptop syslogd 1.5.0#1ubuntu1: restart.
Jul  6 21:28:56 nyxtwilight-laptop kernel: Inspecting /boot/System.map-2.6.24-16-generic
Jul  6 21:28:56 nyxtwilight-laptop kernel: Loaded 27704 symbols from /boot/System.map-2.6.24-16-generic.
Jul  6 21:28:56 nyxtwilight-laptop kernel: Symbols match kernel version 2.6.24.
Jul  6 21:28:56 nyxtwilight-laptop kernel: Loaded 16772 symbols from 81 modules.
Jul  6 21:28:56 nyxtwilight-laptop kernel: [    0.000000] Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
Jul  6 21:28:56 nyxtwilight-laptop kernel: [    0.000000] BIOS-provided physical RAM map:
Jul  6 21:28:56 nyxtwilight-laptop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
Jul  6 21:28:56 nyxtwilight-laptop kernel: [    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
Jul  6 21:28:56 nyxtwilight-laptop kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Jul  6 21:28:56 nyxtwilight-laptop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000001be90000 (usable)
Jul  6 21:28:56 nyxtwilight-laptop kernel: [    0.000000]  BIOS-e820: 000000001be90000 - 000000001be9f000 (ACPI data)
Jul  6 21:28:56 nyxtwilight-laptop kernel: [    0.000000]  BIOS-e820: 000000001be9f000 - 000000001bf00000 (ACPI NVS)
Jul  6 21:28:56 nyxtwilight-laptop kernel: [    0.000000]  BIOS-e820: 000000001bf00000 - 0000000020000000 (reserved)
Jul  6 21:28:56 nyxtwilight-laptop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Jul  6 21:28:56 nyxtwilight-laptop kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Jul  6 21:28:56 nyxtwilight-laptop kernel: [    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
Jul  6 21:28:56 nyxtwilight-laptop kernel: [    0.000000] 0MB HIGHMEM available.
Jul  6 21:28:56 nyxtwilight-laptop kernel: [    0.000000] 446MB LOWMEM available.
Jul  6 21:28:56 nyxtwilight-laptop kernel: [    0.000000] found SMP MP-table at 000f7480
Jul  6 21:28:56 nyxtwilight-laptop kernel: [    0.000000] Zone PFN ranges:
Jul  6 21:28:56 nyxtwilight-laptop kernel: [    0.000000]   DMA             0 ->     4096
Jul  6 21:28:56 nyxtwilight-laptop kernel: [    0.000000]   Normal       4096 ->   114320
Jul  6 21:28:56 nyxtwilight-laptop kernel: [    0.000000]   HighMem    114320 ->   114320
Jul  6 21:28:56 nyxtwilight-laptop kernel: [    0.000000] Movable zone start PFN for each node
Jul  6 21:28:56 nyxtwilight-laptop kernel: [    0.000000] early_node_map[1] active PFN ranges
Jul  6 21:28:56 nyxtwilight-laptop kernel: [    0.000000]     0:        0 ->   114320
Jul  6 21:28:56 nyxtwilight-laptop kernel: [    0.000000] DMI present.
Jul  6 21:28:56 nyxtwilight-laptop kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F73D0 checksum 0
Jul  6 21:28:56 nyxtwilight-laptop kernel: [    0.000000] ACPI: RSDP 000F73D0, 0014 (r0 PTLTD )
Jul  6 21:28:56 nyxtwilight-laptop kernel: [    0.000000] ACPI: RSDT 1BE992D9, 0038 (r1 FSC    PC        6040000  LTP        0)
Jul  6 21:28:56 nyxtwilight-laptop kernel: [    0.000000] ACPI: FACP 1BE9ED70, 0074 (r1 VN896  PTLTW     6040000 PTL_    F4240)
Jul  6 21:28:56 nyxtwilight-laptop kernel: [    0.000000] ACPI: DSDT 1BE99D0E, 5062 (r1  FIC   LM10W     6040000 MSFT  100000E)
Jul  6 21:28:56 nyxtwilight-laptop kernel: [    0.000000] ACPI: FACS 1BE9FFC0, 0040
Jul  6 21:28:56 nyxtwilight-laptop kernel: [    0.000000] ACPI: APIC 1BE9EDE4, 006A (r1 PTLTD  ^I APIC    6040000  LTP        0)
Jul  6 21:28:56 nyxtwilight-laptop kernel: [    0.000000] ACPI: MCFG 1BE9EE4E, 003C (r1 PTLTD    MCFG    6040000  LTP        0)
Jul  6 21:28:56 nyxtwilight-laptop kernel: [    0.000000] ACPI: SLIC 1BE9EE8A, 0176 (r1 FSC    PC        6040000             0)
Jul  6 21:28:56 nyxtwilight-laptop kernel: [    0.000000] ACPI: SSDT 1BE99311, 0519 (r1  PmRef    CpuPm     3000 INTL 20050228)
Jul  6 21:28:56 nyxtwilight-laptop kernel: [    0.000000] ACPI: DMI detected: Fujitsu Siemens
Jul  6 21:28:56 nyxtwilight-laptop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x4008
Jul  6 21:28:56 nyxtwilight-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jul  6 21:28:56 nyxtwilight-laptop kernel: [    0.000000] Processor #0 6:14 APIC version 20
Jul  6 21:28:56 nyxtwilight-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Jul  6 21:28:56 nyxtwilight-laptop kernel: [    0.000000] Processor #1 6:14 APIC version 20
Jul  6 21:28:56 nyxtwilight-laptop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Jul  6 21:28:56 nyxtwilight-laptop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Jul  6 21:28:56 nyxtwilight-laptop kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Jul  6 21:28:56 nyxtwilight-laptop kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
Jul  6 21:28:56 nyxtwilight-laptop kernel: [    0.000000] ACPI: IOAPIC (id[0x03] address[0xfecc0000] gsi_base[24])
Jul  6 21:28:56 nyxtwilight-laptop kernel: [    0.000000] IOAPIC[1]: apic_id 3, version 3, address 0xfecc0000, GSI 24-47
Jul  6 21:28:56 nyxtwilight-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jul  6 21:28:56 nyxtwilight-laptop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 2 I/O APICs
Jul  6 21:28:56 nyxtwilight-laptop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jul  6 21:28:56 nyxtwilight-laptop kernel: [    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
Jul  6 21:28:56 nyxtwilight-laptop kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009d000 - 000000000009e000
Jul  6 21:28:56 nyxtwilight-laptop kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009e000 - 00000000000a0000
Jul  6 21:28:56 nyxtwilight-laptop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
Jul  6 21:28:56 nyxtwilight-laptop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
Jul  6 21:28:56 nyxtwilight-laptop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 113427
Jul  6 21:28:56 nyxtwilight-laptop kernel: [    0.000000] Kernel command line: root=UUID=270f4baf-9a32-4ebc-af92-f1e8eb400da6 ro quiet splash
Jul  6 21:28:56 nyxtwilight-laptop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Jul  6 21:28:56 nyxtwilight-laptop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Jul  6 21:28:56 nyxtwilight-laptop kernel: [    0.000000] Initializing CPU#0
Jul  6 21:28:56 nyxtwilight-laptop kernel: [    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
Jul  6 21:28:56 nyxtwilight-laptop kernel: [    0.000000] Detected 1596.024 MHz processor.
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   21.957532] Console: colour VGA+ 80x25
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   21.957541] console [tty0] enabled
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   21.957846] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   21.958218] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   21.976483] Memory: 440860k/457280k available (2157k kernel code, 15836k reserved, 998k data, 364k init, 0k highmem)
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   21.976500] virtual kernel memory layout:
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   21.976502]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   21.976505]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   21.976508]     vmalloc : 0xdc800000 - 0xff7fe000   ( 559 MB)
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   21.976511]     lowmem  : 0xc0000000 - 0xdbe90000   ( 446 MB)
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   21.976513]       .init : 0xc041b000 - 0xc0476000   ( 364 kB)
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   21.976516]       .data : 0xc031b5a4 - 0xc0414dc4   ( 998 kB)
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   21.976519]       .text : 0xc0100000 - 0xc031b5a4   (2157 kB)
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   21.976526] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   21.976592] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   22.056556] Calibrating delay using timer specific routine.. 3195.63 BogoMIPS (lpj=6391264)
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   22.056603] Security Framework initialized
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   22.056616] SELinux:  Disabled at boot.
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   22.056643] AppArmor: AppArmor initialized
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   22.056651] Failure registering capabilities with primary security module.
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   22.056668] Mount-cache hash table entries: 512
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   22.056917] monitor/mwait feature present.
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   22.056920] using mwait in idle threads.
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   22.056928] CPU: L1 I cache: 32K, L1 D cache: 32K
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   22.056934] CPU: L2 cache: 1024K
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   22.056939] CPU: Physical Processor ID: 0
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   22.056942] CPU: Processor Core ID: 0
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   22.056965] Compat vDSO mapped to ffffe000.
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   22.056988] Checking 'hlt' instruction... OK.
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   22.073305] SMP alternatives: switching to UP code
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   22.076953] Early unpacking initramfs... done
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   22.875581] ACPI: Core revision 20070126
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   22.875700] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   22.991409] CPU0: Intel Genuine Intel(R) CPU           T2060  @ 1.60GHz stepping 0c
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   22.991444] SMP alternatives: switching to SMP code
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   22.992794] Booting processor 1/1 eip 3000
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.003027] Initializing CPU#1
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.083643] Calibrating delay using timer specific routine.. 3192.37 BogoMIPS (lpj=6384748)
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.083670] monitor/mwait feature present.
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.083676] CPU: L1 I cache: 32K, L1 D cache: 32K
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.083681] CPU: L2 cache: 1024K
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.083685] CPU: Physical Processor ID: 0
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.083688] CPU: Processor Core ID: 1
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.084497] CPU1: Intel Genuine Intel(R) CPU           T1060  @ 1.60GHz stepping 0c
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.084541] Total of 2 processors activated (6388.00 BogoMIPS).
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.084916] ENABLING IO-APIC IRQs
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.085140] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.231748] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.251765] Brought up 2 CPUs
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.252313] net_namespace: 64 bytes
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.252331] Booting paravirtualized kernel on bare hardware
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.253347] Time: 20:28:14  Date: 07/06/08
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.253403] NET: Registered protocol family 16
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.253813] EISA bus registered
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.253823] ACPI: bus type pci registered
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.254244] PCI: Using configuration type 1
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.254248] Setting up standard PCI resources
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.467643] ACPI: Interpreter enabled
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.467650] ACPI: (supports S0 S3 S4 S5)
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.467674] ACPI: Using IOAPIC for interrupt routing
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.478606] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.482048] PCI: Transparent bridge - 0000:00:13.1
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.513825] ACPI: PCI Interrupt Link [ALKA] (IRQs 16 17 18 19 20 21 22 23) *9, disabled.
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.513993] ACPI: PCI Interrupt Link [ALKB] (IRQs 16 17 18 19 20 21 22 23) *10, disabled.
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.514154] ACPI: PCI Interrupt Link [ALKC] (IRQs 22) *11, disabled.
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.514309] ACPI: PCI Interrupt Link [ALKD] (IRQs 21) *3, disabled.
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.514519] ACPI: PCI Interrupt Link [LNKA] (IRQs *9 10 11 12)
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.514720] ACPI: PCI Interrupt Link [LNKB] (IRQs 9 *10 11 12)
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.514920] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 *11 12)
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.515119] ACPI: PCI Interrupt Link [LNKD] (IRQs 9 10 11 12) *3
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.515363] ACPI: Power Resource [PFAN] (off)
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.515453] Linux Plug and Play Support v0.97 (c) Adam Belay
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.515528] pnp: PnP ACPI init
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.515544] ACPI: bus type pnp registered
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.517619] pnpacpi: exceeded the max number of mem resources: 12
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.519779] pnp: PnP ACPI: found 10 devices
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.519785] ACPI: ACPI bus type pnp unregistered
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.519793] PnPBIOS: Disabled by ACPI PNP
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.520285] PCI: Using ACPI for IRQ routing
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.520291] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.520303] PCI: Cannot allocate resource region 8 of bridge 0000:00:13.1
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.520376] PCI: Cannot allocate resource region 0 of device 0000:05:01.0
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.543289] NET: Registered protocol family 8
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.543294] NET: Registered protocol family 20
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.543431] AppArmor: AppArmor Filesystem Enabled
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.547259] Time: tsc clocksource has been installed.
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.563321] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.563328] system 00:01: iomem range 0xf0012000-0xf0012fff has been reserved
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.563335] system 00:01: iomem range 0xf0013000-0xf0013fff has been reserved
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.563355] system 00:06: iomem range 0x0-0x9ffff could not be reserved
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.563362] system 00:06: iomem range 0xc0000-0xcffff could not be reserved
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.563368] system 00:06: iomem range 0xe0000-0xfffff could not be reserved
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.563375] system 00:06: iomem range 0xe0000000-0xe01010ff has been reserved
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.563382] system 00:06: iomem range 0xe00100ff-0xe00190fe has been reserved
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.563388] system 00:06: iomem range 0xe00700ff-0xe007a0fe has been reserved
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.563395] system 00:06: iomem range 0xe00800ff-0xe00a00fe has been reserved
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.563402] system 00:06: iomem range 0xe01000ff-0xe06000fe could not be reserved
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.563409] system 00:06: iomem range 0xf00120ff-0xf00140fe could not be reserved
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.563416] system 00:06: iomem range 0xffb80000-0xffc7ffff has been reserved
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.563423] system 00:06: iomem range 0xfff00000-0xffffffff could not be reserved
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.563430] system 00:06: iomem range 0xffee0000-0xffefffff has been reserved
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.563443] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.563449] system 00:07: ioport range 0xfe10-0xfe11 has been reserved
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.563456] system 00:07: ioport range 0xfe00-0xfe00 has been reserved
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.563462] system 00:07: ioport range 0x4000-0x407f has been reserved
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.563468] system 00:07: ioport range 0x4100-0x411f has been reserved
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.594333] PCI: Failed to allocate mem resource #6:10000@c0000000 for 0000:01:00.0
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.594339] PCI: Bridge: 0000:00:01.0
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.594343]   IO window: disabled.
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.594352]   MEM window: c8000000-c8ffffff
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.594359]   PREFETCH window: a0000000-bfffffff
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.594367] PCI: Bridge: 0000:00:02.0
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.594370]   IO window: disabled.
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.594377]   MEM window: disabled.
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.594383]   PREFETCH window: disabled.
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.594391] PCI: Bridge: 0000:00:03.0
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.594397]   IO window: 7000-7fff
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.594405]   MEM window: c9000000-c90fffff
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.594412]   PREFETCH window: disabled.
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.594421] PCI: Bridge: 0000:00:13.0
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.594424]   IO window: disabled.
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.594432]   MEM window: c9100000-c91fffff
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.594438]   PREFETCH window: disabled.
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.594451] PCI: Bridge: 0000:00:13.1
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.594454]   IO window: disabled.
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.594462]   MEM window: disabled.
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.594468]   PREFETCH window: disabled.
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.594532] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 27 (level, low) -> IRQ 16
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.594568] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 31 (level, low) -> IRQ 17
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.594644] NET: Registered protocol family 2
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.635312] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.635727] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.635935] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.636133] TCP: Hash tables configured (established 16384 bind 16384)
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.636138] TCP reno registered
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   23.647439] checking if image is initramfs...<7>Switched to high resolution mode on CPU 1
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   24.413015]  it is
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   25.222189] Freeing initrd memory: 7704k freed
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   25.224037] audit: initializing netlink socket (disabled)
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   25.224070] audit(1215376095.020:1): initialized
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   25.228678] VFS: Disk quotas dquot_6.5.1
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   25.228867] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   25.229154] io scheduler noop registered
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   25.229159] io scheduler anticipatory registered
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   25.229164] io scheduler deadline registered
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   25.229188] io scheduler cfq registered (default)
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   25.229217] PCI: VIA PCI bridge detected. Disabling DAC.
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   33.217700] 0000:00:10.4 EHCI: BIOS handoff failed (BIOS bug ?) 01010001
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   33.218066] assign_interrupt_mode Found MSI capability
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   33.218441] assign_interrupt_mode Found MSI capability
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   33.219110] isapnp: Scanning for PnP cards...
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   33.573810] isapnp: No Plug & Play device found
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   33.633400] Real Time Clock Driver v1.12ac
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   33.633635] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   33.636186] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   33.636342] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   33.636548] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   33.638931] i8042.c: Detected active multiplexing controller, rev 1.1.
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   33.640080] serio: i8042 KBD port at 0x60,0x64 irq 1
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   33.640090] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   33.640096] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   33.640102] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   33.640108] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   33.661415] mice: PS/2 mouse device common for all mice
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   33.661658] EISA: Probing bus 0 at eisa.0
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   33.661690] Cannot allocate resource for EISA slot 4
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   33.661701] Cannot allocate resource for EISA slot 6
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   33.661707] Cannot allocate resource for EISA slot 7
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   33.661717] EISA: Detected 0 cards.
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   33.661724] cpuidle: using governor ladder
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   33.661729] cpuidle: using governor menu
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   33.661931] NET: Registered protocol family 1
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   33.661991] Using IPI No-Shortcut mode
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   33.662058] registered taskstats version 1
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   33.662297]   Magic number: 0:504:497
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   33.662497] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   33.662502] EDD information not available.
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   33.662808] Freeing unused kernel memory: 364k freed
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   33.689491] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   35.132432] fuse init (API version 7.9)
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   35.203302] ACPI: Fan [FAN] (on)
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   35.218283] ACPI: SSDT 1BE99A9F, 01E8 (r1  PmRef  Cpu0Ist     3000 INTL 20050228)
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   35.218961] ACPI: SSDT 1BE9982A, 01F0 (r1  PmRef  Cpu0Cst     3001 INTL 20050228)
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   35.219730] ACPI: CPU0 (power states: C1[C1] C2[C2])
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   35.219741] ACPI: Processor [CPU0] (supports 16 throttling states)
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   35.220207] ACPI: SSDT 1BE99C87, 0087 (r1  PmRef  Cpu1Ist     3000 INTL 20050228)
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   35.220533] ACPI: SSDT 1BE99A1A, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050228)
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   35.221308] ACPI: CPU1 (power states: C1[C1] C2[C2])
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   35.221321] ACPI: Processor [CPU1] (supports 16 throttling states)
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   35.221352] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   35.221376] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   36.301059] ACPI: Thermal Zone [THRM] (29 C)
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   37.168688] SCSI subsystem initialized
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   37.240203] usbcore: registered new interface driver usbfs
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   37.240266] usbcore: registered new interface driver hub
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   37.265800] usbcore: registered new device driver usb
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   37.270923] ACPI: PCI Interrupt 0000:00:0f.0[B] -> GSI 21 (level, low) -> IRQ 18
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   37.270989] sata_via 0000:00:0f.0: routed to hard irq line 10
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   37.272517] scsi0 : sata_via
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   37.286752] scsi1 : sata_via
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   37.287146] ata1: SATA max UDMA/133 cmd 0x60b8 ctl 0x60b0 bmdma 0x6010 irq 18
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   37.287153] ata2: SATA max UDMA/133 cmd 0x6008 ctl 0x6004 bmdma 0x6018 irq 18
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   37.314801] USB Universal Host Controller Interface driver v3.0
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   37.465824] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   37.490558] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   37.654270] ata1.00: ATA-8: FUJITSU MHW2080BH, 00000012, max UDMA/100
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   37.654281] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   37.669810] ata1.00: configured for UDMA/100
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   37.874141] ata2: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   37.885504] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHW2080B 0000 PQ: 0 ANSI: 5
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   37.887247] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 20 (level, low) -> IRQ 19
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   37.887273] uhci_hcd 0000:00:10.0: UHCI Host Controller
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   37.887790] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   37.887835] uhci_hcd 0000:00:10.0: irq 19, io base 0x00006020
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   37.888144] usb usb1: configuration #1 chosen from 1 choice
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   37.888203] hub 1-0:1.0: USB hub found
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   37.888218] hub 1-0:1.0: 2 ports detected
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   37.990280] ACPI: PCI Interrupt 0000:00:10.1[B] -> GSI 22 (level, low) -> IRQ 20
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   37.990312] uhci_hcd 0000:00:10.1: UHCI Host Controller
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   37.990369] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   37.990408] uhci_hcd 0000:00:10.1: irq 20, io base 0x00006040
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   37.990671] usb usb2: configuration #1 chosen from 1 choice
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   37.990722] hub 2-0:1.0: USB hub found
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   37.990735] hub 2-0:1.0: 2 ports detected
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   38.094174] ACPI: PCI Interrupt 0000:00:10.2[C] -> GSI 21 (level, low) -> IRQ 18
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   38.094208] uhci_hcd 0000:00:10.2: UHCI Host Controller
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   38.094272] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   38.094311] uhci_hcd 0000:00:10.2: irq 18, io base 0x00006060
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   38.094555] usb usb3: configuration #1 chosen from 1 choice
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   38.094607] hub 3-0:1.0: USB hub found
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   38.094619] hub 3-0:1.0: 2 ports detected
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   38.198076] ACPI: PCI Interrupt 0000:00:10.3[D] -> GSI 23 (level, low) -> IRQ 21
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   38.198109] uhci_hcd 0000:00:10.3: UHCI Host Controller
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   38.198164] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   38.198206] uhci_hcd 0000:00:10.3: irq 21, io base 0x00006080
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   38.198457] usb usb4: configuration #1 chosen from 1 choice
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   38.198518] hub 4-0:1.0: USB hub found
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   38.198530] hub 4-0:1.0: 2 ports detected
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   38.291747] Driver 'sd' needs updating - please use bus_type methods
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   38.291925] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   38.291953] sd 0:0:0:0: [sda] Write Protect is off
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   38.291997] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   38.292123] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   38.292146] sd 0:0:0:0: [sda] Write Protect is off
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   38.292187] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   38.292195]  sda: sda1 sda2 <<6>ACPI: PCI Interrupt 0000:00:10.4[C] -> GSI 21 (level, low) -> IRQ 18
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   38.302211] ehci_hcd 0000:00:10.4: EHCI Host Controller
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   38.302268] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   38.302338] ehci_hcd 0000:00:10.4: irq 18, io mem 0xc9400000
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   38.313730] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   38.314027] usb usb5: configuration #1 chosen from 1 choice
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   38.314084] hub 5-0:1.0: USB hub found
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   38.314100] hub 5-0:1.0: 8 ports detected
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   38.419235] scsi2 : pata_via
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   38.420219] scsi3 : pata_via
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   38.421569] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x60a0 irq 14
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   38.421585] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x60a8 irq 15
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   38.625503]  sda5 >
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   38.625734] sd 0:0:0:0: [sda] Attached SCSI disk
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   38.637967] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   38.740725] ata4.00: ATAPI: HL-DT-ST DVDRAM GSA-T10N, PW02, max UDMA/33
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   38.912435] ata4.00: configured for UDMA/33
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   38.916365] scsi 3:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T10N  PW02 PQ: 0 ANSI: 5
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   38.916553] scsi 3:0:0:0: Attached scsi generic sg1 type 5
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   38.916720] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 23 (level, low) -> IRQ 21
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   38.921406] eth0: VIA Rhine II at 0xc9400400, 00:14:0b:0b:74:0e, IRQ 21.
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   38.922123] eth0: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000.
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   38.930088] Attempting manual resume
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   38.961222] kjournald starting.  Commit interval 5 seconds
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   38.961245] EXT3-fs: mounted filesystem with ordered data mode.
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   38.961303] Driver 'sr' needs updating - please use bus_type methods
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   38.979654] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   38.979666] Uniform CD-ROM driver Revision: 3.20
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   48.018865] Linux agpgart interface v0.102
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   48.100387] agpgart: Detected VIA P4M900 chipset
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   48.111142] agpgart: AGP aperture is 128M @ 0xc0000000
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   48.323416] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   48.403850] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   49.051546] input: Power Button (FF) as /devices/virtual/input/input2
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   49.075113] ACPI: Power Button (FF) [PWRF]
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   49.075319] input: Power Button (CM) as /devices/virtual/input/input3
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   49.111753] ACPI: Power Button (CM) [PWRB]
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   49.111970] input: Lid Switch as /devices/virtual/input/input4
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   49.112089] ACPI: Lid Switch [LID]
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   49.113171] ACPI: AC Adapter [ACAD] (on-line)
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   49.174713] ACPI: Battery Slot [BAT0] (battery present)
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   50.994180] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:1a/LNXVIDEO:00/input/input5
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   51.017200] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   51.520557] input: PC Speaker as /devices/platform/pcspkr/input/input6
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   52.314126] ath_hal: module license 'Proprietary' taints kernel.
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   52.329419] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   52.492750] wlan: 0.9.4
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   52.525482] ath_pci: 0.9.4
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   52.525628] ACPI: PCI Interrupt 0000:05:01.0[A] -> GSI 18 (level, low) -> IRQ 22
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   52.621416] input: PS/2 Mouse as /devices/virtual/input/input7
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   53.186753] ath_rate_sample: 1.2 (0.9.4)
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   53.187756] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   53.187769] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   53.187790] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   53.187799] wifi0: mac 7.8 phy 4.5 radio 5.6
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   53.187808] wifi0: Use hw queue 1 for WME_AC_BE traffic
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   53.187812] wifi0: Use hw queue 0 for WME_AC_BK traffic
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   53.187817] wifi0: Use hw queue 2 for WME_AC_VI traffic
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   53.187822] wifi0: Use hw queue 3 for WME_AC_VO traffic
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   53.187826] wifi0: Use hw queue 8 for CAB traffic
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   53.187830] wifi0: Use hw queue 9 for beacons
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   53.227407] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio4/input/input8
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   53.289066] wifi0: Atheros 5212: mem=0x30000000, irq=22
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   53.660402] ACPI: PCI Interrupt 0000:04:01.0[A] -> GSI 17 (level, low) -> IRQ 23
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   56.028342] lp: driver loaded but no devices found
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   56.265711] Adding 1309256k swap on /dev/sda5.  Priority:-1 extents:1 across:1309256k
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   56.840826] EXT3 FS on sda1, internal journal
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   58.474626] ip_tables: (C) 2000-2006 Netfilter Core Team
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   64.069868] Clocksource tsc unstable (delta = 4687228484 ns)
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   64.071329] Time: acpi_pm clocksource has been installed.
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   64.351537] No dock devices found.
Jul  6 21:28:56 nyxtwilight-laptop kernel: [   65.722889] apm: BIOS not found.
Jul  6 21:28:57 nyxtwilight-laptop kernel: [   65.866624] ppdev: user-space parallel port driver
Jul  6 21:28:57 nyxtwilight-laptop kernel: [   65.961304] audit(1215376137.126:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4944 profile="/usr/sbin/cupsd" namespace="default"
Jul  6 21:28:57 nyxtwilight-laptop dhcdbd: Started up.
Jul  6 21:28:58 nyxtwilight-laptop kernel: [   67.136362] eth0: link down
Jul  6 21:28:58 nyxtwilight-laptop kernel: [   67.251647] Bluetooth: Core ver 2.11
Jul  6 21:28:58 nyxtwilight-laptop kernel: [   67.252342] NET: Registered protocol family 31
Jul  6 21:28:58 nyxtwilight-laptop kernel: [   67.252345] Bluetooth: HCI device and connection manager initialized
Jul  6 21:28:58 nyxtwilight-laptop kernel: [   67.252350] Bluetooth: HCI socket layer initialized
Jul  6 21:28:58 nyxtwilight-laptop kernel: [   67.284940] Bluetooth: L2CAP ver 2.9
Jul  6 21:28:58 nyxtwilight-laptop kernel: [   67.284949] Bluetooth: L2CAP socket layer initialized
Jul  6 21:28:58 nyxtwilight-laptop kernel: [   67.364837] Bluetooth: RFCOMM socket layer initialized
Jul  6 21:28:58 nyxtwilight-laptop kernel: [   67.365475] Bluetooth: RFCOMM TTY layer initialized
Jul  6 21:28:58 nyxtwilight-laptop kernel: [   67.365480] Bluetooth: RFCOMM ver 1.8
Jul  6 21:29:02 nyxtwilight-laptop kernel: [   71.608649] [drm] Initialized drm 1.0.1 20051102
Jul  6 21:29:02 nyxtwilight-laptop kernel: [   71.642985] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 24
Jul  6 21:29:02 nyxtwilight-laptop kernel: [   71.644928] [drm] Initialized via_chrome9 1.1.2 Thu, 14 Apr 2006 10:00:00 +0800 on minor 0: 
Jul  6 21:29:02 nyxtwilight-laptop kernel: [   71.647152] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
Jul  6 21:29:02 nyxtwilight-laptop kernel: [   71.648094] agpgart: Xorg tried to set rate=x12. Setting to AGP3 x8 mode.
Jul  6 21:29:02 nyxtwilight-laptop kernel: [   71.649115] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
Jul  6 21:29:02 nyxtwilight-laptop kernel: [   71.650257] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
Jul  6 21:29:03 nyxtwilight-laptop kernel: [   72.411273] [drm] pci_driver->suspend is set by  SaveAGPRegisters
Jul  6 21:29:03 nyxtwilight-laptop kernel: [   72.411301] [drm] pci_driver->resume is set by  RestoreAGPRegisters
Jul  6 21:29:03 nyxtwilight-laptop kernel: [   72.411304] [drm] the pci_driver have already been associated with pci_device
Jul  6 21:29:03 nyxtwilight-laptop kernel: [   72.411311] [drm] DMA buffer initialized finished. Use AGP Ring Buffer type!
Jul  6 21:29:03 nyxtwilight-laptop kernel: [   72.411314] [drm] Total AGP DMA buffer size = 16777216 bytes. 
Jul  6 21:29:09 nyxtwilight-laptop kernel: [   78.694201] hda-intel: Invalid position buffer, using LPIB read method instead.
Jul  6 21:29:25 nyxtwilight-laptop kernel: [   94.455446] NET: Registered protocol family 10
Jul  6 21:29:25 nyxtwilight-laptop kernel: [   94.456335] lo: Disabled Privacy Extensions
Jul  6 21:29:25 nyxtwilight-laptop kernel: [   94.458199] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jul  6 21:29:25 nyxtwilight-laptop pulseaudio[5577]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Jul  6 21:29:26 nyxtwilight-laptop pulseaudio[5577]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Jul  6 21:29:26 nyxtwilight-laptop pulseaudio[5577]: alsa-util.c: Cannot find fallback mixer control "Mic".
Jul  6 21:29:35 nyxtwilight-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.reason
Jul  6 21:29:38 nyxtwilight-laptop kernel: [  107.739285] NET: Registered protocol family 17
Jul  6 21:29:48 nyxtwilight-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.host_name
Jul  6 21:29:48 nyxtwilight-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.domain_name
Jul  6 21:29:48 nyxtwilight-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.nis_domain
Jul  6 21:29:48 nyxtwilight-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.nis_servers
Jul  6 21:29:48 nyxtwilight-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.interface_mtu
Jul  6 21:48:56 nyxtwilight-laptop -- MARK --
Jul  6 21:57:24 nyxtwilight-laptop kernel: [ 1771.149632] compiz.real[5675]: segfault at 00000000 eip 00000000 esp bf826d1c error 4
Jul  6 21:58:40 nyxtwilight-laptop kernel: [ 1846.865842] compiz.real[6381]: segfault at 00000000 eip 00000000 esp bfd0865c error 4
Jul  6 22:01:23 nyxtwilight-laptop kernel: [ 2010.086447] compiz.real[6479]: segfault at 00000000 eip 00000000 esp bf95103c error 4
Jul  6 22:03:25 nyxtwilight-laptop kernel: [ 2132.309191] compiz.real[6566]: segfault at 00000000 eip 00000000 esp bfaa195c error 4
Jul  6 22:06:37 nyxtwilight-laptop kernel: [ 2323.526785] compiz.real[6652]: segfault at 00000000 eip 00000000 esp bfaa995c error 4
Jul  6 22:28:56 nyxtwilight-laptop -- MARK --
Jul  6 22:35:26 nyxtwilight-laptop kernel: [ 4050.786549] compiz.real[6763]: segfault at 00000000 eip 00000000 esp bfb2d1dc error 4
Jul  6 22:38:55 nyxtwilight-laptop kernel: [ 4259.760983] compiz.real[6994]: segfault at 00000000 eip 00000000 esp bfd9ad8c error 4
Jul  6 22:40:39 nyxtwilight-laptop kernel: [ 4363.862655] compiz.real[7165]: segfault at 00000000 eip 00000000 esp bfb81d6c error 4
Jul  6 22:42:11 nyxtwilight-laptop kernel: [ 4456.182693] compiz.real[7262]: segfault at 00000000 eip 00000000 esp bfcf0d8c error 4
Jul  6 22:44:17 nyxtwilight-laptop kernel: [ 4581.935544] compiz.real[7356]: segfault at 00000000 eip 00000000 esp bf86171c error 4
Jul  6 23:06:49 nyxtwilight-laptop pulseaudio[5577]: pstream.c: Failed to import memory block.
```

---

### Post by sayakb on 2008-07-06
Try upgrading to the latest compiz:
[http://ubuntuforums.org/showpost.php?p=5332505&postcount=5](http://ubuntuforums.org/showpost.php?p=5332505&postcount=5)

---

