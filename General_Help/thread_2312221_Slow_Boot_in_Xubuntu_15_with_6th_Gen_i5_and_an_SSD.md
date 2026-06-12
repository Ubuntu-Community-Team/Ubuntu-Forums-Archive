---
title: "Slow Boot in Xubuntu 15 with 6th Gen i5 and an SSD"
date: 2016-02-02
forum: General Help
---

### Post by rob156 on 2016-02-02
I purchased a Dell Inspiron 13 7000 2-in-1 series laptop about a month ago, wiped Windows and installed my favorite distro, ie, Xubuntu. Most things went off without a hiccup, although I am getting a bit of screen tearing during videos or website scrolling, and sometimes my touchpad gets disabled when I come out of suspend. For the most part not deal breakers. 

But I have found that it takes ~56 seconds to boot to LDM. This machine has a dual core 6th gen i5, 8 gigs of ram, and an SSD. My old core duo can boot in 17 seconds so this made me curious. When I used $ systemd-analyze I am told the boot process finished in 8.139 seconds. Strange. Anyone have any ideas? Below I will append my dmesg results. I've only seen two things that took a lot of time and they both appear to be wifi related, which is curious as I have no issues with my wireless card. Googling the processes yielded little of help as they search results usually consisted of forum posts about getting their wireless cards to work.

```
[    0.000000] Initializing cgroup subsys cpuset[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 4.2.0-25-generic (buildd@lcy01-02) (gcc version 5.2.1 20151010 (Ubuntu 5.2.1-22ubuntu2) ) #30-Ubuntu SMP Mon Jan 18 12:31:50 UTC 2016 (Ubuntu 4.2.0-25.30-generic 4.2.6)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.2.0-25-generic root=UUID=1dacac5f-be89-45b1-8c3f-d7eebb9bd6d9 ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] x86/fpu: xstate_offset[2]: 0240, xstate_sizes[2]: 0100
[    0.000000] x86/fpu: xstate_offset[3]: 03c0, xstate_sizes[3]: 0040
[    0.000000] x86/fpu: xstate_offset[4]: 0400, xstate_sizes[4]: 0040
[    0.000000] x86/fpu: Supporting XSAVE feature 0x01: 'x87 floating point registers'
[    0.000000] x86/fpu: Supporting XSAVE feature 0x02: 'SSE registers'
[    0.000000] x86/fpu: Supporting XSAVE feature 0x04: 'AVX registers'
[    0.000000] x86/fpu: Supporting XSAVE feature 0x08: 'MPX bounds registers'
[    0.000000] x86/fpu: Supporting XSAVE feature 0x10: 'MPX CSR'
[    0.000000] x86/fpu: Enabled xstate features 0x1f, context size is 0x440 bytes, using 'standard' format.
[    0.000000] x86/fpu: Using 'eager' FPU context switches.
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009c7ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009c800-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000007a41dfff] usable
[    0.000000] BIOS-e820: [mem 0x000000007a41e000-0x000000007a41efff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000007a41f000-0x0000000087650fff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000087651000-0x0000000087f98fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x0000000087f99000-0x0000000087ffefff] ACPI data
[    0.000000] BIOS-e820: [mem 0x0000000088000000-0x00000000880fffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fe000000-0x00000000fe010fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x00000002727fffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.8 present.
[    0.000000] DMI: Dell Inc. Inspiron 13-7353/00FG87, BIOS 01.00.00 08/07/2015
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0x272800 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: write-back
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 00C0000000 mask 7FC0000000 uncachable
[    0.000000]   1 base 00A0000000 mask 7FE0000000 uncachable
[    0.000000]   2 base 0090000000 mask 7FF0000000 uncachable
[    0.000000]   3 base 008C000000 mask 7FFC000000 uncachable
[    0.000000]   4 base 008A000000 mask 7FFE000000 uncachable
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- WT  
[    0.000000] e820: last_pfn = 0x7a41e max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000fcdb0-0x000fcdbf] mapped at [ffff8800000fcdb0]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000096000] 96000 size 24576
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01ff0000, 0x01ff0fff] PGTABLE
[    0.000000] BRK [0x01ff1000, 0x01ff1fff] PGTABLE
[    0.000000] BRK [0x01ff2000, 0x01ff2fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x272600000-0x2727fffff]
[    0.000000]  [mem 0x272600000-0x2727fffff] page 2M
[    0.000000] BRK [0x01ff3000, 0x01ff3fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x260000000-0x2725fffff]
[    0.000000]  [mem 0x260000000-0x2725fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x240000000-0x25fffffff]
[    0.000000]  [mem 0x240000000-0x25fffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0x7a41dfff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x7a3fffff] page 2M
[    0.000000]  [mem 0x7a400000-0x7a41dfff] page 4k
[    0.000000] init_memory_mapping: [mem 0x100000000-0x23fffffff]
[    0.000000]  [mem 0x100000000-0x23fffffff] page 1G
[    0.000000] RAMDISK: [mem 0x33fa4000-0x35fc9fff]
[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x00000000000EF5C0 000024 (v02 DELL  )
[    0.000000] ACPI: XSDT 0x0000000087FD50B0 0000E4 (v01 DELL   CBX3     01072009 AMI  00010013)
[    0.000000] ACPI: FACP 0x0000000087FF3320 00010C (v05 DELL   CBX3     01072009 AMI  00010013)
[    0.000000] ACPI: DSDT 0x0000000087FD5228 01E0F7 (v02 DELL   CBX3     01072009 INTL 20120913)
[    0.000000] ACPI: FACS 0x0000000087F97F80 000040
[    0.000000] ACPI: APIC 0x0000000087FF3430 000084 (v03 DELL   CBX3     01072009 AMI  00010013)
[    0.000000] ACPI: FPDT 0x0000000087FF34B8 000044 (v01 DELL   CBX3     01072009 AMI  00010013)
[    0.000000] ACPI: FIDT 0x0000000087FF3500 00009C (v01 DELL   CBX3     01072009 AMI  00010013)
[    0.000000] ACPI: MCFG 0x0000000087FF35A0 00003C (v01 DELL   CBX3     01072009 MSFT 00000097)
[    0.000000] ACPI: HPET 0x0000000087FF35E0 000038 (v01 DELL   CBX3     01072009 AMI. 0005000B)
[    0.000000] ACPI: SSDT 0x0000000087FF3618 0003DA (v01 SataRe SataTabl 00001000 INTL 20120913)
[    0.000000] ACPI: LPIT 0x0000000087FF39F8 000094 (v01 INTEL  SKL-ULT  00000000 MSFT 0000005F)
[    0.000000] ACPI: SSDT 0x0000000087FF3A90 000248 (v02 INTEL  sensrhub 00000000 INTL 20120913)
[    0.000000] ACPI: SSDT 0x0000000087FF3CD8 000E9E (v02 INTEL  PtidDevc 00001000 INTL 20120913)
[    0.000000] ACPI: SSDT 0x0000000087FF4B78 000551 (v02 INTEL  Ther_Rvp 00001000 INTL 20120913)
[    0.000000] ACPI: DBGP 0x0000000087FF50D0 000034 (v01 INTEL           00000000 MSFT 0000005F)
[    0.000000] ACPI: DBG2 0x0000000087FF5108 000054 (v00 INTEL           00000000 MSFT 0000005F)
[    0.000000] ACPI: SSDT 0x0000000087FF5160 000770 (v02 INTEL  xh_rvp07 00000000 INTL 20120913)
[    0.000000] ACPI: BOOT 0x0000000087FF58D0 000028 (v01 DELL   CBX3     01072009 AMI  00010013)
[    0.000000] ACPI: SSDT 0x0000000087FF58F8 00352C (v02 SaSsdt SaSsdt   00003000 INTL 20120913)
[    0.000000] ACPI: UEFI 0x0000000087FF8E28 000042 (v01                 00000000      00000000)
[    0.000000] ACPI: SSDT 0x0000000087FF8E70 000E58 (v02 CpuRef CpuSsdt  00003000 INTL 20120913)
[    0.000000] ACPI: SSDT 0x0000000087FF9CC8 003720 (v02 DptfTa DptfTabl 00001000 INTL 20120913)
[    0.000000] ACPI: MSDM 0x0000000087FFD3E8 000055 (v03 DELL   CBX3     06222004 AMI  00010013)
[    0.000000] ACPI: SLIC 0x0000000087FFD440 000176 (v03 DELL   CBX3     01072009 MSFT 00010013)
[    0.000000] ACPI: DMAR 0x0000000087FFD5B8 0000F0 (v01 INTEL  SKL      00000001 INTL 00000001)
[    0.000000] ACPI: TPM2 0x0000000087FFD6A8 000034 (v03        Tpm2Tabl 00000001 AMI  00000000)
[    0.000000] ACPI: ASF! 0x0000000087FFD6E0 0000A5 (v32 INTEL   HCG     00000001 TFSM 000F4240)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x00000002727fffff]
[    0.000000] NODE_DATA(0) allocated [mem 0x2727f9000-0x2727fdfff]
[    0.000000]  [ffffea0000000000-ffffea0009dfffff] PMD -> [ffff88026a000000-ffff880271dfffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x0000000000001000-0x0000000000ffffff]
[    0.000000]   DMA32    [mem 0x0000000001000000-0x00000000ffffffff]
[    0.000000]   Normal   [mem 0x0000000100000000-0x00000002727fffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x0000000000001000-0x000000000009bfff]
[    0.000000]   node   0: [mem 0x0000000000100000-0x000000007a41dfff]
[    0.000000]   node   0: [mem 0x0000000100000000-0x00000002727fffff]
[    0.000000] Initmem setup node 0 [mem 0x0000000000001000-0x00000002727fffff]
[    0.000000] On node 0 totalpages: 2018233
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3995 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 7761 pages used for memmap
[    0.000000]   DMA32 zone: 496670 pages, LIFO batch:31
[    0.000000]   Normal zone: 23712 pages used for memmap
[    0.000000]   Normal zone: 1517568 pages, LIFO batch:31
[    0.000000] Reserving Intel graphics stolen memory at 0x8a800000-0x8c7fffff
[    0.000000] ACPI: PM-Timer IO Port: 0x1808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] high edge lint[0x1])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-119
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] smpboot: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009c000-0x0009cfff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009d000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x7a41e000-0x7a41efff]
[    0.000000] PM: Registered nosave memory: [mem 0x7a41f000-0x87650fff]
[    0.000000] PM: Registered nosave memory: [mem 0x87651000-0x87f98fff]
[    0.000000] PM: Registered nosave memory: [mem 0x87f99000-0x87ffefff]
[    0.000000] PM: Registered nosave memory: [mem 0x87fff000-0x87ffffff]
[    0.000000] PM: Registered nosave memory: [mem 0x88000000-0x880fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x88100000-0x8a7fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x8a800000-0x8c7fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x8c800000-0xdfffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfdffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfe000000-0xfe010fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfe011000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfedfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xfeffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xff000000-0xffffffff]
[    0.000000] e820: [mem 0x8c800000-0xdfffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] clocksource: refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645519600211568 ns
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 33 pages/cpu @ffff880272400000 s96728 r8192 d30248 u524288
[    0.000000] pcpu-alloc: s96728 r8192 d30248 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1986675
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.2.0-25-generic root=UUID=1dacac5f-be89-45b1-8c3f-d7eebb9bd6d9 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 7827700K/8072932K available (8148K kernel code, 1237K rwdata, 3800K rodata, 1460K init, 1292K bss, 245232K reserved, 0K cma-reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     Build-time adjustment of leaf fanout to 64.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
[    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=64, nr_cpu_ids=4
[    0.000000] NR_IRQS:16640 nr_irqs:1024 16
[    0.000000]     Offload RCU callbacks from all CPUs
[    0.000000]     Offload RCU callbacks from CPUs: 0-3.
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] clocksource: hpet: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 79635855245 ns
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Unable to calibrate against PIT
[    0.000000] tsc: using HPET reference calibration
[    0.000000] tsc: Detected 2400.025 MHz processor
[    0.000048] Calibrating delay loop (skipped), value calculated using timer frequency.. 4800.05 BogoMIPS (lpj=9600100)
[    0.000051] pid_max: default: 32768 minimum: 301
[    0.000054] ACPI: Core revision 20150619
[    0.031265] ACPI: All ACPI Tables successfully acquired
[    0.031283] Security Framework initialized
[    0.031292] AppArmor: AppArmor initialized
[    0.031293] Yama: becoming mindful.
[    0.031719] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.034114] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.035346] Mount-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.035368] Mountpoint-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.035591] Initializing cgroup subsys blkio
[    0.035594] Initializing cgroup subsys memory
[    0.035600] Initializing cgroup subsys devices
[    0.035602] Initializing cgroup subsys freezer
[    0.035604] Initializing cgroup subsys net_cls
[    0.035606] Initializing cgroup subsys perf_event
[    0.035607] Initializing cgroup subsys net_prio
[    0.035609] Initializing cgroup subsys hugetlb
[    0.035635] CPU: Physical Processor ID: 0
[    0.035636] CPU: Processor Core ID: 0
[    0.035640] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.035641] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.037289] mce: CPU supports 8 MCE banks
[    0.037304] CPU0: Thermal monitoring enabled (TM1)
[    0.037312] process: using mwait in idle threads
[    0.037315] Last level iTLB entries: 4KB 64, 2MB 8, 4MB 8
[    0.037316] Last level dTLB entries: 4KB 64, 2MB 0, 4MB 0, 1GB 4
[    0.037646] Freeing SMP alternatives memory: 28K (ffffffff81ea4000 - ffffffff81eab000)
[    0.039920] ftrace: allocating 30910 entries in 121 pages
[    0.051634] DMAR: Host address width 39
[    0.051637] DMAR: DRHD base: 0x000000fed90000 flags: 0x0
[    0.051646] DMAR: dmar0: reg_base_addr fed90000 ver 1:0 cap 1c0000c40660462 ecap 7e3ff0505e
[    0.051647] DMAR: DRHD base: 0x000000fed91000 flags: 0x1
[    0.051651] DMAR: dmar1: reg_base_addr fed91000 ver 1:0 cap d2008c40660462 ecap f050da
[    0.051653] DMAR: RMRR base: 0x000000875b3000 end: 0x000000875d2fff
[    0.051654] DMAR: RMRR base: 0x0000008a000000 end: 0x0000008c7fffff
[    0.051655] DMAR: ANDD device: 1 name: \_SB.PCI0.I2C0
[    0.051656] DMAR: ANDD device: 2 name: \_SB.PCI0.I2C1
[    0.051657] DMAR-IR: IOAPIC id 2 under DRHD base  0xfed91000 IOMMU 1
[    0.051658] DMAR-IR: HPET id 0 under DRHD base 0xfed91000
[    0.051659] DMAR-IR: x2apic is disabled because BIOS sets x2apic opt out bit.
[    0.051660] DMAR-IR: Use 'intremap=no_x2apic_optout' to override the BIOS setting.
[    0.053198] DMAR-IR: Enabled IRQ remapping in xapic mode
[    0.053199] x2apic: IRQ remapping doesn't support X2APIC mode
[    0.057205] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.096935] TSC deadline timer enabled
[    0.096939] smpboot: CPU0: Intel(R) Core(TM) i5-6200U CPU @ 2.30GHz (fam: 06, model: 4e, stepping: 03)
[    0.096965] Performance Events: PEBS fmt3+, 32-deep LBR, Skylake events, full-width counters, Intel PMU driver.
[    0.096990] ... version:                4
[    0.096990] ... bit width:              48
[    0.096991] ... generic registers:      4
[    0.096992] ... value mask:             0000ffffffffffff
[    0.096992] ... max period:             0000ffffffffffff
[    0.096993] ... fixed-purpose events:   3
[    0.096994] ... event mask:             000000070000000f
[    0.097707] x86: Booting SMP configuration:
[    0.097714] .... node  #0, CPUs:      #1
[    0.102644] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.102726]  #2 #3
[    0.112629] x86: Booted up 1 node, 4 CPUs
[    0.112634] smpboot: Total of 4 processors activated (19200.20 BogoMIPS)
[    0.116409] devtmpfs: initialized
[    0.118278] evm: security.selinux
[    0.118279] evm: security.SMACK64
[    0.118280] evm: security.SMACK64EXEC
[    0.118281] evm: security.SMACK64TRANSMUTE
[    0.118281] evm: security.SMACK64MMAP
[    0.118282] evm: security.ima
[    0.118283] evm: security.capability
[    0.118322] PM: Registering ACPI NVS region [mem 0x7a41e000-0x7a41efff] (4096 bytes)
[    0.118323] PM: Registering ACPI NVS region [mem 0x87651000-0x87f98fff] (9732096 bytes)
[    0.118503] clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
[    0.118582] pinctrl core: initialized pinctrl subsystem
[    0.118750] RTC time:  1:49:23, date: 02/03/16
[    0.118850] NET: Registered protocol family 16
[    0.128261] cpuidle: using governor ladder
[    0.132268] cpuidle: using governor menu
[    0.132304] Simple Boot Flag at 0x47 set to 0x80
[    0.132356] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.132357] ACPI: bus type PCI registered
[    0.132359] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.132427] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.132430] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.132441] PCI: Using configuration type 1 for base access
[    0.132447] dmi type 0xB1 record - unknown flag
[    0.136973] ACPI: Added _OSI(Module Device)
[    0.136974] ACPI: Added _OSI(Processor Device)
[    0.136975] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.136976] ACPI: Added _OSI(Processor Aggregator Device)
[    0.144223] ACPI: Executed 21 blocks of module-level executable AML code
[    0.149759] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.156280] ACPI: Dynamic OEM Table Load:
[    0.156286] ACPI: SSDT 0xFFFF880268479C00 00037F (v02 PmRef  Cpu0Cst  00003001 INTL 20120913)
[    0.157069] ACPI: Dynamic OEM Table Load:
[    0.157073] ACPI: SSDT 0xFFFF880268443000 00061E (v02 PmRef  Cpu0Ist  00003000 INTL 20120913)
[    0.158831] ACPI: Dynamic OEM Table Load:
[    0.158835] ACPI: SSDT 0xFFFF880268443800 0005AA (v02 PmRef  ApIst    00003000 INTL 20120913)
[    0.159784] ACPI: Dynamic OEM Table Load:
[    0.159787] ACPI: SSDT 0xFFFF880268508600 000119 (v02 PmRef  ApCst    00003000 INTL 20120913)
[    0.162099] ACPI : EC: EC started
[    0.164927] ACPI: Interpreter enabled
[    0.164936] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20150619/hwxface-580)
[    0.164944] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20150619/hwxface-580)
[    0.164965] ACPI: (supports S0 S3 S4 S5)
[    0.164966] ACPI: Using IOAPIC for interrupt routing
[    0.165000] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.166144] ACPI: Power Resource [PG00] (on)
[    0.166415] ACPI: Power Resource [PG01] (on)
[    0.166673] ACPI: Power Resource [PG02] (on)
[    0.168184] ACPI: Power Resource [WRST] (off)
[    0.168466] ACPI: Power Resource [WRST] (off)
[    0.168733] ACPI: Power Resource [WRST] (off)
[    0.169003] ACPI: Power Resource [WRST] (off)
[    0.169284] ACPI: Power Resource [WRST] (off)
[    0.169551] ACPI: Power Resource [WRST] (off)
[    0.169819] ACPI: Power Resource [WRST] (off)
[    0.170088] ACPI: Power Resource [WRST] (off)
[    0.170360] ACPI: Power Resource [WRST] (off)
[    0.170831] ACPI: Power Resource [WRST] (off)
[    0.171098] ACPI: Power Resource [WRST] (off)
[    0.171367] ACPI: Power Resource [WRST] (off)
[    0.171633] ACPI: Power Resource [WRST] (off)
[    0.171901] ACPI: Power Resource [WRST] (off)
[    0.172172] ACPI: Power Resource [WRST] (off)
[    0.172444] ACPI: Power Resource [WRST] (off)
[    0.172710] ACPI: Power Resource [WRST] (off)
[    0.172980] ACPI: Power Resource [WRST] (off)
[    0.173260] ACPI: Power Resource [WRST] (off)
[    0.173533] ACPI: Power Resource [WRST] (off)
[    0.183666] ACPI: Power Resource [FN00] (off)
[    0.184639] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[    0.184644] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.186023] acpi PNP0A08:00: _OSC: OS now controls [PCIeHotplug PME AER PCIeCapability]
[    0.186024] acpi PNP0A08:00: FADT indicates ASPM is unsupported, using BIOS configuration
[    0.186572] PCI host bridge to bus 0000:00
[    0.186574] pci_bus 0000:00: root bus resource [bus 00-fe]
[    0.186576] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7 window]
[    0.186578] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff window]
[    0.186579] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff window]
[    0.186580] pci_bus 0000:00: root bus resource [mem 0x8c800000-0xdfffffff window]
[    0.186581] pci_bus 0000:00: root bus resource [mem 0xfd000000-0xfe7fffff window]
[    0.186590] pci 0000:00:00.0: [8086:1904] type 00 class 0x060000
[    0.186695] pci 0000:00:02.0: [8086:1916] type 00 class 0x030000
[    0.186709] pci 0000:00:02.0: reg 0x10: [mem 0xde000000-0xdeffffff 64bit]
[    0.186715] pci 0000:00:02.0: reg 0x18: [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.186719] pci 0000:00:02.0: reg 0x20: [io  0xf000-0xf03f]
[    0.186823] pci 0000:00:04.0: [8086:1903] type 00 class 0x118000
[    0.186840] pci 0000:00:04.0: reg 0x10: [mem 0xdf120000-0xdf127fff 64bit]
[    0.187008] pci 0000:00:14.0: [8086:9d2f] type 00 class 0x0c0330
[    0.187037] pci 0000:00:14.0: reg 0x10: [mem 0xdf110000-0xdf11ffff 64bit]
[    0.187092] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    0.187170] pci 0000:00:14.0: System wakeup disabled by ACPI
[    0.187307] pci 0000:00:15.0: [8086:9d60] type 00 class 0x118000
[    0.187627] pci 0000:00:15.0: reg 0x10: [mem 0xdf137000-0xdf137fff 64bit]
[    0.188394] pci 0000:00:15.1: [8086:9d61] type 00 class 0x118000
[    0.188714] pci 0000:00:15.1: reg 0x10: [mem 0xdf136000-0xdf136fff 64bit]
[    0.189425] pci 0000:00:16.0: [8086:9d3a] type 00 class 0x078000
[    0.189480] pci 0000:00:16.0: reg 0x10: [mem 0xdf135000-0xdf135fff 64bit]
[    0.189569] pci 0000:00:16.0: PME# supported from D3hot
[    0.189667] pci 0000:00:17.0: [8086:9d03] type 00 class 0x010601
[    0.189692] pci 0000:00:17.0: reg 0x10: [mem 0xdf130000-0xdf131fff]
[    0.189700] pci 0000:00:17.0: reg 0x14: [mem 0xdf134000-0xdf1340ff]
[    0.189708] pci 0000:00:17.0: reg 0x18: [io  0xf090-0xf097]
[    0.189716] pci 0000:00:17.0: reg 0x1c: [io  0xf080-0xf083]
[    0.189724] pci 0000:00:17.0: reg 0x20: [io  0xf060-0xf07f]
[    0.189732] pci 0000:00:17.0: reg 0x24: [mem 0xdf133000-0xdf1337ff]
[    0.189759] pci 0000:00:17.0: PME# supported from D3hot
[    0.189873] pci 0000:00:1c.0: [8086:9d14] type 01 class 0x060400
[    0.189939] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.190023] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.190091] pci 0000:00:1f.0: [8086:9d48] type 00 class 0x060100
[    0.190293] pci 0000:00:1f.2: [8086:9d21] type 00 class 0x058000
[    0.190307] pci 0000:00:1f.2: reg 0x10: [mem 0xdf12c000-0xdf12ffff]
[    0.190452] pci 0000:00:1f.3: [8086:9d70] type 00 class 0x040300
[    0.190490] pci 0000:00:1f.3: reg 0x10: [mem 0xdf128000-0xdf12bfff 64bit]
[    0.190524] pci 0000:00:1f.3: reg 0x20: [mem 0xdf100000-0xdf10ffff 64bit]
[    0.190556] pci 0000:00:1f.3: PME# supported from D3hot D3cold
[    0.190676] pci 0000:00:1f.3: System wakeup disabled by ACPI
[    0.190714] pci 0000:00:1f.4: [8086:9d23] type 00 class 0x0c0500
[    0.190768] pci 0000:00:1f.4: reg 0x10: [mem 0xdf132000-0xdf1320ff 64bit]
[    0.190840] pci 0000:00:1f.4: reg 0x20: [io  0xf040-0xf05f]
[    0.191202] pci 0000:01:00.0: [8086:3165] type 00 class 0x028000
[    0.191311] pci 0000:01:00.0: reg 0x10: [mem 0xdf000000-0xdf001fff 64bit]
[    0.191551] pci 0000:01:00.0: PME# supported from D0 D3hot D3cold
[    0.191711] pci 0000:01:00.0: System wakeup disabled by ACPI
[    0.200798] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    0.200803] pci 0000:00:1c.0:   bridge window [mem 0xdf000000-0xdf0fffff]
[    0.202796] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.202847] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 *10 11 12 14 15)
[    0.202896] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.202945] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.202995] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.203044] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.203093] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.203139] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.205565] ACPI: Enabled 7 GPEs in block 00 to 7F
[    0.205648] ACPI : EC: GPE = 0x45, I/O: command/status = 0x934, data = 0x930
[    0.205740] vgaarb: setting as boot device: PCI:0000:00:02.0
[    0.205742] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.205758] vgaarb: loaded
[    0.205759] vgaarb: bridge control possible 0000:00:02.0
[    0.206002] SCSI subsystem initialized
[    0.206041] libata version 3.00 loaded.
[    0.206058] ACPI: bus type USB registered
[    0.206072] usbcore: registered new interface driver usbfs
[    0.206078] usbcore: registered new interface driver hub
[    0.206104] usbcore: registered new device driver usb
[    0.206227] PCI: Using ACPI for IRQ routing
[    0.235133] PCI: pci_cache_line_size set to 64 bytes
[    0.235499] e820: reserve RAM buffer [mem 0x0009c800-0x0009ffff]
[    0.235500] e820: reserve RAM buffer [mem 0x7a41e000-0x7bffffff]
[    0.235501] e820: reserve RAM buffer [mem 0x272800000-0x273ffffff]
[    0.235588] NetLabel: Initializing
[    0.235589] NetLabel:  domain hash size = 128
[    0.235590] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.235599] NetLabel:  unlabeled traffic allowed by default
[    0.235693] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.235697] hpet0: 8 comparators, 64-bit 24.000000 MHz counter
[    0.238765] clocksource: Switched to clocksource hpet
[    0.244020] AppArmor: AppArmor Filesystem Enabled
[    0.244079] pnp: PnP ACPI init
[    0.244262] system 00:00: [io  0x0680-0x069f] has been reserved
[    0.244264] system 00:00: [io  0xffff] has been reserved
[    0.244265] system 00:00: [io  0xffff] has been reserved
[    0.244266] system 00:00: [io  0xffff] has been reserved
[    0.244268] system 00:00: [io  0x1800-0x18fe] could not be reserved
[    0.244269] system 00:00: [io  0x164e-0x164f] has been reserved
[    0.244272] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.244344] pnp 00:01: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.244372] system 00:02: [io  0x1854-0x1857] has been reserved
[    0.244374] system 00:02: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.244528] pnp 00:03: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.244543] pnp 00:04: Plug and Play ACPI device, IDs DLL06fd PNP0f13 (active)
[    0.244701] system 00:05: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.244703] system 00:05: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.244704] system 00:05: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.244705] system 00:05: [mem 0xe0000000-0xefffffff] has been reserved
[    0.244707] system 00:05: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.244708] system 00:05: [mem 0xfed90000-0xfed93fff] could not be reserved
[    0.244709] system 00:05: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.244711] system 00:05: [mem 0xff000000-0xffffffff] has been reserved
[    0.244712] system 00:05: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.244713] system 00:05: [mem 0xdffe0000-0xdfffffff] has been reserved
[    0.244715] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.244743] system 00:06: [mem 0xfd000000-0xfdabffff] has been reserved
[    0.244744] system 00:06: [mem 0xfdad0000-0xfdadffff] has been reserved
[    0.244746] system 00:06: [mem 0xfdb00000-0xfdffffff] has been reserved
[    0.244747] system 00:06: [mem 0xfe000000-0xfe01ffff] could not be reserved
[    0.244749] system 00:06: [mem 0xfe036000-0xfe03bfff] has been reserved
[    0.244750] system 00:06: [mem 0xfe03d000-0xfe3fffff] has been reserved
[    0.244751] system 00:06: [mem 0xfe410000-0xfe7fffff] has been reserved
[    0.244753] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.245553] system 00:07: [mem 0xfe029000-0xfe029fff] has been reserved
[    0.245555] system 00:07: [mem 0xfe028000-0xfe028fff] has been reserved
[    0.245556] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.250408] pnp: PnP ACPI: found 8 devices
[    0.259497] clocksource: acpi_pm: mask: 0xffffff max_cycles: 0xffffff, max_idle_ns: 2085701024 ns
[    0.259518] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    0.259531] pci 0000:00:1c.0:   bridge window [mem 0xdf000000-0xdf0fffff]
[    0.259538] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7 window]
[    0.259539] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff window]
[    0.259541] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff window]
[    0.259542] pci_bus 0000:00: resource 7 [mem 0x8c800000-0xdfffffff window]
[    0.259543] pci_bus 0000:00: resource 8 [mem 0xfd000000-0xfe7fffff window]
[    0.259544] pci_bus 0000:01: resource 1 [mem 0xdf000000-0xdf0fffff]
[    0.259569] NET: Registered protocol family 2
[    0.259720] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
[    0.259901] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.260153] TCP: Hash tables configured (established 65536 bind 65536)
[    0.260183] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.260227] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.260309] NET: Registered protocol family 1
[    0.260322] pci 0000:00:02.0: Video device with shadowed ROM
[    0.261352] PCI: CLS 0 bytes, default 64
[    0.261394] Trying to unpack rootfs image as initramfs...
[    0.709911] Freeing initrd memory: 32920K (ffff880033fa4000 - ffff880035fca000)
[    0.709965] DMAR: ACPI device "device:64" under DMAR at fed91000 as 00:15.0
[    0.709968] DMAR: ACPI device "device:65" under DMAR at fed91000 as 00:15.1
[    0.709978] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.709980] software IO TLB [mem 0x7641e000-0x7a41e000] (64MB) mapped at [ffff88007641e000-ffff88007a41dfff]
[    0.710136] microcode: CPU0 sig=0x406e3, pf=0x80, revision=0x2d
[    0.710147] microcode: CPU1 sig=0x406e3, pf=0x80, revision=0x2d
[    0.710151] microcode: CPU2 sig=0x406e3, pf=0x80, revision=0x2d
[    0.710158] microcode: CPU3 sig=0x406e3, pf=0x80, revision=0x2d
[    0.710238] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.710317] Scanning for low memory corruption every 60 seconds
[    0.710751] futex hash table entries: 1024 (order: 4, 65536 bytes)
[    0.710774] Initialise system trusted keyring
[    0.710792] audit: initializing netlink subsys (disabled)
[    0.710808] audit: type=2000 audit(1454464163.712:1): initialized
[    0.711246] HugeTLB registered 1 GB page size, pre-allocated 0 pages
[    0.711247] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.712455] zpool: loaded
[    0.712458] zbud: loaded
[    0.712677] VFS: Disk quotas dquot_6.6.0
[    0.712704] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.713180] fuse init (API version 7.23)
[    0.713318] Key type big_key registered
[    0.714921] Key type asymmetric registered
[    0.714926] Asymmetric key parser 'x509' registered
[    0.714937] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 249)
[    0.715076] io scheduler noop registered
[    0.715078] io scheduler deadline registered (default)
[    0.715109] io scheduler cfq registered
[    0.715518] aer 0000:00:1c.0:pcie02: service driver aer loaded
[    0.715537] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
[    0.715538] pci 0000:01:00.0: Signaling PME through PCIe PME interrupt
[    0.715541] pcie_pme 0000:00:1c.0:pcie01: service driver pcie_pme loaded
[    0.715546] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.715551] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.715578] vesafb: mode is 1920x1080x32, linelength=7680, pages=0
[    0.715579] vesafb: scrolling: redraw
[    0.715580] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    0.715592] vesafb: framebuffer at 0xc0000000, mapped to 0xffffc90001000000, using 8128k, total 8128k
[    0.715718] Console: switching to colour frame buffer device 240x67
[    0.715736] fb0: VESA VGA frame buffer device
[    0.715749] intel_idle: MWAIT substates: 0x11142120
[    0.715750] intel_idle: v0.4 model 0x4E
[    0.715751] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.717818] ACPI: AC Adapter [AC] (off-line)
[    0.717878] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.718222] ACPI: Lid Switch [LID0]
[    0.718249] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.718252] ACPI: Power Button [PBTN]
[    0.718282] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
[    0.718284] ACPI: Sleep Button [SBTN]
[    0.718311] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.718313] ACPI: Power Button [PWRF]
[    0.720245] thermal LNXTHERM:00: registered as thermal_zone0
[    0.720246] ACPI: Thermal Zone [THM] (25 C)
[    0.720351] ACPI: Invalid active1 threshold
[    0.720436] thermal LNXTHERM:01: registered as thermal_zone1
[    0.720437] ACPI: Thermal Zone [TZ00] (28 C)
[    0.720520] thermal LNXTHERM:02: registered as thermal_zone2
[    0.720521] ACPI: Thermal Zone [TZ01] (30 C)
[    0.720557] GHES: HEST is not enabled!
[    0.720757] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.725452] Linux agpgart interface v0.103
[    0.728136] brd: module loaded
[    0.729888] loop: module loaded
[    0.730154] libphy: Fixed MDIO Bus: probed
[    0.730157] tun: Universal TUN/TAP device driver, 1.6
[    0.730158] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.730295] PPP generic driver version 2.4.2
[    0.730583] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.730589] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 1
[    0.731729] xhci_hcd 0000:00:14.0: hcc params 0x200077c1 hci version 0x100 quirks 0x00109810
[    0.731736] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    0.731854] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.731856] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.731858] usb usb1: Product: xHCI Host Controller
[    0.731860] usb usb1: Manufacturer: Linux 4.2.0-25-generic xhci-hcd
[    0.731862] usb usb1: SerialNumber: 0000:00:14.0
[    0.732121] hub 1-0:1.0: USB hub found
[    0.732142] hub 1-0:1.0: 12 ports detected
[    0.743879] ACPI: Battery Slot [BAT0] (battery present)
[    0.748810] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.748813] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 2
[    0.748840] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003
[    0.748841] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.748842] usb usb2: Product: xHCI Host Controller
[    0.748843] usb usb2: Manufacturer: Linux 4.2.0-25-generic xhci-hcd
[    0.748844] usb usb2: SerialNumber: 0000:00:14.0
[    0.749048] hub 2-0:1.0: USB hub found
[    0.749062] hub 2-0:1.0: 6 ports detected
[    0.751988] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.751992] ehci-pci: EHCI PCI platform driver
[    0.752000] ehci-platform: EHCI generic platform driver
[    0.752009] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.752012] ohci-pci: OHCI PCI platform driver
[    0.752018] ohci-platform: OHCI generic platform driver
[    0.752025] uhci_hcd: USB Universal Host Controller Interface driver
[    0.752062] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.752508] i8042: Warning: Keylock active
[    0.753922] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.753925] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.754339] mousedev: PS/2 mouse device common for all mice
[    0.755401] rtc_cmos 00:01: RTC can wake from S4
[    0.756056] rtc_cmos 00:01: rtc core: registered rtc_cmos as rtc0
[    0.756190] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.756249] rtc_cmos 00:01: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.756256] i2c /dev entries driver
[    0.756433] device-mapper: uevent: version 1.0.3
[    0.756575] device-mapper: ioctl: 4.33.0-ioctl (2015-8-18) initialised: dm-devel@redhat.com
[    0.756605] Intel P-state driver initializing.
[    0.756617] intel_pstate: HWP enabled
[    0.756640] intel_pstate: HWP enabled
[    0.756730] intel_pstate: HWP enabled
[    0.756773] intel_pstate: HWP enabled
[    0.756844] ledtrig-cpu: registered to indicate activity on CPUs
[    0.757558] PCCT header not found.
[    0.757782] NET: Registered protocol family 10
[    0.758179] NET: Registered protocol family 17
[    0.758191] Key type dns_resolver registered
[    0.758972] Loading compiled-in X.509 certificates
[    0.759631] Loaded X.509 cert 'Build time autogenerated kernel key: a41030fbdf1dc962b4bb7d1644c3337ec416db86'
[    0.759645] registered taskstats version 1
[    0.759661] zswap: loading zswap
[    0.759663] zswap: using zbud pool
[    0.759666] zswap: using lzo compressor
[    0.762375] Key type trusted registered
[    0.767409] Key type encrypted registered
[    0.767416] AppArmor: AppArmor sha1 policy hashing enabled
[    0.767420] ima: No TPM chip found, activating TPM-bypass!
[    0.767440] evm: HMAC attrs: 0x1
[    0.768626]   Magic number: 4:90:811
[    0.768941] rtc_cmos 00:01: setting system clock to 2016-02-03 01:49:23 UTC (1454464163)
[    0.769161] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.769161] EDD information not available.
[    0.769218] PM: Hibernation image not present or could not be loaded.
[    0.769710] Freeing unused kernel memory: 1460K (ffffffff81d37000 - ffffffff81ea4000)
[    0.769711] Write protecting the kernel read-only data: 12288k
[    0.770031] Freeing unused kernel memory: 32K (ffff8800017f8000 - ffff880001800000)
[    0.770208] Freeing unused kernel memory: 296K (ffff880001bb6000 - ffff880001c00000)
[    0.782634] random: systemd-udevd urandom read with 11 bits of entropy available
[    0.831162] hidraw: raw HID events driver (C) Jiri Kosina
[    0.833865] wmi: Mapper loaded
[    0.840640] ahci 0000:00:17.0: version 3.0
[    0.840868] ahci 0000:00:17.0: SSS flag set, parallel bus scan disabled
[    0.840900] ahci 0000:00:17.0: AHCI 0001.0301 32 slots 1 ports 6 Gbps 0x1 impl SATA mode
[    0.840904] ahci 0000:00:17.0: flags: 64bit ncq stag pm led clo only pio slum part deso sadm sds apst 
[    0.841335] scsi host0: ahci
[    0.841398] ata1: SATA max UDMA/133 abar m2048@0xdf133000 port 0xdf133100 irq 276
[    0.841796] [drm] Initialized drm 1.1.0 20060810
[    0.862059] [drm] Memory usable by graphics device = 4096M
[    0.863738] checking generic (c0000000 7f0000) vs hw (c0000000 10000000)
[    0.863739] fb: switching to inteldrmfb from VESA VGA
[    0.863769] Console: switching to colour dummy device 80x25
[    0.863905] [drm] Replacing VGA console driver
[    0.871553] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    0.871556] [drm] Driver supports precise vblank timestamp query.
[    0.875436] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    0.888588] fbcon: inteldrmfb (fb0) is primary device
[    0.888692] Console: switching to colour frame buffer device 240x67
[    0.888724] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[    0.888726] i915 0000:00:02.0: registered panic notifier
[    0.896366] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    0.897207] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input7
[    0.897424] [drm] Initialized i915 1.6.0 20150522 for 0000:00:02.0 on minor 0
[    1.115640] usb 1-4: new full-speed USB device number 2 using xhci_hcd
[    1.159561] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.161331] ata1.00: ATA-9: SAMSUNG SSD CM871 2.5 7mm 128GB, FXT01D1Q, max UDMA/133
[    1.161339] ata1.00: 250069680 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.162855] ata1.00: configured for UDMA/133
[    1.163294] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG SSD CM87 1D1Q PQ: 0 ANSI: 5
[    1.164118] sd 0:0:0:0: [sda] 250069680 512-byte logical blocks: (128 GB/119 GiB)
[    1.164501] sd 0:0:0:0: [sda] Write Protect is off
[    1.164509] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.164657] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.164684] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.168056]  sda: sda1 sda2
[    1.169162] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.248843] usb 1-4: New USB device found, idVendor=0483, idProduct=91d1
[    1.248846] usb 1-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.248847] usb 1-4: Product: ST_SENSOR_HUB
[    1.248849] usb 1-4: Manufacturer: STMicroelectronics
[    1.248850] usb 1-4: SerialNumber: ST_SENSOR_HUB
[    1.257091] usbcore: registered new interface driver usbhid
[    1.257093] usbhid: USB HID core driver
[    1.326295] psmouse serio1: elantech: assuming hardware version 4 (with firmware version 0x3a1f08)
[    1.326471] psmouse serio1: elantech: elantech_send_cmd query 0x02 failed.
[    1.326473] psmouse serio1: elantech: failed to query capabilities.
[    1.415801] usb 1-5: new high-speed USB device number 3 using xhci_hcd
[    1.582696] input: ImPS/2 Elantech Touchpad as /devices/platform/i8042/serio1/input/input6
[    1.658578] usb 1-5: New USB device found, idVendor=1bcf, idProduct=28aa
[    1.658585] usb 1-5: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.658589] usb 1-5: Product: Integrated_Webcam_HD
[    1.658593] usb 1-5: Manufacturer: CN0GNXH5724875AUB936A02
[    1.708081] tsc: Refined TSC clocksource calibration: 2400.000 MHz
[    1.708090] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x22983777dd9, max_idle_ns: 440795300422 ns
[    1.896255] usb 1-7: new full-speed USB device number 4 using xhci_hcd
[    2.083725] usb 1-7: New USB device found, idVendor=04f3, idProduct=228b
[    2.083733] usb 1-7: New USB device strings: Mfr=4, Product=14, SerialNumber=0
[    2.083738] usb 1-7: Product: Touchscreen
[    2.083742] usb 1-7: Manufacturer: ELAN
[    2.084102] usb 1-7: ep 0x2 - rounding interval to 64 microframes, ep desc says 80 microframes
[    2.256521] usb 1-8: new full-speed USB device number 5 using xhci_hcd
[    2.442835] usb 1-8: New USB device found, idVendor=8087, idProduct=0a2a
[    2.442843] usb 1-8: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.709207] clocksource: Switched to clocksource tsc
[    2.773174] [drm] RC6 on
[    6.340564] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[    6.464335] systemd[1]: Failed to insert module 'kdbus': Function not implemented
[    6.474854] systemd[1]: systemd 225 running in system mode. (+PAM +AUDIT +SELINUX +IMA +APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT +GNUTLS +ACL +XZ -LZ4 +SECCOMP +BLKID -ELFUTILS +KMOD -IDN)
[    6.475265] systemd[1]: Detected architecture x86-64.
[    6.475543] systemd[1]: Set hostname to <l>.
[    6.552353] systemd[1]: fancontrol.service: Cannot add dependency job, ignoring: Unit fancontrol.service is masked.
[    6.552703] systemd[1]: Reached target Remote File Systems (Pre).
[    6.552757] systemd[1]: Created slice Root Slice.
[    6.552785] systemd[1]: Listening on udev Control Socket.
[    6.552817] systemd[1]: Listening on Journal Socket.
[    6.552930] systemd[1]: Created slice User and Session Slice.
[    6.552952] systemd[1]: Listening on /dev/initctl Compatibility Named Pipe.
[    6.552964] systemd[1]: Listening on fsck to fsckd communication Socket.
[    6.552988] systemd[1]: Started Forward Password Requests to Wall Directory Watch.
[    6.553038] systemd[1]: Created slice System Slice.
[    6.555291] systemd[1]: Starting Load Kernel Modules...
[    6.555670] systemd[1]: Mounting Debug File System...
[    6.556022] systemd[1]: Starting Uncomplicated firewall...
[    6.556413] systemd[1]: Mounting POSIX Message Queue File System...
[    6.556972] systemd[1]: Starting Create list of required static device nodes for the current kernel...
[    6.557183] systemd[1]: Set up automount Arbitrary Executable File Formats File System Automount Point.
[    6.557243] systemd[1]: Listening on Journal Socket (/dev/log).
[    6.557744] systemd[1]: Mounting Huge Pages File System...
[    6.558257] systemd[1]: Starting Setup Virtual Console...
[    6.558280] systemd[1]: Reached target Slices.
[    6.558384] systemd[1]: Created slice system-getty.slice.
[    6.558495] systemd[1]: Created slice system-systemd\x2dcryptsetup.slice.
[    6.559003] systemd[1]: Started Braille Device Support.
[    6.559407] systemd[1]: Reached target User and Group Name Lookups.
[    6.559927] systemd[1]: Started Read required files in advance.
[    6.560032] systemd[1]: Listening on udev Kernel Socket.
[    6.560687] systemd[1]: Starting udev Coldplug all Devices...
[    6.563463] systemd[1]: Listening on Journal Audit Socket.
[    6.563876] systemd[1]: Starting Increase datagram queue length...
[    6.564618] systemd[1]: Started Uncomplicated firewall.
[    6.564839] systemd[1]: Started Create list of required static device nodes for the current kernel.
[    6.564985] systemd[1]: Started Setup Virtual Console.
[    6.567111] systemd[1]: Mounted Huge Pages File System.
[    6.567192] systemd[1]: Mounted POSIX Message Queue File System.
[    6.568001] systemd[1]: Mounted Debug File System.
[    6.568598] systemd[1]: Started Increase datagram queue length.
[    6.574868] lp: driver loaded but no devices found
[    6.577630] ppdev: user-space parallel port driver
[    6.578563] systemd[1]: Listening on Syslog Socket.
[    6.579107] systemd[1]: Starting Journal Service...
[    6.579655] systemd[1]: Starting Create Static Device Nodes in /dev...
[    6.581317] systemd[1]: Started Load Kernel Modules.
[    6.582563] systemd[1]: Starting Apply Kernel Variables...
[    6.583158] systemd[1]: Mounting FUSE Control File System...
[    6.585540] systemd[1]: Mounted FUSE Control File System.
[    6.591898] systemd[1]: Started Apply Kernel Variables.
[    6.597879] systemd[1]: Started Create Static Device Nodes in /dev.
[    6.598522] systemd[1]: Starting udev Kernel Device Manager...
[    6.606796] systemd[1]: Started Journal Service.
[    6.643828] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
[    6.669989] systemd-journald[286]: Received request to flush runtime journal from PID 1
[    6.736095] resource sanity check: requesting [mem 0xfed40040-0xfed4103f], which spans more than MSFT0101:00 [mem 0xfed40000-0xfed4087f]
[    6.736098] ------------[ cut here ]------------
[    6.736103] WARNING: CPU: 2 PID: 430 at /build/linux-ZKbhxl/linux-4.2.0/arch/x86/mm/ioremap.c:198 __ioremap_caller+0x2c5/0x380()
[    6.736104] Info: mapping multiple BARs. Your kernel is fine.
[    6.736105] Modules linked in:
[    6.736107]  tpm_crb(+) int3400_thermal(+) acpi_als acpi_thermal_rel acpi_pad kfifo_buf mac_hid industrialio parport_pc ppdev lp parport autofs4 hid_sensor_custom hid_sensor_hub usbhid i915 psmouse i2c_algo_bit drm_kms_helper drm ahci libahci wmi i2c_hid hid pinctrl_sunrisepoint video pinctrl_intel
[    6.736123] CPU: 2 PID: 430 Comm: systemd-udevd Not tainted 4.2.0-25-generic #30-Ubuntu
[    6.736125] Hardware name: Dell Inc. Inspiron 13-7353/00FG87, BIOS 01.00.00 08/07/2015
[    6.736127]  0000000000000000 00000000b12694ab ffff880074d4b948 ffffffff817e94c9
[    6.736130]  0000000000000000 ffff880074d4b9a0 ffff880074d4b988 ffffffff8107b3d6
[    6.736132]  ffff880074d4b9b8 00000000fed40040 ffffc90000ce0040 0000000000001000
[    6.736135] Call Trace:
[    6.736139]  [<ffffffff817e94c9>] dump_stack+0x45/0x57
[    6.736143]  [<ffffffff8107b3d6>] warn_slowpath_common+0x86/0xc0
[    6.736146]  [<ffffffff8107b465>] warn_slowpath_fmt+0x55/0x70
[    6.736149]  [<ffffffff81067c15>] __ioremap_caller+0x2c5/0x380
[    6.736152]  [<ffffffff81067ce7>] ioremap_nocache+0x17/0x20
[    6.736155]  [<ffffffff813df5ad>] devm_ioremap_nocache+0x3d/0x80
[    6.736159]  [<ffffffffc029e235>] crb_acpi_add+0x105/0x2c0 [tpm_crb]
[    6.736162]  [<ffffffff8145a9f4>] acpi_device_probe+0x50/0xf7
[    6.736165]  [<ffffffff81520eba>] driver_probe_device+0x21a/0x490
[    6.736167]  [<ffffffff815211c0>] __driver_attach+0x90/0xa0
[    6.736169]  [<ffffffff81521130>] ? driver_probe_device+0x490/0x490
[    6.736172]  [<ffffffff8151ea5c>] bus_for_each_dev+0x6c/0xc0
[    6.736174]  [<ffffffff8152065e>] driver_attach+0x1e/0x20
[    6.736177]  [<ffffffff8152018b>] bus_add_driver+0x1eb/0x280
[    6.736179]  [<ffffffffc02a3000>] ? 0xffffffffc02a3000
[    6.736182]  [<ffffffff81521a60>] driver_register+0x60/0xe0
[    6.736184]  [<ffffffff8145b21f>] acpi_bus_register_driver+0x3b/0x43
[    6.736187]  [<ffffffffc02a3010>] crb_acpi_driver_init+0x10/0x1000 [tpm_crb]
[    6.736190]  [<ffffffff81002123>] do_one_initcall+0xb3/0x200
[    6.736193]  [<ffffffff811de1d7>] ? kmem_cache_alloc_trace+0x187/0x1f0
[    6.736195]  [<ffffffff817e6f88>] ? do_init_module+0x28/0x1e7
[    6.736197]  [<ffffffff817e6fc0>] do_init_module+0x60/0x1e7
[    6.736200]  [<ffffffff81102976>] load_module+0x1676/0x1c10
[    6.736203]  [<ffffffff810feac0>] ? __symbol_put+0x60/0x60
[    6.736206]  [<ffffffff81203170>] ? kernel_read+0x50/0x80
[    6.736209]  [<ffffffff81103169>] SyS_finit_module+0xb9/0xf0
[    6.736212]  [<ffffffff817f02b2>] entry_SYSCALL_64_fastpath+0x16/0x75
[    6.736214] ---[ end trace a27d9992dca6c95e ]---
[    6.736216] ACPI Warning: \_SB_.IETM._ART: Return Package type mismatch at index 0 - found Integer, expected Reference (20150619/nspredef-297)
[    6.736220] tpm_crb MSFT0101:00: ioremap of the command buffer failed
[    6.736222] ACPI: Invalid package element [0]: got number, expecting [R]
[    6.736224] _ART package 0 is invalid, ignored
[    6.736226] tpm_crb: probe of MSFT0101:00 failed with error -12
[    6.742770] random: nonblocking pool is initialized
[    6.745293] audit: type=1400 audit(1454464169.466:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=463 comm="apparmor_parser"
[    6.745300] audit: type=1400 audit(1454464169.466:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=463 comm="apparmor_parser"
[    6.747304] audit: type=1400 audit(1454464169.466:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=463 comm="apparmor_parser"
[    6.747311] audit: type=1400 audit(1454464169.466:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=463 comm="apparmor_parser"
[    6.747316] audit: type=1400 audit(1454464169.466:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=463 comm="apparmor_parser"
[    6.747320] audit: type=1400 audit(1454464169.466:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=463 comm="apparmor_parser"
[    6.757924] audit: type=1400 audit(1454464169.478:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince" pid=463 comm="apparmor_parser"
[    6.757932] audit: type=1400 audit(1454464169.478:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=463 comm="apparmor_parser"
[    6.757937] audit: type=1400 audit(1454464169.478:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince-previewer" pid=463 comm="apparmor_parser"
[    6.757941] audit: type=1400 audit(1454464169.478:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=463 comm="apparmor_parser"
[    6.804599] intel-lpss 0000:00:15.0: enabling device (0000 -> 0002)
[    6.806488] Bluetooth: Core ver 2.20
[    6.806501] NET: Registered protocol family 31
[    6.806502] Bluetooth: HCI device and connection manager initialized
[    6.806506] Bluetooth: HCI socket layer initialized
[    6.806508] Bluetooth: L2CAP socket layer initialized
[    6.806513] Bluetooth: SCO socket layer initialized
[    6.813288] idma64 idma64.0: Found Intel integrated DMA 64-bit
[    6.813562] usbcore: registered new interface driver btusb
[    6.822001] media: Linux media interface: v0.10
[    6.829986] input: ELAN Touchscreen as /devices/pci0000:00/0000:00:14.0/usb1/1-7/1-7:1.0/0003:04F3:228B.0002/input/input8
[    6.830288] hid-multitouch 0003:04F3:228B.0002: input,hiddev0,hidraw0: USB HID v1.10 Device [ELAN Touchscreen] on usb-0000:00:14.0-7/input0
[    6.831007] Bluetooth: hci0: read Intel version: 370810011003110e00
[    6.831503] Linux video capture interface: v2.00
[    6.844235] uvcvideo: Found UVC 1.00 device Integrated_Webcam_HD (1bcf:28aa)
[    6.844779] intel-lpss 0000:00:15.1: enabling device (0000 -> 0002)
[    6.844978] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.8.10-fw-1.10.3.11.e.bseq
[    6.845100] idma64 idma64.1: Found Intel integrated DMA 64-bit
[    6.852841] input: Integrated_Webcam_HD as /devices/pci0000:00/0000:00:14.0/usb1/1-5/1-5:1.0/input/input10
[    6.852910] usbcore: registered new interface driver uvcvideo
[    6.852912] USB Video Class driver (1.1.1)
[    6.860113] mei_me 0000:00:16.0: enabling device (0000 -> 0002)
[    6.865396] AVX2 version of gcm_enc/dec engaged.
[    6.865397] AES CTR mode by8 optimization enabled
[    6.870690] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    6.942736] snd_hda_intel 0000:00:1f.3: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
[    6.944739] Intel(R) Wireless WiFi driver for Linux
[    6.944741] Copyright(c) 2003- 2015 Intel Corporation
[    6.946916] iwlwifi 0000:01:00.0: Unsupported splx structure
[    6.947632] iwlwifi 0000:01:00.0: Direct firmware load for iwlwifi-7265D-15.ucode failed with error -2
[    6.947647] iwlwifi 0000:01:00.0: Direct firmware load for iwlwifi-7265D-14.ucode failed with error -2
[    6.951965] iwlwifi 0000:01:00.0: loaded firmware version 25.30.13.0 op_mode iwlmvm
[    6.961247] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[    6.985622] snd_hda_codec_conexant hdaudioC0D0: CX20722: BIOS auto-probing.
[    6.986003] snd_hda_codec_conexant hdaudioC0D0: autoconfig for CX20722: line_outs=1 (0x17/0x0/0x0/0x0/0x0) type:speaker
[    6.986006] snd_hda_codec_conexant hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    6.986009] snd_hda_codec_conexant hdaudioC0D0:    hp_outs=1 (0x16/0x0/0x0/0x0/0x0)
[    6.986010] snd_hda_codec_conexant hdaudioC0D0:    mono: mono_out=0x0
[    6.986012] snd_hda_codec_conexant hdaudioC0D0:    inputs:
[    6.986014] snd_hda_codec_conexant hdaudioC0D0:      Internal Mic=0x1a
[    6.986016] snd_hda_codec_conexant hdaudioC0D0:      Mic=0x19
[    6.986617] intel_rapl: Found RAPL domain package
[    6.986619] intel_rapl: Found RAPL domain core
[    6.986621] intel_rapl: Found RAPL domain uncore
[    6.986623] intel_rapl: Found RAPL domain dram
[    6.986798] input: Dell WMI hotkeys as /devices/virtual/input/input11
[    6.987010] snd_hda_codec_conexant hdaudioC0D0: Enable sync_write for stable communication
[    6.989202] iwlwifi 0000:01:00.0: Detected Intel(R) Dual Band Wireless AC 3165, REV=0x210
[    6.990073] iwlwifi 0000:01:00.0: L1 Enabled - LTR Enabled
[    6.990515] iwlwifi 0000:01:00.0: L1 Enabled - LTR Enabled
[    6.999509] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1f.3/sound/card0/input12
[    6.999559] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1f.3/sound/card0/input13
[    6.999608] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input14
[    6.999651] input: HDA Intel PCH HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input15
[    6.999695] input: HDA Intel PCH HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input16
[    7.036553] cfg80211: World regulatory domain updated:
[    7.036556] cfg80211:  DFS Master region: unset
[    7.036557] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[    7.036558] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[    7.036559] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[    7.036560] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
[    7.036562] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
[    7.036563] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
[    7.036564] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
[    7.036565] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
[    7.036566] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
[    7.046923] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[    7.052597] i2c_hid i2c-DLL06FE:00: error in i2c_hid_init_report size:633 / ret_size:7
[    7.055176] i2c_hid i2c-DLL06FE:00: error in i2c_hid_init_report size:69 / ret_size:7
[    7.059421] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    7.062777] iwlwifi 0000:01:00.0 wlp1s0: renamed from wlan0
[    7.065732] input: DLL06FE:00 04F3:300F UNKNOWN as /devices/pci0000:00/0000:00:15.0/i2c_designware.0/i2c-4/i2c-DLL06FE:00/0018:04F3:300F.0003/input/input17
[    7.065840] hid-multitouch 0018:04F3:300F.0003: input,hidraw1: <UNKNOWN> HID v1.00 Mouse [DLL06FE:00 04F3:300F] on 
[    7.275002] Adding 998908k swap on /dev/mapper/cryptswap1.  Priority:-1 extents:1 across:998908k SSFS
[    7.362552] ACPI: Invalid package element [0]: got number, expecting [R]
[    7.362559] _ART package 0 is invalid, ignored
[    7.362616] ACPI: Invalid package element [0]: got number, expecting [R]
[    7.362620] _ART package 0 is invalid, ignored
[    7.392881] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    7.392885] Bluetooth: BNEP filters: protocol multicast
[    7.392889] Bluetooth: BNEP socket layer initialized
[    7.532230] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready
[    7.532753] iwlwifi 0000:01:00.0: L1 Enabled - LTR Enabled
[    7.533190] iwlwifi 0000:01:00.0: L1 Enabled - LTR Enabled
[    7.593984] iwlwifi 0000:01:00.0: L1 Enabled - LTR Enabled
[    7.594530] iwlwifi 0000:01:00.0: L1 Enabled - LTR Enabled
[    7.615528] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready
[    7.768036] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready
[   10.888206] wlp1s0: authenticate with ac:a3:1e:61:79:01
[   10.896514] wlp1s0: send auth to ac:a3:1e:61:79:01 (try 1/3)
[   10.907985] wlp1s0: authenticated
[   10.911232] wlp1s0: associate with ac:a3:1e:61:79:01 (try 1/3)
[   10.918827] wlp1s0: RX AssocResp from ac:a3:1e:61:79:01 (capab=0x431 status=0 aid=2)
[   10.920092] wlp1s0: associated
[   10.920131] IPv6: ADDRCONF(NETDEV_CHANGE): wlp1s0: link becomes ready
[   36.025417] wlp1s0: deauthenticating from ac:a3:1e:61:79:01 by local choice (Reason: 3=DEAUTH_LEAVING)
[   36.953639] wlp1s0: authenticate with ac:a3:1e:61:79:01
[   36.959128] wlp1s0: send auth to ac:a3:1e:61:79:01 (try 1/3)
[   37.067863] wlp1s0: send auth to ac:a3:1e:61:79:01 (try 2/3)
[   37.179975] wlp1s0: send auth to ac:a3:1e:61:79:01 (try 3/3)
[   37.182623] wlp1s0: authenticated
[   37.183635] wlp1s0: associate with ac:a3:1e:61:79:01 (try 1/3)
[   37.187962] wlp1s0: RX AssocResp from ac:a3:1e:61:79:01 (capab=0x431 status=0 aid=2)
[   37.192169] wlp1s0: associated
[   61.047325] wlp1s0: deauthenticating from ac:a3:1e:61:79:01 by local choice (Reason: 3=DEAUTH_LEAVING)
[   62.091750] wlp1s0: authenticate with ac:a3:1e:61:6a:11
[   62.099255] wlp1s0: send auth to ac:a3:1e:61:6a:11 (try 1/3)
[   62.101147] wlp1s0: authenticated
[   62.103155] wlp1s0: associate with ac:a3:1e:61:6a:11 (try 1/3)
[   62.106988] wlp1s0: RX AssocResp from ac:a3:1e:61:6a:11 (capab=0x411 status=0 aid=1)
[   62.116848] wlp1s0: associated
[   81.166677] wlp1s0: authenticate with ac:a3:1e:61:79:01
[   81.174241] wlp1s0: send auth to ac:a3:1e:61:79:01 (try 1/3)
[   81.177696] wlp1s0: authenticated
[   81.181975] wlp1s0: associate with ac:a3:1e:61:79:01 (try 1/3)
[   81.186533] wlp1s0: RX AssocResp from ac:a3:1e:61:79:01 (capab=0x431 status=0 aid=2)
[   81.193317] wlp1s0: associated
[  373.527373] wlp1s0: authenticate with ac:a3:1e:61:6a:11
[  373.534229] wlp1s0: send auth to ac:a3:1e:61:6a:11 (try 1/3)
[  373.536044] wlp1s0: authenticated
[  373.541237] wlp1s0: associate with ac:a3:1e:61:6a:11 (try 1/3)
[  373.544983] wlp1s0: RX AssocResp from ac:a3:1e:61:6a:11 (capab=0x411 status=0 aid=5)
[  373.545540] wlp1s0: associated
[  404.791463] wlp1s0: authenticate with ac:a3:1e:61:79:01
[  404.797466] wlp1s0: send auth to ac:a3:1e:61:79:01 (try 1/3)
[  404.803719] wlp1s0: authenticated
[  404.808786] wlp1s0: associate with ac:a3:1e:61:79:01 (try 1/3)
[  404.813905] wlp1s0: RX AssocResp from ac:a3:1e:61:79:01 (capab=0x431 status=0 aid=2)
[  404.814967] wlp1s0: associated
[  493.687412] wlp1s0: authenticate with ac:a3:1e:61:6a:11
[  493.696875] wlp1s0: send auth to ac:a3:1e:61:6a:11 (try 1/3)
[  493.698815] wlp1s0: authenticated
[  493.699816] wlp1s0: associate with ac:a3:1e:61:6a:11 (try 1/3)
[  493.703326] wlp1s0: RX AssocResp from ac:a3:1e:61:6a:11 (capab=0x411 status=0 aid=3)
[  493.703961] wlp1s0: associated
[  507.381539] dell_wmi: Unknown WMI event type 0x00: 0xe005
[  507.381542] dell_wmi: Unknown WMI event type 0x00: 0xf
[  613.702135] wlp1s0: authenticate with ac:a3:1e:61:79:01
[  613.708374] wlp1s0: send auth to ac:a3:1e:61:79:01 (try 1/3)
[  613.711584] wlp1s0: authenticated
[  613.713139] wlp1s0: associate with ac:a3:1e:61:79:01 (try 1/3)
[  613.718537] wlp1s0: RX AssocResp from ac:a3:1e:61:79:01 (capab=0x431 status=0 aid=2)
[  613.719618] wlp1s0: associated



```

---

