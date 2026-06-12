---
title: "VERY slow boot.  Ubuntu 13.04."
date: 2013-08-25
forum: General Help
---

### Post by lobo78 on 2013-08-25
My specs (from hardinfo):
Processor		: 3x AMD Athlon(tm) II X3 435 Processor
Memory		: 4049MB
Operating System: Ubuntu 13.04

I'm also running Gnome 3.6.2 as my desktop environment.  Booting up takes a really long time.  I'm talking a few minutes to get to a point where I can interact with the computer.  Below is my dmesg (with deltas).  The line taking the longest seems to be the last one: "Netfilter messages via NETLINK v0.30.".  I've searched the web and these forums and can't find any information on this message.  Why is Ubuntu stuck at this point for 65 seconds?  How do I get Ubunto to boot faster?  Thanks!

```

[    0.000000 <    0.000000>] Initializing cgroup subsys cpuset
[    0.000000 <    0.000000>] Initializing cgroup subsys cpu
[    0.000000 <    0.000000>] Linux version 3.8.0-29-generic (buildd@roseapple) (gcc version 4.7.3 (Ubuntu/Linaro 4.7.3-1ubuntu1) ) #42-Ubuntu SMP Tue Aug 13 19:40:39 UTC 2013 (Ubuntu 3.8.0-29.42-generic 3.8.13.5)
[    0.000000 <    0.000000>] Command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-29-generic root=UUID=063d8c28-ed1a-4a51-8074-a8230b5e67cf ro quiet splash profile vt.handoff=7
[    0.000000 <    0.000000>] KERNEL supported cpus:
[    0.000000 <    0.000000>]   Intel GenuineIntel
[    0.000000 <    0.000000>]   AMD AuthenticAMD
[    0.000000 <    0.000000>]   Centaur CentaurHauls
[    0.000000 <    0.000000>] e820: BIOS-provided physical RAM map:
[    0.000000 <    0.000000>] BIOS-e820: [mem 0x0000000000000000-0x000000000009fbff] usable
[    0.000000 <    0.000000>] BIOS-e820: [mem 0x000000000009fc00-0x000000000009ffff] reserved
[    0.000000 <    0.000000>] BIOS-e820: [mem 0x00000000000e6000-0x00000000000fffff] reserved
[    0.000000 <    0.000000>] BIOS-e820: [mem 0x0000000000100000-0x00000000cff8ffff] usable
[    0.000000 <    0.000000>] BIOS-e820: [mem 0x00000000cff90000-0x00000000cff9dfff] ACPI data
[    0.000000 <    0.000000>] BIOS-e820: [mem 0x00000000cff9e000-0x00000000cffdffff] ACPI NVS
[    0.000000 <    0.000000>] BIOS-e820: [mem 0x00000000cffe0000-0x00000000cfffffff] reserved
[    0.000000 <    0.000000>] BIOS-e820: [mem 0x00000000fff00000-0x00000000ffffffff] reserved
[    0.000000 <    0.000000>] BIOS-e820: [mem 0x0000000100000000-0x000000012fffffff] usable
[    0.000000 <    0.000000>] NX (Execute Disable) protection: active
[    0.000000 <    0.000000>] SMBIOS 2.5 present.
[    0.000000 <    0.000000>] DMI: MICRO-STAR INTERNATIONAL CO.,LTD MS-7596/760GM -E51 (MS-7596), BIOS V1.6 05/14/2010
[    0.000000 <    0.000000>] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
[    0.000000 <    0.000000>] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000 <    0.000000>] No AGP bridge found
[    0.000000 <    0.000000>] e820: last_pfn = 0x130000 max_arch_pfn = 0x400000000
[    0.000000 <    0.000000>] MTRR default type: uncachable
[    0.000000 <    0.000000>] MTRR fixed ranges enabled:
[    0.000000 <    0.000000>]   00000-9FFFF write-back
[    0.000000 <    0.000000>]   A0000-EFFFF uncachable
[    0.000000 <    0.000000>]   F0000-FFFFF write-protect
[    0.000000 <    0.000000>] MTRR variable ranges enabled:
[    0.000000 <    0.000000>]   0 base 000000000000 mask FFFF80000000 write-back
[    0.000000 <    0.000000>]   1 base 000080000000 mask FFFFC0000000 write-back
[    0.000000 <    0.000000>]   2 base 0000C0000000 mask FFFFF0000000 write-back
[    0.000000 <    0.000000>]   3 disabled
[    0.000000 <    0.000000>]   4 disabled
[    0.000000 <    0.000000>]   5 disabled
[    0.000000 <    0.000000>]   6 disabled
[    0.000000 <    0.000000>]   7 disabled
[    0.000000 <    0.000000>] TOM2: 0000000130000000 aka 4864M
[    0.000000 <    0.000000>] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000 <    0.000000>] e820: update [mem 0xd0000000-0xffffffff] usable ==> reserved
[    0.000000 <    0.000000>] e820: last_pfn = 0xcff90 max_arch_pfn = 0x400000000
[    0.000000 <    0.000000>] found SMP MP-table at [mem 0x000ff780-0x000ff78f] mapped at [ffff8800000ff780]
[    0.000000 <    0.000000>] initial memory mapped: [mem 0x00000000-0x1fffffff]
[    0.000000 <    0.000000>] Base memory trampoline at [ffff880000099000] 99000 size 24576
[    0.000000 <    0.000000>] Using GB pages for direct mapping
[    0.000000 <    0.000000>] init_memory_mapping: [mem 0x00000000-0xcff8ffff]
[    0.000000 <    0.000000>]  [mem 0x00000000-0xbfffffff] page 1G
[    0.000000 <    0.000000>]  [mem 0xc0000000-0xcfdfffff] page 2M
[    0.000000 <    0.000000>]  [mem 0xcfe00000-0xcff8ffff] page 4k
[    0.000000 <    0.000000>] kernel direct mapping tables up to 0xcff8ffff @ [mem 0x1fffd000-0x1fffffff]
[    0.000000 <    0.000000>] init_memory_mapping: [mem 0x100000000-0x12fffffff]
[    0.000000 <    0.000000>]  [mem 0x100000000-0x12fffffff] page 2M
[    0.000000 <    0.000000>] kernel direct mapping tables up to 0x12fffffff @ [mem 0xcff8e000-0xcff8ffff]
[    0.000000 <    0.000000>] RAMDISK: [mem 0x360fe000-0x37076fff]
[    0.000000 <    0.000000>] ACPI: RSDP 00000000000faa30 00014 (v00 ACPIAM)
[    0.000000 <    0.000000>] ACPI: RSDT 00000000cff90000 00040 (v01 7596MS A7596100 20100514 MSFT 00000097)
[    0.000000 <    0.000000>] ACPI: FACP 00000000cff90200 00084 (v01 7596MS A7596100 20100514 MSFT 00000097)
[    0.000000 <    0.000000>] ACPI BIOS Bug: Warning: Optional FADT field Pm2ControlBlock has zero address or length: 0x0000000000000000/0x1 (20121018/tbfadt-598)
[    0.000000 <    0.000000>] ACPI: DSDT 00000000cff905d0 09DFE (v01  A7596 A7596100 00000100 INTL 20051117)
[    0.000000 <    0.000000>] ACPI: FACS 00000000cff9e000 00040
[    0.000000 <    0.000000>] ACPI: APIC 00000000cff90390 0007C (v01 7596MS A7596100 20100514 MSFT 00000097)
[    0.000000 <    0.000000>] ACPI: MCFG 00000000cff90410 0003C (v01 7596MS OEMMCFG  20100514 MSFT 00000097)
[    0.000000 <    0.000000>] ACPI: OEMB 00000000cff9e040 00072 (v01 7596MS A7596100 20100514 MSFT 00000097)
[    0.000000 <    0.000000>] ACPI: SRAT 00000000cff9a5d0 000D8 (v03 AMD    FAM_F_10 00000002 AMD  00000001)
[    0.000000 <    0.000000>] ACPI: HPET 00000000cff9a6b0 00038 (v01 7596MS OEMHPET  20100514 MSFT 00000097)
[    0.000000 <    0.000000>] ACPI: SSDT 00000000cff9a6f0 00672 (v01 A M I  POWERNOW 00000001 AMD  00000001)
[    0.000000 <    0.000000>] ACPI: Local APIC address 0xfee00000
[    0.000000 <    0.000000>] SRAT: PXM 0 -> APIC 0x00 -> Node 0
[    0.000000 <    0.000000>] SRAT: PXM 0 -> APIC 0x01 -> Node 0
[    0.000000 <    0.000000>] SRAT: PXM 0 -> APIC 0x02 -> Node 0
[    0.000000 <    0.000000>] SRAT: Node 0 PXM 0 [mem 0x00000000-0x0009ffff]
[    0.000000 <    0.000000>] SRAT: Node 0 PXM 0 [mem 0x00100000-0xcfffffff]
[    0.000000 <    0.000000>] SRAT: Node 0 PXM 0 [mem 0x100000000-0x12fffffff]
[    0.000000 <    0.000000>] NUMA: Node 0 [mem 0x00000000-0x0009ffff] + [mem 0x00100000-0xcfffffff] -> [mem 0x00000000-0xcfffffff]
[    0.000000 <    0.000000>] NUMA: Node 0 [mem 0x00000000-0xcfffffff] + [mem 0x100000000-0x12fffffff] -> [mem 0x00000000-0x12fffffff]
[    0.000000 <    0.000000>] Initmem setup node 0 [mem 0x00000000-0x12fffffff]
[    0.000000 <    0.000000>]   NODE_DATA [mem 0x12fffb000-0x12fffffff]
[    0.000000 <    0.000000>]  [ffffea0000000000-ffffea0004bfffff] PMD -> [ffff88012b600000-ffff88012f5fffff] on node 0
[    0.000000 <    0.000000>] Zone ranges:
[    0.000000 <    0.000000>]   DMA      [mem 0x00010000-0x00ffffff]
[    0.000000 <    0.000000>]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000 <    0.000000>]   Normal   [mem 0x100000000-0x12fffffff]
[    0.000000 <    0.000000>] Movable zone start for each node
[    0.000000 <    0.000000>] Early memory node ranges
[    0.000000 <    0.000000>]   node   0: [mem 0x00010000-0x0009efff]
[    0.000000 <    0.000000>]   node   0: [mem 0x00100000-0xcff8ffff]
[    0.000000 <    0.000000>]   node   0: [mem 0x100000000-0x12fffffff]
[    0.000000 <    0.000000>] On node 0 totalpages: 1048351
[    0.000000 <    0.000000>]   DMA zone: 64 pages used for memmap
[    0.000000 <    0.000000>]   DMA zone: 6 pages reserved
[    0.000000 <    0.000000>]   DMA zone: 3913 pages, LIFO batch:0
[    0.000000 <    0.000000>]   DMA32 zone: 13247 pages used for memmap
[    0.000000 <    0.000000>]   DMA32 zone: 834513 pages, LIFO batch:31
[    0.000000 <    0.000000>]   Normal zone: 3072 pages used for memmap
[    0.000000 <    0.000000>]   Normal zone: 193536 pages, LIFO batch:31
[    0.000000 <    0.000000>] ACPI: PM-Timer IO Port: 0x808
[    0.000000 <    0.000000>] ACPI: Local APIC address 0xfee00000
[    0.000000 <    0.000000>] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000 <    0.000000>] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000 <    0.000000>] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000 <    0.000000>] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000 <    0.000000>] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x84] disabled)
[    0.000000 <    0.000000>] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x85] disabled)
[    0.000000 <    0.000000>] ACPI: IOAPIC (id[0x03] address[0xfec00000] gsi_base[0])
[    0.000000 <    0.000000>] IOAPIC[0]: apic_id 3, version 33, address 0xfec00000, GSI 0-23
[    0.000000 <    0.000000>] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000 <    0.000000>] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000 <    0.000000>] ACPI: IRQ0 used by override.
[    0.000000 <    0.000000>] ACPI: IRQ2 used by override.
[    0.000000 <    0.000000>] ACPI: IRQ9 used by override.
[    0.000000 <    0.000000>] Using ACPI (MADT) for SMP configuration information
[    0.000000 <    0.000000>] ACPI: HPET id: 0x8300 base: 0xfed00000
[    0.000000 <    0.000000>] smpboot: Allowing 6 CPUs, 3 hotplug CPUs
[    0.000000 <    0.000000>] nr_irqs_gsi: 40
[    0.000000 <    0.000000>] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000 <    0.000000>] PM: Registered nosave memory: 00000000000a0000 - 00000000000e6000
[    0.000000 <    0.000000>] PM: Registered nosave memory: 00000000000e6000 - 0000000000100000
[    0.000000 <    0.000000>] PM: Registered nosave memory: 00000000cff90000 - 00000000cff9e000
[    0.000000 <    0.000000>] PM: Registered nosave memory: 00000000cff9e000 - 00000000cffe0000
[    0.000000 <    0.000000>] PM: Registered nosave memory: 00000000cffe0000 - 00000000d0000000
[    0.000000 <    0.000000>] PM: Registered nosave memory: 00000000d0000000 - 00000000fff00000
[    0.000000 <    0.000000>] PM: Registered nosave memory: 00000000fff00000 - 0000000100000000
[    0.000000 <    0.000000>] e820: [mem 0xd0000000-0xffefffff] available for PCI devices
[    0.000000 <    0.000000>] Booting paravirtualized kernel on bare hardware
[    0.000000 <    0.000000>] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:6 nr_node_ids:1
[    0.000000 <    0.000000>] PERCPU: Embedded 28 pages/cpu @ffff88012fc00000 s85056 r8192 d21440 u262144
[    0.000000 <    0.000000>] pcpu-alloc: s85056 r8192 d21440 u262144 alloc=1*2097152
[    0.000000 <    0.000000>] pcpu-alloc: [0] 0 1 2 3 4 5 - - 
[    0.000000 <    0.000000>] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1031962
[    0.000000 <    0.000000>] Policy zone: Normal
[    0.000000 <    0.000000>] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-29-generic root=UUID=063d8c28-ed1a-4a51-8074-a8230b5e67cf ro quiet splash profile vt.handoff=7
[    0.000000 <    0.000000>] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000 <    0.000000>] __ex_table already sorted, skipping sort
[    0.000000 <    0.000000>] Checking aperture...
[    0.000000 <    0.000000>] No AGP bridge found
[    0.000000 <    0.000000>] Node 0: aperture @ 1736000000 size 32 MB
[    0.000000 <    0.000000>] Aperture beyond 4GB. Ignoring.
[    0.000000 <    0.000000>] Your BIOS doesn't leave a aperture memory hole
[    0.000000 <    0.000000>] Please enable the IOMMU option in the BIOS setup
[    0.000000 <    0.000000>] This costs you 64 MB of RAM
[    0.000000 <    0.000000>] Mapping aperture over 65536 KB of RAM @ c4000000
[    0.000000 <    0.000000>] PM: Registered nosave memory: 00000000c4000000 - 00000000c8000000
[    0.000000 <    0.000000>] Memory: 3963940k/4980736k available (7013k kernel code, 787332k absent, 229464k reserved, 6229k data, 996k init)
[    0.000000 <    0.000000>] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=6, Nodes=1
[    0.000000 <    0.000000>] Hierarchical RCU implementation.
[    0.000000 <    0.000000>] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000 <    0.000000>] 	RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=6.
[    0.000000 <    0.000000>] NR_IRQS:16640 nr_irqs:728 16
[    0.000000 <    0.000000>] spurious 8259A interrupt: IRQ7.
[    0.000000 <    0.000000>] Console: colour dummy device 80x25
[    0.000000 <    0.000000>] console [tty0] enabled
[    0.000000 <    0.000000>] allocated 16777216 bytes of page_cgroup
[    0.000000 <    0.000000>] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000 <    0.000000>] hpet clockevent registered
[    0.004000 <    0.000000>] tsc: Fast TSC calibration using PIT
[    0.008000 <    0.004000>] tsc: Detected 2899.906 MHz processor
[    0.000003 <   -0.007997>] Calibrating delay loop (skipped), value calculated using timer frequency.. 5799.81 BogoMIPS (lpj=11599624)
[    0.000006 <    0.000003>] pid_max: default: 32768 minimum: 301
[    0.000027 <    0.000021>] Security Framework initialized
[    0.000037 <    0.000010>] AppArmor: AppArmor initialized
[    0.000038 <    0.000001>] Yama: becoming mindful.
[    0.000298 <    0.000260>] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.001388 <    0.001090>] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.001889 <    0.000501>] Mount-cache hash table entries: 256
[    0.002048 <    0.000159>] Initializing cgroup subsys cpuacct
[    0.002050 <    0.000002>] Initializing cgroup subsys memory
[    0.002056 <    0.000006>] Initializing cgroup subsys devices
[    0.002058 <    0.000002>] Initializing cgroup subsys freezer
[    0.002059 <    0.000001>] Initializing cgroup subsys blkio
[    0.002061 <    0.000002>] Initializing cgroup subsys perf_event
[    0.002063 <    0.000002>] Initializing cgroup subsys hugetlb
[    0.002083 <    0.000020>] tseg: 0000000000
[    0.002095 <    0.000012>] CPU: Physical Processor ID: 0
[    0.002096 <    0.000001>] CPU: Processor Core ID: 0
[    0.002097 <    0.000001>] mce: CPU supports 6 MCE banks
[    0.002102 <    0.000005>] LVT offset 0 assigned for vector 0xf9
[    0.002106 <    0.000004>] process: using AMD E400 aware idle routine
[    0.002109 <    0.000003>] Last level iTLB entries: 4KB 512, 2MB 16, 4MB 8
[    0.002109 <    0.000000>] Last level dTLB entries: 4KB 512, 2MB 128, 4MB 64
[    0.002109 <    0.000000>] tlb_flushall_shift: 4
[    0.002200 <    0.000091>] Freeing SMP alternatives: 24k freed
[    0.003505 <    0.001305>] ACPI: Core revision 20121018
[    0.012599 <    0.009094>] ftrace: allocating 26712 entries in 105 pages
[    0.022927 <    0.010328>] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.062608 <    0.039681>] smpboot: CPU0: AMD Athlon(tm) II X3 435 Processor (fam: 10, model: 05, stepping: 02)
[    0.166902 <    0.104294>] Performance Events: AMD PMU driver.
[    0.166905 <    0.000003>] ... version:                0
[    0.166906 <    0.000001>] ... bit width:              48
[    0.166907 <    0.000001>] ... generic registers:      4
[    0.166908 <    0.000001>] ... value mask:             0000ffffffffffff
[    0.166909 <    0.000001>] ... max period:             00007fffffffffff
[    0.166910 <    0.000001>] ... fixed-purpose events:   0
[    0.166911 <    0.000001>] ... event mask:             000000000000000f
[    0.167835 <    0.000924>] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.180993 <    0.013158>] process: System has AMD C1E enabled
[    0.181009 <    0.000016>] process: Switch to broadcast mode on CPU1
[    0.167903 <   -0.013106>] smpboot: Booting Node   0, Processors  #1 #2
[    0.194044 <    0.026141>] Brought up 3 CPUs
[    0.194047 <    0.000003>] smpboot: Total of 3 processors activated (17399.43 BogoMIPS)
[    0.194420 <    0.000373>] process: Switch to broadcast mode on CPU2
[    0.194527 <    0.000107>] process: Switch to broadcast mode on CPU0
[    0.194672 <    0.000145>] devtmpfs: initialized
[    0.195882 <    0.001210>] EVM: security.selinux
[    0.195883 <    0.000001>] EVM: security.SMACK64
[    0.195884 <    0.000001>] EVM: security.capability
[    0.195989 <    0.000105>] PM: Registering ACPI NVS region [mem 0xcff9e000-0xcffdffff] (270336 bytes)
[    0.196817 <    0.000828>] regulator-dummy: no parameters
[    0.196863 <    0.000046>] NET: Registered protocol family 16
[    0.196954 <    0.000091>] node 0 link 0: io port [1000, ffffff]
[    0.196956 <    0.000002>] TOM: 00000000d0000000 aka 3328M
[    0.196958 <    0.000002>] Fam 10h mmconf [mem 0xe0000000-0xefffffff]
[    0.196961 <    0.000003>] node 0 link 0: mmio [a0000, bffff]
[    0.196963 <    0.000002>] node 0 link 0: mmio [d0000000, dfffffff]
[    0.196965 <    0.000002>] node 0 link 0: mmio [e0000000, efffffff] ==> none
[    0.196966 <    0.000001>] node 0 link 0: mmio [f0000000, ffefffff]
[    0.196968 <    0.000002>] TOM2: 0000000130000000 aka 4864M
[    0.196969 <    0.000001>] bus: [bus 00-07] on node 0 link 0
[    0.196970 <    0.000001>] bus: 00 [io  0x0000-0xffff]
[    0.196972 <    0.000002>] bus: 00 [mem 0x000a0000-0x000bffff]
[    0.196973 <    0.000001>] bus: 00 [mem 0xd0000000-0xdfffffff]
[    0.196974 <    0.000001>] bus: 00 [mem 0xf0000000-0xffffffff]
[    0.196975 <    0.000001>] bus: 00 [mem 0x130000000-0xfcffffffff]
[    0.197063 <    0.000088>] ACPI: bus type pci registered
[    0.197109 <    0.000046>] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.197111 <    0.000002>] PCI: not using MMCONFIG
[    0.197113 <    0.000002>] PCI: Using configuration type 1 for base access
[    0.197114 <    0.000001>] PCI: Using configuration type 1 for extended access
[    0.197245 <    0.000131>] mtrr: your CPUs had inconsistent variable MTRR settings
[    0.197246 <    0.000001>] mtrr: probably your BIOS does not setup all CPUs.
[    0.197246 <    0.000000>] mtrr: corrected configuration.
[    0.197922 <    0.000676>] bio: create slab <bio-0> at 0
[    0.198003 <    0.000081>] ACPI: Added _OSI(Module Device)
[    0.198004 <    0.000001>] ACPI: Added _OSI(Processor Device)
[    0.198005 <    0.000001>] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.198006 <    0.000001>] ACPI: Added _OSI(Processor Aggregator Device)
[    0.198641 <    0.000635>] ACPI: EC: Detected MSI hardware, enabling workarounds.
[    0.198643 <    0.000002>] ACPI: EC: Look up EC in DSDT
[    0.199643 <    0.001000>] ACPI: Executed 4 blocks of module-level executable AML code
[    0.202238 <    0.002595>] ACPI: Interpreter enabled
[    0.202244 <    0.000006>] ACPI: (supports S0 S1 S4 S5)
[    0.202259 <    0.000015>] ACPI: Using IOAPIC for interrupt routing
[    0.202280 <    0.000021>] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.202905 <    0.000625>] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.216978 <    0.014073>] ACPI: No dock devices found.
[    0.216983 <    0.000005>] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.217067 <    0.000084>] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.217069 <    0.000002>] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.217315 <    0.000246>] PCI host bridge to bus 0000:00
[    0.217318 <    0.000003>] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.217320 <    0.000002>] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.217322 <    0.000002>] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.217323 <    0.000001>] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.217325 <    0.000002>] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000dffff]
[    0.217327 <    0.000002>] pci_bus 0000:00: root bus resource [mem 0xd0000000-0xdfffffff]
[    0.217328 <    0.000001>] pci_bus 0000:00: root bus resource [mem 0xf0000000-0xfebfffff]
[    0.217339 <    0.000011>] pci 0000:00:00.0: [1022:9600] type 00 class 0x060000
[    0.217387 <    0.000048>] pci 0000:00:02.0: [1022:9603] type 01 class 0x060400
[    0.217417 <    0.000030>] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.217442 <    0.000025>] pci 0000:00:05.0: [1022:9605] type 01 class 0x060400
[    0.217471 <    0.000029>] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
[    0.217503 <    0.000032>] pci 0000:00:11.0: [1002:4390] type 00 class 0x01018f
[    0.217524 <    0.000021>] pci 0000:00:11.0: reg 10: [io  0xc000-0xc007]
[    0.217533 <    0.000009>] pci 0000:00:11.0: reg 14: [io  0xb000-0xb003]
[    0.217543 <    0.000010>] pci 0000:00:11.0: reg 18: [io  0xa000-0xa007]
[    0.217552 <    0.000009>] pci 0000:00:11.0: reg 1c: [io  0x9000-0x9003]
[    0.217561 <    0.000009>] pci 0000:00:11.0: reg 20: [io  0x8000-0x800f]
[    0.217570 <    0.000009>] pci 0000:00:11.0: reg 24: [mem 0xfe9ffc00-0xfe9fffff]
[    0.217589 <    0.000019>] pci 0000:00:11.0: set SATA to AHCI mode
[    0.217644 <    0.000055>] pci 0000:00:12.0: [1002:4397] type 00 class 0x0c0310
[    0.217657 <    0.000013>] pci 0000:00:12.0: reg 10: [mem 0xfe9fe000-0xfe9fefff]
[    0.217719 <    0.000062>] pci 0000:00:12.1: [1002:4398] type 00 class 0x0c0310
[    0.217732 <    0.000013>] pci 0000:00:12.1: reg 10: [mem 0xfe9fd000-0xfe9fdfff]
[    0.217800 <    0.000068>] pci 0000:00:12.2: [1002:4396] type 00 class 0x0c0320
[    0.217818 <    0.000018>] pci 0000:00:12.2: reg 10: [mem 0xfe9ff800-0xfe9ff8ff]
[    0.217898 <    0.000080>] pci 0000:00:12.2: supports D1 D2
[    0.217900 <    0.000002>] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.217922 <    0.000022>] pci 0000:00:13.0: [1002:4397] type 00 class 0x0c0310
[    0.217934 <    0.000012>] pci 0000:00:13.0: reg 10: [mem 0xfe9fc000-0xfe9fcfff]
[    0.217996 <    0.000062>] pci 0000:00:13.1: [1002:4398] type 00 class 0x0c0310
[    0.218009 <    0.000013>] pci 0000:00:13.1: reg 10: [mem 0xfe9fb000-0xfe9fbfff]
[    0.218076 <    0.000067>] pci 0000:00:13.2: [1002:4396] type 00 class 0x0c0320
[    0.218094 <    0.000018>] pci 0000:00:13.2: reg 10: [mem 0xfe9ff400-0xfe9ff4ff]
[    0.218174 <    0.000080>] pci 0000:00:13.2: supports D1 D2
[    0.218176 <    0.000002>] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.218200 <    0.000024>] pci 0000:00:14.0: [1002:4385] type 00 class 0x0c0500
[    0.218296 <    0.000096>] pci 0000:00:14.1: [1002:439c] type 00 class 0x01018a
[    0.218312 <    0.000016>] pci 0000:00:14.1: reg 10: [io  0x0000-0x0007]
[    0.218321 <    0.000009>] pci 0000:00:14.1: reg 14: [io  0x0000-0x0003]
[    0.218330 <    0.000009>] pci 0000:00:14.1: reg 18: [io  0x0000-0x0007]
[    0.218339 <    0.000009>] pci 0000:00:14.1: reg 1c: [io  0x0000-0x0003]
[    0.218348 <    0.000009>] pci 0000:00:14.1: reg 20: [io  0xff00-0xff0f]
[    0.218403 <    0.000055>] pci 0000:00:14.2: [1002:4383] type 00 class 0x040300
[    0.218424 <    0.000021>] pci 0000:00:14.2: reg 10: [mem 0xfe9f4000-0xfe9f7fff 64bit]
[    0.218487 <    0.000063>] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.218502 <    0.000015>] pci 0000:00:14.3: [1002:439d] type 00 class 0x060100
[    0.218576 <    0.000074>] pci 0000:00:14.4: [1002:4384] type 01 class 0x060401
[    0.218616 <    0.000040>] pci 0000:00:14.5: [1002:4399] type 00 class 0x0c0310
[    0.218629 <    0.000013>] pci 0000:00:14.5: reg 10: [mem 0xfe9fa000-0xfe9fafff]
[    0.218693 <    0.000064>] pci 0000:00:18.0: [1022:1200] type 00 class 0x060000
[    0.218707 <    0.000014>] pci 0000:00:18.1: [1022:1201] type 00 class 0x060000
[    0.218718 <    0.000011>] pci 0000:00:18.2: [1022:1202] type 00 class 0x060000
[    0.218730 <    0.000012>] pci 0000:00:18.3: [1022:1203] type 00 class 0x060000
[    0.218743 <    0.000013>] pci 0000:00:18.4: [1022:1204] type 00 class 0x060000
[    0.218787 <    0.000044>] pci 0000:01:00.0: [1002:9442] type 00 class 0x030000
[    0.218799 <    0.000012>] pci 0000:01:00.0: reg 10: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.218808 <    0.000009>] pci 0000:01:00.0: reg 18: [mem 0xfeaf0000-0xfeafffff 64bit]
[    0.218814 <    0.000006>] pci 0000:01:00.0: reg 20: [io  0xd000-0xd0ff]
[    0.218825 <    0.000011>] pci 0000:01:00.0: reg 30: [mem 0xfeac0000-0xfeadffff pref]
[    0.218852 <    0.000027>] pci 0000:01:00.0: supports D1 D2
[    0.218869 <    0.000017>] pci 0000:01:00.1: [1002:aa30] type 00 class 0x040300
[    0.218881 <    0.000012>] pci 0000:01:00.1: reg 10: [mem 0xfeaec000-0xfeaeffff 64bit]
[    0.218930 <    0.000049>] pci 0000:01:00.1: supports D1 D2
[    0.225088 <    0.006158>] pci 0000:00:02.0: PCI bridge to [bus 01]
[    0.225091 <    0.000003>] pci 0000:00:02.0:   bridge window [io  0xd000-0xdfff]
[    0.225094 <    0.000003>] pci 0000:00:02.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.225097 <    0.000003>] pci 0000:00:02.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.225129 <    0.000032>] pci 0000:02:00.0: [10ec:8168] type 00 class 0x020000
[    0.225141 <    0.000012>] pci 0000:02:00.0: reg 10: [io  0xe800-0xe8ff]
[    0.225161 <    0.000020>] pci 0000:02:00.0: reg 18: [mem 0xfdfff000-0xfdffffff 64bit pref]
[    0.225174 <    0.000013>] pci 0000:02:00.0: reg 20: [mem 0xfdff8000-0xfdffbfff 64bit pref]
[    0.225182 <    0.000008>] pci 0000:02:00.0: reg 30: [mem 0xfebe0000-0xfebfffff pref]
[    0.225227 <    0.000045>] pci 0000:02:00.0: supports D1 D2
[    0.225229 <    0.000002>] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.233084 <    0.007855>] pci 0000:00:05.0: PCI bridge to [bus 02]
[    0.233088 <    0.000004>] pci 0000:00:05.0:   bridge window [io  0xe000-0xefff]
[    0.233090 <    0.000002>] pci 0000:00:05.0:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.233093 <    0.000003>] pci 0000:00:05.0:   bridge window [mem 0xfdf00000-0xfdffffff 64bit pref]
[    0.233150 <    0.000057>] pci 0000:00:14.4: PCI bridge to [bus 03] (subtractive decode)
[    0.233159 <    0.000009>] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.233161 <    0.000002>] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.233162 <    0.000001>] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.233164 <    0.000002>] pci 0000:00:14.4:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.233166 <    0.000002>] pci 0000:00:14.4:   bridge window [mem 0xd0000000-0xdfffffff] (subtractive decode)
[    0.233168 <    0.000002>] pci 0000:00:14.4:   bridge window [mem 0xf0000000-0xfebfffff] (subtractive decode)
[    0.233187 <    0.000019>] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
[    0.233212 <    0.000025>] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE5._PRT]
[    0.233250 <    0.000038>] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
[    0.233293 <    0.000043>]  pci0000:00: ACPI _OSC support notification failed, disabling PCIe ASPM
[    0.233295 <    0.000002>]  pci0000:00: Unable to request _OSC control (_OSC support mask: 0x08)
[    0.234075 <    0.000780>] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 7 10 *11 12 14 15)
[    0.234105 <    0.000030>] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 7 10 *11 12 14 15)
[    0.234133 <    0.000028>] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 7 *10 11 12 14 15)
[    0.234160 <    0.000027>] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 7 *10 11 12 14 15)
[    0.234187 <    0.000027>] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.234214 <    0.000027>] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.234241 <    0.000027>] ACPI: PCI Interrupt Link [LNKG] (IRQs 4 *10 11 12 14 15)
[    0.234268 <    0.000027>] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.234375 <    0.000107>] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.234376 <    0.000001>] vgaarb: loaded
[    0.234377 <    0.000001>] vgaarb: bridge control possible 0000:01:00.0
[    0.234523 <    0.000146>] SCSI subsystem initialized
[    0.234524 <    0.000001>] ACPI: bus type scsi registered
[    0.234587 <    0.000063>] libata version 3.00 loaded.
[    0.234605 <    0.000018>] ACPI: bus type usb registered
[    0.234619 <    0.000014>] usbcore: registered new interface driver usbfs
[    0.234626 <    0.000007>] usbcore: registered new interface driver hub
[    0.234646 <    0.000020>] usbcore: registered new device driver usb
[    0.234724 <    0.000078>] PCI: Using ACPI for IRQ routing
[    0.242996 <    0.008272>] PCI: pci_cache_line_size set to 64 bytes
[    0.243054 <    0.000058>] e820: reserve RAM buffer [mem 0x0009fc00-0x0009ffff]
[    0.243056 <    0.000002>] e820: reserve RAM buffer [mem 0xcff90000-0xcfffffff]
[    0.243126 <    0.000070>] NetLabel: Initializing
[    0.243128 <    0.000002>] NetLabel:  domain hash size = 128
[    0.243129 <    0.000001>] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.243137 <    0.000008>] NetLabel:  unlabeled traffic allowed by default
[    0.243217 <    0.000080>] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.243221 <    0.000004>] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    0.245244 <    0.002023>] Switching to clocksource hpet
[    0.249527 <    0.004283>] AppArmor: AppArmor Filesystem Enabled
[    0.249551 <    0.000024>] pnp: PnP ACPI init
[    0.249563 <    0.000012>] ACPI: bus type pnp registered
[    0.249695 <    0.000132>] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.249734 <    0.000039>] pnp 00:01: [dma 4]
[    0.249750 <    0.000016>] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.249776 <    0.000026>] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.249793 <    0.000017>] pnp 00:03: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.249812 <    0.000019>] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.249998 <    0.000186>] pnp 00:05: [dma 0 disabled]
[    0.250037 <    0.000039>] pnp 00:05: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.250308 <    0.000271>] pnp 00:06: [dma 0 disabled]
[    0.250386 <    0.000078>] pnp 00:06: Plug and Play ACPI device, IDs PNP0400 (active)
[    0.250414 <    0.000028>] pnp 00:07: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.250489 <    0.000075>] system 00:08: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.250491 <    0.000002>] system 00:08: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.250493 <    0.000002>] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.250638 <    0.000145>] system 00:09: [io  0x04d0-0x04d1] has been reserved
[    0.250640 <    0.000002>] system 00:09: [io  0x040b] has been reserved
[    0.250642 <    0.000002>] system 00:09: [io  0x04d6] has been reserved
[    0.250643 <    0.000001>] system 00:09: [io  0x0c00-0x0c01] has been reserved
[    0.250645 <    0.000002>] system 00:09: [io  0x0c14] has been reserved
[    0.250647 <    0.000002>] system 00:09: [io  0x0c50-0x0c51] has been reserved
[    0.250648 <    0.000001>] system 00:09: [io  0x0c52] has been reserved
[    0.250650 <    0.000002>] system 00:09: [io  0x0c6c] has been reserved
[    0.250652 <    0.000002>] system 00:09: [io  0x0c6f] has been reserved
[    0.250653 <    0.000001>] system 00:09: [io  0x0cd0-0x0cd1] has been reserved
[    0.250655 <    0.000002>] system 00:09: [io  0x0cd2-0x0cd3] has been reserved
[    0.250657 <    0.000002>] system 00:09: [io  0x0cd4-0x0cd5] has been reserved
[    0.250659 <    0.000002>] system 00:09: [io  0x0cd6-0x0cd7] has been reserved
[    0.250660 <    0.000001>] system 00:09: [io  0x0cd8-0x0cdf] has been reserved
[    0.250662 <    0.000002>] system 00:09: [io  0x0800-0x089f] has been reserved
[    0.250664 <    0.000002>] system 00:09: [io  0x0b00-0x0b0f] has been reserved
[    0.250666 <    0.000002>] system 00:09: [io  0x0b20-0x0b3f] has been reserved
[    0.250667 <    0.000001>] system 00:09: [io  0x0900-0x090f] has been reserved
[    0.250669 <    0.000002>] system 00:09: [io  0x0910-0x091f] has been reserved
[    0.250671 <    0.000002>] system 00:09: [io  0xfe00-0xfefe] has been reserved
[    0.250674 <    0.000003>] system 00:09: [mem 0xffb80000-0xffbfffff] has been reserved
[    0.250676 <    0.000002>] system 00:09: [mem 0xfec10000-0xfec1001f] has been reserved
[    0.250679 <    0.000003>] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.250782 <    0.000103>] system 00:0a: [io  0x0e80-0x0f5f] has been reserved
[    0.250785 <    0.000003>] system 00:0a: [io  0x0ae0-0x0aef] has been reserved
[    0.250787 <    0.000002>] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.250834 <    0.000047>] system 00:0b: [mem 0xe0000000-0xefffffff] has been reserved
[    0.250836 <    0.000002>] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.251500 <    0.000664>] system 00:0c: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.251504 <    0.000004>] system 00:0c: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.251506 <    0.000002>] system 00:0c: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.251508 <    0.000002>] system 00:0c: [mem 0x00100000-0xcfffffff] could not be reserved
[    0.251510 <    0.000002>] system 00:0c: [mem 0xfec00000-0xffffffff] could not be reserved
[    0.251513 <    0.000003>] system 00:0c: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.251594 <    0.000081>] pnp: PnP ACPI: found 13 devices
[    0.251595 <    0.000001>] ACPI: ACPI bus type pnp unregistered
[    0.258008 <    0.006413>] pci 0000:00:02.0: PCI bridge to [bus 01]
[    0.258011 <    0.000003>] pci 0000:00:02.0:   bridge window [io  0xd000-0xdfff]
[    0.258014 <    0.000003>] pci 0000:00:02.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.258017 <    0.000003>] pci 0000:00:02.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.258020 <    0.000003>] pci 0000:00:05.0: PCI bridge to [bus 02]
[    0.258022 <    0.000002>] pci 0000:00:05.0:   bridge window [io  0xe000-0xefff]
[    0.258024 <    0.000002>] pci 0000:00:05.0:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.258027 <    0.000003>] pci 0000:00:05.0:   bridge window [mem 0xfdf00000-0xfdffffff 64bit pref]
[    0.258030 <    0.000003>] pci 0000:00:14.4: PCI bridge to [bus 03]
[    0.258063 <    0.000033>] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.258065 <    0.000002>] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.258066 <    0.000001>] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.258068 <    0.000002>] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.258069 <    0.000001>] pci_bus 0000:00: resource 8 [mem 0xd0000000-0xdfffffff]
[    0.258071 <    0.000002>] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfebfffff]
[    0.258073 <    0.000002>] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    0.258074 <    0.000001>] pci_bus 0000:01: resource 1 [mem 0xfea00000-0xfeafffff]
[    0.258076 <    0.000002>] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.258078 <    0.000002>] pci_bus 0000:02: resource 0 [io  0xe000-0xefff]
[    0.258079 <    0.000001>] pci_bus 0000:02: resource 1 [mem 0xfeb00000-0xfebfffff]
[    0.258081 <    0.000002>] pci_bus 0000:02: resource 2 [mem 0xfdf00000-0xfdffffff 64bit pref]
[    0.258083 <    0.000002>] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    0.258084 <    0.000001>] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
[    0.258086 <    0.000002>] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    0.258088 <    0.000002>] pci_bus 0000:03: resource 7 [mem 0x000d0000-0x000dffff]
[    0.258089 <    0.000001>] pci_bus 0000:03: resource 8 [mem 0xd0000000-0xdfffffff]
[    0.258091 <    0.000002>] pci_bus 0000:03: resource 9 [mem 0xf0000000-0xfebfffff]
[    0.258123 <    0.000032>] NET: Registered protocol family 2
[    0.258258 <    0.000135>] TCP established hash table entries: 32768 (order: 7, 524288 bytes)
[    0.258401 <    0.000143>] TCP bind hash table entries: 32768 (order: 7, 524288 bytes)
[    0.258524 <    0.000123>] TCP: Hash tables configured (established 32768 bind 32768)
[    0.258564 <    0.000040>] TCP: reno registered
[    0.258573 <    0.000009>] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.258598 <    0.000025>] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.258678 <    0.000080>] NET: Registered protocol family 1
[    0.665267 <    0.406589>] pci 0000:01:00.0: Boot video device
[    0.665274 <    0.000007>] PCI: CLS 64 bytes, default 64
[    0.665319 <    0.000045>] Trying to unpack rootfs image as initramfs...
[    0.891536 <    0.226217>] Freeing initrd memory: 15844k freed
[    0.896120 <    0.004584>] PCI-DMA: Disabling AGP.
[    0.896206 <    0.000086>] PCI-DMA: aperture base @ c4000000 size 65536 KB
[    0.896207 <    0.000001>] PCI-DMA: using GART IOMMU.
[    0.896210 <    0.000003>] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    0.899139 <    0.002929>] LVT offset 1 assigned for vector 0x400
[    0.899149 <    0.000010>] IBS: LVT offset 1 assigned
[    0.899175 <    0.000026>] perf: AMD IBS detected (0x0000001f)
[    0.899326 <    0.000151>] Initialise module verification
[    0.899362 <    0.000036>] audit: initializing netlink socket (disabled)
[    0.899373 <    0.000011>] type=2000 audit(1377379728.792:1): initialized
[    0.921466 <    0.022093>] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.922754 <    0.001288>] VFS: Disk quotas dquot_6.5.2
[    0.922793 <    0.000039>] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.923250 <    0.000457>] fuse init (API version 7.20)
[    0.923319 <    0.000069>] msgmni has been set to 7901
[    0.923851 <    0.000532>] Key type asymmetric registered
[    0.923852 <    0.000001>] Asymmetric key parser 'x509' registered
[    0.923878 <    0.000026>] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.923909 <    0.000031>] io scheduler noop registered
[    0.923910 <    0.000001>] io scheduler deadline registered (default)
[    0.923914 <    0.000004>] io scheduler cfq registered
[    0.924027 <    0.000113>] pcieport 0000:00:02.0: irq 40 for MSI/MSI-X
[    0.924108 <    0.000081>] pcieport 0000:00:05.0: irq 41 for MSI/MSI-X
[    0.924167 <    0.000059>] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.924179 <    0.000012>] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.924266 <    0.000087>] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.924270 <    0.000004>] ACPI: Power Button [PWRB]
[    0.924297 <    0.000027>] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.924299 <    0.000002>] ACPI: Power Button [PWRF]
[    0.924350 <    0.000051>] ACPI: processor limited to max C-state 1
[    0.930960 <    0.006610>] GHES: HEST is not enabled!
[    0.931056 <    0.000096>] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.951523 <    0.020467>] 00:05: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.952813 <    0.001290>] Linux agpgart interface v0.103
[    0.953982 <    0.001169>] brd: module loaded
[    0.954628 <    0.000646>] loop: module loaded
[    0.954929 <    0.000301>] libphy: Fixed MDIO Bus: probed
[    0.954974 <    0.000045>] tun: Universal TUN/TAP device driver, 1.6
[    0.954975 <    0.000001>] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.955017 <    0.000042>] PPP generic driver version 2.4.2
[    0.955088 <    0.000071>] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.955090 <    0.000002>] ehci-pci: EHCI PCI platform driver
[    0.955138 <    0.000048>] ehci-pci 0000:00:12.2: EHCI Host Controller
[    0.955148 <    0.000010>] ehci-pci 0000:00:12.2: new USB bus registered, assigned bus number 1
[    0.955157 <    0.000009>] ehci-pci 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    0.955169 <    0.000012>] ehci-pci 0000:00:12.2: debug port 1
[    0.955207 <    0.000038>] ehci-pci 0000:00:12.2: irq 17, io mem 0xfe9ff800
[    0.965188 <    0.009981>] ehci-pci 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    0.965204 <    0.000016>] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.965206 <    0.000002>] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.965208 <    0.000002>] usb usb1: Product: EHCI Host Controller
[    0.965209 <    0.000001>] usb usb1: Manufacturer: Linux 3.8.0-29-generic ehci_hcd
[    0.965211 <    0.000002>] usb usb1: SerialNumber: 0000:00:12.2
[    0.965297 <    0.000086>] hub 1-0:1.0: USB hub found
[    0.965300 <    0.000003>] hub 1-0:1.0: 6 ports detected
[    0.965418 <    0.000118>] ehci-pci 0000:00:13.2: EHCI Host Controller
[    0.965423 <    0.000005>] ehci-pci 0000:00:13.2: new USB bus registered, assigned bus number 2
[    0.965427 <    0.000004>] ehci-pci 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    0.965438 <    0.000011>] ehci-pci 0000:00:13.2: debug port 1
[    0.965467 <    0.000029>] ehci-pci 0000:00:13.2: irq 19, io mem 0xfe9ff400
[    0.977188 <    0.011721>] ehci-pci 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    0.977197 <    0.000009>] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    0.977198 <    0.000001>] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.977200 <    0.000002>] usb usb2: Product: EHCI Host Controller
[    0.977201 <    0.000001>] usb usb2: Manufacturer: Linux 3.8.0-29-generic ehci_hcd
[    0.977203 <    0.000002>] usb usb2: SerialNumber: 0000:00:13.2
[    0.977265 <    0.000062>] hub 2-0:1.0: USB hub found
[    0.977268 <    0.000003>] hub 2-0:1.0: 6 ports detected
[    0.977353 <    0.000085>] ehci-platform: EHCI generic platform driver
[    0.977359 <    0.000006>] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.977386 <    0.000027>] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    0.977391 <    0.000005>] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    0.977410 <    0.000019>] ohci_hcd 0000:00:12.0: irq 16, io mem 0xfe9fe000
[    1.037152 <    0.059742>] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    1.037153 <    0.000001>] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.037155 <    0.000002>] usb usb3: Product: OHCI Host Controller
[    1.037156 <    0.000001>] usb usb3: Manufacturer: Linux 3.8.0-29-generic ohci_hcd
[    1.037158 <    0.000002>] usb usb3: SerialNumber: 0000:00:12.0
[    1.037257 <    0.000099>] hub 3-0:1.0: USB hub found
[    1.037263 <    0.000006>] hub 3-0:1.0: 3 ports detected
[    1.037344 <    0.000081>] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    1.037348 <    0.000004>] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
[    1.037359 <    0.000011>] ohci_hcd 0000:00:12.1: irq 16, io mem 0xfe9fd000
[    1.097132 <    0.059773>] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    1.097134 <    0.000002>] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.097136 <    0.000002>] usb usb4: Product: OHCI Host Controller
[    1.097137 <    0.000001>] usb usb4: Manufacturer: Linux 3.8.0-29-generic ohci_hcd
[    1.097138 <    0.000001>] usb usb4: SerialNumber: 0000:00:12.1
[    1.097235 <    0.000097>] hub 4-0:1.0: USB hub found
[    1.097242 <    0.000007>] hub 4-0:1.0: 3 ports detected
[    1.097324 <    0.000082>] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    1.097328 <    0.000004>] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    1.097345 <    0.000017>] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfe9fc000
[    1.157123 <    0.059778>] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    1.157125 <    0.000002>] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.157127 <    0.000002>] usb usb5: Product: OHCI Host Controller
[    1.157128 <    0.000001>] usb usb5: Manufacturer: Linux 3.8.0-29-generic ohci_hcd
[    1.157129 <    0.000001>] usb usb5: SerialNumber: 0000:00:13.0
[    1.157225 <    0.000096>] hub 5-0:1.0: USB hub found
[    1.157231 <    0.000006>] hub 5-0:1.0: 3 ports detected
[    1.157316 <    0.000085>] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    1.157320 <    0.000004>] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
[    1.157332 <    0.000012>] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfe9fb000
[    1.217107 <    0.059775>] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
[    1.217108 <    0.000001>] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.217110 <    0.000002>] usb usb6: Product: OHCI Host Controller
[    1.217111 <    0.000001>] usb usb6: Manufacturer: Linux 3.8.0-29-generic ohci_hcd
[    1.217113 <    0.000002>] usb usb6: SerialNumber: 0000:00:13.1
[    1.217215 <    0.000102>] hub 6-0:1.0: USB hub found
[    1.217220 <    0.000005>] hub 6-0:1.0: 3 ports detected
[    1.217302 <    0.000082>] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    1.217306 <    0.000004>] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
[    1.217317 <    0.000011>] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfe9fa000
[    1.277089 <    0.059772>] usb usb7: New USB device found, idVendor=1d6b, idProduct=0001
[    1.277091 <    0.000002>] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.277092 <    0.000001>] usb usb7: Product: OHCI Host Controller
[    1.277094 <    0.000002>] usb usb7: Manufacturer: Linux 3.8.0-29-generic ohci_hcd
[    1.277095 <    0.000001>] usb usb7: SerialNumber: 0000:00:14.5
[    1.277201 <    0.000106>] hub 7-0:1.0: USB hub found
[    1.277207 <    0.000006>] hub 7-0:1.0: 2 ports detected
[    1.277271 <    0.000064>] uhci_hcd: USB Universal Host Controller Interface driver
[    1.277337 <    0.000066>] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    1.277728 <    0.000391>] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.277737 <    0.000009>] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.277889 <    0.000152>] mousedev: PS/2 mouse device common for all mice
[    1.278002 <    0.000113>] rtc_cmos 00:02: RTC can wake from S4
[    1.278104 <    0.000102>] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.278128 <    0.000024>] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.278203 <    0.000075>] device-mapper: uevent: version 1.0.3
[    1.278256 <    0.000053>] device-mapper: ioctl: 4.23.1-ioctl (2012-12-18) initialised: dm-devel@redhat.com
[    1.278262 <    0.000006>] cpuidle: using governor ladder
[    1.278263 <    0.000001>] cpuidle: using governor menu
[    1.278267 <    0.000004>] ledtrig-cpu: registered to indicate activity on CPUs
[    1.278268 <    0.000001>] EFI Variables Facility v0.08 2004-May-17
[    1.278491 <    0.000223>] ashmem: initialized
[    1.278588 <    0.000097>] TCP: cubic registered
[    1.278666 <    0.000078>] NET: Registered protocol family 10
[    1.278797 <    0.000131>] NET: Registered protocol family 17
[    1.278806 <    0.000009>] Key type dns_resolver registered
[    1.278991 <    0.000185>] Loading module verification certificates
[    1.279933 <    0.000942>] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: d8bc1516bb9827ccf9ced525fc4133574da45d40'
[    1.279942 <    0.000009>] registered taskstats version 1
[    1.282139 <    0.002197>] Key type trusted registered
[    1.283994 <    0.001855>] Key type encrypted registered
[    1.286127 <    0.002133>] rtc_cmos 00:02: setting system clock to 2013-08-24 21:28:49 UTC (1377379729)
[    1.286168 <    0.000041>] powernow-k8: this CPU is not supported anymore, using acpi-cpufreq instead.
[    1.287128 <    0.000960>] acpi-cpufreq: overriding BIOS provided _PSD data
[    1.287212 <    0.000084>] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.287213 <    0.000001>] EDD information not available.
[    1.288436 <    0.001223>] Freeing unused kernel memory: 996k freed
[    1.288650 <    0.000214>] Write protecting the kernel read-only data: 12288k
[    1.291711 <    0.003061>] Freeing unused kernel memory: 1168k freed
[    1.294656 <    0.002945>] Freeing unused kernel memory: 1076k freed
[    1.308728 <    0.014072>] udevd[105]: starting version 175
[    1.341401 <    0.032673>] Disabling lock debugging due to kernel taint
[    1.341922 <    0.000521>] ahci 0000:00:11.0: version 3.0
[    1.342017 <    0.000095>] ahci 0000:00:11.0: irq 42 for MSI/MSI-X
[    1.342115 <    0.000098>] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.342118 <    0.000003>] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc 
[    1.343479 <    0.001361>] scsi0 : ahci
[    1.343583 <    0.000104>] scsi1 : ahci
[    1.343687 <    0.000104>] scsi2 : ahci
[    1.343734 <    0.000047>] scsi3 : ahci
[    1.343786 <    0.000052>] ata1: SATA max UDMA/133 abar m1024@0xfe9ffc00 port 0xfe9ffd00 irq 42
[    1.343789 <    0.000003>] ata2: SATA max UDMA/133 abar m1024@0xfe9ffc00 port 0xfe9ffd80 irq 42
[    1.343791 <    0.000002>] ata3: SATA max UDMA/133 abar m1024@0xfe9ffc00 port 0xfe9ffe00 irq 42
[    1.343793 <    0.000002>] ata4: SATA max UDMA/133 abar m1024@0xfe9ffc00 port 0xfe9ffe80 irq 42
[    1.345710 <    0.001917>] pata_atiixp 0000:00:14.1: setting latency timer to 64
[    1.345939 <    0.000229>] scsi4 : pata_atiixp
[    1.346221 <    0.000282>] scsi5 : pata_atiixp
[    1.346407 <    0.000186>] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    1.346409 <    0.000002>] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    1.350579 <    0.004170>] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.350754 <    0.000175>] r8169 0000:02:00.0: irq 43 for MSI/MSI-X
[    1.350879 <    0.000125>] r8169 0000:02:00.0 eth0: RTL8168d/8111d at 0xffffc9000064a000, 40:61:86:e4:65:b2, XID 081000c0 IRQ 43
[    1.350882 <    0.000003>] r8169 0000:02:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    1.485042 <    0.134160>] usb 4-2: new low-speed USB device number 2 using ohci_hcd
[    1.565499 <    0.080457>] ata5.00: ATAPI: PHILIPS SPD2410L1, M5P4, max UDMA/66
[    1.565904 <    0.000405>] ata5.01: ATA-6: HDS722580VLAT20, V32OA60A, max UDMA/100
[    1.565908 <    0.000004>] ata5.01: 160836480 sectors, multi 16: LBA48 
[    1.597392 <    0.031484>] ata5.00: configured for UDMA/66
[    1.621770 <    0.024378>] ata5.01: configured for UDMA/100
[    1.656086 <    0.034316>] usb 4-2: New USB device found, idVendor=046d, idProduct=c505
[    1.656089 <    0.000003>] usb 4-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.656091 <    0.000002>] usb 4-2: Product: USB Receiver
[    1.656092 <    0.000001>] usb 4-2: Manufacturer: Logitech
[    1.660981 <    0.004889>] ata1: SATA link down (SStatus 0 SControl 300)
[    1.665050 <    0.004069>] ata4: SATA link down (SStatus 0 SControl 300)
[    1.665087 <    0.000037>] ata3: SATA link down (SStatus 0 SControl 300)
[    1.679111 <    0.014024>] usbcore: registered new interface driver usbhid
[    1.679113 <    0.000002>] usbhid: USB HID core driver
[    1.681994 <    0.002881>] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:12.1/usb4/4-2/4-2:1.0/input/input2
[    1.682099 <    0.000105>] hid-generic 0003:046D:C505.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:12.1-2/input0
[    1.682389 <    0.000290>] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:12.1/usb4/4-2/4-2:1.1/input/input3
[    1.682461 <    0.000072>] hid-generic 0003:046D:C505.0002: input,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:12.1-2/input1
[    1.836969 <    0.154508>] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.864058 <    0.027089>] ata2.00: ATA-8: ST3320418AS, CC44, max UDMA/133
[    1.864061 <    0.000003>] ata2.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.896944 <    0.032883>] tsc: Refined TSC clocksource calibration: 2900.119 MHz
[    1.896949 <    0.000005>] Switching to clocksource tsc
[    1.903614 <    0.006665>] ata2.00: configured for UDMA/133
[    1.903739 <    0.000125>] scsi 1:0:0:0: Direct-Access     ATA      ST3320418AS      CC44 PQ: 0 ANSI: 5
[    1.903850 <    0.000111>] sd 1:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.903877 <    0.000027>] sd 1:0:0:0: Attached scsi generic sg0 type 0
[    1.903898 <    0.000021>] sd 1:0:0:0: [sda] Write Protect is off
[    1.903902 <    0.000004>] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.903916 <    0.000014>] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.904856 <    0.000940>] scsi 4:0:0:0: CD-ROM            PHILIPS  SPD2410L1        M5P4 PQ: 0 ANSI: 5
[    1.907383 <    0.002527>] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.907385 <    0.000002>] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.907478 <    0.000093>] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    1.907609 <    0.000131>] sr 4:0:0:0: Attached scsi generic sg1 type 5
[    1.907968 <    0.000359>] scsi 4:0:1:0: Direct-Access     ATA      HDS722580VLAT20  V32O PQ: 0 ANSI: 5
[    1.908101 <    0.000133>] sd 4:0:1:0: [sdb] 160836480 512-byte logical blocks: (82.3 GB/76.6 GiB)
[    1.908120 <    0.000019>] sd 4:0:1:0: Attached scsi generic sg2 type 0
[    1.908546 <    0.000426>] sd 4:0:1:0: [sdb] Write Protect is off
[    1.908549 <    0.000003>] sd 4:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    1.908562 <    0.000013>] sd 4:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.931083 <    0.022521>]  sda: sda1 sda2
[    1.931386 <    0.000303>] sd 1:0:0:0: [sda] Attached SCSI disk
[    1.948917 <    0.017531>]  sdb: sdb1 sdb2
[    1.973580 <    0.024663>] sd 4:0:1:0: [sdb] Attached SCSI disk
[    2.485822 <    0.512242>] EXT4-fs (sdb2): INFO: recovery required on readonly filesystem
[    2.485826 <    0.000004>] EXT4-fs (sdb2): write access will be enabled during recovery
[    4.599323 <    2.113497>] EXT4-fs (sdb2): recovery complete
[    4.605769 <    0.006446>] EXT4-fs (sdb2): mounted filesystem with ordered data mode. Opts: (null)
[    8.847115 <    4.241346>] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    8.859180 <    0.012065>] init: bootchart pre-stop process (373) terminated with status 1
[    9.108098 <    0.248918>] udevd[377]: starting version 175
[   10.551318 <    1.443220>] EXT4-fs (sdb2): re-mounted. Opts: errors=remount-ro
[   11.286074 <    0.734756>] lp: driver loaded but no devices found
[   15.199598 <    3.913524>] parport_pc 00:06: reported by Plug and Play ACPI
[   15.199656 <    0.000058>] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   15.293686 <    0.094030>] lp0: using parport0 (interrupt-driven).
[   15.409400 <    0.115714>] ppdev: user-space parallel port driver
[   15.546946 <    0.137546>] wmi: Mapper loaded
[   15.697200 <    0.150254>] microcode: CPU0: patch_level=0x01000086
[   15.726775 <    0.029575>] MCE: In-kernel MCE decoding enabled.
[   15.853278 <    0.126503>] EDAC MC: Ver: 3.0.0
[   15.920224 <    0.066946>] AMD64 EDAC driver v3.4.0
[   15.920265 <    0.000041>] EDAC amd64: DRAM ECC disabled.
[   15.920275 <    0.000010>] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   15.920275 <    0.000000>]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   15.920275 <    0.000000>]  (Note that use of the override may cause unknown side effects.)
[   16.331142 <    0.410867>] ACPI Warning: 0x0000000000000b00-0x0000000000000b07 SystemIO conflicts with Region \SOR1 1 (20121018/utaddress-251)
[   16.331151 <    0.000009>] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   16.649675 <    0.318524>] init: bootchart post-stop process (374) terminated with status 2
[   16.744148 <    0.094473>] sp5100_tco: SP5100/SB800 TCO WatchDog Timer Driver v0.05
[   16.744212 <    0.000064>] sp5100_tco: PCI Revision ID: 0x3c
[   16.744231 <    0.000019>] sp5100_tco: failed to find MMIO address, giving up.
[   16.910894 <    0.166663>] microcode: CPU0: new patch_level=0x010000db
[   16.910908 <    0.000014>] microcode: CPU1: patch_level=0x01000086
[   16.910916 <    0.000008>] microcode: CPU1: new patch_level=0x010000db
[   16.910921 <    0.000005>] microcode: CPU2: patch_level=0x01000086
[   16.910927 <    0.000006>] microcode: CPU2: new patch_level=0x010000db
[   16.910991 <    0.000064>] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   16.951896 <    0.040905>] [drm] Initialized drm 1.1.0 20060810
[   17.632870 <    0.680974>] kvm: Nested Virtualization enabled
[   17.632898 <    0.000028>] kvm: Nested Paging enabled
[   17.900284 <    0.267386>] input: HDA ATI SB Line as /devices/pci0000:00/0000:00:14.2/sound/card0/input4
[   17.900357 <    0.000073>] input: HDA ATI SB Rear Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input5
[   17.900413 <    0.000056>] input: HDA ATI SB Front Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input6
[   17.900458 <    0.000045>] input: HDA ATI SB Front Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input7
[   17.900502 <    0.000044>] input: HDA ATI SB Line Out Side as /devices/pci0000:00/0000:00:14.2/sound/card0/input8
[   17.900547 <    0.000045>] input: HDA ATI SB Line Out CLFE as /devices/pci0000:00/0000:00:14.2/sound/card0/input9
[   17.900590 <    0.000043>] input: HDA ATI SB Line Out Surround as /devices/pci0000:00/0000:00:14.2/sound/card0/input10
[   17.900632 <    0.000042>] input: HDA ATI SB Line Out Front as /devices/pci0000:00/0000:00:14.2/sound/card0/input11
[   17.900882 <    0.000250>] hda-intel 0000:01:00.1: Handle VGA-switcheroo audio client
[   17.900945 <    0.000063>] snd_hda_intel 0000:01:00.1: irq 44 for MSI/MSI-X
[   18.024288 <    0.123343>] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input12
[   18.170798 <    0.146510>] [drm] radeon defaulting to kernel modesetting.
[   18.170801 <    0.000003>] [drm] radeon kernel modesetting enabled.
[   18.171056 <    0.000255>] [drm] initializing kernel modesetting (RV770 0x1002:0x9442 0x1787:0x2009).
[   18.171080 <    0.000024>] [drm] register mmio base: 0xFEAF0000
[   18.171082 <    0.000002>] [drm] register mmio size: 65536
[   18.171658 <    0.000576>] ATOM BIOS: 
[   18.171677 <    0.000019>] radeon 0000:01:00.0: VRAM: 512M 0x0000000000000000 - 0x000000001FFFFFFF (512M used)
[   18.171679 <    0.000002>] radeon 0000:01:00.0: GTT: 512M 0x0000000020000000 - 0x000000003FFFFFFF
[   18.171932 <    0.000253>] [drm] Detected VRAM RAM=512M, BAR=256M
[   18.171935 <    0.000003>] [drm] RAM width 256bits DDR
[   18.172012 <    0.000077>] [TTM] Zone  kernel: Available graphics memory: 2024500 kiB
[   18.172014 <    0.000002>] [TTM] Initializing pool allocator
[   18.172017 <    0.000003>] [TTM] Initializing DMA pool allocator
[   18.172037 <    0.000020>] [drm] radeon: 512M of VRAM memory ready
[   18.172038 <    0.000001>] [drm] radeon: 512M of GTT memory ready.
[   18.172052 <    0.000014>] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   18.172963 <    0.000911>] [drm] probing gen 2 caps for device 1022:9603 = 2/0
[   18.172966 <    0.000003>] [drm] enabling PCIE gen 2 link speeds, disable with radeon.pcie_gen2=0
[   18.173052 <    0.000086>] [drm] Loading RV770 Microcode
[   18.681414 <    0.508362>] [drm] PCIE GART of 512M enabled (table at 0x0000000000040000).
[   18.681473 <    0.000059>] radeon 0000:01:00.0: WB enabled
[   18.681477 <    0.000004>] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000020000c00 and cpu addr 0xffff880127d2fc00
[   18.681479 <    0.000002>] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000020000c0c and cpu addr 0xffff880127d2fc0c
[   18.681481 <    0.000002>] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   18.681482 <    0.000001>] [drm] Driver supports precise vblank timestamp query.
[   18.681512 <    0.000030>] radeon 0000:01:00.0: irq 45 for MSI/MSI-X
[   18.681523 <    0.000011>] radeon 0000:01:00.0: radeon: using MSI.
[   18.681542 <    0.000019>] [drm] radeon: irq initialized.
[   18.727368 <    0.045826>] [drm] ring test on 0 succeeded in 1 usecs
[   18.727425 <    0.000057>] [drm] ring test on 3 succeeded in 1 usecs
[   18.727505 <    0.000080>] [drm] ib test on ring 0 succeeded in 0 usecs
[   18.727517 <    0.000012>] [drm] ib test on ring 3 succeeded in 0 usecs
[   18.727711 <    0.000194>] [drm] Radeon Display Connectors
[   18.727712 <    0.000001>] [drm] Connector 0:
[   18.727713 <    0.000001>] [drm]   HDMI-A-1
[   18.727714 <    0.000001>] [drm]   HPD1
[   18.727716 <    0.000002>] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[   18.727717 <    0.000001>] [drm]   Encoders:
[   18.727718 <    0.000001>] [drm]     DFP1: INTERNAL_UNIPHY
[   18.727719 <    0.000001>] [drm] Connector 1:
[   18.727720 <    0.000001>] [drm]   VGA-1
[   18.727721 <    0.000001>] [drm]   DDC: 0x7e60 0x7e60 0x7e64 0x7e64 0x7e68 0x7e68 0x7e6c 0x7e6c
[   18.727722 <    0.000001>] [drm]   Encoders:
[   18.727723 <    0.000001>] [drm]     CRT2: INTERNAL_KLDSCP_DAC2
[   18.727724 <    0.000001>] [drm] Connector 2:
[   18.727725 <    0.000001>] [drm]   DVI-I-1
[   18.727726 <    0.000001>] [drm]   HPD2
[   18.727727 <    0.000001>] [drm]   DDC: 0x7e20 0x7e20 0x7e24 0x7e24 0x7e28 0x7e28 0x7e2c 0x7e2c
[   18.727728 <    0.000001>] [drm]   Encoders:
[   18.727729 <    0.000001>] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[   18.727730 <    0.000001>] [drm]     DFP2: INTERNAL_KLDSCP_LVTMA
[   18.727754 <    0.000024>] [drm] Internal thermal controller without fan control
[   18.727785 <    0.000031>] [drm] radeon: power management initialized
[   18.770859 <    0.043074>] [drm] fb mappable at 0xD0142000
[   18.770860 <    0.000001>] [drm] vram apper at 0xD0000000
[   18.770861 <    0.000001>] [drm] size 8294400
[   18.770862 <    0.000001>] [drm] fb depth is 24
[   18.770863 <    0.000001>] [drm]    pitch is 7680
[   18.770947 <    0.000084>] fbcon: radeondrmfb (fb0) is primary device
[   18.799564 <    0.028617>] type=1400 audit(1377401347.012:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=780 comm="apparmor_parser"
[   18.799575 <    0.000011>] type=1400 audit(1377401347.012:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=791 comm="apparmor_parser"
[   18.799951 <    0.000376>] type=1400 audit(1377401347.012:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=780 comm="apparmor_parser"
[   18.799964 <    0.000013>] type=1400 audit(1377401347.012:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=791 comm="apparmor_parser"
[   18.800166 <    0.000202>] type=1400 audit(1377401347.012:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=780 comm="apparmor_parser"
[   18.800185 <    0.000019>] type=1400 audit(1377401347.012:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=791 comm="apparmor_parser"
[   18.984779 <    0.184594>] Console: switching to colour frame buffer device 240x67
[   18.991440 <    0.006661>] radeon 0000:01:00.0: fb0: radeondrmfb frame buffer device
[   18.991442 <    0.000002>] radeon 0000:01:00.0: registered panic notifier
[   18.991448 <    0.000006>] [drm] Initialized radeon 2.29.0 20080528 for 0000:01:00.0 on minor 0
[   20.416555 <    1.425107>] init: failsafe main process (870) killed by TERM signal
[   22.142541 <    1.725986>] Bluetooth: Core ver 2.16
[   22.142568 <    0.000027>] NET: Registered protocol family 31
[   22.142570 <    0.000002>] Bluetooth: HCI device and connection manager initialized
[   22.142578 <    0.000008>] Bluetooth: HCI socket layer initialized
[   22.142580 <    0.000002>] Bluetooth: L2CAP socket layer initialized
[   22.142584 <    0.000004>] Bluetooth: SCO socket layer initialized
[   22.283639 <    0.141055>] Bluetooth: RFCOMM TTY layer initialized
[   22.283651 <    0.000012>] Bluetooth: RFCOMM socket layer initialized
[   22.283653 <    0.000002>] Bluetooth: RFCOMM ver 1.11
[   22.674510 <    0.390857>] init: avahi-cups-reload main process (976) terminated with status 1
[   22.696897 <    0.022387>] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   22.696901 <    0.000004>] Bluetooth: BNEP filters: protocol multicast
[   22.696911 <    0.000010>] Bluetooth: BNEP socket layer initialized
[   23.720986 <    1.024075>] type=1400 audit(1377401351.940:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=987 comm="apparmor_parser"
[   23.721433 <    0.000447>] type=1400 audit(1377401351.940:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=987 comm="apparmor_parser"
[   28.571484 <    4.850051>] r8169 0000:02:00.0 eth0: link down
[   28.571492 <    0.000008>] r8169 0000:02:00.0 eth0: link down
[   28.571528 <    0.000036>] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   28.571793 <    0.000265>] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   30.272806 <    1.701013>] r8169 0000:02:00.0 eth0: link up
[   30.272815 <    0.000009>] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   32.420184 <    2.147369>] type=1400 audit(1377401360.636:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper" pid=1091 comm="apparmor_parser"
[   32.420488 <    0.000304>] type=1400 audit(1377401360.636:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper//chromium_browser" pid=1091 comm="apparmor_parser"
[   32.422902 <    0.002414>] type=1400 audit(1377401360.640:12): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1093 comm="apparmor_parser"
[   32.423305 <    0.000403>] type=1400 audit(1377401360.640:13): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1093 comm="apparmor_parser"
[   32.423526 <    0.000221>] type=1400 audit(1377401360.640:14): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1093 comm="apparmor_parser"
[   32.426962 <    0.003436>] type=1400 audit(1377401360.644:15): apparmor="STATUS" operation="profile_load" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-uccsconfigure/uccsconfigure-session-wrapper" pid=1092 comm="apparmor_parser"
[   32.427209 <    0.000247>] type=1400 audit(1377401360.644:16): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1090 comm="apparmor_parser"
[   32.427347 <    0.000138>] type=1400 audit(1377401360.644:17): apparmor="STATUS" operation="profile_load" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-uccsconfigure/uccsconfigure-session-wrapper//chromium_browser" pid=1092 comm="apparmor_parser"
[   32.427513 <    0.000166>] type=1400 audit(1377401360.644:18): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=1090 comm="apparmor_parser"
[   32.431552 <    0.004039>] type=1400 audit(1377401360.648:19): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1097 comm="apparmor_parser"
[   35.506978 <    3.075426>] init: gdm main process (1170) killed by TERM signal
[  101.251988 <   65.745010>] Netfilter messages via NETLINK v0.30.

```

---

### Post by lobo78 on 2013-08-26
bump

---

### Post by Petro Dawg on 2013-08-26
Can't say for sure about 13.04, but in 12.04 I used...

```
sudo sed -i "s/NoDisplay=true/NoDisplay=false/g" /etc/xdg/autostart/*.desktop
```

to make my hidden auto start programs visible in the startup applications menu.  If you know what you are doing, uncheck those processes you do not need auto-started to save on boot time.
Just make sure you don't turn off something you need.

More info referring to what I'm suggesting can be found here [http://www.askmeaboutlinux.com/?p=1974](http://www.askmeaboutlinux.com/?p=1974)

I could only guess at what that Netfilter is, perhaps someone else can chime in who knows what that is for certain.

Hope that helps a little.

---

### Post by oldfred on 2013-08-26
I have no man entry for netfilter. But I have working networking with 12.04. 
Did you turn on firewall or some special networking features?

[http://en.wikipedia.org/wiki/Netfilter](http://en.wikipedia.org/wiki/Netfilter)

---

