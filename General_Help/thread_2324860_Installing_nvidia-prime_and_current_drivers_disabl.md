---
title: "Installing nvidia-prime and current drivers disables my login"
date: 2016-05-17
forum: General Help
---

### Post by Toast2120 on 2016-05-17
After installing the current nvidia-current drivers (361.42) and by default the nvidia-prime I can no longer login to my desktop. In fact the login is disabled so the system logs in for me but after installing I can no longer get to my desktop. I've tried a reinstall of Unity, compiz, and lightdm.

Specs:
[http://www.gigabyte.com/products/product-page.aspx?pid=5452#sp](http://www.gigabyte.com/products/product-page.aspx?pid=5452#sp)

dmesg below

```
[    0.000000] microcode: CPU0 microcode updated early to revision 0x13, date = 2015-08-03
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 4.4.0-22-generic (buildd@lgw01-41) (gcc version 5.3.1 20160413 (Ubuntu 5.3.1-14ubuntu2) ) #40-Ubuntu SMP Thu May 12 22:03:46 UTC 2016 (Ubuntu 4.4.0-22.40-generic 4.4.8)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-22-generic root=UUID=a35e04a1-3b9c-46b3-b722-2539da2dde9a ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] x86/fpu: xstate_offset[2]:  576, xstate_sizes[2]:  256
[    0.000000] x86/fpu: Supporting XSAVE feature 0x01: 'x87 floating point registers'
[    0.000000] x86/fpu: Supporting XSAVE feature 0x02: 'SSE registers'
[    0.000000] x86/fpu: Supporting XSAVE feature 0x04: 'AVX registers'
[    0.000000] x86/fpu: Enabled xstate features 0x7, context size is 832 bytes, using 'standard' format.
[    0.000000] x86/fpu: Using 'eager' FPU context switches.
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009c7ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009c800-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x0000000098839fff] usable
[    0.000000] BIOS-e820: [mem 0x000000009883a000-0x0000000098aeafff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000098aeb000-0x000000009bab2fff] usable
[    0.000000] BIOS-e820: [mem 0x000000009bab3000-0x000000009bb9bfff] reserved
[    0.000000] BIOS-e820: [mem 0x000000009bb9c000-0x000000009bbc3fff] ACPI data
[    0.000000] BIOS-e820: [mem 0x000000009bbc4000-0x000000009cccefff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000009cccf000-0x000000009cffefff] reserved
[    0.000000] BIOS-e820: [mem 0x000000009cfff000-0x000000009cffffff] usable
[    0.000000] BIOS-e820: [mem 0x000000009d800000-0x000000009fffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed03fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000045effffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.8 present.
[    0.000000] DMI: GIGABYTE P34V4/P34V4, BIOS FB03 06/23/2015
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0x45f000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask 7F80000000 write-back
[    0.000000]   1 base 0080000000 mask 7FF0000000 write-back
[    0.000000]   2 base 0090000000 mask 7FF8000000 write-back
[    0.000000]   3 base 0098000000 mask 7FFC000000 write-back
[    0.000000]   4 base 009C000000 mask 7FFF000000 write-back
[    0.000000]   5 base 0100000000 mask 7F00000000 write-back
[    0.000000]   6 base 0200000000 mask 7E00000000 write-back
[    0.000000]   7 base 0400000000 mask 7F80000000 write-back
[    0.000000]   8 base 0460000000 mask 7FE0000000 uncachable
[    0.000000]   9 base 045F000000 mask 7FFF000000 uncachable
[    0.000000] x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- WT  
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 256MB, type WB
[    0.000000] reg 2, base: 2304MB, range: 128MB, type WB
[    0.000000] reg 3, base: 2432MB, range: 64MB, type WB
[    0.000000] reg 4, base: 2496MB, range: 16MB, type WB
[    0.000000] reg 5, base: 4GB, range: 4GB, type WB
[    0.000000] reg 6, base: 8GB, range: 8GB, type WB
[    0.000000] reg 7, base: 16GB, range: 2GB, type WB
[    0.000000] reg 8, base: 17920MB, range: 512MB, type UC
[    0.000000] reg 9, base: 17904MB, range: 16MB, type UC
[    0.000000] total RAM covered: 16320M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K 	chunk_size: 64M 	num_reg: 9  	lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 512MB, type WB
[    0.000000] reg 2, base: 2512MB, range: 16MB, type UC
[    0.000000] reg 3, base: 2528MB, range: 32MB, type UC
[    0.000000] reg 4, base: 4GB, range: 4GB, type WB
[    0.000000] reg 5, base: 8GB, range: 8GB, type WB
[    0.000000] reg 6, base: 16GB, range: 1GB, type WB
[    0.000000] reg 7, base: 17GB, range: 512MB, type WB
[    0.000000] reg 8, base: 17904MB, range: 16MB, type UC
[    0.000000] e820: update [mem 0x9d000000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0x9d000 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000fd8f0-0x000fd8ff] mapped at [ffff8800000fd8f0]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000096000] 96000 size 24576
[    0.000000] Using GB pages for direct mapping
[    0.000000] BRK [0x021ff000, 0x021fffff] PGTABLE
[    0.000000] BRK [0x02200000, 0x02200fff] PGTABLE
[    0.000000] BRK [0x02201000, 0x02201fff] PGTABLE
[    0.000000] BRK [0x02202000, 0x02202fff] PGTABLE
[    0.000000] BRK [0x02203000, 0x02203fff] PGTABLE
[    0.000000] BRK [0x02204000, 0x02204fff] PGTABLE
[    0.000000] RAMDISK: [mem 0x33c88000-0x35e3bfff]
[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x00000000000F0580 000024 (v02 GBT   )
[    0.000000] ACPI: XSDT 0x000000009BBA4098 0000B4 (v01 GBT    GBTUACPI 01072009 AMI  00010013)
[    0.000000] ACPI: FACP 0x000000009BBB9D70 00010C (v05 GBT    GBTUACPI 01072009 AMI  00010013)
[    0.000000] ACPI: DSDT 0x000000009BBA41E0 015B8C (v02 GBT    GBTUACPI 01072009 INTL 20120913)
[    0.000000] ACPI: FACS 0x000000009CCCDF80 000040
[    0.000000] ACPI: APIC 0x000000009BBB9E80 0000BC (v03 GBT    GBTUACPI 01072009 AMI  00010013)
[    0.000000] ACPI: FPDT 0x000000009BBB9F40 000044 (v01 GBT    GBTUACPI 01072009 AMI  00010013)
[    0.000000] ACPI: FIDT 0x000000009BBB9F88 00009C (v01 GBT    GBTUACPI 01072009 AMI  00010013)
[    0.000000] ACPI: MCFG 0x000000009BBBA028 00003C (v01 GBT    GBTUACPI 01072009 MSFT 00000097)
[    0.000000] ACPI: HPET 0x000000009BBBA068 000038 (v01 GBT    GBTUACPI 01072009 AMI. 0005000B)
[    0.000000] ACPI: SSDT 0x000000009BBBA0A0 000315 (v01 SataRe SataTabl 00001000 INTL 20120913)
[    0.000000] ACPI: UEFI 0x000000009BBBA3B8 000042 (v01                 00000000      00000000)
[    0.000000] ACPI: SSDT 0x000000009BBBA400 000333 (v02 Ther_R Ther_Rvp 00001000 INTL 20120913)
[    0.000000] ACPI: ASF! 0x000000009BBBA738 0000A0 (v32 INTEL   HCG     00000001 TFSM 000F4240)
[    0.000000] ACPI: MSDM 0x000000009BBBA7D8 000055 (v03 GBT    GBTUACPI 01072009 AMI  00010013)
[    0.000000] ACPI: SLIC 0x000000009BBBA830 000176 (v01 GBT    GBTUACPI 01072009 AMI  00010013)
[    0.000000] ACPI: SSDT 0x000000009BBBA9A8 000539 (v02 PmRef  Cpu0Ist  00003000 INTL 20120913)
[    0.000000] ACPI: SSDT 0x000000009BBBAEE8 000B74 (v02 CpuRef CpuSsdt  00003000 INTL 20120913)
[    0.000000] ACPI: SSDT 0x000000009BBBBA60 005AF3 (v02 SaSsdt SaSsdt   00003000 INTL 20120913)
[    0.000000] ACPI: SSDT 0x000000009BBC1558 000E21 (v02 SgRef  SgPeg    00001000 INTL 20120913)
[    0.000000] ACPI: DMAR 0x000000009BBC2380 0000B8 (v01 INTEL  BDW      00000001 INTL 00000001)
[    0.000000] ACPI: SSDT 0x000000009BBC2438 001383 (v01 OptRef OptTabl  00001000 INTL 20120913)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000045effffff]
[    0.000000] NODE_DATA(0) allocated [mem 0x45eff8000-0x45effcfff]
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x0000000000001000-0x0000000000ffffff]
[    0.000000]   DMA32    [mem 0x0000000001000000-0x00000000ffffffff]
[    0.000000]   Normal   [mem 0x0000000100000000-0x000000045effffff]
[    0.000000]   Device   empty
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x0000000000001000-0x000000000009bfff]
[    0.000000]   node   0: [mem 0x0000000000100000-0x0000000098839fff]
[    0.000000]   node   0: [mem 0x0000000098aeb000-0x000000009bab2fff]
[    0.000000]   node   0: [mem 0x000000009cfff000-0x000000009cffffff]
[    0.000000]   node   0: [mem 0x0000000100000000-0x000000045effffff]
[    0.000000] Initmem setup node 0 [mem 0x0000000000001000-0x000000045effffff]
[    0.000000] On node 0 totalpages: 4171678
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3995 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 9889 pages used for memmap
[    0.000000]   DMA32 zone: 632835 pages, LIFO batch:31
[    0.000000]   Normal zone: 55232 pages used for memmap
[    0.000000]   Normal zone: 3534848 pages, LIFO batch:31
[    0.000000] Reserving Intel graphics stolen memory at 0x9e000000-0x9fffffff
[    0.000000] ACPI: PM-Timer IO Port: 0x1808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x0])
[    0.000000] ACPI: NMI not connected to LINT 1!
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x0])
[    0.000000] ACPI: NMI not connected to LINT 1!
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x0])
[    0.000000] ACPI: NMI not connected to LINT 1!
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] dfl dfl lint[0x0])
[    0.000000] ACPI: NMI not connected to LINT 1!
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x05] dfl dfl lint[0x0])
[    0.000000] ACPI: NMI not connected to LINT 1!
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x06] dfl dfl lint[0x0])
[    0.000000] ACPI: NMI not connected to LINT 1!
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x07] dfl dfl lint[0x0])
[    0.000000] ACPI: NMI not connected to LINT 1!
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x08] dfl dfl lint[0x0])
[    0.000000] ACPI: NMI not connected to LINT 1!
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] smpboot: Allowing 8 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009c000-0x0009cfff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009d000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x9883a000-0x98aeafff]
[    0.000000] PM: Registered nosave memory: [mem 0x9bab3000-0x9bb9bfff]
[    0.000000] PM: Registered nosave memory: [mem 0x9bb9c000-0x9bbc3fff]
[    0.000000] PM: Registered nosave memory: [mem 0x9bbc4000-0x9cccefff]
[    0.000000] PM: Registered nosave memory: [mem 0x9cccf000-0x9cffefff]
[    0.000000] PM: Registered nosave memory: [mem 0x9d000000-0x9d7fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x9d800000-0x9fffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xa0000000-0xf7ffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf8000000-0xfbffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfc000000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfecfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed00000-0xfed03fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed04000-0xfed1bfff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xfeffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xff000000-0xffffffff]
[    0.000000] e820: [mem 0xa0000000-0xf7ffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] clocksource: refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645519600211568 ns
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 33 pages/cpu @ffff88045ec00000 s98008 r8192 d28968 u262144
[    0.000000] pcpu-alloc: s98008 r8192 d28968 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 4106472
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-22-generic root=UUID=a35e04a1-3b9c-46b3-b722-2539da2dde9a ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 16304128K/16686712K available (8359K kernel code, 1278K rwdata, 3920K rodata, 1480K init, 1292K bss, 382584K reserved, 0K cma-reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	Build-time adjustment of leaf fanout to 64.
[    0.000000] 	RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=64, nr_cpu_ids=8
[    0.000000] NR_IRQS:16640 nr_irqs:488 16
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] clocksource: hpet: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 133484882848 ns
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 2693.822 MHz processor
[    0.000080] Calibrating delay loop (skipped), value calculated using timer frequency.. 5387.64 BogoMIPS (lpj=10775288)
[    0.000087] pid_max: default: 32768 minimum: 301
[    0.000100] ACPI: Core revision 20150930
[    0.059562] ACPI: 8 ACPI AML tables successfully acquired and loaded
[    0.059616] Security Framework initialized
[    0.059620] Yama: becoming mindful.
[    0.059654] AppArmor: AppArmor initialized
[    0.062405] Dentry cache hash table entries: 2097152 (order: 12, 16777216 bytes)
[    0.070913] Inode-cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.074533] Mount-cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.074581] Mountpoint-cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.075131] Initializing cgroup subsys io
[    0.075139] Initializing cgroup subsys memory
[    0.075151] Initializing cgroup subsys devices
[    0.075157] Initializing cgroup subsys freezer
[    0.075161] Initializing cgroup subsys net_cls
[    0.075165] Initializing cgroup subsys perf_event
[    0.075171] Initializing cgroup subsys net_prio
[    0.075175] Initializing cgroup subsys hugetlb
[    0.075182] Initializing cgroup subsys pids
[    0.075235] CPU: Physical Processor ID: 0
[    0.075237] CPU: Processor Core ID: 0
[    0.075247] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.075250] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.077290] mce: CPU supports 9 MCE banks
[    0.077329] CPU0: Thermal monitoring enabled (TM1)
[    0.077356] process: using mwait in idle threads
[    0.077364] Last level iTLB entries: 4KB 64, 2MB 8, 4MB 8
[    0.077366] Last level dTLB entries: 4KB 64, 2MB 0, 4MB 0, 1GB 4
[    0.078300] Freeing SMP alternatives memory: 28K (ffffffff820b3000 - ffffffff820ba000)
[    0.094318] ftrace: allocating 31906 entries in 125 pages
[    0.130895] smpboot: Max logical packages: 2
[    0.130900] smpboot: APIC(0) Converting physical 0 to logical package 0
[    0.130910] DMAR: Host address width 39
[    0.130914] DMAR: DRHD base: 0x000000fed90000 flags: 0x0
[    0.130931] DMAR: dmar0: reg_base_addr fed90000 ver 1:0 cap 1c0000c40660462 ecap 7e1ff0505e
[    0.130935] DMAR: DRHD base: 0x000000fed91000 flags: 0x1
[    0.130944] DMAR: dmar1: reg_base_addr fed91000 ver 1:0 cap d2008c20660462 ecap f010da
[    0.130947] DMAR: RMRR base: 0x0000009cf02000 end: 0x0000009cf11fff
[    0.130951] DMAR: RMRR base: 0x0000009d800000 end: 0x0000009fffffff
[    0.130956] DMAR-IR: IOAPIC id 2 under DRHD base  0xfed91000 IOMMU 1
[    0.130958] DMAR-IR: HPET id 0 under DRHD base 0xfed91000
[    0.130961] DMAR-IR: x2apic is disabled because BIOS sets x2apic opt out bit.
[    0.130964] DMAR-IR: Use 'intremap=no_x2apic_optout' to override the BIOS setting.
[    0.131846] DMAR-IR: Enabled IRQ remapping in xapic mode
[    0.131849] x2apic: IRQ remapping doesn't support X2APIC mode
[    0.132371] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.172071] TSC deadline timer enabled
[    0.172077] smpboot: CPU0: Intel(R) Core(TM) i7-5700HQ CPU @ 2.70GHz (family: 0x6, model: 0x47, stepping: 0x1)
[    0.172114] Performance Events: PEBS fmt2+, 16-deep LBR, Broadwell events, full-width counters, Intel PMU driver.
[    0.172165] ... version:                3
[    0.172167] ... bit width:              48
[    0.172170] ... generic registers:      4
[    0.172172] ... value mask:             0000ffffffffffff
[    0.172175] ... max period:             0000ffffffffffff
[    0.172177] ... fixed-purpose events:   3
[    0.172179] ... event mask:             000000070000000f
[    0.174235] x86: Booting SMP configuration:
[    0.174239] .... node  #0, CPUs:      #1
[    0.177219] microcode: CPU1 microcode updated early to revision 0x13, date = 2015-08-03
[    0.181732] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.181884]  #2
[    0.184858] microcode: CPU2 microcode updated early to revision 0x13, date = 2015-08-03
[    0.189309]  #3
[    0.192296] microcode: CPU3 microcode updated early to revision 0x13, date = 2015-08-03
[    0.196770]  #4 #5 #6 #7
[    0.218559] x86: Booted up 1 node, 8 CPUs
[    0.218565] smpboot: Total of 8 processors activated (43101.15 BogoMIPS)
[    0.240370] devtmpfs: initialized
[    0.248613] evm: security.selinux
[    0.248617] evm: security.SMACK64
[    0.248619] evm: security.SMACK64EXEC
[    0.248621] evm: security.SMACK64TRANSMUTE
[    0.248624] evm: security.SMACK64MMAP
[    0.248626] evm: security.ima
[    0.248628] evm: security.capability
[    0.248786] PM: Registering ACPI NVS region [mem 0x9bbc4000-0x9cccefff] (17870848 bytes)
[    0.249512] clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
[    0.249736] pinctrl core: initialized pinctrl subsystem
[    0.249974] RTC time:  3:38:14, date: 05/17/16
[    0.250268] NET: Registered protocol family 16
[    0.267796] cpuidle: using governor ladder
[    0.279801] cpuidle: using governor menu
[    0.279810] PCCT header not found.
[    0.279992] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.279996] ACPI: bus type PCI registered
[    0.279999] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.280182] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.280188] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.280207] PCI: Using configuration type 1 for base access
[    0.296666] ACPI: Added _OSI(Module Device)
[    0.296671] ACPI: Added _OSI(Processor Device)
[    0.296674] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.296677] ACPI: Added _OSI(Processor Aggregator Device)
[    0.305298] ACPI Error: No handler for Region [ECF2] (ffff88044e0d21f8) [EmbeddedControl] (20150930/evregion-163)
[    0.305309] ACPI Error: Region EmbeddedControl (ID=3) has no handler (20150930/exfldio-297)
[    0.305317] ACPI Error: Method parse/execution failed [\_SB.PCI0.LPCB.EC._REG] (Node ffff88044e0d37a8), AE_NOT_EXIST (20150930/psparse-542)
[    0.309554] ACPI: Executed 18 blocks of module-level executable AML code
[    0.325063] ACPI: Dynamic OEM Table Load:
[    0.325080] ACPI: SSDT 0xFFFF88044BED5400 0003D3 (v02 PmRef  Cpu0Cst  00003001 INTL 20120913)
[    0.327378] ACPI: Dynamic OEM Table Load:
[    0.327393] ACPI: SSDT 0xFFFF88044BEDA000 0005AA (v02 PmRef  ApIst    00003000 INTL 20120913)
[    0.329820] ACPI: Dynamic OEM Table Load:
[    0.329831] ACPI: SSDT 0xFFFF88044BF74200 000119 (v02 PmRef  ApCst    00003000 INTL 20120913)
[    0.336374] ACPI : EC: EC started
[    0.341750] ACPI: Interpreter enabled
[    0.341773] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20150930/hwxface-580)
[    0.341794] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20150930/hwxface-580)
[    0.341834] ACPI: (supports S0 S3 S4 S5)
[    0.341837] ACPI: Using IOAPIC for interrupt routing
[    0.341914] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.348179] ACPI: Power Resource [NVP3] (on)
[    0.348246] ACPI: Power Resource [NVP2] (on)
[    0.451047] ACPI: Power Resource [PG01] (on)
[    0.452007] ACPI: Power Resource [PG02] (on)
[    0.481373] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    0.481390] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.482795] acpi PNP0A08:00: _OSC: OS now controls [PCIeHotplug PME AER PCIeCapability]
[    0.482799] acpi PNP0A08:00: FADT indicates ASPM is unsupported, using BIOS configuration
[    0.484041] PCI host bridge to bus 0000:00
[    0.484050] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7 window]
[    0.484055] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff window]
[    0.484059] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff window]
[    0.484063] pci_bus 0000:00: root bus resource [mem 0xa0000000-0xfeafffff window]
[    0.484068] pci_bus 0000:00: root bus resource [bus 00-3e]
[    0.484086] pci 0000:00:00.0: [8086:1614] type 00 class 0x060000
[    0.484337] pci 0000:00:01.0: [8086:1601] type 01 class 0x060400
[    0.484429] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.484657] pci 0000:00:01.0: System wakeup disabled by ACPI
[    0.484765] pci 0000:00:02.0: [8086:1612] type 00 class 0x030000
[    0.484801] pci 0000:00:02.0: reg 0x10: [mem 0xa1000000-0xa1ffffff 64bit]
[    0.484818] pci 0000:00:02.0: reg 0x18: [mem 0xb0000000-0xbfffffff 64bit pref]
[    0.484830] pci 0000:00:02.0: reg 0x20: [io  0x6000-0x603f]
[    0.485084] pci 0000:00:03.0: [8086:160c] type 00 class 0x040300
[    0.485116] pci 0000:00:03.0: reg 0x10: [mem 0xa3d14000-0xa3d17fff 64bit]
[    0.485405] pci 0000:00:14.0: [8086:8cb1] type 00 class 0x0c0330
[    0.485469] pci 0000:00:14.0: reg 0x10: [mem 0xa3d00000-0xa3d0ffff 64bit]
[    0.485604] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    0.485744] pci 0000:00:14.0: System wakeup disabled by ACPI
[    0.485837] pci 0000:00:16.0: [8086:8cba] type 00 class 0x078000
[    0.485901] pci 0000:00:16.0: reg 0x10: [mem 0xa3d1d000-0xa3d1d00f 64bit]
[    0.486033] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.486287] pci 0000:00:1a.0: [8086:8cad] type 00 class 0x0c0320
[    0.486343] pci 0000:00:1a.0: reg 0x10: [mem 0xa3d1b000-0xa3d1b3ff]
[    0.486497] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.486636] pci 0000:00:1a.0: System wakeup disabled by ACPI
[    0.486734] pci 0000:00:1b.0: [8086:8ca0] type 00 class 0x040300
[    0.486796] pci 0000:00:1b.0: reg 0x10: [mem 0xa3d10000-0xa3d13fff 64bit]
[    0.486942] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.487107] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    0.487202] pci 0000:00:1c.0: [8086:8c90] type 01 class 0x060400
[    0.487366] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.487551] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.487644] pci 0000:00:1c.1: [8086:8c92] type 01 class 0x060400
[    0.487810] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.487992] pci 0000:00:1c.1: System wakeup disabled by ACPI
[    0.488096] pci 0000:00:1c.2: [8086:8c94] type 01 class 0x060400
[    0.488263] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.488445] pci 0000:00:1c.2: System wakeup disabled by ACPI
[    0.488551] pci 0000:00:1d.0: [8086:8ca6] type 00 class 0x0c0320
[    0.488608] pci 0000:00:1d.0: reg 0x10: [mem 0xa3d1a000-0xa3d1a3ff]
[    0.488763] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.488900] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.488992] pci 0000:00:1f.0: [8086:8cc3] type 00 class 0x060100
[    0.489365] pci 0000:00:1f.2: [8086:8c83] type 00 class 0x010601
[    0.489423] pci 0000:00:1f.2: reg 0x10: [io  0x60b0-0x60b7]
[    0.489443] pci 0000:00:1f.2: reg 0x14: [io  0x60a0-0x60a3]
[    0.489461] pci 0000:00:1f.2: reg 0x18: [io  0x6090-0x6097]
[    0.489480] pci 0000:00:1f.2: reg 0x1c: [io  0x6080-0x6083]
[    0.489499] pci 0000:00:1f.2: reg 0x20: [io  0x6060-0x607f]
[    0.489519] pci 0000:00:1f.2: reg 0x24: [mem 0xa3d19000-0xa3d197ff]
[    0.489596] pci 0000:00:1f.2: PME# supported from D3hot
[    0.489788] pci 0000:00:1f.3: [8086:8ca2] type 00 class 0x0c0500
[    0.489828] pci 0000:00:1f.3: reg 0x10: [mem 0xa3d18000-0xa3d180ff 64bit]
[    0.489878] pci 0000:00:1f.3: reg 0x20: [io  0x6040-0x605f]
[    0.490205] pci 0000:01:00.0: [10de:13d8] type 00 class 0x030200
[    0.490235] pci 0000:01:00.0: reg 0x10: [mem 0x00000000-0x00ffffff]
[    0.490250] pci 0000:01:00.0: reg 0x14: [mem 0x00000000-0x0fffffff 64bit pref]
[    0.490265] pci 0000:01:00.0: reg 0x1c: [mem 0x00000000-0x01ffffff 64bit pref]
[    0.490276] pci 0000:01:00.0: reg 0x24: [io  0x0000-0x007f]
[    0.490286] pci 0000:01:00.0: reg 0x30: [mem 0x00000000-0x0007ffff pref]
[    0.490298] pci 0000:01:00.0: Max Payload Size set to 256 (was 128, max 256)
[    0.490477] pci 0000:01:00.0: System wakeup disabled by ACPI
[    0.496041] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.496048] pci 0000:00:01.0:   bridge window [io  0x5000-0x5fff]
[    0.496054] pci 0000:00:01.0:   bridge window [mem 0xa2000000-0xa30fffff]
[    0.496062] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xd1ffffff 64bit pref]
[    0.496281] pci 0000:02:00.0: [10ec:5227] type 00 class 0xff0000
[    0.496450] pci 0000:02:00.0: reg 0x10: [mem 0xa3100000-0xa3100fff]
[    0.496987] pci 0000:02:00.0: supports D1 D2
[    0.496992] pci 0000:02:00.0: PME# supported from D1 D2 D3hot D3cold
[    0.497191] pci 0000:02:00.0: System wakeup disabled by ACPI
[    0.504077] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.504085] pci 0000:00:1c.0:   bridge window [io  0x4000-0x4fff]
[    0.504093] pci 0000:00:1c.0:   bridge window [mem 0xa3100000-0xa3afffff]
[    0.504105] pci 0000:00:1c.0:   bridge window [mem 0xd2100000-0xd2afffff 64bit pref]
[    0.504268] pci 0000:03:00.0: [10ec:8168] type 00 class 0x020000
[    0.504338] pci 0000:03:00.0: reg 0x10: [io  0x3000-0x30ff]
[    0.504390] pci 0000:03:00.0: reg 0x18: [mem 0xa3c04000-0xa3c04fff 64bit]
[    0.504423] pci 0000:03:00.0: reg 0x20: [mem 0xa3c00000-0xa3c03fff 64bit]
[    0.504553] pci 0000:03:00.0: supports D1 D2
[    0.504557] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.504666] pci 0000:03:00.0: System wakeup disabled by ACPI
[    0.512060] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    0.512068] pci 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
[    0.512076] pci 0000:00:1c.1:   bridge window [mem 0xa3c00000-0xa3cfffff]
[    0.512342] pci 0000:04:00.0: [8086:08b1] type 00 class 0x028000
[    0.512658] pci 0000:04:00.0: reg 0x10: [mem 0xa3b00000-0xa3b01fff 64bit]
[    0.513399] pci 0000:04:00.0: PME# supported from D0 D3hot D3cold
[    0.513588] pci 0000:04:00.0: System wakeup disabled by ACPI
[    0.520113] pci 0000:00:1c.2: PCI bridge to [bus 04]
[    0.520126] pci 0000:00:1c.2:   bridge window [mem 0xa3b00000-0xa3bfffff]
[    0.522677] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.522797] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 10 11 12 14 15)
[    0.522913] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 *4 5 6 10 11 12 14 15)
[    0.523027] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 *10 11 12 14 15)
[    0.523137] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.523248] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.523358] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 10 11 12 14 15)
[    0.523467] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.523953] ACPI: Enabled 4 GPEs in block 00 to 3F
[    0.524107] ACPI : EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.524374] vgaarb: setting as boot device: PCI:0000:00:02.0
[    0.524378] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.524386] vgaarb: loaded
[    0.524389] vgaarb: bridge control possible 0000:00:02.0
[    0.524994] SCSI subsystem initialized
[    0.525084] libata version 3.00 loaded.
[    0.525144] ACPI: bus type USB registered
[    0.525181] usbcore: registered new interface driver usbfs
[    0.525202] usbcore: registered new interface driver hub
[    0.525253] usbcore: registered new device driver usb
[    0.525599] PCI: Using ACPI for IRQ routing
[    0.529334] PCI: pci_cache_line_size set to 64 bytes
[    0.529462] e820: reserve RAM buffer [mem 0x0009c800-0x0009ffff]
[    0.529466] e820: reserve RAM buffer [mem 0x9883a000-0x9bffffff]
[    0.529470] e820: reserve RAM buffer [mem 0x9bab3000-0x9bffffff]
[    0.529473] e820: reserve RAM buffer [mem 0x9d000000-0x9fffffff]
[    0.529476] e820: reserve RAM buffer [mem 0x45f000000-0x45fffffff]
[    0.529744] NetLabel: Initializing
[    0.529747] NetLabel:  domain hash size = 128
[    0.529749] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.529779] NetLabel:  unlabeled traffic allowed by default
[    0.529928] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.529940] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.531995] clocksource: Switched to clocksource hpet
[    0.546156] AppArmor: AppArmor Filesystem Enabled
[    0.546296] pnp: PnP ACPI init
[    0.546656] pnp 00:00: disabling [io  0x002e-0x002f] because it overlaps 0000:01:00.0 BAR 5 [io  0x0000-0x007f]
[    0.546663] pnp 00:00: disabling [io  0x004e-0x004f] because it overlaps 0000:01:00.0 BAR 5 [io  0x0000-0x007f]
[    0.546669] pnp 00:00: disabling [io  0x0061] because it overlaps 0000:01:00.0 BAR 5 [io  0x0000-0x007f]
[    0.546675] pnp 00:00: disabling [io  0x0063] because it overlaps 0000:01:00.0 BAR 5 [io  0x0000-0x007f]
[    0.546681] pnp 00:00: disabling [io  0x0065] because it overlaps 0000:01:00.0 BAR 5 [io  0x0000-0x007f]
[    0.546687] pnp 00:00: disabling [io  0x0067] because it overlaps 0000:01:00.0 BAR 5 [io  0x0000-0x007f]
[    0.546692] pnp 00:00: disabling [io  0x0070] because it overlaps 0000:01:00.0 BAR 5 [io  0x0000-0x007f]
[    0.546764] system 00:00: [io  0x0680-0x069f] has been reserved
[    0.546770] system 00:00: [io  0xffff] has been reserved
[    0.546775] system 00:00: [io  0xffff] has been reserved
[    0.546782] system 00:00: [io  0xffff] has been reserved
[    0.546788] system 00:00: [io  0x1800-0x18fe] could not be reserved
[    0.546793] system 00:00: [io  0x164e-0x164f] has been reserved
[    0.546802] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.546940] system 00:01: [io  0x0800-0x087f] has been reserved
[    0.546947] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.547011] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.547116] system 00:03: [io  0x1854-0x1857] has been reserved
[    0.547123] system 00:03: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.547788] system 00:04: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.547794] system 00:04: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.547799] system 00:04: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.547805] system 00:04: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.547811] system 00:04: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.547816] system 00:04: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.547824] system 00:04: [mem 0xfed90000-0xfed93fff] could not be reserved
[    0.547829] system 00:04: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.547835] system 00:04: [mem 0xff000000-0xffffffff] has been reserved
[    0.547840] system 00:04: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.547845] system 00:04: [mem 0xa0010000-0xa001ffff] has been reserved
[    0.547850] system 00:04: [mem 0xa0000000-0xa000ffff] has been reserved
[    0.547857] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.548784] pnp 00:05: Plug and Play ACPI device, IDs ETD0a00 PNP0f13 (active)
[    0.548861] pnp 00:06: Plug and Play ACPI device, IDs MSF0001 PNP0303 (active)
[    0.549431] pnp: PnP ACPI: found 7 devices
[    0.557919] clocksource: acpi_pm: mask: 0xffffff max_cycles: 0xffffff, max_idle_ns: 2085701024 ns
[    0.558006] pci 0000:01:00.0: BAR 1: assigned [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.558022] pci 0000:01:00.0: BAR 3: assigned [mem 0xd0000000-0xd1ffffff 64bit pref]
[    0.558036] pci 0000:01:00.0: BAR 0: assigned [mem 0xa2000000-0xa2ffffff]
[    0.558043] pci 0000:01:00.0: BAR 6: assigned [mem 0xa3000000-0xa307ffff pref]
[    0.558048] pci 0000:01:00.0: BAR 5: assigned [io  0x5000-0x507f]
[    0.558057] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.558062] pci 0000:00:01.0:   bridge window [io  0x5000-0x5fff]
[    0.558070] pci 0000:00:01.0:   bridge window [mem 0xa2000000-0xa30fffff]
[    0.558076] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xd1ffffff 64bit pref]
[    0.558086] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.558092] pci 0000:00:1c.0:   bridge window [io  0x4000-0x4fff]
[    0.558102] pci 0000:00:1c.0:   bridge window [mem 0xa3100000-0xa3afffff]
[    0.558111] pci 0000:00:1c.0:   bridge window [mem 0xd2100000-0xd2afffff 64bit pref]
[    0.558124] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    0.558130] pci 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
[    0.558140] pci 0000:00:1c.1:   bridge window [mem 0xa3c00000-0xa3cfffff]
[    0.558158] pci 0000:00:1c.2: PCI bridge to [bus 04]
[    0.558169] pci 0000:00:1c.2:   bridge window [mem 0xa3b00000-0xa3bfffff]
[    0.558190] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7 window]
[    0.558195] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff window]
[    0.558199] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff window]
[    0.558203] pci_bus 0000:00: resource 7 [mem 0xa0000000-0xfeafffff window]
[    0.558207] pci_bus 0000:01: resource 0 [io  0x5000-0x5fff]
[    0.558211] pci_bus 0000:01: resource 1 [mem 0xa2000000-0xa30fffff]
[    0.558215] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xd1ffffff 64bit pref]
[    0.558219] pci_bus 0000:02: resource 0 [io  0x4000-0x4fff]
[    0.558223] pci_bus 0000:02: resource 1 [mem 0xa3100000-0xa3afffff]
[    0.558226] pci_bus 0000:02: resource 2 [mem 0xd2100000-0xd2afffff 64bit pref]
[    0.558230] pci_bus 0000:03: resource 0 [io  0x3000-0x3fff]
[    0.558234] pci_bus 0000:03: resource 1 [mem 0xa3c00000-0xa3cfffff]
[    0.558238] pci_bus 0000:04: resource 1 [mem 0xa3b00000-0xa3bfffff]
[    0.558315] NET: Registered protocol family 2
[    0.558786] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.559333] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.559593] TCP: Hash tables configured (established 131072 bind 65536)
[    0.559678] UDP hash table entries: 8192 (order: 6, 262144 bytes)
[    0.559804] UDP-Lite hash table entries: 8192 (order: 6, 262144 bytes)
[    0.559975] NET: Registered protocol family 1
[    0.560023] pci 0000:00:02.0: Video device with shadowed ROM
[    0.600223] PCI: CLS 0 bytes, default 64
[    0.600328] Trying to unpack rootfs image as initramfs...
[    2.099746] Freeing initrd memory: 34512K (ffff880033c88000 - ffff880035e3c000)
[    2.099828] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    2.099836] software IO TLB [mem 0x9483a000-0x9883a000] (64MB) mapped at [ffff88009483a000-ffff880098839fff]
[    2.100275] Scanning for low memory corruption every 60 seconds
[    2.101107] futex hash table entries: 2048 (order: 5, 131072 bytes)
[    2.101181] audit: initializing netlink subsys (disabled)
[    2.101214] audit: type=2000 audit(1463456296.048:1): initialized
[    2.102392] Initialise system trusted keyring
[    2.102632] HugeTLB registered 1 GB page size, pre-allocated 0 pages
[    2.102635] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    2.106411] zbud: loaded
[    2.106952] VFS: Disk quotas dquot_6.6.0
[    2.107033] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    2.108214] fuse init (API version 7.23)
[    2.108529] Key type big_key registered
[    2.108597] Allocating IMA MOK and blacklist keyrings.
[    2.109484] Key type asymmetric registered
[    2.109493] Asymmetric key parser 'x509' registered
[    2.109580] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 249)
[    2.109672] io scheduler noop registered
[    2.109683] io scheduler deadline registered (default)
[    2.109755] io scheduler cfq registered
[    2.111352] pcieport 0000:00:01.0: Signaling PME through PCIe PME interrupt
[    2.111357] pci 0000:01:00.0: Signaling PME through PCIe PME interrupt
[    2.111364] pcie_pme 0000:00:01.0:pcie01: service driver pcie_pme loaded
[    2.111405] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
[    2.111409] pci 0000:02:00.0: Signaling PME through PCIe PME interrupt
[    2.111417] pcie_pme 0000:00:1c.0:pcie01: service driver pcie_pme loaded
[    2.111457] pcieport 0000:00:1c.1: Signaling PME through PCIe PME interrupt
[    2.111460] pci 0000:03:00.0: Signaling PME through PCIe PME interrupt
[    2.111468] pcie_pme 0000:00:1c.1:pcie01: service driver pcie_pme loaded
[    2.111507] pcieport 0000:00:1c.2: Signaling PME through PCIe PME interrupt
[    2.111510] pci 0000:04:00.0: Signaling PME through PCIe PME interrupt
[    2.111518] pcie_pme 0000:00:1c.2:pcie01: service driver pcie_pme loaded
[    2.111533] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    2.111558] pciehp 0000:00:1c.0:pcie04: Slot #0 AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug+ Surprise+ Interlock- NoCompl+ LLActRep+
[    2.111631] pciehp 0000:00:1c.0:pcie04: service driver pciehp loaded
[    2.111642] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    2.111729] intel_idle: MWAIT substates: 0x2120
[    2.111732] intel_idle: v0.4.1 model 0x47
[    2.111735] intel_idle: lapic_timer_reliable_states 0xffffffff
[    2.112914] ACPI: AC Adapter [ADP1] (off-line)
[    2.113078] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:17/PNP0C09:01/PNP0C0D:01/input/input0
[    2.116162] ACPI: Lid Switch [LID0]
[    2.116283] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:17/PNP0C09:01/PNP0C0E:00/input/input1
[    2.116291] ACPI: Sleep Button [SLPB]
[    2.116402] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:01/input/input2
[    2.116408] ACPI: Sleep Button [SLPB]
[    2.116487] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input3
[    2.116492] ACPI: Power Button [PWRB]
[    2.116574] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input4
[    2.116579] ACPI: Power Button [PWRF]
[    2.128248] thermal LNXTHERM:00: registered as thermal_zone0
[    2.128254] ACPI: Thermal Zone [TZ01] (30 C)
[    2.128368] GHES: HEST is not enabled!
[    2.128650] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    2.137117] Linux agpgart interface v0.103
[    2.144921] brd: module loaded
[    2.146340] [Firmware Bug]: battery: (dis)charge rate invalid.
[    2.146347] ACPI: Battery Slot [BAT1] (battery present)
[    2.148722] loop: module loaded
[    2.149254] libphy: Fixed MDIO Bus: probed
[    2.149266] tun: Universal TUN/TAP device driver, 1.6
[    2.149269] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    2.149376] PPP generic driver version 2.4.2
[    2.149534] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.149549] ehci-pci: EHCI PCI platform driver
[    2.149797] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    2.149810] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    2.149831] ehci-pci 0000:00:1a.0: debug port 2
[    2.153762] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    2.153791] ehci-pci 0000:00:1a.0: irq 16, io mem 0xa3d1b000
[    2.163983] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    2.164057] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    2.164062] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.164066] usb usb1: Product: EHCI Host Controller
[    2.164069] usb usb1: Manufacturer: Linux 4.4.0-22-generic ehci_hcd
[    2.164073] usb usb1: SerialNumber: 0000:00:1a.0
[    2.164332] hub 1-0:1.0: USB hub found
[    2.164346] hub 1-0:1.0: 2 ports detected
[    2.164827] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    2.164839] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.164858] ehci-pci 0000:00:1d.0: debug port 2
[    2.168777] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    2.168807] ehci-pci 0000:00:1d.0: irq 23, io mem 0xa3d1a000
[    2.179980] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    2.180045] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    2.180049] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.180053] usb usb2: Product: EHCI Host Controller
[    2.180056] usb usb2: Manufacturer: Linux 4.4.0-22-generic ehci_hcd
[    2.180060] usb usb2: SerialNumber: 0000:00:1d.0
[    2.180300] hub 2-0:1.0: USB hub found
[    2.180310] hub 2-0:1.0: 2 ports detected
[    2.180578] ehci-platform: EHCI generic platform driver
[    2.180611] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.180620] ohci-pci: OHCI PCI platform driver
[    2.180645] ohci-platform: OHCI generic platform driver
[    2.180664] uhci_hcd: USB Universal Host Controller Interface driver
[    2.180921] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    2.180932] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
[    2.182063] xhci_hcd 0000:00:14.0: hcc params 0x200077c1 hci version 0x100 quirks 0x00009810
[    2.182074] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    2.182218] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    2.182222] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.182225] usb usb3: Product: xHCI Host Controller
[    2.182229] usb usb3: Manufacturer: Linux 4.4.0-22-generic xhci-hcd
[    2.182232] usb usb3: SerialNumber: 0000:00:14.0
[    2.182476] hub 3-0:1.0: USB hub found
[    2.182500] hub 3-0:1.0: 14 ports detected
[    2.193853] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    2.193861] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 4
[    2.193926] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
[    2.193930] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.193933] usb usb4: Product: xHCI Host Controller
[    2.193937] usb usb4: Manufacturer: Linux 4.4.0-22-generic xhci-hcd
[    2.193941] usb usb4: SerialNumber: 0000:00:14.0
[    2.194193] hub 4-0:1.0: USB hub found
[    2.194212] hub 4-0:1.0: 6 ports detected
[    2.198872] usb: port power management may be unreliable
[    2.200068] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.203023] i8042: Attempting to reset device connected to KBD port
[    2.204992] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.205001] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.205302] mousedev: PS/2 mouse device common for all mice
[    2.205790] rtc_cmos 00:02: RTC can wake from S4
[    2.206004] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    2.206046] rtc_cmos 00:02: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    2.206063] i2c /dev entries driver
[    2.206189] device-mapper: uevent: version 1.0.3
[    2.206332] device-mapper: ioctl: 4.34.0-ioctl (2015-10-28) initialised: dm-devel@redhat.com
[    2.206374] Intel P-state driver initializing.
[    2.206907] ledtrig-cpu: registered to indicate activity on CPUs
[    2.207925] NET: Registered protocol family 10
[    2.208526] NET: Registered protocol family 17
[    2.208556] Key type dns_resolver registered
[    2.209891] microcode: CPU0 sig=0x40671, pf=0x20, revision=0x13
[    2.209939] microcode: CPU1 sig=0x40671, pf=0x20, revision=0x13
[    2.209955] microcode: CPU2 sig=0x40671, pf=0x20, revision=0x13
[    2.210001] microcode: CPU3 sig=0x40671, pf=0x20, revision=0x13
[    2.210048] microcode: CPU4 sig=0x40671, pf=0x20, revision=0x13
[    2.210094] microcode: CPU5 sig=0x40671, pf=0x20, revision=0x13
[    2.210119] microcode: CPU6 sig=0x40671, pf=0x20, revision=0x13
[    2.210155] microcode: CPU7 sig=0x40671, pf=0x20, revision=0x13
[    2.210309] microcode: Microcode Update Driver: v2.01 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    2.210799] registered taskstats version 1
[    2.210859] Loading compiled-in X.509 certificates
[    2.213081] Loaded X.509 cert 'Build time autogenerated kernel key: 10281ca0c0463cd0680138fff55319c9bd7d63b8'
[    2.213136] zswap: loaded using pool lzo/zbud
[    2.217735] Key type trusted registered
[    2.225105] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input7
[    2.226591] Key type encrypted registered
[    2.226611] AppArmor: AppArmor sha1 policy hashing enabled
[    2.226621] ima: No TPM chip found, activating TPM-bypass!
[    2.226674] evm: HMAC attrs: 0x1
[    2.228118]   Magic number: 0:168:614
[    2.228344] rtc_cmos 00:02: setting system clock to 2016-05-17 03:38:16 UTC (1463456296)
[    2.228565] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.228570] EDD information not available.
[    2.228757] PM: Hibernation image not present or could not be loaded.
[    2.231786] Freeing unused kernel memory: 1480K (ffffffff81f41000 - ffffffff820b3000)
[    2.231790] Write protecting the kernel read-only data: 14336k
[    2.233082] Freeing unused kernel memory: 1868K (ffff88000182d000 - ffff880001a00000)
[    2.234306] Freeing unused kernel memory: 176K (ffff880001dd4000 - ffff880001e00000)
[    2.260939] random: systemd-udevd urandom read with 21 bits of entropy available
[    2.346063] FUJITSU Extended Socket Network Device Driver - version 1.0 - Copyright (c) 2015 FUJITSU LIMITED
[    2.349900] hidraw: raw HID events driver (C) Jiri Kosina
[    2.363885] sdhci: Secure Digital Host Controller Interface driver
[    2.363892] sdhci: Copyright(c) Pierre Ossman
[    2.392121] rtsx_pci 0000:02:00.0: rtsx_pci_acquire_irq: pcr->msi_en = 1, pci->irq = 31
[    2.397595] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.397617] r8169 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[    2.401832] ahci 0000:00:1f.2: version 3.0
[    2.402236] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x3 impl SATA mode
[    2.402249] ahci 0000:00:1f.2: flags: 64bit ncq led clo pio slum part ems apst 
[    2.405211] r8169 0000:03:00.0 eth0: RTL8168g/8111g at 0xffffc90001c68000, 40:8d:5c:18:ad:d8, XID 10900800 IRQ 33
[    2.405218] r8169 0000:03:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    2.410379] [drm] Initialized drm 1.1.0 20060810
[    2.414150] scsi host0: ahci
[    2.414473] scsi host1: ahci
[    2.414738] scsi host2: ahci
[    2.414973] scsi host3: ahci
[    2.415201] scsi host4: ahci
[    2.415403] scsi host5: ahci
[    2.415510] ata1: SATA max UDMA/133 abar m2048@0xa3d19000 port 0xa3d19100 irq 32
[    2.415516] ata2: SATA max UDMA/133 abar m2048@0xa3d19000 port 0xa3d19180 irq 32
[    2.415518] ata3: DUMMY
[    2.415521] ata4: DUMMY
[    2.415523] ata5: DUMMY
[    2.415526] ata6: DUMMY
[    2.458167] r8169 0000:03:00.0 enp3s0: renamed from eth0
[    2.476034] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    2.488163] [drm] Memory usable by graphics device = 4096M
[    2.488170] [drm] Replacing VGA console driver
[    2.489116] Console: switching to colour dummy device 80x25
[    2.492021] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    2.495657] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    2.495662] [drm] Driver supports precise vblank timestamp query.
[    2.497095] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    2.503993] usb 3-3: new full-speed USB device number 2 using xhci_hcd
[    2.516409] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    2.517126] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input9
[    2.517390] ACPI Exception: AE_NOT_FOUND, Evaluating _DOD (20150930/video-1216)
[    2.517404] ACPI: Video Device [PEGP] (multi-head: no  rom: yes  post: no)
[    2.517522] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:12/LNXVIDEO:01/input/input10
[    2.517757] [drm] Initialized i915 1.6.0 20151010 for 0000:00:02.0 on minor 0
[    2.572008] [drm] GMBUS [i915 gmbus vga] timed out, falling back to bit banging on pin 2
[    2.608407] usb 1-1: New USB device found, idVendor=8087, idProduct=8009
[    2.608415] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.608994] hub 1-1:1.0: USB hub found
[    2.609127] hub 1-1:1.0: 6 ports detected
[    2.624383] usb 2-1: New USB device found, idVendor=8087, idProduct=8001
[    2.624391] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.624850] hub 2-1:1.0: USB hub found
[    2.624997] hub 2-1:1.0: 8 ports detected
[    2.633298] usb 3-3: New USB device found, idVendor=8087, idProduct=07dc
[    2.633306] usb 3-3: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.731994] ata2: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    2.732029] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    2.732591] ata2.00: supports DRM functions and may not be fully accessible
[    2.734160] ata1.00: supports DRM functions and may not be fully accessible
[    2.734317] ata1.00: disabling queued TRIM support
[    2.734325] ata1.00: ATA-9: Samsung SSD 850 EVO mSATA 1TB, EMT41B6Q, max UDMA/133
[    2.734330] ata1.00: 1953525168 sectors, multi 1: LBA48 NCQ (depth 31/32), AA
[    2.734853] ata1.00: supports DRM functions and may not be fully accessible
[    2.735005] ata1.00: disabling queued TRIM support
[    2.735125] ata1.00: configured for UDMA/133
[    2.735506] scsi 0:0:0:0: Direct-Access     ATA      Samsung SSD 850  1B6Q PQ: 0 ANSI: 5
[    2.736171] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.736186] sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/932 GiB)
[    2.736266] ata2.00: disabling queued TRIM support
[    2.736275] ata2.00: ATA-9: Crucial_CT128MX100SSD1, MU01, max UDMA/133
[    2.736282] ata2.00: 250069680 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.736577] sd 0:0:0:0: [sda] Write Protect is off
[    2.736588] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.736759] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.738082]  sda: sda1 sda2 < sda5 sda6 > sda3
[    2.739459] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.740905] ata2.00: supports DRM functions and may not be fully accessible
[    2.744597] ata2.00: disabling queued TRIM support
[    2.748695] ata2.00: configured for UDMA/133
[    2.749126] scsi 1:0:0:0: Direct-Access     ATA      Crucial_CT128MX1 MU01 PQ: 0 ANSI: 5
[    2.749698] ata2.00: Enabling discard_zeroes_data
[    2.749744] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    2.749746] sd 1:0:0:0: [sdb] 250069680 512-byte logical blocks: (128 GB/119 GiB)
[    2.749752] sd 1:0:0:0: [sdb] 4096-byte physical blocks
[    2.750216] sd 1:0:0:0: [sdb] Write Protect is off
[    2.750226] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.750379] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.750696] ata2.00: Enabling discard_zeroes_data
[    2.752685]  sdb: sdb1 sdb2 sdb3 sdb4
[    2.753446] ata2.00: Enabling discard_zeroes_data
[    2.753560] sd 1:0:0:0: [sdb] Attached SCSI disk
[    2.800005] usb 3-4: new high-speed USB device number 3 using xhci_hcd
[    2.846162] fbcon: inteldrmfb (fb0) is primary device
[    3.016222] psmouse serio1: elantech: assuming hardware version 3 (with firmware version 0x450f01)
[    3.030776] psmouse serio1: elantech: Synaptics capabilities query result 0x58, 0x17, 0x0c.
[    3.043968] usb 3-4: New USB device found, idVendor=1bcf, idProduct=2c6b
[    3.043971] usb 3-4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    3.043974] usb 3-4: Product: HD WebCam
[    3.043977] usb 3-4: Manufacturer: 27C40-06N20-L01S4AE3BW
[    3.044899] psmouse serio1: elantech: Elan sample query result 03, 4c, 85
[    3.100006] tsc: Refined TSC clocksource calibration: 2693.762 MHz
[    3.100011] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x26d439828ff, max_idle_ns: 440795206424 ns
[    3.117819] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio1/input/input8
[    4.100126] clocksource: Switched to clocksource tsc
[    4.228067] Console: switching to colour frame buffer device 240x67
[    4.240916] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[    4.366136] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[    4.481897] systemd[1]: systemd 229 running in system mode. (+PAM +AUDIT +SELINUX +IMA +APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT +GNUTLS +ACL +XZ -LZ4 +SECCOMP +BLKID +ELFUTILS +KMOD -IDN)
[    4.482395] systemd[1]: Detected architecture x86-64.
[    4.482626] systemd[1]: Set hostname to <pancake>.
[    4.609528] systemd[1]: Created slice System Slice.
[    4.610149] systemd[1]: Set up automount Arbitrary Executable File Formats File System Automount Point.
[    4.610194] systemd[1]: Reached target Remote File Systems (Pre).
[    4.610295] systemd[1]: Listening on /dev/initctl Compatibility Named Pipe.
[    4.610326] systemd[1]: Reached target Encrypted Volumes.
[    4.610354] systemd[1]: Reached target Remote File Systems.
[    4.610385] systemd[1]: Reached target Swap.
[    4.610452] systemd[1]: Listening on fsck to fsckd communication Socket.
[    4.610714] systemd[1]: Created slice User and Session Slice.
[    4.610744] systemd[1]: Reached target Slices.
[    4.610835] systemd[1]: Listening on Syslog Socket.
[    4.610954] systemd[1]: Started Forward Password Requests to Wall Directory Watch.
[    4.611029] systemd[1]: Listening on Journal Socket (/dev/log).
[    4.611094] systemd[1]: Listening on udev Kernel Socket.
[    4.611179] systemd[1]: Listening on udev Control Socket.
[    4.611363] systemd[1]: Listening on Journal Audit Socket.
[    4.611667] systemd[1]: Created slice system-getty.slice.
[    4.611700] systemd[1]: Reached target User and Group Name Lookups.
[    4.611800] systemd[1]: Listening on Journal Socket.
[    4.624034] systemd[1]: Mounting Debug File System...
[    4.625931] systemd[1]: Mounting Huge Pages File System...
[    4.627373] systemd[1]: Started Braille Device Support.
[    4.629138] systemd[1]: Starting Create list of required static device nodes for the current kernel...
[    4.630530] systemd[1]: Starting Journal Service...
[    4.631876] systemd[1]: Mounting POSIX Message Queue File System...
[    4.635010] systemd[1]: Starting Load Kernel Modules...
[    4.636486] systemd[1]: Started Read required files in advance.
[    4.638102] systemd[1]: Starting Uncomplicated firewall...
[    4.642597] systemd[1]: Mounted POSIX Message Queue File System.
[    4.642690] systemd[1]: Mounted Debug File System.
[    4.642744] systemd[1]: Mounted Huge Pages File System.
[    4.643427] systemd[1]: Started Create list of required static device nodes for the current kernel.
[    4.643991] systemd[1]: Started Uncomplicated firewall.
[    4.658027] lp: driver loaded but no devices found
[    4.663949] ppdev: user-space parallel port driver
[    4.669990] systemd[1]: Started Load Kernel Modules.
[    4.708811] systemd[1]: Started Journal Service.
[    4.756044] random: nonblocking pool is initialized
[    4.862016] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[    4.933287] systemd-journald[276]: Received request to flush runtime journal from PID 1
[    5.104084] audit: type=1400 audit(1463456299.371:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cups-browsed" pid=482 comm="apparmor_parser"
[    5.105292] audit: type=1400 audit(1463456299.371:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=474 comm="apparmor_parser"
[    5.105319] audit: type=1400 audit(1463456299.371:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=474 comm="apparmor_parser"
[    5.105337] audit: type=1400 audit(1463456299.371:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=474 comm="apparmor_parser"
[    5.105354] audit: type=1400 audit(1463456299.371:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=474 comm="apparmor_parser"
[    5.109003] audit: type=1400 audit(1463456299.375:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/ippusbxd" pid=487 comm="apparmor_parser"
[    5.115320] audit: type=1400 audit(1463456299.379:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=485 comm="apparmor_parser"
[    5.115353] audit: type=1400 audit(1463456299.379:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=485 comm="apparmor_parser"
[    5.115374] audit: type=1400 audit(1463456299.379:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd//third_party" pid=485 comm="apparmor_parser"
[    5.196530] wmi: Mapper loaded
[    5.279756] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    5.382405] Bluetooth: Core ver 2.21
[    5.382435] NET: Registered protocol family 31
[    5.382439] Bluetooth: HCI device and connection manager initialized
[    5.382446] Bluetooth: HCI socket layer initialized
[    5.382451] Bluetooth: L2CAP socket layer initialized
[    5.382463] Bluetooth: SCO socket layer initialized
[    5.399095] media: Linux media interface: v0.10
[    5.415397] nvidia: module license 'NVIDIA' taints kernel.
[    5.415406] Disabling lock debugging due to kernel taint
[    5.424978] usbcore: registered new interface driver btusb
[    5.429445] Linux video capture interface: v2.00
[    5.431042] nvidia: module verification failed: signature and/or required key missing - tainting kernel
[    5.433238] snd_hda_codec_realtek hdaudioC1D0: autoconfig for ALC282: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[    5.433252] snd_hda_codec_realtek hdaudioC1D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    5.433260] snd_hda_codec_realtek hdaudioC1D0:    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
[    5.433267] snd_hda_codec_realtek hdaudioC1D0:    mono: mono_out=0x0
[    5.433273] snd_hda_codec_realtek hdaudioC1D0:    inputs:
[    5.433281] snd_hda_codec_realtek hdaudioC1D0:      Mic=0x19
[    5.433290] snd_hda_codec_realtek hdaudioC1D0:      Internal Mic=0x12
[    5.448984] Bluetooth: hci0: read Intel version: 3707100180012d0d24
[    5.448994] Bluetooth: hci0: Intel device is already patched. patch num: 24
[    5.450000] Intel(R) Wireless WiFi driver for Linux
[    5.450008] Copyright(c) 2003- 2015 Intel Corporation
[    5.475485] nvidia 0000:01:00.0: enabling device (0000 -> 0003)
[    5.478026] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card1/input11
[    5.478373] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card1/input12
[    5.486074] nvidia-nvlink: Nvlink Core is being initialized, major device number 244
[    5.486353] [drm] Initialized nvidia-drm 0.0.0 20150116 for 0000:01:00.0 on minor 1
[    5.486366] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  361.42  Tue Mar 22 18:10:58 PDT 2016
[    5.487387] iwlwifi 0000:04:00.0: Unsupported splx structure
[    5.495972] iwlwifi 0000:04:00.0: Direct firmware load for iwlwifi-7260-17.ucode failed with error -2
[    5.496909] uvcvideo: Found UVC 1.00 device HD WebCam (1bcf:2c6b)
[    5.501373] iwlwifi 0000:04:00.0: loaded firmware version 16.242414.0 op_mode iwlmvm
[    5.509084] input: HD WebCam as /devices/pci0000:00/0000:00:14.0/usb3/3-4/3-4:1.0/input/input13
[    5.512811] usbcore: registered new interface driver uvcvideo
[    5.512820] USB Video Class driver (1.1.1)
[    5.564074] snd_hda_intel 0000:00:03.0: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
[    5.582168] iwlwifi 0000:04:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
[    5.582307] iwlwifi 0000:04:00.0: L1 Enabled - LTR Enabled
[    5.582590] iwlwifi 0000:04:00.0: L1 Enabled - LTR Enabled
[    5.601192] input: HDA Intel HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:03.0/sound/card0/input14
[    5.601471] input: HDA Intel HDMI HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:03.0/sound/card0/input15
[    5.601737] input: HDA Intel HDMI HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:03.0/sound/card0/input16
[    5.648612] AVX2 version of gcm_enc/dec engaged.
[    5.648620] AES CTR mode by8 optimization enabled
[    5.814192] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    5.822687] asus_wmi: Asus Management GUID not found
[    5.823108] intel_rapl: Found RAPL domain package
[    5.823114] intel_rapl: Found RAPL domain core
[    5.823119] intel_rapl: Found RAPL domain uncore
[    5.823124] intel_rapl: Found RAPL domain dram
[    5.823133] intel_rapl: RAPL package 0 domain package locked by BIOS
[    5.823145] intel_rapl: RAPL package 0 domain dram locked by BIOS
[    5.974324] nvidia-modeset: Loading NVIDIA Kernel Mode Setting Driver for UNIX platforms  361.42  Tue Mar 22 17:29:54 PDT 2016
[    5.997174] iwlwifi 0000:04:00.0 wlp4s0: renamed from wlan0
[    6.021041] cfg80211: World regulatory domain updated:
[    6.021050] cfg80211:  DFS Master region: unset
[    6.021054] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[    6.021062] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[    6.021069] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[    6.021074] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
[    6.021081] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
[    6.021089] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
[    6.021095] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
[    6.021100] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
[    6.021107] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
[    6.041621] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    6.041628] Bluetooth: BNEP filters: protocol multicast
[    6.041636] Bluetooth: BNEP socket layer initialized
[    6.127697] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[    6.142190] r8169 0000:03:00.0 enp3s0: link down
[    6.142334] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[    6.166228] IPv6: ADDRCONF(NETDEV_UP): wlp4s0: link is not ready
[    6.166395] iwlwifi 0000:04:00.0: L1 Enabled - LTR Enabled
[    6.166679] iwlwifi 0000:04:00.0: L1 Enabled - LTR Enabled
[    6.389319] iwlwifi 0000:04:00.0: L1 Enabled - LTR Enabled
[    6.389592] iwlwifi 0000:04:00.0: L1 Enabled - LTR Enabled
[    6.404793] IPv6: ADDRCONF(NETDEV_UP): wlp4s0: link is not ready
[    8.754878] Bluetooth: RFCOMM TTY layer initialized
[    8.754894] Bluetooth: RFCOMM socket layer initialized
[    8.754907] Bluetooth: RFCOMM ver 1.11
[  217.111249] usb 3-9: new high-speed USB device number 4 using xhci_hcd
[  217.266150] usb 3-9: New USB device found, idVendor=090c, idProduct=1000
[  217.266154] usb 3-9: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  217.266157] usb 3-9: Product: Flash Disk
[  217.266159] usb 3-9: Manufacturer: USB
[  217.266161] usb 3-9: SerialNumber: FBF1008180000429
[  217.266356] usb 3-9: ep 0x81 - rounding interval to 128 microframes, ep desc says 255 microframes
[  217.266361] usb 3-9: ep 0x2 - rounding interval to 128 microframes, ep desc says 255 microframes
[  217.277546] usb-storage 3-9:1.0: USB Mass Storage device detected
[  217.277598] scsi host6: usb-storage 3-9:1.0
[  217.277650] usbcore: registered new interface driver usb-storage
[  217.278835] usbcore: registered new interface driver uas
[  218.653556] scsi 6:0:0:0: Direct-Access     USB      Flash Disk       1100 PQ: 0 ANSI: 0 CCS
[  218.653944] sd 6:0:0:0: Attached scsi generic sg2 type 0
[  218.654244] sd 6:0:0:0: [sdc] 15663104 512-byte logical blocks: (8.02 GB/7.47 GiB)
[  218.655041] sd 6:0:0:0: [sdc] Write Protect is off
[  218.655045] sd 6:0:0:0: [sdc] Mode Sense: 43 00 00 00
[  218.655837] sd 6:0:0:0: [sdc] No Caching mode page found
[  218.656632] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[  218.660979]  sdc: sdc1 sdc2
[  218.663628] sd 6:0:0:0: [sdc] Attached SCSI removable disk
[  266.677502] ISO 9660 Extensions: Microsoft Joliet Level 3
[  266.680844] ISO 9660 Extensions: RRIP_1991A

```

When trying ```
unity
``` from the terminal I get a ```
WARNING: no DISPLAY variable set, setting it to :0
```

My /etc/lightdm/lightdm.conf looks like this
```
[Seat:*]
autologin-guest=false
autologin-user=toast
autologin-user-timeout=0
```

That all looks good.

```
less default-display-manager
``` outputs ```
/usr/sbin/lightdm
```

Provided everything I can think of, any ideas to help me out?

---

### Post by mastablasta on 2016-05-17
looks like driver loads normally: 

```
[    5.974324] nvidia-modeset: Loading NVIDIA Kernel Mode Setting Driver for UNIX platforms  361.42  Tue Mar 22 17:29:54 PDT 2016
```

i don't see any major erros in dmesg.

how did you install the driver? additional drivers application? did you run some GUI application with *sudo* maybe?

---

### Post by Toast2120 on 2016-05-17
Ran it through Synaptic, selecting the "nvidia-current" driver selects "nvidia-prime" by default. Also worth mentioning that this is the second time I've reinstalled the OS. Also performed the same process through apt-get on a previous installation. No additional programs were run, nothing with sudo or by way of terminal.


edit: additional info

---

### Post by Bashing-om on 2016-05-17
Toast2120; Hello;

Might prove beneficial to see what the situation is in X
```

cat /var/log/Xorg.0.log

```
and confirm what the system thinks it has loaded for a graphic's driver:
```

sudo lshw -C display

```

I have also seen this condition arise with a conflict in the driver sources, will behoove us to check this possibility.
```

tail -v -n +1 /etc/apt/sources.list.d/*

``` to see if there are external sources for drivers.

[INDENT][INDENT]cause and effect
[INDENT][INDENT][INDENT]got to be a reason
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Toast2120 on 2016-05-17
Alright! Here's the output

xorg log

```
[    14.394] 
X.Org X Server 1.18.3
Release Date: 2016-04-04
[    14.394] X Protocol Version 11, Revision 0
[    14.394] Build Operating System: Linux 3.13.0-85-generic x86_64 Ubuntu
[    14.394] Current Operating System: Linux pancake 4.4.0-22-generic #40-Ubuntu SMP Thu May 12 22:03:46 UTC 2016 x86_64
[    14.394] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-22-generic root=UUID=a35e04a1-3b9c-46b3-b722-2539da2dde9a ro quiet splash
[    14.394] Build Date: 07 April 2016  09:18:50AM
[    14.394] xorg-server 2:1.18.3-1ubuntu2 (For technical support please see http://www.ubuntu.com/support) 
[    14.394] Current version of pixman: 0.33.6
[    14.394] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    14.394] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    14.394] (==) Log file: "/var/log/Xorg.0.log", Time: Tue May 17 14:20:31 2016
[    14.394] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    14.394] (==) No Layout section.  Using the first Screen section.
[    14.394] (==) No screen section available. Using defaults.
[    14.394] (**) |-->Screen "Default Screen Section" (0)
[    14.394] (**) |   |-->Monitor "<default monitor>"
[    14.394] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    14.394] (==) Automatically adding devices
[    14.394] (==) Automatically enabling devices
[    14.394] (==) Automatically adding GPU devices
[    14.394] (==) Max clients allowed: 256, resource mask: 0x1fffff
[    14.394] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    14.394] 	Entry deleted from font path.
[    14.394] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    14.394] 	Entry deleted from font path.
[    14.394] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    14.394] 	Entry deleted from font path.
[    14.394] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    14.394] 	Entry deleted from font path.
[    14.394] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    14.394] 	Entry deleted from font path.
[    14.394] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    14.394] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    14.394] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    14.394] (II) Loader magic: 0x55aad0678da0
[    14.394] (II) Module ABI versions:
[    14.394] 	X.Org ANSI C Emulation: 0.4
[    14.394] 	X.Org Video Driver: 20.0
[    14.394] 	X.Org XInput driver : 22.1
[    14.394] 	X.Org Server Extension : 9.0
[    14.394] (++) using VT number 7

[    14.394] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
[    14.395] (II) xfree86: Adding drm device (/dev/dri/card1)
[    14.395] (II) xfree86: Adding drm device (/dev/dri/card0)
[    14.396] (--) PCI:*(0:0:2:0) 8086:1612:1458:a456 rev 10, Mem @ 0xa1000000/16777216, 0xb0000000/268435456, I/O @ 0x00006000/64
[    14.396] (--) PCI: (0:1:0:0) 10de:13d8:1458:a456 rev 161, Mem @ 0xa2000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x00005000/128, BIOS @ 0x????????/524288
[    14.396] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    14.396] (II) "glx" will be loaded by default.
[    14.396] (II) LoadModule: "glx"
[    14.396] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    14.397] (II) Module glx: vendor="X.Org Foundation"
[    14.397] 	compiled for 1.18.3, module version = 1.0.0
[    14.397] 	ABI class: X.Org Server Extension, version 9.0
[    14.397] (==) AIGLX enabled
[    14.397] (==) Matched intel as autoconfigured driver 0
[    14.397] (==) Matched nvidia as autoconfigured driver 1
[    14.397] (==) Matched nouveau as autoconfigured driver 2
[    14.397] (==) Matched intel as autoconfigured driver 3
[    14.397] (==) Matched modesetting as autoconfigured driver 4
[    14.397] (==) Matched fbdev as autoconfigured driver 5
[    14.397] (==) Matched vesa as autoconfigured driver 6
[    14.397] (==) Assigned the driver to the xf86ConfigLayout
[    14.397] (II) LoadModule: "intel"
[    14.397] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    14.397] (II) Module intel: vendor="X.Org Foundation"
[    14.397] 	compiled for 1.18.1, module version = 2.99.917
[    14.397] 	Module class: X.Org Video Driver
[    14.397] 	ABI class: X.Org Video Driver, version 20.0
[    14.397] (II) LoadModule: "nvidia"
[    14.397] (WW) Warning, couldn't open module nvidia
[    14.397] (II) UnloadModule: "nvidia"
[    14.397] (II) Unloading nvidia
[    14.397] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    14.397] (II) LoadModule: "nouveau"
[    14.397] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    14.397] (II) Module nouveau: vendor="X.Org Foundation"
[    14.397] 	compiled for 1.18.1, module version = 1.0.12
[    14.397] 	Module class: X.Org Video Driver
[    14.397] 	ABI class: X.Org Video Driver, version 20.0
[    14.397] (II) LoadModule: "modesetting"
[    14.397] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    14.397] (II) Module modesetting: vendor="X.Org Foundation"
[    14.397] 	compiled for 1.18.3, module version = 1.18.3
[    14.397] 	Module class: X.Org Video Driver
[    14.397] 	ABI class: X.Org Video Driver, version 20.0
[    14.397] (II) LoadModule: "fbdev"
[    14.397] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    14.397] (II) Module fbdev: vendor="X.Org Foundation"
[    14.397] 	compiled for 1.18.1, module version = 0.4.4
[    14.397] 	Module class: X.Org Video Driver
[    14.397] 	ABI class: X.Org Video Driver, version 20.0
[    14.397] (II) LoadModule: "vesa"
[    14.398] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    14.398] (II) Module vesa: vendor="X.Org Foundation"
[    14.398] 	compiled for 1.18.1, module version = 2.3.4
[    14.398] 	Module class: X.Org Video Driver
[    14.398] 	ABI class: X.Org Video Driver, version 20.0
[    14.398] (==) Matched intel as autoconfigured driver 0
[    14.398] (==) Matched nvidia as autoconfigured driver 1
[    14.398] (==) Matched nouveau as autoconfigured driver 2
[    14.398] (==) Matched intel as autoconfigured driver 3
[    14.398] (==) Matched modesetting as autoconfigured driver 4
[    14.398] (==) Matched fbdev as autoconfigured driver 5
[    14.398] (==) Matched vesa as autoconfigured driver 6
[    14.398] (==) Assigned the driver to the xf86ConfigLayout
[    14.398] (II) LoadModule: "intel"
[    14.398] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    14.398] (II) Module intel: vendor="X.Org Foundation"
[    14.398] 	compiled for 1.18.1, module version = 2.99.917
[    14.398] 	Module class: X.Org Video Driver
[    14.398] 	ABI class: X.Org Video Driver, version 20.0
[    14.398] (II) UnloadModule: "intel"
[    14.398] (II) Unloading intel
[    14.398] (II) Failed to load module "intel" (already loaded, 21930)
[    14.398] (II) LoadModule: "nvidia"
[    14.398] (WW) Warning, couldn't open module nvidia
[    14.398] (II) UnloadModule: "nvidia"
[    14.398] (II) Unloading nvidia
[    14.398] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    14.398] (II) LoadModule: "nouveau"
[    14.398] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    14.398] (II) Module nouveau: vendor="X.Org Foundation"
[    14.398] 	compiled for 1.18.1, module version = 1.0.12
[    14.398] 	Module class: X.Org Video Driver
[    14.398] 	ABI class: X.Org Video Driver, version 20.0
[    14.398] (II) UnloadModule: "nouveau"
[    14.398] (II) Unloading nouveau
[    14.398] (II) Failed to load module "nouveau" (already loaded, 0)
[    14.398] (II) LoadModule: "modesetting"
[    14.398] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    14.398] (II) Module modesetting: vendor="X.Org Foundation"
[    14.398] 	compiled for 1.18.3, module version = 1.18.3
[    14.398] 	Module class: X.Org Video Driver
[    14.398] 	ABI class: X.Org Video Driver, version 20.0
[    14.398] (II) UnloadModule: "modesetting"
[    14.398] (II) Unloading modesetting
[    14.398] (II) Failed to load module "modesetting" (already loaded, 0)
[    14.398] (II) LoadModule: "fbdev"
[    14.398] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    14.398] (II) Module fbdev: vendor="X.Org Foundation"
[    14.398] 	compiled for 1.18.1, module version = 0.4.4
[    14.398] 	Module class: X.Org Video Driver
[    14.398] 	ABI class: X.Org Video Driver, version 20.0
[    14.398] (II) UnloadModule: "fbdev"
[    14.398] (II) Unloading fbdev
[    14.398] (II) Failed to load module "fbdev" (already loaded, 0)
[    14.398] (II) LoadModule: "vesa"
[    14.398] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    14.398] (II) Module vesa: vendor="X.Org Foundation"
[    14.398] 	compiled for 1.18.1, module version = 2.3.4
[    14.398] 	Module class: X.Org Video Driver
[    14.398] 	ABI class: X.Org Video Driver, version 20.0
[    14.398] (II) UnloadModule: "vesa"
[    14.398] (II) Unloading vesa
[    14.398] (II) Failed to load module "vesa" (already loaded, 0)
[    14.398] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
	i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
	915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
	Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
	GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[    14.398] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[    14.398] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[    14.398] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[    14.398] (II) NOUVEAU driver Date:   Tue Dec 8 15:52:25 2015 +1000
[    14.398] (II) NOUVEAU driver for NVIDIA chipset families :
[    14.398] 	RIVA TNT        (NV04)
[    14.398] 	RIVA TNT2       (NV05)
[    14.398] 	GeForce 256     (NV10)
[    14.398] 	GeForce 2       (NV11, NV15)
[    14.398] 	GeForce 4MX     (NV17, NV18)
[    14.398] 	GeForce 3       (NV20)
[    14.398] 	GeForce 4Ti     (NV25, NV28)
[    14.398] 	GeForce FX      (NV3x)
[    14.398] 	GeForce 6       (NV4x)
[    14.398] 	GeForce 7       (G7x)
[    14.398] 	GeForce 8       (G8x)
[    14.398] 	GeForce GTX 200 (NVA0)
[    14.398] 	GeForce GTX 400 (NVC0)
[    14.398] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    14.398] (II) FBDEV: driver for framebuffer: fbdev
[    14.398] (II) VESA: driver for VESA chipsets: vesa
[    14.398] (II) intel(0): Using Kernel Mode Setting driver: i915, version 1.6.0 20151010
[    14.398] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.99.917+git20160325-1ubuntu1 (Timo Aaltonen <tjaalton@debian.org>)
[    14.398] (II) intel(0): SNA compiled for use with valgrind
[    14.399] (EE) [drm] Failed to open DRM device for (null): -22
[    14.399] (WW) Falling back to old probe method for modesetting
[    14.399] (WW) Falling back to old probe method for fbdev
[    14.399] (II) Loading sub module "fbdevhw"
[    14.399] (II) LoadModule: "fbdevhw"
[    14.399] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    14.399] (II) Module fbdevhw: vendor="X.Org Foundation"
[    14.399] 	compiled for 1.18.3, module version = 0.0.2
[    14.399] 	ABI class: X.Org Video Driver, version 20.0
[    14.399] (WW) Falling back to old probe method for vesa
[    14.399] (--) intel(0): Integrated Graphics Chipset: Intel(R) HD Graphics 5600
[    14.399] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2, avx, avx2; using a maximum of 4 threads
[    14.399] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    14.399] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    14.399] (==) intel(0): RGB weight 888
[    14.399] (==) intel(0): Default visual is TrueColor
[    14.399] (II) intel(0): Output eDP1 has no monitor section
[    14.416] (--) intel(0): Found backlight control interface intel_backlight (type 'raw') for output eDP1
[    14.416] (II) intel(0): Enabled output eDP1
[    14.416] (II) intel(0): Output VGA1 has no monitor section
[    14.416] (II) intel(0): Enabled output VGA1
[    14.416] (II) intel(0): Output HDMI1 has no monitor section
[    14.416] (II) intel(0): Enabled output HDMI1
[    14.416] (II) intel(0): Output DP1 has no monitor section
[    14.416] (II) intel(0): Enabled output DP1
[    14.416] (II) intel(0): Output HDMI2 has no monitor section
[    14.416] (II) intel(0): Enabled output HDMI2
[    14.416] (--) intel(0): Using a maximum size of 256x256 for hardware cursors
[    14.416] (II) intel(0): Output VIRTUAL1 has no monitor section
[    14.416] (II) intel(0): Enabled output VIRTUAL1
[    14.416] (--) intel(0): Output eDP1 using initial mode 1920x1080 on pipe 0
[    14.416] (==) intel(0): TearFree disabled
[    14.416] (==) intel(0): DPI set to (96, 96)
[    14.416] (II) Loading sub module "dri2"
[    14.416] (II) LoadModule: "dri2"
[    14.416] (II) Module "dri2" already built-in
[    14.416] (II) Loading sub module "present"
[    14.416] (II) LoadModule: "present"
[    14.416] (II) Module "present" already built-in
[    14.416] (II) UnloadModule: "fbdev"
[    14.416] (II) Unloading fbdev
[    14.416] (II) UnloadSubModule: "fbdevhw"
[    14.416] (II) Unloading fbdevhw
[    14.416] (II) UnloadModule: "vesa"
[    14.416] (II) Unloading vesa
[    14.416] (==) Depth 24 pixmap format is 32 bpp
[    14.417] (II) intel(0): SNA initialized with Broadwell (gen8) backend
[    14.417] (==) intel(0): Backing store enabled
[    14.417] (==) intel(0): Silken mouse enabled
[    14.417] (II) intel(0): HW Cursor enabled
[    14.417] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    14.417] (==) intel(0): DPMS enabled
[    14.417] (==) intel(0): Display hotplug detection enabled
[    14.417] (II) intel(0): [DRI2] Setup complete
[    14.417] (II) intel(0): [DRI2]   DRI driver: i965
[    14.417] (II) intel(0): [DRI2]   VDPAU driver: va_gl
[    14.417] (II) intel(0): direct rendering: DRI2 enabled
[    14.417] (II) intel(0): hardware support for Present enabled
[    14.417] (--) RandR disabled
[    14.419] (II) SELinux: Disabled on system
[    14.424] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    14.424] (II) AIGLX: enabled GLX_ARB_create_context
[    14.424] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    14.424] (II) AIGLX: enabled GLX_EXT_create_context_es{,2}_profile
[    14.424] (II) AIGLX: enabled GLX_INTEL_swap_event
[    14.424] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    14.424] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[    14.424] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[    14.424] (II) AIGLX: enabled GLX_EXT_fbconfig_packed_float
[    14.424] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    14.424] (II) AIGLX: enabled GLX_ARB_create_context_robustness
[    14.424] (II) AIGLX: Loaded and initialized i965
[    14.424] (II) GLX: Initialized DRI2 GL provider for screen 0
[    14.426] (II) intel(0): switch to mode 1920x1080@60.0 on eDP1 using pipe 0, position (0, 0), rotation normal, reflection none
[    14.426] (II) intel(0): Setting screen physical size to 508 x 285
[    14.444] (II) config/udev: Adding input device Power Button (/dev/input/event4)
[    14.444] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    14.444] (II) LoadModule: "evdev"
[    14.444] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    14.444] (II) Module evdev: vendor="X.Org Foundation"
[    14.444] 	compiled for 1.18.1, module version = 2.10.1
[    14.444] 	Module class: X.Org XInput Driver
[    14.444] 	ABI class: X.Org XInput driver, version 22.1
[    14.444] (II) Using input driver 'evdev' for 'Power Button'
[    14.444] (**) Power Button: always reports core events
[    14.444] (**) evdev: Power Button: Device: "/dev/input/event4"
[    14.444] (--) evdev: Power Button: Vendor 0 Product 0x1
[    14.445] (--) evdev: Power Button: Found keys
[    14.445] (II) evdev: Power Button: Configuring as keyboard
[    14.445] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input4/event4"
[    14.445] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    14.445] (**) Option "xkb_rules" "evdev"
[    14.445] (**) Option "xkb_model" "pc105"
[    14.445] (**) Option "xkb_layout" "us"
[    14.445] (II) config/udev: Adding input device Video Bus (/dev/input/event6)
[    14.445] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    14.445] (II) Using input driver 'evdev' for 'Video Bus'
[    14.445] (**) Video Bus: always reports core events
[    14.445] (**) evdev: Video Bus: Device: "/dev/input/event6"
[    14.445] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    14.445] (--) evdev: Video Bus: Found keys
[    14.445] (II) evdev: Video Bus: Configuring as keyboard
[    14.445] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input9/event6"
[    14.445] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    14.445] (**) Option "xkb_rules" "evdev"
[    14.445] (**) Option "xkb_model" "pc105"
[    14.445] (**) Option "xkb_layout" "us"
[    14.445] (II) config/udev: Adding input device Video Bus (/dev/input/event7)
[    14.445] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    14.445] (II) Using input driver 'evdev' for 'Video Bus'
[    14.445] (**) Video Bus: always reports core events
[    14.445] (**) evdev: Video Bus: Device: "/dev/input/event7"
[    14.445] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    14.445] (--) evdev: Video Bus: Found keys
[    14.445] (II) evdev: Video Bus: Configuring as keyboard
[    14.445] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:12/LNXVIDEO:01/input/input10/event7"
[    14.445] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 8)
[    14.445] (**) Option "xkb_rules" "evdev"
[    14.445] (**) Option "xkb_model" "pc105"
[    14.445] (**) Option "xkb_layout" "us"
[    14.446] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    14.446] (II) No input driver specified, ignoring this device.
[    14.446] (II) This device may have been added with another device file.
[    14.446] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    14.446] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    14.446] (II) Using input driver 'evdev' for 'Sleep Button'
[    14.446] (**) Sleep Button: always reports core events
[    14.446] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[    14.446] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    14.446] (--) evdev: Sleep Button: Found keys
[    14.446] (II) evdev: Sleep Button: Configuring as keyboard
[    14.446] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:17/PNP0C09:01/PNP0C0E:00/input/input1/event1"
[    14.446] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[    14.446] (**) Option "xkb_rules" "evdev"
[    14.446] (**) Option "xkb_model" "pc105"
[    14.446] (**) Option "xkb_layout" "us"
[    14.446] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    14.446] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    14.446] (II) Using input driver 'evdev' for 'Power Button'
[    14.446] (**) Power Button: always reports core events
[    14.446] (**) evdev: Power Button: Device: "/dev/input/event3"
[    14.446] (--) evdev: Power Button: Vendor 0 Product 0x1
[    14.446] (--) evdev: Power Button: Found keys
[    14.446] (II) evdev: Power Button: Configuring as keyboard
[    14.446] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input3/event3"
[    14.446] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 10)
[    14.446] (**) Option "xkb_rules" "evdev"
[    14.446] (**) Option "xkb_model" "pc105"
[    14.446] (**) Option "xkb_layout" "us"
[    14.446] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    14.446] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    14.446] (II) Using input driver 'evdev' for 'Sleep Button'
[    14.446] (**) Sleep Button: always reports core events
[    14.446] (**) evdev: Sleep Button: Device: "/dev/input/event2"
[    14.446] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    14.446] (--) evdev: Sleep Button: Found keys
[    14.446] (II) evdev: Sleep Button: Configuring as keyboard
[    14.446] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:01/input/input2/event2"
[    14.447] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 11)
[    14.447] (**) Option "xkb_rules" "evdev"
[    14.447] (**) Option "xkb_model" "pc105"
[    14.447] (**) Option "xkb_layout" "us"
[    14.447] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=3 (/dev/input/event11)
[    14.447] (II) No input driver specified, ignoring this device.
[    14.447] (II) This device may have been added with another device file.
[    14.447] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=7 (/dev/input/event12)
[    14.447] (II) No input driver specified, ignoring this device.
[    14.447] (II) This device may have been added with another device file.
[    14.447] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=8 (/dev/input/event13)
[    14.447] (II) No input driver specified, ignoring this device.
[    14.447] (II) This device may have been added with another device file.
[    14.447] (II) config/udev: Adding input device HD WebCam (/dev/input/event14)
[    14.447] (**) HD WebCam: Applying InputClass "evdev keyboard catchall"
[    14.447] (II) Using input driver 'evdev' for 'HD WebCam'
[    14.447] (**) HD WebCam: always reports core events
[    14.447] (**) evdev: HD WebCam: Device: "/dev/input/event14"
[    14.447] (--) evdev: HD WebCam: Vendor 0x1bcf Product 0x2c6b
[    14.447] (--) evdev: HD WebCam: Found keys
[    14.447] (II) evdev: HD WebCam: Configuring as keyboard
[    14.447] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-4/3-4:1.0/input/input16/event14"
[    14.447] (II) XINPUT: Adding extended input device "HD WebCam" (type: KEYBOARD, id 12)
[    14.447] (**) Option "xkb_rules" "evdev"
[    14.447] (**) Option "xkb_model" "pc105"
[    14.447] (**) Option "xkb_layout" "us"
[    14.448] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event9)
[    14.448] (II) No input driver specified, ignoring this device.
[    14.448] (II) This device may have been added with another device file.
[    14.448] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event10)
[    14.448] (II) No input driver specified, ignoring this device.
[    14.448] (II) This device may have been added with another device file.
[    14.448] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event5)
[    14.448] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    14.448] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    14.448] (**) AT Translated Set 2 keyboard: always reports core events
[    14.448] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event5"
[    14.448] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    14.448] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    14.448] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    14.448] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input7/event5"
[    14.448] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 13)
[    14.448] (**) Option "xkb_rules" "evdev"
[    14.448] (**) Option "xkb_model" "pc105"
[    14.448] (**) Option "xkb_layout" "us"
[    14.448] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/event8)
[    14.448] (**) ETPS/2 Elantech Touchpad: Applying InputClass "evdev touchpad catchall"
[    14.448] (**) ETPS/2 Elantech Touchpad: Applying InputClass "evdev touchscreen catchall"
[    14.448] (**) ETPS/2 Elantech Touchpad: Applying InputClass "touchpad catchall"
[    14.448] (**) ETPS/2 Elantech Touchpad: Applying InputClass "Default clickpad buttons"
[    14.448] (II) LoadModule: "synaptics"
[    14.448] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    14.449] (II) Module synaptics: vendor="X.Org Foundation"
[    14.449] 	compiled for 1.18.1, module version = 1.8.2
[    14.449] 	Module class: X.Org XInput Driver
[    14.449] 	ABI class: X.Org XInput driver, version 22.1
[    14.449] (II) Using input driver 'synaptics' for 'ETPS/2 Elantech Touchpad'
[    14.449] (**) ETPS/2 Elantech Touchpad: always reports core events
[    14.449] (**) Option "Device" "/dev/input/event8"
[    14.504] (II) synaptics: ETPS/2 Elantech Touchpad: ignoring touch events for semi-multitouch device
[    14.504] (--) synaptics: ETPS/2 Elantech Touchpad: x-axis range 0 - 2772 (res 31)
[    14.504] (--) synaptics: ETPS/2 Elantech Touchpad: y-axis range 0 - 1320 (res 31)
[    14.504] (--) synaptics: ETPS/2 Elantech Touchpad: pressure range 0 - 255
[    14.504] (--) synaptics: ETPS/2 Elantech Touchpad: finger width range 0 - 15
[    14.504] (--) synaptics: ETPS/2 Elantech Touchpad: buttons: left right double triple
[    14.504] (--) synaptics: ETPS/2 Elantech Touchpad: Vendor 0x2 Product 0xe
[    14.504] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[    14.504] (**) ETPS/2 Elantech Touchpad: always reports core events
[    14.528] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input8/event8"
[    14.528] (II) XINPUT: Adding extended input device "ETPS/2 Elantech Touchpad" (type: TOUCHPAD, id 14)
[    14.528] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MinSpeed is now constant deceleration 2.5
[    14.528] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MaxSpeed is now 1.75
[    14.528] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) AccelFactor is now 0.065
[    14.528] (**) ETPS/2 Elantech Touchpad: (accel) keeping acceleration scheme 1
[    14.528] (**) ETPS/2 Elantech Touchpad: (accel) acceleration profile 1
[    14.528] (**) ETPS/2 Elantech Touchpad: (accel) acceleration factor: 2.000
[    14.528] (**) ETPS/2 Elantech Touchpad: (accel) acceleration threshold: 4
[    14.528] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[    14.528] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/mouse0)
[    14.528] (**) ETPS/2 Elantech Touchpad: Ignoring device from InputClass "touchpad ignore duplicates"
[    14.745] (II) intel(0): EDID vendor "LGD", prod id 1023
[    14.745] (II) intel(0): Printing DDC gathered Modelines:
[    14.745] (II) intel(0): Modeline "1920x1080"x0.0  138.70  1920 1968 2000 2080  1080 1083 1088 1111 -hsync -vsync (66.7 kHz eP)
[    16.912] (II) AIGLX: Suspending AIGLX clients for VT switch

```

There was a second xorg log as well, here is that too
```
[   600.450] 
X.Org X Server 1.18.3
Release Date: 2016-04-04
[   600.450] X Protocol Version 11, Revision 0
[   600.450] Build Operating System: Linux 3.13.0-85-generic x86_64 Ubuntu
[   600.450] Current Operating System: Linux pancake 4.4.0-22-generic #40-Ubuntu SMP Thu May 12 22:03:46 UTC 2016 x86_64
[   600.450] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-22-generic root=UUID=a35e04a1-3b9c-46b3-b722-2539da2dde9a ro quiet splash
[   600.450] Build Date: 07 April 2016  09:18:50AM
[   600.450] xorg-server 2:1.18.3-1ubuntu2 (For technical support please see http://www.ubuntu.com/support) 
[   600.450] Current version of pixman: 0.33.6
[   600.450] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[   600.450] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   600.450] (==) Log file: "/var/log/Xorg.2.log", Time: Mon May 16 22:23:58 2016
[   600.450] (==) Using config file: "/etc/X11/xorg.conf"
[   600.450] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   600.451] (==) ServerLayout "layout"
[   600.451] (**) |-->Screen "nvidia" (0)
[   600.451] (**) |   |-->Monitor "<default monitor>"
[   600.451] (**) |   |-->Device "nvidia"
[   600.451] (**) |   |-->GPUDevice "nvidia"
[   600.451] (==) No monitor specified for screen "nvidia".
	Using a default monitor configuration.
[   600.451] (**) |-->Inactive Device "intel"
[   600.451] (==) Automatically adding devices
[   600.451] (==) Automatically enabling devices
[   600.451] (==) Automatically adding GPU devices
[   600.451] (==) Max clients allowed: 256, resource mask: 0x1fffff
[   600.451] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   600.451] 	Entry deleted from font path.
[   600.451] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   600.451] 	Entry deleted from font path.
[   600.451] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   600.451] 	Entry deleted from font path.
[   600.451] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   600.451] 	Entry deleted from font path.
[   600.451] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   600.451] 	Entry deleted from font path.
[   600.451] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[   600.451] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   600.451] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[   600.451] (II) Loader magic: 0x560c4b7a7da0
[   600.451] (II) Module ABI versions:
[   600.451] 	X.Org ANSI C Emulation: 0.4
[   600.451] 	X.Org Video Driver: 20.0
[   600.451] 	X.Org XInput driver : 22.1
[   600.451] 	X.Org Server Extension : 9.0
[   600.452] (++) using VT number 2

[   600.454] (II) systemd-logind: took control of session /org/freedesktop/login1/session/_33
[   600.454] (II) xfree86: Adding drm device (/dev/dri/card1)
[   600.455] (II) systemd-logind: got fd for /dev/dri/card1 226:1 fd 8 paused 1
[   600.455] (EE) Error systemd-logind returned paused fd for drm node
[   600.455] (II) systemd-logind: releasing fd for 226:1
[   600.455] (II) config/udev: Ignoring already known drm device (/dev/dri/card1)
[   600.455] (II) xfree86: Adding drm device (/dev/dri/card0)
[   600.457] (II) systemd-logind: got fd for /dev/dri/card0 226:0 fd 9 paused 0
[   600.458] (--) PCI:*(0:0:2:0) 8086:1612:1458:a456 rev 10, Mem @ 0xa1000000/16777216, 0xb0000000/268435456, I/O @ 0x00006000/64
[   600.458] (--) PCI: (0:1:0:0) 10de:13d8:1458:a456 rev 161, Mem @ 0xa2000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x00005000/128, BIOS @ 0x????????/524288
[   600.458] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[   600.458] (II) "glx" will be loaded by default.
[   600.458] (II) LoadModule: "glx"
[   600.458] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[   600.462] (II) Module glx: vendor="NVIDIA Corporation"
[   600.462] 	compiled for 4.0.2, module version = 1.0.0
[   600.462] 	Module class: X.Org Server Extension
[   600.462] (II) NVIDIA GLX Module  361.42  Tue Mar 22 17:25:45 PDT 2016
[   600.462] (II) LoadModule: "nvidia"
[   600.462] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[   600.462] (II) Module nvidia: vendor="NVIDIA Corporation"
[   600.462] 	compiled for 4.0.2, module version = 1.0.0
[   600.462] 	Module class: X.Org Video Driver
[   600.462] (II) LoadModule: "modesetting"
[   600.462] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[   600.462] (II) Module modesetting: vendor="X.Org Foundation"
[   600.462] 	compiled for 1.18.3, module version = 1.18.3
[   600.462] 	Module class: X.Org Video Driver
[   600.462] 	ABI class: X.Org Video Driver, version 20.0
[   600.462] (II) NVIDIA dlloader X Driver  361.42  Tue Mar 22 17:04:20 PDT 2016
[   600.462] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[   600.462] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[   600.462] (II) Loading sub module "fb"
[   600.462] (II) LoadModule: "fb"
[   600.463] (II) Loading /usr/lib/xorg/modules/libfb.so
[   600.463] (II) Module fb: vendor="X.Org Foundation"
[   600.463] 	compiled for 1.18.3, module version = 1.0.0
[   600.463] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   600.463] (II) Loading sub module "wfb"
[   600.463] (II) LoadModule: "wfb"
[   600.463] (II) Loading /usr/lib/xorg/modules/libwfb.so
[   600.463] (II) Module wfb: vendor="X.Org Foundation"
[   600.463] 	compiled for 1.18.3, module version = 1.0.0
[   600.463] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   600.463] (II) Loading sub module "ramdac"
[   600.463] (II) LoadModule: "ramdac"
[   600.463] (II) Module "ramdac" already built-in
[   600.463] (II) modeset(G0): using drv /dev/dri/card0
[   600.463] (II) NVIDIA(0): Creating default Display subsection in Screen section
	"nvidia" for depth/fbbpp 24/32
[   600.463] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[   600.463] (==) NVIDIA(0): RGB weight 888
[   600.463] (==) NVIDIA(0): Default visual is TrueColor
[   600.463] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[   600.463] (**) NVIDIA(0): Option "ConstrainCursor" "off"
[   600.463] (**) NVIDIA(0): Option "AllowEmptyInitialConfiguration" "on"
[   600.463] (**) NVIDIA(0): Option "IgnoreDisplayDevices" "CRT"
[   600.463] (**) NVIDIA(0): Enabling 2D acceleration
[   600.465] (II) NVIDIA(GPU-0): Found DRM driver nvidia-drm (20150116)
[   600.465] (II) NVIDIA(0): NVIDIA GPU GeForce GTX 970M (GM204-A) at PCI:1:0:0 (GPU-0)
[   600.465] (--) NVIDIA(0): Memory: 3145728 kBytes
[   600.465] (--) NVIDIA(0): VideoBIOS: 84.04.6b.00.08
[   600.465] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[   600.465] (II) NVIDIA(0): Validated MetaModes:
[   600.465] (II) NVIDIA(0):     "NULL"
[   600.465] (II) NVIDIA(0): Virtual screen size determined to be 640 x 480
[   600.465] (WW) NVIDIA(0): Unable to get display device for DPI computation.
[   600.465] (==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
[   600.466] (==) modeset(G0): Depth 24, (==) framebuffer bpp 32
[   600.466] (**) modeset(G0): Option "AccelMethod" "None"
[   600.466] (==) modeset(G0): RGB weight 888
[   600.466] (==) modeset(G0): Default visual is TrueColor
[   600.466] (**) modeset(G0): glamor disabled
[   600.466] (II) modeset(G0): ShadowFB: preferred YES, enabled YES
[   600.466] (II) modeset(G0): Output eDP-1 has no monitor section
[   600.480] (II) modeset(G0): Output VGA-1 has no monitor section
[   600.608] (II) modeset(G0): Output HDMI-1 has no monitor section
[   600.608] (II) modeset(G0): Output DP-1 has no monitor section
[   600.736] (II) modeset(G0): Output HDMI-2 has no monitor section
[   600.736] (II) modeset(G0): EDID for output eDP-1
[   600.736] (II) modeset(G0): Manufacturer: LGD  Model: 3ff  Serial#: 0
[   600.736] (II) modeset(G0): Year: 2013  Week: 0
[   600.736] (II) modeset(G0): EDID Version: 1.4
[   600.736] (II) modeset(G0): Digital Display Input
[   600.736] (II) modeset(G0): 6 bits per channel
[   600.736] (II) modeset(G0): Digital interface is DisplayPort
[   600.736] (II) modeset(G0): Max Image Size [cm]: horiz.: 31  vert.: 17
[   600.736] (II) modeset(G0): Gamma: 2.20
[   600.736] (II) modeset(G0): DPMS capabilities: StandBy Suspend Off
[   600.736] (II) modeset(G0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[   600.736] (II) modeset(G0): First detailed timing is preferred mode
[   600.736] (II) modeset(G0): Preferred mode is native pixel format and refresh rate
[   600.736] (II) modeset(G0): redX: 0.640 redY: 0.345   greenX: 0.325 greenY: 0.630
[   600.736] (II) modeset(G0): blueX: 0.153 blueY: 0.032   whiteX: 0.313 whiteY: 0.329
[   600.736] (II) modeset(G0): Manufacturer's mask: 0
[   600.736] (II) modeset(G0): Supported detailed timing:
[   600.736] (II) modeset(G0): clock: 138.7 MHz   Image Size:  309 x 175 mm
[   600.736] (II) modeset(G0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
[   600.736] (II) modeset(G0): v_active: 1080  v_sync: 1083  v_sync_end 1088 v_blanking: 1111 v_border: 0
[   600.736] (II) modeset(G0):  LG Display
[   600.736] (II) modeset(G0):  LP140WF1-SPU1
[   600.736] (II) modeset(G0): EDID (in hex):
[   600.736] (II) modeset(G0): 	00ffffffffffff0030e4ff0300000000
[   600.736] (II) modeset(G0): 	00170104951f1178ead555a35853a127
[   600.736] (II) modeset(G0): 	08505400000001010101010101010101
[   600.736] (II) modeset(G0): 	0101010101012e3680a070381f403020
[   600.736] (II) modeset(G0): 	350035af100000190000000000000000
[   600.736] (II) modeset(G0): 	00000000000000000000000000fe004c
[   600.736] (II) modeset(G0): 	4720446973706c61790a2020000000fe
[   600.736] (II) modeset(G0): 	004c503134305746312d535055310070
[   600.736] (II) modeset(G0): Printing probed modes for output eDP-1
[   600.736] (II) modeset(G0): Modeline "1920x1080"x60.0  138.70  1920 1968 2000 2080  1080 1083 1088 1111 -hsync -vsync (66.7 kHz eP)
[   600.736] (II) modeset(G0): Modeline "1920x1080"x59.9  138.50  1920 1968 2000 2080  1080 1083 1088 1111 +hsync -vsync (66.6 kHz d)
[   600.736] (II) modeset(G0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz d)
[   600.736] (II) modeset(G0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz d)
[   600.736] (II) modeset(G0): Modeline "1600x1024"x60.2  103.12  1600 1600 1656 1664  1024 1024 1029 1030 +hsync +vsync (62.0 kHz d)
[   600.736] (II) modeset(G0): Modeline "1400x1050"x60.0  122.00  1400 1488 1640 1880  1050 1052 1064 1082 +hsync +vsync (64.9 kHz d)
[   600.736] (II) modeset(G0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz d)
[   600.736] (II) modeset(G0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz d)
[   600.736] (II) modeset(G0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz d)
[   600.736] (II) modeset(G0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz d)
[   600.736] (II) modeset(G0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz d)
[   600.736] (II) modeset(G0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz d)
[   600.737] (II) modeset(G0): Modeline "1024x768"x120.1  133.47  1024 1100 1212 1400  768 768 770 794 doublescan -hsync +vsync (95.3 kHz d)
[   600.737] (II) modeset(G0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz d)
[   600.737] (II) modeset(G0): Modeline "960x720"x120.0  117.00  960 1024 1128 1300  720 720 722 750 doublescan -hsync +vsync (90.0 kHz d)
[   600.737] (II) modeset(G0): Modeline "928x696"x120.1  109.15  928 976 1088 1264  696 696 698 719 doublescan -hsync +vsync (86.4 kHz d)
[   600.737] (II) modeset(G0): Modeline "896x672"x120.0  102.40  896 960 1060 1224  672 672 674 697 doublescan -hsync +vsync (83.7 kHz d)
[   600.737] (II) modeset(G0): Modeline "960x600"x120.0   77.00  960 984 1000 1040  600 601 604 617 doublescan +hsync -vsync (74.0 kHz d)
[   600.737] (II) modeset(G0): Modeline "960x540"x120.0   69.25  960 984 1000 1040  540 541 544 555 doublescan +hsync -vsync (66.6 kHz d)
[   600.737] (II) modeset(G0): Modeline "800x600"x120.0   81.00  800 832 928 1080  600 600 602 625 doublescan +hsync +vsync (75.0 kHz d)
[   600.737] (II) modeset(G0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz d)
[   600.737] (II) modeset(G0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz d)
[   600.737] (II) modeset(G0): Modeline "840x525"x120.0   73.12  840 892 980 1120  525 526 529 544 doublescan -hsync +vsync (65.3 kHz d)
[   600.737] (II) modeset(G0): Modeline "840x525"x119.8   59.50  840 864 880 920  525 526 529 540 doublescan +hsync -vsync (64.7 kHz d)
[   600.737] (II) modeset(G0): Modeline "800x512"x120.3   51.56  800 800 828 832  512 512 514 515 doublescan +hsync +vsync (62.0 kHz d)
[   600.737] (II) modeset(G0): Modeline "700x525"x120.0   61.00  700 744 820 940  525 526 532 541 doublescan +hsync +vsync (64.9 kHz d)
[   600.737] (II) modeset(G0): Modeline "640x512"x120.0   54.00  640 664 720 844  512 512 514 533 doublescan +hsync +vsync (64.0 kHz d)
[   600.737] (II) modeset(G0): Modeline "720x450"x119.8   53.25  720 760 836 952  450 451 454 467 doublescan -hsync +vsync (55.9 kHz d)
[   600.737] (II) modeset(G0): Modeline "640x480"x120.0   54.00  640 688 744 900  480 480 482 500 doublescan +hsync +vsync (60.0 kHz d)
[   600.737] (II) modeset(G0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz d)
[   600.737] (II) modeset(G0): Modeline "680x384"x119.6   42.38  680 716 784 888  384 385 390 399 doublescan -hsync +vsync (47.7 kHz d)
[   600.737] (II) modeset(G0): Modeline "680x384"x119.9   36.00  680 704 720 760  384 385 390 395 doublescan +hsync -vsync (47.4 kHz d)
[   600.737] (II) modeset(G0): Modeline "576x432"x120.1   40.81  576 608 668 760  432 432 434 447 doublescan -hsync +vsync (53.7 kHz d)
[   600.737] (II) modeset(G0): Modeline "512x384"x120.0   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync (48.4 kHz d)
[   600.737] (II) modeset(G0): Modeline "400x300"x120.6   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz d)
[   600.737] (II) modeset(G0): Modeline "400x300"x112.7   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (35.2 kHz d)
[   600.737] (II) modeset(G0): Modeline "320x240"x120.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz d)
[   600.752] (II) modeset(G0): EDID for output VGA-1
[   600.880] (II) modeset(G0): EDID for output HDMI-1
[   600.880] (II) modeset(G0): EDID for output DP-1
[   601.008] (II) modeset(G0): EDID for output HDMI-2
[   601.008] (II) modeset(G0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[   601.008] (==) modeset(G0): DPI set to (96, 96)
[   601.008] (II) Loading sub module "fb"
[   601.008] (II) LoadModule: "fb"
[   601.008] (II) Loading /usr/lib/xorg/modules/libfb.so
[   601.008] (II) Module fb: vendor="X.Org Foundation"
[   601.008] 	compiled for 1.18.3, module version = 1.0.0
[   601.008] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   601.008] (II) Loading sub module "shadow"
[   601.008] (II) LoadModule: "shadow"
[   601.008] (II) Loading /usr/lib/xorg/modules/libshadow.so
[   601.008] (II) Module shadow: vendor="X.Org Foundation"
[   601.008] 	compiled for 1.18.3, module version = 1.1.0
[   601.008] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   601.008] (--) Depth 24 pixmap format is 32 bpp
[   601.008] (==) modeset(G0): Backing store enabled
[   601.008] (==) modeset(G0): Silken mouse enabled
[   601.008] (II) modeset(G0): RandR 1.2 enabled, ignore the following RandR disabled message.
[   601.008] (==) modeset(G0): DPMS enabled
[   601.008] (WW) modeset(G0): Option "AllowEmptyInitialConfiguration" is not used
[   601.008] (WW) modeset(G0): Option "IgnoreDisplayDevices" is not used
[   601.347] (II) NVIDIA: Using 3072.00 MB of virtual memory for indirect memory
[   601.348] (II) NVIDIA:     access.
[   601.382] (II) NVIDIA(0): Built-in logo is bigger than the screen.
[   601.382] (II) NVIDIA(0): Setting mode "NULL"
[   601.386] (==) NVIDIA(0): Disabling shared memory pixmaps
[   601.386] (==) NVIDIA(0): Backing store enabled
[   601.386] (==) NVIDIA(0): Silken mouse enabled
[   601.386] (==) NVIDIA(0): DPMS enabled
[   601.387] (II) Loading sub module "x11glvnd"
[   601.387] (II) LoadModule: "x11glvnd"
[   601.387] (WW) Warning, couldn't open module x11glvnd
[   601.387] (II) UnloadModule: "x11glvnd"
[   601.387] (II) Unloading x11glvnd
[   601.387] (II) x11glvnd Loading
[   601.387] (II) Loading sub module "dri2"
[   601.387] (II) LoadModule: "dri2"
[   601.387] (II) Module "dri2" already built-in
[   601.387] (II) NVIDIA(0): [DRI2] Setup complete
[   601.387] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[   601.387] (--) RandR disabled
[   601.390] (II) SELinux: Disabled on system
[   601.390] (II) Initializing extension GLX
[   601.390] (II) Indirect GLX disabled.
[   601.391] (II) modeset(G0): Damage tracking initialized
[   601.416] (II) config/udev: Adding input device Power Button (/dev/input/event4)
[   601.416] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   601.416] (II) LoadModule: "evdev"
[   601.416] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   601.417] (II) Module evdev: vendor="X.Org Foundation"
[   601.417] 	compiled for 1.18.1, module version = 2.10.1
[   601.417] 	Module class: X.Org XInput Driver
[   601.417] 	ABI class: X.Org XInput driver, version 22.1
[   601.417] (II) systemd-logind: got fd for /dev/input/event4 13:68 fd 31 paused 0
[   601.417] (II) Using input driver 'evdev' for 'Power Button'
[   601.417] (**) Power Button: always reports core events
[   601.417] (**) evdev: Power Button: Device: "/dev/input/event4"
[   601.417] (--) evdev: Power Button: Vendor 0 Product 0x1
[   601.417] (--) evdev: Power Button: Found keys
[   601.417] (II) evdev: Power Button: Configuring as keyboard
[   601.417] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input4/event4"
[   601.417] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[   601.417] (**) Option "xkb_rules" "evdev"
[   601.417] (**) Option "xkb_model" "pc105"
[   601.417] (**) Option "xkb_layout" "us"
[   601.417] (II) config/udev: Adding input device Video Bus (/dev/input/event6)
[   601.417] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[   601.418] (II) systemd-logind: got fd for /dev/input/event6 13:70 fd 32 paused 0
[   601.418] (II) Using input driver 'evdev' for 'Video Bus'
[   601.418] (**) Video Bus: always reports core events
[   601.418] (**) evdev: Video Bus: Device: "/dev/input/event6"
[   601.418] (--) evdev: Video Bus: Vendor 0 Product 0x6
[   601.418] (--) evdev: Video Bus: Found keys
[   601.418] (II) evdev: Video Bus: Configuring as keyboard
[   601.418] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input9/event6"
[   601.418] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[   601.418] (**) Option "xkb_rules" "evdev"
[   601.418] (**) Option "xkb_model" "pc105"
[   601.418] (**) Option "xkb_layout" "us"
[   601.418] (II) config/udev: Adding input device Video Bus (/dev/input/event7)
[   601.418] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[   601.419] (II) systemd-logind: got fd for /dev/input/event7 13:71 fd 33 paused 0
[   601.419] (II) Using input driver 'evdev' for 'Video Bus'
[   601.419] (**) Video Bus: always reports core events
[   601.419] (**) evdev: Video Bus: Device: "/dev/input/event7"
[   601.419] (--) evdev: Video Bus: Vendor 0 Product 0x6
[   601.419] (--) evdev: Video Bus: Found keys
[   601.419] (II) evdev: Video Bus: Configuring as keyboard
[   601.419] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:12/LNXVIDEO:01/input/input10/event7"
[   601.419] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 8)
[   601.419] (**) Option "xkb_rules" "evdev"
[   601.419] (**) Option "xkb_model" "pc105"
[   601.419] (**) Option "xkb_layout" "us"
[   601.419] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[   601.419] (II) No input driver specified, ignoring this device.
[   601.419] (II) This device may have been added with another device file.
[   601.419] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[   601.419] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[   601.420] (II) systemd-logind: got fd for /dev/input/event1 13:65 fd 34 paused 0
[   601.420] (II) Using input driver 'evdev' for 'Sleep Button'
[   601.420] (**) Sleep Button: always reports core events
[   601.420] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[   601.420] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[   601.420] (--) evdev: Sleep Button: Found keys
[   601.420] (II) evdev: Sleep Button: Configuring as keyboard
[   601.420] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:17/PNP0C09:01/PNP0C0E:00/input/input1/event1"
[   601.420] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[   601.420] (**) Option "xkb_rules" "evdev"
[   601.420] (**) Option "xkb_model" "pc105"
[   601.420] (**) Option "xkb_layout" "us"
[   601.420] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[   601.420] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   601.421] (II) systemd-logind: got fd for /dev/input/event3 13:67 fd 35 paused 0
[   601.421] (II) Using input driver 'evdev' for 'Power Button'
[   601.421] (**) Power Button: always reports core events
[   601.421] (**) evdev: Power Button: Device: "/dev/input/event3"
[   601.421] (--) evdev: Power Button: Vendor 0 Product 0x1
[   601.421] (--) evdev: Power Button: Found keys
[   601.421] (II) evdev: Power Button: Configuring as keyboard
[   601.421] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input3/event3"
[   601.421] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 10)
[   601.421] (**) Option "xkb_rules" "evdev"
[   601.421] (**) Option "xkb_model" "pc105"
[   601.421] (**) Option "xkb_layout" "us"
[   601.421] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[   601.421] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[   601.422] (II) systemd-logind: got fd for /dev/input/event2 13:66 fd 36 paused 0
[   601.422] (II) Using input driver 'evdev' for 'Sleep Button'
[   601.422] (**) Sleep Button: always reports core events
[   601.422] (**) evdev: Sleep Button: Device: "/dev/input/event2"
[   601.422] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[   601.422] (--) evdev: Sleep Button: Found keys
[   601.422] (II) evdev: Sleep Button: Configuring as keyboard
[   601.422] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:01/input/input2/event2"
[   601.422] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 11)
[   601.422] (**) Option "xkb_rules" "evdev"
[   601.422] (**) Option "xkb_model" "pc105"
[   601.422] (**) Option "xkb_layout" "us"
[   601.422] (II) config/udev: Adding drm device (/dev/dri/card1) card1 /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0/drm/card1
[   601.422] (II) xfree86: Adding drm device (/dev/dri/card1)
[   601.422] (II) systemd-logind: got fd for /dev/dri/card1 226:1 fd 37 paused 1
[   601.422] (EE) Error systemd-logind returned paused fd for drm node
[   601.422] (II) systemd-logind: releasing fd for 226:1
[   601.423] (II) config/udev: Ignoring already known drm device (/dev/dri/card1)
[   601.423] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=3 (/dev/input/event12)
[   601.423] (II) No input driver specified, ignoring this device.
[   601.423] (II) This device may have been added with another device file.
[   601.423] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=7 (/dev/input/event13)
[   601.423] (II) No input driver specified, ignoring this device.
[   601.423] (II) This device may have been added with another device file.
[   601.423] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=8 (/dev/input/event14)
[   601.423] (II) No input driver specified, ignoring this device.
[   601.423] (II) This device may have been added with another device file.
[   601.423] (II) config/udev: Adding input device HD WebCam (/dev/input/event11)
[   601.424] (**) HD WebCam: Applying InputClass "evdev keyboard catchall"
[   601.424] (II) systemd-logind: got fd for /dev/input/event11 13:75 fd 38 paused 0
[   601.424] (II) Using input driver 'evdev' for 'HD WebCam'
[   601.424] (**) HD WebCam: always reports core events
[   601.424] (**) evdev: HD WebCam: Device: "/dev/input/event11"
[   601.424] (--) evdev: HD WebCam: Vendor 0x1bcf Product 0x2c6b
[   601.424] (--) evdev: HD WebCam: Found keys
[   601.424] (II) evdev: HD WebCam: Configuring as keyboard
[   601.424] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-4/3-4:1.0/input/input13/event11"
[   601.424] (II) XINPUT: Adding extended input device "HD WebCam" (type: KEYBOARD, id 12)
[   601.424] (**) Option "xkb_rules" "evdev"
[   601.424] (**) Option "xkb_model" "pc105"
[   601.424] (**) Option "xkb_layout" "us"
[   601.424] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event9)
[   601.424] (II) No input driver specified, ignoring this device.
[   601.424] (II) This device may have been added with another device file.
[   601.424] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event10)
[   601.424] (II) No input driver specified, ignoring this device.
[   601.424] (II) This device may have been added with another device file.
[   601.425] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event5)
[   601.425] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[   601.425] (II) systemd-logind: got fd for /dev/input/event5 13:69 fd 39 paused 0
[   601.425] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[   601.425] (**) AT Translated Set 2 keyboard: always reports core events
[   601.425] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event5"
[   601.425] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[   601.425] (--) evdev: AT Translated Set 2 keyboard: Found keys
[   601.425] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[   601.425] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input7/event5"
[   601.425] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 13)
[   601.425] (**) Option "xkb_rules" "evdev"
[   601.425] (**) Option "xkb_model" "pc105"
[   601.425] (**) Option "xkb_layout" "us"
[   601.425] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/event8)
[   601.425] (**) ETPS/2 Elantech Touchpad: Applying InputClass "evdev touchpad catchall"
[   601.425] (**) ETPS/2 Elantech Touchpad: Applying InputClass "evdev touchscreen catchall"
[   601.425] (**) ETPS/2 Elantech Touchpad: Applying InputClass "touchpad catchall"
[   601.425] (**) ETPS/2 Elantech Touchpad: Applying InputClass "Default clickpad buttons"
[   601.425] (II) LoadModule: "synaptics"
[   601.426] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[   601.426] (II) Module synaptics: vendor="X.Org Foundation"
[   601.426] 	compiled for 1.18.1, module version = 1.8.2
[   601.426] 	Module class: X.Org XInput Driver
[   601.426] 	ABI class: X.Org XInput driver, version 22.1
[   601.426] (II) systemd-logind: got fd for /dev/input/event8 13:72 fd 40 paused 0
[   601.426] (II) Using input driver 'synaptics' for 'ETPS/2 Elantech Touchpad'
[   601.426] (**) ETPS/2 Elantech Touchpad: always reports core events
[   601.426] (**) Option "Device" "/dev/input/event8"
[   601.452] (II) synaptics: ETPS/2 Elantech Touchpad: ignoring touch events for semi-multitouch device
[   601.452] (--) synaptics: ETPS/2 Elantech Touchpad: x-axis range 0 - 2772 (res 31)
[   601.452] (--) synaptics: ETPS/2 Elantech Touchpad: y-axis range 0 - 1320 (res 31)
[   601.452] (--) synaptics: ETPS/2 Elantech Touchpad: pressure range 0 - 255
[   601.452] (--) synaptics: ETPS/2 Elantech Touchpad: finger width range 0 - 15
[   601.452] (--) synaptics: ETPS/2 Elantech Touchpad: buttons: left right double triple
[   601.452] (--) synaptics: ETPS/2 Elantech Touchpad: Vendor 0x2 Product 0xe
[   601.452] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[   601.452] (**) ETPS/2 Elantech Touchpad: always reports core events
[   601.452] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input8/event8"
[   601.452] (II) XINPUT: Adding extended input device "ETPS/2 Elantech Touchpad" (type: TOUCHPAD, id 14)
[   601.452] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MinSpeed is now constant deceleration 2.5
[   601.452] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MaxSpeed is now 1.75
[   601.452] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) AccelFactor is now 0.065
[   601.452] (**) ETPS/2 Elantech Touchpad: (accel) keeping acceleration scheme 1
[   601.452] (**) ETPS/2 Elantech Touchpad: (accel) acceleration profile 1
[   601.452] (**) ETPS/2 Elantech Touchpad: (accel) acceleration factor: 2.000
[   601.452] (**) ETPS/2 Elantech Touchpad: (accel) acceleration threshold: 4
[   601.452] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[   601.452] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/mouse0)
[   601.452] (**) ETPS/2 Elantech Touchpad: Ignoring device from InputClass "touchpad ignore duplicates"
[   612.115] (II) systemd-logind: got pause for 13:75
[   612.115] (II) systemd-logind: got pause for 13:65
[   612.115] (II) systemd-logind: got pause for 13:67
[   612.115] (II) systemd-logind: got pause for 13:69
[   612.115] (II) systemd-logind: got pause for 13:72
[   612.115] (II) systemd-logind: got pause for 226:0
[   612.115] (II) systemd-logind: got pause for 13:68
[   612.115] (II) systemd-logind: got pause for 13:70
[   612.115] (II) systemd-logind: got pause for 13:66
[   612.115] (II) systemd-logind: got pause for 13:71
[  1363.597] (II) UnloadModule: "synaptics"
[  1363.597] (II) systemd-logind: releasing fd for 13:72
[  1363.776] (II) evdev: AT Translated Set 2 keyboard: Close
[  1363.776] (II) UnloadModule: "evdev"
[  1363.776] (II) systemd-logind: releasing fd for 13:69
[  1363.840] (II) evdev: HD WebCam: Close
[  1363.840] (II) UnloadModule: "evdev"
[  1363.840] (II) systemd-logind: releasing fd for 13:75
[  1363.892] (II) evdev: Sleep Button: Close
[  1363.892] (II) UnloadModule: "evdev"
[  1363.892] (II) systemd-logind: releasing fd for 13:66
[  1363.924] (II) evdev: Power Button: Close
[  1363.924] (II) UnloadModule: "evdev"
[  1363.924] (II) systemd-logind: releasing fd for 13:67
[  1363.960] (II) evdev: Sleep Button: Close
[  1363.960] (II) UnloadModule: "evdev"
[  1363.960] (II) systemd-logind: releasing fd for 13:65
[  1363.992] (II) evdev: Video Bus: Close
[  1363.992] (II) UnloadModule: "evdev"
[  1363.992] (II) systemd-logind: releasing fd for 13:71
[  1364.024] (II) evdev: Video Bus: Close
[  1364.024] (II) UnloadModule: "evdev"
[  1364.024] (II) systemd-logind: releasing fd for 13:70
[  1364.064] (II) evdev: Power Button: Close
[  1364.064] (II) UnloadModule: "evdev"
[  1364.064] (II) systemd-logind: releasing fd for 13:68
[  1364.112] (II) NVIDIA(GPU-0): Deleting GPU-0
[  1364.112] (WW) xf86CloseConsole: KDSETMODE failed: Input/output error
[  1364.112] (WW) xf86CloseConsole: VT_GETMODE failed: Input/output error
[  1364.112] (WW) xf86CloseConsole: VT_ACTIVATE failed: Input/output error
[  1364.112] (II) Server terminated successfully (0). Closing log file.

```

sudo lshw -C display
```
  *-display
       description: 3D controller
       product: GM204M [GeForce GTX 970M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:a2000000-a2ffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:5000(size=128) memory:a3000000-a307ffff
  *-display
       description: VGA compatible controller
       product: Broadwell-U Integrated Graphics
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 0a
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:34 memory:a1000000-a1ffffff memory:b0000000-bfffffff ioport:6000(size=64)

```

and the sources list, not too much here!
```
==> /etc/apt/sources.list.d/google-chrome.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main

==> /etc/apt/sources.list.d/steam.list <==
deb [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam
deb-src [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam

```

---

### Post by Bashing-om on 2016-05-17
Toast2120; Yuk ...

Above my skill set to know, but:
> 
1364.112] (II) NVIDIA(GPU-0): Deleting GPU-0
[  1364.112] (WW) xf86CloseConsole: KDSETMODE failed: Input/output error
[  1364.112] (WW) xf86CloseConsole: VT_GETMODE failed: Input/output error
[  1364.112] (WW) xf86CloseConsole: VT_ACTIVATE failed: Input/output error
[  1364.112] (II) Server terminated successfully (0). Closing log file.

in the 2nd log file .. does not look promising to me.

[INDENT][INDENT]if I knew better
[INDENT][INDENT][INDENT]I would say more
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Toast2120 on 2016-05-17
Wow I didn't see that, it doesn't look good at all! Appreciate your doing what you could.

---

### Post by Bashing-om on 2016-05-17
Toast2120; Yeah ...

I will hang in here with you , let's see what the big boys (girls) come up with .
While I continue to cogitate on the error advisory .

[INDENT]inquiring minds want to know
[/INDENT]

---

### Post by mastablasta on 2016-05-18
it's loading intel drivers. does the computer have intel GPU? is this an optimus combo (nVidia+intel)? if so, you need to install bumblebee. : [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

```
[    14.398] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[    14.398] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[    14.398] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[    14.398] (II) NOUVEAU driver Date:   Tue Dec 8 15:52:25 2015 +1000
[    14.398] (II) NOUVEAU driver for NVIDIA chipset families :
```

```
 *-display
       description: VGA compatible controller
       product: Broadwell-U Integrated Graphics
       vendor: Intel Corporation

```

---

### Post by mc4man on 2016-05-18
On a failed boot with nvidia-prime what you want to look at is /var/log/gpu-manager.log. You can do so from a tty (if you can open one.
The log can also be saved from the tty if you wish. (once you reboot without nvidia the log will be useless..

The current state of nvidia optimus in 16.04 is a bit of a joke, some hardware is ok, some there is no way to use nvidia thru nvidia-prime.
Here my Intel 4xxx (Haswell) is fine, a Intel 6xxx (Skylake) no way to use. The odds of getting a currently non working to work are slim.

If you fall into the later & need nvidia for some reason then maybe try bumblebee. Otherwise you could try 14.04.1 & if Broadwell benefits from later kernel install the lts kernel for 14.04.x but do not install mesa lts that's the 11 version (14.04.4 lts mesa

2 open bugs on my skylake machine - 
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-drivers-common/+bug/1565516](https://bugs.launchpad.net/ubuntu/+source/ubuntu-drivers-common/+bug/1565516)
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-drivers-common/+bug/1583148](https://bugs.launchpad.net/ubuntu/+source/ubuntu-drivers-common/+bug/1583148)

---

### Post by Toast2120 on 2016-05-18
> **mastablasta said:**
> it's loading intel drivers. does the computer have intel GPU? is this an optimus combo (nVidia+intel)? if so, you need to install bumblebee. : [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

```
[    14.398] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[    14.398] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[    14.398] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[    14.398] (II) NOUVEAU driver Date:   Tue Dec 8 15:52:25 2015 +1000
[    14.398] (II) NOUVEAU driver for NVIDIA chipset families :
```

```
 *-display
       description: VGA compatible controller
       product: Broadwell-U Integrated Graphics
       vendor: Intel Corporation

```

For the optimus combos you have two options, either bumblebee or prime. Prime it seems is a glorious bust, thanks a lot nvidia. So I can try bumblebee and hope for the best.



> **mc4man said:**
> On a failed boot with nvidia-prime what you want to look at is /var/log/gpu-manager.log. You can do so from a tty (if you can open one.
The log can also be saved from the tty if you wish. (once you reboot without nvidia the log will be useless..

The current state of nvidia optimus in 16.04 is a bit of a joke, some hardware is ok, some there is no way to use nvidia thru nvidia-prime.
Here my Intel 4xxx (Haswell) is fine, a Intel 6xxx (Skylake) no way to use. The odds of getting a currently non working to work are slim.

If you fall into the later & need nvidia for some reason then maybe try bumblebee. Otherwise you could try 14.04.1 & if Broadwell benefits from later kernel install the lts kernel for 14.04.x but do not install mesa lts that's the 11 version (14.04.4 lts mesa

2 open bugs on my skylake machine - 
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-drivers-common/+bug/1565516](https://bugs.launchpad.net/ubuntu/+source/ubuntu-drivers-common/+bug/1565516)
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-drivers-common/+bug/1583148](https://bugs.launchpad.net/ubuntu/+source/ubuntu-drivers-common/+bug/1583148)

Joke indeed! Maybe bumblebee will perform what I need, hopefully nvidia puts more work into this at some point. 

Also it seems we are bugbrothers for here is mine.
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-304/+bug/1582895](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-304/+bug/1582895)

---

