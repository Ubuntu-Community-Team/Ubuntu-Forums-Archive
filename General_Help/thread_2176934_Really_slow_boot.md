---
title: "Really slow boot"
date: 2013-09-26
forum: General Help
---

### Post by nlucool on 2013-09-26
Hello everyone, my name is Nicolas.

My Ubuntu 13.04 takes about 3 minutes to boot up and I have no idea what to do

As I see it, i think the problem might be here

```

[    3.445884] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   27.507776] Adding 2110460k swap on /dev/sda5.  Priority:-1 extents:1 across:2110460k 

```

and/or here

```

[   37.377771] init: anacron main process (1334) killed by TERM signal
[  116.812284] ata2.00: exception Emask 0x10 SAct 0x0 SErr 0x50000 action 0xe frozen

```

This is the complete message from dmesg 

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.8.0-30-lowlatency (buildd@lamiak) (gcc version 4.7.3 (Ubuntu/Linaro 4.7.3-1ubuntu1) ) #22-Ubuntu SMP PREEMPT Mon Aug 26 22:31:40 UTC 2013 (Ubuntu 3.8.0-30.22-lowlatency 3.8.13.6)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-30-lowlatency root=UUID=43d608d7-f942-489b-a7c6-16e7c87b297b ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009e7ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009e800-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000cee79fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000cee7a000-0x00000000ceeb9fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000ceeba000-0x00000000ceecafff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ceecb000-0x00000000ceee0fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000ceee1000-0x00000000cef0ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000cef10000-0x00000000cef10fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000cef11000-0x00000000cef13fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000cef14000-0x00000000cef15fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000cef16000-0x00000000cef19fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000cef1a000-0x00000000cef1cfff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000cef1d000-0x00000000cef20fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000cef21000-0x00000000cef2ffff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000cef30000-0x00000000cfffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed10000-0x00000000fed13fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed18000-0x00000000fed19fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffa00000-0x00000000ffbfffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffe00000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000012bffffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.6 present.
[    0.000000] DMI: Sony Corporation VPCCW25FL/VAIO, BIOS R0170Y7 05/14/2010
[    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x12c000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-E7FFF uncachable
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FC0000000 write-back
[    0.000000]   2 base 0C0000000 mask FF0000000 write-back
[    0.000000]   3 base 100000000 mask FE0000000 write-back
[    0.000000]   4 base 120000000 mask FF0000000 write-back
[    0.000000]   5 base 12C000000 mask FFC000000 uncachable
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 256MB, type WB
[    0.000000] reg 3, base: 4GB, range: 512MB, type WB
[    0.000000] reg 4, base: 4608MB, range: 256MB, type WB
[    0.000000] reg 5, base: 4800MB, range: 64MB, type UC
[    0.000000] total RAM covered: 4032M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 64K     num_reg: 6      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 256MB, type WB
[    0.000000] reg 3, base: 4GB, range: 512MB, type WB
[    0.000000] reg 4, base: 4608MB, range: 128MB, type WB
[    0.000000] reg 5, base: 4736MB, range: 64MB, type WB
[    0.000000] e820: update [mem 0xd0000000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xcee7a max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000fc980-0x000fc98f] mapped at [ffff8800000fc980]
[    0.000000] initial memory mapped: [mem 0x00000000-0x1fffffff]
[    0.000000] Base memory trampoline at [ffff880000098000] 98000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0xcee79fff]
[    0.000000]  [mem 0x00000000-0xcedfffff] page 2M
[    0.000000]  [mem 0xcee00000-0xcee79fff] page 4k
[    0.000000] kernel direct mapping tables up to 0xcee79fff @ [mem 0x1fffa000-0x1fffffff]
[    0.000000] init_memory_mapping: [mem 0x100000000-0x12bffffff]
[    0.000000]  [mem 0x100000000-0x12bffffff] page 2M
[    0.000000] kernel direct mapping tables up to 0x12bffffff @ [mem 0xcee78000-0xcee79fff]
[    0.000000] RAMDISK: [mem 0x360ec000-0x3706dfff]
[    0.000000] ACPI: RSDP 00000000000f0410 00024 (v02   Sony)
[    0.000000] ACPI: XSDT 00000000cef1be18 0005C (v01   Sony     VAIO 20100514 MSFT 00010013)
[    0.000000] ACPI: FACP 00000000cef14d98 000F4 (v04   Sony     VAIO 20100514 MSFT 00010013)
[    0.000000] ACPI Warning: 32/64 FACS address mismatch in FADT - two FACS tables! (20121018/tbfadt-394)
[    0.000000] ACPI BIOS Bug: Warning: 32/64X FACS address mismatch in FADT - 0xCEF2CF40/0x00000000CEF2FD40, using 32 (20121018/tbfadt-521)
[    0.000000] ACPI: DSDT 00000000ceecb018 0A3D8 (v01   Sony     VAIO 20100514 INTL 20051117)
[    0.000000] ACPI: FACS 00000000cef2cf40 00040
[    0.000000] ACPI: APIC 00000000cef1af18 0008C (v02   Sony     VAIO 20100514 MSFT 00010013)
[    0.000000] ACPI: MCFG 00000000cef2ed18 0003C (v01   Sony     VAIO 20100514 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000cef2ec98 00038 (v01   Sony     VAIO 20100514 MSFT 00000003)
[    0.000000] ACPI: SLIC 00000000cef27a18 00176 (v01   Sony     VAIO 20100514 Sony 01000000)
[    0.000000] ACPI: SSDT 00000000cef15018 009F1 (v01   Sony     VAIO 20100514 INTL 20051117)
[    0.000000] ACPI: SSDT 00000000cef14c18 0011D (v01   Sony     VAIO 20100514 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000012bffffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x12bffffff]
[    0.000000]   NODE_DATA [mem 0x12bffb000-0x12bffffff]
[    0.000000]  [ffffea0000000000-ffffea0004bfffff] PMD -> [ffff880127600000-ffff88012b5fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00010000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x12bffffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00010000-0x0009dfff]
[    0.000000]   node   0: [mem 0x00100000-0xcee79fff]
[    0.000000]   node   0: [mem 0x100000000-0x12bffffff]
[    0.000000] On node 0 totalpages: 1027592
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 6 pages reserved
[    0.000000]   DMA zone: 3912 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 13178 pages used for memmap
[    0.000000]   DMA32 zone: 830208 pages, LIFO batch:31
[    0.000000]   Normal zone: 2816 pages used for memmap
[    0.000000]   Normal zone: 177408 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x04] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x05] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x06] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] smpboot: Allowing 8 CPUs, 4 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000cee7a000 - 00000000ceeba000
[    0.000000] PM: Registered nosave memory: 00000000ceeba000 - 00000000ceecb000
[    0.000000] PM: Registered nosave memory: 00000000ceecb000 - 00000000ceee1000
[    0.000000] PM: Registered nosave memory: 00000000ceee1000 - 00000000cef10000
[    0.000000] PM: Registered nosave memory: 00000000cef10000 - 00000000cef11000
[    0.000000] PM: Registered nosave memory: 00000000cef11000 - 00000000cef14000
[    0.000000] PM: Registered nosave memory: 00000000cef14000 - 00000000cef16000
[    0.000000] PM: Registered nosave memory: 00000000cef16000 - 00000000cef1a000
[    0.000000] PM: Registered nosave memory: 00000000cef1a000 - 00000000cef1d000
[    0.000000] PM: Registered nosave memory: 00000000cef1d000 - 00000000cef21000
[    0.000000] PM: Registered nosave memory: 00000000cef21000 - 00000000cef30000
[    0.000000] PM: Registered nosave memory: 00000000cef30000 - 00000000d0000000
[    0.000000] PM: Registered nosave memory: 00000000d0000000 - 00000000f8000000
[    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000fc000000
[    0.000000] PM: Registered nosave memory: 00000000fc000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
[    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fed10000
[    0.000000] PM: Registered nosave memory: 00000000fed10000 - 00000000fed14000
[    0.000000] PM: Registered nosave memory: 00000000fed14000 - 00000000fed18000
[    0.000000] PM: Registered nosave memory: 00000000fed18000 - 00000000fed1a000
[    0.000000] PM: Registered nosave memory: 00000000fed1a000 - 00000000fed1c000
[    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
[    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffa00000
[    0.000000] PM: Registered nosave memory: 00000000ffa00000 - 00000000ffc00000
[    0.000000] PM: Registered nosave memory: 00000000ffc00000 - 00000000ffe00000
[    0.000000] PM: Registered nosave memory: 00000000ffe00000 - 0000000100000000
[    0.000000] e820: [mem 0xd0000000-0xf7ffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88012bc00000 s85376 r8192 d21120 u262144
[    0.000000] pcpu-alloc: s85376 r8192 d21120 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1011528
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-30-lowlatency root=UUID=43d608d7-f942-489b-a7c6-16e7c87b297b ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] __ex_table already sorted, skipping sort
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 3946220k/4915200k available (7064k kernel code, 804832k absent, 164148k reserved, 6182k data, 940k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Preemptible hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     Dump stacks of tasks blocking RCU-preempt GP.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 16777216 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.001000] tsc: Detected 2128.017 MHz processor
[    0.000003] Calibrating delay loop (skipped), value calculated using timer frequency.. 4256.03 BogoMIPS (lpj=2128017)
[    0.000006] pid_max: default: 32768 minimum: 301
[    0.000035] Security Framework initialized
[    0.000050] AppArmor: AppArmor initialized
[    0.000051] Yama: becoming mindful.
[    0.000449] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.001481] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.001889] Mount-cache hash table entries: 256
[    0.002160] Initializing cgroup subsys cpuacct
[    0.002164] Initializing cgroup subsys memory
[    0.002171] Initializing cgroup subsys devices
[    0.002173] Initializing cgroup subsys freezer
[    0.002175] Initializing cgroup subsys blkio
[    0.002177] Initializing cgroup subsys perf_event
[    0.002180] Initializing cgroup subsys hugetlb
[    0.002206] CPU: Physical Processor ID: 0
[    0.002208] CPU: Processor Core ID: 0
[    0.002213] mce: CPU supports 9 MCE banks
[    0.002223] CPU0: Thermal monitoring handled by SMI
[    0.002232] process: using mwait in idle threads
[    0.002236] Last level iTLB entries: 4KB 512, 2MB 7, 4MB 7
[    0.002236] Last level dTLB entries: 4KB 512, 2MB 32, 4MB 32
[    0.002236] tlb_flushall_shift: 6
[    0.002398] Freeing SMP alternatives: 24k freed
[    0.003615] ACPI: Core revision 20121018
[    0.015677] ftrace: allocating 26704 entries in 105 pages
[    0.032608] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=0 pin2=0
[    0.042609] smpboot: CPU0: Intel(R) Core(TM) i3 CPU       M 330  @ 2.13GHz (fam: 06, model: 25, stepping: 02)
[    0.144079] Performance Events: PEBS fmt1+, 16-deep LBR, Westmere events, Intel PMU driver.
[    0.144086] perf_event_intel: CPUID marked event: 'bus cycles' unavailable
[    0.144088] ... version:                3
[    0.144090] ... bit width:              48
[    0.144091] ... generic registers:      4
[    0.144092] ... value mask:             0000ffffffffffff
[    0.144093] ... max period:             000000007fffffff
[    0.144094] ... fixed-purpose events:   3
[    0.144096] ... event mask:             000000070000000f
[    0.167289] CPU1: Thermal monitoring handled by SMI
[    0.169491] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.182286] CPU2: Thermal monitoring handled by SMI
[    0.197282] CPU3: Thermal monitoring handled by SMI
[    0.156154] smpboot: Booting Node   0, Processors  #1 #2 #3
[    0.199389] Brought up 4 CPUs
[    0.199394] smpboot: Total of 4 processors activated (17024.13 BogoMIPS)
[    0.202059] devtmpfs: initialized
[    0.203218] EVM: security.selinux
[    0.203220] EVM: security.SMACK64
[    0.203221] EVM: security.capability
[    0.203271] PM: Registering ACPI NVS region [mem 0xcee7a000-0xceeb9fff] (262144 bytes)
[    0.203277] PM: Registering ACPI NVS region [mem 0xceecb000-0xceee0fff] (90112 bytes)
[    0.203280] PM: Registering ACPI NVS region [mem 0xcef10000-0xcef10fff] (4096 bytes)
[    0.203281] PM: Registering ACPI NVS region [mem 0xcef14000-0xcef15fff] (8192 bytes)
[    0.203283] PM: Registering ACPI NVS region [mem 0xcef21000-0xcef2ffff] (61440 bytes)
[    0.204304] regulator-dummy: no parameters
[    0.204361] NET: Registered protocol family 16
[    0.204520] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.204522] ACPI: bus type pci registered
[    0.204595] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.204598] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.211027] PCI: Using configuration type 1 for base access
[    0.211973] bio: create slab <bio-0> at 0
[    0.212078] ACPI: Added _OSI(Module Device)
[    0.212080] ACPI: Added _OSI(Processor Device)
[    0.212082] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.212084] ACPI: Added _OSI(Processor Aggregator Device)
[    0.213863] ACPI: EC: Look up EC in DSDT
[    0.215541] ACPI: Executed 1 blocks of module-level executable AML code
[    0.218815] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.221278] ACPI: SSDT 00000000cef19c18 003A0 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.221697] ACPI: Dynamic OEM Table Load:
[    0.221700] ACPI: SSDT           (null) 003A0 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.221828] ACPI: SSDT 00000000cef17618 005CD (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.222238] ACPI: Dynamic OEM Table Load:
[    0.222241] ACPI: SSDT           (null) 005CD (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.222528] ACPI: SSDT 00000000cef18a98 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.222990] ACPI: Dynamic OEM Table Load:
[    0.222992] ACPI: SSDT           (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.223122] ACPI: SSDT 00000000cef16d98 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.223568] ACPI: Dynamic OEM Table Load:
[    0.223571] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.629287] ACPI: Interpreter enabled
[    0.629293] ACPI: (supports S0 S3 S4 S5)
[    0.629313] ACPI: Using IOAPIC for interrupt routing
[    0.646544] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.646728] ACPI: No dock devices found.
[    0.646733] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.647030] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    0.647033] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.647189] \_SB_.PCI0:_OSC invalid UUID
[    0.647191] _OSC request data:1 8 0 
[    0.647693] PCI host bridge to bus 0000:00
[    0.647698] pci_bus 0000:00: root bus resource [bus 00-3e]
[    0.647700] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.647702] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.647704] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.647706] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff]
[    0.647708] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
[    0.647710] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
[    0.647712] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff]
[    0.647714] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000e3fff]
[    0.647716] pci_bus 0000:00: root bus resource [mem 0x000e4000-0x000e7fff]
[    0.647718] pci_bus 0000:00: root bus resource [mem 0xd0000000-0xfeafffff]
[    0.647729] pci 0000:00:00.0: [8086:0044] type 00 class 0x060000
[    0.647748] DMAR: BIOS has allocated no shadow GTT; disabling IOMMU for graphics
[    0.647772] pci 0000:00:01.0: [8086:0045] type 01 class 0x060400
[    0.647809] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.647868] pci 0000:00:1a.0: [8086:3b3c] type 00 class 0x0c0320
[    0.647895] pci 0000:00:1a.0: reg 10: [mem 0xe8e08000-0xe8e083ff]
[    0.648007] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.648041] pci 0000:00:1b.0: [8086:3b56] type 00 class 0x040300
[    0.648063] pci 0000:00:1b.0: reg 10: [mem 0xe8e00000-0xe8e03fff 64bit]
[    0.648169] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.648201] pci 0000:00:1c.0: [8086:3b42] type 01 class 0x060400
[    0.648304] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.648337] pci 0000:00:1c.1: [8086:3b44] type 01 class 0x060400
[    0.648439] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.648473] pci 0000:00:1c.2: [8086:3b46] type 01 class 0x060400
[    0.648576] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.648612] pci 0000:00:1c.5: [8086:3b4c] type 01 class 0x060400
[    0.648713] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.648755] pci 0000:00:1d.0: [8086:3b34] type 00 class 0x0c0320
[    0.648781] pci 0000:00:1d.0: reg 10: [mem 0xe8e07000-0xe8e073ff]
[    0.648896] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.648923] pci 0000:00:1e.0: [8086:2448] type 01 class 0x060401
[    0.649015] pci 0000:00:1f.0: [8086:3b03] type 00 class 0x060100
[    0.649154] pci 0000:00:1f.2: [8086:3b2f] type 00 class 0x010601
[    0.649184] pci 0000:00:1f.2: reg 10: [io  0xe070-0xe077]
[    0.649196] pci 0000:00:1f.2: reg 14: [io  0xe060-0xe063]
[    0.649208] pci 0000:00:1f.2: reg 18: [io  0xe050-0xe057]
[    0.649219] pci 0000:00:1f.2: reg 1c: [io  0xe040-0xe043]
[    0.649231] pci 0000:00:1f.2: reg 20: [io  0xe020-0xe03f]
[    0.649243] pci 0000:00:1f.2: reg 24: [mem 0xe8e06000-0xe8e067ff]
[    0.649312] pci 0000:00:1f.2: PME# supported from D3hot
[    0.649339] pci 0000:00:1f.3: [8086:3b30] type 00 class 0x0c0500
[    0.649360] pci 0000:00:1f.3: reg 10: [mem 0xe8e05000-0xe8e050ff 64bit]
[    0.649392] pci 0000:00:1f.3: reg 20: [io  0xe000-0xe01f]
[    0.649471] pci 0000:01:00.0: [10de:0a2b] type 00 class 0x030000
[    0.649485] pci 0000:01:00.0: reg 10: [mem 0xe2000000-0xe2ffffff]
[    0.649500] pci 0000:01:00.0: reg 14: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.649514] pci 0000:01:00.0: reg 1c: [mem 0xe0000000-0xe1ffffff 64bit pref]
[    0.649524] pci 0000:01:00.0: reg 24: [io  0xd000-0xd07f]
[    0.649533] pci 0000:01:00.0: reg 30: [mem 0xe3000000-0xe307ffff pref]
[    0.649611] pci 0000:01:00.1: [10de:0be2] type 00 class 0x040300
[    0.649625] pci 0000:01:00.1: reg 10: [mem 0xe3080000-0xe3083fff]
[    0.649749] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.649752] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    0.649755] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xe30fffff]
[    0.649833] pci 0000:02:00.0: [168c:002b] type 00 class 0x028000
[    0.649858] pci 0000:02:00.0: reg 10: [mem 0xe7a00000-0xe7a0ffff 64bit]
[    0.649973] pci 0000:02:00.0: supports D1
[    0.649975] pci 0000:02:00.0: PME# supported from D0 D1 D3hot D3cold
[    0.652183] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.652193] pci 0000:00:1c.0:   bridge window [io  0xc000-0xcfff]
[    0.652202] pci 0000:00:1c.0:   bridge window [mem 0xe7a00000-0xe8dfffff]
[    0.652332] pci 0000:03:00.0: [1180:e822] type 00 class 0x080500
[    0.652350] pci 0000:03:00.0: MMC controller base frequency changed to 50Mhz.
[    0.652373] pci 0000:03:00.0: reg 10: [mem 0xe6603000-0xe66030ff]
[    0.652541] pci 0000:03:00.0: supports D1 D2
[    0.652543] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.652601] pci 0000:03:00.1: [1180:e230] type 00 class 0x088000
[    0.652625] pci 0000:03:00.1: reg 10: [mem 0xe6602000-0xe66020ff]
[    0.652793] pci 0000:03:00.1: supports D1 D2
[    0.652795] pci 0000:03:00.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.652849] pci 0000:03:00.3: [1180:e832] type 00 class 0x0c0010
[    0.652872] pci 0000:03:00.3: reg 10: [mem 0xe6601000-0xe66017ff]
[    0.653038] pci 0000:03:00.3: supports D1 D2
[    0.653040] pci 0000:03:00.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.653093] pci 0000:03:00.4: [1180:e822] type 00 class 0x080500
[    0.653117] pci 0000:03:00.4: reg 10: [mem 0xe6600000-0xe66000ff]
[    0.653323] pci 0000:03:00.4: supports D1 D2
[    0.653326] pci 0000:03:00.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.655236] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    0.655242] pci 0000:00:1c.1:   bridge window [io  0xb000-0xbfff]
[    0.655247] pci 0000:00:1c.1:   bridge window [mem 0xe6600000-0xe79fffff]
[    0.655465] pci 0000:04:00.0: [11ab:4380] type 00 class 0x020000
[    0.655600] pci 0000:04:00.0: reg 10: [mem 0xe5220000-0xe5223fff 64bit]
[    0.655673] pci 0000:04:00.0: reg 18: [io  0xa000-0xa0ff]
[    0.655941] pci 0000:04:00.0: reg 30: [mem 0xe5200000-0xe521ffff pref]
[    0.656284] pci 0000:04:00.0: supports D1 D2
[    0.656286] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.658240] pci 0000:00:1c.2: PCI bridge to [bus 04]
[    0.658245] pci 0000:00:1c.2:   bridge window [io  0xa000-0xafff]
[    0.658250] pci 0000:00:1c.2:   bridge window [mem 0xe5200000-0xe65fffff]
[    0.658314] pci 0000:00:1c.5: PCI bridge to [bus 05-0c]
[    0.658319] pci 0000:00:1c.5:   bridge window [io  0x9000-0x9fff]
[    0.658324] pci 0000:00:1c.5:   bridge window [mem 0xe3200000-0xe51fffff]
[    0.658407] pci 0000:00:1e.0: PCI bridge to [bus 0d] (subtractive decode)
[    0.658420] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.658422] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.658424] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.658426] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
[    0.658428] pci 0000:00:1e.0:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.658430] pci 0000:00:1e.0:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.658432] pci 0000:00:1e.0:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
[    0.658434] pci 0000:00:1e.0:   bridge window [mem 0x000e0000-0x000e3fff] (subtractive decode)
[    0.658436] pci 0000:00:1e.0:   bridge window [mem 0x000e4000-0x000e7fff] (subtractive decode)
[    0.658438] pci 0000:00:1e.0:   bridge window [mem 0xd0000000-0xfeafffff] (subtractive decode)
[    0.658504] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.658563] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.658622] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.658692] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[    0.658742] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[    0.658885] \_SB_.PCI0:_OSC invalid UUID
[    0.658886] _OSC request data:1 1f 0 
[    0.658890]  pci0000:00: ACPI _OSC support notification failed, disabling PCIe ASPM
[    0.658892]  pci0000:00: Unable to request _OSC control (_OSC support mask: 0x08)
[    0.659817] ACPI: PCI Root Bridge [CPBG] (domain 0000 [bus 3f])
[    0.659874] PCI host bridge to bus 0000:3f
[    0.659878] pci_bus 0000:3f: root bus resource [bus 3f]
[    0.659884] pci 0000:3f:00.0: [8086:2c62] type 00 class 0x060000
[    0.659906] pci 0000:3f:00.1: [8086:2d01] type 00 class 0x060000
[    0.659929] pci 0000:3f:02.0: [8086:2d10] type 00 class 0x060000
[    0.659951] pci 0000:3f:02.1: [8086:2d11] type 00 class 0x060000
[    0.659971] pci 0000:3f:02.2: [8086:2d12] type 00 class 0x060000
[    0.659991] pci 0000:3f:02.3: [8086:2d13] type 00 class 0x060000
[    0.660027]  pci0000:3f: ACPI _OSC support notification failed, disabling PCIe ASPM
[    0.660029]  pci0000:3f: Unable to request _OSC control (_OSC support mask: 0x08)
[    0.660206] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.660253] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 *3 4 5 6 7 11 12 14 15)
[    0.660298] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 *4 5 6 7 10 12 14 15)
[    0.660342] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.660387] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.660431] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    0.660476] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 *5 6 7 10 12 14 15)
[    0.660520] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.660633] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.660636] vgaarb: loaded
[    0.660637] vgaarb: bridge control possible 0000:01:00.0
[    0.660821] SCSI subsystem initialized
[    0.660824] ACPI: bus type scsi registered
[    0.660886] libata version 3.00 loaded.
[    0.660905] ACPI: bus type usb registered
[    0.660922] usbcore: registered new interface driver usbfs
[    0.660929] usbcore: registered new interface driver hub
[    0.660955] usbcore: registered new device driver usb
[    0.661044] PCI: Using ACPI for IRQ routing
[    0.663295] PCI: pci_cache_line_size set to 64 bytes
[    0.663517] e820: reserve RAM buffer [mem 0x0009e800-0x0009ffff]
[    0.663519] e820: reserve RAM buffer [mem 0xcee7a000-0xcfffffff]
[    0.663612] NetLabel: Initializing
[    0.663614] NetLabel:  domain hash size = 128
[    0.663615] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.663627] NetLabel:  unlabeled traffic allowed by default
[    0.663690] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.663697] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.665720] Switching to clocksource hpet
[    0.672065] AppArmor: AppArmor Filesystem Enabled
[    0.672101] pnp: PnP ACPI init
[    0.672116] ACPI: bus type pnp registered
[    0.672162] pnp 00:00: [dma 4]
[    0.672184] pnp 00:00: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.672210] pnp 00:01: Plug and Play ACPI device, IDs INT0800 (active)
[    0.672318] pnp 00:02: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.672355] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.672413] system 00:04: [io  0x0680-0x069f] has been reserved
[    0.672416] system 00:04: [io  0xff00-0xff0f] has been reserved
[    0.672418] system 00:04: [io  0xff10-0xff13] has been reserved
[    0.672420] system 00:04: [io  0x0800-0x0803] has been reserved
[    0.672422] system 00:04: [io  0x0400-0x047f] has been reserved
[    0.672425] system 00:04: [io  0x0500-0x057f] has been reserved
[    0.672427] system 00:04: [io  0x164e-0x164f] has been reserved
[    0.672430] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.672458] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.672486] pnp 00:06: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.672511] pnp 00:07: Plug and Play ACPI device, IDs SNY9012 PNP0f13 (active)
[    0.672961] system 00:08: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.672964] system 00:08: [mem 0xfed10000-0xfed13fff] has been reserved
[    0.672966] system 00:08: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.672969] system 00:08: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.672971] system 00:08: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.672974] system 00:08: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.672976] system 00:08: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.672979] system 00:08: [mem 0xff000000-0xffffffff] could not be reserved
[    0.672981] system 00:08: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.672983] system 00:08: [mem 0xe8e0b000-0xe8e0bfff] has been reserved
[    0.672987] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.678542] pnp: PnP ACPI: found 9 devices
[    0.678545] ACPI: ACPI bus type pnp unregistered
[    0.685117] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 02] add_size 200000
[    0.685131] pci 0000:00:1c.1: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 03] add_size 200000
[    0.685142] pci 0000:00:1c.2: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 04] add_size 200000
[    0.685153] pci 0000:00:1c.5: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 05-0c] add_size 200000
[    0.685170] pci 0000:00:1c.0: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.685172] pci 0000:00:1c.1: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.685174] pci 0000:00:1c.2: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.685177] pci 0000:00:1c.5: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.685184] pci 0000:00:1c.0: BAR 15: assigned [mem 0xe8f00000-0xe90fffff 64bit pref]
[    0.685189] pci 0000:00:1c.1: BAR 15: assigned [mem 0xe9100000-0xe92fffff 64bit pref]
[    0.685193] pci 0000:00:1c.2: BAR 15: assigned [mem 0xe9300000-0xe94fffff 64bit pref]
[    0.685197] pci 0000:00:1c.5: BAR 15: assigned [mem 0xe9500000-0xe96fffff 64bit pref]
[    0.685201] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.685204] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    0.685208] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xe30fffff]
[    0.685213] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.685217] pci 0000:00:1c.0:   bridge window [io  0xc000-0xcfff]
[    0.685223] pci 0000:00:1c.0:   bridge window [mem 0xe7a00000-0xe8dfffff]
[    0.685229] pci 0000:00:1c.0:   bridge window [mem 0xe8f00000-0xe90fffff 64bit pref]
[    0.685237] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    0.685240] pci 0000:00:1c.1:   bridge window [io  0xb000-0xbfff]
[    0.685247] pci 0000:00:1c.1:   bridge window [mem 0xe6600000-0xe79fffff]
[    0.685252] pci 0000:00:1c.1:   bridge window [mem 0xe9100000-0xe92fffff 64bit pref]
[    0.685260] pci 0000:00:1c.2: PCI bridge to [bus 04]
[    0.685263] pci 0000:00:1c.2:   bridge window [io  0xa000-0xafff]
[    0.685270] pci 0000:00:1c.2:   bridge window [mem 0xe5200000-0xe65fffff]
[    0.685275] pci 0000:00:1c.2:   bridge window [mem 0xe9300000-0xe94fffff 64bit pref]
[    0.685283] pci 0000:00:1c.5: PCI bridge to [bus 05-0c]
[    0.685286] pci 0000:00:1c.5:   bridge window [io  0x9000-0x9fff]
[    0.685293] pci 0000:00:1c.5:   bridge window [mem 0xe3200000-0xe51fffff]
[    0.685298] pci 0000:00:1c.5:   bridge window [mem 0xe9500000-0xe96fffff 64bit pref]
[    0.685306] pci 0000:00:1e.0: PCI bridge to [bus 0d]
[    0.685372] pci 0000:00:1e.0: setting latency timer to 64
[    0.685377] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.685379] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.685382] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.685384] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.685386] pci_bus 0000:00: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.685388] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.685390] pci_bus 0000:00: resource 10 [mem 0x000dc000-0x000dffff]
[    0.685392] pci_bus 0000:00: resource 11 [mem 0x000e0000-0x000e3fff]
[    0.685394] pci_bus 0000:00: resource 12 [mem 0x000e4000-0x000e7fff]
[    0.685396] pci_bus 0000:00: resource 13 [mem 0xd0000000-0xfeafffff]
[    0.685398] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    0.685400] pci_bus 0000:01: resource 1 [mem 0xd0000000-0xe30fffff]
[    0.685402] pci_bus 0000:02: resource 0 [io  0xc000-0xcfff]
[    0.685404] pci_bus 0000:02: resource 1 [mem 0xe7a00000-0xe8dfffff]
[    0.685407] pci_bus 0000:02: resource 2 [mem 0xe8f00000-0xe90fffff 64bit pref]
[    0.685409] pci_bus 0000:03: resource 0 [io  0xb000-0xbfff]
[    0.685411] pci_bus 0000:03: resource 1 [mem 0xe6600000-0xe79fffff]
[    0.685413] pci_bus 0000:03: resource 2 [mem 0xe9100000-0xe92fffff 64bit pref]
[    0.685415] pci_bus 0000:04: resource 0 [io  0xa000-0xafff]
[    0.685417] pci_bus 0000:04: resource 1 [mem 0xe5200000-0xe65fffff]
[    0.685419] pci_bus 0000:04: resource 2 [mem 0xe9300000-0xe94fffff 64bit pref]
[    0.685421] pci_bus 0000:05: resource 0 [io  0x9000-0x9fff]
[    0.685423] pci_bus 0000:05: resource 1 [mem 0xe3200000-0xe51fffff]
[    0.685425] pci_bus 0000:05: resource 2 [mem 0xe9500000-0xe96fffff 64bit pref]
[    0.685428] pci_bus 0000:0d: resource 4 [io  0x0000-0x0cf7]
[    0.685430] pci_bus 0000:0d: resource 5 [io  0x0d00-0xffff]
[    0.685432] pci_bus 0000:0d: resource 6 [mem 0x000a0000-0x000bffff]
[    0.685434] pci_bus 0000:0d: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.685436] pci_bus 0000:0d: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.685438] pci_bus 0000:0d: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.685440] pci_bus 0000:0d: resource 10 [mem 0x000dc000-0x000dffff]
[    0.685442] pci_bus 0000:0d: resource 11 [mem 0x000e0000-0x000e3fff]
[    0.685444] pci_bus 0000:0d: resource 12 [mem 0x000e4000-0x000e7fff]
[    0.685446] pci_bus 0000:0d: resource 13 [mem 0xd0000000-0xfeafffff]
[    0.685483] NET: Registered protocol family 2
[    0.685652] TCP established hash table entries: 32768 (order: 7, 524288 bytes)
[    0.685884] TCP bind hash table entries: 32768 (order: 7, 524288 bytes)
[    0.686060] TCP: Hash tables configured (established 32768 bind 32768)
[    0.686093] TCP: reno registered
[    0.686101] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.686140] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.686232] NET: Registered protocol family 1
[    1.009703] pci 0000:01:00.0: Boot video device
[    1.009824] PCI: CLS 64 bytes, default 64
[    1.009871] Trying to unpack rootfs image as initramfs...
[    1.322288] Freeing initrd memory: 15880k freed
[    1.326006] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    1.326013] software IO TLB [mem 0xcae78000-0xcee78000] (64MB) mapped at [ffff8800cae78000-ffff8800cee77fff]
[    1.326515] Initialise module verification
[    1.326566] audit: initializing netlink socket (disabled)
[    1.326579] type=2000 audit(1380206898.211:1): initialized
[    1.353302] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.354817] VFS: Disk quotas dquot_6.5.2
[    1.354862] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.355356] fuse init (API version 7.20)
[    1.355437] msgmni has been set to 7738
[    1.356026] Key type asymmetric registered
[    1.356029] Asymmetric key parser 'x509' registered
[    1.356065] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    1.356094] io scheduler noop registered
[    1.356096] io scheduler deadline registered (default)
[    1.356101] io scheduler cfq registered
[    1.356232] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    1.356512] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.356534] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.356606] intel_idle: MWAIT substates: 0x1120
[    1.356609] intel_idle: v0.4 model 0x25
[    1.356610] intel_idle: lapic_timer_reliable_states 0xffffffff
[    1.358153] ACPI: AC Adapter [ADP1] (off-line)
[    1.358220] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    1.359093] ACPI: Lid Switch [LID0]
[    1.359135] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    1.359140] ACPI: Power Button [PWRB]
[    1.359210] ACPI: Requesting acpi_cpufreq
[    1.379519] thermal LNXTHERM:00: registered as thermal_zone0
[    1.379522] ACPI: Thermal Zone [TZ00] (48 C)
[    1.382553] thermal LNXTHERM:01: registered as thermal_zone1
[    1.382555] ACPI: Thermal Zone [TZ01] (48 C)
[    1.382590] GHES: HEST is not enabled!
[    1.382673] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.384190] Linux agpgart interface v0.103
[    1.385601] brd: module loaded
[    1.386305] loop: module loaded
[    1.386628] libphy: Fixed MDIO Bus: probed
[    1.386683] tun: Universal TUN/TAP device driver, 1.6
[    1.386685] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.386724] PPP generic driver version 2.4.2
[    1.386766] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.386768] ehci-pci: EHCI PCI platform driver
[    1.386809] ehci-pci 0000:00:1a.0: setting latency timer to 64
[    1.386814] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    1.386820] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.386837] ehci-pci 0000:00:1a.0: debug port 2
[    1.390757] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    1.390843] ehci-pci 0000:00:1a.0: irq 16, io mem 0xe8e08000
[    1.396509] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.396554] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.396556] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.396558] usb usb1: Product: EHCI Host Controller
[    1.396560] usb usb1: Manufacturer: Linux 3.8.0-30-lowlatency ehci_hcd
[    1.396562] usb usb1: SerialNumber: 0000:00:1a.0
[    1.396672] hub 1-0:1.0: USB hub found
[    1.396677] hub 1-0:1.0: 2 ports detected
[    1.396772] ehci-pci 0000:00:1d.0: setting latency timer to 64
[    1.396776] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    1.396781] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.396795] ehci-pci 0000:00:1d.0: debug port 2
[    1.400743] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    1.400809] ehci-pci 0000:00:1d.0: irq 23, io mem 0xe8e07000
[    1.406508] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.406547] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.406549] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.406552] usb usb2: Product: EHCI Host Controller
[    1.406554] usb usb2: Manufacturer: Linux 3.8.0-30-lowlatency ehci_hcd
[    1.406556] usb usb2: SerialNumber: 0000:00:1d.0
[    1.406655] hub 2-0:1.0: USB hub found
[    1.406658] hub 2-0:1.0: 2 ports detected
[    1.406731] ehci-platform: EHCI generic platform driver
[    1.406738] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.406752] uhci_hcd: USB Universal Host Controller Interface driver
[    1.406807] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.412156] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.412172] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.412265] mousedev: PS/2 mouse device common for all mice
[    1.412393] rtc_cmos 00:05: RTC can wake from S4
[    1.412553] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.412621] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    1.412705] device-mapper: uevent: version 1.0.3
[    1.412777] device-mapper: ioctl: 4.23.1-ioctl (2012-12-18) initialised: dm-devel@redhat.com
[    1.412846] cpuidle: using governor ladder
[    1.412923] cpuidle: using governor menu
[    1.412928] ledtrig-cpu: registered to indicate activity on CPUs
[    1.412929] EFI Variables Facility v0.08 2004-May-17
[    1.413126] ashmem: initialized
[    1.413256] TCP: cubic registered
[    1.413345] NET: Registered protocol family 10
[    1.413560] NET: Registered protocol family 17
[    1.413574] Key type dns_resolver registered
[    1.413872] Loading module verification certificates
[    1.415728] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: 45b2ef271e8c00892d79953d41c9da4447ae753d'
[    1.415754] registered taskstats version 1
[    1.421075] Key type trusted registered
[    1.425768] Key type encrypted registered
[    1.430344] rtc_cmos 00:05: setting system clock to 2013-09-26 14:48:19 UTC (1380206899)
[    1.434441] ACPI: Battery Slot [BAT0] (battery present)
[    1.435411] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.435414] EDD information not available.
[    1.437158] Freeing unused kernel memory: 940k freed
[    1.437311] Write protecting the kernel read-only data: 12288k
[    1.440439] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    1.441081] Freeing unused kernel memory: 1116k freed
[    1.444480] Freeing unused kernel memory: 1088k freed
[    1.466593] udevd[131]: starting version 175
[    1.476720] microcode: CPU0 sig=0x20652, pf=0x10, revision=0x9
[    1.477171] microcode: CPU0 updated to revision 0xe, date = 2013-06-26
[    1.477183] microcode: CPU1 sig=0x20652, pf=0x10, revision=0x9
[    1.477551] microcode: CPU1 updated to revision 0xe, date = 2013-06-26
[    1.477565] microcode: CPU2 sig=0x20652, pf=0x10, revision=0x9
[    1.477932] microcode: CPU2 updated to revision 0xe, date = 2013-06-26
[    1.477942] microcode: CPU3 sig=0x20652, pf=0x10, revision=0x9
[    1.478310] microcode: CPU3 updated to revision 0xe, date = 2013-06-26
[    1.478499] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.535786] sdhci: Secure Digital Host Controller Interface driver
[    1.535790] sdhci: Copyright(c) Pierre Ossman
[    1.537404] sky2: driver version 1.30
[    1.537644] sky2 0000:04:00.0: Yukon-2 UL 2 chip revision 0
[    1.538108] sky2 0000:04:00.0: irq 41 for MSI/MSI-X
[    1.539169] sdhci-pci 0000:03:00.0: SDHCI controller found [1180:e822] (rev 0)
[    1.539278] sdhci-pci 0000:03:00.0: Will use DMA mode even though HW doesn't fully claim to support it.
[    1.539291] mmc0: no vqmmc regulator found
[    1.539294] mmc0: no vmmc regulator found
[    1.540764] sky2 0000:04:00.0 eth0: addr 54:42:49:11:4d:06
[    1.555555] ahci 0000:00:1f.2: version 3.0
[    1.555654] ahci 0000:00:1f.2: irq 42 for MSI/MSI-X
[    1.555747] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 3 Gbps 0x3 impl SATA mode
[    1.555753] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part apst 
[    1.555761] ahci 0000:00:1f.2: setting latency timer to 64
[    1.559450] scsi0 : ahci
[    1.561446] scsi1 : ahci
[    1.561856] scsi2 : ahci
[    1.562131] scsi3 : ahci
[    1.562405] scsi4 : ahci
[    1.562443] mmc0: SDHCI controller on PCI [0000:03:00.0] using DMA
[    1.562592] sdhci-pci 0000:03:00.4: SDHCI controller found [1180:e822] (rev 0)
[    1.562652] sdhci-pci 0000:03:00.4: Will use DMA mode even though HW doesn't fully claim to support it.
[    1.562661] mmc1: no vqmmc regulator found
[    1.562663] mmc1: no vmmc regulator found
[    1.563196] scsi5 : ahci
[    1.563300] ata1: SATA max UDMA/133 abar m2048@0xe8e06000 port 0xe8e06100 irq 42
[    1.563304] ata2: SATA max UDMA/133 abar m2048@0xe8e06000 port 0xe8e06180 irq 42
[    1.563305] ata3: DUMMY
[    1.563306] ata4: DUMMY
[    1.563308] ata5: DUMMY
[    1.563309] ata6: DUMMY
[    1.586558] mmc1: SDHCI controller on PCI [0000:03:00.4] using DMA
[    1.639814] firewire_ohci 0000:03:00.3: added OHCI v1.0 device as card 0, 4 IR + 4 IT contexts, quirks 0x11
[    1.698505] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.813209] usb 1-1: New USB device found, idVendor=8087, idProduct=0020
[    1.813217] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.813598] hub 1-1:1.0: USB hub found
[    1.813792] hub 1-1:1.0: 6 ports detected
[    1.867465] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.868508] ata1.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    1.869468] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.871410] ata2.00: ATAPI: MATSHITADVD-RAM UJ890AS, 1.00, max UDMA/100
[    1.874258] ata2.00: configured for UDMA/100
[    1.914240] ata1.00: ATA-8: ST9500325AS, 0006SDM2, max UDMA/133
[    1.914246] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.916186] ata1.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    1.916380] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    1.916561] ata1.00: configured for UDMA/133
[    1.916943] scsi 0:0:0:0: Direct-Access     ATA      ST9500325AS      0006 PQ: 0 ANSI: 5
[    1.917171] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.917195] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.917243] sd 0:0:0:0: [sda] Write Protect is off
[    1.917247] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.917268] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.920336] scsi 1:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ890AS  1.00 PQ: 0 ANSI: 5
[    1.923762] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.923766] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.923943] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.924206] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.966926]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
[    1.967597] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.031197] usb 2-1: New USB device found, idVendor=8087, idProduct=0020
[    2.031206] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.031655] hub 2-1:1.0: USB hub found
[    2.031889] hub 2-1:1.0: 8 ports detected
[    2.107506] usb 1-1.2: new high-speed USB device number 3 using ehci-pci
[    2.140409] firewire_core 0000:03:00.3: created device fw0: GUID 08004603033663f0, S400
[    2.186852] usb 1-1.2: New USB device found, idVendor=05ca, idProduct=18b5
[    2.186857] usb 1-1.2: New USB device strings: Mfr=1, Product=0, SerialNumber=0
[    2.186860] usb 1-1.2: Manufacturer: Ricoh co. Ltd.
[    2.261414] usb 1-1.6: new full-speed USB device number 4 using ehci-pci
[    2.326169] tsc: Refined TSC clocksource calibration: 2128.123 MHz
[    2.326178] Switching to clocksource tsc
[    2.352742] usb 1-1.6: New USB device found, idVendor=0489, idProduct=e00f
[    2.352750] usb 1-1.6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.352752] usb 1-1.6: Product: Broadcom Bluetooth Device
[    2.352754] usb 1-1.6: Manufacturer: Broadcom Corp
[    2.352756] usb 1-1.6: SerialNumber: F07BCBBDFB8D
[    3.445884] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   27.507776] Adding 2110460k swap on /dev/sda5.  Priority:-1 extents:1 across:2110460k 
[   28.255409] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   28.358513] udevd[422]: starting version 175
[   28.794273] lp: driver loaded but no devices found
[   29.087963] snd_hda_intel 0000:00:1b.0: irq 43 for MSI/MSI-X
[   29.093281] nvidia: module license 'NVIDIA' taints kernel.
[   29.093287] Disabling lock debugging due to kernel taint
[   29.102965] [Firmware Bug]: ACPI(NGFX) defines _DOD but not _DOS
[   29.103178] ACPI: Video Device [NGFX] (multi-head: yes  rom: no  post: no)
[   29.103252] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:4b/LNXVIDEO:01/input/input3
[   29.118670] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   29.119405] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  313.30  Wed Mar 27 16:56:45 PDT 2013
[   29.132834] wmi: Mapper loaded
[   29.146412] cfg80211: Calling CRDA to update world regulatory domain
[   29.147896] hda_codec: ALC262: SKU not ready 0x411111f0
[   29.152285] input: HDA Intel MID Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input4
[   29.152413] input: HDA Intel MID Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
[   29.152714] hda_intel: Disabling MSI
[   29.152724] hda-intel 0000:01:00.1: Handle VGA-switcheroo audio client
[   29.161327] sony_laptop: Sony Notebook Control Driver v0.6
[   29.162244] input: Sony Vaio Keys as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/SNY5001:00/input/input6
[   29.162589] input: Sony Vaio Jogdial as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/SNY5001:00/input/input7
[   29.299435] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20121018/utaddress-251)
[   29.299446] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   29.299451] ACPI Warning: 0x0000000000000540-0x000000000000054f SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
[   29.299454] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   29.299456] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
[   29.299459] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   29.299460] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
[   29.299464] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   29.299465] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   29.399077] ath: phy0: ASPM enabled: 0x42
[   29.399083] ath: EEPROM regdomain: 0x65
[   29.399084] ath: EEPROM indicates we should expect a direct regpair map
[   29.399087] ath: Country alpha2 being used: 00
[   29.399088] ath: Regpair used: 0x65
[   29.404678] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   29.404986] ieee80211 phy0: Atheros AR9285 Rev:2 mem=0xffffc900047c0000, irq=16
[   29.427244] nvidiabl: loading driver version 0.81
[   29.427250] nvidiabl: Sony Corporation - VPCCW2 model detected in DMI tables
[   29.427256] nvidiabl: Supported Nvidia graphics adapter 10de:0a2b:104d:9072 detected
[   29.427306] nvidiabl: smartdimmer register at address 0xe261c084 mapped at address 0xffffc9000066e084
[   29.427308] nvidiabl: backlight type is raw
[   29.427358] nvidiabl: backup register value 0x401
[   29.427361] nvidiabl: using value 0x1ffff as maximum
[   29.427362] nvidiabl: autodetecting off
[   29.427364] nvidiabl: using value 0x0 as off
[   29.427365] nvidiabl: autodetecting minimum
[   29.427367] nvidiabl: minimum is 5% of maximum
[   29.427369] nvidiabl: using value 0x1999 as minimum
[   29.474365] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card2/input8
[   29.474494] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card2/input9
[   29.474585] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card2/input10
[   29.474673] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card2/input11
[   29.506106] type=1400 audit(1380217727.584:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=894 comm="apparmor_parser"
[   29.506137] type=1400 audit(1380217727.584:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=893 comm="apparmor_parser"
[   29.506147] type=1400 audit(1380217727.584:4): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=895 comm="apparmor_parser"
[   29.506575] type=1400 audit(1380217727.585:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=894 comm="apparmor_parser"
[   29.506702] type=1400 audit(1380217727.585:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=893 comm="apparmor_parser"
[   29.506717] type=1400 audit(1380217727.585:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=895 comm="apparmor_parser"
[   29.506828] type=1400 audit(1380217727.585:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=894 comm="apparmor_parser"
[   29.507024] type=1400 audit(1380217727.585:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=893 comm="apparmor_parser"
[   29.507042] type=1400 audit(1380217727.585:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=895 comm="apparmor_parser"
[   29.509280] kvm: VM_EXIT_LOAD_IA32_PERF_GLOBAL_CTRL does not work properly. Using workaround
[   29.610385] cfg80211: World regulatory domain updated:
[   29.610390] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   29.610392] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.610394] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   29.610396] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   29.610398] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.610399] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   30.136416] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04733/0xa40000/0xa0000, board id: 3655, fw id: 587395
[   30.187256] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input12
[   30.472094] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[   30.792744] Bluetooth: Core ver 2.16
[   30.792810] NET: Registered protocol family 31
[   30.792812] Bluetooth: HCI device and connection manager initialized
[   30.792824] Bluetooth: HCI socket layer initialized
[   30.792827] Bluetooth: L2CAP socket layer initialized
[   30.792836] Bluetooth: SCO socket layer initialized
[   30.832867] usbcore: registered new interface driver btusb
[   30.972456] Linux video capture interface: v2.00
[   31.017222] uvcvideo: Found UVC 1.00 device <unnamed> (05ca:18b5)
[   31.019350] input: UVC Camera (05ca:18b5) as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input13
[   31.019456] usbcore: registered new interface driver uvcvideo
[   31.019458] USB Video Class driver (1.1.1)
[   31.758073] init: udev-fallback-graphics main process (1057) terminated with status 1
[   32.533236] init: failsafe main process (1113) killed by TERM signal
[   32.618173] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   32.618177] Bluetooth: BNEP filters: protocol multicast
[   32.618189] Bluetooth: BNEP socket layer initialized
[   32.622487] Bluetooth: RFCOMM TTY layer initialized
[   32.622503] Bluetooth: RFCOMM socket layer initialized
[   32.622504] Bluetooth: RFCOMM ver 1.11
[   32.903307] type=1400 audit(1380217730.983:11): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1218 comm="apparmor_parser"
[   32.964494] init: avahi-cups-reload main process (1227) terminated with status 1
[   33.097990] ppdev: user-space parallel port driver
[   33.414787] init: gdm main process (1336) killed by TERM signal
[   33.530369] zram: module is from the staging directory, the quality is unknown, you have been warned.
[   33.530662] zram: Creating 4 devices ...
[   33.592670] Adding 495656k swap on /dev/zram0.  Priority:5 extents:1 across:495656k SS
[   33.597336] Adding 495656k swap on /dev/zram1.  Priority:5 extents:1 across:495656k SS
[   33.602777] Adding 495656k swap on /dev/zram2.  Priority:5 extents:1 across:495656k SS
[   33.605879] Adding 495656k swap on /dev/zram3.  Priority:5 extents:1 across:495656k SS
[   34.425486] Non-volatile memory driver v1.3
[   34.484770] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   34.490460] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   34.568216] sky2 0000:04:00.0 eth0: enabling interface
[   34.568595] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   34.570267] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   36.512310] init: smbd main process (1137) killed by HUP signal
[   36.512342] init: smbd main process ended, respawning
[   36.581958] wlan0: authenticate with 00:21:29:c2:85:2f
[   36.593993] wlan0: send auth to 00:21:29:c2:85:2f (try 1/3)
[   36.596091] wlan0: authenticated
[   36.596218] ath9k 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[   36.596222] ath9k 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   36.596224] ath9k 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   36.596770] wlan0: associate with 00:21:29:c2:85:2f (try 1/3)
[   36.599488] wlan0: RX AssocResp from 00:21:29:c2:85:2f (capab=0x411 status=0 aid=2)
[   36.599760] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   36.599835] wlan0: associated
[   37.377771] init: anacron main process (1334) killed by TERM signal
[  116.812284] ata2.00: exception Emask 0x10 SAct 0x0 SErr 0x50000 action 0xe frozen
[  116.812293] ata2.00: irq_stat 0x00400000, PHY RDY changed
[  116.812299] ata2: SError: { PHYRdyChg CommWake }
[  116.812308] sr 1:0:0:0: CDB: 
[  116.812311] Get event status notification: 4a 01 00 00 10 00 00 00 08 00
[  116.812334] ata2.00: cmd a0/00:00:00:08:00/00:00:00:00:00/a0 tag 0 pio 16392 in
[  116.812334]          res 50/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x10 (ATA bus error)
[  116.812339] ata2.00: status: { DRDY }
[  116.812349] ata2: hard resetting link
[  117.535092] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[  117.539797] ata2.00: configured for UDMA/100
[  117.552050] ata2: EH complete

```


My PC is a Sony Vaio Laptop w/ a Core i3 330M and 4gb of RAM.


PS: Sorry for my english

---

### Post by oldfred on 2013-09-27
Issue may be the frozen?
[  116.812284] ata2.00: exception Emask 0x10 SAct 0x0 SErr 0x50000 action 0xe [COLOR=#ff0000]frozen[/COLOR]

    

 Hard drive info - will show locked frozen status or not:
sudo hdparm -I /dev/sdd
sudo lshw -class disk
udisks --dump

May be BIOS setting. Do you have drive in AHCI mode?
More info:

 [https://wiki.archlinux.org/index.php/SSD_Memory_Cell_Clearing](https://wiki.archlinux.org/index.php/SSD_Memory_Cell_Clearing)

---

### Post by whitesmith on 2013-09-27
Try running the Disks utility on sda6. Click on the gear. If the drive has SMART capability, run the self-test and see what you get. You may well have a failing drive.

---

### Post by nlucool on 2013-10-03
Well it's going to be a problem if I have a failing drive :/

oldfred here are the logs you asked (?)

```
/dev/sda:

ATA device, with non-removable media
    Model Number:       ST9500325AS                             
    Serial Number:      5VEADRKA
    Firmware Revision:  0006SDM2
    Transport:          Serial
Standards:
    Used: unknown (minor revision code 0x0029) 
    Supported: 8 7 6 5 
    Likely used: 8
Configuration:
    Logical        max    current
    cylinders    16383    16383
    heads        16    16
    sectors/track    63    63
    --
    CHS current addressable sectors:   16514064
    LBA    user addressable sectors:  268435455
    LBA48  user addressable sectors:  976773168
    Logical/Physical Sector size:           512 bytes
    device size with M = 1024*1024:      476940 MBytes
    device size with M = 1000*1000:      500107 MBytes (500 GB)
    cache/buffer size  = 8192 KBytes
    Nominal Media Rotation Rate: 5400
Capabilities:
    LBA, IORDY(can be disabled)
    Queue depth: 32
    Standby timer values: spec'd by Standard, no device specific minimum
    R/W multiple sector transfer: Max = 16    Current = 16
    Advanced power management level: 254
    Recommended acoustic management value: 254, current value: 0
    DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
         Cycle time: min=120ns recommended=120ns
    PIO: pio0 pio1 pio2 pio3 pio4 
         Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
    Enabled    Supported:
       *    SMART feature set
            Security Mode feature set
       *    Power Management feature set
       *    Write cache
       *    Look-ahead
       *    Host Protected Area feature set
       *    WRITE_BUFFER command
       *    READ_BUFFER command
       *    DOWNLOAD_MICROCODE
       *    Advanced Power Management feature set
            SET_MAX security extension
       *    48-bit Address feature set
       *    Device Configuration Overlay feature set
       *    Mandatory FLUSH_CACHE
       *    FLUSH_CACHE_EXT
       *    SMART error logging
       *    SMART self-test
       *    General Purpose Logging feature set
       *    64-bit World wide name
       *    IDLE_IMMEDIATE with UNLOAD
            Write-Read-Verify feature set
       *    WRITE_UNCORRECTABLE_EXT command
       *    {READ,WRITE}_DMA_EXT_GPL commands
       *    Segmented DOWNLOAD_MICROCODE
       *    Gen1 signaling speed (1.5Gb/s)
       *    Native Command Queueing (NCQ)
       *    Phy event counters
            Device-initiated interface power management
       *    Software settings preservation
       *    SMART Command Transport (SCT) feature set
       *    SCT Read/Write Long (AC1), obsolete
       *    SCT Error Recovery Control (AC3)
       *    SCT Features Control (AC4)
       *    SCT Data Tables (AC5)
            unknown 206[12] (vendor specific)
Security: 
    Master password revision code = 65534
        supported
    not    enabled
    not    locked
        [COLOR=#ff0000]frozen[/COLOR]
    not    expired: security count
        supported: enhanced erase
    132min for SECURITY ERASE UNIT. 132min for ENHANCED SECURITY ERASE UNIT. 
Logical Unit WWN Device Identifier: 5000c50024595c82
    NAA        : 5
    IEEE OUI    : 000c50
    Unique ID    : 024595c82
Checksum: correct



```

[COLOR=#000000]sudo lshw -class disk[/COLOR]

```
gabbo@Gabbo-VAIO:~$ sudo lshw -class disk
  *-disk                  
       descripción: ATA Disk
       producto: ST9500325AS
       fabricante: Seagate
       id físico: 0.0.0
       información del bus: scsi@0:0.0.0
       nombre lógico: /dev/sda
       versión: 0006
       serie: 5VEADRKA
       tamaño: 465GiB (500GB)
       capacidades: partitioned partitioned:dos
       configuración: ansiversion=5 sectorsize=512 signature=59646d1c
  *-cdrom
       descripción: DVD-RAM writer
       producto: DVD-RAM UJ890AS
       fabricante: MATSHITA
       id físico: 0.0.0
       información del bus: scsi@1:0.0.0
       nombre lógico: /dev/cdrom
       nombre lógico: /dev/cdrw
       nombre lógico: /dev/dvd
       nombre lógico: /dev/dvdrw
       nombre lógico: /dev/sr0
       versión: 1.00
       capacidades: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuración: ansiversion=5 status=nodisc

```

[COLOR=#000000]udisks --dump

```

[/COLOR]gabbo@Gabbo-VAIO:~$ udisks --dump
========================================================================
Showing information for /org/freedesktop/UDisks/devices/sda
  native-path:                 /sys/devices/pci0000:00/0000:00:1f.2/ata1/host0/target0:0:0/0:0:0:0/block/sda
  device:                      8:0
  device-file:                 /dev/sda
    presentation:              /dev/sda
    by-id:                     /dev/disk/by-id/ata-ST9500325AS_5VEADRKA
    by-id:                     /dev/disk/by-id/scsi-SATA_ST9500325AS_5VEADRKA
    by-id:                     /dev/disk/by-id/wwn-0x5000c50024595c82
    by-path:                   /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0
  detected at:                 jue 03 oct 2013 08:53:00 ART
  system internal:             1
  removable:                   0
  has media:                   1 (detected at jue 03 oct 2013 08:53:00 ART)
    detects change:            0
    detection by polling:      0
    detection inhibitable:     0
    detection inhibited:       0
  is read only:                0
  is mounted:                  0
  mount paths:             
  mounted by uid:              0
  presentation hide:           0
  presentation nopolicy:       0
  presentation name:           
  presentation icon:           
  automount hint:              
  size:                        500107862016
  block size:                  512
  job underway:                no
  usage:                       
  type:                        
  version:                     
  uuid:                        
  label:                       
  partition table:
    scheme:                    mbr
    count:                     6
  drive:
    vendor:                    ATA
    model:                     ST9500325AS
    revision:                  0006SD2M
    serial:                    5VEADRKA
    WWN:                       5000c50024595c82
    detachable:                0
    can spindown:              1
    rotational media:          Yes, at 5400 RPM
    write-cache:               enabled
    ejectable:                 0
    adapter:                   Unknown
    ports:
    similar devices:
    media:                     
      compat:                 
    interface:                 ata
    if speed:                  (unknown)
    ATA SMART:                 Data not collected


========================================================================
Showing information for /org/freedesktop/UDisks/devices/sda1
  native-path:                 /sys/devices/pci0000:00/0000:00:1f.2/ata1/host0/target0:0:0/0:0:0:0/block/sda/sda1
  device:                      8:1
  device-file:                 /dev/sda1
    presentation:              /dev/sda1
    by-id:                     /dev/disk/by-id/ata-ST9500325AS_5VEADRKA-part1
    by-id:                     /dev/disk/by-id/scsi-SATA_ST9500325AS_5VEADRKA-part1
    by-id:                     /dev/disk/by-id/wwn-0x5000c50024595c82-part1
    by-id:                     /dev/disk/by-uuid/C0A092EBA092E6E6
    by-path:                   /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part1
  detected at:                 jue 03 oct 2013 08:53:00 ART
  system internal:             1
  removable:                   0
  has media:                   1 (detected at jue 03 oct 2013 08:53:00 ART)
    detects change:            0
    detection by polling:      0
    detection inhibitable:     0
    detection inhibited:       0
  is read only:                0
  is mounted:                  0
  mount paths:             
  mounted by uid:              0
  presentation hide:           1
  presentation nopolicy:       0
  presentation name:           
  presentation icon:           
  automount hint:              
  size:                        11607736320
  block size:                  512
  job underway:                no
  usage:                       filesystem
  type:                        ntfs
  version:                     
  uuid:                        C0A092EBA092E6E6
  label:                       Recovery
  partition:
    part of:                   /org/freedesktop/UDisks/devices/sda
    scheme:                    mbr
    number:                    1
    type:                      0x27
    flags:                    
    offset:                    1048576
    alignment offset:          0
    size:                      11607736320
    label:                     
    uuid:                      


========================================================================
Showing information for /org/freedesktop/UDisks/devices/sda2
  native-path:                 /sys/devices/pci0000:00/0000:00:1f.2/ata1/host0/target0:0:0/0:0:0:0/block/sda/sda2
  device:                      8:2
  device-file:                 /dev/sda2
    presentation:              /dev/sda2
    by-id:                     /dev/disk/by-id/ata-ST9500325AS_5VEADRKA-part2
    by-id:                     /dev/disk/by-id/scsi-SATA_ST9500325AS_5VEADRKA-part2
    by-id:                     /dev/disk/by-id/wwn-0x5000c50024595c82-part2
    by-id:                     /dev/disk/by-uuid/94A28496A2847F0C
    by-path:                   /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part2
  detected at:                 jue 03 oct 2013 08:53:00 ART
  system internal:             1
  removable:                   0
  has media:                   1 (detected at jue 03 oct 2013 08:53:00 ART)
    detects change:            0
    detection by polling:      0
    detection inhibitable:     0
    detection inhibited:       0
  is read only:                0
  is mounted:                  0
  mount paths:             
  mounted by uid:              0
  presentation hide:           0
  presentation nopolicy:       0
  presentation name:           
  presentation icon:           
  automount hint:              
  size:                        104857600
  block size:                  512
  job underway:                no
  usage:                       filesystem
  type:                        ntfs
  version:                     
  uuid:                        94A28496A2847F0C
  label:                       System Reserved
  partition:
    part of:                   /org/freedesktop/UDisks/devices/sda
    scheme:                    mbr
    number:                    2
    type:                      0x07
    flags:                    
    offset:                    11608784896
    alignment offset:          0
    size:                      104857600
    label:                     
    uuid:                      


========================================================================
Showing information for /org/freedesktop/UDisks/devices/sda3
  native-path:                 /sys/devices/pci0000:00/0000:00:1f.2/ata1/host0/target0:0:0/0:0:0:0/block/sda/sda3
  device:                      8:3
  device-file:                 /dev/sda3
    presentation:              /dev/sda3
    by-id:                     /dev/disk/by-id/ata-ST9500325AS_5VEADRKA-part3
    by-id:                     /dev/disk/by-id/scsi-SATA_ST9500325AS_5VEADRKA-part3
    by-id:                     /dev/disk/by-id/wwn-0x5000c50024595c82-part3
    by-id:                     /dev/disk/by-uuid/F4F686ECF686AE84
    by-path:                   /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part3
  detected at:                 jue 03 oct 2013 08:53:00 ART
  system internal:             1
  removable:                   0
  has media:                   1 (detected at jue 03 oct 2013 08:53:00 ART)
    detects change:            0
    detection by polling:      0
    detection inhibitable:     0
    detection inhibited:       0
  is read only:                0
  is mounted:                  1
  mount paths:             /media/windows7
  mounted by uid:              0
  presentation hide:           0
  presentation nopolicy:       0
  presentation name:           
  presentation icon:           
  automount hint:              
  size:                        381018988544
  block size:                  512
  job underway:                no
  usage:                       filesystem
  type:                        ntfs
  version:                     
  uuid:                        F4F686ECF686AE84
  label:                       
  partition:
    part of:                   /org/freedesktop/UDisks/devices/sda
    scheme:                    mbr
    number:                    3
    type:                      0x07
    flags:                    
    offset:                    11713642496
    alignment offset:          0
    size:                      381018988544
    label:                     
    uuid:                      


========================================================================
Showing information for /org/freedesktop/UDisks/devices/sda4
  native-path:                 /sys/devices/pci0000:00/0000:00:1f.2/ata1/host0/target0:0:0/0:0:0:0/block/sda/sda4
  device:                      8:4
  device-file:                 /dev/sda4
    presentation:              /dev/sda4
    by-id:                     /dev/disk/by-id/ata-ST9500325AS_5VEADRKA-part4
    by-id:                     /dev/disk/by-id/scsi-SATA_ST9500325AS_5VEADRKA-part4
    by-id:                     /dev/disk/by-id/wwn-0x5000c50024595c82-part4
    by-path:                   /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part4
  detected at:                 jue 03 oct 2013 08:53:00 ART
  system internal:             1
  removable:                   0
  has media:                   1 (detected at jue 03 oct 2013 08:53:00 ART)
    detects change:            0
    detection by polling:      0
    detection inhibitable:     0
    detection inhibited:       0
  is read only:                0
  is mounted:                  0
  mount paths:             
  mounted by uid:              0
  presentation hide:           0
  presentation nopolicy:       0
  presentation name:           
  presentation icon:           
  automount hint:              
  size:                        1024
  block size:                  512
  job underway:                no
  usage:                       
  type:                        
  version:                     
  uuid:                        
  label:                       
  partition:
    part of:                   /org/freedesktop/UDisks/devices/sda
    scheme:                    mbr
    number:                    4
    type:                      0x0f
    flags:                     boot
    offset:                    392734702592
    alignment offset:          0
    size:                      107372086272
    label:                     
    uuid:                      


========================================================================
Showing information for /org/freedesktop/UDisks/devices/sda5
  native-path:                 /sys/devices/pci0000:00/0000:00:1f.2/ata1/host0/target0:0:0/0:0:0:0/block/sda/sda5
  device:                      8:5
  device-file:                 /dev/sda5
    presentation:              /dev/sda5
    by-id:                     /dev/disk/by-id/ata-ST9500325AS_5VEADRKA-part5
    by-id:                     /dev/disk/by-id/scsi-SATA_ST9500325AS_5VEADRKA-part5
    by-id:                     /dev/disk/by-id/wwn-0x5000c50024595c82-part5
    by-id:                     /dev/disk/by-uuid/891eb122-0d25-4c3a-9550-820864adad77
    by-path:                   /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part5
  detected at:                 jue 03 oct 2013 08:53:00 ART
  system internal:             1
  removable:                   0
  has media:                   1 (detected at jue 03 oct 2013 08:53:00 ART)
    detects change:            0
    detection by polling:      0
    detection inhibitable:     0
    detection inhibited:       0
  is read only:                0
  is mounted:                  0
  mount paths:             
  mounted by uid:              0
  presentation hide:           0
  presentation nopolicy:       0
  presentation name:           
  presentation icon:           
  automount hint:              
  size:                        2161115136
  block size:                  512
  job underway:                no
  usage:                       other
  type:                        swap
  version:                     2
  uuid:                        891eb122-0d25-4c3a-9550-820864adad77
  label:                       
  partition:
    part of:                   /org/freedesktop/UDisks/devices/sda
    scheme:                    mbr
    number:                    5
    type:                      0x82
    flags:                    
    offset:                    392734703616
    alignment offset:          0
    size:                      2161115136
    label:                     
    uuid:                      


========================================================================
Showing information for /org/freedesktop/UDisks/devices/sda6
  native-path:                 /sys/devices/pci0000:00/0000:00:1f.2/ata1/host0/target0:0:0/0:0:0:0/block/sda/sda6
  device:                      8:6
  device-file:                 /dev/sda6
    presentation:              /dev/sda6
    by-id:                     /dev/disk/by-id/ata-ST9500325AS_5VEADRKA-part6
    by-id:                     /dev/disk/by-id/scsi-SATA_ST9500325AS_5VEADRKA-part6
    by-id:                     /dev/disk/by-id/wwn-0x5000c50024595c82-part6
    by-id:                     /dev/disk/by-uuid/43d608d7-f942-489b-a7c6-16e7c87b297b
    by-path:                   /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part6
  detected at:                 jue 03 oct 2013 08:53:00 ART
  system internal:             1
  removable:                   0
  has media:                   1 (detected at jue 03 oct 2013 08:53:00 ART)
    detects change:            0
    detection by polling:      0
    detection inhibitable:     0
    detection inhibited:       0
  is read only:                0
  is mounted:                  1
  mount paths:             /
  mounted by uid:              0
  presentation hide:           0
  presentation nopolicy:       0
  presentation name:           
  presentation icon:           
  automount hint:              
  size:                        105209921536
  block size:                  512
  job underway:                no
  usage:                       filesystem
  type:                        ext4
  version:                     1.0
  uuid:                        43d608d7-f942-489b-a7c6-16e7c87b297b
  label:                       
  partition:
    part of:                   /org/freedesktop/UDisks/devices/sda
    scheme:                    mbr
    number:                    6
    type:                      0x83
    flags:                    
    offset:                    394896867328
    alignment offset:          0
    size:                      105209921536
    label:                     
    uuid:                      


========================================================================
Showing information for /org/freedesktop/UDisks/devices/sr0
  native-path:                 /sys/devices/pci0000:00/0000:00:1f.2/ata2/host1/target1:0:0/1:0:0:0/block/sr0
  device:                      11:0
  device-file:                 /dev/sr0
    presentation:              /dev/sr0
    by-id:                     /dev/disk/by-id/ata-MATSHITADVD-RAM_UJ890AS_UJ15_302793
    by-path:                   /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0
  detected at:                 jue 03 oct 2013 08:53:00 ART
  system internal:             0
  removable:                   1
  has media:                   0
    detects change:            1
    detection by polling:      1
    detection inhibitable:     1
    detection inhibited:       0
  is read only:                0
  is mounted:                  0
  mount paths:             
  mounted by uid:              0
  presentation hide:           0
  presentation nopolicy:       0
  presentation name:           
  presentation icon:           
  automount hint:              
  size:                        0
  block size:                  0
  job underway:                no
  usage:                       
  type:                        
  version:                     
  uuid:                        
  label:                       
  drive:
    vendor:                    MATSHITA
    model:                     MATSHITADVD-RAM UJ890AS
    revision:                  1.00
    serial:                    UJ15_302793
    WWN:                       
    detachable:                0
    can spindown:              0
    rotational media:          Yes, unknown rate
    write-cache:               unknown
    ejectable:                 1
    adapter:                   Unknown
    ports:
    similar devices:
    media:                     
      compat:                  optical_cd optical_cd_r optical_cd_rw optical_dvd optical_dvd_plus_r optical_dvd_plus_r_dl optical_dvd_plus_rw optical_dvd_r optical_dvd_ram optical_dvd_rw optical_mrw optical_mrw_w
    interface:                 scsi
    if speed:                  (unknown)
    ATA SMART:                 not available


========================================================================
Showing information for /org/freedesktop/UDisks/devices/zram0
  native-path:                 /sys/devices/virtual/block/zram0
  device:                      251:0
  device-file:                 /dev/zram0
    presentation:              /dev/zram0
    by-id:                     /dev/disk/by-uuid/e2c5f2e4-577e-4ecb-b562-d2c2e4091e3e
  detected at:                 jue 03 oct 2013 08:53:00 ART
  system internal:             1
  removable:                   0
  has media:                   1 (detected at jue 03 oct 2013 08:53:00 ART)
    detects change:            0
    detection by polling:      0
    detection inhibitable:     0
    detection inhibited:       0
  is read only:                0
  is mounted:                  0
  mount paths:             
  mounted by uid:              0
  presentation hide:           0
  presentation nopolicy:       1
  presentation name:           
  presentation icon:           
  automount hint:              
  size:                        507555840
  block size:                  4096
  job underway:                no
  usage:                       other
  type:                        swap
  version:                     2
  uuid:                        e2c5f2e4-577e-4ecb-b562-d2c2e4091e3e
  label:                       
  drive:
    vendor:                    
    model:                     
    revision:                  
    serial:                    
    WWN:                       
    detachable:                0
    can spindown:              0
    rotational media:          No
    write-cache:               unknown
    ejectable:                 0
    adapter:                   Unknown
    ports:
    similar devices:
    media:                     
      compat:                 
    interface:                 (unknown)
    if speed:                  (unknown)
    ATA SMART:                 not available


========================================================================
Showing information for /org/freedesktop/UDisks/devices/zram1
  native-path:                 /sys/devices/virtual/block/zram1
  device:                      251:1
  device-file:                 /dev/zram1
    presentation:              /dev/zram1
    by-id:                     /dev/disk/by-uuid/72ed1737-a84b-4d7a-9cb8-547bc7fe0d7b
  detected at:                 jue 03 oct 2013 08:53:00 ART
  system internal:             1
  removable:                   0
  has media:                   1 (detected at jue 03 oct 2013 08:53:00 ART)
    detects change:            0
    detection by polling:      0
    detection inhibitable:     0
    detection inhibited:       0
  is read only:                0
  is mounted:                  0
  mount paths:             
  mounted by uid:              0
  presentation hide:           0
  presentation nopolicy:       1
  presentation name:           
  presentation icon:           
  automount hint:              
  size:                        507555840
  block size:                  4096
  job underway:                no
  usage:                       other
  type:                        swap
  version:                     2
  uuid:                        72ed1737-a84b-4d7a-9cb8-547bc7fe0d7b
  label:                       
  drive:
    vendor:                    
    model:                     
    revision:                  
    serial:                    
    WWN:                       
    detachable:                0
    can spindown:              0
    rotational media:          No
    write-cache:               unknown
    ejectable:                 0
    adapter:                   Unknown
    ports:
    similar devices:
    media:                     
      compat:                 
    interface:                 (unknown)
    if speed:                  (unknown)
    ATA SMART:                 not available


========================================================================
Showing information for /org/freedesktop/UDisks/devices/zram2
  native-path:                 /sys/devices/virtual/block/zram2
  device:                      251:2
  device-file:                 /dev/zram2
    presentation:              /dev/zram2
    by-id:                     /dev/disk/by-uuid/b4833da5-8255-4fba-8f96-f190186ed237
  detected at:                 jue 03 oct 2013 08:53:00 ART
  system internal:             1
  removable:                   0
  has media:                   1 (detected at jue 03 oct 2013 08:53:00 ART)
    detects change:            0
    detection by polling:      0
    detection inhibitable:     0
    detection inhibited:       0
  is read only:                0
  is mounted:                  0
  mount paths:             
  mounted by uid:              0
  presentation hide:           0
  presentation nopolicy:       1
  presentation name:           
  presentation icon:           
  automount hint:              
  size:                        507555840
  block size:                  4096
  job underway:                no
  usage:                       other
  type:                        swap
  version:                     2
  uuid:                        b4833da5-8255-4fba-8f96-f190186ed237
  label:                       
  drive:
    vendor:                    
    model:                     
    revision:                  
    serial:                    
    WWN:                       
    detachable:                0
    can spindown:              0
    rotational media:          No
    write-cache:               unknown
    ejectable:                 0
    adapter:                   Unknown
    ports:
    similar devices:
    media:                     
      compat:                 
    interface:                 (unknown)
    if speed:                  (unknown)
    ATA SMART:                 not available


========================================================================
Showing information for /org/freedesktop/UDisks/devices/zram3
  native-path:                 /sys/devices/virtual/block/zram3
  device:                      251:3
  device-file:                 /dev/zram3
    presentation:              /dev/zram3
    by-id:                     /dev/disk/by-uuid/27c27426-cb06-4a4d-95f6-0d7a15b2d16b
  detected at:                 jue 03 oct 2013 08:53:00 ART
  system internal:             1
  removable:                   0
  has media:                   1 (detected at jue 03 oct 2013 08:53:00 ART)
    detects change:            0
    detection by polling:      0
    detection inhibitable:     0
    detection inhibited:       0
  is read only:                0
  is mounted:                  0
  mount paths:             
  mounted by uid:              0
  presentation hide:           0
  presentation nopolicy:       1
  presentation name:           
  presentation icon:           
  automount hint:              
  size:                        507555840
  block size:                  4096
  job underway:                no
  usage:                       other
  type:                        swap
  version:                     2
  uuid:                        27c27426-cb06-4a4d-95f6-0d7a15b2d16b
  label:                       
  drive:
    vendor:                    
    model:                     
    revision:                  
    serial:                    
    WWN:                       
    detachable:                0
    can spindown:              0
    rotational media:          No
    write-cache:               unknown
    ejectable:                 0
    adapter:                   Unknown
    ports:
    similar devices:
    media:                     
      compat:                 
    interface:                 (unknown)
    if speed:                  (unknown)
    ATA SMART:                 not available


========================================================================



```[COLOR=#000000]
[/COLOR]

---

### Post by oldfred on 2013-10-03
Please use code tags # in Advanced editor makes it easy to add.

First set shows frozen still. I changed it to [COLOR=#ff0000]red[/COLOR], if you scroll down.

---

