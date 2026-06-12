---
title: "Computer hangs, video related issue"
date: 2019-06-06
forum: General Help
---

### Post by xavilai on 2019-06-06
Hi community! 

Recently installed ubuntu on a desktop PC and noticed a message at boot time:

No irq handler for vector

I've followed directions on this [thread]("https://ubuntuforums.org/showthread.php?t=1234983") without any luck 

The problem is very random, say 1 / 5 times it will freeze after launching the browser or playing a movie, on a screen as the following:

Any help would be highly appreciated!

hints, asrock motherboard, integrated graphics

[IMG]https://i.imgur.com/Ev6le3z.jpg[/IMG]


Hi community!

Recently installed ubuntu on a desktop PC and noticed a message at boot time:

No irq handler for vector

I've followed directions on this thread without any luck

The problem is very random, say 1 / 5 times it will freeze after launching the browser or playing a movie, on a screen as the following:

Any help would be highly appreciated!

hints, asrock motherboard, integrated graphics






A lightdm service restart sometimes fixes the issue temporary.


dmesg output:

[    0.000000] Linux version 4.15.0-51-generic (buildd@lgw01-amd64-059) (gcc version 7.3.0 (Ubuntu 7.3.0-16ubuntu3)) #55-Ubuntu SMP Wed May 15 14:27:21 UTC 2019 (Ubuntu 4.15.0-51.55-generic 4.15.18)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.15.0-51-generic root=UUID=59c62809-784f-4409-b7c2-c1171d3e9e44 ro quiet splash pci=nomsi,noaer
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] x86/fpu: x87 FPU will use FXSAVE
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009f7ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009f800-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e4000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000bff9ffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bffa0000-0x00000000bffaffff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000bffb0000-0x00000000bffdffff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bffe0000-0x00000000bfffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000feefffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fff00000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x00000001afffffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.6 present.
[    0.000000] DMI: To Be Filled By O.E.M. To Be Filled By O.E.M./N68-VS3 FX, BIOS P1.80 10/31/2012
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] AGP: No AGP bridge found
[    0.000000] e820: last_pfn = 0x1b0000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
[    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 00000001b0000000 aka 6912M
[    0.000000] x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WP  UC- WT  
[    0.000000] e820: update [mem 0xc0000000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xbffa0 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000ff780-0x000ff78f] mapped at [        (ptrval)]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [        (ptrval)] 99000 size 24576
[    0.000000] Using GB pages for direct mapping
[    0.000000] BRK [0x1ab3f000, 0x1ab3ffff] PGTABLE
[    0.000000] BRK [0x1ab40000, 0x1ab40fff] PGTABLE
[    0.000000] BRK [0x1ab41000, 0x1ab41fff] PGTABLE
[    0.000000] BRK [0x1ab42000, 0x1ab42fff] PGTABLE
[    0.000000] BRK [0x1ab43000, 0x1ab43fff] PGTABLE
[    0.000000] RAMDISK: [mem 0x30c87000-0x3463afff]
[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x00000000000F9E10 000014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 0x00000000BFFA0000 00003C (v01 103112 RSDT1040 20121031 MSFT 00000097)
[    0.000000] ACPI: FACP 0x00000000BFFA0200 000084 (v01 A_M_I  OEMFACP  12000601 MSFT 00000097)
[    0.000000] ACPI: DSDT 0x00000000BFFA0470 004CAE (v01 AS569  AS569171 00000171 INTL 20051117)
[    0.000000] ACPI: FACS 0x00000000BFFB0000 000040
[    0.000000] ACPI: APIC 0x00000000BFFA0390 0000A0 (v01 103112 APIC1040 20121031 MSFT 00000097)
[    0.000000] ACPI: MCFG 0x00000000BFFA0430 00003C (v01 103112 OEMMCFG  20121031 MSFT 00000097)
[    0.000000] ACPI: OEMB 0x00000000BFFB0040 000072 (v01 103112 OEMB1040 20121031 MSFT 00000097)
[    0.000000] ACPI: AAFT 0x00000000BFFAA470 000027 (v01 103112 OEMAAFT  20121031 MSFT 00000097)
[    0.000000] ACPI: SSDT 0x00000000BFFAA4A0 000470 (v01 A M I  POWERNOW 00000001 AMD  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x00000001afffffff]
[    0.000000] NODE_DATA(0) allocated [mem 0x1affd3000-0x1afffdfff]
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x0000000000001000-0x0000000000ffffff]
[    0.000000]   DMA32    [mem 0x0000000001000000-0x00000000ffffffff]
[    0.000000]   Normal   [mem 0x0000000100000000-0x00000001afffffff]
[    0.000000]   Device   empty
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x0000000000001000-0x000000000009efff]
[    0.000000]   node   0: [mem 0x0000000000100000-0x00000000bff9ffff]
[    0.000000]   node   0: [mem 0x0000000100000000-0x00000001afffffff]
[    0.000000] Reserved but unavailable: 194 pages
[    0.000000] Initmem setup node 0 [mem 0x0000000000001000-0x00000001afffffff]
[    0.000000] On node 0 totalpages: 1507134
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3998 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 12223 pages used for memmap
[    0.000000]   DMA32 zone: 782240 pages, LIFO batch:31
[    0.000000]   Normal zone: 11264 pages used for memmap
[    0.000000]   Normal zone: 720896 pages, LIFO batch:31
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x508
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: BIOS IRQ0 override ignored.
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] smpboot: Allowing 8 CPUs, 6 hotplug CPUs
[    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000e3fff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e4000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xbffa0000-0xbffaffff]
[    0.000000] PM: Registered nosave memory: [mem 0xbffb0000-0xbffdffff]
[    0.000000] PM: Registered nosave memory: [mem 0xbffe0000-0xbfffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xc0000000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfedfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfeefffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfef00000-0xffefffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfff00000-0xffffffff]
[    0.000000] e820: [mem 0xc0000000-0xfebfffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] clocksource: refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645519600211568 ns
[    0.000000] random: get_random_bytes called from start_kernel+0x99/0x4fd with crng_init=0
[    0.000000] setup_percpu: NR_CPUS:8192 nr_cpumask_bits:8 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] percpu: Embedded 46 pages/cpu @        (ptrval) s151552 r8192 d28672 u262144
[    0.000000] pcpu-alloc: s151552 r8192 d28672 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists, mobility grouping on.  Total pages: 1483562
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.15.0-51-generic root=UUID=59c62809-784f-4409-b7c2-c1171d3e9e44 ro quiet splash pci=nomsi,noaer
[    0.000000] AGP: Checking aperture...
[    0.000000] AGP: No AGP bridge found
[    0.000000] AGP: Node 0: aperture [bus addr 0x00000000-0x01ffffff] (32MB)
[    0.000000] AGP: Your BIOS doesn't leave an aperture memory hole
[    0.000000] AGP: Please enable the IOMMU option in the BIOS setup
[    0.000000] AGP: This costs you 64MB of RAM
[    0.000000] AGP: Mapping aperture over RAM [mem 0xb4000000-0xb7ffffff] (65536KB)
[    0.000000] PM: Registered nosave memory: [mem 0xb4000000-0xb7ffffff]
[    0.000000] Memory: 5714008K/6028536K available (12300K kernel code, 2473K rwdata, 4272K rodata, 2408K init, 2416K bss, 314528K reserved, 0K cma-reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] ftrace: allocating 39215 entries in 154 pages
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU restricting CPUs from NR_CPUS=8192 to nr_cpu_ids=8.
[    0.000000]     Tasks RCU enabled.
[    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=16, nr_cpu_ids=8
[    0.000000] NR_IRQS: 524544, nr_irqs: 488, preallocated irqs: 16
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] ACPI: Core revision 20170831
[    0.000000] ACPI: 2 ACPI AML tables successfully acquired and loaded
[    0.000000] APIC: Switch to symmetric I/O mode setup
[    0.000000] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.000000] do_IRQ: 0.55 No irq handler for vector
[    0.020000] tsc: Fast TSC calibration using PIT
[    0.024000] tsc: Detected 3415.453 MHz processor
[    0.024000] Calibrating delay loop (skipped), value calculated using timer frequency.. 6830.90 BogoMIPS (lpj=13661812)
[    0.024000] pid_max: default: 32768 minimum: 301
[    0.024000] Security Framework initialized
[    0.024000] Yama: becoming mindful.
[    0.024000] AppArmor: AppArmor initialized
[    0.029175] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.030668] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.030734] Mount-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.030782] Mountpoint-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.031022] mce: CPU supports 6 MCE banks
[    0.031027] LVT offset 0 assigned for vector 0xf9
[    0.031031] Last level iTLB entries: 4KB 512, 2MB 16, 4MB 8
[    0.031032] Last level dTLB entries: 4KB 512, 2MB 128, 4MB 64, 1GB 0
[    0.031034] Spectre V2 : Mitigation: Full AMD retpoline
[    0.031034] Spectre V2 : Spectre v2 / SpectreRSB mitigation: Filling RSB on context switch
[    0.031151] Freeing SMP alternatives memory: 36K
[    0.036000] smpboot: CPU0: AMD Athlon(tm) II X2 270 Processor (family: 0x10, model: 0x6, stepping: 0x3)
[    0.036000] Performance Events: AMD PMU driver.
[    0.036000] ... version:                0
[    0.036000] ... bit width:              48
[    0.036000] ... generic registers:      4
[    0.036000] ... value mask:             0000ffffffffffff
[    0.036000] ... max period:             00007fffffffffff
[    0.036000] ... fixed-purpose events:   0
[    0.036000] ... event mask:             000000000000000f
[    0.036000] Hierarchical SRCU implementation.
[    0.036000] smp: Bringing up secondary CPUs ...
[    0.036000] x86: Booting SMP configuration:
[    0.036000] .... node  #0, CPUs:      #1
[    0.036000] NMI watchdog: Enabled. Permanently consumes one hw-PMU counter.
[    0.036000] smp: Brought up 1 node, 2 CPUs
[    0.036000] smpboot: Max logical packages: 4
[    0.036000] smpboot: Total of 2 processors activated (13661.81 BogoMIPS)
[    0.036000] devtmpfs: initialized
[    0.036000] x86/mm: Memory block size: 128MB
[    0.036000] evm: security.selinux
[    0.036000] evm: security.SMACK64
[    0.036000] evm: security.SMACK64EXEC
[    0.036000] evm: security.SMACK64TRANSMUTE
[    0.036000] evm: security.SMACK64MMAP
[    0.036000] evm: security.apparmor
[    0.036000] evm: security.ima
[    0.036000] evm: security.capability
[    0.036029] PM: Registering ACPI NVS region [mem 0xbffb0000-0xbffdffff] (196608 bytes)
[    0.036088] clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
[    0.036088] futex hash table entries: 2048 (order: 5, 131072 bytes)
[    0.036092] pinctrl core: initialized pinctrl subsystem
[    0.036190] RTC time: 23:32:26, date: 06/06/19
[    0.036296] NET: Registered protocol family 16
[    0.036369] audit: initializing netlink subsys (disabled)
[    0.036381] audit: type=2000 audit(1559863946.036:1): state=initialized audit_enabled=0 res=1
[    0.036381] cpuidle: using governor ladder
[    0.036381] cpuidle: using governor menu
[    0.036381] node 0 link 0: io port [1000, ffffff]
[    0.036381] TOM: 00000000d0000000 aka 3328M
[    0.036381] node 0 link 0: mmio [f0000000, f7ffffff]
[    0.036381] node 0 link 0: mmio [d0000000, efffffff]
[    0.036381] node 0 link 0: mmio [f8000000, fe0bffff]
[    0.036381] node 0 link 0: mmio [a0000, bffff]
[    0.036381] TOM2: 00000001b0000000 aka 6912M
[    0.036381] bus: [bus 00-1f] on node 0 link 0
[    0.036381] bus: 00 [io  0x0000-0xffff]
[    0.036381] bus: 00 [mem 0xd0000000-0xffffffff]
[    0.036381] bus: 00 [mem 0x000a0000-0x000bffff]
[    0.036381] bus: 00 [mem 0x1b0000000-0xfcffffffff]
[    0.036381] ACPI: bus type PCI registered
[    0.036381] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.036381] PCI: MMCONFIG for domain 0000 [bus 00-7f] at [mem 0xf0000000-0xf7ffffff] (base 0xf0000000)
[    0.036381] PCI: not using MMCONFIG
[    0.036381] PCI: Using configuration type 1 for base access
[    0.036381] PCI: Using configuration type 1 for extended access
[    0.036381] mtrr: your CPUs had inconsistent variable MTRR settings
[    0.036381] mtrr: probably your BIOS does not setup all CPUs.
[    0.036381] mtrr: corrected configuration.
[    0.037035] HugeTLB registered 1.00 GiB page size, pre-allocated 0 pages
[    0.037035] HugeTLB registered 2.00 MiB page size, pre-allocated 0 pages
[    0.037035] ACPI: Added _OSI(Module Device)
[    0.037035] ACPI: Added _OSI(Processor Device)
[    0.037035] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.037035] ACPI: Added _OSI(Processor Aggregator Device)
[    0.037035] ACPI: Added _OSI(Linux-Dell-Video)
[    0.037035] ACPI: Added _OSI(Linux-Lenovo-NV-HDMI-Audio)
[    0.037035] ACPI: Added _OSI(Linux-HPI-Hybrid-Graphics)
[    0.037035] ACPI: Executed 1 blocks of module-level executable AML code
[    0.042699] ACPI: Interpreter enabled
[    0.042718] ACPI: (supports S0 S1 S3 S4 S5)
[    0.042719] ACPI: Using IOAPIC for interrupt routing
[    0.042747] PCI: MMCONFIG for domain 0000 [bus 00-7f] at [mem 0xf0000000-0xf7ffffff] (base 0xf0000000)
[    0.043892] PCI: MMCONFIG at [mem 0xf0000000-0xf7ffffff] reserved in ACPI motherboard resources
[    0.043904] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.044210] ACPI: Enabled 10 GPEs in block 00 to 1F
[    0.054244] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.054248] acpi PNP0A03:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments]
[    0.054383] acpi PNP0A03:00: _OSC: not requesting OS control; OS requires [ExtendedConfig ASPM ClockPM MSI]
[    0.054393] acpi PNP0A03:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-7f] only partially covers this bridge
[    0.054616] PCI host bridge to bus 0000:00
[    0.054618] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7 window]
[    0.054619] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff window]
[    0.054620] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff window]
[    0.054622] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000dffff window]
[    0.054623] pci_bus 0000:00: root bus resource [mem 0xd0000000-0xefffffff window]
[    0.054624] pci_bus 0000:00: root bus resource [mem 0xf8000000-0xfebfffff window]
[    0.054625] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.054641] pci 0000:00:00.0: [10de:03e2] type 00 class 0x050000
[    0.054840] pci 0000:00:01.0: [10de:03e1] type 00 class 0x060100
[    0.054848] pci 0000:00:01.0: reg 0x10: [io  0x0900-0x09ff]
[    0.054922] pci 0000:00:01.1: [10de:03eb] type 00 class 0x0c0500
[    0.054932] pci 0000:00:01.1: reg 0x10: [io  0x0e00-0x0e3f]
[    0.054944] pci 0000:00:01.1: reg 0x20: [io  0x0600-0x063f]
[    0.054948] pci 0000:00:01.1: reg 0x24: [io  0x0700-0x073f]
[    0.054971] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.055028] pci 0000:00:01.2: [10de:03f5] type 00 class 0x050000
[    0.055100] pci 0000:00:02.0: [10de:03f1] type 00 class 0x0c0310
[    0.055108] pci 0000:00:02.0: reg 0x10: [mem 0xeffff000-0xefffffff]
[    0.055138] pci 0000:00:02.0: supports D1 D2
[    0.055139] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.055192] pci 0000:00:02.1: [10de:03f2] type 00 class 0x0c0320
[    0.055201] pci 0000:00:02.1: reg 0x10: [mem 0xefffec00-0xefffecff]
[    0.055235] pci 0000:00:02.1: supports D1 D2
[    0.055236] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.055299] pci 0000:00:04.0: [10de:03f3] type 01 class 0x060401
[    0.055375] pci 0000:00:05.0: [10de:03f0] type 00 class 0x040300
[    0.055384] pci 0000:00:05.0: reg 0x10: [mem 0xefff8000-0xefffbfff]
[    0.055418] pci 0000:00:05.0: PME# supported from D3hot D3cold
[    0.055477] pci 0000:00:06.0: [10de:03ec] type 00 class 0x01018a
[    0.055496] pci 0000:00:06.0: reg 0x20: [io  0xffa0-0xffaf]
[    0.055504] pci 0000:00:06.0: legacy IDE quirk: reg 0x10: [io  0x01f0-0x01f7]
[    0.055505] pci 0000:00:06.0: legacy IDE quirk: reg 0x14: [io  0x03f6]
[    0.055506] pci 0000:00:06.0: legacy IDE quirk: reg 0x18: [io  0x0170-0x0177]
[    0.055507] pci 0000:00:06.0: legacy IDE quirk: reg 0x1c: [io  0x0376]
[    0.055567] pci 0000:00:07.0: [10de:03ef] type 00 class 0x068000
[    0.055574] pci 0000:00:07.0: reg 0x10: [mem 0xefffd000-0xefffdfff]
[    0.055577] pci 0000:00:07.0: reg 0x14: [io  0xe080-0xe087]
[    0.055603] pci 0000:00:07.0: supports D1 D2
[    0.055604] pci 0000:00:07.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.055658] pci 0000:00:08.0: [10de:03f6] type 00 class 0x010185
[    0.055665] pci 0000:00:08.0: reg 0x10: [io  0xe000-0xe007]
[    0.055667] pci 0000:00:08.0: reg 0x14: [io  0xdc00-0xdc03]
[    0.055670] pci 0000:00:08.0: reg 0x18: [io  0xd880-0xd887]
[    0.055673] pci 0000:00:08.0: reg 0x1c: [io  0xd800-0xd803]
[    0.055676] pci 0000:00:08.0: reg 0x20: [io  0xd480-0xd48f]
[    0.055678] pci 0000:00:08.0: reg 0x24: [mem 0xefffc000-0xefffcfff]
[    0.055739] pci 0000:00:08.1: [10de:03f6] type 00 class 0x010185
[    0.055746] pci 0000:00:08.1: reg 0x10: [io  0xd400-0xd407]
[    0.055748] pci 0000:00:08.1: reg 0x14: [io  0xd080-0xd083]
[    0.055751] pci 0000:00:08.1: reg 0x18: [io  0xd000-0xd007]
[    0.055754] pci 0000:00:08.1: reg 0x1c: [io  0xcc00-0xcc03]
[    0.055757] pci 0000:00:08.1: reg 0x20: [io  0xc880-0xc88f]
[    0.055759] pci 0000:00:08.1: reg 0x24: [mem 0xefff7000-0xefff7fff]
[    0.055827] pci 0000:00:09.0: [10de:03e8] type 01 class 0x060400
[    0.055849] pci 0000:00:09.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.055909] pci 0000:00:0b.0: [10de:03e9] type 01 class 0x060400
[    0.055930] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.055986] pci 0000:00:0c.0: [10de:03e9] type 01 class 0x060400
[    0.056009] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.056064] pci 0000:00:0d.0: [10de:03d6] type 00 class 0x030000
[    0.056069] pci 0000:00:0d.0: reg 0x10: [mem 0xee000000-0xeeffffff]
[    0.056073] pci 0000:00:0d.0: reg 0x14: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.056076] pci 0000:00:0d.0: reg 0x1c: [mem 0xed000000-0xedffffff 64bit]
[    0.056080] pci 0000:00:0d.0: reg 0x30: [mem 0xeffc0000-0xeffdffff pref]
[    0.056147] pci 0000:00:18.0: [1022:1200] type 00 class 0x060000
[    0.056200] pci 0000:00:18.1: [1022:1201] type 00 class 0x060000
[    0.056250] pci 0000:00:18.2: [1022:1202] type 00 class 0x060000
[    0.056300] pci 0000:00:18.3: [1022:1203] type 00 class 0x060000
[    0.056353] pci 0000:00:18.4: [1022:1204] type 00 class 0x060000
[    0.056452] pci 0000:00:04.0: PCI bridge to [bus 01] (subtractive decode)
[    0.056456] pci 0000:00:04.0:   bridge window [io  0x0000-0x0cf7 window] (subtractive decode)
[    0.056457] pci 0000:00:04.0:   bridge window [io  0x0d00-0xffff window] (subtractive decode)
[    0.056458] pci 0000:00:04.0:   bridge window [mem 0x000a0000-0x000bffff window] (subtractive decode)
[    0.056459] pci 0000:00:04.0:   bridge window [mem 0x000d0000-0x000dffff window] (subtractive decode)
[    0.056460] pci 0000:00:04.0:   bridge window [mem 0xd0000000-0xefffffff window] (subtractive decode)
[    0.056461] pci 0000:00:04.0:   bridge window [mem 0xf8000000-0xfebfffff window] (subtractive decode)
[    0.056491] pci 0000:00:09.0: PCI bridge to [bus 02]
[    0.056521] pci 0000:00:0b.0: PCI bridge to [bus 03]
[    0.056543] pci 0000:00:0c.0: PCI bridge to [bus 04]
[    0.057366] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *0, disabled.
[    0.057500] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *0, disabled.
[    0.057633] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *0, disabled.
[    0.057765] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *0, disabled.
[    0.057897] ACPI: PCI Interrupt Link [LNEA] (IRQs 16 17 18 19) *0, disabled.
[    0.058030] ACPI: PCI Interrupt Link [LNEB] (IRQs 16 17 18 19) *0, disabled.
[    0.058162] ACPI: PCI Interrupt Link [LNEC] (IRQs 16 17 18 19) *0, disabled.
[    0.058295] ACPI: PCI Interrupt Link [LNED] (IRQs 16 17 18 19) *0, disabled.
[    0.058430] ACPI: PCI Interrupt Link [LUB0] (IRQs 20 21 22 23) *10
[    0.058566] ACPI: PCI Interrupt Link [LUB2] (IRQs 20 21 22 23) *11
[    0.058701] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *10
[    0.058836] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *10
[    0.058971] ACPI: PCI Interrupt Link [LMC9] (IRQs 20 21 22 23) *10
[    0.059107] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *11
[    0.059239] ACPI: PCI Interrupt Link [LPMU] (IRQs 20 21 22 23) *0, disabled.
[    0.059376] ACPI: PCI Interrupt Link [LSA0] (IRQs 20 21 22 23) *5
[    0.059511] ACPI: PCI Interrupt Link [LSA1] (IRQs 20 21 22 23) *5
[    0.059701] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.
[    0.059992] SCSI subsystem initialized
[    0.060060] libata version 3.00 loaded.
[    0.060060] pci 0000:00:0d.0: vgaarb: setting as boot VGA device
[    0.060060] pci 0000:00:0d.0: vgaarb: VGA device added: decodes=io+mem,owns=io+mem,locks=none
[    0.060060] pci 0000:00:0d.0: vgaarb: bridge control possible
[    0.060060] vgaarb: loaded
[    0.060060] ACPI: bus type USB registered
[    0.060060] usbcore: registered new interface driver usbfs
[    0.060060] usbcore: registered new interface driver hub
[    0.060062] usbcore: registered new device driver usb
[    0.060105] EDAC MC: Ver: 3.0.0
[    0.060105] PCI: Using ACPI for IRQ routing
[    0.062868] PCI: pci_cache_line_size set to 64 bytes
[    0.062895] e820: reserve RAM buffer [mem 0x0009f800-0x0009ffff]
[    0.062896] e820: reserve RAM buffer [mem 0xbffa0000-0xbfffffff]
[    0.062990] NetLabel: Initializing
[    0.062990] NetLabel:  domain hash size = 128
[    0.062991] NetLabel:  protocols = UNLABELED CIPSOv4 CALIPSO
[    0.063003] NetLabel:  unlabeled traffic allowed by default
[    0.063016] clocksource: Switched to clocksource refined-jiffies
[    0.075784] VFS: Disk quotas dquot_6.6.0
[    0.075806] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.075929] AppArmor: AppArmor Filesystem Enabled
[    0.075961] pnp: PnP ACPI init
[    0.076508] pnp 00:00: [dma 3]
[    0.076619] pnp 00:00: Plug and Play ACPI device, IDs PNP0401 (active)
[    0.077063] system 00:01: [io  0x04d0-0x04d1] has been reserved
[    0.077065] system 00:01: [io  0x0500-0x057f] has been reserved
[    0.077066] system 00:01: [io  0x0580-0x05ff] has been reserved
[    0.077067] system 00:01: [io  0x0800-0x087f] has been reserved
[    0.077068] system 00:01: [io  0x0880-0x08ff] has been reserved
[    0.077069] system 00:01: [io  0x0d00-0x0d7f] has been reserved
[    0.077070] system 00:01: [io  0x0d80-0x0dff] has been reserved
[    0.077072] system 00:01: [io  0x1100-0x117f] has been reserved
[    0.077073] system 00:01: [io  0x1180-0x11ff] has been reserved
[    0.077074] system 00:01: [mem 0x000d0000-0x000d3fff window] has been reserved
[    0.077076] system 00:01: [mem 0x000d4000-0x000d7fff window] has been reserved
[    0.077077] system 00:01: [mem 0x000de000-0x000dffff window] has been reserved
[    0.077078] system 00:01: [mem 0xfec80000-0xfecfffff] has been reserved
[    0.077080] system 00:01: [mem 0xfefe0000-0xfefe01ff] has been reserved
[    0.077081] system 00:01: [mem 0xfefe1000-0xfefe1fff] has been reserved
[    0.077082] system 00:01: [mem 0xfee01000-0xfeefffff] has been reserved
[    0.077083] system 00:01: [mem 0xffb80000-0xffffffff] could not be reserved
[    0.077087] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.077261] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.077372] system 00:03: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.077373] system 00:03: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.077376] system 00:03: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.077629] pnp 00:04: [dma 0 disabled]
[    0.077674] pnp 00:04: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.077787] system 00:05: [io  0x0280-0x028f] has been reserved
[    0.077788] system 00:05: [io  0x0290-0x029f] has been reserved
[    0.077791] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.077859] system 00:06: [mem 0xf0000000-0xf7ffffff] has been reserved
[    0.077862] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.078111] system 00:07: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.078113] system 00:07: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.078114] system 00:07: [mem 0x00100000-0xcfffffff] could not be reserved
[    0.078115] system 00:07: [mem 0xfec00000-0xffffffff] could not be reserved
[    0.078118] system 00:07: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.078417] pnp: PnP ACPI: found 8 devices
[    0.084296] clocksource: acpi_pm: mask: 0xffffff max_cycles: 0xffffff, max_idle_ns: 2085701024 ns
[    0.084320] clocksource: Switched to clocksource acpi_pm
[    0.084339] pci 0000:00:04.0: PCI bridge to [bus 01]
[    0.084345] pci 0000:00:09.0: PCI bridge to [bus 02]
[    0.084348] pci 0000:00:0b.0: PCI bridge to [bus 03]
[    0.084351] pci 0000:00:0c.0: PCI bridge to [bus 04]
[    0.084355] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7 window]
[    0.084356] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff window]
[    0.084357] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff window]
[    0.084358] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff window]
[    0.084359] pci_bus 0000:00: resource 8 [mem 0xd0000000-0xefffffff window]
[    0.084360] pci_bus 0000:00: resource 9 [mem 0xf8000000-0xfebfffff window]
[    0.084362] pci_bus 0000:01: resource 4 [io  0x0000-0x0cf7 window]
[    0.084363] pci_bus 0000:01: resource 5 [io  0x0d00-0xffff window]
[    0.084364] pci_bus 0000:01: resource 6 [mem 0x000a0000-0x000bffff window]
[    0.084365] pci_bus 0000:01: resource 7 [mem 0x000d0000-0x000dffff window]
[    0.084366] pci_bus 0000:01: resource 8 [mem 0xd0000000-0xefffffff window]
[    0.084367] pci_bus 0000:01: resource 9 [mem 0xf8000000-0xfebfffff window]
[    0.084437] NET: Registered protocol family 2
[    0.084678] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
[    0.084865] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.085204] TCP: Hash tables configured (established 65536 bind 65536)
[    0.085297] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.085355] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.085471] NET: Registered protocol family 1
[    0.085802] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 23
[    0.164413] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 22
[    0.164510] pci 0000:00:0d.0: Video device with shadowed ROM at [mem 0x000c0000-0x000dffff]
[    0.164520] PCI: CLS 64 bytes, default 64
[    0.164567] Unpacking initramfs...
[    0.871353] Freeing initrd memory: 59088K
[    0.871947] PCI-DMA: Disabling AGP.
[    0.872030] PCI-DMA: aperture base @ b4000000 size 65536 KB
[    0.872031] PCI-DMA: using GART IOMMU.
[    0.872033] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    0.874185] LVT offset 1 assigned for vector 0x400
[    0.874196] [Firmware Bug]: cpu 1, try to use APIC500 (LVT offset 0) for vector 0x10400, but the register is already in use for vector 0xf9 on another cpu
[    0.874258] [Firmware Bug]: cpu 1, IBS interrupt offset 0 not available (MSRC001103A=0x0000000000000100)
[    0.874389] Scanning for low memory corruption every 60 seconds
[    0.874961] Initialise system trusted keyrings
[    0.874970] Key type blacklist registered
[    0.875155] workingset: timestamp_bits=36 max_order=21 bucket_order=0
[    0.876253] zbud: loaded
[    0.876780] squashfs: version 4.0 (2009/01/31) Phillip Lougher
[    0.877055] fuse init (API version 7.26)
[    0.879204] Key type asymmetric registered
[    0.879206] Asymmetric key parser 'x509' registered
[    0.879259] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 246)
[    0.879310] io scheduler noop registered
[    0.879311] io scheduler deadline registered
[    0.879336] io scheduler cfq registered (default)
[    0.879958] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.879970] ACPI: Power Button [PWRB]
[    0.880033] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.880058] ACPI: Power Button [PWRF]
[    0.880346] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.900783] 00:04: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
[    0.902726] Linux agpgart interface v0.103
[    0.904700] loop: module loaded
[    0.904962] libphy: Fixed MDIO Bus: probed
[    0.904963] tun: Universal TUN/TAP device driver, 1.6
[    0.905055] PPP generic driver version 2.4.2
[    0.905127] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.905130] ehci-pci: EHCI PCI platform driver
[    0.905381] ehci-pci 0000:00:02.1: EHCI Host Controller
[    0.905388] ehci-pci 0000:00:02.1: new USB bus registered, assigned bus number 1
[    0.905395] ehci-pci 0000:00:02.1: debug port 1
[    0.905424] ehci-pci 0000:00:02.1: cache line size of 64 is not supported
[    0.905445] ehci-pci 0000:00:02.1: irq 22, io mem 0xefffec00
[    0.920062] ehci-pci 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    0.920117] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.920118] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.920119] usb usb1: Product: EHCI Host Controller
[    0.920120] usb usb1: Manufacturer: Linux 4.15.0-51-generic ehci_hcd
[    0.920121] usb usb1: SerialNumber: 0000:00:02.1
[    0.920308] hub 1-0:1.0: USB hub found
[    0.920314] hub 1-0:1.0: 10 ports detected
[    0.920518] ehci-platform: EHCI generic platform driver
[    0.920532] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.920539] ohci-pci: OHCI PCI platform driver
[    0.920723] ohci-pci 0000:00:02.0: OHCI PCI host controller
[    0.920729] ohci-pci 0000:00:02.0: new USB bus registered, assigned bus number 2
[    0.920771] ohci-pci 0000:00:02.0: irq 23, io mem 0xeffff000
[    0.982081] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    0.982084] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.982085] usb usb2: Product: OHCI PCI host controller
[    0.982086] usb usb2: Manufacturer: Linux 4.15.0-51-generic ohci_hcd
[    0.982086] usb usb2: SerialNumber: 0000:00:02.0
[    0.982278] hub 2-0:1.0: USB hub found
[    0.982285] hub 2-0:1.0: 10 ports detected
[    0.982477] ohci-platform: OHCI generic platform driver
[    0.982491] uhci_hcd: USB Universal Host Controller Interface driver
[    0.982570] i8042: PNP: No PS/2 controller found.
[    0.982570] i8042: Probing ports directly.
[    0.985070] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.985079] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.985278] mousedev: PS/2 mouse device common for all mice
[    0.985448] rtc_cmos 00:02: RTC can wake from S4
[    0.985620] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.985652] rtc_cmos 00:02: alarms up to one year, y3k, 114 bytes nvram
[    0.985658] i2c /dev entries driver
[    0.985715] device-mapper: uevent: version 1.0.3
[    0.985805] device-mapper: ioctl: 4.37.0-ioctl (2017-09-20) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    0.985836] ledtrig-cpu: registered to indicate activity on CPUs
[    0.986256] NET: Registered protocol family 10
[    0.990040] Segment Routing with IPv6
[    0.990065] NET: Registered protocol family 17
[    0.990156] Key type dns_resolver registered
[    0.990453] RAS: Correctable Errors collector initialized.
[    0.990507] microcode: CPU0: patch_level=0x010000c8
[    0.990525] microcode: CPU1: patch_level=0x010000c8
[    0.990587] microcode: Microcode Update Driver: v2.2.
[    0.990602] sched_clock: Marking stable (990583202, 0)->(1072760342, -82177140)
[    0.990776] registered taskstats version 1
[    0.990784] Loading compiled-in X.509 certificates
[    0.993705] Loaded X.509 cert 'Build time autogenerated kernel key: c1fa4cde9d34780ae4ae655b856adc042b663c06'
[    0.993733] zswap: loaded using pool lzo/zbud
[    0.997509] Key type big_key registered
[    0.997514] Key type trusted registered
[    0.999289] Key type encrypted registered
[    0.999293] AppArmor: AppArmor sha1 policy hashing enabled
[    0.999296] ima: No TPM chip found, activating TPM-bypass! (rc=-19)
[    0.999301] ima: Allocated hash algorithm: sha1
[    0.999319] evm: HMAC attrs: 0x1
[    0.999519]   Magic number: 7:369:554
[    0.999548] clockevents clockevent5: hash matches
[    0.999626] acpi PNP0C0F:05: hash matches
[    0.999628] acpi PNP0C01:00: hash matches
[    0.999713] rtc_cmos 00:02: setting system clock to 2019-06-06 23:32:27 UTC (1559863947)
[    0.999903] acpi_cpufreq: overriding BIOS provided _PSD data
[    0.999969] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.999970] EDD information not available.
[    1.002895] Freeing unused kernel image memory: 2408K
[    1.020054] Write protecting the kernel read-only data: 20480k
[    1.020785] Freeing unused kernel image memory: 2008K
[    1.021352] Freeing unused kernel image memory: 1872K
[    1.029709] x86/mm: Checked W+X mappings: passed, no W+X pages found.
[    1.116430] i2c i2c-0: nForce2 SMBus adapter at 0x600
[    1.116435] ACPI Warning: SystemIO range 0x0000000000000700-0x000000000000073F conflicts with OpRegion 0x0000000000000700-0x000000000000073F (\_SB.PCI0.SM00) (20170831/utaddress-247)
[    1.116440] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    1.116895] sata_nv 0000:00:08.0: version 3.5
[    1.117211] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 21
[    1.124605] scsi host0: sata_nv
[    1.131647] scsi host1: sata_nv
[    1.131702] ata1: SATA max UDMA/133 cmd 0xe000 ctl 0xdc00 bmdma 0xd480 irq 21
[    1.131704] ata2: SATA max UDMA/133 cmd 0xd880 ctl 0xd800 bmdma 0xd488 irq 21
[    1.131788] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.132143] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 20
[    1.524067] usb 2-2: new low-speed USB device number 2 using ohci-pci
[    1.600091] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.600372] ata1.00: ATA-11: KINGSTON SA400S37120G, SBFK71E0, max UDMA/133
[    1.600374] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.600748] ata1.00: configured for UDMA/133
[    1.601033] scsi 0:0:0:0: Direct-Access     ATA      KINGSTON SA400S3 71E0 PQ: 0 ANSI: 5
[    1.601375] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.601391] sd 0:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/112 GiB)
[    1.601403] sd 0:0:0:0: [sda] Write Protect is off
[    1.601404] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.601430] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.601904]  sda: sda1
[    1.602322] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.684800] forcedeth 0000:00:07.0: ifname eth0, PHY OUI 0x732 @ 1, addr bc:5f:f4:07:df:a3
[    1.684803] forcedeth 0000:00:07.0: highdma pwrctl mgmt lnktim msi desc-v3
[    1.684890] pata_amd 0000:00:06.0: version 0.4.1
[    1.685637] forcedeth 0000:00:07.0 enp0s7: renamed from eth0
[    1.685706] scsi host2: pata_amd
[    1.685789] scsi host3: pata_amd
[    1.685816] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    1.685817] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    1.687380] ACPI: PCI Interrupt Link [LSA1] enabled at IRQ 23
[    1.687656] scsi host4: sata_nv
[    1.687735] scsi host5: sata_nv
[    1.687762] ata5: SATA max UDMA/133 cmd 0xd400 ctl 0xd080 bmdma 0xc880 irq 23
[    1.687763] ata6: SATA max UDMA/133 cmd 0xd000 ctl 0xcc00 bmdma 0xc888 irq 23
[    1.688156] ACPI: PCI Interrupt Link [LMC9] enabled at IRQ 22
[    1.688288] nouveau 0000:00:0d.0: NVIDIA C61 (04c000a2)
[    1.697578] nouveau 0000:00:0d.0: bios: version 05.61.32.28.01
[    1.698432] nouveau 0000:00:0d.0: fb: 256 MiB of unknown memory type
[    1.747505] [TTM] Zone  kernel: Available graphics memory: 2922686 kiB
[    1.747506] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB
[    1.747507] [TTM] Initializing pool allocator
[    1.747511] [TTM] Initializing DMA pool allocator
[    1.747522] nouveau 0000:00:0d.0: DRM: VRAM: 253 MiB
[    1.747523] nouveau 0000:00:0d.0: DRM: GART: 512 MiB
[    1.747525] nouveau 0000:00:0d.0: DRM: TMDS table version 1.1
[    1.747526] nouveau 0000:00:0d.0: DRM: DCB version 3.0
[    1.747528] nouveau 0000:00:0d.0: DRM: DCB outp 00: 01000310 00000023
[    1.747530] nouveau 0000:00:0d.0: DRM: DCB outp 01: 00110204 942b0003
[    1.747531] nouveau 0000:00:0d.0: DRM: DCB conn 00: 0000
[    1.747532] nouveau 0000:00:0d.0: DRM: DCB conn 01: 1131
[    1.747533] nouveau 0000:00:0d.0: DRM: DCB conn 02: 0110
[    1.747534] nouveau 0000:00:0d.0: DRM: DCB conn 03: 0111
[    1.747535] nouveau 0000:00:0d.0: DRM: DCB conn 04: 0113
[    1.747711] nouveau 0000:00:0d.0: DRM: Saving VGA fonts
[    1.784150] nouveau 0000:00:0d.0: DRM: DCB type 4 not known
[    1.784151] nouveau 0000:00:0d.0: DRM: Unknown-1 has no encoders, removing
[    1.785234] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    1.785234] [drm] Driver supports precise vblank timestamp query.
[    1.787394] nouveau 0000:00:0d.0: DRM: MM: using M2MF for buffer copies
[    1.815820] nouveau 0000:00:0d.0: DRM: allocated 1680x1050 fb: 0x9000, bo         (ptrval)
[    1.844103] fbcon: nouveaufb (fb0) is primary device
[    1.850120] usb 2-2: New USB device found, idVendor=2a7a, idProduct=9a18
[    1.850122] usb 2-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.850123] usb 2-2: Product: CASUE USB Keyboard
[    1.850124] usb 2-2: Manufacturer: CASUE
[    1.864444] hidraw: raw HID events driver (C) Jiri Kosina
[    1.883319] usbcore: registered new interface driver usbhid
[    1.883320] usbhid: USB HID core driver
[    1.885496] input: CASUE CASUE USB Keyboard as /devices/pci0000:00/0000:00:02.0/usb2/2-2/2-2:1.0/0003:2A7A:9A18.0001/input/input5
[    1.892081] tsc: Refined TSC clocksource calibration: 3415.532 MHz
[    1.892088] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x313b9f76306, max_idle_ns: 440795376533 ns
[    1.925781] Console: switching to colour frame buffer device 210x65
[    1.926497] ata2: SATA link down (SStatus 0 SControl 300)
[    1.926561] ata4: port disabled--ignoring
[    1.927906] nouveau 0000:00:0d.0: fb0: nouveaufb frame buffer device
[    1.940086] [drm] Initialized nouveau 1.3.1 20120801 for 0000:00:0d.0 on minor 0
[    1.944500] hid-generic 0003:2A7A:9A18.0001: input,hidraw0: USB HID v1.10 Keyboard [CASUE CASUE USB Keyboard] on usb-0000:00:02.0-2/input0
[    1.944680] input: CASUE CASUE USB Keyboard as /devices/pci0000:00/0000:00:02.0/usb2/2-2/2-2:1.1/0003:2A7A:9A18.0002/input/input6
[    2.004201] hid-generic 0003:2A7A:9A18.0002: input,hidraw1: USB HID v1.10 Device [CASUE CASUE USB Keyboard] on usb-0000:00:02.0-2/input1
[    2.007904] ata5: SATA link down (SStatus 0 SControl 300)
[    2.236078] usb 2-3: new low-speed USB device number 3 using ohci-pci
[    2.256040] raid6: sse2x1   gen()  4396 MB/s
[    2.304039] raid6: sse2x1   xor()  4563 MB/s
[    2.333009] ata6: SATA link down (SStatus 0 SControl 300)
[    2.352046] raid6: sse2x2   gen()  6605 MB/s
[    2.400037] raid6: sse2x2   xor()  7480 MB/s
[    2.448044] raid6: sse2x4   gen()  7828 MB/s
[    2.471122] usb 2-3: New USB device found, idVendor=0458, idProduct=0186
[    2.471125] usb 2-3: New USB device strings: Mfr=4, Product=40, SerialNumber=0
[    2.471126] usb 2-3: Product: Wired Mouse
[    2.471127] usb 2-3: Manufacturer: KYE SYSTEMS CORP.
[    2.481430] input: KYE SYSTEMS CORP. Wired Mouse as /devices/pci0000:00/0000:00:02.0/usb2/2-3/2-3:1.0/0003:0458:0186.0003/input/input7
[    2.481525] hid-generic 0003:0458:0186.0003: input,hidraw2: USB HID v1.11 Mouse [KYE SYSTEMS CORP. Wired Mouse] on usb-0000:00:02.0-3/input0
[    2.481573] usbhid 2-3:1.1: couldn't find an input interrupt endpoint
[    2.496043] raid6: sse2x4   xor()  4386 MB/s
[    2.496044] raid6: using algorithm sse2x4 gen() 7828 MB/s
[    2.496045] raid6: .... xor() 4386 MB/s, rmw enabled
[    2.496047] raid6: using intx1 recovery algorithm
[    2.499523] xor: measuring software checksum speed
[    2.536033]    prefetch64-sse: 13151.000 MB/sec
[    2.576032]    generic_sse: 12617.000 MB/sec
[    2.576033] xor: using function: prefetch64-sse (13151.000 MB/sec)
[    2.593987] Btrfs loaded, crc32c=crc32c-generic
[    2.652628] random: fast init done
[    2.796501] random: systemd-udevd: uninitialized urandom read (16 bytes read)
[    2.796515] random: systemd-udevd: uninitialized urandom read (16 bytes read)
[    2.796518] random: systemd-udevd: uninitialized urandom read (16 bytes read)
[    2.797294] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    2.912242] clocksource: Switched to clocksource tsc
[    3.018879] ip_tables: (C) 2000-2006 Netfilter Core Team
[    3.031259] systemd[1]: systemd 237 running in system mode. (+PAM +AUDIT +SELINUX +IMA +APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT +GNUTLS +ACL +XZ +LZ4 +SECCOMP +BLKID +ELFUTILS +KMOD -IDN2 +IDN -PCRE2 default-hierarchy=hybrid)
[    3.031370] systemd[1]: Detected architecture x86-64.
[    3.033053] systemd[1]: Set hostname to <inti-desktop>.
[    3.040080] usb 1-4: new high-speed USB device number 4 using ehci-pci
[    3.213644] usb 1-4: New USB device found, idVendor=148f, idProduct=3070
[    3.213646] usb 1-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    3.213647] usb 1-4: Product: 802.11 n WLAN
[    3.213652] usb 1-4: Manufacturer: Ralink
[    3.213653] usb 1-4: SerialNumber: 1.0
[    3.231726] systemd[1]: Reached target User and Group Name Lookups.
[    3.231807] systemd[1]: Reached target Remote File Systems.
[    3.231988] systemd[1]: Created slice System Slice.
[    3.232080] systemd[1]: Listening on udev Kernel Socket.
[    3.232138] systemd[1]: Listening on LVM2 metadata daemon socket.
[    3.232181] systemd[1]: Listening on /dev/initctl Compatibility Named Pipe.
[    3.232227] systemd[1]: Listening on Journal Socket (/dev/log).
[    3.260768] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[    3.322705] lp: driver loaded but no devices found
[    3.336580] ppdev: user-space parallel port driver
[    3.338332] parport_pc 00:00: reported by Plug and Play ACPI
[    3.338399] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[    3.378450] Adding 2097148k swap on /swapfile.  Priority:-2 extents:6 across:2260988k SSFS
[    3.411145] systemd-journald[329]: Received request to flush runtime journal from PID 1
[    3.428189] lp0: using parport0 (interrupt-driven).
[    3.428695] systemd-journald[329]: File /var/log/journal/1975cc0879614ce88a5940de34910d44/system.journal corrupted or uncleanly shut down, renaming and replacing.
[    3.598705] audit: type=1400 audit(1559863950.092:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=441 comm="apparmor_parser"
[    3.598709] audit: type=1400 audit(1559863950.092:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=441 comm="apparmor_parser"
[    3.598710] audit: type=1400 audit(1559863950.092:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=441 comm="apparmor_parser"
[    3.598711] audit: type=1400 audit(1559863950.092:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=441 comm="apparmor_parser"
[    3.599195] audit: type=1400 audit(1559863950.092:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=440 comm="apparmor_parser"
[    3.599199] audit: type=1400 audit(1559863950.092:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session//chromium" pid=440 comm="apparmor_parser"
[    3.604045] audit: type=1400 audit(1559863950.096:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="libreoffice-oopslash" pid=444 comm="apparmor_parser"
[    3.605575] audit: type=1400 audit(1559863950.100:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/man" pid=443 comm="apparmor_parser"
[    3.605579] audit: type=1400 audit(1559863950.100:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="man_filter" pid=443 comm="apparmor_parser"
[    3.854490] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    4.427997] cfg80211: Loading compiled-in X.509 certificates for regulatory database
[    4.433797] kvm: Nested Virtualization enabled
[    4.433804] kvm: Nested Paging enabled
[    4.435578] MCE: In-kernel MCE decoding enabled.
[    4.438783] EDAC amd64: Node 0: DRAM ECC disabled.
[    4.438785] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
                Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
                (Note that use of the override may cause unknown side effects.)
[    4.441902] cfg80211: Loaded X.509 cert 'sforshee: 00b28ddf47aef9cea7'
[    4.541725] EDAC amd64: Node 0: DRAM ECC disabled.
[    4.541727] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
                Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
                (Note that use of the override may cause unknown side effects.)
[    4.670505] IPv6: ADDRCONF(NETDEV_UP): enp0s7: link is not ready
[    4.671248] forcedeth 0000:00:07.0 enp0s7: no link during initialization
[    4.673374] IPv6: ADDRCONF(NETDEV_UP): enp0s7: link is not ready
[    4.779972] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 21
[    4.779982] snd_hda_intel 0000:00:05.0: Disabling MSI
[    4.798751] nouveau 0000:00:0d.0: bus: MMIO write of 00720001 FAULT at 00b000
[    4.852105] usb 1-4: reset high-speed USB device number 4 using ehci-pci
[    5.023053] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[    5.054142] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 0005 detected
[    5.066740] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[    5.067164] usbcore: registered new interface driver rt2800usb
[    5.079278] rt2800usb 1-4:1.0 wlx000f004088a2: renamed from wlan0
[    5.100807] IPv6: ADDRCONF(NETDEV_UP): wlx000f004088a2: link is not ready
[    5.100870] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[    5.105439] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.36
[    5.452686] IPv6: ADDRCONF(NETDEV_UP): wlx000f004088a2: link is not ready
[    5.503245] IPv6: ADDRCONF(NETDEV_UP): wlx000f004088a2: link is not ready
[    5.536159] snd_hda_codec_via hdaudioC0D0: autoconfig for VT1705: line_outs=1 (0x1c/0x0/0x0/0x0/0x0) type:line
[    5.536167] snd_hda_codec_via hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    5.536173] snd_hda_codec_via hdaudioC0D0:    hp_outs=1 (0x1d/0x0/0x0/0x0/0x0)
[    5.536176] snd_hda_codec_via hdaudioC0D0:    mono: mono_out=0x0
[    5.536179] snd_hda_codec_via hdaudioC0D0:    inputs:
[    5.536184] snd_hda_codec_via hdaudioC0D0:      Rear Mic=0x1a
[    5.536189] snd_hda_codec_via hdaudioC0D0:      Front Mic=0x1e
[    5.536193] snd_hda_codec_via hdaudioC0D0:      Line=0x1b
[    5.692444] systemd-journald[329]: File /var/log/journal/1975cc0879614ce88a5940de34910d44/user-1000.journal corrupted or uncleanly shut down, renaming and replacing.
[    6.875252] wlx000f004088a2: authenticate with 8c:10:d4:88:cc:ee
[    6.899541] wlx000f004088a2: send auth to 8c:10:d4:88:cc:ee (try 1/3)
[    6.901520] wlx000f004088a2: authenticated
[    6.904259] wlx000f004088a2: associate with 8c:10:d4:88:cc:ee (try 1/3)
[    6.907637] wlx000f004088a2: RX AssocResp from 8c:10:d4:88:cc:ee (capab=0x1411 status=0 aid=5)
[    6.914997] wlx000f004088a2: associated
[    6.917681] wlx000f004088a2: Limiting TX power to 30 (30 - 0) dBm as advertised by 8c:10:d4:88:cc:ee
[    6.938745] input: HDA NVidia Rear Mic as /devices/pci0000:00/0000:00:05.0/sound/card0/input8
[    6.938804] input: HDA NVidia Line as /devices/pci0000:00/0000:00:05.0/sound/card0/input9
[    6.938850] input: HDA NVidia Line Out as /devices/pci0000:00/0000:00:05.0/sound/card0/input10
[    7.010563] IPv6: ADDRCONF(NETDEV_CHANGE): wlx000f004088a2: link becomes ready
[    7.497880] nouveau 0000:00:0d.0: bus: MMIO write of 01040001 FAULT at 00b010
[  202.002735] random: crng init done
[  202.002742] random: 7 urandom warning(s) missed due to ratelimiting
[  720.233956] nouveau 0000:00:0d.0: bus: MMIO write of 00000000 FAULT at 00b010
[  720.234603] nouveau 0000:00:0d.0: bus: MMIO write of 00720001 FAULT at 00b000
[  721.468835] nouveau 0000:00:0d.0: bus: MMIO write of 00f00001 FAULT at 00b010
[  728.772481] nouveau 0000:00:0d.0: bus: MMIO write of 02420001 FAULT at 00b020
[  728.982311] nouveau 0000:00:0d.0: bus: MMIO write of 00000000 FAULT at 00b020


Edit: Just read this thread.
[https://forums.linuxmint.com/viewtopic.php?t=282580](https://forums.linuxmint.com/viewtopic.php?t=282580)

and looks like the HW I&#7743; using is not supported, 

I'd hate to be forced to use windows, please help!


inxi -Gx



Graphics:
  Device-1: NVIDIA C61 [GeForce 7025 / nForce 630a] vendor: ASRock 
  driver: N/A bus ID: 00:0d.0 
  Display: x11 server: X.Org 1.19.6 driver: fbdev,nouveau 
  unloaded: modesetting,vesa resolution: 640x480~73Hz 
  OpenGL: renderer: llvmpipe (LLVM 7.0 128 bits) v: 3.3 Mesa 18.2.8

---

### Post by him610 on 2019-06-07
> GeForce 7025 / nForce 630a....driver: fbdev,nouveau
 Your GFX is somewhat long in the tooth. You have loaded the open source driver, Nouveau; there may be other issues though.  Normally, it would use the nvidia proprietary driver. 304.128, but I don't think it is included in the repository of the more recent versions of Ubuntu. You may need to go to the Nvidia website to download the driver,  [https://www.nvidia.com/Download/driverResults.aspx/90399/en-us]("https://www.nvidia.com/Download/driverResults.aspx/90399/en-us") (This link is for the 64bit version, for the 32bit version, you may need to search on the Nvidia website.)
That said, you might want to check the Additional Drivers to see if there may be a recommended Nvidia driver for your GFX card. I used to have a card similar similar to yours; never had any issues with it up through LTS 16.04

---

### Post by xavilai on 2019-06-07
Thanks  for your reply!
I know, its old hardware, but is surprising what an SSD drive can do with it.

When I try to activate the 304 driver from Additional Drivers I get dependencies missing:

nvidia-304: Depends: x11-common (>= 1:7.0.0) pero 1:7.7+19ubuntu7.1 no está instalado
            Depends: libgcc1 (>= 1:3.3) pero 1:8.3.0-6ubuntu1~18.04 no está instalado
            Depends: xorg-video-abi-23 pero es un paquete virtual



Currently trying to install with the link you provided but must stop x11 first


EDIT:

[IMG]https://lh3.googleusercontent.com/dXEzqBf3s7YkDYt9E6IGD2LfGSV-d9kg9s5Xh_OhXiuGmJ5xL1Je6Up3_pYBk9T_qb1qbKbYlp1H8kEqG6fZPS_7LlmV6RkipV0xR2oswm5gwLvbwr_uebaw0RTY5EOhk4QvxIAELrCxNojDUHpDSMzHkeSLq-c_nh6vsk6LYYSiBe2Ca9c6Z2pCXtBd_iQSbzMX5pef74LG7-QCkcxF178_fGuCOjmtALZgneZWO5gOajiZvmhu8FI-pj1J7sVga7fSnYSaKE0_YIffp3xsxMcT2pCTCbiz0p3s85UIhDhXoGrehndCnjUogZEVxKy1GUik9o-8nSac-5FucmYDzzIK0wdIs8SbZY4aPJTS_hlQhQjqGKkOSvoiLUz04X1HOWgnYwS6gMoadkM8ycVeKVjnLNSCkX-K8afh7Oq5viic7lOMy-m-EuJXfKaOHVVhUsz3h6UGGpGpld8P2IwaZs-2Y_Y4c7SKey3hTJg9xmmi97d_v-QvVvUbcOHDv0sET-RID92KL663L4KsQJHyblUOcQxSqHp6SlJ7mvAcOzGb4CoZ8lmCwKGIUydoHrwrEjAC0oFcaaFE9FpmFRYiRGU1LMG-XblWJx4RfaG3er_rHx38_RD3ITmDk_Theqf1HdyO12-4FVIQTbz5_0eSHh_AaAuF3RWX8lvOSm0ak22KVxtC80skzplknrTw6mo5u9ygsK6XGtDX-fAtb1rBFqQ1dA=w1043-h782-no[/IMG]



I'm doing my best to recycle and care for the environment but nvidia and nouveau are not helping at all!

Does anyone know the latest release that worked out of the box with GeForce 7025 / nForce 630a /  304 nvidia driver?

---

