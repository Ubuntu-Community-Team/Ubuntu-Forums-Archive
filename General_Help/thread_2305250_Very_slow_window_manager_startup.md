---
title: "Very slow window manager startup"
date: 2015-12-04
forum: General Help
---

### Post by mark1977 on 2015-12-04
After inputting my password, it takes Unity about 5 minutes to become usable (i.e. show a panel and/or allow me to use the keyboard).
During this time, my hard drive sounds busy. This also happens with Xfce.
Ubuntu 14.04 kernel 4.1.0-040100-generic.

dmesg:
```
dmesg[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 4.1.0-040100-generic (kernel@gloin) (gcc version 4.8.4 (Ubuntu 4.8.4-2ubuntu1~14.04) ) #201507030940 SMP Fri Jul 3 09:41:47 UTC 2015
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.1.0-040100-generic root=UUID=15be1a02-8fb7-4705-b945-175a7884ea61 ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009e7ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009e800-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000cc1b6fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000cc1b7000-0x00000000cc5f8fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000cc5f9000-0x00000000cc608fff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000cc609000-0x00000000cca06fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000cca07000-0x00000000cd63bfff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000cd63c000-0x00000000cd63cfff] usable
[    0.000000] BIOS-e820: [mem 0x00000000cd63d000-0x00000000cd83ffff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000cd840000-0x00000000cdc64fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000cdc65000-0x00000000cdff3fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000cdff4000-0x00000000cdffffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000042fffffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.7 present.
[    0.000000] DMI: System manufacturer System Product Name/SABERTOOTH X79, BIOS 3408 02/22/2013
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] AGP: No AGP bridge found
[    0.000000] e820: last_pfn = 0x430000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-E7FFF uncachable
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask 3FFC00000000 write-back
[    0.000000]   1 base 000400000000 mask 3FFFE0000000 write-back
[    0.000000]   2 base 000420000000 mask 3FFFF0000000 write-back
[    0.000000]   3 base 0000CF000000 mask 3FFFFF000000 uncachable
[    0.000000]   4 base 0000D0000000 mask 3FFFF0000000 uncachable
[    0.000000]   5 base 0000E0000000 mask 3FFFE0000000 uncachable
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] PAT configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- UC  
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 16GB, type WB
[    0.000000] reg 1, base: 16GB, range: 512MB, type WB
[    0.000000] reg 2, base: 16896MB, range: 256MB, type WB
[    0.000000] reg 3, base: 3312MB, range: 16MB, type UC
[    0.000000] reg 4, base: 3328MB, range: 256MB, type UC
[    0.000000] reg 5, base: 3584MB, range: 512MB, type UC
[    0.000000] total RAM covered: 16368M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 32M     num_reg: 8      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 256MB, type WB
[    0.000000] reg 3, base: 3312MB, range: 16MB, type UC
[    0.000000] reg 4, base: 4GB, range: 4GB, type WB
[    0.000000] reg 5, base: 8GB, range: 8GB, type WB
[    0.000000] reg 6, base: 16GB, range: 512MB, type WB
[    0.000000] reg 7, base: 16896MB, range: 256MB, type WB
[    0.000000] e820: update [mem 0xcf000000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xce000 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000fd930-0x000fd93f] mapped at [ffff8800000fd930]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000098000] 98000 size 24576
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01fe9000, 0x01fe9fff] PGTABLE
[    0.000000] BRK [0x01fea000, 0x01feafff] PGTABLE
[    0.000000] BRK [0x01feb000, 0x01febfff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x42fe00000-0x42fffffff]
[    0.000000]  [mem 0x42fe00000-0x42fffffff] page 2M
[    0.000000] BRK [0x01fec000, 0x01fecfff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x420000000-0x42fdfffff]
[    0.000000]  [mem 0x420000000-0x42fdfffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x400000000-0x41fffffff]
[    0.000000]  [mem 0x400000000-0x41fffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0xcc1b6fff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x3fffffff] page 2M
[    0.000000]  [mem 0x40000000-0xbfffffff] page 1G
[    0.000000]  [mem 0xc0000000-0xcbffffff] page 2M
[    0.000000]  [mem 0xcc000000-0xcc1b6fff] page 4k
[    0.000000] init_memory_mapping: [mem 0xcd63c000-0xcd63cfff]
[    0.000000]  [mem 0xcd63c000-0xcd63cfff] page 4k
[    0.000000] BRK [0x01fed000, 0x01fedfff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0xcd840000-0xcdc64fff]
[    0.000000]  [mem 0xcd840000-0xcd9fffff] page 4k
[    0.000000]  [mem 0xcda00000-0xcdbfffff] page 2M
[    0.000000]  [mem 0xcdc00000-0xcdc64fff] page 4k
[    0.000000] BRK [0x01fee000, 0x01feefff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0xcdff4000-0xcdffffff]
[    0.000000]  [mem 0xcdff4000-0xcdffffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x100000000-0x3ffffffff]
[    0.000000]  [mem 0x100000000-0x3ffffffff] page 1G
[    0.000000] RAMDISK: [mem 0x35baa000-0x36dccfff]
[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x00000000000F0490 000024 (v02 ALASKA)
[    0.000000] ACPI: XSDT 0x00000000CC600070 00005C (v01 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: FACP 0x00000000CC608110 00010C (v05 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: DSDT 0x00000000CC600168 007FA6 (v02 ALASKA A M I    00000010 INTL 20051117)
[    0.000000] ACPI: FACS 0x00000000CC9FE080 000040
[    0.000000] ACPI: APIC 0x00000000CC608220 0000C8 (v03 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: FPDT 0x00000000CC6082E8 000044 (v01 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: SSDT 0x00000000CC608330 0001D6 (v01 AMICPU PROC     00000001 MSFT 03000001)
[    0.000000] ACPI: MCFG 0x00000000CC608508 00003C (v01 ALASKA OEMMCFG. 01072009 MSFT 00000097)
[    0.000000] ACPI: HPET 0x00000000CC608548 000038 (v01 ALASKA A M I    01072009 AMI. 00000005)
[    0.000000] ACPI: BGRT 0x00000000CC6085D8 000038 (v00 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000042fffffff]
[    0.000000] NODE_DATA(0) allocated [mem 0x42fff7000-0x42fffbfff]
[    0.000000]  [ffffea0000000000-ffffea0010bfffff] PMD -> [ffff88041f600000-ffff88042f5fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x0000000000001000-0x0000000000ffffff]
[    0.000000]   DMA32    [mem 0x0000000001000000-0x00000000ffffffff]
[    0.000000]   Normal   [mem 0x0000000100000000-0x000000042fffffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x0000000000001000-0x000000000009dfff]
[    0.000000]   node   0: [mem 0x0000000000100000-0x00000000cc1b6fff]
[    0.000000]   node   0: [mem 0x00000000cd63c000-0x00000000cd63cfff]
[    0.000000]   node   0: [mem 0x00000000cd840000-0x00000000cdc64fff]
[    0.000000]   node   0: [mem 0x00000000cdff4000-0x00000000cdffffff]
[    0.000000]   node   0: [mem 0x0000000100000000-0x000000042fffffff]
[    0.000000] Initmem setup node 0 [mem 0x0000000000001000-0x000000042fffffff]
[    0.000000] On node 0 totalpages: 4179334
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3997 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 13016 pages used for memmap
[    0.000000]   DMA32 zone: 833001 pages, LIFO batch:31
[    0.000000]   Normal zone: 52224 pages used for memmap
[    0.000000]   Normal zone: 3342336 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x06] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x05] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x07] high edge lint[0x1])
[    0.000000] IOAPIC[0]: apic_id 0, version 32, address 0xfec00000, GSI 0-23
[    0.000000] IOAPIC[1]: apic_id 2, version 32, address 0xfec01000, GSI 24-47
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] smpboot: Allowing 8 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009efff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xcc1b7000-0xcc5f8fff]
[    0.000000] PM: Registered nosave memory: [mem 0xcc5f9000-0xcc608fff]
[    0.000000] PM: Registered nosave memory: [mem 0xcc609000-0xcca06fff]
[    0.000000] PM: Registered nosave memory: [mem 0xcca07000-0xcd63bfff]
[    0.000000] PM: Registered nosave memory: [mem 0xcd63d000-0xcd83ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xcdc65000-0xcdff3fff]
[    0.000000] PM: Registered nosave memory: [mem 0xce000000-0xdfffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfed1bfff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfeffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xff000000-0xffffffff]
[    0.000000] e820: [mem 0xce000000-0xdfffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] clocksource refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645519600211568 ns
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 34 pages/cpu @ffff88042fc00000 s100376 r8192 d30696 u262144
[    0.000000] pcpu-alloc: s100376 r8192 d30696 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 4114009
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.1.0-040100-generic root=UUID=15be1a02-8fb7-4705-b945-175a7884ea61 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave: enabled xstate_bv 0x7, cntxt size 0x340 using standard form
[    0.000000] AGP: Checking aperture...
[    0.000000] AGP: No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 16352792K/16717336K available (8056K kernel code, 1241K rwdata, 3780K rodata, 1424K init, 1292K bss, 364544K reserved, 0K cma-reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=16, nr_cpu_ids=8
[    0.000000] NR_IRQS:16640 nr_irqs:896 16
[    0.000000]     Offload RCU callbacks from all CPUs
[    0.000000]     Offload RCU callbacks from CPUs: 0-7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] clocksource hpet: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 133484882848 ns
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 3601.958 MHz processor
[    0.000025] Calibrating delay loop (skipped), value calculated using timer frequency.. 7203.91 BogoMIPS (lpj=14407832)
[    0.000027] pid_max: default: 32768 minimum: 301
[    0.000031] ACPI: Core revision 20150410
[    0.002504] ACPI: All ACPI Tables successfully acquired
[    0.192205] Security Framework initialized
[    0.192214] AppArmor: AppArmor initialized
[    0.192215] Yama: becoming mindful.
[    0.192892] Dentry cache hash table entries: 2097152 (order: 12, 16777216 bytes)
[    0.195066] Inode-cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.195995] Mount-cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.196008] Mountpoint-cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.196183] Initializing cgroup subsys blkio
[    0.196186] Initializing cgroup subsys memory
[    0.196192] Initializing cgroup subsys devices
[    0.196193] Initializing cgroup subsys freezer
[    0.196195] Initializing cgroup subsys net_cls
[    0.196196] Initializing cgroup subsys perf_event
[    0.196198] Initializing cgroup subsys net_prio
[    0.196199] Initializing cgroup subsys hugetlb
[    0.196218] CPU: Physical Processor ID: 0
[    0.196219] CPU: Processor Core ID: 0
[    0.196222] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.196223] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.196225] mce: CPU supports 16 MCE banks
[    0.196242] CPU0: Thermal monitoring enabled (TM1)
[    0.196254] process: using mwait in idle threads
[    0.196256] Last level iTLB entries: 4KB 512, 2MB 8, 4MB 8
[    0.196257] Last level dTLB entries: 4KB 512, 2MB 32, 4MB 32, 1GB 0
[    0.196372] Freeing SMP alternatives memory: 32K (ffffffff81e9c000 - ffffffff81ea4000)
[    0.197568] ftrace: allocating 30353 entries in 119 pages
[    0.208421] x2apic: IRQ remapping doesn't support X2APIC mode
[    0.208938] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.248582] TSC deadline timer enabled
[    0.248584] smpboot: CPU0: Intel(R) Core(TM) i7-3820 CPU @ 3.60GHz (fam: 06, model: 2d, stepping: 07)
[    0.248601] Performance Events: PEBS fmt1+, 16-deep LBR, SandyBridge events, full-width counters, Intel PMU driver.
[    0.248615] ... version:                3
[    0.248616] ... bit width:              48
[    0.248616] ... generic registers:      4
[    0.248617] ... value mask:             0000ffffffffffff
[    0.248618] ... max period:             0000ffffffffffff
[    0.248618] ... fixed-purpose events:   3
[    0.248619] ... event mask:             000000070000000f
[    0.249186] x86: Booting SMP configuration:
[    0.249187] .... node  #0, CPUs:      #1
[    0.262308] TSC synchronization [CPU#0 -> CPU#1]:
[    0.262310] Measured 21761901326080332 cycles TSC warp between CPUs, turning off TSC clock.
[    0.262314] tsc: Marking TSC unstable due to check_tsc_sync_source failed
[    0.262416] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.262486]  #2 #3 #4 #5 #6 #7
[    0.147395] x86: Booted up 1 node, 8 CPUs
[    0.147398] smpboot: Total of 8 processors activated (57631.32 BogoMIPS)
[    0.148098] devtmpfs: initialized
[    0.150479] evm: security.selinux
[    0.150480] evm: security.SMACK64
[    0.150481] evm: security.SMACK64EXEC
[    0.150481] evm: security.SMACK64TRANSMUTE
[    0.150482] evm: security.SMACK64MMAP
[    0.150483] evm: security.ima
[    0.150483] evm: security.capability
[    0.150495] PM: Registering ACPI NVS region [mem 0xcc609000-0xcca06fff] (4186112 bytes)
[    0.150495] PM: Registering ACPI NVS region [mem 0xcd63d000-0xcd83ffff] (2109440 bytes)
[    0.150495] clocksource jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
[    0.150495] pinctrl core: initialized pinctrl subsystem
[    0.150495] RTC time:  8:36:54, date: 12/04/15
[    0.150495] NET: Registered protocol family 16
[    0.152016] cpuidle: using governor ladder
[    0.156012] cpuidle: using governor menu
[    0.156060] ACPI: bus type PCI registered
[    0.156061] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.156113] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.156114] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.156347] PCI: Using configuration type 1 for base access
[    0.156627] perf_event_intel: PMU erratum BJ122, BV98, HSD29 worked around, HT is on
[    0.160072] ACPI: Added _OSI(Module Device)
[    0.160073] ACPI: Added _OSI(Processor Device)
[    0.160074] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.160075] ACPI: Added _OSI(Processor Aggregator Device)
[    0.161165] ACPI: Executed 1 blocks of module-level executable AML code
[    0.162484] ACPI: Dynamic OEM Table Load:
[    0.162489] ACPI: SSDT 0xFFFF88041D2E4000 00079C (v01 AMI    IST      00000001 MSFT 03000001)
[    0.162784] ACPI: Dynamic OEM Table Load:
[    0.162787] ACPI: SSDT 0xFFFF88041D3AB400 000294 (v01 AMI    CST      00000001 MSFT 03000001)
[    0.163421] ACPI : EC: EC started
[    0.163431] ACPI: Interpreter enabled
[    0.163434] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20150410/hwxface-580)
[    0.163437] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20150410/hwxface-580)
[    0.163444] ACPI: (supports S0 S3 S4 S5)
[    0.163445] ACPI: Using IOAPIC for interrupt routing
[    0.163461] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.167138] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[    0.167142] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.167231] acpi PNP0A08:00: _OSC: platform does not support [PCIeHotplug PME AER]
[    0.167312] acpi PNP0A08:00: _OSC: OS now controls [PCIeCapability]
[    0.167490] PCI host bridge to bus 0000:00
[    0.167493] pci_bus 0000:00: root bus resource [bus 00-fe]
[    0.167494] pci_bus 0000:00: root bus resource [io  0x0000-0x03af window]
[    0.167495] pci_bus 0000:00: root bus resource [io  0x03e0-0x0cf7 window]
[    0.167496] pci_bus 0000:00: root bus resource [io  0x03b0-0x03df window]
[    0.167497] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff window]
[    0.167499] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff window]
[    0.167500] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000dffff window]
[    0.167501] pci_bus 0000:00: root bus resource [mem 0xd0000000-0xfbffffff window]
[    0.167510] pci 0000:00:00.0: [8086:3c00] type 00 class 0x060000
[    0.167561] pci 0000:00:00.0: PME# supported from D0 D3hot D3cold
[    0.167618] pci 0000:00:01.0: [8086:3c02] type 01 class 0x060400
[    0.167674] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.167707] pci 0000:00:01.0: System wakeup disabled by ACPI
[    0.167740] pci 0000:00:02.0: [8086:3c04] type 01 class 0x060400
[    0.167795] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.167827] pci 0000:00:02.0: System wakeup disabled by ACPI
[    0.167857] pci 0000:00:03.0: [8086:3c08] type 01 class 0x060400
[    0.167913] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
[    0.167944] pci 0000:00:03.0: System wakeup disabled by ACPI
[    0.167974] pci 0000:00:05.0: [8086:3c28] type 00 class 0x088000
[    0.168066] pci 0000:00:05.2: [8086:3c2a] type 00 class 0x088000
[    0.168151] pci 0000:00:05.4: [8086:3c2c] type 00 class 0x080020
[    0.168160] pci 0000:00:05.4: reg 0x10: [mem 0xfa72a000-0xfa72afff]
[    0.168254] pci 0000:00:11.0: [8086:1d3e] type 01 class 0x060400
[    0.168326] pci 0000:00:11.0: PME# supported from D0 D3hot D3cold
[    0.168387] pci 0000:00:16.0: [8086:1d3a] type 00 class 0x078000
[    0.168405] pci 0000:00:16.0: reg 0x10: [mem 0xfa729000-0xfa72900f 64bit]
[    0.168466] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.168524] pci 0000:00:19.0: [8086:1503] type 00 class 0x020000
[    0.168536] pci 0000:00:19.0: reg 0x10: [mem 0xfa700000-0xfa71ffff]
[    0.168543] pci 0000:00:19.0: reg 0x14: [mem 0xfa728000-0xfa728fff]
[    0.168550] pci 0000:00:19.0: reg 0x18: [io  0xf040-0xf05f]
[    0.168597] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.168625] pci 0000:00:19.0: System wakeup disabled by ACPI
[    0.168653] pci 0000:00:1a.0: [8086:1d2d] type 00 class 0x0c0320
[    0.168668] pci 0000:00:1a.0: reg 0x10: [mem 0xfa727000-0xfa7273ff]
[    0.168737] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.168767] pci 0000:00:1a.0: System wakeup disabled by ACPI
[    0.168794] pci 0000:00:1b.0: [8086:1d20] type 00 class 0x040300
[    0.168808] pci 0000:00:1b.0: reg 0x10: [mem 0xfa720000-0xfa723fff 64bit]
[    0.168865] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.168918] pci 0000:00:1c.0: [8086:1d10] type 01 class 0x060400
[    0.168979] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.169011] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.169038] pci 0000:00:1c.1: [8086:1d12] type 01 class 0x060400
[    0.169099] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.169129] pci 0000:00:1c.1: System wakeup disabled by ACPI
[    0.169156] pci 0000:00:1c.2: [8086:1d14] type 01 class 0x060400
[    0.169217] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.169248] pci 0000:00:1c.2: System wakeup disabled by ACPI
[    0.169275] pci 0000:00:1c.3: [8086:1d16] type 01 class 0x060400
[    0.169336] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.169366] pci 0000:00:1c.3: System wakeup disabled by ACPI
[    0.169393] pci 0000:00:1c.4: [8086:1d18] type 01 class 0x060400
[    0.169454] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.169485] pci 0000:00:1c.4: System wakeup disabled by ACPI
[    0.169511] pci 0000:00:1c.5: [8086:1d1a] type 01 class 0x060400
[    0.169572] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.169603] pci 0000:00:1c.5: System wakeup disabled by ACPI
[    0.169630] pci 0000:00:1c.7: [8086:1d1e] type 01 class 0x060400
[    0.169691] pci 0000:00:1c.7: PME# supported from D0 D3hot D3cold
[    0.169722] pci 0000:00:1c.7: System wakeup disabled by ACPI
[    0.169749] pci 0000:00:1d.0: [8086:1d26] type 00 class 0x0c0320
[    0.169764] pci 0000:00:1d.0: reg 0x10: [mem 0xfa726000-0xfa7263ff]
[    0.169832] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.169863] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.169887] pci 0000:00:1e.0: [8086:244e] type 01 class 0x060401
[    0.169950] pci 0000:00:1e.0: System wakeup disabled by ACPI
[    0.169976] pci 0000:00:1f.0: [8086:1d41] type 00 class 0x060100
[    0.170111] pci 0000:00:1f.2: [8086:1d02] type 00 class 0x010601
[    0.170124] pci 0000:00:1f.2: reg 0x10: [io  0xf090-0xf097]
[    0.170130] pci 0000:00:1f.2: reg 0x14: [io  0xf080-0xf083]
[    0.170136] pci 0000:00:1f.2: reg 0x18: [io  0xf070-0xf077]
[    0.170142] pci 0000:00:1f.2: reg 0x1c: [io  0xf060-0xf063]
[    0.170148] pci 0000:00:1f.2: reg 0x20: [io  0xf020-0xf03f]
[    0.170155] pci 0000:00:1f.2: reg 0x24: [mem 0xfa725000-0xfa7257ff]
[    0.170184] pci 0000:00:1f.2: PME# supported from D3hot
[    0.170234] pci 0000:00:1f.3: [8086:1d22] type 00 class 0x0c0500
[    0.170246] pci 0000:00:1f.3: reg 0x10: [mem 0xfa724000-0xfa7240ff 64bit]
[    0.170264] pci 0000:00:1f.3: reg 0x20: [io  0xf000-0xf01f]
[    0.170353] pci 0000:00:01.0: PCI bridge to [bus 03]
[    0.170395] pci 0000:01:00.0: [10de:1200] type 00 class 0x030000
[    0.170403] pci 0000:01:00.0: reg 0x10: [mem 0xf8000000-0xf9ffffff]
[    0.170410] pci 0000:01:00.0: reg 0x14: [mem 0xd0000000-0xd7ffffff 64bit pref]
[    0.170417] pci 0000:01:00.0: reg 0x1c: [mem 0xd8000000-0xdbffffff 64bit pref]
[    0.170422] pci 0000:01:00.0: reg 0x24: [io  0xe000-0xe07f]
[    0.170427] pci 0000:01:00.0: reg 0x30: [mem 0xfa000000-0xfa07ffff pref]
[    0.170480] pci 0000:01:00.1: [10de:0e0c] type 00 class 0x040300
[    0.170487] pci 0000:01:00.1: reg 0x10: [mem 0xfa080000-0xfa083fff]
[    0.176026] pci 0000:00:02.0: PCI bridge to [bus 01]
[    0.176041] pci 0000:00:02.0:   bridge window [io  0xe000-0xefff]
[    0.176043] pci 0000:00:02.0:   bridge window [mem 0xf8000000-0xfa0fffff]
[    0.176047] pci 0000:00:02.0:   bridge window [mem 0xd0000000-0xdbffffff 64bit pref]
[    0.176078] pci 0000:00:03.0: PCI bridge to [bus 02]
[    0.176122] pci 0000:00:11.0: PCI bridge to [bus 04]
[    0.176164] pci 0000:00:1c.0: PCI bridge to [bus 05]
[    0.176226] pci 0000:06:00.0: [1b21:1042] type 00 class 0x0c0330
[    0.176256] pci 0000:06:00.0: reg 0x10: [mem 0xfa600000-0xfa607fff 64bit]
[    0.176390] pci 0000:06:00.0: PME# supported from D3hot D3cold
[    0.184024] pci 0000:00:1c.1: PCI bridge to [bus 06]
[    0.184041] pci 0000:00:1c.1:   bridge window [mem 0xfa600000-0xfa6fffff]
[    0.184101] pci 0000:07:00.0: [1b21:1042] type 00 class 0x0c0330
[    0.184131] pci 0000:07:00.0: reg 0x10: [mem 0xfa500000-0xfa507fff 64bit]
[    0.184264] pci 0000:07:00.0: PME# supported from D3hot D3cold
[    0.192023] pci 0000:00:1c.2: PCI bridge to [bus 07]
[    0.192032] pci 0000:00:1c.2:   bridge window [mem 0xfa500000-0xfa5fffff]
[    0.192105] pci 0000:08:00.0: [1b21:1042] type 00 class 0x0c0330
[    0.192135] pci 0000:08:00.0: reg 0x10: [mem 0xfa400000-0xfa407fff 64bit]
[    0.192268] pci 0000:08:00.0: PME# supported from D3hot D3cold
[    0.200023] pci 0000:00:1c.3: PCI bridge to [bus 08]
[    0.200032] pci 0000:00:1c.3:   bridge window [mem 0xfa400000-0xfa4fffff]
[    0.200101] pci 0000:09:00.0: [1b21:0612] type 00 class 0x010601
[    0.200121] pci 0000:09:00.0: reg 0x10: [io  0xd050-0xd057]
[    0.200134] pci 0000:09:00.0: reg 0x14: [io  0xd040-0xd043]
[    0.200146] pci 0000:09:00.0: reg 0x18: [io  0xd030-0xd037]
[    0.200158] pci 0000:09:00.0: reg 0x1c: [io  0xd020-0xd023]
[    0.200171] pci 0000:09:00.0: reg 0x20: [io  0xd000-0xd01f]
[    0.200183] pci 0000:09:00.0: reg 0x24: [mem 0xfa300000-0xfa3001ff]
[    0.208021] pci 0000:00:1c.4: PCI bridge to [bus 09]
[    0.208028] pci 0000:00:1c.4:   bridge window [io  0xd000-0xdfff]
[    0.208034] pci 0000:00:1c.4:   bridge window [mem 0xfa300000-0xfa3fffff]
[    0.208103] pci 0000:0a:00.0: [1106:3403] type 00 class 0x0c0010
[    0.208131] pci 0000:0a:00.0: reg 0x10: [mem 0xfa200000-0xfa2007ff 64bit]
[    0.208144] pci 0000:0a:00.0: reg 0x18: [io  0xc000-0xc0ff]
[    0.208250] pci 0000:0a:00.0: supports D2
[    0.208251] pci 0000:0a:00.0: PME# supported from D2 D3hot D3cold
[    0.216033] pci 0000:00:1c.5: PCI bridge to [bus 0a]
[    0.216036] pci 0000:00:1c.5:   bridge window [io  0xc000-0xcfff]
[    0.216039] pci 0000:00:1c.5:   bridge window [mem 0xfa200000-0xfa2fffff]
[    0.216092] pci 0000:0b:00.0: [1b4b:9130] type 00 class 0x010601
[    0.216111] pci 0000:0b:00.0: reg 0x10: [io  0xb040-0xb047]
[    0.216122] pci 0000:0b:00.0: reg 0x14: [io  0xb030-0xb033]
[    0.216133] pci 0000:0b:00.0: reg 0x18: [io  0xb020-0xb027]
[    0.216144] pci 0000:0b:00.0: reg 0x1c: [io  0xb010-0xb013]
[    0.216156] pci 0000:0b:00.0: reg 0x20: [io  0xb000-0xb00f]
[    0.216167] pci 0000:0b:00.0: reg 0x24: [mem 0xfa110000-0xfa1107ff]
[    0.216178] pci 0000:0b:00.0: reg 0x30: [mem 0xfa100000-0xfa10ffff pref]
[    0.216225] pci 0000:0b:00.0: PME# supported from D3hot
[    0.224020] pci 0000:00:1c.7: PCI bridge to [bus 0b]
[    0.224027] pci 0000:00:1c.7:   bridge window [io  0xb000-0xbfff]
[    0.224032] pci 0000:00:1c.7:   bridge window [mem 0xfa100000-0xfa1fffff]
[    0.224106] pci 0000:00:1e.0: PCI bridge to [bus 0c] (subtractive decode)
[    0.224114] pci 0000:00:1e.0:   bridge window [io  0x0000-0x03af window] (subtractive decode)
[    0.224115] pci 0000:00:1e.0:   bridge window [io  0x03e0-0x0cf7 window] (subtractive decode)
[    0.224116] pci 0000:00:1e.0:   bridge window [io  0x03b0-0x03df window] (subtractive decode)
[    0.224117] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff window] (subtractive decode)
[    0.224119] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff window] (subtractive decode)
[    0.224120] pci 0000:00:1e.0:   bridge window [mem 0x000c0000-0x000dffff window] (subtractive decode)
[    0.224121] pci 0000:00:1e.0:   bridge window [mem 0xd0000000-0xfbffffff window] (subtractive decode)
[    0.224455] ACPI: PCI Root Bridge [UNC0] (domain 0000 [bus ff])
[    0.224458] acpi PNP0A03:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.224460] acpi PNP0A03:00: _OSC failed (AE_NOT_FOUND); disabling ASPM
[    0.224493] PCI host bridge to bus 0000:ff
[    0.224495] pci_bus 0000:ff: root bus resource [bus ff]
[    0.224501] pci 0000:ff:08.0: [8086:3c80] type 00 class 0x088000
[    0.224541] pci 0000:ff:08.3: [8086:3c83] type 00 class 0x088000
[    0.224585] pci 0000:ff:08.4: [8086:3c84] type 00 class 0x088000
[    0.224635] pci 0000:ff:09.0: [8086:3c90] type 00 class 0x088000
[    0.224673] pci 0000:ff:09.3: [8086:3c93] type 00 class 0x088000
[    0.224718] pci 0000:ff:09.4: [8086:3c94] type 00 class 0x088000
[    0.224767] pci 0000:ff:0a.0: [8086:3cc0] type 00 class 0x088000
[    0.224799] pci 0000:ff:0a.1: [8086:3cc1] type 00 class 0x088000
[    0.224831] pci 0000:ff:0a.2: [8086:3cc2] type 00 class 0x088000
[    0.224862] pci 0000:ff:0a.3: [8086:3cd0] type 00 class 0x088000
[    0.224894] pci 0000:ff:0b.0: [8086:3ce0] type 00 class 0x088000
[    0.224924] pci 0000:ff:0b.3: [8086:3ce3] type 00 class 0x088000
[    0.224955] pci 0000:ff:0c.0: [8086:3ce8] type 00 class 0x088000
[    0.224984] pci 0000:ff:0c.1: [8086:3ce8] type 00 class 0x088000
[    0.225015] pci 0000:ff:0c.6: [8086:3cf4] type 00 class 0x088000
[    0.225045] pci 0000:ff:0c.7: [8086:3cf6] type 00 class 0x088000
[    0.225075] pci 0000:ff:0d.0: [8086:3ce8] type 00 class 0x088000
[    0.225104] pci 0000:ff:0d.1: [8086:3ce8] type 00 class 0x088000
[    0.225135] pci 0000:ff:0d.6: [8086:3cf5] type 00 class 0x088000
[    0.225166] pci 0000:ff:0e.0: [8086:3ca0] type 00 class 0x088000
[    0.225198] pci 0000:ff:0e.1: [8086:3c46] type 00 class 0x110100
[    0.225234] pci 0000:ff:0f.0: [8086:3ca8] type 00 class 0x088000
[    0.225274] pci 0000:ff:0f.1: [8086:3c71] type 00 class 0x088000
[    0.225314] pci 0000:ff:0f.2: [8086:3caa] type 00 class 0x088000
[    0.225354] pci 0000:ff:0f.3: [8086:3cab] type 00 class 0x088000
[    0.225394] pci 0000:ff:0f.4: [8086:3cac] type 00 class 0x088000
[    0.225434] pci 0000:ff:0f.5: [8086:3cad] type 00 class 0x088000
[    0.225472] pci 0000:ff:0f.6: [8086:3cae] type 00 class 0x088000
[    0.225507] pci 0000:ff:10.0: [8086:3cb0] type 00 class 0x088000
[    0.225548] pci 0000:ff:10.1: [8086:3cb1] type 00 class 0x088000
[    0.225588] pci 0000:ff:10.2: [8086:3cb2] type 00 class 0x088000
[    0.225629] pci 0000:ff:10.3: [8086:3cb3] type 00 class 0x088000
[    0.225669] pci 0000:ff:10.4: [8086:3cb4] type 00 class 0x088000
[    0.225710] pci 0000:ff:10.5: [8086:3cb5] type 00 class 0x088000
[    0.225750] pci 0000:ff:10.6: [8086:3cb6] type 00 class 0x088000
[    0.225790] pci 0000:ff:10.7: [8086:3cb7] type 00 class 0x088000
[    0.225829] pci 0000:ff:11.0: [8086:3cb8] type 00 class 0x088000
[    0.225866] pci 0000:ff:13.0: [8086:3ce4] type 00 class 0x088000
[    0.225896] pci 0000:ff:13.1: [8086:3c43] type 00 class 0x110100
[    0.225928] pci 0000:ff:13.4: [8086:3ce6] type 00 class 0x110100
[    0.225957] pci 0000:ff:13.5: [8086:3c44] type 00 class 0x110100
[    0.225988] pci 0000:ff:13.6: [8086:3c45] type 00 class 0x088000
[    0.226079] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.226109] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.226138] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 10 11 12 14 *15)
[    0.226166] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 10 11 12 *14 15)
[    0.226195] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.226223] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.226252] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.226281] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.226369] ACPI: Enabled 2 GPEs in block 00 to 3F
[    0.226381] ACPI : EC: GPE = 0x1e, I/O: command/status = 0x66, data = 0x62
[    0.226435] vgaarb: setting as boot device: PCI:0000:01:00.0
[    0.226435] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.226435] vgaarb: loaded
[    0.226435] vgaarb: bridge control possible 0000:01:00.0
[    0.226435] SCSI subsystem initialized
[    0.226435] libata version 3.00 loaded.
[    0.226435] ACPI: bus type USB registered
[    0.226435] usbcore: registered new interface driver usbfs
[    0.226435] usbcore: registered new interface driver hub
[    0.226435] usbcore: registered new device driver usb
[    0.226435] PCI: Using ACPI for IRQ routing
[    0.232158] PCI: pci_cache_line_size set to 64 bytes
[    0.232258] e820: reserve RAM buffer [mem 0x0009e800-0x0009ffff]
[    0.232259] e820: reserve RAM buffer [mem 0xcc1b7000-0xcfffffff]
[    0.232260] e820: reserve RAM buffer [mem 0xcd63d000-0xcfffffff]
[    0.232261] e820: reserve RAM buffer [mem 0xcdc65000-0xcfffffff]
[    0.232262] e820: reserve RAM buffer [mem 0xce000000-0xcfffffff]
[    0.232340] NetLabel: Initializing
[    0.232341] NetLabel:  domain hash size = 128
[    0.232342] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.232351] NetLabel:  unlabeled traffic allowed by default
[    0.232366] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.232366] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.234057] Switched to clocksource hpet
[    0.235982] AppArmor: AppArmor Filesystem Enabled
[    0.236042] pnp: PnP ACPI init
[    0.236099] system 00:00: [mem 0xfc000000-0xfcffffff] has been reserved
[    0.236101] system 00:00: [mem 0xfd000000-0xfdffffff] has been reserved
[    0.236102] system 00:00: [mem 0xfe000000-0xfeafffff] has been reserved
[    0.236103] system 00:00: [mem 0xfbfff000-0xfbffffff] has been reserved
[    0.236104] system 00:00: [mem 0xfeb00000-0xfebfffff] has been reserved
[    0.236106] system 00:00: [mem 0xfed00400-0xfed3ffff] could not be reserved
[    0.236107] system 00:00: [mem 0xfed45000-0xfedfffff] has been reserved
[    0.236110] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.236181] system 00:01: [io  0x0290-0x029f] has been reserved
[    0.236183] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.236206] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.236251] system 00:03: [io  0x04d0-0x04d1] has been reserved
[    0.236253] system 00:03: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.236379] pnp 00:04: [dma 0 disabled]
[    0.236412] pnp 00:04: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.236535] system 00:05: [io  0x0400-0x0453] could not be reserved
[    0.236537] system 00:05: [io  0x0458-0x047f] has been reserved
[    0.236538] system 00:05: [io  0x1180-0x119f] has been reserved
[    0.236539] system 00:05: [io  0x0500-0x057f] has been reserved
[    0.236540] system 00:05: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.236542] system 00:05: [mem 0xfec00000-0xfecfffff] could not be reserved
[    0.236543] system 00:05: [mem 0xfed08000-0xfed08fff] has been reserved
[    0.236544] system 00:05: [mem 0xff000000-0xffffffff] has been reserved
[    0.236546] system 00:05: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.236592] system 00:06: [io  0x0454-0x0457] has been reserved
[    0.236594] system 00:06: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.236706] pnp: PnP ACPI: found 7 devices
[    0.242615] clocksource acpi_pm: mask: 0xffffff max_cycles: 0xffffff, max_idle_ns: 2085701024 ns
[    0.242689] pci 0000:00:01.0: PCI bridge to [bus 03]
[    0.242697] pci 0000:00:02.0: PCI bridge to [bus 01]
[    0.242699] pci 0000:00:02.0:   bridge window [io  0xe000-0xefff]
[    0.242702] pci 0000:00:02.0:   bridge window [mem 0xf8000000-0xfa0fffff]
[    0.242705] pci 0000:00:02.0:   bridge window [mem 0xd0000000-0xdbffffff 64bit pref]
[    0.242708] pci 0000:00:03.0: PCI bridge to [bus 02]
[    0.242716] pci 0000:00:11.0: PCI bridge to [bus 04]
[    0.242726] pci 0000:00:1c.0: PCI bridge to [bus 05]
[    0.242736] pci 0000:00:1c.1: PCI bridge to [bus 06]
[    0.242739] pci 0000:00:1c.1:   bridge window [mem 0xfa600000-0xfa6fffff]
[    0.242746] pci 0000:00:1c.2: PCI bridge to [bus 07]
[    0.242750] pci 0000:00:1c.2:   bridge window [mem 0xfa500000-0xfa5fffff]
[    0.242756] pci 0000:00:1c.3: PCI bridge to [bus 08]
[    0.242760] pci 0000:00:1c.3:   bridge window [mem 0xfa400000-0xfa4fffff]
[    0.242766] pci 0000:00:1c.4: PCI bridge to [bus 09]
[    0.242768] pci 0000:00:1c.4:   bridge window [io  0xd000-0xdfff]
[    0.242772] pci 0000:00:1c.4:   bridge window [mem 0xfa300000-0xfa3fffff]
[    0.242778] pci 0000:00:1c.5: PCI bridge to [bus 0a]
[    0.242780] pci 0000:00:1c.5:   bridge window [io  0xc000-0xcfff]
[    0.242784] pci 0000:00:1c.5:   bridge window [mem 0xfa200000-0xfa2fffff]
[    0.242790] pci 0000:00:1c.7: PCI bridge to [bus 0b]
[    0.242792] pci 0000:00:1c.7:   bridge window [io  0xb000-0xbfff]
[    0.242796] pci 0000:00:1c.7:   bridge window [mem 0xfa100000-0xfa1fffff]
[    0.242802] pci 0000:00:1e.0: PCI bridge to [bus 0c]
[    0.242811] pci_bus 0000:00: resource 4 [io  0x0000-0x03af window]
[    0.242812] pci_bus 0000:00: resource 5 [io  0x03e0-0x0cf7 window]
[    0.242813] pci_bus 0000:00: resource 6 [io  0x03b0-0x03df window]
[    0.242814] pci_bus 0000:00: resource 7 [io  0x0d00-0xffff window]
[    0.242816] pci_bus 0000:00: resource 8 [mem 0x000a0000-0x000bffff window]
[    0.242817] pci_bus 0000:00: resource 9 [mem 0x000c0000-0x000dffff window]
[    0.242818] pci_bus 0000:00: resource 10 [mem 0xd0000000-0xfbffffff window]
[    0.242819] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.242820] pci_bus 0000:01: resource 1 [mem 0xf8000000-0xfa0fffff]
[    0.242821] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdbffffff 64bit pref]
[    0.242823] pci_bus 0000:06: resource 1 [mem 0xfa600000-0xfa6fffff]
[    0.242824] pci_bus 0000:07: resource 1 [mem 0xfa500000-0xfa5fffff]
[    0.242825] pci_bus 0000:08: resource 1 [mem 0xfa400000-0xfa4fffff]
[    0.242826] pci_bus 0000:09: resource 0 [io  0xd000-0xdfff]
[    0.242827] pci_bus 0000:09: resource 1 [mem 0xfa300000-0xfa3fffff]
[    0.242828] pci_bus 0000:0a: resource 0 [io  0xc000-0xcfff]
[    0.242829] pci_bus 0000:0a: resource 1 [mem 0xfa200000-0xfa2fffff]
[    0.242830] pci_bus 0000:0b: resource 0 [io  0xb000-0xbfff]
[    0.242831] pci_bus 0000:0b: resource 1 [mem 0xfa100000-0xfa1fffff]
[    0.242832] pci_bus 0000:0c: resource 4 [io  0x0000-0x03af window]
[    0.242834] pci_bus 0000:0c: resource 5 [io  0x03e0-0x0cf7 window]
[    0.242835] pci_bus 0000:0c: resource 6 [io  0x03b0-0x03df window]
[    0.242836] pci_bus 0000:0c: resource 7 [io  0x0d00-0xffff window]
[    0.242837] pci_bus 0000:0c: resource 8 [mem 0x000a0000-0x000bffff window]
[    0.242838] pci_bus 0000:0c: resource 9 [mem 0x000c0000-0x000dffff window]
[    0.242839] pci_bus 0000:0c: resource 10 [mem 0xd0000000-0xfbffffff window]
[    0.242863] NET: Registered protocol family 2
[    0.243010] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.243174] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.243264] TCP: Hash tables configured (established 131072 bind 65536)
[    0.243291] UDP hash table entries: 8192 (order: 6, 262144 bytes)
[    0.243332] UDP-Lite hash table entries: 8192 (order: 6, 262144 bytes)
[    0.243391] NET: Registered protocol family 1
[    0.284101] pci 0000:01:00.0: Video device with shadowed ROM
[    0.284429] PCI: CLS 64 bytes, default 64
[    0.284465] Trying to unpack rootfs image as initramfs...
[    0.488031] Freeing initrd memory: 18572K (ffff880035baa000 - ffff880036dcd000)
[    0.488053] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.488055] software IO TLB [mem 0xc81b7000-0xcc1b7000] (64MB) mapped at [ffff8800c81b7000-ffff8800cc1b6fff]
[    0.488087] clocksource tsc: mask: 0xffffffffffffffff max_cycles: 0x33eb8d4b9ec, max_idle_ns: 440795286425 ns
[    0.488107] RAPL PMU detected, API unit is 2^-32 Joules, 3 fixed counters 163840 ms ovfl timer
[    0.488108] hw unit of domain pp0-core 2^-16 Joules
[    0.488109] hw unit of domain package 2^-16 Joules
[    0.488109] hw unit of domain dram 2^-16 Joules
[    0.488304] microcode: CPU0 sig=0x206d7, pf=0x4, revision=0x70c
[    0.488310] microcode: CPU1 sig=0x206d7, pf=0x4, revision=0x70c
[    0.488316] microcode: CPU2 sig=0x206d7, pf=0x4, revision=0x70c
[    0.488323] microcode: CPU3 sig=0x206d7, pf=0x4, revision=0x70c
[    0.488328] microcode: CPU4 sig=0x206d7, pf=0x4, revision=0x70c
[    0.488335] microcode: CPU5 sig=0x206d7, pf=0x4, revision=0x70c
[    0.488340] microcode: CPU6 sig=0x206d7, pf=0x4, revision=0x70c
[    0.488345] microcode: CPU7 sig=0x206d7, pf=0x4, revision=0x70c
[    0.488391] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.488407] Scanning for low memory corruption every 60 seconds
[    0.488676] futex hash table entries: 2048 (order: 5, 131072 bytes)
[    0.488695] Initialise system trusted keyring
[    0.488712] audit: initializing netlink subsys (disabled)
[    0.488724] audit: type=2000 audit(1449218213.488:1): initialized
[    0.489102] HugeTLB registered 1 GB page size, pre-allocated 0 pages
[    0.489103] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.490108] zpool: loaded
[    0.490109] zbud: loaded
[    0.490218] VFS: Disk quotas dquot_6.6.0
[    0.490242] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.490549] fuse init (API version 7.23)
[    0.490648] Key type big_key registered
[    0.490957] Key type asymmetric registered
[    0.490959] Asymmetric key parser 'x509' registered
[    0.490983] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 251)
[    0.491029] io scheduler noop registered
[    0.491031] io scheduler deadline registered (default)
[    0.491051] io scheduler cfq registered
[    0.491889] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.491900] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.491932] intel_idle: MWAIT substates: 0x21120
[    0.491933] intel_idle: v0.4 model 0x2D
[    0.491934] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.492198] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.492201] ACPI: Power Button [PWRB]
[    0.492226] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.492227] ACPI: Power Button [PWRF]
[    0.492921] GHES: HEST is not enabled!
[    0.492994] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.513380] 00:04: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
[    0.514560] Linux agpgart interface v0.103
[    0.516727] brd: module loaded
[    0.517484] loop: module loaded
[    0.517639] libphy: Fixed MDIO Bus: probed
[    0.517641] tun: Universal TUN/TAP device driver, 1.6
[    0.517642] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.517673] PPP generic driver version 2.4.2
[    0.517764] xhci_hcd 0000:06:00.0: xHCI Host Controller
[    0.517769] xhci_hcd 0000:06:00.0: new USB bus registered, assigned bus number 1
[    0.578949] xhci_hcd 0000:06:00.0: hcc params 0x0200f180 hci version 0x96 quirks 0x00080000
[    0.579101] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.579102] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.579103] usb usb1: Product: xHCI Host Controller
[    0.579105] usb usb1: Manufacturer: Linux 4.1.0-040100-generic xhci-hcd
[    0.579106] usb usb1: SerialNumber: 0000:06:00.0
[    0.579184] hub 1-0:1.0: USB hub found
[    0.579192] hub 1-0:1.0: 2 ports detected
[    0.579256] xhci_hcd 0000:06:00.0: xHCI Host Controller
[    0.579258] xhci_hcd 0000:06:00.0: new USB bus registered, assigned bus number 2
[    0.579287] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003
[    0.579288] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.579289] usb usb2: Product: xHCI Host Controller
[    0.579290] usb usb2: Manufacturer: Linux 4.1.0-040100-generic xhci-hcd
[    0.579291] usb usb2: SerialNumber: 0000:06:00.0
[    0.579379] hub 2-0:1.0: USB hub found
[    0.579386] hub 2-0:1.0: 2 ports detected
[    0.579476] xhci_hcd 0000:07:00.0: xHCI Host Controller
[    0.579479] xhci_hcd 0000:07:00.0: new USB bus registered, assigned bus number 3
[    0.640656] xhci_hcd 0000:07:00.0: hcc params 0x0200f180 hci version 0x96 quirks 0x00080000
[    0.640791] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    0.640792] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.640794] usb usb3: Product: xHCI Host Controller
[    0.640795] usb usb3: Manufacturer: Linux 4.1.0-040100-generic xhci-hcd
[    0.640796] usb usb3: SerialNumber: 0000:07:00.0
[    0.640892] hub 3-0:1.0: USB hub found
[    0.640899] hub 3-0:1.0: 2 ports detected
[    0.640958] xhci_hcd 0000:07:00.0: xHCI Host Controller
[    0.640960] xhci_hcd 0000:07:00.0: new USB bus registered, assigned bus number 4
[    0.640988] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
[    0.640989] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.640990] usb usb4: Product: xHCI Host Controller
[    0.640991] usb usb4: Manufacturer: Linux 4.1.0-040100-generic xhci-hcd
[    0.640992] usb usb4: SerialNumber: 0000:07:00.0
[    0.641060] hub 4-0:1.0: USB hub found
[    0.641066] hub 4-0:1.0: 2 ports detected
[    0.641154] xhci_hcd 0000:08:00.0: xHCI Host Controller
[    0.641157] xhci_hcd 0000:08:00.0: new USB bus registered, assigned bus number 5
[    0.702331] xhci_hcd 0000:08:00.0: hcc params 0x0200f180 hci version 0x96 quirks 0x00080000
[    0.702470] usb usb5: New USB device found, idVendor=1d6b, idProduct=0002
[    0.702471] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.702472] usb usb5: Product: xHCI Host Controller
[    0.702473] usb usb5: Manufacturer: Linux 4.1.0-040100-generic xhci-hcd
[    0.702474] usb usb5: SerialNumber: 0000:08:00.0
[    0.702566] hub 5-0:1.0: USB hub found
[    0.702573] hub 5-0:1.0: 2 ports detected
[    0.702631] xhci_hcd 0000:08:00.0: xHCI Host Controller
[    0.702633] xhci_hcd 0000:08:00.0: new USB bus registered, assigned bus number 6
[    0.702661] usb usb6: New USB device found, idVendor=1d6b, idProduct=0003
[    0.702662] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.702663] usb usb6: Product: xHCI Host Controller
[    0.702664] usb usb6: Manufacturer: Linux 4.1.0-040100-generic xhci-hcd
[    0.702665] usb usb6: SerialNumber: 0000:08:00.0
[    0.702750] hub 6-0:1.0: USB hub found
[    0.702757] hub 6-0:1.0: 2 ports detected
[    0.702817] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.702821] ehci-pci: EHCI PCI platform driver
[    0.702890] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    0.702894] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 7
[    0.702902] ehci-pci 0000:00:1a.0: debug port 2
[    0.706798] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    0.706808] ehci-pci 0000:00:1a.0: irq 23, io mem 0xfa727000
[    0.716012] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    0.716032] usb usb7: New USB device found, idVendor=1d6b, idProduct=0002
[    0.716033] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.716034] usb usb7: Product: EHCI Host Controller
[    0.716035] usb usb7: Manufacturer: Linux 4.1.0-040100-generic ehci_hcd
[    0.716036] usb usb7: SerialNumber: 0000:00:1a.0
[    0.716132] hub 7-0:1.0: USB hub found
[    0.716136] hub 7-0:1.0: 2 ports detected
[    0.716258] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    0.716262] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 8
[    0.716270] ehci-pci 0000:00:1d.0: debug port 2
[    0.720166] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    0.720169] ehci-pci 0000:00:1d.0: irq 23, io mem 0xfa726000
[    0.732011] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    0.732033] usb usb8: New USB device found, idVendor=1d6b, idProduct=0002
[    0.732034] usb usb8: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.732035] usb usb8: Product: EHCI Host Controller
[    0.732036] usb usb8: Manufacturer: Linux 4.1.0-040100-generic ehci_hcd
[    0.732037] usb usb8: SerialNumber: 0000:00:1d.0
[    0.732185] hub 8-0:1.0: USB hub found
[    0.732189] hub 8-0:1.0: 2 ports detected
[    0.732259] ehci-platform: EHCI generic platform driver
[    0.732265] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.732269] ohci-pci: OHCI PCI platform driver
[    0.732278] ohci-platform: OHCI generic platform driver
[    0.732284] uhci_hcd: USB Universal Host Controller Interface driver
[    0.732317] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    0.735293] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.735298] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.735474] mousedev: PS/2 mouse device common for all mice
[    0.735799] rtc_cmos 00:02: RTC can wake from S4
[    0.735963] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.735989] rtc_cmos 00:02: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.736013] i2c /dev entries driver
[    0.736047] device-mapper: uevent: version 1.0.3
[    0.736120] device-mapper: ioctl: 4.31.0-ioctl (2015-3-12) initialised: dm-devel@redhat.com
[    0.736133] Intel P-state driver initializing.
[    0.736348] ledtrig-cpu: registered to indicate activity on CPUs
[    0.736488] PCCT header not found.
[    0.736621] NET: Registered protocol family 10
[    0.736764] NET: Registered protocol family 17
[    0.736773] Key type dns_resolver registered
[    0.737168] Loading compiled-in X.509 certificates
[    0.737777] Loaded X.509 cert 'Build time autogenerated kernel key: 79c90237faa58206c0c680daf1a7efae24eb12d0'
[    0.737785] registered taskstats version 1
[    0.739318] Key type trusted registered
[    0.741906] Key type encrypted registered
[    0.741911] AppArmor: AppArmor sha1 policy hashing enabled
[    0.741913] ima: No TPM chip found, activating TPM-bypass!
[    0.741928] evm: HMAC attrs: 0x1
[    0.742389]   Magic number: 11:763:623
[    0.742484] rtc_cmos 00:02: setting system clock to 2015-12-04 08:36:54 UTC (1449218214)
[    0.742608] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.742608] EDD information not available.
[    0.742654] PM: Hibernation image not present or could not be loaded.
[    0.742928] Freeing unused kernel memory: 1424K (ffffffff81d38000 - ffffffff81e9c000)
[    0.742929] Write protecting the kernel read-only data: 12288k
[    0.743114] Freeing unused kernel memory: 124K (ffff8800017e1000 - ffff880001800000)
[    0.743212] Freeing unused kernel memory: 316K (ffff880001bb1000 - ffff880001c00000)
[    0.753246] systemd-udevd[167]: starting version 204
[    0.765121] pps_core: LinuxPPS API ver. 1 registered
[    0.765124] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
[    0.766209] PTP clock support registered
[    0.767169] ahci 0000:00:1f.2: version 3.0
[    0.770274] e1000e: Intel(R) PRO/1000 Network Driver - 2.3.2-k
[    0.770275] e1000e: Copyright(c) 1999 - 2014 Intel Corporation.
[    0.780039] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0xa impl SATA mode
[    0.780042] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ems apst 
[    0.788451] scsi host0: ahci
[    0.788553] scsi host1: ahci
[    0.788640] scsi host2: ahci
[    0.788727] scsi host3: ahci
[    0.788812] scsi host4: ahci
[    0.788897] scsi host5: ahci
[    0.788928] ata1: DUMMY
[    0.788930] ata2: SATA max UDMA/133 abar m2048@0xfa725000 port 0xfa725180 irq 51
[    0.788931] ata3: DUMMY
[    0.788932] ata4: SATA max UDMA/133 abar m2048@0xfa725000 port 0xfa725280 irq 51
[    0.788933] ata5: DUMMY
[    0.788934] ata6: DUMMY
[    0.789100] e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    0.789125] ahci 0000:09:00.0: SSS flag set, parallel bus scan disabled
[    0.789174] ahci 0000:09:00.0: AHCI 0001.0200 32 slots 2 ports 6 Gbps 0x3 impl SATA mode
[    0.789175] ahci 0000:09:00.0: flags: 64bit ncq sntf stag led clo pmp pio slum part ccc sxs 
[    0.789386] scsi host6: ahci
[    0.789475] scsi host7: ahci
[    0.789506] ata7: SATA max UDMA/133 abar m512@0xfa300000 port 0xfa300100 irq 52
[    0.789509] ata8: SATA max UDMA/133 abar m512@0xfa300000 port 0xfa300180 irq 52
[    0.804079] ahci 0000:0b:00.0: AHCI 0001.0200 32 slots 8 ports 6 Gbps 0xff impl SATA mode
[    0.804080] ahci 0000:0b:00.0: flags: 64bit ncq pio 
[    0.804688] scsi host8: ahci
[    0.804789] scsi host9: ahci
[    0.804884] scsi host10: ahci
[    0.804970] scsi host11: ahci
[    0.805053] scsi host12: ahci
[    0.805135] scsi host13: ahci
[    0.805217] scsi host14: ahci
[    0.805303] scsi host15: ahci
[    0.805335] ata9: SATA max UDMA/133 abar m2048@0xfa110000 port 0xfa110100 irq 54
[    0.805338] ata10: SATA max UDMA/133 abar m2048@0xfa110000 port 0xfa110180 irq 54
[    0.805340] ata11: SATA max UDMA/133 abar m2048@0xfa110000 port 0xfa110200 irq 54
[    0.805342] ata12: SATA max UDMA/133 abar m2048@0xfa110000 port 0xfa110280 irq 54
[    0.805344] ata13: SATA max UDMA/133 abar m2048@0xfa110000 port 0xfa110300 irq 54
[    0.805347] ata14: SATA max UDMA/133 abar m2048@0xfa110000 port 0xfa110380 irq 54
[    0.805349] ata15: SATA max UDMA/133 abar m2048@0xfa110000 port 0xfa110400 irq 54
[    0.805351] ata16: SATA max UDMA/133 abar m2048@0xfa110000 port 0xfa110480 irq 54
[    0.832075] firewire_ohci 0000:0a:00.0: added OHCI v1.10 device as card 0, 4 IR + 8 IT contexts, quirks 0x10
[    1.008030] usb 3-1: new high-speed USB device number 2 using xhci_hcd
[    1.028058] usb 7-1: new high-speed USB device number 2 using ehci-pci
[    1.044024] usb 8-1: new high-speed USB device number 2 using ehci-pci
[    1.057929] e1000e 0000:00:19.0 eth0: registered PHC clock
[    1.057931] e1000e 0000:00:19.0 eth0: (PCI Express:2.5GT/s:Width x1) 30:85:a9:9a:c7:57
[    1.057932] e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
[    1.057971] e1000e 0000:00:19.0 eth0: MAC: 10, PHY: 11, PBA No: FFFFFF-0FF
[    1.108101] ata7: SATA link down (SStatus 0 SControl 300)
[    1.108105] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.108134] ata2: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.109955] ata4.00: ATAPI: ATAPI   iHAS124   W, HL03, max UDMA/100
[    1.110199] ata2.00: ATA-8: WDC WD1002FAEX-00Z3A0, 05.01D05, max UDMA/133
[    1.110214] ata2.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.111968] ata4.00: configured for UDMA/100
[    1.112613] ata2.00: configured for UDMA/133
[    1.112769] scsi 1:0:0:0: Direct-Access     ATA      WDC WD1002FAEX-0 1D05 PQ: 0 ANSI: 5
[    1.113035] sd 1:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.113042] sd 1:0:0:0: Attached scsi generic sg0 type 0
[    1.113058] sd 1:0:0:0: [sda] Write Protect is off
[    1.113061] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.113076] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.113757] scsi 3:0:0:0: CD-ROM            ATAPI    iHAS124   W      HL03 PQ: 0 ANSI: 5
[    1.124069] ata12: SATA link down (SStatus 0 SControl 300)
[    1.132076] ata9: SATA link down (SStatus 0 SControl 300)
[    1.132110] ata16: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.132135] ata14: SATA link down (SStatus 0 SControl 300)
[    1.132164] ata10: SATA link down (SStatus 0 SControl 300)
[    1.132211] ata11: SATA link down (SStatus 0 SControl 300)
[    1.132242] ata15: SATA link down (SStatus 0 SControl 300)
[    1.132273] ata13: SATA link down (SStatus 0 SControl 300)
[    1.132289] ata16.00: ATAPI: MARVELL VIRTUALL, 1.09, max UDMA/66
[    1.132610] ata16.00: configured for UDMA/66
[    1.134602] sr 3:0:0:0: [sr0] scsi3-mmc drive: 125x/125x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.134605] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.134758] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    1.134848] sr 3:0:0:0: Attached scsi generic sg1 type 5
[    1.144932]  sda: sda1 sda2 < sda5 >
[    1.145264] sd 1:0:0:0: [sda] Attached SCSI disk
[    1.160392] usb 7-1: New USB device found, idVendor=8087, idProduct=0024
[    1.160396] usb 7-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.160669] hub 7-1:1.0: USB hub found
[    1.160740] hub 7-1:1.0: 6 ports detected
[    1.176425] usb 8-1: New USB device found, idVendor=8087, idProduct=0024
[    1.176442] usb 8-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.176693] hub 8-1:1.0: USB hub found
[    1.176933] hub 8-1:1.0: 8 ports detected
[    1.193076] usb 3-1: New USB device found, idVendor=03f0, idProduct=4607
[    1.193104] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.193105] usb 3-1: Product: External HDD
[    1.193106] usb 3-1: Manufacturer: HP
[    1.193107] usb 3-1: SerialNumber: 5743415A4137303336363432
[    1.195760] usb-storage 3-1:1.0: USB Mass Storage device detected
[    1.195900] scsi host16: usb-storage 3-1:1.0
[    1.195941] usbcore: registered new interface driver usb-storage
[    1.196917] usbcore: registered new interface driver uas
[    1.332109] firewire_core 0000:0a:00.0: created device fw0: GUID 001e8c00005eb15e, S400
[    1.448181] usb 8-1.2: new low-speed USB device number 3 using ehci-pci
[    1.452072] ata8: SATA link down (SStatus 0 SControl 300)
[    1.452373] scsi 15:0:0:0: Processor         Marvell  91xx Config      1.01 PQ: 0 ANSI: 5
[    1.468056] ata16.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[    1.468110] ata16.00: irq_stat 0x40000001
[    1.468157] ata16.00: cmd a0/01:00:00:00:01/00:00:00:00:00/a0 tag 1 dma 16640 in
[    1.468157]          Inquiry 12 01 00 00 ff 00res 00/00:00:00:00:00/00:00:00:00:00/00 Emask 0x3 (HSM violation)
[    1.468243] ata16: hard resetting link
[    1.544293] usb 8-1.2: New USB device found, idVendor=0458, idProduct=003a
[    1.544295] usb 8-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.544296] usb 8-1.2: Product: Optical Mouse
[    1.544297] usb 8-1.2: Manufacturer: Genius
[    1.547977] hidraw: raw HID events driver (C) Jiri Kosina
[    1.551295] usbcore: registered new interface driver usbhid
[    1.551296] usbhid: USB HID core driver
[    1.552314] input: Genius Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb8/8-1/8-1.2/8-1.2:1.0/0003:0458:003A.0001/input/input5
[    1.552397] hid-generic 0003:0458:003A.0001: input,hidraw0: USB HID v1.10 Mouse [Genius Optical Mouse] on usb-0000:00:1d.0-1.2/input0
[    1.616179] usb 8-1.3: new low-speed USB device number 4 using ehci-pci
[    1.717042] usb 8-1.3: New USB device found, idVendor=03f0, idProduct=0024
[    1.717044] usb 8-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.717045] usb 8-1.3: Product: HP Basic USB Keyboard
[    1.717046] usb 8-1.3: Manufacturer: CHICONY
[    1.721924] input: CHICONY HP Basic USB Keyboard as /devices/pci0000:00/0000:00:1d.0/usb8/8-1/8-1.3/8-1.3:1.0/0003:03F0:0024.0002/input/input6
[    1.776399] hid-generic 0003:03F0:0024.0002: input,hidraw1: USB HID v1.10 Keyboard [CHICONY HP Basic USB Keyboard] on usb-0000:00:1d.0-1.3/input0
[    1.796074] ata16: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.796571] ata16.00: configured for UDMA/66
[    1.796722] ata16: EH complete
[    1.796956] scsi 15:0:0:0: Attached scsi generic sg2 type 3
[    2.192859] scsi 16:0:0:0: Direct-Access     HP       External HDD     2002 PQ: 0 ANSI: 4
[    2.193491] scsi 16:0:0:1: CD-ROM            HP       Virtual CD 4607  2002 PQ: 0 ANSI: 4
[    2.196272] sd 16:0:0:0: Attached scsi generic sg3 type 0
[    2.196635] sd 16:0:0:0: [sdb] 3905656832 512-byte logical blocks: (1.99 TB/1.81 TiB)
[    2.198170] sd 16:0:0:0: [sdb] Write Protect is off
[    2.198173] sd 16:0:0:0: [sdb] Mode Sense: 23 00 10 00
[    2.199398] sr 16:0:0:1: [sr1] scsi3-mmc drive: 51x/51x caddy
[    2.199541] sr 16:0:0:1: Attached scsi CD-ROM sr1
[    2.199621] sr 16:0:0:1: Attached scsi generic sg4 type 5
[    2.200865] sd 16:0:0:0: [sdb] No Caching mode page found
[    2.200917] sd 16:0:0:0: [sdb] Assuming drive cache: write through
[    2.205781]  sdb: sdb1
[    2.210040] sd 16:0:0:0: [sdb] Attached SCSI disk
[    2.485770] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    2.485772] EXT4-fs (sda1): write access will be enabled during recovery
[    2.751213] random: nonblocking pool is initialized
[    4.424297] EXT4-fs (sda1): recovery complete
[    4.427847] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    6.477753] init: plymouth-upstart-bridge main process (294) terminated with status 1
[    6.477760] init: plymouth-upstart-bridge main process ended, respawning
[    6.478927] init: plymouth-upstart-bridge main process (307) terminated with status 1
[    6.478933] init: plymouth-upstart-bridge main process ended, respawning
[    6.479896] init: plymouth-upstart-bridge main process (309) terminated with status 1
[    6.479902] init: plymouth-upstart-bridge main process ended, respawning
[    6.481041] init: plymouth-upstart-bridge main process (310) terminated with status 1
[    6.481048] init: plymouth-upstart-bridge main process ended, respawning
[    6.481946] init: plymouth-upstart-bridge main process (312) terminated with status 1
[    6.481952] init: plymouth-upstart-bridge main process ended, respawning
[    6.483030] init: plymouth-upstart-bridge main process (313) terminated with status 1
[    6.483036] init: plymouth-upstart-bridge main process ended, respawning
[    6.484040] init: plymouth-upstart-bridge main process (315) terminated with status 1
[    6.484046] init: plymouth-upstart-bridge main process ended, respawning
[    6.485084] init: plymouth-upstart-bridge main process (316) terminated with status 1
[    6.485090] init: plymouth-upstart-bridge main process ended, respawning
[    6.485968] init: plymouth-upstart-bridge main process (318) terminated with status 1
[    6.485973] init: plymouth-upstart-bridge main process ended, respawning
[    6.487020] init: plymouth-upstart-bridge main process (319) terminated with status 1
[    6.487026] init: plymouth-upstart-bridge main process ended, respawning
[    6.487811] init: plymouth-upstart-bridge main process (321) terminated with status 1
[    6.487817] init: plymouth-upstart-bridge respawning too fast, stopped
[    6.614228] init: ureadahead main process (297) terminated with status 5
[    8.014239] Adding 19529724k swap on /dev/sda5.  Priority:-1 extents:1 across:19529724k FS
[    8.998518] systemd-udevd[422]: starting version 204
[   11.208021] lp: driver loaded but no devices found
[   11.316462] ppdev: user-space parallel port driver
[   13.241501] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   13.763189] wmi: Mapper loaded
[   13.980728] EDAC MC: Ver: 3.0.0
[   14.075019] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   14.078362] EDAC sbridge: Seeking for: PCI ID 8086:3ca0
[   14.078371] EDAC sbridge: Seeking for: PCI ID 8086:3ca0
[   14.078374] EDAC sbridge: Seeking for: PCI ID 8086:3ca8
[   14.078379] EDAC sbridge: Seeking for: PCI ID 8086:3ca8
[   14.078380] EDAC sbridge: Seeking for: PCI ID 8086:3c71
[   14.078384] EDAC sbridge: Seeking for: PCI ID 8086:3c71
[   14.078386] EDAC sbridge: Seeking for: PCI ID 8086:3caa
[   14.078390] EDAC sbridge: Seeking for: PCI ID 8086:3caa
[   14.078392] EDAC sbridge: Seeking for: PCI ID 8086:3cab
[   14.078396] EDAC sbridge: Seeking for: PCI ID 8086:3cab
[   14.078397] EDAC sbridge: Seeking for: PCI ID 8086:3cac
[   14.078401] EDAC sbridge: Seeking for: PCI ID 8086:3cac
[   14.078403] EDAC sbridge: Seeking for: PCI ID 8086:3cad
[   14.078407] EDAC sbridge: Seeking for: PCI ID 8086:3cad
[   14.078409] EDAC sbridge: Seeking for: PCI ID 8086:3cb8
[   14.078413] EDAC sbridge: Seeking for: PCI ID 8086:3cb8
[   14.078414] EDAC sbridge: Seeking for: PCI ID 8086:3cf4
[   14.078417] EDAC sbridge: Seeking for: PCI ID 8086:3cf4
[   14.078420] EDAC sbridge: Seeking for: PCI ID 8086:3cf6
[   14.078424] EDAC sbridge: Seeking for: PCI ID 8086:3cf6
[   14.078426] EDAC sbridge: Seeking for: PCI ID 8086:3cf5
[   14.078429] EDAC sbridge: Seeking for: PCI ID 8086:3cf5
[   14.078434] EDAC sbridge: ECC is disabled. Aborting
[   14.078484] EDAC sbridge: Couldn't find mci handler
[   14.259363] device-mapper: multipath: version 1.9.0 loaded
[   14.490111] WARNING! power/level is deprecated; use power/control instead
[   15.218976] AVX version of gcm_enc/dec engaged.
[   15.218978] AES CTR mode by8 optimization enabled
[   15.251322] [drm] Initialized drm 1.1.0 20060810
[   16.192743] snd_hda_intel 0000:01:00.1: Disabling MSI
[   16.192753] snd_hda_intel 0000:01:00.1: Handle VGA-switcheroo audio client
[   16.275757] snd_hda_codec_realtek hdaudioC0D0: autoconfig for ALC892: line_outs=4 (0x14/0x15/0x16/0x17/0x0) type:line
[   16.275760] snd_hda_codec_realtek hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   16.275761] snd_hda_codec_realtek hdaudioC0D0:    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[   16.275762] snd_hda_codec_realtek hdaudioC0D0:    mono: mono_out=0x0
[   16.275763] snd_hda_codec_realtek hdaudioC0D0:    dig-out=0x11/0x1e
[   16.275764] snd_hda_codec_realtek hdaudioC0D0:    inputs:
[   16.275766] snd_hda_codec_realtek hdaudioC0D0:      Front Mic=0x19
[   16.275767] snd_hda_codec_realtek hdaudioC0D0:      Rear Mic=0x18
[   16.275768] snd_hda_codec_realtek hdaudioC0D0:      Line=0x1a
[   16.288814] input: HDA Intel PCH Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   16.289400] input: HDA Intel PCH Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   16.289454] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   16.289501] input: HDA Intel PCH Line Out Front as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   16.289550] input: HDA Intel PCH Line Out Surround as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   16.289597] input: HDA Intel PCH Line Out CLFE as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   16.289639] input: HDA Intel PCH Line Out Side as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   16.289682] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[   16.397152] asus_wmi: ASUS WMI generic driver loaded
[   16.527450] asus_wmi: Initialization: 0x0
[   16.527474] asus_wmi: BIOS WMI version: 0.9
[   16.527515] asus_wmi: SFUN value: 0x0
[   16.527766] input: Eee PC WMI hotkeys as /devices/platform/eeepc-wmi/input/input15
[   16.528230] asus_wmi: Disabling ACPI video driver
[   17.889690] intel_rapl: Found RAPL domain package
[   17.889694] intel_rapl: Found RAPL domain core
[   18.028945] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input16
[   18.029027] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input17
[   18.029180] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input18
[   18.029257] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input19
[   18.630832] audit: type=1400 audit(1449218232.385:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=743 comm="apparmor_parser"
[   18.630836] audit: type=1400 audit(1449218232.385:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=743 comm="apparmor_parser"
[   18.630838] audit: type=1400 audit(1449218232.385:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=743 comm="apparmor_parser"
[   18.630845] audit: type=1400 audit(1449218232.385:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=548 comm="apparmor_parser"
[   18.630849] audit: type=1400 audit(1449218232.385:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=548 comm="apparmor_parser"
[   18.630851] audit: type=1400 audit(1449218232.385:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=548 comm="apparmor_parser"
[   18.631072] audit: type=1400 audit(1449218232.385:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=743 comm="apparmor_parser"
[   18.631075] audit: type=1400 audit(1449218232.385:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=743 comm="apparmor_parser"
[   18.631085] audit: type=1400 audit(1449218232.385:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=548 comm="apparmor_parser"
[   18.631087] audit: type=1400 audit(1449218232.385:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=548 comm="apparmor_parser"
[   20.649923] init: failsafe main process (842) killed by TERM signal
[   21.252559] nvidia: module license 'NVIDIA' taints kernel.
[   21.252561] Disabling lock debugging due to kernel taint
[   21.254560] nvidia: module verification failed: signature and/or required key missing - tainting kernel
[   21.257715] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   21.257889] [drm] Initialized nvidia-drm 0.0.0 20150116 for 0000:01:00.0 on minor 0
[   21.257899] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  352.63  Sat Nov  7 21:25:42 PST 2015
[   23.442330] Bluetooth: Core ver 2.20
[   23.442341] NET: Registered protocol family 31
[   23.442342] Bluetooth: HCI device and connection manager initialized
[   23.442345] Bluetooth: HCI socket layer initialized
[   23.442346] Bluetooth: L2CAP socket layer initialized
[   23.442351] Bluetooth: SCO socket layer initialized
[   23.696529] Bluetooth: RFCOMM TTY layer initialized
[   23.696538] Bluetooth: RFCOMM socket layer initialized
[   23.696541] Bluetooth: RFCOMM ver 1.11
[   23.782727] audit_printk_skb: 45 callbacks suppressed
[   23.782729] audit: type=1400 audit(1449218237.537:27): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1004 comm="apparmor_parser"
[   23.799422] audit: type=1400 audit(1449218237.553:28): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=1000 comm="apparmor_parser"
[   23.799426] audit: type=1400 audit(1449218237.553:29): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=1000 comm="apparmor_parser"
[   23.799429] audit: type=1400 audit(1449218237.553:30): apparmor="STATUS" operation="profile_load" name="pxgsettings" pid=1000 comm="apparmor_parser"
[   23.799430] audit: type=1400 audit(1449218237.553:31): apparmor="STATUS" operation="profile_load" name="sanitized_helper" pid=1000 comm="apparmor_parser"
[   23.799432] audit: type=1400 audit(1449218237.553:32): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-ofono" pid=1000 comm="apparmor_parser"
[   23.799991] audit: type=1400 audit(1449218237.553:33): apparmor="STATUS" operation="profile_replace" name="/usr/lib/telepathy/telepathy-*" pid=1000 comm="apparmor_parser"
[   23.808035] audit: type=1400 audit(1449218237.565:34): apparmor="STATUS" operation="profile_replace" name="pxgsettings" pid=1000 comm="apparmor_parser"
[   23.808039] audit: type=1400 audit(1449218237.565:35): apparmor="STATUS" operation="profile_replace" name="sanitized_helper" pid=1000 comm="apparmor_parser"
[   23.808041] audit: type=1400 audit(1449218237.565:36): apparmor="STATUS" operation="profile_replace" name="/usr/lib/telepathy/telepathy-ofono" pid=1000 comm="apparmor_parser"
[   23.895250] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   23.895252] Bluetooth: BNEP filters: protocol multicast
[   23.895256] Bluetooth: BNEP socket layer initialized
[   24.766758] init: cups main process (1018) killed by HUP signal
[   24.766766] init: cups main process ended, respawning
[   29.653476] init: Failed to spawn amd-config main process: unable to execute: No such file or directory
[   29.702193] init: gdm main process (1385) killed by TERM signal
[   31.220103] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   34.113969] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[   34.114001] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   43.132022] snd_hda_codec_hdmi hdaudioC1D1: HDMI: invalid ELD data byte 9
[   54.937713] audit_printk_skb: 93 callbacks suppressed
[   54.937716] audit: type=1400 audit(1449218268.690:68): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=2085 comm="apparmor_parser"
[   54.937719] audit: type=1400 audit(1449218268.690:69): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=2085 comm="apparmor_parser"
[   54.937959] audit: type=1400 audit(1449218268.690:70): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=2085 comm="apparmor_parser"
[  102.713516] ISO 9660 Extensions: Microsoft Joliet Level 1
[  103.164729] ISO 9660 Extensions: RRIP_1991A
[  103.164758] ISOFS: primary root directory is empty. Disabling Rock Ridge and switching to Joliet.
[  103.164759] ISOFS: changing to secondary root
[  104.913225] init: ureadahead-other main process (2927) terminated with status 2
[ 1441.348910] systemd-hostnamed[5234]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!



```
and bootchart map attached.[ATTACH=CONFIG]265934[/ATTACH]
(Here's a link to my bootchart map image: [http://pasteboard.co/2ClrF8vC.png](http://pasteboard.co/2ClrF8vC.png) )

---

### Post by TheFu on 2015-12-04
Did you look at the bootchart? 

mountall is eating most of the time. So, there's an issue with the disk subsystem. Look for failing hardware there - bad cable, failing HDD, bad SATA port(s). Unplug any USB storage devices too.

Everything else that is slow is probably related to the failing disk component.

Got backup religion?  I'd get it quick, if not.

---

