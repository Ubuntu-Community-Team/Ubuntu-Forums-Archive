---
title: "11 second delay during startup at one step"
date: 2014-06-22
forum: General Help
---

### Post by varun-10 on 2014-06-22
hello guys, I am facing a very slow startup, according to dmeg, the problem is most likely due to

```

[    4.021460] EXT4-fs (sdb3): mounted filesystem with ordered data mode. Opts: (null)
[   15.774680] EXT4-fs (sdb3): re-mounted. Opts: errors=remount-ro

```

the whole log is
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.13.0-29-generic (buildd@brownie) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #53-Ubuntu SMP Wed Jun 4 21:02:19 UTC 2014 (Ubuntu 3.13.0-29.53-generic 3.13.11.2)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009efff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009f000-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000007f66d7ff] usable
[    0.000000] BIOS-e820: [mem 0x000000007f66d800-0x000000007fffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec0ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed18000-0x00000000fed1bfff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed20000-0x00000000fed8ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000feda0000-0x00000000feda5fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee0ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffe00000-0x00000000ffffffff] reserved
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.4 present.
[    0.000000] DMI: Dell Inc. XPS M1330                       /0N6705, BIOS A12 07/08/2008
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0x7f66d max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 07F800000 mask FFF800000 uncachable
[    0.000000]   2 base 07F700000 mask FFFF00000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2040MB, range: 8MB, type UC
[    0.000000] reg 2, base: 2039MB, range: 1MB, type UC
[    0.000000] total RAM covered: 2039M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 16M     num_reg: 3      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2039MB, range: 1MB, type UC
[    0.000000] reg 2, base: 2040MB, range: 8MB, type UC
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] initial memory mapped: [mem 0x00000000-0x01ffffff]
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x37800000-0x379fffff]
[    0.000000]  [mem 0x37800000-0x379fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x34000000-0x377fffff]
[    0.000000]  [mem 0x34000000-0x377fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0x33ffffff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x33ffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x37a00000-0x37bfdfff]
[    0.000000]  [mem 0x37a00000-0x37bfdfff] page 4k
[    0.000000] BRK [0x01b8c000, 0x01b8cfff] PGTABLE
[    0.000000] RAMDISK: [mem 0x35c56000-0x36e22fff]
[    0.000000] ACPI: RSDP 000fbbf0 000024 (v02 DELL  )
[    0.000000] ACPI: XSDT 7f66f200 00005C (v01 DELL    M08     27D80708 ASL  00000061)
[    0.000000] ACPI: FACP 7f66f09c 0000F4 (v04 DELL    M08     27D80708 ASL  00000061)
[    0.000000] ACPI: DSDT 7f66f800 005733 (v02 INT430 SYSFexxx 00001001 INTL 20050624)
[    0.000000] ACPI: FACS 7f67e000 000040
[    0.000000] ACPI: HPET 7f66f300 000038 (v01 DELL    M08     00000001 ASL  00000061)
[    0.000000] ACPI: APIC 7f66f400 000068 (v01 DELL    M08     27D80708 ASL  00000047)
[    0.000000] ACPI: MCFG 7f66f3c0 00003E (v16 DELL    M08     27D80708 ASL  00000061)
[    0.000000] ACPI: SLIC 7f66f49c 000176 (v01 DELL    M08     27D80708 ASL  00000061)
[    0.000000] ACPI: BOOT 7f66efc0 000028 (v01 DELL    M08     27D80708 ASL  00000061)
[    0.000000] ACPI: SSDT 7f66d9bc 0004CC (v01  PmRef    CpuPm 00003000 INTL 20050624)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1146MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] BRK [0x01b8d000, 0x01b8dfff] PGTABLE
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   Normal   [mem 0x01000000-0x37bfdfff]
[    0.000000]   HighMem  [mem 0x37bfe000-0x7f66cfff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009efff]
[    0.000000]   node   0: [mem 0x00100000-0x7f66cfff]
[    0.000000] On node 0 totalpages: 521739
[    0.000000] free_area_init_node: node 0, pgdat c1995100, node_mem_map f4c66020
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3998 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 224254 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2293 pages used for memmap
[    0.000000]   HighMem zone: 293487 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] smpboot: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000fffff]
[    0.000000] e820: [mem 0x80000000-0xf7ffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @f7bd6000 s36096 r0 d21248 u57344
[    0.000000] pcpu-alloc: s36096 r0 d21248 u57344 alloc=14*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519955
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-29-generic root=UUID=95e35aad-c2df-429e-a9c5-e2bec97376a4 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 4174688 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:0007f66d)
[    0.000000] Memory: 2035464K/2086956K available (6522K kernel code, 639K rwdata, 2756K rodata, 872K init, 924K bss, 51492K reserved, 1173948K highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff14000 - 0xfffff000   ( 940 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc19b2000 - 0xc1a8c000   ( 872 kB)
[    0.000000]       .data : 0xc165ee72 - 0xc19b1d80   (3403 kB)
[    0.000000]       .text : 0xc1000000 - 0xc165ee72   (6523 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=8 to nr_cpu_ids=2.
[    0.000000] NR_IRQS:2304 nr_irqs:512 16
[    0.000000] CPU 0 irqstacks, hard=f7008000 soft=f700a000
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 1995.081 MHz processor
[    0.004002] Calibrating delay loop (skipped), value calculated using timer frequency.. 3990.16 BogoMIPS (lpj=7980324)
[    0.004006] pid_max: default: 32768 minimum: 301
[    0.004041] Security Framework initialized
[    0.004063] AppArmor: AppArmor initialized
[    0.004065] Yama: becoming mindful.
[    0.004121] Mount-cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.004125] Mountpoint-cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.004406] Initializing cgroup subsys memory
[    0.004415] Initializing cgroup subsys devices
[    0.004418] Initializing cgroup subsys freezer
[    0.004421] Initializing cgroup subsys blkio
[    0.004424] Initializing cgroup subsys perf_event
[    0.004427] Initializing cgroup subsys hugetlb
[    0.004458] CPU: Physical Processor ID: 0
[    0.004460] CPU: Processor Core ID: 0
[    0.004464] mce: CPU supports 6 MCE banks
[    0.004473] CPU0: Thermal monitoring enabled (TM2)
[    0.004486] Last level iTLB entries: 4KB 128, 2MB 4, 4MB 4
[    0.004486] Last level dTLB entries: 4KB 256, 2MB 0, 4MB 32
[    0.004486] tlb_flushall_shift: -1
[    0.004833] Freeing SMP alternatives memory: 32K (c1a8c000 - c1a94000)
[    0.008853] ACPI: Core revision 20131115
[    0.012444] ACPI: All ACPI Tables successfully acquired
[    0.014024] ftrace: allocating 27749 entries in 55 pages
[    0.024108] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.024579] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.065759] smpboot: CPU0: Intel(R) Core(TM)2 Duo CPU     T7250  @ 2.00GHz (fam: 06, model: 0f, stepping: 0d)
[    0.068000] Performance Events: PEBS fmt0+, 4-deep LBR, Core2 events, Intel PMU driver.
[    0.068000] perf_event_intel: PEBS disabled due to CPU errata
[    0.068000] ... version:                2
[    0.068000] ... bit width:              40
[    0.068000] ... generic registers:      2
[    0.068000] ... value mask:             000000ffffffffff
[    0.068000] ... max period:             000000007fffffff
[    0.068000] ... fixed-purpose events:   3
[    0.068000] ... event mask:             0000000700000003
[    0.069444] CPU 1 irqstacks, hard=f70ec000 soft=f70ee000
[    0.069447] x86: Booting SMP configuration:
[    0.008000] Initializing CPU#1
[    0.069449] .... node  #0, CPUs:      #1
[    0.082524] x86: Booted up 1 node, 2 CPUs
[    0.082529] smpboot: Total of 2 processors activated (7980.32 BogoMIPS)
[    0.082624] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.084059] devtmpfs: initialized
[    0.084273] EVM: security.selinux
[    0.084276] EVM: security.SMACK64
[    0.084278] EVM: security.ima
[    0.084280] EVM: security.capability
[    0.085727] pinctrl core: initialized pinctrl subsystem
[    0.085821] regulator-dummy: no parameters
[    0.085864] RTC time: 21:40:58, date: 06/22/14
[    0.085915] NET: Registered protocol family 16
[    0.086112] EISA bus registered
[    0.086115] cpuidle: using governor ladder
[    0.086116] cpuidle: using governor menu
[    0.086213] ACPI: bus type PCI registered
[    0.086216] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.086299] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.086303] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.086305] PCI: Using MMCONFIG for extended config space
[    0.086307] PCI: Using configuration type 1 for base access
[    0.086320] dmi type 0xB1 record - unknown flag
[    0.086320] bio: create slab <bio-0> at 0
[    0.088001] ACPI: Added _OSI(Module Device)
[    0.088001] ACPI: Added _OSI(Processor Device)
[    0.088001] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.088001] ACPI: Added _OSI(Processor Aggregator Device)
[    0.100806] ACPI: SSDT 7f67e080 000043 (v01  LMPWR  DELLLOM 00001001 INTL 20050624)
[    0.101132] ACPI: Dynamic OEM Table Load:
[    0.101136] ACPI: SSDT   (null) 000043 (v01  LMPWR  DELLLOM 00001001 INTL 20050624)
[    0.101450] ACPI: SSDT 7f66e4f2 000286 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.101793] ACPI: Dynamic OEM Table Load:
[    0.101797] ACPI: SSDT   (null) 000286 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.101934] ACPI: SSDT 7f66de88 0005E5 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.102258] ACPI: Dynamic OEM Table Load:
[    0.102261] ACPI: SSDT   (null) 0005E5 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.102525] ACPI: SSDT 7f66e778 0000C4 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.102860] ACPI: Dynamic OEM Table Load:
[    0.102863] ACPI: SSDT   (null) 0000C4 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.102951] ACPI: SSDT 7f66e46d 000085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.103276] ACPI: Dynamic OEM Table Load:
[    0.103279] ACPI: SSDT   (null) 000085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.103505] ACPI: Interpreter enabled
[    0.103518] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20131115/hwxface-580)
[    0.103523] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)
[    0.103540] ACPI: (supports S0 S3 S4 S5)
[    0.103542] ACPI: Using IOAPIC for interrupt routing
[    0.103573] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.103782] ACPI: No dock devices found.
[    0.156577] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.156584] acpi PNP0A03:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.156591] acpi PNP0A03:00: _OSC failed (AE_NOT_FOUND); disabling ASPM
[    0.179430] acpi PNP0A03:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-3f] only partially covers this bridge
[    0.179712] PCI host bridge to bus 0000:00
[    0.179717] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.179720] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.179723] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.179728] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.179731] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000dffff]
[    0.179734] pci_bus 0000:00: root bus resource [mem 0x80000000-0xf7ffffff]
[    0.179736] pci_bus 0000:00: root bus resource [mem 0xfc000000-0xfebfffff]
[    0.179739] pci_bus 0000:00: root bus resource [mem 0xfec10000-0xfecfffff]
[    0.179742] pci_bus 0000:00: root bus resource [mem 0xfed1c000-0xfed1ffff]
[    0.179744] pci_bus 0000:00: root bus resource [mem 0xfed90000-0xfed9ffff]
[    0.179747] pci_bus 0000:00: root bus resource [mem 0xfeda7000-0xfedfffff]
[    0.179750] pci_bus 0000:00: root bus resource [mem 0xfee10000-0xff9fffff]
[    0.179752] pci_bus 0000:00: root bus resource [mem 0xffc00000-0xffdfffff]
[    0.179764] pci 0000:00:00.0: [8086:2a00] type 00 class 0x060000
[    0.179904] pci 0000:00:02.0: [8086:2a02] type 00 class 0x030000
[    0.179922] pci 0000:00:02.0: reg 0x10: [mem 0xfea00000-0xfeafffff 64bit]
[    0.179933] pci 0000:00:02.0: reg 0x18: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.179940] pci 0000:00:02.0: reg 0x20: [io  0xefe8-0xefef]
[    0.180097] pci 0000:00:02.1: [8086:2a03] type 00 class 0x038000
[    0.180112] pci 0000:00:02.1: reg 0x10: [mem 0xfeb00000-0xfebfffff 64bit]
[    0.180298] pci 0000:00:1a.0: [8086:2834] type 00 class 0x0c0300
[    0.180361] pci 0000:00:1a.0: reg 0x20: [io  0x6f20-0x6f3f]
[    0.182368] pci 0000:00:1a.0: System wakeup disabled by ACPI
[    0.182413] pci 0000:00:1a.1: [8086:2835] type 00 class 0x0c0300
[    0.182475] pci 0000:00:1a.1: reg 0x20: [io  0x6f00-0x6f1f]
[    0.184312] pci 0000:00:1a.1: System wakeup disabled by ACPI
[    0.184376] pci 0000:00:1a.7: [8086:283a] type 00 class 0x0c0320
[    0.184404] pci 0000:00:1a.7: reg 0x10: [mem 0xfed1c400-0xfed1c7ff]
[    0.184522] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.186401] pci 0000:00:1a.7: System wakeup disabled by ACPI
[    0.186461] pci 0000:00:1b.0: [8086:284b] type 00 class 0x040300
[    0.186488] pci 0000:00:1b.0: reg 0x10: [mem 0xfe9fc000-0xfe9fffff 64bit]
[    0.186603] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.186688] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    0.186737] pci 0000:00:1c.0: [8086:283f] type 01 class 0x060400
[    0.186858] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.186944] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.186999] pci 0000:00:1c.1: [8086:2841] type 01 class 0x060400
[    0.187119] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.187205] pci 0000:00:1c.1: System wakeup disabled by ACPI
[    0.187256] pci 0000:00:1c.3: [8086:2845] type 01 class 0x060400
[    0.187376] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.187462] pci 0000:00:1c.3: System wakeup disabled by ACPI
[    0.187512] pci 0000:00:1c.5: [8086:2849] type 01 class 0x060400
[    0.187632] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.187718] pci 0000:00:1c.5: System wakeup disabled by ACPI
[    0.187765] pci 0000:00:1d.0: [8086:2830] type 00 class 0x0c0300
[    0.187827] pci 0000:00:1d.0: reg 0x20: [io  0x6f80-0x6f9f]
[    0.189840] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.189887] pci 0000:00:1d.1: [8086:2831] type 00 class 0x0c0300
[    0.189949] pci 0000:00:1d.1: reg 0x20: [io  0x6f60-0x6f7f]
[    0.191846] pci 0000:00:1d.1: System wakeup disabled by ACPI
[    0.191892] pci 0000:00:1d.2: [8086:2832] type 00 class 0x0c0300
[    0.191955] pci 0000:00:1d.2: reg 0x20: [io  0x6f40-0x6f5f]
[    0.193859] pci 0000:00:1d.2: System wakeup disabled by ACPI
[    0.193920] pci 0000:00:1d.7: [8086:2836] type 00 class 0x0c0320
[    0.193948] pci 0000:00:1d.7: reg 0x10: [mem 0xfed1c000-0xfed1c3ff]
[    0.194066] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.195939] pci 0000:00:1d.7: System wakeup disabled by ACPI
[    0.195991] pci 0000:00:1e.0: [8086:2448] type 01 class 0x060401
[    0.196149] pci 0000:00:1e.0: System wakeup disabled by ACPI
[    0.196200] pci 0000:00:1f.0: [8086:2815] type 00 class 0x060100
[    0.196324] pci 0000:00:1f.0: address space collision: [io  0x1000-0x107f] conflicts with ACPI CPU throttle [??? 0x00001010-0x00001015 flags 0x80000000]
[    0.196332] pci 0000:00:1f.0: quirk: [io  0x1080-0x10bf] claimed by ICH6 GPIO
[    0.196337] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0900 (mask 007f)
[    0.196344] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 0c80 (mask 003f)
[    0.196492] pci 0000:00:1f.1: [8086:2850] type 00 class 0x01018a
[    0.196512] pci 0000:00:1f.1: reg 0x10: [io  0x01f0-0x01f7]
[    0.196525] pci 0000:00:1f.1: reg 0x14: [io  0x03f4-0x03f7]
[    0.196539] pci 0000:00:1f.1: reg 0x18: [io  0x0170-0x0177]
[    0.196552] pci 0000:00:1f.1: reg 0x1c: [io  0x0374-0x0377]
[    0.196566] pci 0000:00:1f.1: reg 0x20: [io  0x6fa0-0x6faf]
[    0.196703] pci 0000:00:1f.2: [8086:2828] type 00 class 0x01018f
[    0.196727] pci 0000:00:1f.2: reg 0x10: [io  0x6eb0-0x6eb7]
[    0.196741] pci 0000:00:1f.2: reg 0x14: [io  0x6eb8-0x6ebb]
[    0.196754] pci 0000:00:1f.2: reg 0x18: [io  0x6ec0-0x6ec7]
[    0.196768] pci 0000:00:1f.2: reg 0x1c: [io  0x6ec8-0x6ecb]
[    0.196781] pci 0000:00:1f.2: reg 0x20: [io  0x6ee0-0x6eef]
[    0.196795] pci 0000:00:1f.2: reg 0x24: [io  0xeff0-0xefff]
[    0.196847] pci 0000:00:1f.2: PME# supported from D3hot
[    0.196957] pci 0000:00:1f.3: [8086:283e] type 00 class 0x0c0500
[    0.196977] pci 0000:00:1f.3: reg 0x10: [mem 0xfe9fbf00-0xfe9fbfff]
[    0.197024] pci 0000:00:1f.3: reg 0x20: [io  0x10c0-0x10df]
[    0.197245] pci 0000:00:1c.0: PCI bridge to [bus 0b]
[    0.197465] pci 0000:0c:00.0: [8086:4222] type 00 class 0x028000
[    0.197524] pci 0000:0c:00.0: reg 0x10: [mem 0xfe8ff000-0xfe8fffff]
[    0.197957] pci 0000:0c:00.0: PME# supported from D0 D3hot D3cold
[    0.198071] pci 0000:0c:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.198112] pci 0000:00:1c.1: PCI bridge to [bus 0c]
[    0.198121] pci 0000:00:1c.1:   bridge window [mem 0xfe800000-0xfe8fffff]
[    0.198238] acpiphp: Slot [1] registered
[    0.198248] pci 0000:00:1c.3: PCI bridge to [bus 0d-0e]
[    0.198254] pci 0000:00:1c.3:   bridge window [io  0xd000-0xdfff]
[    0.198260] pci 0000:00:1c.3:   bridge window [mem 0xfe600000-0xfe7fffff]
[    0.198269] pci 0000:00:1c.3:   bridge window [mem 0xf0000000-0xf01fffff 64bit pref]
[    0.198461] pci 0000:09:00.0: [14e4:1713] type 00 class 0x020000
[    0.198535] pci 0000:09:00.0: reg 0x10: [mem 0xfe5f0000-0xfe5fffff 64bit]
[    0.198971] pci 0000:09:00.0: PME# supported from D3hot D3cold
[    0.199155] pci 0000:00:1c.5: PCI bridge to [bus 09]
[    0.199164] pci 0000:00:1c.5:   bridge window [mem 0xfe500000-0xfe5fffff]
[    0.199260] pci 0000:03:01.0: [1180:0832] type 00 class 0x0c0010
[    0.199279] pci 0000:03:01.0: proprietary Ricoh MMC controller disabled (via firewire function)
[    0.199282] pci 0000:03:01.0: MMC cards are now supported by standard SDHCI controller
[    0.199300] pci 0000:03:01.0: reg 0x10: [mem 0xfe4ff800-0xfe4fffff]
[    0.199411] pci 0000:03:01.0: supports D1 D2
[    0.199414] pci 0000:03:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.199484] pci 0000:03:01.1: [1180:0822] type 00 class 0x080501
[    0.199511] pci 0000:03:01.1: reg 0x10: [mem 0xfe4ff400-0xfe4ff4ff]
[    0.199619] pci 0000:03:01.1: supports D1 D2
[    0.199622] pci 0000:03:01.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.199687] pci 0000:03:01.2: [1180:0592] type 00 class 0x088000
[    0.199712] pci 0000:03:01.2: reg 0x10: [mem 0xfe4ff600-0xfe4ff6ff]
[    0.199821] pci 0000:03:01.2: supports D1 D2
[    0.199823] pci 0000:03:01.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.199890] pci 0000:03:01.3: [1180:0852] type 00 class 0x088000
[    0.199915] pci 0000:03:01.3: reg 0x10: [mem 0xfe4ff700-0xfe4ff7ff]
[    0.200029] pci 0000:03:01.3: supports D1 D2
[    0.200032] pci 0000:03:01.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.200152] pci 0000:00:1e.0: PCI bridge to [bus 03] (subtractive decode)
[    0.200162] pci 0000:00:1e.0:   bridge window [mem 0xfe400000-0xfe4fffff]
[    0.200171] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.200174] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.200177] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.200180] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.200183] pci 0000:00:1e.0:   bridge window [mem 0x80000000-0xf7ffffff] (subtractive decode)
[    0.200186] pci 0000:00:1e.0:   bridge window [mem 0xfc000000-0xfebfffff] (subtractive decode)
[    0.200189] pci 0000:00:1e.0:   bridge window [mem 0xfec10000-0xfecfffff] (subtractive decode)
[    0.200192] pci 0000:00:1e.0:   bridge window [mem 0xfed1c000-0xfed1ffff] (subtractive decode)
[    0.200195] pci 0000:00:1e.0:   bridge window [mem 0xfed90000-0xfed9ffff] (subtractive decode)
[    0.200197] pci 0000:00:1e.0:   bridge window [mem 0xfeda7000-0xfedfffff] (subtractive decode)
[    0.200200] pci 0000:00:1e.0:   bridge window [mem 0xfee10000-0xff9fffff] (subtractive decode)
[    0.200203] pci 0000:00:1e.0:   bridge window [mem 0xffc00000-0xffdfffff] (subtractive decode)
[    0.200254] pci_bus 0000:00: on NUMA node 0
[    0.200837] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[    0.200949] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *10
[    0.201059] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 11) *4
[    0.201172] ACPI: PCI Interrupt Link [LNKD] (IRQs *5 7 9 10 11)
[    0.201283] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.201397] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.201511] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
[    0.201610] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.201849] ACPI: Enabled 4 GPEs in block 00 to 1F
[    0.204000] ACPI: \_SB_.PCI0: notify handler is installed
[    0.204061] Found 1 acpi root devices
[    0.205943] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.205943] vgaarb: loaded
[    0.205943] vgaarb: bridge control possible 0000:00:02.0
[    0.205943] SCSI subsystem initialized
[    0.205950] libata version 3.00 loaded.
[    0.205950] ACPI: bus type USB registered
[    0.205950] usbcore: registered new interface driver usbfs
[    0.205950] usbcore: registered new interface driver hub
[    0.205950] usbcore: registered new device driver usb
[    0.205950] PCI: Using ACPI for IRQ routing
[    0.206685] PCI: pci_cache_line_size set to 64 bytes
[    0.206796] e820: reserve RAM buffer [mem 0x0009f000-0x0009ffff]
[    0.206799] e820: reserve RAM buffer [mem 0x7f66d800-0x7fffffff]
[    0.206905] NetLabel: Initializing
[    0.206907] NetLabel:  domain hash size = 128
[    0.206909] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.206928] NetLabel:  unlabeled traffic allowed by default
[    0.208112] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.208120] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.208125] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.212038] Switched to clocksource hpet
[    0.221766] AppArmor: AppArmor Filesystem Enabled
[    0.221810] pnp: PnP ACPI init
[    0.221830] ACPI: bus type PNP registered
[    0.221937] pnp 00:00: Plug and Play ACPI device, IDs PNP0f13 (active)
[    0.221985] pnp 00:01: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.222030] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.222076] pnp 00:03: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.222157] system 00:04: [io  0x0c80-0x0cff] could not be reserved
[    0.222162] system 00:04: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.222185] pnp 00:05: [dma 4]
[    0.222214] pnp 00:05: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.222259] pnp 00:06: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.222349] system 00:07: [mem 0xfed00000-0xfed003ff] has been reserved
[    0.222353] system 00:07: Plug and Play ACPI device, IDs PNP0103 PNP0c01 (active)
[    0.222536] pnp 00:08: disabling [io  0x1000-0x1005] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.222540] pnp 00:08: disabling [io  0x1008-0x100f] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.222588] system 00:08: [io  0x0900-0x097f] has been reserved
[    0.222592] system 00:08: [io  0x04d0-0x04d1] has been reserved
[    0.222596] system 00:08: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.222631] pnp 00:09: disabling [io  0x1006-0x1007] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.222635] pnp 00:09: disabling [io  0x100a-0x1059] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.222639] pnp 00:09: disabling [io  0x1060-0x107f] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.222642] pnp 00:09: disabling [io  0x1010-0x102f] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.222687] system 00:09: [io  0xf400-0xf4fe] has been reserved
[    0.222691] system 00:09: [io  0x1080-0x10bf] has been reserved
[    0.222694] system 00:09: [io  0x10c0-0x10df] has been reserved
[    0.222697] system 00:09: [io  0x0809] has been reserved
[    0.222701] system 00:09: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.235004] system 00:0a: [mem 0x00000000-0x0009efff] could not be reserved
[    0.235009] system 00:0a: [mem 0x0009f000-0x0009ffff] could not be reserved
[    0.235012] system 00:0a: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.235016] system 00:0a: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.235019] system 00:0a: [mem 0x00100000-0x7f66d7ff] could not be reserved
[    0.235023] system 00:0a: [mem 0x7f66d800-0x7f6fffff] has been reserved
[    0.235026] system 00:0a: [mem 0x7f700000-0x7f7fffff] has been reserved
[    0.235030] system 00:0a: [mem 0x7f700000-0x7fefffff] could not be reserved
[    0.235033] system 00:0a: [mem 0xffe00000-0xffffffff] has been reserved
[    0.235037] system 00:0a: [mem 0xffa00000-0xffbfffff] has been reserved
[    0.235040] system 00:0a: [mem 0xfec00000-0xfec0ffff] could not be reserved
[    0.235043] system 00:0a: [mem 0xfee00000-0xfee0ffff] has been reserved
[    0.235047] system 00:0a: [mem 0xfed20000-0xfed8ffff] has been reserved
[    0.235050] system 00:0a: [mem 0xfeda0000-0xfeda3fff] has been reserved
[    0.235054] system 00:0a: [mem 0xfeda4000-0xfeda4fff] has been reserved
[    0.235057] system 00:0a: [mem 0xfeda5000-0xfeda5fff] has been reserved
[    0.235060] system 00:0a: [mem 0xfeda6000-0xfeda6fff] has been reserved
[    0.235064] system 00:0a: [mem 0xfed18000-0xfed1bfff] has been reserved
[    0.235067] system 00:0a: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.235071] system 00:0a: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.235140] pnp: PnP ACPI: found 11 devices
[    0.235142] ACPI: bus type PNP unregistered
[    0.235146] PnPBIOS: Disabled by ACPI PNP
[    0.272527] pci 0000:00:1c.0: bridge window [io  0x1000-0x0fff] to [bus 0b] add_size 1000
[    0.272533] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 0b] add_size 200000
[    0.272537] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff] to [bus 0b] add_size 200000
[    0.272550] pci 0000:00:1c.1: bridge window [io  0x1000-0x0fff] to [bus 0c] add_size 1000
[    0.272554] pci 0000:00:1c.1: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 0c] add_size 200000
[    0.272577] pci 0000:00:1c.5: bridge window [io  0x1000-0x0fff] to [bus 09] add_size 1000
[    0.272581] pci 0000:00:1c.5: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 09] add_size 200000
[    0.272598] pci 0000:00:1f.0: BAR 13: [io  0x1000-0x107f] has bogus alignment
[    0.272603] pci 0000:00:1c.0: res[14]=[mem 0x00100000-0x000fffff] get_res_add_size add_size 200000
[    0.272607] pci 0000:00:1c.0: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.272610] pci 0000:00:1c.1: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.272613] pci 0000:00:1c.5: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.272616] pci 0000:00:1c.0: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.272619] pci 0000:00:1c.1: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.272622] pci 0000:00:1c.5: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.272629] pci 0000:00:1c.0: BAR 14: assigned [mem 0x80000000-0x801fffff]
[    0.272633] pci 0000:00:1c.0: BAR 15: assigned [mem 0x80200000-0x803fffff 64bit pref]
[    0.272637] pci 0000:00:1c.1: BAR 15: assigned [mem 0x80400000-0x805fffff 64bit pref]
[    0.272641] pci 0000:00:1c.5: BAR 15: assigned [mem 0x80600000-0x807fffff 64bit pref]
[    0.272646] pci 0000:00:1c.0: BAR 13: assigned [io  0x2000-0x2fff]
[    0.272649] pci 0000:00:1c.1: BAR 13: assigned [io  0x3000-0x3fff]
[    0.272653] pci 0000:00:1c.5: BAR 13: assigned [io  0x4000-0x4fff]
[    0.272657] pci 0000:00:1c.0: PCI bridge to [bus 0b]
[    0.272662] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.272669] pci 0000:00:1c.0:   bridge window [mem 0x80000000-0x801fffff]
[    0.272675] pci 0000:00:1c.0:   bridge window [mem 0x80200000-0x803fffff 64bit pref]
[    0.272685] pci 0000:00:1c.1: PCI bridge to [bus 0c]
[    0.272689] pci 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
[    0.272696] pci 0000:00:1c.1:   bridge window [mem 0xfe800000-0xfe8fffff]
[    0.272702] pci 0000:00:1c.1:   bridge window [mem 0x80400000-0x805fffff 64bit pref]
[    0.272711] pci 0000:00:1c.3: PCI bridge to [bus 0d-0e]
[    0.272715] pci 0000:00:1c.3:   bridge window [io  0xd000-0xdfff]
[    0.272723] pci 0000:00:1c.3:   bridge window [mem 0xfe600000-0xfe7fffff]
[    0.272729] pci 0000:00:1c.3:   bridge window [mem 0xf0000000-0xf01fffff 64bit pref]
[    0.272738] pci 0000:00:1c.5: PCI bridge to [bus 09]
[    0.272742] pci 0000:00:1c.5:   bridge window [io  0x4000-0x4fff]
[    0.272749] pci 0000:00:1c.5:   bridge window [mem 0xfe500000-0xfe5fffff]
[    0.272755] pci 0000:00:1c.5:   bridge window [mem 0x80600000-0x807fffff 64bit pref]
[    0.272764] pci 0000:00:1e.0: PCI bridge to [bus 03]
[    0.272772] pci 0000:00:1e.0:   bridge window [mem 0xfe400000-0xfe4fffff]
[    0.272785] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.272788] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.272791] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.272793] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.272796] pci_bus 0000:00: resource 8 [mem 0x80000000-0xf7ffffff]
[    0.272799] pci_bus 0000:00: resource 9 [mem 0xfc000000-0xfebfffff]
[    0.272802] pci_bus 0000:00: resource 10 [mem 0xfec10000-0xfecfffff]
[    0.272805] pci_bus 0000:00: resource 11 [mem 0xfed1c000-0xfed1ffff]
[    0.272807] pci_bus 0000:00: resource 12 [mem 0xfed90000-0xfed9ffff]
[    0.272810] pci_bus 0000:00: resource 13 [mem 0xfeda7000-0xfedfffff]
[    0.272813] pci_bus 0000:00: resource 14 [mem 0xfee10000-0xff9fffff]
[    0.272815] pci_bus 0000:00: resource 15 [mem 0xffc00000-0xffdfffff]
[    0.272819] pci_bus 0000:0b: resource 0 [io  0x2000-0x2fff]
[    0.272821] pci_bus 0000:0b: resource 1 [mem 0x80000000-0x801fffff]
[    0.272824] pci_bus 0000:0b: resource 2 [mem 0x80200000-0x803fffff 64bit pref]
[    0.272827] pci_bus 0000:0c: resource 0 [io  0x3000-0x3fff]
[    0.272830] pci_bus 0000:0c: resource 1 [mem 0xfe800000-0xfe8fffff]
[    0.272833] pci_bus 0000:0c: resource 2 [mem 0x80400000-0x805fffff 64bit pref]
[    0.272836] pci_bus 0000:0d: resource 0 [io  0xd000-0xdfff]
[    0.272838] pci_bus 0000:0d: resource 1 [mem 0xfe600000-0xfe7fffff]
[    0.272841] pci_bus 0000:0d: resource 2 [mem 0xf0000000-0xf01fffff 64bit pref]
[    0.272844] pci_bus 0000:09: resource 0 [io  0x4000-0x4fff]
[    0.272847] pci_bus 0000:09: resource 1 [mem 0xfe500000-0xfe5fffff]
[    0.272850] pci_bus 0000:09: resource 2 [mem 0x80600000-0x807fffff 64bit pref]
[    0.272852] pci_bus 0000:03: resource 1 [mem 0xfe400000-0xfe4fffff]
[    0.272855] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    0.272858] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
[    0.272860] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    0.272863] pci_bus 0000:03: resource 7 [mem 0x000d0000-0x000dffff]
[    0.272866] pci_bus 0000:03: resource 8 [mem 0x80000000-0xf7ffffff]
[    0.272869] pci_bus 0000:03: resource 9 [mem 0xfc000000-0xfebfffff]
[    0.272871] pci_bus 0000:03: resource 10 [mem 0xfec10000-0xfecfffff]
[    0.272874] pci_bus 0000:03: resource 11 [mem 0xfed1c000-0xfed1ffff]
[    0.272877] pci_bus 0000:03: resource 12 [mem 0xfed90000-0xfed9ffff]
[    0.272879] pci_bus 0000:03: resource 13 [mem 0xfeda7000-0xfedfffff]
[    0.272882] pci_bus 0000:03: resource 14 [mem 0xfee10000-0xff9fffff]
[    0.272885] pci_bus 0000:03: resource 15 [mem 0xffc00000-0xffdfffff]
[    0.272927] NET: Registered protocol family 2
[    0.273121] TCP established hash table entries: 8192 (order: 3, 32768 bytes)
[    0.273142] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.273171] TCP: Hash tables configured (established 8192 bind 8192)
[    0.273205] TCP: reno registered
[    0.273208] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.273218] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.273285] NET: Registered protocol family 1
[    0.273301] pci 0000:00:02.0: Boot video device
[    0.276175] PCI: CLS 64 bytes, default 64
[    0.276234] Trying to unpack rootfs image as initramfs...
[    0.689960] Freeing initrd memory: 18228K (f5c56000 - f6e23000)
[    0.690062] Simple Boot Flag at 0x79 set to 0x1
[    0.690247] microcode: CPU0 sig=0x6fd, pf=0x80, revision=0xa3
[    0.690259] microcode: CPU1 sig=0x6fd, pf=0x80, revision=0xa3
[    0.690347] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.690350] Scanning for low memory corruption every 60 seconds
[    0.690658] Initialise system trusted keyring
[    0.690715] audit: initializing netlink socket (disabled)
[    0.690733] type=2000 audit(1403473257.688:1): initialized
[    0.717777] bounce pool size: 64 pages
[    0.717796] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.719524] zbud: loaded
[    0.719600] VFS: Disk quotas dquot_6.5.2
[    0.719660] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.720285] fuse init (API version 7.22)
[    0.720394] msgmni has been set to 1718
[    0.720474] Key type big_key registered
[    0.721129] Key type asymmetric registered
[    0.721132] Asymmetric key parser 'x509' registered
[    0.721175] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.721220] io scheduler noop registered
[    0.721223] io scheduler deadline registered (default)
[    0.721260] io scheduler cfq registered
[    0.721391] pcieport 0000:00:1c.0: device [8086:283f] has invalid IRQ; check vendor BIOS
[    0.721659] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.721745] pcieport 0000:00:1c.1: device [8086:2841] has invalid IRQ; check vendor BIOS
[    0.721970] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.722050] pcieport 0000:00:1c.3: device [8086:2845] has invalid IRQ; check vendor BIOS
[    0.722273] pcieport 0000:00:1c.3: irq 42 for MSI/MSI-X
[    0.722353] pcieport 0000:00:1c.5: device [8086:2849] has invalid IRQ; check vendor BIOS
[    0.722573] pcieport 0000:00:1c.5: irq 43 for MSI/MSI-X
[    0.722686] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.722706] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.722762] vesafb: mode is 1024x768x32, linelength=4096, pages=0
[    0.722764] vesafb: scrolling: redraw
[    0.722767] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    0.722940] vesafb: framebuffer at 0xe0000000, mapped to 0xf8480000, using 3072k, total 3072k
[    0.746981] Console: switching to colour frame buffer device 128x48
[    0.770919] fb0: VESA VGA frame buffer device
[    0.770942] intel_idle: does not run on family 6 model 15
[    0.770952] ipmi message handler version 39.2
[    0.771054] ACPI: AC Adapter [AC] (on-line)
[    0.771186] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.771592] ACPI: Lid Switch [LID]
[    0.771639] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.771643] ACPI: Power Button [PBTN]
[    0.771688] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.771692] ACPI: Sleep Button [SBTN]
[    0.771826] Monitor-Mwait will be used to enter C-1 state
[    0.771832] Monitor-Mwait will be used to enter C-2 state
[    0.771837] Monitor-Mwait will be used to enter C-3 state
[    0.771840] tsc: Marking TSC unstable due to TSC halts in idle
[    0.771853] ACPI: acpi_idle registered with cpuidle
[    0.778754] thermal LNXTHERM:00: registered as thermal_zone0
[    0.778757] ACPI: Thermal Zone [THM] (62 C)
[    0.778793] GHES: HEST is not enabled!
[    0.778899] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.784069] isapnp: Scanning for PnP cards...
[    0.795683] Linux agpgart interface v0.103
[    0.795805] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
[    0.795851] agpgart-intel 0000:00:00.0: detected gtt size: 524288K total, 262144K mappable
[    0.796340] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    0.800882] ACPI: Battery Slot [BAT0] (battery present)
[    0.800945] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
[    0.802663] brd: module loaded
[    0.803569] loop: module loaded
[    0.803729] ata_piix 0000:00:1f.1: version 2.13
[    0.804620] scsi0 : ata_piix
[    0.804691] scsi1 : ata_piix
[    0.804733] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x6fa0 irq 14
[    0.804736] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x6fa8 irq 15
[    0.804953] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.805160] ata2: port disabled--ignoring
[    0.960837] scsi2 : ata_piix
[    0.960901] scsi3 : ata_piix
[    0.960948] ata3: SATA max UDMA/133 cmd 0x6eb0 ctl 0x6eb8 bmdma 0x6ee0 irq 17
[    0.960956] ata4: SATA max UDMA/133 cmd 0x6ec0 ctl 0x6ec8 bmdma 0x6ee8 irq 17
[    0.961367] libphy: Fixed MDIO Bus: probed
[    0.961494] tun: Universal TUN/TAP device driver, 1.6
[    0.961496] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.961563] PPP generic driver version 2.4.2
[    0.961616] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.961621] ehci-pci: EHCI PCI platform driver
[    0.961874] ehci-pci 0000:00:1a.7: EHCI Host Controller
[    0.961884] ehci-pci 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.961902] ehci-pci 0000:00:1a.7: debug port 1
[    0.965804] ehci-pci 0000:00:1a.7: cache line size of 64 is not supported
[    0.965850] ehci-pci 0000:00:1a.7: irq 22, io mem 0xfed1c400
[    0.968511] ata1.00: ATAPI: MATSHITA DVD+/-RW UJ-857G, Z111, max UDMA/33
[    0.976216] ehci-pci 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.976286] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.976289] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.976293] usb usb1: Product: EHCI Host Controller
[    0.976295] usb usb1: Manufacturer: Linux 3.13.0-29-generic ehci_hcd
[    0.976298] usb usb1: SerialNumber: 0000:00:1a.7
[    0.976420] hub 1-0:1.0: USB hub found
[    0.976430] hub 1-0:1.0: 4 ports detected
[    0.976850] ehci-pci 0000:00:1d.7: EHCI Host Controller
[    0.976856] ehci-pci 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.976873] ehci-pci 0000:00:1d.7: debug port 1
[    0.980788] ehci-pci 0000:00:1d.7: cache line size of 64 is not supported
[    0.980811] ehci-pci 0000:00:1d.7: irq 20, io mem 0xfed1c000
[    0.984405] ata1.00: configured for UDMA/33
[    0.992040] ehci-pci 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.992108] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    0.992112] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.992114] usb usb2: Product: EHCI Host Controller
[    0.992117] usb usb2: Manufacturer: Linux 3.13.0-29-generic ehci_hcd
[    0.992120] usb usb2: SerialNumber: 0000:00:1d.7
[    0.992232] hub 2-0:1.0: USB hub found
[    0.992241] hub 2-0:1.0: 6 ports detected
[    0.992528] ehci-platform: EHCI generic platform driver
[    0.992540] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.992542] ohci-pci: OHCI PCI platform driver
[    0.992557] ohci-platform: OHCI generic platform driver
[    0.992566] uhci_hcd: USB Universal Host Controller Interface driver
[    0.992789] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.992795] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.992827] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00006f20
[    0.992886] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    0.992890] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.992892] usb usb3: Product: UHCI Host Controller
[    0.992895] usb usb3: Manufacturer: Linux 3.13.0-29-generic uhci_hcd
[    0.992898] usb usb3: SerialNumber: 0000:00:1a.0
[    0.993012] hub 3-0:1.0: USB hub found
[    0.993022] hub 3-0:1.0: 2 ports detected
[    0.993355] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.993361] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.993402] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00006f00
[    0.993459] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    0.993462] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.993465] usb usb4: Product: UHCI Host Controller
[    0.993467] usb usb4: Manufacturer: Linux 3.13.0-29-generic uhci_hcd
[    0.993470] usb usb4: SerialNumber: 0000:00:1a.1
[    0.993588] hub 4-0:1.0: USB hub found
[    0.993597] hub 4-0:1.0: 2 ports detected
[    0.993930] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.993937] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    0.993965] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00006f80
[    0.994023] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    0.994026] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.994029] usb usb5: Product: UHCI Host Controller
[    0.994031] usb usb5: Manufacturer: Linux 3.13.0-29-generic uhci_hcd
[    0.994034] usb usb5: SerialNumber: 0000:00:1d.0
[    0.994147] hub 5-0:1.0: USB hub found
[    0.994156] hub 5-0:1.0: 2 ports detected
[    0.994490] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.994496] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    0.994525] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00006f60
[    0.994583] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
[    0.994586] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.994589] usb usb6: Product: UHCI Host Controller
[    0.994592] usb usb6: Manufacturer: Linux 3.13.0-29-generic uhci_hcd
[    0.994594] usb usb6: SerialNumber: 0000:00:1d.1
[    0.994703] hub 6-0:1.0: USB hub found
[    0.994712] hub 6-0:1.0: 2 ports detected
[    0.995041] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.995047] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    0.995076] uhci_hcd 0000:00:1d.2: irq 22, io base 0x00006f40
[    0.995133] usb usb7: New USB device found, idVendor=1d6b, idProduct=0001
[    0.995137] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.995140] usb usb7: Product: UHCI Host Controller
[    0.995142] usb usb7: Manufacturer: Linux 3.13.0-29-generic uhci_hcd
[    0.995145] usb usb7: SerialNumber: 0000:00:1d.2
[    0.995254] hub 7-0:1.0: USB hub found
[    0.995263] hub 7-0:1.0: 2 ports detected
[    0.995473] i8042: PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.003678] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.003685] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.003806] mousedev: PS/2 mouse device common for all mice
[    1.003967] rtc_cmos 00:02: RTC can wake from S4
[    1.004148] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.004183] rtc_cmos 00:02: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.004270] device-mapper: uevent: version 1.0.3
[    1.004344] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
[    1.004369] platform eisa.0: Probing EISA bus 0
[    1.004372] platform eisa.0: EISA: Cannot allocate resource for mainboard
[    1.004375] platform eisa.0: Cannot allocate resource for EISA slot 1
[    1.004378] platform eisa.0: Cannot allocate resource for EISA slot 2
[    1.004381] platform eisa.0: Cannot allocate resource for EISA slot 3
[    1.004384] platform eisa.0: Cannot allocate resource for EISA slot 4
[    1.004386] platform eisa.0: Cannot allocate resource for EISA slot 5
[    1.004389] platform eisa.0: Cannot allocate resource for EISA slot 6
[    1.004392] platform eisa.0: Cannot allocate resource for EISA slot 7
[    1.004394] platform eisa.0: Cannot allocate resource for EISA slot 8
[    1.004397] platform eisa.0: EISA: Detected 0 cards
[    1.004406] cpufreq-nforce2: No nForce2 chipset.
[    1.004410] ledtrig-cpu: registered to indicate activity on CPUs
[    1.004579] TCP: cubic registered
[    1.004705] NET: Registered protocol family 10
[    1.004950] NET: Registered protocol family 17
[    1.004965] Key type dns_resolver registered
[    1.005168] Using IPI No-Shortcut mode
[    1.005256] Loading compiled-in X.509 certificates
[    1.009689] Loaded X.509 cert 'Magrathea: Glacier signing key: 497ec33ede6aa573c29cd85a3d778ac2aeb3d36f'
[    1.009704] registered taskstats version 1
[    1.010685] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.012689] Key type trusted registered
[    1.015273] Key type encrypted registered
[    1.017509] AppArmor: AppArmor sha1 policy hashing enabled
[    1.017513] IMA: No TPM chip found, activating TPM-bypass!
[    1.018068] regulator-dummy: disabling
[    1.018120]   Magic number: 2:16:703
[    1.018228] rtc_cmos 00:02: setting system clock to 2014-06-22 21:40:58 UTC (1403473258)
[    1.019133] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.019135] EDD information not available.
[    1.019178] PM: Hibernation image not present or could not be loaded.
[    1.098452] isapnp: No Plug & Play device found
[    1.100136] scsi 0:0:0:0: CD-ROM            MATSHITA DVD+-RW UJ-857G  Z111 PQ: 0 ANSI: 5
[    1.102434] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda caddy
[    1.102438] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.102654] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.102789] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.548090] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    1.681136] usb 2-1: New USB device found, idVendor=1058, idProduct=0820
[    1.681140] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=5
[    1.681143] usb 2-1: Product: My Passport 0820
[    1.681145] usb 2-1: Manufacturer: Western Digital
[    1.681148] usb 2-1: SerialNumber: 5758323145413343464D3736
[    1.760143] ata3.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.760164] ata3.01: SATA link down (SStatus 0 SControl 300)
[    1.821773] ata3.00: ATA-8: ST9160314AS, D003DEM1, max UDMA/133
[    1.821780] ata3.00: 312581808 sectors, multi 8: LBA48 NCQ (depth 0/32)
[    1.836733] ata3.00: configured for UDMA/133
[    1.836948] scsi 2:0:0:0: Direct-Access     ATA      ST9160314AS      D003 PQ: 0 ANSI: 5
[    1.837087] sd 2:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.837096] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    1.837136] sd 2:0:0:0: [sda] Write Protect is off
[    1.837140] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.837162] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.880671]  sda: sda1 sda2 < sda5 > sda3
[    1.881187] sd 2:0:0:0: [sda] Attached SCSI disk
[    2.052062] usb 2-6: new high-speed USB device number 4 using ehci-pci
[    2.189137] usb 2-6: New USB device found, idVendor=05a9, idProduct=2640
[    2.189143] usb 2-6: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.189148] usb 2-6: Product: Laptop Integrated Webcam
[    2.189153] usb 2-6: Manufacturer: OmniVision Technologies, Inc. -2640-07.07.20.3
[    2.316051] ata4.01: failed to resume link (SControl 0)
[    2.316120] ata4.00: SATA link down (SStatus 0 SControl 300)
[    2.316146] ata4.01: SATA link down (SStatus 0 SControl 0)
[    2.316674] Freeing unused kernel memory: 872K (c19b2000 - c1a8c000)
[    2.316752] Write protecting the kernel text: 6524k
[    2.316871] Write protecting the kernel read-only data: 2764k
[    2.316873] NX-protecting the kernel data: 5764k
[    2.333051] systemd-udevd[104]: starting version 204
[    2.372927] pps_core: LinuxPPS API ver. 1 registered
[    2.372931] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
[    2.378281] PTP clock support registered
[    2.389649] tg3.c:v3.134 (Sep 16, 2013)
[    2.407799] sdhci: Secure Digital Host Controller Interface driver
[    2.407803] sdhci: Copyright(c) Pierre Ossman
[    2.428461] tg3 0000:09:00.0 eth0: Tigon3 [partno(BCM95906) rev c002] (PCI Express) MAC address 00:15:c5:87:2a:1e
[    2.428466] tg3 0000:09:00.0 eth0: attached PHY is 5906 (10/100Base-TX Ethernet) (WireSpeed[0], EEE[0])
[    2.428470] tg3 0000:09:00.0 eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[0]
[    2.428473] tg3 0000:09:00.0 eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    2.428812] usb 3-2: new full-speed USB device number 2 using uhci_hcd
[    2.433286] usb-storage 2-1:1.0: USB Mass Storage device detected
[    2.438174] scsi4 : usb-storage 2-1:1.0
[    2.438274] usbcore: registered new interface driver usb-storage
[    2.444510] sdhci-pci 0000:03:01.1: SDHCI controller found [1180:0822] (rev 22)
[    2.447334] sdhci-pci 0000:03:01.1: dummy supplies not allowed
[    2.447339] mmc0: no vqmmc regulator found
[    2.447342] sdhci-pci 0000:03:01.1: dummy supplies not allowed
[    2.447344] mmc0: no vmmc regulator found
[    2.448941] mmc0: SDHCI controller on PCI [0000:03:01.1] using DMA
[    2.520107] firewire_ohci 0000:03:01.0: added OHCI v1.10 device as card 0, 4 IR + 4 IT contexts, quirks 0x11
[    2.601907] usb 3-2: New USB device found, idVendor=0a5c, idProduct=4500
[    2.601915] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.601920] usb 3-2: Product: BCM2045B2
[    2.601925] usb 3-2: Manufacturer: Broadcom
[    2.603978] hub 3-2:1.0: USB hub found
[    2.605902] hub 3-2:1.0: 3 ports detected
[    2.848080] usb 7-1: new full-speed USB device number 2 using uhci_hcd
[    3.020318] firewire_core 0000:03:01.0: created device fw0: GUID 484fc0002dd16838, S400
[    3.021141] usb 7-1: New USB device found, idVendor=0483, idProduct=2016
[    3.021148] usb 7-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    3.021153] usb 7-1: Product: Biometric Coprocessor
[    3.021157] usb 7-1: Manufacturer: STMicroelectronics
[    3.142114] psmouse serio1: synaptics: Touchpad model: 1, fw: 6.3, id: 0x1c0b1, caps: 0xa04753/0x200000/0x0, board id: 3655, fw id: 356587
[    3.178936] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input5
[    3.353907] usb 3-2.1: new full-speed USB device number 3 using uhci_hcd
[    3.436805] scsi 4:0:0:0: Direct-Access     WD       My Passport 0820 1007 PQ: 0 ANSI: 6
[    3.437301] scsi 4:0:0:1: Enclosure         WD       SES Device       1007 PQ: 0 ANSI: 6
[    3.437638] sd 4:0:0:0: Attached scsi generic sg2 type 0
[    3.437791] scsi 4:0:0:1: Attached scsi generic sg3 type 13
[    3.443115] sd 4:0:0:0: [sdb] 1953458176 512-byte logical blocks: (1.00 TB/931 GiB)
[    3.444261] sd 4:0:0:0: [sdb] Write Protect is off
[    3.444265] sd 4:0:0:0: [sdb] Mode Sense: 47 00 10 08
[    3.445246] sd 4:0:0:0: [sdb] No Caching mode page found
[    3.445249] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[    3.451525] sd 4:0:0:0: [sdb] No Caching mode page found
[    3.451532] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[    3.482902] usb 3-2.1: New USB device found, idVendor=413c, idProduct=8126
[    3.482909] usb 3-2.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    3.482914] usb 3-2.1: Product: BCM2045
[    3.482919] usb 3-2.1: Manufacturer: Broadcom Corp
[    3.501324]  sdb: sdb1 sdb2 sdb3
[    3.506149] sd 4:0:0:0: [sdb] No Caching mode page found
[    3.506154] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[    3.506158] sd 4:0:0:0: [sdb] Attached SCSI disk
[    3.507784] ses 4:0:0:1: Attached Enclosure device
[    3.561898] usb 3-2.2: new full-speed USB device number 4 using uhci_hcd
[    3.693907] usb 3-2.2: New USB device found, idVendor=0a5c, idProduct=4502
[    3.693914] usb 3-2.2: New USB device strings: Mfr=1, Product=0, SerialNumber=0
[    3.693919] usb 3-2.2: Manufacturer: Broadcom Corp
[    3.705547] hidraw: raw HID events driver (C) Jiri Kosina
[    3.716371] usbcore: registered new interface driver usbhid
[    3.716375] usbhid: USB HID core driver
[    3.722070] input: Broadcom Corp as /devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2.2/3-2.2:1.0/input/input6
[    3.722183] hid-generic 0003:0A5C:4502.0001: input,hidraw0: USB HID v1.11 Keyboard [Broadcom Corp] on usb-0000:00:1a.0-2.2/input0
[    3.773902] usb 3-2.3: new full-speed USB device number 5 using uhci_hcd
[    3.904917] usb 3-2.3: New USB device found, idVendor=0a5c, idProduct=4503
[    3.904924] usb 3-2.3: New USB device strings: Mfr=1, Product=0, SerialNumber=0
[    3.904930] usb 3-2.3: Manufacturer: Broadcom Corp
[    3.913715] input: Broadcom Corp as /devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2.3/3-2.3:1.0/input/input7
[    3.913848] hid-generic 0003:0A5C:4503.0002: input,hidraw1: USB HID v1.11 Mouse [Broadcom Corp] on usb-0000:00:1a.0-2.3/input0
[    3.996045] random: nonblocking pool is initialized
[    4.021460] EXT4-fs (sdb3): mounted filesystem with ordered data mode. Opts: (null)
[   15.774680] EXT4-fs (sdb3): re-mounted. Opts: errors=remount-ro
[   16.506123] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.591373] init: bootchart main process (334) terminated with status 127
[   16.813515] systemd-udevd[386]: starting version 204
[   16.905971] init: bootchart post-stop process (355) terminated with status 127
[   17.363931] lp: driver loaded but no devices found
[   17.484696] ppdev: user-space parallel port driver
[   18.583149] Bluetooth: Core ver 2.17
[   18.583173] NET: Registered protocol family 31
[   18.583176] Bluetooth: HCI device and connection manager initialized
[   18.583186] Bluetooth: HCI socket layer initialized
[   18.583190] Bluetooth: L2CAP socket layer initialized
[   18.583196] Bluetooth: SCO socket layer initialized
[   18.664848] Bluetooth: RFCOMM TTY layer initialized
[   18.664865] Bluetooth: RFCOMM socket layer initialized
[   18.664872] Bluetooth: RFCOMM ver 1.11
[   18.757743] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   18.757748] Bluetooth: BNEP filters: protocol multicast
[   18.757759] Bluetooth: BNEP socket layer initialized
[   18.874903] init: avahi-cups-reload main process (487) terminated with status 1
[   19.227802] wmi: Mapper loaded
[   19.512819] [drm] Initialized drm 1.1.0 20060810
[   19.608119] usbcore: registered new interface driver btusb
[   19.672065] r592: driver successfully loaded
[   19.734701] cfg80211: Calling CRDA to update world regulatory domain
[   20.034611] [drm] Memory usable by graphics device = 512M
[   20.034618] checking generic (e0000000 300000) vs hw (e0000000 10000000)
[   20.034621] fb: conflicting fb hw usage inteldrmfb vs VESA VGA - removing generic driver
[   20.034667] Console: switching to colour dummy device 80x25
[   20.066874] i915 0000:00:02.0: irq 44 for MSI/MSI-X
[   20.066890] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[   20.066893] [drm] Driver supports precise vblank timestamp query.
[   20.066962] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   20.085398] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   20.085402] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   20.085452] iwl3945 0000:0c:00.0: can't disable ASPM; OS doesn't have ASPM control
[   20.152084] r852: driver loaded successfully
[   20.161206] iwl3945 0000:0c:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   20.161212] iwl3945 0000:0c:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   20.161286] iwl3945 0000:0c:00.0: irq 45 for MSI/MSI-X
[   20.264354] type=1400 audit(1403453477.742:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=518 comm="apparmor_parser"
[   20.264363] type=1400 audit(1403453477.742:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=518 comm="apparmor_parser"
[   20.264370] type=1400 audit(1403453477.742:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=518 comm="apparmor_parser"
[   20.264979] type=1400 audit(1403453477.742:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=518 comm="apparmor_parser"
[   20.264987] type=1400 audit(1403453477.742:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=518 comm="apparmor_parser"
[   20.265292] type=1400 audit(1403453477.742:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=518 comm="apparmor_parser"
[   20.285676] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   20.319607] type=1400 audit(1403453477.794:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=454 comm="apparmor_parser"
[   20.319617] type=1400 audit(1403453477.794:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=454 comm="apparmor_parser"
[   20.319852] [drm] initialized overlay support
[   20.320245] type=1400 audit(1403453477.798:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=454 comm="apparmor_parser"
[   20.370477] Linux video capture interface: v2.00
[   20.379467] fbcon: inteldrmfb (fb0) is primary device
[   20.426748] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   20.724220] uvcvideo: Found UVC 1.00 device Laptop Integrated Webcam (05a9:2640)
[   20.725082] input: Laptop Integrated Webcam as /devices/pci0000:00/0000:00:1d.7/usb2/2-6/2-6:1.0/input/input8
[   20.725226] usbcore: registered new interface driver uvcvideo
[   20.725226] USB Video Class driver (1.1.1)
[   21.199503] input: Dell WMI hotkeys as /devices/virtual/input/input9
[   21.213725] gpio_ich: GPIO from 206 to 255 on gpio_ich
[   21.250417] Console: switching to colour frame buffer device 160x50
[   21.255681] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   21.255683] i915 0000:00:02.0: registered panic notifier
[   21.260939] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[   21.277380] acpi device:35: registered as cooling_device2
[   21.277820] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input10
[   21.278096] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[   21.278250] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   21.278578] snd_hda_intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[   21.351673] autoconfig: line_outs=1 (0xd/0x0/0x0/0x0/0x0) type:speaker
[   21.351678]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   21.351681]    hp_outs=2 (0xf/0xa/0x0/0x0/0x0)
[   21.351682]    mono: mono_out=0x0
[   21.351684]    dig-out=0x21/0x0
[   21.351686]    inputs:
[   21.351688]      Internal Mic=0x13
[   21.351691]      Mic=0xe
[   21.663920] cfg80211: World regulatory domain updated:
[   21.663925] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   21.663928] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   21.663931] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   21.663933] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   21.663936] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   21.663938] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   21.916151] input: HDA Intel HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   21.916375] input: HDA Intel Front Headphone Surround as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   21.916513] input: HDA Intel Front Headphone Front as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   22.009790] init: failsafe main process (571) killed by TERM signal
[   23.588748] type=1400 audit(1403453481.066:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cups-browsed" pid=756 comm="apparmor_parser"
[   24.991916] iwl3945 0000:0c:00.0: loaded firmware version 15.32.2.9
[   25.064280] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   25.064674] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   25.067327] tg3 0000:09:00.0: irq 47 for MSI/MSI-X
[   25.099324] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   25.099735] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   25.312787] type=1400 audit(1403453482.790:12): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=875 comm="apparmor_parser"
[   25.312798] type=1400 audit(1403453482.790:13): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=875 comm="apparmor_parser"
[   25.312806] type=1400 audit(1403453482.790:14): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=875 comm="apparmor_parser"
[   25.313412] type=1400 audit(1403453482.790:15): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=875 comm="apparmor_parser"
[   25.313419] type=1400 audit(1403453482.790:16): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=875 comm="apparmor_parser"
[   25.313724] type=1400 audit(1403453482.790:17): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=875 comm="apparmor_parser"
[   25.516079] type=1400 audit(1403453482.994:18): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/telepathy/mission-control-5" pid=878 comm="apparmor_parser"
[   25.516089] type=1400 audit(1403453482.994:19): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/telepathy/telepathy-*" pid=878 comm="apparmor_parser"
[   25.516096] type=1400 audit(1403453482.994:20): apparmor="STATUS" operation="profile_load" profile="unconfined" name="pxgsettings" pid=878 comm="apparmor_parser"
[   25.516102] type=1400 audit(1403453482.994:21): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=878 comm="apparmor_parser"

```

---

### Post by Gyokuro on 2014-06-22
Hi

Is this always or sometime as your dmesg do not show a problem and I think at the moment it's a trial and error problem but at the moment I can only suggest to install **bootchart** and **pybootchartgui** to monitor the whole boot process.

- HTH

---

### Post by varun-10 on 2014-06-23
sometimes b/w those lines I get these type of messages

```

[    4.082983] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[    4.082988] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[    4.150110] usb 3-2.1: new full-speed USB device number 3 using uhci_hcd
[    4.158383] random: nonblocking pool is initialized
[    4.184872] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[    4.184876] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[    4.276102] usb 3-2.1: New USB device found, idVendor=413c, idProduct=8126
[    4.276109] usb 3-2.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    4.276114] usb 3-2.1: Product: BCM2045
[    4.276119] usb 3-2.1: Manufacturer: Broadcom Corp
[    4.354101] usb 3-2.2: new full-speed USB device number 4 using uhci_hcd
[    4.484087] usb 3-2.2: New USB device found, idVendor=0a5c, idProduct=4502
[    4.484094] usb 3-2.2: New USB device strings: Mfr=1, Product=0, SerialNumber=0
[    4.484100] usb 3-2.2: Manufacturer: Broadcom Corp
[    4.561102] usb 3-2.3: new full-speed USB device number 5 using uhci_hcd
[    4.599882] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[    4.599887] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[    4.691095] usb 3-2.3: New USB device found, idVendor=0a5c, idProduct=4503
[    4.691100] usb 3-2.3: New USB device strings: Mfr=1, Product=0, SerialNumber=0
[    4.691103] usb 3-2.3: Manufacturer: Broadcom Corp
[    4.811745] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[    4.811752] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[    5.112148] usb 3-2: USB disconnect, device number 2
[    5.112157] usb 3-2.1: USB disconnect, device number 3
[    5.112531] usb 3-2.2: USB disconnect, device number 4
[    5.112658] usb 3-2.3: USB disconnect, device number 5
[    5.199146] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[    5.199151] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[    5.215619] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[    5.215624] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[    5.598180] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[    5.598188] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[    5.636072] usb 3-2: new full-speed USB device number 6 using uhci_hcd
[    5.815091] usb 3-2: New USB device found, idVendor=0a5c, idProduct=4500
[    5.815097] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    5.815100] usb 3-2: Product: BCM2045B2
[    5.815103] usb 3-2: Manufacturer: Broadcom
[    5.817134] hub 3-2:1.0: USB hub found
[    5.819105] hub 3-2:1.0: 3 ports detected
[    6.053858] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[    6.053863] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[    6.102077] usb 3-2.1: new full-speed USB device number 7 using uhci_hcd
[    6.230090] usb 3-2.1: New USB device found, idVendor=413c, idProduct=8126
[    6.230097] usb 3-2.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    6.230102] usb 3-2.1: Product: BCM2045
[    6.230107] usb 3-2.1: Manufacturer: Broadcom Corp
[    6.278620] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[    6.278627] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[    6.308140] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[    6.308144] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[    6.310080] usb 3-2.2: new full-speed USB device number 8 using uhci_hcd
[    6.385572] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[    6.385577] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[    6.402828] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[    6.402835] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[    6.437482] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[    6.437489] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[    6.440078] usb 3-2.2: New USB device found, idVendor=0a5c, idProduct=4502
[    6.440084] usb 3-2.2: New USB device strings: Mfr=1, Product=0, SerialNumber=0
[    6.440089] usb 3-2.2: Manufacturer: Broadcom Corp
[    6.518101] usb 3-2.3: new full-speed USB device number 9 using uhci_hcd
[    6.651092] usb 3-2.3: New USB device found, idVendor=0a5c, idProduct=4503
[    6.651099] usb 3-2.3: New USB device strings: Mfr=1, Product=0, SerialNumber=0
[    6.651105] usb 3-2.3: Manufacturer: Broadcom Corp
[    6.983490] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[    6.983497] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[    7.840178] usb 3-2: USB disconnect, device number 6
[    7.840185] usb 3-2.1: USB disconnect, device number 7
[    7.840585] usb 3-2.2: USB disconnect, device number 8
[    7.840750] usb 3-2.3: USB disconnect, device number 9
[    8.036979] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[    8.036987] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[    8.091935] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[    8.091942] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[    8.313182] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[    8.313190] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[    8.464094] usb 3-2: new full-speed USB device number 10 using uhci_hcd
[    8.492467] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[    8.492473] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[    8.642076] usb 3-2: New USB device found, idVendor=0a5c, idProduct=4500
[    8.642082] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    8.642088] usb 3-2: Product: BCM2045B2
[    8.642092] usb 3-2: Manufacturer: Broadcom
[    8.644132] hub 3-2:1.0: USB hub found
[    8.646068] hub 3-2:1.0: 3 ports detected
[    8.926054] usb 3-2.1: new full-speed USB device number 11 using uhci_hcd
[    9.053072] usb 3-2.1: New USB device found, idVendor=413c, idProduct=8126
[    9.053076] usb 3-2.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    9.053079] usb 3-2.1: Product: BCM2045
[    9.053082] usb 3-2.1: Manufacturer: Broadcom Corp
[    9.130081] usb 3-2.2: new full-speed USB device number 12 using uhci_hcd
[    9.260084] usb 3-2.2: New USB device found, idVendor=0a5c, idProduct=4502
[    9.260090] usb 3-2.2: New USB device strings: Mfr=1, Product=0, SerialNumber=0
[    9.260095] usb 3-2.2: Manufacturer: Broadcom Corp
[    9.338081] usb 3-2.3: new full-speed USB device number 13 using uhci_hcd
[    9.372983] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[    9.372986] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[    9.466970] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[    9.466974] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[    9.468075] usb 3-2.3: New USB device found, idVendor=0a5c, idProduct=4503
[    9.468079] usb 3-2.3: New USB device strings: Mfr=1, Product=0, SerialNumber=0
[    9.468082] usb 3-2.3: Manufacturer: Broadcom Corp
[    9.772410] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[    9.772413] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[    9.812509] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[    9.812513] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[   10.816113] usb 3-2: USB disconnect, device number 10
[   10.816118] usb 3-2.1: USB disconnect, device number 11
[   10.816488] usb 3-2.2: USB disconnect, device number 12
[   10.816654] usb 3-2.3: USB disconnect, device number 13
[   11.285943] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[   11.285950] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[   11.300445] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[   11.300449] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[   13.406247] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[   13.406254] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[   13.494887] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[   13.494893] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[   13.581858] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[   13.581863] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[   13.836088] usb 3-2: new full-speed USB device number 14 using uhci_hcd
[   13.914939] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[   13.914943] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[   14.009211] usb 3-2: New USB device found, idVendor=0a5c, idProduct=4500
[   14.009218] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[   14.009223] usb 3-2: Product: BCM2045B2
[   14.009228] usb 3-2: Manufacturer: Broadcom
[   14.011266] hub 3-2:1.0: USB hub found
[   14.013198] hub 3-2:1.0: 3 ports detected
[   14.293188] usb 3-2.1: new full-speed USB device number 15 using uhci_hcd
[   14.419213] usb 3-2.1: New USB device found, idVendor=413c, idProduct=8126
[   14.419220] usb 3-2.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[   14.419225] usb 3-2.1: Product: BCM2045
[   14.419230] usb 3-2.1: Manufacturer: Broadcom Corp
[   14.424787] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[   14.424793] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[   14.482411] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[   14.482416] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[   14.501221] usb 3-2.2: new full-speed USB device number 16 using uhci_hcd
[   14.633214] usb 3-2.2: New USB device found, idVendor=0a5c, idProduct=4502
[   14.633221] usb 3-2.2: New USB device strings: Mfr=1, Product=0, SerialNumber=0
[   14.633226] usb 3-2.2: Manufacturer: Broadcom Corp
[   14.709189] usb 3-2.3: new full-speed USB device number 17 using uhci_hcd
[   14.713359] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[   14.713365] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[   14.840219] usb 3-2.3: New USB device found, idVendor=0a5c, idProduct=4503
[   14.840225] usb 3-2.3: New USB device strings: Mfr=1, Product=0, SerialNumber=0
[   14.840231] usb 3-2.3: Manufacturer: Broadcom Corp
[   15.308824] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[   15.308832] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.

```

whole of it is -

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.13.0-29-generic (buildd@brownie) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #53-Ubuntu SMP Wed Jun 4 21:02:19 UTC 2014 (Ubuntu 3.13.0-29.53-generic 3.13.11.2)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009efff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009f000-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000007f66d7ff] usable
[    0.000000] BIOS-e820: [mem 0x000000007f66d800-0x000000007fffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec0ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed18000-0x00000000fed1bfff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed20000-0x00000000fed8ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000feda0000-0x00000000feda5fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee0ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffe00000-0x00000000ffffffff] reserved
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.4 present.
[    0.000000] DMI: Dell Inc. XPS M1330                       /0N6705, BIOS A12 07/08/2008
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0x7f66d max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 07F800000 mask FFF800000 uncachable
[    0.000000]   2 base 07F700000 mask FFFF00000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2040MB, range: 8MB, type UC
[    0.000000] reg 2, base: 2039MB, range: 1MB, type UC
[    0.000000] total RAM covered: 2039M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 16M     num_reg: 3      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2039MB, range: 1MB, type UC
[    0.000000] reg 2, base: 2040MB, range: 8MB, type UC
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] initial memory mapped: [mem 0x00000000-0x01ffffff]
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x37800000-0x379fffff]
[    0.000000]  [mem 0x37800000-0x379fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x34000000-0x377fffff]
[    0.000000]  [mem 0x34000000-0x377fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0x33ffffff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x33ffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x37a00000-0x37bfdfff]
[    0.000000]  [mem 0x37a00000-0x37bfdfff] page 4k
[    0.000000] BRK [0x01b8c000, 0x01b8cfff] PGTABLE
[    0.000000] RAMDISK: [mem 0x35c56000-0x36e22fff]
[    0.000000] ACPI: RSDP 000fbbf0 000024 (v02 DELL  )
[    0.000000] ACPI: XSDT 7f66f200 00005C (v01 DELL    M08     27D80708 ASL  00000061)
[    0.000000] ACPI: FACP 7f66f09c 0000F4 (v04 DELL    M08     27D80708 ASL  00000061)
[    0.000000] ACPI: DSDT 7f66f800 005733 (v02 INT430 SYSFexxx 00001001 INTL 20050624)
[    0.000000] ACPI: FACS 7f67e000 000040
[    0.000000] ACPI: HPET 7f66f300 000038 (v01 DELL    M08     00000001 ASL  00000061)
[    0.000000] ACPI: APIC 7f66f400 000068 (v01 DELL    M08     27D80708 ASL  00000047)
[    0.000000] ACPI: MCFG 7f66f3c0 00003E (v16 DELL    M08     27D80708 ASL  00000061)
[    0.000000] ACPI: SLIC 7f66f49c 000176 (v01 DELL    M08     27D80708 ASL  00000061)
[    0.000000] ACPI: BOOT 7f66efc0 000028 (v01 DELL    M08     27D80708 ASL  00000061)
[    0.000000] ACPI: SSDT 7f66d9bc 0004CC (v01  PmRef    CpuPm 00003000 INTL 20050624)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1146MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] BRK [0x01b8d000, 0x01b8dfff] PGTABLE
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   Normal   [mem 0x01000000-0x37bfdfff]
[    0.000000]   HighMem  [mem 0x37bfe000-0x7f66cfff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009efff]
[    0.000000]   node   0: [mem 0x00100000-0x7f66cfff]
[    0.000000] On node 0 totalpages: 521739
[    0.000000] free_area_init_node: node 0, pgdat c1995100, node_mem_map f4c66020
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3998 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 224254 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2293 pages used for memmap
[    0.000000]   HighMem zone: 293487 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] smpboot: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000fffff]
[    0.000000] e820: [mem 0x80000000-0xf7ffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @f7bd6000 s36096 r0 d21248 u57344
[    0.000000] pcpu-alloc: s36096 r0 d21248 u57344 alloc=14*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519955
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-29-generic root=UUID=95e35aad-c2df-429e-a9c5-e2bec97376a4 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 4174688 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:0007f66d)
[    0.000000] Memory: 2035464K/2086956K available (6522K kernel code, 639K rwdata, 2756K rodata, 872K init, 924K bss, 51492K reserved, 1173948K highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff14000 - 0xfffff000   ( 940 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc19b2000 - 0xc1a8c000   ( 872 kB)
[    0.000000]       .data : 0xc165ee72 - 0xc19b1d80   (3403 kB)
[    0.000000]       .text : 0xc1000000 - 0xc165ee72   (6523 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=8 to nr_cpu_ids=2.
[    0.000000] NR_IRQS:2304 nr_irqs:512 16
[    0.000000] CPU 0 irqstacks, hard=f7008000 soft=f700a000
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 1994.922 MHz processor
[    0.004002] Calibrating delay loop (skipped), value calculated using timer frequency.. 3989.84 BogoMIPS (lpj=7979688)
[    0.004006] pid_max: default: 32768 minimum: 301
[    0.004041] Security Framework initialized
[    0.004063] AppArmor: AppArmor initialized
[    0.004065] Yama: becoming mindful.
[    0.004121] Mount-cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.004124] Mountpoint-cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.004404] Initializing cgroup subsys memory
[    0.004413] Initializing cgroup subsys devices
[    0.004417] Initializing cgroup subsys freezer
[    0.004420] Initializing cgroup subsys blkio
[    0.004422] Initializing cgroup subsys perf_event
[    0.004426] Initializing cgroup subsys hugetlb
[    0.004457] CPU: Physical Processor ID: 0
[    0.004459] CPU: Processor Core ID: 0
[    0.004463] mce: CPU supports 6 MCE banks
[    0.004472] CPU0: Thermal monitoring enabled (TM2)
[    0.004485] Last level iTLB entries: 4KB 128, 2MB 4, 4MB 4
[    0.004485] Last level dTLB entries: 4KB 256, 2MB 0, 4MB 32
[    0.004485] tlb_flushall_shift: -1
[    0.004831] Freeing SMP alternatives memory: 32K (c1a8c000 - c1a94000)
[    0.008846] ACPI: Core revision 20131115
[    0.012437] ACPI: All ACPI Tables successfully acquired
[    0.014088] ftrace: allocating 27749 entries in 55 pages
[    0.024108] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.024580] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.066348] smpboot: CPU0: Intel(R) Core(TM)2 Duo CPU     T7250  @ 2.00GHz (fam: 06, model: 0f, stepping: 0d)
[    0.068000] Performance Events: PEBS fmt0+, 4-deep LBR, Core2 events, Intel PMU driver.
[    0.068000] perf_event_intel: PEBS disabled due to CPU errata
[    0.068000] ... version:                2
[    0.068000] ... bit width:              40
[    0.068000] ... generic registers:      2
[    0.068000] ... value mask:             000000ffffffffff
[    0.068000] ... max period:             000000007fffffff
[    0.068000] ... fixed-purpose events:   3
[    0.068000] ... event mask:             0000000700000003
[    0.069446] CPU 1 irqstacks, hard=f70ec000 soft=f70ee000
[    0.069449] x86: Booting SMP configuration:
[    0.008000] Initializing CPU#1
[    0.069451] .... node  #0, CPUs:      #1
[    0.082525] x86: Booted up 1 node, 2 CPUs
[    0.082529] smpboot: Total of 2 processors activated (7979.68 BogoMIPS)
[    0.082624] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.084059] devtmpfs: initialized
[    0.084275] EVM: security.selinux
[    0.084277] EVM: security.SMACK64
[    0.084279] EVM: security.ima
[    0.084281] EVM: security.capability
[    0.085732] pinctrl core: initialized pinctrl subsystem
[    0.085826] regulator-dummy: no parameters
[    0.085869] RTC time: 12:18:37, date: 06/23/14
[    0.085920] NET: Registered protocol family 16
[    0.086118] EISA bus registered
[    0.086120] cpuidle: using governor ladder
[    0.086122] cpuidle: using governor menu
[    0.086219] ACPI: bus type PCI registered
[    0.086221] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.086306] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.086309] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.086311] PCI: Using MMCONFIG for extended config space
[    0.086313] PCI: Using configuration type 1 for base access
[    0.086326] dmi type 0xB1 record - unknown flag
[    0.086326] bio: create slab <bio-0> at 0
[    0.088001] ACPI: Added _OSI(Module Device)
[    0.088001] ACPI: Added _OSI(Processor Device)
[    0.088001] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.088001] ACPI: Added _OSI(Processor Aggregator Device)
[    0.100809] ACPI: SSDT 7f67e080 000043 (v01  LMPWR  DELLLOM 00001001 INTL 20050624)
[    0.101135] ACPI: Dynamic OEM Table Load:
[    0.101138] ACPI: SSDT   (null) 000043 (v01  LMPWR  DELLLOM 00001001 INTL 20050624)
[    0.101453] ACPI: SSDT 7f66e4f2 000286 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.101797] ACPI: Dynamic OEM Table Load:
[    0.101800] ACPI: SSDT   (null) 000286 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.101937] ACPI: SSDT 7f66de88 0005E5 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.102262] ACPI: Dynamic OEM Table Load:
[    0.102265] ACPI: SSDT   (null) 0005E5 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.102530] ACPI: SSDT 7f66e778 0000C4 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.102865] ACPI: Dynamic OEM Table Load:
[    0.102868] ACPI: SSDT   (null) 0000C4 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.102956] ACPI: SSDT 7f66e46d 000085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.103281] ACPI: Dynamic OEM Table Load:
[    0.103284] ACPI: SSDT   (null) 000085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.103510] ACPI: Interpreter enabled
[    0.103523] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20131115/hwxface-580)
[    0.103529] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)
[    0.103545] ACPI: (supports S0 S3 S4 S5)
[    0.103548] ACPI: Using IOAPIC for interrupt routing
[    0.103579] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.103788] ACPI: No dock devices found.
[    0.152755] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.152762] acpi PNP0A03:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.152769] acpi PNP0A03:00: _OSC failed (AE_NOT_FOUND); disabling ASPM
[    0.175683] acpi PNP0A03:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-3f] only partially covers this bridge
[    0.175967] PCI host bridge to bus 0000:00
[    0.175971] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.175975] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.175978] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.175983] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.175986] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000dffff]
[    0.175989] pci_bus 0000:00: root bus resource [mem 0x80000000-0xf7ffffff]
[    0.175992] pci_bus 0000:00: root bus resource [mem 0xfc000000-0xfebfffff]
[    0.175995] pci_bus 0000:00: root bus resource [mem 0xfec10000-0xfecfffff]
[    0.176003] pci_bus 0000:00: root bus resource [mem 0xfed1c000-0xfed1ffff]
[    0.176006] pci_bus 0000:00: root bus resource [mem 0xfed90000-0xfed9ffff]
[    0.176008] pci_bus 0000:00: root bus resource [mem 0xfeda7000-0xfedfffff]
[    0.176011] pci_bus 0000:00: root bus resource [mem 0xfee10000-0xff9fffff]
[    0.176014] pci_bus 0000:00: root bus resource [mem 0xffc00000-0xffdfffff]
[    0.176026] pci 0000:00:00.0: [8086:2a00] type 00 class 0x060000
[    0.176166] pci 0000:00:02.0: [8086:2a02] type 00 class 0x030000
[    0.176183] pci 0000:00:02.0: reg 0x10: [mem 0xfea00000-0xfeafffff 64bit]
[    0.176194] pci 0000:00:02.0: reg 0x18: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.176202] pci 0000:00:02.0: reg 0x20: [io  0xefe8-0xefef]
[    0.176333] pci 0000:00:02.1: [8086:2a03] type 00 class 0x038000
[    0.176348] pci 0000:00:02.1: reg 0x10: [mem 0xfeb00000-0xfebfffff 64bit]
[    0.176535] pci 0000:00:1a.0: [8086:2834] type 00 class 0x0c0300
[    0.176598] pci 0000:00:1a.0: reg 0x20: [io  0x6f20-0x6f3f]
[    0.178508] pci 0000:00:1a.0: System wakeup disabled by ACPI
[    0.178553] pci 0000:00:1a.1: [8086:2835] type 00 class 0x0c0300
[    0.178616] pci 0000:00:1a.1: reg 0x20: [io  0x6f00-0x6f1f]
[    0.180311] pci 0000:00:1a.1: System wakeup disabled by ACPI
[    0.180374] pci 0000:00:1a.7: [8086:283a] type 00 class 0x0c0320
[    0.180403] pci 0000:00:1a.7: reg 0x10: [mem 0xfed1c400-0xfed1c7ff]
[    0.180521] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.182393] pci 0000:00:1a.7: System wakeup disabled by ACPI
[    0.182453] pci 0000:00:1b.0: [8086:284b] type 00 class 0x040300
[    0.182480] pci 0000:00:1b.0: reg 0x10: [mem 0xfe9fc000-0xfe9fffff 64bit]
[    0.182595] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.182680] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    0.182729] pci 0000:00:1c.0: [8086:283f] type 01 class 0x060400
[    0.182850] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.182936] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.182990] pci 0000:00:1c.1: [8086:2841] type 01 class 0x060400
[    0.183111] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.183197] pci 0000:00:1c.1: System wakeup disabled by ACPI
[    0.183248] pci 0000:00:1c.3: [8086:2845] type 01 class 0x060400
[    0.183368] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.183454] pci 0000:00:1c.3: System wakeup disabled by ACPI
[    0.183503] pci 0000:00:1c.5: [8086:2849] type 01 class 0x060400
[    0.183622] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.183708] pci 0000:00:1c.5: System wakeup disabled by ACPI
[    0.183755] pci 0000:00:1d.0: [8086:2830] type 00 class 0x0c0300
[    0.184038] pci 0000:00:1d.0: reg 0x20: [io  0x6f80-0x6f9f]
[    0.188312] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.188359] pci 0000:00:1d.1: [8086:2831] type 00 class 0x0c0300
[    0.188421] pci 0000:00:1d.1: reg 0x20: [io  0x6f60-0x6f7f]
[    0.190325] pci 0000:00:1d.1: System wakeup disabled by ACPI
[    0.190372] pci 0000:00:1d.2: [8086:2832] type 00 class 0x0c0300
[    0.190435] pci 0000:00:1d.2: reg 0x20: [io  0x6f40-0x6f5f]
[    0.192312] pci 0000:00:1d.2: System wakeup disabled by ACPI
[    0.192373] pci 0000:00:1d.7: [8086:2836] type 00 class 0x0c0320
[    0.192401] pci 0000:00:1d.7: reg 0x10: [mem 0xfed1c000-0xfed1c3ff]
[    0.192520] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.194393] pci 0000:00:1d.7: System wakeup disabled by ACPI
[    0.194444] pci 0000:00:1e.0: [8086:2448] type 01 class 0x060401
[    0.194599] pci 0000:00:1e.0: System wakeup disabled by ACPI
[    0.194649] pci 0000:00:1f.0: [8086:2815] type 00 class 0x060100
[    0.194773] pci 0000:00:1f.0: address space collision: [io  0x1000-0x107f] conflicts with ACPI CPU throttle [??? 0x00001010-0x00001015 flags 0x80000000]
[    0.194781] pci 0000:00:1f.0: quirk: [io  0x1080-0x10bf] claimed by ICH6 GPIO
[    0.194786] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0900 (mask 007f)
[    0.194793] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 0c80 (mask 003f)
[    0.194942] pci 0000:00:1f.1: [8086:2850] type 00 class 0x01018a
[    0.194961] pci 0000:00:1f.1: reg 0x10: [io  0x01f0-0x01f7]
[    0.194975] pci 0000:00:1f.1: reg 0x14: [io  0x03f4-0x03f7]
[    0.194989] pci 0000:00:1f.1: reg 0x18: [io  0x0170-0x0177]
[    0.195002] pci 0000:00:1f.1: reg 0x1c: [io  0x0374-0x0377]
[    0.195016] pci 0000:00:1f.1: reg 0x20: [io  0x6fa0-0x6faf]
[    0.195153] pci 0000:00:1f.2: [8086:2828] type 00 class 0x01018f
[    0.195177] pci 0000:00:1f.2: reg 0x10: [io  0x6eb0-0x6eb7]
[    0.195191] pci 0000:00:1f.2: reg 0x14: [io  0x6eb8-0x6ebb]
[    0.195204] pci 0000:00:1f.2: reg 0x18: [io  0x6ec0-0x6ec7]
[    0.195218] pci 0000:00:1f.2: reg 0x1c: [io  0x6ec8-0x6ecb]
[    0.195232] pci 0000:00:1f.2: reg 0x20: [io  0x6ee0-0x6eef]
[    0.195245] pci 0000:00:1f.2: reg 0x24: [io  0xeff0-0xefff]
[    0.195297] pci 0000:00:1f.2: PME# supported from D3hot
[    0.195408] pci 0000:00:1f.3: [8086:283e] type 00 class 0x0c0500
[    0.195428] pci 0000:00:1f.3: reg 0x10: [mem 0xfe9fbf00-0xfe9fbfff]
[    0.195474] pci 0000:00:1f.3: reg 0x20: [io  0x10c0-0x10df]
[    0.195697] pci 0000:00:1c.0: PCI bridge to [bus 0b]
[    0.196043] pci 0000:0c:00.0: [8086:4222] type 00 class 0x028000
[    0.196102] pci 0000:0c:00.0: reg 0x10: [mem 0xfe8ff000-0xfe8fffff]
[    0.196534] pci 0000:0c:00.0: PME# supported from D0 D3hot D3cold
[    0.196649] pci 0000:0c:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.196689] pci 0000:00:1c.1: PCI bridge to [bus 0c]
[    0.196699] pci 0000:00:1c.1:   bridge window [mem 0xfe800000-0xfe8fffff]
[    0.196816] acpiphp: Slot [1] registered
[    0.196826] pci 0000:00:1c.3: PCI bridge to [bus 0d-0e]
[    0.196832] pci 0000:00:1c.3:   bridge window [io  0xd000-0xdfff]
[    0.196838] pci 0000:00:1c.3:   bridge window [mem 0xfe600000-0xfe7fffff]
[    0.196847] pci 0000:00:1c.3:   bridge window [mem 0xf0000000-0xf01fffff 64bit pref]
[    0.197039] pci 0000:09:00.0: [14e4:1713] type 00 class 0x020000
[    0.197113] pci 0000:09:00.0: reg 0x10: [mem 0xfe5f0000-0xfe5fffff 64bit]
[    0.197548] pci 0000:09:00.0: PME# supported from D3hot D3cold
[    0.197727] pci 0000:00:1c.5: PCI bridge to [bus 09]
[    0.197736] pci 0000:00:1c.5:   bridge window [mem 0xfe500000-0xfe5fffff]
[    0.197832] pci 0000:03:01.0: [1180:0832] type 00 class 0x0c0010
[    0.197849] pci 0000:03:01.0: proprietary Ricoh MMC controller disabled (via firewire function)
[    0.197852] pci 0000:03:01.0: MMC cards are now supported by standard SDHCI controller
[    0.197871] pci 0000:03:01.0: reg 0x10: [mem 0xfe4ff800-0xfe4fffff]
[    0.197982] pci 0000:03:01.0: supports D1 D2
[    0.197985] pci 0000:03:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.198054] pci 0000:03:01.1: [1180:0822] type 00 class 0x080501
[    0.198080] pci 0000:03:01.1: reg 0x10: [mem 0xfe4ff400-0xfe4ff4ff]
[    0.198188] pci 0000:03:01.1: supports D1 D2
[    0.198191] pci 0000:03:01.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.198255] pci 0000:03:01.2: [1180:0592] type 00 class 0x088000
[    0.198280] pci 0000:03:01.2: reg 0x10: [mem 0xfe4ff600-0xfe4ff6ff]
[    0.198390] pci 0000:03:01.2: supports D1 D2
[    0.198392] pci 0000:03:01.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.198459] pci 0000:03:01.3: [1180:0852] type 00 class 0x088000
[    0.198484] pci 0000:03:01.3: reg 0x10: [mem 0xfe4ff700-0xfe4ff7ff]
[    0.198593] pci 0000:03:01.3: supports D1 D2
[    0.198595] pci 0000:03:01.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.198715] pci 0000:00:1e.0: PCI bridge to [bus 03] (subtractive decode)
[    0.198724] pci 0000:00:1e.0:   bridge window [mem 0xfe400000-0xfe4fffff]
[    0.198734] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.198737] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.198740] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.198743] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.198746] pci 0000:00:1e.0:   bridge window [mem 0x80000000-0xf7ffffff] (subtractive decode)
[    0.198748] pci 0000:00:1e.0:   bridge window [mem 0xfc000000-0xfebfffff] (subtractive decode)
[    0.198751] pci 0000:00:1e.0:   bridge window [mem 0xfec10000-0xfecfffff] (subtractive decode)
[    0.198754] pci 0000:00:1e.0:   bridge window [mem 0xfed1c000-0xfed1ffff] (subtractive decode)
[    0.198757] pci 0000:00:1e.0:   bridge window [mem 0xfed90000-0xfed9ffff] (subtractive decode)
[    0.198760] pci 0000:00:1e.0:   bridge window [mem 0xfeda7000-0xfedfffff] (subtractive decode)
[    0.198763] pci 0000:00:1e.0:   bridge window [mem 0xfee10000-0xff9fffff] (subtractive decode)
[    0.198766] pci 0000:00:1e.0:   bridge window [mem 0xffc00000-0xffdfffff] (subtractive decode)
[    0.198816] pci_bus 0000:00: on NUMA node 0
[    0.199400] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[    0.199512] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *10
[    0.199621] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 11) *4
[    0.199733] ACPI: PCI Interrupt Link [LNKD] (IRQs *5 7 9 10 11)
[    0.199844] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.199957] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.200077] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
[    0.200176] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.200415] ACPI: Enabled 4 GPEs in block 00 to 1F
[    0.200445] ACPI: \_SB_.PCI0: notify handler is installed
[    0.200476] Found 1 acpi root devices
[    0.204987] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.204987] vgaarb: loaded
[    0.204987] vgaarb: bridge control possible 0000:00:02.0
[    0.204987] SCSI subsystem initialized
[    0.204993] libata version 3.00 loaded.
[    0.204993] ACPI: bus type USB registered
[    0.204993] usbcore: registered new interface driver usbfs
[    0.204993] usbcore: registered new interface driver hub
[    0.204993] usbcore: registered new device driver usb
[    0.204993] PCI: Using ACPI for IRQ routing
[    0.205823] PCI: pci_cache_line_size set to 64 bytes
[    0.205935] e820: reserve RAM buffer [mem 0x0009f000-0x0009ffff]
[    0.205937] e820: reserve RAM buffer [mem 0x7f66d800-0x7fffffff]
[    0.206045] NetLabel: Initializing
[    0.206047] NetLabel:  domain hash size = 128
[    0.206049] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.206068] NetLabel:  unlabeled traffic allowed by default
[    0.208113] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.208120] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.208126] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.208126] Switched to clocksource hpet
[    0.217771] AppArmor: AppArmor Filesystem Enabled
[    0.217815] pnp: PnP ACPI init
[    0.217836] ACPI: bus type PNP registered
[    0.217942] pnp 00:00: Plug and Play ACPI device, IDs PNP0f13 (active)
[    0.217991] pnp 00:01: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.218036] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.218082] pnp 00:03: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.218162] system 00:04: [io  0x0c80-0x0cff] could not be reserved
[    0.218167] system 00:04: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.218190] pnp 00:05: [dma 4]
[    0.218219] pnp 00:05: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.218264] pnp 00:06: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.218354] system 00:07: [mem 0xfed00000-0xfed003ff] has been reserved
[    0.218359] system 00:07: Plug and Play ACPI device, IDs PNP0103 PNP0c01 (active)
[    0.218541] pnp 00:08: disabling [io  0x1000-0x1005] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.218544] pnp 00:08: disabling [io  0x1008-0x100f] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.218592] system 00:08: [io  0x0900-0x097f] has been reserved
[    0.218596] system 00:08: [io  0x04d0-0x04d1] has been reserved
[    0.218600] system 00:08: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.218636] pnp 00:09: disabling [io  0x1006-0x1007] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.218639] pnp 00:09: disabling [io  0x100a-0x1059] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.218643] pnp 00:09: disabling [io  0x1060-0x107f] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.218646] pnp 00:09: disabling [io  0x1010-0x102f] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.218691] system 00:09: [io  0xf400-0xf4fe] has been reserved
[    0.218695] system 00:09: [io  0x1080-0x10bf] has been reserved
[    0.218698] system 00:09: [io  0x10c0-0x10df] has been reserved
[    0.218702] system 00:09: [io  0x0809] has been reserved
[    0.218706] system 00:09: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.231029] system 00:0a: [mem 0x00000000-0x0009efff] could not be reserved
[    0.231034] system 00:0a: [mem 0x0009f000-0x0009ffff] could not be reserved
[    0.231038] system 00:0a: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.231041] system 00:0a: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.231045] system 00:0a: [mem 0x00100000-0x7f66d7ff] could not be reserved
[    0.231048] system 00:0a: [mem 0x7f66d800-0x7f6fffff] has been reserved
[    0.231051] system 00:0a: [mem 0x7f700000-0x7f7fffff] has been reserved
[    0.231055] system 00:0a: [mem 0x7f700000-0x7fefffff] could not be reserved
[    0.231058] system 00:0a: [mem 0xffe00000-0xffffffff] has been reserved
[    0.231062] system 00:0a: [mem 0xffa00000-0xffbfffff] has been reserved
[    0.231065] system 00:0a: [mem 0xfec00000-0xfec0ffff] could not be reserved
[    0.231069] system 00:0a: [mem 0xfee00000-0xfee0ffff] has been reserved
[    0.231072] system 00:0a: [mem 0xfed20000-0xfed8ffff] has been reserved
[    0.231076] system 00:0a: [mem 0xfeda0000-0xfeda3fff] has been reserved
[    0.231079] system 00:0a: [mem 0xfeda4000-0xfeda4fff] has been reserved
[    0.231083] system 00:0a: [mem 0xfeda5000-0xfeda5fff] has been reserved
[    0.231086] system 00:0a: [mem 0xfeda6000-0xfeda6fff] has been reserved
[    0.231090] system 00:0a: [mem 0xfed18000-0xfed1bfff] has been reserved
[    0.231093] system 00:0a: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.231097] system 00:0a: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.231166] pnp: PnP ACPI: found 11 devices
[    0.231168] ACPI: bus type PNP unregistered
[    0.231172] PnPBIOS: Disabled by ACPI PNP
[    0.268562] pci 0000:00:1c.0: bridge window [io  0x1000-0x0fff] to [bus 0b] add_size 1000
[    0.268569] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 0b] add_size 200000
[    0.268573] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff] to [bus 0b] add_size 200000
[    0.268586] pci 0000:00:1c.1: bridge window [io  0x1000-0x0fff] to [bus 0c] add_size 1000
[    0.268589] pci 0000:00:1c.1: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 0c] add_size 200000
[    0.268612] pci 0000:00:1c.5: bridge window [io  0x1000-0x0fff] to [bus 09] add_size 1000
[    0.268615] pci 0000:00:1c.5: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 09] add_size 200000
[    0.268633] pci 0000:00:1f.0: BAR 13: [io  0x1000-0x107f] has bogus alignment
[    0.268638] pci 0000:00:1c.0: res[14]=[mem 0x00100000-0x000fffff] get_res_add_size add_size 200000
[    0.268641] pci 0000:00:1c.0: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.268645] pci 0000:00:1c.1: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.268648] pci 0000:00:1c.5: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.268651] pci 0000:00:1c.0: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.268654] pci 0000:00:1c.1: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.268657] pci 0000:00:1c.5: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.268663] pci 0000:00:1c.0: BAR 14: assigned [mem 0x80000000-0x801fffff]
[    0.268667] pci 0000:00:1c.0: BAR 15: assigned [mem 0x80200000-0x803fffff 64bit pref]
[    0.268672] pci 0000:00:1c.1: BAR 15: assigned [mem 0x80400000-0x805fffff 64bit pref]
[    0.268676] pci 0000:00:1c.5: BAR 15: assigned [mem 0x80600000-0x807fffff 64bit pref]
[    0.268680] pci 0000:00:1c.0: BAR 13: assigned [io  0x2000-0x2fff]
[    0.268684] pci 0000:00:1c.1: BAR 13: assigned [io  0x3000-0x3fff]
[    0.268688] pci 0000:00:1c.5: BAR 13: assigned [io  0x4000-0x4fff]
[    0.268692] pci 0000:00:1c.0: PCI bridge to [bus 0b]
[    0.268697] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.268704] pci 0000:00:1c.0:   bridge window [mem 0x80000000-0x801fffff]
[    0.268711] pci 0000:00:1c.0:   bridge window [mem 0x80200000-0x803fffff 64bit pref]
[    0.268720] pci 0000:00:1c.1: PCI bridge to [bus 0c]
[    0.268724] pci 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
[    0.268731] pci 0000:00:1c.1:   bridge window [mem 0xfe800000-0xfe8fffff]
[    0.268737] pci 0000:00:1c.1:   bridge window [mem 0x80400000-0x805fffff 64bit pref]
[    0.268746] pci 0000:00:1c.3: PCI bridge to [bus 0d-0e]
[    0.268750] pci 0000:00:1c.3:   bridge window [io  0xd000-0xdfff]
[    0.268758] pci 0000:00:1c.3:   bridge window [mem 0xfe600000-0xfe7fffff]
[    0.268764] pci 0000:00:1c.3:   bridge window [mem 0xf0000000-0xf01fffff 64bit pref]
[    0.268773] pci 0000:00:1c.5: PCI bridge to [bus 09]
[    0.268777] pci 0000:00:1c.5:   bridge window [io  0x4000-0x4fff]
[    0.268784] pci 0000:00:1c.5:   bridge window [mem 0xfe500000-0xfe5fffff]
[    0.268790] pci 0000:00:1c.5:   bridge window [mem 0x80600000-0x807fffff 64bit pref]
[    0.268799] pci 0000:00:1e.0: PCI bridge to [bus 03]
[    0.268807] pci 0000:00:1e.0:   bridge window [mem 0xfe400000-0xfe4fffff]
[    0.268820] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.268823] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.268826] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.268828] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.268831] pci_bus 0000:00: resource 8 [mem 0x80000000-0xf7ffffff]
[    0.268834] pci_bus 0000:00: resource 9 [mem 0xfc000000-0xfebfffff]
[    0.268837] pci_bus 0000:00: resource 10 [mem 0xfec10000-0xfecfffff]
[    0.268839] pci_bus 0000:00: resource 11 [mem 0xfed1c000-0xfed1ffff]
[    0.268842] pci_bus 0000:00: resource 12 [mem 0xfed90000-0xfed9ffff]
[    0.268845] pci_bus 0000:00: resource 13 [mem 0xfeda7000-0xfedfffff]
[    0.268848] pci_bus 0000:00: resource 14 [mem 0xfee10000-0xff9fffff]
[    0.268850] pci_bus 0000:00: resource 15 [mem 0xffc00000-0xffdfffff]
[    0.268853] pci_bus 0000:0b: resource 0 [io  0x2000-0x2fff]
[    0.268856] pci_bus 0000:0b: resource 1 [mem 0x80000000-0x801fffff]
[    0.268859] pci_bus 0000:0b: resource 2 [mem 0x80200000-0x803fffff 64bit pref]
[    0.268862] pci_bus 0000:0c: resource 0 [io  0x3000-0x3fff]
[    0.268865] pci_bus 0000:0c: resource 1 [mem 0xfe800000-0xfe8fffff]
[    0.268867] pci_bus 0000:0c: resource 2 [mem 0x80400000-0x805fffff 64bit pref]
[    0.268870] pci_bus 0000:0d: resource 0 [io  0xd000-0xdfff]
[    0.268873] pci_bus 0000:0d: resource 1 [mem 0xfe600000-0xfe7fffff]
[    0.268876] pci_bus 0000:0d: resource 2 [mem 0xf0000000-0xf01fffff 64bit pref]
[    0.268879] pci_bus 0000:09: resource 0 [io  0x4000-0x4fff]
[    0.268881] pci_bus 0000:09: resource 1 [mem 0xfe500000-0xfe5fffff]
[    0.268884] pci_bus 0000:09: resource 2 [mem 0x80600000-0x807fffff 64bit pref]
[    0.268887] pci_bus 0000:03: resource 1 [mem 0xfe400000-0xfe4fffff]
[    0.268890] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    0.268892] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
[    0.268895] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    0.268898] pci_bus 0000:03: resource 7 [mem 0x000d0000-0x000dffff]
[    0.268900] pci_bus 0000:03: resource 8 [mem 0x80000000-0xf7ffffff]
[    0.268903] pci_bus 0000:03: resource 9 [mem 0xfc000000-0xfebfffff]
[    0.268906] pci_bus 0000:03: resource 10 [mem 0xfec10000-0xfecfffff]
[    0.268909] pci_bus 0000:03: resource 11 [mem 0xfed1c000-0xfed1ffff]
[    0.268911] pci_bus 0000:03: resource 12 [mem 0xfed90000-0xfed9ffff]
[    0.268914] pci_bus 0000:03: resource 13 [mem 0xfeda7000-0xfedfffff]
[    0.268917] pci_bus 0000:03: resource 14 [mem 0xfee10000-0xff9fffff]
[    0.268920] pci_bus 0000:03: resource 15 [mem 0xffc00000-0xffdfffff]
[    0.268962] NET: Registered protocol family 2
[    0.269157] TCP established hash table entries: 8192 (order: 3, 32768 bytes)
[    0.269178] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.269208] TCP: Hash tables configured (established 8192 bind 8192)
[    0.269242] TCP: reno registered
[    0.269245] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.269254] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.269321] NET: Registered protocol family 1
[    0.269337] pci 0000:00:02.0: Boot video device
[    0.272213] PCI: CLS 64 bytes, default 64
[    0.272272] Trying to unpack rootfs image as initramfs...
[    0.688590] Freeing initrd memory: 18228K (f5c56000 - f6e23000)
[    0.688715] Simple Boot Flag at 0x79 set to 0x1
[    0.688874] microcode: CPU0 sig=0x6fd, pf=0x80, revision=0xa3
[    0.688880] microcode: CPU1 sig=0x6fd, pf=0x80, revision=0xa3
[    0.688965] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.688968] Scanning for low memory corruption every 60 seconds
[    0.689244] Initialise system trusted keyring
[    0.689299] audit: initializing netlink socket (disabled)
[    0.689316] type=2000 audit(1403525917.688:1): initialized
[    0.716352] bounce pool size: 64 pages
[    0.716366] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.718092] zbud: loaded
[    0.718169] VFS: Disk quotas dquot_6.5.2
[    0.718227] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.718839] fuse init (API version 7.22)
[    0.718947] msgmni has been set to 1718
[    0.719023] Key type big_key registered
[    0.719526] Key type asymmetric registered
[    0.719529] Asymmetric key parser 'x509' registered
[    0.719571] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.719610] io scheduler noop registered
[    0.719613] io scheduler deadline registered (default)
[    0.719651] io scheduler cfq registered
[    0.719780] pcieport 0000:00:1c.0: device [8086:283f] has invalid IRQ; check vendor BIOS
[    0.720065] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.720152] pcieport 0000:00:1c.1: device [8086:2841] has invalid IRQ; check vendor BIOS
[    0.720377] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.720458] pcieport 0000:00:1c.3: device [8086:2845] has invalid IRQ; check vendor BIOS
[    0.720680] pcieport 0000:00:1c.3: irq 42 for MSI/MSI-X
[    0.720760] pcieport 0000:00:1c.5: device [8086:2849] has invalid IRQ; check vendor BIOS
[    0.720981] pcieport 0000:00:1c.5: irq 43 for MSI/MSI-X
[    0.721092] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.721114] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.721172] vesafb: mode is 1024x768x32, linelength=4096, pages=0
[    0.721174] vesafb: scrolling: redraw
[    0.721177] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    0.721349] vesafb: framebuffer at 0xe0000000, mapped to 0xf8480000, using 3072k, total 3072k
[    0.745383] Console: switching to colour frame buffer device 128x48
[    0.769321] fb0: VESA VGA frame buffer device
[    0.769344] intel_idle: does not run on family 6 model 15
[    0.769353] ipmi message handler version 39.2
[    0.769457] ACPI: AC Adapter [AC] (off-line)
[    0.769590] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.770019] ACPI: Lid Switch [LID]
[    0.770065] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.770070] ACPI: Power Button [PBTN]
[    0.770116] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.770119] ACPI: Sleep Button [SBTN]
[    0.770255] Monitor-Mwait will be used to enter C-1 state
[    0.770261] Monitor-Mwait will be used to enter C-2 state
[    0.770266] Monitor-Mwait will be used to enter C-3 state
[    0.770270] tsc: Marking TSC unstable due to TSC halts in idle
[    0.770282] ACPI: acpi_idle registered with cpuidle
[    0.777201] thermal LNXTHERM:00: registered as thermal_zone0
[    0.777204] ACPI: Thermal Zone [THM] (40 C)
[    0.777240] GHES: HEST is not enabled!
[    0.777343] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.782508] isapnp: Scanning for PnP cards...
[    0.794141] Linux agpgart interface v0.103
[    0.794262] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
[    0.794307] agpgart-intel 0000:00:00.0: detected gtt size: 524288K total, 262144K mappable
[    0.794783] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    0.794906] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
[    0.796676] brd: module loaded
[    0.797568] loop: module loaded
[    0.797728] ata_piix 0000:00:1f.1: version 2.13
[    0.803046] scsi0 : ata_piix
[    0.803119] ACPI: Battery Slot [BAT0] (battery present)
[    0.803139] scsi1 : ata_piix
[    0.803181] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x6fa0 irq 14
[    0.803184] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x6fa8 irq 15
[    0.803407] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.803617] ata2: port disabled--ignoring
[    0.956610] scsi2 : ata_piix
[    0.956673] scsi3 : ata_piix
[    0.956723] ata3: SATA max UDMA/133 cmd 0x6eb0 ctl 0x6eb8 bmdma 0x6ee0 irq 17
[    0.956730] ata4: SATA max UDMA/133 cmd 0x6ec0 ctl 0x6ec8 bmdma 0x6ee8 irq 17
[    0.957134] libphy: Fixed MDIO Bus: probed
[    0.957267] tun: Universal TUN/TAP device driver, 1.6
[    0.957269] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.957392] PPP generic driver version 2.4.2
[    0.957439] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.957445] ehci-pci: EHCI PCI platform driver
[    0.957701] ehci-pci 0000:00:1a.7: EHCI Host Controller
[    0.957709] ehci-pci 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.957727] ehci-pci 0000:00:1a.7: debug port 1
[    0.961654] ehci-pci 0000:00:1a.7: cache line size of 64 is not supported
[    0.961677] ehci-pci 0000:00:1a.7: irq 22, io mem 0xfed1c400
[    0.968520] ata1.00: ATAPI: MATSHITA DVD+/-RW UJ-857G, Z111, max UDMA/33
[    0.972038] ehci-pci 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.972091] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.972095] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.972098] usb usb1: Product: EHCI Host Controller
[    0.972101] usb usb1: Manufacturer: Linux 3.13.0-29-generic ehci_hcd
[    0.972103] usb usb1: SerialNumber: 0000:00:1a.7
[    0.972227] hub 1-0:1.0: USB hub found
[    0.972238] hub 1-0:1.0: 4 ports detected
[    0.972657] ehci-pci 0000:00:1d.7: EHCI Host Controller
[    0.972663] ehci-pci 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.972680] ehci-pci 0000:00:1d.7: debug port 1
[    0.976577] ehci-pci 0000:00:1d.7: cache line size of 64 is not supported
[    0.976782] ehci-pci 0000:00:1d.7: irq 20, io mem 0xfed1c000
[    0.984401] ata1.00: configured for UDMA/33
[    0.988042] ehci-pci 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.988118] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    0.988121] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.988124] usb usb2: Product: EHCI Host Controller
[    0.988127] usb usb2: Manufacturer: Linux 3.13.0-29-generic ehci_hcd
[    0.988130] usb usb2: SerialNumber: 0000:00:1d.7
[    0.988243] hub 2-0:1.0: USB hub found
[    0.988252] hub 2-0:1.0: 6 ports detected
[    0.988540] ehci-platform: EHCI generic platform driver
[    0.988552] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.988554] ohci-pci: OHCI PCI platform driver
[    0.988569] ohci-platform: OHCI generic platform driver
[    0.988580] uhci_hcd: USB Universal Host Controller Interface driver
[    0.988805] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.988812] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.988842] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00006f20
[    0.988902] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    0.988905] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.988908] usb usb3: Product: UHCI Host Controller
[    0.988911] usb usb3: Manufacturer: Linux 3.13.0-29-generic uhci_hcd
[    0.988914] usb usb3: SerialNumber: 0000:00:1a.0
[    0.989027] hub 3-0:1.0: USB hub found
[    0.989036] hub 3-0:1.0: 2 ports detected
[    0.989367] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.989374] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.989417] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00006f00
[    0.989476] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    0.989479] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.989482] usb usb4: Product: UHCI Host Controller
[    0.989484] usb usb4: Manufacturer: Linux 3.13.0-29-generic uhci_hcd
[    0.989487] usb usb4: SerialNumber: 0000:00:1a.1
[    0.989606] hub 4-0:1.0: USB hub found
[    0.989615] hub 4-0:1.0: 2 ports detected
[    0.989948] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.989954] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    0.989983] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00006f80
[    0.990042] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    0.990045] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.990048] usb usb5: Product: UHCI Host Controller
[    0.990051] usb usb5: Manufacturer: Linux 3.13.0-29-generic uhci_hcd
[    0.990053] usb usb5: SerialNumber: 0000:00:1d.0
[    0.990167] hub 5-0:1.0: USB hub found
[    0.990176] hub 5-0:1.0: 2 ports detected
[    0.990509] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.990517] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    0.990546] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00006f60
[    0.990605] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
[    0.990609] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.990611] usb usb6: Product: UHCI Host Controller
[    0.990614] usb usb6: Manufacturer: Linux 3.13.0-29-generic uhci_hcd
[    0.990617] usb usb6: SerialNumber: 0000:00:1d.1
[    0.990726] hub 6-0:1.0: USB hub found
[    0.990734] hub 6-0:1.0: 2 ports detected
[    0.991062] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.991068] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    0.991097] uhci_hcd 0000:00:1d.2: irq 22, io base 0x00006f40
[    0.991153] usb usb7: New USB device found, idVendor=1d6b, idProduct=0001
[    0.991157] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.991159] usb usb7: Product: UHCI Host Controller
[    0.991162] usb usb7: Manufacturer: Linux 3.13.0-29-generic uhci_hcd
[    0.991165] usb usb7: SerialNumber: 0000:00:1d.2
[    0.991274] hub 7-0:1.0: USB hub found
[    0.991284] hub 7-0:1.0: 2 ports detected
[    0.991493] i8042: PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.995079] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.995085] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.995205] mousedev: PS/2 mouse device common for all mice
[    0.995378] rtc_cmos 00:02: RTC can wake from S4
[    0.995536] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.995577] rtc_cmos 00:02: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.995662] device-mapper: uevent: version 1.0.3
[    0.995729] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
[    0.995756] platform eisa.0: Probing EISA bus 0
[    0.995760] platform eisa.0: EISA: Cannot allocate resource for mainboard
[    0.995763] platform eisa.0: Cannot allocate resource for EISA slot 1
[    0.995766] platform eisa.0: Cannot allocate resource for EISA slot 2
[    0.995769] platform eisa.0: Cannot allocate resource for EISA slot 3
[    0.995772] platform eisa.0: Cannot allocate resource for EISA slot 4
[    0.995774] platform eisa.0: Cannot allocate resource for EISA slot 5
[    0.995777] platform eisa.0: Cannot allocate resource for EISA slot 6
[    0.995780] platform eisa.0: Cannot allocate resource for EISA slot 7
[    0.995783] platform eisa.0: Cannot allocate resource for EISA slot 8
[    0.995785] platform eisa.0: EISA: Detected 0 cards
[    0.995794] cpufreq-nforce2: No nForce2 chipset.
[    0.995799] ledtrig-cpu: registered to indicate activity on CPUs
[    0.995973] TCP: cubic registered
[    0.996120] NET: Registered protocol family 10
[    0.996362] NET: Registered protocol family 17
[    0.996375] Key type dns_resolver registered
[    0.996573] Using IPI No-Shortcut mode
[    0.996664] Loading compiled-in X.509 certificates
[    1.001046] Loaded X.509 cert 'Magrathea: Glacier signing key: 497ec33ede6aa573c29cd85a3d778ac2aeb3d36f'
[    1.001062] registered taskstats version 1
[    1.002433] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.004081] Key type trusted registered
[    1.006687] Key type encrypted registered
[    1.008935] AppArmor: AppArmor sha1 policy hashing enabled
[    1.008939] IMA: No TPM chip found, activating TPM-bypass!
[    1.009509] regulator-dummy: disabling
[    1.009560]   Magic number: 2:272:330
[    1.009600] tty tty51: hash matches
[    1.009676] rtc_cmos 00:02: setting system clock to 2014-06-23 12:18:38 UTC (1403525918)
[    1.010608] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.010610] EDD information not available.
[    1.010655] PM: Hibernation image not present or could not be loaded.
[    1.096858] isapnp: No Plug & Play device found
[    1.098744] scsi 0:0:0:0: CD-ROM            MATSHITA DVD+-RW UJ-857G  Z111 PQ: 0 ANSI: 5
[    1.101127] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda caddy
[    1.101131] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.101341] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.101480] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.178618] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[    1.178622] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[    1.184712] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[    1.184719] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[    1.340665] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[    1.340671] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[    1.432302] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[    1.432305] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[    1.452986] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[    1.452991] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[    1.494504] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[    1.494509] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[    1.530141] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[    1.530147] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[    1.544090] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    1.677381] usb 2-1: New USB device found, idVendor=1058, idProduct=0820
[    1.677387] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=5
[    1.677392] usb 2-1: Product: My Passport 0820
[    1.677397] usb 2-1: Manufacturer: Western Digital
[    1.677401] usb 2-1: SerialNumber: 5758323145413343464D3736
[    1.756136] ata3.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.756158] ata3.01: SATA link down (SStatus 0 SControl 300)
[    1.812234] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[    1.812240] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[    2.048096] usb 2-6: new high-speed USB device number 4 using ehci-pci
[    2.063230] ata3.00: ATA-8: ST9160314AS, D003DEM1, max UDMA/133
[    2.063233] ata3.00: 312581808 sectors, multi 8: LBA48 NCQ (depth 0/32)
[    2.076707] ata3.00: configured for UDMA/133
[    2.076924] scsi 2:0:0:0: Direct-Access     ATA      ST9160314AS      D003 PQ: 0 ANSI: 5
[    2.077079] sd 2:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    2.077082] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    2.077194] sd 2:0:0:0: [sda] Write Protect is off
[    2.077198] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.077284] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.141848]  sda: sda1 sda2 < sda5 > sda3
[    2.142406] sd 2:0:0:0: [sda] Attached SCSI disk
[    2.185239] usb 2-6: New USB device found, idVendor=05a9, idProduct=2640
[    2.185245] usb 2-6: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.185250] usb 2-6: Product: Laptop Integrated Webcam
[    2.185255] usb 2-6: Manufacturer: OmniVision Technologies, Inc. -2640-07.07.20.3
[    2.243966] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[    2.243972] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[    2.304056] ata4.01: failed to resume link (SControl 0)
[    2.304113] ata4.00: SATA link down (SStatus 0 SControl 300)
[    2.304139] ata4.01: SATA link down (SStatus 0 SControl 0)
[    2.304682] Freeing unused kernel memory: 872K (c19b2000 - c1a8c000)
[    2.304761] Write protecting the kernel text: 6524k
[    2.304880] Write protecting the kernel read-only data: 2764k
[    2.304882] NX-protecting the kernel data: 5764k
[    2.321148] systemd-udevd[105]: starting version 204
[    2.358404] pps_core: LinuxPPS API ver. 1 registered
[    2.358408] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
[    2.364518] PTP clock support registered
[    2.377087] tg3.c:v3.134 (Sep 16, 2013)
[    2.386675] usb-storage 2-1:1.0: USB Mass Storage device detected
[    2.389544] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[    2.389548] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[    2.396048] scsi4 : usb-storage 2-1:1.0
[    2.396143] usbcore: registered new interface driver usb-storage
[    2.401395] sdhci: Secure Digital Host Controller Interface driver
[    2.401398] sdhci: Copyright(c) Pierre Ossman
[    2.406825] sdhci-pci 0000:03:01.1: SDHCI controller found [1180:0822] (rev 22)
[    2.416207] sdhci-pci 0000:03:01.1: dummy supplies not allowed
[    2.416211] mmc0: no vqmmc regulator found
[    2.416214] sdhci-pci 0000:03:01.1: dummy supplies not allowed
[    2.416216] mmc0: no vmmc regulator found
[    2.427488] mmc0: SDHCI controller on PCI [0000:03:01.1] using DMA
[    2.436126] tg3 0000:09:00.0 eth0: Tigon3 [partno(BCM95906) rev c002] (PCI Express) MAC address 00:15:c5:87:2a:1e
[    2.436133] tg3 0000:09:00.0 eth0: attached PHY is 5906 (10/100Base-TX Ethernet) (WireSpeed[0], EEE[0])
[    2.436136] tg3 0000:09:00.0 eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[0]
[    2.436139] tg3 0000:09:00.0 eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    2.492107] firewire_ohci 0000:03:01.0: added OHCI v1.10 device as card 0, 4 IR + 4 IT contexts, quirks 0x11
[    2.552081] usb 7-1: new full-speed USB device number 2 using uhci_hcd
[    2.726171] usb 7-1: New USB device found, idVendor=0483, idProduct=2016
[    2.726178] usb 7-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.726183] usb 7-1: Product: Biometric Coprocessor
[    2.726188] usb 7-1: Manufacturer: STMicroelectronics
[    2.992198] firewire_core 0000:03:01.0: created device fw0: GUID 484fc0002dd16838, S400
[    3.138513] psmouse serio1: synaptics: Touchpad model: 1, fw: 6.3, id: 0x1c0b1, caps: 0xa04753/0x200000/0x0, board id: 3655, fw id: 356587
[    3.175385] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input5
[    3.219945] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[    3.219952] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[    3.396792] scsi 4:0:0:0: Direct-Access     WD       My Passport 0820 1007 PQ: 0 ANSI: 6
[    3.397292] scsi 4:0:0:1: Enclosure         WD       SES Device       1007 PQ: 0 ANSI: 6
[    3.397697] sd 4:0:0:0: Attached scsi generic sg2 type 0
[    3.397853] scsi 4:0:0:1: Attached scsi generic sg3 type 13
[    3.400472] sd 4:0:0:0: [sdb] 1953458176 512-byte logical blocks: (1.00 TB/931 GiB)
[    3.401467] sd 4:0:0:0: [sdb] Write Protect is off
[    3.401471] sd 4:0:0:0: [sdb] Mode Sense: 47 00 10 08
[    3.402466] sd 4:0:0:0: [sdb] No Caching mode page found
[    3.402470] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[    3.405717] sd 4:0:0:0: [sdb] No Caching mode page found
[    3.405721] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[    3.462422]  sdb: sdb1 sdb2 sdb3
[    3.469007] sd 4:0:0:0: [sdb] No Caching mode page found
[    3.469014] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[    3.469021] sd 4:0:0:0: [sdb] Attached SCSI disk
[    3.472649] ses 4:0:0:1: Attached Enclosure device
[    3.484095] usb 3-2: new full-speed USB device number 2 using uhci_hcd
[    3.540664] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[    3.540668] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[    3.865120] usb 3-2: New USB device found, idVendor=0a5c, idProduct=4500
[    3.865127] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    3.865133] usb 3-2: Product: BCM2045B2
[    3.865137] usb 3-2: Manufacturer: Broadcom
[    3.867158] hub 3-2:1.0: USB hub found
[    3.869084] hub 3-2:1.0: 3 ports detected
[    4.004576] EXT4-fs (sdb3): mounted filesystem with ordered data mode. Opts: (null)
[    4.082983] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[    4.082988] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[    4.150110] usb 3-2.1: new full-speed USB device number 3 using uhci_hcd
[    4.158383] random: nonblocking pool is initialized
[    4.184872] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[    4.184876] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[    4.276102] usb 3-2.1: New USB device found, idVendor=413c, idProduct=8126
[    4.276109] usb 3-2.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    4.276114] usb 3-2.1: Product: BCM2045
[    4.276119] usb 3-2.1: Manufacturer: Broadcom Corp
[    4.354101] usb 3-2.2: new full-speed USB device number 4 using uhci_hcd
[    4.484087] usb 3-2.2: New USB device found, idVendor=0a5c, idProduct=4502
[    4.484094] usb 3-2.2: New USB device strings: Mfr=1, Product=0, SerialNumber=0
[    4.484100] usb 3-2.2: Manufacturer: Broadcom Corp
[    4.561102] usb 3-2.3: new full-speed USB device number 5 using uhci_hcd
[    4.599882] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[    4.599887] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[    4.691095] usb 3-2.3: New USB device found, idVendor=0a5c, idProduct=4503
[    4.691100] usb 3-2.3: New USB device strings: Mfr=1, Product=0, SerialNumber=0
[    4.691103] usb 3-2.3: Manufacturer: Broadcom Corp
[    4.811745] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[    4.811752] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[    5.112148] usb 3-2: USB disconnect, device number 2
[    5.112157] usb 3-2.1: USB disconnect, device number 3
[    5.112531] usb 3-2.2: USB disconnect, device number 4
[    5.112658] usb 3-2.3: USB disconnect, device number 5
[    5.199146] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[    5.199151] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[    5.215619] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[    5.215624] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[    5.598180] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[    5.598188] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[    5.636072] usb 3-2: new full-speed USB device number 6 using uhci_hcd
[    5.815091] usb 3-2: New USB device found, idVendor=0a5c, idProduct=4500
[    5.815097] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    5.815100] usb 3-2: Product: BCM2045B2
[    5.815103] usb 3-2: Manufacturer: Broadcom
[    5.817134] hub 3-2:1.0: USB hub found
[    5.819105] hub 3-2:1.0: 3 ports detected
[    6.053858] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[    6.053863] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[    6.102077] usb 3-2.1: new full-speed USB device number 7 using uhci_hcd
[    6.230090] usb 3-2.1: New USB device found, idVendor=413c, idProduct=8126
[    6.230097] usb 3-2.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    6.230102] usb 3-2.1: Product: BCM2045
[    6.230107] usb 3-2.1: Manufacturer: Broadcom Corp
[    6.278620] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[    6.278627] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[    6.308140] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[    6.308144] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[    6.310080] usb 3-2.2: new full-speed USB device number 8 using uhci_hcd
[    6.385572] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[    6.385577] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[    6.402828] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[    6.402835] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[    6.437482] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[    6.437489] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[    6.440078] usb 3-2.2: New USB device found, idVendor=0a5c, idProduct=4502
[    6.440084] usb 3-2.2: New USB device strings: Mfr=1, Product=0, SerialNumber=0
[    6.440089] usb 3-2.2: Manufacturer: Broadcom Corp
[    6.518101] usb 3-2.3: new full-speed USB device number 9 using uhci_hcd
[    6.651092] usb 3-2.3: New USB device found, idVendor=0a5c, idProduct=4503
[    6.651099] usb 3-2.3: New USB device strings: Mfr=1, Product=0, SerialNumber=0
[    6.651105] usb 3-2.3: Manufacturer: Broadcom Corp
[    6.983490] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[    6.983497] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[    7.840178] usb 3-2: USB disconnect, device number 6
[    7.840185] usb 3-2.1: USB disconnect, device number 7
[    7.840585] usb 3-2.2: USB disconnect, device number 8
[    7.840750] usb 3-2.3: USB disconnect, device number 9
[    8.036979] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[    8.036987] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[    8.091935] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[    8.091942] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[    8.313182] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[    8.313190] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[    8.464094] usb 3-2: new full-speed USB device number 10 using uhci_hcd
[    8.492467] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[    8.492473] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[    8.642076] usb 3-2: New USB device found, idVendor=0a5c, idProduct=4500
[    8.642082] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    8.642088] usb 3-2: Product: BCM2045B2
[    8.642092] usb 3-2: Manufacturer: Broadcom
[    8.644132] hub 3-2:1.0: USB hub found
[    8.646068] hub 3-2:1.0: 3 ports detected
[    8.926054] usb 3-2.1: new full-speed USB device number 11 using uhci_hcd
[    9.053072] usb 3-2.1: New USB device found, idVendor=413c, idProduct=8126
[    9.053076] usb 3-2.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    9.053079] usb 3-2.1: Product: BCM2045
[    9.053082] usb 3-2.1: Manufacturer: Broadcom Corp
[    9.130081] usb 3-2.2: new full-speed USB device number 12 using uhci_hcd
[    9.260084] usb 3-2.2: New USB device found, idVendor=0a5c, idProduct=4502
[    9.260090] usb 3-2.2: New USB device strings: Mfr=1, Product=0, SerialNumber=0
[    9.260095] usb 3-2.2: Manufacturer: Broadcom Corp
[    9.338081] usb 3-2.3: new full-speed USB device number 13 using uhci_hcd
[    9.372983] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[    9.372986] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[    9.466970] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[    9.466974] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[    9.468075] usb 3-2.3: New USB device found, idVendor=0a5c, idProduct=4503
[    9.468079] usb 3-2.3: New USB device strings: Mfr=1, Product=0, SerialNumber=0
[    9.468082] usb 3-2.3: Manufacturer: Broadcom Corp
[    9.772410] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[    9.772413] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[    9.812509] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[    9.812513] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[   10.816113] usb 3-2: USB disconnect, device number 10
[   10.816118] usb 3-2.1: USB disconnect, device number 11
[   10.816488] usb 3-2.2: USB disconnect, device number 12
[   10.816654] usb 3-2.3: USB disconnect, device number 13
[   11.285943] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[   11.285950] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[   11.300445] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[   11.300449] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[   13.406247] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[   13.406254] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[   13.494887] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[   13.494893] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[   13.581858] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[   13.581863] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[   13.836088] usb 3-2: new full-speed USB device number 14 using uhci_hcd
[   13.914939] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[   13.914943] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[   14.009211] usb 3-2: New USB device found, idVendor=0a5c, idProduct=4500
[   14.009218] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[   14.009223] usb 3-2: Product: BCM2045B2
[   14.009228] usb 3-2: Manufacturer: Broadcom
[   14.011266] hub 3-2:1.0: USB hub found
[   14.013198] hub 3-2:1.0: 3 ports detected
[   14.293188] usb 3-2.1: new full-speed USB device number 15 using uhci_hcd
[   14.419213] usb 3-2.1: New USB device found, idVendor=413c, idProduct=8126
[   14.419220] usb 3-2.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[   14.419225] usb 3-2.1: Product: BCM2045
[   14.419230] usb 3-2.1: Manufacturer: Broadcom Corp
[   14.424787] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[   14.424793] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[   14.482411] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[   14.482416] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[   14.501221] usb 3-2.2: new full-speed USB device number 16 using uhci_hcd
[   14.633214] usb 3-2.2: New USB device found, idVendor=0a5c, idProduct=4502
[   14.633221] usb 3-2.2: New USB device strings: Mfr=1, Product=0, SerialNumber=0
[   14.633226] usb 3-2.2: Manufacturer: Broadcom Corp
[   14.709189] usb 3-2.3: new full-speed USB device number 17 using uhci_hcd
[   14.713359] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[   14.713365] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[   14.840219] usb 3-2.3: New USB device found, idVendor=0a5c, idProduct=4503
[   14.840225] usb 3-2.3: New USB device strings: Mfr=1, Product=0, SerialNumber=0
[   14.840231] usb 3-2.3: Manufacturer: Broadcom Corp
[   15.308824] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[   15.308832] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[   16.012665] EXT4-fs (sdb3): re-mounted. Opts: errors=remount-ro
[   16.272179] usb 3-2: USB disconnect, device number 14
[   16.272187] usb 3-2.1: USB disconnect, device number 15
[   16.272562] usb 3-2.2: USB disconnect, device number 16
[   16.272705] usb 3-2.3: USB disconnect, device number 17
[   16.827849] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.893147] init: bootchart main process (335) terminated with status 127
[   17.210025] init: bootchart post-stop process (352) terminated with status 127
[   17.212110] systemd-udevd[388]: starting version 204
[   17.777378] lp: driver loaded but no devices found
[   17.919304] ppdev: user-space parallel port driver
[   19.583938] Bluetooth: Core ver 2.17
[   19.583967] NET: Registered protocol family 31
[   19.583969] Bluetooth: HCI device and connection manager initialized
[   19.583980] Bluetooth: HCI socket layer initialized
[   19.583983] Bluetooth: L2CAP socket layer initialized
[   19.583990] Bluetooth: SCO socket layer initialized
[   19.644953] Bluetooth: RFCOMM TTY layer initialized
[   19.644967] Bluetooth: RFCOMM socket layer initialized
[   19.644975] Bluetooth: RFCOMM ver 1.11
[   19.715086] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.715091] Bluetooth: BNEP filters: protocol multicast
[   19.715101] Bluetooth: BNEP socket layer initialized
[   19.920887] init: avahi-cups-reload main process (478) terminated with status 1
[   20.621440] type=1400 audit(1403506138.106:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=456 comm="apparmor_parser"
[   20.621449] type=1400 audit(1403506138.106:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=456 comm="apparmor_parser"
[   20.622052] type=1400 audit(1403506138.106:4): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=456 comm="apparmor_parser"
[   20.649969] wmi: Mapper loaded
[   20.926697] atkbd serio0: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[   20.926702] atkbd serio0: Use 'setkeycodes e008 <keycode>' to make it known.
[   21.012968] [drm] Initialized drm 1.1.0 20060810
[   21.121033] r592: driver successfully loaded
[   21.261222] cfg80211: Calling CRDA to update world regulatory domain
[   21.356049] usb 3-2: new full-speed USB device number 18 using uhci_hcd
[   21.533117] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   21.540183] usb 3-2: New USB device found, idVendor=0a5c, idProduct=4500
[   21.540188] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[   21.540192] usb 3-2: Product: BCM2045B2
[   21.540195] usb 3-2: Manufacturer: Broadcom
[   21.543099] hub 3-2:1.0: USB hub found
[   21.545055] hub 3-2:1.0: 3 ports detected
[   21.684370] [drm] Memory usable by graphics device = 512M
[   21.684377] checking generic (e0000000 300000) vs hw (e0000000 10000000)
[   21.684379] fb: conflicting fb hw usage inteldrmfb vs VESA VGA - removing generic driver
[   21.684432] Console: switching to colour dummy device 80x25
[   21.708080] i915 0000:00:02.0: irq 44 for MSI/MSI-X
[   21.708093] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[   21.708095] [drm] Driver supports precise vblank timestamp query.
[   21.708155] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   21.761704] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   21.761709] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   21.761765] iwl3945 0000:0c:00.0: can't disable ASPM; OS doesn't have ASPM control
[   21.786430] type=1400 audit(1403506139.270:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=527 comm="apparmor_parser"
[   21.786440] type=1400 audit(1403506139.270:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=527 comm="apparmor_parser"
[   21.786446] type=1400 audit(1403506139.270:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=527 comm="apparmor_parser"
[   21.787055] type=1400 audit(1403506139.270:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=527 comm="apparmor_parser"
[   21.787061] type=1400 audit(1403506139.270:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=527 comm="apparmor_parser"
[   21.787369] type=1400 audit(1403506139.270:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=527 comm="apparmor_parser"
[   21.792551] type=1400 audit(1403506139.278:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=517 comm="apparmor_parser"
[   21.817586] iwl3945 0000:0c:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   21.817592] iwl3945 0000:0c:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   21.817668] iwl3945 0000:0c:00.0: irq 45 for MSI/MSI-X
[   21.891094] usb 3-2.1: new full-speed USB device number 19 using uhci_hcd
[   21.952395] [drm] initialized overlay support
[   21.999594] fbcon: inteldrmfb (fb0) is primary device
[   22.037423] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   22.038008] r852: driver loaded successfully
[   22.086058] usb 3-2.1: New USB device found, idVendor=413c, idProduct=8126
[   22.086060] usb 3-2.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[   22.086062] usb 3-2.1: Product: BCM2045
[   22.086064] usb 3-2.1: Manufacturer: Broadcom Corp
[   22.165063] usb 3-2.2: new full-speed USB device number 20 using uhci_hcd
[   22.202050] input: Dell WMI hotkeys as /devices/virtual/input/input6
[   22.215388] gpio_ich: GPIO from 206 to 255 on gpio_ich
[   22.301697] Linux video capture interface: v2.00
[   22.303091] usb 3-2.2: New USB device found, idVendor=0a5c, idProduct=4502
[   22.303093] usb 3-2.2: New USB device strings: Mfr=1, Product=0, SerialNumber=0
[   22.303095] usb 3-2.2: Manufacturer: Broadcom Corp
[   22.382152] usb 3-2.3: new full-speed USB device number 21 using uhci_hcd
[   22.515068] usb 3-2.3: New USB device found, idVendor=0a5c, idProduct=4503
[   22.515071] usb 3-2.3: New USB device strings: Mfr=1, Product=0, SerialNumber=0
[   22.515073] usb 3-2.3: Manufacturer: Broadcom Corp
[   22.678695] uvcvideo: Found UVC 1.00 device Laptop Integrated Webcam (05a9:2640)
[   22.681005] input: Laptop Integrated Webcam as /devices/pci0000:00/0000:00:1d.7/usb2/2-6/2-6:1.0/input/input7
[   22.681229] usbcore: registered new interface driver uvcvideo
[   22.681230] USB Video Class driver (1.1.1)
[   22.707286] cfg80211: World regulatory domain updated:
[   22.707288] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   22.707289] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.707291] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.707292] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   22.707293] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.707295] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.790854] usbcore: registered new interface driver btusb
[   22.798997] hidraw: raw HID events driver (C) Jiri Kosina
[   22.823213] Console: switching to colour frame buffer device 160x50
[   22.828496] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   22.828498] i915 0000:00:02.0: registered panic notifier
[   22.852337] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[   22.888683] acpi device:35: registered as cooling_device2
[   22.890725] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input8
[   22.909170] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[   22.909891] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   22.910341] snd_hda_intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[   22.916625] usbcore: registered new interface driver usbhid
[   22.916629] usbhid: USB HID core driver
[   22.974894] autoconfig: line_outs=1 (0xd/0x0/0x0/0x0/0x0) type:speaker
[   22.974900]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   22.974902]    hp_outs=2 (0xf/0xa/0x0/0x0/0x0)
[   22.974904]    mono: mono_out=0x0
[   22.974906]    dig-out=0x21/0x0
[   22.974907]    inputs:
[   22.974910]      Internal Mic=0x13
[   22.974912]      Mic=0xe
[   22.985969] input: Broadcom Corp as /devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2.2/3-2.2:1.0/input/input9
[   22.987338] hid-generic 0003:0A5C:4502.0001: input,hidraw0: USB HID v1.11 Keyboard [Broadcom Corp] on usb-0000:00:1a.0-2.2/input0
[   22.990869] input: Broadcom Corp as /devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2.3/3-2.3:1.0/input/input10
[   22.995073] hid-generic 0003:0A5C:4503.0002: input,hidraw1: USB HID v1.11 Mouse [Broadcom Corp] on usb-0000:00:1a.0-2.3/input0
[   23.540315] input: HDA Intel HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   23.540634] input: HDA Intel Front Headphone Surround as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   23.540847] input: HDA Intel Front Headphone Front as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   24.284530] init: failsafe main process (569) killed by TERM signal
[   24.456121] usb 3-2: USB disconnect, device number 18
[   24.456127] usb 3-2.1: USB disconnect, device number 19
[   24.460995] usb 3-2.2: USB disconnect, device number 20
[   24.524897] usb 3-2.3: USB disconnect, device number 21
[   25.764070] usb 3-2: new full-speed USB device number 22 using uhci_hcd
[   25.938146] usb 3-2: New USB device found, idVendor=0a5c, idProduct=4500
[   25.938154] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[   25.938159] usb 3-2: Product: BCM2045B2
[   25.938164] usb 3-2: Manufacturer: Broadcom
[   25.940201] hub 3-2:1.0: USB hub found
[   25.942131] hub 3-2:1.0: 3 ports detected
[   26.225136] usb 3-2.1: new full-speed USB device number 23 using uhci_hcd
[   26.282162] audit_printk_skb: 15 callbacks suppressed
[   26.282167] type=1400 audit(1403506143.766:17): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cups-browsed" pid=763 comm="apparmor_parser"
[   26.354133] usb 3-2.1: New USB device found, idVendor=413c, idProduct=8126
[   26.354138] usb 3-2.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[   26.354141] usb 3-2.1: Product: BCM2045
[   26.354144] usb 3-2.1: Manufacturer: Broadcom Corp
[   26.433129] usb 3-2.2: new full-speed USB device number 24 using uhci_hcd
[   26.566141] usb 3-2.2: New USB device found, idVendor=0a5c, idProduct=4502
[   26.566151] usb 3-2.2: New USB device strings: Mfr=1, Product=0, SerialNumber=0
[   26.566157] usb 3-2.2: Manufacturer: Broadcom Corp
[   26.573117] input: Broadcom Corp as /devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2.2/3-2.2:1.0/input/input14
[   26.573236] hid-generic 0003:0A5C:4502.0003: input,hidraw0: USB HID v1.11 Keyboard [Broadcom Corp] on usb-0000:00:1a.0-2.2/input0
[   26.645148] usb 3-2.3: new full-speed USB device number 25 using uhci_hcd
[   26.778146] usb 3-2.3: New USB device found, idVendor=0a5c, idProduct=4503
[   26.778152] usb 3-2.3: New USB device strings: Mfr=1, Product=0, SerialNumber=0
[   26.778155] usb 3-2.3: Manufacturer: Broadcom Corp
[   26.787865] input: Broadcom Corp as /devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2.3/3-2.3:1.0/input/input15
[   26.788085] hid-generic 0003:0A5C:4503.0004: input,hidraw1: USB HID v1.11 Mouse [Broadcom Corp] on usb-0000:00:1a.0-2.3/input0
[   27.830980] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   27.833174] tg3 0000:09:00.0: irq 47 for MSI/MSI-X
[   27.865134] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   27.865573] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   28.019317] iwl3945 0000:0c:00.0: loaded firmware version 15.32.2.9
[   28.019456] iwl3945 0000:0c:00.0: Radio disabled by HW RF Kill switch
[   28.424187] usb 3-2: USB disconnect, device number 22
[   28.424193] usb 3-2.1: USB disconnect, device number 23
[   28.428950] usb 3-2.2: USB disconnect, device number 24
[   28.480127] usb 3-2.3: USB disconnect, device number 25
[   29.082435] type=1400 audit(1403506146.566:18): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=874 comm="apparmor_parser"
[   29.082447] type=1400 audit(1403506146.566:19): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=874 comm="apparmor_parser"
[   29.082454] type=1400 audit(1403506146.566:20): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=874 comm="apparmor_parser"
[   29.083056] type=1400 audit(1403506146.566:21): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=874 comm="apparmor_parser"
[   29.083064] type=1400 audit(1403506146.566:22): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=874 comm="apparmor_parser"
[   29.084906] type=1400 audit(1403506146.570:23): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=874 comm="apparmor_parser"
[   29.303153] type=1400 audit(1403506146.786:24): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/telepathy/mission-control-5" pid=879 comm="apparmor_parser"
[   29.303164] type=1400 audit(1403506146.786:25): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/telepathy/telepathy-*" pid=879 comm="apparmor_parser"
[   29.303171] type=1400 audit(1403506146.786:26): apparmor="STATUS" operation="profile_load" profile="unconfined" name="pxgsettings" pid=879 comm="apparmor_parser"
[   29.392115] usb 3-2: new full-speed USB device number 26 using uhci_hcd
[   29.988105] usb 3-2: New USB device found, idVendor=0a5c, idProduct=4500
[   29.988110] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[   29.988113] usb 3-2: Product: BCM2045B2
[   29.988116] usb 3-2: Manufacturer: Broadcom
[   29.991163] hub 3-2:1.0: USB hub found
[   29.993103] hub 3-2:1.0: 3 ports detected
[   30.277097] usb 3-2.1: new full-speed USB device number 27 using uhci_hcd

```
here is the bootchart
[IMG]http://i57.tinypic.com/2vb795h.png[/IMG]
link - [http://i57.tinypic.com/2vb795h.png](http://i57.tinypic.com/2vb795h.png)

the point is it is still very slow compared to older times

---

### Post by varun-10 on 2014-06-24
-bump-

---

