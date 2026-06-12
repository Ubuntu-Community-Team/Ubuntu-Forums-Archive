---
title: "Started getting lots of boot issues. No idea what to do."
date: 2012-12-26
forum: General Help
---

### Post by kaldor on 2012-12-26
[SIZE=3][COLOR=DarkRed]*To readers: If weird stuff starts happening on your PC, check your RAM. Run Memtest. Even if it shows no Failures, reseat or remove the RAM just in case. *[/COLOR][/SIZE]

Ubuntu 12.04.1 LTS x64

I've been around here for years and I haven't seen the likes of this before. I have no idea what's going on and I need help getting this resolved :(

I did not make any changes to packages/configurations at all. I just booted up my PC like always. 

As soon as I select Ubuntu in GRUB (or just let it do so automatically), I get varying following error messages. Sometimes it instantly throws up a kernel "oops", other times it gets halfway through boot, etc. This time the boot succeeded, but desktop refused to load. 

In recovery mode, the boot does not finish (stops at loading an input device related to audio).

Older kernel sometimes gets me to a desktop, but then things frequently crash, are slow, and I cannot really do anything.

I ran Memtest for 10 minutes; nothing showed up negatively there. Windows 7 partition is working as usual.

As I was typing this, a load of cryptic things popped up on the screen with "Fixing recursive fault but reboot is needed!" at the end.

I'm willing to get any information that is needed. 

Dmesg:

```
$ cat /var/log/dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-35-generic (buildd@allspice) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #55-Ubuntu SMP Wed Dec 5 17:42:16 UTC 2012 (Ubuntu 3.2.0-35.55-generic 3.2.34)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-35-generic root=UUID=b615a0a8-be18-43c5-8395-6bc4c55719d3 ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009a400 (usable)
[    0.000000]  BIOS-e820: 000000000009a400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cffb0000 (usable)
[    0.000000]  BIOS-e820: 00000000cffb0000 - 00000000cffbe000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cffbe000 - 00000000cffe0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cffe0000 - 00000000d0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000330000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI present.
[    0.000000] DMI: Hewlett-Packard p7-1038/2AB1 , BIOS 6.06 03/22/2011
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x330000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
[    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
[    0.000000]   2 base 0000C0000000 mask FFFFF0000000 write-back
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 0000000330000000 aka 13056M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000d0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xcffb0 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Base memory trampoline at [ffff880000095000] 95000 size 20480
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: 0000000000000000-00000000cffb0000
[    0.000000]  0000000000 - 00c0000000 page 1G
[    0.000000]  00c0000000 - 00cfe00000 page 2M
[    0.000000]  00cfe00000 - 00cffb0000 page 4k
[    0.000000] kernel direct mapping tables up to cffb0000 @ 1fffd000-20000000
[    0.000000] init_memory_mapping: 0000000100000000-0000000330000000
[    0.000000]  0100000000 - 0300000000 page 1G
[    0.000000]  0300000000 - 0330000000 page 2M
[    0.000000] kernel direct mapping tables up to 330000000 @ cffae000-cffb0000
[    0.000000] RAMDISK: 364d6000 - 37263000
[    0.000000] ACPI: RSDP 00000000000fb050 00024 (v02 HPQOEM)
[    0.000000] ACPI: XSDT 00000000cffb0100 0006C (v01 HPQOEM SLIC-CPC 20110322 MSFT 00000097)
[    0.000000] ACPI: FACP 00000000cffb0290 000F4 (v03 HPQOEM SLIC-CPC 20110322 MSFT 00000097)
[    0.000000] ACPI Warning: Optional field Pm2ControlBlock has zero address or length: 0x0000000000000000/0x1 (20110623/tbfadt-560)
[    0.000000] ACPI: DSDT 00000000cffb05d0 04AB6 (v01 HPQOEM SLIC-CPC 00000322 INTL 20051117)
[    0.000000] ACPI: FACS 00000000cffbe000 00040
[    0.000000] ACPI: APIC 00000000cffb0390 0007C (v01 HPQOEM SLIC-CPC 20110322 MSFT 00000097)
[    0.000000] ACPI: MCFG 00000000cffb0410 0003C (v01 HPQOEM SLIC-CPC 20110322 MSFT 00000097)
[    0.000000] ACPI: SLIC 00000000cffb0450 00176 (v01 HPQOEM SLIC-CPC 00000001 MSFT 00000001)
[    0.000000] ACPI: OEMB 00000000cffbe040 00072 (v01 HPQOEM SLIC-CPC 20110322 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000cffba6b0 00843 (v01 HPQOEM SLIC-CPC 00000001 INTL 20051117)
[    0.000000] ACPI: SRAT 00000000cffbaf00 00108 (v03 HPQOEM SLIC-CPC 00000002 AMD  00000001)
[    0.000000] ACPI: HPET 00000000cffbb010 00038 (v01 HPQOEM SLIC-CPC 20110322 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000cffbb050 00DA4 (v01 HPQOEM SLIC-CPC 00000001 AMD  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] SRAT: PXM 0 -> APIC 0x00 -> Node 0
[    0.000000] SRAT: PXM 0 -> APIC 0x01 -> Node 0
[    0.000000] SRAT: PXM 0 -> APIC 0x02 -> Node 0
[    0.000000] SRAT: PXM 0 -> APIC 0x03 -> Node 0
[    0.000000] SRAT: PXM 0 -> APIC 0x04 -> Node 0
[    0.000000] SRAT: PXM 0 -> APIC 0x05 -> Node 0
[    0.000000] SRAT: Node 0 PXM 0 0-a0000
[    0.000000] SRAT: Node 0 PXM 0 100000-d0000000
[    0.000000] SRAT: Node 0 PXM 0 100000000-330000000
[    0.000000] NUMA: Node 0 [0,a0000) + [100000,d0000000) -> [0,d0000000)
[    0.000000] NUMA: Node 0 [0,d0000000) + [100000000,330000000) -> [0,330000000)
[    0.000000] Initmem setup node 0 0000000000000000-0000000330000000
[    0.000000]   NODE_DATA [000000032fffb000 - 000000032fffffff]
[    0.000000]  [ffffea0000000000-ffffea000cbfffff] PMD -> [ffff880323600000-ffff88032f5fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00330000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009a
[    0.000000]     0: 0x00000100 -> 0x000cffb0
[    0.000000]     0: 0x00100000 -> 0x00330000
[    0.000000] On node 0 totalpages: 3145530
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 5 pages reserved
[    0.000000]   DMA zone: 3909 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 16320 pages used for memmap
[    0.000000]   DMA32 zone: 831472 pages, LIFO batch:31
[    0.000000]   Normal zone: 35840 pages used for memmap
[    0.000000]   Normal zone: 2257920 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x05] enabled)
[    0.000000] ACPI: IOAPIC (id[0x06] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 6, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000
[    0.000000] SMP: Allowing 6 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009a000 - 000000000009b000
[    0.000000] PM: Registered nosave memory: 000000000009b000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000cffb0000 - 00000000cffbe000
[    0.000000] PM: Registered nosave memory: 00000000cffbe000 - 00000000cffe0000
[    0.000000] PM: Registered nosave memory: 00000000cffe0000 - 00000000d0000000
[    0.000000] PM: Registered nosave memory: 00000000d0000000 - 00000000fff00000
[    0.000000] PM: Registered nosave memory: 00000000fff00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at d0000000 (gap: d0000000:2ff00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:6 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88032fc00000 s83136 r8192 d23360 u262144
[    0.000000] pcpu-alloc: s83136 r8192 d23360 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 - - 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 3093301
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-35-generic root=UUID=b615a0a8-be18-43c5-8395-6bc4c55719d3 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Node 0: aperture @ 5a40000000 size 32 MB
[    0.000000] Aperture beyond 4GB. Ignoring.
[    0.000000] Your BIOS doesn't leave a aperture memory hole
[    0.000000] Please enable the IOMMU option in the BIOS setup
[    0.000000] This costs you 64 MB of RAM
[    0.000000] Mapping aperture over 65536 KB of RAM @ c4000000
[    0.000000] PM: Registered nosave memory: 00000000c4000000 - 00000000c8000000
[    0.000000] Memory: 12223548k/13369344k available (6569k kernel code, 787224k absent, 358572k reserved, 6634k data, 924k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=6, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:728 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 100663296 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2892.886 MHz processor.
[    0.004003] Calibrating delay loop (skipped), value calculated using timer frequency.. 5785.77 BogoMIPS (lpj=11571544)
[    0.004007] pid_max: default: 32768 minimum: 301
[    0.004024] Security Framework initialized
[    0.004035] AppArmor: AppArmor initialized
[    0.004036] Yama: becoming mindful.
[    0.004874] Dentry cache hash table entries: 2097152 (order: 12, 16777216 bytes)
[    0.010610] Inode-cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.012801] Mount-cache hash table entries: 256
[    0.012902] Initializing cgroup subsys cpuacct
[    0.012907] Initializing cgroup subsys memory
[    0.012914] Initializing cgroup subsys devices
[    0.012915] Initializing cgroup subsys freezer
[    0.012917] Initializing cgroup subsys blkio
[    0.012922] Initializing cgroup subsys perf_event
[    0.012943] tseg: 0000000000
[    0.012954] CPU: Physical Processor ID: 0
[    0.012955] CPU: Processor Core ID: 0
[    0.012957] mce: CPU supports 6 MCE banks
[    0.014085] ACPI: Core revision 20110623
[    0.016011] ftrace: allocating 27030 entries in 107 pages
[    0.020409] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.060417] CPU0: AMD Phenom(tm) II X6 1065T Processor stepping 00
[    0.064003] Performance Events: AMD PMU driver.
[    0.064003] ... version:                0
[    0.064003] ... bit width:              48
[    0.064003] ... generic registers:      4
[    0.064003] ... value mask:             0000ffffffffffff
[    0.064003] ... max period:             00007fffffffffff
[    0.064003] ... fixed-purpose events:   0
[    0.064003] ... event mask:             000000000000000f
[    0.064003] NMI watchdog enabled, takes one hw-pmu counter.
[    0.064003] Booting Node   0, Processors  #1
[    0.064003] smpboot cpu 1: start_ip = 95000
[    0.152024] NMI watchdog enabled, takes one hw-pmu counter.
[    0.152081]  #2
[    0.152082] smpboot cpu 2: start_ip = 95000
[    0.244027] NMI watchdog enabled, takes one hw-pmu counter.
[    0.244077]  #3
[    0.244078] smpboot cpu 3: start_ip = 95000
[    0.336048] NMI watchdog enabled, takes one hw-pmu counter.
[    0.336104]  #4
[    0.336105] smpboot cpu 4: start_ip = 95000
[    0.428040] NMI watchdog enabled, takes one hw-pmu counter.
[    0.428107]  #5 Ok.
[    0.428108] smpboot cpu 5: start_ip = 95000
[    0.520046] NMI watchdog enabled, takes one hw-pmu counter.
[    0.520073] Brought up 6 CPUs
[    0.520076] Total of 6 processors activated (34713.41 BogoMIPS).
[    0.524194] devtmpfs: initialized
[    0.529141] EVM: security.selinux
[    0.529142] EVM: security.SMACK64
[    0.529143] EVM: security.capability
[    0.529205] PM: Registering ACPI NVS region at cffbe000 (139264 bytes)
[    0.529205] print_constraints: dummy: 
[    0.529205] RTC time: 14:50:15, date: 12/26/12
[    0.529205] NET: Registered protocol family 16
[    0.529205] node 0 link 0: io port [1000, ffffff]
[    0.529205] TOM: 00000000d0000000 aka 3328M
[    0.529205] Fam 10h mmconf [mem 0xe0000000-0xefffffff]
[    0.529205] node 0 link 0: mmio [a0000, bffff]
[    0.529205] node 0 link 0: mmio [d0000000, dfffffff]
[    0.529205] node 0 link 0: mmio [e0000000, efffffff] ==> none
[    0.529205] node 0 link 0: mmio [f0000000, ffefffff]
[    0.529205] TOM2: 0000000330000000 aka 13056M
[    0.529205] bus: [00, 07] on node 0 link 0
[    0.529205] bus: 00 index 0 [io  0x0000-0xffff]
[    0.529205] bus: 00 index 1 [mem 0x000a0000-0x000bffff]
[    0.529205] bus: 00 index 2 [mem 0xd0000000-0xdfffffff]
[    0.529205] bus: 00 index 3 [mem 0xf0000000-0xffffffff]
[    0.529205] bus: 00 index 4 [mem 0x330000000-0xfcffffffff]
[    0.529205] Extended Config Space enabled on 1 nodes
[    0.529205] ACPI: bus type pci registered
[    0.529205] Trying to unpack rootfs image as initramfs...
[    0.529205] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.529205] PCI: not using MMCONFIG
[    0.529205] PCI: Using configuration type 1 for base access
[    0.529205] PCI: Using configuration type 1 for extended access
[    0.529768] bio: create slab <bio-0> at 0
[    0.529768] ACPI: Added _OSI(Module Device)
[    0.529768] ACPI: Added _OSI(Processor Device)
[    0.529768] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.529768] ACPI: Added _OSI(Processor Aggregator Device)
[    0.529768] ACPI: EC: Look up EC in DSDT
[    0.532213] ACPI: Executed 3 blocks of module-level executable AML code
[    0.533802] ACPI: Interpreter enabled
[    0.533805] ACPI: (supports S0 S1 S3 S4 S5)
[    0.533822] ACPI: Using IOAPIC for interrupt routing
[    0.533842] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.534306] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.552841] ACPI: No dock devices found.
[    0.552843] HEST: Table not found.
[    0.552846] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.552897] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.553001] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
[    0.553002] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
[    0.553004] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.553006] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff]
[    0.553007] pci_root PNP0A03:00: host bridge window [mem 0xd0000000-0xdfffffff]
[    0.553009] pci_root PNP0A03:00: host bridge window [mem 0xf0000000-0xfebfffff]
[    0.553021] pci 0000:00:00.0: [1022:9601] type 0 class 0x000600
[    0.553074] pci 0000:00:02.0: [1022:9603] type 1 class 0x000604
[    0.553103] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.553105] pci 0000:00:02.0: PME# disabled
[    0.553119] pci 0000:00:05.0: [1022:9605] type 1 class 0x000604
[    0.553146] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
[    0.553148] pci 0000:00:05.0: PME# disabled
[    0.553176] pci 0000:00:0a.0: [1022:9609] type 1 class 0x000604
[    0.553203] pci 0000:00:0a.0: PME# supported from D0 D3hot D3cold
[    0.553205] pci 0000:00:0a.0: PME# disabled
[    0.553229] pci 0000:00:11.0: [1002:4391] type 0 class 0x000106
[    0.553247] pci 0000:00:11.0: reg 10: [io  0xc000-0xc007]
[    0.553255] pci 0000:00:11.0: reg 14: [io  0xb000-0xb003]
[    0.553264] pci 0000:00:11.0: reg 18: [io  0xa000-0xa007]
[    0.553273] pci 0000:00:11.0: reg 1c: [io  0x9000-0x9003]
[    0.553282] pci 0000:00:11.0: reg 20: [io  0x8000-0x800f]
[    0.553290] pci 0000:00:11.0: reg 24: [mem 0xfe9ffc00-0xfe9fffff]
[    0.553344] pci 0000:00:12.0: [1002:4397] type 0 class 0x000c03
[    0.553357] pci 0000:00:12.0: reg 10: [mem 0xfe9fe000-0xfe9fefff]
[    0.553417] pci 0000:00:12.1: [1002:4398] type 0 class 0x000c03
[    0.553430] pci 0000:00:12.1: reg 10: [mem 0xfe9fd000-0xfe9fdfff]
[    0.553496] pci 0000:00:12.2: [1002:4396] type 0 class 0x000c03
[    0.553513] pci 0000:00:12.2: reg 10: [mem 0xfe9ff800-0xfe9ff8ff]
[    0.553592] pci 0000:00:12.2: supports D1 D2
[    0.553593] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.553596] pci 0000:00:12.2: PME# disabled
[    0.553616] pci 0000:00:13.0: [1002:4397] type 0 class 0x000c03
[    0.553628] pci 0000:00:13.0: reg 10: [mem 0xfe9fc000-0xfe9fcfff]
[    0.553690] pci 0000:00:13.1: [1002:4398] type 0 class 0x000c03
[    0.553703] pci 0000:00:13.1: reg 10: [mem 0xfe9fb000-0xfe9fbfff]
[    0.553769] pci 0000:00:13.2: [1002:4396] type 0 class 0x000c03
[    0.553786] pci 0000:00:13.2: reg 10: [mem 0xfe9ff400-0xfe9ff4ff]
[    0.553865] pci 0000:00:13.2: supports D1 D2
[    0.553866] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.553869] pci 0000:00:13.2: PME# disabled
[    0.553892] pci 0000:00:14.0: [1002:4385] type 0 class 0x000c05
[    0.553987] pci 0000:00:14.2: [1002:4383] type 0 class 0x000403
[    0.554007] pci 0000:00:14.2: reg 10: [mem 0xfe9f4000-0xfe9f7fff 64bit]
[    0.554069] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.554073] pci 0000:00:14.2: PME# disabled
[    0.554084] pci 0000:00:14.3: [1002:439d] type 0 class 0x000601
[    0.554156] pci 0000:00:14.4: [1002:4384] type 1 class 0x000604
[    0.554199] pci 0000:00:18.0: [1022:1200] type 0 class 0x000600
[    0.554212] pci 0000:00:18.1: [1022:1201] type 0 class 0x000600
[    0.554223] pci 0000:00:18.2: [1022:1202] type 0 class 0x000600
[    0.554234] pci 0000:00:18.3: [1022:1203] type 0 class 0x000600
[    0.554246] pci 0000:00:18.4: [1022:1204] type 0 class 0x000600
[    0.554293] pci 0000:01:00.0: [10de:1245] type 0 class 0x000300
[    0.554302] pci 0000:01:00.0: reg 10: [mem 0xfc000000-0xfdffffff]
[    0.554311] pci 0000:01:00.0: reg 14: [mem 0xd8000000-0xdfffffff 64bit pref]
[    0.554320] pci 0000:01:00.0: reg 1c: [mem 0xd4000000-0xd7ffffff 64bit pref]
[    0.554327] pci 0000:01:00.0: reg 24: [io  0xd800-0xd87f]
[    0.554333] pci 0000:01:00.0: reg 30: [mem 0xfbf80000-0xfbffffff pref]
[    0.554385] pci 0000:01:00.1: [10de:0bee] type 0 class 0x000403
[    0.554393] pci 0000:01:00.1: reg 10: [mem 0xfbf7c000-0xfbf7ffff]
[    0.560053] pci 0000:00:02.0: PCI bridge to [bus 01-01]
[    0.560057] pci 0000:00:02.0:   bridge window [io  0xd000-0xdfff]
[    0.560060] pci 0000:00:02.0:   bridge window [mem 0xfbf00000-0xfdffffff]
[    0.560063] pci 0000:00:02.0:   bridge window [mem 0xd4000000-0xdfffffff 64bit pref]
[    0.560099] pci 0000:02:00.0: [1814:5390] type 0 class 0x000280
[    0.560111] pci 0000:02:00.0: reg 10: [mem 0xfeaf0000-0xfeafffff]
[    0.568053] pci 0000:00:05.0: PCI bridge to [bus 02-02]
[    0.568058] pci 0000:00:05.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.568098] pci 0000:03:00.0: [10ec:8136] type 0 class 0x000200
[    0.568110] pci 0000:03:00.0: reg 10: [io  0xe800-0xe8ff]
[    0.568129] pci 0000:03:00.0: reg 18: [mem 0xfebff000-0xfebfffff 64bit]
[    0.568142] pci 0000:03:00.0: reg 20: [mem 0xfaffc000-0xfaffffff 64bit pref]
[    0.568208] pci 0000:03:00.0: supports D1 D2
[    0.568209] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.568213] pci 0000:03:00.0: PME# disabled
[    0.576052] pci 0000:00:0a.0: PCI bridge to [bus 03-03]
[    0.576056] pci 0000:00:0a.0:   bridge window [io  0xe000-0xefff]
[    0.576058] pci 0000:00:0a.0:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.576061] pci 0000:00:0a.0:   bridge window [mem 0xfaf00000-0xfaffffff 64bit pref]
[    0.576121] pci 0000:00:14.4: PCI bridge to [bus 04-04] (subtractive decode)
[    0.576129] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.576131] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.576133] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.576134] pci 0000:00:14.4:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.576136] pci 0000:00:14.4:   bridge window [mem 0xd0000000-0xdfffffff] (subtractive decode)
[    0.576138] pci 0000:00:14.4:   bridge window [mem 0xf0000000-0xfebfffff] (subtractive decode)
[    0.576153] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.576299] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
[    0.576319] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE5._PRT]
[    0.576342] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCEA._PRT]
[    0.576397]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.576400]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.576402] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.578659] ACPI: PCI Interrupt Link [LNKA] (IRQs *4 7 10 11 12 14 15)
[    0.578685] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 7 10 *11 12 14 15)
[    0.578710] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 7 *10 11 12 14 15)
[    0.578735] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 7 *10 11 12 14 15)
[    0.578759] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.578783] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.578808] ACPI: PCI Interrupt Link [LNKG] (IRQs 4 *7 10 11 12 14 15)
[    0.578832] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.578918] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.578918] vgaarb: loaded
[    0.578918] vgaarb: bridge control possible 0000:01:00.0
[    0.578918] i2c-core: driver [aat2870] using legacy suspend method
[    0.578918] i2c-core: driver [aat2870] using legacy resume method
[    0.578918] SCSI subsystem initialized
[    0.578918] libata version 3.00 loaded.
[    0.578918] usbcore: registered new interface driver usbfs
[    0.578918] usbcore: registered new interface driver hub
[    0.578918] usbcore: registered new device driver usb
[    0.578918] PCI: Using ACPI for IRQ routing
[    0.587735] PCI: pci_cache_line_size set to 64 bytes
[    0.587793] reserve RAM buffer: 000000000009a400 - 000000000009ffff 
[    0.587795] reserve RAM buffer: 00000000cffb0000 - 00000000cfffffff 
[    0.587868] NetLabel: Initializing
[    0.587870] NetLabel:  domain hash size = 128
[    0.587871] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.587878] NetLabel:  unlabeled traffic allowed by default
[    0.587913] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.587913] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    0.589057] Switching to clocksource hpet
[    0.592741] AppArmor: AppArmor Filesystem Enabled
[    0.592761] pnp: PnP ACPI init
[    0.592776] ACPI: bus type pnp registered
[    0.592860] pnp 00:00: [bus 00-ff]
[    0.592862] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.592863] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.592865] pnp 00:00: [io  0x0d00-0xffff window]
[    0.592867] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.592868] pnp 00:00: [mem 0x000d0000-0x000dffff window]
[    0.592870] pnp 00:00: [mem 0xd0000000-0xdfffffff window]
[    0.592873] pnp 00:00: [mem 0xf0000000-0xfebfffff window]
[    0.592912] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.592965] pnp 00:01: [mem 0x00000000-0xffffffffffffffff disabled]
[    0.592967] pnp 00:01: [mem 0x00000000-0xffffffffffffffff disabled]
[    0.593005] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.593030] pnp 00:02: [dma 4]
[    0.593031] pnp 00:02: [io  0x0000-0x000f]
[    0.593033] pnp 00:02: [io  0x0081-0x0083]
[    0.593034] pnp 00:02: [io  0x0087]
[    0.593035] pnp 00:02: [io  0x0089-0x008b]
[    0.593036] pnp 00:02: [io  0x008f]
[    0.593037] pnp 00:02: [io  0x00c0-0x00df]
[    0.593059] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.593065] pnp 00:03: [io  0x0070-0x0071]
[    0.593073] pnp 00:03: [irq 8]
[    0.593090] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.593095] pnp 00:04: [io  0x0061]
[    0.593111] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.593116] pnp 00:05: [io  0x00f0-0x00ff]
[    0.593128] pnp 00:05: [irq 13]
[    0.593145] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.593161] pnp 00:06: [mem 0xfed00000-0xfed003ff]
[    0.593178] pnp 00:06: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.593222] pnp 00:07: [io  0x0060]
[    0.593223] pnp 00:07: [io  0x0064]
[    0.593225] pnp 00:07: [mem 0xfec00000-0xfec00fff]
[    0.593226] pnp 00:07: [mem 0xfee00000-0xfee00fff]
[    0.593254] system 00:07: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.593256] system 00:07: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.593258] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.593335] pnp 00:08: [io  0x0010-0x001f]
[    0.593336] pnp 00:08: [io  0x0022-0x003f]
[    0.593338] pnp 00:08: [io  0x0062-0x0063]
[    0.593339] pnp 00:08: [io  0x0065-0x006f]
[    0.593340] pnp 00:08: [io  0x0072-0x007f]
[    0.593341] pnp 00:08: [io  0x0080]
[    0.593342] pnp 00:08: [io  0x0084-0x0086]
[    0.593343] pnp 00:08: [io  0x0088]
[    0.593344] pnp 00:08: [io  0x008c-0x008e]
[    0.593345] pnp 00:08: [io  0x0090-0x009f]
[    0.593347] pnp 00:08: [io  0x00a2-0x00bf]
[    0.593348] pnp 00:08: [io  0x00b1]
[    0.593349] pnp 00:08: [io  0x00e0-0x00ef]
[    0.593350] pnp 00:08: [io  0x04d0-0x04d1]
[    0.593351] pnp 00:08: [io  0x040b]
[    0.593352] pnp 00:08: [io  0x04d6]
[    0.593353] pnp 00:08: [io  0x0c00-0x0c01]
[    0.593354] pnp 00:08: [io  0x0c14]
[    0.593355] pnp 00:08: [io  0x0c50-0x0c51]
[    0.593356] pnp 00:08: [io  0x0c52]
[    0.593358] pnp 00:08: [io  0x0c6c]
[    0.593359] pnp 00:08: [io  0x0c6f]
[    0.593361] pnp 00:08: [io  0x0cd0-0x0cd1]
[    0.593363] pnp 00:08: [io  0x0cd2-0x0cd3]
[    0.593364] pnp 00:08: [io  0x0cd4-0x0cd5]
[    0.593365] pnp 00:08: [io  0x0cd6-0x0cd7]
[    0.593366] pnp 00:08: [io  0x0cd8-0x0cdf]
[    0.593367] pnp 00:08: [io  0x0800-0x089f]
[    0.593369] pnp 00:08: [io  0x0000-0xffffffffffffffff disabled]
[    0.593370] pnp 00:08: [io  0x0b00-0x0b0f]
[    0.593371] pnp 00:08: [io  0x0b20-0x0b3f]
[    0.593372] pnp 00:08: [io  0x0900-0x090f]
[    0.593373] pnp 00:08: [io  0x0910-0x091f]
[    0.593375] pnp 00:08: [io  0xfe00-0xfefe]
[    0.593376] pnp 00:08: [io  0x0060]
[    0.593377] pnp 00:08: [io  0x0064]
[    0.593378] pnp 00:08: [mem 0xffb80000-0xffbfffff]
[    0.593379] pnp 00:08: [mem 0xfec10000-0xfec1001f]
[    0.593423] system 00:08: [io  0x04d0-0x04d1] has been reserved
[    0.593424] system 00:08: [io  0x040b] has been reserved
[    0.593426] system 00:08: [io  0x04d6] has been reserved
[    0.593427] system 00:08: [io  0x0c00-0x0c01] has been reserved
[    0.593429] system 00:08: [io  0x0c14] has been reserved
[    0.593430] system 00:08: [io  0x0c50-0x0c51] has been reserved
[    0.593432] system 00:08: [io  0x0c52] has been reserved
[    0.593433] system 00:08: [io  0x0c6c] has been reserved
[    0.593435] system 00:08: [io  0x0c6f] has been reserved
[    0.593436] system 00:08: [io  0x0cd0-0x0cd1] has been reserved
[    0.593438] system 00:08: [io  0x0cd2-0x0cd3] has been reserved
[    0.593440] system 00:08: [io  0x0cd4-0x0cd5] has been reserved
[    0.593441] system 00:08: [io  0x0cd6-0x0cd7] has been reserved
[    0.593443] system 00:08: [io  0x0cd8-0x0cdf] has been reserved
[    0.593444] system 00:08: [io  0x0800-0x089f] has been reserved
[    0.593446] system 00:08: [io  0x0b00-0x0b0f] has been reserved
[    0.593449] system 00:08: [io  0x0b20-0x0b3f] has been reserved
[    0.593451] system 00:08: [io  0x0900-0x090f] has been reserved
[    0.593452] system 00:08: [io  0x0910-0x091f] has been reserved
[    0.593454] system 00:08: [io  0xfe00-0xfefe] has been reserved
[    0.593456] system 00:08: [mem 0xffb80000-0xffbfffff] has been reserved
[    0.593458] system 00:08: [mem 0xfec10000-0xfec1001f] has been reserved
[    0.593460] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.593539] pnp 00:09: [io  0x0000-0xffffffffffffffff disabled]
[    0.593541] pnp 00:09: [io  0x0e00-0x0e0f]
[    0.593542] pnp 00:09: [io  0x0e80-0x0e8f]
[    0.593543] pnp 00:09: [io  0x0f40-0x0f4f]
[    0.593571] system 00:09: [io  0x0e00-0x0e0f] has been reserved
[    0.593573] system 00:09: [io  0x0e80-0x0e8f] has been reserved
[    0.593575] system 00:09: [io  0x0f40-0x0f4f] has been reserved
[    0.593577] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.593596] pnp 00:0a: [mem 0xe0000000-0xefffffff]
[    0.593623] system 00:0a: [mem 0xe0000000-0xefffffff] has been reserved
[    0.593625] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.593688] pnp 00:0b: [mem 0x00000000-0x0009ffff]
[    0.593690] pnp 00:0b: [mem 0x000c0000-0x000cffff]
[    0.593691] pnp 00:0b: [mem 0x000e0000-0x000fffff]
[    0.593693] pnp 00:0b: [mem 0x00100000-0xcfffffff]
[    0.593694] pnp 00:0b: [mem 0xfec00000-0xffffffff]
[    0.593724] system 00:0b: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.593726] system 00:0b: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.593728] system 00:0b: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.593729] system 00:0b: [mem 0x00100000-0xcfffffff] could not be reserved
[    0.593731] system 00:0b: [mem 0xfec00000-0xffffffff] could not be reserved
[    0.593733] system 00:0b: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.593797] pnp: PnP ACPI: found 12 devices
[    0.593798] ACPI: ACPI bus type pnp unregistered
[    0.600477] PCI: max bus depth: 1 pci_try_num: 2
[    0.600493] pci 0000:00:02.0: PCI bridge to [bus 01-01]
[    0.600495] pci 0000:00:02.0:   bridge window [io  0xd000-0xdfff]
[    0.600497] pci 0000:00:02.0:   bridge window [mem 0xfbf00000-0xfdffffff]
[    0.600500] pci 0000:00:02.0:   bridge window [mem 0xd4000000-0xdfffffff 64bit pref]
[    0.600502] pci 0000:00:05.0: PCI bridge to [bus 02-02]
[    0.600505] pci 0000:00:05.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.600508] pci 0000:00:0a.0: PCI bridge to [bus 03-03]
[    0.600510] pci 0000:00:0a.0:   bridge window [io  0xe000-0xefff]
[    0.600512] pci 0000:00:0a.0:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.600514] pci 0000:00:0a.0:   bridge window [mem 0xfaf00000-0xfaffffff 64bit pref]
[    0.600517] pci 0000:00:14.4: PCI bridge to [bus 04-04]
[    0.600539] pci 0000:00:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.600542] pci 0000:00:02.0: setting latency timer to 64
[    0.600549] pci 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.600551] pci 0000:00:05.0: setting latency timer to 64
[    0.600554] pci 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.600556] pci 0000:00:0a.0: setting latency timer to 64
[    0.600563] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.600564] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.600566] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.600567] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.600569] pci_bus 0000:00: resource 8 [mem 0xd0000000-0xdfffffff]
[    0.600571] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfebfffff]
[    0.600572] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    0.600574] pci_bus 0000:01: resource 1 [mem 0xfbf00000-0xfdffffff]
[    0.600576] pci_bus 0000:01: resource 2 [mem 0xd4000000-0xdfffffff 64bit pref]
[    0.600578] pci_bus 0000:02: resource 1 [mem 0xfea00000-0xfeafffff]
[    0.600580] pci_bus 0000:03: resource 0 [io  0xe000-0xefff]
[    0.600581] pci_bus 0000:03: resource 1 [mem 0xfeb00000-0xfebfffff]
[    0.600583] pci_bus 0000:03: resource 2 [mem 0xfaf00000-0xfaffffff 64bit pref]
[    0.600585] pci_bus 0000:04: resource 4 [io  0x0000-0x0cf7]
[    0.600587] pci_bus 0000:04: resource 5 [io  0x0d00-0xffff]
[    0.600588] pci_bus 0000:04: resource 6 [mem 0x000a0000-0x000bffff]
[    0.600590] pci_bus 0000:04: resource 7 [mem 0x000d0000-0x000dffff]
[    0.600592] pci_bus 0000:04: resource 8 [mem 0xd0000000-0xdfffffff]
[    0.600593] pci_bus 0000:04: resource 9 [mem 0xf0000000-0xfebfffff]
[    0.600623] NET: Registered protocol family 2
[    0.600855] IP route cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.602450] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.604987] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.605300] TCP: Hash tables configured (established 524288 bind 65536)
[    0.605301] TCP reno registered
[    0.605317] UDP hash table entries: 8192 (order: 6, 262144 bytes)
[    0.605419] UDP-Lite hash table entries: 8192 (order: 6, 262144 bytes)
[    0.605576] NET: Registered protocol family 1
[    0.605611] pci 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.332051] pci 0000:00:12.0: PCI INT A disabled
[    1.332066] pci 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.381470] Freeing initrd memory: 13876k freed
[    1.412088] pci 0000:00:12.1: PCI INT A disabled
[    1.412121] pci 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.412210] pci 0000:00:12.2: PCI INT B disabled
[    1.412217] pci 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.492078] pci 0000:00:13.0: PCI INT A disabled
[    1.492105] pci 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.572085] pci 0000:00:13.1: PCI INT A disabled
[    1.572134] pci 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.572231] pci 0000:00:13.2: PCI INT B disabled
[    1.572261] pci 0000:01:00.0: Boot video device
[    1.572274] PCI: CLS 64 bytes, default 64
[    1.572527] PCI-DMA: Disabling AGP.
[    1.572649] PCI-DMA: aperture base @ c4000000 size 65536 KB
[    1.572650] PCI-DMA: using GART IOMMU.
[    1.572653] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    1.575881] IBS: LVT offset 1 assigned
[    1.575919] perf: AMD IBS detected (0x0000001f)
[    1.576058] audit: initializing netlink socket (disabled)
[    1.576076] type=2000 audit(1356533416.572:1): initialized
[    1.592200] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.594489] VFS: Disk quotas dquot_6.5.2
[    1.594527] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.594937] fuse init (API version 7.17)
[    1.595009] msgmni has been set to 24030
[    1.595464] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.595497] io scheduler noop registered
[    1.595498] io scheduler deadline registered
[    1.595524] io scheduler cfq registered (default)
[    1.595618] pcieport 0000:00:02.0: setting latency timer to 64
[    1.595642] pcieport 0000:00:02.0: irq 40 for MSI/MSI-X
[    1.595677] pcieport 0000:00:05.0: setting latency timer to 64
[    1.595695] pcieport 0000:00:05.0: irq 41 for MSI/MSI-X
[    1.595726] pcieport 0000:00:0a.0: setting latency timer to 64
[    1.595744] pcieport 0000:00:0a.0: irq 42 for MSI/MSI-X
[    1.595794] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.595810] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.595897] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    1.595902] ACPI: Power Button [PWRB]
[    1.595930] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.595932] ACPI: Power Button [PWRF]
[    1.595978] ACPI: acpi_idle registered with cpuidle
[    1.596804] ERST: Table is not found!
[    1.596805] GHES: HEST is not enabled!
[    1.596882] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.813323] Linux agpgart interface v0.103
[    1.814471] brd: module loaded
[    1.815066] loop: module loaded
[    1.815161] ahci 0000:00:11.0: version 3.0
[    1.815178] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.815319] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.815322] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc 
[    1.815850] scsi0 : ahci
[    1.815926] scsi1 : ahci
[    1.815990] scsi2 : ahci
[    1.816064] scsi3 : ahci
[    1.816101] ata1: SATA max UDMA/133 abar m1024@0xfe9ffc00 port 0xfe9ffd00 irq 22
[    1.816104] ata2: SATA max UDMA/133 abar m1024@0xfe9ffc00 port 0xfe9ffd80 irq 22
[    1.816106] ata3: SATA max UDMA/133 abar m1024@0xfe9ffc00 port 0xfe9ffe00 irq 22
[    1.816109] ata4: SATA max UDMA/133 abar m1024@0xfe9ffc00 port 0xfe9ffe80 irq 22
[    1.816572] Fixed MDIO Bus: probed
[    1.816587] tun: Universal TUN/TAP device driver, 1.6
[    1.816588] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.816638] PPP generic driver version 2.4.2
[    1.816733] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.816755] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.816768] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    1.816835] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.816842] ehci_hcd 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.816863] ehci_hcd 0000:00:12.2: debug port 1
[    1.816879] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfe9ff800
[    1.828064] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.828252] hub 1-0:1.0: USB hub found
[    1.828255] hub 1-0:1.0: 6 ports detected
[    1.828339] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.828354] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    1.828409] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.828415] ehci_hcd 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.828432] ehci_hcd 0000:00:13.2: debug port 1
[    1.828449] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfe9ff400
[    1.840071] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.840245] hub 2-0:1.0: USB hub found
[    1.840248] hub 2-0:1.0: 6 ports detected
[    1.840325] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.840349] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.840362] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    1.840418] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    1.840438] ohci_hcd 0000:00:12.0: irq 16, io mem 0xfe9fe000
[    1.900157] hub 3-0:1.0: USB hub found
[    1.900166] hub 3-0:1.0: 3 ports detected
[    1.900238] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.900251] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    1.900305] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
[    1.900318] ohci_hcd 0000:00:12.1: irq 16, io mem 0xfe9fd000
[    1.960142] hub 4-0:1.0: USB hub found
[    1.960152] hub 4-0:1.0: 3 ports detected
[    1.960224] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.960235] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    1.960293] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    1.960311] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfe9fc000
[    2.020143] hub 5-0:1.0: USB hub found
[    2.020152] hub 5-0:1.0: 3 ports detected
[    2.020224] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.020236] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    2.020294] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
[    2.020308] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfe9fb000
[    2.080165] hub 6-0:1.0: USB hub found
[    2.080174] hub 6-0:1.0: 3 ports detected
[    2.080243] uhci_hcd: USB Universal Host Controller Interface driver
[    2.080292] usbcore: registered new interface driver libusual
[    2.080315] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    2.080678] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.080682] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.080865] mousedev: PS/2 mouse device common for all mice
[    2.081085] rtc_cmos 00:03: RTC can wake from S4
[    2.081263] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    2.081299] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    2.081358] device-mapper: uevent: version 1.0.3
[    2.081421] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    2.081515] cpuidle: using governor ladder
[    2.081686] cpuidle: using governor menu
[    2.081687] EFI Variables Facility v0.08 2004-May-17
[    2.081870] TCP cubic registered
[    2.081943] NET: Registered protocol family 10
[    2.082273] NET: Registered protocol family 17
[    2.082275] Registering the dns_resolver key type
[    2.082418] PM: Hibernation image not present or could not be loaded.
[    2.082425] registered taskstats version 1
[    2.089014]   Magic number: 8:264:840
[    2.089145] rtc_cmos 00:03: setting system clock to 2012-12-26 14:50:17 UTC (1356533417)
[    2.089201] powernow-k8: Found 1 AMD Phenom(tm) II X6 1065T Processor (6 cpu cores) (version 2.20.00)
[    2.089234] powernow-k8: Core Performance Boosting: on.
[    2.089258] powernow-k8:    0 : pstate 0 (2900 MHz)
[    2.089259] powernow-k8:    1 : pstate 1 (2200 MHz)
[    2.089260] powernow-k8:    2 : pstate 2 (1500 MHz)
[    2.089261] powernow-k8:    3 : pstate 3 (800 MHz)
[    2.090287] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.090288] EDD information not available.
[    2.136168] ata2: SATA link down (SStatus 0 SControl 300)
[    2.136245] ata4: SATA link down (SStatus 0 SControl 300)
[    2.308102] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.308147] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.312307] ata3.00: ATAPI: hp      DVD-RAM GH60L, RD05, max UDMA/100
[    2.313343] ata1.00: ATA-8: WDC WD15EARS-60MVWB0, 51.0AB51, max UDMA/100
[    2.313353] ata1.00: 2930277168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.317199] ata3.00: configured for UDMA/100
[    2.318338] ata1.00: configured for UDMA/100
[    2.318563] scsi 0:0:0:0: Direct-Access     ATA      WDC WD15EARS-60M 51.0 PQ: 0 ANSI: 5
[    2.318779] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.318949] sd 0:0:0:0: [sda] 2930277168 512-byte logical blocks: (1.50 TB/1.36 TiB)
[    2.318952] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    2.319189] sd 0:0:0:0: [sda] Write Protect is off
[    2.319192] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.319298] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.326344] scsi 2:0:0:0: CD-ROM            hp       DVD-RAM GH60L    RD05 PQ: 0 ANSI: 5
[    2.336034] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.336043] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.336196] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    2.336249] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    2.359187]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
[    2.359976] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.361089] Freeing unused kernel memory: 924k freed
[    2.361270] Write protecting the kernel read-only data: 12288k
[    2.365096] Freeing unused kernel memory: 1604k freed
[    2.368357] Freeing unused kernel memory: 1196k freed
[    2.386734] udevd[113]: starting version 175
[    2.401301] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.401324] r8169 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.401358] r8169 0000:03:00.0: setting latency timer to 64
[    2.401406] r8169 0000:03:00.0: irq 43 for MSI/MSI-X
[    2.401777] r8169 0000:03:00.0: eth0: RTL8168e/8111e at 0xffffc9000187c000, 2c:27:d7:1a:a3:d5, XID 0c200000 IRQ 43
[    2.401780] r8169 0000:03:00.0: eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    2.404044] usb 3-2: new low-speed USB device number 2 using ohci_hcd
[    2.572102] Refined TSC clocksource calibration: 2892.750 MHz.
[    2.572114] Switching to clocksource tsc
[    2.582344] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:12.0/usb3/3-2/3-2:1.0/input/input2
[    2.582443] generic-usb 0003:046D:C01E.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:12.0-2/input0
[    2.582455] usbcore: registered new interface driver usbhid
[    2.582456] usbhid: USB HID core driver
[    2.684086] usb 2-6: new high-speed USB device number 2 using ehci_hcd
[    2.819957] Initializing USB Mass Storage driver...
[    2.820102] scsi4 : usb-storage 2-6:1.0
[    2.820185] usbcore: registered new interface driver usb-storage
[    2.820186] USB Mass Storage support registered.
[    2.820189] usbcore: registered new interface driver uas
[    3.080092] usb 4-1: new low-speed USB device number 2 using ohci_hcd
[    3.264442] input: HP USB Multimedia Keyboard as /devices/pci0000:00/0000:00:12.1/usb4/4-1/4-1:1.0/input/input3
[    3.264531] generic-usb 0003:0461:4DD7.0002: input,hidraw1: USB HID v1.11 Keyboard [HP USB Multimedia Keyboard] on usb-0000:00:12.1-1/input0
[    3.278433] input: HP USB Multimedia Keyboard as /devices/pci0000:00/0000:00:12.1/usb4/4-1/4-1:1.1/input/input4
[    3.278557] generic-usb 0003:0461:4DD7.0003: input,hiddev0,hidraw2: USB HID v1.11 Device [HP USB Multimedia Keyboard] on usb-0000:00:12.1-1/input1
[    3.470748] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[    3.820847] scsi 4:0:0:0: Direct-Access     Generic- SD/MMC           1.00 PQ: 0 ANSI: 0
[    3.821404] scsi 4:0:0:1: Direct-Access     Generic- Compact Flash    1.01 PQ: 0 ANSI: 0
[    3.822026] scsi 4:0:0:2: Direct-Access     Generic- SM/xD-Picture    1.02 PQ: 0 ANSI: 0
[    3.822746] scsi 4:0:0:3: Direct-Access     Generic- MS/MS-Pro        1.03 PQ: 0 ANSI: 0 CCS
[    3.823174] sd 4:0:0:0: Attached scsi generic sg2 type 0
[    3.823319] sd 4:0:0:1: Attached scsi generic sg3 type 0
[    3.823442] sd 4:0:0:2: Attached scsi generic sg4 type 0
[    3.823565] sd 4:0:0:3: Attached scsi generic sg5 type 0
[    3.829477] sd 4:0:0:2: [sdd] Attached SCSI removable disk
[    3.830228] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[    3.831728] sd 4:0:0:3: [sde] Attached SCSI removable disk
[    3.832469] sd 4:0:0:1: [sdc] Attached SCSI removable disk
[   25.943981] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   25.947734] init: bootchart main process (329) terminated with status 127
[   26.126667] init: bootchart post-stop process (340) terminated with status 127
[   26.263951] Adding 8387580k swap on /dev/sda5.  Priority:-1 extents:1 across:8387580k 
[   26.281680] udevd[354]: starting version 175
[   26.461150] type=1400 audit(1356546041.867:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=413 comm="apparmor_parser"
[   26.461392] type=1400 audit(1356546041.867:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=516 comm="apparmor_parser"
[   26.461556] type=1400 audit(1356546041.867:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=413 comm="apparmor_parser"
[   26.461764] type=1400 audit(1356546041.867:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=413 comm="apparmor_parser"
[   26.461793] type=1400 audit(1356546041.867:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=516 comm="apparmor_parser"
[   26.462037] type=1400 audit(1356546041.867:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=516 comm="apparmor_parser"
[   27.702476] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[   28.238838] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[   28.328221] wmi: Mapper loaded
[   28.486853] lp: driver loaded but no devices found
[   28.503685] MCE: In-kernel MCE decoding enabled.
[   28.518787] EDAC MC: Ver: 2.1.0
[   28.540064] AMD64 EDAC driver v3.4.0
[   28.540105] EDAC amd64: DRAM ECC disabled.
[   28.540131] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   28.540135]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   28.540139]  (Note that use of the override may cause unknown side effects.)
[   28.564744] cfg80211: Calling CRDA to update world regulatory domain
[   28.569151] cfg80211: World regulatory domain updated:
[   28.569153] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   28.569155] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   28.569157] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   28.569159] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   28.569160] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   28.569162] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   28.696494] SP5100 TCO timer: SP5100 TCO WatchDog Timer Driver v0.01
[   28.696566] SP5100 TCO timer: mmio address 0xfec000f0 already in use
[   28.804257] nvidia: module license 'NVIDIA' taints kernel.
[   28.804265] Disabling lock debugging due to kernel taint
[   28.837242] nvidia 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   28.837251] nvidia 0000:01:00.0: setting latency timer to 64
[   28.837261] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   28.837398] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  310.14  Tue Oct  9 11:52:41 PDT 2012
[   29.400560] rt2800pci 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   29.400568] rt2800pci 0000:02:00.0: setting latency timer to 64
[   29.402440] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   29.402442] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.402444] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   29.402446] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.402447] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   29.402449] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.402450] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   29.402452] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.402453] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   29.402455] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.402457] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   29.402458] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.402460] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   29.402462] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.402463] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   29.402465] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.402466] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   29.402468] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.402469] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   29.402471] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.402473] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   29.402474] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.402476] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   29.402478] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   29.402479] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   29.402481] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   29.402482] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   29.402484] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   29.488188] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   29.488659] Registered led device: rt2800pci-phy0::radio
[   29.488675] Registered led device: rt2800pci-phy0::assoc
[   29.488692] Registered led device: rt2800pci-phy0::quality
[   29.595087] snd_hda_intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   29.689090] hda_codec: ALC888-VD: BIOS auto-probing.
[   29.700288] input: HDA ATI SB Line as /devices/pci0000:00/0000:00:14.2/sound/card0/input5
[   29.700378] input: HDA ATI SB Front Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input6
[   29.700440] input: HDA ATI SB Rear Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input7
[   29.700500] input: HDA ATI SB Front Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input8
[   29.700555] input: HDA ATI SB Line-Out Side as /devices/pci0000:00/0000:00:14.2/sound/card0/input9
[   29.700610] input: HDA ATI SB Line-Out CLFE as /devices/pci0000:00/0000:00:14.2/sound/card0/input10
[   29.700664] input: HDA ATI SB Line-Out Surround as /devices/pci0000:00/0000:00:14.2/sound/card0/input11
[   29.700719] input: HDA ATI SB Line-Out Front as /devices/pci0000:00/0000:00:14.2/sound/card0/input12
[   29.700969] snd_hda_intel 0000:01:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   29.700971] hda_intel: Disabling MSI
[   29.701019] snd_hda_intel 0000:01:00.1: setting latency timer to 64
[   29.944285] init: failsafe main process (976) killed by TERM signal
[   30.086494] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   30.098971] ppdev: user-space parallel port driver
[   30.175401] type=1400 audit(1356546045.579:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1076 comm="apparmor_parser"
[   30.175630] type=1400 audit(1356546045.579:9): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1077 comm="apparmor_parser"
[   30.176055] type=1400 audit(1356546045.583:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1077 comm="apparmor_parser"
[   30.176152] type=1400 audit(1356546045.583:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=1080 comm="apparmor_parser"
[   30.258947] Bluetooth: Core ver 2.16
[   30.258968] NET: Registered protocol family 31
[   30.258970] Bluetooth: HCI device and connection manager initialized
[   30.258973] Bluetooth: HCI socket layer initialized
[   30.258974] Bluetooth: L2CAP socket layer initialized
[   30.258978] Bluetooth: SCO socket layer initialized
[   30.269244] r8169 0000:03:00.0: eth0: link down
[   30.269257] r8169 0000:03:00.0: eth0: link down
[   30.270650] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   30.270892] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   30.332020] Bluetooth: RFCOMM TTY layer initialized
[   30.332024] Bluetooth: RFCOMM socket layer initialized
[   30.332026] Bluetooth: RFCOMM ver 1.11
[   30.519241] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   30.519243] Bluetooth: BNEP filters: protocol multicast
[   30.740096] HDMI status: Codec=0 Pin=5 Presence_Detect=0 ELD_Valid=0
[   30.764126] HDMI status: Codec=1 Pin=5 Presence_Detect=0 ELD_Valid=0

```More information:

Getting a different error this time. It's another super cryptic thing that I have no idea about. It ends with "---[ end trace 2375bad7859dab8 ]---"

More information again:

Windows 7 is no longer booting. It gives me a BSOD. I am running Memtest again.

---

### Post by sudodus on 2012-12-26
The list is cryptic for me too.

But I suspect you might have problems with your hard disk drive.

If you have logical errors, you need boot from another drive and to run
```
sudo e2fsck -f /dev/sdxy
``` for the relevant drive x and partition y.

If you have hardware errors, for example bad sectors, that can be read only sometimes or not at all, you should check the S.M.A.R.T. status of your HDD (if it is enabled).
Often there is a summary in a bios menu. Otherwise it can be viewed (summary or details) with ***smartctl***

```
sudo apt-get install smartmontools
```

Summary for drive a:
```
sudo smartctl -H /dev/sda
```

If the drive is failing, save what you can with ***ddrescue*** as soon as possible. The info page
```
info ddrescue
``` is very good (including a tutorial with typical examples).

---

### Post by sammiev on 2012-12-26
memtest is a great place to start but it maybe that your HDD is failing.

---

### Post by kaldor on 2012-12-26
I removed my new-ish (bought in September) RAM stick despite Memtest showing no issues. Everything looks fine right now. I had no issue during boot, and oddly, the system is much faster and more responsive. 

I'm not 100% sure this has fixed anything (may just be a lucky reboot). I'm going to test out my Windows partition now to see what happens.

Moral of the story: RAM causes all kinds of crazy.

Edit: Windows is working fine. It seems like everything is resolved. Thanks to both of you for suggesting the Hard Drive stuff even though it turned out to not be the issue- this thread may be of use to others in the future. 

Not marking it as solved yet. If all is good for the next little while then I'll do that.

---

### Post by sudodus on 2012-12-26
Glad you localized the problem :-)

My experience it that memtest will usually but not always find bad ram quickly. Sometimes you need to run through *all* test cycles more than once, and it takes a long time.

*Edit:* By the way, the problem with bad ram might have cause some logical error written to the HDD. I'd recommend that you check for that.

---

### Post by kaldor on 2012-12-26
> **sudodus said:**
> Glad you localized the problem :-)

My experience it that memtest will usually but not always find bad ram quickly. Sometimes you need to run through *all* test cycles more than once, and it takes a long time.

*Edit:* By the way, the problem with bad ram might have cause some logical error written to the HDD. I'd recommend that you check for that.

I had thought about that myself. I assume it was okay that I simply used Disk Utility to check my SMART status? It says "healthy".

Now I need to see whether or not I can get this RAM replaced/refunded.

Edit: My PC is lightning fast now. I spent the last 2 months complaining about how slow Ubuntu was. I was constantly trying to reduce boot times, get rid of bloat, etc. Could this have been an early warning sign for bad RAM?

---

### Post by sudodus on 2012-12-26
> **kaldor said:**
> I had thought about that myself. I assume it was okay that I simply used Disk Utility to check my SMART status? It says "healthy".

Now I need to see whether or not I can get this RAM replaced/refunded.

Edit: My PC is lightning fast now. I spent the last 2 months complaining about how slow Ubuntu was. I was constantly trying to reduce boot times, get rid of bloat, etc. Could this have been an early warning sign for bad RAM?

Disk utility is OK for a summary for SMART. But I'd recommend that you check the logical status, check for file system errors with [FONT="Courier New"][SIZE="3"]e2fsck -f[/SIZE][/FONT]

Yes, it could be that the RAM was getting bad or a problem that the two RAM sticks would not cooperate with each other, so that either of them would work alone, but not together.

---

### Post by sammiev on 2012-12-26
Glad you found your problem and good luck with the rest. :)

---

### Post by kaldor on 2012-12-26
Marking this as solved. I've been switching between Win7 and Ubuntu a couple of times without issues. 

Thanks guys :)

---

