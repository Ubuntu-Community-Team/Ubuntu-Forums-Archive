---
title: "error message in boot up"
date: 2014-12-04
forum: General Help
---

### Post by kccv42 on 2014-12-04
Here i provided the dsmeg message. Can you tell me what error or message it tells me when my computer boots up and how i fix it.


[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.13.0-32-generic (buildd@kissel) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #57-Ubuntu SMP Tue Jul 15 03:51:08 UTC 2014 (Ubuntu 3.13.0-32.57-generic 3.13.11.4)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-32-generic root=UUID=871bf1e7-1d33-4d2f-a779-fda41f1edf72 ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009f7ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009f800-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000006e455fff] usable
[    0.000000] BIOS-e820: [mem 0x000000006e456000-0x000000006e655fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000006e656000-0x000000006fd3efff] usable
[    0.000000] BIOS-e820: [mem 0x000000006fd3f000-0x000000006fdbefff] reserved
[    0.000000] BIOS-e820: [mem 0x000000006fdbf000-0x000000006febefff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000006febf000-0x000000006fef5fff] ACPI data
[    0.000000] BIOS-e820: [mem 0x000000006fef6000-0x000000006fefffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec10000-0x00000000fec10fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffe00000-0x00000000ffffffff] reserved
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.6 present.
[    0.000000] DMI: Hewlett-Packard Presario CQ56 Notebook PC/1604, BIOS F.00 06/21/2010
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x6ff00 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFFC0000000 write-back
[    0.000000]   1 base 000040000000 mask FFFFE0000000 write-back
[    0.000000]   2 base 000060000000 mask FFFFF0000000 write-back
[    0.000000]   3 base 00006FEBC000 mask FFFFFFFFF000 uncachable
[    0.000000]   4 base 0000FFE00000 mask FFFFFFE00000 write-protect
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 24576
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01fdf000, 0x01fdffff] PGTABLE
[    0.000000] BRK [0x01fe0000, 0x01fe0fff] PGTABLE
[    0.000000] BRK [0x01fe1000, 0x01fe1fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x6fa00000-0x6fbfffff]
[    0.000000]  [mem 0x6fa00000-0x6fbfffff] page 2M
[    0.000000] BRK [0x01fe2000, 0x01fe2fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x6c000000-0x6e455fff]
[    0.000000]  [mem 0x6c000000-0x6e3fffff] page 2M
[    0.000000]  [mem 0x6e400000-0x6e455fff] page 4k
[    0.000000] BRK [0x01fe3000, 0x01fe3fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x6e656000-0x6f9fffff]
[    0.000000]  [mem 0x6e656000-0x6e7fffff] page 4k
[    0.000000]  [mem 0x6e800000-0x6f9fffff] page 2M
[    0.000000] BRK [0x01fe4000, 0x01fe4fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x00100000-0x6bffffff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x6bffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x6fc00000-0x6fd3efff]
[    0.000000]  [mem 0x6fc00000-0x6fd3efff] page 4k
[    0.000000] init_memory_mapping: [mem 0x6fef6000-0x6fefffff]
[    0.000000]  [mem 0x6fef6000-0x6fefffff] page 4k
[    0.000000] RAMDISK: [mem 0x35b5a000-0x36da4fff]
[    0.000000] ACPI: RSDP 00000000000fe020 000024 (v02 HP    )
[    0.000000] ACPI: XSDT 000000006fef5120 00005C (v01 HPQOEM SLIC-MPC 00000003      01000013)
[    0.000000] ACPI: FACP 000000006fef4000 0000F4 (v04 HP     1604     00000003 MSFT 01000013)
[    0.000000] ACPI BIOS Error (bug): 32/64X address mismatch in FADT/Pm2ControlBlock: 0x00000900/0x0000000000000800, using 32 (20131115/tbfadt-462)
[    0.000000] ACPI: DSDT 000000006fee3000 00D737 (v01 HP     1604     F0000000 MSFT 01000013)
[    0.000000] ACPI: FACS 000000006fe9b000 000040
[    0.000000] ACPI: HPET 000000006fef3000 000038 (v01 HP     1604     00000001 MSFT 01000013)
[    0.000000] ACPI: APIC 000000006fef2000 000084 (v02 HP     1604     00000001 MSFT 01000013)
[    0.000000] ACPI: MCFG 000000006fef1000 00003C (v01 HP     1604     00000001 MSFT 01000013)
[    0.000000] ACPI: BOOT 000000006fee2000 000028 (v01 HP     1604     00000001 MSFT 01000013)
[    0.000000] ACPI: SLIC 000000006fee1000 000176 (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: SSDT 000000006fee0000 0001B7 (v01 AMD    POWERNOW 00000001 AMD  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000006fefffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x6fefffff]
[    0.000000]   NODE_DATA [mem 0x6fefb000-0x6fefffff]
[    0.000000]  [ffffea0000000000-ffffea0001bfffff] PMD -> [ffff88006c800000-ffff88006e3fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   empty
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009efff]
[    0.000000]   node   0: [mem 0x00100000-0x6e455fff]
[    0.000000]   node   0: [mem 0x6e656000-0x6fd3efff]
[    0.000000]   node   0: [mem 0x6fef6000-0x6fefffff]
[    0.000000] On node 0 totalpages: 457447
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3998 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 7100 pages used for memmap
[    0.000000]   DMA32 zone: 453449 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x1002a201 base: 0xfed00000
[    0.000000] smpboot: Allowing 4 CPUs, 3 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x6e456000-0x6e655fff]
[    0.000000] PM: Registered nosave memory: [mem 0x6fd3f000-0x6fdbefff]
[    0.000000] PM: Registered nosave memory: [mem 0x6fdbf000-0x6febefff]
[    0.000000] PM: Registered nosave memory: [mem 0x6febf000-0x6fef5fff]
[    0.000000] e820: [mem 0x6ff00000-0xf7ffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 29 pages/cpu @ffff88006f800000 s86336 r8192 d24256 u524288
[    0.000000] pcpu-alloc: s86336 r8192 d24256 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 450262
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-32-generic root=UUID=871bf1e7-1d33-4d2f-a779-fda41f1edf72 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Node 0: aperture @ e944000000 size 32 MB
[    0.000000] Aperture beyond 4GB. Ignoring.
[    0.000000] Memory: 1765284K/1829788K available (7363K kernel code, 1142K rwdata, 3400K rodata, 1336K init, 1440K bss, 64504K reserved)
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
[    0.000000] allocated 7340032 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.004000] tsc: Detected 2294.423 MHz processor
[    0.000003] Calibrating delay loop (skipped), value calculated using timer frequency.. 4588.84 BogoMIPS (lpj=9177692)
[    0.000007] pid_max: default: 32768 minimum: 301
[    0.000033] Security Framework initialized
[    0.000054] AppArmor: AppArmor initialized
[    0.000056] Yama: becoming mindful.
[    0.000252] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.001015] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.001381] Mount-cache hash table entries: 4096 (order: 3, 32768 bytes)
[    0.001385] Mountpoint-cache hash table entries: 4096 (order: 3, 32768 bytes)
[    0.001623] Initializing cgroup subsys memory
[    0.001631] Initializing cgroup subsys devices
[    0.001633] Initializing cgroup subsys freezer
[    0.001635] Initializing cgroup subsys blkio
[    0.001636] Initializing cgroup subsys perf_event
[    0.001639] Initializing cgroup subsys hugetlb
[    0.001660] tseg: 006ff00000
[    0.001664] mce: CPU supports 6 MCE banks
[    0.001671] LVT offset 0 assigned for vector 0xf9
[    0.001675] process: using AMD E400 aware idle routine
[    0.001678] Last level iTLB entries: 4KB 512, 2MB 16, 4MB 8
[    0.001678] Last level dTLB entries: 4KB 512, 2MB 128, 4MB 64
[    0.001678] tlb_flushall_shift: 4
[    0.009562] ACPI: Core revision 20131115
[    0.014694] ACPI: All ACPI Tables successfully acquired
[    0.018475] ftrace: allocating 28495 entries in 112 pages
[    0.032636] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.072297] smpboot: CPU0: AMD V140 Processor (fam: 10, model: 06, stepping: 03)
[    0.179677] Performance Events: AMD PMU driver.
[    0.179681] ... version:                0
[    0.179683] ... bit width:              48
[    0.179684] ... generic registers:      4
[    0.179685] ... value mask:             0000ffffffffffff
[    0.179686] ... max period:             00007fffffffffff
[    0.179687] ... fixed-purpose events:   0
[    0.179688] ... event mask:             000000000000000f
[    0.181414] x86: Booted up 1 node, 1 CPUs
[    0.181418] smpboot: Total of 1 processors activated (4588.84 BogoMIPS)
[    0.181752] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.181864] devtmpfs: initialized
[    0.185571] EVM: security.selinux
[    0.185573] EVM: security.SMACK64
[    0.185574] EVM: security.ima
[    0.185575] EVM: security.capability
[    0.185625] PM: Registering ACPI NVS region [mem 0x6e456000-0x6e655fff] (2097152 bytes)
[    0.185655] PM: Registering ACPI NVS region [mem 0x6fdbf000-0x6febefff] (1048576 bytes)
[    0.186757] pinctrl core: initialized pinctrl subsystem
[    0.186837] regulator-dummy: no parameters
[    0.186902] RTC time: 21:29:33, date: 12/04/14
[    0.186949] NET: Registered protocol family 16
[    0.187068] cpuidle: using governor ladder
[    0.187070] cpuidle: using governor menu
[    0.187075] node 0 link 0: io port [0, ffffff]
[    0.187077] TOM: 0000000080000000 aka 2048M
[    0.187080] Fam 10h mmconf [mem 0xf8000000-0xfbffffff]
[    0.187082] node 0 link 0: mmio [a0000, bffff]
[    0.187085] node 0 link 0: mmio [80000000, 8fffffff]
[    0.187087] node 0 link 0: mmio [90000000, 901fffff]
[    0.187088] node 0 link 0: mmio [90200000, 903fffff]
[    0.187090] node 0 link 0: mmio [90400000, f7ffffff]
[    0.187091] node 0 link 0: mmio [f8000000, fbffffff] ==> none
[    0.187093] node 0 link 0: mmio [fc000000, ffdfffff]
[    0.187095] bus: [bus 00-1f] on node 0 link 0
[    0.187097] bus: 00 [io  0x0000-0xffff]
[    0.187098] bus: 00 [mem 0x000a0000-0x000bffff]
[    0.187099] bus: 00 [mem 0x80000000-0xf7ffffff]
[    0.187101] bus: 00 [mem 0xfc000000-0xfcffffffff]
[    0.187188] ACPI: bus type PCI registered
[    0.187190] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.187292] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.187295] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.190301] PCI: Using configuration type 1 for base access
[    0.191166] bio: create slab <bio-0> at 0
[    0.191312] ACPI: Added _OSI(Module Device)
[    0.191313] ACPI: Added _OSI(Processor Device)
[    0.191315] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.191316] ACPI: Added _OSI(Processor Aggregator Device)
[    0.194100] ACPI: Executed 1 blocks of module-level executable AML code
[    0.196132] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.196524] process: System has AMD C1E enabled
[    0.196534] process: Switch to broadcast mode on CPU0
[    0.201829] ACPI: Interpreter enabled
[    0.201848] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20131115/hwxface-580)
[    0.201854] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)
[    0.201875] ACPI: (supports S0 S3 S4 S5)
[    0.201876] ACPI: Using IOAPIC for interrupt routing
[    0.202035] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.202177] ACPI: No dock devices found.
[    0.209630] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.209639] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.209645] acpi PNP0A08:00: _OSC failed (AE_NOT_FOUND); disabling ASPM
[    0.210281] acpi PNP0A08:00: ignoring host bridge window [mem 0x000cc000-0x000cffff] (conflicts with Video ROM [mem 0x000c0000-0x000cedff])
[    0.210285] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-3f] only partially covers this bridge
[    0.210462] PCI host bridge to bus 0000:00
[    0.210465] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.210467] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.210469] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.210471] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.210473] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000c3fff]
[    0.210475] pci_bus 0000:00: root bus resource [mem 0x000c4000-0x000c7fff]
[    0.210476] pci_bus 0000:00: root bus resource [mem 0x000c8000-0x000cbfff]
[    0.210478] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff]
[    0.210480] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
[    0.210482] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
[    0.210484] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff]
[    0.210486] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000e3fff]
[    0.210487] pci_bus 0000:00: root bus resource [mem 0x000e4000-0x000e7fff]
[    0.210489] pci_bus 0000:00: root bus resource [mem 0x000e8000-0x000ebfff]
[    0.210491] pci_bus 0000:00: root bus resource [mem 0x000ec000-0x000effff]
[    0.210493] pci_bus 0000:00: root bus resource [mem 0x80000000-0xf7ffffff]
[    0.210495] pci_bus 0000:00: root bus resource [mem 0xfc000000-0xfed3ffff]
[    0.210497] pci_bus 0000:00: root bus resource [mem 0xfed45000-0xffffffff]
[    0.210508] pci 0000:00:00.0: [1022:9601] type 00 class 0x060000
[    0.210603] pci 0000:00:01.0: [1022:9602] type 01 class 0x060400
[    0.210698] pci 0000:00:05.0: [1022:9605] type 01 class 0x060400
[    0.210733] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
[    0.210770] pci 0000:00:05.0: System wakeup disabled by ACPI
[    0.210801] pci 0000:00:06.0: [1022:9606] type 01 class 0x060400
[    0.210836] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.211610] pci 0000:00:06.0: System wakeup disabled by ACPI
[    0.211713] pci 0000:00:11.0: [1002:4391] type 00 class 0x010601
[    0.211734] pci 0000:00:11.0: reg 0x10: [io  0x4038-0x403f]
[    0.211743] pci 0000:00:11.0: reg 0x14: [io  0x404c-0x404f]
[    0.211752] pci 0000:00:11.0: reg 0x18: [io  0x4030-0x4037]
[    0.211761] pci 0000:00:11.0: reg 0x1c: [io  0x4048-0x404b]
[    0.211770] pci 0000:00:11.0: reg 0x20: [io  0x4010-0x401f]
[    0.211779] pci 0000:00:11.0: reg 0x24: [mem 0x90408000-0x904083ff]
[    0.211936] pci 0000:00:12.0: [1002:4397] type 00 class 0x0c0310
[    0.211949] pci 0000:00:12.0: reg 0x10: [mem 0x90407000-0x90407fff]
[    0.212033] pci 0000:00:12.0: System wakeup disabled by ACPI
[    0.212101] pci 0000:00:12.2: [1002:4396] type 00 class 0x0c0320
[    0.212501] pci 0000:00:12.2: reg 0x10: [mem 0x90408600-0x904086ff]
[    0.214803] pci 0000:00:12.2: supports D1 D2
[    0.214805] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.214843] pci 0000:00:12.2: System wakeup disabled by ACPI
[    0.214876] pci 0000:00:13.0: [1002:4397] type 00 class 0x0c0310
[    0.214889] pci 0000:00:13.0: reg 0x10: [mem 0x90406000-0x90406fff]
[    0.214970] pci 0000:00:13.0: System wakeup disabled by ACPI
[    0.215002] pci 0000:00:13.2: [1002:4396] type 00 class 0x0c0320
[    0.215390] pci 0000:00:13.2: reg 0x10: [mem 0x90408500-0x904085ff]
[    0.217685] pci 0000:00:13.2: supports D1 D2
[    0.217687] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.217725] pci 0000:00:13.2: System wakeup disabled by ACPI
[    0.217792] pci 0000:00:14.0: [1002:4385] type 00 class 0x0c0500
[    0.217943] pci 0000:00:14.2: [1002:4383] type 00 class 0x040300
[    0.217963] pci 0000:00:14.2: reg 0x10: [mem 0x90400000-0x90403fff 64bit]
[    0.218025] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.218117] pci 0000:00:14.3: [1002:439d] type 00 class 0x060100
[    0.218228] pci 0000:00:14.4: [1002:4384] type 01 class 0x060401
[    0.218289] pci 0000:00:14.4: System wakeup disabled by ACPI
[    0.218352] pci 0000:00:14.5: [1002:4399] type 00 class 0x0c0310
[    0.218365] pci 0000:00:14.5: reg 0x10: [mem 0x90405000-0x90405fff]
[    0.218507] pci 0000:00:16.0: [1002:4397] type 00 class 0x0c0310
[    0.218520] pci 0000:00:16.0: reg 0x10: [mem 0x90404000-0x90404fff]
[    0.218627] pci 0000:00:16.2: [1002:4396] type 00 class 0x0c0320
[    0.219016] pci 0000:00:16.2: reg 0x10: [mem 0x90408400-0x904084ff]
[    0.221312] pci 0000:00:16.2: supports D1 D2
[    0.221313] pci 0000:00:16.2: PME# supported from D0 D1 D2 D3hot
[    0.221351] pci 0000:00:16.2: System wakeup disabled by ACPI
[    0.221417] pci 0000:00:18.0: [1022:1200] type 00 class 0x060000
[    0.221472] pci 0000:00:18.1: [1022:1201] type 00 class 0x060000
[    0.221524] pci 0000:00:18.2: [1022:1202] type 00 class 0x060000
[    0.221575] pci 0000:00:18.3: [1022:1203] type 00 class 0x060000
[    0.221628] pci 0000:00:18.4: [1022:1204] type 00 class 0x060000
[    0.221736] pci 0000:01:05.0: [1002:9712] type 00 class 0x030000
[    0.221745] pci 0000:01:05.0: reg 0x10: [mem 0x80000000-0x8fffffff pref]
[    0.221750] pci 0000:01:05.0: reg 0x14: [io  0x3000-0x30ff]
[    0.221755] pci 0000:01:05.0: reg 0x18: [mem 0x90300000-0x9030ffff]
[    0.221765] pci 0000:01:05.0: reg 0x24: [mem 0x90200000-0x902fffff]
[    0.221783] pci 0000:01:05.0: supports D1 D2
[    0.221874] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.221878] pci 0000:00:01.0:   bridge window [io  0x3000-0x3fff]
[    0.221880] pci 0000:00:01.0:   bridge window [mem 0x90200000-0x903fffff]
[    0.221884] pci 0000:00:01.0:   bridge window [mem 0x80000000-0x8fffffff 64bit pref]
[    0.221982] pci 0000:02:00.0: [168c:002b] type 00 class 0x028000
[    0.221999] pci 0000:02:00.0: reg 0x10: [mem 0x90100000-0x9010ffff 64bit]
[    0.222076] pci 0000:02:00.0: supports D1
[    0.222077] pci 0000:02:00.0: PME# supported from D0 D1 D3hot
[    0.228593] pci 0000:00:05.0: PCI bridge to [bus 02]
[    0.228603] pci 0000:00:05.0:   bridge window [mem 0x90100000-0x901fffff]
[    0.228723] pci 0000:03:00.0: [10ec:8136] type 00 class 0x020000
[    0.228739] pci 0000:03:00.0: reg 0x10: [io  0x2000-0x20ff]
[    0.228759] pci 0000:03:00.0: reg 0x18: [mem 0x90010000-0x90010fff 64bit pref]
[    0.228773] pci 0000:03:00.0: reg 0x20: [mem 0x90000000-0x9000ffff 64bit pref]
[    0.228783] pci 0000:03:00.0: reg 0x30: [mem 0xffff0000-0xffffffff pref]
[    0.228833] pci 0000:03:00.0: supports D1 D2
[    0.228835] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.236607] pci 0000:00:06.0: PCI bridge to [bus 03]
[    0.236615] pci 0000:00:06.0:   bridge window [io  0x2000-0x2fff]
[    0.236620] pci 0000:00:06.0:   bridge window [mem 0x90000000-0x900fffff 64bit pref]
[    0.236717] pci 0000:00:14.4: PCI bridge to [bus 04] (subtractive decode)
[    0.236725] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.236728] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.236737] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.236739] pci 0000:00:14.4:   bridge window [mem 0x000c0000-0x000c3fff] (subtractive decode)
[    0.236741] pci 0000:00:14.4:   bridge window [mem 0x000c4000-0x000c7fff] (subtractive decode)
[    0.236743] pci 0000:00:14.4:   bridge window [mem 0x000c8000-0x000cbfff] (subtractive decode)
[    0.236744] pci 0000:00:14.4:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
[    0.236746] pci 0000:00:14.4:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.236748] pci 0000:00:14.4:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.236750] pci 0000:00:14.4:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
[    0.236752] pci 0000:00:14.4:   bridge window [mem 0x000e0000-0x000e3fff] (subtractive decode)
[    0.236754] pci 0000:00:14.4:   bridge window [mem 0x000e4000-0x000e7fff] (subtractive decode)
[    0.236756] pci 0000:00:14.4:   bridge window [mem 0x000e8000-0x000ebfff] (subtractive decode)
[    0.236758] pci 0000:00:14.4:   bridge window [mem 0x000ec000-0x000effff] (subtractive decode)
[    0.236760] pci 0000:00:14.4:   bridge window [mem 0x80000000-0xf7ffffff] (subtractive decode)
[    0.236762] pci 0000:00:14.4:   bridge window [mem 0xfc000000-0xfed3ffff] (subtractive decode)
[    0.236764] pci 0000:00:14.4:   bridge window [mem 0xfed45000-0xffffffff] (subtractive decode)
[    0.237233] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.237299] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.237361] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.237422] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.237471] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.237511] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.237551] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.237590] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.238139] ACPI: \_SB_.PCI0: notify handler is installed
[    0.238199] Found 1 acpi root devices
[    0.238250] ACPI : EC: GPE = 0x5, I/O: command/status = 0x66, data = 0x62
[    0.238361] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
[    0.238363] vgaarb: loaded
[    0.238365] vgaarb: bridge control possible 0000:01:05.0
[    0.238543] SCSI subsystem initialized
[    0.238599] libata version 3.00 loaded.
[    0.238618] ACPI: bus type USB registered
[    0.238634] usbcore: registered new interface driver usbfs
[    0.238643] usbcore: registered new interface driver hub
[    0.238663] usbcore: registered new device driver usb
[    0.238753] PCI: Using ACPI for IRQ routing
[    0.240632] PCI: pci_cache_line_size set to 64 bytes
[    0.240697] e820: reserve RAM buffer [mem 0x0009f800-0x0009ffff]
[    0.240699] e820: reserve RAM buffer [mem 0x6e456000-0x6fffffff]
[    0.240701] e820: reserve RAM buffer [mem 0x6fd3f000-0x6fffffff]
[    0.240703] e820: reserve RAM buffer [mem 0x6ff00000-0x6fffffff]
[    0.240791] NetLabel: Initializing
[    0.240792] NetLabel:  domain hash size = 128
[    0.240793] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.240809] NetLabel:  unlabeled traffic allowed by default
[    0.240882] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.240886] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
[    0.242935] Switched to clocksource hpet
[    0.247702] AppArmor: AppArmor Filesystem Enabled
[    0.247736] pnp: PnP ACPI init
[    0.247752] ACPI: bus type PNP registered
[    0.248051] system 00:00: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.248054] system 00:00: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.248057] system 00:00: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.248059] system 00:00: [mem 0xfed80000-0xfed80fff] has been reserved
[    0.248061] system 00:00: [mem 0xfec10000-0xfec1001f] has been reserved
[    0.248063] system 00:00: [mem 0xfed80000-0xfed80fff] has been reserved
[    0.248067] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.248205] pnp 00:01: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.248243] pnp 00:02: [dma 4]
[    0.248260] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.248288] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.248332] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.248353] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.248385] pnp 00:06: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.248414] pnp 00:07: Plug and Play ACPI device, IDs SYN1e35 SYN1e00 SYN0002 PNP0f13 (active)
[    0.248458] system 00:08: [io  0x0400-0x04cf] could not be reserved
[    0.248461] system 00:08: [io  0x04d0-0x04d1] has been reserved
[    0.248463] system 00:08: [io  0x04d6] has been reserved
[    0.248465] system 00:08: [io  0x0550] has been reserved
[    0.248467] system 00:08: [io  0x0680-0x06ff] has been reserved
[    0.248470] system 00:08: [io  0x077a] has been reserved
[    0.248472] system 00:08: [io  0x0c00-0x0c01] has been reserved
[    0.248474] system 00:08: [io  0x0c14] has been reserved
[    0.248476] system 00:08: [io  0x0c50-0x0c52] has been reserved
[    0.248478] system 00:08: [io  0x0c6c] has been reserved
[    0.248480] system 00:08: [io  0x0c6f] has been reserved
[    0.248482] system 00:08: [io  0x0cd0-0x0cdb] has been reserved
[    0.248485] system 00:08: [io  0x0380-0x0387] has been reserved
[    0.248487] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.248558] system 00:09: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.248561] system 00:09: [mem 0xffe00000-0xffffffff] has been reserved
[    0.248564] system 00:09: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.249001] pnp: PnP ACPI: found 10 devices
[    0.249006] ACPI: bus type PNP unregistered
[    0.254755] pci 0000:03:00.0: no compatible bridge window for [mem 0xffff0000-0xffffffff pref]
[    0.254774] pci 0000:00:05.0: bridge window [io  0x1000-0x0fff] to [bus 02] add_size 1000
[    0.254778] pci 0000:00:05.0: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 02] add_size 200000
[    0.254792] pci 0000:00:05.0: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.254795] pci 0000:00:05.0: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.254802] pci 0000:00:05.0: BAR 15: assigned [mem 0x90500000-0x906fffff 64bit pref]
[    0.254806] pci 0000:00:06.0: BAR 14: assigned [mem 0x90700000-0x907fffff]
[    0.254809] pci 0000:00:05.0: BAR 13: assigned [io  0x1000-0x1fff]
[    0.254812] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.254815] pci 0000:00:01.0:   bridge window [io  0x3000-0x3fff]
[    0.254818] pci 0000:00:01.0:   bridge window [mem 0x90200000-0x903fffff]
[    0.254821] pci 0000:00:01.0:   bridge window [mem 0x80000000-0x8fffffff 64bit pref]
[    0.254825] pci 0000:00:05.0: PCI bridge to [bus 02]
[    0.254827] pci 0000:00:05.0:   bridge window [io  0x1000-0x1fff]
[    0.254830] pci 0000:00:05.0:   bridge window [mem 0x90100000-0x901fffff]
[    0.254832] pci 0000:00:05.0:   bridge window [mem 0x90500000-0x906fffff 64bit pref]
[    0.254836] pci 0000:03:00.0: BAR 6: assigned [mem 0x90020000-0x9002ffff pref]
[    0.254838] pci 0000:00:06.0: PCI bridge to [bus 03]
[    0.254840] pci 0000:00:06.0:   bridge window [io  0x2000-0x2fff]
[    0.254843] pci 0000:00:06.0:   bridge window [mem 0x90700000-0x907fffff]
[    0.254846] pci 0000:00:06.0:   bridge window [mem 0x90000000-0x900fffff 64bit pref]
[    0.254849] pci 0000:00:14.4: PCI bridge to [bus 04]
[    0.254861] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.254863] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.254865] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.254867] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff]
[    0.254869] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff]
[    0.254871] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff]
[    0.254873] pci_bus 0000:00: resource 10 [mem 0x000d0000-0x000d3fff]
[    0.254874] pci_bus 0000:00: resource 11 [mem 0x000d4000-0x000d7fff]
[    0.254876] pci_bus 0000:00: resource 12 [mem 0x000d8000-0x000dbfff]
[    0.254878] pci_bus 0000:00: resource 13 [mem 0x000dc000-0x000dffff]
[    0.254880] pci_bus 0000:00: resource 14 [mem 0x000e0000-0x000e3fff]
[    0.254881] pci_bus 0000:00: resource 15 [mem 0x000e4000-0x000e7fff]
[    0.254883] pci_bus 0000:00: resource 16 [mem 0x000e8000-0x000ebfff]
[    0.254885] pci_bus 0000:00: resource 17 [mem 0x000ec000-0x000effff]
[    0.254887] pci_bus 0000:00: resource 18 [mem 0x80000000-0xf7ffffff]
[    0.254889] pci_bus 0000:00: resource 19 [mem 0xfc000000-0xfed3ffff]
[    0.254891] pci_bus 0000:00: resource 20 [mem 0xfed45000-0xffffffff]
[    0.254893] pci_bus 0000:01: resource 0 [io  0x3000-0x3fff]
[    0.254895] pci_bus 0000:01: resource 1 [mem 0x90200000-0x903fffff]
[    0.254897] pci_bus 0000:01: resource 2 [mem 0x80000000-0x8fffffff 64bit pref]
[    0.254899] pci_bus 0000:02: resource 0 [io  0x1000-0x1fff]
[    0.254901] pci_bus 0000:02: resource 1 [mem 0x90100000-0x901fffff]
[    0.254903] pci_bus 0000:02: resource 2 [mem 0x90500000-0x906fffff 64bit pref]
[    0.254905] pci_bus 0000:03: resource 0 [io  0x2000-0x2fff]
[    0.254907] pci_bus 0000:03: resource 1 [mem 0x90700000-0x907fffff]
[    0.254909] pci_bus 0000:03: resource 2 [mem 0x90000000-0x900fffff 64bit pref]
[    0.254911] pci_bus 0000:04: resource 4 [io  0x0000-0x0cf7]
[    0.254913] pci_bus 0000:04: resource 5 [io  0x0d00-0xffff]
[    0.254914] pci_bus 0000:04: resource 6 [mem 0x000a0000-0x000bffff]
[    0.254916] pci_bus 0000:04: resource 7 [mem 0x000c0000-0x000c3fff]
[    0.254918] pci_bus 0000:04: resource 8 [mem 0x000c4000-0x000c7fff]
[    0.254920] pci_bus 0000:04: resource 9 [mem 0x000c8000-0x000cbfff]
[    0.254928] pci_bus 0000:04: resource 10 [mem 0x000d0000-0x000d3fff]
[    0.254930] pci_bus 0000:04: resource 11 [mem 0x000d4000-0x000d7fff]
[    0.254932] pci_bus 0000:04: resource 12 [mem 0x000d8000-0x000dbfff]
[    0.254934] pci_bus 0000:04: resource 13 [mem 0x000dc000-0x000dffff]
[    0.254935] pci_bus 0000:04: resource 14 [mem 0x000e0000-0x000e3fff]
[    0.254937] pci_bus 0000:04: resource 15 [mem 0x000e4000-0x000e7fff]
[    0.254939] pci_bus 0000:04: resource 16 [mem 0x000e8000-0x000ebfff]
[    0.254941] pci_bus 0000:04: resource 17 [mem 0x000ec000-0x000effff]
[    0.254943] pci_bus 0000:04: resource 18 [mem 0x80000000-0xf7ffffff]
[    0.254945] pci_bus 0000:04: resource 19 [mem 0xfc000000-0xfed3ffff]
[    0.254947] pci_bus 0000:04: resource 20 [mem 0xfed45000-0xffffffff]
[    0.254988] NET: Registered protocol family 2
[    0.255171] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.255233] TCP bind hash table entries: 16384 (order: 6, 262144 bytes)
[    0.255311] TCP: Hash tables configured (established 16384 bind 16384)
[    0.255357] TCP: reno registered
[    0.255363] UDP hash table entries: 1024 (order: 3, 32768 bytes)
[    0.255381] UDP-Lite hash table entries: 1024 (order: 3, 32768 bytes)
[    0.255472] NET: Registered protocol family 1
[    0.255484] pci 0000:00:01.0: MSI quirk detected; subordinate MSI disabled
[    1.042576] pci 0000:01:05.0: Boot video device
[    1.042591] PCI: CLS 64 bytes, default 64
[    1.042665] Trying to unpack rootfs image as initramfs...
[    1.393965] Freeing initrd memory: 18732K (ffff880035b5a000 - ffff880036da5000)
[    1.394306] Simple Boot Flag at 0x44 set to 0x1
[    1.394342] LVT offset 1 assigned for vector 0x400
[    1.394347] IBS: LVT offset 1 assigned
[    1.394370] perf: AMD IBS detected (0x0000001f)
[    1.394413] microcode: CPU0: patch_level=0x010000c8
[    1.394458] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.394460] Scanning for low memory corruption every 60 seconds
[    1.394704] Initialise system trusted keyring
[    1.394756] audit: initializing netlink socket (disabled)
[    1.394770] type=2000 audit(1417728574.284:1): initialized
[    1.423496] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.424617] zbud: loaded
[    1.424769] VFS: Disk quotas dquot_6.5.2
[    1.424819] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.425343] fuse init (API version 7.22)
[    1.425407] msgmni has been set to 3484
[    1.425463] Key type big_key registered
[    1.425736] Key type asymmetric registered
[    1.425738] Asymmetric key parser 'x509' registered
[    1.425771] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    1.425800] io scheduler noop registered
[    1.425802] io scheduler deadline registered (default)
[    1.425827] io scheduler cfq registered
[    1.426126] pcieport 0000:00:05.0: irq 40 for MSI/MSI-X
[    1.426260] pcieport 0000:00:06.0: irq 41 for MSI/MSI-X
[    1.426310] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.426324] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.426365] vesafb: mode is 1366x768x32, linelength=5504, pages=0
[    1.426366] vesafb: scrolling: redraw
[    1.426368] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[    1.426598] vesafb: framebuffer at 0x80000000, mapped to 0xffffc90004400000, using 4160k, total 4160k
[    1.590100] Console: switching to colour frame buffer device 170x48
[    1.753107] fb0: VESA VGA frame buffer device
[    1.753251] ipmi message handler version 39.2
[    1.753927] ACPI: AC Adapter [ACAD] (on-line)
[    1.754048] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    1.754053] ACPI: Power Button [PWRB]
[    1.754102] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    1.754477] ACPI: Lid Switch [LID]
[    1.754563] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    1.754568] ACPI: Power Button [PWRF]
[    1.754611] ACPI: processor limited to max C-state 1
[    1.755079] [Firmware Bug]: Invalid critical threshold (0)
[    1.756618] thermal LNXTHERM:00: registered as thermal_zone0
[    1.756623] ACPI: Thermal Zone [THRM] (29 C)
[    1.756718] GHES: HEST is not enabled!
[    1.756835] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.756927] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.756931] ACPI: Battery Slot [BAT0] (battery absent)
[    1.758056] Linux agpgart interface v0.103
[    1.759259] brd: module loaded
[    1.759899] loop: module loaded
[    1.760281] libphy: Fixed MDIO Bus: probed
[    1.760370] tun: Universal TUN/TAP device driver, 1.6
[    1.760371] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.760422] PPP generic driver version 2.4.2
[    1.760460] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.760463] ehci-pci: EHCI PCI platform driver
[    1.760650] QUIRK: Enable AMD PLL fix
[    1.760676] ehci-pci 0000:00:12.2: EHCI Host Controller
[    1.760682] ehci-pci 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.760689] ehci-pci 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.760700] ehci-pci 0000:00:12.2: debug port 1
[    1.760744] ehci-pci 0000:00:12.2: irq 17, io mem 0x90408600
[    1.769888] ehci-pci 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.769973] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.769975] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.769977] usb usb1: Product: EHCI Host Controller
[    1.769979] usb usb1: Manufacturer: Linux 3.13.0-32-generic ehci_hcd
[    1.769980] usb usb1: SerialNumber: 0000:00:12.2
[    1.770114] hub 1-0:1.0: USB hub found
[    1.770121] hub 1-0:1.0: 5 ports detected
[    1.770434] ehci-pci 0000:00:13.2: EHCI Host Controller
[    1.770440] ehci-pci 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.770443] ehci-pci 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.770454] ehci-pci 0000:00:13.2: debug port 1
[    1.770487] ehci-pci 0000:00:13.2: irq 17, io mem 0x90408500
[    1.781879] ehci-pci 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.781951] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.781953] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.781954] usb usb2: Product: EHCI Host Controller
[    1.781956] usb usb2: Manufacturer: Linux 3.13.0-32-generic ehci_hcd
[    1.781958] usb usb2: SerialNumber: 0000:00:13.2
[    1.782078] hub 2-0:1.0: USB hub found
[    1.782085] hub 2-0:1.0: 5 ports detected
[    1.782381] ehci-pci 0000:00:16.2: EHCI Host Controller
[    1.782386] ehci-pci 0000:00:16.2: new USB bus registered, assigned bus number 3
[    1.782390] ehci-pci 0000:00:16.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.782401] ehci-pci 0000:00:16.2: debug port 1
[    1.782433] ehci-pci 0000:00:16.2: irq 17, io mem 0x90408400
[    1.793870] ehci-pci 0000:00:16.2: USB 2.0 started, EHCI 1.00
[    1.793936] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    1.793938] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.793940] usb usb3: Product: EHCI Host Controller
[    1.793942] usb usb3: Manufacturer: Linux 3.13.0-32-generic ehci_hcd
[    1.793944] usb usb3: SerialNumber: 0000:00:16.2
[    1.794074] hub 3-0:1.0: USB hub found
[    1.794084] hub 3-0:1.0: 4 ports detected
[    1.794245] ehci-platform: EHCI generic platform driver
[    1.794257] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.794258] ohci-pci: OHCI PCI platform driver
[    1.794407] ohci-pci 0000:00:12.0: OHCI PCI host controller
[    1.794412] ohci-pci 0000:00:12.0: new USB bus registered, assigned bus number 4
[    1.794438] ohci-pci 0000:00:12.0: irq 18, io mem 0x90407000
[    1.853845] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    1.853850] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.853851] usb usb4: Product: OHCI PCI host controller
[    1.853853] usb usb4: Manufacturer: Linux 3.13.0-32-generic ohci_hcd
[    1.853855] usb usb4: SerialNumber: 0000:00:12.0
[    1.853997] hub 4-0:1.0: USB hub found
[    1.854041] hub 4-0:1.0: 5 ports detected
[    1.854317] ohci-pci 0000:00:13.0: OHCI PCI host controller
[    1.854322] ohci-pci 0000:00:13.0: new USB bus registered, assigned bus number 5
[    1.854338] ohci-pci 0000:00:13.0: irq 18, io mem 0x90406000
[    1.913798] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    1.913802] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.913804] usb usb5: Product: OHCI PCI host controller
[    1.913806] usb usb5: Manufacturer: Linux 3.13.0-32-generic ohci_hcd
[    1.913808] usb usb5: SerialNumber: 0000:00:13.0
[    1.913940] hub 5-0:1.0: USB hub found
[    1.913953] hub 5-0:1.0: 5 ports detected
[    1.914202] ohci-pci 0000:00:14.5: OHCI PCI host controller
[    1.914209] ohci-pci 0000:00:14.5: new USB bus registered, assigned bus number 6
[    1.914226] ohci-pci 0000:00:14.5: irq 18, io mem 0x90405000
[    1.973830] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
[    1.973835] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.973837] usb usb6: Product: OHCI PCI host controller
[    1.973838] usb usb6: Manufacturer: Linux 3.13.0-32-generic ohci_hcd
[    1.973840] usb usb6: SerialNumber: 0000:00:14.5
[    1.973982] hub 6-0:1.0: USB hub found
[    1.973994] hub 6-0:1.0: 2 ports detected
[    1.974223] ohci-pci 0000:00:16.0: OHCI PCI host controller
[    1.974229] ohci-pci 0000:00:16.0: new USB bus registered, assigned bus number 7
[    1.974246] ohci-pci 0000:00:16.0: irq 18, io mem 0x90404000
[    2.033711] usb usb7: New USB device found, idVendor=1d6b, idProduct=0001
[    2.033716] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.033718] usb usb7: Product: OHCI PCI host controller
[    2.033720] usb usb7: Manufacturer: Linux 3.13.0-32-generic ohci_hcd
[    2.033721] usb usb7: SerialNumber: 0000:00:16.0
[    2.033869] hub 7-0:1.0: USB hub found
[    2.033883] hub 7-0:1.0: 4 ports detected
[    2.034017] ohci-platform: OHCI generic platform driver
[    2.034028] uhci_hcd: USB Universal Host Controller Interface driver
[    2.034094] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.053771] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.053777] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.053873] mousedev: PS/2 mouse device common for all mice
[    2.055290] rtc_cmos 00:04: RTC can wake from S4
[    2.055390] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    2.055415] rtc_cmos 00:04: alarms up to one day, 114 bytes nvram, hpet irqs
[    2.055484] device-mapper: uevent: version 1.0.3
[    2.055531] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: [email]dm-devel@redhat.com[/email]
[    2.055538] ledtrig-cpu: registered to indicate activity on CPUs
[    2.055643] TCP: cubic registered
[    2.055730] NET: Registered protocol family 10
[    2.055914] NET: Registered protocol family 17
[    2.055924] Key type dns_resolver registered
[    2.056082] Loading compiled-in X.509 certificates
[    2.057264] Loaded X.509 cert 'Magrathea: Glacier signing key: 5e3c0f9ca6e36543535fa2bb5b709e84f16da7c7'
[    2.057277] registered taskstats version 1
[    2.059811] Key type trusted registered
[    2.062145] Key type encrypted registered
[    2.064415] AppArmor: AppArmor sha1 policy hashing enabled
[    2.064420] IMA: No TPM chip found, activating TPM-bypass!
[    2.064662] regulator-dummy: disabling
[    2.064704]   Magic number: 10:491:499
[    2.064805] rtc_cmos 00:04: setting system clock to 2014-12-04 21:29:35 UTC (1417728575)
[    2.064903] acpi-cpufreq: overriding BIOS provided _PSD data
[    2.064935] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.064936] EDD information not available.
[    2.064975] PM: Hibernation image not present or could not be loaded.
[    2.066708] Freeing unused kernel memory: 1336K (ffffffff81d1f000 - ffffffff81e6d000)
[    2.066712] Write protecting the kernel read-only data: 12288k
[    2.069356] Freeing unused kernel memory: 816K (ffff880001734000 - ffff880001800000)
[    2.071645] Freeing unused kernel memory: 696K (ffff880001b52000 - ffff880001c00000)
[    2.080668] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    2.097851] systemd-udevd[97]: starting version 204
[    2.147717] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.147733] r8169 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[    2.147975] r8169 0000:03:00.0: irq 42 for MSI/MSI-X
[    2.148140] r8169 0000:03:00.0 eth0: RTL8102e at 0xffffc9000036c000, 78:ac:c0:52:16:ac, XID 04e00000 IRQ 42
[    2.152544] ahci 0000:00:11.0: version 3.0
[    2.152796] ahci 0000:00:11.0: AHCI 0001.0200 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[    2.152800] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
[    2.156025] scsi0 : ahci
[    2.159650] scsi1 : ahci
[    2.159723] ata1: SATA max UDMA/133 abar m1024@0x90408000 port 0x90408100 irq 19
[    2.159727] ata2: SATA max UDMA/133 abar m1024@0x90408000 port 0x90408180 irq 19
[    2.293508] usb 4-1: new low-speed USB device number 2 using ohci-pci
[    2.393423] tsc: Refined TSC clocksource calibration: 2294.255 MHz
[    2.460479] usb 4-1: New USB device found, idVendor=093a, idProduct=2510
[    2.460485] usb 4-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.460487] usb 4-1: Product: USB OPTICAL MOUSE
[    2.460489] usb 4-1: Manufacturer: PIXART
[    2.469649] hidraw: raw HID events driver (C) Jiri Kosina
[    2.476946] usbcore: registered new interface driver usbhid
[    2.476950] usbhid: USB HID core driver
[    2.479543] input: PIXART USB OPTICAL MOUSE as /devices/pci0000:00/0000:00:12.0/usb4/4-1/4-1:1.0/input/input6
[    2.480374] hid-generic 0003:093A:2510.0001: input,hidraw0: USB HID v1.11 Mouse [PIXART USB OPTICAL MOUSE] on usb-0000:00:12.0-1/input0
[    2.649244] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.651850] ata1.00: ATA-7: IMATION-MAC25-128, VER2.009, max UDMA/133
[    2.651856] ata1.00: 253754928 sectors, multi 1: LBA48 
[    2.653238] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.655249] ata2.00: ATAPI: hp       CDDVDW TS-L633R, 0200, max UDMA/100
[    2.655267] ata1.00: configured for UDMA/133
[    2.655405] scsi 0:0:0:0: Direct-Access     ATA      IMATION-MAC25-12 VER2 PQ: 0 ANSI: 5
[    2.655627] sd 0:0:0:0: [sda] 253754928 512-byte logical blocks: (129 GB/120 GiB)
[    2.655676] sd 0:0:0:0: [sda] Write Protect is off
[    2.655678] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.655699] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.655894] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.658522]  sda: sda1 sda2 < sda5 >
[    2.658865] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.659862] ata2.00: configured for UDMA/100
[    2.663685] scsi 1:0:0:0: CD-ROM            hp       CDDVDW TS-L633R  0200 PQ: 0 ANSI: 5
[    2.671532] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.671537] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.671662] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.671714] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.908996] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    3.141850] random: init urandom read with 42 bits of entropy available
[    3.241481] init: plymouth-upstart-bridge main process (152) terminated with status 1
[    3.241531] init: plymouth-upstart-bridge main process ended, respawning
[    3.251726] init: plymouth-upstart-bridge main process (163) terminated with status 1
[    3.251777] init: plymouth-upstart-bridge main process ended, respawning
[    3.265949] init: plymouth-upstart-bridge main process (165) terminated with status 1
[    3.265981] init: plymouth-upstart-bridge main process ended, respawning
[    3.275320] init: plymouth-upstart-bridge main process (167) terminated with status 1
[    3.275336] init: plymouth-upstart-bridge main process ended, respawning
[    3.290647] init: plymouth-upstart-bridge main process (170) terminated with status 1
[    3.290664] init: plymouth-upstart-bridge main process ended, respawning
[    3.392716] Switched to clocksource tsc
[    3.486310] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.4, id: 0x1e0b1, caps: 0xd04773/0xe40000/0xa0400, board id: 3655, fw id: 639099
[    3.583234] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input5
[    3.824433] Adding 1827836k swap on /dev/sda5.  Priority:-1 extents:1 across:1827836k SSFS
[    3.956747] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    4.123465] systemd-udevd[279]: starting version 204
[    4.323271] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    4.399605] cfg80211: Calling CRDA to update world regulatory domain
[    4.413051] [drm] Initialized drm 1.1.0 20060810
[    4.438073] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[    4.501722] lp: driver loaded but no devices found
[    4.533592] ppdev: user-space parallel port driver
[    4.573286] acpi device:04: registered as cooling_device1
[    4.586332] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input7
[    4.586730] wmi: Mapper loaded
[    4.596503] type=1400 audit(1417728578.028:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=311 comm="apparmor_parser"
[    4.596513] type=1400 audit(1417728578.028:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=311 comm="apparmor_parser"
[    4.596517] type=1400 audit(1417728578.028:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=311 comm="apparmor_parser"
[    4.597083] type=1400 audit(1417728578.028:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=311 comm="apparmor_parser"
[    4.597088] type=1400 audit(1417728578.028:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=311 comm="apparmor_parser"
[    4.597376] type=1400 audit(1417728578.028:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=311 comm="apparmor_parser"
[    4.708524] ACPI Warning: 0x0000000000000b00-0x0000000000000b07 SystemIO conflicts with Region \_SB_.PCI0.SMBS.SMBI 1 (20131115/utaddress-251)
[    4.708532] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    4.731815] sp5100_tco: SP5100/SB800 TCO WatchDog Timer Driver v0.05
[    4.738312] sp5100_tco: PCI Revision ID: 0x42
[    4.738389] sp5100_tco: Using 0xfed80b00 for watchdog MMIO address
[    4.738402] sp5100_tco: Last reboot was not triggered by watchdog.
[    4.742537] sp5100_tco: initialized (0xffffc900043c4b00). heartbeat=60 sec (nowayout=0)
[    4.753551] MCE: In-kernel MCE decoding enabled.
[    4.773861] [drm] radeon kernel modesetting enabled.
[    4.773946] checking generic (80000000 410000) vs hw (80000000 10000000)
[    4.773948] fb: conflicting fb hw usage radeondrmfb vs VESA VGA - removing generic driver
[    4.773972] Console: switching to colour dummy device 80x25
[    4.774522] [drm] initializing kernel modesetting (RS880 0x1002:0x9712 0x103C:0x1604).
[    4.774541] [drm] register mmio base: 0x90300000
[    4.774542] [drm] register mmio size: 65536
[    4.774609] ATOM BIOS: HP_JoYaHeWi
[    4.774680] radeon 0000:01:05.0: VRAM: 256M 0x00000000C0000000 - 0x00000000CFFFFFFF (256M used)
[    4.774682] radeon 0000:01:05.0: GTT: 512M 0x00000000A0000000 - 0x00000000BFFFFFFF
[    4.774687] [drm] Detected VRAM RAM=256M, BAR=256M
[    4.774689] [drm] RAM width 32bits DDR
[    4.780127] EDAC MC: Ver: 3.0.0
[    4.784105] [TTM] Zone  kernel: Available graphics memory: 893432 kiB
[    4.784110] [TTM] Initializing pool allocator
[    4.784119] [TTM] Initializing DMA pool allocator
[    4.784145] [drm] radeon: 256M of VRAM memory ready
[    4.784147] [drm] radeon: 512M of GTT memory ready.
[    4.784162] [drm] Loading RS780 Microcode
[    4.855673] ath: phy0: Enable LNA combining
[    4.856280] AMD64 EDAC driver v3.4.0
[    4.856324] EDAC amd64: DRAM ECC disabled.
[    4.856327] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[    4.856327]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[    4.856327]  (Note that use of the override may cause unknown side effects.)
[    4.875536] ath: phy0: ASPM enabled: 0x43
[    4.875543] ath: EEPROM regdomain: 0x60
[    4.875545] ath: EEPROM indicates we should expect a direct regpair map
[    4.875548] ath: Country alpha2 being used: 00
[    4.875549] ath: Regpair used: 0x60
[    4.935762] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[    4.936356] ieee80211 phy0: Atheros AR9285 Rev:2 mem=0xffffc90004400000, irq=17
[    5.025386] [drm] GART: num cpu pages 131072, num gpu pages 131072
[    5.043433] [drm] PCIE GART of 512M enabled (table at 0x00000000C0040000).
[    5.056054] kvm: disabled by bios
[    5.084580] radeon 0000:01:05.0: WB enabled
[    5.084588] radeon 0000:01:05.0: fence driver on ring 0 use gpu addr 0x00000000a0000c00 and cpu addr 0xffff880069bf3c00
[    5.084591] radeon 0000:01:05.0: fence driver on ring 3 use gpu addr 0x00000000a0000c0c and cpu addr 0xffff880069bf3c0c
[    5.084595] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    5.084596] [drm] Driver supports precise vblank timestamp query.
[    5.084613] [drm] radeon: irq initialized.
[    5.139937] [drm] ring test on 0 succeeded in 1 usecs
[    5.140000] [drm] ring test on 3 succeeded in 1 usecs
[    5.140110] [drm] Enabling audio 0 support
[    5.140129] [drm] ib test on ring 0 succeeded in 0 usecs
[    5.140145] [drm] ib test on ring 3 succeeded in 0 usecs
[    5.140720] [drm] radeon atom DIG backlight initialized
[    5.140723] [drm] Radeon Display Connectors
[    5.140725] [drm] Connector 0:
[    5.140726] [drm]   VGA-1
[    5.140728] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[    5.140729] [drm]   Encoders:
[    5.140730] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[    5.140731] [drm] Connector 1:
[    5.140732] [drm]   LVDS-1
[    5.140734] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
[    5.140734] [drm]   Encoders:
[    5.140735] [drm]     LCD1: INTERNAL_KLDSCP_LVTMA
[    5.140736] [drm] Connector 2:
[    5.140737] [drm]   HDMI-A-1
[    5.140738] [drm]   HPD1
[    5.140740] [drm]   DDC: 0x7e20 0x7e20 0x7e24 0x7e24 0x7e28 0x7e28 0x7e2c 0x7e2c
[    5.140741] [drm]   Encoders:
[    5.140742] [drm]     DFP1: INTERNAL_UNIPHY
[    5.140824] [drm] radeon: power management initialized
[    5.629292] hda-intel 0000:00:14.2: Using LPIB position fix
[    5.649264] hda-intel 0000:00:14.2: Enable sync_write for stable communication
[    5.695528] SKU: Nid=0x1d sku_cfg=0x40079a2d
[    5.695533] SKU: port_connectivity=0x1
[    5.695534] SKU: enable_pcbeep=0x0
[    5.695535] SKU: check_sum=0x00000007
[    5.695536] SKU: customization=0x0000009a
[    5.695537] SKU: external_amp=0x5
[    5.695538] SKU: platform_type=0x1
[    5.695539] SKU: swap=0x0
[    5.695540] SKU: override=0x1
[    5.695831] autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[    5.695833]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    5.695835]    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
[    5.695836]    mono: mono_out=0x0
[    5.695836]    inputs:
[    5.695838]      Internal Mic=0x19
[    5.695840]      Mic=0x18
[    5.695841] realtek: No valid SSID, checking pincfg 0x40079a2d for NID 0x1d
[    5.695842] realtek: Enabling init ASM_ID=0x9a2d CODEC_ID=10ec0270
[    5.708587] input: HP WMI hotkeys as /devices/virtual/input/input8
[    5.766090] cfg80211: World regulatory domain updated:
[    5.766096] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    5.766099] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    5.766101] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    5.766103] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    5.766104] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    5.766105] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    5.899142] input: HDA ATI SB Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input10
[    5.901651] input: HDA ATI SB Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input9
[    6.130593] [drm] fb mappable at 0x80141000
[    6.130597] [drm] vram apper at 0x80000000
[    6.130599] [drm] size 4325376
[    6.130600] [drm] fb depth is 24
[    6.130601] [drm]    pitch is 5632
[    6.130804] fbcon: radeondrmfb (fb0) is primary device
[    6.178662] Console: switching to colour frame buffer device 170x48
[    6.189903] radeon 0000:01:05.0: fb0: radeondrmfb frame buffer device
[    6.189905] radeon 0000:01:05.0: registered panic notifier
[    6.190022] [drm] Initialized radeon 2.36.0 20080528 for 0000:01:05.0 on minor 0
[    8.115333] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[    8.251508] random: nonblocking pool is initialized
[    8.865801] init: failsafe main process (584) killed by TERM signal
[    9.227643] Bluetooth: Core ver 2.17
[    9.227673] NET: Registered protocol family 31
[    9.227675] Bluetooth: HCI device and connection manager initialized
[    9.228291] Bluetooth: HCI socket layer initialized
[    9.228297] Bluetooth: L2CAP socket layer initialized
[    9.228305] Bluetooth: SCO socket layer initialized
[    9.259041] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    9.259091] Bluetooth: BNEP filters: protocol multicast
[    9.259388] Bluetooth: BNEP socket layer initialized
[    9.385623] Bluetooth: RFCOMM TTY layer initialized
[    9.385638] Bluetooth: RFCOMM socket layer initialized
[    9.385647] Bluetooth: RFCOMM ver 1.11
[    9.675227] type=1400 audit(1417728583.108:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=726 comm="apparmor_parser"
[    9.675238] type=1400 audit(1417728583.108:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=726 comm="apparmor_parser"
[    9.675769] type=1400 audit(1417728583.108:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=726 comm="apparmor_parser"
[    9.898193] init: samba-ad-dc main process (696) terminated with status 1
[    9.957320] type=1400 audit(1417728583.392:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=790 comm="apparmor_parser"
[    9.957330] type=1400 audit(1417728583.392:12): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=790 comm="apparmor_parser"
[    9.957694] type=1400 audit(1417728583.392:13): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="chromium" pid=790 comm="apparmor_parser"
[    9.985194] type=1400 audit(1417728583.420:14): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=793 comm="apparmor_parser"
[    9.985205] type=1400 audit(1417728583.420:15): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=793 comm="apparmor_parser"
[    9.985210] type=1400 audit(1417728583.420:16): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=793 comm="apparmor_parser"
[    9.985755] type=1400 audit(1417728583.420:17): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=793 comm="apparmor_parser"
[   10.017843] init: cups main process (733) killed by HUP signal
[   10.017858] init: cups main process ended, respawning
[   10.179124] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   10.183640] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   10.196735] r8169 0000:03:00.0 eth0: link down
[   10.199688] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   10.202954] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready

---

