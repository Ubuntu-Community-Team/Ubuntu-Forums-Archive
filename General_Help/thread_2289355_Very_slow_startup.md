---
title: "Very slow startup"
date: 2015-08-03
forum: General Help
---

### Post by matek2305 on 2015-08-03
Hey, I just installed Ubuntu MATE 15.04 on my HP notebook and everything is running great but startup time. It takes several minutes to get into desktop. I had ubuntu 14.04 lts before and there was no problem with that. Here is output from dmesg command:

```
[COLOR=#000000][    0.000000] CPU0 microcode updated early to revision 0x1c, date = 2014-07-03[/COLOR][    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.19.0-15-generic (buildd@komainu) (gcc version 4.9.2 (Ubuntu 4.9.2-10ubuntu13) ) #15-Ubuntu SMP Thu Apr 16 23:32:37 UTC 2015 (Ubuntu 3.19.0-15.15-generic 3.19.3)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.19.0-15-generic root=UUID=51885ac5-af27-4d13-b5bd-9eb591337c94 ro persistent quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009dbff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009dc00-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x0000000053b7efff] usable
[    0.000000] BIOS-e820: [mem 0x0000000053b7f000-0x0000000054e7efff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000054e7f000-0x0000000054f7efff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x0000000054f7f000-0x0000000054ffefff] ACPI data
[    0.000000] BIOS-e820: [mem 0x0000000054fff000-0x0000000054ffffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000055000000-0x000000005fffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed10000-0x00000000fed13fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed18000-0x00000000fed19fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff800000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000049dffffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.7 present.
[    0.000000] DMI: Hewlett-Packard HP ZBook 15/1909, BIOS L70 Ver. 01.06 10/25/2013
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] AGP: No AGP bridge found
[    0.000000] e820: last_pfn = 0x49e000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 00FF800000 mask 7FFF800000 write-protect
[    0.000000]   1 base 0000000000 mask 7FC0000000 write-back
[    0.000000]   2 base 0040000000 mask 7FE0000000 write-back
[    0.000000]   3 base 0100000000 mask 7F00000000 write-back
[    0.000000]   4 base 0200000000 mask 7E00000000 write-back
[    0.000000]   5 base 0400000000 mask 7F80000000 write-back
[    0.000000]   6 base 0480000000 mask 7FE0000000 write-back
[    0.000000]   7 base 049E000000 mask 7FFE000000 uncachable
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] PAT configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- UC  
[    0.000000] e820: last_pfn = 0x55000 max_arch_pfn = 0x400000000
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000097000] 97000 size 24576
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01fe5000, 0x01fe5fff] PGTABLE
[    0.000000] BRK [0x01fe6000, 0x01fe6fff] PGTABLE
[    0.000000] BRK [0x01fe7000, 0x01fe7fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x49de00000-0x49dffffff]
[    0.000000]  [mem 0x49de00000-0x49dffffff] page 2M
[    0.000000] BRK [0x01fe8000, 0x01fe8fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x480000000-0x49ddfffff]
[    0.000000]  [mem 0x480000000-0x49ddfffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x460000000-0x47fffffff]
[    0.000000]  [mem 0x460000000-0x47fffffff] page 1G
[    0.000000] init_memory_mapping: [mem 0x00100000-0x53b7efff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x539fffff] page 2M
[    0.000000]  [mem 0x53a00000-0x53b7efff] page 4k
[    0.000000] init_memory_mapping: [mem 0x54fff000-0x54ffffff]
[    0.000000]  [mem 0x54fff000-0x54ffffff] page 4k
[    0.000000] BRK [0x01fe9000, 0x01fe9fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x100000000-0x45fffffff]
[    0.000000]  [mem 0x100000000-0x45fffffff] page 1G
[    0.000000] RAMDISK: [mem 0x346de000-0x36366fff]
[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x00000000000F2FE0 000024 (v02 HPQOEM)
[    0.000000] ACPI: XSDT 0x0000000054FFE120 0000B4 (v01 HPQOEM SLIC-MPC 00000001      01000013)
[    0.000000] ACPI: FACP 0x0000000054FFC000 00010C (v05 HPQOEM 1909     00000001 HP   00000001)
[    0.000000] ACPI: DSDT 0x0000000054FD2000 024472 (v02 HPQOEM 1909     00000001 INTL 20110112)
[    0.000000] ACPI: FACS 0x0000000054E31000 000040
[    0.000000] ACPI: HPET 0x0000000054FFB000 000038 (v01 HPQOEM 1909     00000001 HP   00000001)
[    0.000000] ACPI: APIC 0x0000000054FFA000 0000BC (v01 HPQOEM 1909     00000001 HP   00000001)
[    0.000000] ACPI: MCFG 0x0000000054FF9000 00003C (v01 HPQOEM 1909     00000001 HP   00000001)
[    0.000000] ACPI: TCPA 0x0000000054FF7000 000032 (v02 HPQOEM 1909     00000000 HP   00000001)
[    0.000000] ACPI: SSDT 0x0000000054FCF000 00045D (v01 HPQOEM SataAhci 00001000 INTL 20110112)
[    0.000000] ACPI: SSDT 0x0000000054FCE000 00048A (v01 HPQOEM PtidDevc 00001000 INTL 20110112)
[    0.000000] ACPI: SLIC 0x0000000054FCD000 000176 (v01 HPQOEM SLIC-MPC 00000001 HP   00000001)
[    0.000000] ACPI: MSDM 0x0000000054FCC000 000055 (v03 HPQOEM SLIC-MPC 00000000 HP   00000001)
[    0.000000] ACPI: FPDT 0x0000000054FCB000 000044 (v01 HPQOEM 1909     00000001 HP   00000001)
[    0.000000] ACPI: BGRT 0x0000000054FCA000 000038 (v00 HPQOEM 1909     00000001 HP   00000001)
[    0.000000] ACPI: SSDT 0x0000000054FC7000 001A19 (v01 HPQOEM NVIDIAGF 00000001 INTL 20110112)
[    0.000000] ACPI: SSDT 0x0000000054FC4000 000544 (v01 PmRef  Cpu0Ist  00003000 INTL 20110112)
[    0.000000] ACPI: SSDT 0x0000000054FC3000 000AF3 (v01 PmRef  CpuPm    00003000 INTL 20110112)
[    0.000000] ACPI: SSDT 0x0000000054FC2000 0001D5 (v01 PmRef  LakeTiny 00003000 INTL 20110112)
[    0.000000] ACPI: SSDT 0x0000000054FC1000 0005B6 (v01 SaSsdt SaSsdt   00003000 INTL 20110112)
[    0.000000] ACPI: ASF! 0x0000000054FF8000 0000A5 (v32 HPQOEM 1909     00000001 HP   00000001)
[    0.000000] ACPI: DMAR 0x0000000054FC0000 000080 (v01 INTEL  HSW      00000001 INTL 00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000049dffffff]
[    0.000000] NODE_DATA(0) allocated [mem 0x49dff9000-0x49dffdfff]
[    0.000000]  [ffffea0000000000-ffffea00127fffff] PMD -> [ffff88048d800000-ffff88049d5fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x49dffffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009cfff]
[    0.000000]   node   0: [mem 0x00100000-0x53b7efff]
[    0.000000]   node   0: [mem 0x54fff000-0x54ffffff]
[    0.000000]   node   0: [mem 0x100000000-0x49dffffff]
[    0.000000] Initmem setup node 0 [mem 0x00001000-0x49dffffff]
[    0.000000] On node 0 totalpages: 4135708
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3996 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 5294 pages used for memmap
[    0.000000]   DMA32 zone: 338816 pages, LIFO batch:31
[    0.000000]   Normal zone: 59264 pages used for memmap
[    0.000000]   Normal zone: 3792896 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x1808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x07] enabled)
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
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] smpboot: Allowing 8 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009d000-0x0009dfff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x53b7f000-0x54e7efff]
[    0.000000] PM: Registered nosave memory: [mem 0x54e7f000-0x54f7efff]
[    0.000000] PM: Registered nosave memory: [mem 0x54f7f000-0x54ffefff]
[    0.000000] PM: Registered nosave memory: [mem 0x55000000-0x5fffffff]
[    0.000000] PM: Registered nosave memory: [mem 0x60000000-0xdfffffff]
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
[    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xff7fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xff800000-0xffffffff]
[    0.000000] e820: [mem 0x60000000-0xdfffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 31 pages/cpu @ffff88049dc00000 s87040 r8192 d31744 u262144
[    0.000000] pcpu-alloc: s87040 r8192 d31744 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 4071065
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.19.0-15-generic root=UUID=51885ac5-af27-4d13-b5bd-9eb591337c94 ro persistent quiet splash
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave: enabled xstate_bv 0x7, cntxt size 0x340 using standard form
[    0.000000] AGP: Checking aperture...
[    0.000000] AGP: No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 16169808K/16542832K available (7993K kernel code, 1232K rwdata, 3752K rodata, 1408K init, 1300K bss, 373024K reserved, 0K cma-reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=16, nr_cpu_ids=8
[    0.000000] NR_IRQS:16640 nr_irqs:488 16
[    0.000000]     Offload RCU callbacks from all CPUs
[    0.000000]     Offload RCU callbacks from CPUs: 0-7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 2693.598 MHz processor
[    0.000025] Calibrating delay loop (skipped), value calculated using timer frequency.. 5387.19 BogoMIPS (lpj=10774392)
[    0.000028] pid_max: default: 32768 minimum: 301
[    0.000033] ACPI: Core revision 20141107
[    0.012545] ACPI: All ACPI Tables successfully acquired
[    0.012836] Security Framework initialized
[    0.012850] AppArmor: AppArmor initialized
[    0.012851] Yama: becoming mindful.
[    0.013684] Dentry cache hash table entries: 2097152 (order: 12, 16777216 bytes)
[    0.016309] Inode-cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.017425] Mount-cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.017440] Mountpoint-cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.017640] Initializing cgroup subsys memory
[    0.017645] Initializing cgroup subsys devices
[    0.017647] Initializing cgroup subsys freezer
[    0.017648] Initializing cgroup subsys net_cls
[    0.017650] Initializing cgroup subsys blkio
[    0.017651] Initializing cgroup subsys perf_event
[    0.017653] Initializing cgroup subsys net_prio
[    0.017655] Initializing cgroup subsys hugetlb
[    0.017674] CPU: Physical Processor ID: 0
[    0.017675] CPU: Processor Core ID: 0
[    0.017679] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.018521] mce: CPU supports 9 MCE banks
[    0.018533] CPU0: Thermal monitoring enabled (TM1)
[    0.018545] Last level iTLB entries: 4KB 1024, 2MB 1024, 4MB 1024
Last level dTLB entries: 4KB 1024, 2MB 1024, 4MB 1024, 1GB 4
[    0.018638] Freeing SMP alternatives memory: 32K (ffffffff81e96000 - ffffffff81e9e000)
[    0.019582] ftrace: allocating 30078 entries in 118 pages
[    0.030265] dmar: Host address width 39
[    0.030267] dmar: DRHD base: 0x000000fed90000 flags: 0x1
[    0.030271] dmar: IOMMU 0: reg_base_addr fed90000 ver 1:0 cap d2008c20660462 ecap f010da
[    0.030272] dmar: RMRR base: 0x00000054d18000 end: 0x00000054d37fff
[    0.030338] IOAPIC id 0 under DRHD base  0xfed90000 IOMMU 0
[    0.030338] HPET id 0 under DRHD base 0xfed90000
[    0.030339] Queued invalidation will be enabled to support x2apic and Intr-remapping.
[    0.030406] Enabled IRQ remapping in x2apic mode
[    0.030407] Enabling x2apic
[    0.030408] Enabled x2apic
[    0.030413] Switched APIC routing to cluster x2apic.
[    0.030840] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.070508] smpboot: CPU0: Intel(R) Core(TM) i7-4800MQ CPU @ 2.70GHz (fam: 06, model: 3c, stepping: 03)
[    0.070514] TSC deadline timer enabled
[    0.070535] Performance Events: PEBS fmt2+, 16-deep LBR, Haswell events, full-width counters, Intel PMU driver.
[    0.070553] ... version:                3
[    0.070554] ... bit width:              48
[    0.070555] ... generic registers:      4
[    0.070556] ... value mask:             0000ffffffffffff
[    0.070556] ... max period:             0000ffffffffffff
[    0.070557] ... fixed-purpose events:   3
[    0.070558] ... event mask:             000000070000000f
[    0.071254] x86: Booting SMP configuration:
[    0.071256] .... node  #0, CPUs:      #1
[    0.085149] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.085231]  #2
[    0.097165] CPU2 microcode updated early to revision 0x1c, date = 2014-07-03
[    0.100226]  #3
[    0.114225]  #4
[    0.126158] CPU4 microcode updated early to revision 0x1c, date = 2014-07-03
[    0.129220]  #5
[    0.143218]  #6
[    0.155156] CPU6 microcode updated early to revision 0x1c, date = 2014-07-03
[    0.158209]  #7
[    0.172142] x86: Booted up 1 node, 8 CPUs
[    0.172144] smpboot: Total of 8 processors activated (43097.56 BogoMIPS)
[    0.179132] devtmpfs: initialized
[    0.181516] evm: security.selinux
[    0.181517] evm: security.SMACK64
[    0.181518] evm: security.SMACK64EXEC
[    0.181518] evm: security.SMACK64TRANSMUTE
[    0.181519] evm: security.SMACK64MMAP
[    0.181520] evm: security.ima
[    0.181520] evm: security.capability
[    0.181563] PM: Registering ACPI NVS region [mem 0x54e7f000-0x54f7efff] (1048576 bytes)
[    0.181721] pinctrl core: initialized pinctrl subsystem
[    0.181807] RTC time:  5:43:12, date: 08/03/15
[    0.181900] NET: Registered protocol family 16
[    0.182978] cpuidle: using governor ladder
[    0.186978] cpuidle: using governor menu
[    0.187019] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.187021] ACPI: bus type PCI registered
[    0.187022] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.187086] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.187088] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.187341] PCI: Using configuration type 1 for base access
[    0.187653] mtrr: your CPUs had inconsistent variable MTRR settings
[    0.187654] mtrr: probably your BIOS does not setup all CPUs.
[    0.187655] mtrr: corrected configuration.
[    0.191318] ACPI: Added _OSI(Module Device)
[    0.191320] ACPI: Added _OSI(Processor Device)
[    0.191321] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.191321] ACPI: Added _OSI(Processor Aggregator Device)
[    0.199521] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.201529] ACPI: Dynamic OEM Table Load:
[    0.201537] ACPI: SSDT 0xFFFF88048B08C400 0003F3 (v01 PmRef  Cpu0Cst  00003001 INTL 20110112)
[    0.202126] ACPI: Dynamic OEM Table Load:
[    0.202132] ACPI: SSDT 0xFFFF88048B053800 0005DB (v01 PmRef  ApIst    00003000 INTL 20110112)
[    0.202747] ACPI: Dynamic OEM Table Load:
[    0.202752] ACPI: SSDT 0xFFFF88048B1EC200 000119 (v01 PmRef  ApCst    00003000 INTL 20110112)
[    2.213184] ACPI: Interpreter enabled
[    2.213191] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20141107/hwxface-580)
[    2.213196] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20141107/hwxface-580)
[    2.213208] ACPI: (supports S0 S3 S4 S5)
[    2.213210] ACPI: Using IOAPIC for interrupt routing
[    2.213225] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    2.214835] ACPI: Power Resource [APPR] (off)
[    2.216769] ACPI: Power Resource [COMP] (on)
[    2.217004] ACPI: Power Resource [LPP] (on)
[    2.219643] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[    2.219648] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    2.220278] acpi PNP0A08:00: _OSC: platform does not support [PCIeHotplug PME]
[    2.221123] acpi PNP0A08:00: _OSC: OS now controls [AER PCIeCapability]
[    2.221663] PCI host bridge to bus 0000:00
[    2.221666] pci_bus 0000:00: root bus resource [bus 00-fe]
[    2.221667] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    2.221669] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    2.221670] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    2.221671] pci_bus 0000:00: root bus resource [mem 0x60000000-0xdfffffff]
[    2.221673] pci_bus 0000:00: root bus resource [mem 0xf0000000-0xfedfffff]
[    2.221674] pci_bus 0000:00: root bus resource [mem 0xfee01000-0xffffffff]
[    2.221680] pci 0000:00:00.0: [8086:0c04] type 00 class 0x060000
[    2.221769] pci 0000:00:01.0: [8086:0c01] type 01 class 0x060400
[    2.221804] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    2.221894] pci 0000:00:14.0: [8086:8c31] type 00 class 0x0c0330
[    2.221911] pci 0000:00:14.0: reg 0x10: [mem 0xd0320000-0xd032ffff 64bit]
[    2.221964] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    2.222009] pci 0000:00:14.0: System wakeup disabled by ACPI
[    2.222040] pci 0000:00:16.0: [8086:8c3a] type 00 class 0x078000
[    2.222058] pci 0000:00:16.0: reg 0x10: [mem 0xd0335000-0xd033500f 64bit]
[    2.222120] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    2.222191] pci 0000:00:16.3: [8086:8c3d] type 00 class 0x070002
[    2.222205] pci 0000:00:16.3: reg 0x10: [io  0x6070-0x6077]
[    2.222213] pci 0000:00:16.3: reg 0x14: [mem 0xd033c000-0xd033cfff]
[    2.222343] pci 0000:00:19.0: [8086:153a] type 00 class 0x020000
[    2.222358] pci 0000:00:19.0: reg 0x10: [mem 0xd0300000-0xd031ffff]
[    2.222365] pci 0000:00:19.0: reg 0x14: [mem 0xd033b000-0xd033bfff]
[    2.222373] pci 0000:00:19.0: reg 0x18: [io  0x6040-0x605f]
[    2.222433] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    2.222478] pci 0000:00:19.0: System wakeup disabled by ACPI
[    2.222511] pci 0000:00:1a.0: [8086:8c2d] type 00 class 0x0c0320
[    2.222529] pci 0000:00:1a.0: reg 0x10: [mem 0xd033a000-0xd033a3ff]
[    2.222617] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    2.222664] pci 0000:00:1a.0: System wakeup disabled by ACPI
[    2.222696] pci 0000:00:1b.0: [8086:8c20] type 00 class 0x040300
[    2.222710] pci 0000:00:1b.0: reg 0x10: [mem 0xd0330000-0xd0333fff 64bit]
[    2.222778] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    2.222851] pci 0000:00:1c.0: [8086:8c10] type 01 class 0x060400
[    2.222927] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    2.223004] pci 0000:00:1c.4: [8086:8c18] type 01 class 0x060400
[    2.223073] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    2.223120] pci 0000:00:1c.4: System wakeup disabled by ACPI
[    2.223148] pci 0000:00:1c.6: [8086:8c1c] type 01 class 0x060400
[    2.223218] pci 0000:00:1c.6: PME# supported from D0 D3hot D3cold
[    2.223265] pci 0000:00:1c.6: System wakeup disabled by ACPI
[    2.223291] pci 0000:00:1c.7: [8086:8c1e] type 01 class 0x060400
[    2.223361] pci 0000:00:1c.7: PME# supported from D0 D3hot D3cold
[    2.223413] pci 0000:00:1c.7: System wakeup disabled by ACPI
[    2.223446] pci 0000:00:1d.0: [8086:8c26] type 00 class 0x0c0320
[    2.223464] pci 0000:00:1d.0: reg 0x10: [mem 0xd0339000-0xd03393ff]
[    2.223553] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    2.223600] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    2.223630] pci 0000:00:1f.0: [8086:8c4f] type 00 class 0x060100
[    2.223798] pci 0000:00:1f.2: [8086:8c03] type 00 class 0x010601
[    2.223812] pci 0000:00:1f.2: reg 0x10: [io  0x6068-0x606f]
[    2.223819] pci 0000:00:1f.2: reg 0x14: [io  0x607c-0x607f]
[    2.223826] pci 0000:00:1f.2: reg 0x18: [io  0x6060-0x6067]
[    2.223833] pci 0000:00:1f.2: reg 0x1c: [io  0x6078-0x607b]
[    2.223840] pci 0000:00:1f.2: reg 0x20: [io  0x6020-0x603f]
[    2.223847] pci 0000:00:1f.2: reg 0x24: [mem 0xd0338000-0xd03387ff]
[    2.223886] pci 0000:00:1f.2: PME# supported from D3hot
[    2.223953] pci 0000:00:1f.3: [8086:8c22] type 00 class 0x0c0500
[    2.223967] pci 0000:00:1f.3: reg 0x10: [mem 0xd0334000-0xd03340ff 64bit]
[    2.223985] pci 0000:00:1f.3: reg 0x20: [io  0xef80-0xef9f]
[    2.224108] pci 0000:01:00.0: [10de:11fc] type 00 class 0x030000
[    2.224120] pci 0000:01:00.0: reg 0x10: [mem 0xcf000000-0xcfffffff]
[    2.224130] pci 0000:01:00.0: reg 0x14: [mem 0x70000000-0x7fffffff 64bit pref]
[    2.224140] pci 0000:01:00.0: reg 0x1c: [mem 0x80000000-0x81ffffff 64bit pref]
[    2.224147] pci 0000:01:00.0: reg 0x24: [io  0x5000-0x507f]
[    2.224154] pci 0000:01:00.0: reg 0x30: [mem 0xfff80000-0xffffffff pref]
[    2.224241] pci 0000:01:00.1: [10de:0e0b] type 00 class 0x040300
[    2.224252] pci 0000:01:00.1: reg 0x10: [mem 0xd0000000-0xd0003fff]
[    2.231387] pci 0000:00:01.0: PCI bridge to [bus 01]
[    2.231389] pci 0000:00:01.0:   bridge window [io  0x5000-0x5fff]
[    2.231391] pci 0000:00:01.0:   bridge window [mem 0xcf000000-0xd00fffff]
[    2.231394] pci 0000:00:01.0:   bridge window [mem 0x70000000-0x81ffffff 64bit pref]
[    2.231455] acpiphp: Slot [1] registered
[    2.231461] pci 0000:00:1c.0: PCI bridge to [bus 02-3a]
[    2.231466] pci 0000:00:1c.0:   bridge window [mem 0xb8000000-0xce0fffff]
[    2.231471] pci 0000:00:1c.0:   bridge window [mem 0x90000000-0xb1ffffff 64bit pref]
[    2.231533] acpiphp: Slot [1-1] registered
[    2.231557] pci 0000:00:1c.4: PCI bridge to [bus 3b-5b]
[    2.231561] pci 0000:00:1c.4:   bridge window [io  0x3000-0x4fff]
[    2.231564] pci 0000:00:1c.4:   bridge window [mem 0xb4000000-0xb7ffffff]
[    2.231656] pci 0000:5c:00.0: [8086:08b1] type 00 class 0x028000
[    2.231709] pci 0000:5c:00.0: reg 0x10: [mem 0xd0200000-0xd0201fff 64bit]
[    2.231966] pci 0000:5c:00.0: PME# supported from D0 D3hot D3cold
[    2.239402] pci 0000:00:1c.6: PCI bridge to [bus 5c]
[    2.239407] pci 0000:00:1c.6:   bridge window [mem 0xd0200000-0xd02fffff]
[    2.239527] pci 0000:5d:00.0: [10ec:5249] type 00 class 0xff0000
[    2.239556] pci 0000:5d:00.0: reg 0x10: [mem 0xd0100000-0xd0100fff]
[    2.239903] pci 0000:5d:00.0: supports D1 D2
[    2.239904] pci 0000:5d:00.0: PME# supported from D1 D2 D3hot D3cold
[    2.247411] pci 0000:00:1c.7: PCI bridge to [bus 5d]
[    2.247415] pci 0000:00:1c.7:   bridge window [mem 0xd0100000-0xd01fffff]
[    2.247458] acpi PNP0A08:00: Disabling ASPM (FADT indicates it is unsupported)
[    2.248286] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 *10 11 12 14 15)
[    2.248320] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 *10 11 12 14 15)
[    2.248352] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 *10 11 12 14 15)
[    2.248385] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 10 *11 12 14 15)
[    2.248418] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 10 11 12 14 15)
[    2.248450] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    2.248482] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 *10 11 12 14 15)
[    2.248513] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    2.248734] ACPI: Enabled 6 GPEs in block 00 to 3F
[    2.248897] ACPI : EC: GPE = 0x16, I/O: command/status = 0x66, data = 0x62
[    2.248966] vgaarb: setting as boot device: PCI:0000:01:00.0
[    2.248968] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    2.248969] vgaarb: loaded
[    2.248970] vgaarb: bridge control possible 0000:01:00.0
[    2.249149] SCSI subsystem initialized
[    2.249188] libata version 3.00 loaded.
[    2.249209] ACPI: bus type USB registered
[    2.249222] usbcore: registered new interface driver usbfs
[    2.249228] usbcore: registered new interface driver hub
[    2.249247] usbcore: registered new device driver usb
[    2.249351] PCI: Using ACPI for IRQ routing
[    2.254836] PCI: pci_cache_line_size set to 64 bytes
[    2.254882] e820: reserve RAM buffer [mem 0x0009dc00-0x0009ffff]
[    2.254883] e820: reserve RAM buffer [mem 0x53b7f000-0x53ffffff]
[    2.254884] e820: reserve RAM buffer [mem 0x55000000-0x57ffffff]
[    2.254885] e820: reserve RAM buffer [mem 0x49e000000-0x49fffffff]
[    2.254975] NetLabel: Initializing
[    2.254976] NetLabel:  domain hash size = 128
[    2.254976] NetLabel:  protocols = UNLABELED CIPSOv4
[    2.254985] NetLabel:  unlabeled traffic allowed by default
[    2.255033] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    2.255037] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    2.257072] Switched to clocksource hpet
[    2.261720] AppArmor: AppArmor Filesystem Enabled
[    2.261772] pnp: PnP ACPI init
[    2.261926] system 00:00: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    2.261928] system 00:00: [mem 0xfed10000-0xfed17fff] could not be reserved
[    2.261929] system 00:00: [mem 0xfed18000-0xfed18fff] has been reserved
[    2.261931] system 00:00: [mem 0xfed19000-0xfed19fff] has been reserved
[    2.261932] system 00:00: [mem 0xe0000000-0xefffffff] has been reserved
[    2.261933] system 00:00: [mem 0xfed20000-0xfed3ffff] has been reserved
[    2.261935] system 00:00: [mem 0xfed90000-0xfed93fff] could not be reserved
[    2.261936] system 00:00: [mem 0xfed45000-0xfed8ffff] has been reserved
[    2.261937] system 00:00: [mem 0xfec00000-0xfec00fff] could not be reserved
[    2.261938] system 00:00: [mem 0x60010000-0x6001ffff] has been reserved
[    2.261941] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    2.262084] pnp 00:01: Plug and Play ACPI device, IDs IFX0102 PNP0c31 (active)
[    2.262145] system 00:02: [io  0x0200-0x027f] has been reserved
[    2.262146] system 00:02: [io  0xffff] has been reserved
[    2.262148] system 00:02: [io  0xffff] has been reserved
[    2.262149] system 00:02: [io  0xffff] has been reserved
[    2.262150] system 00:02: [io  0x1800-0x18fe] could not be reserved
[    2.262152] system 00:02: [io  0xef80-0xef9f] has been reserved
[    2.262153] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
[    2.262185] system 00:03: [io  0x0800-0x087f] has been reserved
[    2.262186] system 00:03: Plug and Play ACPI device, IDs PNP0c02 (active)
[    2.262210] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
[    2.262495] pnp 00:05: Plug and Play ACPI device, IDs PNP0501 PNP0500 (active)
[    2.262721] pnp 00:06: [dma 0 disabled]
[    2.262765] pnp 00:06: Plug and Play ACPI device, IDs PNP0401 (active)
[    2.262785] pnp 00:07: Plug and Play ACPI device, IDs HPQ8001 PNP0303 (active)
[    2.262804] pnp 00:08: Plug and Play ACPI device, IDs SYN300a SYN0100 SYN0002 PNP0f13 (active)
[    2.263103] pnp: PnP ACPI: found 9 devices
[    2.269105] pci 0000:01:00.0: can't claim BAR 6 [mem 0xfff80000-0xffffffff pref]: no compatible bridge window
[    2.269119] pci 0000:00:1c.0: bridge window [io  0x1000-0x0fff] to [bus 02-3a] add_size 1000
[    2.269127] pci 0000:00:1c.4: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 3b-5b] add_size 200000
[    2.269139] pci 0000:00:1c.7: bridge window [io  0x1000-0x0fff] to [bus 5d] add_size 1000
[    2.269141] pci 0000:00:1c.7: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 5d] add_size 200000
[    2.269144] pci 0000:00:1c.4: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    2.269146] pci 0000:00:1c.7: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    2.269147] pci 0000:00:1c.0: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    2.269148] pci 0000:00:1c.7: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    2.269154] pci 0000:00:1c.4: BAR 15: assigned [mem 0x60100000-0x602fffff 64bit pref]
[    2.269158] pci 0000:00:1c.7: BAR 15: assigned [mem 0x60300000-0x604fffff 64bit pref]
[    2.269159] pci 0000:00:1c.0: BAR 13: assigned [io  0x2000-0x2fff]
[    2.269161] pci 0000:00:1c.7: BAR 13: assigned [io  0x7000-0x7fff]
[    2.269164] pci 0000:01:00.0: BAR 6: assigned [mem 0xd0080000-0xd00fffff pref]
[    2.269165] pci 0000:00:01.0: PCI bridge to [bus 01]
[    2.269167] pci 0000:00:01.0:   bridge window [io  0x5000-0x5fff]
[    2.269169] pci 0000:00:01.0:   bridge window [mem 0xcf000000-0xd00fffff]
[    2.269171] pci 0000:00:01.0:   bridge window [mem 0x70000000-0x81ffffff 64bit pref]
[    2.269174] pci 0000:00:1c.0: PCI bridge to [bus 02-3a]
[    2.269177] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    2.269181] pci 0000:00:1c.0:   bridge window [mem 0xb8000000-0xce0fffff]
[    2.269185] pci 0000:00:1c.0:   bridge window [mem 0x90000000-0xb1ffffff 64bit pref]
[    2.269190] pci 0000:00:1c.4: PCI bridge to [bus 3b-5b]
[    2.269193] pci 0000:00:1c.4:   bridge window [io  0x3000-0x4fff]
[    2.269197] pci 0000:00:1c.4:   bridge window [mem 0xb4000000-0xb7ffffff]
[    2.269201] pci 0000:00:1c.4:   bridge window [mem 0x60100000-0x602fffff 64bit pref]
[    2.269206] pci 0000:00:1c.6: PCI bridge to [bus 5c]
[    2.269210] pci 0000:00:1c.6:   bridge window [mem 0xd0200000-0xd02fffff]
[    2.269217] pci 0000:00:1c.7: PCI bridge to [bus 5d]
[    2.269219] pci 0000:00:1c.7:   bridge window [io  0x7000-0x7fff]
[    2.269223] pci 0000:00:1c.7:   bridge window [mem 0xd0100000-0xd01fffff]
[    2.269227] pci 0000:00:1c.7:   bridge window [mem 0x60300000-0x604fffff 64bit pref]
[    2.269232] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    2.269234] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    2.269235] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    2.269236] pci_bus 0000:00: resource 7 [mem 0x60000000-0xdfffffff]
[    2.269237] pci_bus 0000:00: resource 8 [mem 0xf0000000-0xfedfffff]
[    2.269238] pci_bus 0000:00: resource 9 [mem 0xfee01000-0xffffffff]
[    2.269239] pci_bus 0000:01: resource 0 [io  0x5000-0x5fff]
[    2.269241] pci_bus 0000:01: resource 1 [mem 0xcf000000-0xd00fffff]
[    2.269242] pci_bus 0000:01: resource 2 [mem 0x70000000-0x81ffffff 64bit pref]
[    2.269243] pci_bus 0000:02: resource 0 [io  0x2000-0x2fff]
[    2.269244] pci_bus 0000:02: resource 1 [mem 0xb8000000-0xce0fffff]
[    2.269245] pci_bus 0000:02: resource 2 [mem 0x90000000-0xb1ffffff 64bit pref]
[    2.269246] pci_bus 0000:3b: resource 0 [io  0x3000-0x4fff]
[    2.269248] pci_bus 0000:3b: resource 1 [mem 0xb4000000-0xb7ffffff]
[    2.269249] pci_bus 0000:3b: resource 2 [mem 0x60100000-0x602fffff 64bit pref]
[    2.269250] pci_bus 0000:5c: resource 1 [mem 0xd0200000-0xd02fffff]
[    2.269252] pci_bus 0000:5d: resource 0 [io  0x7000-0x7fff]
[    2.269253] pci_bus 0000:5d: resource 1 [mem 0xd0100000-0xd01fffff]
[    2.269254] pci_bus 0000:5d: resource 2 [mem 0x60300000-0x604fffff 64bit pref]
[    2.269277] NET: Registered protocol family 2
[    2.269443] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    2.269611] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    2.269718] TCP: Hash tables configured (established 131072 bind 65536)
[    2.269730] TCP: reno registered
[    2.269744] UDP hash table entries: 8192 (order: 6, 262144 bytes)
[    2.269784] UDP-Lite hash table entries: 8192 (order: 6, 262144 bytes)
[    2.269842] NET: Registered protocol family 1
[    2.269857] pci 0000:00:14.0: enabling device (0000 -> 0002)
[    2.270319] pci 0000:01:00.0: Video device with shadowed ROM
[    2.270335] PCI: CLS 64 bytes, default 64
[    2.270372] Trying to unpack rootfs image as initramfs...
[    2.647973] Freeing initrd memory: 29220K (ffff8800346de000 - ffff880036367000)
[    2.647994] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    2.647997] software IO TLB [mem 0x4fb7f000-0x53b7f000] (64MB) mapped at [ffff88004fb7f000-ffff880053b7efff]
[    2.648234] RAPL PMU detected, hw unit 2^-14 Joules, API unit is 2^-32 Joules, 4 fixed counters 655360 ms ovfl timer
[    2.648282] microcode: CPU0 sig=0x306c3, pf=0x10, revision=0x1c
[    2.648288] microcode: CPU1 sig=0x306c3, pf=0x10, revision=0x1c
[    2.648295] microcode: CPU2 sig=0x306c3, pf=0x10, revision=0x1c
[    2.648302] microcode: CPU3 sig=0x306c3, pf=0x10, revision=0x1c
[    2.648308] microcode: CPU4 sig=0x306c3, pf=0x10, revision=0x1c
[    2.648315] microcode: CPU5 sig=0x306c3, pf=0x10, revision=0x1c
[    2.648322] microcode: CPU6 sig=0x306c3, pf=0x10, revision=0x1c
[    2.648329] microcode: CPU7 sig=0x306c3, pf=0x10, revision=0x1c
[    2.648369] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    2.648389] Scanning for low memory corruption every 60 seconds
[    2.648661] futex hash table entries: 2048 (order: 5, 131072 bytes)
[    2.648680] Initialise system trusted keyring
[    2.648703] audit: initializing netlink subsys (disabled)
[    2.648713] audit: type=2000 audit(1438580594.640:1): initialized
[    2.649018] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    2.650112] zpool: loaded
[    2.650115] zbud: loaded
[    2.650251] VFS: Disk quotas dquot_6.5.2
[    2.650277] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    2.650618] fuse init (API version 7.23)
[    2.650724] Key type big_key registered
[    2.651089] Key type asymmetric registered
[    2.651092] Asymmetric key parser 'x509' registered
[    2.651117] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    2.651158] io scheduler noop registered
[    2.651160] io scheduler deadline registered (default)
[    2.651181] io scheduler cfq registered
[    2.651750] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    2.651762] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    2.651790] intel_idle: MWAIT substates: 0x42120
[    2.651792] intel_idle: v0.4 model 0x3C
[    2.651793] intel_idle: lapic_timer_reliable_states 0xffffffff
[    2.652171] ACPI: AC Adapter [AC] (on-line)
[    2.652310] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0
[    2.652313] ACPI: Sleep Button [SLPB]
[    2.652340] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    2.652355] ACPI: Lid Switch [LID]
[    2.652383] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    2.652384] ACPI: Power Button [PWRF]
[    2.677898] thermal LNXTHERM:00: registered as thermal_zone0
[    2.677900] ACPI: Thermal Zone [CPUZ] (30 C)
[    2.692077] ACPI Error: [CFGD] Namespace lookup failure, AE_NOT_FOUND (20141107/psargs-359)
[    2.692081] ACPI Error: Method parse/execution failed [\_TZ_.PSL_] (Node ffff88048d4ae118), AE_NOT_FOUND (20141107/psparse-536)
[    2.692085] ACPI Error: Method parse/execution failed [\_TZ_.GFXZ._PSL] (Node ffff88048d4adcf8), AE_NOT_FOUND (20141107/psparse-536)
[    2.692088] ACPI: Invalid passive threshold
[    2.702138] thermal LNXTHERM:01: registered as thermal_zone1
[    2.702139] ACPI: Thermal Zone [GFXZ] (25 C)
[    2.718286] thermal LNXTHERM:02: registered as thermal_zone2
[    2.718287] ACPI: Thermal Zone [EXTZ] (0 C)
[    2.733437] thermal LNXTHERM:03: registered as thermal_zone3
[    2.733438] ACPI: Thermal Zone [LOCZ] (0 C)
[    2.738658] ACPI Error: [CFGD] Namespace lookup failure, AE_NOT_FOUND (20141107/psargs-359)
[    2.738661] ACPI Error: Method parse/execution failed [\_TZ_.PSL_] (Node ffff88048d4ae118), AE_NOT_FOUND (20141107/psparse-536)
[    2.738664] ACPI Error: Method parse/execution failed [\_TZ_.BATZ._PSL] (Node ffff88048d4adf28), AE_NOT_FOUND (20141107/psparse-536)
[    2.738668] ACPI: Invalid passive threshold
[    2.748610] thermal LNXTHERM:04: registered as thermal_zone4
[    2.748611] ACPI: Thermal Zone [BATZ] (30 C)
[    2.748799] thermal LNXTHERM:05: registered as thermal_zone5
[    2.748800] ACPI: Thermal Zone [PCHZ] (114 C)
[    2.748840] GHES: HEST is not enabled!
[    2.748928] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    2.769328] 00:05: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
[    2.791035] 0000:00:16.3: ttyS4 at I/O 0x6070 (irq = 19, base_baud = 115200) is a 16550A
[    2.791515] Linux agpgart interface v0.103
[    2.792495] tpm_tis 00:01: 1.2 TPM (device-id 0xB, rev-id 16)
[    2.794378] ACPI: Battery Slot [BAT0] (battery present)
[    2.794433] ACPI: Battery Slot [BAT1] (battery absent)
[    3.076861] tpm_tis 00:01: TPM is disabled/deactivated (0x7)
[    3.078461] brd: module loaded
[    3.078894] loop: module loaded
[    3.079078] libphy: Fixed MDIO Bus: probed
[    3.079081] tun: Universal TUN/TAP device driver, 1.6
[    3.079082] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    3.079117] PPP generic driver version 2.4.2
[    3.079284] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    3.079289] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 1
[    3.079374] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    3.079445] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    3.079447] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    3.079448] usb usb1: Product: xHCI Host Controller
[    3.079449] usb usb1: Manufacturer: Linux 3.19.0-15-generic xhci-hcd
[    3.079450] usb usb1: SerialNumber: 0000:00:14.0
[    3.079532] hub 1-0:1.0: USB hub found
[    3.079548] hub 1-0:1.0: 15 ports detected
[    3.080337] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    3.080340] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 2
[    3.080370] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003
[    3.080371] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    3.080372] usb usb2: Product: xHCI Host Controller
[    3.080373] usb usb2: Manufacturer: Linux 3.19.0-15-generic xhci-hcd
[    3.080374] usb usb2: SerialNumber: 0000:00:14.0
[    3.080445] hub 2-0:1.0: USB hub found
[    3.080455] hub 2-0:1.0: 6 ports detected
[    3.080601] usb: failed to peer usb2-port3 and usb1-port1 by location (usb2-port3:none) (usb1-port1:usb2-port1)
[    3.080602] usb usb2-port3: failed to peer to usb1-port1 (-16)
[    3.080603] usb: port power management may be unreliable
[    3.080648] usb: failed to peer usb2-port4 and usb1-port1 by location (usb2-port4:none) (usb1-port1:usb2-port1)
[    3.080649] usb usb2-port4: failed to peer to usb1-port1 (-16)
[    3.080815] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.080818] ehci-pci: EHCI PCI platform driver
[    3.080905] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    3.080909] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    3.080919] ehci-pci 0000:00:1a.0: debug port 2
[    3.084809] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    3.084820] ehci-pci 0000:00:1a.0: irq 16, io mem 0xd033a000
[    3.096778] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    3.096809] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    3.096810] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    3.096812] usb usb3: Product: EHCI Host Controller
[    3.096813] usb usb3: Manufacturer: Linux 3.19.0-15-generic ehci_hcd
[    3.096814] usb usb3: SerialNumber: 0000:00:1a.0
[    3.096906] hub 3-0:1.0: USB hub found
[    3.096909] hub 3-0:1.0: 3 ports detected
[    3.097092] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    3.097096] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 4
[    3.097105] ehci-pci 0000:00:1d.0: debug port 2
[    3.101007] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    3.101017] ehci-pci 0000:00:1d.0: irq 17, io mem 0xd0339000
[    3.112771] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    3.112798] usb usb4: New USB device found, idVendor=1d6b, idProduct=0002
[    3.112799] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    3.112800] usb usb4: Product: EHCI Host Controller
[    3.112801] usb usb4: Manufacturer: Linux 3.19.0-15-generic ehci_hcd
[    3.112802] usb usb4: SerialNumber: 0000:00:1d.0
[    3.112895] hub 4-0:1.0: USB hub found
[    3.112898] hub 4-0:1.0: 3 ports detected
[    3.112999] ehci-platform: EHCI generic platform driver
[    3.113007] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.113010] ohci-pci: OHCI PCI platform driver
[    3.113017] ohci-platform: OHCI generic platform driver
[    3.113023] uhci_hcd: USB Universal Host Controller Interface driver
[    3.113063] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    3.114253] i8042: Detected active multiplexing controller, rev 1.1
[    3.114901] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.114904] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    3.114922] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    3.114936] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    3.114950] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    3.115067] mousedev: PS/2 mouse device common for all mice
[    3.115270] rtc_cmos 00:04: RTC can wake from S4
[    3.115395] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    3.115419] rtc_cmos 00:04: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    3.115432] i2c /dev entries driver
[    3.115478] device-mapper: uevent: version 1.0.3
[    3.115543] device-mapper: ioctl: 4.29.0-ioctl (2014-10-28) initialised: dm-devel@redhat.com
[    3.115556] Intel P-state driver initializing.
[    3.115730] Consider also installing thermald for improved thermal control.
[    3.115734] ledtrig-cpu: registered to indicate activity on CPUs
[    3.115908] PCCT header not found.
[    3.115909] ACPI PCC probe failed.
[    3.116020] TCP: cubic registered
[    3.116083] NET: Registered protocol family 10
[    3.116319] NET: Registered protocol family 17
[    3.116333] Key type dns_resolver registered
[    3.116663] Loading compiled-in X.509 certificates
[    3.117310] Loaded X.509 cert 'Magrathea: Glacier signing key: 9e64807092f3a6a8f66f3b7ea4cb3767fdfae08a'
[    3.117322] registered taskstats version 1
[    3.118576] Key type trusted registered
[    3.120878] Key type encrypted registered
[    3.120883] AppArmor: AppArmor sha1 policy hashing enabled
[    3.139672] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    3.180820] tpm_tis 00:01: A TPM error (7) occurred attempting to read a pcr value
[    3.180882] ima: No TPM chip found, activating TPM-bypass!
[    3.180910] evm: HMAC attrs: 0x1
[    3.181564]   Magic number: 11:448:718
[    3.181708] rtc_cmos 00:04: setting system clock to 2015-08-03 05:43:15 UTC (1438580595)
[    3.181862] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.181864] EDD information not available.
[    3.181926] PM: Hibernation image not present or could not be loaded.
[    3.182220] Freeing unused kernel memory: 1408K (ffffffff81d36000 - ffffffff81e96000)
[    3.182221] Write protecting the kernel read-only data: 12288k
[    3.182405] Freeing unused kernel memory: 188K (ffff8800017d1000 - ffff880001800000)
[    3.182497] Freeing unused kernel memory: 344K (ffff880001baa000 - ffff880001c00000)
[    3.191042] random: systemd-udevd urandom read with 14 bits of entropy available
[    3.198853] ACPI: Video Device [DGFX] (multi-head: yes  rom: yes  post: no)
[    3.199583] acpi device:01: registered as cooling_device8
[    3.199656] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/LNXVIDEO:00/input/input8
[    3.204500] pps_core: LinuxPPS API ver. 1 registered
[    3.204503] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
[    3.205005] rtsx_pci 0000:5d:00.0: rtsx_pci_acquire_irq: pcr->msi_en = 1, pci->irq = 27
[    3.205683] PTP clock support registered
[    3.205938] ahci 0000:00:1f.2: version 3.0
[    3.206040] ahci 0000:00:1f.2: SSS flag set, parallel bus scan disabled
[    3.206065] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x2f impl SATA mode
[    3.206067] ahci 0000:00:1f.2: flags: 64bit ncq stag pm led clo pio slum part ems sxs apst 
[    3.209534] e1000e: Intel(R) PRO/1000 Network Driver - 2.3.2-k
[    3.209536] e1000e: Copyright(c) 1999 - 2014 Intel Corporation.
[    3.237423] scsi host0: ahci
[    3.237604] scsi host1: ahci
[    3.237768] scsi host2: ahci
[    3.237929] scsi host3: ahci
[    3.238072] scsi host4: ahci
[    3.238182] scsi host5: ahci
[    3.238217] ata1: SATA max UDMA/133 abar m2048@0xd0338000 port 0xd0338100 irq 28
[    3.238219] ata2: SATA max UDMA/133 abar m2048@0xd0338000 port 0xd0338180 irq 28
[    3.238222] ata3: SATA max UDMA/133 abar m2048@0xd0338000 port 0xd0338200 irq 28
[    3.238223] ata4: SATA max UDMA/133 abar m2048@0xd0338000 port 0xd0338280 irq 28
[    3.238224] ata5: DUMMY
[    3.238226] ata6: SATA max UDMA/133 abar m2048@0xd0338000 port 0xd0338380 irq 28
[    3.238409] e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    3.292777] usb 2-1: new SuperSpeed USB device number 2 using xhci_hcd
[    3.309121] usb 2-1: New USB device found, idVendor=0424, idProduct=5434
[    3.309122] usb 2-1: New USB device strings: Mfr=2, Product=3, SerialNumber=1
[    3.309124] usb 2-1: Product: USB5534
[    3.309124] usb 2-1: Manufacturer: SMSC
[    3.309125] usb 2-1: SerialNumber: 1239567
[    3.309456] hub 2-1:1.0: USB hub found
[    3.309472] hub 2-1:1.0: 4 ports detected
[    3.388755] usb 1-1: new high-speed USB device number 2 using xhci_hcd
[    3.408744] usb 3-1: new high-speed USB device number 2 using ehci-pci
[    3.424743] usb 4-1: new high-speed USB device number 2 using ehci-pci
[    3.502035] e1000e 0000:00:19.0 eth0: registered PHC clock
[    3.502048] e1000e 0000:00:19.0 eth0: (PCI Express:2.5GT/s:Width x1) a0:1d:48:0e:1e:71
[    3.502049] e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
[    3.502089] e1000e 0000:00:19.0 eth0: MAC: 11, PHY: 12, PBA No: FFFFFF-0FF
[    3.516855] usb 1-1: New USB device found, idVendor=0424, idProduct=5434
[    3.516858] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    3.517202] hub 1-1:1.0: USB hub found
[    3.517221] hub 1-1:1.0: 4 ports detected
[    3.541437] usb 3-1: New USB device found, idVendor=8087, idProduct=8008
[    3.541440] usb 3-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    3.541737] hub 3-1:1.0: USB hub found
[    3.541879] hub 3-1:1.0: 6 ports detected
[    3.556688] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.557086] usb 4-1: New USB device found, idVendor=8087, idProduct=8000
[    3.557089] usb 4-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    3.557362] hub 4-1:1.0: USB hub found
[    3.557497] hub 4-1:1.0: 8 ports detected
[    3.558189] ata1.00: ATA-8: Hitachi HTS727575A9E364, JF4OA0E0, max UDMA/100
[    3.558192] ata1.00: 1465149168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    3.578733] ata1.00: configured for UDMA/100
[    3.578928] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS72757 A0E0 PQ: 0 ANSI: 5
[    3.579220] sd 0:0:0:0: [sda] 1465149168 512-byte logical blocks: (750 GB/698 GiB)
[    3.579223] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    3.579236] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.579252] sd 0:0:0:0: [sda] Write Protect is off
[    3.579255] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.579264] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.637636]  sda: sda1 sda2
[    3.637979] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.644615] tsc: Refined TSC clocksource calibration: 2693.763 MHz
[    3.684651] usb 1-5: new full-speed USB device number 3 using xhci_hcd
[    3.814170] usb 1-5: New USB device found, idVendor=138a, idProduct=003f
[    3.814173] usb 1-5: New USB device strings: Mfr=0, Product=0, SerialNumber=1
[    3.814175] usb 1-5: SerialNumber: 0030f6f6ac91
[    3.884628] usb 1-1.4: new low-speed USB device number 4 using xhci_hcd
[    3.896567] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.900589] ata2.00: ATAPI: hp      DVD A  DU8A5SH, NH62, max UDMA/100
[    3.901488] ata2.00: configured for UDMA/100
[    3.913971] scsi 1:0:0:0: CD-ROM            hp       DVD A  DU8A5SH   NH62 PQ: 0 ANSI: 5
[    3.938062] sr 1:0:0:0: [sr0] scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.938065] cdrom: Uniform CD-ROM driver Revision: 3.20
[    3.938228] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    3.938297] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    4.003947] usb 1-1.4: New USB device found, idVendor=03f0, idProduct=0024
[    4.003950] usb 1-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    4.003952] usb 1-1.4: Product: HP Basic USB Keyboard
[    4.003953] usb 1-1.4: Manufacturer: CHICONY
[    4.004132] usb 1-1.4: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[    4.007322] hidraw: raw HID events driver (C) Jiri Kosina
[    4.015369] usbcore: registered new interface driver usbhid
[    4.015370] usbhid: USB HID core driver
[    4.016556] input: CHICONY HP Basic USB Keyboard as /devices/pci0000:00/0000:00:14.0/usb1/1-1/1-1.4/1-1.4:1.0/0003:03F0:0024.0001/input/input11
[    4.072562] hid-generic 0003:03F0:0024.0001: input,hidraw0: USB HID v1.11 Keyboard [CHICONY HP Basic USB Keyboard] on usb-0000:00:14.0-1.4/input0
[    4.156398] usb 1-6: new full-speed USB device number 5 using xhci_hcd
[    4.256450] ata3: SATA link down (SStatus 0 SControl 300)
[    4.287050] usb 1-6: New USB device found, idVendor=046d, idProduct=c52f
[    4.287053] usb 1-6: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    4.287055] usb 1-6: Product: USB Receiver
[    4.287056] usb 1-6: Manufacturer: Logitech
[    4.289229] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:14.0/usb1/1-6/1-6:1.0/0003:046D:C52F.0002/input/input12
[    4.289345] hid-generic 0003:046D:C52F.0002: input,hidraw1: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:14.0-6/input0
[    4.291217] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:14.0/usb1/1-6/1-6:1.1/0003:046D:C52F.0003/input/input13
[    4.297297] input: PS/2 Generic Mouse as /devices/platform/i8042/serio2/input/input10
[    4.344577] hid-generic 0003:046D:C52F.0003: input,hiddev0,hidraw2: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:14.0-6/input1
[    4.456370] usb 1-7: new high-speed USB device number 6 using xhci_hcd
[    4.576319] ata4: SATA link down (SStatus 0 SControl 300)
[    4.621545] usb 1-7: New USB device found, idVendor=04f2, idProduct=b3ed
[    4.621548] usb 1-7: New USB device strings: Mfr=3, Product=1, SerialNumber=2
[    4.621550] usb 1-7: Product: HP HD Webcam
[    4.621551] usb 1-7: Manufacturer: Chicony Electronics Co.,Ltd.
[    4.621552] usb 1-7: SerialNumber: 200901010001
[    4.644485] Switched to clocksource tsc
[    4.788241] usb 1-11: new high-speed USB device number 7 using xhci_hcd
[    4.896197] ata6: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    4.896780] ata6.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[    4.896892] ata6.00: failed to get NCQ Send/Recv Log Emask 0x1
[    4.896895] ata6.00: ATA-9: SAMSUNG MZMPF032HCFV-000H1, FXM42H2Q, max UDMA/133
[    4.896896] ata6.00: 62533296 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    4.897696] ata6.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[    4.897762] ata6.00: failed to get NCQ Send/Recv Log Emask 0x1
[    4.897794] ata6.00: configured for UDMA/133
[    4.897916] scsi 5:0:0:0: Direct-Access     ATA      SAMSUNG MZMPF032 2H2Q PQ: 0 ANSI: 5
[    4.898153] sd 5:0:0:0: [sdb] 62533296 512-byte logical blocks: (32.0 GB/29.8 GiB)
[    4.898173] sd 5:0:0:0: Attached scsi generic sg2 type 0
[    4.898262] sd 5:0:0:0: [sdb] Write Protect is off
[    4.898265] sd 5:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    4.898304] sd 5:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.898702]  sdb: sdb1
[    4.898905] sd 5:0:0:0: [sdb] Attached SCSI disk
[    4.918298] usb 1-11: New USB device found, idVendor=03f0, idProduct=521d
[    4.918301] usb 1-11: New USB device strings: Mfr=5, Product=4, SerialNumber=0
[    4.918303] usb 1-11: Product: HP hs3110 HSPA+ Mobile Broadband Device
[    4.918304] usb 1-11: Manufacturer: Hewlett-Packard
[    5.032156] usb 1-12: new full-speed USB device number 8 using xhci_hcd
[    5.136090] psmouse serio3: synaptics: queried max coordinates: x [..5660], y [..4730]
[    5.161300] usb 1-12: New USB device found, idVendor=8087, idProduct=07dc
[    5.161315] usb 1-12: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    5.170500] psmouse serio3: synaptics: queried min coordinates: x [1324..], y [1248..]
[    5.228651] psmouse serio3: synaptics: Touchpad model: 1, fw: 8.1, id: 0x1e2b1, caps: 0xd40123/0x840300/0x26800, board id: 2706, fw id: 1486004
[    5.265773] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio3/input/input14
[   11.241077] EXT4-fs (sda2): INFO: recovery required on readonly filesystem
[   11.241080] EXT4-fs (sda2): write access will be enabled during recovery
[   11.520459] random: nonblocking pool is initialized
[   12.153088] EXT4-fs (sda2): orphan cleanup on readonly fs
[   12.298801] EXT4-fs (sda2): 25 orphan inodes deleted
[   12.298805] EXT4-fs (sda2): recovery complete
[   12.544526] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[   13.409596] systemd[1]: Inserted module 'autofs4'
[   13.551273] systemd[1]: systemd 219 running in system mode. (+PAM +AUDIT +SELINUX +IMA +APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT -GNUTLS +ACL +XZ -LZ4 -SECCOMP +BLKID -ELFUTILS +KMOD -IDN)
[   13.551413] systemd[1]: Detected architecture x86-64.
[   13.571235] systemd[1]: Set hostname to <mateusz-ubuntu-mate>.
[   14.030237] systemd[1]: Reached target Remote File Systems (Pre).
[   14.030246] systemd[1]: Starting Remote File Systems (Pre).
[   14.030286] systemd[1]: Created slice Root Slice.
[   14.030292] systemd[1]: Starting Root Slice.
[   14.030331] systemd[1]: Listening on Journal Audit Socket.
[   14.030336] systemd[1]: Starting Journal Audit Socket.
[   14.030366] systemd[1]: Listening on udev Kernel Socket.
[   14.030372] systemd[1]: Starting udev Kernel Socket.
[   14.030418] systemd[1]: Listening on Journal Socket.
[   14.030428] systemd[1]: Starting Journal Socket.
[   14.030458] systemd[1]: Listening on fsck to fsckd communication Socket.
[   14.030464] systemd[1]: Starting fsck to fsckd communication Socket.
[   14.030496] systemd[1]: Listening on udev Control Socket.
[   14.030501] systemd[1]: Starting udev Control Socket.
[   14.030587] systemd[1]: Created slice User and Session Slice.
[   14.030593] systemd[1]: Starting User and Session Slice.
[   14.030742] systemd[1]: Set up automount Arbitrary Executable File Formats File System Automount Point.
[   14.030749] systemd[1]: Starting Arbitrary Executable File Formats File System Automount Point.
[   14.030775] systemd[1]: Started Forward Password Requests to Wall Directory Watch.
[   14.030780] systemd[1]: Starting Forward Password Requests to Wall Directory Watch.
[   14.030819] systemd[1]: Listening on /dev/initctl Compatibility Named Pipe.
[   14.030825] systemd[1]: Starting /dev/initctl Compatibility Named Pipe.
[   14.030899] systemd[1]: Created slice System Slice.
[   14.030910] systemd[1]: Starting System Slice.
[   14.075311] systemd[1]: Starting Load Kernel Modules...
[   14.075656] systemd[1]: Starting Uncomplicated firewall...
[   14.075768] systemd[1]: Created slice system-systemd\x2dcryptsetup.slice.
[   14.075779] systemd[1]: Starting system-systemd\x2dcryptsetup.slice.
[   14.076133] systemd[1]: Starting Increase datagram queue length...
[   14.076476] systemd[1]: Mounting POSIX Message Queue File System...
[   14.076587] systemd[1]: Created slice system-getty.slice.
[   14.076599] systemd[1]: Starting system-getty.slice.
[   14.076684] systemd[1]: Created slice system-systemd\x2dfsck.slice.
[   14.076692] systemd[1]: Starting system-systemd\x2dfsck.slice.
[   14.076989] systemd[1]: Mounting Debug File System...
[   14.077055] systemd[1]: Reached target Slices.
[   14.077074] systemd[1]: Starting Slices.
[   14.196834] systemd[1]: Started Set Up Additional Binary Formats.
[   14.197320] systemd[1]: Starting Create list of required static device nodes for the current kernel...
[   14.197698] systemd[1]: Starting udev Coldplug all Devices...
[   14.198001] systemd[1]: Starting Setup Virtual Console...
[   14.198292] systemd[1]: Starting Nameserver information manager...
[   14.198613] systemd[1]: Mounting Huge Pages File System...
[   14.198718] systemd[1]: Listening on Delayed Shutdown Socket.
[   14.198726] systemd[1]: Starting Delayed Shutdown Socket.
[   14.199042] systemd[1]: Started Braille Device Support.
[   14.199254] systemd[1]: Starting Braille Device Support...
[   14.199569] systemd[1]: Started Read required files in advance.
[   14.199705] systemd[1]: Starting Read required files in advance...
[   14.199755] systemd[1]: Listening on Journal Socket (/dev/log).
[   14.199764] systemd[1]: Starting Journal Socket (/dev/log).
[   14.274185] systemd[1]: Started Setup Virtual Console.
[   14.379064] systemd[1]: Started udev Coldplug all Devices.
[   14.379488] systemd[1]: Starting udev Wait for Complete Device Initialization...
[   14.415272] systemd[1]: Started Uncomplicated firewall.
[   14.458724] systemd[1]: Started Create list of required static device nodes for the current kernel.
[   14.459208] systemd[1]: Starting Create Static Device Nodes in /dev...
[   14.524691] lp: driver loaded but no devices found
[   14.540450] ppdev: user-space parallel port driver
[   14.552826] parport_pc 00:06: reported by Plug and Play ACPI
[   14.552867] parport0: PC-style at 0x378 (0x778), irq 5, using FIFO [PCSPP,TRISTATE,COMPAT,EPP,ECP]
[   14.648766] lp0: using parport0 (interrupt-driven).
[   14.660007] systemd[1]: Mounted Debug File System.
[   14.660209] systemd[1]: Mounted POSIX Message Queue File System.
[   14.660315] systemd[1]: Mounted Huge Pages File System.
[   14.660553] systemd[1]: Started Increase datagram queue length.
[   14.665608] systemd[1]: Listening on Syslog Socket.
[   14.665616] systemd[1]: Starting Syslog Socket.
[   14.665904] systemd[1]: Starting Journal Service...
[   14.730469] systemd[1]: Started Load Kernel Modules.
[   14.730950] systemd[1]: Starting Apply Kernel Variables...
[   14.731020] systemd[1]: Mounted Configuration File System.
[   14.731369] systemd[1]: Mounting FUSE Control File System...
[   14.732577] systemd[1]: Mounted FUSE Control File System.
[   14.762864] systemd[1]: Started Nameserver information manager.
[   14.921722] systemd[1]: Started Journal Service.
[   17.078724] EDAC MC: Ver: 3.0.0
[   17.110464] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   17.115681] hp_accel: hardware type HPZBook15 found
[   17.132845] Initializing HPQ6001 module
[   17.132876] input: HP Wireless hotkeys as /devices/virtual/input/input16
[   17.213402] EDAC ie31200: No ECC support
[   17.239651] lis3lv02d: 8 bits 3DC sensor found
[   17.419046] Bluetooth: Core ver 2.20
[   17.419056] NET: Registered protocol family 31
[   17.419056] Bluetooth: HCI device and connection manager initialized
[   17.419059] Bluetooth: HCI socket layer initialized
[   17.419060] Bluetooth: L2CAP socket layer initialized
[   17.419063] Bluetooth: SCO socket layer initialized
[   17.444614] cfg80211: Calling CRDA to update world regulatory domain
[   17.458020] [drm] Initialized drm 1.1.0 20060810
[   17.490311] Intel(R) Wireless WiFi driver for Linux, in-tree:
[   17.490312] Copyright(c) 2003- 2014 Intel Corporation
[   17.538347] iwlwifi 0000:5c:00.0: loaded firmware version 25.15.12.0 op_mode iwlmvm
[   17.557287] snd_hda_intel 0000:01:00.1: Disabling MSI
[   17.557292] snd_hda_intel 0000:01:00.1: Handle VGA-switcheroo audio client
[   17.564260] usbcore: registered new interface driver btusb
[   17.576287] AVX2 version of gcm_enc/dec engaged.
[   17.576289] AES CTR mode by8 optimization enabled
[   17.577319] Bluetooth: hci0: read Intel version: 370710018002030d00
[   17.612379] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.2.3.d.bseq
[   17.614342] sound hdaudioC0D0: autoconfig: line_outs=1 (0xa/0x0/0x0/0x0/0x0) type:line
[   17.614344] sound hdaudioC0D0:    speaker_outs=1 (0xd/0x0/0x0/0x0/0x0)
[   17.614346] sound hdaudioC0D0:    hp_outs=1 (0xb/0x0/0x0/0x0/0x0)
[   17.614346] sound hdaudioC0D0:    mono: mono_out=0x0
[   17.614347] sound hdaudioC0D0:    inputs:
[   17.614348] sound hdaudioC0D0:      Mic=0xc
[   17.614349] sound hdaudioC0D0:      Internal Mic=0x11
[   17.614350] sound hdaudioC0D0:      Line=0xf
[   17.622960] iwlwifi 0000:5c:00.0: Detected Intel(R) Dual Band Wireless N 7260, REV=0x144
[   17.623013] iwlwifi 0000:5c:00.0: L1 Disabled - LTR Enabled
[   17.623243] iwlwifi 0000:5c:00.0: L1 Disabled - LTR Enabled
[   17.656701] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input17
[   17.656738] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input18
[   17.656770] input: HDA Intel PCH Dock Line Out as /devices/pci0000:00/0000:00:1b.0/sound/card0/input19
[   17.656803] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input20
[   17.735877] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[   17.814672] nvidia: module license 'NVIDIA' taints kernel.
[   17.814675] Disabling lock debugging due to kernel taint
[   17.816568] nvidia: module verification failed: signature and/or  required key missing - tainting kernel
[   17.819329] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   17.819540] [drm] Initialized nvidia-drm 0.0.0 20150116 for 0000:01:00.0 on minor 0
[   17.819544] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  346.59  Tue Mar 31 14:10:31 PDT 2015
[   17.875869] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[   17.967748] intel_rapl: Found RAPL domain package
[   17.967752] intel_rapl: Found RAPL domain core
[   17.967756] intel_rapl: Found RAPL domain dram
[   18.055588] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input21
[   18.055634] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input22
[   18.055671] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input23
[   18.234590] media: Linux media interface: v0.10
[   18.493703] Linux video capture interface: v2.00
[   18.547233] input: ST LIS3LV02DL Accelerometer as /devices/platform/lis3lv02d/input/input24
[   18.548035] wmi: Mapper loaded
[   18.611428] uvcvideo: Found UVC 1.00 device HP HD Webcam (04f2:b3ed)
[   18.612582] input: HP HD Webcam as /devices/pci0000:00/0000:00:14.0/usb1/1-7/1-7:1.0/input/input25
[   18.612629] usbcore: registered new interface driver uvcvideo
[   18.612630] USB Video Class driver (1.1.1)
[   18.669534] cfg80211: World regulatory domain updated:
[   18.669537] cfg80211:  DFS Master region: unset
[   18.669539] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[   18.669541] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   18.669542] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   18.669543] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
[   18.669544] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   18.669545] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   18.702756] input: HP WMI hotkeys as /devices/virtual/input/input26
[  194.463105] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
[  194.513346] systemd-journald[333]: Received request to flush runtime journal from PID 1
[  194.766935] Adding 7904764k swap on /dev/mapper/cryptswap1.  Priority:-1 extents:1 across:7904764k FS
[  194.912375] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[  194.978145] audit: type=1400 audit(1438580787.359:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=684 comm="apparmor_parser"
[  194.978150] audit: type=1400 audit(1438580787.359:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=684 comm="apparmor_parser"
[  194.979160] audit: type=1400 audit(1438580787.359:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=684 comm="apparmor_parser"
[  194.979164] audit: type=1400 audit(1438580787.359:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=684 comm="apparmor_parser"
[  194.979166] audit: type=1400 audit(1438580787.359:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=684 comm="apparmor_parser"
[  194.979169] audit: type=1400 audit(1438580787.359:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=684 comm="apparmor_parser"
[  194.979735] audit: type=1400 audit(1438580787.363:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cups-browsed" pid=684 comm="apparmor_parser"
[  194.980886] audit: type=1400 audit(1438580787.363:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=684 comm="apparmor_parser"
[  194.980889] audit: type=1400 audit(1438580787.363:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=684 comm="apparmor_parser"
[  194.980892] audit: type=1400 audit(1438580787.363:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="third_party" pid=684 comm="apparmor_parser"
[  195.382367] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  195.382369] Bluetooth: BNEP filters: protocol multicast
[  195.382372] Bluetooth: BNEP socket layer initialized
[  195.384533] Bluetooth: RFCOMM TTY layer initialized
[  195.384537] Bluetooth: RFCOMM socket layer initialized
[  195.384540] Bluetooth: RFCOMM ver 1.11
[  196.284809] iwlwifi 0000:5c:00.0: L1 Disabled - LTR Enabled
[  196.285040] iwlwifi 0000:5c:00.0: L1 Disabled - LTR Enabled
[  197.272951] ACPI Warning: \_SB_.PCI0.PEGP.DGFX._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)
[  197.273053] ACPI Warning: \_SB_.PCI0.PEGP.DGFX._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)
[  197.273133] ACPI Warning: \_SB_.PCI0.PEGP.DGFX._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)
[  197.273316] ACPI Warning: \_SB_.PCI0.PEGP.DGFX._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)
[  197.273398] ACPI Warning: \_SB_.PCI0.PEGP.DGFX._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)
[  197.273637] ACPI Warning: \_SB_.PCI0.PEGP.DGFX._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)
[  197.273867] ACPI Warning: \_SB_.PCI0.PEGP.DGFX._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)
[  197.273948] ACPI Warning: \_SB_.PCI0.PEGP.DGFX._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)
[  197.274029] ACPI Warning: \_SB_.PCI0.PEGP.DGFX._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)
[  197.274304] ACPI Warning: \_SB_.PCI0.PEGP.DGFX._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)
[  197.282502] ACPI Warning: \_SB_.PCI0.PEGP.DGFX._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)
[  197.282728] ACPI Warning: \_SB_.PCI0.PEGP.DGFX._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)
[  197.533606] ACPI Warning: \_SB_.PCI0.PEGP.DGFX._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)
[  197.535537] ACPI Warning: \_SB_.PCI0.PEGP.DGFX._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)
[  197.827843] ACPI Warning: \_SB_.PCI0.PEGP.DGFX._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)
[  197.858431] ACPI Warning: \_SB_.PCI0.PEGP.DGFX._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)
[  197.920452] ACPI Warning: \_SB_.PCI0.PEGP.DGFX._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)
[  198.168935] WARNING! power/level is deprecated; use power/control instead
[  199.209208] ACPI Warning: \_SB_.PCI0.PEGP.DGFX._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)
[  199.211713] ACPI Warning: \_SB_.PCI0.PEGP.DGFX._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)
[  208.740153] ACPI Warning: \_SB_.PCI0.PEGP.DGFX._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)
[  208.801213] ACPI Warning: \_SB_.PCI0.PEGP.DGFX._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)
[  208.862537] ACPI Warning: \_SB_.PCI0.PEGP.DGFX._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)
[  211.074775] ACPI Warning: \_SB_.PCI0.PEGP.DGFX._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)
[  215.075828] ACPI Warning: \_SB_.PCI0.PEGP.DGFX._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95) [COLOR=#000000][  352.818224] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx[/COLOR]
```

I also installed bootchart but after reboot there is no image in /var/log/bootchart directory. I saw similar threads on internet but it looks like there is no universal resolution and some boot log analysis is needed, Can anyone help me deal with it? I would be thankful.

---

### Post by pqwoerituytrueiwoq on 2015-08-03
it will show boot chart a min or 2 after boot in that folder

id start with a check/repair using gparted on a live session on sda2
also run a smart test on the drive just to make sure (gsmartcontrol or gnome-disks)

---

### Post by kerry_s on 2015-08-03
looks like acpi issues. try what it says to do:
```
[    2.213225] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug

```

so alt+f2 & run:
```
pkexec pluma /etc/default/grub
```

change this line:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

to this:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pci=nocrs"


close & save

now open a terminal & run:
```
sudo update-grub
```

now reboot & see what happens. good luck

---

### Post by matek2305 on 2015-08-04
I tried adding "pci=nocrs" but it has no effect, still very long boot time. I will try again with bootchart and post results here. I also did smart test with gnome-disks on sda2 and it says that disk is ok. Thanks for help guys.

---

### Post by kerry_s on 2015-08-04
[https://wiki.ubuntu.com/DebuggingACPI](https://wiki.ubuntu.com/DebuggingACPI)

this looks like it would help. good luck

---

### Post by pqwoerituytrueiwoq on 2015-08-04
try to make sure your UUIDs match the ones in /etc/fstab
also look in /etc/mtab
i once had a issue when i replaced my swap partition that caused a long boot

---

### Post by matek2305 on 2015-08-05
Here is content of my /etc/fstab:

```
# /etc/fstab: static file system information.#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=51885ac5-af27-4d13-b5bd-9eb591337c94 /               ext4    errors=remount-ro 0       1
# /media/data was on /dev/sdb1 during installation
UUID=2efe9f37-4717-4dcb-a28f-9d9a05cfa657 /media/data     ext4    defaults        0       2
# swap was on /dev/sda1 during installation
#UUID=9074851e-7b96-4f96-867b-c024f1036a22 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0

```

And here is /etc/mtab:

```
sysfs /sys sysfs rw,nosuid,nodev,noexec,relatime 0 0proc /proc proc rw,nosuid,nodev,noexec,relatime 0 0
udev /dev devtmpfs rw,relatime,size=8084916k,nr_inodes=2021229,mode=755 0 0
devpts /dev/pts devpts rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000 0 0
tmpfs /run tmpfs rw,nosuid,noexec,relatime,size=1620100k,mode=755 0 0
none /dev/.bootchart/proc proc rw,relatime 0 0
/dev/disk/by-uuid/51885ac5-af27-4d13-b5bd-9eb591337c94 / ext4 rw,relatime,errors=remount-ro,data=ordered 0 0
securityfs /sys/kernel/security securityfs rw,nosuid,nodev,noexec,relatime 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
tmpfs /run/lock tmpfs rw,nosuid,nodev,noexec,relatime,size=5120k 0 0
tmpfs /sys/fs/cgroup tmpfs ro,nosuid,nodev,noexec,mode=755 0 0
cgroup /sys/fs/cgroup/systemd cgroup rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd 0 0
pstore /sys/fs/pstore pstore rw,nosuid,nodev,noexec,relatime 0 0
cgroup /sys/fs/cgroup/perf_event cgroup rw,nosuid,nodev,noexec,relatime,perf_event 0 0
cgroup /sys/fs/cgroup/cpu,cpuacct cgroup rw,nosuid,nodev,noexec,relatime,cpu,cpuacct 0 0
cgroup /sys/fs/cgroup/net_cls,net_prio cgroup rw,nosuid,nodev,noexec,relatime,net_cls,net_prio 0 0
cgroup /sys/fs/cgroup/cpuset cgroup rw,nosuid,nodev,noexec,relatime,cpuset,clone_children 0 0
cgroup /sys/fs/cgroup/hugetlb cgroup rw,nosuid,nodev,noexec,relatime,hugetlb 0 0
cgroup /sys/fs/cgroup/devices cgroup rw,nosuid,nodev,noexec,relatime,devices 0 0
cgroup /sys/fs/cgroup/blkio cgroup rw,nosuid,nodev,noexec,relatime,blkio 0 0
cgroup /sys/fs/cgroup/freezer cgroup rw,nosuid,nodev,noexec,relatime,freezer 0 0
cgroup /sys/fs/cgroup/memory cgroup rw,nosuid,nodev,noexec,relatime,memory 0 0
systemd-1 /proc/sys/fs/binfmt_misc autofs rw,relatime,fd=21,pgrp=1,timeout=300,minproto=5,maxproto=5,direct 0 0
mqueue /dev/mqueue mqueue rw,relatime 0 0
debugfs /sys/kernel/debug debugfs rw,relatime 0 0
hugetlbfs /dev/hugepages hugetlbfs rw,relatime 0 0
fusectl /sys/fs/fuse/connections fusectl rw,relatime 0 0
/dev/sdb1 /media/data ext4 rw,relatime,data=ordered 0 0
tmpfs /run/user/1000 tmpfs rw,nosuid,nodev,relatime,size=1620100k,mode=700,uid=1000,gid=1000 0 0
/home/mateusz/.Private /home/mateusz ecryptfs rw,nosuid,nodev,relatime,ecryptfs_fnek_sig=f82cc4d051dd6808,ecryptfs_sig=50a4bf08dd8b254e,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs 0 0

```

How can i check if they are correct? Also I found that I can chceck boot times with systemd-analyze blame command, here is result:

```
       3min 42ms systemd-udev-settle.service
          8.846s plymouth-quit-wait.service
          6.496s mysql.service
          5.949s gpu-manager.service
          5.687s NetworkManager-wait-online.service
          4.577s ModemManager.service
          4.252s dev-disk-by\x2duuid-51885ac5\x2daf27\x2d4d13\x2db5bd\x2d9eb591337c94.device
          4.069s NetworkManager.service
          3.977s udisks2.service
          3.490s accounts-daemon.service
          3.232s systemd-tmpfiles-setup.service
          2.368s bluetooth.service
          2.352s systemd-logind.service
          2.348s rsyslog.service
          2.348s irqbalance.service
          2.347s grub-common.service
          2.346s loadcpufreq.service
          2.344s avahi-daemon.service
          2.344s apport.service
          2.342s pppd-dns.service
          2.341s console-kit-log-system-start.service
          2.074s apparmor.service
          1.862s console-kit-daemon.service
          1.532s systemd-cryptsetup@cryptswap1.service
           992ms systemd-tmpfiles-setup-dev.service
           933ms polkitd.service
           892ms lightdm.service
           653ms systemd-journald.service
           613ms systemd-modules-load.service
           598ms virtualbox.service
           520ms systemd-udevd.service
           515ms resolvconf.service
           405ms upower.service
           393ms systemd-udev-trigger.service
           389ms dbus.service
           388ms ufw.service
           346ms ondemand.service
           342ms systemd-sysctl.service
           337ms console-setup.service
           335ms networking.service
           319ms ifup-wait-all-auto.service
           281ms systemd-backlight@backlight:acpi_video0.service
           274ms kerneloops.service
           260ms sys-kernel-debug.mount
           259ms dev-mqueue.mount
           259ms systemd-setup-dgram-qlen.service
           259ms dev-hugepages.mount
           222ms rtkit-daemon.service
           187ms plymouth-read-write.service
           184ms systemd-journal-flush.service
           178ms systemd-rfkill@rfkill0.service
           177ms systemd-random-seed.service
           170ms systemd-fsck-root.service
           164ms systemd-vconsole-setup.service
           145ms kmod-static-nodes.service
            87ms rc-local.service
            86ms user@1000.service
            86ms dev-mapper-cryptswap1.swap
            47ms systemd-tmpfiles-clean.service
            47ms systemd-update-utmp.service
            31ms alsa-restore.service
            29ms dns-clean.service
            28ms udev-finish.service
            22ms systemd-user-sessions.service
            20ms systemd-remount-fs.service
            17ms systemd-update-utmp-runlevel.service
            15ms speech-dispatcher.service
            13ms systemd-fsck@dev-disk-by\x2duuid-2efe9f37\x2d4717\x2d4dcb\x2da28f\x2d9d9a05cfa657.service
            12ms plymouth-start.service
             7ms ntp.service
             3ms media-data.mount
             3ms cpufrequtils.service
             2ms ureadahead-stop.service
             1ms sys-fs-fuse-connections.mount
             1ms systemd-rfkill@rfkill3.service
```

And here we have that systemd-udev-settle.service is taking more than 3 minutes when booting so it looks like it is source of the problem. But still I dont know how to deal with it.

---

### Post by kerry_s on 2015-08-05
your install is encrypted ?

google ubuntu slow boot encrypted drives, you'll see the bugs on that.

---

### Post by matek2305 on 2015-08-05
I have only home directory encrypted, anyway I runned ```
systemctl mask systemd-udev-settle
``` and now booting is a lot faster so I think that problem is resolved.

---

