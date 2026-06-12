---
title: "Ubuntu 15.10 hang on mounting root partition"
date: 2015-10-31
forum: General Help
---

### Post by sean-fedex on 2015-10-31
Decided to venture back into the Linux world after being away from it since version 12.04 hehe been a while. Having issues with 15.10 and 15.04 where there is a hang on boot for me. It seems to be a big gap in my dmesg were it goes from USB to mounting the ext4 root partition. I have searched but have not found anything online on how to fix this or speed it up. What is weird is on the LTS 14.04 it works perfectly fine, stupid fast bootup but there is a good hang on 15.XX distro's. Was wondering if y'all had any ideas on how to fix this. Below is my dmesg and /etc/fstab. Jumps from 2 seconds to 91 seconds. Thanks! Edit: Also this is booting of a Samsung 830 SSD, so shouldn't be this slow. Thanks!

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 4.2.0-16-generic (buildd@lcy01-07) (gcc version 5.2.1 20151003 (Ubuntu 5.2.1-21ubuntu2) ) #19-Ubuntu SMP Thu Oct 8 15:35:06 UTC 2015 (Ubuntu 4.2.0-16.19-generic 4.2.3)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.2.0-16-generic.efi.signed root=UUID=354d4818-8aee-400e-989e-1aaed09ff5a6 ro recovery nomodeset
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] x86/fpu: xstate_offset[2]: 0240, xstate_sizes[2]: 0100
[    0.000000] x86/fpu: Supporting XSAVE feature 0x01: 'x87 floating point registers'
[    0.000000] x86/fpu: Supporting XSAVE feature 0x02: 'SSE registers'
[    0.000000] x86/fpu: Supporting XSAVE feature 0x04: 'AVX registers'
[    0.000000] x86/fpu: Enabled xstate features 0x7, context size is 0x340 bytes, using 'standard' format.
[    0.000000] x86/fpu: Using 'eager' FPU context switches.
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009dfff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009e000-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000de5f9fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000de5fa000-0x00000000dea78fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000dea79000-0x00000000dea88fff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000dea89000-0x00000000deb9bfff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000deb9c000-0x00000000dee05fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000dee06000-0x00000000dee89fff] type 20
[    0.000000] BIOS-e820: [mem 0x00000000dee8a000-0x00000000dee8afff] usable
[    0.000000] BIOS-e820: [mem 0x00000000dee8b000-0x00000000deecdfff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000deece000-0x00000000df7fffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000f0000000-0x00000000f7ffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed03fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000041effffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] efi: EFI v2.31 by American Megatrends
[    0.000000] efi:  ACPI=0xdea7c000  ACPI 2.0=0xdea7c000  SMBIOS=0xdee04498 
[    0.000000] SMBIOS 2.7 present.
[    0.000000] DMI:                  /DZ77GA-70K, BIOS GAZ7711H.86A.0066.2013.0521.1509 05/21/2013
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0x41f000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask C00000000 write-back
[    0.000000]   1 base 400000000 mask FF0000000 write-back
[    0.000000]   2 base 410000000 mask FF8000000 write-back
[    0.000000]   3 base 418000000 mask FFC000000 write-back
[    0.000000]   4 base 41C000000 mask FFE000000 write-back
[    0.000000]   5 base 41E000000 mask FFF000000 write-back
[    0.000000]   6 base 0E0000000 mask FE0000000 uncachable
[    0.000000]   7 disabled
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- WT  
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 16GB, type WB
[    0.000000] reg 1, base: 16GB, range: 256MB, type WB
[    0.000000] reg 2, base: 16640MB, range: 128MB, type WB
[    0.000000] reg 3, base: 16768MB, range: 64MB, type WB
[    0.000000] reg 4, base: 16832MB, range: 32MB, type WB
[    0.000000] reg 5, base: 16864MB, range: 16MB, type WB
[    0.000000] reg 6, base: 3584MB, range: 512MB, type UC
[    0.000000] total RAM covered: 16368M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 32M     num_reg: 7      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 512MB, type WB
[    0.000000] reg 3, base: 4GB, range: 4GB, type WB
[    0.000000] reg 4, base: 8GB, range: 8GB, type WB
[    0.000000] reg 5, base: 16GB, range: 512MB, type WB
[    0.000000] reg 6, base: 16880MB, range: 16MB, type UC
[    0.000000] e820: update [mem 0xe0000000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xdf800 max_arch_pfn = 0x400000000
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000098000] 98000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x03ff0000, 0x03ff0fff] PGTABLE
[    0.000000] BRK [0x03ff1000, 0x03ff1fff] PGTABLE
[    0.000000] BRK [0x03ff2000, 0x03ff2fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x41ee00000-0x41effffff]
[    0.000000]  [mem 0x41ee00000-0x41effffff] page 2M
[    0.000000] BRK [0x03ff3000, 0x03ff3fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x400000000-0x41edfffff]
[    0.000000]  [mem 0x400000000-0x41edfffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x3e0000000-0x3ffffffff]
[    0.000000]  [mem 0x3e0000000-0x3ffffffff] page 2M
[    0.000000] BRK [0x03ff4000, 0x03ff4fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x00100000-0xde5f9fff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0xde3fffff] page 2M
[    0.000000]  [mem 0xde400000-0xde5f9fff] page 4k
[    0.000000] init_memory_mapping: [mem 0xdee8a000-0xdee8afff]
[    0.000000]  [mem 0xdee8a000-0xdee8afff] page 4k
[    0.000000] BRK [0x03ff5000, 0x03ff5fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0xdeece000-0xdf7fffff]
[    0.000000]  [mem 0xdeece000-0xdeffffff] page 4k
[    0.000000]  [mem 0xdf000000-0xdf7fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x100000000-0x3dfffffff]
[    0.000000]  [mem 0x100000000-0x3dfffffff] page 2M
[    0.000000] RAMDISK: [mem 0x33f98000-0x35fc3fff]
[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x00000000DEA7C000 000024 (v02 INTEL )
[    0.000000] ACPI: XSDT 0x00000000DEA7C078 00006C (v01 INTEL  DZ77GA   00000042 AMI  00010013)
[    0.000000] ACPI: FACP 0x00000000DEA867A8 00010C (v05 INTEL  DZ77GA   00000042 AMI  00010013)
[    0.000000] ACPI: DSDT 0x00000000DEA7C170 00A636 (v02 INTEL  DZ77GA   00000022 INTL 20051117)
[    0.000000] ACPI: FACS 0x00000000DEB9A080 000040
[    0.000000] ACPI: APIC 0x00000000DEA868B8 000092 (v03 INTEL  DZ77GA   00000042 AMI  00010013)
[    0.000000] ACPI: FPDT 0x00000000DEA86950 000044 (v01 INTEL  DZ77GA   00000042 AMI  00010013)
[    0.000000] ACPI: MCFG 0x00000000DEA86998 00003C (v01 INTEL  DZ77GA   00000042 MSFT 00000097)
[    0.000000] ACPI: HPET 0x00000000DEA869D8 000038 (v01 INTEL  DZ77GA   00000042 ^.^  00000005)
[    0.000000] ACPI: SSDT 0x00000000DEA86A10 00036D (v01 SataRe SataTabl 00001000 INTL 20091112)
[    0.000000] ACPI: SSDT 0x00000000DEA86D80 0009AA (v01 PmRef  Cpu0Ist  00003000 INTL 20051117)
[    0.000000] ACPI: SSDT 0x00000000DEA87730 000A92 (v01 PmRef  CpuPm    00003000 INTL 20051117)
[    0.000000] ACPI: BGRT 0x00000000DEA881C8 000038 (v00 INTEL  DZ77GA   00000042 AMI  00010013)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000041effffff]
[    0.000000] NODE_DATA(0) allocated [mem 0x41efec000-0x41eff0fff]
[    0.000000]  [ffffea0000000000-ffffea00107fffff] PMD -> [ffff88040e600000-ffff88041e5fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x0000000000001000-0x0000000000ffffff]
[    0.000000]   DMA32    [mem 0x0000000001000000-0x00000000ffffffff]
[    0.000000]   Normal   [mem 0x0000000100000000-0x000000041effffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x0000000000001000-0x000000000009dfff]
[    0.000000]   node   0: [mem 0x0000000000100000-0x00000000de5f9fff]
[    0.000000]   node   0: [mem 0x00000000dee8a000-0x00000000dee8afff]
[    0.000000]   node   0: [mem 0x00000000deece000-0x00000000df7fffff]
[    0.000000]   node   0: [mem 0x0000000100000000-0x000000041effffff]
[    0.000000] Initmem setup node 0 [mem 0x0000000000001000-0x000000041effffff]
[    0.000000] On node 0 totalpages: 4185802
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 24 pages reserved
[    0.000000]   DMA zone: 3997 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14205 pages used for memmap
[    0.000000]   DMA32 zone: 909101 pages, LIFO batch:31
[    0.000000]   Normal zone: 51136 pages used for memmap
[    0.000000]   Normal zone: 3272704 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] smpboot: Allowing 8 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xde5fa000-0xdea78fff]
[    0.000000] PM: Registered nosave memory: [mem 0xdea79000-0xdea88fff]
[    0.000000] PM: Registered nosave memory: [mem 0xdea89000-0xdeb9bfff]
[    0.000000] PM: Registered nosave memory: [mem 0xdeb9c000-0xdee05fff]
[    0.000000] PM: Registered nosave memory: [mem 0xdee06000-0xdee89fff]
[    0.000000] PM: Registered nosave memory: [mem 0xdee8b000-0xdeecdfff]
[    0.000000] PM: Registered nosave memory: [mem 0xdf800000-0xefffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xf7ffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf8000000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfecfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed00000-0xfed03fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed04000-0xfed1bfff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xfeffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xff000000-0xffffffff]
[    0.000000] e820: [mem 0xdf800000-0xefffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] clocksource: refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645519600211568 ns
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 33 pages/cpu @ffff88041ec00000 s96728 r8192 d30248 u262144
[    0.000000] pcpu-alloc: s96728 r8192 d30248 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 4120373
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.2.0-16-generic.efi.signed root=UUID=354d4818-8aee-400e-989e-1aaed09ff5a6 ro recovery nomodeset
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 16316640K/16743208K available (8146K kernel code, 1237K rwdata, 3800K rodata, 1460K init, 1292K bss, 426568K reserved, 0K cma-reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     Build-time adjustment of leaf fanout to 64.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=64, nr_cpu_ids=8
[    0.000000] NR_IRQS:16640 nr_irqs:488 16
[    0.000000]     Offload RCU callbacks from all CPUs
[    0.000000]     Offload RCU callbacks from CPUs: 0-7.
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] clocksource: hpet: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 133484882848 ns
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 3491.869 MHz processor
[    0.000025] Calibrating delay loop (skipped), value calculated using timer frequency.. 6983.73 BogoMIPS (lpj=13967476)
[    0.000031] pid_max: default: 32768 minimum: 301
[    0.000036] ACPI: Core revision 20150619
[    0.004803] ACPI: All ACPI Tables successfully acquired
[    0.005696] Security Framework initialized
[    0.005707] AppArmor: AppArmor initialized
[    0.005709] Yama: becoming mindful.
[    0.006379] Dentry cache hash table entries: 2097152 (order: 12, 16777216 bytes)
[    0.009146] Inode-cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.010372] Mount-cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.010386] Mountpoint-cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.010569] Initializing cgroup subsys blkio
[    0.010574] Initializing cgroup subsys memory
[    0.010581] Initializing cgroup subsys devices
[    0.010585] Initializing cgroup subsys freezer
[    0.010588] Initializing cgroup subsys net_cls
[    0.010591] Initializing cgroup subsys perf_event
[    0.010594] Initializing cgroup subsys net_prio
[    0.010598] Initializing cgroup subsys hugetlb
[    0.010616] CPU: Physical Processor ID: 0
[    0.010619] CPU: Processor Core ID: 0
[    0.010624] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.010627] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.010882] mce: CPU supports 9 MCE banks
[    0.010893] CPU0: Thermal monitoring enabled (TM1)
[    0.010900] process: using mwait in idle threads
[    0.010903] Last level iTLB entries: 4KB 512, 2MB 8, 4MB 8
[    0.010906] Last level dTLB entries: 4KB 512, 2MB 32, 4MB 32, 1GB 0
[    0.011003] Freeing SMP alternatives memory: 28K (ffffffff81ea4000 - ffffffff81eab000)
[    0.016798] ftrace: allocating 30905 entries in 121 pages
[    0.027790] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.067444] TSC deadline timer enabled
[    0.067448] smpboot: CPU0: Intel(R) Core(TM) i7-3770K CPU @ 3.50GHz (fam: 06, model: 3a, stepping: 09)
[    0.067469] Performance Events: PEBS fmt1+, 16-deep LBR, IvyBridge events, full-width counters, Intel PMU driver.
[    0.067487] ... version:                3
[    0.067490] ... bit width:              48
[    0.067492] ... generic registers:      4
[    0.067495] ... value mask:             0000ffffffffffff
[    0.067497] ... max period:             0000ffffffffffff
[    0.067499] ... fixed-purpose events:   3
[    0.067502] ... event mask:             000000070000000f
[    0.068073] x86: Booting SMP configuration:
[    0.068076] .... node  #0, CPUs:      #1
[    0.071472] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.071552]  #2 #3 #4 #5 #6 #7
[    0.092323] x86: Booted up 1 node, 8 CPUs
[    0.092330] smpboot: Total of 8 processors activated (55869.90 BogoMIPS)
[    0.098863] devtmpfs: initialized
[    0.101149] evm: security.selinux
[    0.101152] evm: security.SMACK64
[    0.101154] evm: security.SMACK64EXEC
[    0.101157] evm: security.SMACK64TRANSMUTE
[    0.101159] evm: security.SMACK64MMAP
[    0.101161] evm: security.ima
[    0.101164] evm: security.capability
[    0.101204] PM: Registering ACPI NVS region [mem 0xdea89000-0xdeb9bfff] (1126400 bytes)
[    0.101217] PM: Registering ACPI NVS region [mem 0xdee8b000-0xdeecdfff] (274432 bytes)
[    0.101277] clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
[    0.101341] pinctrl core: initialized pinctrl subsystem
[    0.101429] RTC time: 12:44:40, date: 10/31/15
[    0.101509] NET: Registered protocol family 16
[    0.106706] cpuidle: using governor ladder
[    0.110702] cpuidle: using governor menu
[    0.110798] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.110802] ACPI: bus type PCI registered
[    0.110805] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.110853] PCI: MMCONFIG for domain 0000 [bus 00-7f] at [mem 0xf0000000-0xf7ffffff] (base 0xf0000000)
[    0.110858] PCI: MMCONFIG at [mem 0xf0000000-0xf7ffffff] reserved in E820
[    0.110868] PCI: Using configuration type 1 for base access
[    0.111141] perf_event_intel: PMU erratum BJ122, BV98, HSD29 worked around, HT is on
[    0.114967] ACPI: Added _OSI(Module Device)
[    0.114970] ACPI: Added _OSI(Processor Device)
[    0.114973] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.114975] ACPI: Added _OSI(Processor Aggregator Device)
[    0.116771] ACPI: Executed 1 blocks of module-level executable AML code
[    0.118589] ACPI: Dynamic OEM Table Load:
[    0.118596] ACPI: SSDT 0xFFFF88040BCF8000 00083B (v01 PmRef  Cpu0Cst  00003001 INTL 20051117)
[    0.118945] ACPI: Dynamic OEM Table Load:
[    0.118950] ACPI: SSDT 0xFFFF88040BC5D000 000303 (v01 PmRef  ApIst    00003000 INTL 20051117)
[    0.119246] ACPI: Dynamic OEM Table Load:
[    0.119250] ACPI: SSDT 0xFFFF88040BC57400 000119 (v01 PmRef  ApCst    00003000 INTL 20051117)
[    0.120170] ACPI: Interpreter enabled
[    0.120176] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20150619/hwxface-580)
[    0.120183] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20150619/hwxface-580)
[    0.120196] ACPI: (supports S0 S3 S4 S5)
[    0.120199] ACPI: Using IOAPIC for interrupt routing
[    0.120218] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.124862] ACPI: Power Resource [FN00] (off)
[    0.124917] ACPI: Power Resource [FN01] (off)
[    0.124970] ACPI: Power Resource [FN02] (off)
[    0.125022] ACPI: Power Resource [FN03] (off)
[    0.125075] ACPI: Power Resource [FN04] (off)
[    0.125384] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-7e])
[    0.125389] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.125532] acpi PNP0A08:00: _OSC: platform does not support [PCIeHotplug PME]
[    0.125615] acpi PNP0A08:00: _OSC: OS now controls [AER PCIeCapability]
[    0.125618] acpi PNP0A08:00: FADT indicates ASPM is unsupported, using BIOS configuration
[    0.125871] PCI host bridge to bus 0000:00
[    0.125875] pci_bus 0000:00: root bus resource [bus 00-7e]
[    0.125878] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7 window]
[    0.125881] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff window]
[    0.125884] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff window]
[    0.125889] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000c3fff window]
[    0.125893] pci_bus 0000:00: root bus resource [mem 0x000c4000-0x000c7fff window]
[    0.125897] pci_bus 0000:00: root bus resource [mem 0x000c8000-0x000cbfff window]
[    0.125901] pci_bus 0000:00: root bus resource [mem 0x000cc000-0x000cffff window]
[    0.125906] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff window]
[    0.125910] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff window]
[    0.125914] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff window]
[    0.125918] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff window]
[    0.125922] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000e3fff window]
[    0.125927] pci_bus 0000:00: root bus resource [mem 0x000e4000-0x000e7fff window]
[    0.125931] pci_bus 0000:00: root bus resource [mem 0x000e8000-0x000ebfff window]
[    0.125935] pci_bus 0000:00: root bus resource [mem 0x000ec000-0x000effff window]
[    0.125939] pci_bus 0000:00: root bus resource [mem 0xe0000000-0xfeafffff window]
[    0.125948] pci 0000:00:00.0: [8086:0150] type 00 class 0x060000
[    0.126010] pci 0000:00:01.0: [8086:0151] type 01 class 0x060400
[    0.126032] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.126060] pci 0000:00:01.0: System wakeup disabled by ACPI
[    0.126110] pci 0000:00:14.0: [8086:1e31] type 00 class 0x0c0330
[    0.126139] pci 0000:00:14.0: reg 0x10: [mem 0xef620000-0xef62ffff 64bit]
[    0.126190] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    0.126220] pci 0000:00:14.0: System wakeup disabled by ACPI
[    0.126250] pci 0000:00:16.0: [8086:1e3a] type 00 class 0x078000
[    0.126279] pci 0000:00:16.0: reg 0x10: [mem 0xef63b000-0xef63b00f 64bit]
[    0.126333] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.126393] pci 0000:00:19.0: [8086:1503] type 00 class 0x020000
[    0.126417] pci 0000:00:19.0: reg 0x10: [mem 0xef600000-0xef61ffff]
[    0.126425] pci 0000:00:19.0: reg 0x14: [mem 0xef639000-0xef639fff]
[    0.126433] pci 0000:00:19.0: reg 0x18: [io  0xf040-0xf05f]
[    0.126475] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.126505] pci 0000:00:19.0: System wakeup disabled by ACPI
[    0.126535] pci 0000:00:1a.0: [8086:1e2d] type 00 class 0x0c0320
[    0.126561] pci 0000:00:1a.0: reg 0x10: [mem 0xef638000-0xef6383ff]
[    0.126624] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.126664] pci 0000:00:1a.0: System wakeup disabled by ACPI
[    0.126699] pci 0000:00:1b.0: [8086:1e20] type 00 class 0x040300
[    0.126722] pci 0000:00:1b.0: reg 0x10: [mem 0xef630000-0xef633fff 64bit]
[    0.126768] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.126799] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    0.126835] pci 0000:00:1c.0: [8086:1e10] type 01 class 0x060400
[    0.126950] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.126989] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.127020] pci 0000:00:1c.4: [8086:1e18] type 01 class 0x060400
[    0.127084] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.127117] pci 0000:00:1c.4: System wakeup disabled by ACPI
[    0.127145] pci 0000:00:1c.5: [8086:1e1a] type 01 class 0x060400
[    0.127210] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.127242] pci 0000:00:1c.5: System wakeup disabled by ACPI
[    0.127274] pci 0000:00:1d.0: [8086:1e26] type 00 class 0x0c0320
[    0.127300] pci 0000:00:1d.0: reg 0x10: [mem 0xef637000-0xef6373ff]
[    0.127363] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.127402] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.127433] pci 0000:00:1f.0: [8086:1e44] type 00 class 0x060100
[    0.127575] pci 0000:00:1f.2: [8086:1e02] type 00 class 0x010601
[    0.127597] pci 0000:00:1f.2: reg 0x10: [io  0xf090-0xf097]
[    0.127604] pci 0000:00:1f.2: reg 0x14: [io  0xf080-0xf083]
[    0.127611] pci 0000:00:1f.2: reg 0x18: [io  0xf070-0xf077]
[    0.127618] pci 0000:00:1f.2: reg 0x1c: [io  0xf060-0xf063]
[    0.127626] pci 0000:00:1f.2: reg 0x20: [io  0xf020-0xf03f]
[    0.127632] pci 0000:00:1f.2: reg 0x24: [mem 0xef636000-0xef6367ff]
[    0.127657] pci 0000:00:1f.2: PME# supported from D3hot
[    0.127708] pci 0000:00:1f.3: [8086:1e22] type 00 class 0x0c0500
[    0.127723] pci 0000:00:1f.3: reg 0x10: [mem 0xef635000-0xef6350ff 64bit]
[    0.127743] pci 0000:00:1f.3: reg 0x20: [io  0xf000-0xf01f]
[    0.127834] pci 0000:01:00.0: [10de:1184] type 00 class 0x030000
[    0.127851] pci 0000:01:00.0: reg 0x10: [mem 0xee000000-0xeeffffff]
[    0.127860] pci 0000:01:00.0: reg 0x14: [mem 0xe0000000-0xe7ffffff 64bit pref]
[    0.127868] pci 0000:01:00.0: reg 0x1c: [mem 0xe8000000-0xe9ffffff 64bit pref]
[    0.127874] pci 0000:01:00.0: reg 0x24: [io  0xe000-0xe07f]
[    0.127880] pci 0000:01:00.0: reg 0x30: [mem 0xef000000-0xef07ffff pref]
[    0.127932] pci 0000:01:00.1: [10de:0e0a] type 00 class 0x040300
[    0.127947] pci 0000:01:00.1: reg 0x10: [mem 0xef080000-0xef083fff]
[    0.134710] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.134718] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.134722] pci 0000:00:01.0:   bridge window [mem 0xee000000-0xef0fffff]
[    0.134726] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xe9ffffff 64bit pref]
[    0.134804] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.134958] pci 0000:03:00.0: [8086:10d3] type 00 class 0x020000
[    0.135048] pci 0000:03:00.0: reg 0x10: [mem 0xef520000-0xef53ffff]
[    0.135073] pci 0000:03:00.0: reg 0x14: [mem 0xef500000-0xef51ffff]
[    0.135099] pci 0000:03:00.0: reg 0x18: [io  0xd000-0xd01f]
[    0.135125] pci 0000:03:00.0: reg 0x1c: [mem 0xef540000-0xef543fff]
[    0.135292] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[    0.135336] pci 0000:03:00.0: System wakeup disabled by ACPI
[    0.142780] pci 0000:00:1c.4: PCI bridge to [bus 03]
[    0.142786] pci 0000:00:1c.4:   bridge window [io  0xd000-0xdfff]
[    0.142790] pci 0000:00:1c.4:   bridge window [mem 0xef500000-0xef5fffff]
[    0.142854] pci 0000:04:00.0: [10b5:8606] type 01 class 0x060400
[    0.142892] pci 0000:04:00.0: reg 0x10: [mem 0xef300000-0xef31ffff]
[    0.142999] pci 0000:04:00.0: PME# supported from D0 D3hot D3cold
[    0.143028] pci 0000:04:00.0: System wakeup disabled by ACPI
[    0.150701] pci 0000:00:1c.5: PCI bridge to [bus 04-0b]
[    0.150711] pci 0000:00:1c.5:   bridge window [io  0xc000-0xcfff]
[    0.150716] pci 0000:00:1c.5:   bridge window [mem 0xef100000-0xef3fffff]
[    0.150804] pci 0000:05:01.0: [10b5:8606] type 01 class 0x060400
[    0.150944] pci 0000:05:01.0: PME# supported from D0 D3hot D3cold
[    0.151003] pci 0000:05:04.0: [10b5:8606] type 01 class 0x060400
[    0.151140] pci 0000:05:04.0: PME# supported from D0 D3hot D3cold
[    0.151195] pci 0000:05:05.0: [10b5:8606] type 01 class 0x060400
[    0.151334] pci 0000:05:05.0: PME# supported from D0 D3hot D3cold
[    0.151390] pci 0000:05:07.0: [10b5:8606] type 01 class 0x060400
[    0.151529] pci 0000:05:07.0: PME# supported from D0 D3hot D3cold
[    0.151584] pci 0000:05:09.0: [10b5:8606] type 01 class 0x060400
[    0.151723] pci 0000:05:09.0: PME# supported from D0 D3hot D3cold
[    0.151796] pci 0000:04:00.0: PCI bridge to [bus 05-0b]
[    0.151805] pci 0000:04:00.0:   bridge window [io  0xc000-0xcfff]
[    0.151810] pci 0000:04:00.0:   bridge window [mem 0xef100000-0xef2fffff]
[    0.151864] pci 0000:05:01.0: PCI bridge to [bus 06]
[    0.151954] pci 0000:07:00.0: [1b4b:9172] type 00 class 0x010601
[    0.152007] pci 0000:07:00.0: reg 0x10: [io  0xc040-0xc047]
[    0.152020] pci 0000:07:00.0: reg 0x14: [io  0xc030-0xc033]
[    0.152034] pci 0000:07:00.0: reg 0x18: [io  0xc020-0xc027]
[    0.152047] pci 0000:07:00.0: reg 0x1c: [io  0xc010-0xc013]
[    0.152061] pci 0000:07:00.0: reg 0x20: [io  0xc000-0xc00f]
[    0.152075] pci 0000:07:00.0: reg 0x24: [mem 0xef220000-0xef2201ff]
[    0.152089] pci 0000:07:00.0: reg 0x30: [mem 0xef200000-0xef21ffff pref]
[    0.152148] pci 0000:07:00.0: PME# supported from D3hot
[    0.152220] pci 0000:05:04.0: PCI bridge to [bus 07]
[    0.152229] pci 0000:05:04.0:   bridge window [io  0xc000-0xcfff]
[    0.152234] pci 0000:05:04.0:   bridge window [mem 0xef200000-0xef2fffff]
[    0.152290] pci 0000:05:05.0: PCI bridge to [bus 08]
[    0.152356] pci 0000:05:07.0: PCI bridge to [bus 09]
[    0.152446] pci 0000:0a:00.0: [1283:8892] type 01 class 0x060401
[    0.152655] pci 0000:0a:00.0: supports D1 D2
[    0.152656] pci 0000:0a:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.152699] pci 0000:05:09.0: PCI bridge to [bus 0a-0b]
[    0.152712] pci 0000:05:09.0:   bridge window [mem 0xef100000-0xef1fffff]
[    0.152811] pci 0000:0b:02.0: [104c:8023] type 00 class 0x0c0010
[    0.152872] pci 0000:0b:02.0: reg 0x10: [mem 0xef104000-0xef1047ff]
[    0.152890] pci 0000:0b:02.0: reg 0x14: [mem 0xef100000-0xef103fff]
[    0.153046] pci 0000:0b:02.0: supports D1 D2
[    0.153047] pci 0000:0b:02.0: PME# supported from D0 D1 D2 D3hot
[    0.153190] pci 0000:0a:00.0: PCI bridge to [bus 0b] (subtractive decode)
[    0.153213] pci 0000:0a:00.0:   bridge window [mem 0xef100000-0xef1fffff]
[    0.153229] pci 0000:0a:00.0:   bridge window [mem 0xef100000-0xef1fffff] (subtractive decode)
[    0.153812] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.153851] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.153889] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.153927] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.153965] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.154002] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.154039] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.154076] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.154233] ACPI: Enabled 4 GPEs in block 00 to 3F
[    0.154304] vgaarb: setting as boot device: PCI:0000:01:00.0
[    0.154307] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.154312] vgaarb: loaded
[    0.154315] vgaarb: bridge control possible 0000:01:00.0
[    0.154480] SCSI subsystem initialized
[    0.154506] libata version 3.00 loaded.
[    0.154521] ACPI: bus type USB registered
[    0.154535] usbcore: registered new interface driver usbfs
[    0.154543] usbcore: registered new interface driver hub
[    0.154558] usbcore: registered new device driver usb
[    0.154678] PCI: Using ACPI for IRQ routing
[    0.157444] PCI: pci_cache_line_size set to 64 bytes
[    0.157535] e820: reserve RAM buffer [mem 0x0009e000-0x0009ffff]
[    0.157536] e820: reserve RAM buffer [mem 0xde5fa000-0xdfffffff]
[    0.157537] e820: reserve RAM buffer [mem 0xdee8b000-0xdfffffff]
[    0.157538] e820: reserve RAM buffer [mem 0xdf800000-0xdfffffff]
[    0.157539] e820: reserve RAM buffer [mem 0x41f000000-0x41fffffff]
[    0.157611] NetLabel: Initializing
[    0.157614] NetLabel:  domain hash size = 128
[    0.157616] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.157626] NetLabel:  unlabeled traffic allowed by default
[    0.157675] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.157680] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.159704] clocksource: Switched to clocksource hpet
[    0.163646] AppArmor: AppArmor Filesystem Enabled
[    0.163693] pnp: PnP ACPI init
[    0.163765] system 00:00: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.163770] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.163823] system 00:01: [io  0x0680-0x069f] has been reserved
[    0.163826] system 00:01: [io  0x1000-0x100f] has been reserved
[    0.163829] system 00:01: [io  0xffff] has been reserved
[    0.163832] system 00:01: [io  0xffff] has been reserved
[    0.163835] system 00:01: [io  0x0400-0x0453] could not be reserved
[    0.163838] system 00:01: [io  0x0458-0x047f] has been reserved
[    0.163841] system 00:01: [io  0x0500-0x057f] has been reserved
[    0.163844] system 00:01: [io  0x164e-0x164f] has been reserved
[    0.163848] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.163864] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.163896] system 00:03: [io  0x0454-0x0457] has been reserved
[    0.163900] system 00:03: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.163949] system 00:04: [io  0x0a00-0x0a0f] has been reserved
[    0.163952] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.164071] system 00:05: [io  0x04d0-0x04d1] has been reserved
[    0.164075] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.164260] system 00:06: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.164263] system 00:06: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.164266] system 00:06: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.164269] system 00:06: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.164272] system 00:06: [mem 0xf0000000-0xf7ffffff] has been reserved
[    0.164276] system 00:06: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.164279] system 00:06: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.164282] system 00:06: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.164285] system 00:06: [mem 0xff000000-0xffffffff] has been reserved
[    0.164288] system 00:06: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.164291] system 00:06: [mem 0xea000000-0xea000fff] has been reserved
[    0.164295] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.164370] pnp: PnP ACPI: found 7 devices
[    0.170208] clocksource: acpi_pm: mask: 0xffffff max_cycles: 0xffffff, max_idle_ns: 2085701024 ns
[    0.170326] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.170330] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.170334] pci 0000:00:01.0:   bridge window [mem 0xee000000-0xef0fffff]
[    0.170337] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xe9ffffff 64bit pref]
[    0.170343] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.170361] pci 0000:00:1c.4: PCI bridge to [bus 03]
[    0.170365] pci 0000:00:1c.4:   bridge window [io  0xd000-0xdfff]
[    0.170372] pci 0000:00:1c.4:   bridge window [mem 0xef500000-0xef5fffff]
[    0.170381] pci 0000:05:01.0: PCI bridge to [bus 06]
[    0.170399] pci 0000:05:04.0: PCI bridge to [bus 07]
[    0.170403] pci 0000:05:04.0:   bridge window [io  0xc000-0xcfff]
[    0.170411] pci 0000:05:04.0:   bridge window [mem 0xef200000-0xef2fffff]
[    0.170424] pci 0000:05:05.0: PCI bridge to [bus 08]
[    0.170441] pci 0000:05:07.0: PCI bridge to [bus 09]
[    0.170458] pci 0000:0a:00.0: PCI bridge to [bus 0b]
[    0.170472] pci 0000:0a:00.0:   bridge window [mem 0xef100000-0xef1fffff]
[    0.170496] pci 0000:05:09.0: PCI bridge to [bus 0a-0b]
[    0.170504] pci 0000:05:09.0:   bridge window [mem 0xef100000-0xef1fffff]
[    0.170516] pci 0000:04:00.0: PCI bridge to [bus 05-0b]
[    0.170521] pci 0000:04:00.0:   bridge window [io  0xc000-0xcfff]
[    0.170529] pci 0000:04:00.0:   bridge window [mem 0xef100000-0xef2fffff]
[    0.170541] pci 0000:00:1c.5: PCI bridge to [bus 04-0b]
[    0.170545] pci 0000:00:1c.5:   bridge window [io  0xc000-0xcfff]
[    0.170552] pci 0000:00:1c.5:   bridge window [mem 0xef100000-0xef3fffff]
[    0.170562] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7 window]
[    0.170563] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff window]
[    0.170564] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff window]
[    0.170566] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff window]
[    0.170567] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff window]
[    0.170568] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff window]
[    0.170569] pci_bus 0000:00: resource 10 [mem 0x000cc000-0x000cffff window]
[    0.170570] pci_bus 0000:00: resource 11 [mem 0x000d0000-0x000d3fff window]
[    0.170571] pci_bus 0000:00: resource 12 [mem 0x000d4000-0x000d7fff window]
[    0.170572] pci_bus 0000:00: resource 13 [mem 0x000d8000-0x000dbfff window]
[    0.170573] pci_bus 0000:00: resource 14 [mem 0x000dc000-0x000dffff window]
[    0.170574] pci_bus 0000:00: resource 15 [mem 0x000e0000-0x000e3fff window]
[    0.170575] pci_bus 0000:00: resource 16 [mem 0x000e4000-0x000e7fff window]
[    0.170576] pci_bus 0000:00: resource 17 [mem 0x000e8000-0x000ebfff window]
[    0.170578] pci_bus 0000:00: resource 18 [mem 0x000ec000-0x000effff window]
[    0.170579] pci_bus 0000:00: resource 19 [mem 0xe0000000-0xfeafffff window]
[    0.170580] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.170581] pci_bus 0000:01: resource 1 [mem 0xee000000-0xef0fffff]
[    0.170582] pci_bus 0000:01: resource 2 [mem 0xe0000000-0xe9ffffff 64bit pref]
[    0.170583] pci_bus 0000:03: resource 0 [io  0xd000-0xdfff]
[    0.170584] pci_bus 0000:03: resource 1 [mem 0xef500000-0xef5fffff]
[    0.170585] pci_bus 0000:04: resource 0 [io  0xc000-0xcfff]
[    0.170586] pci_bus 0000:04: resource 1 [mem 0xef100000-0xef3fffff]
[    0.170588] pci_bus 0000:05: resource 0 [io  0xc000-0xcfff]
[    0.170589] pci_bus 0000:05: resource 1 [mem 0xef100000-0xef2fffff]
[    0.170590] pci_bus 0000:07: resource 0 [io  0xc000-0xcfff]
[    0.170591] pci_bus 0000:07: resource 1 [mem 0xef200000-0xef2fffff]
[    0.170592] pci_bus 0000:0a: resource 1 [mem 0xef100000-0xef1fffff]
[    0.170593] pci_bus 0000:0b: resource 1 [mem 0xef100000-0xef1fffff]
[    0.170594] pci_bus 0000:0b: resource 4 [mem 0xef100000-0xef1fffff]
[    0.170616] NET: Registered protocol family 2
[    0.170748] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.170906] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.171012] TCP: Hash tables configured (established 131072 bind 65536)
[    0.171035] UDP hash table entries: 8192 (order: 6, 262144 bytes)
[    0.171076] UDP-Lite hash table entries: 8192 (order: 6, 262144 bytes)
[    0.171132] NET: Registered protocol family 1
[    0.211770] pci 0000:01:00.0: Video device with shadowed ROM
[    0.211842] PCI: CLS mismatch (64 != 32), using 64 bytes
[    0.211884] Trying to unpack rootfs image as initramfs...
[    0.558409] Freeing initrd memory: 32944K (ffff880033f98000 - ffff880035fc4000)
[    0.558422] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.558426] software IO TLB [mem 0xd76bc000-0xdb6bc000] (64MB) mapped at [ffff8800d76bc000-ffff8800db6bbfff]
[    0.558494] RAPL PMU detected, API unit is 2^-32 Joules, 3 fixed counters 163840 ms ovfl timer
[    0.558499] hw unit of domain pp0-core 2^-16 Joules
[    0.558501] hw unit of domain package 2^-16 Joules
[    0.558503] hw unit of domain pp1-gpu 2^-16 Joules
[    0.558621] microcode: CPU0 sig=0x306a9, pf=0x2, revision=0x17
[    0.558629] microcode: CPU1 sig=0x306a9, pf=0x2, revision=0x17
[    0.558637] microcode: CPU2 sig=0x306a9, pf=0x2, revision=0x17
[    0.558645] microcode: CPU3 sig=0x306a9, pf=0x2, revision=0x17
[    0.558653] microcode: CPU4 sig=0x306a9, pf=0x2, revision=0x17
[    0.558663] microcode: CPU5 sig=0x306a9, pf=0x2, revision=0x17
[    0.558669] microcode: CPU6 sig=0x306a9, pf=0x2, revision=0x17
[    0.558676] microcode: CPU7 sig=0x306a9, pf=0x2, revision=0x17
[    0.558725] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.558789] Scanning for low memory corruption every 60 seconds
[    0.559039] futex hash table entries: 2048 (order: 5, 131072 bytes)
[    0.559060] Initialise system trusted keyring
[    0.559081] audit: initializing netlink subsys (disabled)
[    0.559095] audit: type=2000 audit(1446295480.552:1): initialized
[    0.559375] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.560306] zpool: loaded
[    0.560310] zbud: loaded
[    0.560441] VFS: Disk quotas dquot_6.6.0
[    0.560466] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.560781] fuse init (API version 7.23)
[    0.560876] Key type big_key registered
[    0.561178] Key type asymmetric registered
[    0.561183] Asymmetric key parser 'x509' registered
[    0.561193] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 249)
[    0.561240] io scheduler noop registered
[    0.561244] io scheduler deadline registered (default)
[    0.561265] io scheduler cfq registered
[    0.562592] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.562599] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.562627] efifb: probing for efifb
[    0.562639] efifb: framebuffer at 0xe0000000, mapped to 0xffffc90002000000, using 8640k, total 8640k
[    0.562643] efifb: mode is 1920x1080x32, linelength=8192, pages=1
[    0.562645] efifb: scrolling: redraw
[    0.562648] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    0.566433] Console: switching to colour frame buffer device 240x67
[    0.570129] fb0: EFI VGA frame buffer device
[    0.570148] intel_idle: MWAIT substates: 0x1120
[    0.570149] intel_idle: v0.4 model 0x3A
[    0.570150] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.570380] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.570406] ACPI: Power Button [PWRB]
[    0.570441] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.570464] ACPI: Power Button [PWRF]
[    0.571055] thermal LNXTHERM:00: registered as thermal_zone0
[    0.571073] ACPI: Thermal Zone [TZ00] (28 C)
[    0.571236] thermal LNXTHERM:01: registered as thermal_zone1
[    0.571254] ACPI: Thermal Zone [TZ01] (30 C)
[    0.571296] GHES: HEST is not enabled!
[    0.571383] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.572635] Linux agpgart interface v0.103
[    0.574475] brd: module loaded
[    0.575125] loop: module loaded
[    0.575295] libphy: Fixed MDIO Bus: probed
[    0.575309] tun: Universal TUN/TAP device driver, 1.6
[    0.575325] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.575384] PPP generic driver version 2.4.2
[    0.575508] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.575528] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 1
[    0.575632] xhci_hcd 0000:00:14.0: hcc params 0x20007181 hci version 0x100 quirks 0x0000b930
[    0.575662] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    0.575730] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.575751] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.575773] usb usb1: Product: xHCI Host Controller
[    0.575788] usb usb1: Manufacturer: Linux 4.2.0-16-generic xhci-hcd
[    0.575807] usb usb1: SerialNumber: 0000:00:14.0
[    0.575899] hub 1-0:1.0: USB hub found
[    0.575919] hub 1-0:1.0: 4 ports detected
[    0.576149] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.576167] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 2
[    0.576211] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003
[    0.576232] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.576254] usb usb2: Product: xHCI Host Controller
[    0.576269] usb usb2: Manufacturer: Linux 4.2.0-16-generic xhci-hcd
[    0.576288] usb usb2: SerialNumber: 0000:00:14.0
[    0.576368] hub 2-0:1.0: USB hub found
[    0.576387] hub 2-0:1.0: 4 ports detected
[    0.576611] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.576634] ehci-pci: EHCI PCI platform driver
[    0.576712] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    0.576731] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.576762] ehci-pci 0000:00:1a.0: debug port 2
[    0.581554] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    0.581561] ehci-pci 0000:00:1a.0: irq 16, io mem 0xef638000
[    0.591369] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    0.592298] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    0.593205] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.594118] usb usb3: Product: EHCI Host Controller
[    0.595033] usb usb3: Manufacturer: Linux 4.2.0-16-generic ehci_hcd
[    0.595955] usb usb3: SerialNumber: 0000:00:1a.0
[    0.596961] hub 3-0:1.0: USB hub found
[    0.597872] hub 3-0:1.0: 2 ports detected
[    0.598912] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    0.599831] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 4
[    0.600752] ehci-pci 0000:00:1d.0: debug port 2
[    0.605550] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    0.605556] ehci-pci 0000:00:1d.0: irq 23, io mem 0xef637000
[    0.615348] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    0.616271] usb usb4: New USB device found, idVendor=1d6b, idProduct=0002
[    0.617183] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.618093] usb usb4: Product: EHCI Host Controller
[    0.618997] usb usb4: Manufacturer: Linux 4.2.0-16-generic ehci_hcd
[    0.619908] usb usb4: SerialNumber: 0000:00:1d.0
[    0.620903] hub 4-0:1.0: USB hub found
[    0.621793] hub 4-0:1.0: 2 ports detected
[    0.622747] ehci-platform: EHCI generic platform driver
[    0.623640] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.624530] ohci-pci: OHCI PCI platform driver
[    0.625419] ohci-platform: OHCI generic platform driver
[    0.626304] uhci_hcd: USB Universal Host Controller Interface driver
[    0.627211] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    0.631365] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.632237] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.633324] mousedev: PS/2 mouse device common for all mice
[    0.634553] rtc_cmos 00:02: RTC can wake from S4
[    0.635591] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.636475] rtc_cmos 00:02: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.637346] i2c /dev entries driver
[    0.638254] device-mapper: uevent: version 1.0.3
[    0.639171] device-mapper: ioctl: 4.33.0-ioctl (2015-8-18) initialised: dm-devel@redhat.com
[    0.640060] Intel P-state driver initializing.
[    0.641276] ledtrig-cpu: registered to indicate activity on CPUs
[    0.643094] EFI Variables Facility v0.08 2004-May-17
[    0.654069] PCCT header not found.
[    0.655062] NET: Registered protocol family 10
[    0.656508] NET: Registered protocol family 17
[    0.657314] Key type dns_resolver registered
[    0.658567] Loading compiled-in X.509 certificates
[    0.659937] Loaded X.509 cert 'Build time autogenerated kernel key: 6a1c9c21f04ab86fd1d7ced6ca113540fc8e35b6'
[    0.660758] registered taskstats version 1
[    0.661569] zswap: loading zswap
[    0.662366] zswap: using zbud pool
[    0.663157] zswap: using lzo compressor
[    0.666877] Key type trusted registered
[    0.674791] Key type encrypted registered
[    0.675671] AppArmor: AppArmor sha1 policy hashing enabled
[    0.676478] ima: No TPM chip found, activating TPM-bypass!
[    0.677323] evm: HMAC attrs: 0x1
[    0.678695]   Magic number: 3:312:735
[    0.679647] rtc_cmos 00:02: setting system clock to 2015-10-31 12:44:40 UTC (1446295480)
[    0.680651] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.681497] EDD information not available.
[    0.682354] PM: Hibernation image not present or could not be loaded.
[    0.682731] Freeing unused kernel memory: 1460K (ffffffff81d37000 - ffffffff81ea4000)
[    0.683570] Write protecting the kernel read-only data: 12288k
[    0.684708] Freeing unused kernel memory: 36K (ffff8800037f7000 - ffff880003800000)
[    0.685716] Freeing unused kernel memory: 296K (ffff880003bb6000 - ffff880003c00000)
[    0.695983] random: systemd-udevd urandom read with 4 bits of entropy available
[    0.718117] wmi: Mapper loaded
[    0.726764] pps_core: LinuxPPS API ver. 1 registered
[    0.727729] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
[    0.729682] [drm] Initialized drm 1.1.0 20060810
[    0.730760] PTP clock support registered
[    0.731797] ahci 0000:00:1f.2: version 3.0
[    0.733915] firewire_ohci 0000:0b:02.0: enabling device (0100 -> 0102)
[    0.735184] e1000e: Intel(R) PRO/1000 Network Driver - 3.2.5-k
[    0.736105] e1000e: Copyright(c) 1999 - 2015 Intel Corporation.
[    0.747273] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x23 impl SATA mode
[    0.748345] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part ems apst 
[    0.767687] scsi host0: ahci
[    0.768727] scsi host1: ahci
[    0.769733] scsi host2: ahci
[    0.770701] scsi host3: ahci
[    0.771698] scsi host4: ahci
[    0.772680] scsi host5: ahci
[    0.773569] ata1: SATA max UDMA/133 abar m2048@0xef636000 port 0xef636100 irq 32
[    0.774441] ata2: SATA max UDMA/133 abar m2048@0xef636000 port 0xef636180 irq 32
[    0.775325] ata3: DUMMY
[    0.776205] ata4: DUMMY
[    0.777049] ata5: DUMMY
[    0.777894] ata6: SATA max UDMA/133 abar m2048@0xef636000 port 0xef636380 irq 32
[    0.778780] ahci 0000:07:00.0: enabling device (0100 -> 0103)
[    0.778988] e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    0.780743] ahci 0000:07:00.0: AHCI 0001.0000 32 slots 2 ports 6 Gbps 0x3 impl SATA mode
[    0.781627] ahci 0000:07:00.0: flags: 64bit ncq sntf led only pmp fbs pio slum part sxs 
[    0.782746] scsi host6: ahci
[    0.783783] scsi host7: ahci
[    0.784697] ata7: SATA max UDMA/133 abar m512@0xef220000 port 0xef220100 irq 34
[    0.785579] ata8: SATA max UDMA/133 abar m512@0xef220000 port 0xef220180 irq 34
[    0.787303] firewire_ohci 0000:0b:02.0: added OHCI v1.10 device as card 0, 4 IR + 8 IT contexts, quirks 0x2
[    0.887413] usb 2-1: new SuperSpeed USB device number 2 using xhci_hcd
[    0.887552] usb 1-1: new high-speed USB device number 2 using xhci_hcd
[    0.907139] usb 3-1: new high-speed USB device number 2 using ehci-pci
[    0.908922] usb 2-1: New USB device found, idVendor=05e3, idProduct=0612
[    0.909799] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    0.910661] usb 2-1: Product: USB3.0 Hub 123
[    0.911522] usb 2-1: Manufacturer: GenesysLogic
[    0.923100] hub 2-1:1.0: USB hub found
[    0.924535] hub 2-1:1.0: 3 ports detected
[    0.926253] usb: failed to peer 2-1-port1 and usb1-port1 by location (2-1-port1:none) (usb1-port1:usb2-port1)
[    0.927138] usb 2-1-port1: failed to peer to usb1-port1 (-16)
[    0.928013] usb: port power management may be unreliable
[    0.928895] usb: failed to peer 2-1-port2 and usb1-port1 by location (2-1-port2:none) (usb1-port1:usb2-port1)
[    0.929781] usb 2-1-port2: failed to peer to usb1-port1 (-16)
[    0.930681] usb: failed to peer 2-1-port3 and usb1-port1 by location (2-1-port3:none) (usb1-port1:usb2-port1)
[    0.931097] usb 4-1: new high-speed USB device number 2 using ehci-pci
[    0.932493] usb 2-1-port3: failed to peer to usb1-port1 (-16)
[    1.037582] e1000e 0000:00:19.0 eth0: registered PHC clock
[    1.038507] e1000e 0000:00:19.0 eth0: (PCI Express:2.5GT/s:Width x1) 00:22:4d:9e:b0:7f
[    1.039418] usb 3-1: New USB device found, idVendor=8087, idProduct=0024
[    1.039418] usb 3-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.040548] hub 3-1:1.0: USB hub found
[    1.041475] hub 3-1:1.0: 6 ports detected
[    1.043388] e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
[    1.044358] e1000e 0000:00:19.0 eth0: MAC: 10, PHY: 11, PBA No: FFFFFF-0FF
[    1.045365] e1000e 0000:03:00.0: Disabling ASPM L0s L1
[    1.046313] e1000e 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[    1.047452] e1000e 0000:03:00.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    1.051419] usb 2-4: new SuperSpeed USB device number 3 using xhci_hcd
[    1.067612] usb 4-1: New USB device found, idVendor=8087, idProduct=0024
[    1.068542] usb 4-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.069690] hub 4-1:1.0: USB hub found
[    1.070772] hub 4-1:1.0: 8 ports detected
[    1.071732] usb 2-4: New USB device found, idVendor=05e3, idProduct=0612
[    1.071733] usb 2-4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.071734] usb 2-4: Product: USB3.0 Hub 123
[    1.071735] usb 2-4: Manufacturer: GenesysLogic
[    1.076687] usb 1-1: New USB device found, idVendor=05e3, idProduct=0610
[    1.077672] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.078574] usb 1-1: Product: USB2.0 Hub 456
[    1.079495] usb 1-1: Manufacturer: GenesysLogic
[    1.081468] hub 2-4:1.0: USB hub found
[    1.082023] hub 1-1:1.0: USB hub found
[    1.082837] hub 1-1:1.0: 3 ports detected
[    1.084668] hub 2-4:1.0: 3 ports detected
[    1.085067] usb: failed to peer 1-1-port1 and usb2-port1 by location (1-1-port1:none) (usb2-port1:usb1-port1)
[    1.085068] usb 1-1-port1: failed to peer to usb2-port1 (-16)
[    1.085086] usb: failed to peer 1-1-port2 and usb2-port1 by location (1-1-port2:none) (usb2-port1:usb1-port1)
[    1.085086] usb 1-1-port2: failed to peer to usb2-port1 (-16)
[    1.085102] usb: failed to peer 1-1-port3 and usb2-port1 by location (1-1-port3:none) (usb2-port1:usb1-port1)
[    1.085102] usb 1-1-port3: failed to peer to usb2-port1 (-16)
[    1.094999] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.096075] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.097803] ata1.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    1.097808] ata1.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    1.098988] ata1.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    1.100347] ata6.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    1.100349] ata6.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    1.101505] ata6.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    1.102998] ata7: SATA link down (SStatus 0 SControl 300)
[    1.103045] ata8: SATA link down (SStatus 0 SControl 300)
[    1.105426] ata1.00: supports DRM functions and may not be fully accessible
[    1.106374] ata2: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.107711] ata1.00: READ LOG DMA EXT failed, trying unqueued
[    1.108966] ata1.00: failed to get NCQ Send/Recv Log Emask 0x1
[    1.108968] ata1.00: ATA-9: Samsung SSD 850 EVO 500GB, EMT01B6Q, max UDMA/133
[    1.110121] ata1.00: 976773168 sectors, multi 1: LBA48 NCQ (depth 31/32), AA
[    1.111321] ata6.00: ATA-8: WDC WD1001FALS-00E3A0, 05.01D05, max UDMA/133
[    1.112272] ata6.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.113216] ata2.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    1.113218] ata2.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    1.114843] ata2.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    1.116389] ata1.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    1.116393] ata1.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    1.118034] ata1.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    1.119230] ata2.00: ATA-9: SAMSUNG SSD 830 Series, CXM03B1Q, max UDMA/133
[    1.120383] ata2.00: 500118192 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.121698] ata1.00: supports DRM functions and may not be fully accessible
[    1.123234] ata6.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    1.123236] ata6.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    1.124833] ata6.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    1.126600] ata1.00: failed to get NCQ Send/Recv Log Emask 0x1
[    1.126645] ata2.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    1.126648] ata2.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    1.127633] ata2.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    1.128606] ata1.00: configured for UDMA/133
[    1.129898] ata2.00: configured for UDMA/133
[    1.129930] scsi 0:0:0:0: Direct-Access     ATA      Samsung SSD 850  1B6Q PQ: 0 ANSI: 5
[    1.130222] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.130256] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.130263] sd 0:0:0:0: [sda] Write Protect is off
[    1.130264] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.130272] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.131676]  sda: sda1 sda2 sda3 sda4
[    1.132089] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.138611] ata6.00: configured for UDMA/133
[    1.138639] scsi 1:0:0:0: Direct-Access     ATA      SAMSUNG SSD 830  3B1Q PQ: 0 ANSI: 5
[    1.138872] sd 1:0:0:0: [sdb] 500118192 512-byte logical blocks: (256 GB/238 GiB)
[    1.138904] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    1.138929] sd 1:0:0:0: [sdb] Write Protect is off
[    1.138931] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.138955] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.140324]  sdb: sdb1 sdb2
[    1.140487] sd 1:0:0:0: [sdb] Attached SCSI disk
[    1.147416] scsi 5:0:0:0: Direct-Access     ATA      WDC WD1001FALS-0 1D05 PQ: 0 ANSI: 5
[    1.148575] sd 5:0:0:0: [sdc] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.148632] sd 5:0:0:0: Attached scsi generic sg2 type 0
[    1.150737] sd 5:0:0:0: [sdc] Write Protect is off
[    1.152111] sd 5:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    1.152123] sd 5:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.158344] e1000e 0000:03:00.0 eth1: registered PHC clock
[    1.159378] e1000e 0000:03:00.0 eth1: (PCI Express:2.5GT/s:Width x1) 00:22:4d:9e:b0:83
[    1.160368] e1000e 0000:03:00.0 eth1: Intel(R) PRO/1000 Network Connection
[    1.161367] e1000e 0000:03:00.0 eth1: MAC: 3, PHY: 8, PBA No: FFFFFF-0FF
[    1.163045] e1000e 0000:00:19.0 eno1: renamed from eth0
[    1.179305]  sdc: sdc1
[    1.180421] sd 5:0:0:0: [sdc] Attached SCSI disk
[    1.183105] e1000e 0000:03:00.0 rename3: renamed from eth1
[    1.198904] usb 1-4: new high-speed USB device number 3 using xhci_hcd
[    1.287008] firewire_core 0000:0b:02.0: created device fw0: GUID 00224dffffa1ce8b, S400
[    1.310813] usb 3-1.2: new full-speed USB device number 3 using ehci-pci
[    1.346799] usb 4-1.5: new full-speed USB device number 3 using ehci-pci
[    1.388677] usb 1-4: New USB device found, idVendor=05e3, idProduct=0610
[    1.389700] usb 1-4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.390683] usb 1-4: Product: USB2.0 Hub 456
[    1.391651] usb 1-4: Manufacturer: GenesysLogic
[    1.393225] hub 1-4:1.0: USB hub found
[    1.394582] hub 1-4:1.0: 3 ports detected
[    1.397606] usb: failed to peer 1-4-port1 and usb2-port1 by location (1-4-port1:none) (usb2-port1:usb1-port1)
[    1.398554] usb 1-4-port1: failed to peer to usb2-port1 (-16)
[    1.399570] usb: failed to peer 1-4-port2 and usb2-port1 by location (1-4-port2:none) (usb2-port1:usb1-port1)
[    1.400538] usb 1-4-port2: failed to peer to usb2-port1 (-16)
[    1.401519] usb: failed to peer 1-4-port3 and usb2-port1 by location (1-4-port3:none) (usb2-port1:usb1-port1)
[    1.402503] usb 1-4-port3: failed to peer to usb2-port1 (-16)
[    1.405611] usb 3-1.2: New USB device found, idVendor=1b1c, idProduct=0c04
[    1.406680] usb 3-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.407699] usb 3-1.2: Product: Integrated USB Bridge
[    1.408708] usb 3-1.2: Manufacturer: Corsair Memory, Inc.
[    1.412186] hidraw: raw HID events driver (C) Jiri Kosina
[    1.414770] usbcore: registered new interface driver usbhid
[    1.415831] usbhid: USB HID core driver
[    1.418219] hid-generic 0003:1B1C:0C04.0001: hiddev0,hidraw0: USB HID v1.11 Device [Corsair Memory, Inc. Integrated USB Bridge] on usb-0000:00:1a.0-1.2/input0
[    1.441208] usb 4-1.5: New USB device found, idVendor=0d8c, idProduct=0014
[    1.442243] usb 4-1.5: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.443265] usb 4-1.5: Product: USB Audio Device
[    1.444273] usb 4-1.5: Manufacturer: C-Media Electronics Inc.
[    1.446390] input: C-Media Electronics Inc. USB Audio Device as /devices/pci0000:00/0000:00:1d.0/usb4/4-1/4-1.5/4-1.5:1.3/0003:0D8C:0014.0002/input/input5
[    1.478675] usb 3-1.5: new full-speed USB device number 4 using ehci-pci
[    1.502854] hid-generic 0003:0D8C:0014.0002: input,hidraw1: USB HID v1.00 Device [C-Media Electronics Inc. USB Audio Device] on usb-0000:00:1d.0-1.5/input3
[    1.554618] tsc: Refined TSC clocksource calibration: 3492.066 MHz
[    1.555724] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x32560a6ac7e, max_idle_ns: 440795371154 ns
[    1.573688] usb 3-1.5: New USB device found, idVendor=046d, idProduct=c080
[    1.574582] usb 4-1.7: new high-speed USB device number 4 using ehci-pci
[    1.575878] usb 3-1.5: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.576971] usb 3-1.5: Product: Gaming Mouse G303
[    1.578054] usb 3-1.5: Manufacturer: Logitech
[    1.579145] usb 3-1.5: SerialNumber: 1071345D3031
[    1.581757] input: Logitech Gaming Mouse G303 as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.5/3-1.5:1.0/0003:046D:C080.0003/input/input6
[    1.583034] hid-generic 0003:046D:C080.0003: input,hidraw2: USB HID v1.11 Mouse [Logitech Gaming Mouse G303] on usb-0000:00:1a.0-1.5/input0
[    1.586743] input: Logitech Gaming Mouse G303 as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.5/3-1.5:1.1/0003:046D:C080.0004/input/input7
[    1.642897] hid-generic 0003:046D:C080.0004: input,hiddev0,hidraw3: USB HID v1.11 Keyboard [Logitech Gaming Mouse G303] on usb-0000:00:1a.0-1.5/input1
[    1.668639] usb 4-1.7: New USB device found, idVendor=058f, idProduct=6366
[    1.669796] usb 4-1.7: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.671014] usb 4-1.7: Product: Flash Card Reader/Writer
[    1.672191] usb 4-1.7: Manufacturer: Generic
[    1.673365] usb 4-1.7: SerialNumber: 058F63666438
[    1.676606] usb-storage 4-1.7:1.0: USB Mass Storage device detected
[    1.677946] scsi host8: usb-storage 4-1.7:1.0
[    1.679195] usbcore: registered new interface driver usb-storage
[    1.681297] usbcore: registered new interface driver uas
[    1.714467] usb 3-1.6: new full-speed USB device number 5 using ehci-pci
[    1.808028] usb 3-1.6: New USB device found, idVendor=04d9, idProduct=0183
[    1.809156] usb 3-1.6: New USB device strings: Mfr=0, Product=2, SerialNumber=0
[    1.810277] usb 3-1.6: Product: USB Keyboard
[    1.812364] input: USB Keyboard as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.6/3-1.6:1.0/0003:04D9:0183.0005/input/input8
[    1.866508] hid-generic 0003:04D9:0183.0005: input,hidraw4: USB HID v1.11 Keyboard [USB Keyboard] on usb-0000:00:1a.0-1.6/input0
[    1.868877] hid-generic 0003:04D9:0183.0006: hiddev0,hidraw5: USB HID v1.11 Device [USB Keyboard] on usb-0000:00:1a.0-1.6/input1
[    1.871297] input: USB Keyboard as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.6/3-1.6:1.2/0003:04D9:0183.0007/input/input9
[    1.926457] hid-generic 0003:04D9:0183.0007: input,hidraw6: USB HID v1.11 Keyboard [USB Keyboard] on usb-0000:00:1a.0-1.6/input2
[    2.553982] clocksource: Switched to clocksource tsc
[    2.678540] scsi 8:0:0:0: Direct-Access     Multiple Card  Reader     1.00 PQ: 0 ANSI: 0
[    2.679932] sd 8:0:0:0: Attached scsi generic sg3 type 0
[    2.681327] sd 8:0:0:0: [sdd] Attached SCSI removable disk
[   91.332599] EXT4-fs (sdb2): mounted filesystem with ordered data mode. Opts: (null)
[   91.392192] systemd[1]: RTC configured in localtime, applying delta of -300 minutes to system time.
[   91.404210] systemd[1]: Failed to insert module 'kdbus': Function not implemented
[   91.426504] systemd[1]: systemd 225 running in system mode. (+PAM +AUDIT +SELINUX +IMA +APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT +GNUTLS +ACL +XZ -LZ4 +SECCOMP +BLKID -ELFUTILS +KMOD -IDN)
[   91.427941] systemd[1]: Detected architecture x86-64.
[   91.433521] systemd[1]: Set hostname to <Beast-Ubi>.
[   91.435826] systemd[1]: Initializing machine ID from random generator.
[   91.437115] systemd[1]: Installed transient /etc/machine-id file.
[   91.439484] systemd[1]: /etc/mtab is not a symlink or not pointing to /proc/self/mounts. This is not supported anymore. Please make sure to replace this file by a symlink to avoid incorrect or misleading mount(8) output.
[   91.507222] systemd[1]: Set up automount Arbitrary Executable File Formats File System Automount Point.
[   91.509907] systemd[1]: Started Forward Password Requests to Wall Directory Watch.
[   91.512508] systemd[1]: Reached target Remote File Systems (Pre).
[   91.515120] systemd[1]: Created slice Root Slice.
[   91.517714] systemd[1]: Listening on Journal Audit Socket.
[   91.520218] systemd[1]: Listening on Journal Socket (/dev/log).
[   91.522680] systemd[1]: Listening on /dev/initctl Compatibility Named Pipe.
[   91.525101] systemd[1]: Listening on udev Kernel Socket.
[   91.527521] systemd[1]: Listening on Journal Socket.
[   91.529986] systemd[1]: Created slice User and Session Slice.
[   91.532416] systemd[1]: Reached target Encrypted Volumes.
[   91.534744] systemd[1]: Reached target User and Group Name Lookups.
[   91.537066] systemd[1]: Created slice System Slice.
[   91.539668] systemd[1]: Starting Setup Virtual Console...
[   91.542110] systemd[1]: Created slice system-getty.slice.
[   91.544930] systemd[1]: Starting Increase datagram queue length...
[   91.547646] systemd[1]: Starting Uncomplicated firewall...
[   91.550440] systemd[1]: Started Read required files in advance.
[   91.553327] systemd[1]: Started Braille Device Support.
[   91.556048] systemd[1]: Mounting Huge Pages File System...
[   91.558531] systemd[1]: Created slice system-systemd\x2dfsck.slice.
[   91.560965] systemd[1]: Listening on udev Control Socket.
[   91.563756] systemd[1]: Starting udev Coldplug all Devices...
[   91.566586] systemd[1]: Starting Create list of required static device nodes for the current kernel...
[   91.569486] systemd[1]: Mounting POSIX Message Queue File System...
[   91.571922] systemd[1]: Listening on fsck to fsckd communication Socket.
[   91.574619] systemd[1]: Mounting Debug File System...
[   91.577022] systemd[1]: Reached target Slices.
[   91.580047] systemd[1]: Starting Load Kernel Modules...
[   91.583850] systemd[1]: Mounted Debug File System.
[   91.586448] systemd[1]: Mounted Huge Pages File System.
[   91.588993] systemd[1]: Mounted POSIX Message Queue File System.
[   91.591394] systemd[1]: Started Setup Virtual Console.
[   91.593032] lp: driver loaded but no devices found
[   91.594792] systemd[1]: Started Increase datagram queue length.
[   91.595283] ppdev: user-space parallel port driver
[   91.598264] systemd[1]: Started Uncomplicated firewall.
[   91.601394] systemd[1]: Started Create list of required static device nodes for the current kernel.
[   91.603777] systemd[1]: Started Load Kernel Modules.
[   91.614585] systemd[1]: Starting Apply Kernel Variables...
[   91.617029] systemd[1]: Mounting FUSE Control File System...
[   91.619938] systemd[1]: Starting Create Static Device Nodes in /dev...
[   91.621073] systemd[1]: Listening on Syslog Socket.
[   91.622556] systemd[1]: Starting Journal Service...
[   91.624399] systemd[1]: Mounted FUSE Control File System.
[   91.625589] systemd[1]: Started Apply Kernel Variables.
[   91.629856] systemd[1]: Started Create Static Device Nodes in /dev.
[   91.631855] systemd[1]: Starting udev Kernel Device Manager...
[   91.634174] systemd[1]: Started udev Coldplug all Devices.
[   91.656604] systemd[1]: Started udev Kernel Device Manager.
[   91.658147] systemd[1]: Starting Recovery mode menu...
[   91.659309] systemd[1]: Started Dispatch Password Requests to Console Directory Watch.
[   91.660772] systemd[1]: Started Journal Service.
[   91.702094] EDAC MC: Ver: 3.0.0
[   91.703945] ACPI Warning: SystemIO range 0x0000000000000428-0x000000000000042F conflicts with OpRegion 0x0000000000000400-0x000000000000047F (\PMIO) (20150619/utaddress-254)
[   91.703951] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   91.703954] ACPI Warning: SystemIO range 0x0000000000000540-0x000000000000054F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20150619/utaddress-254)
[   91.703957] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   91.703959] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20150619/utaddress-254)
[   91.703962] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   91.703963] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20150619/utaddress-254)
[   91.703966] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052F conflicts with OpRegion 0x000000000000050F-0x000000000000050F (\_SB_.PCI0.RLED.DBG0) (20150619/utaddress-254)
[   91.703969] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   91.703970] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   91.704143] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   91.735111] snd_hda_intel 0000:00:1b.0: enabling device (0000 -> 0002)
[   91.735293] snd_hda_intel 0000:01:00.1: enabling device (0000 -> 0002)
[   91.735322] snd_hda_intel 0000:01:00.1: Disabling MSI
[   91.735328] snd_hda_intel 0000:01:00.1: Handle VGA-switcheroo audio client
[   91.755385] snd_hda_codec_realtek hdaudioC0D2: autoconfig for ALC898: line_outs=3 (0x14/0x15/0x16/0x0/0x0) type:line
[   91.755387] snd_hda_codec_realtek hdaudioC0D2:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   91.755388] snd_hda_codec_realtek hdaudioC0D2:    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[   91.755389] snd_hda_codec_realtek hdaudioC0D2:    mono: mono_out=0x0
[   91.755390] snd_hda_codec_realtek hdaudioC0D2:    dig-out=0x11/0x1e
[   91.755391] snd_hda_codec_realtek hdaudioC0D2:    inputs:
[   91.755393] snd_hda_codec_realtek hdaudioC0D2:      Front Mic=0x19
[   91.755394] snd_hda_codec_realtek hdaudioC0D2:      Rear Mic=0x18
[   91.755395] snd_hda_codec_realtek hdaudioC0D2:      Line=0x1a
[   91.757037] usbcore: registered new interface driver snd-usb-audio
[   91.763439] AVX version of gcm_enc/dec engaged.
[   91.763441] AES CTR mode by8 optimization enabled
[   91.768583] input: HDA Intel PCH Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   91.768648] input: HDA Intel PCH Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   91.768951] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   91.769013] input: HDA Intel PCH Line Out Front as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   91.769073] input: HDA Intel PCH Line Out Surround as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[   91.769130] input: HDA Intel PCH Line Out CLFE as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
[   91.769185] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input16
[   91.778676] Adding 1951740k swap on /dev/sdb1.  Priority:-1 extents:1 across:1951740k SSFS
[   91.797086] intel_rapl: Found RAPL domain package
[   91.797089] intel_rapl: Found RAPL domain core
[   92.234478] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input17
[   92.234534] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input18
[   92.234587] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input19
[   92.234631] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input20
[   96.566856] random: nonblocking pool is initialized
[   97.708314] EXT4-fs (sdb2): re-mounted. Opts: errors=remount-ro
[   97.715791] systemd-journald[303]: Received request to flush runtime journal from PID 1
[   97.785374] audit: type=1400 audit(1446313577.681:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=762 comm="apparmor_parser"
[   97.785379] audit: type=1400 audit(1446313577.681:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=762 comm="apparmor_parser"
[   97.785382] audit: type=1400 audit(1446313577.681:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=762 comm="apparmor_parser"
[   97.785384] audit: type=1400 audit(1446313577.681:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=762 comm="apparmor_parser"
[   99.390533] audit: type=1400 audit(1446313579.285:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince" pid=762 comm="apparmor_parser"
[   99.390824] audit: type=1400 audit(1446313579.285:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=762 comm="apparmor_parser"
[   99.391285] audit: type=1400 audit(1446313579.285:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince-previewer" pid=762 comm="apparmor_parser"
[   99.391500] audit: type=1400 audit(1446313579.285:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=762 comm="apparmor_parser"
[   99.391956] audit: type=1400 audit(1446313579.289:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince-thumbnailer" pid=762 comm="apparmor_parser"
[   99.392143] audit: type=1400 audit(1446313579.289:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=762 comm="apparmor_parser"
[   99.564104] IPv6: ADDRCONF(NETDEV_UP): rename3: link is not ready
[   99.644101] IPv6: ADDRCONF(NETDEV_UP): rename3: link is not ready
[   99.645645] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[   99.899497] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[  102.922842] e1000e: eno1 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[  102.922876] IPv6: ADDRCONF(NETDEV_CHANGE): eno1: link becomes ready
[  105.525782] audit_printk_skb: 33 callbacks suppressed
[  105.525786] audit: type=1400 audit(1446313585.425:23): apparmor="DENIED" operation="open" profile="/usr/lib/telepathy/mission-control-5" name="/usr/share/dconf/profile/gdm" pid=1383 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=120 ouid=0
```

Fstab
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb2 during installation
UUID=354d4818-8aee-400e-989e-1aaed09ff5a6 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda2 during installation
UUID=BC6A-187A  /boot/efi       vfat    umask=0077      0       1
# swap was on /dev/sdb1 during installation
UUID=28ab55c9-1c79-42ca-8f3d-5165a33b68ea none            swap    sw              0       0



```

---

### Post by sean-fedex on 2015-10-31
Anyone have any ideas? Looked around and even ran a repair with fsck and saying it is okay. Also the SSD has a GPT partition table and is running on a UEFI based system.

---

### Post by sean-fedex on 2015-11-01
Bump

---

### Post by sean-fedex on 2015-11-01
Here is some more information if that helps anyone. Also what is weird fedora works fine on the 4.2 kernel but yet ubuntu does not. Anyone have any ideas at all? 

Systemd-analyze blame
```
534ms gpu-manager.service
           529ms plymouth-quit-wait.service
           348ms plymouth-start.service
           312ms dev-sdb5.device
           196ms plymouth-read-write.service
           174ms NetworkManager.service
           164ms ModemManager.service
           144ms accounts-daemon.service
           141ms grub-common.service
           126ms avahi-daemon.service
           102ms apport.service
            82ms apparmor.service
            66ms networking.service
            65ms dev-disk-by\x2duuid-91174844\x2d78f2\x2d4c4d\x2dbbfa\x2d7c9eae
            62ms systemd-hostnamed.service
            58ms systemd-logind.service
            55ms alsa-restore.service
            55ms systemd-localed.service
            54ms irqbalance.service
            51ms rsyslog.service
            47ms systemd-udev-trigger.service
            46ms systemd-journald.service
            39ms systemd-tmpfiles-setup.service
            38ms polkitd.service
            36ms systemd-fsck@dev-disk-by\x2duuid-BC6A\x2d187A.service
            29ms udisks2.service
            28ms kerneloops.service
            27ms systemd-modules-load.service
            25ms console-setup.service
            21ms systemd-tmpfiles-setup-dev.service
            18ms systemd-update-utmp.service
            16ms user@1000.service
            14ms user@120.service
            14ms systemd-udevd.service
             9ms sys-kernel-debug.mount
             9ms kmod-static-nodes.service
             8ms systemd-timesyncd.service
             8ms ufw.service
             7ms dev-hugepages.mount
             7ms ondemand.service
             7ms thermald.service
             7ms systemd-journal-flush.service
             7ms systemd-user-sessions.service
             7ms upower.service
             6ms systemd-setup-dgram-qlen.service
             6ms colord.service
             6ms dev-mqueue.mount
             6ms systemd-remount-fs.service
             6ms systemd-sysctl.service
             5ms pppd-dns.service
             4ms speech-dispatcher.service
             3ms dns-clean.service
             3ms boot-efi.mount
             3ms gdm.service
             3ms wpa_supplicant.service
             3ms resolvconf.service
             3ms systemd-random-seed.service
             2ms rtkit-daemon.service
             2ms ureadahead-stop.service
             2ms ifup-wait-all-auto.service
             2ms systemd-update-utmp-runlevel.service
             2ms rc-local.service
             1ms systemd-vconsole-setup.service
             1ms sys-fs-fuse-connections.mount


```

systemd-analyze-Here you can obviously see it is the kernel. 
```
Startup finished in 16.726s (firmware) + 2.440s (loader) + 1min 31.347s (kernel) + 1.290s (userspace) = 1min 51.804s
```

---

