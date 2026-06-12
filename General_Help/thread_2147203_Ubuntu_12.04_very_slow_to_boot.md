---
title: "Ubuntu 12.04 very slow to boot"
date: 2013-05-21
forum: General Help
---

### Post by Mamoun on 2013-05-21
Hi all,

I'm a new ubuntu user. I just installed the 12.04 version on an external hard drive (of 500 Go). The only problem is that it takes about 2 min to boot which I believe isn't normal.
I hope it's not something wrong with the installation procedure.

Here's my computer specifications:

Version 12.04 (precise) 64 bits
Noyau Linux 3.5.0-30-generic
GNOME 3.4.2
Memory: 3,7 Gio
Processor: Intel® Core™ i3 CPU M 370 @ 2.40GHz × 4
Available space on the disk: 99,5 Gio

Here's what I get with the dmesg command on the terminal:

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.5.0-30-generic (buildd@panlong) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #51~precise1-Ubuntu SMP Wed May 15 08:48:19 UTC 2013 (Ubuntu 3.5.0-30.51~precise1-generic 3.5.7.9)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-30-generic root=UUID=8664dc65-32f7-4b39-8d50-8623489bf15f ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009c3ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009c400-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000bb27bfff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bb27c000-0x00000000bb281fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000bb282000-0x00000000bb3ecfff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bb3ed000-0x00000000bb40efff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000bb40f000-0x00000000bb46efff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bb46f000-0x00000000bb46ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000bb470000-0x00000000bb4f0fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bb4f1000-0x00000000bb70efff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000bb70f000-0x00000000bb716fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bb717000-0x00000000bb71efff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000bb71f000-0x00000000bb77efff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bb77f000-0x00000000bb79efff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bb79f000-0x00000000bb7e0fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bb7e1000-0x00000000bb7fefff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000bb7ff000-0x00000000bb7fffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bb800000-0x00000000bfffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000f080a000-0x00000000f080afff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000feaff000-0x00000000feafffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec0ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed003ff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed8ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x0000000137ffffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.6 present.
[    0.000000] DMI: LENOVO 03192AG/03192AG, BIOS 80ET54WW (1.31 ) 09/15/2011
[    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x138000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-D3FFF write-protect
[    0.000000]   D4000-DBFFF uncachable
[    0.000000]   DC000-FFFFF write-through
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 disabled
[    0.000000]   1 base 000000000 mask F80000000 write-back
[    0.000000]   2 base 080000000 mask FC0000000 write-back
[    0.000000]   3 base 100000000 mask FC0000000 write-back
[    0.000000]   4 base 138000000 mask FF8000000 uncachable
[    0.000000]   5 base 0BC000000 mask FFC000000 uncachable
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 1, base: 0GB, range: 2GB, type WB
[    0.000000] reg 2, base: 2GB, range: 1GB, type WB
[    0.000000] reg 3, base: 4GB, range: 1GB, type WB
[    0.000000] reg 4, base: 4992MB, range: 128MB, type UC
[    0.000000] reg 5, base: 3008MB, range: 64MB, type UC
[    0.000000] total RAM covered: 3904M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 256M     num_reg: 5      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3008MB, range: 64MB, type UC
[    0.000000] reg 3, base: 4GB, range: 1GB, type WB
[    0.000000] reg 4, base: 4992MB, range: 128MB, type UC
[    0.000000] e820: update [mem 0xbc000000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xbb800 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000f6760-0x000f676f] mapped at [ffff8800000f6760]
[    0.000000] initial memory mapped: [mem 0x00000000-0x1fffffff]
[    0.000000] Base memory trampoline at [ffff880000096000] 96000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0xbb7fffff]
[    0.000000]  [mem 0x00000000-0xbb7fffff] page 2M
[    0.000000] kernel direct mapping tables up to 0xbb7fffff @ [mem 0x1fffc000-0x1fffffff]
[    0.000000] init_memory_mapping: [mem 0x100000000-0x137ffffff]
[    0.000000]  [mem 0x100000000-0x137ffffff] page 2M
[    0.000000] kernel direct mapping tables up to 0x137ffffff @ [mem 0xbb7df000-0xbb7e0fff]
[    0.000000] RAMDISK: [mem 0x36294000-0x37141fff]
[    0.000000] ACPI: RSDP 00000000000f6410 00024 (v04 LENOVO)
[    0.000000] ACPI: XSDT 00000000bb7f2ea8 0005C (v01 LENOVO TP-80    00001310  LTP 00000000)
[    0.000000] ACPI: FACP 00000000bb7e3000 000F4 (v03 LENOVO TP-80    00001310 PTEC 00000001)
[    0.000000] ACPI: DSDT 00000000bb7e4000 0BCC6 (v02 LENOVO TP-80    00001310 INTL 20050624)
[    0.000000] ACPI: FACS 00000000bb79bfc0 00040
[    0.000000] ACPI: HPET 00000000bb7fed6a 00038 (v01 LENOVO TP-80    00001310 PTEC 00000001)
[    0.000000] ACPI: MCFG 00000000bb7feda2 0003C (v01 LENOVO TP-80    00001310 PTEC 00000001)
[    0.000000] ACPI: APIC 00000000bb7fedde 00084 (v01 LENOVO TP-80    00001310  LTP 00000000)
[    0.000000] ACPI: BOOT 00000000bb7fee62 00028 (v01 LENOVO TP-80    00001310  LTP 00000001)
[    0.000000] ACPI: SLIC 00000000bb7fee8a 00176 (v01 LENOVO TP-80    00001310  LTP 00000000)
[    0.000000] ACPI: SSDT 00000000bb7e2000 009F1 (v01  PmRef    CpuPm 00003000 INTL 20050624)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x0000000137ffffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x137ffffff]
[    0.000000]   NODE_DATA [mem 0x137ffc000-0x137ffffff]
[    0.000000]  [ffffea0000000000-ffffea0004dfffff] PMD -> [ffff880133800000-ffff8801375fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00010000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x137ffffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00010000-0x0009bfff]
[    0.000000]   node   0: [mem 0x00100000-0xbb27bfff]
[    0.000000]   node   0: [mem 0xbb282000-0xbb3ecfff]
[    0.000000]   node   0: [mem 0xbb40f000-0xbb46efff]
[    0.000000]   node   0: [mem 0xbb70f000-0xbb716fff]
[    0.000000]   node   0: [mem 0xbb71f000-0xbb77efff]
[    0.000000]   node   0: [mem 0xbb79f000-0xbb7e0fff]
[    0.000000]   node   0: [mem 0xbb7ff000-0xbb7fffff]
[    0.000000]   node   0: [mem 0x100000000-0x137ffffff]
[    0.000000] On node 0 totalpages: 996478
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 6 pages reserved
[    0.000000]   DMA zone: 3910 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 16320 pages used for memmap
[    0.000000]   DMA32 zone: 746802 pages, LIFO batch:31
[    0.000000]   Normal zone: 3584 pages used for memmap
[    0.000000]   Normal zone: 225792 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009c000 - 000000000009d000
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000bb27c000 - 00000000bb282000
[    0.000000] PM: Registered nosave memory: 00000000bb3ed000 - 00000000bb40f000
[    0.000000] PM: Registered nosave memory: 00000000bb46f000 - 00000000bb470000
[    0.000000] PM: Registered nosave memory: 00000000bb470000 - 00000000bb4f1000
[    0.000000] PM: Registered nosave memory: 00000000bb4f1000 - 00000000bb70f000
[    0.000000] PM: Registered nosave memory: 00000000bb717000 - 00000000bb71f000
[    0.000000] PM: Registered nosave memory: 00000000bb77f000 - 00000000bb79f000
[    0.000000] PM: Registered nosave memory: 00000000bb7e1000 - 00000000bb7ff000
[    0.000000] PM: Registered nosave memory: 00000000bb800000 - 00000000c0000000
[    0.000000] PM: Registered nosave memory: 00000000c0000000 - 00000000e0000000
[    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
[    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000f080a000
[    0.000000] PM: Registered nosave memory: 00000000f080a000 - 00000000f080b000
[    0.000000] PM: Registered nosave memory: 00000000f080b000 - 00000000feaff000
[    0.000000] PM: Registered nosave memory: 00000000feaff000 - 00000000feb00000
[    0.000000] PM: Registered nosave memory: 00000000feb00000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec10000
[    0.000000] PM: Registered nosave memory: 00000000fec10000 - 00000000fed00000
[    0.000000] PM: Registered nosave memory: 00000000fed00000 - 00000000fed1c000
[    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed90000
[    0.000000] PM: Registered nosave memory: 00000000fed90000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ff000000
[    0.000000] PM: Registered nosave memory: 00000000ff000000 - 0000000100000000
[    0.000000] e820: [mem 0xc0000000-0xdfffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff880137c00000 s83584 r8192 d22912 u524288
[    0.000000] pcpu-alloc: s83584 r8192 d22912 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 976504
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-30-generic root=UUID=8664dc65-32f7-4b39-8d50-8623489bf15f ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] __ex_table already sorted, skipping sort
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 3825024k/5111808k available (6820k kernel code, 1125896k absent, 160888k reserved, 6347k data, 948k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:712 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 16252928 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.004000] Detected 2393.930 MHz processor.
[    0.000003] Calibrating delay loop (skipped), value calculated using timer frequency.. 4787.86 BogoMIPS (lpj=9575720)
[    0.000006] pid_max: default: 32768 minimum: 301
[    0.000026] Security Framework initialized
[    0.000041] AppArmor: AppArmor initialized
[    0.000042] Yama: becoming mindful.
[    0.000357] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.001420] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.001865] Mount-cache hash table entries: 256
[    0.002058] Initializing cgroup subsys cpuacct
[    0.002061] Initializing cgroup subsys memory
[    0.002068] Initializing cgroup subsys devices
[    0.002070] Initializing cgroup subsys freezer
[    0.002071] Initializing cgroup subsys blkio
[    0.002073] Initializing cgroup subsys perf_event
[    0.002099] CPU: Physical Processor ID: 0
[    0.002101] CPU: Processor Core ID: 0
[    0.002106] mce: CPU supports 9 MCE banks
[    0.002116] CPU0: Thermal monitoring handled by SMI
[    0.002124] using mwait in idle threads.
[    0.004348] ACPI: Core revision 20120320
[    0.035333] ftrace: allocating 27621 entries in 108 pages
[    0.050519] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.090136] CPU0: Intel(R) Core(TM) i3 CPU       M 370  @ 2.40GHz stepping 05
[    0.195219] Performance Events: PEBS fmt1+, 16-deep LBR, Westmere events, Intel PMU driver.
[    0.195225] CPUID marked event: 'bus cycles' unavailable
[    0.195228] ... version:                3
[    0.195229] ... bit width:              48
[    0.195230] ... generic registers:      4
[    0.195231] ... value mask:             0000ffffffffffff
[    0.195232] ... max period:             000000007fffffff
[    0.195233] ... fixed-purpose events:   3
[    0.195234] ... event mask:             000000070000000f
[    0.195402] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.206518] CPU1: Thermal monitoring handled by SMI
[    0.219765] CPU2: Thermal monitoring handled by SMI
[    0.195486] Booting Node   0, Processors  #1 #2 #3 Ok.
[    0.232995] CPU3: Thermal monitoring handled by SMI
[    0.235142] Brought up 4 CPUs
[    0.235153] Total of 4 processors activated (19151.44 BogoMIPS).
[    0.238041] devtmpfs: initialized
[    0.239117] EVM: security.selinux
[    0.239119] EVM: security.SMACK64
[    0.239120] EVM: security.capability
[    0.239172] PM: Registering ACPI NVS region [mem 0xbb470000-0xbb4f0fff] (528384 bytes)
[    0.239182] PM: Registering ACPI NVS region [mem 0xbb77f000-0xbb79efff] (131072 bytes)
[    0.239956] dummy: 
[    0.239991] RTC time:  9:59:45, date: 05/21/13
[    0.240026] NET: Registered protocol family 16
[    0.240126] Trying to unpack rootfs image as initramfs...
[    0.240187] ACPI: bus type pci registered
[    0.240257] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.240260] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.270003] PCI: Using configuration type 1 for base access
[    0.270957] bio: create slab <bio-0> at 0
[    0.271047] ACPI: Added _OSI(Module Device)
[    0.271049] ACPI: Added _OSI(Processor Device)
[    0.271050] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.271051] ACPI: Added _OSI(Processor Aggregator Device)
[    0.272822] ACPI: EC: Look up EC in DSDT
[    0.279023] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.279414] ACPI: SSDT 00000000bb71a918 00432 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.279837] ACPI: Dynamic OEM Table Load:
[    0.279839] ACPI: SSDT           (null) 00432 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.279983] ACPI: SSDT 00000000bb718018 00891 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.280388] ACPI: Dynamic OEM Table Load:
[    0.280390] ACPI: SSDT           (null) 00891 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.327296] ACPI: SSDT 00000000bb719a98 00303 (v01  PmRef    ApIst 00003000 INTL 20050624)
[    0.327766] ACPI: Dynamic OEM Table Load:
[    0.327769] ACPI: SSDT           (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20050624)
[    0.355100] ACPI: SSDT 00000000bb717d98 00119 (v01  PmRef    ApCst 00003000 INTL 20050624)
[    0.355540] ACPI: Dynamic OEM Table Load:
[    0.355542] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20050624)
[    0.393759] ACPI: Interpreter enabled
[    0.393768] ACPI: (supports S0 S3 S4 S5)
[    0.393810] ACPI: Using IOAPIC for interrupt routing
[    0.403739] ACPI: EC: GPE = 0x16, I/O: command/status = 0x66, data = 0x62
[    0.403934] ACPI: No dock devices found.
[    0.403939] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.404274] \_SB_.PCI0:_OSC invalid UUID
[    0.404276] _OSC request data:1 8 1f 
[    0.404280] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[    0.404776] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.404778] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.404780] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.404783] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    0.404784] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    0.404786] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000dffff]
[    0.404789] pci_root PNP0A08:00: host bridge window [mem 0xc0000000-0xfeafffff]
[    0.404818] PCI host bridge to bus 0000:00
[    0.404821] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.404823] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.404824] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.404826] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
[    0.404828] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
[    0.404830] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff]
[    0.404832] pci_bus 0000:00: root bus resource [mem 0xc0000000-0xfeafffff]
[    0.404842] pci 0000:00:00.0: [8086:0044] type 00 class 0x060000
[    0.404860] DMAR: BIOS has allocated no shadow GTT; disabling IOMMU for graphics
[    0.404883] pci 0000:00:02.0: [8086:0046] type 00 class 0x030000
[    0.404894] pci 0000:00:02.0: reg 10: [mem 0xf0000000-0xf03fffff 64bit]
[    0.404900] pci 0000:00:02.0: reg 18: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.404905] pci 0000:00:02.0: reg 20: [io  0x1800-0x1807]
[    0.404971] pci 0000:00:16.0: [8086:3b64] type 00 class 0x078000
[    0.405000] pci 0000:00:16.0: reg 10: [mem 0xf0804000-0xf080400f 64bit]
[    0.405092] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.405137] pci 0000:00:1a.0: [8086:3b3c] type 00 class 0x0c0320
[    0.405161] pci 0000:00:1a.0: reg 10: [mem 0xf0806000-0xf08063ff]
[    0.405272] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.405305] pci 0000:00:1b.0: [8086:3b56] type 00 class 0x040300
[    0.405326] pci 0000:00:1b.0: reg 10: [mem 0xf0800000-0xf0803fff 64bit]
[    0.405424] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.405455] pci 0000:00:1c.0: [8086:3b42] type 01 class 0x060400
[    0.405562] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.405595] pci 0000:00:1c.1: [8086:3b44] type 01 class 0x060400
[    0.405698] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.405730] pci 0000:00:1c.2: [8086:3b46] type 01 class 0x060400
[    0.405831] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.405865] pci 0000:00:1c.3: [8086:3b48] type 01 class 0x060400
[    0.405966] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.405998] pci 0000:00:1c.4: [8086:3b4a] type 01 class 0x060400
[    0.406101] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.406133] pci 0000:00:1c.5: [8086:3b4c] type 01 class 0x060400
[    0.406235] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.406273] pci 0000:00:1d.0: [8086:3b34] type 00 class 0x0c0320
[    0.406298] pci 0000:00:1d.0: reg 10: [mem 0xf0807000-0xf08073ff]
[    0.406407] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.406434] pci 0000:00:1e.0: [8086:2448] type 01 class 0x060401
[    0.406521] pci 0000:00:1f.0: [8086:3b09] type 00 class 0x060100
[    0.406652] pci 0000:00:1f.2: [8086:3b29] type 00 class 0x010601
[    0.406679] pci 0000:00:1f.2: reg 10: [io  0x1818-0x181f]
[    0.406690] pci 0000:00:1f.2: reg 14: [io  0x180c-0x180f]
[    0.406701] pci 0000:00:1f.2: reg 18: [io  0x1810-0x1817]
[    0.406713] pci 0000:00:1f.2: reg 1c: [io  0x1808-0x180b]
[    0.406724] pci 0000:00:1f.2: reg 20: [io  0x1820-0x183f]
[    0.406735] pci 0000:00:1f.2: reg 24: [mem 0xf0808000-0xf08087ff]
[    0.406802] pci 0000:00:1f.2: PME# supported from D3hot
[    0.406827] pci 0000:00:1f.3: [8086:3b30] type 00 class 0x0c0500
[    0.406849] pci 0000:00:1f.3: reg 10: [mem 0xf0809000-0xf08090ff 64bit]
[    0.406880] pci 0000:00:1f.3: reg 20: [io  0x1840-0x185f]
[    0.406932] pci 0000:00:1f.6: [8086:3b32] type 00 class 0x118000
[    0.406961] pci 0000:00:1f.6: reg 10: [mem 0xf080a000-0xf080afff 64bit]
[    0.407116] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.407215] pci 0000:03:00.0: [10ec:8176] type 00 class 0x028000
[    0.407241] pci 0000:03:00.0: reg 10: [io  0x2000-0x20ff]
[    0.407282] pci 0000:03:00.0: reg 18: [mem 0xf0500000-0xf0503fff 64bit]
[    0.407414] pci 0000:03:00.0: supports D1 D2
[    0.407415] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.417536] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    0.417544] pci 0000:00:1c.1:   bridge window [io  0x2000-0x2fff]
[    0.417550] pci 0000:00:1c.1:   bridge window [mem 0xf0500000-0xf05fffff]
[    0.417617] pci 0000:00:1c.2: PCI bridge to [bus 04-04]
[    0.417685] pci 0000:00:1c.3: PCI bridge to [bus 05-07]
[    0.417690] pci 0000:00:1c.3:   bridge window [io  0x3000-0x3fff]
[    0.417695] pci 0000:00:1c.3:   bridge window [mem 0xf0400000-0xf04fffff]
[    0.417702] pci 0000:00:1c.3:   bridge window [mem 0xf0a00000-0xf0bfffff 64bit pref]
[    0.417760] pci 0000:00:1c.4: PCI bridge to [bus 08-08]
[    0.417844] pci 0000:09:00.0: [10ec:8168] type 00 class 0x020000
[    0.417863] pci 0000:09:00.0: reg 10: [io  0x4000-0x40ff]
[    0.417892] pci 0000:09:00.0: reg 18: [mem 0xf0904000-0xf0904fff 64bit pref]
[    0.417910] pci 0000:09:00.0: reg 20: [mem 0xf0900000-0xf0903fff 64bit pref]
[    0.417922] pci 0000:09:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.417991] pci 0000:09:00.0: supports D1 D2
[    0.417993] pci 0000:09:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.425509] pci 0000:00:1c.5: PCI bridge to [bus 09-09]
[    0.425515] pci 0000:00:1c.5:   bridge window [io  0x4000-0x4fff]
[    0.425526] pci 0000:00:1c.5:   bridge window [mem 0xf0900000-0xf09fffff 64bit pref]
[    0.425602] pci 0000:00:1e.0: PCI bridge to [bus 0c-0c] (subtractive decode)
[    0.425615] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.425617] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.425619] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.425621] pci 0000:00:1e.0:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.425623] pci 0000:00:1e.0:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.425625] pci 0000:00:1e.0:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
[    0.425627] pci 0000:00:1e.0:   bridge window [mem 0xc0000000-0xfeafffff] (subtractive decode)
[    0.425675] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.425885] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.426002] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.426053] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.426103] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.426152] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.426201] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
[    0.426249] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[    0.426345] \_SB_.PCI0:_OSC invalid UUID
[    0.426347] _OSC request data:1 1f 1f 
[    0.426352]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.426382] \_SB_.PCI0:_OSC invalid UUID
[    0.426383] _OSC request data:1 0 1d 
[    0.426387]  pci0000:00: ACPI _OSC request failed (AE_ERROR), returned control mask: 0x1d
[    0.426388] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.430604] ACPI: PCI Root Bridge [CPBG] (domain 0000 [bus ff])
[    0.430660] PCI host bridge to bus 0000:ff
[    0.430668] pci 0000:ff:00.0: [8086:2c62] type 00 class 0x060000
[    0.430692] pci 0000:ff:00.1: [8086:2d01] type 00 class 0x060000
[    0.430712] pci 0000:ff:02.0: [8086:2d10] type 00 class 0x060000
[    0.430731] pci 0000:ff:02.1: [8086:2d11] type 00 class 0x060000
[    0.430749] pci 0000:ff:02.2: [8086:2d12] type 00 class 0x060000
[    0.430768] pci 0000:ff:02.3: [8086:2d13] type 00 class 0x060000
[    0.430802]  pci0000:ff: Requesting ACPI _OSC control (0x1d)
[    0.430805]  pci0000:ff: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.430806] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.431000] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.431045] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.431089] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.431131] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.431174] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.431217] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    0.431264] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.431307] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.431411] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.431420] vgaarb: loaded
[    0.431421] vgaarb: bridge control possible 0000:00:02.0
[    0.431579] SCSI subsystem initialized
[    0.431643] libata version 3.00 loaded.
[    0.431664] ACPI: bus type usb registered
[    0.431686] usbcore: registered new interface driver usbfs
[    0.431695] usbcore: registered new interface driver hub
[    0.431718] usbcore: registered new device driver usb
[    0.431795] PCI: Using ACPI for IRQ routing
[    0.441614] PCI: pci_cache_line_size set to 64 bytes
[    0.441714] e820: reserve RAM buffer [mem 0x0009c400-0x0009ffff]
[    0.441717] e820: reserve RAM buffer [mem 0xbb27c000-0xbbffffff]
[    0.441720] e820: reserve RAM buffer [mem 0xbb3ed000-0xbbffffff]
[    0.441722] e820: reserve RAM buffer [mem 0xbb46f000-0xbbffffff]
[    0.441724] e820: reserve RAM buffer [mem 0xbb717000-0xbbffffff]
[    0.441726] e820: reserve RAM buffer [mem 0xbb77f000-0xbbffffff]
[    0.441727] e820: reserve RAM buffer [mem 0xbb7e1000-0xbbffffff]
[    0.441729] e820: reserve RAM buffer [mem 0xbb800000-0xbbffffff]
[    0.441837] NetLabel: Initializing
[    0.441839] NetLabel:  domain hash size = 128
[    0.441839] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.441851] NetLabel:  unlabeled traffic allowed by default
[    0.441929] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.441935] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.443956] Switching to clocksource hpet
[    0.450043] AppArmor: AppArmor Filesystem Enabled
[    0.450075] pnp: PnP ACPI init
[    0.450092] ACPI: bus type pnp registered
[    0.450405] pnp 00:00: [bus 00-fe]
[    0.450408] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.450410] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.450412] pnp 00:00: [io  0x0d00-0xffff window]
[    0.450414] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.450416] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    0.450418] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    0.450420] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    0.450421] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    0.450423] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    0.450425] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    0.450427] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    0.450429] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    0.450430] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    0.450432] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    0.450434] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    0.450436] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    0.450438] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    0.450440] pnp 00:00: [mem 0xc0000000-0xfeafffff window]
[    0.450441] pnp 00:00: [mem 0xfed40000-0xfed44fff window]
[    0.450524] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.450563] pnp 00:01: [io  0x0000-0x001f]
[    0.450565] pnp 00:01: [io  0x0081-0x0091]
[    0.450567] pnp 00:01: [io  0x0093-0x009f]
[    0.450569] pnp 00:01: [io  0x00c0-0x00df]
[    0.450571] pnp 00:01: [dma 4]
[    0.450591] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.450598] pnp 00:02: [mem 0xff000000-0xffffffff]
[    0.450619] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
[    0.450697] pnp 00:03: [irq 0 disabled]
[    0.450708] pnp 00:03: [irq 8]
[    0.450710] pnp 00:03: [mem 0xfed00000-0xfed003ff]
[    0.450731] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.450741] pnp 00:04: [io  0x00f0]
[    0.450746] pnp 00:04: [irq 13]
[    0.450772] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.450783] pnp 00:05: [io  0x002e-0x002f]
[    0.450785] pnp 00:05: [io  0x004e-0x004f]
[    0.450786] pnp 00:05: [io  0x0061]
[    0.450789] pnp 00:05: [io  0x0063]
[    0.450791] pnp 00:05: [io  0x0065]
[    0.450793] pnp 00:05: [io  0x0067]
[    0.450794] pnp 00:05: [io  0x0070]
[    0.450796] pnp 00:05: [io  0x0080]
[    0.450797] pnp 00:05: [io  0x0092]
[    0.450799] pnp 00:05: [io  0x00b2-0x00b3]
[    0.450801] pnp 00:05: [io  0x0680-0x069f]
[    0.450802] pnp 00:05: [io  0x0500-0x050f]
[    0.450804] pnp 00:05: [io  0x0600-0x0603]
[    0.450806] pnp 00:05: [io  0xffff]
[    0.450807] pnp 00:05: [io  0x0400-0x047f]
[    0.450809] pnp 00:05: [io  0x1180-0x11ff]
[    0.450811] pnp 00:05: [io  0x1600-0x16fe]
[    0.450812] pnp 00:05: [io  0xfe00]
[    0.450814] pnp 00:05: [io  0x0068]
[    0.450816] pnp 00:05: [io  0x006c]
[    0.450817] pnp 00:05: [io  0x0700-0x070f]
[    0.450879] system 00:05: [io  0x0680-0x069f] has been reserved
[    0.450881] system 00:05: [io  0x0500-0x050f] has been reserved
[    0.450883] system 00:05: [io  0x0600-0x0603] has been reserved
[    0.450885] system 00:05: [io  0xffff] has been reserved
[    0.450887] system 00:05: [io  0x0400-0x047f] has been reserved
[    0.450889] system 00:05: [io  0x1180-0x11ff] has been reserved
[    0.450891] system 00:05: [io  0x1600-0x16fe] has been reserved
[    0.450893] system 00:05: [io  0xfe00] has been reserved
[    0.450895] system 00:05: [io  0x0700-0x070f] has been reserved
[    0.450899] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.450928] pnp 00:06: [io  0x06a0-0x06af]
[    0.450930] pnp 00:06: [io  0x06b0-0x06ff]
[    0.450963] system 00:06: [io  0x06a0-0x06af] has been reserved
[    0.450965] system 00:06: [io  0x06b0-0x06ff] has been reserved
[    0.450968] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.450996] pnp 00:07: [io  0x0070-0x0077]
[    0.451020] pnp 00:07: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.451029] pnp 00:08: [io  0x0060]
[    0.451031] pnp 00:08: [io  0x0064]
[    0.451037] pnp 00:08: [irq 1]
[    0.451062] pnp 00:08: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.451073] pnp 00:09: [irq 12]
[    0.451095] pnp 00:09: Plug and Play ACPI device, IDs LEN0017 PNP0f13 (active)
[    0.451356] pnp 00:0a: [mem 0xfed1c000-0xfed1ffff]
[    0.451359] pnp 00:0a: [mem 0xfed10000-0xfed13fff]
[    0.451360] pnp 00:0a: [mem 0xfed18000-0xfed18fff]
[    0.451362] pnp 00:0a: [mem 0xfed19000-0xfed19fff]
[    0.451364] pnp 00:0a: [mem 0xe0000000-0xefffffff]
[    0.451366] pnp 00:0a: [mem 0x00000000-0xffffffffffffffff disabled]
[    0.451367] pnp 00:0a: [mem 0xfeaff000-0xfeafffff]
[    0.451369] pnp 00:0a: [mem 0xfed20000-0xfed3ffff]
[    0.451371] pnp 00:0a: [mem 0xfed90000-0xfed8ffff disabled]
[    0.451373] pnp 00:0a: [mem 0xfed40000-0xfed44fff]
[    0.451374] pnp 00:0a: [mem 0xfed45000-0xfed8ffff]
[    0.451376] pnp 00:0a: [mem 0xff000000-0xffffffff]
[    0.451378] pnp 00:0a: [mem 0xfee00000-0xfeefffff]
[    0.451428] system 00:0a: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.451430] system 00:0a: [mem 0xfed10000-0xfed13fff] has been reserved
[    0.451433] system 00:0a: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.451435] system 00:0a: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.451437] system 00:0a: [mem 0xe0000000-0xefffffff] has been reserved
[    0.451439] system 00:0a: [mem 0xfeaff000-0xfeafffff] has been reserved
[    0.451441] system 00:0a: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.451443] system 00:0a: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.451446] system 00:0a: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.451450] system 00:0a: [mem 0xff000000-0xffffffff] has been reserved
[    0.451453] system 00:0a: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.451456] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.451595] pnp 00:0b: [bus ff]
[    0.451633] pnp 00:0b: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.451999] pnp: PnP ACPI: found 12 devices
[    0.452001] ACPI: ACPI bus type pnp unregistered
[    0.459171] pci 0000:00:1c.0: bridge window [io  0x1000-0x0fff] to [bus 02-02] add_size 1000
[    0.459176] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 02-02] add_size 200000
[    0.459179] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff] to [bus 02-02] add_size 200000
[    0.459190] pci 0000:00:1c.1: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 03-03] add_size 200000
[    0.459201] pci 0000:00:1c.2: bridge window [io  0x1000-0x0fff] to [bus 04-04] add_size 1000
[    0.459204] pci 0000:00:1c.2: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 04-04] add_size 200000
[    0.459206] pci 0000:00:1c.2: bridge window [mem 0x00100000-0x000fffff] to [bus 04-04] add_size 200000
[    0.459226] pci 0000:00:1c.4: bridge window [io  0x1000-0x0fff] to [bus 08-08] add_size 1000
[    0.459228] pci 0000:00:1c.4: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 08-08] add_size 200000
[    0.459230] pci 0000:00:1c.4: bridge window [mem 0x00100000-0x000fffff] to [bus 08-08] add_size 200000
[    0.459243] pci 0000:00:1c.5: bridge window [mem 0x00100000-0x001fffff] to [bus 09-09] add_size 400000
[    0.459261] pci 0000:00:1c.0: res[14]=[mem 0x00100000-0x000fffff] get_res_add_size add_size 200000
[    0.459264] pci 0000:00:1c.0: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.459266] pci 0000:00:1c.1: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.459268] pci 0000:00:1c.2: res[14]=[mem 0x00100000-0x000fffff] get_res_add_size add_size 200000
[    0.459270] pci 0000:00:1c.2: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.459272] pci 0000:00:1c.4: res[14]=[mem 0x00100000-0x000fffff] get_res_add_size add_size 200000
[    0.459274] pci 0000:00:1c.4: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.459276] pci 0000:00:1c.5: res[14]=[mem 0x00100000-0x001fffff] get_res_add_size add_size 400000
[    0.459278] pci 0000:00:1c.0: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.459280] pci 0000:00:1c.2: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.459282] pci 0000:00:1c.4: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.459288] pci 0000:00:1c.0: BAR 14: assigned [mem 0xc0000000-0xc01fffff]
[    0.459291] pci 0000:00:1c.0: BAR 15: assigned [mem 0xc0200000-0xc03fffff 64bit pref]
[    0.459294] pci 0000:00:1c.1: BAR 15: assigned [mem 0xc0400000-0xc05fffff 64bit pref]
[    0.459296] pci 0000:00:1c.2: BAR 14: assigned [mem 0xc0600000-0xc07fffff]
[    0.459299] pci 0000:00:1c.2: BAR 15: assigned [mem 0xc0800000-0xc09fffff 64bit pref]
[    0.459302] pci 0000:00:1c.4: BAR 14: assigned [mem 0xc0a00000-0xc0bfffff]
[    0.459304] pci 0000:00:1c.4: BAR 15: assigned [mem 0xc0c00000-0xc0dfffff 64bit pref]
[    0.459307] pci 0000:00:1c.5: BAR 14: assigned [mem 0xc0e00000-0xc12fffff]
[    0.459310] pci 0000:00:1c.0: BAR 13: assigned [io  0x5000-0x5fff]
[    0.459313] pci 0000:00:1c.2: BAR 13: assigned [io  0x6000-0x6fff]
[    0.459315] pci 0000:00:1c.4: BAR 13: assigned [io  0x7000-0x7fff]
[    0.459319] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.459323] pci 0000:00:1c.0:   bridge window [io  0x5000-0x5fff]
[    0.459329] pci 0000:00:1c.0:   bridge window [mem 0xc0000000-0xc01fffff]
[    0.459334] pci 0000:00:1c.0:   bridge window [mem 0xc0200000-0xc03fffff 64bit pref]
[    0.459342] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    0.459345] pci 0000:00:1c.1:   bridge window [io  0x2000-0x2fff]
[    0.459351] pci 0000:00:1c.1:   bridge window [mem 0xf0500000-0xf05fffff]
[    0.459356] pci 0000:00:1c.1:   bridge window [mem 0xc0400000-0xc05fffff 64bit pref]
[    0.459364] pci 0000:00:1c.2: PCI bridge to [bus 04-04]
[    0.459367] pci 0000:00:1c.2:   bridge window [io  0x6000-0x6fff]
[    0.459373] pci 0000:00:1c.2:   bridge window [mem 0xc0600000-0xc07fffff]
[    0.459378] pci 0000:00:1c.2:   bridge window [mem 0xc0800000-0xc09fffff 64bit pref]
[    0.459386] pci 0000:00:1c.3: PCI bridge to [bus 05-07]
[    0.459389] pci 0000:00:1c.3:   bridge window [io  0x3000-0x3fff]
[    0.459395] pci 0000:00:1c.3:   bridge window [mem 0xf0400000-0xf04fffff]
[    0.459400] pci 0000:00:1c.3:   bridge window [mem 0xf0a00000-0xf0bfffff 64bit pref]
[    0.459408] pci 0000:00:1c.4: PCI bridge to [bus 08-08]
[    0.459411] pci 0000:00:1c.4:   bridge window [io  0x7000-0x7fff]
[    0.459417] pci 0000:00:1c.4:   bridge window [mem 0xc0a00000-0xc0bfffff]
[    0.459422] pci 0000:00:1c.4:   bridge window [mem 0xc0c00000-0xc0dfffff 64bit pref]
[    0.459431] pci 0000:09:00.0: BAR 6: assigned [mem 0xf0920000-0xf093ffff pref]
[    0.459433] pci 0000:00:1c.5: PCI bridge to [bus 09-09]
[    0.459437] pci 0000:00:1c.5:   bridge window [io  0x4000-0x4fff]
[    0.459443] pci 0000:00:1c.5:   bridge window [mem 0xc0e00000-0xc12fffff]
[    0.459448] pci 0000:00:1c.5:   bridge window [mem 0xf0900000-0xf09fffff 64bit pref]
[    0.459455] pci 0000:00:1e.0: PCI bridge to [bus 0c-0c]
[    0.459535] pci 0000:00:1e.0: setting latency timer to 64
[    0.459540] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.459542] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.459544] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.459546] pci_bus 0000:00: resource 7 [mem 0x000d4000-0x000d7fff]
[    0.459548] pci_bus 0000:00: resource 8 [mem 0x000d8000-0x000dbfff]
[    0.459549] pci_bus 0000:00: resource 9 [mem 0x000dc000-0x000dffff]
[    0.459551] pci_bus 0000:00: resource 10 [mem 0xc0000000-0xfeafffff]
[    0.459553] pci_bus 0000:02: resource 0 [io  0x5000-0x5fff]
[    0.459555] pci_bus 0000:02: resource 1 [mem 0xc0000000-0xc01fffff]
[    0.459557] pci_bus 0000:02: resource 2 [mem 0xc0200000-0xc03fffff 64bit pref]
[    0.459559] pci_bus 0000:03: resource 0 [io  0x2000-0x2fff]
[    0.459561] pci_bus 0000:03: resource 1 [mem 0xf0500000-0xf05fffff]
[    0.459563] pci_bus 0000:03: resource 2 [mem 0xc0400000-0xc05fffff 64bit pref]
[    0.459565] pci_bus 0000:04: resource 0 [io  0x6000-0x6fff]
[    0.459567] pci_bus 0000:04: resource 1 [mem 0xc0600000-0xc07fffff]
[    0.459569] pci_bus 0000:04: resource 2 [mem 0xc0800000-0xc09fffff 64bit pref]
[    0.459571] pci_bus 0000:05: resource 0 [io  0x3000-0x3fff]
[    0.459573] pci_bus 0000:05: resource 1 [mem 0xf0400000-0xf04fffff]
[    0.459575] pci_bus 0000:05: resource 2 [mem 0xf0a00000-0xf0bfffff 64bit pref]
[    0.459577] pci_bus 0000:08: resource 0 [io  0x7000-0x7fff]
[    0.459578] pci_bus 0000:08: resource 1 [mem 0xc0a00000-0xc0bfffff]
[    0.459580] pci_bus 0000:08: resource 2 [mem 0xc0c00000-0xc0dfffff 64bit pref]
[    0.459583] pci_bus 0000:09: resource 0 [io  0x4000-0x4fff]
[    0.459584] pci_bus 0000:09: resource 1 [mem 0xc0e00000-0xc12fffff]
[    0.459586] pci_bus 0000:09: resource 2 [mem 0xf0900000-0xf09fffff 64bit pref]
[    0.459589] pci_bus 0000:0c: resource 4 [io  0x0000-0x0cf7]
[    0.459590] pci_bus 0000:0c: resource 5 [io  0x0d00-0xffff]
[    0.459592] pci_bus 0000:0c: resource 6 [mem 0x000a0000-0x000bffff]
[    0.459594] pci_bus 0000:0c: resource 7 [mem 0x000d4000-0x000d7fff]
[    0.459596] pci_bus 0000:0c: resource 8 [mem 0x000d8000-0x000dbfff]
[    0.459598] pci_bus 0000:0c: resource 9 [mem 0x000dc000-0x000dffff]
[    0.459600] pci_bus 0000:0c: resource 10 [mem 0xc0000000-0xfeafffff]
[    0.459639] NET: Registered protocol family 2
[    0.459753] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.460463] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.462395] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.462637] TCP: Hash tables configured (established 524288 bind 65536)
[    0.462639] TCP: reno registered
[    0.462647] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.462668] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.462755] NET: Registered protocol family 1
[    0.462773] pci 0000:00:02.0: Boot video device
[    0.462930] PCI: CLS 64 bytes, default 64
[    0.462932] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.462935] software IO TLB [mem 0xb727c000-0xbb27bfff] (64MB) mapped at [ffff8800b727c000-ffff8800bb27bfff]
[    0.462972] Simple Boot Flag at 0x36 set to 0x1
[    0.463490] audit: initializing netlink socket (disabled)
[    0.463500] type=2000 audit(1369130384.328:1): initialized
[    0.485871] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.487404] VFS: Disk quotas dquot_6.5.2
[    0.487443] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.487907] fuse init (API version 7.19)
[    0.488023] msgmni has been set to 7470
[    0.488424] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.488456] io scheduler noop registered
[    0.488459] io scheduler deadline registered (default)
[    0.488482] io scheduler cfq registered
[    0.488898] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.488911] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.488953] intel_idle: MWAIT substates: 0x1120
[    0.488955] intel_idle: v0.4 model 0x25
[    0.488956] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.499029] Freeing initrd memory: 15032k freed
[    0.689330] ACPI: AC Adapter [ACAD] (off-line)
[    0.689442] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.689954] ACPI: Lid Switch [LID]
[    0.689993] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.689996] ACPI: Power Button [PWRB]
[    0.690026] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.690029] ACPI: Power Button [PWRF]
[    0.690096] ACPI: Requesting acpi_cpufreq
[    1.458224] Refined TSC clocksource calibration: 2393.983 MHz.
[    1.458233] Switching to clocksource tsc
[    1.700800] thermal LNXTHERM:00: registered as thermal_zone0
[    1.700802] ACPI: Thermal Zone [TZ00] (63 C)
[    1.700827] ACPI: Battery Slot [BAT1] (battery present)
[    1.700844] GHES: HEST is not enabled!
[    1.700924] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.702291] Linux agpgart interface v0.103
[    1.702363] agpgart-intel 0000:00:00.0: Intel HD Graphics Chipset
[    1.702451] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    1.703267] agpgart-intel 0000:00:00.0: detected 32768K stolen memory
[    1.703422] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    1.704501] brd: module loaded
[    1.705092] loop: module loaded
[    1.705392] Fixed MDIO Bus: probed
[    1.705425] tun: Universal TUN/TAP device driver, 1.6
[    1.705426] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.705458] PPP generic driver version 2.4.2
[    1.705496] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.705543] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.705548] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    1.705554] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.705584] ehci_hcd 0000:00:1a.0: debug port 2
[    1.709480] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    1.709500] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xf0806000
[    1.717764] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.717813] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.717819] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.717824] usb usb1: Product: EHCI Host Controller
[    1.717829] usb usb1: Manufacturer: Linux 3.5.0-30-generic ehci_hcd
[    1.717834] usb usb1: SerialNumber: 0000:00:1a.0
[    1.717951] hub 1-0:1.0: USB hub found
[    1.717956] hub 1-0:1.0: 3 ports detected
[    1.718030] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.718034] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    1.718039] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.718065] ehci_hcd 0000:00:1d.0: debug port 2
[    1.721960] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    1.721974] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xf0807000
[    1.733742] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.733785] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.733791] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.733795] usb usb2: Product: EHCI Host Controller
[    1.733800] usb usb2: Manufacturer: Linux 3.5.0-30-generic ehci_hcd
[    1.733805] usb usb2: SerialNumber: 0000:00:1d.0
[    1.733902] hub 2-0:1.0: USB hub found
[    1.733905] hub 2-0:1.0: 3 ports detected
[    1.733955] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.733970] uhci_hcd: USB Universal Host Controller Interface driver
[    1.734009] usbcore: registered new interface driver libusual
[    1.734043] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.776309] i8042: Detected active multiplexing controller, rev 1.1
[    1.805310] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.805314] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.805340] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.805356] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.805372] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.805487] mousedev: PS/2 mouse device common for all mice
[    1.805669] rtc_cmos 00:07: RTC can wake from S4
[    1.805790] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    1.805851] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.805915] device-mapper: uevent: version 1.0.3
[    1.805974] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    1.806078] cpuidle: using governor ladder
[    1.806172] cpuidle: using governor menu
[    1.806174] EFI Variables Facility v0.08 2004-May-17
[    1.806466] ashmem: initialized
[    1.806697] TCP: cubic registered
[    1.807019] NET: Registered protocol family 10
[    1.807468] NET: Registered protocol family 17
[    1.807487] Key type dns_resolver registered
[    1.807867] PM: Hibernation image not present or could not be loaded.
[    1.807891] registered taskstats version 1
[    1.812631] Key type trusted registered
[    1.817252] Key type encrypted registered
[    1.821827]   Magic number: 13:965:980
[    1.822010] rtc_cmos 00:07: setting system clock to 2013-05-21 09:59:46 UTC (1369130386)
[    1.823278] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.823280] EDD information not available.
[    1.880812] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    2.008511] ACPI: Battery Slot [BAT1] (battery present)
[    2.010148] Freeing unused kernel memory: 948k freed
[    2.010297] Write protecting the kernel read-only data: 12288k
[    2.014475] Freeing unused kernel memory: 1360k freed
[    2.017867] Freeing unused kernel memory: 1064k freed
[    2.029237] usb 1-1: new high-speed USB device number 2 using ehci_hcd
[    2.037977] udevd[102]: starting version 175
[    2.161457] usb 1-1: New USB device found, idVendor=8087, idProduct=0020
[    2.161463] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.161857] hub 1-1:1.0: USB hub found
[    2.162060] hub 1-1:1.0: 6 ports detected
[    2.272845] usb 2-1: new high-speed USB device number 2 using ehci_hcd
[    2.291367] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.291501] r8169 0000:09:00.0: irq 40 for MSI/MSI-X
[    2.291711] r8169 0000:09:00.0: eth0: RTL8168d/8111d at 0xffffc90000668000, e8:9a:8f:de:1d:4b, XID 083000c0 IRQ 40
[    2.291715] r8169 0000:09:00.0: eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    2.294911] ahci 0000:00:1f.2: version 3.0
[    2.295001] ahci 0000:00:1f.2: irq 41 for MSI/MSI-X
[    2.295050] ahci: SSS flag set, parallel bus scan disabled
[    2.295104] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 4 ports 3 Gbps 0x33 impl SATA mode
[    2.295109] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck stag pm led clo pio slum part ems sxs apst 
[    2.295116] ahci 0000:00:1f.2: setting latency timer to 64
[    2.317302] scsi0 : ahci
[    2.317511] scsi1 : ahci
[    2.317580] scsi2 : ahci
[    2.317652] scsi3 : ahci
[    2.317902] scsi4 : ahci
[    2.317968] scsi5 : ahci
[    2.318197] ata1: SATA max UDMA/133 abar m2048@0xf0808000 port 0xf0808100 irq 41
[    2.318202] ata2: SATA max UDMA/133 abar m2048@0xf0808000 port 0xf0808180 irq 41
[    2.318204] ata3: DUMMY
[    2.318206] ata4: DUMMY
[    2.318210] ata5: SATA max UDMA/133 abar m2048@0xf0808000 port 0xf0808300 irq 41
[    2.318214] ata6: SATA max UDMA/133 abar m2048@0xf0808000 port 0xf0808380 irq 41
[    2.405314] usb 2-1: New USB device found, idVendor=8087, idProduct=0020
[    2.405322] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.405726] hub 2-1:1.0: USB hub found
[    2.405893] hub 2-1:1.0: 8 ports detected
[    2.476662] usb 1-1.4: new high-speed USB device number 3 using ehci_hcd
[    2.579869] usb 1-1.4: New USB device found, idVendor=0bda, idProduct=0158
[    2.579875] usb 1-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.579879] usb 1-1.4: Product: USB2.0-CRW
[    2.579882] usb 1-1.4: Manufacturer: Generic
[    2.579885] usb 1-1.4: SerialNumber: 20071114173400000
[    2.586626] Initializing USB Mass Storage driver...
[    2.586676] usbcore: registered new interface driver usb-storage
[    2.586677] USB Mass Storage support registered.
[    2.636258] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.637198] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    2.637202] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    2.656402] usb 1-1.6: new full-speed USB device number 4 using ehci_hcd
[    2.752598] usb 1-1.6: New USB device found, idVendor=0a5c, idProduct=217f
[    2.752607] usb 1-1.6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.752612] usb 1-1.6: Product: Broadcom Bluetooth Device
[    2.752617] usb 1-1.6: Manufacturer: Broadcom Corp
[    2.752622] usb 1-1.6: SerialNumber: CCAF78F2A794
[    2.824216] usb 2-1.1: new high-speed USB device number 3 using ehci_hcd
[    2.917522] usb 2-1.1: New USB device found, idVendor=1058, idProduct=07a8
[    2.917527] usb 2-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.917531] usb 2-1.1: Product: My Passport 07A8
[    2.917534] usb 2-1.1: Manufacturer: Western Digital
[    2.917537] usb 2-1.1: SerialNumber: 575834314142324639373332
[    2.918122] scsi6 : usb-storage 2-1.1:1.0
[    2.946278] ata1.00: ATA-8: ST9500325AS, 0020LVM1, max UDMA/100
[    2.946284] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.948230] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    2.948234] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    2.961060] ata1.00: configured for UDMA/100
[    2.961351] scsi 0:0:0:0: Direct-Access     ATA      ST9500325AS      0020 PQ: 0 ANSI: 5
[    2.961523] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    2.961568] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.961604] sd 0:0:0:0: [sda] Write Protect is off
[    2.961607] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.961640] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.987796] usb 2-1.4: new high-speed USB device number 4 using ehci_hcd
[    2.989984]  sda: sda1 sda2 sda3
[    2.991090] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.085856] usb 2-1.4: New USB device found, idVendor=17ef, idProduct=4815
[    3.085862] usb 2-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    3.085866] usb 2-1.4: Product: Integrated Camera
[    3.085869] usb 2-1.4: Manufacturer: Ricoh Company Ltd.
[    3.279176] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.282531] ata2.00: unexpected _GTF length (8)
[    3.282535] ata2.00: ATAPI: SlimtypeDVD A  DS8A5SH, XL63, max UDMA/100
[    3.284142] ata2.00: unexpected _GTF length (8)
[    3.284146] ata2.00: configured for UDMA/100
[    3.291013] scsi 1:0:0:0: CD-ROM            Slimtype DVD A  DS8A5SH   XL63 PQ: 0 ANSI: 5
[    3.296477] sr0: scsi3-mmc drive: 24x/8x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.296482] cdrom: Uniform CD-ROM driver Revision: 3.20
[    3.296727] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    3.296847] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    3.614562] ata5: SATA link down (SStatus 0 SControl 300)
[    3.914953] scsi 6:0:0:0: Direct-Access     WD       My Passport 07A8 1033 PQ: 0 ANSI: 6
[    3.915468] scsi 6:0:0:1: Enclosure         WD       SES Device       1033 PQ: 0 ANSI: 6
[    3.916986] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    3.917123] scsi 6:0:0:1: Attached scsi generic sg3 type 13
[    3.917585] sd 6:0:0:0: [sdb] 976707584 512-byte logical blocks: (500 GB/465 GiB)
[    3.918391] sd 6:0:0:0: [sdb] Write Protect is off
[    3.918394] sd 6:0:0:0: [sdb] Mode Sense: 53 00 10 08
[    3.919131] sd 6:0:0:0: [sdb] No Caching mode page present
[    3.919135] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    3.921803] sd 6:0:0:0: [sdb] No Caching mode page present
[    3.921811] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    3.934016] ata6: SATA link down (SStatus 0 SControl 300)
[    4.005778]  sdb: sdb1 sdb2 sdb3 sdb4 < sdb5 >
[    4.009621] sd 6:0:0:0: [sdb] No Caching mode page present
[    4.009630] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    4.009636] sd 6:0:0:0: [sdb] Attached SCSI disk
[    4.024943] scsi7 : usb-storage 1-1.4:1.0
[    4.025119] usbcore: registered new interface driver ums-realtek
[    4.078975] ses 6:0:0:1: Attached Enclosure device
[    4.266682] usb 1-1.4: USB disconnect, device number 3
[    4.714705] EXT4-fs (sdb2): mounted filesystem with ordered data mode. Opts: (null)
[   12.295622] Adding 4194300k swap on /dev/sdb1.  Priority:-1 extents:1 across:4194300k 
[   12.410442] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   12.466944] udevd[493]: starting version 175
[   12.762270] lp: driver loaded but no devices found
[   13.248540] EXT4-fs (sdb2): re-mounted. Opts: errors=remount-ro
[   13.379902] EXT4-fs (sdb3): mounted filesystem with ordered data mode. Opts: (null)
[   13.567331] ppdev: user-space parallel port driver
[   13.618991] type=1400 audit(1369123198.313:2): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=598 comm="apparmor_parser"
[   13.619470] type=1400 audit(1369123198.313:3): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=598 comm="apparmor_parser"
[   13.625136] Bluetooth: Core ver 2.16
[   13.625181] NET: Registered protocol family 31
[   13.625184] Bluetooth: HCI device and connection manager initialized
[   13.625186] Bluetooth: HCI socket layer initialized
[   13.625188] Bluetooth: L2CAP socket layer initialized
[   13.625194] Bluetooth: SCO socket layer initialized
[   13.671838] Bluetooth: RFCOMM TTY layer initialized
[   13.671847] Bluetooth: RFCOMM socket layer initialized
[   13.671849] Bluetooth: RFCOMM ver 1.11
[   13.675005] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   13.675011] Bluetooth: BNEP filters: protocol multicast
[   13.763454] wmi: Mapper loaded
[   13.809184] Non-volatile memory driver v1.3
[   14.044258] mei 0000:00:16.0: setting latency timer to 64
[   14.044336] mei 0000:00:16.0: irq 42 for MSI/MSI-X
[   14.048293] mei 0000:00:16.0: wd: failed to find the client
[   14.070257] intel ips 0000:00:1f.6: CPU TDP doesn't match expected value (found 25, expected 29)
[   14.070297] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled until i915 loads
[   14.070388] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 90
[   14.077867] ACPI Warning: 0x0000000000000460-0x000000000000047f SystemIO conflicts with Region \PMIO 1 (20120320/utaddress-251)
[   14.077873] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   14.077875] lpc_ich: Resource conflict(s) found affecting iTCO_wdt
[   14.077878] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20120320/utaddress-251)
[   14.077882] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   14.077885] ACPI Warning: 0x0000000000001180-0x00000000000011ff SystemIO conflicts with Region \GPIO 1 (20120320/utaddress-251)
[   14.077888] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   14.077889] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   14.092865] type=1400 audit(1369123198.789:4): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=814 comm="apparmor_parser"
[   14.093157] type=1400 audit(1369123198.789:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=813 comm="apparmor_parser"
[   14.093233] type=1400 audit(1369123198.789:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=814 comm="apparmor_parser"
[   14.093447] type=1400 audit(1369123198.789:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=814 comm="apparmor_parser"
[   14.093529] type=1400 audit(1369123198.789:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=813 comm="apparmor_parser"
[   14.093752] type=1400 audit(1369123198.789:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=813 comm="apparmor_parser"
[   14.123294] cfg80211: Calling CRDA to update world regulatory domain
[   14.149427] usbcore: registered new interface driver btusb
[   14.226431] microcode: CPU0 sig=0x20655, pf=0x10, revision=0x2
[   14.549308] Linux video capture interface: v2.00
[   14.648965] microcode: CPU1 sig=0x20655, pf=0x10, revision=0x2
[   14.650403] microcode: CPU2 sig=0x20655, pf=0x10, revision=0x2
[   14.651622] microcode: CPU3 sig=0x20655, pf=0x10, revision=0x2
[   14.653025] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   14.905552] cfg80211: World regulatory domain updated:
[   14.905558] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   14.905561] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.905564] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.905567] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.905569] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.905571] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.921214] uvcvideo: Found UVC 1.00 device Integrated Camera (17ef:4815)
[   14.922721] input: Integrated Camera as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.0/input/input4
[   14.922804] usbcore: registered new interface driver uvcvideo
[   14.922806] USB Video Class driver (1.1.1)
[   14.926765] [drm] Initialized drm 1.1.0 20060810
[   15.188691] thinkpad_acpi: ThinkPad ACPI Extras v0.24
[   15.188696] thinkpad_acpi: [http://ibm-acpi.sf.net/](http://ibm-acpi.sf.net/)
[   15.188699] thinkpad_acpi: ThinkPad BIOS 80ET54WW (1.31 ), EC 80HT38WW-1.220000
[   15.188701] thinkpad_acpi: Lenovo ThinkPad Edge, model 03192AG
[   15.189208] thinkpad_acpi: detected a 8-level brightness capable ThinkPad
[   15.192957] thinkpad_acpi: radio switch found; radios are enabled
[   15.192969] thinkpad_acpi: possible tablet mode switch found; ThinkPad in laptop mode
[   15.193105] thinkpad_acpi: This ThinkPad has standard ACPI backlight brightness control, supported by the ACPI video driver
[   15.193108] thinkpad_acpi: Disabling thinkpad-acpi brightness events by default...
[   15.193774] thinkpad_acpi: asked for hotkey mask 0x04000070, but firmware forced it to 0x00000070
[   15.199857] i915 0000:00:02.0: setting latency timer to 64
[   15.210749] thinkpad_acpi: rfkill switch tpacpi_bluetooth_sw: radio is unblocked
[   15.215029] Registered led device: tpacpi::thinklight
[   15.215223] Registered led device: tpacpi::power
[   15.215322] Registered led device: tpacpi::standby
[   15.215725] Registered led device: tpacpi::thinkvantage
[   15.229374] thinkpad_acpi: Standard ACPI backlight interface available, not loading native one
[   15.229469] thinkpad_acpi: Console audio control enabled, mode: monitor (read only)
[   15.231340] input: ThinkPad Extra Buttons as /devices/platform/thinkpad_acpi/input/input5
[   15.249907] i915 0000:00:02.0: irq 43 for MSI/MSI-X
[   15.249918] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   15.249919] [drm] Driver supports precise vblank timestamp query.
[   15.249969] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   15.266964] kvm: disabled by bios
[   15.271547] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   15.271550] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   15.271552] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   15.271554] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   15.271556] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   15.271558] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   15.271560] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   15.271562] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   15.271564] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   15.271566] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   15.271568] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   15.271571] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   15.271573] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   15.271575] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   15.271577] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   15.271580] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   15.271582] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   15.271584] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   15.271587] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   15.271589] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   15.271591] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   15.271593] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   15.271595] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   15.271597] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   15.271599] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   15.271601] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   15.271603] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   15.271780] rtl8192ce: Using firmware rtlwifi/rtl8192cfw.bin
[   15.358268] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   15.447771] init: failsafe main process (849) killed by TERM signal
[   15.465139] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   15.465378] rtlwifi: wireless switch is on
[   15.497873] type=1400 audit(1369123200.193:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=975 comm="apparmor_parser"
[   15.499551] type=1400 audit(1369123200.197:11): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=976 comm="apparmor_parser"
[   15.542923] psmouse serio4: synaptics: Touchpad model: 1, fw: 7.4, id: 0x1e0b1, caps: 0xd047b3/0xb40000/0xa0400
[   15.542932] psmouse serio4: synaptics: serio: Synaptics pass-through port at isa0060/serio4/input0
[   15.610514] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input6
[   15.802444] fbcon: inteldrmfb (fb0) is primary device
[   15.802657] Console: switching to colour frame buffer device 170x48
[   15.802690] fb0: inteldrmfb frame buffer device
[   15.802693] drm: registered panic notifier
[   16.031733] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.032574] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.088551] r8169 0000:09:00.0: eth0: link down
[   16.089001] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.089406] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.093516] ACPI Warning: _BQC returned an invalid level (20120320/video-494)
[   16.094686] acpi device:05: registered as cooling_device4
[   16.094923] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   16.094986] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input7
[   16.096887] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   16.099018] snd_hda_intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[   16.143597] init: anacron main process (1049) killed by TERM signal
[   16.197110] input: HDA Intel HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   16.197288] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   16.197346] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   18.653063] wlan0: authenticate with 00:0f:61:5e:5f:00
[   18.672812] wlan0: direct probe to 00:0f:61:5e:5f:00 (try 1/3)
[   18.877456] wlan0: direct probe to 00:0f:61:5e:5f:00 (try 2/3)
[   19.079733] wlan0: direct probe to 00:0f:61:5e:5f:00 (try 3/3)
[   19.259471] intel ips 0000:00:1f.6: i915 driver attached, reenabling gpu turbo
[   19.283384] wlan0: authentication with 00:0f:61:5e:5f:00 timed out
[   25.210679] psmouse serio5: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   25.457303] wlan0: authenticate with 00:0f:61:57:c5:90
[   25.476988] wlan0: direct probe to 00:0f:61:57:c5:90 (try 1/3)
[   25.540856] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio4/serio5/input/input11
[   25.680337] wlan0: direct probe to 00:0f:61:57:c5:90 (try 2/3)
[   25.883981] wlan0: direct probe to 00:0f:61:57:c5:90 (try 3/3)
[   26.087627] wlan0: authentication with 00:0f:61:57:c5:90 timed out
[   32.249451] wlan0: authenticate with 00:0f:61:57:3f:70
[   32.269327] wlan0: send auth to 00:0f:61:57:3f:70 (try 1/3)
[   32.275579] wlan0: authenticated
[   32.288844] wlan0: associate with 00:0f:61:57:3f:70 (try 1/3)
[   32.290163] wlan0: RX AssocResp from 00:0f:61:57:3f:70 (capab=0x21 status=0 aid=12)
[   32.290345] wlan0: associated
[   32.290756] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   32.290858] cfg80211: Calling CRDA for country: CH
[   32.294623] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   32.294627] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   32.294629] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   32.294631] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   32.294632] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   32.294634] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   32.294635] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   32.294637] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   32.294638] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   32.294640] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   32.294641] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   32.294643] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   32.294644] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   32.294646] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   32.294647] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   32.294649] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   32.294650] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   32.294651] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   32.294653] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   32.294654] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   32.294656] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   32.294657] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   32.294659] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   32.294660] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   32.294662] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   32.294663] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   32.294665] cfg80211: Disabling freq 2484 MHz
[   32.294669] cfg80211: Regulatory domain changed to country: CH
[   32.294670] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   32.294671] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   32.294673] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   32.294674] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   32.294676] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[   38.680374] wlan0: authenticate with 00:0f:61:5d:de:50
[   38.690500] wlan0: direct probe to 00:0f:61:5d:de:50 (try 1/3)
[   38.893419] wlan0: direct probe to 00:0f:61:5d:de:50 (try 2/3)
[   39.097095] wlan0: direct probe to 00:0f:61:5d:de:50 (try 3/3)
[   39.300765] wlan0: authentication with 00:0f:61:5d:de:50 timed out
[   45.462421] wlan0: deauthenticating from 00:0f:61:57:3f:70 by local choice (reason=2)
[   45.472291] cfg80211: All devices are disconnected, going to restore regulatory settings
[   45.472295] cfg80211: Restoring regulatory settings
[   45.472308] cfg80211: Calling CRDA to update world regulatory domain
[   45.472542] wlan0: authenticate with 00:0f:61:5e:5f:00
[   45.482689] wlan0: direct probe to 00:0f:61:5e:5f:00 (try 1/3)
[   45.482887] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   45.482890] cfg80211: World regulatory domain updated:
[   45.482892] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   45.482894] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   45.482896] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   45.482898] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   45.482900] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   45.482903] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   45.685715] wlan0: direct probe to 00:0f:61:5e:5f:00 (try 2/3)
[   45.889356] wlan0: direct probe to 00:0f:61:5e:5f:00 (try 3/3)
[   46.093004] wlan0: authentication with 00:0f:61:5e:5f:00 timed out
[   52.258786] wlan0: authenticate with 00:0f:61:58:45:20
[   52.278589] wlan0: send auth to 00:0f:61:58:45:20 (try 1/3)
[   52.282113] wlan0: authenticated
[   52.294254] wlan0: associate with 00:0f:61:58:45:20 (try 1/3)
[   52.295429] wlan0: RX AssocResp from 00:0f:61:58:45:20 (capab=0x421 status=0 aid=7)
[   52.295598] wlan0: associated
[   52.296143] cfg80211: Calling CRDA for country: CH
[   52.299825] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   52.299830] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   52.299832] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   52.299834] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   52.299835] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   52.299837] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   52.299838] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   52.299840] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   52.299841] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   52.299842] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   52.299844] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   52.299845] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   52.299847] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   52.299848] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   52.299850] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   52.299851] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   52.299852] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   52.299854] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   52.299855] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   52.299857] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   52.299858] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   52.299860] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   52.299861] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   52.299863] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   52.299864] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   52.299866] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   52.299867] cfg80211: Disabling freq 2484 MHz
[   52.299873] cfg80211: Regulatory domain changed to country: CH
[   52.299875] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   52.299876] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   52.299877] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   52.299879] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   52.299880] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[   68.814747] audit_printk_skb: 45 callbacks suppressed
[   68.814752] type=1400 audit(1369123253.605:27): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/telepathy/mission-control-5" name="/usr/share/gvfs/remote-volume-monitors/" pid=2068 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[  325.665407] type=1400 audit(1369123510.901:28): apparmor="DENIED" operation="capable" parent=1 profile="/usr/sbin/cupsd" pid=599 comm="cupsd" pid=599 comm="cupsd" capability=36  capname="block_suspend"
[  362.611581] type=1400 audit(1369123547.909:29): apparmor="DENIED" operation="capable" parent=1 profile="/usr/sbin/cupsd" pid=599 comm="cupsd" pid=599 comm="cupsd" capability=36  capname="block_suspend"
[  900.112113] type=1400 audit(1369124086.341:30): apparmor="DENIED" operation="capable" parent=1 profile="/usr/sbin/cupsd" pid=599 comm="cupsd" pid=599 comm="cupsd" capability=36  capname="block_suspend"
[ 1002.724475] wlan0: deauthenticating from 00:0f:61:58:45:20 by local choice (reason=3)
[ 1002.749306] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 1002.749320] cfg80211: Restoring regulatory settings
[ 1002.749334] cfg80211: Calling CRDA to update world regulatory domain
[ 1002.755878] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[ 1002.755885] cfg80211: World regulatory domain updated:
[ 1002.755886] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1002.755888] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1002.755890] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1002.755891] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1002.755893] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1002.755894] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1003.672591] wlan0: authenticate with 00:0f:61:57:3f:70
[ 1003.692196] wlan0: send auth to 00:0f:61:57:3f:70 (try 1/3)
[ 1003.703441] wlan0: authenticated
[ 1003.715638] wlan0: associate with 00:0f:61:57:3f:70 (try 1/3)
[ 1003.717004] wlan0: RX AssocResp from 00:0f:61:57:3f:70 (capab=0x21 status=0 aid=10)
[ 1003.717168] wlan0: associated
[ 1003.717698] cfg80211: Calling CRDA for country: CH
[ 1003.724399] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[ 1003.724409] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1003.724413] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[ 1003.724418] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1003.724422] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[ 1003.724426] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1003.724429] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[ 1003.724434] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1003.724437] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[ 1003.724441] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1003.724445] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[ 1003.724449] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1003.724452] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[ 1003.724456] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1003.724460] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[ 1003.724464] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1003.724468] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[ 1003.724472] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1003.724475] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[ 1003.724479] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1003.724483] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[ 1003.724487] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1003.724491] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[ 1003.724495] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1003.724498] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[ 1003.724502] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1003.724506] cfg80211: Disabling freq 2484 MHz
[ 1003.724514] cfg80211: Regulatory domain changed to country: CH
[ 1003.724517] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1003.724521] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 1003.724525] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 1003.724528] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 1003.724532] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[ 1569.104139] wlan0: deauthenticating from 00:0f:61:57:3f:70 by local choice (reason=3)
[ 1569.126917] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 1569.126924] cfg80211: Restoring regulatory settings
[ 1569.126929] cfg80211: Calling CRDA to update world regulatory domain
[ 1569.132095] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[ 1569.132106] cfg80211: World regulatory domain updated:
[ 1569.132111] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1569.132117] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1569.132123] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1569.132129] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1569.132135] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1569.132141] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1571.373613] init: anacron main process (2861) killed by TERM signal
[ 1571.490384] PM: Syncing filesystems ... done.
[ 1571.492262] PM: Preparing system for mem sleep
[ 1571.744647] Freezing user space processes ... (elapsed 0.01 seconds) done.
[ 1571.760688] Freezing remaining freezable tasks ... (elapsed 0.06 seconds) done.
[ 1571.824486] PM: Entering mem sleep
[ 1571.824560] Suspending console(s) (use no_console_suspend to debug)
[ 1572.023202] PM: suspend of drv:psmouse dev:serio5 complete after 198.807 msecs
[ 1572.023393] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[ 1572.219794] PM: suspend of drv:snd_hda_intel dev:0000:00:1b.0 complete after 116.708 msecs
[ 1573.972283] sd 0:0:0:0: [sda] Stopping disk
[ 1574.381102] PM: suspend of drv:sd dev:0:0:0:0 complete after 2361.805 msecs
[ 1574.381195] PM: suspend of drv:scsi dev:target0:0:0 complete after 2361.877 msecs
[ 1574.381283] PM: suspend of drv:scsi dev:host0 complete after 2361.828 msecs
[ 1574.381572] PM: suspend of drv: dev:ata1 complete after 2362.019 msecs
[ 1574.396018] PM: suspend of drv:ahci dev:0000:00:1f.2 complete after 2296.777 msecs
[ 1574.396093] PM: suspend of drv: dev:pci0000:00 complete after 2296.686 msecs
[ 1574.396168] PM: suspend of devices complete after 2575.914 msecs
[ 1574.396171] PM: suspend devices took 2.576 seconds
[ 1574.396327] PM: late suspend of devices complete after 0.155 msecs
[ 1574.396564] r8169 0000:09:00.0: wake-up capability enabled by ACPI
[ 1574.428167] ehci_hcd 0000:00:1d.0: wake-up capability enabled by ACPI
[ 1574.443988] ehci_hcd 0000:00:1a.0: wake-up capability enabled by ACPI
[ 1574.475890] PM: noirq suspend of devices complete after 79.687 msecs
[ 1574.476050] ACPI: Preparing to enter system sleep state S3
[ 1574.496158] PM: Saving platform NVS memory
[ 1574.498316] Disabling non-boot CPUs ...
[ 1574.500546] CPU 1 is now offline
[ 1574.603681] CPU 2 is now offline
[ 1574.707435] CPU 3 is now offline
[ 1574.707882] Extended CMOS year: 2000
[ 1574.708700] ACPI: Low-level resume complete
[ 1574.708760] PM: Restoring platform NVS memory
[ 1574.709197] CPU0: Thermal monitoring enabled (TM1)
[ 1574.709257] Extended CMOS year: 2000
[ 1574.709307] Enabling non-boot CPUs ...
[ 1574.709437] Booting Node 0 Processor 1 APIC 0x4
[ 1574.720472] CPU1: Thermal monitoring handled by SMI
[ 1574.723049] CPU1 is up
[ 1574.723121] Booting Node 0 Processor 2 APIC 0x1
[ 1574.734158] CPU2: Thermal monitoring handled by SMI
[ 1574.736763] CPU2 is up
[ 1574.736847] Booting Node 0 Processor 3 APIC 0x5
[ 1574.747880] CPU3: Thermal monitoring handled by SMI
[ 1574.750526] CPU3 is up
[ 1574.753396] ACPI: Waking up from system sleep state S3
[ 1574.900822] ehci_hcd 0000:00:1a.0: wake-up capability disabled by ACPI
[ 1574.901325] ehci_hcd 0000:00:1d.0: wake-up capability disabled by ACPI
[ 1574.901913] PM: noirq resume of devices complete after 1.301 msecs
[ 1574.902103] PM: early resume of devices complete after 0.123 msecs
[ 1574.902146] i915 0000:00:02.0: setting latency timer to 64
[ 1574.902194] mei 0000:00:16.0: irq 42 for MSI/MSI-X
[ 1574.902243] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[ 1574.902292] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[ 1574.902297] snd_hda_intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[ 1574.902308] pci 0000:00:1e.0: setting latency timer to 64
[ 1574.902333] rtlwifi: wireless switch is on
[ 1574.902337] ahci 0000:00:1f.2: setting latency timer to 64
[ 1574.902366] r8169 0000:09:00.0: wake-up capability disabled by ACPI
[ 1574.903094] mei 0000:00:16.0: wd: failed to find the client
[ 1575.080202] PM: resume of drv:usb dev:1-1.6 complete after 177.068 msecs
[ 1575.080207] PM: resume of drv: dev:ep_00 complete after 177.830 msecs
[ 1575.080277] PM: resume of drv:hub dev:1-1:1.0 complete after 177.947 msecs
[ 1575.080294] PM: resume of drv:hub dev:2-1:1.0 complete after 177.226 msecs
[ 1575.080297] PM: resume of drv: dev:ep_00 complete after 177.191 msecs
[ 1575.080302] PM: resume of drv: dev:ep_81 complete after 177.214 msecs
[ 1575.080307] PM: resume of drv:usb dev:2-1.4 complete after 176.720 msecs
[ 1575.080310] PM: resume of drv:usb dev:2-1.1 complete after 176.929 msecs
[ 1575.080321] PM: resume of drv: dev:ep_81 complete after 177.973 msecs
[ 1575.124060] Extended CMOS year: 2000
[ 1575.128344] PM: resume of drv: dev:ep_00 complete after 224.920 msecs
[ 1575.128372] PM: resume of drv:usb-storage dev:2-1.1:1.0 complete after 225.048 msecs
[ 1575.128410] PM: resume of drv: dev:ep_8b complete after 225.028 msecs
[ 1575.128415] PM: resume of drv: dev:ep_0a complete after 225.007 msecs
[ 1575.128420] PM: resume of drv:scsi dev:host6 complete after 225.065 msecs
[ 1575.128439] PM: resume of drv:scsi_host dev:host6 complete after 225.077 msecs
[ 1575.128446] PM: resume of drv:scsi dev:target6:0:0 complete after 224.783 msecs
[ 1575.128467] PM: resume of drv:sd dev:6:0:0:0 complete after 224.784 msecs
[ 1575.128472] PM: resume of drv:ses dev:6:0:0:1 complete after 224.743 msecs
[ 1575.128499] PM: resume of drv:scsi_device dev:6:0:0:0 complete after 224.794 msecs
[ 1575.128518] PM: resume of drv:scsi_device dev:6:0:0:1 complete after 224.768 msecs
[ 1575.152332] usb 2-1.4: reset high-speed USB device number 4 using ehci_hcd
[ 1575.235917] ata5: SATA link down (SStatus 0 SControl 300)
[ 1575.243912] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 1575.244493] ata2.00: unexpected _GTF length (8)
[ 1575.246005] ata2.00: unexpected _GTF length (8)
[ 1575.246009] ata2.00: configured for UDMA/100
[ 1575.252016] PM: resume of drv:scsi dev:host4 complete after 349.344 msecs
[ 1575.252043] PM: resume of drv:scsi_host dev:host4 complete after 349.353 msecs
[ 1575.253859] PM: resume of drv:uvcvideo dev:2-1.4:1.1 complete after 350.505 msecs
[ 1575.253865] PM: resume of drv:uvcvideo dev:2-1.4:1.0 complete after 350.546 msecs
[ 1575.253871] PM: resume of drv: dev:ep_00 complete after 350.499 msecs
[ 1575.253884] PM: resume of drv: dev:ep_81 complete after 350.554 msecs
[ 1575.255874] ata6: SATA link down (SStatus 0 SControl 300)
[ 1575.271932] PM: resume of drv:scsi dev:host5 complete after 369.258 msecs
[ 1575.271988] PM: resume of drv:scsi_host dev:host5 complete after 369.289 msecs
[ 1575.275955] PM: resume of drv:scsi dev:host1 complete after 373.452 msecs
[ 1575.275972] PM: resume of drv:scsi_host dev:host1 complete after 373.447 msecs
[ 1575.275976] PM: resume of drv:scsi dev:target1:0:0 complete after 372.624 msecs
[ 1575.276044] PM: resume of drv:sr dev:1:0:0:0 complete after 372.676 msecs
[ 1575.276110] PM: resume of drv:scsi_device dev:1:0:0:0 complete after 372.721 msecs
[ 1575.320068] usb 1-1.6: reset full-speed USB device number 4 using ehci_hcd
[ 1575.413866] btusb 1-1.6:1.0: no reset_resume for driver btusb?
[ 1575.413868] btusb 1-1.6:1.1: no reset_resume for driver btusb?
[ 1575.414155] PM: resume of drv:usb dev:1-1.6:1.0 complete after 511.586 msecs
[ 1575.414158] PM: resume of drv:usb dev:1-1.6:1.1 complete after 511.508 msecs
[ 1575.414165] PM: resume of drv:usb dev:1-1.6:1.2 complete after 511.450 msecs
[ 1575.414176] PM: resume of drv: dev:ep_81 complete after 511.589 msecs
[ 1575.414179] PM: resume of drv: dev:ep_03 complete after 511.492 msecs
[ 1575.414182] PM: resume of drv: dev:ep_83 complete after 511.510 msecs
[ 1575.414185] PM: resume of drv:usb dev:1-1.6:1.3 complete after 511.411 msecs
[ 1575.414190] PM: resume of drv: dev:ep_82 complete after 511.578 msecs
[ 1575.414201] PM: resume of drv: dev:ep_04 complete after 511.453 msecs
[ 1575.414205] PM: resume of drv: dev:ep_02 complete after 511.581 msecs
[ 1575.414206] PM: resume of drv: dev:ep_84 complete after 511.480 msecs
[ 1575.414210] PM: resume of drv: dev:ep_00 complete after 511.426 msecs
[ 1576.326010] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 1576.329719] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[ 1576.329721] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[ 1576.334025] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[ 1576.334027] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[ 1576.334396] ata1.00: configured for UDMA/100
[ 1576.350049] PM: resume of drv:scsi dev:host0 complete after 1449.474 msecs
[ 1576.350062] PM: resume of drv:ata_port dev:ata1 complete after 1228.094 msecs
[ 1576.350079] PM: resume of drv:scsi_host dev:host0 complete after 1449.450 msecs
[ 1576.350081] PM: resume of drv:scsi dev:target0:0:0 complete after 1448.747 msecs
[ 1576.350096] PM: resume of drv:sd dev:0:0:0:0 complete after 1448.752 msecs
[ 1576.350100] sd 0:0:0:0: [sda] Starting disk
[ 1576.377037] PM: resume of drv:scsi_device dev:0:0:0:0 complete after 1475.715 msecs
[ 1576.397508] PM: resume of devices complete after 1497.990 msecs
[ 1576.397753] PM: resume devices took 1.496 seconds
[ 1576.397859] PM: Finishing wakeup.
[ 1576.397860] Restarting tasks ... done.
[ 1576.495739] video LNXVIDEO:01: Restoring backlight state
[ 1579.214980] init: anacron main process (3326) killed by TERM signal
[ 1579.763927] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1579.830751] r8169 0000:09:00.0: eth0: link down
[ 1579.831319] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1582.787784] wlan0: authenticate with 00:0f:61:58:45:20
[ 1582.807188] wlan0: send auth to 00:0f:61:58:45:20 (try 1/3)
[ 1582.810704] wlan0: authenticated
[ 1582.822716] wlan0: associate with 00:0f:61:58:45:20 (try 1/3)
[ 1582.823788] wlan0: RX AssocResp from 00:0f:61:58:45:20 (capab=0x421 status=0 aid=12)
[ 1582.823920] wlan0: associated
[ 1582.824975] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1582.825833] cfg80211: Calling CRDA for country: CH
[ 1582.829460] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[ 1582.829465] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1582.829467] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[ 1582.829469] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1582.829470] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[ 1582.829472] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1582.829473] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[ 1582.829475] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1582.829476] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[ 1582.829478] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1582.829479] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[ 1582.829481] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1582.829482] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[ 1582.829484] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1582.829485] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[ 1582.829487] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1582.829488] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[ 1582.829490] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1582.829491] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[ 1582.829493] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1582.829494] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[ 1582.829496] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1582.829497] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[ 1582.829499] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1582.829500] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[ 1582.829502] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1582.829503] cfg80211: Disabling freq 2484 MHz
[ 1582.829507] cfg80211: Regulatory domain changed to country: CH
[ 1582.829509] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1582.829510] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 1582.829512] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 1582.829513] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 1582.829514] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)



```

Tell me if you need any other information.

Thanks
Mamoun

---

### Post by ajgreeny on 2013-05-21
I believe it will always be much slower to boot on an external drive that an internal one; the basic I/O transfer speeds are so much slower on USB2 than when using an internal sata drive.  Whether that 2 mins is normal or not, I can not tell you, as I have never used an external hard drive for an OS, just for data storage, where the I/O speeds are not quite so much of a problem.

---

### Post by oldfred on 2013-05-21
Please use Code tags, # in advanced editor on long text outputs.

I do not know wlan issues, but that seems to consistently be the gaps in you log. Not sure if other issue on cups is the same or not. Do you have a wireless printer?

    ```
32.294676] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[   38.680374] [COLOR=#ff0000]wlan0[/COLOR]: authenticate with 00:0f:61:5d:de:50

   46.093004] wlan0: authentication with 00:0f:61:5e:5f:00 timed out
[   52.258786] [COLOR=#ff0000]wlan0[/COLOR]: authenticate with 00:0f:61:58:45:20

   [   52.299880] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[   68.814747] audit_printk_skb: 45 callbacks suppressed
[   68.814752] type=1400 audit(1369123253.605:27): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/telepathy/mission-control-5" name="/usr/share/gvfs/remote-volume-monitors/" pid=2068 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[  325.665407] type=1400 audit(1369123510.901:28): apparmor="DENIED" operation="capable" parent=1 profile="/usr/sbin/cupsd" pid=599 comm="cupsd" pid=599 comm="cupsd" capability=36  capname="block_suspend"
[  362.611581] type=1400 audit(1369123547.909:29): apparmor="DENIED" operation="capable" parent=1 profile="/usr/sbin/cupsd" pid=599 comm="cupsd" pid=599 comm="cupsd" capability=36  capname="block_suspend"
[  900.112113] type=1400 audit(1369124086.341:30): apparmor="DENIED" operation="capable" parent=1 profile="/usr/sbin/cupsd" pid=599 comm="cupsd" pid=599 comm="cupsd" capability=36  capname="block_suspend"
[ 1002.724475][COLOR=#ff0000] wlan0[/COLOR]: deauthenticating from 00:0f:61:58:45:20 by local choice (reason=3)
```

---

### Post by Mamoun on 2013-05-23
Hi,

No I don't have a wireless printer. I still beleive that it's not normal.
Maybe I'll try to reinsall ubuntu when I have time.

Thanks anyway =)

---

### Post by HiImTye on 2013-05-23
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
you will see slow speeds booting from USB by the nature of how USB functions, but I don't know if 2 minutes is normal. try using a liveUSB and see if it is comparable. additionally, check /var/log/syslog and /var/log/kern.log for any large pauses to see if anything is hanging at boot

---

### Post by Mamoun on 2013-05-23
Hi,

I tried with a liveUSB and it works in ~20s. This is real strange.
What am I supposed to look for in those file ? (Sorry, I'm a new ubuntu user)

Thanks

---

### Post by HiImTye on 2013-05-23
look at the time stamps at the start of the line and see if there are any large hangs

---

