---
title: "failed command: WRITE DMA"
date: 2013-01-16
forum: General Help
---

### Post by ARMac on 2013-01-16
Hi all. I am getting the following error occasionally. There is no specific time or action that triggers this, it happens if the disk is idle or in use.

```
Jan 17 00:16:34 mkdlab1 kernel: [ 1991.008082] ata1: lost interrupt (Status 0x50)
Jan 17 00:16:34 mkdlab1 kernel: [ 1991.008124] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Jan 17 00:16:34 mkdlab1 kernel: [ 1991.008530] ata1.00: failed command: WRITE DMA
Jan 17 00:16:34 mkdlab1 kernel: [ 1991.008798] ata1.00: cmd ca/00:08:38:37:49/00:00:00:00:00/e4 tag 0 dma 4096 out
Jan 17 00:16:34 mkdlab1 kernel: [ 1991.008805]          res 40/00:00:09:4f:c2/00:00:00:00:00/10 Emask 0x4 (timeout)
Jan 17 00:16:34 mkdlab1 kernel: [ 1991.009594] ata1.00: status: { DRDY }
Jan 17 00:16:34 mkdlab1 kernel: [ 1991.009832] ata1: soft resetting link
Jan 17 00:16:34 mkdlab1 kernel: [ 1991.180395] ata1: FORCE: cable set to 40c
Jan 17 00:16:34 mkdlab1 kernel: [ 1991.188351] ata1.00: configured for UDMA/33
Jan 17 00:16:34 mkdlab1 kernel: [ 1991.196245] ata1.01: configured for UDMA/33
Jan 17 00:16:34 mkdlab1 kernel: [ 1991.196282] ata1: EH complete
```

The disk drive WD Caviar 160gb SATA (WD1600JS-22NCB1) has been checked with all possible tools, sata cable and PSU has been replaced. 

The only thing I managed to do that somehow lowered the amount of those errors is that i added "libata.force=40c" in the grub, that forces the system to think 40 wires ata cable is in use (which makes no sense since the drive is sata), but I still get this occasionally. The system does not freeze or lock up when this happens. Hdd was scanned with HDAT2, HDD sentinel, WD Diagnostics etc. SMART is clean, no bad or reallocated sectors.

The system spec:
Asrock pv530a-itx
2-gb DDR3
Connected on onboard SATA controller:
HDD1 WD160gb (the problematic one)
HDD2 WD80gb
Hard drives connected on addon IDE/SATA controller (VIA VT6421)
HDD3 Excelstore PATA 160GB
HDD4 Maxtor PATA 80gb

Thats about it.

Edit, forgot to mention its Ubuntu server 12.04

Here is complete dmesg log.
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-29-generic-pae (buildd@roseapple) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #46-Ubuntu SMP Fri Jul 27 17:25:43 UTC 2012 (Ubuntu 3.2.0-29.46-generic-pae 3.2.24)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e8000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007efa0000 (usable)
[    0.000000]  BIOS-e820: 000000007efa0000 - 000000007efb0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007efb0000 - 000000007efe0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007efe0000 - 000000007f000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fecc0000 - 00000000fecc1000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI present.
[    0.000000] DMI: To Be Filled By O.E.M. To Be Filled By O.E.M./PV530A-ITX, BIOS P1.00 12/20/2011
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x7efa0 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-DFFFF uncachable
[    0.000000]   E0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 07F000000 mask FFF000000 uncachable
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2032MB, range: 16MB, type UC
[    0.000000] total RAM covered: 2032M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K 	chunk_size: 32M 	num_reg: 2  	lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2032MB, range: 16MB, type UC
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] initial memory mapped : 0 - 02000000
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-0000000037bfe000
[    0.000000]  0000000000 - 0000200000 page 4k
[    0.000000]  0000200000 - 0037a00000 page 2M
[    0.000000]  0037a00000 - 0037bfe000 page 4k
[    0.000000] kernel direct mapping tables up to 37bfe000 @ 1ffb000-2000000
[    0.000000] RAMDISK: 364e4000 - 3726a000
[    0.000000] ACPI: RSDP 000fadf0 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 7efa0000 00040 (v01 122011 RSDT2129 20111220 MSFT 00000097)
[    0.000000] ACPI: FACP 7efa0200 00084 (v01 122011 FACP2129 20111220 MSFT 00000097)
[    0.000000] ACPI: DSDT 7efa0430 03B72 (v01  AS615 AS615004 00000004 INTL 20051117)
[    0.000000] ACPI: FACS 7efb0000 00040
[    0.000000] ACPI: APIC 7efa0390 00060 (v01 122011 APIC2129 20111220 MSFT 00000097)
[    0.000000] ACPI: MCFG 7efa03f0 0003C (v01 122011 OEMMCFG  20111220 MSFT 00000097)
[    0.000000] ACPI: OEMB 7efb0040 00082 (v01 122011 OEMB2129 20111220 MSFT 00000097)
[    0.000000] ACPI: AAFT 7efaa430 00027 (v01 122011 OEMAAFT  20111220 MSFT 00000097)
[    0.000000] ACPI: HPET 7efaa460 00038 (v01 122011 VIA HPET 20111220 MSFT 00000097)
[    0.000000] ACPI: SSDT 7efb00d0 0023A (v01    AMI   P001PM 00000001 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1139MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00037bfe
[    0.000000]   HighMem  0x00037bfe -> 0x0007efa0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007efa0
[    0.000000] On node 0 totalpages: 519983
[    0.000000] free_area_init_node: node 0, pgdat c1866a40, node_mem_map f5504200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 222502 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2280 pages used for memmap
[    0.000000]   HighMem zone: 289466 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfecc0000] gsi_base[24])
[    0.000000] IOAPIC[1]: apic_id 2, version 3, address 0xfecc0000, GSI 24-47
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x11068201 base: 0xfed00000
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 64
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e8000
[    0.000000] PM: Registered nosave memory: 00000000000e8000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 7f000000 (gap: 7f000000:7fc00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @f7be3000 s34240 r0 d23104 u57344
[    0.000000] pcpu-alloc: s34240 r0 d23104 u57344 alloc=14*4096
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 515919
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-29-generic-pae root=UUID=907cf675-ed0e-4de0-997a-94d16c15ad69 ro libata.force=40c
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 8321280 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:0007efa0)
[    0.000000] Memory: 2030432k/2080384k available (5814k kernel code, 49500k reserved, 2841k data, 740k init, 1166984k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc1875000 - 0xc192e000   ( 740 kB)
[    0.000000]       .data : 0xc15adb64 - 0xc1874240   (2841 kB)
[    0.000000]       .text : 0xc1000000 - 0xc15adb64   (5814 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:256 16
[    0.000000] CPU 0 irqstacks, hard=f5008000 soft=f500a000
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1795.394 MHz processor.
[    0.004003] Calibrating delay loop (skipped), value calculated using timer frequency.. 3590.78 BogoMIPS (lpj=7181576)
[    0.004029] pid_max: default: 32768 minimum: 301
[    0.004087] Security Framework initialized
[    0.004129] AppArmor: AppArmor initialized
[    0.004140] Yama: becoming mindful.
[    0.004266] Mount-cache hash table entries: 512
[    0.004519] Initializing cgroup subsys cpuacct
[    0.004542] Initializing cgroup subsys memory
[    0.004564] Initializing cgroup subsys devices
[    0.004576] Initializing cgroup subsys freezer
[    0.004589] Initializing cgroup subsys blkio
[    0.004607] Initializing cgroup subsys perf_event
[    0.005022] SMP alternatives: switching to UP code
[    0.029735] Freeing SMP alternatives: 24k freed
[    0.029781] ACPI: Core revision 20110623
[    0.040017] ftrace: allocating 26545 entries in 52 pages
[    0.044115] Enabling APIC mode:  Flat.  Using 2 I/O APICs
[    0.044752] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.084926] CPU0: Centaur VIA C7-D Processor 1800MHz stepping 00
[    0.088009] Performance Events: 
[    0.088292] NMI watchdog disabled (cpu0): hardware events not enabled
[    0.088362] Brought up 1 CPUs
[    0.088372] Total of 1 processors activated (3590.78 BogoMIPS).
[    0.089216] devtmpfs: initialized
[    0.089467] EVM: security.selinux
[    0.089475] EVM: security.SMACK64
[    0.089483] EVM: security.capability
[    0.089551] PM: Registering ACPI NVS region at 7efb0000 (196608 bytes)
[    0.092069] print_constraints: dummy: 
[    0.092135] RTC time: 22:43:23, date: 01/16/13
[    0.092225] NET: Registered protocol family 16
[    0.092472] EISA bus registered
[    0.092505] ACPI: bus type pci registered
[    0.092657] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.092678] PCI: not using MMCONFIG
[    0.092901] PCI : PCI BIOS aera is rw and x. Use pci=nobios if you want it NX.
[    0.092977] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=3
[    0.092988] PCI: Using configuration type 1 for base access
[    0.095749] bio: create slab <bio-0> at 0
[    0.095956] ACPI: Added _OSI(Module Device)
[    0.095967] ACPI: Added _OSI(Processor Device)
[    0.095978] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.095988] ACPI: Added _OSI(Processor Aggregator Device)
[    0.097628] ACPI: EC: Look up EC in DSDT
[    0.100217] ACPI: Executed 2 blocks of module-level executable AML code
[    0.104237] ACPI: Interpreter enabled
[    0.104262] ACPI: (supports S0 S1 S4 S5)
[    0.104306] ACPI: Using IOAPIC for interrupt routing
[    0.104360] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.104426] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.104442] PCI: Using MMCONFIG for extended config space
[    0.105424] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.112556] ACPI: No dock devices found.
[    0.112576] HEST: Table not found.
[    0.112591] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.113226] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.114024] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
[    0.114039] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
[    0.114052] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.114069] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff]
[    0.114085] pci_root PNP0A03:00: host bridge window [mem 0x7f000000-0xdfffffff]
[    0.114102] pci_root PNP0A03:00: host bridge window [mem 0xf0000000-0xfebfffff]
[    0.114140] pci 0000:00:00.0: [1106:0410] type 0 class 0x000600
[    0.114209] pci 0000:00:00.1: [1106:1410] type 0 class 0x000600
[    0.114267] pci 0000:00:00.2: [1106:2410] type 0 class 0x000600
[    0.114324] pci 0000:00:00.3: [1106:3410] type 0 class 0x000600
[    0.114381] pci 0000:00:00.4: [1106:4410] type 0 class 0x000600
[    0.114439] pci 0000:00:00.5: [1106:5410] type 0 class 0x000600
[    0.114501] pci 0000:00:00.6: [1106:6410] type 0 class 0x000600
[    0.114558] pci 0000:00:00.7: [1106:7410] type 0 class 0x000600
[    0.114619] pci 0000:00:01.0: [1106:7122] type 0 class 0x000300
[    0.114637] pci 0000:00:01.0: reg 10: [mem 0xfd000000-0xfdffffff]
[    0.114649] pci 0000:00:01.0: reg 14: [mem 0xfc000000-0xfcffffff]
[    0.114661] pci 0000:00:01.0: reg 18: [mem 0xfa000000-0xfaffffff pref]
[    0.114687] pci 0000:00:01.0: reg 30: [mem 0xfeaf0000-0xfeafffff pref]
[    0.114716] pci 0000:00:01.0: supports D1 D2
[    0.114741] pci 0000:00:03.0: [1106:a410] type 1 class 0x000604
[    0.114825] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
[    0.114833] pci 0000:00:03.0: PME# disabled
[    0.114866] pci 0000:00:03.2: [1106:c410] type 1 class 0x000604
[    0.114949] pci 0000:00:03.2: PME# supported from D0 D3hot D3cold
[    0.114957] pci 0000:00:03.2: PME# disabled
[    0.114986] pci 0000:00:03.4: [1106:e410] type 0 class 0x000600
[    0.115062] pci 0000:00:0f.0: [1106:9001] type 0 class 0x000101
[    0.115082] pci 0000:00:0f.0: reg 10: [io  0xcc00-0xcc07]
[    0.115095] pci 0000:00:0f.0: reg 14: [io  0xc880-0xc883]
[    0.115108] pci 0000:00:0f.0: reg 18: [io  0xc800-0xc807]
[    0.115121] pci 0000:00:0f.0: reg 1c: [io  0xc480-0xc483]
[    0.115134] pci 0000:00:0f.0: reg 20: [io  0xc400-0xc40f]
[    0.115194] pci 0000:00:10.0: [1106:3038] type 0 class 0x000c03
[    0.115238] pci 0000:00:10.0: reg 20: [io  0xb880-0xb89f]
[    0.115278] pci 0000:00:10.0: supports D1 D2
[    0.115284] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.115292] pci 0000:00:10.0: PME# disabled
[    0.115315] pci 0000:00:10.1: [1106:3038] type 0 class 0x000c03
[    0.115359] pci 0000:00:10.1: reg 20: [io  0xbc00-0xbc1f]
[    0.115399] pci 0000:00:10.1: supports D1 D2
[    0.115405] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.115412] pci 0000:00:10.1: PME# disabled
[    0.115434] pci 0000:00:10.2: [1106:3038] type 0 class 0x000c03
[    0.115478] pci 0000:00:10.2: reg 20: [io  0xc000-0xc01f]
[    0.115518] pci 0000:00:10.2: supports D1 D2
[    0.115523] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.115531] pci 0000:00:10.2: PME# disabled
[    0.115552] pci 0000:00:10.3: [1106:3038] type 0 class 0x000c03
[    0.115597] pci 0000:00:10.3: reg 20: [io  0xc080-0xc09f]
[    0.115636] pci 0000:00:10.3: supports D1 D2
[    0.115642] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.115650] pci 0000:00:10.3: PME# disabled
[    0.115673] pci 0000:00:10.4: [1106:3104] type 0 class 0x000c03
[    0.115694] pci 0000:00:10.4: reg 10: [mem 0xfeaefc00-0xfeaefcff]
[    0.115766] pci 0000:00:10.4: supports D1 D2
[    0.115772] pci 0000:00:10.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.115780] pci 0000:00:10.4: PME# disabled
[    0.115807] pci 0000:00:11.0: [1106:8410] type 0 class 0x000601
[    0.115908] pci 0000:00:11.7: [1106:a353] type 0 class 0x000600
[    0.115961] pci 0000:00:13.0: [1106:b353] type 1 class 0x000604
[    0.116092] pci 0000:00:03.0: PCI bridge to [bus 02-02]
[    0.116114] pci 0000:00:03.0:   bridge window [mem 0xfbf00000-0xfbffffff 64bit pref]
[    0.116183] pci 0000:01:00.0: [10ec:8136] type 0 class 0x000200
[    0.116204] pci 0000:01:00.0: reg 10: [io  0xd800-0xd8ff]
[    0.116233] pci 0000:01:00.0: reg 18: [mem 0xfbeff000-0xfbefffff 64bit pref]
[    0.116255] pci 0000:01:00.0: reg 20: [mem 0xfbef8000-0xfbefbfff 64bit pref]
[    0.116326] pci 0000:01:00.0: supports D1 D2
[    0.116331] pci 0000:01:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.116340] pci 0000:01:00.0: PME# disabled
[    0.124032] pci 0000:00:03.2: PCI bridge to [bus 01-01]
[    0.124047] pci 0000:00:03.2:   bridge window [io  0xd000-0xdfff]
[    0.124060] pci 0000:00:03.2:   bridge window [mem 0xfbe00000-0xfbefffff 64bit pref]
[    0.124104] pci 0000:03:03.0: [1106:3249] type 0 class 0x000104
[    0.124124] pci 0000:03:03.0: reg 10: [io  0xec00-0xec0f]
[    0.124137] pci 0000:03:03.0: reg 14: [io  0xe880-0xe88f]
[    0.124150] pci 0000:03:03.0: reg 18: [io  0xe800-0xe80f]
[    0.124164] pci 0000:03:03.0: reg 1c: [io  0xe480-0xe48f]
[    0.124177] pci 0000:03:03.0: reg 20: [io  0xe400-0xe41f]
[    0.124190] pci 0000:03:03.0: reg 24: [io  0xe000-0xe0ff]
[    0.124203] pci 0000:03:03.0: reg 30: [mem 0xfebf0000-0xfebfffff pref]
[    0.124267] pci 0000:00:13.0: PCI bridge to [bus 03-03] (subtractive decode)
[    0.124283] pci 0000:00:13.0:   bridge window [io  0xe000-0xefff]
[    0.124291] pci 0000:00:13.0:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.124302] pci 0000:00:13.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.124309] pci 0000:00:13.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.124316] pci 0000:00:13.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.124324] pci 0000:00:13.0:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.124332] pci 0000:00:13.0:   bridge window [mem 0x7f000000-0xdfffffff] (subtractive decode)
[    0.124339] pci 0000:00:13.0:   bridge window [mem 0xf0000000-0xfebfffff] (subtractive decode)
[    0.124360] pci_bus 0000:00: on NUMA node 0
[    0.124369] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.124657] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NBP2._PRT]
[    0.124795] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.125107]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.125746]  pci0000:00: ACPI _OSC control (0x1c) granted
[    0.144513] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.144622] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.144725] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.144818] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.144911] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.145009] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.145108] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.145207] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.145508] vgaarb: device added: PCI:0000:00:01.0,decodes=io+mem,owns=io+mem,locks=none
[    0.145542] vgaarb: loaded
[    0.145550] vgaarb: bridge control possible 0000:00:01.0
[    0.145828] i2c-core: driver [aat2870] using legacy suspend method
[    0.145840] i2c-core: driver [aat2870] using legacy resume method
[    0.146015] SCSI subsystem initialized
[    0.146129] libata version 3.00 loaded.
[    0.146244] usbcore: registered new interface driver usbfs
[    0.146282] usbcore: registered new interface driver hub
[    0.146338] usbcore: registered new device driver usb
[    0.146550] PCI: Using ACPI for IRQ routing
[    0.146567] PCI: pci_cache_line_size set to 64 bytes
[    0.146698] reserve RAM buffer: 000000000009f800 - 000000000009ffff 
[    0.146705] reserve RAM buffer: 000000007efa0000 - 000000007fffffff 
[    0.146934] NetLabel: Initializing
[    0.146944] NetLabel:  domain hash size = 128
[    0.146953] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.146981] NetLabel:  unlabeled traffic allowed by default
[    0.147119] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.147136] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.147153] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
[    0.152118] Switching to clocksource hpet
[    0.167756] AppArmor: AppArmor Filesystem Enabled
[    0.167830] pnp: PnP ACPI init
[    0.167870] ACPI: bus type pnp registered
[    0.168345] pnp 00:00: [bus 00-ff]
[    0.168352] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.168358] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.168364] pnp 00:00: [io  0x0d00-0xffff window]
[    0.168371] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.168377] pnp 00:00: [mem 0x000d0000-0x000dffff window]
[    0.168384] pnp 00:00: [mem 0x7f000000-0xdfffffff window]
[    0.168390] pnp 00:00: [mem 0xf0000000-0xfebfffff window]
[    0.168507] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.168558] pnp 00:01: [mem 0xe0000000-0xefffffff]
[    0.168675] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    0.168695] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.168860] pnp 00:02: [dma 4]
[    0.168865] pnp 00:02: [io  0x0000-0x000f]
[    0.168871] pnp 00:02: [io  0x0081-0x0083]
[    0.168876] pnp 00:02: [io  0x0087]
[    0.168881] pnp 00:02: [io  0x0089-0x008b]
[    0.168891] pnp 00:02: [io  0x008f]
[    0.168896] pnp 00:02: [io  0x00c0-0x00df]
[    0.168959] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.169720] pnp 00:03: [io  0x0070-0x0071]
[    0.169788] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.169807] pnp 00:04: [io  0x0061]
[    0.169868] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.169887] pnp 00:05: [io  0x00f0-0x00ff]
[    0.169907] pnp 00:05: [irq 13]
[    0.169977] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.170365] pnp 00:06: [io  0x0000-0xffffffffffffffff disabled]
[    0.170371] pnp 00:06: [io  0x0280-0x028f]
[    0.170377] pnp 00:06: [io  0x0290-0x029f]
[    0.170498] system 00:06: [io  0x0280-0x028f] has been reserved
[    0.170517] system 00:06: [io  0x0290-0x029f] has been reserved
[    0.170532] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.170768] pnp 00:07: [io  0x0010-0x001f]
[    0.170774] pnp 00:07: [io  0x0022-0x003f]
[    0.170779] pnp 00:07: [io  0x0044-0x005f]
[    0.170785] pnp 00:07: [io  0x0062-0x0063]
[    0.170790] pnp 00:07: [io  0x0065-0x006f]
[    0.170795] pnp 00:07: [io  0x0072-0x007f]
[    0.170801] pnp 00:07: [io  0x0080]
[    0.170806] pnp 00:07: [io  0x0084-0x0086]
[    0.170811] pnp 00:07: [io  0x0088]
[    0.170816] pnp 00:07: [io  0x008c-0x008e]
[    0.170822] pnp 00:07: [io  0x0090-0x009f]
[    0.170827] pnp 00:07: [io  0x00a2-0x00bf]
[    0.170832] pnp 00:07: [io  0x00e0-0x00ef]
[    0.170838] pnp 00:07: [io  0x04d0-0x04d1]
[    0.170843] pnp 00:07: [io  0x0800-0x087f]
[    0.170849] pnp 00:07: [io  0x0400-0x041f]
[    0.170855] pnp 00:07: [io  0x0000-0xffffffffffffffff disabled]
[    0.170862] pnp 00:07: [mem 0xfed01000-0xfed013ff]
[    0.170868] pnp 00:07: [mem 0xfed02000-0xfed02fff]
[    0.170874] pnp 00:07: [mem 0xfed03000-0xfed03fff]
[    0.170880] pnp 00:07: [mem 0xfed05000-0xfed05fff]
[    0.170886] pnp 00:07: [mem 0xfff00000-0xffffffff]
[    0.170892] pnp 00:07: [mem 0xfecc0000-0xfecc0fff]
[    0.171034] system 00:07: [io  0x04d0-0x04d1] has been reserved
[    0.171049] system 00:07: [io  0x0800-0x087f] has been reserved
[    0.171063] system 00:07: [io  0x0400-0x041f] has been reserved
[    0.171078] system 00:07: [mem 0xfed01000-0xfed013ff] has been reserved
[    0.171093] system 00:07: [mem 0xfed02000-0xfed02fff] has been reserved
[    0.171107] system 00:07: [mem 0xfed03000-0xfed03fff] has been reserved
[    0.171122] system 00:07: [mem 0xfed05000-0xfed05fff] has been reserved
[    0.171137] system 00:07: [mem 0xfff00000-0xffffffff] has been reserved
[    0.171151] system 00:07: [mem 0xfecc0000-0xfecc0fff] could not be reserved
[    0.171166] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.171285] pnp 00:08: [mem 0xfed00000-0xfed003ff]
[    0.171291] pnp 00:08: [irq 0 disabled]
[    0.171304] pnp 00:08: [irq 8]
[    0.171372] pnp 00:08: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.171429] pnp 00:09: [io  0x0060]
[    0.171434] pnp 00:09: [io  0x0064]
[    0.171443] pnp 00:09: [irq 1]
[    0.171522] pnp 00:09: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.171605] pnp 00:0a: [irq 12]
[    0.171685] pnp 00:0a: Plug and Play ACPI device, IDs PNP0f03 PNP0f13 (active)
[    0.171849] pnp 00:0b: [mem 0xfec00000-0xfec00fff]
[    0.171855] pnp 00:0b: [mem 0xfee00000-0xfee00fff]
[    0.171964] system 00:0b: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.171982] system 00:0b: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.171997] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.172324] pnp 00:0c: [mem 0xe0000000-0xefffffff]
[    0.172441] system 00:0c: [mem 0xe0000000-0xefffffff] has been reserved
[    0.172458] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.172688] pnp 00:0d: [mem 0x00000000-0x0009ffff]
[    0.172695] pnp 00:0d: [mem 0x000c0000-0x000cffff]
[    0.172701] pnp 00:0d: [mem 0x000e0000-0x000fffff]
[    0.172707] pnp 00:0d: [mem 0x00100000-0x7effffff]
[    0.172713] pnp 00:0d: [mem 0xfec00000-0xffffffff]
[    0.172823] system 00:0d: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.172840] system 00:0d: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.172854] system 00:0d: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.172869] system 00:0d: [mem 0x00100000-0x7effffff] could not be reserved
[    0.172884] system 00:0d: [mem 0xfec00000-0xffffffff] could not be reserved
[    0.172899] system 00:0d: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.173147] pnp: PnP ACPI: found 14 devices
[    0.173158] ACPI: ACPI bus type pnp unregistered
[    0.173170] PnPBIOS: Disabled by ACPI PNP
[    0.211528] PCI: max bus depth: 1 pci_try_num: 2
[    0.211586] pci 0000:00:03.2: BAR 14: assigned [mem 0x7f000000-0x7f3fffff]
[    0.211609] pci 0000:00:03.0: PCI bridge to [bus 02-02]
[    0.211627] pci 0000:00:03.0:   bridge window [mem 0xfbf00000-0xfbffffff 64bit pref]
[    0.211648] pci 0000:00:03.2: PCI bridge to [bus 01-01]
[    0.211661] pci 0000:00:03.2:   bridge window [io  0xd000-0xdfff]
[    0.211677] pci 0000:00:03.2:   bridge window [mem 0x7f000000-0x7f3fffff]
[    0.211693] pci 0000:00:03.2:   bridge window [mem 0xfbe00000-0xfbefffff 64bit pref]
[    0.211713] pci 0000:00:13.0: PCI bridge to [bus 03-03]
[    0.211726] pci 0000:00:13.0:   bridge window [io  0xe000-0xefff]
[    0.211741] pci 0000:00:13.0:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.211791] pci 0000:00:03.0: PCI INT A -> GSI 27 (level, low) -> IRQ 27
[    0.211808] pci 0000:00:03.0: setting latency timer to 64
[    0.211828] pci 0000:00:03.2: PCI INT C -> GSI 35 (level, low) -> IRQ 35
[    0.211843] pci 0000:00:03.2: setting latency timer to 64
[    0.211854] pci 0000:00:13.0: setting latency timer to 64
[    0.211862] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.211868] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.211875] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.211882] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.211889] pci_bus 0000:00: resource 8 [mem 0x7f000000-0xdfffffff]
[    0.211896] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfebfffff]
[    0.211904] pci_bus 0000:02: resource 2 [mem 0xfbf00000-0xfbffffff 64bit pref]
[    0.211911] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    0.211917] pci_bus 0000:01: resource 1 [mem 0x7f000000-0x7f3fffff]
[    0.211925] pci_bus 0000:01: resource 2 [mem 0xfbe00000-0xfbefffff 64bit pref]
[    0.211932] pci_bus 0000:03: resource 0 [io  0xe000-0xefff]
[    0.211939] pci_bus 0000:03: resource 1 [mem 0xfeb00000-0xfebfffff]
[    0.211945] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    0.211952] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
[    0.211958] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    0.211965] pci_bus 0000:03: resource 7 [mem 0x000d0000-0x000dffff]
[    0.211972] pci_bus 0000:03: resource 8 [mem 0x7f000000-0xdfffffff]
[    0.211979] pci_bus 0000:03: resource 9 [mem 0xf0000000-0xfebfffff]
[    0.212089] NET: Registered protocol family 2
[    0.212233] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.212804] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.214168] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.214858] TCP: Hash tables configured (established 131072 bind 65536)
[    0.214878] TCP reno registered
[    0.214892] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.214922] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.215113] NET: Registered protocol family 1
[    0.215176] pci 0000:00:01.0: Boot video device
[    0.215183] pci 0000:00:03.0: disabling DAC on VIA PCI bridge
[    0.215242] pci 0000:00:10.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.215270] pci 0000:00:10.0: PCI INT A disabled
[    0.215298] pci 0000:00:10.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    0.215323] pci 0000:00:10.1: PCI INT B disabled
[    0.215352] pci 0000:00:10.2: PCI INT C -> GSI 21 (level, low) -> IRQ 21
[    0.215377] pci 0000:00:10.2: PCI INT C disabled
[    0.215405] pci 0000:00:10.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.215429] pci 0000:00:10.3: PCI INT D disabled
[    0.215449] pci 0000:00:10.4: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.215495] pci 0000:00:10.4: PCI INT D disabled
[    0.215524] PCI: CLS 32 bytes, default 64
[    0.216041] audit: initializing netlink socket (disabled)
[    0.216076] type=2000 audit(1358376202.212:1): initialized
[    0.270431] Trying to unpack rootfs image as initramfs...
[    0.364380] highmem bounce pool size: 64 pages
[    0.364407] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.444639] VFS: Disk quotas dquot_6.5.2
[    0.444825] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.452708] fuse init (API version 7.17)
[    0.452977] msgmni has been set to 1686
[    0.461274] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.461350] io scheduler noop registered
[    0.461360] io scheduler deadline registered
[    0.461381] io scheduler cfq registered (default)
[    0.461649] pcieport 0000:00:03.0: setting latency timer to 64
[    0.461719] pcieport 0000:00:03.0: irq 64 for MSI/MSI-X
[    0.461892] pcieport 0000:00:03.2: setting latency timer to 64
[    0.461949] pcieport 0000:00:03.2: irq 65 for MSI/MSI-X
[    0.462160] aer 0000:00:03.0:pcie02: service driver aer loaded
[    0.462206] aer 0000:00:03.2:pcie02: service driver aer loaded
[    0.462239] pcieport 0000:00:03.0: Signaling PME through PCIe PME interrupt
[    0.462257] pcie_pme 0000:00:03.0:pcie01: service driver pcie_pme loaded
[    0.462273] pcieport 0000:00:03.2: Signaling PME through PCIe PME interrupt
[    0.462286] pci 0000:01:00.0: Signaling PME through PCIe PME interrupt
[    0.462301] pcie_pme 0000:00:03.2:pcie01: service driver pcie_pme loaded
[    0.462344] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.462411] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.462737] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.462761] ACPI: Power Button [PWRB]
[    0.462880] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.462898] ACPI: Power Button [PWRF]
[    0.465718] ERST: Table is not found!
[    0.465735] GHES: HEST is not enabled!
[    0.468479] isapnp: Scanning for PnP cards...
[    0.474214] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.525647] Linux agpgart interface v0.103
[    0.529232] brd: module loaded
[    0.533977] loop: module loaded
[    0.534525] pata_acpi 0000:00:0f.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    0.534615] pata_acpi 0000:00:0f.0: PCI INT A disabled
[    0.535435] Fixed MDIO Bus: probed
[    0.535497] tun: Universal TUN/TAP device driver, 1.6
[    0.535507] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.540132] PPP generic driver version 2.4.2
[    0.540386] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.540450] ehci_hcd 0000:00:10.4: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.540494] ehci_hcd 0000:00:10.4: EHCI Host Controller
[    0.540586] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 1
[    0.540640] ehci_hcd 0000:00:10.4: debug port 1
[    0.540687] ehci_hcd 0000:00:10.4: irq 23, io mem 0xfeaefc00
[    0.552054] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00
[    0.552397] hub 1-0:1.0: USB hub found
[    0.552413] hub 1-0:1.0: 8 ports detected
[    0.552586] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.552644] uhci_hcd: USB Universal Host Controller Interface driver
[    0.552717] uhci_hcd 0000:00:10.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.552743] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    0.552862] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
[    0.552928] uhci_hcd 0000:00:10.0: irq 20, io base 0x0000b880
[    0.553215] hub 2-0:1.0: USB hub found
[    0.553230] hub 2-0:1.0: 2 ports detected
[    0.553372] uhci_hcd 0000:00:10.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    0.553394] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    0.553490] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
[    0.553547] uhci_hcd 0000:00:10.1: irq 22, io base 0x0000bc00
[    0.553822] hub 3-0:1.0: USB hub found
[    0.553837] hub 3-0:1.0: 2 ports detected
[    0.553977] uhci_hcd 0000:00:10.2: PCI INT C -> GSI 21 (level, low) -> IRQ 21
[    0.553999] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    0.554091] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
[    0.554152] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000c000
[    0.554430] hub 4-0:1.0: USB hub found
[    0.554445] hub 4-0:1.0: 2 ports detected
[    0.554582] uhci_hcd 0000:00:10.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.554604] uhci_hcd 0000:00:10.3: UHCI Host Controller
[    0.554695] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 5
[    0.554735] uhci_hcd 0000:00:10.3: irq 23, io base 0x0000c080
[    0.555011] hub 5-0:1.0: USB hub found
[    0.555026] hub 5-0:1.0: 2 ports detected
[    0.555332] usbcore: registered new interface driver libusual
[    0.555456] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    0.560858] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.560896] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.561219] mousedev: PS/2 mouse device common for all mice
[    0.561488] rtc_cmos 00:03: RTC can wake from S4
[    0.561704] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.561761] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    0.561920] device-mapper: uevent: version 1.0.3
[    0.562079] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    0.562192] EISA: Probing bus 0 at eisa.0
[    0.562203] EISA: Cannot allocate resource for mainboard
[    0.562215] Cannot allocate resource for EISA slot 1
[    0.562226] Cannot allocate resource for EISA slot 2
[    0.562236] Cannot allocate resource for EISA slot 3
[    0.562247] Cannot allocate resource for EISA slot 4
[    0.562258] Cannot allocate resource for EISA slot 5
[    0.562269] Cannot allocate resource for EISA slot 6
[    0.562279] Cannot allocate resource for EISA slot 7
[    0.562290] Cannot allocate resource for EISA slot 8
[    0.562300] EISA: Detected 0 cards.
[    0.562323] cpufreq-nforce2: No nForce2 chipset.
[    0.562335] cpuidle: using governor ladder
[    0.562345] cpuidle: using governor menu
[    0.562354] EFI Variables Facility v0.08 2004-May-17
[    0.562921] TCP cubic registered
[    0.563205] NET: Registered protocol family 10
[    0.564415] NET: Registered protocol family 17
[    0.564433] Registering the dns_resolver key type
[    0.564488] Using IPI No-Shortcut mode
[    0.564723] PM: Hibernation image not present or could not be loaded.
[    0.564746] registered taskstats version 1
[    0.727817] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    0.955726] usb 1-8: new high-speed USB device number 2 using ehci_hcd
[    1.112026] isapnp: No Plug & Play device found
[    1.212198] Refined TSC clocksource calibration: 1795.499 MHz.
[    1.212227] Switching to clocksource tsc
[    1.372359] hub 1-0:1.0: over-current condition on port 1
[    1.499685] Freeing initrd memory: 13848k freed
[    1.520645] Initializing USB Mass Storage driver...
[    1.523243] scsi0 : usb-storage 1-8:1.0
[    1.523464] usbcore: registered new interface driver usb-storage
[    1.523477] USB Mass Storage support registered.
[    1.534344]   Magic number: 13:190:755
[    1.534424] tty ttyS6: hash matches
[    1.534578] rtc_cmos 00:03: setting system clock to 2013-01-16 22:43:24 UTC (1358376204)
[    1.534837] longhaul: APIC detected. Longhaul is currently broken in this configuration.
[    1.534856] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.534867] EDD information not available.
[    1.535274] Freeing unused kernel memory: 740k freed
[    1.536308] Write protecting the kernel text: 5816k
[    1.536366] Write protecting the kernel read-only data: 2376k
[    1.536378] NX-protecting the kernel data: 4424k
[    1.580149] hub 1-0:1.0: over-current condition on port 2
[    1.595476] udevd[85]: starting version 175
[    1.788085] hub 1-0:1.0: over-current condition on port 3
[    1.955719] r8101 Fast Ethernet driver 1.022.00-NAPI loaded
[    1.955816] r8101 0000:01:00.0: PCI INT A -> GSI 32 (level, low) -> IRQ 32
[    1.955849] r8101 0000:01:00.0: PCI: Disallowing DAC for device
[    1.955865] r8101 0000:01:00.0: setting latency timer to 64
[    1.964948] pata_via 0000:00:0f.0: version 0.3.4
[    1.964976] pata_via 0000:00:0f.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    1.981290] scsi1 : pata_via
[    1.990923] scsi2 : pata_via
[    1.996095] hub 1-0:1.0: over-current condition on port 4
[    1.997354] r8101: This product is covered by one or more of the following patents: US5,307,459, US5,434,872, US5,732,094, US6,570,884, US6,115,776, and US6,327,625.
[    1.997389] eth0: Identified chip type is 'RTL8105E'.
[    1.997398] eth0: RTL8101E at 0xf840c000, bc:5f:f4:21:bc:28, IRQ 32
[    2.002360] ata1: PATA max UDMA/133 cmd 0xcc00 ctl 0xc880 bmdma 0xc400 irq 21
[    2.002385] ata2: DUMMY
[    2.017710] sata_via 0000:03:03.0: version 2.6
[    2.017761] sata_via 0000:03:03.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.017851] sata_via 0000:03:03.0: routed to hard irq line 7
[    2.030281] scsi3 : sata_via
[    2.034122] scsi4 : sata_via
[    2.037453] scsi5 : sata_via
[    2.037624] ata3: SATA max UDMA/133 port i16@0xec00 bmdma 0xe400 irq 16
[    2.037639] ata4: SATA max UDMA/133 port i16@0xe880 bmdma 0xe408 irq 16
[    2.037653] ata5: PATA max UDMA/133 port i16@0xe800 bmdma 0xe410 irq 16
[    2.184028] r8101  Copyright (C) 2012  Realtek NIC software team <nicfae@realtek.com> 
[    2.184033]  This program comes with ABSOLUTELY NO WARRANTY; for details, please see <http://www.gnu.org/licenses/>. 
[    2.184038]  This is free software, and you are welcome to redistribute it under certain conditions; see <http://www.gnu.org/licenses/>. 
[    2.216246] ata1: FORCE: cable set to 40c
[    2.216382] ata1.00: ATA-7: WDC WD1600JS-22NCB1, 10.02E02, max UDMA/133
[    2.216397] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.216420] ata1.01: ATA-7: WDC WD800JD-60LUA0, 07.01D07, max UDMA/100
[    2.216433] ata1.01: 156301488 sectors, multi 16: LBA48 
[    2.216450] ata1.00: limited to UDMA/33 due to 40-wire cable
[    2.216463] ata1.01: limited to UDMA/33 due to 40-wire cable
[    2.224329] ata1.00: configured for UDMA/33
[    2.232170] ata1.01: configured for UDMA/33
[    2.232438] scsi 1:0:0:0: Direct-Access     ATA      WDC WD1600JS-22N 10.0 PQ: 0 ANSI: 5
[    2.232883] sd 1:0:0:0: Attached scsi generic sg0 type 0
[    2.233204] scsi 1:0:1:0: Direct-Access     ATA      WDC WD800JD-60LU 07.0 PQ: 0 ANSI: 5
[    2.233544] sd 1:0:1:0: Attached scsi generic sg1 type 0
[    2.233775] sd 1:0:1:0: [sdb] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    2.233871] sd 1:0:1:0: [sdb] Write Protect is off
[    2.233885] sd 1:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    2.233922] sd 1:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.237046]  sdb: sdb1
[    2.237210] sd 1:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    2.237305] sd 1:0:0:0: [sda] Write Protect is off
[    2.237319] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.237355] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.247792] sd 1:0:1:0: [sdb] Attached SCSI disk
[    2.272316]  sda: sda1 sda2 < sda5 >
[    2.272988] sd 1:0:0:0: [sda] Attached SCSI disk
[    2.370470] ata3: SATA link down (SStatus 0 SControl 310)
[    2.370495] ata3: FORCE: cable set to 40c
[    2.521281] scsi 0:0:0:0: Direct-Access     Verbatim STORE N GO       5.00 PQ: 0 ANSI: 0 CCS
[    2.526937] sd 0:0:0:0: Attached scsi generic sg2 type 0
[    2.527660] sd 0:0:0:0: [sdc] 3911680 512-byte logical blocks: (2.00 GB/1.86 GiB)
[    2.528287] sd 0:0:0:0: [sdc] Write Protect is off
[    2.528312] sd 0:0:0:0: [sdc] Mode Sense: 23 00 00 00
[    2.528912] sd 0:0:0:0: [sdc] No Caching mode page present
[    2.528937] sd 0:0:0:0: [sdc] Assuming drive cache: write through
[    2.532157] sd 0:0:0:0: [sdc] No Caching mode page present
[    2.532182] sd 0:0:0:0: [sdc] Assuming drive cache: write through
[    2.533375]  sdc: sdc1
[    2.536153] sd 0:0:0:0: [sdc] No Caching mode page present
[    2.536177] sd 0:0:0:0: [sdc] Assuming drive cache: write through
[    2.536191] sd 0:0:0:0: [sdc] Attached SCSI removable disk
[    2.698488] ata4: SATA link down (SStatus 0 SControl 310)
[    2.698521] ata4: FORCE: cable set to 40c
[    2.884322] ata5: FORCE: cable set to 40c
[    2.884517] ata5.00: ATA-7: ExcelStor Technology J8160, P22OA85A, max UDMA/133
[    2.884535] ata5.00: 321672960 sectors, multi 0: LBA48 
[    2.884727] ata5.01: ATA-7: Maxtor 6Y080L0, YAR41BW0, max UDMA/133
[    2.884741] ata5.01: 160086528 sectors, multi 0: LBA 
[    2.884756] ata5.00: limited to UDMA/33 due to 40-wire cable
[    2.884769] ata5.01: limited to UDMA/33 due to 40-wire cable
[    2.900372] ata5.00: configured for UDMA/33
[    2.916373] ata5.01: configured for UDMA/33
[    2.916619] scsi 5:0:0:0: Direct-Access     ATA      ExcelStor Techno P22O PQ: 0 ANSI: 5
[    2.917306] sd 5:0:0:0: [sdd] 321672960 512-byte logical blocks: (164 GB/153 GiB)
[    2.917405] sd 5:0:0:0: [sdd] Write Protect is off
[    2.917419] sd 5:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[    2.917455] sd 5:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.918535] sd 5:0:0:0: Attached scsi generic sg3 type 0
[    2.937835]  sdd: sdd1
[    2.938273] scsi 5:0:1:0: Direct-Access     ATA      Maxtor 6Y080L0   YAR4 PQ: 0 ANSI: 5
[    2.938567] sd 5:0:1:0: [sde] 160086528 512-byte logical blocks: (81.9 GB/76.3 GiB)
[    2.938659] sd 5:0:1:0: [sde] Write Protect is off
[    2.938672] sd 5:0:1:0: [sde] Mode Sense: 00 3a 00 00
[    2.938708] sd 5:0:1:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.940263] sd 5:0:1:0: Attached scsi generic sg4 type 0
[    2.963317]  sde: sde1
[    2.963819] sd 5:0:1:0: [sde] Attached SCSI disk
[    2.963962] sd 5:0:0:0: [sdd] Attached SCSI disk
[    3.435940] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   12.468313] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   12.536799] udevd[327]: starting version 175
[   12.614101] Adding 2077692k swap on /dev/sda5.  Priority:-1 extents:1 across:2077692k 
[   12.658734] lp: driver loaded but no devices found
[   12.756142] hwmon_vid: Using 7-bit VID table for VIA C7-D CPU
[   12.824201] w83627ehf: Found W83627DHG-P chip at 0x290
[   12.824566] hwmon_vid: Using 7-bit VID table for VIA C7-D CPU
[   12.880168] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   13.153631] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[   13.169126] acpi device:09: registered as cooling_device1
[   13.170503] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:00/input/input3
[   13.176078] ACPI: Video Device [VUMA] (multi-head: yes  rom: no  post: no)
[   13.916851] type=1400 audit(1358376216.878:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=474 comm="apparmor_parser"
[   13.922044] type=1400 audit(1358376216.882:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=474 comm="apparmor_parser"
[   13.922697] type=1400 audit(1358376216.882:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=474 comm="apparmor_parser"
[   14.053992] r8101: eth0: link down
[   14.115571] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   15.445255] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input4
[   15.644480] r8101: eth0: link up
[   15.645333] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   16.175708] init: failsafe main process (802) killed by TERM signal
[   16.445187] type=1400 audit(1358376219.406:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=898 comm="apparmor_parser"
[   16.451738] type=1400 audit(1358376219.410:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=898 comm="apparmor_parser"
[   16.455327] type=1400 audit(1358376219.414:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=898 comm="apparmor_parser"
[   16.471738] type=1400 audit(1358376219.430:8): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld" pid=902 comm="apparmor_parser"
[   16.502639] type=1400 audit(1358376219.462:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=907 comm="apparmor_parser"
[   17.247555] type=1400 audit(1358376220.206:10): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=1053 comm="apparmor_parser"
[   17.394843] vesafb: mode is 640x480x32, linelength=2560, pages=0
[   17.394851] vesafb: scrolling: redraw
[   17.394858] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[   17.395737] vesafb: framebuffer at 0xfa000000, mapped to 0xf8580000, using 1216k, total 1216k
[   17.397286] Console: switching to colour frame buffer device 80x30
[   17.402104] fb0: VESA VGA frame buffer device

```

---

### Post by ARMac on 2013-01-17
*bump*

Surely any of you experts knows something about this ;)

More info, so I ran another test. The problem with libdata.force=40c (half) solution is that is slows the drives to crawl. I am getting 10-15 mb/s disk to disk transfer, and without it I get 30-50 mb/s.  So I removed "libdata.force=40c" and the errors immediately came back.

Note that the error comes up for all the drives, not just ata1.0 I've seen it come up for all of them, including the one attached to the PCI sata controller. Is this bug in the kernel or bug with the sata controller driver perhaps?

Here is more kern.log messages

*EDIT* - Forgot to mention, this exact same system was running on 8.04 hardy perfectly fine. Which leans me suspecting that tke 3.x.x kernel is doing all of this.

```
Jan 17 21:23:11 mkdlab1 kernel: [   81.268041] Marking TSC unstable due to cpufreq changes
Jan 17 21:23:11 mkdlab1 kernel: [   81.268154] Switching to clocksource hpet
Jan 17 21:23:38 mkdlab1 kernel: [  108.076452] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Jan 17 21:23:38 mkdlab1 kernel: [  108.076643] ata5.00: BMDMA stat 0x4
Jan 17 21:23:38 mkdlab1 kernel: [  108.076736] ata5.00: failed command: WRITE DMA EXT
Jan 17 21:23:38 mkdlab1 kernel: [  108.076867] ata5.00: cmd 35/00:00:08:b1:03/00:04:00:00:00/e0 tag 0 dma 524288 out
Jan 17 21:23:38 mkdlab1 kernel: [  108.076871]          res 51/84:00:07:b5:03/84:00:00:00:00/e0 Emask 0x10 (ATA bus error)
Jan 17 21:23:38 mkdlab1 kernel: [  108.077247] ata5.00: status: { DRDY ERR }
Jan 17 21:23:38 mkdlab1 kernel: [  108.077349] ata5.00: error: { ICRC ABRT }
Jan 17 21:23:38 mkdlab1 kernel: [  108.077467] ata5: soft resetting link
Jan 17 21:23:38 mkdlab1 kernel: [  108.256484] ata5.00: configured for UDMA/133
Jan 17 21:23:38 mkdlab1 kernel: [  108.272461] ata5.01: configured for UDMA/133
Jan 17 21:23:38 mkdlab1 kernel: [  108.272491] ata5: EH complete
Jan 17 21:23:38 mkdlab1 kernel: [  108.292075] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Jan 17 21:23:38 mkdlab1 kernel: [  108.292251] ata5.00: BMDMA stat 0x4
Jan 17 21:23:38 mkdlab1 kernel: [  108.292344] ata5.00: failed command: WRITE DMA EXT
Jan 17 21:23:38 mkdlab1 kernel: [  108.292475] ata5.00: cmd 35/00:00:78:68:01/00:04:00:00:00/e0 tag 0 dma 524288 out
Jan 17 21:23:38 mkdlab1 kernel: [  108.292478]          res 51/84:00:77:6c:01/84:00:00:00:00/e0 Emask 0x10 (ATA bus error)
Jan 17 21:23:38 mkdlab1 kernel: [  108.292855] ata5.00: status: { DRDY ERR }
Jan 17 21:23:38 mkdlab1 kernel: [  108.292957] ata5.00: error: { ICRC ABRT }
Jan 17 21:23:38 mkdlab1 kernel: [  108.293074] ata5: soft resetting link
Jan 17 21:23:38 mkdlab1 kernel: [  108.536487] ata5.00: configured for UDMA/133
Jan 17 21:23:38 mkdlab1 kernel: [  108.552440] ata5.01: configured for UDMA/133
Jan 17 21:23:38 mkdlab1 kernel: [  108.552469] ata5: EH complete
Jan 17 21:23:38 mkdlab1 kernel: [  108.577176] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Jan 17 21:23:38 mkdlab1 kernel: [  108.577380] ata5.00: BMDMA stat 0x4
Jan 17 21:23:38 mkdlab1 kernel: [  108.577474] ata5.00: failed command: WRITE DMA EXT
Jan 17 21:23:38 mkdlab1 kernel: [  108.577605] ata5.00: cmd 35/00:00:78:78:01/00:04:00:00:00/e0 tag 0 dma 524288 out
Jan 17 21:23:38 mkdlab1 kernel: [  108.577608]          res 51/84:00:77:7c:01/84:00:00:00:00/e0 Emask 0x10 (ATA bus error)
Jan 17 21:23:38 mkdlab1 kernel: [  108.577984] ata5.00: status: { DRDY ERR }
Jan 17 21:23:38 mkdlab1 kernel: [  108.581351] ata5.00: error: { ICRC ABRT }
Jan 17 21:23:38 mkdlab1 kernel: [  108.584587] ata5: soft resetting link
Jan 17 21:23:38 mkdlab1 kernel: [  108.772501] ata5.00: configured for UDMA/133
Jan 17 21:23:38 mkdlab1 kernel: [  108.788483] ata5.01: configured for UDMA/133
Jan 17 21:23:38 mkdlab1 kernel: [  108.788525] ata5: EH complete
Jan 17 21:23:38 mkdlab1 kernel: [  108.794887] ata5.00: limiting speed to UDMA/100:PIO4
Jan 17 21:23:38 mkdlab1 kernel: [  108.794908] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Jan 17 21:23:38 mkdlab1 kernel: [  108.802273] ata5.00: BMDMA stat 0x4
Jan 17 21:23:38 mkdlab1 kernel: [  108.809385] ata5.00: failed command: WRITE DMA EXT
Jan 17 21:23:38 mkdlab1 kernel: [  108.816297] ata5.00: cmd 35/00:00:78:78:01/00:04:00:00:00/e0 tag 0 dma 524288 out
Jan 17 21:23:38 mkdlab1 kernel: [  108.816305]          res 51/84:00:77:7c:01/84:00:00:00:00/e0 Emask 0x10 (ATA bus error)
Jan 17 21:23:38 mkdlab1 kernel: [  108.844623] ata5.00: status: { DRDY ERR }
Jan 17 21:23:38 mkdlab1 kernel: [  108.851755] ata5.00: error: { ICRC ABRT }
Jan 17 21:23:38 mkdlab1 kernel: [  108.858633] ata5: soft resetting link
Jan 17 21:23:39 mkdlab1 kernel: [  109.044499] ata5.00: configured for UDMA/100
Jan 17 21:23:39 mkdlab1 kernel: [  109.060525] ata5.01: configured for UDMA/133
Jan 17 21:23:39 mkdlab1 kernel: [  109.060568] ata5: EH complete
Jan 17 21:25:42 mkdlab1 kernel: [  232.864083] ata1: lost interrupt (Status 0x50)
Jan 17 21:25:42 mkdlab1 kernel: [  232.864127] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Jan 17 21:25:42 mkdlab1 kernel: [  232.871242] ata1.00: failed command: READ DMA
Jan 17 21:25:42 mkdlab1 kernel: [  232.878337] ata1.00: cmd c8/00:20:e0:08:e4/00:00:00:00:00/e3 tag 0 dma 16384 in
Jan 17 21:25:42 mkdlab1 kernel: [  232.878345]          res 40/00:00:09:4f:c2/00:00:00:00:00/10 Emask 0x4 (timeout)
Jan 17 21:25:42 mkdlab1 kernel: [  232.907215] ata1.00: status: { DRDY }
Jan 17 21:25:42 mkdlab1 kernel: [  232.914476] ata1: soft resetting link
Jan 17 21:25:43 mkdlab1 kernel: [  233.092361] ata1.00: configured for UDMA/33
Jan 17 21:25:43 mkdlab1 kernel: [  233.100241] ata1.01: configured for UDMA/33
Jan 17 21:25:43 mkdlab1 kernel: [  233.100280] ata1: EH complete
Jan 17 21:29:13 mkdlab1 kernel: [  443.378674] kjournald starting.  Commit interval 5 seconds
Jan 17 21:29:13 mkdlab1 kernel: [  443.379516] EXT3-fs (sdd1): using internal journal
Jan 17 21:29:13 mkdlab1 kernel: [  443.379535] EXT3-fs (sdd1): mounted filesystem with ordered data mode

```

---

### Post by tgalati4 on 2013-01-17
SMART captures perhaps 60% of the failure modes.  The rest are not captured and turn up at unreasonable times.  You might have a SATA chip failing on the drive.  I've had Raptor's fail in such a manner.  Monitor the temperatures of the drive and see if the errors are more frequent as temperature goes up.

In the meantime, backup your data and expect the drive to fail at any time.

Go back through your log files and see how far back you can trace these errors.  If the drive is under warranty, then it's time to enforce it.

Clean the SATA card with an eraser and reseat it.

---

### Post by ARMac on 2013-01-18
Thanks for the reply, but as I said, the HDD was diagnosed with all the specialized tools for HDD diagnostics, including WD diag, that give out far more info then ubuntu can, and there is absolutely no hiccups. Besides, its highly unlikely that all of the 4 different hard drives are failing at the same time with the same error.

Nevertheless I unpacked brand new WD Caviar blue sata II disk last night and replaced the system disk with that one, brand new sata cable as well. 

Same error. In the meantime I found couple of similar reports on launchpad (especially about the failed command: FLUSH CACHE EXT) all with 12.04 and 3.x kernels. Apparently its a bug with certain SATA/ATA controllers, and its not looking good.

Since I have to have this system stable and running in about 2 weeks, I don't see an alternative but to rollback to distro which comfortably uses older 2.x.x kernel since apparently its not Ubuntu specific problem, saw it across other distros with 3.x kernels too.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1040981](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1040981)

Just as a reference, the controllers in question are:

Via VX900 (SoC) using the pata_via module
Via VT6421 add-on PCI controller using the sata_via module

---

### Post by Doug S on 2013-01-18
Somehow, I didn't see this thread until now, and I wonder if your issue is similar to one I have been having for almost a year now. 
 
The way to test if your issue is the same as mine is to change one line in /lib/udev/rules.d/60-persistent-storage.rules back to what it used to be and see if the problem persists. The following is cut and pasted from my web notes:
 
The difference between the problem occuring or not occuring has been isolated down to the udev package:
udev 175-0ubuntu6 rule-based device node and kernel event manager - does not have the problem.
udev 175-0ubuntu7 rule-based device node and kernel event manager - has the problem. (as do all later versions. Tested up to version udev 175-0ubuntu17)
Further, the issue has been isolated to the single line change of launchpad revision 2760 (while revision 2761 edits the same line again, the results are the same).
Specifically: in the file /lib/udev/rules.d/60-persistent-storage.rules, this line:```
ACTION=="add", KERNEL=="sr*", ATTR{events_poll_msecs}=="0", ATTR{events_poll_msecs}="2000"

```works fine, but when it is changed to this (2760):```
ACTION=="add", KERNEL=="sr*", ATTR{events_poll_msecs}=="-1", ATTR{events_poll_msecs}="2000"

```or this (2761 and subsequent):```
ACTION=="add", ATTR{removable}=="1", ATTR{events_poll_msecs}=="-1", ATTR{events_poll_msecs}="2000"

```the problem exists. (and yes, the rule is for removable devices, but effects non-removable devices.)
 
To test, save the original file first, for restoring later, make the single line change back to the original line and save the file. Execute this:```
sudo update-initramfs -u
```Then re-boot.
 
References:
[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/986654](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/986654)
[http://www.smythies.com/~doug/network/hd_race/index.html](http://www.smythies.com/~doug/network/hd_race/index.html) (my site is safe, but you have no reason to believe me.)
 
While all of my examples are for read issues, it did also occur for me during write. I see that the problem also occured for you during read.
 
Edit: My notes in this posting refer to your ATA1 issues. I suspect your ATA5 issues might be a different issue.

---

### Post by dcstar on 2013-01-19
> **ARMac said:**
> Hi all. I am getting the following error occasionally. There is no specific time or action that triggers this, it happens if the disk is idle or in use.
............
The disk drive WD Caviar 160gb SATA (WD1600JS-22NCB1) has been checked with all possible tools, sata cable and PSU has been replaced. 

The only thing I managed to do that somehow lowered the amount of those errors is that i added "libata.force=40c" in the grub, that forces the system to think 40 wires ata cable is in use (which makes no sense since the drive is sata), but I still get this occasionally. The system does not freeze or lock up when this happens. Hdd was scanned with HDAT2, HDD sentinel, WD Diagnostics etc. SMART is clean, no bad or reallocated sectors.

The system spec:
Asrock pv530a-itx
2-gb DDR3
Connected on onboard SATA controller:
**HDD1 WD160gb (the problematic one)**
HDD2 WD80gb
Hard drives connected on **addon IDE/SATA** controller (VIA VT6421)
HDD3 Excelstore PATA 160GB
HDD4 Maxtor PATA 80gb
.......

[LIST=1]
[*]Move drive connection to SATA port on other controller.
[*]If there are still issues, replace SATA cable.
[/LIST]

---

### Post by tgalati4 on 2013-01-19
"Via" and "stable" are not normally found in the same sentence.  Try a different controller.

---

