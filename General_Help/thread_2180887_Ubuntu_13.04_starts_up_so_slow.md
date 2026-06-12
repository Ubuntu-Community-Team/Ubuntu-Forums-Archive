---
title: "Ubuntu 13.04 starts up so slow"
date: 2013-10-15
forum: General Help
---

### Post by tqjustc on 2013-10-15
My PC is THINKPAD T410. The output of ```
dmesg
``` is as follows. Anyone can help ? Thanks !

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.8.0-31-generic (buildd@panlong) (gcc version 4.7.3 (Ubuntu/Linaro 4.7.3-1ubuntu1) ) #46-Ubuntu SMP Tue Sep 10 20:03:44 UTC 2013 (Ubuntu 3.8.0-31.46-generic 3.8.13.8)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-31-generic root=UUID=8606e121-f863-4aa7-858c-502142cecc1b ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009e7ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009e800-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000d2000-0x00000000000d3fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000dc000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000bb27bfff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bb27c000-0x00000000bb281fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000bb282000-0x00000000bb35efff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bb35f000-0x00000000bb370fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000bb371000-0x00000000bb3f1fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bb3f2000-0x00000000bb40efff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000bb40f000-0x00000000bb46efff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bb46f000-0x00000000bb667fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000bb668000-0x00000000bb6e7fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bb6e8000-0x00000000bb70efff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000bb70f000-0x00000000bb716fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bb717000-0x00000000bb71efff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000bb71f000-0x00000000bb76bfff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bb76c000-0x00000000bb777fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bb778000-0x00000000bb77afff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000bb77b000-0x00000000bb78afff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bb78b000-0x00000000bb78bfff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000bb78c000-0x00000000bb79efff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bb79f000-0x00000000bb7fefff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000bb7ff000-0x00000000bb7fffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bb800000-0x00000000bfffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000feaff000-0x00000000feafffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec0ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed003ff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed8ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x00000001fbffffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000200000000-0x000000023bffffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.6 present.
[    0.000000] DMI: LENOVO 2516ADU/2516ADU, BIOS 6IET68WW (1.28 ) 07/12/2010
[    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x23c000 max_arch_pfn = 0x400000000
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
[    0.000000]   3 base 100000000 mask F00000000 write-back
[    0.000000]   4 base 200000000 mask FC0000000 write-back
[    0.000000]   5 base 23C000000 mask FFC000000 uncachable
[    0.000000]   6 base 0BC000000 mask FFC000000 uncachable
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 1, base: 0GB, range: 2GB, type WB
[    0.000000] reg 2, base: 2GB, range: 1GB, type WB
[    0.000000] reg 3, base: 4GB, range: 4GB, type WB
[    0.000000] reg 4, base: 8GB, range: 1GB, type WB
[    0.000000] reg 5, base: 9152MB, range: 64MB, type UC
[    0.000000] reg 6, base: 3008MB, range: 64MB, type UC
[    0.000000] total RAM covered: 8064M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 128M     num_reg: 6      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3008MB, range: 64MB, type UC
[    0.000000] reg 3, base: 4GB, range: 4GB, type WB
[    0.000000] reg 4, base: 8GB, range: 1GB, type WB
[    0.000000] reg 5, base: 9152MB, range: 64MB, type UC
[    0.000000] e820: update [mem 0xbc000000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xbb800 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000f68b0-0x000f68bf] mapped at [ffff8800000f68b0]
[    0.000000] initial memory mapped: [mem 0x00000000-0x1fffffff]
[    0.000000] Base memory trampoline at [ffff880000098000] 98000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0xbb7fffff]
[    0.000000]  [mem 0x00000000-0xbb7fffff] page 2M
[    0.000000] kernel direct mapping tables up to 0xbb7fffff @ [mem 0x1fffc000-0x1fffffff]
[    0.000000] init_memory_mapping: [mem 0x100000000-0x1fbffffff]
[    0.000000]  [mem 0x100000000-0x1fbffffff] page 2M
[    0.000000] kernel direct mapping tables up to 0x1fbffffff @ [mem 0xbb767000-0xbb76bfff]
[    0.000000] init_memory_mapping: [mem 0x200000000-0x23bffffff]
[    0.000000]  [mem 0x200000000-0x23bffffff] page 2M
[    0.000000] kernel direct mapping tables up to 0x23bffffff @ [mem 0x1fbffe000-0x1fbffffff]
[    0.000000] RAMDISK: [mem 0x360fc000-0x37075fff]
[    0.000000] ACPI: RSDP 00000000000f6870 00024 (v02 LENOVO)
[    0.000000] ACPI: XSDT 00000000bb7ef338 00094 (v01 LENOVO TP-6I    00001280  LTP 00000000)
[    0.000000] ACPI: FACP 00000000bb7ef400 000F4 (v04 LENOVO TP-6I    00001280 LNVO 00000001)
[    0.000000] ACPI: DSDT 00000000bb7ef7d1 0F2F8 (v01 LENOVO TP-6I    00001280 MSFT 03000001)
[    0.000000] ACPI: FACS 00000000bb6e7000 00040
[    0.000000] ACPI: SSDT 00000000bb7ef5b4 0021D (v01 LENOVO TP-6I    00001280 MSFT 03000001)
[    0.000000] ACPI: ECDT 00000000bb7feac9 00052 (v01 LENOVO TP-6I    00001280 LNVO 00000001)
[    0.000000] ACPI: APIC 00000000bb7feb1b 00084 (v01 LENOVO TP-6I    00001280 LNVO 00000001)
[    0.000000] ACPI: MCFG 00000000bb7febd7 0003C (v01 LENOVO TP-6I    00001280 LNVO 00000001)
[    0.000000] ACPI: HPET 00000000bb7fec13 00038 (v01 LENOVO TP-6I    00001280 LNVO 00000001)
[    0.000000] ACPI: ASF! 00000000bb7fedbe 000A4 (v16 LENOVO TP-6I    00001280 PTL  00000001)
[    0.000000] ACPI: SLIC 00000000bb7fee62 00176 (v01 LENOVO TP-6I    00001280  LTP 00000000)
[    0.000000] ACPI: BOOT 00000000bb7fefd8 00028 (v01 LENOVO TP-6I    00001280  LTP 00000001)
[    0.000000] ACPI: SSDT 00000000bb6e591a 0084B (v01 LENOVO TP-6I    00001280 INTL 20050513)
[    0.000000] ACPI: TCPA 00000000bb78b000 00032 (v02    PTL  CRESTLN 06040000      00005A52)
[    0.000000] ACPI: SSDT 00000000bb77a000 009F1 (v01  PmRef    CpuPm 00003000 INTL 20061109)
[    0.000000] ACPI: SSDT 00000000bb779000 00259 (v01  PmRef  Cpu0Tst 00003000 INTL 20061109)
[    0.000000] ACPI: SSDT 00000000bb778000 0049F (v01  PmRef    ApTst 00003000 INTL 20061109)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000023bffffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x23bffffff]
[    0.000000]   NODE_DATA [mem 0x23bffb000-0x23bffffff]
[    0.000000]  [ffffea0000000000-ffffea0008ffffff] PMD -> [ffff880233600000-ffff88023b5fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00010000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x23bffffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00010000-0x0009dfff]
[    0.000000]   node   0: [mem 0x00100000-0xbb27bfff]
[    0.000000]   node   0: [mem 0xbb282000-0xbb35efff]
[    0.000000]   node   0: [mem 0xbb40f000-0xbb46efff]
[    0.000000]   node   0: [mem 0xbb70f000-0xbb716fff]
[    0.000000]   node   0: [mem 0xbb71f000-0xbb76bfff]
[    0.000000]   node   0: [mem 0xbb7ff000-0xbb7fffff]
[    0.000000]   node   0: [mem 0x100000000-0x1fbffffff]
[    0.000000]   node   0: [mem 0x200000000-0x23bffffff]
[    0.000000] On node 0 totalpages: 2044829
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 6 pages reserved
[    0.000000]   DMA zone: 3912 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 11921 pages used for memmap
[    0.000000]   DMA32 zone: 750974 pages, LIFO batch:31
[    0.000000]   Normal zone: 20224 pages used for memmap
[    0.000000]   Normal zone: 1257728 pages, LIFO batch:31
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
[    0.000000] smpboot: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
[    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
[    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000dc000
[    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000bb27c000 - 00000000bb282000
[    0.000000] PM: Registered nosave memory: 00000000bb35f000 - 00000000bb371000
[    0.000000] PM: Registered nosave memory: 00000000bb371000 - 00000000bb3f2000
[    0.000000] PM: Registered nosave memory: 00000000bb3f2000 - 00000000bb40f000
[    0.000000] PM: Registered nosave memory: 00000000bb46f000 - 00000000bb668000
[    0.000000] PM: Registered nosave memory: 00000000bb668000 - 00000000bb6e8000
[    0.000000] PM: Registered nosave memory: 00000000bb6e8000 - 00000000bb70f000
[    0.000000] PM: Registered nosave memory: 00000000bb717000 - 00000000bb71f000
[    0.000000] PM: Registered nosave memory: 00000000bb76c000 - 00000000bb778000
[    0.000000] PM: Registered nosave memory: 00000000bb778000 - 00000000bb77b000
[    0.000000] PM: Registered nosave memory: 00000000bb77b000 - 00000000bb78b000
[    0.000000] PM: Registered nosave memory: 00000000bb78b000 - 00000000bb78c000
[    0.000000] PM: Registered nosave memory: 00000000bb78c000 - 00000000bb79f000
[    0.000000] PM: Registered nosave memory: 00000000bb79f000 - 00000000bb7ff000
[    0.000000] PM: Registered nosave memory: 00000000bb800000 - 00000000c0000000
[    0.000000] PM: Registered nosave memory: 00000000c0000000 - 00000000e0000000
[    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
[    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000feaff000
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
[    0.000000] PM: Registered nosave memory: 00000001fc000000 - 0000000200000000
[    0.000000] e820: [mem 0xc0000000-0xdfffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88023bc00000 s84928 r8192 d21568 u524288
[    0.000000] pcpu-alloc: s84928 r8192 d21568 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2012614
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-31-generic root=UUID=8606e121-f863-4aa7-858c-502142cecc1b ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] __ex_table already sorted, skipping sort
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 7950052k/9371648k available (7014k kernel code, 1192332k absent, 229264k reserved, 6228k data, 996k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
[    0.000000] NR_IRQS:16640 nr_irqs:712 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 33554432 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.004000] tsc: Detected 2393.921 MHz processor
[    0.000004] Calibrating delay loop (skipped), value calculated using timer frequency.. 4787.84 BogoMIPS (lpj=9575684)
[    0.000009] pid_max: default: 32768 minimum: 301
[    0.000053] Security Framework initialized
[    0.000074] AppArmor: AppArmor initialized
[    0.000076] Yama: becoming mindful.
[    0.001177] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.004402] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.005761] Mount-cache hash table entries: 256
[    0.006077] Initializing cgroup subsys cpuacct
[    0.006082] Initializing cgroup subsys memory
[    0.006093] Initializing cgroup subsys devices
[    0.006096] Initializing cgroup subsys freezer
[    0.006098] Initializing cgroup subsys blkio
[    0.006101] Initializing cgroup subsys perf_event
[    0.006106] Initializing cgroup subsys hugetlb
[    0.006144] CPU: Physical Processor ID: 0
[    0.006146] CPU: Processor Core ID: 0
[    0.006155] mce: CPU supports 9 MCE banks
[    0.006172] CPU0: Thermal monitoring enabled (TM1)
[    0.006183] process: using mwait in idle threads
[    0.006190] Last level iTLB entries: 4KB 512, 2MB 7, 4MB 7
[    0.006190] Last level dTLB entries: 4KB 512, 2MB 32, 4MB 32
[    0.006190] tlb_flushall_shift: 6
[    0.006444] Freeing SMP alternatives: 24k freed
[    0.010498] ACPI: Core revision 20121018
[    2.281411] ftrace: allocating 26713 entries in 105 pages
[    2.307938] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    2.347558] smpboot: CPU0: Intel(R) Core(TM) i5 CPU       M 520  @ 2.40GHz (fam: 06, model: 25, stepping: 02)
[    2.454864] Performance Events: PEBS fmt1+, 16-deep LBR, Westmere events, Intel PMU driver.
[    2.454875] perf_event_intel: CPUID marked event: 'bus cycles' unavailable
[    2.454879] ... version:                3
[    2.454881] ... bit width:              48
[    2.454883] ... generic registers:      4
[    2.454885] ... value mask:             0000ffffffffffff
[    2.454887] ... max period:             000000007fffffff
[    2.454889] ... fixed-purpose events:   3
[    2.454891] ... event mask:             000000070000000f
[    2.469987] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    2.456757] smpboot: Booting Node   0, Processors  #1 #2 #3 OK
[    2.496579] Brought up 4 CPUs
[    2.496586] smpboot: Total of 4 processors activated (19151.36 BogoMIPS)
[    2.500163] devtmpfs: initialized
[    2.502618] EVM: security.selinux
[    2.502621] EVM: security.SMACK64
[    2.502623] EVM: security.capability
[    2.502708] PM: Registering ACPI NVS region [mem 0xbb371000-0xbb3f1fff] (528384 bytes)
[    2.502727] PM: Registering ACPI NVS region [mem 0xbb668000-0xbb6e7fff] (524288 bytes)
[    2.502747] PM: Registering ACPI NVS region [mem 0xbb76c000-0xbb777fff] (49152 bytes)
[    2.502750] PM: Registering ACPI NVS region [mem 0xbb77b000-0xbb78afff] (65536 bytes)
[    2.502754] PM: Registering ACPI NVS region [mem 0xbb78c000-0xbb79efff] (77824 bytes)
[    2.504407] regulator-dummy: no parameters
[    2.504493] NET: Registered protocol family 16
[    2.504759] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    2.504763] ACPI: bus type pci registered
[    2.504858] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    2.504863] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    2.578226] PCI: Using configuration type 1 for base access
[    2.579935] bio: create slab <bio-0> at 0
[    2.580088] ACPI: Added _OSI(Module Device)
[    2.580092] ACPI: Added _OSI(Processor Device)
[    2.580097] ACPI: Added _OSI(3.0 _SCP Extensions)
[    2.580101] ACPI: Added _OSI(Processor Aggregator Device)
[    2.583397] ACPI: EC: EC description table is found, configuring boot EC
[    2.592711] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    2.671077] ACPI: SSDT 00000000bb71aa18 0046F (v01  PmRef  Cpu0Ist 00003000 INTL 20061109)
[    2.671897] ACPI: Dynamic OEM Table Load:
[    2.671902] ACPI: SSDT           (null) 0046F (v01  PmRef  Cpu0Ist 00003000 INTL 20061109)
[    2.672145] ACPI: SSDT 00000000bb718718 006B2 (v01  PmRef  Cpu0Cst 00003001 INTL 20061109)
[    2.672987] ACPI: Dynamic OEM Table Load:
[    2.672991] ACPI: SSDT           (null) 006B2 (v01  PmRef  Cpu0Cst 00003001 INTL 20061109)
[    2.673544] ACPI: SSDT 00000000bb719a98 00303 (v01  PmRef    ApIst 00003000 INTL 20061109)
[    2.674451] ACPI: Dynamic OEM Table Load:
[    2.674455] ACPI: SSDT           (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20061109)
[    2.674704] ACPI: SSDT 00000000bb717d98 00119 (v01  PmRef    ApCst 00003000 INTL 20061109)
[    2.675559] ACPI: Dynamic OEM Table Load:
[    2.675564] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20061109)
[    2.685072] ACPI: Interpreter enabled
[    2.685079] ACPI: (supports S0 S3 S4 S5)
[    2.685110] ACPI: Using IOAPIC for interrupt routing
[    2.692993] ACPI: Power Resource [PUBS] (on)
[    2.699163] ACPI: EC: GPE = 0x11, I/O: command/status = 0x66, data = 0x62
[    2.700484] ACPI: ACPI Dock Station Driver: 2 docks/bays found
[    2.700491] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    2.700512] ACPI: PCI Root Bridge [UNCR] (domain 0000 [bus ff])
[    2.700564] PCI host bridge to bus 0000:ff
[    2.700570] pci_bus 0000:ff: root bus resource [bus ff]
[    2.700583] pci 0000:ff:00.0: [8086:2c62] type 00 class 0x060000
[    2.700624] pci 0000:ff:00.1: [8086:2d01] type 00 class 0x060000
[    2.700663] pci 0000:ff:02.0: [8086:2d10] type 00 class 0x060000
[    2.700696] pci 0000:ff:02.1: [8086:2d11] type 00 class 0x060000
[    2.700730] pci 0000:ff:02.2: [8086:2d12] type 00 class 0x060000
[    2.700766] pci 0000:ff:02.3: [8086:2d13] type 00 class 0x060000
[    2.700828]  pci0000:ff: ACPI _OSC support notification failed, disabling PCIe ASPM
[    2.700832]  pci0000:ff: Unable to request _OSC control (_OSC support mask: 0x08)
[    2.701059] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[    2.701063] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    2.701440] PCI host bridge to bus 0000:00
[    2.701446] pci_bus 0000:00: root bus resource [bus 00-fe]
[    2.701450] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    2.701453] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    2.701457] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    2.701461] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
[    2.701464] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
[    2.701468] pci_bus 0000:00: root bus resource [mem 0xc0000000-0xfebfffff]
[    2.701481] pci 0000:00:00.0: [8086:0044] type 00 class 0x060000
[    2.701511] DMAR: BIOS has allocated no shadow GTT; disabling IOMMU for graphics
[    2.701545] pci 0000:00:02.0: [8086:0046] type 00 class 0x030000
[    2.701565] pci 0000:00:02.0: reg 10: [mem 0xf2000000-0xf23fffff 64bit]
[    2.701576] pci 0000:00:02.0: reg 18: [mem 0xd0000000-0xdfffffff 64bit pref]
[    2.701585] pci 0000:00:02.0: reg 20: [io  0x1800-0x1807]
[    2.701688] pci 0000:00:16.0: [8086:3b64] type 00 class 0x078000
[    2.701729] pci 0000:00:16.0: reg 10: [mem 0xf2827800-0xf282780f 64bit]
[    2.701857] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    2.701898] pci 0000:00:16.3: [8086:3b67] type 00 class 0x070002
[    2.701930] pci 0000:00:16.3: reg 10: [io  0x1808-0x180f]
[    2.701947] pci 0000:00:16.3: reg 14: [mem 0xf2624000-0xf2624fff]
[    2.702107] pci 0000:00:19.0: [8086:10ea] type 00 class 0x020000
[    2.702140] pci 0000:00:19.0: reg 10: [mem 0xf2600000-0xf261ffff]
[    2.702156] pci 0000:00:19.0: reg 14: [mem 0xf2625000-0xf2625fff]
[    2.702172] pci 0000:00:19.0: reg 18: [io  0x1820-0x183f]
[    2.702284] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    2.702327] pci 0000:00:1a.0: [8086:3b3c] type 00 class 0x0c0320
[    2.702360] pci 0000:00:1a.0: reg 10: [mem 0xf2828000-0xf28283ff]
[    2.702509] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    2.702555] pci 0000:00:1b.0: [8086:3b56] type 00 class 0x040300
[    2.702583] pci 0000:00:1b.0: reg 10: [mem 0xf2620000-0xf2623fff 64bit]
[    2.702708] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    2.702752] pci 0000:00:1c.0: [8086:3b42] type 01 class 0x060400
[    2.702881] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    2.702923] pci 0000:00:1c.1: [8086:3b44] type 01 class 0x060400
[    2.703050] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    2.703094] pci 0000:00:1c.3: [8086:3b48] type 01 class 0x060400
[    2.703220] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    2.703262] pci 0000:00:1c.4: [8086:3b4a] type 01 class 0x060400
[    2.703387] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    2.703441] pci 0000:00:1d.0: [8086:3b34] type 00 class 0x0c0320
[    2.703474] pci 0000:00:1d.0: reg 10: [mem 0xf2828400-0xf28287ff]
[    2.703613] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    2.703650] pci 0000:00:1e.0: [8086:2448] type 01 class 0x060401
[    2.703762] pci 0000:00:1f.0: [8086:3b07] type 00 class 0x060100
[    2.703927] pci 0000:00:1f.2: [8086:3b2f] type 00 class 0x010601
[    2.703962] pci 0000:00:1f.2: reg 10: [io  0x1860-0x1867]
[    2.703978] pci 0000:00:1f.2: reg 14: [io  0x1814-0x1817]
[    2.703993] pci 0000:00:1f.2: reg 18: [io  0x1818-0x181f]
[    2.704009] pci 0000:00:1f.2: reg 1c: [io  0x1810-0x1813]
[    2.704024] pci 0000:00:1f.2: reg 20: [io  0x1840-0x185f]
[    2.704039] pci 0000:00:1f.2: reg 24: [mem 0xf2827000-0xf28277ff]
[    2.704125] pci 0000:00:1f.2: PME# supported from D3hot
[    2.704162] pci 0000:00:1f.3: [8086:3b30] type 00 class 0x0c0500
[    2.704191] pci 0000:00:1f.3: reg 10: [mem 0xf2828800-0xf28288ff 64bit]
[    2.704230] pci 0000:00:1f.3: reg 20: [io  0x1880-0x189f]
[    2.704296] pci 0000:00:1f.6: [8086:3b32] type 00 class 0x118000
[    2.704333] pci 0000:00:1f.6: reg 10: [mem 0xf2626000-0xf2626fff 64bit]
[    2.704531] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    2.704640] pci 0000:03:00.0: [10ec:8172] type 00 class 0x028000
[    2.704664] pci 0000:03:00.0: reg 10: [io  0x2000-0x20ff]
[    2.704680] pci 0000:03:00.0: reg 14: [mem 0xf2400000-0xf2403fff]
[    2.704809] pci 0000:03:00.0: supports D1 D2
[    2.704813] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot
[    2.710438] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    2.710446] pci 0000:00:1c.1:   bridge window [io  0x2000-0x2fff]
[    2.710453] pci 0000:00:1c.1:   bridge window [mem 0xf2400000-0xf24fffff]
[    2.710534] pci 0000:00:1c.3: PCI bridge to [bus 05-0c]
[    2.710541] pci 0000:00:1c.3:   bridge window [io  0x3000-0x3fff]
[    2.710548] pci 0000:00:1c.3:   bridge window [mem 0xf0000000-0xf1ffffff]
[    2.710559] pci 0000:00:1c.3:   bridge window [mem 0xf2900000-0xf29fffff 64bit pref]
[    2.710707] pci 0000:0d:00.0: [1180:e822] type 00 class 0x080500
[    2.710728] pci 0000:0d:00.0: MMC controller base frequency changed to 50Mhz.
[    2.710758] pci 0000:0d:00.0: reg 10: [mem 0xf2500000-0xf25000ff]
[    2.710948] pci 0000:0d:00.0: supports D1 D2
[    2.710951] pci 0000:0d:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    2.711051] pci 0000:0d:00.1: [1180:e230] type 00 class 0x088000
[    2.711080] pci 0000:0d:00.1: reg 10: [mem 0xf2500400-0xf25004ff]
[    2.711268] pci 0000:0d:00.1: supports D1 D2
[    2.711272] pci 0000:0d:00.1: PME# supported from D0 D1 D2 D3hot D3cold
[    2.711336] pci 0000:0d:00.3: [1180:e832] type 00 class 0x0c0010
[    2.711365] pci 0000:0d:00.3: reg 10: [mem 0xf2500800-0xf2500fff]
[    2.711551] pci 0000:0d:00.3: supports D1 D2
[    2.711555] pci 0000:0d:00.3: PME# supported from D0 D1 D2 D3hot D3cold
[    2.718487] pci 0000:00:1c.4: PCI bridge to [bus 0d]
[    2.718498] pci 0000:00:1c.4:   bridge window [mem 0xf2500000-0xf25fffff]
[    2.718611] pci 0000:00:1e.0: PCI bridge to [bus 0e] (subtractive decode)
[    2.718628] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    2.718632] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    2.718636] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    2.718639] pci 0000:00:1e.0:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    2.718643] pci 0000:00:1e.0:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    2.718647] pci 0000:00:1e.0:   bridge window [mem 0xc0000000-0xfebfffff] (subtractive decode)
[    2.718722] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[    2.718774] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[    2.718821] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP4._PRT]
[    2.718869] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP5._PRT]
[    2.719095]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    2.719393]  pci0000:00: ACPI _OSC request failed (AE_SUPPORT), returned control mask: 0x0d
[    2.719395] ACPI _OSC control for PCIe not granted, disabling ASPM
[    2.720781] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11)
[    2.720889] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)
[    2.720978] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[    2.721083] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
[    2.721185] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11)
[    2.721287] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11)
[    2.721372] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[    2.721481] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11)
[    2.721665] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    2.721673] vgaarb: loaded
[    2.721675] vgaarb: bridge control possible 0000:00:02.0
[    2.721972] SCSI subsystem initialized
[    2.721976] ACPI: bus type scsi registered
[    2.722049] libata version 3.00 loaded.
[    2.722083] ACPI: bus type usb registered
[    2.722109] usbcore: registered new interface driver usbfs
[    2.722122] usbcore: registered new interface driver hub
[    2.722162] usbcore: registered new device driver usb
[    2.722306] PCI: Using ACPI for IRQ routing
[    2.734134] PCI: pci_cache_line_size set to 64 bytes
[    2.734353] e820: reserve RAM buffer [mem 0x0009e800-0x0009ffff]
[    2.734357] e820: reserve RAM buffer [mem 0xbb27c000-0xbbffffff]
[    2.734362] e820: reserve RAM buffer [mem 0xbb35f000-0xbbffffff]
[    2.734367] e820: reserve RAM buffer [mem 0xbb46f000-0xbbffffff]
[    2.734376] e820: reserve RAM buffer [mem 0xbb717000-0xbbffffff]
[    2.734380] e820: reserve RAM buffer [mem 0xbb76c000-0xbbffffff]
[    2.734384] e820: reserve RAM buffer [mem 0xbb800000-0xbbffffff]
[    2.734520] NetLabel: Initializing
[    2.734523] NetLabel:  domain hash size = 128
[    2.734525] NetLabel:  protocols = UNLABELED CIPSOv4
[    2.734542] NetLabel:  unlabeled traffic allowed by default
[    2.734650] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    2.734661] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    2.736677] Switching to clocksource hpet
[    2.745841] AppArmor: AppArmor Filesystem Enabled
[    2.745882] pnp: PnP ACPI init
[    2.745906] ACPI: bus type pnp registered
[    2.747773] system 00:00: [mem 0x00000000-0x0009ffff] could not be reserved
[    2.747780] system 00:00: [mem 0x000c0000-0x000c3fff] could not be reserved
[    2.747784] system 00:00: [mem 0x000c4000-0x000c7fff] could not be reserved
[    2.747788] system 00:00: [mem 0x000c8000-0x000cbfff] has been reserved
[    2.747792] system 00:00: [mem 0x000cc000-0x000cffff] has been reserved
[    2.747796] system 00:00: [mem 0x000d0000-0x000d3fff] could not be reserved
[    2.747801] system 00:00: [mem 0x000dc000-0x000dffff] could not be reserved
[    2.747805] system 00:00: [mem 0x000e0000-0x000e3fff] could not be reserved
[    2.747809] system 00:00: [mem 0x000e4000-0x000e7fff] could not be reserved
[    2.747813] system 00:00: [mem 0x000e8000-0x000ebfff] could not be reserved
[    2.747817] system 00:00: [mem 0x000ec000-0x000effff] could not be reserved
[    2.747821] system 00:00: [mem 0x000f0000-0x000fffff] could not be reserved
[    2.747825] system 00:00: [mem 0x00100000-0xbfffffff] could not be reserved
[    2.747831] system 00:00: [mem 0xfec00000-0xfed3ffff] could not be reserved
[    2.747835] system 00:00: [mem 0xfed4c000-0xffffffff] could not be reserved
[    2.747842] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    2.748366] system 00:01: [io  0x164e-0x164f] has been reserved
[    2.748372] system 00:01: [io  0x1000-0x107f] has been reserved
[    2.748376] system 00:01: [io  0x1180-0x11ff] has been reserved
[    2.748381] system 00:01: [io  0x0800-0x080f] has been reserved
[    2.748385] system 00:01: [io  0x15e0-0x15ef] has been reserved
[    2.748389] system 00:01: [io  0x1600-0x1641] has been reserved
[    2.748393] system 00:01: [io  0x1644-0x167f] could not be reserved
[    2.748398] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    2.748403] system 00:01: [mem 0xfeaff000-0xfeafffff] has been reserved
[    2.748407] system 00:01: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    2.748411] system 00:01: [mem 0xfed10000-0xfed13fff] has been reserved
[    2.748416] system 00:01: [mem 0xfed18000-0xfed18fff] has been reserved
[    2.748420] system 00:01: [mem 0xfed19000-0xfed19fff] has been reserved
[    2.748424] system 00:01: [mem 0xfed45000-0xfed4bfff] has been reserved
[    2.748430] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    2.748508] pnp 00:02: Plug and Play ACPI device, IDs PNP0103 (active)
[    2.748525] pnp 00:03: [dma 4]
[    2.748552] pnp 00:03: Plug and Play ACPI device, IDs PNP0200 (active)
[    2.748595] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[    2.748648] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    2.748719] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    2.748770] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 (active)
[    2.748813] pnp 00:08: Plug and Play ACPI device, IDs LEN0015 PNP0f13 (active)
[    2.749278] pnp 00:09: Plug and Play ACPI device, IDs SMO1200 PNP0c31 (active)
[    2.750488] pnp: PnP ACPI: found 10 devices
[    2.750493] ACPI: ACPI bus type pnp unregistered
[    2.758737] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    2.758761] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    2.758767] pci 0000:00:1c.1:   bridge window [io  0x2000-0x2fff]
[    2.758777] pci 0000:00:1c.1:   bridge window [mem 0xf2400000-0xf24fffff]
[    2.758791] pci 0000:00:1c.3: PCI bridge to [bus 05-0c]
[    2.758797] pci 0000:00:1c.3:   bridge window [io  0x3000-0x3fff]
[    2.758806] pci 0000:00:1c.3:   bridge window [mem 0xf0000000-0xf1ffffff]
[    2.758813] pci 0000:00:1c.3:   bridge window [mem 0xf2900000-0xf29fffff 64bit pref]
[    2.758825] pci 0000:00:1c.4: PCI bridge to [bus 0d]
[    2.758834] pci 0000:00:1c.4:   bridge window [mem 0xf2500000-0xf25fffff]
[    2.758849] pci 0000:00:1e.0: PCI bridge to [bus 0e]
[    2.758929] pci 0000:00:1e.0: setting latency timer to 64
[    2.758937] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    2.758940] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    2.758944] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    2.758948] pci_bus 0000:00: resource 7 [mem 0x000d4000-0x000d7fff]
[    2.758951] pci_bus 0000:00: resource 8 [mem 0x000d8000-0x000dbfff]
[    2.758955] pci_bus 0000:00: resource 9 [mem 0xc0000000-0xfebfffff]
[    2.758959] pci_bus 0000:03: resource 0 [io  0x2000-0x2fff]
[    2.758963] pci_bus 0000:03: resource 1 [mem 0xf2400000-0xf24fffff]
[    2.758967] pci_bus 0000:05: resource 0 [io  0x3000-0x3fff]
[    2.758970] pci_bus 0000:05: resource 1 [mem 0xf0000000-0xf1ffffff]
[    2.758974] pci_bus 0000:05: resource 2 [mem 0xf2900000-0xf29fffff 64bit pref]
[    2.758978] pci_bus 0000:0d: resource 1 [mem 0xf2500000-0xf25fffff]
[    2.758982] pci_bus 0000:0e: resource 4 [io  0x0000-0x0cf7]
[    2.758986] pci_bus 0000:0e: resource 5 [io  0x0d00-0xffff]
[    2.758989] pci_bus 0000:0e: resource 6 [mem 0x000a0000-0x000bffff]
[    2.758993] pci_bus 0000:0e: resource 7 [mem 0x000d4000-0x000d7fff]
[    2.758996] pci_bus 0000:0e: resource 8 [mem 0x000d8000-0x000dbfff]
[    2.759000] pci_bus 0000:0e: resource 9 [mem 0xc0000000-0xfebfffff]
[    2.759059] NET: Registered protocol family 2
[    2.759385] TCP established hash table entries: 65536 (order: 8, 1048576 bytes)
[    2.760121] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    2.760770] TCP: Hash tables configured (established 65536 bind 65536)
[    2.760814] TCP: reno registered
[    2.760837] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    2.760969] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    2.761180] NET: Registered protocol family 1
[    2.761216] pci 0000:00:02.0: Boot video device
[    2.761450] PCI: CLS 64 bytes, default 64
[    2.761517] Trying to unpack rootfs image as initramfs...
[    3.297655] Freeing initrd memory: 15848k freed
[    3.301857] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    3.301867] software IO TLB [mem 0xb727c000-0xbb27c000] (64MB) mapped at [ffff8800b727c000-ffff8800bb27bfff]
[    3.301932] Simple Boot Flag at 0x35 set to 0x1
[    3.302521] Initialise module verification
[    3.302604] audit: initializing netlink socket (disabled)
[    3.302629] type=2000 audit(1381823082.872:1): initialized
[    3.358382] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    3.361001] VFS: Disk quotas dquot_6.5.2
[    3.361078] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    3.361872] fuse init (API version 7.20)
[    3.361993] msgmni has been set to 15558
[    3.362821] Key type asymmetric registered
[    3.362826] Asymmetric key parser 'x509' registered
[    3.362888] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    3.362933] io scheduler noop registered
[    3.362937] io scheduler deadline registered (default)
[    3.362947] io scheduler cfq registered
[    3.363364] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    3.363388] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    3.363454] intel_idle: MWAIT substates: 0x1120
[    3.363457] intel_idle: v0.4 model 0x25
[    3.363459] intel_idle: lapic_timer_reliable_states 0xffffffff
[    3.363981] ACPI: AC Adapter [AC] (off-line)
[    3.364118] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    3.364437] ACPI: Lid Switch [LID]
[    3.364503] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    3.364510] ACPI: Sleep Button [SLPB]
[    3.364577] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    3.364582] ACPI: Power Button [PWRF]
[    3.364691] ACPI: Requesting acpi_cpufreq
[    3.384651] thermal LNXTHERM:00: registered as thermal_zone0
[    3.384657] ACPI: Thermal Zone [THM0] (48 C)
[    3.384709] GHES: HEST is not enabled!
[    3.384850] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    3.407993] 0000:00:16.3: ttyS4 at I/O 0x1808 (irq = 17) is a 16550A
[    3.408341] Linux agpgart interface v0.103
[    3.408492] agpgart-intel 0000:00:00.0: Intel HD Graphics Chipset
[    3.408693] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    3.409930] agpgart-intel 0000:00:00.0: detected 32768K stolen memory
[    3.410149] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    3.412734] brd: module loaded
[    3.414055] loop: module loaded
[    3.414679] libphy: Fixed MDIO Bus: probed
[    3.414817] tun: Universal TUN/TAP device driver, 1.6
[    3.414820] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    3.414891] PPP generic driver version 2.4.2
[    3.414963] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.414966] ehci-pci: EHCI PCI platform driver
[    3.415026] ehci-pci 0000:00:1a.0: setting latency timer to 64
[    3.415057] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    3.415067] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    3.415089] ehci-pci 0000:00:1a.0: debug port 2
[    3.419037] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    3.419070] ehci-pci 0000:00:1a.0: irq 23, io mem 0xf2828000
[    3.423643] ACPI: Battery Slot [BAT0] (battery present)
[    3.427529] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    3.427573] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    3.427577] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    3.427581] usb usb1: Product: EHCI Host Controller
[    3.427585] usb usb1: Manufacturer: Linux 3.8.0-31-generic ehci_hcd
[    3.427588] usb usb1: SerialNumber: 0000:00:1a.0
[    3.427755] hub 1-0:1.0: USB hub found
[    3.427763] hub 1-0:1.0: 3 ports detected
[    3.427939] ehci-pci 0000:00:1d.0: setting latency timer to 64
[    3.427945] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    3.427953] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    3.427973] ehci-pci 0000:00:1d.0: debug port 2
[    3.431882] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    3.431905] ehci-pci 0000:00:1d.0: irq 19, io mem 0xf2828400
[    3.443500] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    3.443527] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    3.443531] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    3.443534] usb usb2: Product: EHCI Host Controller
[    3.443538] usb usb2: Manufacturer: Linux 3.8.0-31-generic ehci_hcd
[    3.443541] usb usb2: SerialNumber: 0000:00:1d.0
[    3.443680] hub 2-0:1.0: USB hub found
[    3.443686] hub 2-0:1.0: 3 ports detected
[    3.443824] ehci-platform: EHCI generic platform driver
[    3.443836] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.443858] uhci_hcd: USB Universal Host Controller Interface driver
[    3.443951] i8042: PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    3.447371] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.447381] serio: i8042 AUX port at 0x60,0x64 irq 12
[    3.447577] mousedev: PS/2 mouse device common for all mice
[    3.447880] rtc_cmos 00:06: RTC can wake from S4
[    3.448069] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    3.448107] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    3.448251] device-mapper: uevent: version 1.0.3
[    3.448366] device-mapper: ioctl: 4.23.1-ioctl (2012-12-18) initialised: dm-devel@redhat.com
[    3.448490] cpuidle: using governor ladder
[    3.448619] cpuidle: using governor menu
[    3.448637] ledtrig-cpu: registered to indicate activity on CPUs
[    3.448640] EFI Variables Facility v0.08 2004-May-17
[    3.448920] ashmem: initialized
[    3.449104] TCP: cubic registered
[    3.449254] NET: Registered protocol family 10
[    3.449535] NET: Registered protocol family 17
[    3.449550] Key type dns_resolver registered
[    3.449905] Loading module verification certificates
[    3.450830] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    3.451858] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: beedac769733b6dde22c1ae0d3a2045ac52087e1'
[    3.451881] registered taskstats version 1
[    3.455945] Key type trusted registered
[    3.459101] Key type encrypted registered
[    3.463025] rtc_cmos 00:06: setting system clock to 2013-10-15 07:44:46 UTC (1381823086)
[    3.466116] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.466118] EDD information not available.
[    3.467325] Freeing unused kernel memory: 996k freed
[    3.467521] Write protecting the kernel read-only data: 12288k
[    3.470140] Freeing unused kernel memory: 1168k freed
[    3.472683] Freeing unused kernel memory: 1076k freed
[    3.483274] udevd[106]: starting version 175
[    3.512025] Disabling lock debugging due to kernel taint
[    3.512558] e1000e: Intel(R) PRO/1000 Network Driver - 2.1.4-k
[    3.512561] e1000e: Copyright(c) 1999 - 2012 Intel Corporation.
[    3.512601] e1000e 0000:00:19.0: setting latency timer to 64
[    3.512676] e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    3.512726] e1000e 0000:00:19.0: irq 40 for MSI/MSI-X
[    3.516172] sdhci: Secure Digital Host Controller Interface driver
[    3.516175] sdhci: Copyright(c) Pierre Ossman
[    3.517811] sdhci-pci 0000:0d:00.0: SDHCI controller found [1180:e822] (rev 1)
[    3.517953] sdhci-pci 0000:0d:00.0: Will use DMA mode even though HW doesn't fully claim to support it.
[    3.517959] mmc0: no vqmmc regulator found
[    3.517961] mmc0: no vmmc regulator found
[    3.547331] mmc0: SDHCI controller on PCI [0000:0d:00.0] using DMA
[    3.611310] firewire_ohci 0000:0d:00.3: added OHCI v1.10 device as card 0, 4 IR + 4 IT contexts, quirks 0x11
[    3.696806] e1000e 0000:00:19.0 eth0: (PCI Express:2.5GT/s:Width x1) f0:de:f1:02:91:6e
[    3.696809] e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
[    3.696877] e1000e 0000:00:19.0 eth0: MAC: 9, PHY: 10, PBA No: A002FF-0FF
[    3.696969] ahci 0000:00:1f.2: version 3.0
[    3.697054] ahci 0000:00:1f.2: irq 41 for MSI/MSI-X
[    3.697106] ahci: SSS flag set, parallel bus scan disabled
[    3.697173] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 3 Gbps 0x33 impl SATA mode
[    3.697177] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck stag pm led clo pio slum part ems sxs apst 
[    3.697182] ahci 0000:00:1f.2: setting latency timer to 64
[    3.719473] scsi0 : ahci
[    3.719572] scsi1 : ahci
[    3.719717] scsi2 : ahci
[    3.719862] scsi3 : ahci
[    3.719989] scsi4 : ahci
[    3.720123] scsi5 : ahci
[    3.720209] ata1: SATA max UDMA/133 abar m2048@0xf2827000 port 0xf2827100 irq 41
[    3.720212] ata2: SATA max UDMA/133 abar m2048@0xf2827000 port 0xf2827180 irq 41
[    3.720214] ata3: DUMMY
[    3.720215] ata4: DUMMY
[    3.720217] ata5: SATA max UDMA/133 abar m2048@0xf2827000 port 0xf2827300 irq 41
[    3.720220] ata6: SATA max UDMA/133 abar m2048@0xf2827000 port 0xf2827380 irq 41
[    3.738999] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    3.871338] usb 1-1: New USB device found, idVendor=8087, idProduct=0020
[    3.871345] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    3.871687] hub 1-1:1.0: USB hub found
[    3.871924] hub 1-1:1.0: 6 ports detected
[    3.982600] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    4.110617] firewire_core 0000:0d:00.3: created device fw0: GUID f0def1ff02916eff, S400
[    4.115166] usb 2-1: New USB device found, idVendor=8087, idProduct=0020
[    4.115171] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    4.115550] hub 2-1:1.0: USB hub found
[    4.115759] hub 2-1:1.0: 8 ports detected
[    4.190493] usb 1-1.6: new high-speed USB device number 3 using ehci-pci
[    4.288082] usb 1-1.6: New USB device found, idVendor=17ef, idProduct=480f
[    4.288088] usb 1-1.6: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    4.288092] usb 1-1.6: Product: Integrated Camera
[    4.288096] usb 1-1.6: Manufacturer: Chicony Electronics Co., Ltd.
[    4.298043] tsc: Refined TSC clocksource calibration: 2394.000 MHz
[    4.298050] Switching to clocksource tsc
[    5.715654] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    5.716662] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[    5.716668] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    5.716672] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    5.767059] ata1.00: ATA-8: TOSHIBA MK5061GSY, MC102E, max UDMA/100
[    5.767064] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    5.768311] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[    5.768317] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    5.768321] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    5.769415] ata1.00: configured for UDMA/100
[    5.769622] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK5061GS MC10 PQ: 0 ANSI: 5
[    5.769793] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    5.769842] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    5.769937] sd 0:0:0:0: [sda] Write Protect is off
[    5.769940] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.769960] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.859901]  sda: sda1 sda2 < sda5 >
[    5.860783] sd 0:0:0:0: [sda] Attached SCSI disk
[    6.087016] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    6.092711] ata2.00: ACPI cmd e3/00:1f:00:00:00:a0 (IDLE) succeeded
[    6.093616] ata2.00: ACPI cmd e3/00:02:00:00:00:a0 (IDLE) succeeded
[    6.097363] ata2.00: ATAPI: HL-DT-ST DVDRAM GU10N, MX05, max UDMA/133
[    6.103780] ata2.00: ACPI cmd e3/00:1f:00:00:00:a0 (IDLE) succeeded
[    6.104675] ata2.00: ACPI cmd e3/00:02:00:00:00:a0 (IDLE) succeeded
[    6.108476] ata2.00: configured for UDMA/133
[    6.113994] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GU10N     MX05 PQ: 0 ANSI: 5
[    6.119081] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    6.119085] cdrom: Uniform CD-ROM driver Revision: 3.20
[    6.119231] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    6.119287] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    6.438423] ata5: SATA link down (SStatus 0 SControl 300)
[    6.757858] ata6: SATA link down (SStatus 0 SControl 300)
[    9.380515] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    9.380518] EXT4-fs (sda1): write access will be enabled during recovery
[  111.137933] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[  111.137940] ata1.00: failed command: FLUSH CACHE EXT
[  111.137948] ata1.00: cmd ea/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[  111.137948]          res 40/00:01:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[  111.137951] ata1.00: status: { DRDY }
[  111.137958] ata1: hard resetting link
[  114.140759] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[  114.141943] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[  114.141949] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[  114.141953] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[  114.200690] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[  114.200696] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[  114.200700] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[  114.201868] ata1.00: configured for UDMA/100
[  114.201873] ata1.00: retrying FLUSH 0xea Emask 0x4
[  114.202017] ata1.00: device reported invalid CHS sector 0
[  114.202029] ata1: EH complete
[  115.798044] EXT4-fs (sda1): recovery complete
[  117.383551] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[  128.246013] Adding 8177660k swap on /dev/sda5.  Priority:-1 extents:1 across:8177660k 
[  128.302113] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[  128.308388] init: bootchart main process (368) terminated with status 127
[  128.341929] udevd[380]: starting version 175
[  128.791540] intel ips 0000:00:1f.6: CPU TDP doesn't match expected value (found 25, expected 29)
[  128.791594] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled until i915 loads
[  128.791671] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 90
[  128.793026] lp: driver loaded but no devices found
[  128.794907] mei 0000:00:16.0: setting latency timer to 64
[  128.794972] mei 0000:00:16.0: irq 42 for MSI/MSI-X
[  128.799283] [drm] Initialized drm 1.1.0 20060810
[  128.802081] type=1400 audit(1381823212.049:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=535 comm="apparmor_parser"
[  128.802633] type=1400 audit(1381823212.049:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=535 comm="apparmor_parser"
[  128.802948] type=1400 audit(1381823212.049:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=535 comm="apparmor_parser"
[  128.803166] microcode: CPU0 sig=0x20652, pf=0x10, revision=0x9
[  128.806994] type=1400 audit(1381823212.053:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=536 comm="apparmor_parser"
[  128.807430] type=1400 audit(1381823212.057:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=536 comm="apparmor_parser"
[  128.807665] type=1400 audit(1381823212.057:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=536 comm="apparmor_parser"
[  128.813371] ACPI Warning: 0x0000000000001028-0x000000000000102f SystemIO conflicts with Region \_SB_.PCI0.LPC_.PMIO 1 (20121018/utaddress-251)
[  128.813380] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[  128.813418] ACPI Warning: 0x00000000000011c0-0x00000000000011cf SystemIO conflicts with Region \_SB_.PCI0.LPC_.LPIO 1 (20121018/utaddress-251)
[  128.813423] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[  128.813426] ACPI Warning: 0x00000000000011b0-0x00000000000011bf SystemIO conflicts with Region \_SB_.PCI0.LPC_.LPIO 1 (20121018/utaddress-251)
[  128.813429] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[  128.813431] ACPI Warning: 0x0000000000001180-0x00000000000011af SystemIO conflicts with Region \_SB_.PCI0.LPC_.LPIO 1 (20121018/utaddress-251)
[  128.813435] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[  128.813437] lpc_ich: Resource conflict(s) found affecting gpio_ich
[  128.822162] cfg80211: Calling CRDA to update world regulatory domain
[  128.823456] i915 0000:00:02.0: setting latency timer to 64
[  128.885282] rtl8192se: FW Power Save off (module option)
[  128.885338] rtl8192se: Driver for Realtek RTL8192SE/RTL8191SE
[  128.885338] Loading firmware rtlwifi/rtl8192sefw.bin
[  128.894166] wmi: Mapper loaded
[  128.894863] i915 0000:00:02.0: irq 43 for MSI/MSI-X
[  128.894875] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[  128.894877] [drm] Driver supports precise vblank timestamp query.
[  128.895278] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[  128.899062] Non-volatile memory driver v1.3
[  128.904538] thinkpad_acpi: ThinkPad ACPI Extras v0.24
[  128.904543] thinkpad_acpi: http://ibm-acpi.sf.net/
[  128.904545] thinkpad_acpi: ThinkPad BIOS 6IET68WW (1.28 ), EC 6IHT36WW-1.11
[  128.904547] thinkpad_acpi: Lenovo ThinkPad T410, model 2516ADU
[  128.906629] thinkpad_acpi: detected a 8-level brightness capable ThinkPad
[  128.906798] thinkpad_acpi: radio switch found; radios are enabled
[  128.906927] thinkpad_acpi: This ThinkPad has standard ACPI backlight brightness control, supported by the ACPI video driver
[  128.906930] thinkpad_acpi: Disabling thinkpad-acpi brightness events by default...
[  128.917899] thinkpad_acpi: Standard ACPI backlight interface available, not loading native one
[  128.918027] thinkpad_acpi: Console audio control enabled, mode: monitor (read only)
[  128.918412] tpm_tis 00:09: 1.2 TPM (device-id 0x0, rev-id 78)
[  128.920791] input: ThinkPad Extra Buttons as /devices/platform/thinkpad_acpi/input/input4
[  128.975201] tpm_tis 00:09: TPM is disabled/deactivated (0x6)
[  129.162868] [drm] GMBUS [i915 gmbus dpb] timed out, falling back to bit banging on pin 5
[  129.276926] fbcon: inteldrmfb (fb0) is primary device
[  129.791716] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd047b3/0xb40000/0xa0000, board id: 71, fw id: 578367
[  129.791724] psmouse serio1: synaptics: serio: Synaptics pass-through port at isa0060/serio1/input0
[  129.801867] Console: switching to colour frame buffer device 160x50
[  129.804356] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[  129.804357] i915 0000:00:02.0: registered panic notifier
[  129.808049] acpi device:01: registered as cooling_device4
[  129.809619] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[  129.809793] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input5
[  129.810060] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[  129.810592] snd_hda_intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[  129.823535] hda_codec: CX20585: BIOS auto-probing.
[  129.831911] input: HDA Intel MID HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[  129.832082] input: HDA Intel MID HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[  129.832207] input: HDA Intel MID HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[  129.832327] input: HDA Intel MID Dock Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[  129.832439] input: HDA Intel MID Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[  129.832553] input: HDA Intel MID Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[  129.833017] input: HDA Intel MID Dock Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[  129.846363] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input13
[  132.168799] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[  132.174860] Linux video capture interface: v2.00
[  132.182860] uvcvideo: Found UVC 1.00 device Integrated Camera (17ef:480f)
[  132.184086] input: Integrated Camera as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/input/input14
[  132.184205] usbcore: registered new interface driver uvcvideo
[  132.184207] USB Video Class driver (1.1.1)
[  133.386964] psmouse serio2: alps: Unknown ALPS touchpad: E7=10 00 64, EC=10 00 64
[  133.982614] intel ips 0000:00:1f.6: i915 driver attached, reenabling gpu turbo
[  135.477404] cfg80211: World regulatory domain updated:
[  135.477409] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  135.477411] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  135.477414] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  135.477416] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  135.477417] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  135.477419] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  135.530747] microcode: CPU1 sig=0x20652, pf=0x10, revision=0x9
[  135.532023] microcode: CPU2 sig=0x20652, pf=0x10, revision=0x9
[  135.533185] microcode: CPU3 sig=0x20652, pf=0x10, revision=0x9
[  135.534517] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[  135.543565] kvm: disabled by bios
[  135.544897] kvm: disabled by bios
[  135.596399] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[  137.341377] psmouse serio2: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3
[  137.599963] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/serio2/input/input15
[  143.349994] init: failsafe main process (838) killed by TERM signal
[  144.051347] Bluetooth: Core ver 2.16
[  144.051370] NET: Registered protocol family 31
[  144.051371] Bluetooth: HCI device and connection manager initialized
[  144.051381] Bluetooth: HCI socket layer initialized
[  144.051383] Bluetooth: L2CAP socket layer initialized
[  144.051387] Bluetooth: SCO socket layer initialized
[  144.055258] Bluetooth: RFCOMM TTY layer initialized
[  144.055273] Bluetooth: RFCOMM socket layer initialized
[  144.055275] Bluetooth: RFCOMM ver 1.11
[  144.055614] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  144.055617] Bluetooth: BNEP filters: protocol multicast
[  144.055623] Bluetooth: BNEP socket layer initialized
[  144.376781] init: bootchart post-stop process (377) terminated with status 127
[  144.486007] ppdev: user-space parallel port driver
[  144.641905] init: avahi-cups-reload main process (917) terminated with status 1
[  144.656516] type=1400 audit(1381823227.933:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=945 comm="apparmor_parser"
[  144.656988] type=1400 audit(1381823227.933:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=945 comm="apparmor_parser"
[  145.221447] e1000e 0000:00:19.0: irq 40 for MSI/MSI-X
[  145.323016] e1000e 0000:00:19.0: irq 40 for MSI/MSI-X
[  145.323131] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[  145.323447] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[  145.475874] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  145.476189] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  145.487599] type=1400 audit(1381823228.765:10): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1006 comm="apparmor_parser"
[  145.488049] type=1400 audit(1381823228.765:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1003 comm="apparmor_parser"
[  145.488057] type=1400 audit(1381823228.765:12): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1006 comm="apparmor_parser"
[  145.488108] type=1400 audit(1381823228.765:13): apparmor="STATUS" operation="profile_load" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper" pid=1004 comm="apparmor_parser"
[  145.488116] type=1400 audit(1381823228.765:14): apparmor="STATUS" operation="profile_load" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-uccsconfigure/uccsconfigure-session-wrapper" pid=1005 comm="apparmor_parser"
[  145.488364] type=1400 audit(1381823228.765:15): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1006 comm="apparmor_parser"
[  145.488455] type=1400 audit(1381823228.765:16): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=1003 comm="apparmor_parser"
[  145.488550] type=1400 audit(1381823228.765:17): apparmor="STATUS" operation="profile_load" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper//chromium_browser" pid=1004 comm="apparmor_parser"
[  147.220706] wlan0: authenticate with 00:18:4d:54:f8:3c
[  147.239666] wlan0: send auth to 00:18:4d:54:f8:3c (try 1/3)
[  147.242948] wlan0: authenticated
[  147.243260] rtl8192se 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  147.243675] wlan0: associate with 00:18:4d:54:f8:3c (try 1/3)
[  147.246932] wlan0: RX AssocResp from 00:18:4d:54:f8:3c (capab=0x431 status=0 aid=1)
[  147.247943] wlan0: associated
[  147.247951] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  149.636796] init: plymouth-stop pre-start process (1495) terminated with status 1
[  153.163289] init: winbind main process (1902) terminated with status 127
[  153.163315] init: winbind main process ended, respawning
[  153.167389] init: winbind main process (1915) terminated with status 127
[  153.167413] init: winbind main process ended, respawning
[  153.173207] init: winbind main process (1917) terminated with status 127
[  153.173238] init: winbind main process ended, respawning
[  153.177110] init: winbind main process (1919) terminated with status 127
[  153.177132] init: winbind main process ended, respawning
[  153.181212] init: winbind main process (1921) terminated with status 127
[  153.181245] init: winbind main process ended, respawning
[  153.184905] init: winbind main process (1923) terminated with status 127
[  153.184926] init: winbind main process ended, respawning
[  153.188394] init: winbind main process (1925) terminated with status 127
[  153.188416] init: winbind main process ended, respawning
[  153.192356] init: winbind main process (1927) terminated with status 127
[  153.192377] init: winbind main process ended, respawning
[  153.196209] init: winbind main process (1929) terminated with status 127
[  153.196231] init: winbind main process ended, respawning
[  153.199730] init: winbind main process (1931) terminated with status 127
[  153.199759] init: winbind main process ended, respawning
[  153.203379] init: winbind main process (1933) terminated with status 127
[  153.203407] init: winbind respawning too fast, stopped
[  453.507132] usb 1-1.2: new high-speed USB device number 4 using ehci-pci
[  453.680016] usb 1-1.2: New USB device found, idVendor=045e, idProduct=04ec
[  453.680021] usb 1-1.2: New USB device strings: Mfr=0, Product=8, SerialNumber=9
[  453.680023] usb 1-1.2: Product: RM-801|NOKIA Lumia 800
[  453.680025] usb 1-1.2: SerialNumber: 99461300-b56a-0801-82c9-dc6a6adc7909
[  455.608962] systemd-hostnamed[2566]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
```

---

