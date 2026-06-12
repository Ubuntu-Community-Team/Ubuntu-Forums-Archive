---
title: "Very slow Boot in Ubuntu 14.04"
date: 2014-04-23
forum: General Help
---

### Post by jab6 on 2014-04-23
Hi,

i installed Lubuntu 14.04 from scratch. I used Ubuntu 10.04 before. Unfortunately boot time increased a lot. My setup may be a little bit non standard but according to best practices:
AMD Athlon(tm) II X4 620
4 GB of RAM
2x SATA HDD
- Software Raid 1 on top of the two discs (md126)
- There is a Raid 1 for /boot with ext4 (md127)
- Full disc encryption using LUKS on top of md126

You can see the problem in dmesg. Luks promt appears after about 60s.

May be similar to this problem: [http://ubuntuforums.org/showthread.php?t=2217967](http://ubuntuforums.org/showthread.php?t=2217967)

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.13.0-24-generic (buildd@panlong) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #46-Ubuntu SMP Thu Apr 10 19:11:08 UTC 2014 (Ubuntu 3.13.0-24.46-generic 3.13.9)
[    0.000000] Command line: BOOT_IMAGE=/vmlinuz-3.13.0-24-generic root=UUID=444dd5ef-45e8-4c93-8bee-c5ba8383512d ro quiet splash nomdmonddf nomdmonisw vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009f7ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009f800-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000f0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000cfddffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000cfde0000-0x00000000cfde2fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000cfde3000-0x00000000cfdeffff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000cfdf0000-0x00000000cfdfffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000012fffffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.4 present.
[    0.000000] DMI: Gigabyte Technology Co., Ltd. GA-MA770T-UD3P/GA-MA770T-UD3P, BIOS F3 08/06/2009
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x130000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
[    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
[    0.000000]   2 base 0000C0000000 mask FFFFF0000000 write-back
[    0.000000]   3 base 0000CFE00000 mask FFFFFFE00000 uncachable
[    0.000000]   4 base 000100000000 mask FFFFE0000000 write-back
[    0.000000]   5 base 000120000000 mask FFFFF0000000 write-back
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 0000000130000000 aka 4864M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 256MB, type WB
[    0.000000] reg 3, base: 3326MB, range: 2MB, type UC
[    0.000000] reg 4, base: 4GB, range: 512MB, type WB
[    0.000000] reg 5, base: 4608MB, range: 256MB, type WB
[    0.000000] total RAM covered: 3326M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 4M     num_reg: 4      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 256MB, type WB
[    0.000000] reg 3, base: 3326MB, range: 2MB, type UC
[    0.000000] e820: update [mem 0xcfe00000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xcfde0 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000f55a0-0x000f55af] mapped at [ffff8800000f55a0]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 24576
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01fdd000, 0x01fddfff] PGTABLE
[    0.000000] BRK [0x01fde000, 0x01fdefff] PGTABLE
[    0.000000] BRK [0x01fdf000, 0x01fdffff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x12fe00000-0x12fffffff]
[    0.000000]  [mem 0x12fe00000-0x12fffffff] page 2M
[    0.000000] BRK [0x01fe0000, 0x01fe0fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x12c000000-0x12fdfffff]
[    0.000000]  [mem 0x12c000000-0x12fdfffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x100000000-0x12bffffff]
[    0.000000]  [mem 0x100000000-0x12bffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0xcfddffff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x3fffffff] page 2M
[    0.000000]  [mem 0x40000000-0xbfffffff] page 1G
[    0.000000]  [mem 0xc0000000-0xcfbfffff] page 2M
[    0.000000]  [mem 0xcfc00000-0xcfddffff] page 4k
[    0.000000] RAMDISK: [mem 0x348ee000-0x3646efff]
[    0.000000] ACPI: RSDP 00000000000f6fb0 000014 (v00 GBT   )
[    0.000000] ACPI: RSDT 00000000cfde3000 00003C (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: FACP 00000000cfde3040 000074 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: DSDT 00000000cfde30c0 005E23 (v01 GBT    GBTUACPI 00001000 MSFT 03000000)
[    0.000000] ACPI: FACS 00000000cfde0000 000040
[    0.000000] ACPI: SSDT 00000000cfde8fc0 00088C (v01 PTLTD  POWERNOW 00000001  LTP 00000001)
[    0.000000] ACPI: HPET 00000000cfde9880 000038 (v01 GBT    GBTUACPI 42302E31 GBTU 00000098)
[    0.000000] ACPI: MCFG 00000000cfde98c0 00003C (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: TAMG 00000000cfde9900 0002FA (v01 GBT    GBT   B0 5455312E BG?? 53450101)
[    0.000000] ACPI: APIC 00000000cfde8f00 000084 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000012fffffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x12fffffff]
[    0.000000]   NODE_DATA [mem 0x12fff9000-0x12fffdfff]
[    0.000000]  [ffffea0000000000-ffffea0004bfffff] PMD -> [ffff88012b600000-ffff88012f5fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x12fffffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009efff]
[    0.000000]   node   0: [mem 0x00100000-0xcfddffff]
[    0.000000]   node   0: [mem 0x100000000-0x12fffffff]
[    0.000000] On node 0 totalpages: 1047934
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3998 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 13240 pages used for memmap
[    0.000000]   DMA32 zone: 847328 pages, LIFO batch:31
[    0.000000]   Normal zone: 3072 pages used for memmap
[    0.000000]   Normal zone: 196608 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x10b9a201 base: 0xfed00000
[    0.000000] smpboot: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000effff]
[    0.000000] PM: Registered nosave memory: [mem 0x000f0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xcfde0000-0xcfde2fff]
[    0.000000] PM: Registered nosave memory: [mem 0xcfde3000-0xcfdeffff]
[    0.000000] PM: Registered nosave memory: [mem 0xcfdf0000-0xcfdfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xcfe00000-0xdfffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xffffffff]
[    0.000000] e820: [mem 0xcfe00000-0xdfffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 29 pages/cpu @ffff88012fc00000 s86336 r8192 d24256 u524288
[    0.000000] pcpu-alloc: s86336 r8192 d24256 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1031537
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-3.13.0-24-generic root=UUID=444dd5ef-45e8-4c93-8bee-c5ba8383512d ro quiet splash nomdmonddf nomdmonisw vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Node 0: aperture @ 6442000000 size 32 MB
[    0.000000] Aperture beyond 4GB. Ignoring.
[    0.000000] Your BIOS doesn't leave a aperture memory hole
[    0.000000] Please enable the IOMMU option in the BIOS setup
[    0.000000] This costs you 64 MB of RAM
[    0.000000] Mapping aperture over 65536 KB of RAM @ c4000000
[    0.000000] PM: Registered nosave memory: [mem 0xc4000000-0xc7ffffff]
[    0.000000] Memory: 3949356K/4191736K available (7338K kernel code, 1138K rwdata, 3388K rodata, 1332K init, 1440K bss, 242380K reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
[    0.000000]     Offload RCU callbacks from all CPUs
[    0.000000]     Offload RCU callbacks from CPUs: 0-3.
[    0.000000] NR_IRQS:16640 nr_irqs:712 16
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 16777216 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.004000] tsc: Fast TSC calibration using PIT
[    0.008000] tsc: Detected 2611.774 MHz processor
[    0.000003] Calibrating delay loop (skipped), value calculated using timer frequency.. 5223.54 BogoMIPS (lpj=10447096)
[    0.000006] pid_max: default: 32768 minimum: 301
[    0.000028] Security Framework initialized
[    0.000042] AppArmor: AppArmor initialized
[    0.000044] Yama: becoming mindful.
[    0.000437] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.001590] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.002092] Mount-cache hash table entries: 8192 (order: 4, 65536 bytes)
[    0.002101] Mountpoint-cache hash table entries: 8192 (order: 4, 65536 bytes)
[    0.002304] Initializing cgroup subsys memory
[    0.002311] Initializing cgroup subsys devices
[    0.002312] Initializing cgroup subsys freezer
[    0.002314] Initializing cgroup subsys blkio
[    0.002315] Initializing cgroup subsys perf_event
[    0.002318] Initializing cgroup subsys hugetlb
[    0.002335] tseg: 00cfe00000
[    0.002338] CPU: Physical Processor ID: 0
[    0.002339] CPU: Processor Core ID: 0
[    0.002341] mce: CPU supports 6 MCE banks
[    0.002346] LVT offset 0 assigned for vector 0xf9
[    0.002351] Last level iTLB entries: 4KB 512, 2MB 16, 4MB 8
[    0.002351] Last level dTLB entries: 4KB 512, 2MB 128, 4MB 64
[    0.002351] tlb_flushall_shift: 4
[    0.002444] Freeing SMP alternatives memory: 32K (ffffffff81e6b000 - ffffffff81e73000)
[    0.003197] ACPI: Core revision 20131115
[    0.004936] ACPI: All ACPI Tables successfully acquired
[    0.018830] ftrace: allocating 28408 entries in 111 pages
[    0.031023] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.070702] smpboot: CPU0: AMD Athlon(tm) II X4 620 Processor (fam: 10, model: 05, stepping: 02)
[    0.176873] Performance Events: AMD PMU driver.
[    0.176877] ... version:                0
[    0.176878] ... bit width:              48
[    0.176879] ... generic registers:      4
[    0.176880] ... value mask:             0000ffffffffffff
[    0.176881] ... max period:             00007fffffffffff
[    0.176882] ... fixed-purpose events:   0
[    0.176883] ... event mask:             000000000000000f
[    0.178369] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.178448] x86: Booting SMP configuration:
[    0.178450] .... node  #0, CPUs:      #1 #2 #3
[    0.217717] x86: Booted up 1 node, 4 CPUs
[    0.217719] smpboot: Total of 4 processors activated (20894.19 BogoMIPS)
[    0.218561] devtmpfs: initialized
[    0.221804] EVM: security.selinux
[    0.221805] EVM: security.SMACK64
[    0.221807] EVM: security.ima
[    0.221808] EVM: security.capability
[    0.221908] PM: Registering ACPI NVS region [mem 0xcfde0000-0xcfde2fff] (12288 bytes)
[    0.222851] pinctrl core: initialized pinctrl subsystem
[    0.222919] regulator-dummy: no parameters
[    0.222947] RTC time: 17:46:37, date: 04/23/14
[    0.222986] NET: Registered protocol family 16
[    0.223103] cpuidle: using governor ladder
[    0.223105] cpuidle: using governor menu
[    0.223109] node 0 link 0: io port [c000, ffff]
[    0.223111] TOM: 00000000d0000000 aka 3328M
[    0.223124] Fam 10h mmconf [mem 0xe0000000-0xe00fffff]
[    0.223126] node 0 link 0: mmio [a0000, bffff]
[    0.223129] node 0 link 0: mmio [d0000000, dfffffff]
[    0.223131] node 0 link 0: mmio [f0000000, fe02ffff]
[    0.223133] node 0 link 0: mmio [e0000000, e03fffff] ==> [e0100000, e03fffff]
[    0.223135] TOM2: 0000000130000000 aka 4864M
[    0.223137] bus: [bus 00-03] on node 0 link 0
[    0.223139] bus: 00 [io  0x0000-0xffff]
[    0.223140] bus: 00 [mem 0x000a0000-0x000bffff]
[    0.223142] bus: 00 [mem 0xd0000000-0xdfffffff]
[    0.223143] bus: 00 [mem 0xe0400000-0xffffffff]
[    0.223144] bus: 00 [mem 0xe0100000-0xe03fffff]
[    0.223145] bus: 00 [mem 0x130000000-0xfcffffffff]
[    0.223225] ACPI: bus type PCI registered
[    0.223227] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.223283] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.223285] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.232219] PCI: Using configuration type 1 for base access
[    0.233294] bio: create slab <bio-0> at 0
[    0.233471] ACPI: Added _OSI(Module Device)
[    0.233473] ACPI: Added _OSI(Processor Device)
[    0.233474] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.233475] ACPI: Added _OSI(Processor Aggregator Device)
[    0.237736] ACPI: Interpreter enabled
[    0.237746] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20131115/hwxface-580)
[    0.237750] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)
[    0.237763] ACPI: (supports S0 S3 S4 S5)
[    0.237764] ACPI: Using IOAPIC for interrupt routing
[    0.237827] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.237927] ACPI: No dock devices found.
[    0.281823] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.281831] acpi PNP0A03:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.281836] acpi PNP0A03:00: _OSC failed (AE_NOT_FOUND); disabling ASPM
[    0.282082] PCI host bridge to bus 0000:00
[    0.282085] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.282087] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.282089] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.282091] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.282093] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000dffff]
[    0.282094] pci_bus 0000:00: root bus resource [mem 0xcff00000-0xfebfffff]
[    0.282104] pci 0000:00:00.0: [1002:5957] type 00 class 0x060000
[    0.282116] pci 0000:00:00.0: reg 0x1c: [mem 0xe0000000-0xffffffff 64bit]
[    0.282202] pci 0000:00:02.0: [1002:5978] type 01 class 0x060400
[    0.282233] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.282278] pci 0000:00:02.0: System wakeup disabled by ACPI
[    0.282313] pci 0000:00:0a.0: [1002:597f] type 01 class 0x060400
[    0.282343] pci 0000:00:0a.0: PME# supported from D0 D3hot D3cold
[    0.282386] pci 0000:00:0a.0: System wakeup disabled by ACPI
[    0.282432] pci 0000:00:11.0: [1002:4391] type 00 class 0x010601
[    0.282451] pci 0000:00:11.0: reg 0x10: [io  0xff00-0xff07]
[    0.282460] pci 0000:00:11.0: reg 0x14: [io  0xfe00-0xfe03]
[    0.282469] pci 0000:00:11.0: reg 0x18: [io  0xfd00-0xfd07]
[    0.282479] pci 0000:00:11.0: reg 0x1c: [io  0xfc00-0xfc03]
[    0.282488] pci 0000:00:11.0: reg 0x20: [io  0xfb00-0xfb0f]
[    0.282498] pci 0000:00:11.0: reg 0x24: [mem 0xfe02f000-0xfe02f3ff]
[    0.282605] pci 0000:00:12.0: [1002:4397] type 00 class 0x0c0310
[    0.282619] pci 0000:00:12.0: reg 0x10: [mem 0xfe02e000-0xfe02efff]
[    0.282712] pci 0000:00:12.0: System wakeup disabled by ACPI
[    0.282737] pci 0000:00:12.1: [1002:4398] type 00 class 0x0c0310
[    0.282750] pci 0000:00:12.1: reg 0x10: [mem 0xfe02d000-0xfe02dfff]
[    0.282843] pci 0000:00:12.1: System wakeup disabled by ACPI
[    0.282874] pci 0000:00:12.2: [1002:4396] type 00 class 0x0c0320
[    0.282892] pci 0000:00:12.2: reg 0x10: [mem 0xfe02c000-0xfe02c0ff]
[    0.282973] pci 0000:00:12.2: supports D1 D2
[    0.282975] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.283021] pci 0000:00:12.2: System wakeup disabled by ACPI
[    0.283052] pci 0000:00:13.0: [1002:4397] type 00 class 0x0c0310
[    0.283066] pci 0000:00:13.0: reg 0x10: [mem 0xfe02b000-0xfe02bfff]
[    0.283171] pci 0000:00:13.0: System wakeup disabled by ACPI
[    0.283197] pci 0000:00:13.1: [1002:4398] type 00 class 0x0c0310
[    0.283210] pci 0000:00:13.1: reg 0x10: [mem 0xfe02a000-0xfe02afff]
[    0.283304] pci 0000:00:13.1: System wakeup disabled by ACPI
[    0.283335] pci 0000:00:13.2: [1002:4396] type 00 class 0x0c0320
[    0.283354] pci 0000:00:13.2: reg 0x10: [mem 0xfe029000-0xfe0290ff]
[    0.283435] pci 0000:00:13.2: supports D1 D2
[    0.283437] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.283483] pci 0000:00:13.2: System wakeup disabled by ACPI
[    0.283518] pci 0000:00:14.0: [1002:4385] type 00 class 0x0c0500
[    0.283665] pci 0000:00:14.1: [1002:439c] type 00 class 0x01018a
[    0.283681] pci 0000:00:14.1: reg 0x10: [io  0x0000-0x0007]
[    0.283690] pci 0000:00:14.1: reg 0x14: [io  0x0000-0x0003]
[    0.283699] pci 0000:00:14.1: reg 0x18: [io  0x0000-0x0007]
[    0.283708] pci 0000:00:14.1: reg 0x1c: [io  0x0000-0x0003]
[    0.283718] pci 0000:00:14.1: reg 0x20: [io  0xfa00-0xfa0f]
[    0.283825] pci 0000:00:14.2: [1002:4383] type 00 class 0x040300
[    0.283846] pci 0000:00:14.2: reg 0x10: [mem 0xfe024000-0xfe027fff 64bit]
[    0.283911] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.283956] pci 0000:00:14.2: System wakeup disabled by ACPI
[    0.283981] pci 0000:00:14.3: [1002:439d] type 00 class 0x060100
[    0.284106] pci 0000:00:14.4: [1002:4384] type 01 class 0x060401
[    0.284178] pci 0000:00:14.4: System wakeup disabled by ACPI
[    0.284203] pci 0000:00:14.5: [1002:4399] type 00 class 0x0c0310
[    0.284216] pci 0000:00:14.5: reg 0x10: [mem 0xfe028000-0xfe028fff]
[    0.284309] pci 0000:00:14.5: System wakeup disabled by ACPI
[    0.284338] pci 0000:00:18.0: [1022:1200] type 00 class 0x060000
[    0.284402] pci 0000:00:18.1: [1022:1201] type 00 class 0x060000
[    0.284463] pci 0000:00:18.2: [1022:1202] type 00 class 0x060000
[    0.284524] pci 0000:00:18.3: [1022:1203] type 00 class 0x060000
[    0.284588] pci 0000:00:18.4: [1022:1204] type 00 class 0x060000
[    0.284698] pci 0000:01:00.0: [1002:954f] type 00 class 0x030000
[    0.284710] pci 0000:01:00.0: reg 0x10: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.284720] pci 0000:01:00.0: reg 0x18: [mem 0xfdfe0000-0xfdfeffff 64bit]
[    0.284727] pci 0000:01:00.0: reg 0x20: [io  0xee00-0xeeff]
[    0.284738] pci 0000:01:00.0: reg 0x30: [mem 0x00000000-0x0001ffff pref]
[    0.284766] pci 0000:01:00.0: supports D1 D2
[    0.284800] pci 0000:01:00.1: [1002:aa38] type 00 class 0x040300
[    0.284812] pci 0000:01:00.1: reg 0x10: [mem 0xfdffc000-0xfdffffff 64bit]
[    0.284864] pci 0000:01:00.1: supports D1 D2
[    0.291140] pci 0000:00:02.0: PCI bridge to [bus 01]
[    0.291148] pci 0000:00:02.0:   bridge window [io  0xe000-0xefff]
[    0.291150] pci 0000:00:02.0:   bridge window [mem 0xfdf00000-0xfdffffff]
[    0.291154] pci 0000:00:02.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.291222] pci 0000:02:00.0: [10ec:8168] type 00 class 0x020000
[    0.291236] pci 0000:02:00.0: reg 0x10: [io  0xde00-0xdeff]
[    0.291257] pci 0000:02:00.0: reg 0x18: [mem 0xfdbff000-0xfdbfffff 64bit pref]
[    0.291270] pci 0000:02:00.0: reg 0x20: [mem 0xfdbe0000-0xfdbeffff 64bit pref]
[    0.291279] pci 0000:02:00.0: reg 0x30: [mem 0x00000000-0x0000ffff pref]
[    0.291325] pci 0000:02:00.0: supports D1 D2
[    0.291327] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.299141] pci 0000:00:0a.0: PCI bridge to [bus 02]
[    0.299148] pci 0000:00:0a.0:   bridge window [io  0xd000-0xdfff]
[    0.299151] pci 0000:00:0a.0:   bridge window [mem 0xfde00000-0xfdefffff]
[    0.299154] pci 0000:00:0a.0:   bridge window [mem 0xfdb00000-0xfdbfffff 64bit pref]
[    0.299234] pci 0000:03:0e.0: [104c:8024] type 00 class 0x0c0010
[    0.299258] pci 0000:03:0e.0: reg 0x10: [mem 0xfddff000-0xfddff7ff]
[    0.299271] pci 0000:03:0e.0: reg 0x14: [mem 0xfddf8000-0xfddfbfff]
[    0.299364] pci 0000:03:0e.0: supports D1 D2
[    0.299366] pci 0000:03:0e.0: PME# supported from D0 D1 D2 D3hot
[    0.299427] pci 0000:00:14.4: PCI bridge to [bus 03] (subtractive decode)
[    0.299431] pci 0000:00:14.4:   bridge window [io  0xc000-0xcfff]
[    0.299435] pci 0000:00:14.4:   bridge window [mem 0xfdd00000-0xfddfffff]
[    0.299439] pci 0000:00:14.4:   bridge window [mem 0xfdc00000-0xfdcfffff pref]
[    0.299442] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.299444] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.299446] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.299448] pci 0000:00:14.4:   bridge window [mem 0x000c0000-0x000dffff] (subtractive decode)
[    0.299450] pci 0000:00:14.4:   bridge window [mem 0xcff00000-0xfebfffff] (subtractive decode)
[    0.315232] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.315280] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.315321] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.315361] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.315401] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.315441] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.315481] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.315521] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.316010] ACPI: \_SB_.PCI0: notify handler is installed
[    0.316045] Found 1 acpi root devices
[    0.316172] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.316174] vgaarb: loaded
[    0.316175] vgaarb: bridge control possible 0000:01:00.0
[    0.316335] SCSI subsystem initialized
[    0.316422] libata version 3.00 loaded.
[    0.316439] ACPI: bus type USB registered
[    0.316457] usbcore: registered new interface driver usbfs
[    0.316465] usbcore: registered new interface driver hub
[    0.316488] usbcore: registered new device driver usb
[    0.316621] PCI: Using ACPI for IRQ routing
[    0.324990] PCI: pci_cache_line_size set to 64 bytes
[    0.324998] pci 0000:00:00.0: no compatible bridge window for [mem 0xe0000000-0xffffffff 64bit]
[    0.325053] e820: reserve RAM buffer [mem 0x0009f800-0x0009ffff]
[    0.325055] e820: reserve RAM buffer [mem 0xcfde0000-0xcfffffff]
[    0.325135] NetLabel: Initializing
[    0.325136] NetLabel:  domain hash size = 128
[    0.325137] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.325147] NetLabel:  unlabeled traffic allowed by default
[    0.325240] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.325244] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    0.327330] Switched to clocksource hpet
[    0.332533] AppArmor: AppArmor Filesystem Enabled
[    0.332560] pnp: PnP ACPI init
[    0.332575] ACPI: bus type PNP registered
[    0.332663] system 00:00: [io  0x04d0-0x04d1] has been reserved
[    0.332665] system 00:00: [io  0x0220-0x0225] has been reserved
[    0.332668] system 00:00: [io  0x0290-0x0294] has been reserved
[    0.332671] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.347497] pnp 00:01: disabling [mem 0x00000000-0x00000fff window] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    0.347523] pnp 00:01: disabling [mem 0x00000000-0x00000fff window disabled] because it overlaps 0000:01:00.0 BAR 6 [mem 0x00000000-0x0001ffff pref]
[    0.347528] pnp 00:01: disabling [mem 0x00000000-0x00000fff window disabled] because it overlaps 0000:02:00.0 BAR 6 [mem 0x00000000-0x0000ffff pref]
[    0.347568] system 00:01: [io  0x4100-0x411f] has been reserved
[    0.347571] system 00:01: [io  0x0228-0x022f] has been reserved
[    0.347573] system 00:01: [io  0x040b] has been reserved
[    0.347574] system 00:01: [io  0x04d6] has been reserved
[    0.347576] system 00:01: [io  0x0c00-0x0c01] has been reserved
[    0.347578] system 00:01: [io  0x0c14] has been reserved
[    0.347580] system 00:01: [io  0x0c50-0x0c52] has been reserved
[    0.347582] system 00:01: [io  0x0c6c-0x0c6d] has been reserved
[    0.347584] system 00:01: [io  0x0c6f] has been reserved
[    0.347586] system 00:01: [io  0x0cd0-0x0cd1] has been reserved
[    0.347588] system 00:01: [io  0x0cd2-0x0cd3] has been reserved
[    0.347590] system 00:01: [io  0x0cd4-0x0cdf] has been reserved
[    0.347592] system 00:01: [io  0x4000-0x40fe] could not be reserved
[    0.347594] system 00:01: [io  0x4210-0x4217] has been reserved
[    0.347596] system 00:01: [io  0x0b00-0x0b0f] has been reserved
[    0.347598] system 00:01: [io  0x0b10-0x0b1f] has been reserved
[    0.347600] system 00:01: [io  0x0b20-0x0b3f] has been reserved
[    0.347602] system 00:01: [mem 0xfee00400-0xfee00fff window] has been reserved
[    0.347606] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.347691] pnp 00:02: [dma 4]
[    0.347707] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.347760] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.347802] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.347823] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.347850] pnp 00:06: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.348112] pnp 00:07: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.348295] pnp 00:08: Plug and Play ACPI device, IDs PNP0400 (active)
[    0.348410] system 00:09: [mem 0xe0000000-0xefffffff] has been reserved
[    0.348413] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.348503] pnp 00:0a: disabling [mem 0x000d1c00-0x000d3fff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    0.348506] pnp 00:0a: disabling [mem 0x000f0000-0x000f7fff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    0.348508] pnp 00:0a: disabling [mem 0x000f8000-0x000fbfff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    0.348511] pnp 00:0a: disabling [mem 0x000fc000-0x000fffff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    0.348513] pnp 00:0a: disabling [mem 0x00000000-0x0009ffff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    0.348516] pnp 00:0a: disabling [mem 0x00100000-0xcfddffff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    0.348552] system 00:0a: [mem 0xcfde0000-0xcfdfffff] could not be reserved
[    0.348554] system 00:0a: [mem 0xffff0000-0xffffffff] has been reserved
[    0.348556] system 00:0a: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.348559] system 00:0a: [mem 0xfee00000-0xfee00fff] could not be reserved
[    0.348561] system 00:0a: [mem 0xfff80000-0xfffeffff] has been reserved
[    0.348563] system 00:0a: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.348580] pnp: PnP ACPI: found 11 devices
[    0.348581] ACPI: bus type PNP unregistered
[    0.354985] pci 0000:01:00.0: BAR 6: assigned [mem 0xfdf00000-0xfdf1ffff pref]
[    0.354989] pci 0000:00:02.0: PCI bridge to [bus 01]
[    0.354992] pci 0000:00:02.0:   bridge window [io  0xe000-0xefff]
[    0.354995] pci 0000:00:02.0:   bridge window [mem 0xfdf00000-0xfdffffff]
[    0.354997] pci 0000:00:02.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.355001] pci 0000:02:00.0: BAR 6: assigned [mem 0xfdb00000-0xfdb0ffff pref]
[    0.355003] pci 0000:00:0a.0: PCI bridge to [bus 02]
[    0.355005] pci 0000:00:0a.0:   bridge window [io  0xd000-0xdfff]
[    0.355008] pci 0000:00:0a.0:   bridge window [mem 0xfde00000-0xfdefffff]
[    0.355010] pci 0000:00:0a.0:   bridge window [mem 0xfdb00000-0xfdbfffff 64bit pref]
[    0.355014] pci 0000:00:14.4: PCI bridge to [bus 03]
[    0.355017] pci 0000:00:14.4:   bridge window [io  0xc000-0xcfff]
[    0.355021] pci 0000:00:14.4:   bridge window [mem 0xfdd00000-0xfddfffff]
[    0.355025] pci 0000:00:14.4:   bridge window [mem 0xfdc00000-0xfdcfffff pref]
[    0.355032] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.355033] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.355035] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.355037] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000dffff]
[    0.355039] pci_bus 0000:00: resource 8 [mem 0xcff00000-0xfebfffff]
[    0.355041] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.355043] pci_bus 0000:01: resource 1 [mem 0xfdf00000-0xfdffffff]
[    0.355045] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.355046] pci_bus 0000:02: resource 0 [io  0xd000-0xdfff]
[    0.355048] pci_bus 0000:02: resource 1 [mem 0xfde00000-0xfdefffff]
[    0.355050] pci_bus 0000:02: resource 2 [mem 0xfdb00000-0xfdbfffff 64bit pref]
[    0.355052] pci_bus 0000:03: resource 0 [io  0xc000-0xcfff]
[    0.355054] pci_bus 0000:03: resource 1 [mem 0xfdd00000-0xfddfffff]
[    0.355055] pci_bus 0000:03: resource 2 [mem 0xfdc00000-0xfdcfffff pref]
[    0.355057] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    0.355059] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
[    0.355061] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    0.355063] pci_bus 0000:03: resource 7 [mem 0x000c0000-0x000dffff]
[    0.355064] pci_bus 0000:03: resource 8 [mem 0xcff00000-0xfebfffff]
[    0.355098] NET: Registered protocol family 2
[    0.355256] TCP established hash table entries: 32768 (order: 6, 262144 bytes)
[    0.355382] TCP bind hash table entries: 32768 (order: 7, 524288 bytes)
[    0.355507] TCP: Hash tables configured (established 32768 bind 32768)
[    0.355546] TCP: reno registered
[    0.355557] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.355581] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.355672] NET: Registered protocol family 1
[    0.779432] pci 0000:01:00.0: Boot video device
[    0.779444] PCI: CLS 4 bytes, default 64
[    0.779513] Trying to unpack rootfs image as initramfs...
[    1.240072] Freeing initrd memory: 28164K (ffff8800348ee000 - ffff88003646f000)
[    1.240317] PCI-DMA: Disabling AGP.
[    1.240405] PCI-DMA: aperture base @ c4000000 size 65536 KB
[    1.240406] PCI-DMA: using GART IOMMU.
[    1.240409] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    1.243527] LVT offset 1 assigned for vector 0x400
[    1.243537] IBS: LVT offset 1 assigned
[    1.243562] perf: AMD IBS detected (0x0000001f)
[    1.243603] microcode: CPU0: patch_level=0x01000086
[    1.243610] microcode: CPU1: patch_level=0x01000086
[    1.243621] microcode: CPU2: patch_level=0x01000086
[    1.243631] microcode: CPU3: patch_level=0x01000086
[    1.243697] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.243698] Scanning for low memory corruption every 60 seconds
[    1.243894] Initialise system trusted keyring
[    1.243940] audit: initializing netlink socket (disabled)
[    1.243951] type=2000 audit(1398275198.136:1): initialized
[    1.269021] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.270317] VFS: Disk quotas dquot_6.5.2
[    1.270363] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.270861] fuse init (API version 7.22)
[    1.270929] msgmni has been set to 7897
[    1.270978] Key type big_key registered
[    1.271468] Key type asymmetric registered
[    1.271472] Asymmetric key parser 'x509' registered
[    1.271524] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    1.271564] io scheduler noop registered
[    1.271566] io scheduler deadline registered (default)
[    1.271590] io scheduler cfq registered
[    1.271810] pcieport 0000:00:02.0: irq 40 for MSI/MSI-X
[    1.271949] pcieport 0000:00:0a.0: irq 41 for MSI/MSI-X
[    1.272003] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.272017] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.272059] vesafb: mode is 1400x1050x32, linelength=5632, pages=0
[    1.272060] vesafb: scrolling: redraw
[    1.272062] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[    1.272277] vesafb: framebuffer at 0xd0000000, mapped to 0xffffc90010780000, using 5824k, total 5824k
[    1.287366] Console: switching to colour frame buffer device 175x65
[    1.302257] fb0: VESA VGA frame buffer device
[    1.302274] ipmi message handler version 39.2
[    1.302322] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    1.302326] ACPI: Power Button [PWRB]
[    1.302365] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.302367] ACPI: Power Button [PWRF]
[    1.302523] GHES: HEST is not enabled!
[    1.302641] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.323097] 00:07: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
[    1.324487] Linux agpgart interface v0.103
[    1.325786] brd: module loaded
[    1.326464] loop: module loaded
[    1.326843] libphy: Fixed MDIO Bus: probed
[    1.326924] tun: Universal TUN/TAP device driver, 1.6
[    1.326926] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.326993] PPP generic driver version 2.4.2
[    1.327032] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.327037] ehci-pci: EHCI PCI platform driver
[    1.327231] ehci-pci 0000:00:12.2: EHCI Host Controller
[    1.327237] ehci-pci 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.327241] ehci-pci 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.327252] ehci-pci 0000:00:12.2: debug port 1
[    1.327307] ehci-pci 0000:00:12.2: irq 17, io mem 0xfe02c000
[    1.339200] ehci-pci 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.339254] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.339256] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.339258] usb usb1: Product: EHCI Host Controller
[    1.339260] usb usb1: Manufacturer: Linux 3.13.0-24-generic ehci_hcd
[    1.339261] usb usb1: SerialNumber: 0000:00:12.2
[    1.339417] hub 1-0:1.0: USB hub found
[    1.339423] hub 1-0:1.0: 6 ports detected
[    1.339694] ehci-pci 0000:00:13.2: EHCI Host Controller
[    1.339699] ehci-pci 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.339703] ehci-pci 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.339714] ehci-pci 0000:00:13.2: debug port 1
[    1.339763] ehci-pci 0000:00:13.2: irq 19, io mem 0xfe029000
[    1.351199] ehci-pci 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.351258] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.351261] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.351262] usb usb2: Product: EHCI Host Controller
[    1.351264] usb usb2: Manufacturer: Linux 3.13.0-24-generic ehci_hcd
[    1.351265] usb usb2: SerialNumber: 0000:00:13.2
[    1.351405] hub 2-0:1.0: USB hub found
[    1.351411] hub 2-0:1.0: 6 ports detected
[    1.351530] ehci-platform: EHCI generic platform driver
[    1.351542] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.351543] ohci-pci: OHCI PCI platform driver
[    1.351690] ohci-pci 0000:00:12.0: OHCI PCI host controller
[    1.351695] ohci-pci 0000:00:12.0: new USB bus registered, assigned bus number 3
[    1.351728] ohci-pci 0000:00:12.0: irq 16, io mem 0xfe02e000
[    1.411205] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    1.411209] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.411211] usb usb3: Product: OHCI PCI host controller
[    1.411212] usb usb3: Manufacturer: Linux 3.13.0-24-generic ohci_hcd
[    1.411214] usb usb3: SerialNumber: 0000:00:12.0
[    1.411367] hub 3-0:1.0: USB hub found
[    1.411377] hub 3-0:1.0: 3 ports detected
[    1.411599] ohci-pci 0000:00:12.1: OHCI PCI host controller
[    1.411604] ohci-pci 0000:00:12.1: new USB bus registered, assigned bus number 4
[    1.411621] ohci-pci 0000:00:12.1: irq 16, io mem 0xfe02d000
[    1.471196] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    1.471199] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.471201] usb usb4: Product: OHCI PCI host controller
[    1.471203] usb usb4: Manufacturer: Linux 3.13.0-24-generic ohci_hcd
[    1.471204] usb usb4: SerialNumber: 0000:00:12.1
[    1.471390] hub 4-0:1.0: USB hub found
[    1.471403] hub 4-0:1.0: 3 ports detected
[    1.471629] ohci-pci 0000:00:13.0: OHCI PCI host controller
[    1.471634] ohci-pci 0000:00:13.0: new USB bus registered, assigned bus number 5
[    1.471669] ohci-pci 0000:00:13.0: irq 18, io mem 0xfe02b000
[    1.531189] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    1.531193] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.531195] usb usb5: Product: OHCI PCI host controller
[    1.531196] usb usb5: Manufacturer: Linux 3.13.0-24-generic ohci_hcd
[    1.531198] usb usb5: SerialNumber: 0000:00:13.0
[    1.531355] hub 5-0:1.0: USB hub found
[    1.531365] hub 5-0:1.0: 3 ports detected
[    1.531586] ohci-pci 0000:00:13.1: OHCI PCI host controller
[    1.531592] ohci-pci 0000:00:13.1: new USB bus registered, assigned bus number 6
[    1.531608] ohci-pci 0000:00:13.1: irq 18, io mem 0xfe02a000
[    1.591173] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
[    1.591177] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.591179] usb usb6: Product: OHCI PCI host controller
[    1.591180] usb usb6: Manufacturer: Linux 3.13.0-24-generic ohci_hcd
[    1.591182] usb usb6: SerialNumber: 0000:00:13.1
[    1.591336] hub 6-0:1.0: USB hub found
[    1.591347] hub 6-0:1.0: 3 ports detected
[    1.591578] ohci-pci 0000:00:14.5: OHCI PCI host controller
[    1.591583] ohci-pci 0000:00:14.5: new USB bus registered, assigned bus number 7
[    1.591598] ohci-pci 0000:00:14.5: irq 18, io mem 0xfe028000
[    1.651163] usb usb7: New USB device found, idVendor=1d6b, idProduct=0001
[    1.651166] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.651168] usb usb7: Product: OHCI PCI host controller
[    1.651170] usb usb7: Manufacturer: Linux 3.13.0-24-generic ohci_hcd
[    1.651171] usb usb7: SerialNumber: 0000:00:14.5
[    1.651326] hub 7-0:1.0: USB hub found
[    1.651336] hub 7-0:1.0: 2 ports detected
[    1.651419] ohci-platform: OHCI generic platform driver
[    1.651430] uhci_hcd: USB Universal Host Controller Interface driver
[    1.651487] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    1.685635] i8042: Failed to disable AUX port, but continuing anyway... Is this a SiS?
[    1.685636] i8042: If AUX port is really absent please use the 'i8042.noaux' option
[    1.935196] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.935365] mousedev: PS/2 mouse device common for all mice
[    1.935498] rtc_cmos 00:04: RTC can wake from S4
[    1.935608] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    1.935641] rtc_cmos 00:04: alarms up to one month, 242 bytes nvram, hpet irqs
[    1.935700] device-mapper: uevent: version 1.0.3
[    1.935759] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
[    1.935765] ledtrig-cpu: registered to indicate activity on CPUs
[    1.935862] TCP: cubic registered
[    1.935944] NET: Registered protocol family 10
[    1.936106] NET: Registered protocol family 17
[    1.936114] Key type dns_resolver registered
[    1.936435] Loading compiled-in X.509 certificates
[    1.937479] Loaded X.509 cert 'Magrathea: Glacier signing key: 00a5a65759de474bc5c43120880c1b94a539f431'
[    1.937491] registered taskstats version 1
[    1.940083] Key type trusted registered
[    1.942282] Key type encrypted registered
[    1.944501] AppArmor: AppArmor sha1 policy hashing enabled
[    1.944506] IMA: No TPM chip found, activating TPM-bypass!
[    1.944727] regulator-dummy: disabling
[    1.944793]   Magic number: 10:754:795
[    1.944889] rtc_cmos 00:04: setting system clock to 2014-04-23 17:46:39 UTC (1398275199)
[    1.944988] acpi-cpufreq: overriding BIOS provided _PSD data
[    1.945100] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.945101] EDD information not available.
[    1.945125] PM: Hibernation image not present or could not be loaded.
[    1.946557] Freeing unused kernel memory: 1332K (ffffffff81d1e000 - ffffffff81e6b000)
[    1.946560] Write protecting the kernel read-only data: 12288k
[    1.949008] Freeing unused kernel memory: 844K (ffff88000172d000 - ffff880001800000)
[    1.950967] Freeing unused kernel memory: 708K (ffff880001b4f000 - ffff880001c00000)
[    1.968463] systemd-udevd[114]: starting version 204
[    1.978642] wmi: Mapper loaded
[    1.984902] [drm] Initialized drm 1.1.0 20060810
[    1.987878] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.987893] r8169 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
[    1.988103] r8169 0000:02:00.0: irq 42 for MSI/MSI-X
[    1.988270] r8169 0000:02:00.0 eth0: RTL8168c/8111c at 0xffffc90000638000, 00:24:1d:d8:63:09, XID 1c4000c0 IRQ 42
[    1.988273] r8169 0000:02:00.0 eth0: jumbo features [frames: 6128 bytes, tx checksumming: ko]
[    1.994073] ahci 0000:00:11.0: version 3.0
[    1.994331] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
[    1.994335] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc 
[    1.997201] scsi0 : ahci
[    1.997792] scsi1 : ahci
[    1.997882] scsi2 : ahci
[    1.997940] scsi3 : ahci
[    1.997994] scsi4 : ahci
[    1.998050] scsi5 : ahci
[    1.998094] ata1: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f100 irq 22
[    1.998097] ata2: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f180 irq 22
[    1.998099] ata3: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f200 irq 22
[    1.998102] ata4: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f280 irq 22
[    1.998105] ata5: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f300 irq 22
[    1.998107] ata6: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f380 irq 22
[    1.999096] scsi6 : pata_atiixp
[    1.999177] scsi7 : pata_atiixp
[    1.999230] ata7: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfa00 irq 14
[    1.999232] ata8: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfa08 irq 15
[    2.012502] [drm] radeon kernel modesetting enabled.
[    2.012578] checking generic (d0000000 5b0000) vs hw (d0000000 10000000)
[    2.012580] fb: conflicting fb hw usage radeondrmfb vs VESA VGA - removing generic driver
[    2.012600] Console: switching to colour dummy device 80x25
[    2.012913] [drm] initializing kernel modesetting (RV710 0x1002:0x954F 0x1043:0x02A8).
[    2.012928] [drm] register mmio base: 0xFDFE0000
[    2.012929] [drm] register mmio size: 65536
[    2.013306] ATOM BIOS: 
[    2.013339] radeon 0000:01:00.0: VRAM: 512M 0x0000000000000000 - 0x000000001FFFFFFF (512M used)
[    2.013342] radeon 0000:01:00.0: GTT: 1024M 0x0000000020000000 - 0x000000005FFFFFFF
[    2.013344] [drm] Detected VRAM RAM=512M, BAR=256M
[    2.013345] [drm] RAM width 64bits DDR
[    2.013533] [TTM] Zone  kernel: Available graphics memory: 2023194 kiB
[    2.013537] [TTM] Initializing pool allocator
[    2.013542] [TTM] Initializing DMA pool allocator
[    2.013564] [drm] radeon: 512M of VRAM memory ready
[    2.013565] [drm] radeon: 1024M of GTT memory ready.
[    2.013581] [drm] Loading RV710 Microcode
[    2.013802] [drm] GART: num cpu pages 262144, num gpu pages 262144
[    2.015692] [drm] enabling PCIE gen 2 link speeds, disable with radeon.pcie_gen2=0
[    2.022388] [drm] PCIE GART of 1024M enabled (table at 0x000000000025D000).
[    2.022424] radeon 0000:01:00.0: WB enabled
[    2.022428] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000020000c00 and cpu addr 0xffff8800cf064c00
[    2.022430] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000020000c0c and cpu addr 0xffff8800cf064c0c
[    2.022848] radeon 0000:01:00.0: fence driver on ring 5 use gpu addr 0x000000000005c598 and cpu addr 0xffffc9001141c598
[    2.022850] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    2.022851] [drm] Driver supports precise vblank timestamp query.
[    2.022874] radeon 0000:01:00.0: irq 43 for MSI/MSI-X
[    2.022888] radeon 0000:01:00.0: radeon: using MSI.
[    2.022911] [drm] radeon: irq initialized.
[    2.055133] firewire_ohci 0000:03:0e.0: added OHCI v1.10 device as card 0, 4 IR + 8 IT contexts, quirks 0x2
[    2.068816] [drm] ring test on 0 succeeded in 1 usecs
[    2.068872] [drm] ring test on 3 succeeded in 1 usecs
[    2.243066] tsc: Refined TSC clocksource calibration: 2611.801 MHz
[    2.263441] [drm] ring test on 5 succeeded in 1 usecs
[    2.263447] [drm] UVD initialized successfully.
[    2.263565] [drm] Enabling audio 0 support
[    2.263585] [drm] ib test on ring 0 succeeded in 0 usecs
[    2.263601] [drm] ib test on ring 3 succeeded in 0 usecs
[    2.323078] ata6: SATA link down (SStatus 0 SControl 300)
[    2.323115] ata4: SATA link down (SStatus 0 SControl 300)
[    2.323154] ata5: SATA link down (SStatus 0 SControl 300)
[    2.422735] [drm] ib test on ring 5 succeeded
[    2.423030] [drm] Radeon Display Connectors
[    2.423031] [drm] Connector 0:
[    2.423033] [drm]   VGA-1
[    2.423035] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[    2.423036] [drm]   Encoders:
[    2.423037] [drm]     CRT2: INTERNAL_KLDSCP_DAC2
[    2.423038] [drm] Connector 1:
[    2.423039] [drm]   HDMI-A-1
[    2.423040] [drm]   HPD1
[    2.423041] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
[    2.423042] [drm]   Encoders:
[    2.423043] [drm]     DFP1: INTERNAL_UNIPHY
[    2.423044] [drm] Connector 2:
[    2.423045] [drm]   DVI-I-1
[    2.423046] [drm]   HPD4
[    2.423048] [drm]   DDC: 0x7f10 0x7f10 0x7f14 0x7f14 0x7f18 0x7f18 0x7f1c 0x7f1c
[    2.423049] [drm]   Encoders:
[    2.423050] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[    2.423051] [drm]     DFP2: INTERNAL_UNIPHY2
[    2.423073] [drm] Internal thermal controller without fan control
[    2.424803] [drm] radeon: dpm initialized
[    2.491014] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.495018] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.496530] ata3.00: ATAPI: TSSTcorp CDDVDW SH-S223C, SB00, max UDMA/100
[    2.496686] ata1.00: ATA-8: SAMSUNG HD103SJ, 1AJ100E4, max UDMA/133
[    2.496688] ata1.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    2.498418] ata3.00: configured for UDMA/100
[    2.499046] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.502442] ata1.00: configured for UDMA/133
[    2.502660] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HD103SJ  1AJ1 PQ: 0 ANSI: 5
[    2.502838] sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    2.502872] sd 0:0:0:0: [sda] Write Protect is off
[    2.502875] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.502878] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.502890] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.504748] ata2.00: ATA-8: SAMSUNG HD103SJ, 1AJ100E4, max UDMA/133
[    2.504751] ata2.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    2.510492] ata2.00: configured for UDMA/133
[    2.510710] scsi 1:0:0:0: Direct-Access     ATA      SAMSUNG HD103SJ  1AJ1 PQ: 0 ANSI: 5
[    2.510861] sd 1:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    2.510875] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    2.510953] sd 1:0:0:0: [sdb] Write Protect is off
[    2.510972] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.511009] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.512235] scsi 2:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S223C  SB00 PQ: 0 ANSI: 5
[    2.512428] [drm] fb mappable at 0xD045E000
[    2.512432] [drm] vram apper at 0xD0000000
[    2.512433] [drm] size 8294400
[    2.512434] [drm] fb depth is 24
[    2.512435] [drm]    pitch is 7680
[    2.512510] fbcon: radeondrmfb (fb0) is primary device
[    2.513427] Console: switching to colour frame buffer device 240x67
[    2.516184] sr0: scsi3-mmc drive: 52x/52x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.516186] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.516356] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    2.516425] sr 2:0:0:0: Attached scsi generic sg2 type 5
[    2.520152] radeon 0000:01:00.0: fb0: radeondrmfb frame buffer device
[    2.520154] radeon 0000:01:00.0: registered panic notifier
[    2.520159] [drm] Initialized radeon 2.36.0 20080528 for 0000:01:00.0 on minor 0
[    2.526181]  sda: sda1 sda2 sda3
[    2.526681] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.550648]  sdb: sdb1 sdb2 sdb3
[    2.551145] sd 1:0:0:0: [sdb] Attached SCSI disk
[    2.567098] firewire_core 0000:03:0e.0: created device fw0: GUID 00e108650000241d, S400
[    2.571031] usb 6-2: new full-speed USB device number 2 using ohci-pci
[    2.685397] md: bind<sdb1>
[    2.687479] md: bind<sdb2>
[    2.722980] md: bind<sda2>
[    2.726666] md: raid1 personality registered for level 1
[    2.726974] md/raid1:md127: active with 2 out of 2 mirrors
[    2.726994] md127: detected capacity change from 0 to 1003356160
[    2.728991]  md127: unknown partition table
[    2.729145] md: bind<sda1>
[    2.730879] md/raid1:md126: active with 2 out of 2 mirrors
[    2.730902] md126: detected capacity change from 0 to 995999023104
[    2.738099] usb 6-2: New USB device found, idVendor=04a9, idProduct=2204
[    2.738104] usb 6-2: New USB device strings: Mfr=0, Product=3, SerialNumber=0
[    2.738106] usb 6-2: Product: CanoScan FB630U
[    2.740233]  md126: unknown partition table
[    2.874954] usb 5-1: new low-speed USB device number 2 using ohci-pci
[    3.044084] usb 5-1: New USB device found, idVendor=046d, idProduct=c069
[    3.044088] usb 5-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    3.044090] usb 5-1: Product: USB Laser Mouse
[    3.044092] usb 5-1: Manufacturer: Logitech
[    3.052387] hidraw: raw HID events driver (C) Jiri Kosina
[    3.059236] usbcore: registered new interface driver usbhid
[    3.059239] usbhid: USB HID core driver
[    3.061083] input: Logitech USB Laser Mouse as /devices/pci0000:00/0000:00:13.0/usb5/5-1/5-1:1.0/input/input3
[    3.061236] hid-generic 0003:046D:C069.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB Laser Mouse] on usb-0000:00:13.0-1/input0
[    3.182903] usb 5-2: new low-speed USB device number 3 using ohci-pci
[    3.243042] Switched to clocksource tsc
[    3.353052] usb 5-2: New USB device found, idVendor=046a, idProduct=0023
[    3.353056] usb 5-2: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    3.377205] input: HID 046a:0023 as /devices/pci0000:00/0000:00:13.0/usb5/5-2/5-2:1.0/input/input4
[    3.377309] cherry 0003:046A:0023.0002: input,hidraw1: USB HID v1.11 Keyboard [HID 046a:0023] on usb-0000:00:13.0-2/input0
[    3.382155] input: HID 046a:0023 as /devices/pci0000:00/0000:00:13.0/usb5/5-2/5-2:1.1/input/input5
[    3.382272] cherry 0003:046A:0023.0003: input,hidraw2: USB HID v1.11 Device [HID 046a:0023] on usb-0000:00:13.0-2/input1
[   32.897848] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[   32.897854] ata3.00: failed command: IDENTIFY PACKET DEVICE
[   32.897859] ata3.00: cmd a1/00:01:00:00:00/00:00:00:00:00/00 tag 0 pio 512 in
[   32.897859]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[   32.897861] ata3.00: status: { DRDY }
[   32.897865] ata3: hard resetting link
[   33.389760] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   33.393108] ata3.00: configured for UDMA/100
[   33.394541] ata3: EH complete
[   51.714222] random: nonblocking pool is initialized
[   63.681647] md: linear personality registered for level -1
[   63.684674] md: multipath personality registered for level -4
[   63.687691] md: raid0 personality registered for level 0
[   63.760566] raid6: sse2x1    3714 MB/s
[   63.828547] raid6: sse2x2    5799 MB/s
[   63.896531] raid6: sse2x4    6930 MB/s
[   63.896533] raid6: using algorithm sse2x4 (6930 MB/s)
[   63.896535] raid6: using intx1 recovery algorithm
[   63.897981] xor: measuring software checksum speed
[   63.932578] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[   63.932584] ata3.00: failed command: IDENTIFY PACKET DEVICE
[   63.932589] ata3.00: cmd a1/00:01:00:00:00/00:00:00:00:00/00 tag 0 pio 512 in
[   63.932589]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[   63.932591] ata3.00: status: { DRDY }
[   63.932595] ata3: hard resetting link
[   63.936527]    prefetch64-sse: 10718.000 MB/sec
[   63.976520]    generic_sse: 10153.000 MB/sec
[   63.976521] xor: using function: prefetch64-sse (10718.000 MB/sec)
[   63.977769] async_tx: api initialized (async)
[   63.985419] md: raid6 personality registered for level 6
[   63.985423] md: raid5 personality registered for level 5
[   63.985425] md: raid4 personality registered for level 4
[   63.992428] md: raid10 personality registered for level 10
[   64.424483] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   64.427848] ata3.00: configured for UDMA/100
[   64.429330] ata3: EH complete
[   74.274429] bio: create slab <bio-1> at 1
[   74.470560] bio: create slab <bio-1> at 1
[   79.586530] EXT4-fs (dm-0): INFO: recovery required on readonly filesystem
[   79.586534] EXT4-fs (dm-0): write access will be enabled during recovery
[   81.815540] EXT4-fs (dm-0): orphan cleanup on readonly fs
[   81.815619] EXT4-fs (dm-0): 1 orphan inode deleted
[   81.815621] EXT4-fs (dm-0): recovery complete
[   81.991359] EXT4-fs (dm-0): mounted filesystem with ordered data mode. Opts: (null)
[   86.552719] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   86.601663] systemd-udevd[421]: starting version 204
[   86.699609] lp: driver loaded but no devices found
[   86.706832] ppdev: user-space parallel port driver
[   86.710027] parport_pc 00:08: reported by Plug and Play ACPI
[   86.710083] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   86.798499] ACPI Warning: 0x0000000000000b00-0x0000000000000b07 SystemIO conflicts with Region \SOR1 1 (20131115/utaddress-251)
[   86.798507] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   86.799878] sp5100_tco: SP5100/SB800 TCO WatchDog Timer Driver v0.05
[   86.799940] sp5100_tco: PCI Revision ID: 0x3c
[   86.799957] sp5100_tco: failed to find MMIO address, giving up.
[   86.804812] lp0: using parport0 (interrupt-driven).
[   86.813278] MCE: In-kernel MCE decoding enabled.
[   86.815741] EDAC MC: Ver: 3.0.0
[   86.817853] AMD64 EDAC driver v3.4.0
[   86.817936] EDAC amd64: DRAM ECC disabled.
[   86.817943] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   86.817943]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   86.817943]  (Note that use of the override may cause unknown side effects.)
[   86.838534] hda_intel: position_fix set to 1 for device 1458:a022
[   86.844908] kvm: Nested Virtualization enabled
[   86.844913] kvm: Nested Paging enabled
[   86.845689] WARNING! power/level is deprecated; use power/control instead
[   86.850205] hda-intel 0000:00:14.2: Enable sync_write for stable communication
[   86.861718] SKU: Nid=0x0 sku_cfg=0x0000e601
[   86.861722] SKU: port_connectivity=0x0
[   86.861723] SKU: enable_pcbeep=0x1
[   86.861734] SKU: check_sum=0x00000000
[   86.861735] SKU: customization=0x00000000
[   86.861736] SKU: external_amp=0x0
[   86.861737] SKU: platform_type=0x0
[   86.861737] SKU: swap=0x0
[   86.861738] SKU: override=0x1
[   86.862217] autoconfig: line_outs=4 (0x14/0x15/0x16/0x17/0x0) type:line
[   86.862218]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   86.862219]    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[   86.862220]    mono: mono_out=0x0
[   86.862222]    dig-out=0x1e/0x0
[   86.862222]    inputs:
[   86.862233]      Rear Mic=0x18
[   86.862234]      Front Mic=0x19
[   86.862235]      Line=0x1a
[   86.862237]      CD=0x1c
[   86.862237]    dig-in=0x1f
[   86.862239] realtek: Enabling init ASM_ID=0xe601 CODEC_ID=10ec0888
[   86.875620] input: HDA ATI SB Front Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input13
[   86.875865] input: HDA ATI SB Line Out Side as /devices/pci0000:00/0000:00:14.2/sound/card0/input12
[   86.875968] input: HDA ATI SB Line Out CLFE as /devices/pci0000:00/0000:00:14.2/sound/card0/input11
[   86.876035] input: HDA ATI SB Line Out Surround as /devices/pci0000:00/0000:00:14.2/sound/card0/input10
[   86.877352] input: HDA ATI SB Line Out Front as /devices/pci0000:00/0000:00:14.2/sound/card0/input9
[   86.877431] input: HDA ATI SB Line as /devices/pci0000:00/0000:00:14.2/sound/card0/input8
[   86.878110] input: HDA ATI SB Front Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input7
[   86.878188] input: HDA ATI SB Rear Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input6
[   86.878954] hda-intel 0000:01:00.1: Handle VGA-switcheroo audio client
[   86.878957] hda-intel 0000:01:00.1: Using LPIB position fix
[   86.879000] snd_hda_intel 0000:01:00.1: irq 44 for MSI/MSI-X
[   86.882362] hda-intel 0000:01:00.1: Enable sync_write for stable communication
[   86.894415] HDMI ATI/AMD: no speaker allocation for ELD
[   86.895109] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input14
[   87.126582] type=1400 audit(1398275284.691:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=497 comm="apparmor_parser"
[   87.126590] type=1400 audit(1398275284.691:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=497 comm="apparmor_parser"
[   87.126595] type=1400 audit(1398275284.691:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=497 comm="apparmor_parser"
[   87.126610] type=1400 audit(1398275284.691:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=506 comm="apparmor_parser"
[   87.126619] type=1400 audit(1398275284.691:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=506 comm="apparmor_parser"
[   87.126624] type=1400 audit(1398275284.691:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=506 comm="apparmor_parser"
[   87.127060] type=1400 audit(1398275284.691:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=497 comm="apparmor_parser"
[   87.127066] type=1400 audit(1398275284.691:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=497 comm="apparmor_parser"
[   87.127111] type=1400 audit(1398275284.691:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=506 comm="apparmor_parser"
[   87.127115] type=1400 audit(1398275284.691:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=506 comm="apparmor_parser"
[   88.378137] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
[   88.573675] EXT4-fs (md127): mounted filesystem with ordered data mode. Opts: (null)
[   88.673014] init: failsafe main process (792) killed by TERM signal
[   88.946052] Bluetooth: Core ver 2.17
[   88.946081] NET: Registered protocol family 31
[   88.946083] Bluetooth: HCI device and connection manager initialized
[   88.946092] Bluetooth: HCI socket layer initialized
[   88.946094] Bluetooth: L2CAP socket layer initialized
[   88.946098] Bluetooth: SCO socket layer initialized
[   88.949765] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   88.949769] Bluetooth: BNEP filters: protocol multicast
[   88.949778] Bluetooth: BNEP socket layer initialized
[   88.950840] Bluetooth: RFCOMM TTY layer initialized
[   88.950853] Bluetooth: RFCOMM socket layer initialized
[   88.950863] Bluetooth: RFCOMM ver 1.11
[   89.095308] init: cups main process (895) killed by HUP signal
[   89.095321] init: cups main process ended, respawning
[   89.677469] r8169 0000:02:00.0 eth0: link down
[   89.677495] r8169 0000:02:00.0 eth0: link down
[   89.677513] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   89.677789] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   92.036345] r8169 0000:02:00.0 eth0: link up
[   92.036355] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  116.911504] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[  116.911526] ata3.00: failed command: IDENTIFY PACKET DEVICE
[  116.911531] ata3.00: cmd a1/00:01:00:00:00/00:00:00:00:00/00 tag 0 pio 512 in
[  116.911531]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[  116.911534] ata3.00: status: { DRDY }
[  116.911537] ata3: hard resetting link
[  117.403434] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[  117.407108] ata3.00: configured for UDMA/100
[  117.408848] ata3: EH complete
[  117.471777] Adding 3124636k swap on /dev/mapper/sdb3_crypt.  Priority:-1 extents:1 across:3124636k FS
[  117.576605] audit_printk_skb: 21 callbacks suppressed
[  117.576610] type=1400 audit(1398275315.151:19): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=1536 comm="apparmor_parser"
[  117.576617] type=1400 audit(1398275315.151:20): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1536 comm="apparmor_parser"
[  117.576622] type=1400 audit(1398275315.151:21): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1536 comm="apparmor_parser"
[  117.577087] type=1400 audit(1398275315.151:22): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1536 comm="apparmor_parser"
[  117.577091] type=1400 audit(1398275315.151:23): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1536 comm="apparmor_parser"
[  117.577203] type=1400 audit(1398275315.151:24): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=1535 comm="apparmor_parser"
[  117.577212] type=1400 audit(1398275315.151:25): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=1535 comm="apparmor_parser"
[  117.577339] type=1400 audit(1398275315.151:26): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1536 comm="apparmor_parser"
[  117.577508] type=1400 audit(1398275315.151:27): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="chromium" pid=1535 comm="apparmor_parser"
[  117.580615] type=1400 audit(1398275315.155:28): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/ntpd" pid=1541 comm="apparmor_parser"
[  119.134469] HDMI ATI/AMD: no speaker allocation for ELD
[  119.297709] init: plymouth-upstart-bridge main process ended, respawning
[  119.304667] init: plymouth-upstart-bridge main process (1872) terminated with status 1
[  119.304682] init: plymouth-upstart-bridge main process ended, respawning
[  119.431196] HDMI ATI/AMD: no speaker allocation for ELD
[  119.731161] HDMI ATI/AMD: no speaker allocation for ELD
[  120.031104] HDMI ATI/AMD: no speaker allocation for ELD
[  120.331083] HDMI ATI/AMD: no speaker allocation for ELD
[  120.631064] HDMI ATI/AMD: no speaker allocation for ELD
[  120.931036] HDMI ATI/AMD: no speaker allocation for ELD
[  121.230988] HDMI ATI/AMD: no speaker allocation for ELD
[  121.530955] HDMI ATI/AMD: no speaker allocation for ELD

```


Regards,
Jan

---

### Post by jab6 on 2014-04-23
I attached a bootchart to futher understand the problem. Its still not 100% clear to me. Is this an udev problem? ATA3/DVD Rom error look unreleated to me. Any ideas?

---

### Post by Sandgoose on 2014-04-23
I have a similar problem with slow booting in 14.04, didn't want to make a new thread

I have 14.04 installed on my SSD takes 1 minute 3 seconds from grub to get to the login screen almost the entire boot process is a black screen, the cool swirly loading screen displays for about 2 seconds right before the login screen is up. I thought this was maybe my SSD just being slow but I benchmarked it and it reported 80mb/s write on 14.04 after it had booted.

13.10 installed on an ancient 40gb usb hdd takes 48.71 seconds to boot (I expect this drive to be slow) and shows the cool spinny loading screen during most of it, that drive benchmarks around 38mb/s write.

I think 14.04 feels much slower due to the fact it sits on a black screen for so long but given the drive it is installed on it should in theory be loading much faster than the 13.10 install, right ?

---

### Post by jab6 on 2014-04-23
Hi Sandgoose,

can you install bootchart? Its pretty simple. Just run:
```

sudo apt-get install bootchart

```
Afterwards reboot and get the image from /var/log/bootchart/. If you attach it, this will allow me or others to see if we experience similar issues or if they are different. 


Jan

---

### Post by Jonathan_Traill on 2014-04-23
I'm also experiencing slow boots, though mine prefigured 14.04.  No solution as yet.  You can [view my efforts here]("http://ubuntuforums.org/showthread.php?t=2217967").
 
You need to provide a verbal boot log, so open a terminal and code [COLOR=#000000]dmesg > dmesg.txt.  It won't appear to do anything, but when you look in your file system you'll see a txt doc called dmsg, which will give you a break down of what the computer is doing at each stage during the boot and load process.  Copy'n'paste it here.  As it is going to be quite long, make sure you post it as a code extract (use the # icon in Advanced reply).

Would also be good to know what machines you are using and specifications.

EDIT - Salutes to jab6 for premepting me with the verbal log.[/COLOR]

---

### Post by Sandgoose on 2014-04-23
installed 13.10 to just to double check and the ssd boot time was 10 seconds, have to give me a few minutes need to reinstall the usb boot drive and reinstall.

---

### Post by Sandgoose on 2014-04-23
should I post the whole log, it's kind of long and contains magic numbers ? :)  (seriously what are they?)

the only delay I can see during the boot process is the following...

[    2.603163] Switched to clocksource tsc
[   53.786823] regulator-dummy: disabling

system has a dual core celeron 2955U @ 1.4ghz with 2gb of DDR3 ram, Intel HD graphics, not the best but it will do for what I need

[ATTACH=CONFIG]252433[/ATTACH][ATTACH]252436[/ATTACH]
made it a zip so it wouldn't get autoscaled

---

### Post by jab6 on 2014-04-24
Hi Sandgoose,

your problem looks different. Your system seems to hang in init, while mine hangs in udevadm. I attached my image again as zip (because of autoscaling).


Jan

---

### Post by Sandgoose on 2014-04-24
worth a mention, someone on a different forum for a similar hang  got around it by "disabling the pata modules" ? anyway the instructions were outdated and I'm not sure how or if it would do anything...

I did find my exact problem is already reported & confirmed on launchpad.net, although it is not assigned to anyone and not assigned to a specific package just to ubuntu in general as far as I can see.

think it is worth just sticking with 14 and putting up with horrible boot times (for now) while waiting for a fix? seems to run ok once it is up.

thanks

ps:not great at the tech stuff just curious if your boot problem the frozen thing around 32 seconds?

---

### Post by jab6 on 2014-04-25
Hi,

i dont know if its worth to wait for a fix if its unconfirmed. Can some month or even years. Can you post a link to your launchpad bug?

I did not find the exact same problem on launchpad. I will create an additional bug there since its annoying to wait one additional minute (!) at boot.


Jan

---

### Post by Sandgoose on 2014-04-25
yep, heres the link.. [https://bugs.launchpad.net/ubuntu/+bug/1308264](https://bugs.launchpad.net/ubuntu/+bug/1308264) a bug from beta 2 that seems to have made it live, pretty sure its the clocksource tsc thing, it is confirmed just unassigned, the bot also says it needs a package, I have no idea what package clocksource belongs to?

I also found some people got it working by downgrading to an older kernel, I have tried the custom kernel stuff in the past and its probably not for me ;)

---

### Post by jab6 on 2014-04-25
Cool. Thanks for that link. I added my bootchart to the bug. May be it will help sb. Looks like my problem is similar. May be we can escalate it to the Kernel Mailinglist. However, I do not yet understand it sufficiently to report it properly.

---

### Post by ocir30 on 2014-04-30
I have te same problem with my mac mini (late 2012, dual boot, Ubuntu 14.04). 

If somebody can help me, I report my bootchart...[IMG]https://dl.dropboxusercontent.com/u/3760328/tmp/jj-mini-trusty-20140430-1.png[/IMG]

---

### Post by pbhj2 on 2014-05-02
> **Sandgoose said:**
> I have no idea what package clocksource belongs to?

I'm not on my Kubuntu box at the mo to test but I would do something like: 

$ locate -e -i clocksource

to find files that mention it in their path and then do

$ apt-file search [nameOfFile]

to find the package that includes that file, the package name is listed on the far-left of the apt-file output. Then I'd use 

$ sudo aptitude update && sudo aptitude

to use aptitude package manager and have a look at the package in question to see if it could be removed.

HTH.

---

### Post by Sandgoose on 2014-05-02
just post this workaround here (from the launchpad page (Sebastián & "Zhi")) for anyone with the same problem 

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.12.17-trusty/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.12.17-trusty/)

downgrading to that v3.12.17-trusty solved the boot issue in my case although it is hardly ideal and as mentioned in the launchpad breaks a custom kernel patch and the automatic script I used to install it (touchpad :( )

@pbh2j2 I figured it was a kernel thing but wasn't 100% sure, locate does indeed list kernel header files, thanks

also I have seen a few people around other forums mentioning avoiding 14 due to the "nasty boot bug"

---

### Post by Sandgoose on 2014-07-15
for anyone still experiecing the problem it is fixed by adding the following

GRUB_CMDLINE_LINUX_DEFAULT="tpm_tis.force=1" and running sudo update-grub 

thanks goes to the guys on the bug reporting page linked above somewhere

---

### Post by beretta13 on 2014-07-23
I too have a much slower boot time than expected when loading lubuntu. Attached is my bootload chart.

---

### Post by jrbenito on 2014-08-21
I too was experiencing very slow boot with black screen on Ubuntu 14.04. Today I figured out what was taking time and it was ATA Id delaying udev and everything after it.

Here I show the bootchart before (-6) and after removing my CD-ROM drive (-7). I don't know why it is taking so long to recognize my CDROM, since I am not using it I found easier to simply disconnect it without looking ahead to solve the issue.

However, I am still having issue with splash screen. Notice how the plymouth initialize late after udev and together a lot of other things; since I boot from a SSD 840 EVO my boot is very fast, when splashscreen is ready to be shown it is already too late and login screen is going to take place. It is odd because I see black screen for a little while instead of splash screen. Therefore I tried to disconnect a HDD I have as secondary storage and Ubuntu almost instantaneous pop with splash screen and a notice about LVM drive missing (even do it is not used for system to run it is on fstab for mount on boot). This means that video and screen is ready to receive data on very early boot but plymouth is only putting splash screen in place after longer than an SSD boot process really need it.

Anyway, since my boot time is under 10 seconds now I can live without splash screen (but it is too ugly :D)

Best regards,
Benito

---

