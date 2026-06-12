---
title: "Random Abnormal Shutdown"
date: 2014-05-15
forum: General Help
---

### Post by digiPixel on 2014-05-15
Have an old desktop PC running Xubuntu 14.04 where every once in a while an instant/abnormal shutdown would occur after a few seconds (around 5). Just before the instant shutdown occurs the Xfce shutdown dialog appears. Clicking on the Cancel button in the dialog when it appears without manual intervention a second time also causes an instant shutdown to occur.

Did see some warning on ACPI via **dmesg** but don't think it is very likely to be related to the issue. Previously the PC was running Ubuntu 12.04 and didn't have the abnormal/instant shutdown issue. There is an important kernel update to install in the Security section of the Software Updater although it is highly unlikely to fix the issue.


=====================
**[SIZE=5]Dmesg Log[/SIZE]**
=====================

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.13.0-24-generic (buildd@komainu) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #47-Ubuntu SMP Fri May 2 23:31:42 UTC 2014 (Ubuntu 3.13.0-24.47-generic 3.13.9)
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
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009fbff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009fc00-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e4000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000007ffbffff] usable
[    0.000000] BIOS-e820: [mem 0x000000007ffc0000-0x000000007ffcffff] ACPI data
[    0.000000] BIOS-e820: [mem 0x000000007ffd0000-0x000000007fffffff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff7c0000-0x00000000ffffffff] reserved
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.3 present.
[    0.000000] DMI: ASUSTek Computer Inc. K8N/'K8N', BIOS 1004.005 11/26/2004
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0x7ffc0 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FF80000000 write-back
[    0.000000]   1 disabled
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] found SMP MP-table at [mem 0x000ff780-0x000ff78f] mapped at [c00ff780]
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
[    0.000000] BRK [0x01b88000, 0x01b88fff] PGTABLE
[    0.000000] RAMDISK: [mem 0x35c70000-0x36e2ffff]
[    0.000000] ACPI: RSDP 000fa010 000014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 7ffc0000 000030 (v01 A M I  OEMRSDT  11000426 MSFT 00000097)
[    0.000000] ACPI: FACP 7ffc0200 000081 (v02 A M I  OEMFACP  11000426 MSFT 00000097)
[    0.000000] ACPI: DSDT 7ffc0400 00441D (v01  A0128 A0128003 00000003 INTL 02002026)
[    0.000000] ACPI: FACS 7ffd0000 000040
[    0.000000] ACPI: APIC 7ffc0390 000068 (v01 A M I  OEMAPIC  11000426 MSFT 00000097)
[    0.000000] ACPI: OEMB 7ffd0040 000041 (v01 A M I  OEMBIOS  11000426 MSFT 00000097)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1155MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] BRK [0x01b89000, 0x01b89fff] PGTABLE
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   Normal   [mem 0x01000000-0x37bfdfff]
[    0.000000]   HighMem  [mem 0x37bfe000-0x7ffbffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009efff]
[    0.000000]   node   0: [mem 0x00100000-0x7ffbffff]
[    0.000000] On node 0 totalpages: 524126
[    0.000000] free_area_init_node: node 0, pgdat c1990a80, node_mem_map f4c70020
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3998 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 224254 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2312 pages used for memmap
[    0.000000]   HighMem zone: 295874 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: BIOS IRQ0 override ignored.
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] smpboot: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000e3fff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e4000-0x000fffff]
[    0.000000] e820: [mem 0x80000000-0xfebfffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @f7be4000 s36096 r0 d21248 u57344
[    0.000000] pcpu-alloc: s36096 r0 d21248 u57344 alloc=14*4096
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 522342
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic root=UUID=7552b070-edb5-486a-9fe3-b3db47447598 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 4193784 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:0007ffc0)
[    0.000000] Memory: 2045056K/2096504K available (6507K kernel code, 641K rwdata, 2752K rodata, 872K init, 924K bss, 51448K reserved, 1183496K highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff14000 - 0xfffff000   ( 940 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc19ae000 - 0xc1a88000   ( 872 kB)
[    0.000000]       .data : 0xc165b132 - 0xc19ad4c0   (3400 kB)
[    0.000000]       .text : 0xc1000000 - 0xc165b132   (6508 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU restricting CPUs from NR_CPUS=8 to nr_cpu_ids=1.
[    0.000000] NR_IRQS:2304 nr_irqs:256 16
[    0.000000] CPU 0 irqstacks, hard=f7008000 soft=f700a000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 1808.985 MHz processor
[    0.004004] Calibrating delay loop (skipped), value calculated using timer frequency.. 3617.97 BogoMIPS (lpj=7235940)
[    0.004011] pid_max: default: 32768 minimum: 301
[    0.004074] Security Framework initialized
[    0.004125] AppArmor: AppArmor initialized
[    0.004127] Yama: becoming mindful.
[    0.004231] Mount-cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.004235] Mountpoint-cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.004739] Initializing cgroup subsys memory
[    0.004757] Initializing cgroup subsys devices
[    0.004761] Initializing cgroup subsys freezer
[    0.004765] Initializing cgroup subsys blkio
[    0.004768] Initializing cgroup subsys perf_event
[    0.004773] Initializing cgroup subsys hugetlb
[    0.004831] mce: CPU supports 5 MCE banks
[    0.004874] Last level iTLB entries: 4KB 512, 2MB 8, 4MB 4
[    0.004874] Last level dTLB entries: 4KB 512, 2MB 8, 4MB 4
[    0.004874] tlb_flushall_shift: 4
[    0.020280] Freeing SMP alternatives memory: 32K (c1a88000 - c1a90000)
[    0.021909] ACPI: Core revision 20131115
[    0.025889] ACPI: All ACPI Tables successfully acquired
[    0.028022] ftrace: allocating 27695 entries in 55 pages
[    0.044306] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.044696] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.086298] smpboot: CPU0: AMD Athlon(tm) 64 Processor 2800+ (fam: 0f, model: 04, stepping: 0a)
[    0.088000] Performance Events: AMD PMU driver.
[    0.088000] ... version:                0
[    0.088000] ... bit width:              48
[    0.088000] ... generic registers:      4
[    0.088000] ... value mask:             0000ffffffffffff
[    0.088000] ... max period:             00007fffffffffff
[    0.088000] ... fixed-purpose events:   0
[    0.088000] ... event mask:             000000000000000f
[    0.089846] x86: Booted up 1 node, 1 CPUs
[    0.089857] smpboot: Total of 1 processors activated (3617.97 BogoMIPS)
[    0.090336] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.090737] devtmpfs: initialized
[    0.091018] EVM: security.selinux
[    0.091020] EVM: security.SMACK64
[    0.091022] EVM: security.ima
[    0.091024] EVM: security.capability
[    0.091119] PM: Registering ACPI NVS region [mem 0x7ffd0000-0x7fffffff] (196608 bytes)
[    0.093089] pinctrl core: initialized pinctrl subsystem
[    0.093228] regulator-dummy: no parameters
[    0.093268] RTC time: 10:35:18, date: 05/15/14
[    0.093339] NET: Registered protocol family 16
[    0.093565] EISA bus registered
[    0.093569] cpuidle: using governor ladder
[    0.093572] cpuidle: using governor menu
[    0.093580] node 0 link 0: io port [1000, ffffff]
[    0.093586] TOM: 0000000080000000 aka 2048M
[    0.093592] node 0 link 0: mmio [a0000, bffff]
[    0.093598] node 0 link 0: mmio [80000000, fe0bffff]
[    0.093603] bus: [bus 00-ff] on node 0 link 0
[    0.093606] bus: 00 [io  0x0000-0xffff]
[    0.093609] bus: 00 [mem 0x000a0000-0x000bffff]
[    0.093611] bus: 00 [mem 0x80000000-0xfcffffffff]
[    0.093690] ACPI: bus type PCI registered
[    0.093694] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.094818] PCI : PCI BIOS area is rw and x. Use pci=nobios if you want it NX.
[    0.094839] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=2
[    0.094842] PCI: Using configuration type 1 for base access
[    0.096664] bio: create slab <bio-0> at 0
[    0.096923] ACPI: Added _OSI(Module Device)
[    0.096926] ACPI: Added _OSI(Processor Device)
[    0.096928] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.096930] ACPI: Added _OSI(Processor Aggregator Device)
[    0.098872] ACPI: Executed 1 blocks of module-level executable AML code
[    0.099223] ACPI: Actual Package length (266) is larger than NumElements field (2), truncated
[    0.100919] ACPI: Interpreter enabled
[    0.100943] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)
[    0.100963] ACPI: (supports S0 S1 S3 S4 S5)
[    0.100966] ACPI: Using IOAPIC for interrupt routing
[    0.101008] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.101148] ACPI: No dock devices found.
[    0.106500] ACPI: Power Resource [ISAV] (on)
[    0.109803] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.109815] acpi PNP0A03:00: _OSC: OS supports [ASPM ClockPM Segments MSI]
[    0.109822] acpi PNP0A03:00: _OSC failed (AE_NOT_FOUND); disabling ASPM
[    0.109942] acpi PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.109946] acpi PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.109950] acpi PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.109953] acpi PNP0A03:00: host bridge window [mem 0x80000000-0xff7bffff] (ignored)
[    0.109957] PCI: root bus 00: hardware-probed resources
[    0.109965] acpi PNP0A03:00: fail to add MMCONFIG information, can't access extended PCI configuration space under this bridge.
[    0.110126] PCI host bridge to bus 0000:00
[    0.110131] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.110135] pci_bus 0000:00: root bus resource [io  0x0000-0xffff]
[    0.110139] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.110142] pci_bus 0000:00: root bus resource [mem 0x80000000-0xfcffffffff]
[    0.110164] pci 0000:00:00.0: [10de:00e1] type 00 class 0x060000
[    0.110177] pci 0000:00:00.0: reg 0x10: [mem 0xf0000000-0xf7ffffff pref]
[    0.110301] pci 0000:00:01.0: [10de:00e0] type 00 class 0x060100
[    0.110388] pci 0000:00:01.1: [10de:00e4] type 00 class 0x0c0500
[    0.110397] pci 0000:00:01.1: reg 0x10: [io  0x5080-0x509f]
[    0.110411] pci 0000:00:01.1: reg 0x20: [io  0x5000-0x503f]
[    0.110417] pci 0000:00:01.1: reg 0x24: [io  0x5040-0x507f]
[    0.110434] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.110515] pci 0000:00:02.0: [10de:00e7] type 00 class 0x0c0310
[    0.110524] pci 0000:00:02.0: reg 0x10: [mem 0xfebfd000-0xfebfdfff]
[    0.110552] pci 0000:00:02.0: supports D1 D2
[    0.110556] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.110600] pci 0000:00:02.0: System wakeup disabled by ACPI
[    0.110650] pci 0000:00:02.1: [10de:00e7] type 00 class 0x0c0310
[    0.110659] pci 0000:00:02.1: reg 0x10: [mem 0xfebfe000-0xfebfefff]
[    0.110687] pci 0000:00:02.1: supports D1 D2
[    0.110690] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.110725] pci 0000:00:02.1: System wakeup disabled by ACPI
[    0.110767] pci 0000:00:02.2: [10de:00e8] type 00 class 0x0c0320
[    0.110778] pci 0000:00:02.2: reg 0x10: [mem 0xfebffc00-0xfebffcff]
[    0.110812] pci 0000:00:02.2: supports D1 D2
[    0.110815] pci 0000:00:02.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.110868] pci 0000:00:02.2: System wakeup disabled by ACPI
[    0.110922] pci 0000:00:05.0: [10de:00df] type 00 class 0x068000
[    0.110932] pci 0000:00:05.0: reg 0x10: [mem 0xfebfc000-0xfebfcfff]
[    0.110938] pci 0000:00:05.0: reg 0x14: [io  0xec00-0xec07]
[    0.110963] pci 0000:00:05.0: supports D1 D2
[    0.110967] pci 0000:00:05.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.111001] pci 0000:00:05.0: System wakeup disabled by ACPI
[    0.111049] pci 0000:00:06.0: [10de:00ea] type 00 class 0x040100
[    0.111058] pci 0000:00:06.0: reg 0x10: [io  0xe800-0xe8ff]
[    0.111064] pci 0000:00:06.0: reg 0x14: [io  0xe400-0xe47f]
[    0.111070] pci 0000:00:06.0: reg 0x18: [mem 0xfebfb000-0xfebfbfff]
[    0.111093] pci 0000:00:06.0: supports D1 D2
[    0.111157] pci 0000:00:08.0: [10de:00e5] type 00 class 0x01018a
[    0.111176] pci 0000:00:08.0: reg 0x20: [io  0xffa0-0xffaf]
[    0.111263] pci 0000:00:0a.0: [10de:00e3] type 00 class 0x010185
[    0.111273] pci 0000:00:0a.0: reg 0x10: [io  0x09f0-0x09f7]
[    0.111279] pci 0000:00:0a.0: reg 0x14: [io  0x0bf0-0x0bf3]
[    0.111285] pci 0000:00:0a.0: reg 0x18: [io  0x0970-0x0977]
[    0.111290] pci 0000:00:0a.0: reg 0x1c: [io  0x0b70-0x0b73]
[    0.111296] pci 0000:00:0a.0: reg 0x20: [io  0xc800-0xc80f]
[    0.111302] pci 0000:00:0a.0: reg 0x24: [io  0xc400-0xc47f]
[    0.111378] pci 0000:00:0b.0: [10de:00e2] type 01 class 0x060400
[    0.111468] pci 0000:00:0e.0: [10de:00ed] type 01 class 0x060400
[    0.111512] pci 0000:00:0e.0: System wakeup disabled by ACPI
[    0.111560] pci 0000:00:18.0: [1022:1100] type 00 class 0x060000
[    0.111645] pci 0000:00:18.1: [1022:1101] type 00 class 0x060000
[    0.111714] pci 0000:00:18.2: [1022:1102] type 00 class 0x060000
[    0.111790] pci 0000:00:18.3: [1022:1103] type 00 class 0x060000
[    0.111905] pci 0000:01:00.0: [10de:02e1] type 00 class 0x030000
[    0.111925] pci 0000:01:00.0: reg 0x10: [mem 0xfd000000-0xfdffffff]
[    0.111937] pci 0000:01:00.0: reg 0x14: [mem 0xd0000000-0xdfffffff pref]
[    0.111948] pci 0000:01:00.0: reg 0x18: [mem 0xfc000000-0xfcffffff]
[    0.111982] pci 0000:01:00.0: reg 0x30: [mem 0xfe9e0000-0xfe9fffff pref]
[    0.112081] pci 0000:00:0b.0: PCI bridge to [bus 01]
[    0.112088] pci 0000:00:0b.0:   bridge window [mem 0xfa900000-0xfe9fffff]
[    0.112093] pci 0000:00:0b.0:   bridge window [mem 0xca800000-0xea7fffff pref]
[    0.112136] pci 0000:02:07.0: [1814:0301] type 00 class 0x028000
[    0.112150] pci 0000:02:07.0: reg 0x10: [mem 0xfeaf8000-0xfeafffff]
[    0.112254] pci 0000:00:0e.0: PCI bridge to [bus 02]
[    0.112259] pci 0000:00:0e.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.112268] pci_bus 0000:00: on NUMA node 0
[    0.113153] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *0, disabled.
[    0.113254] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *11
[    0.113352] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *0, disabled.
[    0.113450] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *0, disabled.
[    0.113548] ACPI: PCI Interrupt Link [LNKE] (IRQs 16 17 18 19) *11
[    0.113653] ACPI: PCI Interrupt Link [LUS0] (IRQs 20 21 22) *3
[    0.113752] ACPI: PCI Interrupt Link [LUS1] (IRQs 20 21 22) *9
[    0.113846] ACPI: PCI Interrupt Link [LUS2] (IRQs 20 21 22) *10
[    0.113939] ACPI: PCI Interrupt Link [LKLN] (IRQs 20 21 22) *9
[    0.114033] ACPI: PCI Interrupt Link [LAUI] (IRQs 20 21 22) *10
[    0.114127] ACPI: PCI Interrupt Link [LKMO] (IRQs 20 21 22) *0, disabled.
[    0.114221] ACPI: PCI Interrupt Link [LKSM] (IRQs 20 21 22) *0, disabled.
[    0.114315] ACPI: PCI Interrupt Link [LTID] (IRQs 20 21 22) *0
[    0.114418] ACPI: PCI Interrupt Link [LTIE] (IRQs 20 21 22) *0, disabled.
[    0.114532] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22) *14
[    0.114625] ACPI: \_SB_.PCI0: notify handler is installed
[    0.114663] Found 1 acpi root devices
[    0.114907] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.114910] vgaarb: loaded
[    0.114912] vgaarb: bridge control possible 0000:01:00.0
[    0.115343] SCSI subsystem initialized
[    0.115482] libata version 3.00 loaded.
[    0.115524] ACPI: bus type USB registered
[    0.115580] usbcore: registered new interface driver usbfs
[    0.115596] usbcore: registered new interface driver hub
[    0.115635] usbcore: registered new device driver usb
[    0.115847] PCI: Using ACPI for IRQ routing
[    0.115854] PCI: pci_cache_line_size set to 64 bytes
[    0.115897] e820: reserve RAM buffer [mem 0x0009fc00-0x0009ffff]
[    0.115902] e820: reserve RAM buffer [mem 0x7ffc0000-0x7fffffff]
[    0.116096] NetLabel: Initializing
[    0.116098] NetLabel:  domain hash size = 128
[    0.116100] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.116128] NetLabel:  unlabeled traffic allowed by default
[    0.116310] Switched to clocksource refined-jiffies
[    0.128905] AppArmor: AppArmor Filesystem Enabled
[    0.128994] pnp: PnP ACPI init
[    0.129025] ACPI: bus type PNP registered
[    0.129124] pnp 00:00: [dma 4]
[    0.129171] pnp 00:00: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.129240] pnp 00:01: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.129277] pnp 00:02: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.129315] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.129729] pnp 00:04: [dma 2]
[    0.129806] pnp 00:04: Plug and Play ACPI device, IDs PNP0700 (active)
[    0.130087] pnp 00:05: [dma 3]
[    0.130251] pnp 00:05: Plug and Play ACPI device, IDs PNP0401 (active)
[    0.130543] pnp 00:06: Plug and Play ACPI device, IDs PNPb006 (active)
[    0.130812] system 00:07: [io  0x0190-0x0193] has been reserved
[    0.130817] system 00:07: [io  0x04d0-0x04d1] has been reserved
[    0.130822] system 00:07: [io  0x4000-0x40ff window] has been reserved
[    0.130826] system 00:07: [io  0x4400-0x44ff window] has been reserved
[    0.130830] system 00:07: [io  0x4800-0x48ff window] has been reserved
[    0.130836] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.130948] system 00:08: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.130953] system 00:08: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.130957] system 00:08: [mem 0xff780000-0xff7bffff] has been reserved
[    0.130961] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.131029] pnp 00:09: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.131203] system 00:0a: [io  0x0480-0x0487] has been reserved
[    0.131208] system 00:0a: [io  0x0d00-0x0d07] has been reserved
[    0.131212] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.131460] pnp 00:0b: Plug and Play ACPI device, IDs PNPb02f (active)
[    0.131738] pnp 00:0c: [dma 0 disabled]
[    0.131811] pnp 00:0c: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.132071] system 00:0d: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.132076] system 00:0d: [mem 0x000c0000-0x000dffff] could not be reserved
[    0.132080] system 00:0d: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.132084] system 00:0d: [mem 0x00100000-0x7fffffff] could not be reserved
[    0.132089] system 00:0d: [mem 0xff7c0000-0xffffffff] has been reserved
[    0.132093] system 00:0d: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.132374] pnp: PnP ACPI: found 14 devices
[    0.132376] ACPI: bus type PNP unregistered
[    0.132381] PnPBIOS: Disabled by ACPI PNP
[    0.169252] Switched to clocksource acpi_pm
[    0.169284] pci 0000:00:0b.0: PCI bridge to [bus 01]
[    0.169294] pci 0000:00:0b.0:   bridge window [mem 0xfa900000-0xfe9fffff]
[    0.169299] pci 0000:00:0b.0:   bridge window [mem 0xca800000-0xea7fffff pref]
[    0.169306] pci 0000:00:0e.0: PCI bridge to [bus 02]
[    0.169311] pci 0000:00:0e.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.169318] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
[    0.169321] pci_bus 0000:00: resource 5 [mem 0x000a0000-0x000bffff]
[    0.169325] pci_bus 0000:00: resource 6 [mem 0x80000000-0xfcffffffff]
[    0.169329] pci_bus 0000:01: resource 1 [mem 0xfa900000-0xfe9fffff]
[    0.169332] pci_bus 0000:01: resource 2 [mem 0xca800000-0xea7fffff pref]
[    0.169336] pci_bus 0000:02: resource 1 [mem 0xfea00000-0xfeafffff]
[    0.169408] NET: Registered protocol family 2
[    0.169769] TCP established hash table entries: 8192 (order: 3, 32768 bytes)
[    0.170002] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.170148] TCP: Hash tables configured (established 8192 bind 8192)
[    0.170302] TCP: reno registered
[    0.170306] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.170344] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.170470] NET: Registered protocol family 1
[    0.170811] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 22
[    0.252244] ACPI: PCI Interrupt Link [LUS1] enabled at IRQ 21
[    0.324245] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 20
[    0.324357] pci 0000:01:00.0: Boot video device
[    0.324364] PCI: CLS 32 bytes, default 64
[    0.324487] Trying to unpack rootfs image as initramfs...
[    0.922659] Freeing initrd memory: 18176K (f5c70000 - f6e30000)
[    0.922995] microcode: AMD CPU family 0xf not supported
[    0.922999] Scanning for low memory corruption every 60 seconds
[    0.923554] Initialise system trusted keyring
[    0.923647] audit: initializing netlink socket (disabled)
[    0.923680] type=2000 audit(1400150117.919:1): initialized
[    0.955851] bounce pool size: 64 pages
[    0.955871] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.957830] VFS: Disk quotas dquot_6.5.2
[    0.957905] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.958625] fuse init (API version 7.22)
[    0.958733] msgmni has been set to 1718
[    0.958849] Key type big_key registered
[    0.959286] Key type asymmetric registered
[    0.959290] Asymmetric key parser 'x509' registered
[    0.959343] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.959386] io scheduler noop registered
[    0.959389] io scheduler deadline registered (default)
[    0.959430] io scheduler cfq registered
[    0.959664] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.959692] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.959784] ipmi message handler version 39.2
[    0.959929] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.959941] ACPI: Power Button [PWRB]
[    0.960072] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.960075] ACPI: Power Button [PWRF]
[    0.960228] GHES: HEST is not enabled!
[    0.960405] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.980849] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
[    0.980908] isapnp: Scanning for PnP cards...
[    1.075203] Linux agpgart interface v0.103
[    1.075241] agpgart-amd64 0000:00:00.0: AGP bridge [10de/00e1]
[    1.075249] agpgart-amd64 0000:00:00.0: aperture size 4096 MB is not right, using settings from NB
[    1.075257] agpgart-amd64 0000:00:00.0: setting up Nforce3 AGP
[    1.125748] agpgart-amd64 0000:00:00.0: AGP aperture is 128M @ 0xf0000000
[    1.127625] brd: module loaded
[    1.128590] loop: module loaded
[    1.129372] libphy: Fixed MDIO Bus: probed
[    1.129555] tun: Universal TUN/TAP device driver, 1.6
[    1.129557] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.129617] PPP generic driver version 2.4.2
[    1.129681] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.129687] ehci-pci: EHCI PCI platform driver
[    1.129914] ehci-pci 0000:00:02.2: EHCI Host Controller
[    1.129926] ehci-pci 0000:00:02.2: new USB bus registered, assigned bus number 1
[    1.129942] ehci-pci 0000:00:02.2: debug port 1
[    1.130004] ehci-pci 0000:00:02.2: cache line size of 32 is not supported
[    1.130042] ehci-pci 0000:00:02.2: irq 20, io mem 0xfebffc00
[    1.173604] ehci-pci 0000:00:02.2: USB 2.0 started, EHCI 1.00
[    1.173720] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.173724] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.173728] usb usb1: Product: EHCI Host Controller
[    1.173731] usb usb1: Manufacturer: Linux 3.13.0-24-generic ehci_hcd
[    1.173734] usb usb1: SerialNumber: 0000:00:02.2
[    1.173895] hub 1-0:1.0: USB hub found
[    1.173910] hub 1-0:1.0: 8 ports detected
[    1.174194] ehci-platform: EHCI generic platform driver
[    1.174210] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.174212] ohci-pci: OHCI PCI platform driver
[    1.174298] ohci-pci 0000:00:02.0: OHCI PCI host controller
[    1.174306] ohci-pci 0000:00:02.0: new USB bus registered, assigned bus number 2
[    1.174342] ohci-pci 0000:00:02.0: irq 22, io mem 0xfebfd000
[    1.263320] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    1.263324] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.263327] usb usb2: Product: OHCI PCI host controller
[    1.263330] usb usb2: Manufacturer: Linux 3.13.0-24-generic ohci_hcd
[    1.263334] usb usb2: SerialNumber: 0000:00:02.0
[    1.263452] hub 2-0:1.0: USB hub found
[    1.263462] hub 2-0:1.0: 4 ports detected
[    1.263660] ohci-pci 0000:00:02.1: OHCI PCI host controller
[    1.263667] ohci-pci 0000:00:02.1: new USB bus registered, assigned bus number 3
[    1.263705] ohci-pci 0000:00:02.1: irq 21, io mem 0xfebfe000
[    1.350699] isapnp: No Plug & Play device found
[    1.352766] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    1.352769] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.352773] usb usb3: Product: OHCI PCI host controller
[    1.352776] usb usb3: Manufacturer: Linux 3.13.0-24-generic ohci_hcd
[    1.352779] usb usb3: SerialNumber: 0000:00:02.1
[    1.352902] hub 3-0:1.0: USB hub found
[    1.352911] hub 3-0:1.0: 4 ports detected
[    1.353045] ohci-platform: OHCI generic platform driver
[    1.353067] uhci_hcd: USB Universal Host Controller Interface driver
[    1.353189] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    1.353192] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    1.354043] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.354177] mousedev: PS/2 mouse device common for all mice
[    1.354370] rtc_cmos 00:01: RTC can wake from S4
[    1.354528] rtc_cmos 00:01: rtc core: registered rtc_cmos as rtc0
[    1.354556] rtc_cmos 00:01: alarms up to one year, y3k, 114 bytes nvram
[    1.354664] device-mapper: uevent: version 1.0.3
[    1.354744] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
[    1.354768] platform eisa.0: Probing EISA bus 0
[    1.354775] platform eisa.0: EISA: Cannot allocate resource for mainboard
[    1.354779] platform eisa.0: Cannot allocate resource for EISA slot 1
[    1.354783] platform eisa.0: Cannot allocate resource for EISA slot 2
[    1.354786] platform eisa.0: Cannot allocate resource for EISA slot 3
[    1.354790] platform eisa.0: Cannot allocate resource for EISA slot 4
[    1.354793] platform eisa.0: Cannot allocate resource for EISA slot 5
[    1.354797] platform eisa.0: Cannot allocate resource for EISA slot 6
[    1.354801] platform eisa.0: Cannot allocate resource for EISA slot 7
[    1.354804] platform eisa.0: Cannot allocate resource for EISA slot 8
[    1.354808] platform eisa.0: EISA: Detected 0 cards
[    1.354821] cpufreq-nforce2: No nForce2 chipset.
[    1.354827] ledtrig-cpu: registered to indicate activity on CPUs
[    1.355058] TCP: cubic registered
[    1.355220] NET: Registered protocol family 10
[    1.355565] NET: Registered protocol family 17
[    1.355586] Key type dns_resolver registered
[    1.355761] Using IPI No-Shortcut mode
[    1.355867] Loading compiled-in X.509 certificates
[    1.360828] Loaded X.509 cert 'Magrathea: Glacier signing key: 5682f337b8a0a17eef58c6ac5e9a85712c9208df'
[    1.360874] registered taskstats version 1
[    1.365422] Key type trusted registered
[    1.369065] Key type encrypted registered
[    1.372806] AppArmor: AppArmor sha1 policy hashing enabled
[    1.372817] IMA: No TPM chip found, activating TPM-bypass!
[    1.373083] regulator-dummy: disabling
[    1.373149]   Magic number: 14:209:578
[    1.373225] platform pcspkr: hash matches
[    1.373343] rtc_cmos 00:01: setting system clock to 2014-05-15 10:35:19 UTC (1400150119)
[    1.373551] powernow-k8: fid 0xa (1800 MHz), vid 0x2
[    1.373554] powernow-k8: fid 0x2 (1000 MHz), vid 0x12
[    1.373601] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 2800+ (1 cpu cores) (version 2.20.00)
[    1.373613] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.373615] EDD information not available.
[    1.373664] PM: Hibernation image not present or could not be loaded.
[    1.375168] Freeing unused kernel memory: 872K (c19ae000 - c1a88000)
[    1.375243] Write protecting the kernel text: 6512k
[    1.375329] Write protecting the kernel read-only data: 2756k
[    1.375331] NX-protecting the kernel data: 5776k
[    1.382437] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    1.404430] systemd-udevd[88]: starting version 204
[    1.509046] pata_amd 0000:00:08.0: version 0.4.1
[    1.517154] scsi0 : pata_amd
[    1.518371] Floppy drive(s): fd0 is 1.44M
[    1.520229] scsi1 : pata_amd
[    1.520313] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    1.520317] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    1.525251] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.525581] ACPI: PCI Interrupt Link [LKLN] enabled at IRQ 22
[    1.535928] FDC 0 is a post-1991 82077
[    1.684599] ata1.00: ATAPI: SONY CDU4811, PY0A, max UDMA/33, CDB intr
[    1.684613] ata1.01: ATAPI: ASUS    DRW-1814BL, 1.10, max UDMA/66
[    1.684626] ata1: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc0c50000) ACPI=0x701f (60:30:0x1f)
[    1.684632] ata1: nv_mode_filter: 0x1f39f&0x1f39f->0x1f39f, BIOS=0x1f000 (0xc0c50000) ACPI=0x1f01f (60:30:0x1f)
[    1.692313] ata1.00: configured for UDMA/33
[    1.708187] ata1.01: configured for UDMA/66
[    1.709311] scsi 0:0:0:0: CD-ROM            SONY     CDU4811          PY0A PQ: 0 ANSI: 5
[    1.710750] sr0: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
[    1.710755] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.710917] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.711136] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.711735] scsi 0:0:1:0: CD-ROM            ASUS     DRW-1814BL       1.10 PQ: 0 ANSI: 5
[    1.714119] sr1: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.714263] sr 0:0:1:0: Attached scsi CD-ROM sr1
[    1.714349] sr 0:0:1:0: Attached scsi generic sg1 type 5
[    1.920038] tsc: Refined TSC clocksource calibration: 1808.801 MHz
[    1.940039] usb 3-1: new low-speed USB device number 2 using ohci-pci
[    2.048614] forcedeth 0000:00:05.0: ifname eth0, PHY OUI 0x90c3 @ 1, addr 00:11:d8:65:ba:39
[    2.048619] forcedeth 0000:00:05.0: csum timirq lnktim desc-v2
[    2.048961] sata_nv 0000:00:0a.0: version 3.5
[    2.049297] ACPI: PCI Interrupt Link [LTID] BIOS reported IRQ 0, using IRQ 21
[    2.049300] ACPI: PCI Interrupt Link [LTID] enabled at IRQ 21
[    2.051292] scsi2 : sata_nv
[    2.051468] scsi3 : sata_nv
[    2.051527] ata3: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xc800 irq 21
[    2.051531] ata4: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xc808 irq 21
[    2.154740] usb 3-1: New USB device found, idVendor=045e, idProduct=0083
[    2.154750] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.154753] usb 3-1: Product: Basic Optical Mouse
[    2.154757] usb 3-1: Manufacturer: Microsoft
[    2.170497] hidraw: raw HID events driver (C) Jiri Kosina
[    2.185632] usbcore: registered new interface driver usbhid
[    2.185641] usbhid: USB HID core driver
[    2.193090] input: Microsoft Basic Optical Mouse as /devices/pci0000:00/0000:00:02.1/usb3/3-1/3-1:1.0/input/input3
[    2.194245] hid-generic 0003:045E:0083.0001: input,hidraw0: USB HID v1.10 Mouse [Microsoft Basic Optical Mouse] on usb-0000:00:02.1-1/input0
[    2.520045] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.556290] ata3.00: ATA-7: ST3160812AS, 2AAA, max UDMA/133
[    2.556295] ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.631239] ata3.00: configured for UDMA/133
[    2.631467] scsi 2:0:0:0: Direct-Access     ATA      ST3160812AS      2AAA PQ: 0 ANSI: 5
[    2.631763] sd 2:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    2.631839] sd 2:0:0:0: [sda] Write Protect is off
[    2.631844] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.631876] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.632323] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    2.705395]  sda: sda1 sda2 < sda5 sda6 > sda3
[    2.705937] sd 2:0:0:0: [sda] Attached SCSI disk
[    2.920118] Switched to clocksource tsc
[    2.944026] ata4: SATA link down (SStatus 0 SControl 300)
[    3.569114] EXT4-fs (sda3): INFO: recovery required on readonly filesystem
[    3.569124] EXT4-fs (sda3): write access will be enabled during recovery
[    8.284662] EXT4-fs (sda3): orphan cleanup on readonly fs
[    8.285147] EXT4-fs (sda3): 9 orphan inodes deleted
[    8.285150] EXT4-fs (sda3): recovery complete
[    8.316392] random: nonblocking pool is initialized
[    8.345419] EXT4-fs (sda3): mounted filesystem with ordered data mode. Opts: (null)
[   18.979003] Adding 4101556k swap on /dev/sda6.  Priority:-1 extents:1 across:4101556k FS
[   19.157012] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.511075] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro
[   19.582949] systemd-udevd[275]: starting version 204
[   19.882722] lp: driver loaded but no devices found
[   19.926869] ppdev: user-space parallel port driver
[   19.963379] parport_pc 00:05: reported by Plug and Play ACPI
[   19.963452] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   20.064469] lp0: using parport0 (interrupt-driven).
[   20.576093] gameport gameport0: NS558 PnP Gameport is pnp00:0b/gameport0, io 0x200, speed 903kHz
[   20.674823] ACPI Warning: 0x00005000-0x0000503f SystemIO conflicts with Region \_SB_.PCI0.SMBS.SMRG 1 (20131115/utaddress-251)
[   20.674844] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   20.675402] i2c i2c-0: nForce2 SMBus adapter at 0x5040
[   21.282223] Bluetooth: Core ver 2.17
[   21.285414] NET: Registered protocol family 31
[   21.285424] Bluetooth: HCI device and connection manager initialized
[   21.285447] Bluetooth: HCI socket layer initialized
[   21.285452] Bluetooth: L2CAP socket layer initialized
[   21.285476] Bluetooth: SCO socket layer initialized
[   21.343068] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   21.343078] Bluetooth: BNEP filters: protocol multicast
[   21.343099] Bluetooth: BNEP socket layer initialized
[   21.383355] Bluetooth: RFCOMM TTY layer initialized
[   21.383386] Bluetooth: RFCOMM socket layer initialized
[   21.383399] Bluetooth: RFCOMM ver 1.11
[   21.538186] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   21.551366] type=1400 audit(1400106939.670:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=465 comm="apparmor_parser"
[   21.551386] type=1400 audit(1400106939.670:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=465 comm="apparmor_parser"
[   21.554286] type=1400 audit(1400106939.674:4): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=465 comm="apparmor_parser"
[   21.727817] type=1400 audit(1400106939.846:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=480 comm="apparmor_parser"
[   21.727840] type=1400 audit(1400106939.846:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=480 comm="apparmor_parser"
[   21.727847] type=1400 audit(1400106939.846:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=480 comm="apparmor_parser"
[   21.742210] type=1400 audit(1400106939.862:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=480 comm="apparmor_parser"
[   21.742234] type=1400 audit(1400106939.862:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=480 comm="apparmor_parser"
[   21.742658] type=1400 audit(1400106939.862:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=480 comm="apparmor_parser"
[   21.950651] init: cups main process (471) killed by HUP signal
[   21.950675] init: cups main process ended, respawning
[   21.952266] ip_tables: (C) 2000-2006 Netfilter Core Team
[   22.070951] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   22.247257] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   22.505539] cfg80211: Calling CRDA to update world regulatory domain
[   22.506298] ACPI: PCI Interrupt Link [LAUI] enabled at IRQ 20
[   22.919372] nvidia: module license 'NVIDIA' taints kernel.
[   22.919385] Disabling lock debugging due to kernel taint
[   23.018721] intel8x0_measure_ac97_clock: measured 110762 usecs (5376 samples)
[   23.018733] intel8x0: clocking to 47469
[   23.258461] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 19
[   23.283360] ieee80211 phy0: rt2x00_set_chip: Info - Chipset detected - rt: 2561, rf: 0003, rev: 000c
[   23.342382] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   23.449292] nvidia: module verification failed: signature and/or  required key missing - tainting kernel
[   23.687810] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 18
[   23.687879] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=none
[   23.767905] NVRM: loading NVIDIA UNIX x86 Kernel Module  304.117  Tue Nov 26 21:36:39 PST 2013
[   24.145704] init: failsafe main process (620) killed by TERM signal
[   24.687167] cfg80211: World regulatory domain updated:
[   24.687181] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   24.687185] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.687188] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.687190] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   24.687193] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.687195] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   25.393985] type=1400 audit(1400106943.514:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=786 comm="apparmor_parser"
[   25.573144] forcedeth 0000:00:05.0 eth0: no link during initialization
[   25.577828] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   25.581252] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   25.617435] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2561s.bin'
[   25.642123] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.8
[   25.680185] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   25.680806] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   25.852297] init: udev-fallback-graphics main process (796) terminated with status 1
[   27.978270] wlan0: authenticate with 98:fc:11:9d:64:93
[   27.992211] wlan0: send auth to 98:fc:11:9d:64:93 (try 1/3)
[   27.993784] wlan0: authenticated
[   27.996362] wlan0: associate with 98:fc:11:9d:64:93 (try 1/3)
[   27.999466] wlan0: RX AssocResp from 98:fc:11:9d:64:93 (capab=0x411 status=0 aid=3)
[   27.999779] wlan0: associated
[   28.000261] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   28.282003] wlan0: deauthenticating from 98:fc:11:9d:64:93 by local choice (reason=2)
[   28.296433] wlan0: authenticate with 98:fc:11:9d:64:93
[   28.296568] wlan0: send auth to 98:fc:11:9d:64:93 (try 1/3)
[   28.298166] wlan0: authenticated
[   28.298920] cfg80211: Calling CRDA to update world regulatory domain
[   28.304113] wlan0: associate with 98:fc:11:9d:64:93 (try 1/3)
[   28.306653] wlan0: RX AssocResp from 98:fc:11:9d:64:93 (capab=0x411 status=0 aid=3)
[   28.306961] wlan0: associated
[   28.319282] cfg80211: World regulatory domain updated:
[   28.319294] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   28.319297] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   28.319300] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   28.319303] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   28.319305] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   28.319308] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)

```

---

