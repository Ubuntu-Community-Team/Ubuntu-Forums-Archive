---
title: "Ubuntu crashing"
date: 2008-01-20
forum: General Help
---

### Post by Jakadinho on 2008-01-20
Hy. I have 1 problem. My ubuntu keeps crashing. It happens randomly.
I use ASUS a6j laptop with gutsy + ati graphic card. I tought that ati driver is responsible for this so u install older one but still the same


Here's the log of the crash



Jan 20 23:57:00 jakadinho-laptop kernel: Inspecting /boot/System.map-2.6.22-14-generic
Jan 20 23:57:00 jakadinho-laptop kernel: Loaded 25445 symbols from /boot/System.map-2.6.22-14-generic.
Jan 20 23:57:00 jakadinho-laptop kernel: Symbols match kernel version 2.6.22.
Jan 20 23:57:00 jakadinho-laptop kernel: No module symbols loaded - kernel modules not enabled. 
Jan 20 23:57:00 jakadinho-laptop kernel: [    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Dec 18 08:02:57 UTC 2007 (Ubuntu 2.6.22-14.47-generic)
Jan 20 23:57:00 jakadinho-laptop kernel: [    0.000000] BIOS-provided physical RAM map:
Jan 20 23:57:00 jakadinho-laptop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Jan 20 23:57:00 jakadinho-laptop kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Jan 20 23:57:00 jakadinho-laptop kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Jan 20 23:57:00 jakadinho-laptop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000003ffd0000 (usable)
Jan 20 23:57:00 jakadinho-laptop kernel: [    0.000000]  BIOS-e820: 000000003ffd0000 - 000000003ffde000 (ACPI data)
Jan 20 23:57:00 jakadinho-laptop kernel: [    0.000000]  BIOS-e820: 000000003ffde000 - 0000000040000000 (ACPI NVS)
Jan 20 23:57:00 jakadinho-laptop kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Jan 20 23:57:00 jakadinho-laptop kernel: [    0.000000]  BIOS-e820: 00000000ffb80000 - 0000000100000000 (reserved)
Jan 20 23:57:00 jakadinho-laptop kernel: [    0.000000] 127MB HIGHMEM available.
Jan 20 23:57:00 jakadinho-laptop kernel: [    0.000000] 896MB LOWMEM available.
Jan 20 23:57:00 jakadinho-laptop kernel: [    0.000000] found SMP MP-table at 000ff780
Jan 20 23:57:00 jakadinho-laptop kernel: [    0.000000] Zone PFN ranges:
Jan 20 23:57:00 jakadinho-laptop kernel: [    0.000000]   DMA             0 ->     4096
Jan 20 23:57:00 jakadinho-laptop kernel: [    0.000000]   Normal       4096 ->   229376
Jan 20 23:57:00 jakadinho-laptop kernel: [    0.000000]   HighMem    229376 ->   262096
Jan 20 23:57:00 jakadinho-laptop kernel: [    0.000000] early_node_map[1] active PFN ranges
Jan 20 23:57:00 jakadinho-laptop kernel: [    0.000000]     0:        0 ->   262096
Jan 20 23:57:00 jakadinho-laptop kernel: [    0.000000] DMI 2.3 present.
Jan 20 23:57:00 jakadinho-laptop kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F7BB0 checksum 0
Jan 20 23:57:00 jakadinho-laptop kernel: [    0.000000] ACPI: RSDP 000F7BB0, 0014 (r0 ACPIAM)
Jan 20 23:57:00 jakadinho-laptop kernel: [    0.000000] ACPI: RSDT 3FFD0000, 0038 (r1 A M I  OEMRSDT   8000601 MSFT       97)
Jan 20 23:57:00 jakadinho-laptop kernel: [    0.000000] ACPI: FACP 3FFD0200, 0084 (r2 A M I  OEMFACP   8000601 MSFT       97)
Jan 20 23:57:00 jakadinho-laptop kernel: [    0.000000] ACPI: DSDT 3FFD0460, 772E (r1  A6Je0 A6Je0005        5 INTL 20051117)
Jan 20 23:57:00 jakadinho-laptop kernel: [    0.000000] ACPI: FACS 3FFDE000, 0040
Jan 20 23:57:00 jakadinho-laptop kernel: [    0.000000] ACPI: APIC 3FFD0390, 005C (r1 A M I  OEMAPIC   8000601 MSFT       97)
Jan 20 23:57:00 jakadinho-laptop kernel: [    0.000000] ACPI: MCFG 3FFD03F0, 003C (r1 A M I  OEMMCFG   8000601 MSFT       97)
Jan 20 23:57:00 jakadinho-laptop kernel: [    0.000000] ACPI: BOOT 3FFD0430, 0028 (r1 A M I  OEMBOOT   8000601 MSFT       97)
Jan 20 23:57:00 jakadinho-laptop kernel: [    0.000000] ACPI: OEMB 3FFDE040, 0046 (r1 A M I  AMI_OEM   8000601 MSFT       97)
Jan 20 23:57:00 jakadinho-laptop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Jan 20 23:57:00 jakadinho-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Jan 20 23:57:00 jakadinho-laptop kernel: [    0.000000] Processor #0 6:15 APIC version 20
Jan 20 23:57:00 jakadinho-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Jan 20 23:57:00 jakadinho-laptop kernel: [    0.000000] Processor #1 6:15 APIC version 20
Jan 20 23:57:00 jakadinho-laptop kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Jan 20 23:57:00 jakadinho-laptop kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Jan 20 23:57:00 jakadinho-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jan 20 23:57:00 jakadinho-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jan 20 23:57:00 jakadinho-laptop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Jan 20 23:57:00 jakadinho-laptop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jan 20 23:57:00 jakadinho-laptop kernel: [    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bee00000)
Jan 20 23:57:00 jakadinho-laptop kernel: [    0.000000] Built 1 zonelists.  Total pages: 260049
Jan 20 23:57:00 jakadinho-laptop kernel: [    0.000000] Kernel command line: root=/dev/sda2 ro quiet splash
Jan 20 23:57:00 jakadinho-laptop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Jan 20 23:57:00 jakadinho-laptop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Jan 20 23:57:00 jakadinho-laptop kernel: [    0.000000] Initializing CPU#0
Jan 20 23:57:00 jakadinho-laptop kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Jan 20 23:57:00 jakadinho-laptop kernel: [    0.000000] Detected 1662.567 MHz processor.
Jan 20 23:57:00 jakadinho-laptop kernel: [   18.507332] Console: colour VGA+ 80x25
Jan 20 23:57:00 jakadinho-laptop kernel: [   18.507598] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Jan 20 23:57:00 jakadinho-laptop kernel: [   18.507894] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Jan 20 23:57:00 jakadinho-laptop kernel: [   18.534835] Memory: 1025592k/1048384k available (2015k kernel code, 22148k reserved, 916k data, 364k init, 130880k highmem)
Jan 20 23:57:00 jakadinho-laptop kernel: [   18.534844] virtual kernel memory layout:
Jan 20 23:57:00 jakadinho-laptop kernel: [   18.534845]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
Jan 20 23:57:00 jakadinho-laptop kernel: [   18.534846]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Jan 20 23:57:00 jakadinho-laptop kernel: [   18.534847]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Jan 20 23:57:00 jakadinho-laptop kernel: [   18.534848]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Jan 20 23:57:00 jakadinho-laptop kernel: [   18.534850]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
Jan 20 23:57:00 jakadinho-laptop kernel: [   18.534851]       .data : 0xc02f7de6 - 0xc03dce84   ( 916 kB)
Jan 20 23:57:00 jakadinho-laptop kernel: [   18.534852]       .text : 0xc0100000 - 0xc02f7de6   (2015 kB)
Jan 20 23:57:00 jakadinho-laptop kernel: [   18.534855] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Jan 20 23:57:00 jakadinho-laptop kernel: [   18.534885] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Jan 20 23:57:00 jakadinho-laptop kernel: [   18.614793] Calibrating delay using timer specific routine.. 3329.12 BogoMIPS (lpj=6658240)
Jan 20 23:57:00 jakadinho-laptop kernel: [   18.614814] Security Framework v1.0.0 initialized
Jan 20 23:57:00 jakadinho-laptop kernel: [   18.614819] SELinux:  Disabled at boot.
Jan 20 23:57:00 jakadinho-laptop kernel: [   18.614831] Mount-cache hash table entries: 512
Jan 20 23:57:00 jakadinho-laptop kernel: [   18.614944] monitor/mwait feature present.
Jan 20 23:57:00 jakadinho-laptop kernel: [   18.614946] using mwait in idle threads.
Jan 20 23:57:00 jakadinho-laptop kernel: [   18.614950] CPU: L1 I cache: 32K, L1 D cache: 32K
Jan 20 23:57:00 jakadinho-laptop kernel: [   18.614952] CPU: L2 cache: 2048K
Jan 20 23:57:00 jakadinho-laptop kernel: [   18.614954] CPU: Physical Processor ID: 0
Jan 20 23:57:00 jakadinho-laptop kernel: [   18.614956] CPU: Processor Core ID: 0
Jan 20 23:57:00 jakadinho-laptop kernel: [   18.614966] Compat vDSO mapped to ffffe000.
Jan 20 23:57:00 jakadinho-laptop kernel: [   18.614978] Checking 'hlt' instruction... OK.
Jan 20 23:57:00 jakadinho-laptop kernel: [   18.630863] SMP alternatives: switching to UP code
Jan 20 23:57:00 jakadinho-laptop kernel: [   18.631249] Early unpacking initramfs... done
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.028899] ACPI: Core revision 20070126
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.028955] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.044675] CPU0: Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz stepping 06
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.044691] SMP alternatives: switching to SMP code
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.044774] Booting processor 1/1 eip 3000
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.054978] Initializing CPU#1
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.134027] Calibrating delay using timer specific routine.. 3325.27 BogoMIPS (lpj=6650541)
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.134039] monitor/mwait feature present.
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.134042] CPU: L1 I cache: 32K, L1 D cache: 32K
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.134044] CPU: L2 cache: 2048K
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.134046] CPU: Physical Processor ID: 0
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.134047] CPU: Processor Core ID: 1
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.134610] CPU1: Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz stepping 06
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.134632] Total of 2 processors activated (6654.39 BogoMIPS).
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.134833] ENABLING IO-APIC IRQs
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.135028] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.281914] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.301900] Brought up 2 CPUs
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.463777] migration_cost=75
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.463908] Booting paravirtualized kernel on bare hardware
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.463982] Time: 23:56:35  Date: 00/20/108
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.464001] NET: Registered protocol family 16
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.464081] EISA bus registered
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.464085] ACPI: bus type pci registered
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.464266] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=5
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.464268] PCI: Using configuration type 1
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.464270] Setting up standard PCI resources
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.468682] ACPI: EC: GPE=0x1c, ports=0x66, 0x62
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.543868] ACPI: Interpreter enabled
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.543871] ACPI: (supports S0 S1 S3 S4 S5)
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.543894] ACPI: Using IOAPIC for interrupt routing
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.552247] ACPI: EC: GPE=0x1c, ports=0x66, 0x62
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.552381] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.553108] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.553113] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.554290] PCI: Transparent bridge - 0000:00:1e.0
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.566113] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *11 12)
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.566268] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 12)
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.566421] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 12)
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.566573] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 6 7 12)
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.566724] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 12)
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.566876] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 *7 12)
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.567028] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 *6 7 12)
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.567180] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 *4 5 6 7 12)
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.567355] ACPI: Power Resource [GFAN] (off)
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.567361] Linux Plug and Play Support v0.97 (c) Adam Belay
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.567371] pnp: PnP ACPI init
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.567383] ACPI: bus type pnp registered
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.569733] pnp: PnP ACPI: found 14 devices
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.569736] ACPI: ACPI bus type pnp unregistered
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.569739] PnPBIOS: Disabled by ACPI PNP
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.569811] PCI: Using ACPI for IRQ routing
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.569814] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.587182] NET: Registered protocol family 8
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.587184] NET: Registered protocol family 20
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.587252] pnp: 00:01: iomem range 0xfed13000-0xfed19fff has been reserved
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.587262] pnp: 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.587265] pnp: 00:08: iomem range 0xfed20000-0xfed8ffff has been reserved
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.587270] pnp: 00:09: iomem range 0xffb80000-0xffbfffff could not be reserved
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.587273] pnp: 00:09: iomem range 0xfff80000-0xffffffff could not be reserved
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.587278] pnp: 00:0a: iomem range 0xffc00000-0xfff7ffff could not be reserved
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.587283] pnp: 00:0b: ioport range 0x400-0x41f has been reserved
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.587286] pnp: 00:0b: iomem range 0xfec00000-0xfec00fff has been reserved
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.587290] pnp: 00:0b: iomem range 0xfee00000-0xfee00fff could not be reserved
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.587293] pnp: 00:0b: iomem range 0xfec10000-0xfec17fff has been reserved
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.587298] pnp: 00:0b: iomem range 0xfec28000-0xfec2ffff has been reserved
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.587303] pnp: 00:0c: iomem range 0xe0000000-0xe3ffffff has been reserved
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.587308] pnp: 00:0d: iomem range 0x0-0x9ffff could not be reserved
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.587311] pnp: 00:0d: iomem range 0xc0000-0xcffff could not be reserved
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.587314] pnp: 00:0d: iomem range 0xe0000-0xfffff could not be reserved
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.587317] pnp: 00:0d: iomem range 0x100000-0x3fffffff could not be reserved
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.589380] Time: tsc clocksource has been installed.
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.617600] PCI: Bridge: 0000:00:01.0
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.617603]   IO window: 9000-bfff
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.617607]   MEM window: fdf00000-fdffffff
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.617611]   PREFETCH window: bdf00000-ddefffff
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.617615] PCI: Bridge: 0000:00:1c.0
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.617618]   IO window: c000-cfff
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.617624]   MEM window: fe000000-fe0fffff
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.617629]   PREFETCH window: disabled.
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.617635] PCI: Bridge: 0000:00:1c.3
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.617636]   IO window: disabled.
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.617643]   MEM window: fe100000-fe1fffff
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.617647]   PREFETCH window: disabled.
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.617661] PCI: Bus 5, cardbus bridge: 0000:04:01.0
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.617663]   IO window: 0000d000-0000d0ff
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.617668]   IO window: 0000d400-0000d4ff
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.617673]   PREFETCH window: 50000000-53ffffff
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.617678]   MEM window: 54000000-57ffffff
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.617682] PCI: Bridge: 0000:00:1e.0
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.617686]   IO window: d000-dfff
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.617692]   MEM window: fe200000-feafffff
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.617697]   PREFETCH window: ddf00000-dfefffff
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.617714] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.617744] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 20 (level, low) -> IRQ 17
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.617776] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 18
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.617813] ACPI: PCI Interrupt 0000:04:01.0[A] -> GSI 17 (level, low) -> IRQ 19
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.617826] NET: Registered protocol family 2
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.657400] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.657458] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.658186] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.658475] TCP: Hash tables configured (established 131072 bind 65536)
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.658479] TCP reno registered
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.669507] checking if image is initramfs... it is
Jan 20 23:57:00 jakadinho-laptop kernel: [   20.120619] Switched to high resolution mode on CPU 0
Jan 20 23:57:00 jakadinho-laptop kernel: [   20.120697] Switched to high resolution mode on CPU 1
Jan 20 23:57:00 jakadinho-laptop kernel: [   20.454243] Freeing initrd memory: 9242k freed
Jan 20 23:57:00 jakadinho-laptop kernel: [   20.454370] Simple Boot Flag at 0x52 set to 0x1
Jan 20 23:57:00 jakadinho-laptop kernel: [   20.454848] audit: initializing netlink socket (disabled)
Jan 20 23:57:00 jakadinho-laptop kernel: [   20.454861] audit(1200873395.360:1): initialized
Jan 20 23:57:00 jakadinho-laptop kernel: [   20.454946] highmem bounce pool size: 64 pages
Jan 20 23:57:00 jakadinho-laptop kernel: [   20.456923] VFS: Disk quotas dquot_6.5.1
Jan 20 23:57:00 jakadinho-laptop kernel: [   20.456969] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jan 20 23:57:00 jakadinho-laptop kernel: [   20.457058] io scheduler noop registered
Jan 20 23:57:00 jakadinho-laptop kernel: [   20.457060] io scheduler anticipatory registered
Jan 20 23:57:00 jakadinho-laptop kernel: [   20.457062] io scheduler deadline registered
Jan 20 23:57:00 jakadinho-laptop kernel: [   20.457075] io scheduler cfq registered (default)
Jan 20 23:57:00 jakadinho-laptop kernel: [   20.457307] assign_interrupt_mode Found MSI capability
Jan 20 23:57:00 jakadinho-laptop kernel: [   20.457455] assign_interrupt_mode Found MSI capability
Jan 20 23:57:00 jakadinho-laptop kernel: [   20.457657] assign_interrupt_mode Found MSI capability
Jan 20 23:57:00 jakadinho-laptop kernel: [   20.457862] isapnp: Scanning for PnP cards...
Jan 20 23:57:00 jakadinho-laptop kernel: [   20.811737] isapnp: No Plug & Play device found
Jan 20 23:57:00 jakadinho-laptop kernel: [   20.833271] Real Time Clock Driver v1.12ac
Jan 20 23:57:00 jakadinho-laptop kernel: [   20.833393] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Jan 20 23:57:00 jakadinho-laptop kernel: [   20.834525] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Jan 20 23:57:00 jakadinho-laptop kernel: [   20.834655] input: Macintosh mouse button emulation as /class/input/input0
Jan 20 23:57:00 jakadinho-laptop kernel: [   20.834743] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
Jan 20 23:57:00 jakadinho-laptop kernel: [   20.836895] i8042.c: Detected active multiplexing controller, rev 1.1.
Jan 20 23:57:00 jakadinho-laptop kernel: [   20.838370] serio: i8042 KBD port at 0x60,0x64 irq 1
Jan 20 23:57:00 jakadinho-laptop kernel: [   20.838375] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Jan 20 23:57:00 jakadinho-laptop kernel: [   20.838378] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Jan 20 23:57:00 jakadinho-laptop kernel: [   20.838381] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Jan 20 23:57:00 jakadinho-laptop kernel: [   20.838383] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Jan 20 23:57:00 jakadinho-laptop kernel: [   20.838523] mice: PS/2 mouse device common for all mice
Jan 20 23:57:00 jakadinho-laptop kernel: [   20.838656] EISA: Probing bus 0 at eisa.0
Jan 20 23:57:00 jakadinho-laptop kernel: [   20.838693] EISA: Detected 0 cards.
Jan 20 23:57:00 jakadinho-laptop kernel: [   20.838781] TCP cubic registered
Jan 20 23:57:00 jakadinho-laptop kernel: [   20.838794] NET: Registered protocol family 1
Jan 20 23:57:00 jakadinho-laptop kernel: [   20.838814] Using IPI No-Shortcut mode
Jan 20 23:57:00 jakadinho-laptop kernel: [   20.838988]   Magic number: 8:802:959
Jan 20 23:57:00 jakadinho-laptop kernel: [   20.838997]   hash matches device ttyb0
Jan 20 23:57:00 jakadinho-laptop kernel: [   20.839291] Freeing unused kernel memory: 364k freed
Jan 20 23:57:00 jakadinho-laptop kernel: [   20.871420] input: AT Translated Set 2 keyboard as /class/input/input1
Jan 20 23:57:00 jakadinho-laptop kernel: [   22.037521] fuse init (API version 7.8)
Jan 20 23:57:00 jakadinho-laptop kernel: [   22.042396] Capability LSM initialized
Jan 20 23:57:00 jakadinho-laptop kernel: [   22.045726] ACPI: Transitioning device [FN00] to D3
Jan 20 23:57:00 jakadinho-laptop kernel: [   22.045729] ACPI: Transitioning device [FN00] to D3
Jan 20 23:57:00 jakadinho-laptop kernel: [   22.045732] ACPI: Fan [FN00] (off)
Jan 20 23:57:00 jakadinho-laptop kernel: [   22.049806] ACPI Warning (tbutils-0217): Incorrect checksum in table [SSDT] -  83, should be 4D [20070126]
Jan 20 23:57:00 jakadinho-laptop kernel: [   22.049815] ACPI: SSDT 3FFD7B90, 0CC3 (r1    AMI   CPU1PM        1 INTL 20051117)
Jan 20 23:57:00 jakadinho-laptop kernel: [   22.050194] ACPI: CPU0 (power states: C1[C1] C2[C2])
Jan 20 23:57:00 jakadinho-laptop kernel: [   22.050198] ACPI: Processor [CPU1] (supports 8 throttling states)
Jan 20 23:57:00 jakadinho-laptop kernel: [   22.050253] ACPI Warning (tbutils-0217): Incorrect checksum in table [SSDT] -  1A, should be E0 [20070126]
Jan 20 23:57:00 jakadinho-laptop kernel: [   22.050258] ACPI: SSDT 3FFD8860, 04A4 (r1    AMI   CPU2PM        1 INTL 20051117)
Jan 20 23:57:00 jakadinho-laptop kernel: [   22.050642] ACPI: CPU1 (power states: C1[C1] C2[C2])
Jan 20 23:57:00 jakadinho-laptop kernel: [   22.050647] ACPI: Processor [CPU2] (supports 8 throttling states)
Jan 20 23:57:00 jakadinho-laptop kernel: [   22.060002] ACPI: Thermal Zone [THRM] (65 C)
Jan 20 23:57:00 jakadinho-laptop kernel: [    3.340000] Marking TSC unstable due to: possible TSC halt in C2.
Jan 20 23:57:00 jakadinho-laptop kernel: [    3.344000] Time: acpi_pm clocksource has been installed.
Jan 20 23:57:00 jakadinho-laptop kernel: [    3.796000] r8169 Gigabit Ethernet driver 2.2LK loaded
Jan 20 23:57:00 jakadinho-laptop kernel: [    3.796000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Jan 20 23:57:00 jakadinho-laptop kernel: [    3.796000] eth0: RTL8168b/8111b at 0xf8850000, 00:18:f3:ce:b1:06, XID 38000000 IRQ 16
Jan 20 23:57:00 jakadinho-laptop kernel: [    3.828000] usbcore: registered new interface driver usbfs
Jan 20 23:57:00 jakadinho-laptop kernel: [    3.828000] usbcore: registered new interface driver hub
Jan 20 23:57:00 jakadinho-laptop kernel: [    3.828000] usbcore: registered new device driver usb
Jan 20 23:57:00 jakadinho-laptop kernel: [    3.828000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 20
Jan 20 23:57:00 jakadinho-laptop kernel: [    3.828000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Jan 20 23:57:00 jakadinho-laptop kernel: [    3.828000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
Jan 20 23:57:00 jakadinho-laptop kernel: [    3.828000] ehci_hcd 0000:00:1d.7: debug port 1
Jan 20 23:57:00 jakadinho-laptop kernel: [    3.828000] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xfebfbc00
Jan 20 23:57:00 jakadinho-laptop kernel: [    3.832000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Jan 20 23:57:00 jakadinho-laptop kernel: [    3.832000] usb usb1: configuration #1 chosen from 1 choice
Jan 20 23:57:00 jakadinho-laptop kernel: [    3.832000] hub 1-0:1.0: USB hub found
Jan 20 23:57:00 jakadinho-laptop kernel: [    3.832000] hub 1-0:1.0: 8 ports detected
Jan 20 23:57:00 jakadinho-laptop kernel: [    3.856000] SCSI subsystem initialized
Jan 20 23:57:00 jakadinho-laptop kernel: [    3.896000] USB Universal Host Controller Interface driver v3.0
Jan 20 23:57:00 jakadinho-laptop kernel: [    3.936000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 20
Jan 20 23:57:00 jakadinho-laptop kernel: [    3.936000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Jan 20 23:57:00 jakadinho-laptop kernel: [    3.936000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Jan 20 23:57:00 jakadinho-laptop kernel: [    3.936000] uhci_hcd 0000:00:1d.0: irq 20, io base 0x0000ec00
Jan 20 23:57:00 jakadinho-laptop kernel: [    3.936000] usb usb2: configuration #1 chosen from 1 choice
Jan 20 23:57:00 jakadinho-laptop kernel: [    3.936000] hub 2-0:1.0: USB hub found
Jan 20 23:57:00 jakadinho-laptop kernel: [    3.936000] hub 2-0:1.0: 2 ports detected
Jan 20 23:57:00 jakadinho-laptop kernel: [    4.040000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 20 (level, low) -> IRQ 17
Jan 20 23:57:00 jakadinho-laptop kernel: [    4.040000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Jan 20 23:57:00 jakadinho-laptop kernel: [    4.040000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
Jan 20 23:57:00 jakadinho-laptop kernel: [    4.040000] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000e880
Jan 20 23:57:00 jakadinho-laptop kernel: [    4.040000] usb usb3: configuration #1 chosen from 1 choice
Jan 20 23:57:00 jakadinho-laptop kernel: [    4.040000] hub 3-0:1.0: USB hub found
Jan 20 23:57:00 jakadinho-laptop kernel: [    4.040000] hub 3-0:1.0: 2 ports detected
Jan 20 23:57:00 jakadinho-laptop kernel: [    4.144000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 22 (level, low) -> IRQ 21
Jan 20 23:57:00 jakadinho-laptop kernel: [    4.144000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Jan 20 23:57:00 jakadinho-laptop kernel: [    4.144000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
Jan 20 23:57:00 jakadinho-laptop kernel: [    4.144000] uhci_hcd 0000:00:1d.2: irq 21, io base 0x0000e800
Jan 20 23:57:00 jakadinho-laptop kernel: [    4.144000] usb usb4: configuration #1 chosen from 1 choice
Jan 20 23:57:00 jakadinho-laptop kernel: [    4.144000] hub 4-0:1.0: USB hub found
Jan 20 23:57:00 jakadinho-laptop kernel: [    4.144000] hub 4-0:1.0: 2 ports detected
Jan 20 23:57:00 jakadinho-laptop kernel: [    4.248000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 18 (level, low) -> IRQ 22
Jan 20 23:57:00 jakadinho-laptop kernel: [    4.248000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Jan 20 23:57:00 jakadinho-laptop kernel: [    4.248000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
Jan 20 23:57:00 jakadinho-laptop kernel: [    4.248000] uhci_hcd 0000:00:1d.3: irq 22, io base 0x0000e480
Jan 20 23:57:00 jakadinho-laptop kernel: [    4.248000] usb usb5: configuration #1 chosen from 1 choice
Jan 20 23:57:00 jakadinho-laptop kernel: [    4.248000] hub 5-0:1.0: USB hub found
Jan 20 23:57:00 jakadinho-laptop kernel: [    4.248000] hub 5-0:1.0: 2 ports detected
Jan 20 23:57:00 jakadinho-laptop kernel: [    4.352000] ACPI: PCI Interrupt 0000:04:01.1[B] -> GSI 18 (level, low) -> IRQ 22
Jan 20 23:57:00 jakadinho-laptop kernel: [    4.380000] usb 1-4: new high speed USB device using ehci_hcd and address 3
Jan 20 23:57:00 jakadinho-laptop kernel: [    4.404000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[22]  MMIO=[feaff800-feafffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
Jan 20 23:57:00 jakadinho-laptop kernel: [    4.412000] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
Jan 20 23:57:00 jakadinho-laptop kernel: [    4.412000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 18
Jan 20 23:57:00 jakadinho-laptop kernel: [    4.412000] scsi0 : ata_piix
Jan 20 23:57:00 jakadinho-laptop kernel: [    4.412000] scsi1 : ata_piix
Jan 20 23:57:00 jakadinho-laptop kernel: [    4.412000] ata1: SATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ffa0 irq 14
Jan 20 23:57:00 jakadinho-laptop kernel: [    4.412000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ffa8 irq 15
Jan 20 23:57:00 jakadinho-laptop kernel: [    4.576000] ata1.00: ATA-7: Hitachi HTS541612J9SA00, SBDOC70P, max UDMA/100
Jan 20 23:57:00 jakadinho-laptop kernel: [    4.576000] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 0/32)
Jan 20 23:57:00 jakadinho-laptop kernel: [    4.596000] ata1.00: configured for UDMA/100
Jan 20 23:57:00 jakadinho-laptop kernel: [    4.804000] usb 1-4: configuration #1 chosen from 1 choice
Jan 20 23:57:00 jakadinho-laptop kernel: [    4.940000] ata2.00: ATAPI: TSSTcorpCD/DVDW TS-L632D, AS05, max UDMA/33
Jan 20 23:57:00 jakadinho-laptop kernel: [    5.132000] ata2.00: configured for UDMA/33
Jan 20 23:57:00 jakadinho-laptop kernel: [    5.132000] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54161 SBDO PQ: 0 ANSI: 5
Jan 20 23:57:00 jakadinho-laptop kernel: [    5.140000] scsi 1:0:0:0: CD-ROM            TSSTcorp CD/DVDW TS-L632D AS05 PQ: 0 ANSI: 5
Jan 20 23:57:00 jakadinho-laptop kernel: [    5.144000] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
Jan 20 23:57:00 jakadinho-laptop kernel: [    5.144000] sd 0:0:0:0: [sda] Write Protect is off
Jan 20 23:57:00 jakadinho-laptop kernel: [    5.144000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jan 20 23:57:00 jakadinho-laptop kernel: [    5.144000] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
Jan 20 23:57:00 jakadinho-laptop kernel: [    5.144000] sd 0:0:0:0: [sda] Write Protect is off
Jan 20 23:57:00 jakadinho-laptop kernel: [    5.144000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jan 20 23:57:00 jakadinho-laptop kernel: [    5.144000]  sda: sda1 sda2 sda3 < sda5 sda6 > sda4
Jan 20 23:57:00 jakadinho-laptop kernel: [    5.216000] sd 0:0:0:0: [sda] Attached SCSI disk
Jan 20 23:57:00 jakadinho-laptop kernel: [    5.220000] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jan 20 23:57:00 jakadinho-laptop kernel: [    5.220000] sr 1:0:0:0: Attached scsi generic sg1 type 5
Jan 20 23:57:00 jakadinho-laptop kernel: [    5.292000] usb 1-6: new high speed USB device using ehci_hcd and address 5
Jan 20 23:57:00 jakadinho-laptop kernel: [    5.296000] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Jan 20 23:57:00 jakadinho-laptop kernel: [    5.296000] Uniform CD-ROM driver Revision: 3.20
Jan 20 23:57:00 jakadinho-laptop kernel: [    5.424000] usb 1-6: configuration #1 chosen from 1 choice
Jan 20 23:57:00 jakadinho-laptop kernel: [    5.620000] EXT3-fs: INFO: recovery required on readonly filesystem.
Jan 20 23:57:00 jakadinho-laptop kernel: [    5.620000] EXT3-fs: write access will be enabled during recovery.
Jan 20 23:57:00 jakadinho-laptop kernel: [    5.668000] usb 2-2: new low speed USB device using uhci_hcd and address 2
Jan 20 23:57:00 jakadinho-laptop kernel: [    5.844000] usb 2-2: configuration #1 chosen from 1 choice
Jan 20 23:57:00 jakadinho-laptop kernel: [    6.228000] usb 4-1: new full speed USB device using uhci_hcd and address 2
Jan 20 23:57:00 jakadinho-laptop kernel: [    6.472000] usb 4-1: configuration #1 chosen from 1 choice
Jan 20 23:57:00 jakadinho-laptop kernel: [    6.604000] usbcore: registered new interface driver libusual
Jan 20 23:57:00 jakadinho-laptop kernel: [    6.604000] usbcore: registered new interface driver hiddev
Jan 20 23:57:00 jakadinho-laptop kernel: [    6.608000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Jan 20 23:57:00 jakadinho-laptop kernel: [    6.608000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Jan 20 23:57:00 jakadinho-laptop kernel: [    6.608000] Initializing USB Mass Storage driver...
Jan 20 23:57:00 jakadinho-laptop kernel: [    6.608000] scsi2 : SCSI emulation for USB Mass Storage devices
Jan 20 23:57:00 jakadinho-laptop kernel: [    6.616000] input: Logitech USB Receiver as /class/input/input2
Jan 20 23:57:00 jakadinho-laptop kernel: [    6.616000] input: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-2
Jan 20 23:57:00 jakadinho-laptop kernel: [    6.648000] input: Logitech USB Receiver as /class/input/input3
Jan 20 23:57:00 jakadinho-laptop kernel: [    6.648000] input,hiddev96: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.0-2
Jan 20 23:57:00 jakadinho-laptop kernel: [    6.648000] usbcore: registered new interface driver usbhid
Jan 20 23:57:00 jakadinho-laptop kernel: [    6.648000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Jan 20 23:57:00 jakadinho-laptop kernel: [    6.652000] usbcore: registered new interface driver usb-storage
Jan 20 23:57:00 jakadinho-laptop kernel: [    6.652000] USB Mass Storage support registered.
Jan 20 23:57:00 jakadinho-laptop kernel: [    9.904000] kjournald starting.  Commit interval 5 seconds
Jan 20 23:57:00 jakadinho-laptop kernel: [    9.904000] EXT3-fs: recovery complete.
Jan 20 23:57:00 jakadinho-laptop kernel: [    9.904000] EXT3-fs: mounted filesystem with ordered data mode.
Jan 20 23:57:00 jakadinho-laptop kernel: [   11.608000] scsi 2:0:0:0: Direct-Access     WD       5000AAK External 1.65 PQ: 0 ANSI: 0
Jan 20 23:57:00 jakadinho-laptop kernel: [   11.608000] sd 2:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
Jan 20 23:57:00 jakadinho-laptop kernel: [   11.608000] sd 2:0:0:0: [sdb] Write Protect is off
Jan 20 23:57:00 jakadinho-laptop kernel: [   11.608000] sd 2:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
Jan 20 23:57:00 jakadinho-laptop kernel: [   11.612000] sd 2:0:0:0: [sdb] Write Protect is off
Jan 20 23:57:00 jakadinho-laptop kernel: [   11.612000]  sdb: sdb1
Jan 20 23:57:00 jakadinho-laptop kernel: [   17.780000] sd 2:0:0:0: [sdb] Attached SCSI disk
Jan 20 23:57:00 jakadinho-laptop kernel: [   17.780000] sd 2:0:0:0: Attached scsi generic sg2 type 0
Jan 20 23:57:00 jakadinho-laptop kernel: [   18.456000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jan 20 23:57:00 jakadinho-laptop kernel: [   18.468000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jan 20 23:57:00 jakadinho-laptop kernel: [   18.544000] sdhci: Secure Digital Host Controller Interface driver
Jan 20 23:57:00 jakadinho-laptop kernel: [   18.544000] sdhci: Copyright(c) Pierre Ossman
Jan 20 23:57:00 jakadinho-laptop kernel: [   18.544000] sdhci: SDHCI controller found at 0000:04:01.2 [1180:0822] (rev 17)
Jan 20 23:57:00 jakadinho-laptop kernel: [   18.544000] ACPI: PCI Interrupt 0000:04:01.2[B] -> GSI 18 (level, low) -> IRQ 22
Jan 20 23:57:00 jakadinho-laptop kernel: [   18.544000] mmc0: SDHCI at 0xfeaff400 irq 22 DMA
Jan 20 23:57:00 jakadinho-laptop kernel: [   18.612000] iTCO_vendor_support: vendor-support=0
Jan 20 23:57:00 jakadinho-laptop kernel: [   18.612000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
Jan 20 23:57:00 jakadinho-laptop kernel: [   18.696000] Yenta: CardBus bridge found at 0000:04:01.0 [1043:1437]
Jan 20 23:57:00 jakadinho-laptop kernel: [   18.712000] Linux agpgart interface v0.102 (c) Dave Jones
Jan 20 23:57:00 jakadinho-laptop kernel: [   18.824000] Yenta: ISA IRQ mask 0x0cb8, PCI irq 19
Jan 20 23:57:00 jakadinho-laptop kernel: [   18.824000] Socket status: 30000006
Jan 20 23:57:00 jakadinho-laptop kernel: [   18.824000] Yenta: Raising subordinate bus# of parent bus (#04) from #05 to #08
Jan 20 23:57:00 jakadinho-laptop kernel: [   18.824000] pcmcia: parent PCI bridge I/O window: 0xd000 - 0xdfff
Jan 20 23:57:00 jakadinho-laptop kernel: [   18.824000] cs: IO port probe 0xd000-0xdfff: clean.
Jan 20 23:57:00 jakadinho-laptop kernel: [   18.824000] pcmcia: parent PCI bridge Memory window: 0xfe200000 - 0xfeafffff
Jan 20 23:57:00 jakadinho-laptop kernel: [   18.824000] pcmcia: parent PCI bridge Memory window: 0xddf00000 - 0xdfefffff
Jan 20 23:57:00 jakadinho-laptop kernel: [   18.888000] ieee80211: 802.11 data/management/control stack, git-1.1.13
Jan 20 23:57:00 jakadinho-laptop kernel: [   18.888000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Jan 20 23:57:00 jakadinho-laptop kernel: [   18.952000] Bluetooth: Core ver 2.11
Jan 20 23:57:00 jakadinho-laptop kernel: [   18.960000] NET: Registered protocol family 31
Jan 20 23:57:00 jakadinho-laptop kernel: [   18.960000] Bluetooth: HCI device and connection manager initialized
Jan 20 23:57:00 jakadinho-laptop kernel: [   18.960000] Bluetooth: HCI socket layer initialized
Jan 20 23:57:00 jakadinho-laptop kernel: [   18.980000] Bluetooth: HCI USB driver ver 2.9
Jan 20 23:57:00 jakadinho-laptop kernel: [   18.992000] usbcore: registered new interface driver hci_usb
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.008000] usbcore: registered new interface driver xpad
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.008000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: driver for Xbox controllers v0.1.6
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.044000] Synaptics Touchpad, model: 1, fw: 6.1, id: 0xa3a0b3, caps: 0xa04713/0x10008
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.080000] input: SynPS/2 Synaptics TouchPad as /class/input/input4
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.080000] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x0860)
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.080000] input: PC Speaker as /class/input/input5
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.080000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.116000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.120000] [fglrx] Maximum main memory to use for locked dma buffers: 929 MBytes.
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.120000] [fglrx] USWC is disabled in module parameters
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.120000] [fglrx] PAT is disabled!
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.120000] [fglrx] module loaded - fglrx 8.40.4 [Jul 31 2007] on minor 0
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.128000] Linux video capture interface: v2.00
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.192000] stk11xx: Syntek USB2.0 webcam driver startup
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.192000] stk11xx: Syntek USB2.0 - STK-1135 based webcam found.
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.192000] stk11xx: Syntek AVStream USB2.0 1.3M WebCam - Product ID 0xA311.
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.192000] stk11xx: Release: 0005
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.192000] stk11xx: Number of interfaces : 1
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.192000] stk11xx: Initialize USB2.0 Syntek Camera
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.204000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.2mp
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.204000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.204000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 19 (level, low) -> IRQ 18
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.216000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.412000] stk11xx: Syntek USB2.0 Camera is ready
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.412000] stk11xx: Syntek USB2.0 Camera is now controlling video device /dev/video0
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.412000] usbcore: registered new interface driver usb_stk11xx_driver
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.412000] stk11xx: v1.3.0 : Syntek USB Video Camera
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.416000] cs: IO port probe 0x100-0x3af: clean.
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.416000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.416000] cs: IO port probe 0x820-0x8ff: clean.
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.416000] cs: IO port probe 0xc00-0xcf7: clean.
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.420000] cs: IO port probe 0xa00-0xaff: clean.
Jan 20 23:57:00 jakadinho-laptop kernel: [   19.600000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 23
Jan 20 23:57:00 jakadinho-laptop kernel: [   21.180000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
Jan 20 23:57:00 jakadinho-laptop kernel: [   21.204000] lp: driver loaded but no devices found
Jan 20 23:57:00 jakadinho-laptop kernel: [   21.320000] asus-laptop: Asus Laptop Support version 0.42-cvs
Jan 20 23:57:00 jakadinho-laptop kernel: [   21.320000] asus-laptop:   A6Je model detected
Jan 20 23:57:00 jakadinho-laptop kernel: [   21.328000] Registered led device: asus:mail
Jan 20 23:57:00 jakadinho-laptop kernel: [   21.908000] EXT3 FS on sda2, internal journal
Jan 20 23:57:00 jakadinho-laptop kernel: [   22.920000] kjournald starting.  Commit interval 5 seconds
Jan 20 23:57:00 jakadinho-laptop kernel: [   22.932000] EXT3 FS on sda1, internal journal
Jan 20 23:57:00 jakadinho-laptop kernel: [   22.932000] EXT3-fs: mounted filesystem with ordered data mode.
Jan 20 23:57:00 jakadinho-laptop kernel: [   25.248000] No dock devices found.
Jan 20 23:57:00 jakadinho-laptop kernel: [   25.320000] ACPI: Battery Slot [BAT0] (battery present)
Jan 20 23:57:00 jakadinho-laptop kernel: [   25.372000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
Jan 20 23:57:00 jakadinho-laptop kernel: [   25.384000] ACPI: AC Adapter [AC0] (on-line)
Jan 20 23:57:00 jakadinho-laptop kernel: [   25.408000] input: Power Button (FF) as /class/input/input6
Jan 20 23:57:00 jakadinho-laptop kernel: [   25.408000] ACPI: Power Button (FF) [PWRF]
Jan 20 23:57:00 jakadinho-laptop kernel: [   25.408000] input: Lid Switch as /class/input/input7
Jan 20 23:57:00 jakadinho-laptop kernel: [   25.408000] ACPI: Lid Switch [LID]
Jan 20 23:57:00 jakadinho-laptop kernel: [   25.408000] input: Power Button (CM) as /class/input/input8
Jan 20 23:57:00 jakadinho-laptop kernel: [   25.408000] ACPI: Power Button (CM) [PWRB]
Jan 20 23:57:00 jakadinho-laptop kernel: [   25.408000] input: Sleep Button (CM) as /class/input/input9
Jan 20 23:57:00 jakadinho-laptop kernel: [   25.408000] ACPI: Sleep Button (CM) [SLPB]
Jan 20 23:57:01 jakadinho-laptop kernel: [   26.748000] r8169: eth2: link up
Jan 20 23:57:01 jakadinho-laptop kernel: [   26.748000] r8169: eth2: link up
Jan 20 23:57:03 jakadinho-laptop kernel: [   28.772000] ppdev: user-space parallel port driver
Jan 20 23:57:04 jakadinho-laptop kernel: [   29.500000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Jan 20 23:57:04 jakadinho-laptop kernel: [   29.564000] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
Jan 20 23:57:04 jakadinho-laptop kernel: [   29.740000] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Jan 20 23:57:04 jakadinho-laptop kernel: [   29.756000] NFSD: starting 90-second grace period
Jan 20 23:57:06 jakadinho-laptop dhcdbd: Started up.
Jan 20 23:57:06 jakadinho-laptop kernel: [   31.164000] Bluetooth: L2CAP ver 2.8
Jan 20 23:57:06 jakadinho-laptop kernel: [   31.164000] Bluetooth: L2CAP socket layer initialized
Jan 20 23:57:06 jakadinho-laptop kernel: [   31.240000] Bluetooth: RFCOMM socket layer initialized
Jan 20 23:57:06 jakadinho-laptop kernel: [   31.240000] Bluetooth: RFCOMM TTY layer initialized
Jan 20 23:57:06 jakadinho-laptop kernel: [   31.240000] Bluetooth: RFCOMM ver 1.8
Jan 20 23:57:06 jakadinho-laptop kernel: [   31.672000] [fglrx] total      GART = 130023424
Jan 20 23:57:06 jakadinho-laptop kernel: [   31.672000] [fglrx] free       GART = 114032640
Jan 20 23:57:06 jakadinho-laptop kernel: [   31.672000] [fglrx] max single GART = 114032640
Jan 20 23:57:06 jakadinho-laptop kernel: [   31.672000] [fglrx] total      LFB  = 134086656
Jan 20 23:57:06 jakadinho-laptop kernel: [   31.672000] [fglrx] free       LFB  = 99209216
Jan 20 23:57:06 jakadinho-laptop kernel: [   31.672000] [fglrx] max single LFB  = 99209216
Jan 20 23:57:06 jakadinho-laptop kernel: [   31.672000] [fglrx] total      Inv  = 0
Jan 20 23:57:06 jakadinho-laptop kernel: [   31.672000] [fglrx] free       Inv  = 0
Jan 20 23:57:06 jakadinho-laptop kernel: [   31.672000] [fglrx] max single Inv  = 0
Jan 20 23:57:06 jakadinho-laptop kernel: [   31.672000] [fglrx] total      TIM  = 0
Jan 20 23:57:08 jakadinho-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth2 for sub-path eth2.dbus.get.reason
Jan 20 23:57:10 jakadinho-laptop kernel: [   35.436000] NET: Registered protocol family 17
Jan 20 23:57:11 jakadinho-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth2 for sub-path eth2.dbus.get.host_name
Jan 20 23:57:11 jakadinho-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth2 for sub-path eth2.dbus.get.nis_domain
Jan 20 23:57:11 jakadinho-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth2 for sub-path eth2.dbus.get.nis_servers


I dont understand this log but i guess the problem is in last few lines that coused it. So it might be about  lan driver or graphic one. Any ideas

---

### Post by rosegarden78 on 2008-01-21
Someone will be with you shortly please hold ... 	](*,)

---

