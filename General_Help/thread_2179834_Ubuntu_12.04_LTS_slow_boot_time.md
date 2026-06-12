---
title: "Ubuntu 12.04 LTS slow boot time"
date: 2013-10-10
forum: General Help
---

### Post by Niels1974 on 2013-10-10
Hi I have recently installed hplip (3.13.9) and since then my boot time has increased considerably. I first see the text login, and after waiting more than 20 seconds lighdm starts. 

Here is the output from dmesg:

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.8.0-31-generic (buildd@panlong) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #46~precise1-Ubuntu SMP Wed Sep 11 18:21:16 UTC 2013 (Ubuntu 3.8.0-31.46~precise1-generic 3.8.13.8)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-31-generic root=UUID=569c0b83-1355-45cd-aca4-0850dfffd17f ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009f7ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009f800-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000f0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000df79ffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000df7a0000-0x00000000df7a2fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000df7a3000-0x00000000df7dffff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000df7e0000-0x00000000df7fffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000f4000000-0x00000000f7ffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000021f7fffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.4 present.
[    0.000000] DMI: Gigabyte Technology Co., Ltd. H61M-D2H-USB3/H61M-D2H-USB3, BIOS F2 10/12/2011
[    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x21f800 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CCFFF write-protect
[    0.000000]   CD000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-through
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F00000000 write-back
[    0.000000]   1 base 0E0000000 mask FE0000000 uncachable
[    0.000000]   2 base 100000000 mask F00000000 write-back
[    0.000000]   3 base 200000000 mask FE0000000 write-back
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 4GB, type WB
[    0.000000] reg 1, base: 3584MB, range: 512MB, type UC
[    0.000000] reg 2, base: 4GB, range: 4GB, type WB
[    0.000000] reg 3, base: 8GB, range: 512MB, type WB
[    0.000000] total RAM covered: 8192M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 64K     num_reg: 5      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 512MB, type WB
[    0.000000] reg 3, base: 4GB, range: 4GB, type WB
[    0.000000] reg 4, base: 8GB, range: 512MB, type WB
[    0.000000] e820: update [mem 0xe0000000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xdf7a0 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000f5870-0x000f587f] mapped at [ffff8800000f5870]
[    0.000000] initial memory mapped: [mem 0x00000000-0x1fffffff]
[    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0xdf79ffff]
[    0.000000]  [mem 0x00000000-0xdf5fffff] page 2M
[    0.000000]  [mem 0xdf600000-0xdf79ffff] page 4k
[    0.000000] kernel direct mapping tables up to 0xdf79ffff @ [mem 0x1fffa000-0x1fffffff]
[    0.000000] init_memory_mapping: [mem 0x100000000-0x21f7fffff]
[    0.000000]  [mem 0x100000000-0x21f7fffff] page 2M
[    0.000000] kernel direct mapping tables up to 0x21f7fffff @ [mem 0xdf79a000-0xdf79ffff]
[    0.000000] RAMDISK: [mem 0x36104000-0x37079fff]
[    0.000000] ACPI: RSDP 00000000000f7030 00014 (v00 GBT   )
[    0.000000] ACPI: RSDT 00000000df7a3040 00050 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: FACP 00000000df7a3100 00074 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: DSDT 00000000df7a31c0 04CED (v01 GBT    GBTUACPI 00001000 MSFT 04000000)
[    0.000000] ACPI: FACS 00000000df7a0000 00040
[    0.000000] ACPI: MSDM 00000000df7a8000 00055 (v03 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: HPET 00000000df7a80c0 00038 (v01 GBT    GBTUACPI 42302E31 GBTU 00000098)
[    0.000000] ACPI: MCFG 00000000df7a8140 0003C (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: ASPT 00000000df7a8200 00034 (v07 GBT    PerfTune 312E3042 UTBG 01010101)
[    0.000000] ACPI: SSPT 00000000df7a8240 022F4 (v01 GBT    SsptHead 312E3042 UTBG 01010101)
[    0.000000] ACPI: EUDS 00000000df7aa540 000C0 (v01 GBT             00000000      00000000)
[    0.000000] ACPI: TAMG 00000000df7aa600 00422 (v01 GBT    GBT   B0 5455312E BG?? 45240101)
[    0.000000] ACPI: APIC 00000000df7a7f00 000BC (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: SSDT 00000000df7aaa40 03E74 (v01  INTEL PPM RCM  80000001 INTL 20061109)
[    0.000000] ACPI: MATS 00000000df7ae8c0 099E5 (v01        MATS RCM 80000001 INTL 20061109)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000021f7fffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x21f7fffff]
[    0.000000]   NODE_DATA [mem 0x21f7fb000-0x21f7fffff]
[    0.000000]  [ffffea0000000000-ffffea00087fffff] PMD -> [ffff880216e00000-ffff88021edfffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00010000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x21f7fffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00010000-0x0009efff]
[    0.000000]   node   0: [mem 0x00100000-0xdf79ffff]
[    0.000000]   node   0: [mem 0x100000000-0x21f7fffff]
[    0.000000] On node 0 totalpages: 2092847
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 6 pages reserved
[    0.000000]   DMA zone: 3913 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14239 pages used for memmap
[    0.000000]   DMA32 zone: 897025 pages, LIFO batch:31
[    0.000000]   Normal zone: 18400 pages used for memmap
[    0.000000]   Normal zone: 1159200 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x07] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x05] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x06] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x07] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] smpboot: Allowing 8 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000df7a0000 - 00000000df7a3000
[    0.000000] PM: Registered nosave memory: 00000000df7a3000 - 00000000df7e0000
[    0.000000] PM: Registered nosave memory: 00000000df7e0000 - 00000000df800000
[    0.000000] PM: Registered nosave memory: 00000000df800000 - 00000000f4000000
[    0.000000] PM: Registered nosave memory: 00000000f4000000 - 00000000f8000000
[    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 0000000100000000
[    0.000000] e820: [mem 0xdf800000-0xf3ffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88021f400000 s84928 r8192 d21568 u262144
[    0.000000] pcpu-alloc: s84928 r8192 d21568 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2060138
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-31-generic root=UUID=569c0b83-1355-45cd-aca4-0850dfffd17f ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] __ex_table already sorted, skipping sort
[    0.000000] xsave: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 8141668k/8904704k available (7171k kernel code, 533316k absent, 229720k reserved, 6072k data, 1012k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 33554432 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.004000] tsc: Detected 3392.235 MHz processor
[    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 6784.47 BogoMIPS (lpj=13568940)
[    0.000003] pid_max: default: 32768 minimum: 301
[    0.000018] Security Framework initialized
[    0.000027] AppArmor: AppArmor initialized
[    0.000027] Yama: becoming mindful.
[    0.000390] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.001523] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.001993] Mount-cache hash table entries: 256
[    0.002105] Initializing cgroup subsys cpuacct
[    0.002106] Initializing cgroup subsys memory
[    0.002110] Initializing cgroup subsys devices
[    0.002111] Initializing cgroup subsys freezer
[    0.002112] Initializing cgroup subsys blkio
[    0.002113] Initializing cgroup subsys perf_event
[    0.002115] Initializing cgroup subsys hugetlb
[    0.002131] CPU: Physical Processor ID: 0
[    0.002132] CPU: Processor Core ID: 0
[    0.002135] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.002135] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.002137] mce: CPU supports 9 MCE banks
[    0.002147] CPU0: Thermal monitoring enabled (TM1)
[    0.002153] process: using mwait in idle threads
[    0.002156] Last level iTLB entries: 4KB 512, 2MB 0, 4MB 0
[    0.002156] Last level dTLB entries: 4KB 512, 2MB 32, 4MB 32
[    0.002156] tlb_flushall_shift: 5
[    0.002247] Freeing SMP alternatives: 24k freed
[    0.003990] ACPI: Core revision 20121018
[    0.008459] ftrace: allocating 29359 entries in 115 pages
[    0.018863] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.058433] smpboot: CPU0: Intel(R) Core(TM) i7-2600 CPU @ 3.40GHz (fam: 06, model: 2a, stepping: 07)
[    0.058438] TSC deadline timer enabled
[    0.058440] Performance Events: PEBS fmt1+, 16-deep LBR, SandyBridge events, Intel PMU driver.
[    0.058444] perf_event_intel: PEBS disabled due to CPU errata, please upgrade microcode
[    0.058445] ... version:                3
[    0.058446] ... bit width:              48
[    0.058446] ... generic registers:      4
[    0.058447] ... value mask:             0000ffffffffffff
[    0.058448] ... max period:             000000007fffffff
[    0.058449] ... fixed-purpose events:   3
[    0.058449] ... event mask:             000000070000000f
[    0.072368] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.059210] smpboot: Booting Node   0, Processors  #1 #2 #3 #4 #5 #6 #7 OK
[    0.151350] Brought up 8 CPUs
[    0.151353] smpboot: Total of 8 processors activated (54275.76 BogoMIPS)
[    0.157940] devtmpfs: initialized
[    0.158601] EVM: security.selinux
[    0.158602] EVM: security.SMACK64
[    0.158603] EVM: security.capability
[    0.158627] PM: Registering ACPI NVS region [mem 0xdf7a0000-0xdf7a2fff] (12288 bytes)
[    0.159114] regulator-dummy: no parameters
[    0.159144] NET: Registered protocol family 16
[    0.159234] ACPI: bus type pci registered
[    0.159275] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf4000000-0xf7ffffff] (base 0xf4000000)
[    0.159277] PCI: MMCONFIG at [mem 0xf4000000-0xf7ffffff] reserved in E820
[    0.162502] PCI: Using configuration type 1 for base access
[    0.163109] bio: create slab <bio-0> at 0
[    0.163160] ACPI: Added _OSI(Module Device)
[    0.163161] ACPI: Added _OSI(Processor Device)
[    0.163162] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.163162] ACPI: Added _OSI(Processor Aggregator Device)
[    0.163652] ACPI: EC: Look up EC in DSDT
[    0.167073] ACPI: Interpreter enabled
[    0.167076] ACPI: (supports S0 S3 S4 S5)
[    0.167085] ACPI: Using IOAPIC for interrupt routing
[    0.169046] ACPI: No dock devices found.
[    0.169049] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.169076] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3f])
[    0.169077] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.169185] PCI host bridge to bus 0000:00
[    0.169187] pci_bus 0000:00: root bus resource [bus 00-3f]
[    0.169189] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.169190] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.169191] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.169193] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000dffff]
[    0.169194] pci_bus 0000:00: root bus resource [mem 0xe0000000-0xfebfffff]
[    0.169200] pci 0000:00:00.0: [8086:0100] type 00 class 0x060000
[    0.169227] pci 0000:00:01.0: [8086:0101] type 01 class 0x060400
[    0.169249] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.169286] pci 0000:00:16.0: [8086:1c3a] type 00 class 0x078000
[    0.169306] pci 0000:00:16.0: reg 10: [mem 0xfbfff000-0xfbfff00f 64bit]
[    0.169375] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.169404] pci 0000:00:1a.0: [8086:1c2d] type 00 class 0x0c0320
[    0.169423] pci 0000:00:1a.0: reg 10: [mem 0xfbffe000-0xfbffe3ff]
[    0.169506] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.169529] pci 0000:00:1b.0: [8086:1c20] type 00 class 0x040300
[    0.169542] pci 0000:00:1b.0: reg 10: [mem 0xfbff8000-0xfbffbfff 64bit]
[    0.169604] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.169623] pci 0000:00:1c.0: [8086:1c10] type 01 class 0x060400
[    0.169695] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.169716] pci 0000:00:1c.1: [8086:244e] type 01 class 0x060401
[    0.169787] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.169809] pci 0000:00:1c.2: [8086:1c14] type 01 class 0x060400
[    0.169880] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.169902] pci 0000:00:1c.4: [8086:1c18] type 01 class 0x060400
[    0.169974] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.170003] pci 0000:00:1d.0: [8086:1c26] type 00 class 0x0c0320
[    0.170021] pci 0000:00:1d.0: reg 10: [mem 0xfbffd000-0xfbffd3ff]
[    0.170105] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.170127] pci 0000:00:1f.0: [8086:1c5c] type 00 class 0x060100
[    0.170239] pci 0000:00:1f.2: [8086:1c00] type 00 class 0x01018f
[    0.170252] pci 0000:00:1f.2: reg 10: [io  0xff00-0xff07]
[    0.170258] pci 0000:00:1f.2: reg 14: [io  0xfe00-0xfe03]
[    0.170265] pci 0000:00:1f.2: reg 18: [io  0xfd00-0xfd07]
[    0.170271] pci 0000:00:1f.2: reg 1c: [io  0xfc00-0xfc03]
[    0.170278] pci 0000:00:1f.2: reg 20: [io  0xfb00-0xfb0f]
[    0.170284] pci 0000:00:1f.2: reg 24: [io  0xfa00-0xfa0f]
[    0.170324] pci 0000:00:1f.3: [8086:1c22] type 00 class 0x0c0500
[    0.170337] pci 0000:00:1f.3: reg 10: [mem 0xfbffc000-0xfbffc0ff 64bit]
[    0.170356] pci 0000:00:1f.3: reg 20: [io  0x0500-0x051f]
[    0.170385] pci 0000:00:1f.5: [8086:1c08] type 00 class 0x010185
[    0.170397] pci 0000:00:1f.5: reg 10: [io  0xf800-0xf807]
[    0.170404] pci 0000:00:1f.5: reg 14: [io  0xf700-0xf703]
[    0.170411] pci 0000:00:1f.5: reg 18: [io  0xf600-0xf607]
[    0.170417] pci 0000:00:1f.5: reg 1c: [io  0xf500-0xf503]
[    0.170424] pci 0000:00:1f.5: reg 20: [io  0xf400-0xf40f]
[    0.170430] pci 0000:00:1f.5: reg 24: [io  0xf300-0xf30f]
[    0.170492] pci 0000:01:00.0: [10de:0de1] type 00 class 0x030000
[    0.170500] pci 0000:01:00.0: reg 10: [mem 0xf9000000-0xf9ffffff]
[    0.170508] pci 0000:01:00.0: reg 14: [mem 0xe0000000-0xe7ffffff 64bit pref]
[    0.170516] pci 0000:01:00.0: reg 1c: [mem 0xee000000-0xefffffff 64bit pref]
[    0.170521] pci 0000:01:00.0: reg 24: [io  0xdf00-0xdf7f]
[    0.170527] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0007ffff pref]
[    0.170571] pci 0000:01:00.1: [10de:0bea] type 00 class 0x040300
[    0.170578] pci 0000:01:00.1: reg 10: [mem 0xfaffc000-0xfaffffff]
[    0.178462] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.178466] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    0.178470] pci 0000:00:01.0:   bridge window [mem 0xf9000000-0xfaffffff]
[    0.178475] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xefffffff 64bit pref]
[    0.178530] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.178598] pci 0000:03:00.0: [1283:8892] type 01 class 0x060401
[    0.178753] pci 0000:03:00.0: supports D1 D2
[    0.178754] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.178777] pci 0000:00:1c.1: PCI bridge to [bus 03-04] (subtractive decode)
[    0.178786] pci 0000:00:1c.1:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.178787] pci 0000:00:1c.1:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.178788] pci 0000:00:1c.1:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.178789] pci 0000:00:1c.1:   bridge window [mem 0x000c0000-0x000dffff] (subtractive decode)
[    0.178790] pci 0000:00:1c.1:   bridge window [mem 0xe0000000-0xfebfffff] (subtractive decode)
[    0.178940] pci 0000:03:00.0: PCI bridge to [bus 04] (subtractive decode)
[    0.178965] pci 0000:03:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
[    0.178966] pci 0000:03:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
[    0.178967] pci 0000:03:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
[    0.178968] pci 0000:03:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
[    0.178969] pci 0000:03:00.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.178970] pci 0000:03:00.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.178972] pci 0000:03:00.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.178973] pci 0000:03:00.0:   bridge window [mem 0x000c0000-0x000dffff] (subtractive decode)
[    0.178974] pci 0000:03:00.0:   bridge window [mem 0xe0000000-0xfebfffff] (subtractive decode)
[    0.179046] pci 0000:05:00.0: [1b6f:7023] type 00 class 0x0c0330
[    0.179071] pci 0000:05:00.0: reg 10: [mem 0xfbef8000-0xfbefffff 64bit]
[    0.179191] pci 0000:05:00.0: supports D1 D2
[    0.179192] pci 0000:05:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.186445] pci 0000:00:1c.2: PCI bridge to [bus 05]
[    0.186452] pci 0000:00:1c.2:   bridge window [mem 0xfbe00000-0xfbefffff]
[    0.186534] pci 0000:06:00.0: [1969:1083] type 00 class 0x020000
[    0.186560] pci 0000:06:00.0: reg 10: [mem 0xfbdc0000-0xfbdfffff 64bit]
[    0.186574] pci 0000:06:00.0: reg 18: [io  0xef00-0xef7f]
[    0.186696] pci 0000:06:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.194425] pci 0000:00:1c.4: PCI bridge to [bus 06]
[    0.194430] pci 0000:00:1c.4:   bridge window [io  0xe000-0xefff]
[    0.194435] pci 0000:00:1c.4:   bridge window [mem 0xfbd00000-0xfbdfffff]
[    0.194482] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEG0._PRT]
[    0.194500] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    0.194514] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX1._PRT]
[    0.194528] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX2._PRT]
[    0.194542] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX4._PRT]
[    0.194571]  pci0000:00: ACPI _OSC support notification failed, disabling PCIe ASPM
[    0.194572]  pci0000:00: Unable to request _OSC control (_OSC support mask: 0x08)
[    0.194985] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.195011] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.195037] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 *4 5 6 7 9 10 11 12 14 15)
[    0.195060] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.195084] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.195108] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.195132] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 9 10 11 *12 14 15)
[    0.195156] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.195214] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.195216] vgaarb: loaded
[    0.195216] vgaarb: bridge control possible 0000:01:00.0
[    0.195313] SCSI subsystem initialized
[    0.195315] ACPI: bus type scsi registered
[    0.195332] libata version 3.00 loaded.
[    0.195341] ACPI: bus type usb registered
[    0.195350] usbcore: registered new interface driver usbfs
[    0.195355] usbcore: registered new interface driver hub
[    0.195365] usbcore: registered new device driver usb
[    0.195410] PCI: Using ACPI for IRQ routing
[    0.196794] PCI: pci_cache_line_size set to 64 bytes
[    0.196841] e820: reserve RAM buffer [mem 0x0009f800-0x0009ffff]
[    0.196843] e820: reserve RAM buffer [mem 0xdf7a0000-0xdfffffff]
[    0.196844] e820: reserve RAM buffer [mem 0x21f800000-0x21fffffff]
[    0.196894] NetLabel: Initializing
[    0.196895] NetLabel:  domain hash size = 128
[    0.196896] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.196902] NetLabel:  unlabeled traffic allowed by default
[    0.196931] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.196935] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.198940] Switching to clocksource hpet
[    0.202005] AppArmor: AppArmor Filesystem Enabled
[    0.202017] pnp: PnP ACPI init
[    0.202023] ACPI: bus type pnp registered
[    0.202100] system 00:00: [io  0x04d0-0x04d1] has been reserved
[    0.202102] system 00:00: [io  0x0290-0x029f] has been reserved
[    0.202103] system 00:00: [io  0x0800-0x087f] has been reserved
[    0.202105] system 00:00: [io  0x0290-0x0294] has been reserved
[    0.202106] system 00:00: [io  0x0880-0x088f] has been reserved
[    0.202108] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.202114] pnp 00:01: [dma 4]
[    0.202123] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.202161] pnp 00:02: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.202182] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.202193] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.202208] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.202441] pnp 00:06: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.202569] pnp 00:07: Plug and Play ACPI device, IDs PNP0400 (active)
[    0.202643] system 00:08: [io  0x0400-0x04cf] has been reserved
[    0.202644] system 00:08: [io  0x04d2-0x04ff] has been reserved
[    0.202646] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.202665] system 00:09: [io  0x1000-0x107f] has been reserved
[    0.202666] system 00:09: [io  0x1080-0x10ff] has been reserved
[    0.202667] system 00:09: [io  0x1100-0x117f] has been reserved
[    0.202668] system 00:09: [io  0x1180-0x11ff] has been reserved
[    0.202670] system 00:09: Plug and Play ACPI device, IDs ICD0001 PNP0c02 (active)
[    0.202773] system 00:0a: [io  0x0454-0x0457] has been reserved
[    0.202775] system 00:0a: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.202797] system 00:0b: [mem 0xf4000000-0xf7ffffff] has been reserved
[    0.202799] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.202902] system 00:0c: [mem 0x000cda00-0x000cffff] has been reserved
[    0.202903] system 00:0c: [mem 0x000f0000-0x000f7fff] could not be reserved
[    0.202905] system 00:0c: [mem 0x000f8000-0x000fbfff] could not be reserved
[    0.202906] system 00:0c: [mem 0x000fc000-0x000fffff] could not be reserved
[    0.202907] system 00:0c: [mem 0xdf7a0000-0xdf7affff] could not be reserved
[    0.202909] system 00:0c: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.202910] system 00:0c: [mem 0x00100000-0xdf79ffff] could not be reserved
[    0.202911] system 00:0c: [mem 0xdf7b0000-0xdf7cffff] could not be reserved
[    0.202913] system 00:0c: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.202914] system 00:0c: [mem 0xfed10000-0xfed1dfff] has been reserved
[    0.202915] system 00:0c: [mem 0xfed20000-0xfed8ffff] has been reserved
[    0.202917] system 00:0c: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.202918] system 00:0c: [mem 0xffb00000-0xffb7ffff] has been reserved
[    0.202919] system 00:0c: [mem 0xfff00000-0xffffffff] has been reserved
[    0.202922] system 00:0c: [mem 0x000e0000-0x000effff] has been reserved
[    0.202923] system 00:0c: [mem 0x20000000-0x201fffff] could not be reserved
[    0.202924] system 00:0c: [mem 0x40000000-0x400fffff] could not be reserved
[    0.202934] system 00:0c: [mem 0xdf800000-0xdfffffff] could not be reserved
[    0.202940] system 00:0c: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.202959] pnp 00:0d: Plug and Play ACPI device, IDs INT0800 (active)
[    0.202962] pnp: PnP ACPI: found 14 devices
[    0.202963] ACPI: ACPI bus type pnp unregistered
[    0.208465] pci 0000:00:1c.0: bridge window [io  0x1000-0x0fff] to [bus 02] add_size 1000
[    0.208467] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 02] add_size 200000
[    0.208468] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff] to [bus 02] add_size 200000
[    0.208505] pci 0000:00:1c.0: res[14]=[mem 0x00100000-0x000fffff] get_res_add_size add_size 200000
[    0.208506] pci 0000:00:1c.0: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.208507] pci 0000:00:1c.0: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.208510] pci 0000:00:1c.0: BAR 14: assigned [mem 0xf0000000-0xf01fffff]
[    0.208512] pci 0000:00:1c.0: BAR 15: assigned [mem 0xf0200000-0xf03fffff 64bit pref]
[    0.208514] pci 0000:00:1c.0: BAR 13: assigned [io  0x2000-0x2fff]
[    0.208516] pci 0000:01:00.0: BAR 6: assigned [mem 0xe8000000-0xe807ffff pref]
[    0.208518] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.208519] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    0.208521] pci 0000:00:01.0:   bridge window [mem 0xf9000000-0xfaffffff]
[    0.208523] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xefffffff 64bit pref]
[    0.208525] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.208527] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.208531] pci 0000:00:1c.0:   bridge window [mem 0xf0000000-0xf01fffff]
[    0.208535] pci 0000:00:1c.0:   bridge window [mem 0xf0200000-0xf03fffff 64bit pref]
[    0.208540] pci 0000:03:00.0: PCI bridge to [bus 04]
[    0.208562] pci 0000:00:1c.1: PCI bridge to [bus 03-04]
[    0.208571] pci 0000:00:1c.2: PCI bridge to [bus 05]
[    0.208575] pci 0000:00:1c.2:   bridge window [mem 0xfbe00000-0xfbefffff]
[    0.208582] pci 0000:00:1c.4: PCI bridge to [bus 06]
[    0.208584] pci 0000:00:1c.4:   bridge window [io  0xe000-0xefff]
[    0.208588] pci 0000:00:1c.4:   bridge window [mem 0xfbd00000-0xfbdfffff]
[    0.208603] pci 0000:00:1c.0: enabling device (0000 -> 0003)
[    0.208626] pci 0000:03:00.0: setting latency timer to 64
[    0.208638] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.208639] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.208640] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.208642] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000dffff]
[    0.208643] pci_bus 0000:00: resource 8 [mem 0xe0000000-0xfebfffff]
[    0.208644] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    0.208645] pci_bus 0000:01: resource 1 [mem 0xf9000000-0xfaffffff]
[    0.208646] pci_bus 0000:01: resource 2 [mem 0xe0000000-0xefffffff 64bit pref]
[    0.208647] pci_bus 0000:02: resource 0 [io  0x2000-0x2fff]
[    0.208649] pci_bus 0000:02: resource 1 [mem 0xf0000000-0xf01fffff]
[    0.208650] pci_bus 0000:02: resource 2 [mem 0xf0200000-0xf03fffff 64bit pref]
[    0.208651] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    0.208652] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
[    0.208653] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    0.208654] pci_bus 0000:03: resource 7 [mem 0x000c0000-0x000dffff]
[    0.208656] pci_bus 0000:03: resource 8 [mem 0xe0000000-0xfebfffff]
[    0.208657] pci_bus 0000:04: resource 8 [io  0x0000-0x0cf7]
[    0.208658] pci_bus 0000:04: resource 9 [io  0x0d00-0xffff]
[    0.208659] pci_bus 0000:04: resource 10 [mem 0x000a0000-0x000bffff]
[    0.208660] pci_bus 0000:04: resource 11 [mem 0x000c0000-0x000dffff]
[    0.208661] pci_bus 0000:04: resource 12 [mem 0xe0000000-0xfebfffff]
[    0.208663] pci_bus 0000:05: resource 1 [mem 0xfbe00000-0xfbefffff]
[    0.208664] pci_bus 0000:06: resource 0 [io  0xe000-0xefff]
[    0.208665] pci_bus 0000:06: resource 1 [mem 0xfbd00000-0xfbdfffff]
[    0.208683] NET: Registered protocol family 2
[    0.208792] TCP established hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.208933] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.209033] TCP: Hash tables configured (established 65536 bind 65536)
[    0.209046] TCP: reno registered
[    0.209053] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.209074] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.209120] NET: Registered protocol family 1
[    0.238877] pci 0000:01:00.0: Boot video device
[    0.238940] PCI: CLS 4 bytes, default 64
[    0.238966] Trying to unpack rootfs image as initramfs...
[    0.410156] Freeing initrd memory: 15832k freed
[    0.411541] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.411545] software IO TLB [mem 0xdb79a000-0xdf79a000] (64MB) mapped at [ffff8800db79a000-ffff8800df799fff]
[    0.411898] Initialise module verification
[    0.411927] audit: initializing netlink socket (disabled)
[    0.411939] type=2000 audit(1381395112.400:1): initialized
[    0.430820] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.431712] VFS: Disk quotas dquot_6.5.2
[    0.431737] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.431995] fuse init (API version 7.20)
[    0.432035] msgmni has been set to 15932
[    0.432255] Key type asymmetric registered
[    0.432256] Asymmetric key parser 'x509' registered
[    0.432273] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.432289] io scheduler noop registered
[    0.432290] io scheduler deadline registered (default)
[    0.432293] io scheduler cfq registered
[    0.432360] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.432494] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.432501] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.432525] intel_idle: MWAIT substates: 0x1120
[    0.432526] intel_idle: v0.4 model 0x2A
[    0.432526] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.432569] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.432572] ACPI: Power Button [PWRB]
[    0.432595] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.432597] ACPI: Power Button [PWRF]
[    0.432638] ACPI: Requesting acpi_cpufreq
[    0.434935] GHES: HEST is not enabled!
[    0.434976] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.455323] 00:06: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.456030] Linux agpgart interface v0.103
[    0.456699] brd: module loaded
[    0.457050] loop: module loaded
[    0.457105] ata_piix 0000:00:1f.2: version 2.13
[    0.457119] ata_piix 0000:00:1f.2: MAP [
[    0.457120]  P0 P2 P1 P3 ]
[    0.609803] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.609941] scsi0 : ata_piix
[    0.610071] scsi1 : ata_piix
[    0.610176] ata1: SATA max UDMA/133 cmd 0xff00 ctl 0xfe00 bmdma 0xfb00 irq 19
[    0.610180] ata2: SATA max UDMA/133 cmd 0xfd00 ctl 0xfc00 bmdma 0xfb08 irq 19
[    0.610192] ata_piix 0000:00:1f.5: MAP [
[    0.610193]  P0 -- P1 -- ]
[    0.610223] ata_piix 0000:00:1f.5: setting latency timer to 64
[    0.610304] scsi2 : ata_piix
[    0.610400] scsi3 : ata_piix
[    0.610480] ata3: SATA max UDMA/133 cmd 0xf800 ctl 0xf700 bmdma 0xf400 irq 19
[    0.610483] ata4: SATA max UDMA/133 cmd 0xf600 ctl 0xf500 bmdma 0xf408 irq 19
[    0.610606] libphy: Fixed MDIO Bus: probed
[    0.610637] tun: Universal TUN/TAP device driver, 1.6
[    0.610638] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.610661] PPP generic driver version 2.4.2
[    0.610694] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.610695] ehci-pci: EHCI PCI platform driver
[    0.610721] ehci-pci 0000:00:1a.0: setting latency timer to 64
[    0.610723] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    0.610728] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    0.610739] ehci-pci 0000:00:1a.0: debug port 2
[    0.614630] ehci-pci 0000:00:1a.0: cache line size of 4 is not supported
[    0.614640] ehci-pci 0000:00:1a.0: irq 18, io mem 0xfbffe000
[    0.625743] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    0.625774] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.625777] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.625779] usb usb1: Product: EHCI Host Controller
[    0.625782] usb usb1: Manufacturer: Linux 3.8.0-31-generic ehci_hcd
[    0.625784] usb usb1: SerialNumber: 0000:00:1a.0
[    0.625851] hub 1-0:1.0: USB hub found
[    0.625854] hub 1-0:1.0: 2 ports detected
[    0.625908] ehci-pci 0000:00:1d.0: setting latency timer to 64
[    0.625910] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    0.625913] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.625923] ehci-pci 0000:00:1d.0: debug port 2
[    0.629814] ehci-pci 0000:00:1d.0: cache line size of 4 is not supported
[    0.629823] ehci-pci 0000:00:1d.0: irq 23, io mem 0xfbffd000
[    0.641696] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    0.641720] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    0.641723] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.641725] usb usb2: Product: EHCI Host Controller
[    0.641727] usb usb2: Manufacturer: Linux 3.8.0-31-generic ehci_hcd
[    0.641730] usb usb2: SerialNumber: 0000:00:1d.0
[    0.641794] hub 2-0:1.0: USB hub found
[    0.641796] hub 2-0:1.0: 2 ports detected
[    0.641840] ehci-platform: EHCI generic platform driver
[    0.641844] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.641851] uhci_hcd: USB Universal Host Controller Interface driver
[    0.641875] xhci_hcd 0000:05:00.0: xHCI Host Controller
[    0.641878] xhci_hcd 0000:05:00.0: new USB bus registered, assigned bus number 3
[    0.642046] xhci_hcd 0000:05:00.0: irq 41 for MSI/MSI-X
[    0.642098] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    0.642099] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.642100] usb usb3: Product: xHCI Host Controller
[    0.642101] usb usb3: Manufacturer: Linux 3.8.0-31-generic xhci_hcd
[    0.642103] usb usb3: SerialNumber: 0000:05:00.0
[    0.642134] xHCI xhci_add_endpoint called for root hub
[    0.642135] xHCI xhci_check_bandwidth called for root hub
[    0.642146] hub 3-0:1.0: USB hub found
[    0.642151] hub 3-0:1.0: 2 ports detected
[    0.642186] xhci_hcd 0000:05:00.0: xHCI Host Controller
[    0.642188] xhci_hcd 0000:05:00.0: new USB bus registered, assigned bus number 4
[    0.642220] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
[    0.642222] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.642223] usb usb4: Product: xHCI Host Controller
[    0.642224] usb usb4: Manufacturer: Linux 3.8.0-31-generic xhci_hcd
[    0.642225] usb usb4: SerialNumber: 0000:05:00.0
[    0.642254] xHCI xhci_add_endpoint called for root hub
[    0.642255] xHCI xhci_check_bandwidth called for root hub
[    0.642264] hub 4-0:1.0: USB hub found
[    0.642270] hub 4-0:1.0: 2 ports detected
[    0.642364] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    0.675422] i8042: Failed to disable AUX port, but continuing anyway... Is this a SiS?
[    0.675423] i8042: If AUX port is really absent please use the 'i8042.noaux' option
[    0.924969] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.925020] mousedev: PS/2 mouse device common for all mice
[    0.925090] rtc_cmos 00:03: RTC can wake from S4
[    0.925184] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.925208] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    0.925253] device-mapper: uevent: version 1.0.3
[    0.925283] device-mapper: ioctl: 4.23.1-ioctl (2012-12-18) initialised: dm-devel@redhat.com
[    0.925350] cpuidle: using governor ladder
[    0.925439] cpuidle: using governor menu
[    0.925442] ledtrig-cpu: registered to indicate activity on CPUs
[    0.925443] EFI Variables Facility v0.08 2004-May-17
[    0.925529] ashmem: initialized
[    0.925596] TCP: cubic registered
[    0.925645] NET: Registered protocol family 10
[    0.925738] NET: Registered protocol family 17
[    0.925744] Key type dns_resolver registered
[    0.925891] Loading module verification certificates
[    0.926500] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: ef66b5fef7cf2d982f954bc9bd9879a3cb821073'
[    0.926505] registered taskstats version 1
[    0.927736] Key type trusted registered
[    0.928714] Key type encrypted registered
[    0.939626] rtc_cmos 00:03: setting system clock to 2013-10-10 08:51:53 UTC (1381395113)
[    0.939646] ata3: SATA link down (SStatus 0 SControl 300)
[    0.950395] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    0.950397] ata4: SATA link down (SStatus 0 SControl 300)
[    0.950553] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.950554] EDD information not available.
[    1.080886] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
[    1.080891] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.081165] hub 1-1:1.0: USB hub found
[    1.081256] hub 1-1:1.0: 4 ports detected
[    1.192142] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    1.324194] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
[    1.324200] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.324468] hub 2-1:1.0: USB hub found
[    1.324557] hub 2-1:1.0: 6 ports detected
[    1.407521] tsc: Refined TSC clocksource calibration: 3392.293 MHz
[    1.407527] Switching to clocksource tsc
[    1.435432] usb 3-2: new low-speed USB device number 2 using xhci_hcd
[    1.485003] usb 3-2: New USB device found, idVendor=0a81, idProduct=0101
[    1.485008] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.485011] usb 3-2: Product: USB Keyboard
[    1.485013] usb 3-2: Manufacturer: CHESEN
[    1.485133] usb 3-2: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[    1.485136] usb 3-2: ep 0x82 - rounding interval to 64 microframes, ep desc says 80 microframes
[    1.595159] usb 2-1.2: new full-speed USB device number 3 using ehci-pci
[    1.693481] usb 2-1.2: New USB device found, idVendor=046d, idProduct=0a0b
[    1.693486] usb 2-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.693489] usb 2-1.2: Product: Logitech USB Headset
[    1.693491] usb 2-1.2: Manufacturer: Logitech
[    1.762678] usb 2-1.5: new low-speed USB device number 4 using ehci-pci
[    1.860399] usb 2-1.5: New USB device found, idVendor=046d, idProduct=c050
[    1.860404] usb 2-1.5: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.860407] usb 2-1.5: Product: USB-PS/2 Optical Mouse
[    1.860410] usb 2-1.5: Manufacturer: Logitech
[    1.930197] usb 2-1.6: new high-speed USB device number 5 using ehci-pci
[    1.953952] ata1.01: failed to resume link (SControl 0)
[    1.954023] ata2.01: failed to resume link (SControl 0)
[    2.022691] usb 2-1.6: New USB device found, idVendor=03f0, idProduct=5312
[    2.022696] usb 2-1.6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.022699] usb 2-1.6: Product: Officejet Pro 8500 A910
[    2.022701] usb 2-1.6: Manufacturer: HP
[    2.022704] usb 2-1.6: SerialNumber: CN12HCM1C9
[    2.109580] ata2.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.109592] ata2.01: SATA link down (SStatus 0 SControl 0)
[    2.109610] ata2.01: link offline, clearing class 3 to NONE
[    2.109732] ata1.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.109743] ata1.01: SATA link down (SStatus 0 SControl 0)
[    2.117901] ata2.00: ATAPI: HL-DT-ST DVDRAM GH24NS90, IN01, max UDMA/100
[    2.118304] ata1.00: ATA-8: ST500DM002-1BD142, KC45, max UDMA/133
[    2.118309] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.133905] ata2.00: configured for UDMA/100
[    2.134184] ata1.00: configured for UDMA/133
[    2.134384] scsi 0:0:0:0: Direct-Access     ATA      ST500DM002-1BD14 KC45 PQ: 0 ANSI: 5
[    2.134577] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    2.134578] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.134580] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    2.134738] sd 0:0:0:0: [sda] Write Protect is off
[    2.134740] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.134840] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.149271] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH24NS90  IN01 PQ: 0 ANSI: 5
[    2.168405] sr0: scsi3-mmc drive: 48x/12x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.168410] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.168551] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.168684] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.172375]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
[    2.173001] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.174072] Freeing unused kernel memory: 1012k freed
[    2.174151] Write protecting the kernel read-only data: 12288k
[    2.176184] Freeing unused kernel memory: 1012k freed
[    2.178168] Freeing unused kernel memory: 1008k freed
[    2.188119] udevd[141]: starting version 175
[    2.200367] Disabling lock debugging due to kernel taint
[    2.202570] Initializing USB Mass Storage driver...
[    2.202647] scsi4 : usb-storage 2-1.6:1.2
[    2.202694] usbcore: registered new interface driver usb-storage
[    2.202695] USB Mass Storage support registered.
[    2.230380] atl1c 0000:06:00.0: version 1.0.1.1-NAPI
[    2.234383] usbcore: registered new interface driver usbhid
[    2.234385] usbhid: USB HID core driver
[    2.235441] input: CHESEN USB Keyboard as /devices/pci0000:00/0000:00:1c.2/0000:05:00.0/usb3/3-2/3-2:1.0/input/input2
[    2.235486] hid-generic 0003:0A81:0101.0001: input,hidraw0: USB HID v1.10 Keyboard [CHESEN USB Keyboard] on usb-0000:05:00.0-2/input0
[    2.242838] input: CHESEN USB Keyboard as /devices/pci0000:00/0000:00:1c.2/0000:05:00.0/usb3/3-2/3-2:1.1/input/input3
[    2.242877] hid-generic 0003:0A81:0101.0002: input,hidraw1: USB HID v1.10 Device [CHESEN USB Keyboard] on usb-0000:05:00.0-2/input1
[    2.243173] input: Logitech Logitech USB Headset as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.3/input/input4
[    2.243233] hid-generic 0003:046D:0A0B.0003: input,hidraw2: USB HID v1.00 Device [Logitech Logitech USB Headset] on usb-0000:00:1d.0-1.2/input3
[    2.243326] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.0/input/input5
[    2.243402] hid-generic 0003:046D:C050.0004: input,hidraw3: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.0-1.5/input0
[    2.850719] EXT4-fs (sda3): mounted filesystem with ordered data mode. Opts: (null)
[    3.199134] scsi 4:0:0:0: Direct-Access     HP       Officejet Pro 85 1.00 PQ: 0 ANSI: 5
[    3.199577] sd 4:0:0:0: Attached scsi generic sg2 type 0
[    3.200927] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[    3.668441] init: ureadahead main process (324) terminated with status 5
[    4.503729] Adding 1951740k swap on /dev/sda5.  Priority:-1 extents:1 across:1951740k 
[    4.952198] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    5.075499] udevd[400]: starting version 175
[    5.863877] lp: driver loaded but no devices found
[    6.063906] parport_pc 00:07: reported by Plug and Play ACPI
[    6.063955] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[    6.157988] lp0: using parport0 (interrupt-driven).
[    6.158167] ppdev: user-space parallel port driver
[    6.209137] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \GP2C 1 (20121018/utaddress-251)
[    6.209143] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    6.209160] lpc_ich: Resource conflict(s) found affecting gpio_ich
[    6.380923] mei 0000:00:16.0: setting latency timer to 64
[    6.380967] mei 0000:00:16.0: irq 42 for MSI/MSI-X
[    6.544983] microcode: CPU0 sig=0x206a7, pf=0x2, revision=0x23
[    6.629165] gpio_ich: GPIO from 180 to 255 on gpio_ich
[    6.831891] [drm] Initialized drm 1.1.0 20060810
[    6.915483] microcode: CPU1 sig=0x206a7, pf=0x2, revision=0x23
[    6.916232] microcode: CPU2 sig=0x206a7, pf=0x2, revision=0x23
[    6.916936] microcode: CPU3 sig=0x206a7, pf=0x2, revision=0x23
[    6.917603] microcode: CPU4 sig=0x206a7, pf=0x2, revision=0x23
[    6.918302] microcode: CPU5 sig=0x206a7, pf=0x2, revision=0x23
[    6.918961] microcode: CPU6 sig=0x206a7, pf=0x2, revision=0x23
[    6.919599] microcode: CPU7 sig=0x206a7, pf=0x2, revision=0x23
[    6.920282] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    7.510021] usbcore: registered new interface driver snd-usb-audio
[    7.656833] snd_hda_intel 0000:00:1b.0: irq 43 for MSI/MSI-X
[    7.768000] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[    7.768060] input: HDA Intel PCH Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[    7.768095] input: HDA Intel PCH Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[    7.768129] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[    7.768159] input: HDA Intel PCH Line Out as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[    7.768274] hda_intel: Disabling MSI
[    7.768278] hda-intel 0000:01:00.1: Handle VGA-switcheroo audio client
[    8.603002] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card2/input11
[    8.603084] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card2/input12
[    8.603156] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card2/input13
[    8.603228] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card2/input14
[    8.887918] type=1400 audit(1381391521.478:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=778 comm="apparmor_parser"
[    8.887925] type=1400 audit(1381391521.478:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=768 comm="apparmor_parser"
[    8.888153] type=1400 audit(1381391521.478:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=778 comm="apparmor_parser"
[    8.888159] type=1400 audit(1381391521.478:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=768 comm="apparmor_parser"
[    8.888285] type=1400 audit(1381391521.478:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=778 comm="apparmor_parser"
[    8.888293] type=1400 audit(1381391521.478:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=768 comm="apparmor_parser"
[    9.242297] nvidia: module license 'NVIDIA' taints kernel.
[    9.247374] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[    9.247492] [drm] Initialized nvidia-drm 0.0.0 20130102 for 0000:01:00.0 on minor 0
[    9.247498] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  319.32  Wed Jun 19 15:51:20 PDT 2013
[    9.647392] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro
[   10.432155] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   10.791836] init: failsafe main process (1000) killed by TERM signal
[   11.781680] type=1400 audit(1381391524.378:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1055 comm="apparmor_parser"
[   11.781947] type=1400 audit(1381391524.382:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1055 comm="apparmor_parser"
[   11.782085] type=1400 audit(1381391524.382:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1055 comm="apparmor_parser"
[   11.986402] type=1400 audit(1381391524.586:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1061 comm="apparmor_parser"
[   14.583117] Bluetooth: Core ver 2.16
[   14.583130] NET: Registered protocol family 31
[   14.583131] Bluetooth: HCI device and connection manager initialized
[   14.583137] Bluetooth: HCI socket layer initialized
[   14.583138] Bluetooth: L2CAP socket layer initialized
[   14.583141] Bluetooth: SCO socket layer initialized
[   14.607838] vboxdrv: Found 8 processor cores.
[   14.607954] vboxdrv: fAsync=0 offMin=0x203 offMax=0x27d0
[   14.608011] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   14.608012] vboxdrv: Successfully loaded version 4.2.18 (interface 0x001a0005).
[   14.693570] Bluetooth: RFCOMM TTY layer initialized
[   14.693578] Bluetooth: RFCOMM socket layer initialized
[   14.693580] Bluetooth: RFCOMM ver 1.11
[   14.895144] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   14.895146] Bluetooth: BNEP filters: protocol multicast
[   14.895159] Bluetooth: BNEP socket layer initialized
[   15.110836] vboxpci: IOMMU not found (not registered)
[   17.669537] atl1c 0000:06:00.0: irq 44 for MSI/MSI-X
[   17.670083] atl1c 0000:06:00.0: atl1c: eth0 NIC Link is Up<100 Mbps Full Duplex>
[   48.742827] audit_printk_skb: 48 callbacks suppressed
[   48.742829] type=1400 audit(1381391561.436:28): apparmor="DENIED" operation="capable" parent=1 profile="/usr/sbin/cupsd" pid=1164 comm="cupsd" pid=1164 comm="cupsd" capability=36  capname="block_suspend"
[   49.255819] type=1400 audit(1381391561.948:29): apparmor="DENIED" operation="capable" parent=1 profile="/usr/sbin/cupsd" pid=1164 comm="cupsd" pid=1164 comm="cupsd" capability=36  capname="block_suspend"
[   55.996230] type=1400 audit(1381391568.704:30): apparmor="DENIED" operation="capable" parent=1 profile="/usr/sbin/cupsd" pid=1164 comm="cupsd" pid=1164 comm="cupsd" capability=36  capname="block_suspend"
[   67.087911] WARNING! power/level is deprecated; use power/control instead
[   67.123998] usblp 2-1.6:1.1: usblp0: USB Bidirectional printer dev 5 if 1 alt 0 proto 2 vid 0x03F0 pid 0x5312
[   67.124341] usblp 2-1.6:1.3: usblp1: USB Bidirectional printer dev 5 if 3 alt 0 proto 2 vid 0x03F0 pid 0x5312
[   67.124363] usbcore: registered new interface driver usblp
[   67.165335] init: udev-fallback-graphics main process (1594) terminated with status 1
[   67.178071] init: plymouth-splash main process (1603) terminated with status 1
[   68.595248] usblp0: removed
[   68.595918] usblp 2-1.6:1.1: usblp0: USB Bidirectional printer dev 5 if 1 alt 0 proto 2 vid 0x03F0 pid 0x5312
[   68.595991] usblp1: removed
[   68.597018] usblp 2-1.6:1.3: usblp1: USB Bidirectional printer dev 5 if 3 alt 0 proto 2 vid 0x03F0 pid 0x5312
[   68.597470] type=1400 audit(1381391581.338:31): apparmor="DENIED" operation="capable" parent=1 profile="/usr/sbin/cupsd" pid=1164 comm="cupsd" pid=1164 comm="cupsd" capability=36  capname="block_suspend"
[   75.856655] type=1400 audit(1381391588.610:32): apparmor="DENIED" operation="capable" parent=1 profile="/usr/sbin/cupsd" pid=1164 comm="cupsd" pid=1164 comm="cupsd" capability=36  capname="block_suspend"
[   92.359749] type=1400 audit(1381391605.154:33): apparmor="DENIED" operation="capable" parent=1 profile="/usr/sbin/cupsd" pid=1164 comm="cupsd" pid=1164 comm="cupsd" capability=36  capname="block_suspend"
[   98.680730] type=1400 audit(1381391611.491:34): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/telepathy/mission-control-5" name="/usr/share/gvfs/remote-volume-monitors/" pid=2366 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0

```

Any ideas?

---

### Post by theDaveTheRave on 2013-10-10
Neils1974,

I've had a quick search through your dmesg and found these lines 

lines : 660 - 663
```

 [    2.022691] usb 2-1.6: New USB device found, idVendor=03f0, idProduct=5312
        [    2.022696] usb 2-1.6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
        [    2.022699] usb 2-1.6: Product: Officejet Pro 8500 A910
        [    2.022701] usb 2-1.6: Manufacturer: HP

```

```

[   67.123998] usblp 2-1.6:1.1: usblp0: USB Bidirectional printer dev 5 if 1 alt 0 proto 2 vid 0x03F0 pid 0x5312
        [   67.124341] usblp 2-1.6:1.3: usblp1: USB Bidirectional printer dev 5 if 3 alt 0 proto 2 vid 0x03F0 pid 0x5312
        [   67.124363] usbcore: registered new interface driver usblp
        [   67.165335] init: udev-fallback-graphics main process (1594) terminated with status 1
        [   67.178071] init: plymouth-splash main process (1603) terminated with status 1
        [   68.595248] usblp0: removed
        [   68.595918] usblp 2-1.6:1.1: usblp0: USB Bidirectional printer dev 5 if 1 alt 0 proto 2 vid 0x03F0 pid 0x5312
        [   68.595991] usblp1: removed
        [   68.597018] usblp 2-1.6:1.3: usblp1: USB Bidirectional printer dev 5 if 3 alt 0 proto 2 vid 0x03F0 pid 0x5312

```

I'm no expert, but it looks as though the device is loading then being re-loaded.

I've had a quick look for usblp (part of cups) and a couple of threads seem to propose that it is no longer needed ?? not sure if this is true on ubuntu or not.

There seems to be lots of info on the [Arch wiki]("https://wiki.archlinux.org/index.php/CUPS"). Check out the section on [USB printers and usblp]("https://wiki.archlinux.org/index.php/CUPS#Hardware_support_and_configuration")

A quick read of the [link]("http://lists.linuxfoundation.org/pipermail/printing-architecture/2012/002412.html") supplied in the above passage, reads...

> 
Formerly, under Unix everything was a file, but now, with printers being 
more complex, one moves to general USB device access as supplied via 
libusb. HP's CUPS backend as shipped with HPLIP for example is 
libusb-based and detaches printers from the usblp kernel module. On HP's 
multi-function devices one can do things like simultaneous, independent 
printing and scanning.


so it seems that blacklisting usblp may help you ?? you'll need to check it out.

Other than that, you need to confirm that the problem realy has been caused by the printer, so try booting up without the device attached to the pc, check the time to boot. Then after you attach the printer, send the tail end of dmesg , just to be sure we are looking at the correct thing, it may also be usefull to send out the messages from CUPS...

```

tail /var/log/cups/error_log

```
and also 
```

tail /var/log/cups/access_log

```

may be helpull.... you may need to adjust the number of lines in you tail (it will default to the last 10).... eg for the last 30 lines
```

tail -n 30 /var/log/cups/error_log

```

Good luck....

David

---

### Post by Niels1974 on 2013-10-11
Thanks for the help!

When I remove the USB cable that connects computer and printer from the computer, the computer boots normally. That is, no text login appears and lightdm starts immediately. It thus appears to be related to my printer (HP officejet pro 8500A plus).

dmesg output:
```
[   13.675037] Bluetooth: BNEP socket layer initialized
[   13.899095] vboxpci: IOMMU not found (not registered)
[   15.619647] atl1c 0000:06:00.0: irq 44 for MSI/MSI-X
[   15.620204] atl1c 0000:06:00.0: atl1c: eth0 NIC Link is Up<100 Mbps Full Duplex>
[   52.370111] audit_printk_skb: 48 callbacks suppressed
[   52.370114] type=1400 audit(1381477912.069:28): apparmor="DENIED" operation="capable" parent=1 profile="/usr/sbin/cupsd" pid=1163 comm="cupsd" pid=1163 comm="cupsd" capability=36  capname="block_suspend"
[   56.855763] type=1400 audit(1381477916.567:29): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/telepathy/mission-control-5" name="/usr/share/gvfs/remote-volume-monitors/" pid=2255 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
```

output from more /var/log/cups/error_log
```
W [10/Oct/2013:09:05:44 +0100] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Officejet_Pro_8500_A910' already exists
W [10/Oct/2013:09:05:44 +0100] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Officejet_Pro_8500_A910_fax-Gray..' already exists
W [10/Oct/2013:09:05:44 +0100] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Officejet_Pro_8500_A910_fax-RGB..' already exists
W [10/Oct/2013:09:05:44 +0100] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Officejet_Pro_8500_A910_fax' already exists
E [10/Oct/2013:14:16:27 +0100] Unknown directive SystemGroup on line 16 of /etc/cups/cupsd.conf.
W [10/Oct/2013:14:16:34 +0100] failed to CreateProfile: org.freedesktop.DBus.Error.NoReply:Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
E [10/Oct/2013:14:18:14 +0100] Avahi client failed, closing client to allow a clean restart
E [11/Oct/2013:08:51:14 +0100] Unknown directive SystemGroup on line 16 of /etc/cups/cupsd.conf.
W [11/Oct/2013:08:51:21 +0100] failed to CreateProfile: org.freedesktop.DBus.Error.NoReply:Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
W [11/Oct/2013:08:51:26 +0100] failed to CreateProfile: org.freedesktop.DBus.Error.NoReply:Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
```

Output from more /var/log/cups/access_log

```
localhost - - [10/Oct/2013:14:17:19 +0100] "POST / HTTP/1.1" 401 244 CUPS-Get-Devices successful-ok
localhost - root [10/Oct/2013:14:17:20 +0100] "POST / HTTP/1.1" 200 2691 CUPS-Get-Devices -
localhost - - [10/Oct/2013:14:17:49 +0100] "POST / HTTP/1.1" 200 176 Create-Printer-Subscription successful-ok
localhost - - [10/Oct/2013:14:31:50 +0100] "POST / HTTP/1.1" 401 186 Renew-Subscription successful-ok
localhost - username [10/Oct/2013:14:31:50 +0100] "POST / HTTP/1.1" 200 186 Renew-Subscription successful-ok
localhost - username [10/Oct/2013:14:45:50 +0100] "POST / HTTP/1.1" 200 186 Renew-Subscription successful-ok
localhost - username [10/Oct/2013:14:59:50 +0100] "POST / HTTP/1.1" 200 186 Renew-Subscription successful-ok
localhost - username [10/Oct/2013:15:13:50 +0100] "POST / HTTP/1.1" 200 186 Renew-Subscription successful-ok
localhost - username [10/Oct/2013:15:27:50 +0100] "POST / HTTP/1.1" 200 186 Renew-Subscription successful-ok
localhost - - [11/Oct/2013:08:51:52 +0100] "POST / HTTP/1.1" 200 176 Create-Printer-Subscription successful-ok
```

I will look into blacklisting the usblp. However, this is my office computer and I do not have much time. If this were the problem, I am surprised it is not affecting more people. Could it be a hardware defect with a usb port?

Thanks again for your help! Much appreciated.

---

### Post by theDaveTheRave on 2013-10-11
So we can assume that it is somehow connected to the connection of the printer to the system.

Just to confirm what I understand from your last post.

You and your colleagues are all running linux desktops ~  Good on you.

They all have this same printer plugged into thier workstations ? How many of these printers do you have ? 

Have you tried swapping your printer for one from your colleagues, it could be that the usb port on the printer is at fault.
Obviously also try connecting your printer (and your colleagues) to various usb ports.

Finaly I'm not sure if it is possible, maybe someone else on the forums would be able to help, but it may be that you can prevent the printer daemon from starting up untill later in the boot cycle (ie at a later run level)

I assume that this would normally be done during run level 1 or 2, you may be able to get it to run through during run level 3 (this is user land, and doesn't kick in untill the user is actually logged in ~ as far as I understand).

Alternatively you may be able to chage the 'nice' value, to prevent it from hogging resources, not sure if this will actually make any difference or not.

David

---

