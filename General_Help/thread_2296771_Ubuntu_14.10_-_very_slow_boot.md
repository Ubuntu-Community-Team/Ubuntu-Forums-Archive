---
title: "Ubuntu 14.10 - very slow boot"
date: 2015-09-28
forum: General Help
---

### Post by tom209 on 2015-09-28
Hi, recently my Ubuntu installation has been acting up and booting it up has become an extremely lengthy process. After checking my dmesg output I was able to shave off 200 seconds, but I'm afraid that's as far as my google-fu will take me. I'd be very grateful if you could help me with eliminating some of the delays, since all I can find are bug reports without any solutions.
Here's my dmesg output after my fixes:

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.16.0-37-generic (buildd@toyol) (gcc version 4.9.1 (Ubuntu 4.9.1-16ubuntu6) ) #51-Ubuntu SMP Tue May 5 13:45:59 UTC 2015 (Ubuntu 3.16.0-37.51-generic 3.16.7-ckt9)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.16.0-37-generic root=UUID=70d30715-c155-4b74-bd98-99dd3801af8c ro vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009dbff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009dc00-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000001fffffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000020000000-0x00000000201fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000020200000-0x0000000040003fff] usable
[    0.000000] BIOS-e820: [mem 0x0000000040004000-0x0000000040004fff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000040005000-0x00000000a6cf3fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000a6cf4000-0x00000000a7ebcfff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000a7ebd000-0x00000000a7fbcfff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000a7fbd000-0x00000000a7ffefff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000a7fff000-0x00000000a7ffffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000a8000000-0x00000000af1fffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed10000-0x00000000fed13fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed18000-0x00000000fed19fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffb00000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000024fdfffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.7 present.
[    0.000000] DMI: Hewlett-Packard HP ProBook 450 G0/1949, BIOS 68IRF Ver. F.50 08/07/2014
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] AGP: No AGP bridge found
[    0.000000] e820: last_pfn = 0x24fe00 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0FF800000 mask FFF800000 write-protect
[    0.000000]   1 base 000000000 mask F80000000 write-back
[    0.000000]   2 base 080000000 mask FE0000000 write-back
[    0.000000]   3 base 0A0000000 mask FF8000000 write-back
[    0.000000]   4 base 0A8000000 mask FFF000000 uncachable
[    0.000000]   5 base 100000000 mask F00000000 write-back
[    0.000000]   6 base 200000000 mask FC0000000 write-back
[    0.000000]   7 base 240000000 mask FE0000000 write-back
[    0.000000]   8 base 250000000 mask FF0000000 uncachable
[    0.000000]   9 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820: last_pfn = 0xa8000 max_arch_pfn = 0x400000000
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000097000] 97000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01fd2000, 0x01fd2fff] PGTABLE
[    0.000000] BRK [0x01fd3000, 0x01fd3fff] PGTABLE
[    0.000000] BRK [0x01fd4000, 0x01fd4fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x24fc00000-0x24fdfffff]
[    0.000000]  [mem 0x24fc00000-0x24fdfffff] page 2M
[    0.000000] BRK [0x01fd5000, 0x01fd5fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x24c000000-0x24fbfffff]
[    0.000000]  [mem 0x24c000000-0x24fbfffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x200000000-0x24bffffff]
[    0.000000]  [mem 0x200000000-0x24bffffff] page 2M
[    0.000000] BRK [0x01fd6000, 0x01fd6fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x00100000-0x1fffffff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x1fffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x20200000-0x40003fff]
[    0.000000]  [mem 0x20200000-0x3fffffff] page 2M
[    0.000000]  [mem 0x40000000-0x40003fff] page 4k
[    0.000000] BRK [0x01fd7000, 0x01fd7fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x40005000-0xa6cf3fff]
[    0.000000]  [mem 0x40005000-0x401fffff] page 4k
[    0.000000]  [mem 0x40200000-0xa6bfffff] page 2M
[    0.000000]  [mem 0xa6c00000-0xa6cf3fff] page 4k
[    0.000000] init_memory_mapping: [mem 0xa7fff000-0xa7ffffff]
[    0.000000]  [mem 0xa7fff000-0xa7ffffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x100000000-0x1ffffffff]
[    0.000000]  [mem 0x100000000-0x1ffffffff] page 2M
[    0.000000] RAMDISK: [mem 0x358fe000-0x36c76fff]
[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x00000000000F2F10 000024 (v02 HPQOEM)
[    0.000000] ACPI: XSDT 0x00000000A7FFE120 000094 (v01 HPQOEM SLIC-MPC 0000000F      01000013)
[    0.000000] ACPI: FACP 0x00000000A7FFC000 00010C (v05 HPQOEM 1949     0000000F HP   00000001)
[    0.000000] ACPI: DSDT 0x00000000A7FD5000 021B9D (v02 HPQOEM 1949     00000001 INTL 20110112)
[    0.000000] ACPI: FACS 0x00000000A7E72000 000040
[    0.000000] ACPI: HPET 0x00000000A7FFB000 000038 (v01 HPQOEM 1949     00000001 HP   00000001)
[    0.000000] ACPI: APIC 0x00000000A7FFA000 0000BC (v01 HPQOEM 1949     00000001 HP   00000001)
[    0.000000] ACPI: MCFG 0x00000000A7FF9000 00003C (v01 HPQOEM 1949     00000001 HP   00000001)
[    0.000000] ACPI: ASF! 0x00000000A7FF8000 0000A5 (v32 HPQOEM 1949     00000001 HP   00000001)
[    0.000000] ACPI: SSDT 0x00000000A7FD2000 0002CA (v01 HPQOEM SataAhci 00001000 INTL 20110112)
[    0.000000] ACPI: SSDT 0x00000000A7FD1000 00048A (v01 HPQOEM PtidDevc 00001000 INTL 20110112)
[    0.000000] ACPI: SLIC 0x00000000A7FD0000 000176 (v01 HPQOEM SLIC-MPC 00000001 HP   00000001)
[    0.000000] ACPI: MSDM 0x00000000A7FCF000 000055 (v03 HPQOEM SLIC-MPC 00000000 HP   00000001)
[    0.000000] ACPI: FPDT 0x00000000A7FCE000 000044 (v01 HPQOEM 1949     00000001 HP   00000001)
[    0.000000] ACPI: BGRT 0x00000000A7FCD000 000038 (v00 HPQOEM 1949     00000001 HP   00000001)
[    0.000000] ACPI: SSDT 0x00000000A7FCC000 0009B6 (v01 PmRef  Cpu0Ist  00003000 INTL 20110112)
[    0.000000] ACPI: SSDT 0x00000000A7FCB000 000AAD (v01 PmRef  CpuPm    00003000 INTL 20110112)
[    0.000000] ACPI: SSDT 0x00000000A7FCA000 000B46 (v01 SgRef  SgTabl   00001000 INTL 20110112)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000024fdfffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x24fdfffff]
[    0.000000]   NODE_DATA [mem 0x24fdf3000-0x24fdf7fff]
[    0.000000]  [ffffea0000000000-ffffea00093fffff] PMD -> [ffff880247600000-ffff88024f3fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x24fdfffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009cfff]
[    0.000000]   node   0: [mem 0x00100000-0x1fffffff]
[    0.000000]   node   0: [mem 0x20200000-0x40003fff]
[    0.000000]   node   0: [mem 0x40005000-0xa6cf3fff]
[    0.000000]   node   0: [mem 0xa7fff000-0xa7ffffff]
[    0.000000]   node   0: [mem 0x100000000-0x24fdfffff]
[    0.000000] On node 0 totalpages: 2058384
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3996 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 10604 pages used for memmap
[    0.000000]   DMA32 zone: 678644 pages, LIFO batch:31
[    0.000000]   Normal zone: 21496 pages used for memmap
[    0.000000]   Normal zone: 1375744 pages, LIFO batch:31
[    0.000000] Reserving Intel graphics stolen memory at 0xa9200000-0xaf1fffff
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x05] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x06] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x07] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x00] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 0, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] smpboot: Allowing 8 CPUs, 4 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: [mem 0x0009d000-0x0009dfff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x20000000-0x201fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x40004000-0x40004fff]
[    0.000000] PM: Registered nosave memory: [mem 0xa6cf4000-0xa7ebcfff]
[    0.000000] PM: Registered nosave memory: [mem 0xa7ebd000-0xa7fbcfff]
[    0.000000] PM: Registered nosave memory: [mem 0xa7fbd000-0xa7ffefff]
[    0.000000] PM: Registered nosave memory: [mem 0xa8000000-0xaf1fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xaf200000-0xdfffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfed0ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed10000-0xfed13fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed14000-0xfed17fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed18000-0xfed19fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1a000-0xfed1bfff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xffafffff]
[    0.000000] PM: Registered nosave memory: [mem 0xffb00000-0xffffffff]
[    0.000000] e820: [mem 0xaf200000-0xdfffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88024fa00000 s82432 r8192 d24064 u262144
[    0.000000] pcpu-alloc: s82432 r8192 d24064 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2026199
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.16.0-37-generic root=UUID=70d30715-c155-4b74-bd98-99dd3801af8c ro vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] AGP: Checking aperture...
[    0.000000] AGP: No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 8001012K/8233536K available (7750K kernel code, 1197K rwdata, 3612K rodata, 1360K init, 1308K bss, 232524K reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000]     Offload RCU callbacks from all CPUs
[    0.000000]     Offload RCU callbacks from CPUs: 0-7.
[    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=16, nr_cpu_ids=8
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 33030144 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 2593.891 MHz processor
[    0.000033] Calibrating delay loop (skipped), value calculated using timer frequency.. 5187.78 BogoMIPS (lpj=10375564)
[    0.000035] pid_max: default: 32768 minimum: 301
[    0.000042] ACPI: Core revision 20140424
[    0.010060] ACPI: All ACPI Tables successfully acquired
[    0.061785] Security Framework initialized
[    0.061801] AppArmor: AppArmor initialized
[    0.061802] Yama: becoming mindful.
[    0.062271] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.064152] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.064992] Mount-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.065001] Mountpoint-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.065216] Initializing cgroup subsys memory
[    0.065237] Initializing cgroup subsys devices
[    0.065243] Initializing cgroup subsys freezer
[    0.065245] Initializing cgroup subsys net_cls
[    0.065249] Initializing cgroup subsys blkio
[    0.065252] Initializing cgroup subsys perf_event
[    0.065253] Initializing cgroup subsys net_prio
[    0.065259] Initializing cgroup subsys hugetlb
[    0.065279] CPU: Physical Processor ID: 0
[    0.065280] CPU: Processor Core ID: 0
[    0.065284] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.065626] mce: CPU supports 7 MCE banks
[    0.065636] CPU0: Thermal monitoring enabled (TM1)
[    0.065645] Last level iTLB entries: 4KB 512, 2MB 8, 4MB 8
Last level dTLB entries: 4KB 512, 2MB 32, 4MB 32, 1GB 0
tlb_flushall_shift: 2
[    0.065761] Freeing SMP alternatives memory: 32K (ffffffff81e81000 - ffffffff81e89000)
[    0.066936] ftrace: allocating 29340 entries in 115 pages
[    0.080363] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.120071] smpboot: CPU0: Intel(R) Core(TM) i5-3230M CPU @ 2.60GHz (fam: 06, model: 3a, stepping: 09)
[    0.120079] TSC deadline timer enabled
[    0.120103] Performance Events: PEBS fmt1+, 16-deep LBR, IvyBridge events, full-width counters, Intel PMU driver.
[    0.120122] ... version:                3
[    0.120123] ... bit width:              48
[    0.120123] ... generic registers:      4
[    0.120124] ... value mask:             0000ffffffffffff
[    0.120125] ... max period:             0000ffffffffffff
[    0.120126] ... fixed-purpose events:   3
[    0.120127] ... event mask:             000000070000000f
[    0.121724] x86: Booting SMP configuration:
[    0.121726] .... node  #0, CPUs:      #1
[    0.135232] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.135309]  #2 #3
[    0.162088] x86: Booted up 1 node, 4 CPUs
[    0.162092] smpboot: Total of 4 processors activated (20751.12 BogoMIPS)
[    0.165209] devtmpfs: initialized
[    0.167573] evm: security.selinux
[    0.167574] evm: security.SMACK64
[    0.167575] evm: security.SMACK64EXEC
[    0.167576] evm: security.SMACK64TRANSMUTE
[    0.167577] evm: security.SMACK64MMAP
[    0.167578] evm: security.ima
[    0.167579] evm: security.capability
[    0.167623] PM: Registering ACPI NVS region [mem 0xa7ebd000-0xa7fbcfff] (1048576 bytes)
[    0.168393] pinctrl core: initialized pinctrl subsystem
[    0.168454] regulator-dummy: no parameters
[    0.168488] RTC time: 22:11:06, date: 09/28/15
[    0.168533] NET: Registered protocol family 16
[    0.168667] cpuidle: using governor ladder
[    0.168669] cpuidle: using governor menu
[    0.168712] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.168713] ACPI: bus type PCI registered
[    0.168715] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.168784] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.168786] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.169056] PCI: Using configuration type 1 for base access
[    0.169253] mtrr: your CPUs had inconsistent variable MTRR settings
[    0.169254] mtrr: probably your BIOS does not setup all CPUs.
[    0.169255] mtrr: corrected configuration.
[    0.170480] ACPI: Added _OSI(Module Device)
[    0.170482] ACPI: Added _OSI(Processor Device)
[    0.170483] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.170484] ACPI: Added _OSI(Processor Aggregator Device)
[    0.173642] ACPI: Executed 1 blocks of module-level executable AML code
[    0.194179] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.214723] ACPI: Dynamic OEM Table Load:
[    0.214732] ACPI: SSDT 0xFFFF880243D8B000 000861 (v01 PmRef  Cpu0Cst  00003001 INTL 20110112)
[    0.218359] ACPI: Dynamic OEM Table Load:
[    0.218365] ACPI: SSDT 0xFFFF880243D6A000 000303 (v01 PmRef  ApIst    00003000 INTL 20110112)
[    0.222258] ACPI: Dynamic OEM Table Load:
[    0.222263] ACPI: SSDT 0xFFFF880243E68200 000119 (v01 PmRef  ApCst    00003000 INTL 20110112)
[    1.832350] ACPI: Interpreter enabled
[    1.832357] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20140424/hwxface-580)
[    1.832361] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20140424/hwxface-580)
[    1.832374] ACPI: (supports S0 S3 S4 S5)
[    1.832375] ACPI: Using IOAPIC for interrupt routing
[    1.832398] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    1.833682] ACPI: Power Resource [APPR] (off)
[    1.836427] ACPI: Power Resource [COMP] (on)
[    1.836567] ACPI: Power Resource [LPP] (on)
[    1.839298] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    1.839303] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    1.840570] acpi PNP0A08:00: _OSC: OS now controls [PCIeHotplug PME AER PCIeCapability]
[    1.841112] PCI host bridge to bus 0000:00
[    1.841115] pci_bus 0000:00: root bus resource [bus 00-3e]
[    1.841117] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    1.841118] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    1.841120] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    1.841121] pci_bus 0000:00: root bus resource [mem 0xaf200000-0xdfffffff]
[    1.841122] pci_bus 0000:00: root bus resource [mem 0xf0000000-0xfedfffff]
[    1.841124] pci_bus 0000:00: root bus resource [mem 0xfee01000-0xffffffff]
[    1.841131] pci 0000:00:00.0: [8086:0154] type 00 class 0x060000
[    1.841203] pci 0000:00:01.0: [8086:0151] type 01 class 0x060400
[    1.841234] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    1.841294] pci 0000:00:02.0: [8086:0166] type 00 class 0x030000
[    1.841304] pci 0000:00:02.0: reg 0x10: [mem 0xd0000000-0xd03fffff 64bit]
[    1.841310] pci 0000:00:02.0: reg 0x18: [mem 0xc0000000-0xcfffffff 64bit pref]
[    1.841315] pci 0000:00:02.0: reg 0x20: [io  0x4000-0x403f]
[    1.841401] pci 0000:00:14.0: [8086:1e31] type 00 class 0x0c0330
[    1.841422] pci 0000:00:14.0: reg 0x10: [mem 0xd0a00000-0xd0a0ffff 64bit]
[    1.841482] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    1.841513] pci 0000:00:14.0: System wakeup disabled by ACPI
[    1.841550] pci 0000:00:16.0: [8086:1e3a] type 00 class 0x078000
[    1.841573] pci 0000:00:16.0: reg 0x10: [mem 0xd0a14000-0xd0a1400f 64bit]
[    1.841648] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    1.841722] pci 0000:00:1a.0: [8086:1e2d] type 00 class 0x0c0320
[    1.841740] pci 0000:00:1a.0: reg 0x10: [mem 0xd0a19000-0xd0a193ff]
[    1.841816] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    1.841849] pci 0000:00:1a.0: System wakeup disabled by ACPI
[    1.841884] pci 0000:00:1b.0: [8086:1e20] type 00 class 0x040300
[    1.841900] pci 0000:00:1b.0: reg 0x10: [mem 0xd0a10000-0xd0a13fff 64bit]
[    1.841973] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    1.842040] pci 0000:00:1c.0: [8086:1e10] type 01 class 0x060400
[    1.842175] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    1.842255] pci 0000:00:1c.2: [8086:1e14] type 01 class 0x060400
[    1.842391] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    1.842435] pci 0000:00:1c.2: System wakeup disabled by ACPI
[    1.842473] pci 0000:00:1c.3: [8086:1e16] type 01 class 0x060400
[    1.842609] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    1.842652] pci 0000:00:1c.3: System wakeup disabled by ACPI
[    1.842687] pci 0000:00:1c.5: [8086:1e1a] type 01 class 0x060400
[    1.842771] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    1.842806] pci 0000:00:1c.5: System wakeup disabled by ACPI
[    1.842846] pci 0000:00:1d.0: [8086:1e26] type 00 class 0x0c0320
[    1.842865] pci 0000:00:1d.0: reg 0x10: [mem 0xd0a18000-0xd0a183ff]
[    1.842941] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    1.842974] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    1.843009] pci 0000:00:1f.0: [8086:1e59] type 00 class 0x060100
[    1.843168] pci 0000:00:1f.2: [8086:1e03] type 00 class 0x010601
[    1.843186] pci 0000:00:1f.2: reg 0x10: [io  0x4068-0x406f]
[    1.843194] pci 0000:00:1f.2: reg 0x14: [io  0x4074-0x4077]
[    1.843202] pci 0000:00:1f.2: reg 0x18: [io  0x4060-0x4067]
[    1.843210] pci 0000:00:1f.2: reg 0x1c: [io  0x4070-0x4073]
[    1.843217] pci 0000:00:1f.2: reg 0x20: [io  0x4040-0x405f]
[    1.843225] pci 0000:00:1f.2: reg 0x24: [mem 0xd0a17000-0xd0a177ff]
[    1.843270] pci 0000:00:1f.2: PME# supported from D3hot
[    1.843370] pci 0000:01:00.0: [1002:6600] type 00 class 0x030000
[    1.843382] pci 0000:01:00.0: reg 0x10: [mem 0xb0000000-0xbfffffff 64bit pref]
[    1.843390] pci 0000:01:00.0: reg 0x18: [mem 0xd0900000-0xd093ffff 64bit]
[    1.843395] pci 0000:01:00.0: reg 0x20: [io  0x3000-0x30ff]
[    1.843404] pci 0000:01:00.0: reg 0x30: [mem 0xfffe0000-0xffffffff pref]
[    1.843445] pci 0000:01:00.0: supports D1 D2
[    1.843447] pci 0000:01:00.0: PME# supported from D1 D2 D3hot
[    1.850760] pci 0000:00:01.0: PCI bridge to [bus 01]
[    1.850765] pci 0000:00:01.0:   bridge window [io  0x3000-0x3fff]
[    1.850769] pci 0000:00:01.0:   bridge window [mem 0xd0900000-0xd09fffff]
[    1.850776] pci 0000:00:01.0:   bridge window [mem 0xb0000000-0xbfffffff 64bit pref]
[    1.850874] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    1.850882] pci 0000:00:1c.0:   bridge window [mem 0xd0800000-0xd08fffff]
[    1.850997] pci 0000:00:1c.2: PCI bridge to [bus 03]
[    1.851005] pci 0000:00:1c.2:   bridge window [mem 0xd0700000-0xd07fffff]
[    1.852757] pci 0000:04:00.0: [1814:3290] type 00 class 0x028000
[    1.852780] pci 0000:04:00.0: reg 0x10: [mem 0xd0610000-0xd061ffff]
[    1.852926] pci 0000:04:00.0: PME# supported from D0 D3hot
[    1.852955] pci 0000:04:00.0: System wakeup disabled by ACPI
[    1.854640] pci 0000:04:00.1: [1814:3298] type 00 class 0x0d1100
[    1.854663] pci 0000:04:00.1: reg 0x10: [mem 0xd0600000-0xd060ffff]
[    1.854813] pci 0000:04:00.1: supports D1
[    1.854814] pci 0000:04:00.1: PME# supported from D0 D1 D3hot
[    1.866079] pci 0000:00:1c.3: PCI bridge to [bus 04]
[    1.866085] pci 0000:00:1c.3:   bridge window [mem 0xd0600000-0xd06fffff]
[    1.866173] pci 0000:05:00.0: [10ec:8168] type 00 class 0x020000
[    1.866196] pci 0000:05:00.0: reg 0x10: [io  0x2000-0x20ff]
[    1.866230] pci 0000:05:00.0: reg 0x18: [mem 0xd0500000-0xd0500fff 64bit]
[    1.866252] pci 0000:05:00.0: reg 0x20: [mem 0xd0400000-0xd0403fff 64bit pref]
[    1.866366] pci 0000:05:00.0: supports D1 D2
[    1.866367] pci 0000:05:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.866405] pci 0000:05:00.0: System wakeup disabled by ACPI
[    1.874796] pci 0000:00:1c.5: PCI bridge to [bus 05]
[    1.874802] pci 0000:00:1c.5:   bridge window [io  0x2000-0x2fff]
[    1.874809] pci 0000:00:1c.5:   bridge window [mem 0xd0500000-0xd05fffff]
[    1.874832] pci 0000:00:1c.5:   bridge window [mem 0xd0400000-0xd04fffff 64bit pref]
[    1.874864] acpi PNP0A08:00: Disabling ASPM (FADT indicates it is unsupported)
[    1.875578] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 *10 11 12 14 15)
[    1.875619] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 10 11 12 14 15)
[    1.875657] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 *10 11 12 14 15)
[    1.875695] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 *10 11 12 14 15)
[    1.875733] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 *10 11 12 14 15)
[    1.875771] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    1.875809] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 10 *11 12 14 15)
[    1.875847] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    1.876064] ACPI: Enabled 5 GPEs in block 00 to 3F
[    1.876109] ACPI : EC: GPE = 0x16, I/O: command/status = 0x66, data = 0x62
[    1.876229] vgaarb: setting as boot device: PCI:0000:00:02.0
[    1.876232] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    1.876235] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=none,locks=none
[    1.876236] vgaarb: loaded
[    1.876237] vgaarb: bridge control possible 0000:01:00.0
[    1.876238] vgaarb: no bridge control possible 0000:00:02.0
[    1.876453] SCSI subsystem initialized
[    1.876499] libata version 3.00 loaded.
[    1.876536] ACPI: bus type USB registered
[    1.876553] usbcore: registered new interface driver usbfs
[    1.876562] usbcore: registered new interface driver hub
[    1.876585] usbcore: registered new device driver usb
[    1.876701] PCI: Using ACPI for IRQ routing
[    1.882937] PCI: pci_cache_line_size set to 64 bytes
[    1.882986] e820: reserve RAM buffer [mem 0x0009dc00-0x0009ffff]
[    1.882987] e820: reserve RAM buffer [mem 0x40004000-0x43ffffff]
[    1.882989] e820: reserve RAM buffer [mem 0xa6cf4000-0xa7ffffff]
[    1.882990] e820: reserve RAM buffer [mem 0x24fe00000-0x24fffffff]
[    1.883090] NetLabel: Initializing
[    1.883091] NetLabel:  domain hash size = 128
[    1.883092] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.883102] NetLabel:  unlabeled traffic allowed by default
[    1.883160] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    1.883165] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    1.885200] Switched to clocksource hpet
[    1.889996] AppArmor: AppArmor Filesystem Enabled
[    1.890027] pnp: PnP ACPI init
[    1.890040] ACPI: bus type PNP registered
[    1.890199] system 00:00: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    1.890202] system 00:00: [mem 0xfed10000-0xfed17fff] could not be reserved
[    1.890203] system 00:00: [mem 0xfed18000-0xfed18fff] has been reserved
[    1.890205] system 00:00: [mem 0xfed19000-0xfed19fff] has been reserved
[    1.890207] system 00:00: [mem 0xe0000000-0xefffffff] has been reserved
[    1.890208] system 00:00: [mem 0xfed20000-0xfed3ffff] has been reserved
[    1.890210] system 00:00: [mem 0xfed90000-0xfed93fff] has been reserved
[    1.890211] system 00:00: [mem 0xfed45000-0xfed8ffff] has been reserved
[    1.890213] system 00:00: [mem 0xfec00000-0xfec00fff] could not be reserved
[    1.890216] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.890364] system 00:01: [io  0xfe00-0xfe0f] has been reserved
[    1.890366] system 00:01: [io  0xfe80-0xfe8f] has been reserved
[    1.890368] system 00:01: [mem 0xfed40000-0xfed44fff] has been reserved
[    1.890370] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.890438] system 00:02: [io  0x0200-0x027f] has been reserved
[    1.890440] system 00:02: [io  0x1000-0x100f] has been reserved
[    1.890441] system 00:02: [io  0xffff] has been reserved
[    1.890443] system 00:02: [io  0xffff] has been reserved
[    1.890444] system 00:02: [io  0x0400-0x047f] could not be reserved
[    1.890446] system 00:02: [io  0x0500-0x057f] has been reserved
[    1.890447] system 00:02: [io  0xef80-0xef9f] has been reserved
[    1.890449] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.890479] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    1.890578] pnp 00:04: Plug and Play ACPI device, IDs HPQ8001 PNP0303 (active)
[    1.890603] pnp 00:05: Plug and Play ACPI device, IDs SYN3007 SYN0100 SYN0002 PNP0f13 (active)
[    1.890809] system 00:06: [mem 0x20000000-0x201fffff] has been reserved
[    1.890811] system 00:06: [mem 0x40004000-0x40004fff] has been reserved
[    1.890813] system 00:06: Plug and Play ACPI device, IDs PNP0c01 (active)
[    1.890945] pnp: PnP ACPI: found 7 devices
[    1.890947] ACPI: bus type PNP unregistered
[    1.897425] pci 0000:01:00.0: can't claim BAR 6 [mem 0xfffe0000-0xffffffff pref]: no compatible bridge window
[    1.897464] pci 0000:01:00.0: BAR 6: assigned [mem 0xd0940000-0xd095ffff pref]
[    1.897466] pci 0000:00:01.0: PCI bridge to [bus 01]
[    1.897468] pci 0000:00:01.0:   bridge window [io  0x3000-0x3fff]
[    1.897471] pci 0000:00:01.0:   bridge window [mem 0xd0900000-0xd09fffff]
[    1.897473] pci 0000:00:01.0:   bridge window [mem 0xb0000000-0xbfffffff 64bit pref]
[    1.897476] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    1.897481] pci 0000:00:1c.0:   bridge window [mem 0xd0800000-0xd08fffff]
[    1.897489] pci 0000:00:1c.2: PCI bridge to [bus 03]
[    1.897495] pci 0000:00:1c.2:   bridge window [mem 0xd0700000-0xd07fffff]
[    1.897502] pci 0000:00:1c.3: PCI bridge to [bus 04]
[    1.897508] pci 0000:00:1c.3:   bridge window [mem 0xd0600000-0xd06fffff]
[    1.897516] pci 0000:00:1c.5: PCI bridge to [bus 05]
[    1.897519] pci 0000:00:1c.5:   bridge window [io  0x2000-0x2fff]
[    1.897524] pci 0000:00:1c.5:   bridge window [mem 0xd0500000-0xd05fffff]
[    1.897528] pci 0000:00:1c.5:   bridge window [mem 0xd0400000-0xd04fffff 64bit pref]
[    1.897535] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    1.897536] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    1.897538] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    1.897539] pci_bus 0000:00: resource 7 [mem 0xaf200000-0xdfffffff]
[    1.897541] pci_bus 0000:00: resource 8 [mem 0xf0000000-0xfedfffff]
[    1.897542] pci_bus 0000:00: resource 9 [mem 0xfee01000-0xffffffff]
[    1.897544] pci_bus 0000:01: resource 0 [io  0x3000-0x3fff]
[    1.897545] pci_bus 0000:01: resource 1 [mem 0xd0900000-0xd09fffff]
[    1.897546] pci_bus 0000:01: resource 2 [mem 0xb0000000-0xbfffffff 64bit pref]
[    1.897548] pci_bus 0000:02: resource 1 [mem 0xd0800000-0xd08fffff]
[    1.897550] pci_bus 0000:03: resource 1 [mem 0xd0700000-0xd07fffff]
[    1.897551] pci_bus 0000:04: resource 1 [mem 0xd0600000-0xd06fffff]
[    1.897553] pci_bus 0000:05: resource 0 [io  0x2000-0x2fff]
[    1.897554] pci_bus 0000:05: resource 1 [mem 0xd0500000-0xd05fffff]
[    1.897556] pci_bus 0000:05: resource 2 [mem 0xd0400000-0xd04fffff 64bit pref]
[    1.897581] NET: Registered protocol family 2
[    1.897745] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
[    1.897877] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    1.897979] TCP: Hash tables configured (established 65536 bind 65536)
[    1.897993] TCP: reno registered
[    1.898004] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    1.898029] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    1.898081] NET: Registered protocol family 1
[    1.898096] pci 0000:00:02.0: Video device with shadowed ROM
[    1.898103] pci 0000:00:14.0: enabling device (0000 -> 0002)
[    1.898205] pci 0000:00:14.0: can't derive routing for PCI INT A
[    1.898206] pci 0000:00:14.0: PCI INT A: no GSI
[    1.898318] pci 0000:00:14.0: can't derive routing for PCI INT A
[    1.898328] pci 0000:00:1a.0: enabling device (0000 -> 0002)
[    1.898520] pci 0000:00:1d.0: enabling device (0000 -> 0002)
[    1.898706] PCI: CLS 64 bytes, default 64
[    1.898754] Trying to unpack rootfs image as initramfs...
[    2.177092] Freeing initrd memory: 19940K (ffff8800358fe000 - ffff880036c77000)
[    2.177109] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    2.177112] software IO TLB [mem 0xa2cf4000-0xa6cf4000] (64MB) mapped at [ffff8800a2cf4000-ffff8800a6cf3fff]
[    2.177309] resource sanity check: requesting [mem 0xfed10000-0xfed15fff], which spans more than reserved [mem 0xfed10000-0xfed13fff]
[    2.177311] ------------[ cut here ]------------
[    2.177315] WARNING: CPU: 2 PID: 1 at /build/buildd/linux-3.16.0/arch/x86/mm/ioremap.c:183 __ioremap_caller+0x25a/0x2e0()
[    2.177316] Info: mapping multiple BARs. Your kernel is fine.
[    2.177317] Modules linked in:

[    2.177320] CPU: 2 PID: 1 Comm: swapper/0 Not tainted 3.16.0-37-generic #51-Ubuntu
[    2.177321] Hardware name: Hewlett-Packard HP ProBook 450 G0/1949, BIOS 68IRF Ver. F.50 08/07/2014
[    2.177323]  0000000000000009 ffff880244127b78 ffffffff81784a0e ffff880244127bc0
[    2.177325]  ffff880244127bb0 ffffffff8106fefd ffffc90010e88000 0000000000006000
[    2.177327]  ffffc90010e88000 ffffc90010e88000 00000000fed10000 ffff880244127c10
[    2.177329] Call Trace:
[    2.177333]  [<ffffffff81784a0e>] dump_stack+0x45/0x56
[    2.177336]  [<ffffffff8106fefd>] warn_slowpath_common+0x7d/0xa0
[    2.177339]  [<ffffffff8106ff6c>] warn_slowpath_fmt+0x4c/0x50
[    2.177341]  [<ffffffff810773d7>] ? iomem_map_sanity_check+0xc7/0xd0
[    2.177344]  [<ffffffff8105d5ea>] __ioremap_caller+0x25a/0x2e0
[    2.177346]  [<ffffffff8105d687>] ioremap_nocache+0x17/0x20
[    2.177349]  [<ffffffff81033eed>] snb_uncore_imc_init_box+0x6d/0x90
[    2.177352]  [<ffffffff81036e3e>] uncore_pci_probe+0xce/0x1b0
[    2.177355]  [<ffffffff813e6dc5>] local_pci_probe+0x45/0xa0
[    2.177358]  [<ffffffff813e80a5>] ? pci_match_device+0xe5/0x110
[    2.177360]  [<ffffffff813e81e9>] pci_device_probe+0xd9/0x130
[    2.177363]  [<ffffffff814d3c83>] driver_probe_device+0xa3/0x410
[    2.177365]  [<ffffffff814d40bb>] __driver_attach+0x8b/0x90
[    2.177367]  [<ffffffff814d4030>] ? __device_attach+0x40/0x40
[    2.177370]  [<ffffffff814d1afb>] bus_for_each_dev+0x6b/0xb0
[    2.177371]  [<ffffffff814d370e>] driver_attach+0x1e/0x20
[    2.177373]  [<ffffffff814d3310>] bus_add_driver+0x180/0x250
[    2.177376]  [<ffffffff81d505af>] ? uncore_types_init+0x1a1/0x1a1
[    2.177377]  [<ffffffff814d4894>] driver_register+0x64/0xf0
[    2.177380]  [<ffffffff813e663c>] __pci_register_driver+0x4c/0x50
[    2.177382]  [<ffffffff81d50723>] intel_uncore_init+0x174/0x40b
[    2.177385]  [<ffffffff81d505af>] ? uncore_types_init+0x1a1/0x1a1
[    2.177388]  [<ffffffff81002148>] do_one_initcall+0xd8/0x210
[    2.177391]  [<ffffffff81092bc0>] ? parse_args+0x160/0x4e0
[    2.177408]  [<ffffffff81d4311d>] kernel_init_freeable+0x190/0x218
[    2.177410]  [<ffffffff81777e10>] ? rest_init+0x80/0x80
[    2.177412]  [<ffffffff81777e1e>] kernel_init+0xe/0xf0
[    2.177415]  [<ffffffff8178c958>] ret_from_fork+0x58/0x90
[    2.177417]  [<ffffffff81777e10>] ? rest_init+0x80/0x80
[    2.177422] ---[ end trace ab9b7e57054f3ba8 ]---
[    2.177467] RAPL PMU detected, hw unit 2^-16 Joules, API unit is 2^-32 Joules, 3 fixed counters 163840 ms ovfl timer
[    2.177509] microcode: CPU0 sig=0x306a9, pf=0x10, revision=0x16
[    2.177516] microcode: CPU1 sig=0x306a9, pf=0x10, revision=0x16
[    2.177519] microcode: CPU2 sig=0x306a9, pf=0x10, revision=0x16
[    2.177526] microcode: CPU3 sig=0x306a9, pf=0x10, revision=0x16
[    2.177580] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    2.177600] Scanning for low memory corruption every 60 seconds
[    2.177904] futex hash table entries: 2048 (order: 5, 131072 bytes)
[    2.177926] Initialise system trusted keyring
[    2.177947] audit: initializing netlink subsys (disabled)
[    2.177958] audit: type=2000 audit(1443478268.120:1): initialized
[    2.178291] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    2.179509] zpool: loaded
[    2.179513] zbud: loaded
[    2.179657] VFS: Disk quotas dquot_6.5.2
[    2.179686] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    2.180072] fuse init (API version 7.23)
[    2.180151] msgmni has been set to 15665
[    2.180202] Key type big_key registered
[    2.180560] Key type asymmetric registered
[    2.180563] Asymmetric key parser 'x509' registered
[    2.180594] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    2.180639] io scheduler noop registered
[    2.180642] io scheduler deadline registered (default)
[    2.180681] io scheduler cfq registered
[    2.180875] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    2.181027] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    2.181189] pcieport 0000:00:1c.2: irq 42 for MSI/MSI-X
[    2.181347] pcieport 0000:00:1c.3: irq 43 for MSI/MSI-X
[    2.181526] pcieport 0000:00:1c.5: irq 44 for MSI/MSI-X
[    2.181606] pcieport 0000:00:01.0: Signaling PME through PCIe PME interrupt
[    2.181608] pci 0000:01:00.0: Signaling PME through PCIe PME interrupt
[    2.181610] pcie_pme 0000:00:01.0:pcie01: service driver pcie_pme loaded
[    2.181627] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
[    2.181631] pcie_pme 0000:00:1c.0:pcie01: service driver pcie_pme loaded
[    2.181649] pcieport 0000:00:1c.2: Signaling PME through PCIe PME interrupt
[    2.181653] pcie_pme 0000:00:1c.2:pcie01: service driver pcie_pme loaded
[    2.181668] pcieport 0000:00:1c.3: Signaling PME through PCIe PME interrupt
[    2.181670] pci 0000:04:00.0: Signaling PME through PCIe PME interrupt
[    2.181671] pci 0000:04:00.1: Signaling PME through PCIe PME interrupt
[    2.181675] pcie_pme 0000:00:1c.3:pcie01: service driver pcie_pme loaded
[    2.181690] pcieport 0000:00:1c.5: Signaling PME through PCIe PME interrupt
[    2.181692] pci 0000:05:00.0: Signaling PME through PCIe PME interrupt
[    2.181696] pcie_pme 0000:00:1c.5:pcie01: service driver pcie_pme loaded
[    2.181709] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    2.181723] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    2.181764] vesafb: mode is 1366x768x32, linelength=5504, pages=0
[    2.181765] vesafb: scrolling: redraw
[    2.181767] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    2.181779] vesafb: framebuffer at 0xc0000000, mapped to 0xffffc90010f00000, using 4160k, total 4160k
[    2.181853] Console: switching to colour frame buffer device 170x48
[    2.181868] fb0: VESA VGA frame buffer device
[    2.181889] intel_idle: MWAIT substates: 0x21120
[    2.181890] intel_idle: v0.4 model 0x3A
[    2.181891] intel_idle: lapic_timer_reliable_states 0xffffffff
[    2.182187] ACPI: AC Adapter [AC] (on-line)
[    2.182343] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0
[    2.182347] ACPI: Sleep Button [SLPB]
[    2.182378] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    2.182395] ACPI: Lid Switch [LID]
[    2.182426] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    2.182428] ACPI: Power Button [PWRF]
[    2.206043] thermal LNXTHERM:00: registered as thermal_zone0
[    2.206046] ACPI: Thermal Zone [CPUZ] (54 C)
[    2.230675] thermal LNXTHERM:01: registered as thermal_zone1
[    2.230678] ACPI: Thermal Zone [GFXZ] (0 C)
[    2.245484] thermal LNXTHERM:02: registered as thermal_zone2
[    2.245486] ACPI: Thermal Zone [EXTZ] (42 C)
[    2.260230] thermal LNXTHERM:03: registered as thermal_zone3
[    2.260232] ACPI: Thermal Zone [LOCZ] (48 C)
[    2.275075] thermal LNXTHERM:04: registered as thermal_zone4
[    2.275077] ACPI: Thermal Zone [BATZ] (0 C)
[    2.275340] thermal LNXTHERM:05: registered as thermal_zone5
[    2.275341] ACPI: Thermal Zone [PCHZ] (127 C)
[    2.275374] GHES: HEST is not enabled!
[    2.275519] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    2.277426] Linux agpgart interface v0.103
[    2.278495] brd: module loaded
[    2.279004] loop: module loaded
[    2.279191] libphy: Fixed MDIO Bus: probed
[    2.279195] tun: Universal TUN/TAP device driver, 1.6
[    2.279196] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    2.279240] PPP generic driver version 2.4.2
[    2.279280] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.279285] ehci-pci: EHCI PCI platform driver
[    2.279412] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    2.279417] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    2.279430] ehci-pci 0000:00:1a.0: debug port 2
[    2.283319] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    2.283339] ehci-pci 0000:00:1a.0: irq 16, io mem 0xd0a19000
[    2.293509] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    2.293589] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    2.293591] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.293592] usb usb1: Product: EHCI Host Controller
[    2.293594] usb usb1: Manufacturer: Linux 3.16.0-37-generic ehci_hcd
[    2.293595] usb usb1: SerialNumber: 0000:00:1a.0
[    2.293761] hub 1-0:1.0: USB hub found
[    2.293768] hub 1-0:1.0: 2 ports detected
[    2.293989] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    2.293993] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.294004] ehci-pci 0000:00:1d.0: debug port 2
[    2.297917] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    2.297929] ehci-pci 0000:00:1d.0: irq 16, io mem 0xd0a18000
[    2.309522] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    2.309584] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    2.309586] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.309587] usb usb2: Product: EHCI Host Controller
[    2.309589] usb usb2: Manufacturer: Linux 3.16.0-37-generic ehci_hcd
[    2.309590] usb usb2: SerialNumber: 0000:00:1d.0
[    2.309754] hub 2-0:1.0: USB hub found
[    2.309760] hub 2-0:1.0: 2 ports detected
[    2.309874] ehci-platform: EHCI generic platform driver
[    2.309883] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.309888] ohci-pci: OHCI PCI platform driver
[    2.309896] ohci-platform: OHCI generic platform driver
[    2.309902] uhci_hcd: USB Universal Host Controller Interface driver
[    2.310009] xhci_hcd 0000:00:14.0: can't derive routing for PCI INT A
[    2.310011] xhci_hcd 0000:00:14.0: PCI INT A: no GSI
[    2.310027] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    2.310030] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
[    2.310120] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    2.310138] xhci_hcd 0000:00:14.0: irq 45 for MSI/MSI-X
[    2.310194] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    2.310195] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.310197] usb usb3: Product: xHCI Host Controller
[    2.310198] usb usb3: Manufacturer: Linux 3.16.0-37-generic xhci_hcd
[    2.310199] usb usb3: SerialNumber: 0000:00:14.0
[    2.310374] hub 3-0:1.0: USB hub found
[    2.310385] hub 3-0:1.0: 4 ports detected
[    2.310663] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    2.310666] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 4
[    2.310699] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
[    2.310700] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.310702] usb usb4: Product: xHCI Host Controller
[    2.310703] usb usb4: Manufacturer: Linux 3.16.0-37-generic xhci_hcd
[    2.310704] usb usb4: SerialNumber: 0000:00:14.0
[    2.310855] hub 4-0:1.0: USB hub found
[    2.310866] hub 4-0:1.0: 4 ports detected
[    2.311196] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.312972] i8042: Detected active multiplexing controller, rev 1.1
[    2.313649] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.313653] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    2.313674] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    2.313692] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    2.313709] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    2.313913] mousedev: PS/2 mouse device common for all mice
[    2.314211] rtc_cmos 00:03: RTC can wake from S4
[    2.314371] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    2.314400] rtc_cmos 00:03: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    2.314459] device-mapper: uevent: version 1.0.3
[    2.314520] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
[    2.314533] Intel P-state driver initializing.
[    2.314549] Intel pstate controlling: cpu 0
[    2.314567] Intel pstate controlling: cpu 1
[    2.314586] Intel pstate controlling: cpu 2
[    2.314602] Intel pstate controlling: cpu 3
[    2.314633] Consider also installing thermald for improved thermal control.
[    2.314637] ledtrig-cpu: registered to indicate activity on CPUs
[    2.314720] TCP: cubic registered
[    2.314803] NET: Registered protocol family 10
[    2.315012] NET: Registered protocol family 17
[    2.315023] Key type dns_resolver registered
[    2.315259] Loading compiled-in X.509 certificates
[    2.315966] Loaded X.509 cert 'Magrathea: Glacier signing key: bc5ddea14b638acdbbea44ffe74e821062411d12'
[    2.315982] registered taskstats version 1
[    2.318017] Key type trusted registered
[    2.318687] ACPI: Battery Slot [BAT0] (battery present)
[    2.321189] Key type encrypted registered
[    2.321195] AppArmor: AppArmor sha1 policy hashing enabled
[    2.321198] ima: No TPM chip found, activating TPM-bypass!
[    2.321211] evm: HMAC attrs: 0x1
[    2.321566]   Magic number: 15:75:200
[    2.321660] rtc_cmos 00:03: setting system clock to 2015-09-28 22:11:08 UTC (1443478268)
[    2.321723] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.321724] EDD information not available.
[    2.321786] PM: Hibernation image not present or could not be loaded.
[    2.322428] Freeing unused kernel memory: 1360K (ffffffff81d2d000 - ffffffff81e81000)
[    2.322430] Write protecting the kernel read-only data: 12288k
[    2.323224] Freeing unused kernel memory: 428K (ffff880001795000 - ffff880001800000)
[    2.324056] Freeing unused kernel memory: 484K (ffff880001b87000 - ffff880001c00000)
[    2.338212] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    2.338259] systemd-udevd[140]: starting version 208
[    2.338821] random: systemd-udevd urandom read with 9 bits of entropy available
[    2.359969] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.359978] r8169 0000:05:00.0: can't disable ASPM; OS doesn't have ASPM control
[    2.360260] ahci 0000:00:1f.2: version 3.0
[    2.360385] ahci 0000:00:1f.2: irq 46 for MSI/MSI-X
[    2.360403] ahci 0000:00:1f.2: SSS flag set, parallel bus scan disabled
[    2.360422] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x1 impl SATA mode
[    2.360424] ahci 0000:00:1f.2: flags: 64bit ncq stag pm led clo pio slum part ems apst 
[    2.360874] scsi0 : ahci
[    2.361147] scsi1 : ahci
[    2.361284] scsi2 : ahci
[    2.361607] scsi3 : ahci
[    2.361788] scsi4 : ahci
[    2.364741] scsi5 : ahci
[    2.364809] ata1: SATA max UDMA/133 abar m2048@0xd0a17000 port 0xd0a17100 irq 46
[    2.364811] ata2: DUMMY
[    2.364813] ata3: DUMMY
[    2.364814] ata4: DUMMY
[    2.364816] ata5: DUMMY
[    2.364817] ata6: DUMMY
[    2.365922] r8169 0000:05:00.0: irq 47 for MSI/MSI-X
[    2.366076] r8169 0000:05:00.0 eth0: RTL8168g/8111g at 0xffffc90000c86000, c8:cb:b8:c2:ac:a8, XID 0c000800 IRQ 47
[    2.366078] r8169 0000:05:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    2.605774] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    2.681781] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.683430] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[    2.683606] ata1.00: ATA-9: HGST HTS541010A9E680, JA0OA590, max UDMA/133
[    2.683613] ata1.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.685349] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[    2.685532] ata1.00: configured for UDMA/133
[    2.690022] scsi 0:0:0:0: Direct-Access     ATA      HGST HTS541010A9 A590 PQ: 0 ANSI: 5
[    2.690375] sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    2.690379] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    2.690408] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.690456] sd 0:0:0:0: [sda] Write Protect is off
[    2.690458] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.690488] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.730641]  sda: sda1 sda2 sda3 sda4
[    2.731047] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.738442] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
[    2.738446] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.738854] hub 1-1:1.0: USB hub found
[    2.738939] hub 1-1:1.0: 6 ports detected
[    2.906003] usb 3-3: new low-speed USB device number 2 using xhci_hcd
[    3.094979] usb 3-3: New USB device found, idVendor=045e, idProduct=077d
[    3.094986] usb 3-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    3.094989] usb 3-3: Product: Comfort Mouse 6000
[    3.094992] usb 3-3: Manufacturer: Microsoft
[    3.095107] usb 3-3: ep 0x83 - rounding interval to 64 microframes, ep desc says 80 microframes
[    3.097916] hidraw: raw HID events driver (C) Jiri Kosina
[    3.108699] usbcore: registered new interface driver usbhid
[    3.108701] usbhid: USB HID core driver
[    3.110040] input: Microsoft Comfort Mouse 6000 as /devices/pci0000:00/0000:00:14.0/usb3/3-3/3-3:1.0/0003:045E:077D.0001/input/input12
[    3.110155] hid-generic 0003:045E:077D.0001: input,hidraw0: USB HID v1.11 Mouse [Microsoft Comfort Mouse 6000] on usb-0000:00:14.0-3/input0
[    3.174097] tsc: Refined TSC clocksource calibration: 2594.106 MHz
[    3.206102] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    3.291857] psmouse serio4: synaptics: Touchpad model: 1, fw: 7.5, id: 0x1e0b1, caps: 0xf00173/0x640000/0xa2400, board id: 2654, fw id: 1323623
[    3.307845] EXT4-fs (sda3): mounting ext2 file system using the ext4 subsystem
[    3.319079] EXT4-fs (sda3): mounted filesystem without journal. Opts: (null)
[    3.337150] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input11
[    3.338583] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
[    3.338590] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    3.338873] hub 2-1:1.0: USB hub found
[    3.338945] hub 2-1:1.0: 6 ports detected
[    3.410375] usb 1-1.3: new high-speed USB device number 3 using ehci-pci
[    3.576331] usb 1-1.3: New USB device found, idVendor=05c8, idProduct=0359
[    3.576335] usb 1-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    3.576336] usb 1-1.3: Product: HP HD Webcam
[    3.576337] usb 1-1.3: Manufacturer: SunplusIT INC.
[    4.136323] random: nonblocking pool is initialized
[    4.174795] Switched to clocksource tsc
[    5.074469] init: plymouth-upstart-bridge main process (213) terminated with status 1
[    5.074481] init: plymouth-upstart-bridge main process ended, respawning
[    5.075860] init: plymouth-upstart-bridge main process (229) terminated with status 1
[    5.075872] init: plymouth-upstart-bridge main process ended, respawning
[    5.077229] init: plymouth-upstart-bridge main process (231) terminated with status 1
[    5.077240] init: plymouth-upstart-bridge main process ended, respawning
[    5.078494] init: plymouth-upstart-bridge main process (232) terminated with status 1
[    5.078506] init: plymouth-upstart-bridge main process ended, respawning
[    5.079838] init: plymouth-upstart-bridge main process (234) terminated with status 1
[    5.079850] init: plymouth-upstart-bridge main process ended, respawning
[    5.081094] init: plymouth-upstart-bridge main process (235) terminated with status 1
[    5.081106] init: plymouth-upstart-bridge main process ended, respawning
[    5.082445] init: plymouth-upstart-bridge main process (237) terminated with status 1
[    5.082456] init: plymouth-upstart-bridge main process ended, respawning
[    5.083727] init: plymouth-upstart-bridge main process (238) terminated with status 1
[    5.083740] init: plymouth-upstart-bridge main process ended, respawning
[    5.085032] init: plymouth-upstart-bridge main process (240) terminated with status 1
[    5.085043] init: plymouth-upstart-bridge main process ended, respawning
[    5.086247] init: plymouth-upstart-bridge main process (241) terminated with status 1
[    5.086258] init: plymouth-upstart-bridge main process ended, respawning
[    5.087572] init: plymouth-upstart-bridge main process (243) terminated with status 1
[    5.087583] init: plymouth-upstart-bridge respawning too fast, stopped
[    6.882213] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro
[   14.288692] systemd-udevd[434]: starting version 208
[   15.783456] lp: driver loaded but no devices found
[   15.819278] ppdev: user-space parallel port driver
[   17.168434] ACPI Warning: SystemIO range 0x0000000000000428-0x000000000000042f conflicts with OpRegion 0x0000000000000400-0x000000000000047f (\PMIO) (20140424/utaddress-258)
[   17.168442] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   17.168446] ACPI Warning: SystemIO range 0x0000000000000540-0x000000000000054f conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20140424/utaddress-258)
[   17.168449] ACPI Warning: SystemIO range 0x0000000000000540-0x000000000000054f conflicts with OpRegion 0x0000000000000500-0x000000000000055f (\_SB_.PCI0.PEGP.DGFX.GPIO) (20140424/utaddress-258)
[   17.168451] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   17.168452] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053f conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20140424/utaddress-258)
[   17.168454] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053f conflicts with OpRegion 0x0000000000000500-0x000000000000055f (\_SB_.PCI0.PEGP.DGFX.GPIO) (20140424/utaddress-258)
[   17.168456] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   17.168457] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052f conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20140424/utaddress-258)
[   17.168459] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052f conflicts with OpRegion 0x0000000000000500-0x000000000000055f (\_SB_.PCI0.PEGP.DGFX.GPIO) (20140424/utaddress-258)
[   17.168461] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   17.168462] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   17.214143] Initializing HPQ6001 module
[   17.214214] input: HP Wireless hotkeys as /devices/virtual/input/input13
[   17.215754] hp_accel: laptop model unknown, using default axes configuration
[   17.254912] wmi: Mapper loaded
[   17.258188] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   17.343121] lis3lv02d: 8 bits 3DC sensor found
[   17.441297] mei_me 0000:00:16.0: irq 48 for MSI/MSI-X
[   18.003539] [drm] Initialized drm 1.1.0 20060810
[   18.252157] input: HP WMI hotkeys as /devices/virtual/input/input14
[   18.569447] AVX version of gcm_enc/dec engaged.
[   18.659270] init: avahi-cups-reload main process (608) terminated with status 1
[   18.782712] cfg80211: Calling CRDA to update world regulatory domain
[   18.892474] input: ST LIS3LV02DL Accelerometer as /devices/platform/lis3lv02d/input/input15
[   18.943791] snd_hda_intel 0000:00:1b.0: irq 49 for MSI/MSI-X
[   19.094946] [drm] Memory usable by graphics device = 2048M
[   19.094951] checking generic (c0000000 410000) vs hw (c0000000 10000000)
[   19.094952] fb: switching to inteldrmfb from VESA VGA
[   19.094985] Console: switching to colour dummy device 80x25
[   19.095047] [drm] Replacing VGA console driver
[   19.116549] i915 0000:00:02.0: irq 50 for MSI/MSI-X
[   19.116559] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[   19.116560] [drm] Driver supports precise vblank timestamp query.
[   19.116647] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=none:owns=none
[   19.157804] fbcon: inteldrmfb (fb0) is primary device
[   19.157852] Console: switching to colour frame buffer device 170x48
[   19.157868] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   19.157869] i915 0000:00:02.0: registered panic notifier
[   19.164778] [Firmware Bug]: ACPI(DGFX) defines _DOD but not _DOS
[   19.172860] ACPI: Video Device [DGFX] (multi-head: yes  rom: no  post: no)
[   19.172900] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/LNXVIDEO:00/input/input16
[   19.173145] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   19.173224] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input17
[   19.173314] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   19.222461] audit: type=1400 audit(1443471085.386:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=532 comm="apparmor_parser"
[   19.222467] audit: type=1400 audit(1443471085.386:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=532 comm="apparmor_parser"
[   19.222471] audit: type=1400 audit(1443471085.386:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=532 comm="apparmor_parser"
[   19.222479] audit: type=1400 audit(1443471085.386:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=553 comm="apparmor_parser"
[   19.222485] audit: type=1400 audit(1443471085.386:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=553 comm="apparmor_parser"
[   19.222488] audit: type=1400 audit(1443471085.386:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=553 comm="apparmor_parser"
[   19.245058] audit: type=1400 audit(1443471085.410:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=585 comm="apparmor_parser"
[   19.245064] audit: type=1400 audit(1443471085.410:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=585 comm="apparmor_parser"
[   19.245067] audit: type=1400 audit(1443471085.410:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="third_party" pid=585 comm="apparmor_parser"
[   19.356749] [drm] radeon kernel modesetting enabled.
[   19.356762] VGA switcheroo: detected switching method \_SB_.PCI0.GFX0.ATPX handle
[   19.356810] radeon 0000:01:00.0: enabling device (0000 -> 0003)
[   19.356980] [drm] initializing kernel modesetting (OLAND 0x1002:0x6600 0x103C:0x194D).
[   19.356995] [drm] register mmio base: 0xD0900000
[   19.356996] [drm] register mmio size: 262144
[   19.356998] vga_switcheroo: enabled
[   19.357053] ATPX version 1, functions 0x00000003
[   19.404902] media: Linux media interface: v0.10
[   19.579708] sound hdaudioC0D0: autoconfig: line_outs=1 (0xd/0x0/0x0/0x0/0x0) type:speaker
[   19.579712] sound hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   19.579713] sound hdaudioC0D0:    hp_outs=1 (0xb/0x0/0x0/0x0/0x0)
[   19.579714] sound hdaudioC0D0:    mono: mono_out=0x0
[   19.579715] sound hdaudioC0D0:    inputs:
[   19.579717] sound hdaudioC0D0:      Internal Mic=0x11
[   19.579718] sound hdaudioC0D0:      Mic=0xc
[   19.683311] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input18
[   19.683378] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input19
[   19.683425] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input20
[   19.709363] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 3290, rev 0015 detected
[   19.717658] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 3290 detected
[   19.764087] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   19.819101] Linux video capture interface: v2.00
[   20.042681] intel_rapl: Found RAPL domain package
[   20.042685] intel_rapl: Found RAPL domain core
[   20.042686] intel_rapl: Found RAPL domain uncore
[   20.114969] uvcvideo: Found UVC 1.00 device HP HD Webcam (05c8:0359)
[   20.123666] input: HP HD Webcam as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.0/input/input21
[   20.123728] usbcore: registered new interface driver uvcvideo
[   20.123729] USB Video Class driver (1.1.1)
[   20.209742] cfg80211: World regulatory domain updated:
[   20.209745] cfg80211:  DFS Master region: unset
[   20.209746] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[   20.209747] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   20.209749] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   20.209750] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
[   20.209751] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   20.209752] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   20.472799] Bluetooth: Core ver 2.19
[   20.472817] NET: Registered protocol family 31
[   20.472818] Bluetooth: HCI device and connection manager initialized
[   20.472825] Bluetooth: HCI socket layer initialized
[   20.472828] Bluetooth: L2CAP socket layer initialized
[   20.472839] Bluetooth: SCO socket layer initialized
[   20.568346] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   20.568357] Bluetooth: BNEP filters: protocol multicast
[   20.568364] Bluetooth: BNEP socket layer initialized
[   20.572022] Bluetooth: RFCOMM TTY layer initialized
[   20.572029] Bluetooth: RFCOMM socket layer initialized
[   20.572034] Bluetooth: RFCOMM ver 1.11
[   20.854035] [drm] Enabling RC6 states: RC6 on, RC6p on, RC6pp off
[   20.950202] init: failsafe main process (680) killed by TERM signal
[   21.678569] ATOM BIOS: HP
[   21.678582] [drm] GPU not posted. posting now...
[   21.681912] radeon 0000:01:00.0: VRAM: 2048M 0x0000000000000000 - 0x000000007FFFFFFF (2048M used)
[   21.681914] radeon 0000:01:00.0: GTT: 1024M 0x0000000080000000 - 0x00000000BFFFFFFF
[   21.681915] [drm] Detected VRAM RAM=2048M, BAR=256M
[   21.681916] [drm] RAM width 128bits DDR
[   21.681987] [TTM] Zone  kernel: Available graphics memory: 4011628 kiB
[   21.681989] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB
[   21.681998] [TTM] Initializing pool allocator
[   21.682003] [TTM] Initializing DMA pool allocator
[   21.682018] [drm] radeon: 2048M of VRAM memory ready
[   21.682019] [drm] radeon: 1024M of GTT memory ready.
[   21.682030] [drm] Loading OLAND Microcode
[   22.433468] [drm] radeon/OLAND_mc2.bin: 31452 bytes
[   22.539958] [drm] Internal thermal controller without fan control
[   22.540051] [drm] probing gen 2 caps for device 8086:151 = 261ad03/e
[   22.545503] [drm] radeon: dpm initialized
[   22.656129] [drm] GART: num cpu pages 262144, num gpu pages 262144
[   22.656695] [drm] probing gen 2 caps for device 8086:151 = 261ad03/e
[   22.656698] [drm] PCIE gen 3 link speeds already enabled
[   22.658611] [drm] PCIE GART of 1024M enabled (table at 0x0000000000276000).
[   22.658705] radeon 0000:01:00.0: WB enabled
[   22.658708] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000080000c00 and cpu addr 0xffff8802414a6c00
[   22.658710] radeon 0000:01:00.0: fence driver on ring 1 use gpu addr 0x0000000080000c04 and cpu addr 0xffff8802414a6c04
[   22.658711] radeon 0000:01:00.0: fence driver on ring 2 use gpu addr 0x0000000080000c08 and cpu addr 0xffff8802414a6c08
[   22.658712] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000080000c0c and cpu addr 0xffff8802414a6c0c
[   22.658713] radeon 0000:01:00.0: fence driver on ring 4 use gpu addr 0x0000000080000c10 and cpu addr 0xffff8802414a6c10
[   22.659158] radeon 0000:01:00.0: fence driver on ring 5 use gpu addr 0x0000000000075a18 and cpu addr 0xffffc90011735a18
[   22.659168] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[   22.659169] [drm] Driver supports precise vblank timestamp query.
[   22.659171] radeon 0000:01:00.0: radeon: MSI limited to 32-bit
[   22.659195] radeon 0000:01:00.0: irq 51 for MSI/MSI-X
[   22.659207] radeon 0000:01:00.0: radeon: using MSI.
[   22.659234] [drm] radeon: irq initialized.
[   22.795257] [drm] ring test on 0 succeeded in 2 usecs
[   22.795262] [drm] ring test on 1 succeeded in 1 usecs
[   22.795265] [drm] ring test on 2 succeeded in 1 usecs
[   22.795271] [drm] ring test on 3 succeeded in 3 usecs
[   22.795276] [drm] ring test on 4 succeeded in 3 usecs
[   22.980989] [drm] ring test on 5 succeeded in 2 usecs
[   22.980996] [drm] UVD initialized successfully.
[   22.981162] [drm] ib test on ring 0 succeeded in 0 usecs
[   22.981194] [drm] ib test on ring 1 succeeded in 0 usecs
[   22.981222] [drm] ib test on ring 2 succeeded in 0 usecs
[   22.981238] [drm] ib test on ring 3 succeeded in 0 usecs
[   22.981254] [drm] ib test on ring 4 succeeded in 0 usecs
[   23.066699] audit: type=1400 audit(1443471089.226:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=905 comm="apparmor_parser"
[   23.131843] [drm] ib test on ring 5 succeeded
[   23.135165] [drm] Radeon Display Connectors
[   23.145328] radeon 0000:01:00.0: No connectors reported connected with modes
[   23.145331] [drm] Cannot find any crtc or sizes - going 1024x768
[   23.145891] [drm] fb mappable at 0xB0478000
[   23.145891] [drm] vram apper at 0xB0000000
[   23.145892] [drm] size 3145728
[   23.145893] [drm] fb depth is 24
[   23.145893] [drm]    pitch is 4096
[   23.146010] radeon 0000:01:00.0: fb1: radeondrmfb frame buffer device
[   23.146097] [drm] Initialized radeon 2.39.0 20080528 for 0000:01:00.0 on minor 1
[   24.349470] audit_printk_skb: 60 callbacks suppressed
[   24.349473] audit: type=1400 audit(1443471090.510:32): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/mysqld" pid=905 comm="apparmor_parser"
[   24.668907] audit: type=1400 audit(1443471090.830:33): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/tcpdump" pid=905 comm="apparmor_parser"
[   24.685904] audit: type=1400 audit(1443471090.846:34): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cups-browsed" pid=951 comm="apparmor_parser"
[   25.601227] systemd-logind[1038]: New seat seat0.
[   25.618824] systemd-logind[1038]: Watching system buttons on /dev/input/event2 (Power Button)
[   25.618870] systemd-logind[1038]: Watching system buttons on /dev/input/event10 (Video Bus)
[   25.618911] systemd-logind[1038]: Watching system buttons on /dev/input/event9 (Video Bus)
[   25.618949] systemd-logind[1038]: Watching system buttons on /dev/input/event1 (Lid Switch)
[   25.618986] systemd-logind[1038]: Watching system buttons on /dev/input/event0 (Sleep Button)
[   25.709417] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt3290.bin'
[   25.862837] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.37
[   25.985315] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   26.238355] audit: type=1400 audit(1443471092.398:35): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/mysqld" pid=1193 comm="apparmor_parser"
[   26.331359] r8169 0000:05:00.0 eth0: link down
[   26.331396] r8169 0000:05:00.0 eth0: link down
[   26.331408] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   26.618850] init: Failed to spawn mysql main process: unable to execute: No such file or directory
[   29.358264] r8169 0000:05:00.0 eth0: link up
[   29.358277] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   30.206446] Non-volatile memory driver v1.3
[   39.490428] [drm] probing gen 2 caps for device 8086:151 = 261ad03/e
[   39.490433] [drm] PCIE gen 3 link speeds already enabled
[   39.492971] [drm] PCIE GART of 1024M enabled (table at 0x0000000000276000).
[   39.493054] radeon 0000:01:00.0: WB enabled
[   39.493056] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000080000c00 and cpu addr 0xffff8802414a6c00
[   39.493057] radeon 0000:01:00.0: fence driver on ring 1 use gpu addr 0x0000000080000c04 and cpu addr 0xffff8802414a6c04
[   39.493059] radeon 0000:01:00.0: fence driver on ring 2 use gpu addr 0x0000000080000c08 and cpu addr 0xffff8802414a6c08
[   39.493060] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000080000c0c and cpu addr 0xffff8802414a6c0c
[   39.493061] radeon 0000:01:00.0: fence driver on ring 4 use gpu addr 0x0000000080000c10 and cpu addr 0xffff8802414a6c10
[   39.493470] radeon 0000:01:00.0: fence driver on ring 5 use gpu addr 0x0000000000075a18 and cpu addr 0xffffc90011735a18
[   39.630098] [drm] ring test on 0 succeeded in 2 usecs
[   39.630103] [drm] ring test on 1 succeeded in 1 usecs
[   39.630106] [drm] ring test on 2 succeeded in 1 usecs
[   39.630112] [drm] ring test on 3 succeeded in 3 usecs
[   39.630117] [drm] ring test on 4 succeeded in 3 usecs
[   39.815816] [drm] ring test on 5 succeeded in 2 usecs
[   39.815822] [drm] UVD initialized successfully.
[   39.815847] [drm] ib test on ring 0 succeeded in 0 usecs
[   39.815870] [drm] ib test on ring 1 succeeded in 0 usecs
[   39.815900] [drm] ib test on ring 2 succeeded in 0 usecs
[   39.815918] [drm] ib test on ring 3 succeeded in 0 usecs
[   39.815933] [drm] ib test on ring 4 succeeded in 0 usecs
[   39.966541] [drm] ib test on ring 5 succeeded
[   40.257734] [drm:cpt_set_fifo_underrun_reporting] *ERROR* uncleared pch fifo underrun on pch transcoder A
[   40.257744] [drm:cpt_serr_int_handler] *ERROR* PCH transcoder A FIFO underrun
[   50.853943] systemd-logind[1038]: Failed to start unit user@112.service: Unknown unit: user@112.service
[   50.853949] systemd-logind[1038]: Failed to start user service: Unknown unit: user@112.service
[   50.856996] systemd-logind[1038]: New session c1 of user lightdm.
[   50.857017] systemd-logind[1038]: Linked /tmp/.X11-unix/X0 to /run/user/112/X11-display.
[   65.205625] systemd-logind[1038]: Failed to start unit user@1000.service: Unknown unit: user@1000.service
[   65.205631] systemd-logind[1038]: Failed to start user service: Unknown unit: user@1000.service
[   65.208935] systemd-logind[1038]: New session c2 of user tom.
[   65.208951] systemd-logind[1038]: Linked /tmp/.X11-unix/X0 to /run/user/1000/X11-display.
[   86.280351] init: bootchart post-stop process (2591) terminated with status 1

```

Thank you very much.

---

### Post by TheFu on 2015-09-28
Support for 14.10 ended in June. [https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS) explains.

Either run 14.04 (5 yrs of support) or run 15.04 until January when that support ends. In a few weeks, 15.10 will be released with support until June.

If you cannot reload an OS every 6 months, please run an LTS release.

---

