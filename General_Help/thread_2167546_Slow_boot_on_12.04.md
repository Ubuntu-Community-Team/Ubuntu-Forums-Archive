---
title: "Slow boot on 12.04"
date: 2013-08-14
forum: General Help
---

### Post by jolindbe on 2013-08-14
Hi,

Since I upgraded to Ubuntu 12.04 a year or so ago, it has booted fairly slowly (~45-60 seconds). I thought that I finally should try to do something about it, and found that "dmesg" could be used to see what happens during boot. However, I have difficulties interpreting the output - but it seems like it has something to do with recovery of my filesystem on sda5, which is my / directory(!) and/or writing stuff to the swap space... can anyone help me figure out what's wrong? 

This is the output of dmesg:
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-51-generic-pae (buildd@komainu) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #77-Ubuntu SMP Wed Jul 24 20:40:32 UTC 2013 (Ubuntu 3.2.0-51.77-generic-pae 3.2.48)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e800 (usable)
[    0.000000]  BIOS-e820: 000000000009e800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bf27c000 (usable)
[    0.000000]  BIOS-e820: 00000000bf27c000 - 00000000bf282000 (reserved)
[    0.000000]  BIOS-e820: 00000000bf282000 - 00000000bf35f000 (usable)
[    0.000000]  BIOS-e820: 00000000bf35f000 - 00000000bf371000 (reserved)
[    0.000000]  BIOS-e820: 00000000bf371000 - 00000000bf3f2000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bf3f2000 - 00000000bf40f000 (reserved)
[    0.000000]  BIOS-e820: 00000000bf40f000 - 00000000bf46f000 (usable)
[    0.000000]  BIOS-e820: 00000000bf46f000 - 00000000bf668000 (reserved)
[    0.000000]  BIOS-e820: 00000000bf668000 - 00000000bf6e8000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bf6e8000 - 00000000bf70f000 (reserved)
[    0.000000]  BIOS-e820: 00000000bf70f000 - 00000000bf717000 (usable)
[    0.000000]  BIOS-e820: 00000000bf717000 - 00000000bf71f000 (reserved)
[    0.000000]  BIOS-e820: 00000000bf71f000 - 00000000bf76c000 (usable)
[    0.000000]  BIOS-e820: 00000000bf76c000 - 00000000bf778000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bf778000 - 00000000bf77b000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bf77b000 - 00000000bf78b000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bf78b000 - 00000000bf78c000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bf78c000 - 00000000bf79f000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bf79f000 - 00000000bf7ff000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bf7ff000 - 00000000bf800000 (usable)
[    0.000000]  BIOS-e820: 00000000bf800000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000feaff000 - 00000000feb00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000138000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.6 present.
[    0.000000] DMI: LENOVO 2522KDG/2522KDG, BIOS 6IET65WW (1.25 ) 06/07/2010
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x138000 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-D3FFF write-protect
[    0.000000]   D4000-DBFFF uncachable
[    0.000000]   DC000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 disabled
[    0.000000]   1 base 000000000 mask F80000000 write-back
[    0.000000]   2 base 080000000 mask FC0000000 write-back
[    0.000000]   3 base 100000000 mask FC0000000 write-back
[    0.000000]   4 base 138000000 mask FF8000000 uncachable
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 1, base: 0GB, range: 2GB, type WB
[    0.000000] reg 2, base: 2GB, range: 1GB, type WB
[    0.000000] reg 3, base: 4GB, range: 1GB, type WB
[    0.000000] reg 4, base: 4992MB, range: 128MB, type UC
[    0.000000] total RAM covered: 3968M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K 	chunk_size: 256M 	num_reg: 4  	lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 4GB, range: 1GB, type WB
[    0.000000] reg 3, base: 4992MB, range: 128MB, type UC
[    0.000000] e820 update range: 00000000c0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] found SMP MP-table at [c00f68c0] f68c0
[    0.000000] initial memory mapped : 0 - 02000000
[    0.000000] Base memory trampoline at [c009a000] 9a000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-0000000037bfe000
[    0.000000]  0000000000 - 0000200000 page 4k
[    0.000000]  0000200000 - 0037a00000 page 2M
[    0.000000]  0037a00000 - 0037bfe000 page 4k
[    0.000000] kernel direct mapping tables up to 37bfe000 @ 1ffa000-2000000
[    0.000000] RAMDISK: 35a26000 - 36d0b000
[    0.000000] ACPI: RSDP 000f6880 00024 (v02 LENOVO)
[    0.000000] ACPI: XSDT bf7ef338 00094 (v01 LENOVO TP-6I    00001250  LTP 00000000)
[    0.000000] ACPI: FACP bf7ef400 000F4 (v04 LENOVO TP-6I    00001250 LNVO 00000001)
[    0.000000] ACPI: DSDT bf7ef7d1 0F2F8 (v01 LENOVO TP-6I    00001250 MSFT 03000001)
[    0.000000] ACPI: FACS bf6e7000 00040
[    0.000000] ACPI: SSDT bf7ef5b4 0021D (v01 LENOVO TP-6I    00001250 MSFT 03000001)
[    0.000000] ACPI: ECDT bf7feac9 00052 (v01 LENOVO TP-6I    00001250 LNVO 00000001)
[    0.000000] ACPI: APIC bf7feb1b 00084 (v01 LENOVO TP-6I    00001250 LNVO 00000001)
[    0.000000] ACPI: MCFG bf7febd7 0003C (v01 LENOVO TP-6I    00001250 LNVO 00000001)
[    0.000000] ACPI: HPET bf7fec13 00038 (v01 LENOVO TP-6I    00001250 LNVO 00000001)
[    0.000000] ACPI: ASF! bf7fedbe 000A4 (v16 LENOVO TP-6I    00001250 PTL  00000001)
[    0.000000] ACPI: SLIC bf7fee62 00176 (v01 LENOVO TP-6I    00001250  LTP 00000000)
[    0.000000] ACPI: BOOT bf7fefd8 00028 (v01 LENOVO TP-6I    00001250  LTP 00000001)
[    0.000000] ACPI: SSDT bf6e591a 0084B (v01 LENOVO TP-6I    00001250 INTL 20050513)
[    0.000000] ACPI: TCPA bf78b000 00032 (v02    PTL  CRESTLN 06040000      00005A52)
[    0.000000] ACPI: SSDT bf77a000 009F1 (v01  PmRef    CpuPm 00003000 INTL 20061109)
[    0.000000] ACPI: SSDT bf779000 00259 (v01  PmRef  Cpu0Tst 00003000 INTL 20061109)
[    0.000000] ACPI: SSDT bf778000 0049F (v01  PmRef    ApTst 00003000 INTL 20061109)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 4100MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00037bfe
[    0.000000]   HighMem  0x00037bfe -> 0x00138000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[8] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x000bf27c
[    0.000000]     0: 0x000bf282 -> 0x000bf35f
[    0.000000]     0: 0x000bf40f -> 0x000bf46f
[    0.000000]     0: 0x000bf70f -> 0x000bf717
[    0.000000]     0: 0x000bf71f -> 0x000bf76c
[    0.000000]     0: 0x000bf7ff -> 0x000bf800
[    0.000000]     0: 0x00100000 -> 0x00138000
[    0.000000] On node 0 totalpages: 1012637
[    0.000000] free_area_init_node: node 0, pgdat c18719c0, node_mem_map f3326200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3950 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 222502 pages, LIFO batch:31
[    0.000000]   HighMem zone: 8201 pages used for memmap
[    0.000000]   HighMem zone: 776200 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
[    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
[    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000dc000
[    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:20000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @f7bb2000 s34240 r0 d23104 u57344
[    0.000000] pcpu-alloc: s34240 r0 d23104 u57344 alloc=14*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 [0] 2 [0] 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1002652
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-51-generic-pae root=UUID=14697179-dbb4-43df-9202-220506027d87 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 20446976 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:00138000)
[    0.000000] Memory: 3959784k/5111808k available (5837k kernel code, 90764k reserved, 2863k data, 744k init, 3137604k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc1880000 - 0xc193a000   ( 744 kB)
[    0.000000]       .data : 0xc15b343c - 0xc187f1c0   (2863 kB)
[    0.000000]       .text : 0xc1000000 - 0xc15b343c   (5837 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:712 16
[    0.000000] CPU 0 irqstacks, hard=f740a000 soft=f740c000
[    0.000000] Extended CMOS year: 2000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.004000] Detected 2659.997 MHz processor.
[    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 5319.99 BogoMIPS (lpj=10639988)
[    0.000009] pid_max: default: 32768 minimum: 301
[    0.000045] Security Framework initialized
[    0.000068] AppArmor: AppArmor initialized
[    0.000071] Yama: becoming mindful.
[    0.000159] Mount-cache hash table entries: 512
[    0.000342] Initializing cgroup subsys cpuacct
[    0.000352] Initializing cgroup subsys memory
[    0.000364] Initializing cgroup subsys devices
[    0.000367] Initializing cgroup subsys freezer
[    0.000371] Initializing cgroup subsys blkio
[    0.000380] Initializing cgroup subsys perf_event
[    0.000418] CPU: Physical Processor ID: 0
[    0.000421] CPU: Processor Core ID: 0
[    0.000429] mce: CPU supports 9 MCE banks
[    0.000445] CPU0: Thermal monitoring enabled (TM1)
[    0.000457] using mwait in idle threads.
[    0.003886] ACPI: Core revision 20110623
[    0.028825] ftrace: allocating 26134 entries in 52 pages
[    0.043105] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.043622] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.083210] CPU0: Intel(R) Core(TM) i7 CPU       M 620  @ 2.67GHz stepping 02
[    0.190653] Performance Events: PEBS fmt1+, Westmere events, Intel PMU driver.
[    0.190664] ... version:                3
[    0.190667] ... bit width:              48
[    0.190670] ... generic registers:      4
[    0.190672] ... value mask:             0000ffffffffffff
[    0.190675] ... max period:             000000007fffffff
[    0.190678] ... fixed-purpose events:   3
[    0.190681] ... event mask:             000000070000000f
[    0.190897] NMI watchdog enabled, takes one hw-pmu counter.
[    0.191033] CPU 1 irqstacks, hard=f7512000 soft=f7514000
[    0.191036] Booting Node   0, Processors  #1
[    0.191041] smpboot cpu 1: start_ip = 9a000
[    0.201249] Initializing CPU#1
[    0.298523] NMI watchdog enabled, takes one hw-pmu counter.
[    0.298674] CPU 2 irqstacks, hard=f7520000 soft=f7522000
[    0.298678]  #2
[    0.298680] smpboot cpu 2: start_ip = 9a000
[    0.308890] Initializing CPU#2
[    0.406275] NMI watchdog enabled, takes one hw-pmu counter.
[    0.406416] CPU 3 irqstacks, hard=f7554000 soft=f7556000
[    0.406420]  #3 Ok.
[    0.406422] smpboot cpu 3: start_ip = 9a000
[    0.416631] Initializing CPU#3
[    0.514015] NMI watchdog enabled, takes one hw-pmu counter.
[    0.514066] Brought up 4 CPUs
[    0.514070] Total of 4 processors activated (21279.70 BogoMIPS).
[    0.518388] devtmpfs: initialized
[    0.518592] EVM: security.selinux
[    0.518595] EVM: security.SMACK64
[    0.518597] EVM: security.capability
[    0.518639] PM: Registering ACPI NVS region at bf371000 (528384 bytes)
[    0.518665] PM: Registering ACPI NVS region at bf668000 (524288 bytes)
[    0.518688] PM: Registering ACPI NVS region at bf76c000 (49152 bytes)
[    0.518693] PM: Registering ACPI NVS region at bf77b000 (65536 bytes)
[    0.518699] PM: Registering ACPI NVS region at bf78c000 (77824 bytes)
[    0.520472] print_constraints: dummy: 
[    0.520513] RTC time:  9:22:14, date: 08/14/13
[    0.520576] NET: Registered protocol family 16
[    0.520736] Trying to unpack rootfs image as initramfs...
[    0.520761] EISA bus registered
[    0.520788] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.520792] ACPI: bus type pci registered
[    0.520898] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.520904] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.520907] PCI: Using MMCONFIG for extended config space
[    0.520910] PCI: Using configuration type 1 for base access
[    0.522801] bio: create slab <bio-0> at 0
[    0.522951] ACPI: Added _OSI(Module Device)
[    0.522955] ACPI: Added _OSI(Processor Device)
[    0.522959] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.522963] ACPI: Added _OSI(Processor Aggregator Device)
[    0.526959] ACPI: EC: EC description table is found, configuring boot EC
[    0.538180] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.663284] ACPI: SSDT bf71a598 004F3 (v01  PmRef  Cpu0Ist 00003000 INTL 20061109)
[    0.664283] ACPI: Dynamic OEM Table Load:
[    0.664289] ACPI: SSDT   (null) 004F3 (v01  PmRef  Cpu0Ist 00003000 INTL 20061109)
[    0.664542] ACPI: SSDT bf718718 006B2 (v01  PmRef  Cpu0Cst 00003001 INTL 20061109)
[    0.665555] ACPI: Dynamic OEM Table Load:
[    0.665560] ACPI: SSDT   (null) 006B2 (v01  PmRef  Cpu0Cst 00003001 INTL 20061109)
[    0.721934] ACPI: SSDT bf719a98 00303 (v01  PmRef    ApIst 00003000 INTL 20061109)
[    0.723042] ACPI: Dynamic OEM Table Load:
[    0.723047] ACPI: SSDT   (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20061109)
[    0.753550] ACPI: SSDT bf717d98 00119 (v01  PmRef    ApCst 00003000 INTL 20061109)
[    0.754572] ACPI: Dynamic OEM Table Load:
[    0.754577] ACPI: SSDT   (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20061109)
[    0.787570] ACPI: Interpreter enabled
[    0.787583] ACPI: (supports S0 S3 S4 S5)
[    0.787623] ACPI: Using IOAPIC for interrupt routing
[    0.798474] ACPI: Power Resource [PUBS] (on)
[    0.806581] ACPI: EC: GPE = 0x11, I/O: command/status = 0x66, data = 0x62
[    0.808111] ACPI: ACPI Dock Station Driver: 2 docks/bays found
[    0.808116] HEST: Table not found.
[    0.808123] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.808148] ACPI: PCI Root Bridge [UNCR] (domain 0000 [bus ff])
[    0.808227] pci 0000:ff:00.0: [8086:2c62] type 0 class 0x000600
[    0.808271] pci 0000:ff:00.1: [8086:2d01] type 0 class 0x000600
[    0.808311] pci 0000:ff:02.0: [8086:2d10] type 0 class 0x000600
[    0.808346] pci 0000:ff:02.1: [8086:2d11] type 0 class 0x000600
[    0.808381] pci 0000:ff:02.2: [8086:2d12] type 0 class 0x000600
[    0.808415] pci 0000:ff:02.3: [8086:2d13] type 0 class 0x000600
[    0.808469] pci_bus 0000:ff: on NUMA node 0
[    0.808485]  pci0000:ff: Requesting ACPI _OSC control (0x1d)
[    0.808490]  pci0000:ff: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.808493] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.809082] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[    0.809182] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.809187] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.809191] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.809196] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    0.809201] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    0.809206] pci_root PNP0A08:00: host bridge window [mem 0xc0000000-0xfebfffff]
[    0.809225] pci 0000:00:00.0: [8086:0044] type 0 class 0x000600
[    0.809267] DMAR: BIOS has allocated no shadow GTT; disabling IOMMU for graphics
[    0.809303] pci 0000:00:01.0: [8086:0045] type 1 class 0x000604
[    0.809364] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.809370] pci 0000:00:01.0: PME# disabled
[    0.809442] pci 0000:00:16.0: [8086:3b64] type 0 class 0x000780
[    0.809488] pci 0000:00:16.0: reg 10: [mem 0xf2427800-0xf242780f 64bit]
[    0.809632] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.809640] pci 0000:00:16.0: PME# disabled
[    0.809682] pci 0000:00:16.3: [8086:3b67] type 0 class 0x000700
[    0.809716] pci 0000:00:16.3: reg 10: [io  0x1800-0x1807]
[    0.809736] pci 0000:00:16.3: reg 14: [mem 0xf2424000-0xf2424fff]
[    0.809919] pci 0000:00:19.0: [8086:10ea] type 0 class 0x000200
[    0.809956] pci 0000:00:19.0: reg 10: [mem 0xf2400000-0xf241ffff]
[    0.809972] pci 0000:00:19.0: reg 14: [mem 0xf2425000-0xf2425fff]
[    0.809989] pci 0000:00:19.0: reg 18: [io  0x1820-0x183f]
[    0.810117] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.810124] pci 0000:00:19.0: PME# disabled
[    0.810168] pci 0000:00:1a.0: [8086:3b3c] type 0 class 0x000c03
[    0.810204] pci 0000:00:1a.0: reg 10: [mem 0xf2428000-0xf24283ff]
[    0.810362] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.810369] pci 0000:00:1a.0: PME# disabled
[    0.810416] pci 0000:00:1b.0: [8086:3b56] type 0 class 0x000403
[    0.810447] pci 0000:00:1b.0: reg 10: [mem 0xf2420000-0xf2423fff 64bit]
[    0.810589] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.810596] pci 0000:00:1b.0: PME# disabled
[    0.810636] pci 0000:00:1c.0: [8086:3b42] type 1 class 0x000604
[    0.810788] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.810795] pci 0000:00:1c.0: PME# disabled
[    0.810839] pci 0000:00:1c.1: [8086:3b44] type 1 class 0x000604
[    0.810992] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.811000] pci 0000:00:1c.1: PME# disabled
[    0.811045] pci 0000:00:1c.3: [8086:3b48] type 1 class 0x000604
[    0.811196] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.811203] pci 0000:00:1c.3: PME# disabled
[    0.811248] pci 0000:00:1c.4: [8086:3b4a] type 1 class 0x000604
[    0.811400] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.811407] pci 0000:00:1c.4: PME# disabled
[    0.811464] pci 0000:00:1d.0: [8086:3b34] type 0 class 0x000c03
[    0.811502] pci 0000:00:1d.0: reg 10: [mem 0xf2428400-0xf24287ff]
[    0.811662] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.811669] pci 0000:00:1d.0: PME# disabled
[    0.811707] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
[    0.811835] pci 0000:00:1f.0: [8086:3b07] type 0 class 0x000601
[    0.812024] pci 0000:00:1f.2: [8086:3b2f] type 0 class 0x000106
[    0.812065] pci 0000:00:1f.2: reg 10: [io  0x1818-0x181f]
[    0.812082] pci 0000:00:1f.2: reg 14: [io  0x180c-0x180f]
[    0.812099] pci 0000:00:1f.2: reg 18: [io  0x1810-0x1817]
[    0.812115] pci 0000:00:1f.2: reg 1c: [io  0x1808-0x180b]
[    0.812131] pci 0000:00:1f.2: reg 20: [io  0x1840-0x185f]
[    0.812148] pci 0000:00:1f.2: reg 24: [mem 0xf2427000-0xf24277ff]
[    0.812249] pci 0000:00:1f.2: PME# supported from D3hot
[    0.812256] pci 0000:00:1f.2: PME# disabled
[    0.812290] pci 0000:00:1f.3: [8086:3b30] type 0 class 0x000c05
[    0.812323] pci 0000:00:1f.3: reg 10: [mem 0xf2428800-0xf24288ff 64bit]
[    0.812368] pci 0000:00:1f.3: reg 20: [io  0x1860-0x187f]
[    0.812442] pci 0000:00:1f.6: [8086:3b32] type 0 class 0x001180
[    0.812483] pci 0000:00:1f.6: reg 10: [mem 0xf2426000-0xf2426fff 64bit]
[    0.812690] pci 0000:01:00.0: [10de:0a6c] type 0 class 0x000300
[    0.812711] pci 0000:01:00.0: reg 10: [mem 0xcc000000-0xccffffff]
[    0.812733] pci 0000:01:00.0: reg 14: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.812755] pci 0000:01:00.0: reg 1c: [mem 0xce000000-0xcfffffff 64bit pref]
[    0.812771] pci 0000:01:00.0: reg 24: [io  0x2000-0x207f]
[    0.812787] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0007ffff pref]
[    0.812904] pci 0000:01:00.1: [10de:0be3] type 0 class 0x000403
[    0.812924] pci 0000:01:00.1: reg 10: [mem 0xcdefc000-0xcdefffff]
[    0.813112] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.813117] pci 0000:00:01.0:   bridge window [io  0x2000-0x2fff]
[    0.813123] pci 0000:00:01.0:   bridge window [mem 0xcc000000-0xcdefffff]
[    0.813130] pci 0000:00:01.0:   bridge window [mem 0xce000000-0xdfffffff 64bit pref]
[    0.813213] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.813359] pci 0000:03:00.0: [8086:4238] type 0 class 0x000280
[    0.813409] pci 0000:03:00.0: reg 10: [mem 0xf2000000-0xf2001fff 64bit]
[    0.813643] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[    0.813654] pci 0000:03:00.0: PME# disabled
[    0.821246] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    0.821258] pci 0000:00:1c.1:   bridge window [mem 0xf2000000-0xf20fffff]
[    0.821352] pci 0000:00:1c.3: PCI bridge to [bus 05-0c]
[    0.821359] pci 0000:00:1c.3:   bridge window [io  0x3000-0x3fff]
[    0.821367] pci 0000:00:1c.3:   bridge window [mem 0xf0000000-0xf1ffffff]
[    0.821379] pci 0000:00:1c.3:   bridge window [mem 0xf2500000-0xf25fffff 64bit pref]
[    0.821543] pci 0000:0d:00.0: [1180:e822] type 0 class 0x000805
[    0.821565] pci 0000:0d:00.0: MMC controller base frequency changed to 50Mhz.
[    0.821597] pci 0000:0d:00.0: reg 10: [mem 0xf2100000-0xf21000ff]
[    0.821807] pci 0000:0d:00.0: supports D1 D2
[    0.821810] pci 0000:0d:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.821850] pci 0000:0d:00.0: PME# disabled
[    0.821919] pci 0000:0d:00.1: [1180:e230] type 0 class 0x000880
[    0.821949] pci 0000:0d:00.1: reg 10: [mem 0xf2100400-0xf21004ff]
[    0.822159] pci 0000:0d:00.1: supports D1 D2
[    0.822163] pci 0000:0d:00.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.822175] pci 0000:0d:00.1: PME# disabled
[    0.822241] pci 0000:0d:00.3: [1180:e832] type 0 class 0x000c00
[    0.822271] pci 0000:0d:00.3: reg 10: [mem 0xf2100800-0xf2100fff]
[    0.822480] pci 0000:0d:00.3: supports D1 D2
[    0.822483] pci 0000:0d:00.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.822523] pci 0000:0d:00.3: PME# disabled
[    0.829283] pci 0000:00:1c.4: PCI bridge to [bus 0d-0d]
[    0.829295] pci 0000:00:1c.4:   bridge window [mem 0xf2100000-0xf21fffff]
[    0.829416] pci 0000:00:1e.0: PCI bridge to [bus 0e-0e] (subtractive decode)
[    0.829436] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.829440] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.829445] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.829449] pci 0000:00:1e.0:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.829454] pci 0000:00:1e.0:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.829459] pci 0000:00:1e.0:   bridge window [mem 0xc0000000-0xfebfffff] (subtractive decode)
[    0.829510] pci_bus 0000:00: on NUMA node 0
[    0.829516] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.829734] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEG_._PRT]
[    0.829796] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[    0.829851] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[    0.829909] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP4._PRT]
[    0.829971] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP5._PRT]
[    0.830229]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.830565]  pci0000:00: ACPI _OSC request failed (AE_SUPPORT), returned control mask: 0x0d
[    0.830569] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.837721] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11)
[    0.837842] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)
[    0.837939] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[    0.838057] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
[    0.838174] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11)
[    0.838290] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11)
[    0.838386] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[    0.838504] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11)
[    0.838728] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.838736] vgaarb: loaded
[    0.838738] vgaarb: bridge control possible 0000:01:00.0
[    0.838924] i2c-core: driver [aat2870] using legacy suspend method
[    0.838927] i2c-core: driver [aat2870] using legacy resume method
[    0.839057] SCSI subsystem initialized
[    0.839137] libata version 3.00 loaded.
[    0.839213] usbcore: registered new interface driver usbfs
[    0.839232] usbcore: registered new interface driver hub
[    0.839277] usbcore: registered new device driver usb
[    0.839434] PCI: Using ACPI for IRQ routing
[    0.851294] PCI: pci_cache_line_size set to 64 bytes
[    0.851563] reserve RAM buffer: 000000000009e800 - 000000000009ffff 
[    0.851568] reserve RAM buffer: 00000000bf27c000 - 00000000bfffffff 
[    0.851576] reserve RAM buffer: 00000000bf35f000 - 00000000bfffffff 
[    0.851583] reserve RAM buffer: 00000000bf46f000 - 00000000bfffffff 
[    0.851590] reserve RAM buffer: 00000000bf717000 - 00000000bfffffff 
[    0.851595] reserve RAM buffer: 00000000bf76c000 - 00000000bfffffff 
[    0.851601] reserve RAM buffer: 00000000bf800000 - 00000000bfffffff 
[    0.851765] NetLabel: Initializing
[    0.851769] NetLabel:  domain hash size = 128
[    0.851771] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.851788] NetLabel:  unlabeled traffic allowed by default
[    0.851906] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.851918] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.853951] Switching to clocksource hpet
[    0.866157] AppArmor: AppArmor Filesystem Enabled
[    0.866195] pnp: PnP ACPI init
[    0.866221] ACPI: bus type pnp registered
[    0.868055] pnp 00:00: [mem 0x00000000-0x0009ffff]
[    0.868059] pnp 00:00: [mem 0x000c0000-0x000c3fff]
[    0.868063] pnp 00:00: [mem 0x000c4000-0x000c7fff]
[    0.868067] pnp 00:00: [mem 0x000c8000-0x000cbfff]
[    0.868071] pnp 00:00: [mem 0x000cc000-0x000cffff]
[    0.868074] pnp 00:00: [mem 0x000d0000-0x000d3fff]
[    0.868078] pnp 00:00: [mem 0x000d4000-0x000d3fff disabled]
[    0.868082] pnp 00:00: [mem 0x000d8000-0x000d7fff disabled]
[    0.868086] pnp 00:00: [mem 0x000dc000-0x000dffff]
[    0.868090] pnp 00:00: [mem 0x000e0000-0x000e3fff]
[    0.868093] pnp 00:00: [mem 0x000e4000-0x000e7fff]
[    0.868097] pnp 00:00: [mem 0x000e8000-0x000ebfff]
[    0.868100] pnp 00:00: [mem 0x000ec000-0x000effff]
[    0.868107] pnp 00:00: [mem 0x000f0000-0x000fffff]
[    0.868110] pnp 00:00: [mem 0x00100000-0xbfffffff]
[    0.868114] pnp 00:00: [mem 0xfec00000-0xfed3ffff]
[    0.868118] pnp 00:00: [mem 0xfed4c000-0xffffffff]
[    0.868244] system 00:00: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.868250] system 00:00: [mem 0x000c0000-0x000c3fff] could not be reserved
[    0.868255] system 00:00: [mem 0x000c4000-0x000c7fff] could not be reserved
[    0.868259] system 00:00: [mem 0x000c8000-0x000cbfff] has been reserved
[    0.868264] system 00:00: [mem 0x000cc000-0x000cffff] could not be reserved
[    0.868269] system 00:00: [mem 0x000d0000-0x000d3fff] could not be reserved
[    0.868274] system 00:00: [mem 0x000dc000-0x000dffff] could not be reserved
[    0.868279] system 00:00: [mem 0x000e0000-0x000e3fff] could not be reserved
[    0.868284] system 00:00: [mem 0x000e4000-0x000e7fff] could not be reserved
[    0.868288] system 00:00: [mem 0x000e8000-0x000ebfff] could not be reserved
[    0.868293] system 00:00: [mem 0x000ec000-0x000effff] could not be reserved
[    0.868298] system 00:00: [mem 0x000f0000-0x000fffff] could not be reserved
[    0.868303] system 00:00: [mem 0x00100000-0xbfffffff] could not be reserved
[    0.868309] system 00:00: [mem 0xfec00000-0xfed3ffff] could not be reserved
[    0.868314] system 00:00: [mem 0xfed4c000-0xffffffff] could not be reserved
[    0.868321] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.868345] pnp 00:01: [bus ff]
[    0.868438] pnp 00:01: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.868471] pnp 00:02: [bus 00-fe]
[    0.868475] pnp 00:02: [io  0x0cf8-0x0cff]
[    0.868479] pnp 00:02: [io  0x0000-0x0cf7 window]
[    0.868483] pnp 00:02: [io  0x0d00-0xffff window]
[    0.868487] pnp 00:02: [mem 0x000a0000-0x000bffff window]
[    0.868491] pnp 00:02: [mem 0x000c0000-0x000c3fff window]
[    0.868495] pnp 00:02: [mem 0x000c4000-0x000c7fff window]
[    0.868499] pnp 00:02: [mem 0x000c8000-0x000cbfff window]
[    0.868503] pnp 00:02: [mem 0x000cc000-0x000cffff window]
[    0.868507] pnp 00:02: [mem 0x000d0000-0x000d3fff window]
[    0.868511] pnp 00:02: [mem 0x000d4000-0x000d7fff window]
[    0.868515] pnp 00:02: [mem 0x000d8000-0x000dbfff window]
[    0.868519] pnp 00:02: [mem 0x000dc000-0x000dffff window]
[    0.868523] pnp 00:02: [mem 0x000e0000-0x000e3fff window]
[    0.868526] pnp 00:02: [mem 0x000e4000-0x000e7fff window]
[    0.868530] pnp 00:02: [mem 0x000e8000-0x000ebfff window]
[    0.868534] pnp 00:02: [mem 0x000ec000-0x000effff window]
[    0.868538] pnp 00:02: [mem 0xc0000000-0xfebfffff window]
[    0.868542] pnp 00:02: [mem 0xfed40000-0xfed4bfff window]
[    0.868626] pnp 00:02: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.869037] pnp 00:03: [io  0x0010-0x001f]
[    0.869041] pnp 00:03: [io  0x0090-0x009f]
[    0.869045] pnp 00:03: [io  0x0024-0x0025]
[    0.869048] pnp 00:03: [io  0x0028-0x0029]
[    0.869052] pnp 00:03: [io  0x002c-0x002d]
[    0.869055] pnp 00:03: [io  0x0030-0x0031]
[    0.869058] pnp 00:03: [io  0x0034-0x0035]
[    0.869062] pnp 00:03: [io  0x0038-0x0039]
[    0.869065] pnp 00:03: [io  0x003c-0x003d]
[    0.869068] pnp 00:03: [io  0x00a4-0x00a5]
[    0.869072] pnp 00:03: [io  0x00a8-0x00a9]
[    0.869075] pnp 00:03: [io  0x00ac-0x00ad]
[    0.869078] pnp 00:03: [io  0x00b0-0x00b5]
[    0.869081] pnp 00:03: [io  0x00b8-0x00b9]
[    0.869085] pnp 00:03: [io  0x00bc-0x00bd]
[    0.869088] pnp 00:03: [io  0x0050-0x0053]
[    0.869091] pnp 00:03: [io  0x0072-0x0077]
[    0.869095] pnp 00:03: [io  0x164e-0x164f]
[    0.869098] pnp 00:03: [io  0x002e-0x002f]
[    0.869102] pnp 00:03: [io  0x1000-0x107f]
[    0.869105] pnp 00:03: [io  0x1180-0x11ff]
[    0.869109] pnp 00:03: [io  0x0800-0x080f]
[    0.869112] pnp 00:03: [io  0x15e0-0x15ef]
[    0.869115] pnp 00:03: [io  0x1600-0x1641]
[    0.869119] pnp 00:03: [io  0x1644-0x167f]
[    0.869122] pnp 00:03: [mem 0xe0000000-0xefffffff]
[    0.869126] pnp 00:03: [mem 0xfeaff000-0xfeafffff]
[    0.869130] pnp 00:03: [mem 0xfed1c000-0xfed1ffff]
[    0.869133] pnp 00:03: [mem 0xfed10000-0xfed13fff]
[    0.869137] pnp 00:03: [mem 0xfed18000-0xfed18fff]
[    0.869140] pnp 00:03: [mem 0xfed19000-0xfed19fff]
[    0.869144] pnp 00:03: [mem 0xfed45000-0xfed4bfff]
[    0.869294] system 00:03: [io  0x164e-0x164f] has been reserved
[    0.869300] system 00:03: [io  0x1000-0x107f] has been reserved
[    0.869304] system 00:03: [io  0x1180-0x11ff] has been reserved
[    0.869309] system 00:03: [io  0x0800-0x080f] has been reserved
[    0.869314] system 00:03: [io  0x15e0-0x15ef] has been reserved
[    0.869319] system 00:03: [io  0x1600-0x1641] has been reserved
[    0.869323] system 00:03: [io  0x1644-0x167f] could not be reserved
[    0.869329] system 00:03: [mem 0xe0000000-0xefffffff] has been reserved
[    0.869341] system 00:03: [mem 0xfeaff000-0xfeafffff] has been reserved
[    0.869346] system 00:03: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.869351] system 00:03: [mem 0xfed10000-0xfed13fff] has been reserved
[    0.869356] system 00:03: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.869361] system 00:03: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.869366] system 00:03: [mem 0xfed45000-0xfed4bfff] has been reserved
[    0.869372] system 00:03: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.869427] pnp 00:04: [mem 0xfed00000-0xfed003ff]
[    0.869486] pnp 00:04: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.869503] pnp 00:05: [io  0x0000-0x000f]
[    0.869506] pnp 00:05: [io  0x0080-0x008f]
[    0.869510] pnp 00:05: [io  0x00c0-0x00df]
[    0.869514] pnp 00:05: [dma 4]
[    0.869567] pnp 00:05: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.869582] pnp 00:06: [io  0x0061]
[    0.869635] pnp 00:06: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.869650] pnp 00:07: [io  0x00f0]
[    0.869665] pnp 00:07: [irq 13]
[    0.869722] pnp 00:07: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.869738] pnp 00:08: [io  0x0070-0x0071]
[    0.869746] pnp 00:08: [irq 8]
[    0.869802] pnp 00:08: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.869817] pnp 00:09: [io  0x0060]
[    0.869821] pnp 00:09: [io  0x0064]
[    0.869828] pnp 00:09: [irq 1]
[    0.869884] pnp 00:09: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.869903] pnp 00:0a: [irq 12]
[    0.869986] pnp 00:0a: Plug and Play ACPI device, IDs LEN0015 PNP0f13 (active)
[    0.870419] pnp 00:0b: [mem 0xfed40000-0xfed44fff]
[    0.870482] pnp 00:0b: Plug and Play ACPI device, IDs SMO1200 PNP0c31 (active)
[    0.871634] pnp: PnP ACPI: found 12 devices
[    0.871640] ACPI: ACPI bus type pnp unregistered
[    0.871647] PnPBIOS: Disabled by ACPI PNP
[    0.911580] PCI: max bus depth: 1 pci_try_num: 2
[    0.911688] pci 0000:01:00.0: BAR 6: assigned [mem 0xcd000000-0xcd07ffff pref]
[    0.911696] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.911705] pci 0000:00:01.0:   bridge window [io  0x2000-0x2fff]
[    0.911714] pci 0000:00:01.0:   bridge window [mem 0xcc000000-0xcdefffff]
[    0.911723] pci 0000:00:01.0:   bridge window [mem 0xce000000-0xdfffffff 64bit pref]
[    0.911734] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.911760] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    0.911773] pci 0000:00:1c.1:   bridge window [mem 0xf2000000-0xf20fffff]
[    0.911793] pci 0000:00:1c.3: PCI bridge to [bus 05-0c]
[    0.911801] pci 0000:00:1c.3:   bridge window [io  0x3000-0x3fff]
[    0.911814] pci 0000:00:1c.3:   bridge window [mem 0xf0000000-0xf1ffffff]
[    0.911826] pci 0000:00:1c.3:   bridge window [mem 0xf2500000-0xf25fffff 64bit pref]
[    0.911843] pci 0000:00:1c.4: PCI bridge to [bus 0d-0d]
[    0.911855] pci 0000:00:1c.4:   bridge window [mem 0xf2100000-0xf21fffff]
[    0.911875] pci 0000:00:1e.0: PCI bridge to [bus 0e-0e]
[    0.911927] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.911936] pci 0000:00:01.0: setting latency timer to 64
[    0.911961] pci 0000:00:1c.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.911973] pci 0000:00:1c.0: setting latency timer to 64
[    0.911998] pci 0000:00:1c.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.912007] pci 0000:00:1c.1: setting latency timer to 64
[    0.912031] pci 0000:00:1c.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.912042] pci 0000:00:1c.3: setting latency timer to 64
[    0.912058] pci 0000:00:1c.4: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.912068] pci 0000:00:1c.4: setting latency timer to 64
[    0.912084] pci 0000:00:1e.0: setting latency timer to 64
[    0.912095] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.912102] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.912109] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.912115] pci_bus 0000:00: resource 7 [mem 0x000d4000-0x000d7fff]
[    0.912122] pci_bus 0000:00: resource 8 [mem 0x000d8000-0x000dbfff]
[    0.912129] pci_bus 0000:00: resource 9 [mem 0xc0000000-0xfebfffff]
[    0.912136] pci_bus 0000:01: resource 0 [io  0x2000-0x2fff]
[    0.912143] pci_bus 0000:01: resource 1 [mem 0xcc000000-0xcdefffff]
[    0.912150] pci_bus 0000:01: resource 2 [mem 0xce000000-0xdfffffff 64bit pref]
[    0.912158] pci_bus 0000:03: resource 1 [mem 0xf2000000-0xf20fffff]
[    0.912165] pci_bus 0000:05: resource 0 [io  0x3000-0x3fff]
[    0.912172] pci_bus 0000:05: resource 1 [mem 0xf0000000-0xf1ffffff]
[    0.912179] pci_bus 0000:05: resource 2 [mem 0xf2500000-0xf25fffff 64bit pref]
[    0.912187] pci_bus 0000:0d: resource 1 [mem 0xf2100000-0xf21fffff]
[    0.912194] pci_bus 0000:0e: resource 4 [io  0x0000-0x0cf7]
[    0.912200] pci_bus 0000:0e: resource 5 [io  0x0d00-0xffff]
[    0.912207] pci_bus 0000:0e: resource 6 [mem 0x000a0000-0x000bffff]
[    0.912214] pci_bus 0000:0e: resource 7 [mem 0x000d4000-0x000d7fff]
[    0.912221] pci_bus 0000:0e: resource 8 [mem 0x000d8000-0x000dbfff]
[    0.912228] pci_bus 0000:0e: resource 9 [mem 0xc0000000-0xfebfffff]
[    0.912318] NET: Registered protocol family 2
[    0.912463] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.912953] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.914368] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.915072] TCP: Hash tables configured (established 131072 bind 65536)
[    0.915078] TCP reno registered
[    0.915086] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.915109] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.915257] NET: Registered protocol family 1
[    0.915329] pci 0000:00:1a.0: power state changed by ACPI to D0
[    0.915339] pci 0000:00:1a.0: power state changed by ACPI to D0
[    0.915353] pci 0000:00:1a.0: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.915405] pci 0000:00:1a.0: PCI INT D disabled
[    0.915445] pci 0000:00:1d.0: power state changed by ACPI to D0
[    0.915455] pci 0000:00:1d.0: power state changed by ACPI to D0
[    0.915479] pci 0000:00:1d.0: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.915516] pci 0000:00:1d.0: PCI INT D disabled
[    0.915574] pci 0000:01:00.0: Boot video device
[    0.915667] PCI: CLS 64 bytes, default 64
[    0.915677] Simple Boot Flag at 0x35 set to 0x1
[    0.916902] audit: initializing netlink socket (disabled)
[    0.916918] type=2000 audit(1376472133.656:1): initialized
[    0.975497] highmem bounce pool size: 64 pages
[    0.975509] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.981371] VFS: Disk quotas dquot_6.5.2
[    0.981529] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.982982] fuse init (API version 7.17)
[    0.983231] msgmni has been set to 1605
[    0.984033] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.984092] io scheduler noop registered
[    0.984097] io scheduler deadline registered
[    0.984115] io scheduler cfq registered (default)
[    0.984385] pcieport 0000:00:01.0: setting latency timer to 64
[    0.984447] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.984984] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.985045] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.985201] intel_idle: MWAIT substates: 0x1120
[    0.985206] intel_idle: v0.4 model 0x25
[    0.985210] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.985511] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.985717] ACPI: AC Adapter [AC] (off-line)
[    0.985981] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.986229] ACPI: Lid Switch [LID]
[    0.986306] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.986314] ACPI: Sleep Button [SLPB]
[    0.986401] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.986406] ACPI: Power Button [PWRF]
[    0.999702] thermal LNXTHERM:00: registered as thermal_zone0
[    0.999707] ACPI: Thermal Zone [THM0] (48 C)
[    0.999743] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.999757] ACPI: Battery Slot [BAT0] (battery present)
[    0.999820] ERST: Table is not found!
[    0.999825] GHES: HEST is not enabled!
[    0.999978] isapnp: Scanning for PnP cards...
[    0.999985] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.016207] ACPI: Battery Slot [BAT0] (battery present)
[    1.354748] isapnp: No Plug & Play device found
[    1.492977] Freeing initrd memory: 19348k freed
[    1.584450] serial 0000:00:16.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.604884] 0000:00:16.3: ttyS4 at I/O 0x1800 (irq = 17) is a 16550A
[    1.624365] Linux agpgart interface v0.103
[    1.627284] brd: module loaded
[    1.628668] loop: module loaded
[    1.628884] ahci 0000:00:1f.2: version 3.0
[    1.628899] ahci 0000:00:1f.2: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    1.628970] ahci 0000:00:1f.2: irq 41 for MSI/MSI-X
[    1.629024] ahci: SSS flag set, parallel bus scan disabled
[    1.629081] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 3 Gbps 0x33 impl SATA mode
[    1.629088] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck stag pm led clo pmp pio slum part ems sxs apst 
[    1.629097] ahci 0000:00:1f.2: setting latency timer to 64
[    1.652898] scsi0 : ahci
[    1.653049] scsi1 : ahci
[    1.653180] scsi2 : ahci
[    1.653319] scsi3 : ahci
[    1.653450] scsi4 : ahci
[    1.653580] scsi5 : ahci
[    1.654404] ata1: SATA max UDMA/133 abar m2048@0xf2427000 port 0xf2427100 irq 41
[    1.654411] ata2: SATA max UDMA/133 abar m2048@0xf2427000 port 0xf2427180 irq 41
[    1.654415] ata3: DUMMY
[    1.654417] ata4: DUMMY
[    1.654421] ata5: SATA max UDMA/133 abar m2048@0xf2427000 port 0xf2427300 irq 41
[    1.654427] ata6: SATA max UDMA/133 abar m2048@0xf2427000 port 0xf2427380 irq 41
[    1.655096] Fixed MDIO Bus: probed
[    1.655130] tun: Universal TUN/TAP device driver, 1.6
[    1.655133] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.655211] PPP generic driver version 2.4.2
[    1.655369] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.655392] ehci_hcd 0000:00:1a.0: power state changed by ACPI to D0
[    1.655399] ehci_hcd 0000:00:1a.0: power state changed by ACPI to D0
[    1.655410] ehci_hcd 0000:00:1a.0: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    1.655433] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.655439] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    1.655527] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.655567] ehci_hcd 0000:00:1a.0: debug port 2
[    1.659464] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    1.659488] ehci_hcd 0000:00:1a.0: irq 23, io mem 0xf2428000
[    1.671945] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.672163] hub 1-0:1.0: USB hub found
[    1.672170] hub 1-0:1.0: 3 ports detected
[    1.672294] ehci_hcd 0000:00:1d.0: power state changed by ACPI to D0
[    1.672301] ehci_hcd 0000:00:1d.0: power state changed by ACPI to D0
[    1.672312] ehci_hcd 0000:00:1d.0: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    1.672334] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.672340] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    1.672418] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.672456] ehci_hcd 0000:00:1d.0: debug port 2
[    1.676360] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    1.676383] ehci_hcd 0000:00:1d.0: irq 19, io mem 0xf2428400
[    1.691895] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.692094] hub 2-0:1.0: USB hub found
[    1.692101] hub 2-0:1.0: 3 ports detected
[    1.692214] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.692237] uhci_hcd: USB Universal Host Controller Interface driver
[    1.692323] usbcore: registered new interface driver libusual
[    1.692399] i8042: PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    1.695429] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.695439] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.695650] mousedev: PS/2 mouse device common for all mice
[    1.695972] rtc_cmos 00:08: RTC can wake from S4
[    1.696138] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
[    1.696175] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.696270] device-mapper: uevent: version 1.0.3
[    1.696394] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    1.696426] EISA: Probing bus 0 at eisa.0
[    1.696430] EISA: Cannot allocate resource for mainboard
[    1.696436] Cannot allocate resource for EISA slot 1
[    1.696443] Cannot allocate resource for EISA slot 2
[    1.696446] Cannot allocate resource for EISA slot 3
[    1.696449] Cannot allocate resource for EISA slot 4
[    1.696452] Cannot allocate resource for EISA slot 5
[    1.696455] Cannot allocate resource for EISA slot 6
[    1.696458] Cannot allocate resource for EISA slot 7
[    1.696461] Cannot allocate resource for EISA slot 8
[    1.696464] EISA: Detected 0 cards.
[    1.696478] cpufreq-nforce2: No nForce2 chipset.
[    1.696665] cpuidle: using governor ladder
[    1.696980] cpuidle: using governor menu
[    1.696984] EFI Variables Facility v0.08 2004-May-17
[    1.697373] TCP cubic registered
[    1.697580] NET: Registered protocol family 10
[    1.698442] NET: Registered protocol family 17
[    1.698449] Registering the dns_resolver key type
[    1.698479] Using IPI No-Shortcut mode
[    1.698704] PM: Hibernation image not present or could not be loaded.
[    1.698722] registered taskstats version 1
[    1.699163] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.712047]   Magic number: 9:838:373
[    1.712086] vc vcsa1: hash matches
[    1.712100] pci 0000:ff:00.1: hash matches
[    1.712229] rtc_cmos 00:08: setting system clock to 2013-08-14 09:22:15 UTC (1376472135)
[    1.715572] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.715573] EDD information not available.
[    1.911493] Refined TSC clocksource calibration: 2660.000 MHz.
[    1.911501] Switching to clocksource tsc
[    1.983221] usb 1-1: new high-speed USB device number 2 using ehci_hcd
[    2.116024] hub 1-1:1.0: USB hub found
[    2.116247] hub 1-1:1.0: 6 ports detected
[    2.142829] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.144186] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[    2.144193] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    2.144449] ata1.00: ACPI cmd ef/5f:00:00:00:00:a0 (SET FEATURES) succeeded
[    2.144456] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    2.145538] ata1.00: ATA-8: HITACHI HTS725050A9A364, PC4ZC70F, max UDMA/100
[    2.145543] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.146763] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[    2.146770] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    2.147016] ata1.00: ACPI cmd ef/5f:00:00:00:00:a0 (SET FEATURES) succeeded
[    2.147022] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    2.148106] ata1.00: configured for UDMA/100
[    2.148478] scsi 0:0:0:0: Direct-Access     ATA      HITACHI HTS72505 PC4Z PQ: 0 ANSI: 5
[    2.148783] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    2.148790] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.148955] sd 0:0:0:0: [sda] Write Protect is off
[    2.148960] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.149085] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.204817]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
[    2.206574] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.226586] usb 2-1: new high-speed USB device number 2 using ehci_hcd
[    2.359159] hub 2-1:1.0: USB hub found
[    2.359365] hub 2-1:1.0: 8 ports detected
[    2.430315] usb 1-1.3: new full-speed USB device number 3 using ehci_hcd
[    2.593924] usb 1-1.4: new full-speed USB device number 4 using ehci_hcd
[    2.637584] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.645220] ata2.00: ACPI cmd e3/00:1f:00:00:00:a0 (IDLE) succeeded
[    2.650227] ata2.00: ACPI cmd e3/00:02:00:00:00:a0 (IDLE) succeeded
[    2.651962] ata2.00: ATAPI: Optiarc DVD RW AD-7930H, 1.D0, max UDMA/100
[    2.664442] ata2.00: ACPI cmd e3/00:1f:00:00:00:a0 (IDLE) succeeded
[    2.669481] ata2.00: ACPI cmd e3/00:02:00:00:00:a0 (IDLE) succeeded
[    2.671217] ata2.00: configured for UDMA/100
[    2.687180] scsi 1:0:0:0: CD-ROM            Optiarc  DVD RW AD-7930H  1.D0 PQ: 0 ANSI: 5
[    2.703895] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.703901] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.704177] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.704353] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.761499] usb 1-1.6: new high-speed USB device number 5 using ehci_hcd
[    2.929106] usb 2-1.1: new low-speed USB device number 3 using ehci_hcd
[    3.020636] ata5: SATA link down (SStatus 0 SControl 300)
[    3.096686] usb 2-1.4: new high-speed USB device number 4 using ehci_hcd
[    3.190298] usb 2-1.4: config 1 has an invalid interface number: 1 but max is 0
[    3.190303] usb 2-1.4: config 1 has no interface number 0
[    3.339833] ata6: SATA link down (SStatus 0 SControl 300)
[    3.340119] Freeing unused kernel memory: 744k freed
[    3.340396] Write protecting the kernel text: 5840k
[    3.340423] Write protecting the kernel read-only data: 2388k
[    3.340424] NX-protecting the kernel data: 4400k
[    3.358569] udevd[108]: starting version 175
[    3.381406] e1000e: Intel(R) PRO/1000 Network Driver - 1.5.1-k
[    3.381408] e1000e: Copyright(c) 1999 - 2011 Intel Corporation.
[    3.381445] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    3.381457] e1000e 0000:00:19.0: setting latency timer to 64
[    3.381601] e1000e 0000:00:19.0: irq 42 for MSI/MSI-X
[    3.383586] sdhci: Secure Digital Host Controller Interface driver
[    3.383588] sdhci: Copyright(c) Pierre Ossman
[    3.383897] sdhci-pci 0000:0d:00.0: SDHCI controller found [1180:e822] (rev 1)
[    3.383958] sdhci-pci 0000:0d:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.384027] sdhci-pci 0000:0d:00.0: Will use DMA mode even though HW doesn't fully claim to support it.
[    3.384035] sdhci-pci 0000:0d:00.0: setting latency timer to 64
[    3.384061] mmc0: no vmmc regulator found
[    3.384140] Registered led device: mmc0::
[    3.389155] mmc0: SDHCI controller on PCI [0000:0d:00.0] using DMA
[    3.389605] firewire_ohci 0000:0d:00.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    3.389650] firewire_ohci 0000:0d:00.3: setting latency timer to 64
[    3.394839] input: HID 0430:0100 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.0/input/input4
[    3.394950] generic-usb 0003:0430:0100.0001: input,hidraw0: USB HID v1.10 Mouse [HID 0430:0100] on usb-0000:00:1d.0-1.1/input0
[    3.394969] usbcore: registered new interface driver usbhid
[    3.394971] usbhid: USB HID core driver
[    3.415144] acpi device:0b: registered as cooling_device4
[    3.415338] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:0a/LNXVIDEO:01/input/input5
[    3.415843] ACPI: Video Device [VID1] (multi-head: yes  rom: yes  post: no)
[    3.451585] firewire_ohci: Added fw-ohci device 0000:0d:00.3, OHCI v1.10, 4 IR + 4 IT contexts, quirks 0x11
[    3.560145] e1000e 0000:00:19.0: eth0: (PCI Express:2.5GT/s:Width x1) 5c:ff:35:01:e7:aa
[    3.560148] e1000e 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    3.560199] e1000e 0000:00:19.0: eth0: MAC: 9, PHY: 10, PBA No: A002FF-0FF
[    3.950481] firewire_core: created device fw0: GUID 5cff35ff01e7aaff, S400
[    4.970253] vesafb: mode is 640x480x32, linelength=2560, pages=0
[    4.970255] vesafb: scrolling: redraw
[    4.970258] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    4.972058] vesafb: framebuffer at 0xcf000000, mapped to 0xf8600000, using 1216k, total 1216k
[    4.972231] Console: switching to colour frame buffer device 80x30
[    4.972256] fb0: VESA VGA frame buffer device
[    5.230971] EXT4-fs (sda5): INFO: recovery required on readonly filesystem
[    5.230973] EXT4-fs (sda5): write access will be enabled during recovery
[   11.396037] EXT4-fs (sda5): recovery complete
[   11.396339] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[   32.754774] Adding 9034748k swap on /dev/sda6.  Priority:-1 extents:1 across:9034748k 
[   32.758704] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   32.791554] udevd[392]: starting version 175
[   32.798865] lp: driver loaded but no devices found
[   32.802535] hdaps: supported laptop not found!
[   32.802537] hdaps: driver init failed (ret=-19)!
[   32.825950] nvidia: module license 'NVIDIA' taints kernel.
[   32.825954] Disabling lock debugging due to kernel taint
[   32.833236] cfg80211: Calling CRDA to update world regulatory domain
[   32.845553] mei: module is from the staging directory, the quality is unknown, you have been warned.
[   32.849666] mei 0000:00:16.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   32.849675] mei 0000:00:16.0: setting latency timer to 64
[   32.849925] mei 0000:00:16.0: irq 43 for MSI/MSI-X
[   32.876240] Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   32.876243] Copyright(c) 2003-2011 Intel Corporation
[   32.876296] iwlwifi 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   32.876305] iwlwifi 0000:03:00.0: setting latency timer to 64
[   32.876330] iwlwifi 0000:03:00.0: pci_resource_len = 0x00002000
[   32.876332] iwlwifi 0000:03:00.0: pci_resource_base = f84fc000
[   32.876334] iwlwifi 0000:03:00.0: HW Revision ID = 0x35
[   32.876414] iwlwifi 0000:03:00.0: irq 44 for MSI/MSI-X
[   32.876448] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Ultimate-N 6300 AGN, REV=0x74
[   32.876510] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   32.886377] iwlwifi 0000:03:00.0: device EEPROM VER=0x436, CALIB=0x6
[   32.886380] iwlwifi 0000:03:00.0: Device SKU: 0X1f0
[   32.886382] iwlwifi 0000:03:00.0: Valid Tx ant: 0X7, Valid Rx ant: 0X7
[   32.892284] iwlwifi 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   32.900320] Non-volatile memory driver v1.3
[   32.902523] thinkpad_acpi: ThinkPad ACPI Extras v0.24
[   32.902525] thinkpad_acpi: http://ibm-acpi.sf.net/
[   32.902527] thinkpad_acpi: ThinkPad BIOS 6IET65WW (1.25 ), EC 6IHT35WW-1.10
[   32.902529] thinkpad_acpi: Lenovo ThinkPad T410, model 2522KDG
[   32.904484] wmi: Mapper loaded
[   32.915166] tpm_tis 00:0b: 1.2 TPM (device-id 0x0, rev-id 78)
[   32.922173] intel ips 0000:00:1f.6: CPU TDP doesn't match expected value (found 25, expected 29)
[   32.922188] intel ips 0000:00:1f.6: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[   32.922229] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled
[   32.924456] thinkpad_acpi: detected a 8-level brightness capable ThinkPad
[   32.930631] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 90
[   32.955466] snd_hda_intel 0000:00:1b.0: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   32.955545] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   32.955579] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   32.973262] nvidia 0000:01:00.0: power state changed by ACPI to D0
[   32.973272] nvidia 0000:01:00.0: power state changed by ACPI to D0
[   32.973282] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   32.973294] nvidia 0000:01:00.0: setting latency timer to 64
[   32.973300] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   32.973416] NVRM: loading NVIDIA UNIX x86 Kernel Module  304.88  Wed Mar 27 14:31:12 PDT 2013
[   32.975289] thinkpad_acpi: radio switch found; radios are enabled
[   32.975313] thinkpad_acpi: This ThinkPad has standard ACPI backlight brightness control, supported by the ACPI video driver
[   32.975316] thinkpad_acpi: Disabling thinkpad-acpi brightness events by default...
[   32.979034] thinkpad_acpi: rfkill switch tpacpi_bluetooth_sw: radio is unblocked
[   32.981613] thinkpad_acpi: rfkill switch tpacpi_wwan_sw: radio is unblocked
[   32.981948] Registered led device: tpacpi::thinklight
[   32.981982] Registered led device: tpacpi::power
[   32.982006] Registered led device: tpacpi::standby
[   32.982024] Registered led device: tpacpi::thinkvantage
[   32.983921] thinkpad_acpi: Standard ACPI backlight interface available, not loading native one
[   32.984086] thinkpad_acpi: Console audio control enabled, mode: monitor (read only)
[   32.986693] input: ThinkPad Extra Buttons as /devices/platform/thinkpad_acpi/input/input6
[   32.990005] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   32.990150] type=1400 audit(1376464966.852:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=645 comm="apparmor_parser"
[   32.990565] type=1400 audit(1376464966.852:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=645 comm="apparmor_parser"
[   32.990806] type=1400 audit(1376464966.852:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=645 comm="apparmor_parser"
[   33.007670] Bluetooth: Core ver 2.16
[   33.007690] NET: Registered protocol family 31
[   33.007692] Bluetooth: HCI device and connection manager initialized
[   33.007695] Bluetooth: HCI socket layer initialized
[   33.007697] Bluetooth: L2CAP socket layer initialized
[   33.007703] Bluetooth: SCO socket layer initialized
[   33.008003] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   33.009633] usbcore: registered new interface driver btusb
[   33.011210] snd_hda_intel 0000:01:00.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   33.011213] hda_intel: Disabling MSI
[   33.011252] snd_hda_intel 0000:01:00.1: setting latency timer to 64
[   33.023356] Linux video capture interface: v2.00
[   33.023872] uvcvideo: Found UVC 1.00 device Integrated Camera (17ef:480f)
[   33.028692] usbcore: registered new interface driver usbserial
[   33.028731] USB Serial support registered for generic
[   33.029798] input: Integrated Camera as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/input/input7
[   33.029876] usbcore: registered new interface driver uvcvideo
[   33.029878] USB Video Class driver (1.1.1)
[   33.029994] usbcore: registered new interface driver usbserial_generic
[   33.029997] usbserial: USB Serial Driver core
[   33.030695] USB Serial support registered for Qualcomm USB modem
[   33.030727] qcserial 2-1.4:1.1: Qualcomm USB modem converter detected
[   33.031081] usb 2-1.4: Qualcomm USB modem converter now attached to ttyUSB0
[   33.032136] usbcore: registered new interface driver qcserial
[   33.098052] cfg80211: World regulatory domain updated:
[   33.098055] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   33.098057] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   33.098059] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   33.098060] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   33.098062] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   33.098063] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   33.188097] iwlwifi 0000:03:00.0: loaded firmware version 9.221.4.1 build 25532
[   33.188348] Registered led device: phy0-led
[   33.188379] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   33.191202] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   33.404284] init: failsafe main process (1003) killed by TERM signal
[   33.495518] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   33.495521] Bluetooth: BNEP filters: protocol multicast
[   33.506043] Bluetooth: RFCOMM TTY layer initialized
[   33.506048] Bluetooth: RFCOMM socket layer initialized
[   33.506050] Bluetooth: RFCOMM ver 1.11
[   33.513477] ppdev: user-space parallel port driver
[   33.528328] type=1400 audit(1376464967.392:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1123 comm="apparmor_parser"
[   33.528983] type=1400 audit(1376464967.392:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1123 comm="apparmor_parser"
[   33.537022] type=1400 audit(1376464967.400:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1141 comm="apparmor_parser"
[   33.537426] type=1400 audit(1376464967.400:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=1141 comm="apparmor_parser"
[   33.541454] type=1400 audit(1376464967.404:9): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1142 comm="apparmor_parser"
[   33.541621] type=1400 audit(1376464967.404:10): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1140 comm="apparmor_parser"
[   33.541931] type=1400 audit(1376464967.404:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1142 comm="apparmor_parser"
[   33.835373] HDMI status: Codec=0 Pin=5 Presence_Detect=0 ELD_Valid=0
[   33.859271] HDMI status: Codec=1 Pin=5 Presence_Detect=0 ELD_Valid=0
[   33.883223] HDMI status: Codec=2 Pin=5 Presence_Detect=0 ELD_Valid=0
[   33.901107] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd047b3/0xb40000/0xa0000
[   33.901114] psmouse serio1: synaptics: serio: Synaptics pass-through port at isa0060/serio1/input0
[   33.912505] HDMI status: Codec=3 Pin=5 Presence_Detect=0 ELD_Valid=0
[   33.912788] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input8
[   33.913025] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input9
[   33.913427] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input10
[   33.913600] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input11
[   33.929798] usbcore: registered new interface driver Promethean ActivDriver
[   33.929802] 5.7.23:USB Activboard/Activhub Driver
[   33.952466] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input12
[   33.985683] init: gdm main process (1274) killed by TERM signal
[   34.006388] hdaps: supported laptop not found!
[   34.006391] hdaps: driver init failed (ret=-19)!
[   34.118834] e1000e 0000:00:19.0: irq 42 for MSI/MSI-X
[   34.174582] e1000e 0000:00:19.0: irq 42 for MSI/MSI-X
[   34.174817] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   34.175142] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   34.177998] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   34.178185] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1
[   34.378308] vboxdrv: Found 4 processor cores.
[   34.378468] vboxdrv: fAsync=0 offMin=0x157 offMax=0x17ff
[   34.378528] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   34.378531] vboxdrv: Successfully loaded version 4.1.12_Ubuntu (interface 0x00190000).
[   34.385745] vboxpci: IOMMU not found (not registered)
[   34.421834] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   34.422099] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1
[   34.546661] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   34.547136] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   35.756976] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: None
[   35.756981] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   35.757182] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   35.774555] NVRM: Your system is not currently configured to drive a VGA console
[   35.774559] NVRM: on the primary VGA device. The NVIDIA Linux graphics driver
[   35.774562] NVRM: requires the use of a text-mode VGA console. Use of other console
[   35.774564] NVRM: drivers including, but not limited to, vesafb, may result in
[   35.774566] NVRM: corruption and stability problems, and is not supported.
[   36.192775] cfg80211: Found new beacon on frequency: 2472 MHz (Ch 13) on phy0
[   36.251702] cfg80211: Found new beacon on frequency: 5180 MHz (Ch 36) on phy0
[   36.365007] cfg80211: Found new beacon on frequency: 5200 MHz (Ch 40) on phy0
[   36.365457] cfg80211: Found new beacon on frequency: 5200 MHz (Ch 40) on phy0
[   36.365751] cfg80211: Found new beacon on frequency: 5200 MHz (Ch 40) on phy0
[   36.409110] cfg80211: Found new beacon on frequency: 5200 MHz (Ch 40) on phy0
[   36.409500] cfg80211: Found new beacon on frequency: 5200 MHz (Ch 40) on phy0
[   36.409821] cfg80211: Found new beacon on frequency: 5200 MHz (Ch 40) on phy0
[   36.467164] cfg80211: Found new beacon on frequency: 5200 MHz (Ch 40) on phy0
[   36.467563] cfg80211: Found new beacon on frequency: 5200 MHz (Ch 40) on phy0
[   36.534949] cfg80211: Found new beacon on frequency: 5220 MHz (Ch 44) on phy0
[   36.535346] cfg80211: Found new beacon on frequency: 5220 MHz (Ch 44) on phy0
[   36.535603] cfg80211: Found new beacon on frequency: 5220 MHz (Ch 44) on phy0
[   36.539230] cfg80211: Found new beacon on frequency: 5220 MHz (Ch 44) on phy0
[   36.621799] cfg80211: Found new beacon on frequency: 5240 MHz (Ch 48) on phy0
[   36.622142] cfg80211: Found new beacon on frequency: 5240 MHz (Ch 48) on phy0
[   36.628469] cfg80211: Found new beacon on frequency: 5240 MHz (Ch 48) on phy0
[   36.628843] cfg80211: Found new beacon on frequency: 5240 MHz (Ch 48) on phy0
[   36.629190] cfg80211: Found new beacon on frequency: 5240 MHz (Ch 48) on phy0
[   41.122209] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   41.379927] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/serio2/input/input13
[   43.764093] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   43.764279] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1
[   43.902936] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   44.059231] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   44.059418] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1
[   44.194203] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   44.451966] e1000e 0000:00:19.0: irq 42 for MSI/MSI-X
[   44.504720] e1000e 0000:00:19.0: irq 42 for MSI/MSI-X
[   44.505033] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   44.912229] e1000e 0000:00:19.0: irq 42 for MSI/MSI-X
[   44.967617] e1000e 0000:00:19.0: irq 42 for MSI/MSI-X
[   44.967899] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   46.573860] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: None
[   46.573866] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   46.574021] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   92.517025] eth0: no IPv6 routers present
```

---

### Post by TheFu on 2013-08-14
Looks like you shutdown the PC without using the "shutdown" command. At the next boot, the file system saw it was inconsistent and corrected itself.  No big deal, but if you are using the shutdown command to end your computer use, then it is time to look at other logs in /var/log/* to learn more.

---

### Post by jolindbe on 2013-08-14
Thanks for the reply. I am shutting down the computer with the Shut Down dialogue, so that shouldn't be the problem. Which log files should I have a look at?

---

### Post by jolindbe on 2013-08-16
Does anybody have an idea of in which log files I should look to find out why the computer does not go through the shutdown properly?

---

### Post by TheFu on 2013-08-16
> **jolindbe said:**
> Thanks for the reply. I am shutting down the computer with the Shut Down dialogue, so that shouldn't be the problem. Which log files should I have a look at?

You should look at all of them - look for errors, warnings and anything else that seems "funny."
[http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files](http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files) should explain.

---

### Post by jolindbe on 2013-08-16
I ran the command "sudo egrep -i 'error|warning' /var/log/*log" as suggested on your linked page, and the output is a bit overwhelming... should I get these many errors/warnings? It is very difficult for me to see what is relevant and what is not.
I did a shutdown and then boot around Fri Aug 16 16:50, if that helps.

```

/var/log/apport.log:ERROR: apport (pid 7765) Fri Aug 16 11:55:28 2013: called for pid 3802, signal 11
/var/log/apport.log:ERROR: apport (pid 7765) Fri Aug 16 11:55:28 2013: executable: /usr/lib/firefox/firefox (command line "/usr/lib/firefox/firefox")
/var/log/apport.log:ERROR: apport (pid 7765) Fri Aug 16 11:55:29 2013: debug: session gdbus call: (true,)
/var/log/apport.log:ERROR: apport (pid 7765) Fri Aug 16 11:56:26 2013: wrote report /var/crash/_usr_lib_firefox_firefox.1000.crash
/var/log/auth.log:Aug 12 09:04:07 bilbo dbus[971]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.33" (uid=117 pid=2351 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.24" (uid=0 pid=1975 comm="/usr/sbin/console-kit-daemon --no-daemon ")
/var/log/auth.log:Aug 12 09:04:10 bilbo dbus[971]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.43" (uid=117 pid=2404 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.24" (uid=0 pid=1975 comm="/usr/sbin/console-kit-daemon --no-daemon ")
/var/log/auth.log:Aug 12 09:04:22 bilbo dbus[971]: [system] Rejected send message, 2 matched rules; type="method_return", sender=":1.3" (uid=0 pid=1031 comm="/usr/sbin/bluetoothd ") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.54" (uid=1000 pid=2567 comm="bluetooth-applet ")
/var/log/auth.log:Aug 12 09:05:25 bilbo dbus[971]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.70" (uid=1000 pid=3723 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.24" (uid=0 pid=1975 comm="/usr/sbin/console-kit-daemon --no-daemon ")
/var/log/auth.log:Aug 12 09:39:17 bilbo dbus[1098]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.30" (uid=117 pid=2299 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.22" (uid=0 pid=1833 comm="/usr/sbin/console-kit-daemon --no-daemon ")
/var/log/auth.log:Aug 12 09:39:27 bilbo dbus[1098]: [system] Rejected send message, 2 matched rules; type="method_return", sender=":1.2" (uid=0 pid=1123 comm="/usr/sbin/bluetoothd ") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.51" (uid=1000 pid=2752 comm="bluetooth-applet ")
/var/log/auth.log:Aug 12 09:40:21 bilbo dbus[1098]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.73" (uid=1000 pid=3470 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.22" (uid=0 pid=1833 comm="/usr/sbin/console-kit-daemon --no-daemon ")
/var/log/auth.log:Aug 12 19:15:08 bilbo dbus[1024]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.30" (uid=117 pid=2078 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.22" (uid=0 pid=1732 comm="/usr/sbin/console-kit-daemon --no-daemon ")
/var/log/auth.log:Aug 12 19:15:44 bilbo dbus[1024]: [system] Rejected send message, 2 matched rules; type="method_return", sender=":1.2" (uid=0 pid=1049 comm="/usr/sbin/bluetoothd ") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.50" (uid=1000 pid=2532 comm="bluetooth-applet ")
/var/log/auth.log:Aug 12 19:16:31 bilbo dbus[1024]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.68" (uid=1000 pid=3114 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.22" (uid=0 pid=1732 comm="/usr/sbin/console-kit-daemon --no-daemon ")
/var/log/auth.log:Aug 13 08:38:34 bilbo dbus[1016]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.30" (uid=117 pid=2059 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.22" (uid=0 pid=1714 comm="/usr/sbin/console-kit-daemon --no-daemon ")
/var/log/auth.log:Aug 13 08:38:45 bilbo lightdm: pam_winbind(lightdm:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
/var/log/auth.log:Aug 13 08:39:05 bilbo dbus[1016]: [system] Rejected send message, 2 matched rules; type="method_return", sender=":1.3" (uid=0 pid=1041 comm="/usr/sbin/bluetoothd ") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.49" (uid=1000 pid=2510 comm="bluetooth-applet ")
/var/log/auth.log:Aug 13 08:39:46 bilbo dbus[1016]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.68" (uid=1000 pid=3020 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.22" (uid=0 pid=1714 comm="/usr/sbin/console-kit-daemon --no-daemon ")
/var/log/auth.log:Aug 13 09:16:10 bilbo dbus[1016]: [system] Rejected send message, 3 matched rules; type="error", sender=":1.58" (uid=1000 pid=2497 comm="/usr/bin/pulseaudio --start --log-target=syslog ") interface="(unset)" member="(unset)" error name="org.freedesktop.DBus.Error.UnknownMethod" requested_reply="0" destination=":1.3" (uid=0 pid=1041 comm="/usr/sbin/bluetoothd ")
/var/log/auth.log:Aug 13 09:16:10 bilbo dbus[1016]: [system] Rejected send message, 3 matched rules; type="error", sender=":1.49" (uid=1000 pid=2510 comm="bluetooth-applet ") interface="(unset)" member="(unset)" error name="org.freedesktop.DBus.Error.UnknownMethod" requested_reply="0" destination=":1.3" (uid=0 pid=1041 comm="/usr/sbin/bluetoothd ")
/var/log/auth.log:Aug 13 21:53:30 bilbo dbus[1022]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.30" (uid=117 pid=2190 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.22" (uid=0 pid=1721 comm="/usr/sbin/console-kit-daemon --no-daemon ")
/var/log/auth.log:Aug 13 21:53:40 bilbo dbus[1022]: [system] Rejected send message, 2 matched rules; type="method_return", sender=":1.3" (uid=0 pid=1038 comm="/usr/sbin/bluetoothd ") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.49" (uid=1000 pid=2535 comm="bluetooth-applet ")
/var/log/auth.log:Aug 13 21:54:24 bilbo dbus[1022]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.68" (uid=1000 pid=3612 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.22" (uid=0 pid=1721 comm="/usr/sbin/console-kit-daemon --no-daemon ")
/var/log/auth.log:Aug 14 09:22:53 bilbo dbus[1042]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.30" (uid=117 pid=2233 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.22" (uid=0 pid=1789 comm="/usr/sbin/console-kit-daemon --no-daemon ")
/var/log/auth.log:Aug 14 09:23:37 bilbo dbus[1042]: [system] Rejected send message, 2 matched rules; type="method_return", sender=":1.2" (uid=0 pid=1074 comm="/usr/sbin/bluetoothd ") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.48" (uid=1000 pid=2727 comm="bluetooth-applet ")
/var/log/auth.log:Aug 14 09:24:25 bilbo dbus[1042]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.69" (uid=1000 pid=3263 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.22" (uid=0 pid=1789 comm="/usr/sbin/console-kit-daemon --no-daemon ")
/var/log/auth.log:Aug 14 20:52:40 bilbo dbus[1013]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.30" (uid=117 pid=2109 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.22" (uid=0 pid=1751 comm="/usr/sbin/console-kit-daemon --no-daemon ")
/var/log/auth.log:Aug 14 20:52:49 bilbo dbus[1013]: [system] Rejected send message, 2 matched rules; type="method_return", sender=":1.3" (uid=0 pid=1029 comm="/usr/sbin/bluetoothd ") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.51" (uid=1000 pid=2537 comm="bluetooth-applet ")
/var/log/auth.log:Aug 14 20:53:31 bilbo dbus[1013]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.68" (uid=1000 pid=3054 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.22" (uid=0 pid=1751 comm="/usr/sbin/console-kit-daemon --no-daemon ")
/var/log/auth.log:Aug 15 07:49:17 bilbo dbus[1055]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.35" (uid=117 pid=2297 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.23" (uid=0 pid=1751 comm="/usr/sbin/console-kit-daemon --no-daemon ")
/var/log/auth.log:Aug 15 07:49:29 bilbo dbus[1055]: [system] Rejected send message, 2 matched rules; type="method_return", sender=":1.5" (uid=0 pid=1107 comm="/usr/sbin/bluetoothd ") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.54" (uid=1000 pid=2500 comm="bluetooth-applet ")
/var/log/auth.log:Aug 15 07:50:12 bilbo dbus[1055]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.68" (uid=1000 pid=2871 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.23" (uid=0 pid=1751 comm="/usr/sbin/console-kit-daemon --no-daemon ")
/var/log/auth.log:Aug 15 09:40:47 bilbo dbus[741]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.30" (uid=117 pid=2307 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.21" (uid=0 pid=1819 comm="/usr/sbin/console-kit-daemon --no-daemon ")
/var/log/auth.log:Aug 15 09:40:49 bilbo dbus[741]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.43" (uid=117 pid=2370 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.21" (uid=0 pid=1819 comm="/usr/sbin/console-kit-daemon --no-daemon ")
/var/log/auth.log:Aug 15 09:40:58 bilbo dbus[741]: [system] Rejected send message, 2 matched rules; type="method_return", sender=":1.1" (uid=0 pid=763 comm="/usr/sbin/bluetoothd ") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.54" (uid=1000 pid=2631 comm="bluetooth-applet ")
/var/log/auth.log:Aug 15 09:41:45 bilbo dbus[741]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.72" (uid=1000 pid=3175 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.21" (uid=0 pid=1819 comm="/usr/sbin/console-kit-daemon --no-daemon ")
/var/log/auth.log:Aug 15 19:48:55 bilbo dbus[1016]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.32" (uid=117 pid=2232 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.22" (uid=0 pid=1743 comm="/usr/sbin/console-kit-daemon --no-daemon ")
/var/log/auth.log:Aug 15 19:49:02 bilbo dbus[1016]: [system] Rejected send message, 2 matched rules; type="method_return", sender=":1.2" (uid=0 pid=1044 comm="/usr/sbin/bluetoothd ") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.49" (uid=1000 pid=2436 comm="bluetooth-applet ")
/var/log/auth.log:Aug 15 19:49:39 bilbo dbus[1016]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.67" (uid=1000 pid=3128 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.22" (uid=0 pid=1743 comm="/usr/sbin/console-kit-daemon --no-daemon ")
/var/log/auth.log:Aug 16 09:50:26 bilbo dbus[1110]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.30" (uid=117 pid=2199 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.22" (uid=0 pid=1817 comm="/usr/sbin/console-kit-daemon --no-daemon ")
/var/log/auth.log:Aug 16 09:50:28 bilbo dbus[1110]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.43" (uid=117 pid=2399 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.22" (uid=0 pid=1817 comm="/usr/sbin/console-kit-daemon --no-daemon ")
/var/log/auth.log:Aug 16 09:50:35 bilbo dbus[1110]: [system] Rejected send message, 2 matched rules; type="method_return", sender=":1.2" (uid=0 pid=1124 comm="/usr/sbin/bluetoothd ") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.54" (uid=1000 pid=2946 comm="bluetooth-applet ")
/var/log/auth.log:Aug 16 09:51:23 bilbo dbus[1110]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.75" (uid=1000 pid=3509 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.22" (uid=0 pid=1817 comm="/usr/sbin/console-kit-daemon --no-daemon ")
/var/log/auth.log:Aug 16 16:43:45 bilbo sudo:    johan : TTY=pts/5 ; PWD=/home/johan ; USER=root ; COMMAND=/bin/egrep -i error|warning /var/log/alternatives.log /var/log/apport.log /var/log/auth.log /var/log/boot.log /var/log/bootstrap.log /var/log/daemon.log /var/log/dpkg.log /var/log/faillog /var/log/fontconfig.log /var/log/jockey.log /var/log/kern.log /var/log/lastlog /var/log/lpr.log /var/log/mail.log /var/log/mysql.log /var/log/pm-powersave.log /var/log/pm-suspend.log /var/log/pycentral.log /var/log/syslog /var/log/ufw.log /var/log/user.log /var/log/wvdialconf.log /var/log/Xorg.0.log /var/log/Xorg.1.log /var/log/Xorg.2.log /var/log/Xorg.3.log /var/log/Xorg.failsafe.log
/var/log/auth.log:Aug 16 16:46:30 bilbo sudo:    johan : TTY=pts/5 ; PWD=/home/johan ; USER=root ; COMMAND=/bin/egrep -i error|warning /var/log/alternatives.log /var/log/apport.log /var/log/auth.log /var/log/boot.log /var/log/bootstrap.log /var/log/daemon.log /var/log/dpkg.log /var/log/faillog /var/log/fontconfig.log /var/log/jockey.log /var/log/kern.log /var/log/lastlog /var/log/lpr.log /var/log/mail.log /var/log/mysql.log /var/log/pm-powersave.log /var/log/pm-suspend.log /var/log/pycentral.log /var/log/syslog /var/log/ufw.log /var/log/user.log /var/log/wvdialconf.log /var/log/Xorg.0.log /var/log/Xorg.1.log /var/log/Xorg.2.log /var/log/Xorg.3.log /var/log/Xorg.failsafe.log
/var/log/auth.log:Aug 16 16:49:43 bilbo sudo:    johan : TTY=pts/5 ; PWD=/home/johan ; USER=root ; COMMAND=/bin/egrep -i error|warning /var/log/alternatives.log /var/log/apport.log /var/log/auth.log /var/log/boot.log /var/log/bootstrap.log /var/log/daemon.log /var/log/dpkg.log /var/log/faillog /var/log/fontconfig.log /var/log/jockey.log /var/log/kern.log /var/log/lastlog /var/log/lpr.log /var/log/mail.log /var/log/mysql.log /var/log/pm-powersave.log /var/log/pm-suspend.log /var/log/pycentral.log /var/log/syslog /var/log/ufw.log /var/log/user.log /var/log/wvdialconf.log /var/log/Xorg.0.log /var/log/Xorg.1.log /var/log/Xorg.2.log /var/log/Xorg.3.log /var/log/Xorg.failsafe.log
/var/log/auth.log:Aug 16 16:51:55 bilbo dbus[1066]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.30" (uid=117 pid=2303 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.21" (uid=0 pid=1729 comm="/usr/sbin/console-kit-daemon --no-daemon ")
/var/log/auth.log:Aug 16 16:52:02 bilbo dbus[1066]: [system] Rejected send message, 2 matched rules; type="method_return", sender=":1.3" (uid=0 pid=1083 comm="/usr/sbin/bluetoothd ") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.56" (uid=1000 pid=2608 comm="bluetooth-applet ")
/var/log/auth.log:Aug 16 16:52:34 bilbo dbus[1066]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.70" (uid=1000 pid=3006 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.21" (uid=0 pid=1729 comm="/usr/sbin/console-kit-daemon --no-daemon ")
/var/log/auth.log:Aug 16 16:53:40 bilbo sudo:    johan : TTY=pts/0 ; PWD=/home/johan ; USER=root ; COMMAND=/bin/egrep -i error|warning /var/log/alternatives.log /var/log/apport.log /var/log/auth.log /var/log/boot.log /var/log/bootstrap.log /var/log/daemon.log /var/log/dpkg.log /var/log/faillog /var/log/fontconfig.log /var/log/jockey.log /var/log/kern.log /var/log/lastlog /var/log/lpr.log /var/log/mail.log /var/log/mysql.log /var/log/pm-powersave.log /var/log/pm-suspend.log /var/log/pycentral.log /var/log/syslog /var/log/ufw.log /var/log/user.log /var/log/wvdialconf.log /var/log/Xorg.0.log /var/log/Xorg.1.log /var/log/Xorg.2.log /var/log/Xorg.3.log /var/log/Xorg.failsafe.log
/var/log/auth.log:Aug 16 16:56:41 bilbo sudo:    johan : TTY=pts/0 ; PWD=/home/johan ; USER=root ; COMMAND=/bin/egrep -i error|warning /var/log/alternatives.log /var/log/apport.log /var/log/auth.log /var/log/boot.log /var/log/bootstrap.log /var/log/daemon.log /var/log/dpkg.log /var/log/faillog /var/log/fontconfig.log /var/log/jockey.log /var/log/kern.log /var/log/lastlog /var/log/lpr.log /var/log/mail.log /var/log/mysql.log /var/log/pm-powersave.log /var/log/pm-suspend.log /var/log/pycentral.log /var/log/syslog /var/log/ufw.log /var/log/user.log /var/log/wvdialconf.log /var/log/Xorg.0.log /var/log/Xorg.1.log /var/log/Xorg.2.log /var/log/Xorg.3.log /var/log/Xorg.failsafe.log
/var/log/auth.log:Aug 16 16:57:09 bilbo sudo:    johan : TTY=pts/0 ; PWD=/home/johan ; USER=root ; COMMAND=/bin/egrep -i error|warning /var/log/alternatives.log /var/log/apport.log /var/log/auth.log /var/log/boot.log /var/log/bootstrap.log /var/log/daemon.log /var/log/dpkg.log /var/log/faillog /var/log/fontconfig.log /var/log/jockey.log /var/log/kern.log /var/log/lastlog /var/log/lpr.log /var/log/mail.log /var/log/mysql.log /var/log/pm-powersave.log /var/log/pm-suspend.log /var/log/pycentral.log /var/log/syslog /var/log/ufw.log /var/log/user.log /var/log/wvdialconf.log /var/log/Xorg.0.log /var/log/Xorg.1.log /var/log/Xorg.2.log /var/log/Xorg.3.log /var/log/Xorg.failsafe.log
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:insserv: warning: script 'hostname' missing LSB tags and overrides
/var/log/bootstrap.log:insserv: warning: script 'network-interface-security' missing LSB tags and overrides
/var/log/bootstrap.log:insserv: warning: script 'network-interface' missing LSB tags and overrides
/var/log/bootstrap.log:insserv: warning: script 'module-init-tools' missing LSB tags and overrides
/var/log/bootstrap.log:insserv: warning: script 'plymouth' missing LSB tags and overrides
/var/log/bootstrap.log:insserv: warning: script 'plymouth-log' missing LSB tags and overrides
/var/log/bootstrap.log:insserv: warning: script 'plymouth-splash' missing LSB tags and overrides
/var/log/bootstrap.log:insserv: warning: script 'plymouth-stop' missing LSB tags and overrides
/var/log/bootstrap.log:insserv: warning: script 'procps' missing LSB tags and overrides
/var/log/bootstrap.log:insserv: warning: script 'udev' missing LSB tags and overrides
/var/log/bootstrap.log:insserv: warning: script 'udev-finish' missing LSB tags and overrides
/var/log/bootstrap.log:insserv: warning: script 'udevtrigger' missing LSB tags and overrides
/var/log/bootstrap.log:insserv: warning: script 'udevmonitor' missing LSB tags and overrides
/var/log/bootstrap.log:insserv: warning: script 'hwclock' missing LSB tags and overrides
/var/log/bootstrap.log:insserv: warning: script 'hwclock-save' missing LSB tags and overrides
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:install-info: warning: maintainer scripts should not call install-info anymore,
/var/log/bootstrap.log:install-info: warning: this is handled now by a dpkg trigger provided by the
/var/log/bootstrap.log:install-info: warning: install-info package; package cpio should be updated.
/var/log/bootstrap.log:ifupdown.postinst: Warning: No 'iface lo' definition found in /etc/network/interfaces
/var/log/bootstrap.log:ifupdown.postinst: Warning:  adding it for you
/var/log/bootstrap.log:ifupdown.postinst: Warning: No 'auto lo' statement found in /etc/network/interfaces
/var/log/bootstrap.log:ifupdown.postinst: Warning:  adding it for you
/var/log/bootstrap.log:Warning: Fake initctl called, doing nothing
/var/log/bootstrap.log:Warning: Fake initctl called, doing nothing
/var/log/bootstrap.log:Unpacking libgpg-error0 (from .../libgpg-error0_1.6-1ubuntu2_i386.deb) ...
/var/log/bootstrap.log:Setting up libgpg-error0 (1.6-1ubuntu2) ...
/var/log/bootstrap.log:Warning: Fake initctl called, doing nothing
/var/log/bootstrap.log:Warning: Fake initctl called, doing nothing
/var/log/bootstrap.log:Updating certificates in /etc/ssl/certs... WARNING: Skipping duplicate certificate ca-certificates.crt
/var/log/kern.log:Aug 11 22:54:30 bilbo kernel: [22103.924904] indicator-skype[19349]: segfault at 6e6f80 ip b777fcb7 sp bfdadfe0 error 4 in libpthread-2.15.so[b7777000+17000]
/var/log/kern.log:Aug 12 09:03:21 bilbo kernel: [   12.145428] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Aug 12 09:26:21 bilbo kernel: [ 1393.350384] indicator-skype[3843]: segfault at 6e6f80 ip b771acb7 sp bfafda20 error 4 in libpthread-2.15.so[b7712000+17000]
/var/log/kern.log:Aug 12 09:39:11 bilbo kernel: [   31.954474] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Aug 12 09:39:30 bilbo kernel: [   51.025339] EXT3-fs (sdb1): warning: maximal mount count reached, running e2fsck is recommended
/var/log/kern.log:Aug 12 19:15:03 bilbo kernel: [   30.223070] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Aug 12 22:02:54 bilbo kernel: [10078.133227] indicator-skype[3038]: segfault at c ip b76d5cb7 sp bff4f290 error 4 in libpthread-2.15.so[b76cd000+17000]
/var/log/kern.log:Aug 13 08:38:28 bilbo kernel: [   30.141075] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Aug 13 09:16:10 bilbo kernel: [ 1444.632287] watchdog: error registering /dev/watchdog (err=-16).
/var/log/kern.log:Aug 13 21:53:23 bilbo kernel: [   29.651786] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Aug 14 09:22:47 bilbo kernel: [   32.990005] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Aug 14 20:52:33 bilbo kernel: [   29.725063] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Aug 14 23:09:07 bilbo kernel: [ 8203.448835] indicator-skype[3158]: segfault at 53656d71 ip b779acb7 sp bfb6ed90 error 4 in libpthread-2.15.so[b7792000+17000]
/var/log/kern.log:Aug 15 07:48:51 bilbo kernel: [  116.541399] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Aug 15 09:40:40 bilbo kernel: [   31.964078] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Aug 15 09:41:00 bilbo kernel: [   52.022801] EXT3-fs (sdb1): warning: maximal mount count reached, running e2fsck is recommended
/var/log/kern.log:Aug 15 19:48:49 bilbo kernel: [   32.577997] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Aug 15 21:07:12 bilbo kernel: [ 4724.287025] plugin-containe[3627]: segfault at 6 ip b070a49e sp bffd5ff0 error 4 in libflashplayer.so[aff71000+1017000]
/var/log/kern.log:Aug 15 23:10:42 bilbo kernel: [12115.254085] indicator-skype[3270]: segfault at 53656d71 ip b76f7cb7 sp bf82bf30 error 4 in libpthread-2.15.so[b76ef000+17000]
/var/log/kern.log:Aug 16 09:50:19 bilbo kernel: [   30.505558] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Aug 16 09:50:37 bilbo kernel: [   49.156053] EXT3-fs (sdb1): warning: maximal mount count reached, running e2fsck is recommended
/var/log/kern.log:Aug 16 16:51:48 bilbo kernel: [   33.345934] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Aug 16 16:52:03 bilbo kernel: [   49.603544] EXT3-fs (sdb1): warning: maximal mount count reached, running e2fsck is recommended
/var/log/syslog:Aug 16 16:51:48 bilbo kernel: [   33.345934] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
/var/log/syslog:Aug 16 16:52:01 bilbo gnome-session[2505]: WARNING: Failed to start app: Unable to start application: Failed to execute child process "/usr/bin/checkgmail" (No such file or directory)
/var/log/syslog:Aug 16 16:52:02 bilbo gnome-session[2505]: WARNING: Failed to start app: Unable to start application: Failed to execute child process "gmailwatcher" (No such file or directory)
/var/log/syslog:Aug 16 16:52:03 bilbo NetworkManager[1088]: <warn> error monitoring device for netlink events: error processing netlink message: Object busy
/var/log/syslog:Aug 16 16:52:03 bilbo kernel: [   49.603544] EXT3-fs (sdb1): warning: maximal mount count reached, running e2fsck is recommended
/var/log/syslog:Aug 16 16:52:14 bilbo NetworkManager[1088]: <warn> error monitoring device for netlink events: error processing netlink message: Object busy
/var/log/Xorg.0.log:	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
/var/log/Xorg.1.log:	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
/var/log/Xorg.2.log:	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
/var/log/Xorg.3.log:	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
/var/log/Xorg.failsafe.log:	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
/var/log/Xorg.failsafe.log:Fatal server error:
/var/log/Xorg.failsafe.log:[    32.975] Server terminated with error (1). Closing log file.
```

---

### Post by TheFu on 2013-08-16
The way that I trouble shoot errors is by googling the error with enough specifics to find an answer, but not so many specifics that nothing is found. Does that make sense?  Going through the warnings and errors 1 at a time looking for information on each is the only way I know. Over time, you'll learn what is important.

I quickly scanned the errors.  The file system seemed to just hit a normal limit that required an fsck during startup.  The setting that controls this can be tuned, but I think the default is 30 or 60 days. That is usually reasonable. If these scans happen every time, I'd suspect a failing HDD, bad SATA cable, bad SATA port, failing disk controller, or issue with the motherboard.  Notice the specific partitions being rescanned. If those change - fine. If they are always the same --- backup your data, and get prepared for a failure.

A slowly booting system can be due to all sorts of things from running too many processes at boot or running boot processes in the wrong order or failing hardware or not having a network connection.  I see that skype-something is crashing in your logs.  I'd remove it to see if that helped speed things up.  Some network-centric programs have to time-out before continuing. That can take 30 seconds or 300 seconds depending on the settings and program.

Anyway, I hope this helped.

---

### Post by VMC on 2013-08-16
You can start with this one :
```
EXT3-fs (sdb1): warning: maximal mount count reached, running e2fsck is recommended
```

Try using running  ```
sudo fsck /dev/sdb1
``` Make sure its unmounted.

---

### Post by jolindbe on 2013-08-16
> **TheFu said:**
> The way that I trouble shoot errors is by googling the error with enough specifics to find an answer, but not so many specifics that nothing is found. Does that make sense?  Going through the warnings and errors 1 at a time looking for information on each is the only way I know. Over time, you'll learn what is important.

I will give it a try.

> **TheFu said:**
> 
I quickly scanned the errors.  The file system seemed to just hit a normal limit that required an fsck during startup.  The setting that controls this can be tuned, but I think the default is 30 or 60 days. That is usually reasonable. If these scans happen every time, I'd suspect a failing HDD, bad SATA cable, bad SATA port, failing disk controller, or issue with the motherboard.  Notice the specific partitions being rescanned. If those change - fine. If they are always the same --- backup your data, and get prepared for a failure.


Do you mean the "EXT3-fs (sdb1): warning: maximal mount count reached, running e2fsck is recommended"? That apparently refers to my external backup hard drive at work, and seems to come up every time I boot with that one plugged in. However, the slow boot occurs also when that drive is not plugged in.

> **TheFu said:**
> 
A slowly booting system can be due to all sorts of things from running too many processes at boot or running boot processes in the wrong order or failing hardware or not having a network connection.  I see that skype-something is crashing in your logs.  I'd remove it to see if that helped speed things up.  Some network-centric programs have to time-out before continuing. That can take 30 seconds or 300 seconds depending on the settings and program.

Anyway, I hope this helped.

I tried to terminate the indicator-skype before shutdown, but still long bootup time. I will keep looking, thanks for your help!

> **VMC said:**
> You can start with this one :
```
EXT3-fs (sdb1): warning: maximal mount count reached, running e2fsck is recommended
```

Try using running  ```
sudo fsck /dev/sdb1
``` Make sure its unmounted.

As I write above, this is my external hard drive at work. I got home before I got your message, but will try to fsck it on Monday. Still, the slow boot occurs also when that drive is not plugged in.

---

### Post by TheFu on 2013-08-16
> **jolindbe said:**
> I will give it a try.



Do you mean the "EXT3-fs (sdb1): warning: maximal mount count reached, running e2fsck is recommended"? That apparently refers to my external backup hard drive at work, and seems to come up every time I boot with that one plugged in. However, the slow boot occurs also when that drive is not plugged in.



I tried to terminate the indicator-skype before shutdown, but still long bootup time. I will keep looking, thanks for your help!



As I write above, this is my external hard drive at work. I got home before I got your message, but will try to fsck it on Monday. Still, the slow boot occurs also when that drive is not plugged in.

The Skype stuff will auto-restart. You need to remove that program or somehow prevent it from starting at all.

If you external HDD is not eSATA - it will be slow.  USB2 is really, really slow.  Did you set the machine to always mount it at boot?  If it is USB2, disable that and test again.  I bet that is the issue.

---

### Post by jolindbe on 2013-08-16
> **TheFu said:**
> 
If you external HDD is not eSATA - it will be slow.  USB2 is really, really slow.  Did you set the machine to always mount it at boot?  If it is USB2, disable that and test again.  I bet that is the issue.

It is indeed a USB2 drive. Would this really make the computer boot slower also when the drive is not connected (which is the case)?
I can't remember if I've set it to automatically mount at boot (I have not made a fresh install since 10.04), but it is not listed in /etc/fstab at least - could the automatic mount be set somewhere else?

I will see what I can do with indicator-skype, but if it cuts Skype functionality, I'm not that happy with removing it.

---

### Post by TheFu on 2013-08-16
> **jolindbe said:**
> It is indeed a USB2 drive. Would this really make the computer boot slower also when the drive is not connected (which is the case)?
I can't remember if I've set it to automatically mount at boot (I have not made a fresh install since 10.04), but it is not listed in /etc/fstab at least - could the automatic mount be set somewhere else?

I will see what I can do with indicator-skype, but if it cuts Skype functionality, I'm not that happy with removing it.

**I'm reaching at straws,** but isn't USB2 100x slower than SATA.  If anything performs a scan on that USB2 device during boot, it would be slower. Does that make sense?

I can see where Unity's "dash" might want to scan the drive every time to look for programs, but I don't know - don't use Unity here. There might be other programs doing that too.  Perhaps anacron has some scripts that look?  I dunno. Still reaching.

Perhaps if you could boot the slow machine, then ssh in from another ASAP (when the network and ssh come up), but before the GUI is available, you could look at the process table to see what was running and using most of the I/O?  **top** and **saidar** and **lsof** would help.

Still, it could be failing hardware too. Slow booting is a common symptom of hardware failures about to happen. Have you reseated the drive cables?

PING!!!!   I vaguely remember a bug where USB devices were not being umounted during a reboot or shutdown.  At your next shutdown, please manually umount the USB drive first and let it clear the cache.  Typing "sync; sync; sync" is the old-school way.  Until the last sync returns, do not press the shutdown command/button.  Time the restart. See if it is faster, please.  Use a watch to be accurate to a few seconds. I'd start writing down how long it takes for every major part of a boot process going forward too. Facts and data of that type have not been included here yet.

---

### Post by jolindbe on 2013-08-17
> **TheFu said:**
> **I'm reaching at straws,** but isn't USB2 100x slower than SATA.  If anything performs a scan on that USB2 device during boot, it would be slower. Does that make sense?

As I've already said several times: The computer boots slowly also when the USB drive is one mile away not connected to the computer. How can it make a scan on an disconnected drive?

> **TheFu said:**
> 
I can see where Unity's "dash" might want to scan the drive every time to look for programs, but I don't know - don't use Unity here. There might be other programs doing that too.  Perhaps anacron has some scripts that look?  I dunno. Still reaching.

Perhaps if you could boot the slow machine, then ssh in from another ASAP (when the network and ssh come up), but before the GUI is available, you could look at the process table to see what was running and using most of the I/O?  **top** and **saidar** and **lsof** would help.


Hmm, I could make a try. I guess I would need to connect it by ethernet, since the wireless often is a bit slow to connect.

> **TheFu said:**
> 
Still, it could be failing hardware too. Slow booting is a common symptom of hardware failures about to happen. Have you reseated the drive cables?


I would doubt it, since it has been like this since I upgraded to 12.04 a year ago - it has not become better or worse during that time, I just recently realised that 12.04 is supposed to boot in 10 seconds, after seeing a colleagues computer boot.

> **TheFu said:**
> 
PING!!!!   I vaguely remember a bug where USB devices were not being umounted during a reboot or shutdown.  At your next shutdown, please manually umount the USB drive first and let it clear the cache.  Typing "sync; sync; sync" is the old-school way.  Until the last sync returns, do not press the shutdown command/button.  Time the restart. See if it is faster, please.  Use a watch to be accurate to a few seconds. I'd start writing down how long it takes for every major part of a boot process going forward too. Facts and data of that type have not been included here yet.

As I said, would this really happen if the USB drive was not at all connected (both during shutdown and during the next boot)?

---

### Post by mörgæs on 2013-08-17
> **jolindbe said:**
> I have not made a fresh install since 10.04.

Then I would suggest this as a first step.

---

### Post by VMC on 2013-08-17
Or you could try using [*bootchart*]("http://en.kioskea.net/faq/4268-ubuntu-monitor-your-boot-sequence-with-bootchart") to see where the time booting is being used.

---

### Post by jolindbe on 2013-08-17
> **TheFu said:**
> 
Perhaps if you could boot the slow machine, then ssh in from another ASAP (when the network and ssh come up), but before the GUI is available, you could look at the process table to see what was running and using most of the I/O?  **top** and **saidar** and **lsof** would help.


That was indeed a great idea, we have a breakthrough! I saw that Dropbox and Skype were heavy users during startup, so I timed boots with these startups toggled. Times are from password entered until desktop is seen:
Without Skype and Dropbox 19s
Without Dropbox, but with Skype 35s
Without Skype, but with Dropbox 28s
With both 54s

So it seems that Skype in particular, but also Dropbox slows down the boot. Strangely enough, if I try starting these application after the computer has properly booted Skype starts in less than 5 seconds and Dropbox in no time. I found this thread: [http://ubuntuforums.org/showthread.php?t=2122854](http://ubuntuforums.org/showthread.php?t=2122854) telling me to delay the startup of Dropbox (and Skype in my case) by using this command in the startup:

```
sh -c "sleep 5m; dropbox start -i"
```

I lowered 5m to 1m (could probably cut it to 30s also), and it works like a charm. I get a working desktop within 20s, and a while later Skype and Dropbox start, which is fine by me.

Thanks for the help, I am marking this as SOLVED.

> **mörgæs said:**
> Then I would suggest [doing a fresh Ubuntu install] as a first step.

I do see your point, but I don't really have the time for that kind of thing now. Anyway, problem solved without reinstall - I try to see a fresh install as a last resort, I don't see the point in spending >5 hours to wipe my harddrive and reinstall everything every time I run into a problem, or every new Ubuntu release. Instead I am running LTS with upgrades until it breaks too badly.

> **VMC said:**
> Or you could try using [*bootchart*]("http://en.kioskea.net/faq/4268-ubuntu-monitor-your-boot-sequence-with-bootchart") to see where the time booting is being used.

Seems like a neat utility which I would have tried out if I hadn't solved the problem. I'll keep it in mind for later.

---

### Post by jolindbe on 2013-08-17
Umm.. not so fast, apparently. The first reboot it works fine, but then the startup command for Dropbox apparently changes to the old command, without the sleep. Why, how?

---

### Post by jolindbe on 2013-08-17
Ok, found a solution to that too: Instead of editing the existing Dropbox startup preferences, in Dropbox Preferences toggle off "Start Dropbox on system startup", then create a homemade startup preference with the correct command. Done!

---

