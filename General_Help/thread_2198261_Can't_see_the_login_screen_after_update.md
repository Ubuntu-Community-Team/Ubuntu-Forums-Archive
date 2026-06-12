---
title: "Can't see the login screen after update"
date: 2014-01-07
forum: General Help
---

### Post by zrzhu11 on 2014-01-07
i have ubuntu 12.04 on my computer, installed with Wubi. I installed a few updates from "update manager" last night. when I tried to boot into ubuntu, it shows black screen, not the normal login screen. I'm able to press shift key to log into "previous version". I attached a screenshot of my recent updates. Which one should I uninstalled in order to fix the problem. Thanks

[ATTACH=CONFIG]249313[/ATTACH]

syslog:
Jan  7 21:26:19 ubuntu kernel: imklog 5.8.6, log source = /proc/kmsg started.
Jan  7 21:26:19 ubuntu rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="707" x-info="http://www.rsyslog.com"] start
Jan  7 21:26:19 ubuntu rsyslogd: rsyslogd's groupid changed to 103
Jan  7 21:26:19 ubuntu rsyslogd: rsyslogd's userid changed to 101
Jan  7 21:26:19 ubuntu rsyslogd-2039: Could not open output pipe '/dev/xconsole' [try [http://www.rsyslog.com/e/2039](http://www.rsyslog.com/e/2039) ]
Jan  7 21:26:19 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpuset
Jan  7 21:26:19 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpu
Jan  7 21:26:19 ubuntu kernel: [    0.000000] Linux version 3.5.0-45-generic (buildd@allspice) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #68~precise1-Ubuntu SMP Wed Dec 4 16:19:28 UTC 2013 (Ubuntu 3.5.0-45.68~precise1-generic 3.5.7.26)
Jan  7 21:26:19 ubuntu kernel: [    0.000000] KERNEL supported cpus:
Jan  7 21:26:19 ubuntu kernel: [    0.000000]   Intel GenuineIntel
Jan  7 21:26:19 ubuntu kernel: [    0.000000]   AMD AuthenticAMD
Jan  7 21:26:19 ubuntu kernel: [    0.000000]   NSC Geode by NSC
Jan  7 21:26:19 ubuntu kernel: [    0.000000]   Cyrix CyrixInstead
Jan  7 21:26:19 ubuntu kernel: [    0.000000]   Centaur CentaurHauls
Jan  7 21:26:19 ubuntu kernel: [    0.000000]   Transmeta GenuineTMx86
Jan  7 21:26:19 ubuntu kernel: [    0.000000]   Transmeta TransmetaCPU
Jan  7 21:26:19 ubuntu kernel: [    0.000000]   UMC UMC UMC UMC
Jan  7 21:26:19 ubuntu kernel: [    0.000000] Disabled fast string operations
Jan  7 21:26:19 ubuntu kernel: [    0.000000] e820: BIOS-provided physical RAM map:
Jan  7 21:26:19 ubuntu kernel: [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009efff] usable
Jan  7 21:26:19 ubuntu kernel: [    0.000000] BIOS-e820: [mem 0x000000000009f000-0x000000000009ffff] reserved
Jan  7 21:26:19 ubuntu kernel: [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000bfed33ff] usable
Jan  7 21:26:19 ubuntu kernel: [    0.000000] BIOS-e820: [mem 0x00000000bfed3400-0x00000000bfffffff] reserved
Jan  7 21:26:19 ubuntu kernel: [    0.000000] BIOS-e820: [mem 0x00000000f0000000-0x00000000f4006fff] reserved
Jan  7 21:26:19 ubuntu kernel: [    0.000000] BIOS-e820: [mem 0x00000000f4008000-0x00000000f400bfff] reserved
Jan  7 21:26:19 ubuntu kernel: [    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec0ffff] reserved
Jan  7 21:26:19 ubuntu kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed20000-0x00000000fed9ffff] reserved
Jan  7 21:26:19 ubuntu kernel: [    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee0ffff] reserved
Jan  7 21:26:19 ubuntu kernel: [    0.000000] BIOS-e820: [mem 0x00000000ffb00000-0x00000000ffffffff] reserved
Jan  7 21:26:19 ubuntu kernel: [    0.000000] NX (Execute Disable) protection: active
Jan  7 21:26:19 ubuntu kernel: [    0.000000] SMBIOS 2.4 present.
Jan  7 21:26:19 ubuntu kernel: [    0.000000] DMI: Dell Inc. MM061                           /0XD720, BIOS A17 06/13/2007
Jan  7 21:26:19 ubuntu kernel: [    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
Jan  7 21:26:19 ubuntu kernel: [    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
Jan  7 21:26:19 ubuntu kernel: [    0.000000] e820: last_pfn = 0xbfed3 max_arch_pfn = 0x1000000
Jan  7 21:26:19 ubuntu kernel: [    0.000000] MTRR default type: uncachable
Jan  7 21:26:19 ubuntu kernel: [    0.000000] MTRR fixed ranges enabled:
Jan  7 21:26:19 ubuntu kernel: [    0.000000]   00000-9FFFF write-back
Jan  7 21:26:19 ubuntu kernel: [    0.000000]   A0000-BFFFF uncachable
Jan  7 21:26:19 ubuntu kernel: [    0.000000]   C0000-CFFFF write-protect
Jan  7 21:26:19 ubuntu kernel: [    0.000000]   D0000-EFFFF uncachable
Jan  7 21:26:19 ubuntu kernel: [    0.000000]   F0000-FFFFF write-protect
Jan  7 21:26:19 ubuntu kernel: [    0.000000] MTRR variable ranges enabled:
Jan  7 21:26:19 ubuntu kernel: [    0.000000]   0 base 000000000 mask F80000000 write-back
Jan  7 21:26:19 ubuntu kernel: [    0.000000]   1 base 080000000 mask FC0000000 write-back
Jan  7 21:26:19 ubuntu kernel: [    0.000000]   2 base 0BFF00000 mask FFFF00000 uncachable
Jan  7 21:26:19 ubuntu kernel: [    0.000000]   3 disabled
Jan  7 21:26:19 ubuntu kernel: [    0.000000]   4 disabled
Jan  7 21:26:19 ubuntu kernel: [    0.000000]   5 disabled
Jan  7 21:26:19 ubuntu kernel: [    0.000000]   6 disabled
Jan  7 21:26:19 ubuntu kernel: [    0.000000]   7 disabled
Jan  7 21:26:19 ubuntu kernel: [    0.000000] PAT not supported by CPU.
Jan  7 21:26:19 ubuntu kernel: [    0.000000] original variable MTRRs
Jan  7 21:26:19 ubuntu kernel: [    0.000000] reg 0, base: 0GB, range: 2GB, type WB
Jan  7 21:26:19 ubuntu kernel: [    0.000000] reg 1, base: 2GB, range: 1GB, type WB
Jan  7 21:26:19 ubuntu kernel: [    0.000000] reg 2, base: 3071MB, range: 1MB, type UC
Jan  7 21:26:19 ubuntu kernel: [    0.000000] total RAM covered: 3071M
Jan  7 21:26:19 ubuntu kernel: [    0.000000] Found optimal setting for mtrr clean up
Jan  7 21:26:19 ubuntu kernel: [    0.000000]  gran_size: 64K 	chunk_size: 2M 	num_reg: 3  	lose cover RAM: 0G
Jan  7 21:26:19 ubuntu kernel: [    0.000000] New variable MTRRs
Jan  7 21:26:19 ubuntu kernel: [    0.000000] reg 0, base: 0GB, range: 2GB, type WB
Jan  7 21:26:19 ubuntu kernel: [    0.000000] reg 1, base: 2GB, range: 1GB, type WB
Jan  7 21:26:19 ubuntu kernel: [    0.000000] reg 2, base: 3071MB, range: 1MB, type UC
Jan  7 21:26:19 ubuntu kernel: [    0.000000] initial memory mapped: [mem 0x00000000-0x01ffffff]
Jan  7 21:26:19 ubuntu kernel: [    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
Jan  7 21:26:19 ubuntu kernel: [    0.000000] init_memory_mapping: [mem 0x00000000-0x37bfdfff]
Jan  7 21:26:19 ubuntu kernel: [    0.000000]  [mem 0x00000000-0x001fffff] page 4k
Jan  7 21:26:19 ubuntu kernel: [    0.000000]  [mem 0x00200000-0x379fffff] page 2M
Jan  7 21:26:19 ubuntu kernel: [    0.000000]  [mem 0x37a00000-0x37bfdfff] page 4k
Jan  7 21:26:19 ubuntu kernel: [    0.000000] kernel direct mapping tables up to 0x37bfdfff @ [mem 0x01ffa000-0x01ffffff]
Jan  7 21:26:19 ubuntu kernel: [    0.000000] RAMDISK: [mem 0x36248000-0x3711bfff]
Jan  7 21:26:19 ubuntu kernel: [    0.000000] ACPI: RSDP 000fc1d0 00014 (v00 DELL  )
Jan  7 21:26:19 ubuntu kernel: [    0.000000] ACPI: RSDT bfed39cd 00040 (v01 DELL    M07     27D7060D ASL  00000061)
Jan  7 21:26:19 ubuntu kernel: [    0.000000] ACPI: FACP bfed4800 00074 (v01 DELL    M07     27D7060D ASL  00000061)
Jan  7 21:26:19 ubuntu kernel: [    0.000000] ACPI: DSDT bfed5400 04766 (v01 INT430 SYSFexxx 00001001 INTL 20050624)
Jan  7 21:26:19 ubuntu kernel: [    0.000000] ACPI: FACS bfee3c00 00040
Jan  7 21:26:19 ubuntu kernel: [    0.000000] ACPI: HPET bfed4f00 00038 (v01 DELL    M07     00000001 ASL  00000061)
Jan  7 21:26:19 ubuntu kernel: [    0.000000] ACPI: APIC bfed5000 00068 (v01 DELL    M07     27D7060D ASL  00000047)
Jan  7 21:26:19 ubuntu kernel: [    0.000000] ACPI: MCFG bfed4fc0 0003E (v16 DELL    M07     27D7060D ASL  00000061)
Jan  7 21:26:19 ubuntu kernel: [    0.000000] ACPI: SLIC bfed509c 00176 (v01 DELL    M07     27D7060D ASL  00000061)
Jan  7 21:26:19 ubuntu kernel: [    0.000000] ACPI: BOOT bfed4bc0 00028 (v01 DELL    M07     27D7060D ASL  00000061)
Jan  7 21:26:19 ubuntu kernel: [    0.000000] ACPI: SSDT bfed3a0d 004DC (v01  PmRef    CpuPm 00003000 INTL 20050624)
Jan  7 21:26:19 ubuntu kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jan  7 21:26:19 ubuntu kernel: [    0.000000] 2178MB HIGHMEM available.
Jan  7 21:26:19 ubuntu kernel: [    0.000000] 891MB LOWMEM available.
Jan  7 21:26:19 ubuntu kernel: [    0.000000]   mapped low ram: 0 - 37bfe000
Jan  7 21:26:19 ubuntu kernel: [    0.000000]   low ram: 0 - 37bfe000
Jan  7 21:26:19 ubuntu kernel: [    0.000000] Zone ranges:
Jan  7 21:26:19 ubuntu kernel: [    0.000000]   DMA      [mem 0x00010000-0x00ffffff]
Jan  7 21:26:19 ubuntu kernel: [    0.000000]   Normal   [mem 0x01000000-0x37bfdfff]
Jan  7 21:26:19 ubuntu kernel: [    0.000000]   HighMem  [mem 0x37bfe000-0xbfed2fff]
Jan  7 21:26:19 ubuntu kernel: [    0.000000] Movable zone start for each node
Jan  7 21:26:19 ubuntu kernel: [    0.000000] Early memory node ranges
Jan  7 21:26:19 ubuntu kernel: [    0.000000]   node   0: [mem 0x00010000-0x0009efff]
Jan  7 21:26:19 ubuntu kernel: [    0.000000]   node   0: [mem 0x00100000-0xbfed2fff]
Jan  7 21:26:19 ubuntu kernel: [    0.000000] On node 0 totalpages: 786018
Jan  7 21:26:19 ubuntu kernel: [    0.000000] free_area_init_node: node 0, pgdat c18c85c0, node_mem_map f4a48200
Jan  7 21:26:19 ubuntu kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Jan  7 21:26:19 ubuntu kernel: [    0.000000]   DMA zone: 0 pages reserved
Jan  7 21:26:19 ubuntu kernel: [    0.000000]   DMA zone: 3951 pages, LIFO batch:0
Jan  7 21:26:19 ubuntu kernel: [    0.000000]   Normal zone: 1752 pages used for memmap
Jan  7 21:26:19 ubuntu kernel: [    0.000000]   Normal zone: 222502 pages, LIFO batch:31
Jan  7 21:26:19 ubuntu kernel: [    0.000000]   HighMem zone: 4358 pages used for memmap
Jan  7 21:26:19 ubuntu kernel: [    0.000000]   HighMem zone: 553423 pages, LIFO batch:31
Jan  7 21:26:19 ubuntu kernel: [    0.000000] Using APIC driver default
Jan  7 21:26:19 ubuntu kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Jan  7 21:26:19 ubuntu kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jan  7 21:26:19 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jan  7 21:26:19 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Jan  7 21:26:19 ubuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Jan  7 21:26:19 ubuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Jan  7 21:26:19 ubuntu kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Jan  7 21:26:19 ubuntu kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Jan  7 21:26:19 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jan  7 21:26:19 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jan  7 21:26:19 ubuntu kernel: [    0.000000] ACPI: IRQ0 used by override.
Jan  7 21:26:19 ubuntu kernel: [    0.000000] ACPI: IRQ2 used by override.
Jan  7 21:26:19 ubuntu kernel: [    0.000000] ACPI: IRQ9 used by override.
Jan  7 21:26:19 ubuntu kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jan  7 21:26:19 ubuntu kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Jan  7 21:26:19 ubuntu kernel: [    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
Jan  7 21:26:19 ubuntu kernel: [    0.000000] nr_irqs_gsi: 40
Jan  7 21:26:19 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jan  7 21:26:19 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 0000000000100000
Jan  7 21:26:19 ubuntu kernel: [    0.000000] e820: [mem 0xc0000000-0xefffffff] available for PCI devices
Jan  7 21:26:19 ubuntu kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Jan  7 21:26:19 ubuntu kernel: [    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
Jan  7 21:26:19 ubuntu kernel: [    0.000000] PERCPU: Embedded 14 pages/cpu @f7bcf000 s34176 r0 d23168 u57344
Jan  7 21:26:19 ubuntu kernel: [    0.000000] pcpu-alloc: s34176 r0 d23168 u57344 alloc=14*4096
Jan  7 21:26:19 ubuntu kernel: [    0.000000] pcpu-alloc: [0] 0 [0] 1 
Jan  7 21:26:19 ubuntu kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 779876
Jan  7 21:26:19 ubuntu kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-45-generic root=UUID=00D2D857D2D85290 loop=/ubuntu/disks/root.disk ro quiet splash vt.handoff=7
Jan  7 21:26:19 ubuntu kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Jan  7 21:26:19 ubuntu kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Jan  7 21:26:19 ubuntu kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Jan  7 21:26:19 ubuntu kernel: [    0.000000] __ex_table already sorted, skipping sort
Jan  7 21:26:19 ubuntu kernel: [    0.000000] Initializing CPU#0
Jan  7 21:26:19 ubuntu kernel: [    0.000000] allocated 6288920 bytes of page_cgroup
Jan  7 21:26:19 ubuntu kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Jan  7 21:26:19 ubuntu kernel: [    0.000000] Initializing HighMem for node 0 (00037bfe:000bfed3)
Jan  7 21:26:19 ubuntu kernel: [    0.000000] Memory: 3086404k/3144524k available (6061k kernel code, 57668k reserved, 2983k data, 764k init, 2231124k highmem)
Jan  7 21:26:19 ubuntu kernel: [    0.000000] virtual kernel memory layout:
Jan  7 21:26:19 ubuntu kernel: [    0.000000]     fixmap  : 0xfff15000 - 0xfffff000   ( 936 kB)
Jan  7 21:26:19 ubuntu kernel: [    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
Jan  7 21:26:19 ubuntu kernel: [    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
Jan  7 21:26:19 ubuntu kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
Jan  7 21:26:19 ubuntu kernel: [    0.000000]       .init : 0xc18d6000 - 0xc1995000   ( 764 kB)
Jan  7 21:26:19 ubuntu kernel: [    0.000000]       .data : 0xc15eb595 - 0xc18d54c0   (2983 kB)
Jan  7 21:26:19 ubuntu kernel: [    0.000000]       .text : 0xc1000000 - 0xc15eb595   (6061 kB)
Jan  7 21:26:19 ubuntu kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Jan  7 21:26:19 ubuntu kernel: [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Jan  7 21:26:19 ubuntu kernel: [    0.000000] Hierarchical RCU implementation.
Jan  7 21:26:19 ubuntu kernel: [    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
Jan  7 21:26:19 ubuntu kernel: [    0.000000] NR_IRQS:2304 nr_irqs:512 16
Jan  7 21:26:19 ubuntu kernel: [    0.000000] CPU 0 irqstacks, hard=f4408000 soft=f440a000
Jan  7 21:26:19 ubuntu kernel: [    0.000000] vt handoff: transparent VT on vt#7
Jan  7 21:26:19 ubuntu kernel: [    0.000000] Console: colour dummy device 80x25
Jan  7 21:26:19 ubuntu kernel: [    0.000000] console [tty0] enabled
Jan  7 21:26:19 ubuntu kernel: [    0.000000] hpet clockevent registered
Jan  7 21:26:19 ubuntu kernel: [    0.000000] Fast TSC calibration using PIT
Jan  7 21:26:19 ubuntu kernel: [    0.000000] Detected 1728.983 MHz processor.
Jan  7 21:26:19 ubuntu kernel: [    0.004002] Calibrating delay loop (skipped), value calculated using timer frequency.. 3457.96 BogoMIPS (lpj=6915932)
Jan  7 21:26:19 ubuntu kernel: [    0.004008] pid_max: default: 32768 minimum: 301
Jan  7 21:26:19 ubuntu kernel: [    0.004041] Security Framework initialized
Jan  7 21:26:19 ubuntu kernel: [    0.004063] AppArmor: AppArmor initialized
Jan  7 21:26:19 ubuntu kernel: [    0.004065] Yama: becoming mindful.
Jan  7 21:26:19 ubuntu kernel: [    0.004166] Mount-cache hash table entries: 512
Jan  7 21:26:19 ubuntu kernel: [    0.004527] Initializing cgroup subsys cpuacct
Jan  7 21:26:19 ubuntu kernel: [    0.004532] Initializing cgroup subsys memory
Jan  7 21:26:19 ubuntu kernel: [    0.004546] Initializing cgroup subsys devices
Jan  7 21:26:19 ubuntu kernel: [    0.004549] Initializing cgroup subsys freezer
Jan  7 21:26:19 ubuntu kernel: [    0.004552] Initializing cgroup subsys blkio
Jan  7 21:26:19 ubuntu kernel: [    0.004556] Initializing cgroup subsys perf_event
Jan  7 21:26:19 ubuntu kernel: [    0.004595] Disabled fast string operations
Jan  7 21:26:19 ubuntu kernel: [    0.004602] CPU: Physical Processor ID: 0
Jan  7 21:26:19 ubuntu kernel: [    0.004604] CPU: Processor Core ID: 0
Jan  7 21:26:19 ubuntu kernel: [    0.004609] mce: CPU supports 6 MCE banks
Jan  7 21:26:19 ubuntu kernel: [    0.004620] CPU0: Thermal monitoring enabled (TM2)
Jan  7 21:26:19 ubuntu kernel: [    0.004625] using mwait in idle threads.
Jan  7 21:26:19 ubuntu kernel: [    0.010188] ACPI: Core revision 20120320
Jan  7 21:26:19 ubuntu kernel: [    0.015096] ftrace: allocating 27163 entries in 54 pages
Jan  7 21:26:19 ubuntu kernel: [    0.028094] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Jan  7 21:26:19 ubuntu kernel: [    0.028578] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Jan  7 21:26:19 ubuntu kernel: [    0.069434] CPU0: Genuine Intel(R) CPU           T2080  @ 1.73GHz stepping 0c
Jan  7 21:26:19 ubuntu kernel: [    0.072003] Performance Events: Core events, core PMU driver.
Jan  7 21:26:19 ubuntu kernel: [    0.072003] ... version:                1
Jan  7 21:26:19 ubuntu kernel: [    0.072003] ... bit width:              40
Jan  7 21:26:19 ubuntu kernel: [    0.072003] ... generic registers:      2
Jan  7 21:26:19 ubuntu kernel: [    0.072003] ... value mask:             000000ffffffffff
Jan  7 21:26:19 ubuntu kernel: [    0.072003] ... max period:             000000007fffffff
Jan  7 21:26:19 ubuntu kernel: [    0.072003] ... fixed-purpose events:   0
Jan  7 21:26:19 ubuntu kernel: [    0.072003] ... event mask:             0000000000000003
Jan  7 21:26:19 ubuntu kernel: [    0.072003] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
Jan  7 21:26:19 ubuntu kernel: [    0.072003] CPU 1 irqstacks, hard=f44c8000 soft=f44ca000
Jan  7 21:26:19 ubuntu kernel: [    0.072003] Booting Node   0, Processors  #1 Ok.
Jan  7 21:26:19 ubuntu kernel: [    0.008000] Initializing CPU#1
Jan  7 21:26:19 ubuntu kernel: [    0.008000] Disabled fast string operations
Jan  7 21:26:19 ubuntu kernel: [    0.080004] TSC synchronization [CPU#0 -> CPU#1]:
Jan  7 21:26:19 ubuntu kernel: [    0.080004] Measured 3509174305 cycles TSC warp between CPUs, turning off TSC clock.
Jan  7 21:26:19 ubuntu kernel: [    0.080004] Marking TSC unstable due to check_tsc_sync_source failed
Jan  7 21:26:19 ubuntu kernel: [    0.080109] Brought up 2 CPUs
Jan  7 21:26:19 ubuntu kernel: [    0.080113] Total of 2 processors activated (6915.93 BogoMIPS).
Jan  7 21:26:19 ubuntu kernel: [    0.081229] devtmpfs: initialized
Jan  7 21:26:19 ubuntu kernel: [    0.081229] EVM: security.selinux
Jan  7 21:26:19 ubuntu kernel: [    0.081229] EVM: security.SMACK64
Jan  7 21:26:19 ubuntu kernel: [    0.081229] EVM: security.capability
Jan  7 21:26:19 ubuntu kernel: [    0.084869] dummy: 
Jan  7 21:26:19 ubuntu kernel: [    0.084917] RTC time: 21:25:29, date: 01/07/14
Jan  7 21:26:19 ubuntu kernel: [    0.084980] NET: Registered protocol family 16
Jan  7 21:26:19 ubuntu kernel: [    0.084996] Trying to unpack rootfs image as initramfs...
Jan  7 21:26:19 ubuntu kernel: [    0.085228] EISA bus registered
Jan  7 21:26:19 ubuntu kernel: [    0.085359] ACPI: bus type pci registered
Jan  7 21:26:19 ubuntu kernel: [    0.085460] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf0000000-0xf3ffffff] (base 0xf0000000)
Jan  7 21:26:19 ubuntu kernel: [    0.085465] PCI: MMCONFIG at [mem 0xf0000000-0xf3ffffff] reserved in E820
Jan  7 21:26:19 ubuntu kernel: [    0.085467] PCI: Using MMCONFIG for extended config space
Jan  7 21:26:19 ubuntu kernel: [    0.085470] PCI: Using configuration type 1 for base access
Jan  7 21:26:19 ubuntu kernel: [    0.085484] dmi type 0xB1 record - unknown flag
Jan  7 21:26:19 ubuntu kernel: [    0.100180] bio: create slab <bio-0> at 0
Jan  7 21:26:19 ubuntu kernel: [    0.100324] ACPI: Added _OSI(Module Device)
Jan  7 21:26:19 ubuntu kernel: [    0.100328] ACPI: Added _OSI(Processor Device)
Jan  7 21:26:19 ubuntu kernel: [    0.100331] ACPI: Added _OSI(3.0 _SCP Extensions)
Jan  7 21:26:19 ubuntu kernel: [    0.100335] ACPI: Added _OSI(Processor Aggregator Device)
Jan  7 21:26:19 ubuntu kernel: [    0.102006] ACPI: EC: Look up EC in DSDT
Jan  7 21:26:19 ubuntu kernel: [    0.108796] ACPI: SSDT bfed4134 00244 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
Jan  7 21:26:19 ubuntu kernel: [    0.109220] ACPI: Dynamic OEM Table Load:
Jan  7 21:26:19 ubuntu kernel: [    0.109225] ACPI: SSDT   (null) 00244 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
Jan  7 21:26:19 ubuntu kernel: [    0.109369] ACPI: SSDT bfed3ee9 001C6 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
Jan  7 21:26:19 ubuntu kernel: [    0.109765] ACPI: Dynamic OEM Table Load:
Jan  7 21:26:19 ubuntu kernel: [    0.109769] ACPI: SSDT   (null) 001C6 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
Jan  7 21:26:19 ubuntu kernel: [    0.110082] ACPI: SSDT bfed4378 000C4 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
Jan  7 21:26:19 ubuntu kernel: [    0.110491] ACPI: Dynamic OEM Table Load:
Jan  7 21:26:19 ubuntu kernel: [    0.110495] ACPI: SSDT   (null) 000C4 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
Jan  7 21:26:19 ubuntu kernel: [    0.110621] ACPI: SSDT bfed40af 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
Jan  7 21:26:19 ubuntu kernel: [    0.111018] ACPI: Dynamic OEM Table Load:
Jan  7 21:26:19 ubuntu kernel: [    0.111022] ACPI: SSDT   (null) 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
Jan  7 21:26:19 ubuntu kernel: [    0.111286] ACPI: Interpreter enabled
Jan  7 21:26:19 ubuntu kernel: [    0.111298] ACPI: (supports S0 S3 S4 S5)
Jan  7 21:26:19 ubuntu kernel: [    0.111326] ACPI: Using IOAPIC for interrupt routing
Jan  7 21:26:19 ubuntu kernel: [    0.136594] ACPI: No dock devices found.
Jan  7 21:26:19 ubuntu kernel: [    0.136609] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
Jan  7 21:26:19 ubuntu kernel: [    0.144447] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Jan  7 21:26:19 ubuntu kernel: [    0.158785] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
Jan  7 21:26:19 ubuntu kernel: [    0.158792] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
Jan  7 21:26:19 ubuntu kernel: [    0.158796] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
Jan  7 21:26:19 ubuntu kernel: [    0.158800] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff] (ignored)
Jan  7 21:26:19 ubuntu kernel: [    0.158804] pci_root PNP0A03:00: host bridge window [mem 0xc0000000-0xefffffff] (ignored)
Jan  7 21:26:19 ubuntu kernel: [    0.158808] pci_root PNP0A03:00: host bridge window [mem 0xf4007000-0xf4007fff] (ignored)
Jan  7 21:26:19 ubuntu kernel: [    0.158812] pci_root PNP0A03:00: host bridge window [mem 0xf400c000-0xfebfffff] (ignored)
Jan  7 21:26:19 ubuntu kernel: [    0.158816] pci_root PNP0A03:00: host bridge window [mem 0xfec10000-0xfecfffff] (ignored)
Jan  7 21:26:19 ubuntu kernel: [    0.158820] pci_root PNP0A03:00: host bridge window [mem 0xfed00400-0xfed1ffff] (ignored)
Jan  7 21:26:19 ubuntu kernel: [    0.158824] pci_root PNP0A03:00: host bridge window [mem 0xfee10000-0xffafffff] (ignored)
Jan  7 21:26:19 ubuntu kernel: [    0.158829] PCI: root bus 00: using default resources
Jan  7 21:26:19 ubuntu kernel: [    0.158911] PCI host bridge to bus 0000:00
Jan  7 21:26:19 ubuntu kernel: [    0.158916] pci_bus 0000:00: root bus resource [io  0x0000-0xffff]
Jan  7 21:26:19 ubuntu kernel: [    0.158920] pci_bus 0000:00: root bus resource [mem 0x00000000-0xffffffff]
Jan  7 21:26:19 ubuntu kernel: [    0.158937] pci 0000:00:00.0: [8086:27a0] type 00 class 0x060000
Jan  7 21:26:19 ubuntu kernel: [    0.159010] pci 0000:00:01.0: [8086:27a1] type 01 class 0x060400
Jan  7 21:26:19 ubuntu kernel: [    0.159076] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
Jan  7 21:26:19 ubuntu kernel: [    0.159158] pci 0000:00:1b.0: [8086:27d8] type 00 class 0x040300
Jan  7 21:26:19 ubuntu kernel: [    0.159187] pci 0000:00:1b.0: reg 10: [mem 0xefffc000-0xefffffff 64bit]
Jan  7 21:26:19 ubuntu kernel: [    0.159310] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Jan  7 21:26:19 ubuntu kernel: [    0.159349] pci 0000:00:1c.0: [8086:27d0] type 01 class 0x060400
Jan  7 21:26:19 ubuntu kernel: [    0.159479] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Jan  7 21:26:19 ubuntu kernel: [    0.159525] pci 0000:00:1c.3: [8086:27d6] type 01 class 0x060400
Jan  7 21:26:19 ubuntu kernel: [    0.159655] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
Jan  7 21:26:19 ubuntu kernel: [    0.159698] pci 0000:00:1d.0: [8086:27c8] type 00 class 0x0c0300
Jan  7 21:26:19 ubuntu kernel: [    0.159764] pci 0000:00:1d.0: reg 20: [io  0xbf80-0xbf9f]
Jan  7 21:26:19 ubuntu kernel: [    0.159815] pci 0000:00:1d.1: [8086:27c9] type 00 class 0x0c0300
Jan  7 21:26:19 ubuntu kernel: [    0.159882] pci 0000:00:1d.1: reg 20: [io  0xbf60-0xbf7f]
Jan  7 21:26:19 ubuntu kernel: [    0.159934] pci 0000:00:1d.2: [8086:27ca] type 00 class 0x0c0300
Jan  7 21:26:19 ubuntu kernel: [    0.160001] pci 0000:00:1d.2: reg 20: [io  0xbf40-0xbf5f]
Jan  7 21:26:19 ubuntu kernel: [    0.160067] pci 0000:00:1d.3: [8086:27cb] type 00 class 0x0c0300
Jan  7 21:26:19 ubuntu kernel: [    0.160133] pci 0000:00:1d.3: reg 20: [io  0xbf20-0xbf3f]
Jan  7 21:26:19 ubuntu kernel: [    0.160198] pci 0000:00:1d.7: [8086:27cc] type 00 class 0x0c0320
Jan  7 21:26:19 ubuntu kernel: [    0.160227] pci 0000:00:1d.7: reg 10: [mem 0xffa80000-0xffa803ff]
Jan  7 21:26:19 ubuntu kernel: [    0.160350] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Jan  7 21:26:19 ubuntu kernel: [    0.160382] pci 0000:00:1e.0: [8086:2448] type 01 class 0x060401
Jan  7 21:26:19 ubuntu kernel: [    0.160496] pci 0000:00:1f.0: [8086:27b9] type 00 class 0x060100
Jan  7 21:26:19 ubuntu kernel: [    0.160626] pci 0000:00:1f.0: quirk: [io  0x1000-0x107f] claimed by ICH6 ACPI/GPIO/TCO
Jan  7 21:26:19 ubuntu kernel: [    0.160634] pci 0000:00:1f.0: quirk: [io  0x1080-0x10bf] claimed by ICH6 GPIO
Jan  7 21:26:19 ubuntu kernel: [    0.160641] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0900 (mask 007f)
Jan  7 21:26:19 ubuntu kernel: [    0.160649] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 0c80 (mask 003f)
Jan  7 21:26:19 ubuntu kernel: [    0.160725] pci 0000:00:1f.2: [8086:27c4] type 00 class 0x010180
Jan  7 21:26:19 ubuntu kernel: [    0.160751] pci 0000:00:1f.2: reg 10: [io  0x01f0-0x01f7]
Jan  7 21:26:19 ubuntu kernel: [    0.160766] pci 0000:00:1f.2: reg 14: [io  0x03f4-0x03f7]
Jan  7 21:26:19 ubuntu kernel: [    0.160781] pci 0000:00:1f.2: reg 18: [io  0x0170-0x0177]
Jan  7 21:26:19 ubuntu kernel: [    0.160796] pci 0000:00:1f.2: reg 1c: [io  0x0374-0x0377]
Jan  7 21:26:19 ubuntu kernel: [    0.160811] pci 0000:00:1f.2: reg 20: [io  0xbfa0-0xbfaf]
Jan  7 21:26:19 ubuntu kernel: [    0.160879] pci 0000:00:1f.2: PME# supported from D3hot
Jan  7 21:26:19 ubuntu kernel: [    0.160905] pci 0000:00:1f.3: [8086:27da] type 00 class 0x0c0500
Jan  7 21:26:19 ubuntu kernel: [    0.160988] pci 0000:00:1f.3: reg 20: [io  0x10c0-0x10df]
Jan  7 21:26:19 ubuntu kernel: [    0.161107] pci 0000:01:00.0: [1002:7145] type 00 class 0x030000
Jan  7 21:26:19 ubuntu kernel: [    0.161126] pci 0000:01:00.0: reg 10: [mem 0xd0000000-0xdfffffff pref]
Jan  7 21:26:19 ubuntu kernel: [    0.161140] pci 0000:01:00.0: reg 14: [io  0xee00-0xeeff]
Jan  7 21:26:19 ubuntu kernel: [    0.161154] pci 0000:01:00.0: reg 18: [mem 0xefdf0000-0xefdfffff]
Jan  7 21:26:19 ubuntu kernel: [    0.161191] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
Jan  7 21:26:19 ubuntu kernel: [    0.161239] pci 0000:01:00.0: supports D1 D2
Jan  7 21:26:19 ubuntu kernel: [    0.161257] pci 0000:01:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
Jan  7 21:26:19 ubuntu kernel: [    0.161274] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Jan  7 21:26:19 ubuntu kernel: [    0.161280] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
Jan  7 21:26:19 ubuntu kernel: [    0.161285] pci 0000:00:01.0:   bridge window [mem 0xefd00000-0xefefffff]
Jan  7 21:26:19 ubuntu kernel: [    0.161292] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
Jan  7 21:26:19 ubuntu kernel: [    0.161441] pci 0000:0b:00.0: [14e4:4311] type 00 class 0x028000
Jan  7 21:26:19 ubuntu kernel: [    0.161511] pci 0000:0b:00.0: reg 10: [mem 0xefcfc000-0xefcfffff]
Jan  7 21:26:19 ubuntu kernel: [    0.162028] pci 0000:0b:00.0: supports D1 D2
Jan  7 21:26:19 ubuntu kernel: [    0.162115] pci 0000:0b:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
Jan  7 21:26:19 ubuntu kernel: [    0.162143] pci 0000:00:1c.0: PCI bridge to [bus 0b-0b]
Jan  7 21:26:19 ubuntu kernel: [    0.162153] pci 0000:00:1c.0:   bridge window [mem 0xefc00000-0xefcfffff]
Jan  7 21:26:19 ubuntu kernel: [    0.162232] pci 0000:00:1c.3: PCI bridge to [bus 0c-0d]
Jan  7 21:26:19 ubuntu kernel: [    0.162239] pci 0000:00:1c.3:   bridge window [io  0xd000-0xdfff]
Jan  7 21:26:19 ubuntu kernel: [    0.162247] pci 0000:00:1c.3:   bridge window [mem 0xefa00000-0xefbfffff]
Jan  7 21:26:19 ubuntu kernel: [    0.162257] pci 0000:00:1c.3:   bridge window [mem 0xe0000000-0xe01fffff 64bit pref]
Jan  7 21:26:19 ubuntu kernel: [    0.162313] pci 0000:03:00.0: [14e4:170c] type 00 class 0x020000
Jan  7 21:26:19 ubuntu kernel: [    0.162339] pci 0000:03:00.0: reg 10: [mem 0xef9fe000-0xef9fffff]
Jan  7 21:26:19 ubuntu kernel: [    0.162449] pci 0000:03:00.0: supports D1 D2
Jan  7 21:26:19 ubuntu kernel: [    0.162453] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Jan  7 21:26:19 ubuntu kernel: [    0.162482] pci 0000:03:01.0: [1180:0832] type 00 class 0x0c0010
Jan  7 21:26:19 ubuntu kernel: [    0.162502] pci 0000:03:01.0: proprietary Ricoh MMC controller disabled (via firewire function)
Jan  7 21:26:19 ubuntu kernel: [    0.162506] pci 0000:03:01.0: MMC cards are now supported by standard SDHCI controller
Jan  7 21:26:19 ubuntu kernel: [    0.162525] pci 0000:03:01.0: reg 10: [mem 0xef9fd800-0xef9fdfff]
Jan  7 21:26:19 ubuntu kernel: [    0.162639] pci 0000:03:01.0: supports D1 D2
Jan  7 21:26:19 ubuntu kernel: [    0.162643] pci 0000:03:01.0: PME# supported from D0 D1 D2 D3hot D3cold
Jan  7 21:26:19 ubuntu kernel: [    0.162672] pci 0000:03:01.1: [1180:0822] type 00 class 0x080501
Jan  7 21:26:19 ubuntu kernel: [    0.162699] pci 0000:03:01.1: reg 10: [mem 0xef9fd400-0xef9fd4ff]
Jan  7 21:26:19 ubuntu kernel: [    0.162814] pci 0000:03:01.1: supports D1 D2
Jan  7 21:26:19 ubuntu kernel: [    0.162817] pci 0000:03:01.1: PME# supported from D0 D1 D2 D3hot D3cold
Jan  7 21:26:19 ubuntu kernel: [    0.162848] pci 0000:03:01.2: [1180:0592] type 00 class 0x088000
Jan  7 21:26:19 ubuntu kernel: [    0.162874] pci 0000:03:01.2: reg 10: [mem 0xef9fd600-0xef9fd6ff]
Jan  7 21:26:19 ubuntu kernel: [    0.162987] pci 0000:03:01.2: supports D1 D2
Jan  7 21:26:19 ubuntu kernel: [    0.162990] pci 0000:03:01.2: PME# supported from D0 D1 D2 D3hot D3cold
Jan  7 21:26:19 ubuntu kernel: [    0.163020] pci 0000:03:01.3: [1180:0852] type 00 class 0x088000
Jan  7 21:26:19 ubuntu kernel: [    0.163046] pci 0000:03:01.3: reg 10: [mem 0xef9fd700-0xef9fd7ff]
Jan  7 21:26:19 ubuntu kernel: [    0.163160] pci 0000:03:01.3: supports D1 D2
Jan  7 21:26:19 ubuntu kernel: [    0.163164] pci 0000:03:01.3: PME# supported from D0 D1 D2 D3hot D3cold
Jan  7 21:26:19 ubuntu kernel: [    0.163251] pci 0000:00:1e.0: PCI bridge to [bus 03-03] (subtractive decode)
Jan  7 21:26:19 ubuntu kernel: [    0.163261] pci 0000:00:1e.0:   bridge window [mem 0xef900000-0xef9fffff]
Jan  7 21:26:19 ubuntu kernel: [    0.163272] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
Jan  7 21:26:19 ubuntu kernel: [    0.163276] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xffffffff] (subtractive decode)
Jan  7 21:26:19 ubuntu kernel: [    0.163307] pci_bus 0000:00: on NUMA node 0
Jan  7 21:26:19 ubuntu kernel: [    0.163317] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Jan  7 21:26:19 ubuntu kernel: [    0.163716] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
Jan  7 21:26:19 ubuntu kernel: [    0.163785] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
Jan  7 21:26:19 ubuntu kernel: [    0.163874] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
Jan  7 21:26:19 ubuntu kernel: [    0.163957] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
Jan  7 21:26:19 ubuntu kernel: [    0.164053]  pci0000:00: Requesting ACPI _OSC control (0x1d)
Jan  7 21:26:19 ubuntu kernel: [    0.164058]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
Jan  7 21:26:19 ubuntu kernel: [    0.164060] ACPI _OSC control for PCIe not granted, disabling ASPM
Jan  7 21:26:19 ubuntu kernel: [    0.173811] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 11) *4
Jan  7 21:26:19 ubuntu kernel: [    0.173916] ACPI: PCI Interrupt Link [LNKB] (IRQs *5 7)
Jan  7 21:26:19 ubuntu kernel: [    0.174011] ACPI: PCI Interrupt Link [LNKC] (IRQs *9 10 11)
Jan  7 21:26:19 ubuntu kernel: [    0.174107] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 11) *3
Jan  7 21:26:19 ubuntu kernel: [    0.174205] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Jan  7 21:26:19 ubuntu kernel: [    0.174307] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Jan  7 21:26:19 ubuntu kernel: [    0.174409] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
Jan  7 21:26:19 ubuntu kernel: [    0.174512] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
Jan  7 21:26:19 ubuntu kernel: [    0.174713] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Jan  7 21:26:19 ubuntu kernel: [    0.174723] vgaarb: loaded
Jan  7 21:26:19 ubuntu kernel: [    0.174725] vgaarb: bridge control possible 0000:01:00.0
Jan  7 21:26:19 ubuntu kernel: [    0.175058] SCSI subsystem initialized
Jan  7 21:26:19 ubuntu kernel: [    0.175145] libata version 3.00 loaded.
Jan  7 21:26:19 ubuntu kernel: [    0.175179] ACPI: bus type usb registered
Jan  7 21:26:19 ubuntu kernel: [    0.175215] usbcore: registered new interface driver usbfs
Jan  7 21:26:19 ubuntu kernel: [    0.175231] usbcore: registered new interface driver hub
Jan  7 21:26:19 ubuntu kernel: [    0.175270] usbcore: registered new device driver usb
Jan  7 21:26:19 ubuntu kernel: [    0.175416] PCI: Using ACPI for IRQ routing
Jan  7 21:26:19 ubuntu kernel: [    0.178170] PCI: pci_cache_line_size set to 64 bytes
Jan  7 21:26:19 ubuntu kernel: [    0.178305] e820: reserve RAM buffer [mem 0x0009f000-0x0009ffff]
Jan  7 21:26:19 ubuntu kernel: [    0.178310] e820: reserve RAM buffer [mem 0xbfed3400-0xbfffffff]
Jan  7 21:26:19 ubuntu kernel: [    0.178481] NetLabel: Initializing
Jan  7 21:26:19 ubuntu kernel: [    0.178484] NetLabel:  domain hash size = 128
Jan  7 21:26:19 ubuntu kernel: [    0.178487] NetLabel:  protocols = UNLABELED CIPSOv4
Jan  7 21:26:19 ubuntu kernel: [    0.178502] NetLabel:  unlabeled traffic allowed by default
Jan  7 21:26:19 ubuntu kernel: [    0.178684] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
Jan  7 21:26:19 ubuntu kernel: [    0.178692] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Jan  7 21:26:19 ubuntu kernel: [    0.178700] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
Jan  7 21:26:19 ubuntu kernel: [    0.184108] Switching to clocksource hpet
Jan  7 21:26:19 ubuntu kernel: [    0.198094] AppArmor: AppArmor Filesystem Enabled
Jan  7 21:26:19 ubuntu kernel: [    0.198141] pnp: PnP ACPI init
Jan  7 21:26:19 ubuntu kernel: [    0.198168] ACPI: bus type pnp registered
Jan  7 21:26:19 ubuntu kernel: [    0.209153] pnp 00:00: [mem 0x00000000-0x0009fbff]
Jan  7 21:26:19 ubuntu kernel: [    0.209160] pnp 00:00: [mem 0x0009fc00-0x0009ffff]
Jan  7 21:26:19 ubuntu kernel: [    0.209163] pnp 00:00: [mem 0x000c0000-0x000cffff]
Jan  7 21:26:19 ubuntu kernel: [    0.209167] pnp 00:00: [mem 0x000e0000-0x000fffff]
Jan  7 21:26:19 ubuntu kernel: [    0.209171] pnp 00:00: [mem 0x00100000-0xbfed33ff]
Jan  7 21:26:19 ubuntu kernel: [    0.209174] pnp 00:00: [mem 0xbfed3400-0xbfefffff]
Jan  7 21:26:19 ubuntu kernel: [    0.209178] pnp 00:00: [mem 0xbff00000-0xbfffffff]
Jan  7 21:26:19 ubuntu kernel: [    0.209182] pnp 00:00: [mem 0xffb00000-0xffffffff]
Jan  7 21:26:19 ubuntu kernel: [    0.209185] pnp 00:00: [mem 0xfec00000-0xfec0ffff]
Jan  7 21:26:19 ubuntu kernel: [    0.209189] pnp 00:00: [mem 0xfee00000-0xfee0ffff]
Jan  7 21:26:19 ubuntu kernel: [    0.209193] pnp 00:00: [mem 0xfed20000-0xfed9ffff]
Jan  7 21:26:19 ubuntu kernel: [    0.209196] pnp 00:00: [mem 0xffa80000-0xffa83fff]
Jan  7 21:26:19 ubuntu kernel: [    0.209200] pnp 00:00: [mem 0xf4000000-0xf4003fff]
Jan  7 21:26:19 ubuntu kernel: [    0.209203] pnp 00:00: [mem 0xf4004000-0xf4004fff]
Jan  7 21:26:19 ubuntu kernel: [    0.209207] pnp 00:00: [mem 0xf4005000-0xf4005fff]
Jan  7 21:26:19 ubuntu kernel: [    0.209211] pnp 00:00: [mem 0xf4006000-0xf4006fff]
Jan  7 21:26:19 ubuntu kernel: [    0.209214] pnp 00:00: [mem 0xf4008000-0xf400bfff]
Jan  7 21:26:19 ubuntu kernel: [    0.209218] pnp 00:00: [mem 0xf0000000-0xf3ffffff]
Jan  7 21:26:19 ubuntu kernel: [    0.209342] system 00:00: [mem 0x00000000-0x0009fbff] could not be reserved
Jan  7 21:26:19 ubuntu kernel: [    0.209347] system 00:00: [mem 0x0009fc00-0x0009ffff] could not be reserved
Jan  7 21:26:19 ubuntu kernel: [    0.209352] system 00:00: [mem 0x000c0000-0x000cffff] could not be reserved
Jan  7 21:26:19 ubuntu kernel: [    0.209356] system 00:00: [mem 0x000e0000-0x000fffff] could not be reserved
Jan  7 21:26:19 ubuntu kernel: [    0.209361] system 00:00: [mem 0x00100000-0xbfed33ff] could not be reserved
Jan  7 21:26:19 ubuntu kernel: [    0.209365] system 00:00: [mem 0xbfed3400-0xbfefffff] has been reserved
Jan  7 21:26:19 ubuntu kernel: [    0.209369] system 00:00: [mem 0xbff00000-0xbfffffff] has been reserved
Jan  7 21:26:19 ubuntu kernel: [    0.209374] system 00:00: [mem 0xffb00000-0xffffffff] has been reserved
Jan  7 21:26:19 ubuntu kernel: [    0.209379] system 00:00: [mem 0xfec00000-0xfec0ffff] could not be reserved
Jan  7 21:26:19 ubuntu kernel: [    0.209383] system 00:00: [mem 0xfee00000-0xfee0ffff] has been reserved
Jan  7 21:26:19 ubuntu kernel: [    0.209387] system 00:00: [mem 0xfed20000-0xfed9ffff] has been reserved
Jan  7 21:26:19 ubuntu kernel: [    0.209392] system 00:00: [mem 0xffa80000-0xffa83fff] could not be reserved
Jan  7 21:26:19 ubuntu kernel: [    0.209396] system 00:00: [mem 0xf4000000-0xf4003fff] has been reserved
Jan  7 21:26:19 ubuntu kernel: [    0.209405] system 00:00: [mem 0xf4004000-0xf4004fff] has been reserved
Jan  7 21:26:19 ubuntu kernel: [    0.209410] system 00:00: [mem 0xf4005000-0xf4005fff] has been reserved
Jan  7 21:26:19 ubuntu kernel: [    0.209414] system 00:00: [mem 0xf4006000-0xf4006fff] has been reserved
Jan  7 21:26:19 ubuntu kernel: [    0.209419] system 00:00: [mem 0xf4008000-0xf400bfff] has been reserved
Jan  7 21:26:19 ubuntu kernel: [    0.209423] system 00:00: [mem 0xf0000000-0xf3ffffff] has been reserved
Jan  7 21:26:19 ubuntu kernel: [    0.209430] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
Jan  7 21:26:19 ubuntu kernel: [    0.216557] pnp 00:01: [bus 00-ff]
Jan  7 21:26:19 ubuntu kernel: [    0.216564] pnp 00:01: [io  0x0000-0x0cf7 window]
Jan  7 21:26:19 ubuntu kernel: [    0.216568] pnp 00:01: [io  0x0cf8-0x0cff]
Jan  7 21:26:19 ubuntu kernel: [    0.216572] pnp 00:01: [io  0x0d00-0xffff window]
Jan  7 21:26:19 ubuntu kernel: [    0.216576] pnp 00:01: [mem 0x000a0000-0x000bffff window]
Jan  7 21:26:19 ubuntu kernel: [    0.216580] pnp 00:01: [mem 0x000d0000-0x000dffff window]
Jan  7 21:26:19 ubuntu kernel: [    0.216584] pnp 00:01: [mem 0xc0000000-0xefffffff window]
Jan  7 21:26:19 ubuntu kernel: [    0.216587] pnp 00:01: [mem 0xf4007000-0xf4007fff window]
Jan  7 21:26:19 ubuntu kernel: [    0.216591] pnp 00:01: [mem 0xf400c000-0xfebfffff window]
Jan  7 21:26:19 ubuntu kernel: [    0.216595] pnp 00:01: [mem 0xfec10000-0xfecfffff window]
Jan  7 21:26:19 ubuntu kernel: [    0.216599] pnp 00:01: [mem 0xfed00400-0xfed1ffff window]
Jan  7 21:26:19 ubuntu kernel: [    0.216603] pnp 00:01: [mem 0xfeda0000-0xfed9ffff window disabled]
Jan  7 21:26:19 ubuntu kernel: [    0.216607] pnp 00:01: [mem 0xfee10000-0xffafffff window]
Jan  7 21:26:19 ubuntu kernel: [    0.216733] pnp 00:01: Plug and Play ACPI device, IDs PNP0a03 (active)
Jan  7 21:26:19 ubuntu kernel: [    0.216767] pnp 00:02: [io  0x0092]
Jan  7 21:26:19 ubuntu kernel: [    0.216771] pnp 00:02: [io  0x00b2]
Jan  7 21:26:19 ubuntu kernel: [    0.216774] pnp 00:02: [io  0x0020-0x0021]
Jan  7 21:26:19 ubuntu kernel: [    0.216778] pnp 00:02: [io  0x00a0-0x00a1]
Jan  7 21:26:19 ubuntu kernel: [    0.216782] pnp 00:02: [irq 0 disabled]
Jan  7 21:26:19 ubuntu kernel: [    0.216785] pnp 00:02: [io  0x04d0-0x04d1]
Jan  7 21:26:19 ubuntu kernel: [    0.216789] pnp 00:02: [io  0x1000-0x1005]
Jan  7 21:26:19 ubuntu kernel: [    0.216792] pnp 00:02: [io  0x1008-0x100f]
Jan  7 21:26:19 ubuntu kernel: [    0.216819] pnp 00:02: disabling [io  0x1000-0x1005] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
Jan  7 21:26:19 ubuntu kernel: [    0.216824] pnp 00:02: disabling [io  0x1008-0x100f] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
Jan  7 21:26:19 ubuntu kernel: [    0.216892] system 00:02: [io  0x04d0-0x04d1] has been reserved
Jan  7 21:26:19 ubuntu kernel: [    0.216899] system 00:02: Plug and Play ACPI device, IDs PNP0c01 (active)
Jan  7 21:26:19 ubuntu kernel: [    0.216926] pnp 00:03: [io  0xf400-0xf4fe]
Jan  7 21:26:19 ubuntu kernel: [    0.216930] pnp 00:03: [io  0x0086]
Jan  7 21:26:19 ubuntu kernel: [    0.216934] pnp 00:03: [io  0x00b3]
Jan  7 21:26:19 ubuntu kernel: [    0.216937] pnp 00:03: [io  0x1006-0x1007]
Jan  7 21:26:19 ubuntu kernel: [    0.216940] pnp 00:03: [io  0x100a-0x1059]
Jan  7 21:26:19 ubuntu kernel: [    0.216944] pnp 00:03: [io  0x1060-0x107f]
Jan  7 21:26:19 ubuntu kernel: [    0.216947] pnp 00:03: [io  0x1080-0x10bf]
Jan  7 21:26:19 ubuntu kernel: [    0.216951] pnp 00:03: [io  0x10c0-0x10df]
Jan  7 21:26:19 ubuntu kernel: [    0.216954] pnp 00:03: [io  0x1010-0x102f]
Jan  7 21:26:19 ubuntu kernel: [    0.216958] pnp 00:03: [io  0x0809]
Jan  7 21:26:19 ubuntu kernel: [    0.216979] pnp 00:03: disabling [io  0x1006-0x1007] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
Jan  7 21:26:19 ubuntu kernel: [    0.216984] pnp 00:03: disabling [io  0x100a-0x1059] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
Jan  7 21:26:19 ubuntu kernel: [    0.216988] pnp 00:03: disabling [io  0x1060-0x107f] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
Jan  7 21:26:19 ubuntu kernel: [    0.216993] pnp 00:03: disabling [io  0x1010-0x102f] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
Jan  7 21:26:19 ubuntu kernel: [    0.217049] system 00:03: [io  0xf400-0xf4fe] has been reserved
Jan  7 21:26:19 ubuntu kernel: [    0.217054] system 00:03: [io  0x1080-0x10bf] has been reserved
Jan  7 21:26:19 ubuntu kernel: [    0.217058] system 00:03: [io  0x10c0-0x10df] has been reserved
Jan  7 21:26:19 ubuntu kernel: [    0.217063] system 00:03: [io  0x0809] has been reserved
Jan  7 21:26:19 ubuntu kernel: [    0.217068] system 00:03: Plug and Play ACPI device, IDs PNP0c01 (active)
Jan  7 21:26:19 ubuntu kernel: [    0.217106] pnp 00:04: [irq 12]
Jan  7 21:26:19 ubuntu kernel: [    0.217148] pnp 00:04: Plug and Play ACPI device, IDs PNP0f13 (active)
Jan  7 21:26:19 ubuntu kernel: [    0.217172] pnp 00:05: [io  0x0060]
Jan  7 21:26:19 ubuntu kernel: [    0.217176] pnp 00:05: [io  0x0064]
Jan  7 21:26:19 ubuntu kernel: [    0.217180] pnp 00:05: [io  0x0062]
Jan  7 21:26:19 ubuntu kernel: [    0.217183] pnp 00:05: [io  0x0066]
Jan  7 21:26:19 ubuntu kernel: [    0.217191] pnp 00:05: [irq 1]
Jan  7 21:26:19 ubuntu kernel: [    0.217238] pnp 00:05: Plug and Play ACPI device, IDs PNP0303 (active)
Jan  7 21:26:19 ubuntu kernel: [    0.217264] pnp 00:06: [io  0x0070-0x0071]
Jan  7 21:26:19 ubuntu kernel: [    0.217272] pnp 00:06: [irq 8]
Jan  7 21:26:19 ubuntu kernel: [    0.217275] pnp 00:06: [io  0x0072-0x0077]
Jan  7 21:26:19 ubuntu kernel: [    0.217318] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
Jan  7 21:26:19 ubuntu kernel: [    0.217344] pnp 00:07: [io  0x0061]
Jan  7 21:26:19 ubuntu kernel: [    0.217348] pnp 00:07: [io  0x0063]
Jan  7 21:26:19 ubuntu kernel: [    0.217351] pnp 00:07: [io  0x0065]
Jan  7 21:26:19 ubuntu kernel: [    0.217355] pnp 00:07: [io  0x0067]
Jan  7 21:26:19 ubuntu kernel: [    0.217398] pnp 00:07: Plug and Play ACPI device, IDs PNP0800 (active)
Jan  7 21:26:19 ubuntu kernel: [    0.217422] pnp 00:08: [io  0x0c80-0x0cff]
Jan  7 21:26:19 ubuntu kernel: [    0.217426] pnp 00:08: [io  0x0910-0x091f]
Jan  7 21:26:19 ubuntu kernel: [    0.217429] pnp 00:08: [io  0x0920-0x092f]
Jan  7 21:26:19 ubuntu kernel: [    0.217436] pnp 00:08: [io  0x0cb0-0x0cbf]
Jan  7 21:26:19 ubuntu kernel: [    0.217439] pnp 00:08: [io  0x0930-0x097f]
Jan  7 21:26:19 ubuntu kernel: [    0.217513] system 00:08: [io  0x0c80-0x0cff] could not be reserved
Jan  7 21:26:19 ubuntu kernel: [    0.217518] system 00:08: [io  0x0910-0x091f] has been reserved
Jan  7 21:26:19 ubuntu kernel: [    0.217522] system 00:08: [io  0x0920-0x092f] has been reserved
Jan  7 21:26:19 ubuntu kernel: [    0.217526] system 00:08: [io  0x0cb0-0x0cbf] has been reserved
Jan  7 21:26:19 ubuntu kernel: [    0.217530] system 00:08: [io  0x0930-0x097f] has been reserved
Jan  7 21:26:19 ubuntu kernel: [    0.217536] system 00:08: Plug and Play ACPI device, IDs PNP0c01 (active)
Jan  7 21:26:19 ubuntu kernel: [    0.217563] pnp 00:09: [dma 4]
Jan  7 21:26:19 ubuntu kernel: [    0.217567] pnp 00:09: [io  0x0000-0x000f]
Jan  7 21:26:19 ubuntu kernel: [    0.217571] pnp 00:09: [io  0x0080-0x0085]
Jan  7 21:26:19 ubuntu kernel: [    0.217574] pnp 00:09: [io  0x0087-0x008f]
Jan  7 21:26:19 ubuntu kernel: [    0.217578] pnp 00:09: [io  0x00c0-0x00df]
Jan  7 21:26:19 ubuntu kernel: [    0.217581] pnp 00:09: [io  0x0010-0x001f]
Jan  7 21:26:19 ubuntu kernel: [    0.217585] pnp 00:09: [io  0x0090-0x0091]
Jan  7 21:26:19 ubuntu kernel: [    0.217588] pnp 00:09: [io  0x0093-0x009f]
Jan  7 21:26:19 ubuntu kernel: [    0.217634] pnp 00:09: Plug and Play ACPI device, IDs PNP0200 (active)
Jan  7 21:26:19 ubuntu kernel: [    0.217657] pnp 00:0a: [io  0x00f0-0x00ff]
Jan  7 21:26:19 ubuntu kernel: [    0.217666] pnp 00:0a: [irq 13]
Jan  7 21:26:19 ubuntu kernel: [    0.217716] pnp 00:0a: Plug and Play ACPI device, IDs PNP0c04 (active)
Jan  7 21:26:19 ubuntu kernel: [    0.217784] pnp 00:0b: [mem 0xfed00000-0xfed003ff]
Jan  7 21:26:19 ubuntu kernel: [    0.217861] system 00:0b: [mem 0xfed00000-0xfed003ff] has been reserved
Jan  7 21:26:19 ubuntu kernel: [    0.217867] system 00:0b: Plug and Play ACPI device, IDs PNP0103 PNP0c01 (active)
Jan  7 21:26:19 ubuntu kernel: [    0.218288] pnp: PnP ACPI: found 12 devices
Jan  7 21:26:19 ubuntu kernel: [    0.218292] ACPI: ACPI bus type pnp unregistered
Jan  7 21:26:19 ubuntu kernel: [    0.218297] PnPBIOS: Disabled by ACPI PNP
Jan  7 21:26:19 ubuntu kernel: [    0.255534] pci 0000:00:1c.0: bridge window [io  0x1000-0x0fff] to [bus 0b-0b] add_size 1000
Jan  7 21:26:19 ubuntu kernel: [    0.255544] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 0b-0b] add_size 200000
Jan  7 21:26:19 ubuntu kernel: [    0.255578] pci 0000:00:1c.0: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
Jan  7 21:26:19 ubuntu kernel: [    0.255583] pci 0000:00:1c.0: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
Jan  7 21:26:19 ubuntu kernel: [    0.255593] pci 0000:00:1c.0: BAR 15: assigned [mem 0xc0000000-0xc01fffff 64bit pref]
Jan  7 21:26:19 ubuntu kernel: [    0.255600] pci 0000:00:1c.0: BAR 13: assigned [io  0x2000-0x2fff]
Jan  7 21:26:19 ubuntu kernel: [    0.255606] pci 0000:01:00.0: BAR 6: assigned [mem 0xefd00000-0xefd1ffff pref]
Jan  7 21:26:19 ubuntu kernel: [    0.255611] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Jan  7 21:26:19 ubuntu kernel: [    0.255616] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
Jan  7 21:26:19 ubuntu kernel: [    0.255622] pci 0000:00:01.0:   bridge window [mem 0xefd00000-0xefefffff]
Jan  7 21:26:19 ubuntu kernel: [    0.255628] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
Jan  7 21:26:19 ubuntu kernel: [    0.255635] pci 0000:00:1c.0: PCI bridge to [bus 0b-0b]
Jan  7 21:26:19 ubuntu kernel: [    0.255640] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
Jan  7 21:26:19 ubuntu kernel: [    0.255649] pci 0000:00:1c.0:   bridge window [mem 0xefc00000-0xefcfffff]
Jan  7 21:26:19 ubuntu kernel: [    0.255656] pci 0000:00:1c.0:   bridge window [mem 0xc0000000-0xc01fffff 64bit pref]
Jan  7 21:26:19 ubuntu kernel: [    0.255666] pci 0000:00:1c.3: PCI bridge to [bus 0c-0d]
Jan  7 21:26:19 ubuntu kernel: [    0.255671] pci 0000:00:1c.3:   bridge window [io  0xd000-0xdfff]
Jan  7 21:26:19 ubuntu kernel: [    0.255680] pci 0000:00:1c.3:   bridge window [mem 0xefa00000-0xefbfffff]
Jan  7 21:26:19 ubuntu kernel: [    0.255687] pci 0000:00:1c.3:   bridge window [mem 0xe0000000-0xe01fffff 64bit pref]
Jan  7 21:26:19 ubuntu kernel: [    0.255698] pci 0000:00:1e.0: PCI bridge to [bus 03-03]
Jan  7 21:26:19 ubuntu kernel: [    0.255707] pci 0000:00:1e.0:   bridge window [mem 0xef900000-0xef9fffff]
Jan  7 21:26:19 ubuntu kernel: [    0.255773] pci 0000:00:1e.0: setting latency timer to 64
Jan  7 21:26:19 ubuntu kernel: [    0.255780] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
Jan  7 21:26:19 ubuntu kernel: [    0.255784] pci_bus 0000:00: resource 5 [mem 0x00000000-0xffffffff]
Jan  7 21:26:19 ubuntu kernel: [    0.255788] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
Jan  7 21:26:19 ubuntu kernel: [    0.255792] pci_bus 0000:01: resource 1 [mem 0xefd00000-0xefefffff]
Jan  7 21:26:19 ubuntu kernel: [    0.255796] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
Jan  7 21:26:19 ubuntu kernel: [    0.255800] pci_bus 0000:0b: resource 0 [io  0x2000-0x2fff]
Jan  7 21:26:19 ubuntu kernel: [    0.255804] pci_bus 0000:0b: resource 1 [mem 0xefc00000-0xefcfffff]
Jan  7 21:26:19 ubuntu kernel: [    0.255807] pci_bus 0000:0b: resource 2 [mem 0xc0000000-0xc01fffff 64bit pref]
Jan  7 21:26:19 ubuntu kernel: [    0.255811] pci_bus 0000:0c: resource 0 [io  0xd000-0xdfff]
Jan  7 21:26:19 ubuntu kernel: [    0.255815] pci_bus 0000:0c: resource 1 [mem 0xefa00000-0xefbfffff]
Jan  7 21:26:19 ubuntu kernel: [    0.255819] pci_bus 0000:0c: resource 2 [mem 0xe0000000-0xe01fffff 64bit pref]
Jan  7 21:26:19 ubuntu kernel: [    0.255823] pci_bus 0000:03: resource 1 [mem 0xef900000-0xef9fffff]
Jan  7 21:26:19 ubuntu kernel: [    0.255827] pci_bus 0000:03: resource 4 [io  0x0000-0xffff]
Jan  7 21:26:19 ubuntu kernel: [    0.255831] pci_bus 0000:03: resource 5 [mem 0x00000000-0xffffffff]
Jan  7 21:26:19 ubuntu kernel: [    0.255886] NET: Registered protocol family 2
Jan  7 21:26:19 ubuntu kernel: [    0.255979] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Jan  7 21:26:19 ubuntu kernel: [    0.256227] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Jan  7 21:26:19 ubuntu kernel: [    0.257017] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Jan  7 21:26:19 ubuntu kernel: [    0.257491] TCP: Hash tables configured (established 131072 bind 65536)
Jan  7 21:26:19 ubuntu kernel: [    0.257494] TCP: reno registered
Jan  7 21:26:19 ubuntu kernel: [    0.257501] UDP hash table entries: 512 (order: 2, 16384 bytes)
Jan  7 21:26:19 ubuntu kernel: [    0.257518] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
Jan  7 21:26:19 ubuntu kernel: [    0.257650] NET: Registered protocol family 1
Jan  7 21:26:19 ubuntu kernel: [    0.257920] pci 0000:01:00.0: Boot video device
Jan  7 21:26:19 ubuntu kernel: [    0.257949] PCI: CLS 64 bytes, default 64
Jan  7 21:26:19 ubuntu kernel: [    0.258055] Simple Boot Flag at 0x79 set to 0x1
Jan  7 21:26:19 ubuntu kernel: [    0.258602] audit: initializing netlink socket (disabled)
Jan  7 21:26:19 ubuntu kernel: [    0.258621] type=2000 audit(1389129929.252:1): initialized
Jan  7 21:26:19 ubuntu kernel: [    0.290073] highmem bounce pool size: 64 pages
Jan  7 21:26:19 ubuntu kernel: [    0.290097] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Jan  7 21:26:19 ubuntu kernel: [    0.293117] VFS: Disk quotas dquot_6.5.2
Jan  7 21:26:19 ubuntu kernel: [    0.293205] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jan  7 21:26:19 ubuntu kernel: [    0.294077] fuse init (API version 7.19)
Jan  7 21:26:19 ubuntu kernel: [    0.294210] msgmni has been set to 1670
Jan  7 21:26:19 ubuntu kernel: [    0.294696] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
Jan  7 21:26:19 ubuntu kernel: [    0.294737] io scheduler noop registered
Jan  7 21:26:19 ubuntu kernel: [    0.294740] io scheduler deadline registered (default)
Jan  7 21:26:19 ubuntu kernel: [    0.294750] io scheduler cfq registered
Jan  7 21:26:19 ubuntu kernel: [    0.294981] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
Jan  7 21:26:19 ubuntu kernel: [    0.295124] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
Jan  7 21:26:19 ubuntu kernel: [    0.295283] pcieport 0000:00:1c.3: irq 42 for MSI/MSI-X
Jan  7 21:26:19 ubuntu kernel: [    0.295416] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jan  7 21:26:19 ubuntu kernel: [    0.295446] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Jan  7 21:26:19 ubuntu kernel: [    0.295540] intel_idle: does not run on family 6 model 14
Jan  7 21:26:19 ubuntu kernel: [    0.296299] ACPI: AC Adapter [AC] (on-line)
Jan  7 21:26:19 ubuntu kernel: [    0.296423] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
Jan  7 21:26:19 ubuntu kernel: [    0.296770] ACPI: Lid Switch [LID]
Jan  7 21:26:19 ubuntu kernel: [    0.296839] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
Jan  7 21:26:19 ubuntu kernel: [    0.296845] ACPI: Power Button [PBTN]
Jan  7 21:26:19 ubuntu kernel: [    0.296908] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
Jan  7 21:26:19 ubuntu kernel: [    0.296913] ACPI: Sleep Button [SBTN]
Jan  7 21:26:19 ubuntu kernel: [    0.297041] ACPI: Requesting acpi_cpufreq
Jan  7 21:26:19 ubuntu kernel: [    0.535357] Freeing initrd memory: 15184k freed
Jan  7 21:26:19 ubuntu kernel: [    0.546725] ACPI: acpi_idle registered with cpuidle
Jan  7 21:26:19 ubuntu kernel: [    0.555143] thermal LNXTHERM:00: registered as thermal_zone0
Jan  7 21:26:19 ubuntu kernel: [    0.555149] ACPI: Thermal Zone [THM] (25 C)
Jan  7 21:26:19 ubuntu kernel: [    0.555182] ACPI: Battery Slot [BAT0] (battery present)
Jan  7 21:26:19 ubuntu kernel: [    0.555238] GHES: HEST is not enabled!
Jan  7 21:26:19 ubuntu kernel: [    0.555367] isapnp: Scanning for PnP cards...
Jan  7 21:26:19 ubuntu kernel: [    0.562408] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Jan  7 21:26:19 ubuntu kernel: [    0.576110] ACPI: Battery Slot [BAT0] (battery present)
Jan  7 21:26:19 ubuntu kernel: [    0.585820] Linux agpgart interface v0.103
Jan  7 21:26:19 ubuntu kernel: [    0.588398] brd: module loaded
Jan  7 21:26:19 ubuntu kernel: [    0.589514] loop: module loaded
Jan  7 21:26:19 ubuntu kernel: [    0.589694] ata_piix 0000:00:1f.2: version 2.13
Jan  7 21:26:19 ubuntu kernel: [    0.589732] ata_piix 0000:00:1f.2: MAP [
Jan  7 21:26:19 ubuntu kernel: [    0.589734]  P0 P2 IDE IDE ]
Jan  7 21:26:19 ubuntu kernel: [    0.589790] ata_piix 0000:00:1f.2: setting latency timer to 64
Jan  7 21:26:19 ubuntu kernel: [    0.590262] scsi0 : ata_piix
Jan  7 21:26:19 ubuntu kernel: [    0.590362] scsi1 : ata_piix
Jan  7 21:26:19 ubuntu kernel: [    0.590995] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
Jan  7 21:26:19 ubuntu kernel: [    0.590999] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
Jan  7 21:26:19 ubuntu kernel: [    0.591496] Fixed MDIO Bus: probed
Jan  7 21:26:19 ubuntu kernel: [    0.591579] tun: Universal TUN/TAP device driver, 1.6
Jan  7 21:26:19 ubuntu kernel: [    0.591582] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Jan  7 21:26:19 ubuntu kernel: [    0.591657] PPP generic driver version 2.4.2
Jan  7 21:26:19 ubuntu kernel: [    0.591723] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Jan  7 21:26:19 ubuntu kernel: [    0.591776] ehci_hcd 0000:00:1d.7: setting latency timer to 64
Jan  7 21:26:19 ubuntu kernel: [    0.591782] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Jan  7 21:26:19 ubuntu kernel: [    0.591791] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
Jan  7 21:26:19 ubuntu kernel: [    0.591818] ehci_hcd 0000:00:1d.7: using broken periodic workaround
Jan  7 21:26:19 ubuntu kernel: [    0.591834] ehci_hcd 0000:00:1d.7: debug port 1
Jan  7 21:26:19 ubuntu kernel: [    0.595721] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
Jan  7 21:26:19 ubuntu kernel: [    0.595749] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xffa80000
Jan  7 21:26:19 ubuntu kernel: [    0.604027] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Jan  7 21:26:19 ubuntu kernel: [    0.604089] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
Jan  7 21:26:19 ubuntu kernel: [    0.604093] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jan  7 21:26:19 ubuntu kernel: [    0.604097] usb usb1: Product: EHCI Host Controller
Jan  7 21:26:19 ubuntu kernel: [    0.604100] usb usb1: Manufacturer: Linux 3.5.0-45-generic ehci_hcd
Jan  7 21:26:19 ubuntu kernel: [    0.604104] usb usb1: SerialNumber: 0000:00:1d.7
Jan  7 21:26:19 ubuntu kernel: [    0.604282] hub 1-0:1.0: USB hub found
Jan  7 21:26:19 ubuntu kernel: [    0.604289] hub 1-0:1.0: 8 ports detected
Jan  7 21:26:19 ubuntu kernel: [    0.604418] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Jan  7 21:26:19 ubuntu kernel: [    0.604449] uhci_hcd: USB Universal Host Controller Interface driver
Jan  7 21:26:19 ubuntu kernel: [    0.604485] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Jan  7 21:26:19 ubuntu kernel: [    0.604490] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Jan  7 21:26:19 ubuntu kernel: [    0.604497] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Jan  7 21:26:19 ubuntu kernel: [    0.604530] uhci_hcd 0000:00:1d.0: irq 20, io base 0x0000bf80
Jan  7 21:26:19 ubuntu kernel: [    0.604579] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
Jan  7 21:26:19 ubuntu kernel: [    0.604583] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jan  7 21:26:19 ubuntu kernel: [    0.604587] usb usb2: Product: UHCI Host Controller
Jan  7 21:26:19 ubuntu kernel: [    0.604591] usb usb2: Manufacturer: Linux 3.5.0-45-generic uhci_hcd
Jan  7 21:26:19 ubuntu kernel: [    0.604594] usb usb2: SerialNumber: 0000:00:1d.0
Jan  7 21:26:19 ubuntu kernel: [    0.604760] hub 2-0:1.0: USB hub found
Jan  7 21:26:19 ubuntu kernel: [    0.604766] hub 2-0:1.0: 2 ports detected
Jan  7 21:26:19 ubuntu kernel: [    0.604872] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Jan  7 21:26:19 ubuntu kernel: [    0.604877] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Jan  7 21:26:19 ubuntu kernel: [    0.604885] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
Jan  7 21:26:19 ubuntu kernel: [    0.604929] uhci_hcd 0000:00:1d.1: irq 21, io base 0x0000bf60
Jan  7 21:26:19 ubuntu kernel: [    0.604977] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
Jan  7 21:26:19 ubuntu kernel: [    0.604981] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jan  7 21:26:19 ubuntu kernel: [    0.604984] usb usb3: Product: UHCI Host Controller
Jan  7 21:26:19 ubuntu kernel: [    0.604988] usb usb3: Manufacturer: Linux 3.5.0-45-generic uhci_hcd
Jan  7 21:26:19 ubuntu kernel: [    0.604991] usb usb3: SerialNumber: 0000:00:1d.1
Jan  7 21:26:19 ubuntu kernel: [    0.605147] hub 3-0:1.0: USB hub found
Jan  7 21:26:19 ubuntu kernel: [    0.605154] hub 3-0:1.0: 2 ports detected
Jan  7 21:26:19 ubuntu kernel: [    0.605258] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Jan  7 21:26:19 ubuntu kernel: [    0.605264] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Jan  7 21:26:19 ubuntu kernel: [    0.605271] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
Jan  7 21:26:19 ubuntu kernel: [    0.605315] uhci_hcd 0000:00:1d.2: irq 22, io base 0x0000bf40
Jan  7 21:26:19 ubuntu kernel: [    0.605360] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
Jan  7 21:26:19 ubuntu kernel: [    0.605364] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jan  7 21:26:19 ubuntu kernel: [    0.605368] usb usb4: Product: UHCI Host Controller
Jan  7 21:26:19 ubuntu kernel: [    0.605371] usb usb4: Manufacturer: Linux 3.5.0-45-generic uhci_hcd
Jan  7 21:26:19 ubuntu kernel: [    0.605375] usb usb4: SerialNumber: 0000:00:1d.2
Jan  7 21:26:19 ubuntu kernel: [    0.605533] hub 4-0:1.0: USB hub found
Jan  7 21:26:19 ubuntu kernel: [    0.605539] hub 4-0:1.0: 2 ports detected
Jan  7 21:26:19 ubuntu kernel: [    0.605646] uhci_hcd 0000:00:1d.3: setting latency timer to 64
Jan  7 21:26:19 ubuntu kernel: [    0.605651] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Jan  7 21:26:19 ubuntu kernel: [    0.605658] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
Jan  7 21:26:19 ubuntu kernel: [    0.605702] uhci_hcd 0000:00:1d.3: irq 23, io base 0x0000bf20
Jan  7 21:26:19 ubuntu kernel: [    0.605749] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
Jan  7 21:26:19 ubuntu kernel: [    0.605753] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jan  7 21:26:19 ubuntu kernel: [    0.605757] usb usb5: Product: UHCI Host Controller
Jan  7 21:26:19 ubuntu kernel: [    0.605761] usb usb5: Manufacturer: Linux 3.5.0-45-generic uhci_hcd
Jan  7 21:26:19 ubuntu kernel: [    0.605764] usb usb5: SerialNumber: 0000:00:1d.3
Jan  7 21:26:19 ubuntu kernel: [    0.605931] hub 5-0:1.0: USB hub found
Jan  7 21:26:19 ubuntu kernel: [    0.605937] hub 5-0:1.0: 2 ports detected
Jan  7 21:26:19 ubuntu kernel: [    0.606113] usbcore: registered new interface driver libusual
Jan  7 21:26:19 ubuntu kernel: [    0.606184] i8042: PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Jan  7 21:26:19 ubuntu kernel: [    0.609106] serio: i8042 KBD port at 0x60,0x64 irq 1
Jan  7 21:26:19 ubuntu kernel: [    0.609115] serio: i8042 AUX port at 0x60,0x64 irq 12
Jan  7 21:26:19 ubuntu kernel: [    0.609273] mousedev: PS/2 mouse device common for all mice
Jan  7 21:26:19 ubuntu kernel: [    0.609476] rtc_cmos 00:06: RTC can wake from S4
Jan  7 21:26:19 ubuntu kernel: [    0.609662] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
Jan  7 21:26:19 ubuntu kernel: [    0.609700] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
Jan  7 21:26:19 ubuntu kernel: [    0.609791] device-mapper: uevent: version 1.0.3
Jan  7 21:26:19 ubuntu kernel: [    0.609881] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: [email]dm-devel@redhat.com[/email]
Jan  7 21:26:19 ubuntu kernel: [    0.609909] EISA: Probing bus 0 at eisa.0
Jan  7 21:26:19 ubuntu kernel: [    0.609979] EISA: Mainboard R__FFFF detected.
Jan  7 21:26:19 ubuntu kernel: [    0.610004] Cannot allocate resource for EISA slot 1
Jan  7 21:26:19 ubuntu kernel: [    0.610008] Cannot allocate resource for EISA slot 2
Jan  7 21:26:19 ubuntu kernel: [    0.610039] EISA: Detected 0 cards.
Jan  7 21:26:19 ubuntu kernel: [    0.610117] cpuidle: using governor ladder
Jan  7 21:26:19 ubuntu kernel: [    0.610205] cpuidle: using governor menu
Jan  7 21:26:19 ubuntu kernel: [    0.610208] EFI Variables Facility v0.08 2004-May-17
Jan  7 21:26:19 ubuntu kernel: [    0.610478] ashmem: initialized
Jan  7 21:26:19 ubuntu kernel: [    0.610665] TCP: cubic registered
Jan  7 21:26:19 ubuntu kernel: [    0.610852] NET: Registered protocol family 10
Jan  7 21:26:19 ubuntu kernel: [    0.611160] NET: Registered protocol family 17
Jan  7 21:26:19 ubuntu kernel: [    0.611176] Key type dns_resolver registered
Jan  7 21:26:19 ubuntu kernel: [    0.611302] Using IPI No-Shortcut mode
Jan  7 21:26:19 ubuntu kernel: [    0.611425] PM: Hibernation image not present or could not be loaded.
Jan  7 21:26:19 ubuntu kernel: [    0.611447] registered taskstats version 1
Jan  7 21:26:19 ubuntu kernel: [    0.612024] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
Jan  7 21:26:19 ubuntu kernel: [    0.614895] Key type trusted registered
Jan  7 21:26:19 ubuntu kernel: [    0.617873] Key type encrypted registered
Jan  7 21:26:19 ubuntu kernel: [    0.620925]   Magic number: 14:97:449
Jan  7 21:26:19 ubuntu kernel: [    0.621069] rtc_cmos 00:06: setting system clock to 2014-01-07 21:25:30 UTC (1389129930)
Jan  7 21:26:19 ubuntu kernel: [    0.621850] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jan  7 21:26:19 ubuntu kernel: [    0.621854] EDD information not available.
Jan  7 21:26:19 ubuntu kernel: [    0.757800] ata1.00: ATA-7: ST980811AS, 3.CDD, max UDMA/133
Jan  7 21:26:19 ubuntu kernel: [    0.757805] ata1.00: 156301488 sectors, multi 8: LBA48 NCQ (depth 0/32)
Jan  7 21:26:19 ubuntu kernel: [    0.764406] ata2.00: ATAPI: CD-RW/DVD-ROM DW224EV, D.CF, max UDMA/33
Jan  7 21:26:19 ubuntu kernel: [    0.772603] ata1.00: configured for UDMA/133
Jan  7 21:26:19 ubuntu kernel: [    0.780286] ata2.00: configured for UDMA/33
Jan  7 21:26:19 ubuntu kernel: [    0.913543] isapnp: No Plug & Play device found
Jan  7 21:26:19 ubuntu kernel: [    0.913756] scsi 0:0:0:0: Direct-Access     ATA      ST980811AS       3.CD PQ: 0 ANSI: 5
Jan  7 21:26:19 ubuntu kernel: [    0.913944] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
Jan  7 21:26:19 ubuntu kernel: [    0.913987] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jan  7 21:26:19 ubuntu kernel: [    0.914016] sd 0:0:0:0: [sda] Write Protect is off
Jan  7 21:26:19 ubuntu kernel: [    0.914021] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jan  7 21:26:19 ubuntu kernel: [    0.914052] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jan  7 21:26:19 ubuntu kernel: [    1.035962]  sda: sda1 sda2 sda3 sda4 < sda5 >
Jan  7 21:26:19 ubuntu kernel: [    1.036679] sd 0:0:0:0: [sda] Attached SCSI disk
Jan  7 21:26:19 ubuntu kernel: [    1.038270] scsi 1:0:0:0: CD-ROM            TEAC     CDRWDVD DW224EV  D.CF PQ: 0 ANSI: 5
Jan  7 21:26:19 ubuntu kernel: [    1.040399] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
Jan  7 21:26:19 ubuntu kernel: [    1.040403] cdrom: Uniform CD-ROM driver Revision: 3.20
Jan  7 21:26:19 ubuntu kernel: [    1.040576] sr 1:0:0:0: Attached scsi CD-ROM sr0
Jan  7 21:26:19 ubuntu kernel: [    1.040742] sr 1:0:0:0: Attached scsi generic sg1 type 5
Jan  7 21:26:19 ubuntu kernel: [    1.040998] Freeing unused kernel memory: 764k freed
Jan  7 21:26:19 ubuntu kernel: [    1.041503] Write protecting the kernel text: 6064k
Jan  7 21:26:19 ubuntu kernel: [    1.041548] Write protecting the kernel read-only data: 2480k
Jan  7 21:26:19 ubuntu kernel: [    1.041551] NX-protecting the kernel data: 4176k
Jan  7 21:26:19 ubuntu kernel: [    1.152105] ssb: Found chip with id 0x4311, rev 0x01 and package 0x00
Jan  7 21:26:19 ubuntu kernel: [    1.152124] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x11, vendor 0x4243)
Jan  7 21:26:19 ubuntu kernel: [    1.152139] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0A, vendor 0x4243)
Jan  7 21:26:19 ubuntu kernel: [    1.152150] ssb: Core 2 found: USB 1.1 Host (cc 0x817, rev 0x03, vendor 0x4243)
Jan  7 21:26:19 ubuntu kernel: [    1.152160] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x01, vendor 0x4243)
Jan  7 21:26:19 ubuntu kernel: [    1.156049] usb 2-1: new low-speed USB device number 2 using uhci_hcd
Jan  7 21:26:19 ubuntu kernel: [    1.202049] sdhci: Secure Digital Host Controller Interface driver
Jan  7 21:26:19 ubuntu kernel: [    1.202055] sdhci: Copyright(c) Pierre Ossman
Jan  7 21:26:19 ubuntu kernel: [    1.211312] sdhci-pci 0000:03:01.1: SDHCI controller found [1180:0822] (rev 19)
Jan  7 21:26:19 ubuntu kernel: [    1.212655] mmc0: no vmmc regulator found
Jan  7 21:26:19 ubuntu kernel: [    1.213707] Registered led device: mmc0::
Jan  7 21:26:19 ubuntu kernel: [    1.216179] ssb: Sonics Silicon Backplane found on PCI device 0000:0b:00.0
Jan  7 21:26:19 ubuntu kernel: [    1.244038] mmc0: SDHCI controller on PCI [0000:03:01.1] using DMA
Jan  7 21:26:19 ubuntu kernel: [    1.312110] firewire_ohci 0000:03:01.0: added OHCI v1.10 device as card 0, 4 IR + 4 IT contexts, quirks 0x11
Jan  7 21:26:19 ubuntu kernel: [    1.327601] usb 2-1: New USB device found, idVendor=1d57, idProduct=0008
Jan  7 21:26:19 ubuntu kernel: [    1.327608] usb 2-1: New USB device strings: Mfr=0, Product=1, SerialNumber=0
Jan  7 21:26:19 ubuntu kernel: [    1.327612] usb 2-1: Product: 2.4G Wireless Optical Mouse
Jan  7 21:26:19 ubuntu kernel: [    1.336174] ssb: Found chip with id 0x4401, rev 0x02 and package 0x00
Jan  7 21:26:19 ubuntu kernel: [    1.336186] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243)
Jan  7 21:26:19 ubuntu kernel: [    1.336194] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243)
Jan  7 21:26:19 ubuntu kernel: [    1.336202] ssb: Core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243)
Jan  7 21:26:19 ubuntu kernel: [    1.348681] usbcore: registered new interface driver usbhid
Jan  7 21:26:19 ubuntu kernel: [    1.348686] usbhid: USB HID core driver
Jan  7 21:26:19 ubuntu kernel: [    1.352384] input: 2.4G Wireless Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input4
Jan  7 21:26:19 ubuntu kernel: [    1.352551] hid-generic 0003:1D57:0008.0001: input,hidraw0: USB HID v1.10 Mouse [2.4G Wireless Optical Mouse] on usb-0000:00:1d.0-1/input0
Jan  7 21:26:19 ubuntu kernel: [    1.376228] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
Jan  7 21:26:19 ubuntu kernel: [    1.376491] b44: Broadcom 44xx/47xx 10/100 PCI ethernet driver version 2.0
Jan  7 21:26:19 ubuntu kernel: [    1.397996] b44 ssb1:0: eth0: Broadcom 44xx/47xx 10/100 PCI ethernet driver 00:19:b9:71:50:70
Jan  7 21:26:19 ubuntu kernel: [    1.572073] usb 3-1: new low-speed USB device number 2 using uhci_hcd
Jan  7 21:26:19 ubuntu kernel: [    1.742009] usb 3-1: New USB device found, idVendor=17ef, idProduct=600e
Jan  7 21:26:19 ubuntu kernel: [    1.742016] usb 3-1: New USB device strings: Mfr=0, Product=2, SerialNumber=0
Jan  7 21:26:19 ubuntu kernel: [    1.742020] usb 3-1: Product: Lenovo Optical Mouse
Jan  7 21:26:19 ubuntu kernel: [    1.770079] input: Lenovo Optical Mouse as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input5
Jan  7 21:26:19 ubuntu kernel: [    1.770310] hid-generic 0003:17EF:600E.0002: input,hidraw1: USB HID v1.11 Mouse [Lenovo Optical Mouse] on usb-0000:00:1d.1-1/input0
Jan  7 21:26:19 ubuntu kernel: [    1.812207] firewire_core 0000:03:01.0: created device fw0: GUID 324fc00003a87961, S400
Jan  7 21:26:19 ubuntu kernel: [    2.895846] kjournald starting.  Commit interval 5 seconds
Jan  7 21:26:19 ubuntu kernel: [    2.915191] EXT3-fs (loop0): mounted filesystem with ordered data mode
Jan  7 21:26:19 ubuntu kernel: [   44.705247] Adding 262140k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:1 across:262140k 
Jan  7 21:26:19 ubuntu kernel: [   44.714264] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Jan  7 21:26:19 ubuntu kernel: [   44.725973] EXT3-fs (loop0): using internal journal
Jan  7 21:26:19 ubuntu kernel: [   45.934716] type=1400 audit(1389147975.809:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=563 comm="apparmor_parser"
Jan  7 21:26:19 ubuntu kernel: [   45.935416] type=1400 audit(1389147975.809:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=563 comm="apparmor_parser"
Jan  7 21:26:19 ubuntu kernel: [   45.935784] type=1400 audit(1389147975.809:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=563 comm="apparmor_parser"
Jan  7 21:26:19 ubuntu kernel: [   48.013872] microcode: CPU0 sig=0x6ec, pf=0x80, revision=0x59
Jan  7 21:26:19 ubuntu kernel: [   48.018715] wmi: Mapper loaded
Jan  7 21:26:19 ubuntu kernel: [   48.371660] acpi device:23: registered as cooling_device2
Jan  7 21:26:19 ubuntu kernel: [   48.372032] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
Jan  7 21:26:19 ubuntu kernel: [   48.372305] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:20/LNXVIDEO:00/input/input6
Jan  7 21:26:19 ubuntu kernel: [   48.372543] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
Jan  7 21:26:19 ubuntu kernel: [   48.626159] type=1400 audit(1389147978.501:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=789 comm="apparmor_parser"
Jan  7 21:26:19 ubuntu kernel: [   48.626817] type=1400 audit(1389147978.501:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=789 comm="apparmor_parser"
Jan  7 21:26:19 ubuntu kernel: [   48.627184] type=1400 audit(1389147978.501:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=789 comm="apparmor_parser"
Jan  7 21:26:19 ubuntu kernel: [   48.628581] type=1400 audit(1389147978.505:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=788 comm="apparmor_parser"
Jan  7 21:26:19 ubuntu kernel: [   48.629116] type=1400 audit(1389147978.505:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=788 comm="apparmor_parser"
Jan  7 21:26:19 ubuntu kernel: [   48.640564] type=1400 audit(1389147978.517:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=794 comm="apparmor_parser"
Jan  7 21:26:19 ubuntu kernel: [   48.641317] type=1400 audit(1389147978.517:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=794 comm="apparmor_parser"
Jan  7 21:26:19 ubuntu polkitd[783]: started daemon version 0.104 using authority implementation `local' version `0.104'
Jan  7 21:26:19 ubuntu dbus[704]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'
Jan  7 21:26:19 ubuntu NetworkManager[753]:    SCPlugin-Ifupdown: init!
Jan  7 21:26:19 ubuntu NetworkManager[753]:    SCPlugin-Ifupdown: update_system_hostname
Jan  7 21:26:19 ubuntu NetworkManager[753]:    SCPluginIfupdown: management mode: unmanaged
Jan  7 21:26:19 ubuntu NetworkManager[753]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:03:00.0/ssb1:0/net/eth0, iface: eth0)
Jan  7 21:26:19 ubuntu NetworkManager[753]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:03:00.0/ssb1:0/net/eth0, iface: eth0): no ifupdown configuration found.
Jan  7 21:26:19 ubuntu NetworkManager[753]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Jan  7 21:26:19 ubuntu NetworkManager[753]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Jan  7 21:26:19 ubuntu NetworkManager[753]:    SCPlugin-Ifupdown: end _init.
Jan  7 21:26:19 ubuntu NetworkManager[753]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Jan  7 21:26:19 ubuntu NetworkManager[753]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Jan  7 21:26:19 ubuntu NetworkManager[753]:    Ifupdown: get unmanaged devices count: 0
Jan  7 21:26:19 ubuntu NetworkManager[753]:    SCPlugin-Ifupdown: (165447592) ... get_connections.
Jan  7 21:26:19 ubuntu NetworkManager[753]:    SCPlugin-Ifupdown: (165447592) ... get_connections (managed=false): return empty list.
Jan  7 21:26:19 ubuntu NetworkManager[753]:    keyfile: parsing 07FX09042629 1 ... 
Jan  7 21:26:19 ubuntu NetworkManager[753]:    keyfile:     read connection '07FX09042629 1'
Jan  7 21:26:19 ubuntu NetworkManager[753]:    keyfile: parsing 8LGL3 ... 
Jan  7 21:26:19 ubuntu NetworkManager[753]:    keyfile:     read connection '8LGL3'
Jan  7 21:26:19 ubuntu NetworkManager[753]:    keyfile: parsing SecurityKiss ... 
Jan  7 21:26:19 ubuntu NetworkManager[753]:    keyfile:     read connection 'SecurityKiss'
Jan  7 21:26:19 ubuntu NetworkManager[753]:    keyfile: parsing VAGE1 ... 
Jan  7 21:26:19 ubuntu kernel: [   49.536340] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
Jan  7 21:26:20 ubuntu NetworkManager[753]:    keyfile:     read connection 'VAGE1'
Jan  7 21:26:20 ubuntu NetworkManager[753]:    keyfile: parsing MQZ-Wireless ... 
Jan  7 21:26:20 ubuntu NetworkManager[753]:    keyfile:     read connection 'MQZ-Wireless'
Jan  7 21:26:20 ubuntu NetworkManager[753]:    keyfile: parsing Galaxy S III_5339 ... 
Jan  7 21:26:20 ubuntu NetworkManager[753]:    keyfile:     read connection 'Galaxy S III_5339'
Jan  7 21:26:21 ubuntu kernel: [   51.634870] microcode: CPU1 sig=0x6ec, pf=0x80, revision=0x59
Jan  7 21:26:21 ubuntu kernel: [   51.638159] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
Jan  7 21:26:22 ubuntu NetworkManager[753]:    Ifupdown: get unmanaged devices count: 0
Jan  7 21:26:22 ubuntu NetworkManager[753]: <info> modem-manager is now available
Jan  7 21:26:22 ubuntu NetworkManager[753]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jan  7 21:26:22 ubuntu NetworkManager[753]: <info> WiFi enabled by radio killswitch; enabled by state file
Jan  7 21:26:22 ubuntu NetworkManager[753]: <info> WWAN enabled by radio killswitch; enabled by state file
Jan  7 21:26:22 ubuntu NetworkManager[753]: <info> WiMAX enabled by radio killswitch; enabled by state file
Jan  7 21:26:22 ubuntu NetworkManager[753]: <info> Networking is enabled by state file
Jan  7 21:26:22 ubuntu NetworkManager[753]: <warn> failed to allocate link cache: (-10) Operation not supported
Jan  7 21:26:22 ubuntu NetworkManager[753]: <info> (eth0): carrier is OFF
Jan  7 21:26:22 ubuntu NetworkManager[753]: <info> (eth0): new Ethernet device (driver: 'b44' ifindex: 2)
Jan  7 21:26:22 ubuntu NetworkManager[753]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Jan  7 21:26:22 ubuntu NetworkManager[753]: <info> (eth0): now managed
Jan  7 21:26:22 ubuntu NetworkManager[753]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jan  7 21:26:22 ubuntu NetworkManager[753]: <info> (eth0): bringing up device.
Jan  7 21:26:22 ubuntu NetworkManager[753]: <info> (eth0): preparing device.
Jan  7 21:26:22 ubuntu NetworkManager[753]: <info> (eth0): deactivating device (reason 'managed') [2]
Jan  7 21:26:22 ubuntu kernel: [   52.343102] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Jan  7 21:26:22 ubuntu kernel: [   52.343499] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Jan  7 21:26:22 ubuntu NetworkManager[753]: <info> Added default wired connection 'Wired connection 1' for /sys/devices/pci0000:00/0000:00:1e.0/0000:03:00.0/ssb1:0/net/eth0
Jan  7 21:26:22 ubuntu kernel: [   53.056790] intel_rng: FWH not detected
Jan  7 21:26:23 ubuntu kernel: [   53.258325] Bluetooth: Core ver 2.16
Jan  7 21:26:23 ubuntu kernel: [   53.258361] NET: Registered protocol family 31
Jan  7 21:26:23 ubuntu kernel: [   53.258364] Bluetooth: HCI device and connection manager initialized
Jan  7 21:26:23 ubuntu kernel: [   53.258367] Bluetooth: HCI socket layer initialized
Jan  7 21:26:23 ubuntu kernel: [   53.258369] Bluetooth: L2CAP socket layer initialized
Jan  7 21:26:23 ubuntu kernel: [   53.258378] Bluetooth: SCO socket layer initialized
Jan  7 21:26:23 ubuntu bluetoothd[719]: Failed to init alert plugin
Jan  7 21:26:23 ubuntu bluetoothd[719]: Failed to init time plugin
Jan  7 21:26:23 ubuntu bluetoothd[719]: Failed to init proximity plugin
Jan  7 21:26:23 ubuntu kernel: [   53.569761] cfg80211: Calling CRDA to update world regulatory domain
Jan  7 21:26:23 ubuntu kernel: [   53.581408] cfg80211: World regulatory domain updated:
Jan  7 21:26:23 ubuntu kernel: [   53.581415] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jan  7 21:26:23 ubuntu kernel: [   53.581418] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  7 21:26:23 ubuntu kernel: [   53.581422] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jan  7 21:26:23 ubuntu kernel: [   53.581425] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jan  7 21:26:23 ubuntu kernel: [   53.581428] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  7 21:26:23 ubuntu kernel: [   53.581431] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  7 21:26:23 ubuntu kernel: [   53.673743] input: Dell WMI hotkeys as /devices/virtual/input/input7
Jan  7 21:26:23 ubuntu kernel: [   53.819237] lp: driver loaded but no devices found
Jan  7 21:26:23 ubuntu udev-configure-printer: add /module/lp
Jan  7 21:26:23 ubuntu udev-configure-printer: Failed to get parent
Jan  7 21:26:24 ubuntu anacron[923]: Anacron 2.3 started on 2014-01-07
Jan  7 21:26:24 ubuntu acpid: starting up with proc fs
Jan  7 21:26:24 ubuntu acpid: 35 rules loaded
Jan  7 21:26:24 ubuntu acpid: waiting for events: event logging is off
Jan  7 21:26:24 ubuntu cron[859]: (CRON) INFO (pidfile fd = 3)
Jan  7 21:26:24 ubuntu bluetoothd[719]: Failed to init gatt_example plugin
Jan  7 21:26:24 ubuntu kernel: [   54.441714] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Jan  7 21:26:24 ubuntu kernel: [   54.441720] Bluetooth: BNEP filters: protocol multicast
Jan  7 21:26:24 ubuntu kernel: [   54.444910] ppdev: user-space parallel port driver
Jan  7 21:26:24 ubuntu kernel: [   54.447376] Bluetooth: RFCOMM TTY layer initialized
Jan  7 21:26:24 ubuntu kernel: [   54.447387] Bluetooth: RFCOMM socket layer initialized
Jan  7 21:26:24 ubuntu kernel: [   54.447390] Bluetooth: RFCOMM ver 1.11
Jan  7 21:26:24 ubuntu cron[939]: (CRON) STARTUP (fork ok)
Jan  7 21:26:24 ubuntu kernel: [   54.529400] ACPI Warning: 0xf400b410-0xf400b414 SystemMemory conflicts with Region \RCRB 1 (20120320/utaddress-251)
Jan  7 21:26:24 ubuntu kernel: [   54.529413] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Jan  7 21:26:24 ubuntu kernel: [   54.529416] lpc_ich: Resource conflict(s) found affecting iTCO_wdt
Jan  7 21:26:24 ubuntu udev-configure-printer: add /bus/pci/drivers/lpc_ich
Jan  7 21:26:24 ubuntu udev-configure-printer: Failed to get parent
Jan  7 21:26:24 ubuntu udev-configure-printer: add /module/lpc_ich
Jan  7 21:26:24 ubuntu udev-configure-printer: Failed to get parent
Jan  7 21:26:24 ubuntu kernel: [   54.551740] psmouse serio1: synaptics: Touchpad model: 1, fw: 6.2, id: 0x180b1, caps: 0xa04713/0x200000/0x0
Jan  7 21:26:24 ubuntu kernel: [   54.587551] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
Jan  7 21:26:24 ubuntu cron[939]: (CRON) INFO (Running @reboot jobs)
Jan  7 21:26:24 ubuntu kernel: [   54.679243] r592 0000:03:01.2: setting latency timer to 64
Jan  7 21:26:24 ubuntu kernel: [   54.689624] audit_printk_skb: 33 callbacks suppressed
Jan  7 21:26:24 ubuntu kernel: [   54.689631] type=1400 audit(1389147984.565:23): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=964 comm="apparmor_parser"
Jan  7 21:26:24 ubuntu kernel: [   54.689918] r592: driver successfully loaded
Jan  7 21:26:24 ubuntu kernel: [   54.692570] type=1400 audit(1389147984.569:24): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=964 comm="apparmor_parser"
Jan  7 21:26:25 ubuntu anacron[923]: Will run job `cron.daily' in 5 min.
Jan  7 21:26:25 ubuntu anacron[923]: Jobs will be executed sequentially
Jan  7 21:26:25 ubuntu kernel: [   55.291262] [drm] Initialized drm 1.1.0 20060810
Jan  7 21:26:25 ubuntu kernel: [   55.317870] leds_ss4200: no LED devices found
Jan  7 21:26:25 ubuntu acpid: client connected from 951[0:0]
Jan  7 21:26:25 ubuntu acpid: 1 client rule loaded
Jan  7 21:26:25 ubuntu kernel: [   55.684950] gpio_ich: GPIO from 206 to 255 on gpio_ich
Jan  7 21:26:25 ubuntu kernel: [   55.924278] r852 0000:03:01.3: setting latency timer to 64
Jan  7 21:26:25 ubuntu kernel: [   55.924386] r852: Non dma capable device detected, dma disabled
Jan  7 21:26:25 ubuntu kernel: [   55.924403] r852: driver loaded successfully
Jan  7 21:26:26 ubuntu kernel: [   56.140289] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
Jan  7 21:26:26 ubuntu kernel: [   56.210057] Broadcom 43xx driver loaded [ Features: PNL ]
Jan  7 21:26:26 ubuntu kernel: [   56.224752] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
Jan  7 21:26:26 ubuntu kernel: [   56.224758] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  7 21:26:26 ubuntu kernel: [   56.224762] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
Jan  7 21:26:26 ubuntu kernel: [   56.224765] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  7 21:26:26 ubuntu kernel: [   56.224768] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
Jan  7 21:26:26 ubuntu kernel: [   56.224771] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  7 21:26:26 ubuntu kernel: [   56.224774] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
Jan  7 21:26:26 ubuntu kernel: [   56.224777] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  7 21:26:26 ubuntu kernel: [   56.224780] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
Jan  7 21:26:26 ubuntu kernel: [   56.224783] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  7 21:26:26 ubuntu kernel: [   56.224786] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
Jan  7 21:26:26 ubuntu kernel: [   56.224789] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  7 21:26:26 ubuntu kernel: [   56.224792] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
Jan  7 21:26:26 ubuntu kernel: [   56.224795] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  7 21:26:26 ubuntu kernel: [   56.224798] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
Jan  7 21:26:26 ubuntu kernel: [   56.224801] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  7 21:26:26 ubuntu kernel: [   56.224804] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
Jan  7 21:26:26 ubuntu kernel: [   56.224807] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  7 21:26:26 ubuntu kernel: [   56.224810] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
Jan  7 21:26:26 ubuntu kernel: [   56.224813] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  7 21:26:26 ubuntu kernel: [   56.224816] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
Jan  7 21:26:26 ubuntu kernel: [   56.224819] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  7 21:26:26 ubuntu kernel: [   56.224822] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
Jan  7 21:26:26 ubuntu kernel: [   56.224825] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jan  7 21:26:26 ubuntu kernel: [   56.224828] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
Jan  7 21:26:26 ubuntu kernel: [   56.224831] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jan  7 21:26:26 ubuntu kernel: [   56.224834] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
Jan  7 21:26:26 ubuntu kernel: [   56.224838] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jan  7 21:26:26 ubuntu NetworkManager[753]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:1c.0/0000:0b:00.0/ssb0:0/ieee80211/phy0/rfkill0) (driver (unknown))
Jan  7 21:26:26 ubuntu udev-configure-printer: add /module/lp
Jan  7 21:26:26 ubuntu udev-configure-printer: Failed to get parent
Jan  7 21:26:26 ubuntu udev-configure-printer: add /module/lpc_ich
Jan  7 21:26:26 ubuntu udev-configure-printer: Failed to get parent
Jan  7 21:26:27 ubuntu kernel: [   57.842657] snd_hda_intel 0000:00:1b.0: irq 43 for MSI/MSI-X
Jan  7 21:26:27 ubuntu kernel: [   57.850565] [drm] radeon defaulting to kernel modesetting.
Jan  7 21:26:27 ubuntu kernel: [   57.850572] [drm] radeon kernel modesetting enabled.
Jan  7 21:26:27 ubuntu kernel: [   57.851184] [drm] initializing kernel modesetting (RV515 0x1002:0x7145 0x1028:0x2003).
Jan  7 21:26:27 ubuntu kernel: [   57.851210] [drm] register mmio base: 0xEFDF0000
Jan  7 21:26:27 ubuntu kernel: [   57.851212] [drm] register mmio size: 65536
Jan  7 21:26:27 ubuntu kernel: [   57.851354] ATOM BIOS: M54P
Jan  7 21:26:27 ubuntu kernel: [   57.851380] [drm] Generation 2 PCI interface, using max accessible memory
Jan  7 21:26:27 ubuntu kernel: [   57.851389] radeon 0000:01:00.0: VRAM: 256M 0x0000000000000000 - 0x000000000FFFFFFF (128M used)
Jan  7 21:26:27 ubuntu kernel: [   57.851394] radeon 0000:01:00.0: GTT: 512M 0x0000000010000000 - 0x000000002FFFFFFF
Jan  7 21:26:27 ubuntu kernel: [   57.852501] [drm] Detected VRAM RAM=256M, BAR=256M
Jan  7 21:26:27 ubuntu kernel: [   57.852506] [drm] RAM width 64bits DDR
Jan  7 21:26:27 ubuntu kernel: [   57.852588] [TTM] Zone  kernel: Available graphics memory: 435614 kiB
Jan  7 21:26:27 ubuntu kernel: [   57.852591] [TTM] Zone highmem: Available graphics memory: 1551176 kiB
Jan  7 21:26:27 ubuntu kernel: [   57.852594] [TTM] Initializing pool allocator
Jan  7 21:26:27 ubuntu kernel: [   57.852600] [TTM] Initializing DMA pool allocator
Jan  7 21:26:27 ubuntu kernel: [   57.852635] [drm] radeon: 128M of VRAM memory ready
Jan  7 21:26:27 ubuntu kernel: [   57.852637] [drm] radeon: 512M of GTT memory ready.
Jan  7 21:26:27 ubuntu kernel: [   57.852661] [drm] GART: num cpu pages 131072, num gpu pages 131072
Jan  7 21:26:27 ubuntu kernel: [   57.855144] [drm] radeon: 1 quad pipes, 1 z pipes initialized.
Jan  7 21:26:27 ubuntu kernel: [   57.856969] [drm] PCIE GART of 512M enabled (table at 0x0000000000040000).
Jan  7 21:26:27 ubuntu kernel: [   57.857471] radeon 0000:01:00.0: WB enabled
Jan  7 21:26:27 ubuntu kernel: [   57.857477] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000010000000 and cpu addr 0xffdc3000
Jan  7 21:26:27 ubuntu kernel: [   57.857481] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
Jan  7 21:26:27 ubuntu kernel: [   57.857484] [drm] Driver supports precise vblank timestamp query.
Jan  7 21:26:27 ubuntu kernel: [   57.857521] [drm] radeon: irq initialized.
Jan  7 21:26:27 ubuntu kernel: [   57.858288] [drm] Loading R500 Microcode
Jan  7 21:26:27 ubuntu kernel: [   57.862034] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
Jan  7 21:26:27 ubuntu kernel: [   57.862498] Registered led device: b43-phy0::tx
Jan  7 21:26:27 ubuntu kernel: [   57.862530] Registered led device: b43-phy0::rx
Jan  7 21:26:27 ubuntu kernel: [   57.862560] Registered led device: b43-phy0::radio
Jan  7 21:26:27 ubuntu kernel: [   57.869461] [drm] radeon: ring at 0x0000000010001000
Jan  7 21:26:27 ubuntu kernel: [   57.869502] [drm] ring test succeeded in 9 usecs
Jan  7 21:26:27 ubuntu kernel: [   57.869776] [drm] ib test succeeded in 0 usecs
Jan  7 21:26:27 ubuntu kernel: [   57.871112] [drm] radeon atom DIG backlight initialized
Jan  7 21:26:27 ubuntu kernel: [   57.871117] [drm] Radeon Display Connectors
Jan  7 21:26:27 ubuntu kernel: [   57.871120] [drm] Connector 0:
Jan  7 21:26:27 ubuntu kernel: [   57.871122] [drm]   VGA-1
Jan  7 21:26:27 ubuntu kernel: [   57.871126] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
Jan  7 21:26:27 ubuntu kernel: [   57.871128] [drm]   Encoders:
Jan  7 21:26:27 ubuntu kernel: [   57.871131] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
Jan  7 21:26:27 ubuntu kernel: [   57.871133] [drm] Connector 1:
Jan  7 21:26:27 ubuntu kernel: [   57.871136] [drm]   LVDS-1
Jan  7 21:26:27 ubuntu kernel: [   57.871139] [drm]   DDC: 0x7e30 0x7e30 0x7e34 0x7e34 0x7e38 0x7e38 0x7e3c 0x7e3c
Jan  7 21:26:27 ubuntu kernel: [   57.871141] [drm]   Encoders:
Jan  7 21:26:27 ubuntu kernel: [   57.871144] [drm]     LCD1: INTERNAL_LVTM1
Jan  7 21:26:27 ubuntu kernel: [   57.871146] [drm] Connector 2:
Jan  7 21:26:27 ubuntu kernel: [   57.871148] [drm]   SVIDEO-1
Jan  7 21:26:27 ubuntu kernel: [   57.871150] [drm]   Encoders:
Jan  7 21:26:27 ubuntu kernel: [   57.871152] [drm]     TV1: INTERNAL_KLDSCP_DAC2
Jan  7 21:26:27 ubuntu kernel: [   57.871175] [drm] radeon: power management initialized
Jan  7 21:26:27 ubuntu NetworkManager[753]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:0b:00.0/ssb0:0/net/wlan0, iface: wlan0)
Jan  7 21:26:27 ubuntu NetworkManager[753]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:0b:00.0/ssb0:0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jan  7 21:26:27 ubuntu NetworkManager[753]: <info> (wlan0): using nl80211 for WiFi device control
Jan  7 21:26:27 ubuntu NetworkManager[753]: <warn> (wlan0): driver supports Access Point (AP) mode
Jan  7 21:26:27 ubuntu NetworkManager[753]: <info> (wlan0): new 802.11 WiFi device (driver: 'b43' ifindex: 3)
Jan  7 21:26:27 ubuntu NetworkManager[753]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Jan  7 21:26:27 ubuntu NetworkManager[753]: <info> (wlan0): now managed
Jan  7 21:26:27 ubuntu NetworkManager[753]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jan  7 21:26:27 ubuntu NetworkManager[753]: <info> (wlan0): bringing up device.
Jan  7 21:26:27 ubuntu kernel: [   57.925342] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
Jan  7 21:26:27 ubuntu kernel: [   57.925640] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
Jan  7 21:26:27 ubuntu kernel: [   58.048054] b43-phy0: Loading firmware version 508.1084 (2009-01-14 01:32:01)
Jan  7 21:26:28 ubuntu NetworkManager[753]: <info> (wlan0): preparing device.
Jan  7 21:26:28 ubuntu NetworkManager[753]: <info> (wlan0): deactivating device (reason 'managed') [2]
Jan  7 21:26:28 ubuntu dbus[704]: [system] Activating service name='fi.w1.wpa_supplicant1' (using servicehelper)
Jan  7 21:26:28 ubuntu kernel: [   58.140617] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan  7 21:26:28 ubuntu kernel: [   58.141281] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan  7 21:26:28 ubuntu dbus[704]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'
Jan  7 21:26:28 ubuntu NetworkManager[753]: <info> wpa_supplicant started
Jan  7 21:26:28 ubuntu NetworkManager[753]: <info> (wlan0): supplicant interface state: starting -> ready
Jan  7 21:26:28 ubuntu NetworkManager[753]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jan  7 21:26:28 ubuntu NetworkManager[753]: <info> (wlan0): supplicant interface state: ready -> inactive
Jan  7 21:26:28 ubuntu NetworkManager[753]: <warn> Trying to remove a non-existant call id.
Jan  7 21:26:28 ubuntu kernel: [   58.346755] [drm] fb mappable at 0xD00C0000
Jan  7 21:26:28 ubuntu kernel: [   58.346761] [drm] vram apper at 0xD0000000
Jan  7 21:26:28 ubuntu kernel: [   58.346763] [drm] size 4096000
Jan  7 21:26:28 ubuntu kernel: [   58.346765] [drm] fb depth is 24
Jan  7 21:26:28 ubuntu kernel: [   58.346767] [drm]    pitch is 5120
Jan  7 21:26:28 ubuntu kernel: [   58.347023] fbcon: radeondrmfb (fb0) is primary device
Jan  7 21:26:28 ubuntu kernel: [   58.348354] Console: switching to colour frame buffer device 160x50
Jan  7 21:26:28 ubuntu kernel: [   58.348371] fb0: radeondrmfb frame buffer device
Jan  7 21:26:28 ubuntu kernel: [   58.348374] drm: registered panic notifier
Jan  7 21:26:28 ubuntu kernel: [   58.348397] [drm] Initialized radeon 2.18.0 20080528 for 0000:01:00.0 on minor 0
Jan  7 21:26:29 ubuntu dbus[704]: [system] Activating service name='org.freedesktop.Accounts' (using servicehelper)
Jan  7 21:26:29 ubuntu dbus[704]: [system] Successfully activated service 'org.freedesktop.Accounts'
Jan  7 21:26:29 ubuntu accounts-daemon[1163]: started daemon version 0.6.15
Jan  7 21:26:29 ubuntu NetworkManager[753]: <info> Auto-activating connection '8LGL3'.
Jan  7 21:26:29 ubuntu NetworkManager[753]: <info> Activation (wlan0) starting connection '8LGL3'
Jan  7 21:26:29 ubuntu NetworkManager[753]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jan  7 21:26:29 ubuntu NetworkManager[753]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jan  7 21:26:29 ubuntu NetworkManager[753]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jan  7 21:26:29 ubuntu NetworkManager[753]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jan  7 21:26:29 ubuntu NetworkManager[753]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jan  7 21:26:29 ubuntu NetworkManager[753]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jan  7 21:26:29 ubuntu NetworkManager[753]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jan  7 21:26:29 ubuntu NetworkManager[753]: <info> Activation (wlan0/wireless): connection '8LGL3' has security, and secrets exist.  No new secrets needed.
Jan  7 21:26:29 ubuntu NetworkManager[753]: <info> Config: added 'ssid' value '8LGL3'
Jan  7 21:26:29 ubuntu NetworkManager[753]: <info> Config: added 'scan_ssid' value '1'
Jan  7 21:26:29 ubuntu NetworkManager[753]: <info> Config: added 'key_mgmt' value 'NONE'
Jan  7 21:26:29 ubuntu NetworkManager[753]: <info> Config: added 'wep_key0' value '<omitted>'
Jan  7 21:26:29 ubuntu NetworkManager[753]: <info> Config: added 'wep_tx_keyidx' value '0'
Jan  7 21:26:29 ubuntu NetworkManager[753]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jan  7 21:26:29 ubuntu NetworkManager[753]: <info> Config: set interface ap_scan to 1
Jan  7 21:26:29 ubuntu NetworkManager[753]: <info> (wlan0): supplicant interface state: inactive -> scanning
Jan  7 21:26:30 ubuntu dbus[704]: [system] Activating service name='org.freedesktop.ConsoleKit' (using servicehelper)
Jan  7 21:26:30 ubuntu dbus[704]: [system] Successfully activated service 'org.freedesktop.ConsoleKit'
Jan  7 21:26:31 ubuntu wpa_supplicant[1144]: Trying to authenticate with 00:26:62:5c:2a:41 (SSID='8LGL3' freq=2412 MHz)
Jan  7 21:26:31 ubuntu kernel: [   61.261292] wlan0: authenticate with 00:26:62:5c:2a:41
Jan  7 21:26:31 ubuntu NetworkManager[753]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jan  7 21:26:31 ubuntu kernel: [   61.280380] wlan0: send auth to 00:26:62:5c:2a:41 (try 1/3)
Jan  7 21:26:31 ubuntu wpa_supplicant[1144]: Trying to associate with 00:26:62:5c:2a:41 (SSID='8LGL3' freq=2412 MHz)
Jan  7 21:26:31 ubuntu kernel: [   61.284777] wlan0: authenticated
Jan  7 21:26:31 ubuntu kernel: [   61.288068] wlan0: associate with 00:26:62:5c:2a:41 (try 1/3)
Jan  7 21:26:31 ubuntu NetworkManager[753]: <info> (wlan0): supplicant interface state: authenticating -> associating
Jan  7 21:26:31 ubuntu wpa_supplicant[1144]: Associated with 00:26:62:5c:2a:41
Jan  7 21:26:31 ubuntu wpa_supplicant[1144]: CTRL-EVENT-CONNECTED - Connection to 00:26:62:5c:2a:41 completed (auth) [id=0 id_str=]
Jan  7 21:26:31 ubuntu kernel: [   61.290696] wlan0: RX AssocResp from 00:26:62:5c:2a:41 (capab=0x431 status=0 aid=2)
Jan  7 21:26:31 ubuntu kernel: [   61.291176] wlan0: associated
Jan  7 21:26:31 ubuntu kernel: [   61.291393] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jan  7 21:26:31 ubuntu kernel: [   61.291476] cfg80211: Calling CRDA for country: US
Jan  7 21:26:31 ubuntu NetworkManager[753]: <info> (wlan0): supplicant interface state: associating -> completed
Jan  7 21:26:31 ubuntu NetworkManager[753]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network '8LGL3'.
Jan  7 21:26:31 ubuntu NetworkManager[753]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Jan  7 21:26:31 ubuntu NetworkManager[753]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Jan  7 21:26:31 ubuntu NetworkManager[753]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Jan  7 21:26:31 ubuntu NetworkManager[753]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jan  7 21:26:31 ubuntu kernel: [   61.298119] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
Jan  7 21:26:31 ubuntu kernel: [   61.298127] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jan  7 21:26:31 ubuntu kernel: [   61.298130] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
Jan  7 21:26:31 ubuntu kernel: [   61.298133] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jan  7 21:26:31 ubuntu kernel: [   61.298136] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
Jan  7 21:26:31 ubuntu kernel: [   61.298139] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jan  7 21:26:31 ubuntu kernel: [   61.298142] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
Jan  7 21:26:31 ubuntu kernel: [   61.298145] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jan  7 21:26:31 ubuntu kernel: [   61.298148] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
Jan  7 21:26:31 ubuntu kernel: [   61.298152] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jan  7 21:26:31 ubuntu kernel: [   61.298155] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
Jan  7 21:26:31 ubuntu kernel: [   61.298158] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jan  7 21:26:31 ubuntu kernel: [   61.298161] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
Jan  7 21:26:31 ubuntu kernel: [   61.298164] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jan  7 21:26:31 ubuntu kernel: [   61.298167] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
Jan  7 21:26:31 ubuntu kernel: [   61.298170] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jan  7 21:26:31 ubuntu kernel: [   61.298173] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
Jan  7 21:26:31 ubuntu kernel: [   61.298176] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jan  7 21:26:31 ubuntu kernel: [   61.298179] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
Jan  7 21:26:31 ubuntu kernel: [   61.298182] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jan  7 21:26:31 ubuntu kernel: [   61.298185] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
Jan  7 21:26:31 ubuntu kernel: [   61.298188] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jan  7 21:26:31 ubuntu kernel: [   61.298190] cfg80211: Disabling freq 2467 MHz
Jan  7 21:26:31 ubuntu kernel: [   61.298193] cfg80211: Disabling freq 2472 MHz
Jan  7 21:26:31 ubuntu kernel: [   61.298195] cfg80211: Disabling freq 2484 MHz
Jan  7 21:26:31 ubuntu kernel: [   61.298199] cfg80211: Regulatory domain changed to country: US
Jan  7 21:26:31 ubuntu kernel: [   61.298202] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jan  7 21:26:31 ubuntu kernel: [   61.298205] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jan  7 21:26:31 ubuntu kernel: [   61.298208] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
Jan  7 21:26:31 ubuntu kernel: [   61.298211] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  7 21:26:31 ubuntu kernel: [   61.298214] cfg80211:   (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  7 21:26:31 ubuntu kernel: [   61.298217] cfg80211:   (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  7 21:26:31 ubuntu kernel: [   61.298220] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
Jan  7 21:26:31 ubuntu NetworkManager[753]: <info> dhclient started with pid 1255
Jan  7 21:26:31 ubuntu NetworkManager[753]: <info> Activation (wlan0) Beginning IP6 addrconf.
Jan  7 21:26:31 ubuntu dhclient: Internet Systems Consortium DHCP Client 4.1-ESV-R4
Jan  7 21:26:31 ubuntu dhclient: Copyright 2004-2011 Internet Systems Consortium.
Jan  7 21:26:31 ubuntu dhclient: All rights reserved.
Jan  7 21:26:31 ubuntu dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Jan  7 21:26:31 ubuntu dhclient: 
Jan  7 21:26:31 ubuntu NetworkManager[753]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jan  7 21:26:31 ubuntu NetworkManager[753]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Jan  7 21:26:31 ubuntu dhclient: Listening on LPF/wlan0/00:19:7e:66:cd:ee
Jan  7 21:26:31 ubuntu dhclient: Sending on   LPF/wlan0/00:19:7e:66:cd:ee
Jan  7 21:26:31 ubuntu dhclient: Sending on   Socket/fallback
Jan  7 21:26:31 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Jan  7 21:26:32 ubuntu dhclient: DHCPREQUEST of 192.168.1.2 on wlan0 to 255.255.255.255 port 67
Jan  7 21:26:32 ubuntu dhclient: DHCPOFFER of 192.168.1.2 from 192.168.1.1
Jan  7 21:26:32 ubuntu dhclient: DHCPACK of 192.168.1.2 from 192.168.1.1
Jan  7 21:26:32 ubuntu NetworkManager[753]: <info> (wlan0): DHCPv4 state changed preinit -> bound
Jan  7 21:26:32 ubuntu NetworkManager[753]: <info>   address 192.168.1.2
Jan  7 21:26:32 ubuntu NetworkManager[753]: <info>   prefix 24 (255.255.255.0)
Jan  7 21:26:32 ubuntu NetworkManager[753]: <info>   gateway 192.168.1.1
Jan  7 21:26:32 ubuntu NetworkManager[753]: <info>   hostname 'ubuntu'
Jan  7 21:26:32 ubuntu NetworkManager[753]: <info>   nameserver '192.168.1.1'
Jan  7 21:26:32 ubuntu NetworkManager[753]: <info>   domain name 'home'
Jan  7 21:26:32 ubuntu NetworkManager[753]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Jan  7 21:26:32 ubuntu NetworkManager[753]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Jan  7 21:26:32 ubuntu dhclient: bound to 192.168.1.2 -- renewal in 40005 seconds.
Jan  7 21:26:33 ubuntu NetworkManager[753]: <info> DNS: starting dnsmasq...
Jan  7 21:26:33 ubuntu NetworkManager[753]: <error> [1389147993.661934] [nm-dns-dnsmasq.c:393] update(): dnsmasq not available on the bus, can't update servers.
Jan  7 21:26:33 ubuntu NetworkManager[753]: <error> [1389147993.661985] [nm-dns-dnsmasq.c:395] update(): dnsmasq owner not found on bus: Could not get owner of name 'uk.org.thekelleys.dnsmasq': no such name
Jan  7 21:26:33 ubuntu NetworkManager[753]: <warn> DNS: plugin dnsmasq update failed
Jan  7 21:26:33 ubuntu NetworkManager[753]: <info> (wlan0): writing resolv.conf to /sbin/resolvconf
Jan  7 21:26:33 ubuntu dnsmasq[1299]: started, version 2.59 cache disabled
Jan  7 21:26:33 ubuntu dnsmasq[1299]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
Jan  7 21:26:33 ubuntu dnsmasq[1299]: DBus support enabled: connected to system bus
Jan  7 21:26:33 ubuntu dnsmasq[1299]: warning: no upstream servers configured
Jan  7 21:26:33 ubuntu NetworkManager[753]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Jan  7 21:26:33 ubuntu NetworkManager[753]: <info> Policy set '8LGL3' (wlan0) as default for IPv4 routing and DNS.
Jan  7 21:26:33 ubuntu NetworkManager[753]: <info> Activation (wlan0) successful, device activated.
Jan  7 21:26:33 ubuntu NetworkManager[753]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Jan  7 21:26:33 ubuntu dbus[704]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Jan  7 21:26:33 ubuntu NetworkManager[753]: <warn> dnsmasq appeared on DBus: :1.20
Jan  7 21:26:33 ubuntu NetworkManager[753]: <info> (wlan0): writing resolv.conf to /sbin/resolvconf
Jan  7 21:26:33 ubuntu dnsmasq[1299]: setting upstream servers from DBus
Jan  7 21:26:33 ubuntu dnsmasq[1299]: using nameserver 192.168.1.1#53
Jan  7 21:26:33 ubuntu dbus[704]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jan  7 21:26:34 ubuntu ntpdate[1404]: Can't find host ntp.ubuntu.com: Name or service not known (-2)
Jan  7 21:26:34 ubuntu ntpdate[1404]: no servers can be used, exiting
Jan  7 21:26:39 ubuntu acpid: client 951[0:0] has disconnected
Jan  7 21:26:39 ubuntu acpid: client connected from 1431[0:0]
Jan  7 21:26:39 ubuntu acpid: 1 client rule loaded
Jan  7 21:26:51 ubuntu NetworkManager[753]: <info> (wlan0): IP6 addrconf timed out or failed.
Jan  7 21:26:51 ubuntu NetworkManager[753]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Jan  7 21:26:51 ubuntu NetworkManager[753]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Jan  7 21:26:51 ubuntu NetworkManager[753]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Jan  7 21:29:42 ubuntu kernel: imklog 5.8.6, log source = /proc/kmsg started.
Jan  7 21:29:42 ubuntu rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="630" x-info="http://www.rsyslog.com"] start
Jan  7 21:29:42 ubuntu rsyslogd: rsyslogd's groupid changed to 103
Jan  7 21:29:42 ubuntu rsyslogd: rsyslogd's userid changed to 101
Jan  7 21:29:42 ubuntu rsyslogd-2039: Could not open output pipe '/dev/xconsole' [try [http://www.rsyslog.com/e/2039](http://www.rsyslog.com/e/2039) ]
Jan  7 21:29:42 ubuntu modem-manager[721]: <info>  ModemManager (version 0.5.2.0) starting...
Jan  7 21:29:42 ubuntu modem-manager[721]: <info>  Loaded plugin Linktop
Jan  7 21:29:42 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpuset
Jan  7 21:29:42 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpu
Jan  7 21:29:42 ubuntu kernel: [    0.000000] Linux version 3.5.0-45-generic (buildd@allspice) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #68~precise1-Ubuntu SMP Wed Dec 4 16:19:28 UTC 2013 (Ubuntu 3.5.0-45.68~precise1-generic 3.5.7.26)
Jan  7 21:29:42 ubuntu kernel: [    0.000000] KERNEL supported cpus:
Jan  7 21:29:42 ubuntu kernel: [    0.000000]   Intel GenuineIntel
Jan  7 21:29:42 ubuntu kernel: [    0.000000]   AMD AuthenticAMD
Jan  7 21:29:42 ubuntu kernel: [    0.000000]   NSC Geode by NSC
Jan  7 21:29:42 ubuntu kernel: [    0.000000]   Cyrix CyrixInstead
Jan  7 21:29:42 ubuntu kernel: [    0.000000]   Centaur CentaurHauls
Jan  7 21:29:42 ubuntu kernel: [    0.000000]   Transmeta GenuineTMx86
Jan  7 21:29:42 ubuntu kernel: [    0.000000]   Transmeta TransmetaCPU
Jan  7 21:29:42 ubuntu kernel: [    0.000000]   UMC UMC UMC UMC
Jan  7 21:29:42 ubuntu kernel: [    0.000000] Disabled fast string operations
Jan  7 21:29:42 ubuntu kernel: [    0.000000] e820: BIOS-provided physical RAM map:
Jan  7 21:29:42 ubuntu kernel: [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009efff] usable
Jan  7 21:29:42 ubuntu kernel: [    0.000000] BIOS-e820: [mem 0x000000000009f000-0x000000000009ffff] reserved
Jan  7 21:29:42 ubuntu kernel: [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000bfed33ff] usable
Jan  7 21:29:42 ubuntu kernel: [    0.000000] BIOS-e820: [mem 0x00000000bfed3400-0x00000000bfffffff] reserved
Jan  7 21:29:42 ubuntu kernel: [    0.000000] BIOS-e820: [mem 0x00000000f0000000-0x00000000f4006fff] reserved
Jan  7 21:29:42 ubuntu kernel: [    0.000000] BIOS-e820: [mem 0x00000000f4008000-0x00000000f400bfff] reserved
Jan  7 21:29:42 ubuntu kernel: [    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec0ffff] reserved
Jan  7 21:29:42 ubuntu kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed20000-0x00000000fed9ffff] reserved
Jan  7 21:29:42 ubuntu kernel: [    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee0ffff] reserved
Jan  7 21:29:42 ubuntu kernel: [    0.000000] BIOS-e820: [mem 0x00000000ffb00000-0x00000000ffffffff] reserved
Jan  7 21:29:42 ubuntu kernel: [    0.000000] NX (Execute Disable) protection: active
Jan  7 21:29:42 ubuntu kernel: [    0.000000] SMBIOS 2.4 present.
Jan  7 21:29:42 ubuntu kernel: [    0.000000] DMI: Dell Inc. MM061                           /0XD720, BIOS A17 06/13/2007
Jan  7 21:29:42 ubuntu kernel: [    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
Jan  7 21:29:42 ubuntu kernel: [    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
Jan  7 21:29:42 ubuntu kernel: [    0.000000] e820: last_pfn = 0xbfed3 max_arch_pfn = 0x1000000
Jan  7 21:29:42 ubuntu kernel: [    0.000000] MTRR default type: uncachable
Jan  7 21:29:42 ubuntu kernel: [    0.000000] MTRR fixed ranges enabled:
Jan  7 21:29:42 ubuntu kernel: [    0.000000]   00000-9FFFF write-back
Jan  7 21:29:42 ubuntu kernel: [    0.000000]   A0000-BFFFF uncachable
Jan  7 21:29:42 ubuntu kernel: [    0.000000]   C0000-CFFFF write-protect
Jan  7 21:29:42 ubuntu kernel: [    0.000000]   D0000-EFFFF uncachable
Jan  7 21:29:42 ubuntu kernel: [    0.000000]   F0000-FFFFF write-protect
Jan  7 21:29:42 ubuntu kernel: [    0.000000] MTRR variable ranges enabled:
Jan  7 21:29:42 ubuntu kernel: [    0.000000]   0 base 000000000 mask F80000000 write-back
Jan  7 21:29:42 ubuntu kernel: [    0.000000]   1 base 080000000 mask FC0000000 write-back
Jan  7 21:29:42 ubuntu kernel: [    0.000000]   2 base 0BFF00000 mask FFFF00000 uncachable
Jan  7 21:29:42 ubuntu kernel: [    0.000000]   3 disabled
Jan  7 21:29:42 ubuntu kernel: [    0.000000]   4 disabled
Jan  7 21:29:42 ubuntu kernel: [    0.000000]   5 disabled
Jan  7 21:29:42 ubuntu kernel: [    0.000000]   6 disabled
Jan  7 21:29:42 ubuntu kernel: [    0.000000]   7 disabled
Jan  7 21:29:42 ubuntu kernel: [    0.000000] PAT not supported by CPU.
Jan  7 21:29:42 ubuntu kernel: [    0.000000] original variable MTRRs
Jan  7 21:29:42 ubuntu kernel: [    0.000000] reg 0, base: 0GB, range: 2GB, type WB
Jan  7 21:29:42 ubuntu kernel: [    0.000000] reg 1, base: 2GB, range: 1GB, type WB
Jan  7 21:29:42 ubuntu kernel: [    0.000000] reg 2, base: 3071MB, range: 1MB, type UC
Jan  7 21:29:42 ubuntu kernel: [    0.000000] total RAM covered: 3071M
Jan  7 21:29:42 ubuntu kernel: [    0.000000] Found optimal setting for mtrr clean up
Jan  7 21:29:42 ubuntu kernel: [    0.000000]  gran_size: 64K 	chunk_size: 2M 	num_reg: 3  	lose cover RAM: 0G
Jan  7 21:29:42 ubuntu kernel: [    0.000000] New variable MTRRs
Jan  7 21:29:42 ubuntu kernel: [    0.000000] reg 0, base: 0GB, range: 2GB, type WB
Jan  7 21:29:42 ubuntu kernel: [    0.000000] reg 1, base: 2GB, range: 1GB, type WB
Jan  7 21:29:42 ubuntu kernel: [    0.000000] reg 2, base: 3071MB, range: 1MB, type UC
Jan  7 21:29:42 ubuntu kernel: [    0.000000] initial memory mapped: [mem 0x00000000-0x01ffffff]
Jan  7 21:29:42 ubuntu kernel: [    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
Jan  7 21:29:42 ubuntu kernel: [    0.000000] init_memory_mapping: [mem 0x00000000-0x37bfdfff]
Jan  7 21:29:42 ubuntu kernel: [    0.000000]  [mem 0x00000000-0x001fffff] page 4k
Jan  7 21:29:42 ubuntu kernel: [    0.000000]  [mem 0x00200000-0x379fffff] page 2M
Jan  7 21:29:42 ubuntu kernel: [    0.000000]  [mem 0x37a00000-0x37bfdfff] page 4k
Jan  7 21:29:42 ubuntu kernel: [    0.000000] kernel direct mapping tables up to 0x37bfdfff @ [mem 0x01ffa000-0x01ffffff]
Jan  7 21:29:42 ubuntu kernel: [    0.000000] RAMDISK: [mem 0x36248000-0x3711bfff]
Jan  7 21:29:42 ubuntu kernel: [    0.000000] ACPI: RSDP 000fc1d0 00014 (v00 DELL  )
Jan  7 21:29:42 ubuntu kernel: [    0.000000] ACPI: RSDT bfed39cd 00040 (v01 DELL    M07     27D7060D ASL  00000061)
Jan  7 21:29:42 ubuntu kernel: [    0.000000] ACPI: FACP bfed4800 00074 (v01 DELL    M07     27D7060D ASL  00000061)
Jan  7 21:29:42 ubuntu kernel: [    0.000000] ACPI: DSDT bfed5400 04766 (v01 INT430 SYSFexxx 00001001 INTL 20050624)
Jan  7 21:29:42 ubuntu kernel: [    0.000000] ACPI: FACS bfee3c00 00040
Jan  7 21:29:42 ubuntu kernel: [    0.000000] ACPI: HPET bfed4f00 00038 (v01 DELL    M07     00000001 ASL  00000061)
Jan  7 21:29:42 ubuntu kernel: [    0.000000] ACPI: APIC bfed5000 00068 (v01 DELL    M07     27D7060D ASL  00000047)
Jan  7 21:29:42 ubuntu kernel: [    0.000000] ACPI: MCFG bfed4fc0 0003E (v16 DELL    M07     27D7060D ASL  00000061)
Jan  7 21:29:42 ubuntu kernel: [    0.000000] ACPI: SLIC bfed509c 00176 (v01 DELL    M07     27D7060D ASL  00000061)
Jan  7 21:29:42 ubuntu kernel: [    0.000000] ACPI: BOOT bfed4bc0 00028 (v01 DELL    M07     27D7060D ASL  00000061)
Jan  7 21:29:42 ubuntu kernel: [    0.000000] ACPI: SSDT bfed3a0d 004DC (v01  PmRef    CpuPm 00003000 INTL 20050624)
Jan  7 21:29:42 ubuntu kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jan  7 21:29:42 ubuntu kernel: [    0.000000] 2178MB HIGHMEM available.
Jan  7 21:29:42 ubuntu kernel: [    0.000000] 891MB LOWMEM available.
Jan  7 21:29:42 ubuntu kernel: [    0.000000]   mapped low ram: 0 - 37bfe000
Jan  7 21:29:42 ubuntu kernel: [    0.000000]   low ram: 0 - 37bfe000
Jan  7 21:29:42 ubuntu kernel: [    0.000000] Zone ranges:
Jan  7 21:29:42 ubuntu kernel: [    0.000000]   DMA      [mem 0x00010000-0x00ffffff]
Jan  7 21:29:42 ubuntu kernel: [    0.000000]   Normal   [mem 0x01000000-0x37bfdfff]
Jan  7 21:29:42 ubuntu kernel: [    0.000000]   HighMem  [mem 0x37bfe000-0xbfed2fff]
Jan  7 21:29:42 ubuntu kernel: [    0.000000] Movable zone start for each node
Jan  7 21:29:42 ubuntu kernel: [    0.000000] Early memory node ranges
Jan  7 21:29:42 ubuntu kernel: [    0.000000]   node   0: [mem 0x00010000-0x0009efff]
Jan  7 21:29:42 ubuntu kernel: [    0.000000]   node   0: [mem 0x00100000-0xbfed2fff]
Jan  7 21:29:42 ubuntu kernel: [    0.000000] On node 0 totalpages: 786018
Jan  7 21:29:42 ubuntu kernel: [    0.000000] free_area_init_node: node 0, pgdat c18c85c0, node_mem_map f4a48200
Jan  7 21:29:42 ubuntu kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Jan  7 21:29:42 ubuntu kernel: [    0.000000]   DMA zone: 0 pages reserved
Jan  7 21:29:42 ubuntu kernel: [    0.000000]   DMA zone: 3951 pages, LIFO batch:0
Jan  7 21:29:42 ubuntu kernel: [    0.000000]   Normal zone: 1752 pages used for memmap
Jan  7 21:29:42 ubuntu kernel: [    0.000000]   Normal zone: 222502 pages, LIFO batch:31
Jan  7 21:29:42 ubuntu kernel: [    0.000000]   HighMem zone: 4358 pages used for memmap
Jan  7 21:29:42 ubuntu kernel: [    0.000000]   HighMem zone: 553423 pages, LIFO batch:31
Jan  7 21:29:42 ubuntu kernel: [    0.000000] Using APIC driver default
Jan  7 21:29:42 ubuntu kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Jan  7 21:29:42 ubuntu kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jan  7 21:29:42 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jan  7 21:29:42 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Jan  7 21:29:42 ubuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Jan  7 21:29:42 ubuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Jan  7 21:29:42 ubuntu kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Jan  7 21:29:42 ubuntu kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Jan  7 21:29:42 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jan  7 21:29:42 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jan  7 21:29:42 ubuntu kernel: [    0.000000] ACPI: IRQ0 used by override.
Jan  7 21:29:42 ubuntu kernel: [    0.000000] ACPI: IRQ2 used by override.
Jan  7 21:29:42 ubuntu kernel: [    0.000000] ACPI: IRQ9 used by override.
Jan  7 21:29:42 ubuntu kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jan  7 21:29:42 ubuntu kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Jan  7 21:29:42 ubuntu kernel: [    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
Jan  7 21:29:42 ubuntu kernel: [    0.000000] nr_irqs_gsi: 40
Jan  7 21:29:42 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jan  7 21:29:42 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 0000000000100000
Jan  7 21:29:42 ubuntu kernel: [    0.000000] e820: [mem 0xc0000000-0xefffffff] available for PCI devices
Jan  7 21:29:42 ubuntu kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Jan  7 21:29:42 ubuntu kernel: [    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
Jan  7 21:29:42 ubuntu kernel: [    0.000000] PERCPU: Embedded 14 pages/cpu @f7bcf000 s34176 r0 d23168 u57344
Jan  7 21:29:42 ubuntu kernel: [    0.000000] pcpu-alloc: s34176 r0 d23168 u57344 alloc=14*4096
Jan  7 21:29:42 ubuntu kernel: [    0.000000] pcpu-alloc: [0] 0 [0] 1 
Jan  7 21:29:42 ubuntu kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 779876
Jan  7 21:29:42 ubuntu kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-45-generic root=UUID=00D2D857D2D85290 loop=/ubuntu/disks/root.disk ro quiet splash vt.handoff=7
Jan  7 21:29:42 ubuntu kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Jan  7 21:29:42 ubuntu kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Jan  7 21:29:42 ubuntu kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Jan  7 21:29:42 ubuntu kernel: [    0.000000] __ex_table already sorted, skipping sort
Jan  7 21:29:42 ubuntu kernel: [    0.000000] Initializing CPU#0
Jan  7 21:29:42 ubuntu kernel: [    0.000000] allocated 6288920 bytes of page_cgroup
Jan  7 21:29:42 ubuntu kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Jan  7 21:29:42 ubuntu kernel: [    0.000000] Initializing HighMem for node 0 (00037bfe:000bfed3)
Jan  7 21:29:42 ubuntu kernel: [    0.000000] Memory: 3086404k/3144524k available (6061k kernel code, 57668k reserved, 2983k data, 764k init, 2231124k highmem)
Jan  7 21:29:42 ubuntu kernel: [    0.000000] virtual kernel memory layout:
Jan  7 21:29:42 ubuntu kernel: [    0.000000]     fixmap  : 0xfff15000 - 0xfffff000   ( 936 kB)
Jan  7 21:29:42 ubuntu kernel: [    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
Jan  7 21:29:42 ubuntu kernel: [    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
Jan  7 21:29:42 ubuntu kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
Jan  7 21:29:42 ubuntu kernel: [    0.000000]       .init : 0xc18d6000 - 0xc1995000   ( 764 kB)
Jan  7 21:29:42 ubuntu kernel: [    0.000000]       .data : 0xc15eb595 - 0xc18d54c0   (2983 kB)
Jan  7 21:29:42 ubuntu kernel: [    0.000000]       .text : 0xc1000000 - 0xc15eb595   (6061 kB)
Jan  7 21:29:42 ubuntu kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Jan  7 21:29:42 ubuntu kernel: [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Jan  7 21:29:42 ubuntu kernel: [    0.000000] Hierarchical RCU implementation.
Jan  7 21:29:42 ubuntu kernel: [    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
Jan  7 21:29:42 ubuntu kernel: [    0.000000] NR_IRQS:2304 nr_irqs:512 16
Jan  7 21:29:42 ubuntu kernel: [    0.000000] CPU 0 irqstacks, hard=f4408000 soft=f440a000
Jan  7 21:29:42 ubuntu kernel: [    0.000000] vt handoff: transparent VT on vt#7
Jan  7 21:29:42 ubuntu kernel: [    0.000000] Console: colour dummy device 80x25
Jan  7 21:29:42 ubuntu kernel: [    0.000000] console [tty0] enabled
Jan  7 21:29:42 ubuntu kernel: [    0.000000] hpet clockevent registered
Jan  7 21:29:42 ubuntu kernel: [    0.000000] Fast TSC calibration using PIT
Jan  7 21:29:42 ubuntu kernel: [    0.000000] Detected 1728.885 MHz processor.
Jan  7 21:29:42 ubuntu kernel: [    0.004002] Calibrating delay loop (skipped), value calculated using timer frequency.. 3457.77 BogoMIPS (lpj=6915540)
Jan  7 21:29:42 ubuntu kernel: [    0.004008] pid_max: default: 32768 minimum: 301
Jan  7 21:29:42 ubuntu kernel: [    0.004041] Security Framework initialized
Jan  7 21:29:42 ubuntu kernel: [    0.004062] AppArmor: AppArmor initialized
Jan  7 21:29:42 ubuntu kernel: [    0.004065] Yama: becoming mindful.
Jan  7 21:29:42 ubuntu kernel: [    0.004166] Mount-cache hash table entries: 512
Jan  7 21:29:42 ubuntu kernel: [    0.008046] Initializing cgroup subsys cpuacct
Jan  7 21:29:42 ubuntu kernel: [    0.008051] Initializing cgroup subsys memory
Jan  7 21:29:42 ubuntu kernel: [    0.008064] Initializing cgroup subsys devices
Jan  7 21:29:42 ubuntu kernel: [    0.008068] Initializing cgroup subsys freezer
Jan  7 21:29:42 ubuntu kernel: [    0.008071] Initializing cgroup subsys blkio
Jan  7 21:29:42 ubuntu kernel: [    0.008074] Initializing cgroup subsys perf_event
Jan  7 21:29:42 ubuntu kernel: [    0.008114] Disabled fast string operations
Jan  7 21:29:42 ubuntu kernel: [    0.008120] CPU: Physical Processor ID: 0
Jan  7 21:29:42 ubuntu kernel: [    0.008123] CPU: Processor Core ID: 0
Jan  7 21:29:42 ubuntu kernel: [    0.008127] mce: CPU supports 6 MCE banks
Jan  7 21:29:42 ubuntu kernel: [    0.008139] CPU0: Thermal monitoring enabled (TM2)
Jan  7 21:29:42 ubuntu kernel: [    0.008143] using mwait in idle threads.
Jan  7 21:29:42 ubuntu kernel: [    0.012060] ACPI: Core revision 20120320
Jan  7 21:29:42 ubuntu kernel: [    0.016964] ftrace: allocating 27163 entries in 54 pages
Jan  7 21:29:42 ubuntu kernel: [    0.028095] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Jan  7 21:29:42 ubuntu kernel: [    0.028577] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Jan  7 21:29:42 ubuntu kernel: [    0.071277] CPU0: Genuine Intel(R) CPU           T2080  @ 1.73GHz stepping 0c
Jan  7 21:29:42 ubuntu kernel: [    0.072003] Performance Events: Core events, core PMU driver.
Jan  7 21:29:42 ubuntu kernel: [    0.072003] ... version:                1
Jan  7 21:29:42 ubuntu kernel: [    0.072003] ... bit width:              40
Jan  7 21:29:42 ubuntu kernel: [    0.072003] ... generic registers:      2
Jan  7 21:29:42 ubuntu kernel: [    0.072003] ... value mask:             000000ffffffffff
Jan  7 21:29:42 ubuntu kernel: [    0.072003] ... max period:             000000007fffffff
Jan  7 21:29:42 ubuntu kernel: [    0.072003] ... fixed-purpose events:   0
Jan  7 21:29:42 ubuntu kernel: [    0.072003] ... event mask:             0000000000000003
Jan  7 21:29:42 ubuntu kernel: [    0.072003] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
Jan  7 21:29:42 ubuntu kernel: [    0.072003] CPU 1 irqstacks, hard=f44c8000 soft=f44ca000
Jan  7 21:29:42 ubuntu kernel: [    0.072003] Booting Node   0, Processors  #1 Ok.
Jan  7 21:29:42 ubuntu kernel: [    0.008000] Initializing CPU#1
Jan  7 21:29:42 ubuntu kernel: [    0.008000] Disabled fast string operations
Jan  7 21:29:42 ubuntu kernel: [    0.080004] TSC synchronization [CPU#0 -> CPU#1]:
Jan  7 21:29:42 ubuntu kernel: [    0.080004] Measured 3485865591 cycles TSC warp between CPUs, turning off TSC clock.
Jan  7 21:29:42 ubuntu kernel: [    0.080004] Marking TSC unstable due to check_tsc_sync_source failed
Jan  7 21:29:42 ubuntu kernel: [    0.080110] Brought up 2 CPUs
Jan  7 21:29:42 ubuntu kernel: [    0.080114] Total of 2 processors activated (6915.54 BogoMIPS).
Jan  7 21:29:42 ubuntu kernel: [    0.081230] devtmpfs: initialized
Jan  7 21:29:42 ubuntu kernel: [    0.081230] EVM: security.selinux
Jan  7 21:29:42 ubuntu kernel: [    0.081230] EVM: security.SMACK64
Jan  7 21:29:42 ubuntu kernel: [    0.081230] EVM: security.capability
Jan  7 21:29:42 ubuntu kernel: [    0.084869] dummy: 
Jan  7 21:29:42 ubuntu kernel: [    0.084917] RTC time: 21:28:52, date: 01/07/14
Jan  7 21:29:42 ubuntu kernel: [    0.084981] NET: Registered protocol family 16
Jan  7 21:29:42 ubuntu kernel: [    0.084997] Trying to unpack rootfs image as initramfs...
Jan  7 21:29:42 ubuntu kernel: [    0.085228] EISA bus registered
Jan  7 21:29:42 ubuntu kernel: [    0.085359] ACPI: bus type pci registered
Jan  7 21:29:42 ubuntu kernel: [    0.085459] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf0000000-0xf3ffffff] (base 0xf0000000)
Jan  7 21:29:42 ubuntu kernel: [    0.085464] PCI: MMCONFIG at [mem 0xf0000000-0xf3ffffff] reserved in E820
Jan  7 21:29:42 ubuntu kernel: [    0.085466] PCI: Using MMCONFIG for extended config space
Jan  7 21:29:42 ubuntu kernel: [    0.085469] PCI: Using configuration type 1 for base access
Jan  7 21:29:42 ubuntu kernel: [    0.085483] dmi type 0xB1 record - unknown flag
Jan  7 21:29:42 ubuntu kernel: [    0.100182] bio: create slab <bio-0> at 0
Jan  7 21:29:42 ubuntu kernel: [    0.100325] ACPI: Added _OSI(Module Device)
Jan  7 21:29:42 ubuntu kernel: [    0.100328] ACPI: Added _OSI(Processor Device)
Jan  7 21:29:42 ubuntu kernel: [    0.100332] ACPI: Added _OSI(3.0 _SCP Extensions)
Jan  7 21:29:42 ubuntu kernel: [    0.100335] ACPI: Added _OSI(Processor Aggregator Device)
Jan  7 21:29:42 ubuntu kernel: [    0.102006] ACPI: EC: Look up EC in DSDT
Jan  7 21:29:42 ubuntu kernel: [    0.108795] ACPI: SSDT bfed4134 00244 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
Jan  7 21:29:42 ubuntu kernel: [    0.109220] ACPI: Dynamic OEM Table Load:
Jan  7 21:29:42 ubuntu kernel: [    0.109225] ACPI: SSDT   (null) 00244 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
Jan  7 21:29:42 ubuntu kernel: [    0.109369] ACPI: SSDT bfed3ee9 001C6 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
Jan  7 21:29:42 ubuntu kernel: [    0.109764] ACPI: Dynamic OEM Table Load:
Jan  7 21:29:42 ubuntu kernel: [    0.109769] ACPI: SSDT   (null) 001C6 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
Jan  7 21:29:42 ubuntu kernel: [    0.110082] ACPI: SSDT bfed4378 000C4 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
Jan  7 21:29:42 ubuntu kernel: [    0.110490] ACPI: Dynamic OEM Table Load:
Jan  7 21:29:42 ubuntu kernel: [    0.110495] ACPI: SSDT   (null) 000C4 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
Jan  7 21:29:42 ubuntu kernel: [    0.110620] ACPI: SSDT bfed40af 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
Jan  7 21:29:42 ubuntu kernel: [    0.111017] ACPI: Dynamic OEM Table Load:
Jan  7 21:29:42 ubuntu kernel: [    0.111021] ACPI: SSDT   (null) 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
Jan  7 21:29:42 ubuntu kernel: [    0.111285] ACPI: Interpreter enabled
Jan  7 21:29:42 ubuntu kernel: [    0.111297] ACPI: (supports S0 S3 S4 S5)
Jan  7 21:29:42 ubuntu kernel: [    0.111324] ACPI: Using IOAPIC for interrupt routing
Jan  7 21:29:42 ubuntu kernel: [    0.136500] ACPI: No dock devices found.
Jan  7 21:29:42 ubuntu kernel: [    0.136515] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
Jan  7 21:29:42 ubuntu kernel: [    0.144449] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Jan  7 21:29:42 ubuntu kernel: [    0.158767] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
Jan  7 21:29:42 ubuntu kernel: [    0.158774] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
Jan  7 21:29:42 ubuntu kernel: [    0.158778] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
Jan  7 21:29:42 ubuntu kernel: [    0.158782] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff] (ignored)
Jan  7 21:29:42 ubuntu kernel: [    0.158786] pci_root PNP0A03:00: host bridge window [mem 0xc0000000-0xefffffff] (ignored)
Jan  7 21:29:42 ubuntu kernel: [    0.158790] pci_root PNP0A03:00: host bridge window [mem 0xf4007000-0xf4007fff] (ignored)
Jan  7 21:29:42 ubuntu kernel: [    0.158794] pci_root PNP0A03:00: host bridge window [mem 0xf400c000-0xfebfffff] (ignored)
Jan  7 21:29:42 ubuntu kernel: [    0.158798] pci_root PNP0A03:00: host bridge window [mem 0xfec10000-0xfecfffff] (ignored)
Jan  7 21:29:42 ubuntu kernel: [    0.158802] pci_root PNP0A03:00: host bridge window [mem 0xfed00400-0xfed1ffff] (ignored)
Jan  7 21:29:42 ubuntu kernel: [    0.158806] pci_root PNP0A03:00: host bridge window [mem 0xfee10000-0xffafffff] (ignored)
Jan  7 21:29:42 ubuntu kernel: [    0.158811] PCI: root bus 00: using default resources
Jan  7 21:29:42 ubuntu kernel: [    0.158895] PCI host bridge to bus 0000:00
Jan  7 21:29:42 ubuntu kernel: [    0.158900] pci_bus 0000:00: root bus resource [io  0x0000-0xffff]
Jan  7 21:29:42 ubuntu kernel: [    0.158904] pci_bus 0000:00: root bus resource [mem 0x00000000-0xffffffff]
Jan  7 21:29:42 ubuntu kernel: [    0.158921] pci 0000:00:00.0: [8086:27a0] type 00 class 0x060000
Jan  7 21:29:42 ubuntu kernel: [    0.158994] pci 0000:00:01.0: [8086:27a1] type 01 class 0x060400
Jan  7 21:29:42 ubuntu kernel: [    0.159060] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
Jan  7 21:29:42 ubuntu kernel: [    0.159142] pci 0000:00:1b.0: [8086:27d8] type 00 class 0x040300
Jan  7 21:29:42 ubuntu kernel: [    0.159171] pci 0000:00:1b.0: reg 10: [mem 0xefffc000-0xefffffff 64bit]
Jan  7 21:29:42 ubuntu kernel: [    0.159295] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Jan  7 21:29:42 ubuntu kernel: [    0.159334] pci 0000:00:1c.0: [8086:27d0] type 01 class 0x060400
Jan  7 21:29:42 ubuntu kernel: [    0.159464] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Jan  7 21:29:42 ubuntu kernel: [    0.159510] pci 0000:00:1c.3: [8086:27d6] type 01 class 0x060400
Jan  7 21:29:42 ubuntu kernel: [    0.159641] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
Jan  7 21:29:42 ubuntu kernel: [    0.159684] pci 0000:00:1d.0: [8086:27c8] type 00 class 0x0c0300
Jan  7 21:29:42 ubuntu kernel: [    0.159750] pci 0000:00:1d.0: reg 20: [io  0xbf80-0xbf9f]
Jan  7 21:29:42 ubuntu kernel: [    0.159800] pci 0000:00:1d.1: [8086:27c9] type 00 class 0x0c0300
Jan  7 21:29:42 ubuntu kernel: [    0.159867] pci 0000:00:1d.1: reg 20: [io  0xbf60-0xbf7f]
Jan  7 21:29:42 ubuntu kernel: [    0.159919] pci 0000:00:1d.2: [8086:27ca] type 00 class 0x0c0300
Jan  7 21:29:42 ubuntu kernel: [    0.159987] pci 0000:00:1d.2: reg 20: [io  0xbf40-0xbf5f]
Jan  7 21:29:42 ubuntu kernel: [    0.160054] pci 0000:00:1d.3: [8086:27cb] type 00 class 0x0c0300
Jan  7 21:29:42 ubuntu kernel: [    0.160120] pci 0000:00:1d.3: reg 20: [io  0xbf20-0xbf3f]
Jan  7 21:29:42 ubuntu kernel: [    0.160185] pci 0000:00:1d.7: [8086:27cc] type 00 class 0x0c0320
Jan  7 21:29:42 ubuntu kernel: [    0.160214] pci 0000:00:1d.7: reg 10: [mem 0xffa80000-0xffa803ff]
Jan  7 21:29:42 ubuntu kernel: [    0.160338] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Jan  7 21:29:42 ubuntu kernel: [    0.160370] pci 0000:00:1e.0: [8086:2448] type 01 class 0x060401
Jan  7 21:29:42 ubuntu kernel: [    0.160484] pci 0000:00:1f.0: [8086:27b9] type 00 class 0x060100
Jan  7 21:29:42 ubuntu kernel: [    0.160612] pci 0000:00:1f.0: quirk: [io  0x1000-0x107f] claimed by ICH6 ACPI/GPIO/TCO
Jan  7 21:29:42 ubuntu kernel: [    0.160621] pci 0000:00:1f.0: quirk: [io  0x1080-0x10bf] claimed by ICH6 GPIO
Jan  7 21:29:42 ubuntu kernel: [    0.160627] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0900 (mask 007f)
Jan  7 21:29:42 ubuntu kernel: [    0.160635] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 0c80 (mask 003f)
Jan  7 21:29:42 ubuntu kernel: [    0.160712] pci 0000:00:1f.2: [8086:27c4] type 00 class 0x010180
Jan  7 21:29:42 ubuntu kernel: [    0.160738] pci 0000:00:1f.2: reg 10: [io  0x01f0-0x01f7]
Jan  7 21:29:42 ubuntu kernel: [    0.160752] pci 0000:00:1f.2: reg 14: [io  0x03f4-0x03f7]
Jan  7 21:29:42 ubuntu kernel: [    0.160768] pci 0000:00:1f.2: reg 18: [io  0x0170-0x0177]
Jan  7 21:29:42 ubuntu kernel: [    0.160782] pci 0000:00:1f.2: reg 1c: [io  0x0374-0x0377]
Jan  7 21:29:42 ubuntu kernel: [    0.160797] pci 0000:00:1f.2: reg 20: [io  0xbfa0-0xbfaf]
Jan  7 21:29:42 ubuntu kernel: [    0.160866] pci 0000:00:1f.2: PME# supported from D3hot
Jan  7 21:29:42 ubuntu kernel: [    0.160891] pci 0000:00:1f.3: [8086:27da] type 00 class 0x0c0500
Jan  7 21:29:42 ubuntu kernel: [    0.160974] pci 0000:00:1f.3: reg 20: [io  0x10c0-0x10df]
Jan  7 21:29:42 ubuntu kernel: [    0.161093] pci 0000:01:00.0: [1002:7145] type 00 class 0x030000
Jan  7 21:29:42 ubuntu kernel: [    0.161112] pci 0000:01:00.0: reg 10: [mem 0xd0000000-0xdfffffff pref]
Jan  7 21:29:42 ubuntu kernel: [    0.161126] pci 0000:01:00.0: reg 14: [io  0xee00-0xeeff]
Jan  7 21:29:42 ubuntu kernel: [    0.161140] pci 0000:01:00.0: reg 18: [mem 0xefdf0000-0xefdfffff]
Jan  7 21:29:42 ubuntu kernel: [    0.161176] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
Jan  7 21:29:42 ubuntu kernel: [    0.161225] pci 0000:01:00.0: supports D1 D2
Jan  7 21:29:42 ubuntu kernel: [    0.161243] pci 0000:01:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
Jan  7 21:29:42 ubuntu kernel: [    0.161260] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Jan  7 21:29:42 ubuntu kernel: [    0.161266] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
Jan  7 21:29:42 ubuntu kernel: [    0.161271] pci 0000:00:01.0:   bridge window [mem 0xefd00000-0xefefffff]
Jan  7 21:29:42 ubuntu kernel: [    0.161278] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
Jan  7 21:29:42 ubuntu kernel: [    0.161424] pci 0000:0b:00.0: [14e4:4311] type 00 class 0x028000
Jan  7 21:29:42 ubuntu kernel: [    0.161494] pci 0000:0b:00.0: reg 10: [mem 0xefcfc000-0xefcfffff]
Jan  7 21:29:42 ubuntu kernel: [    0.162010] pci 0000:0b:00.0: supports D1 D2
Jan  7 21:29:42 ubuntu kernel: [    0.162093] pci 0000:0b:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
Jan  7 21:29:42 ubuntu kernel: [    0.162121] pci 0000:00:1c.0: PCI bridge to [bus 0b-0b]
Jan  7 21:29:42 ubuntu kernel: [    0.162131] pci 0000:00:1c.0:   bridge window [mem 0xefc00000-0xefcfffff]
Jan  7 21:29:42 ubuntu kernel: [    0.162209] pci 0000:00:1c.3: PCI bridge to [bus 0c-0d]
Jan  7 21:29:42 ubuntu kernel: [    0.162216] pci 0000:00:1c.3:   bridge window [io  0xd000-0xdfff]
Jan  7 21:29:42 ubuntu kernel: [    0.162223] pci 0000:00:1c.3:   bridge window [mem 0xefa00000-0xefbfffff]
Jan  7 21:29:42 ubuntu kernel: [    0.162234] pci 0000:00:1c.3:   bridge window [mem 0xe0000000-0xe01fffff 64bit pref]
Jan  7 21:29:42 ubuntu kernel: [    0.162290] pci 0000:03:00.0: [14e4:170c] type 00 class 0x020000
Jan  7 21:29:42 ubuntu kernel: [    0.162316] pci 0000:03:00.0: reg 10: [mem 0xef9fe000-0xef9fffff]
Jan  7 21:29:42 ubuntu kernel: [    0.162426] pci 0000:03:00.0: supports D1 D2
Jan  7 21:29:42 ubuntu kernel: [    0.162430] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Jan  7 21:29:42 ubuntu kernel: [    0.162459] pci 0000:03:01.0: [1180:0832] type 00 class 0x0c0010
Jan  7 21:29:42 ubuntu kernel: [    0.162479] pci 0000:03:01.0: proprietary Ricoh MMC controller disabled (via firewire function)
Jan  7 21:29:42 ubuntu kernel: [    0.162483] pci 0000:03:01.0: MMC cards are now supported by standard SDHCI controller
Jan  7 21:29:42 ubuntu kernel: [    0.162502] pci 0000:03:01.0: reg 10: [mem 0xef9fd800-0xef9fdfff]
Jan  7 21:29:42 ubuntu kernel: [    0.162616] pci 0000:03:01.0: supports D1 D2
Jan  7 21:29:42 ubuntu kernel: [    0.162619] pci 0000:03:01.0: PME# supported from D0 D1 D2 D3hot D3cold
Jan  7 21:29:42 ubuntu kernel: [    0.162648] pci 0000:03:01.1: [1180:0822] type 00 class 0x080501
Jan  7 21:29:42 ubuntu kernel: [    0.162675] pci 0000:03:01.1: reg 10: [mem 0xef9fd400-0xef9fd4ff]
Jan  7 21:29:42 ubuntu kernel: [    0.162788] pci 0000:03:01.1: supports D1 D2
Jan  7 21:29:42 ubuntu kernel: [    0.162792] pci 0000:03:01.1: PME# supported from D0 D1 D2 D3hot D3cold
Jan  7 21:29:42 ubuntu kernel: [    0.162822] pci 0000:03:01.2: [1180:0592] type 00 class 0x088000
Jan  7 21:29:42 ubuntu kernel: [    0.162849] pci 0000:03:01.2: reg 10: [mem 0xef9fd600-0xef9fd6ff]
Jan  7 21:29:42 ubuntu kernel: [    0.162962] pci 0000:03:01.2: supports D1 D2
Jan  7 21:29:42 ubuntu kernel: [    0.162965] pci 0000:03:01.2: PME# supported from D0 D1 D2 D3hot D3cold
Jan  7 21:29:42 ubuntu kernel: [    0.162995] pci 0000:03:01.3: [1180:0852] type 00 class 0x088000
Jan  7 21:29:42 ubuntu kernel: [    0.163022] pci 0000:03:01.3: reg 10: [mem 0xef9fd700-0xef9fd7ff]
Jan  7 21:29:42 ubuntu kernel: [    0.163135] pci 0000:03:01.3: supports D1 D2
Jan  7 21:29:42 ubuntu kernel: [    0.163138] pci 0000:03:01.3: PME# supported from D0 D1 D2 D3hot D3cold
Jan  7 21:29:42 ubuntu kernel: [    0.163224] pci 0000:00:1e.0: PCI bridge to [bus 03-03] (subtractive decode)
Jan  7 21:29:42 ubuntu kernel: [    0.163235] pci 0000:00:1e.0:   bridge window [mem 0xef900000-0xef9fffff]
Jan  7 21:29:42 ubuntu kernel: [    0.163245] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
Jan  7 21:29:42 ubuntu kernel: [    0.163249] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xffffffff] (subtractive decode)
Jan  7 21:29:42 ubuntu kernel: [    0.163281] pci_bus 0000:00: on NUMA node 0
Jan  7 21:29:42 ubuntu kernel: [    0.163291] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Jan  7 21:29:42 ubuntu kernel: [    0.163687] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
Jan  7 21:29:42 ubuntu kernel: [    0.163754] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
Jan  7 21:29:42 ubuntu kernel: [    0.163843] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
Jan  7 21:29:42 ubuntu kernel: [    0.163926] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
Jan  7 21:29:42 ubuntu kernel: [    0.164020]  pci0000:00: Requesting ACPI _OSC control (0x1d)
Jan  7 21:29:42 ubuntu kernel: [    0.164025]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
Jan  7 21:29:42 ubuntu kernel: [    0.164028] ACPI _OSC control for PCIe not granted, disabling ASPM
Jan  7 21:29:42 ubuntu kernel: [    0.173738] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 11) *4
Jan  7 21:29:42 ubuntu kernel: [    0.173842] ACPI: PCI Interrupt Link [LNKB] (IRQs *5 7)
Jan  7 21:29:42 ubuntu kernel: [    0.173938] ACPI: PCI Interrupt Link [LNKC] (IRQs *9 10 11)
Jan  7 21:29:42 ubuntu kernel: [    0.174034] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 11) *3
Jan  7 21:29:42 ubuntu kernel: [    0.174131] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Jan  7 21:29:42 ubuntu kernel: [    0.174233] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Jan  7 21:29:42 ubuntu kernel: [    0.174335] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
Jan  7 21:29:42 ubuntu kernel: [    0.174437] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
Jan  7 21:29:42 ubuntu kernel: [    0.174639] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Jan  7 21:29:42 ubuntu kernel: [    0.174649] vgaarb: loaded
Jan  7 21:29:42 ubuntu kernel: [    0.174651] vgaarb: bridge control possible 0000:01:00.0
Jan  7 21:29:42 ubuntu kernel: [    0.174984] SCSI subsystem initialized
Jan  7 21:29:42 ubuntu kernel: [    0.175069] libata version 3.00 loaded.
Jan  7 21:29:42 ubuntu kernel: [    0.175104] ACPI: bus type usb registered
Jan  7 21:29:42 ubuntu kernel: [    0.175139] usbcore: registered new interface driver usbfs
Jan  7 21:29:42 ubuntu kernel: [    0.175155] usbcore: registered new interface driver hub
Jan  7 21:29:42 ubuntu kernel: [    0.175195] usbcore: registered new device driver usb
Jan  7 21:29:42 ubuntu kernel: [    0.175335] PCI: Using ACPI for IRQ routing
Jan  7 21:29:42 ubuntu kernel: [    0.178087] PCI: pci_cache_line_size set to 64 bytes
Jan  7 21:29:42 ubuntu kernel: [    0.178225] e820: reserve RAM buffer [mem 0x0009f000-0x0009ffff]
Jan  7 21:29:42 ubuntu kernel: [    0.178229] e820: reserve RAM buffer [mem 0xbfed3400-0xbfffffff]
Jan  7 21:29:42 ubuntu kernel: [    0.178401] NetLabel: Initializing
Jan  7 21:29:42 ubuntu kernel: [    0.178404] NetLabel:  domain hash size = 128
Jan  7 21:29:42 ubuntu kernel: [    0.178406] NetLabel:  protocols = UNLABELED CIPSOv4
Jan  7 21:29:42 ubuntu kernel: [    0.178422] NetLabel:  unlabeled traffic allowed by default
Jan  7 21:29:42 ubuntu kernel: [    0.178600] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
Jan  7 21:29:42 ubuntu kernel: [    0.178609] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Jan  7 21:29:42 ubuntu kernel: [    0.178616] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
Jan  7 21:29:42 ubuntu kernel: [    0.184106] Switching to clocksource hpet
Jan  7 21:29:42 ubuntu modem-manager[721]: <info>  Loaded plugin AnyData
Jan  7 21:29:42 ubuntu modem-manager[721]: <info>  Loaded plugin Option High-Speed
Jan  7 21:29:42 ubuntu modem-manager[721]: <info>  Loaded plugin Ericsson MBM
Jan  7 21:29:42 ubuntu modem-manager[721]: <info>  Loaded plugin Option
Jan  7 21:29:42 ubuntu modem-manager[721]: <info>  Loaded plugin Gobi
Jan  7 21:29:42 ubuntu modem-manager[721]: <info>  Loaded plugin Huawei
Jan  7 21:29:42 ubuntu modem-manager[721]: <info>  Loaded plugin Wavecom
Jan  7 21:29:42 ubuntu modem-manager[721]: <info>  Loaded plugin X22X
Jan  7 21:29:42 ubuntu modem-manager[721]: <info>  Loaded plugin Longcheer
Jan  7 21:29:42 ubuntu modem-manager[721]: <info>  Loaded plugin Sierra
Jan  7 21:29:42 ubuntu NetworkManager[726]: <info> NetworkManager (version 0.9.4.0) is starting...
Jan  7 21:29:42 ubuntu NetworkManager[726]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Jan  7 21:29:42 ubuntu modem-manager[721]: <info>  Loaded plugin Nokia
Jan  7 21:29:42 ubuntu NetworkManager[726]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Jan  7 21:29:42 ubuntu NetworkManager[726]: <info> DNS: loaded plugin dnsmasq
Jan  7 21:29:42 ubuntu modem-manager[721]: <info>  Loaded plugin Samsung
Jan  7 21:29:42 ubuntu modem-manager[721]: <info>  Loaded plugin ZTE
Jan  7 21:29:42 ubuntu modem-manager[721]: <info>  Loaded plugin SimTech
Jan  7 21:29:42 ubuntu modem-manager[721]: <info>  Loaded plugin Generic
Jan  7 21:29:42 ubuntu modem-manager[721]: <info>  Loaded plugin MotoC
Jan  7 21:29:42 ubuntu modem-manager[721]: <info>  Loaded plugin Novatel
Jan  7 21:29:42 ubuntu kernel: [    0.198112] AppArmor: AppArmor Filesystem Enabled
Jan  7 21:29:42 ubuntu kernel: [    0.198160] pnp: PnP ACPI init
Jan  7 21:29:42 ubuntu kernel: [    0.198187] ACPI: bus type pnp registered
Jan  7 21:29:42 ubuntu kernel: [    0.209178] pnp 00:00: [mem 0x00000000-0x0009fbff]
Jan  7 21:29:42 ubuntu kernel: [    0.209185] pnp 00:00: [mem 0x0009fc00-0x0009ffff]
Jan  7 21:29:42 ubuntu kernel: [    0.209188] pnp 00:00: [mem 0x000c0000-0x000cffff]
Jan  7 21:29:42 ubuntu kernel: [    0.209192] pnp 00:00: [mem 0x000e0000-0x000fffff]
Jan  7 21:29:42 ubuntu kernel: [    0.209196] pnp 00:00: [mem 0x00100000-0xbfed33ff]
Jan  7 21:29:42 ubuntu kernel: [    0.209199] pnp 00:00: [mem 0xbfed3400-0xbfefffff]
Jan  7 21:29:42 ubuntu kernel: [    0.209203] pnp 00:00: [mem 0xbff00000-0xbfffffff]
Jan  7 21:29:42 ubuntu kernel: [    0.209207] pnp 00:00: [mem 0xffb00000-0xffffffff]
Jan  7 21:29:42 ubuntu kernel: [    0.209210] pnp 00:00: [mem 0xfec00000-0xfec0ffff]
Jan  7 21:29:42 ubuntu kernel: [    0.209214] pnp 00:00: [mem 0xfee00000-0xfee0ffff]
Jan  7 21:29:42 ubuntu kernel: [    0.209218] pnp 00:00: [mem 0xfed20000-0xfed9ffff]
Jan  7 21:29:42 ubuntu kernel: [    0.209221] pnp 00:00: [mem 0xffa80000-0xffa83fff]
Jan  7 21:29:42 ubuntu kernel: [    0.209225] pnp 00:00: [mem 0xf4000000-0xf4003fff]
Jan  7 21:29:42 ubuntu kernel: [    0.209228] pnp 00:00: [mem 0xf4004000-0xf4004fff]
Jan  7 21:29:42 ubuntu kernel: [    0.209232] pnp 00:00: [mem 0xf4005000-0xf4005fff]
Jan  7 21:29:42 ubuntu kernel: [    0.209236] pnp 00:00: [mem 0xf4006000-0xf4006fff]
Jan  7 21:29:42 ubuntu kernel: [    0.209239] pnp 00:00: [mem 0xf4008000-0xf400bfff]
Jan  7 21:29:42 ubuntu kernel: [    0.209243] pnp 00:00: [mem 0xf0000000-0xf3ffffff]
Jan  7 21:29:42 ubuntu kernel: [    0.209366] system 00:00: [mem 0x00000000-0x0009fbff] could not be reserved
Jan  7 21:29:42 ubuntu kernel: [    0.209371] system 00:00: [mem 0x0009fc00-0x0009ffff] could not be reserved
Jan  7 21:29:42 ubuntu kernel: [    0.209376] system 00:00: [mem 0x000c0000-0x000cffff] could not be reserved
Jan  7 21:29:42 ubuntu kernel: [    0.209380] system 00:00: [mem 0x000e0000-0x000fffff] could not be reserved
Jan  7 21:29:42 ubuntu kernel: [    0.209385] system 00:00: [mem 0x00100000-0xbfed33ff] could not be reserved
Jan  7 21:29:42 ubuntu kernel: [    0.209389] system 00:00: [mem 0xbfed3400-0xbfefffff] has been reserved
Jan  7 21:29:42 ubuntu kernel: [    0.209393] system 00:00: [mem 0xbff00000-0xbfffffff] has been reserved
Jan  7 21:29:42 ubuntu kernel: [    0.209398] system 00:00: [mem 0xffb00000-0xffffffff] has been reserved
Jan  7 21:29:42 ubuntu kernel: [    0.209403] system 00:00: [mem 0xfec00000-0xfec0ffff] could not be reserved
Jan  7 21:29:42 ubuntu kernel: [    0.209407] system 00:00: [mem 0xfee00000-0xfee0ffff] has been reserved
Jan  7 21:29:42 ubuntu kernel: [    0.209411] system 00:00: [mem 0xfed20000-0xfed9ffff] has been reserved
Jan  7 21:29:42 ubuntu kernel: [    0.209416] system 00:00: [mem 0xffa80000-0xffa83fff] could not be reserved
Jan  7 21:29:42 ubuntu kernel: [    0.209420] system 00:00: [mem 0xf4000000-0xf4003fff] has been reserved
Jan  7 21:29:42 ubuntu kernel: [    0.209429] system 00:00: [mem 0xf4004000-0xf4004fff] has been reserved
Jan  7 21:29:42 ubuntu kernel: [    0.209433] system 00:00: [mem 0xf4005000-0xf4005fff] has been reserved
Jan  7 21:29:42 ubuntu kernel: [    0.209438] system 00:00: [mem 0xf4006000-0xf4006fff] has been reserved
Jan  7 21:29:42 ubuntu kernel: [    0.209442] system 00:00: [mem 0xf4008000-0xf400bfff] has been reserved
Jan  7 21:29:42 ubuntu kernel: [    0.209447] system 00:00: [mem 0xf0000000-0xf3ffffff] has been reserved
Jan  7 21:29:42 ubuntu kernel: [    0.209454] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
Jan  7 21:29:42 ubuntu kernel: [    0.216583] pnp 00:01: [bus 00-ff]
Jan  7 21:29:42 ubuntu kernel: [    0.216590] pnp 00:01: [io  0x0000-0x0cf7 window]
Jan  7 21:29:42 ubuntu kernel: [    0.216594] pnp 00:01: [io  0x0cf8-0x0cff]
Jan  7 21:29:42 ubuntu kernel: [    0.216598] pnp 00:01: [io  0x0d00-0xffff window]
Jan  7 21:29:42 ubuntu kernel: [    0.216602] pnp 00:01: [mem 0x000a0000-0x000bffff window]
Jan  7 21:29:42 ubuntu kernel: [    0.216606] pnp 00:01: [mem 0x000d0000-0x000dffff window]
Jan  7 21:29:42 ubuntu kernel: [    0.216610] pnp 00:01: [mem 0xc0000000-0xefffffff window]
Jan  7 21:29:42 ubuntu kernel: [    0.216614] pnp 00:01: [mem 0xf4007000-0xf4007fff window]
Jan  7 21:29:42 ubuntu kernel: [    0.216617] pnp 00:01: [mem 0xf400c000-0xfebfffff window]
Jan  7 21:29:42 ubuntu kernel: [    0.216621] pnp 00:01: [mem 0xfec10000-0xfecfffff window]
Jan  7 21:29:42 ubuntu kernel: [    0.216625] pnp 00:01: [mem 0xfed00400-0xfed1ffff window]
Jan  7 21:29:42 ubuntu kernel: [    0.216629] pnp 00:01: [mem 0xfeda0000-0xfed9ffff window disabled]
Jan  7 21:29:42 ubuntu kernel: [    0.216633] pnp 00:01: [mem 0xfee10000-0xffafffff window]
Jan  7 21:29:42 ubuntu kernel: [    0.216758] pnp 00:01: Plug and Play ACPI device, IDs PNP0a03 (active)
Jan  7 21:29:42 ubuntu kernel: [    0.216792] pnp 00:02: [io  0x0092]
Jan  7 21:29:42 ubuntu kernel: [    0.216796] pnp 00:02: [io  0x00b2]
Jan  7 21:29:42 ubuntu kernel: [    0.216800] pnp 00:02: [io  0x0020-0x0021]
Jan  7 21:29:42 ubuntu kernel: [    0.216803] pnp 00:02: [io  0x00a0-0x00a1]
Jan  7 21:29:42 ubuntu kernel: [    0.216807] pnp 00:02: [irq 0 disabled]
Jan  7 21:29:42 ubuntu kernel: [    0.216811] pnp 00:02: [io  0x04d0-0x04d1]
Jan  7 21:29:42 ubuntu kernel: [    0.216814] pnp 00:02: [io  0x1000-0x1005]
Jan  7 21:29:42 ubuntu kernel: [    0.216818] pnp 00:02: [io  0x1008-0x100f]
Jan  7 21:29:42 ubuntu kernel: [    0.216845] pnp 00:02: disabling [io  0x1000-0x1005] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
Jan  7 21:29:42 ubuntu kernel: [    0.216850] pnp 00:02: disabling [io  0x1008-0x100f] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
Jan  7 21:29:42 ubuntu kernel: [    0.216919] system 00:02: [io  0x04d0-0x04d1] has been reserved
Jan  7 21:29:42 ubuntu kernel: [    0.216925] system 00:02: Plug and Play ACPI device, IDs PNP0c01 (active)
Jan  7 21:29:42 ubuntu kernel: [    0.216953] pnp 00:03: [io  0xf400-0xf4fe]
Jan  7 21:29:42 ubuntu kernel: [    0.216956] pnp 00:03: [io  0x0086]
Jan  7 21:29:42 ubuntu kernel: [    0.216960] pnp 00:03: [io  0x00b3]
Jan  7 21:29:42 ubuntu kernel: [    0.216963] pnp 00:03: [io  0x1006-0x1007]
Jan  7 21:29:42 ubuntu kernel: [    0.216967] pnp 00:03: [io  0x100a-0x1059]
Jan  7 21:29:42 ubuntu kernel: [    0.216970] pnp 00:03: [io  0x1060-0x107f]
Jan  7 21:29:42 ubuntu kernel: [    0.216974] pnp 00:03: [io  0x1080-0x10bf]
Jan  7 21:29:42 ubuntu kernel: [    0.216977] pnp 00:03: [io  0x10c0-0x10df]
Jan  7 21:29:42 ubuntu kernel: [    0.216981] pnp 00:03: [io  0x1010-0x102f]
Jan  7 21:29:42 ubuntu kernel: [    0.216984] pnp 00:03: [io  0x0809]
Jan  7 21:29:42 ubuntu kernel: [    0.217005] pnp 00:03: disabling [io  0x1006-0x1007] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
Jan  7 21:29:42 ubuntu kernel: [    0.217010] pnp 00:03: disabling [io  0x100a-0x1059] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
Jan  7 21:29:42 ubuntu kernel: [    0.217014] pnp 00:03: disabling [io  0x1060-0x107f] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
Jan  7 21:29:42 ubuntu kernel: [    0.217019] pnp 00:03: disabling [io  0x1010-0x102f] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
Jan  7 21:29:42 ubuntu kernel: [    0.217075] system 00:03: [io  0xf400-0xf4fe] has been reserved
Jan  7 21:29:42 ubuntu kernel: [    0.217080] system 00:03: [io  0x1080-0x10bf] has been reserved
Jan  7 21:29:42 ubuntu kernel: [    0.217085] system 00:03: [io  0x10c0-0x10df] has been reserved
Jan  7 21:29:42 ubuntu kernel: [    0.217089] system 00:03: [io  0x0809] has been reserved
Jan  7 21:29:42 ubuntu kernel: [    0.217094] system 00:03: Plug and Play ACPI device, IDs PNP0c01 (active)
Jan  7 21:29:42 ubuntu kernel: [    0.217132] pnp 00:04: [irq 12]
Jan  7 21:29:42 ubuntu kernel: [    0.217175] pnp 00:04: Plug and Play ACPI device, IDs PNP0f13 (active)
Jan  7 21:29:42 ubuntu kernel: [    0.217199] pnp 00:05: [io  0x0060]
Jan  7 21:29:42 ubuntu kernel: [    0.217203] pnp 00:05: [io  0x0064]
Jan  7 21:29:42 ubuntu kernel: [    0.217206] pnp 00:05: [io  0x0062]
Jan  7 21:29:42 ubuntu kernel: [    0.217210] pnp 00:05: [io  0x0066]
Jan  7 21:29:42 ubuntu kernel: [    0.217219] pnp 00:05: [irq 1]
Jan  7 21:29:42 ubuntu kernel: [    0.217266] pnp 00:05: Plug and Play ACPI device, IDs PNP0303 (active)
Jan  7 21:29:42 ubuntu kernel: [    0.217290] pnp 00:06: [io  0x0070-0x0071]
Jan  7 21:29:42 ubuntu kernel: [    0.217299] pnp 00:06: [irq 8]
Jan  7 21:29:42 ubuntu kernel: [    0.217302] pnp 00:06: [io  0x0072-0x0077]
Jan  7 21:29:42 ubuntu kernel: [    0.217345] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
Jan  7 21:29:42 ubuntu kernel: [    0.217371] pnp 00:07: [io  0x0061]
Jan  7 21:29:42 ubuntu kernel: [    0.217375] pnp 00:07: [io  0x0063]
Jan  7 21:29:42 ubuntu kernel: [    0.217378] pnp 00:07: [io  0x0065]
Jan  7 21:29:42 ubuntu kernel: [    0.217381] pnp 00:07: [io  0x0067]
Jan  7 21:29:42 ubuntu kernel: [    0.217425] pnp 00:07: Plug and Play ACPI device, IDs PNP0800 (active)
Jan  7 21:29:42 ubuntu kernel: [    0.217448] pnp 00:08: [io  0x0c80-0x0cff]
Jan  7 21:29:42 ubuntu kernel: [    0.217452] pnp 00:08: [io  0x0910-0x091f]
Jan  7 21:29:42 ubuntu kernel: [    0.217456] pnp 00:08: [io  0x0920-0x092f]
Jan  7 21:29:42 ubuntu kernel: [    0.217462] pnp 00:08: [io  0x0cb0-0x0cbf]
Jan  7 21:29:42 ubuntu kernel: [    0.217466] pnp 00:08: [io  0x0930-0x097f]
Jan  7 21:29:42 ubuntu kernel: [    0.217539] system 00:08: [io  0x0c80-0x0cff] could not be reserved
Jan  7 21:29:42 ubuntu kernel: [    0.217544] system 00:08: [io  0x0910-0x091f] has been reserved
Jan  7 21:29:42 ubuntu kernel: [    0.217548] system 00:08: [io  0x0920-0x092f] has been reserved
Jan  7 21:29:42 ubuntu kernel: [    0.217552] system 00:08: [io  0x0cb0-0x0cbf] has been reserved
Jan  7 21:29:42 ubuntu kernel: [    0.217557] system 00:08: [io  0x0930-0x097f] has been reserved
Jan  7 21:29:42 ubuntu kernel: [    0.217562] system 00:08: Plug and Play ACPI device, IDs PNP0c01 (active)
Jan  7 21:29:42 ubuntu kernel: [    0.217590] pnp 00:09: [dma 4]
Jan  7 21:29:42 ubuntu kernel: [    0.217594] pnp 00:09: [io  0x0000-0x000f]
Jan  7 21:29:42 ubuntu kernel: [    0.217597] pnp 00:09: [io  0x0080-0x0085]
Jan  7 21:29:42 ubuntu kernel: [    0.217601] pnp 00:09: [io  0x0087-0x008f]
Jan  7 21:29:42 ubuntu kernel: [    0.217604] pnp 00:09: [io  0x00c0-0x00df]
Jan  7 21:29:42 ubuntu kernel: [    0.217608] pnp 00:09: [io  0x0010-0x001f]
Jan  7 21:29:42 ubuntu kernel: [    0.217611] pnp 00:09: [io  0x0090-0x0091]
Jan  7 21:29:42 ubuntu kernel: [    0.217615] pnp 00:09: [io  0x0093-0x009f]
Jan  7 21:29:42 ubuntu kernel: [    0.217661] pnp 00:09: Plug and Play ACPI device, IDs PNP0200 (active)
Jan  7 21:29:42 ubuntu kernel: [    0.217684] pnp 00:0a: [io  0x00f0-0x00ff]
Jan  7 21:29:42 ubuntu kernel: [    0.217693] pnp 00:0a: [irq 13]
Jan  7 21:29:42 ubuntu kernel: [    0.217744] pnp 00:0a: Plug and Play ACPI device, IDs PNP0c04 (active)
Jan  7 21:29:42 ubuntu kernel: [    0.217812] pnp 00:0b: [mem 0xfed00000-0xfed003ff]
Jan  7 21:29:42 ubuntu kernel: [    0.217889] system 00:0b: [mem 0xfed00000-0xfed003ff] has been reserved
Jan  7 21:29:42 ubuntu kernel: [    0.217894] system 00:0b: Plug and Play ACPI device, IDs PNP0103 PNP0c01 (active)
Jan  7 21:29:42 ubuntu kernel: [    0.218313] pnp: PnP ACPI: found 12 devices
Jan  7 21:29:42 ubuntu kernel: [    0.218317] ACPI: ACPI bus type pnp unregistered
Jan  7 21:29:42 ubuntu kernel: [    0.218323] PnPBIOS: Disabled by ACPI PNP
Jan  7 21:29:42 ubuntu kernel: [    0.255563] pci 0000:00:1c.0: bridge window [io  0x1000-0x0fff] to [bus 0b-0b] add_size 1000
Jan  7 21:29:42 ubuntu kernel: [    0.255573] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 0b-0b] add_size 200000
Jan  7 21:29:42 ubuntu kernel: [    0.255607] pci 0000:00:1c.0: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
Jan  7 21:29:42 ubuntu kernel: [    0.255612] pci 0000:00:1c.0: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
Jan  7 21:29:42 ubuntu kernel: [    0.255621] pci 0000:00:1c.0: BAR 15: assigned [mem 0xc0000000-0xc01fffff 64bit pref]
Jan  7 21:29:42 ubuntu kernel: [    0.255628] pci 0000:00:1c.0: BAR 13: assigned [io  0x2000-0x2fff]
Jan  7 21:29:42 ubuntu kernel: [    0.255634] pci 0000:01:00.0: BAR 6: assigned [mem 0xefd00000-0xefd1ffff pref]
Jan  7 21:29:42 ubuntu kernel: [    0.255639] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Jan  7 21:29:42 ubuntu kernel: [    0.255644] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
Jan  7 21:29:42 ubuntu kernel: [    0.255651] pci 0000:00:01.0:   bridge window [mem 0xefd00000-0xefefffff]
Jan  7 21:29:42 ubuntu kernel: [    0.255656] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
Jan  7 21:29:42 ubuntu kernel: [    0.255663] pci 0000:00:1c.0: PCI bridge to [bus 0b-0b]
Jan  7 21:29:42 ubuntu kernel: [    0.255669] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
Jan  7 21:29:42 ubuntu kernel: [    0.255677] pci 0000:00:1c.0:   bridge window [mem 0xefc00000-0xefcfffff]
Jan  7 21:29:42 ubuntu kernel: [    0.255684] pci 0000:00:1c.0:   bridge window [mem 0xc0000000-0xc01fffff 64bit pref]
Jan  7 21:29:42 ubuntu kernel: [    0.255695] pci 0000:00:1c.3: PCI bridge to [bus 0c-0d]
Jan  7 21:29:42 ubuntu kernel: [    0.255700] pci 0000:00:1c.3:   bridge window [io  0xd000-0xdfff]
Jan  7 21:29:42 ubuntu kernel: [    0.255708] pci 0000:00:1c.3:   bridge window [mem 0xefa00000-0xefbfffff]
Jan  7 21:29:42 ubuntu kernel: [    0.255715] pci 0000:00:1c.3:   bridge window [mem 0xe0000000-0xe01fffff 64bit pref]
Jan  7 21:29:42 ubuntu kernel: [    0.255727] pci 0000:00:1e.0: PCI bridge to [bus 03-03]
Jan  7 21:29:42 ubuntu kernel: [    0.255736] pci 0000:00:1e.0:   bridge window [mem 0xef900000-0xef9fffff]
Jan  7 21:29:42 ubuntu kernel: [    0.255799] pci 0000:00:1e.0: setting latency timer to 64
Jan  7 21:29:42 ubuntu kernel: [    0.255807] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
Jan  7 21:29:42 ubuntu kernel: [    0.255811] pci_bus 0000:00: resource 5 [mem 0x00000000-0xffffffff]
Jan  7 21:29:42 ubuntu kernel: [    0.255814] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
Jan  7 21:29:42 ubuntu kernel: [    0.255818] pci_bus 0000:01: resource 1 [mem 0xefd00000-0xefefffff]
Jan  7 21:29:42 ubuntu kernel: [    0.255822] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
Jan  7 21:29:42 ubuntu kernel: [    0.255826] pci_bus 0000:0b: resource 0 [io  0x2000-0x2fff]
Jan  7 21:29:42 ubuntu kernel: [    0.255830] pci_bus 0000:0b: resource 1 [mem 0xefc00000-0xefcfffff]
Jan  7 21:29:42 ubuntu kernel: [    0.255834] pci_bus 0000:0b: resource 2 [mem 0xc0000000-0xc01fffff 64bit pref]
Jan  7 21:29:42 ubuntu kernel: [    0.255838] pci_bus 0000:0c: resource 0 [io  0xd000-0xdfff]
Jan  7 21:29:42 ubuntu kernel: [    0.255842] pci_bus 0000:0c: resource 1 [mem 0xefa00000-0xefbfffff]
Jan  7 21:29:42 ubuntu kernel: [    0.255846] pci_bus 0000:0c: resource 2 [mem 0xe0000000-0xe01fffff 64bit pref]
Jan  7 21:29:42 ubuntu kernel: [    0.255850] pci_bus 0000:03: resource 1 [mem 0xef900000-0xef9fffff]
Jan  7 21:29:42 ubuntu kernel: [    0.255853] pci_bus 0000:03: resource 4 [io  0x0000-0xffff]
Jan  7 21:29:42 ubuntu kernel: [    0.255857] pci_bus 0000:03: resource 5 [mem 0x00000000-0xffffffff]
Jan  7 21:29:42 ubuntu kernel: [    0.255912] NET: Registered protocol family 2
Jan  7 21:29:42 ubuntu kernel: [    0.256034] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Jan  7 21:29:42 ubuntu kernel: [    0.256253] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Jan  7 21:29:42 ubuntu kernel: [    0.257043] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Jan  7 21:29:42 ubuntu kernel: [    0.257521] TCP: Hash tables configured (established 131072 bind 65536)
Jan  7 21:29:42 ubuntu kernel: [    0.257526] TCP: reno registered
Jan  7 21:29:42 ubuntu kernel: [    0.257532] UDP hash table entries: 512 (order: 2, 16384 bytes)
Jan  7 21:29:42 ubuntu kernel: [    0.257548] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
Jan  7 21:29:42 ubuntu kernel: [    0.257679] NET: Registered protocol family 1
Jan  7 21:29:42 ubuntu kernel: [    0.257953] pci 0000:01:00.0: Boot video device
Jan  7 21:29:42 ubuntu kernel: [    0.257983] PCI: CLS 64 bytes, default 64
Jan  7 21:29:42 ubuntu kernel: [    0.258088] Simple Boot Flag at 0x79 set to 0x1
Jan  7 21:29:42 ubuntu kernel: [    0.258636] audit: initializing netlink socket (disabled)
Jan  7 21:29:42 ubuntu kernel: [    0.258654] type=2000 audit(1389130132.252:1): initialized
Jan  7 21:29:42 ubuntu kernel: [    0.290109] highmem bounce pool size: 64 pages
Jan  7 21:29:42 ubuntu kernel: [    0.290133] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Jan  7 21:29:42 ubuntu kernel: [    0.293155] VFS: Disk quotas dquot_6.5.2
Jan  7 21:29:42 ubuntu kernel: [    0.293240] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jan  7 21:29:42 ubuntu kernel: [    0.294105] fuse init (API version 7.19)
Jan  7 21:29:42 ubuntu kernel: [    0.294236] msgmni has been set to 1670
Jan  7 21:29:42 ubuntu kernel: [    0.294720] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
Jan  7 21:29:42 ubuntu kernel: [    0.294765] io scheduler noop registered
Jan  7 21:29:42 ubuntu kernel: [    0.294769] io scheduler deadline registered (default)
Jan  7 21:29:42 ubuntu kernel: [    0.294779] io scheduler cfq registered
Jan  7 21:29:42 ubuntu kernel: [    0.295009] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
Jan  7 21:29:42 ubuntu kernel: [    0.295153] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
Jan  7 21:29:42 ubuntu kernel: [    0.295314] pcieport 0000:00:1c.3: irq 42 for MSI/MSI-X
Jan  7 21:29:42 ubuntu kernel: [    0.295445] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jan  7 21:29:42 ubuntu kernel: [    0.295475] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Jan  7 21:29:42 ubuntu kernel: [    0.295569] intel_idle: does not run on family 6 model 14
Jan  7 21:29:42 ubuntu kernel: [    0.296402] ACPI: AC Adapter [AC] (on-line)
Jan  7 21:29:42 ubuntu kernel: [    0.296520] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
Jan  7 21:29:42 ubuntu kernel: [    0.296861] ACPI: Lid Switch [LID]
Jan  7 21:29:42 ubuntu kernel: [    0.296926] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
Jan  7 21:29:42 ubuntu kernel: [    0.296933] ACPI: Power Button [PBTN]
Jan  7 21:29:42 ubuntu kernel: [    0.296997] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
Jan  7 21:29:42 ubuntu kernel: [    0.297001] ACPI: Sleep Button [SBTN]
Jan  7 21:29:42 ubuntu kernel: [    0.297133] ACPI: Requesting acpi_cpufreq
Jan  7 21:29:42 ubuntu kernel: [    0.535290] Freeing initrd memory: 15184k freed
Jan  7 21:29:42 ubuntu kernel: [    0.546672] ACPI: acpi_idle registered with cpuidle
Jan  7 21:29:42 ubuntu kernel: [    0.555101] thermal LNXTHERM:00: registered as thermal_zone0
Jan  7 21:29:42 ubuntu kernel: [    0.555107] ACPI: Thermal Zone [THM] (36 C)
Jan  7 21:29:42 ubuntu kernel: [    0.555139] ACPI: Battery Slot [BAT0] (battery present)
Jan  7 21:29:42 ubuntu kernel: [    0.555195] GHES: HEST is not enabled!
Jan  7 21:29:42 ubuntu kernel: [    0.555323] isapnp: Scanning for PnP cards...
Jan  7 21:29:42 ubuntu kernel: [    0.562365] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Jan  7 21:29:42 ubuntu kernel: [    0.575448] ACPI: Battery Slot [BAT0] (battery present)
Jan  7 21:29:42 ubuntu kernel: [    0.581821] Linux agpgart interface v0.103
Jan  7 21:29:42 ubuntu kernel: [    0.584692] brd: module loaded
Jan  7 21:29:42 ubuntu kernel: [    0.585809] loop: module loaded
Jan  7 21:29:42 ubuntu kernel: [    0.585989] ata_piix 0000:00:1f.2: version 2.13
Jan  7 21:29:42 ubuntu kernel: [    0.586026] ata_piix 0000:00:1f.2: MAP [
Jan  7 21:29:42 ubuntu kernel: [    0.586029]  P0 P2 IDE IDE ]
Jan  7 21:29:42 ubuntu kernel: [    0.586085] ata_piix 0000:00:1f.2: setting latency timer to 64
Jan  7 21:29:42 ubuntu kernel: [    0.586557] scsi0 : ata_piix
Jan  7 21:29:42 ubuntu kernel: [    0.586655] scsi1 : ata_piix
Jan  7 21:29:42 ubuntu kernel: [    0.587289] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
Jan  7 21:29:42 ubuntu kernel: [    0.587293] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
Jan  7 21:29:42 ubuntu kernel: [    0.587790] Fixed MDIO Bus: probed
Jan  7 21:29:42 ubuntu kernel: [    0.587873] tun: Universal TUN/TAP device driver, 1.6
Jan  7 21:29:42 ubuntu kernel: [    0.587876] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Jan  7 21:29:42 ubuntu kernel: [    0.587950] PPP generic driver version 2.4.2
Jan  7 21:29:42 ubuntu kernel: [    0.588037] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Jan  7 21:29:42 ubuntu kernel: [    0.588091] ehci_hcd 0000:00:1d.7: setting latency timer to 64
Jan  7 21:29:42 ubuntu kernel: [    0.588096] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Jan  7 21:29:42 ubuntu kernel: [    0.588106] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
Jan  7 21:29:42 ubuntu kernel: [    0.588133] ehci_hcd 0000:00:1d.7: using broken periodic workaround
Jan  7 21:29:42 ubuntu kernel: [    0.588148] ehci_hcd 0000:00:1d.7: debug port 1
Jan  7 21:29:42 ubuntu kernel: [    0.592035] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
Jan  7 21:29:42 ubuntu kernel: [    0.592157] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xffa80000
Jan  7 21:29:42 ubuntu kernel: [    0.604027] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Jan  7 21:29:42 ubuntu kernel: [    0.604089] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
Jan  7 21:29:42 ubuntu kernel: [    0.604093] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jan  7 21:29:42 ubuntu kernel: [    0.604096] usb usb1: Product: EHCI Host Controller
Jan  7 21:29:42 ubuntu kernel: [    0.604100] usb usb1: Manufacturer: Linux 3.5.0-45-generic ehci_hcd
Jan  7 21:29:42 ubuntu kernel: [    0.604104] usb usb1: SerialNumber: 0000:00:1d.7
Jan  7 21:29:42 ubuntu kernel: [    0.604281] hub 1-0:1.0: USB hub found
Jan  7 21:29:42 ubuntu kernel: [    0.604288] hub 1-0:1.0: 8 ports detected
Jan  7 21:29:42 ubuntu kernel: [    0.604417] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Jan  7 21:29:42 ubuntu kernel: [    0.604447] uhci_hcd: USB Universal Host Controller Interface driver
Jan  7 21:29:42 ubuntu kernel: [    0.604483] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Jan  7 21:29:42 ubuntu kernel: [    0.604488] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Jan  7 21:29:42 ubuntu kernel: [    0.604496] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Jan  7 21:29:42 ubuntu kernel: [    0.604529] uhci_hcd 0000:00:1d.0: irq 20, io base 0x0000bf80
Jan  7 21:29:42 ubuntu kernel: [    0.604577] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
Jan  7 21:29:42 ubuntu kernel: [    0.604581] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jan  7 21:29:42 ubuntu kernel: [    0.604585] usb usb2: Product: UHCI Host Controller
Jan  7 21:29:42 ubuntu kernel: [    0.604588] usb usb2: Manufacturer: Linux 3.5.0-45-generic uhci_hcd
Jan  7 21:29:42 ubuntu kernel: [    0.604592] usb usb2: SerialNumber: 0000:00:1d.0
Jan  7 21:29:42 ubuntu kernel: [    0.604757] hub 2-0:1.0: USB hub found
Jan  7 21:29:42 ubuntu kernel: [    0.604764] hub 2-0:1.0: 2 ports detected
Jan  7 21:29:42 ubuntu kernel: [    0.604869] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Jan  7 21:29:42 ubuntu kernel: [    0.604874] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Jan  7 21:29:42 ubuntu kernel: [    0.604882] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
Jan  7 21:29:42 ubuntu kernel: [    0.604928] uhci_hcd 0000:00:1d.1: irq 21, io base 0x0000bf60
Jan  7 21:29:42 ubuntu kernel: [    0.604976] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
Jan  7 21:29:42 ubuntu kernel: [    0.604980] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jan  7 21:29:42 ubuntu kernel: [    0.604984] usb usb3: Product: UHCI Host Controller
Jan  7 21:29:42 ubuntu kernel: [    0.604987] usb usb3: Manufacturer: Linux 3.5.0-45-generic uhci_hcd
Jan  7 21:29:42 ubuntu kernel: [    0.604991] usb usb3: SerialNumber: 0000:00:1d.1
Jan  7 21:29:42 ubuntu kernel: [    0.605147] hub 3-0:1.0: USB hub found
Jan  7 21:29:42 ubuntu kernel: [    0.605153] hub 3-0:1.0: 2 ports detected
Jan  7 21:29:42 ubuntu kernel: [    0.605258] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Jan  7 21:29:42 ubuntu kernel: [    0.605263] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Jan  7 21:29:42 ubuntu kernel: [    0.605271] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
Jan  7 21:29:42 ubuntu kernel: [    0.605315] uhci_hcd 0000:00:1d.2: irq 22, io base 0x0000bf40
Jan  7 21:29:42 ubuntu kernel: [    0.605360] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
Jan  7 21:29:42 ubuntu kernel: [    0.605364] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jan  7 21:29:42 ubuntu kernel: [    0.605368] usb usb4: Product: UHCI Host Controller
Jan  7 21:29:42 ubuntu kernel: [    0.605372] usb usb4: Manufacturer: Linux 3.5.0-45-generic uhci_hcd
Jan  7 21:29:42 ubuntu kernel: [    0.605375] usb usb4: SerialNumber: 0000:00:1d.2
Jan  7 21:29:42 ubuntu kernel: [    0.605535] hub 4-0:1.0: USB hub found
Jan  7 21:29:42 ubuntu kernel: [    0.605541] hub 4-0:1.0: 2 ports detected
Jan  7 21:29:42 ubuntu kernel: [    0.605648] uhci_hcd 0000:00:1d.3: setting latency timer to 64
Jan  7 21:29:42 ubuntu kernel: [    0.605653] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Jan  7 21:29:42 ubuntu kernel: [    0.605660] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
Jan  7 21:29:42 ubuntu kernel: [    0.605705] uhci_hcd 0000:00:1d.3: irq 23, io base 0x0000bf20
Jan  7 21:29:42 ubuntu kernel: [    0.605753] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
Jan  7 21:29:42 ubuntu kernel: [    0.605757] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jan  7 21:29:42 ubuntu kernel: [    0.605761] usb usb5: Product: UHCI Host Controller
Jan  7 21:29:42 ubuntu kernel: [    0.605764] usb usb5: Manufacturer: Linux 3.5.0-45-generic uhci_hcd
Jan  7 21:29:42 ubuntu kernel: [    0.605768] usb usb5: SerialNumber: 0000:00:1d.3
Jan  7 21:29:42 ubuntu kernel: [    0.605935] hub 5-0:1.0: USB hub found
Jan  7 21:29:42 ubuntu kernel: [    0.605941] hub 5-0:1.0: 2 ports detected
Jan  7 21:29:42 ubuntu kernel: [    0.606117] usbcore: registered new interface driver libusual
Jan  7 21:29:42 ubuntu kernel: [    0.606187] i8042: PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Jan  7 21:29:42 ubuntu kernel: [    0.609111] serio: i8042 KBD port at 0x60,0x64 irq 1
Jan  7 21:29:42 ubuntu kernel: [    0.609119] serio: i8042 AUX port at 0x60,0x64 irq 12
Jan  7 21:29:42 ubuntu kernel: [    0.609277] mousedev: PS/2 mouse device common for all mice
Jan  7 21:29:42 ubuntu kernel: [    0.609479] rtc_cmos 00:06: RTC can wake from S4
Jan  7 21:29:42 ubuntu kernel: [    0.609661] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
Jan  7 21:29:42 ubuntu kernel: [    0.609702] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
Jan  7 21:29:42 ubuntu kernel: [    0.609781] device-mapper: uevent: version 1.0.3
Jan  7 21:29:42 ubuntu kernel: [    0.609871] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: [email]dm-devel@redhat.com[/email]
Jan  7 21:29:42 ubuntu kernel: [    0.609900] EISA: Probing bus 0 at eisa.0
Jan  7 21:29:42 ubuntu kernel: [    0.609969] EISA: Mainboard R__FFFF detected.
Jan  7 21:29:42 ubuntu kernel: [    0.609995] Cannot allocate resource for EISA slot 1
Jan  7 21:29:42 ubuntu kernel: [    0.609998] Cannot allocate resource for EISA slot 2
Jan  7 21:29:42 ubuntu kernel: [    0.610029] EISA: Detected 0 cards.
Jan  7 21:29:42 ubuntu kernel: [    0.610106] cpuidle: using governor ladder
Jan  7 21:29:42 ubuntu kernel: [    0.610195] cpuidle: using governor menu
Jan  7 21:29:42 ubuntu kernel: [    0.610198] EFI Variables Facility v0.08 2004-May-17
Jan  7 21:29:42 ubuntu kernel: [    0.610468] ashmem: initialized
Jan  7 21:29:42 ubuntu kernel: [    0.610670] TCP: cubic registered
Jan  7 21:29:42 ubuntu kernel: [    0.610836] NET: Registered protocol family 10
Jan  7 21:29:42 ubuntu kernel: [    0.611109] NET: Registered protocol family 17
Jan  7 21:29:42 ubuntu kernel: [    0.611127] Key type dns_resolver registered
Jan  7 21:29:42 ubuntu kernel: [    0.611238] Using IPI No-Shortcut mode
Jan  7 21:29:42 ubuntu kernel: [    0.611362] PM: Hibernation image not present or could not be loaded.
Jan  7 21:29:42 ubuntu kernel: [    0.611385] registered taskstats version 1
Jan  7 21:29:42 ubuntu kernel: [    0.612706] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
Jan  7 21:29:42 ubuntu kernel: [    0.614935] Key type trusted registered
Jan  7 21:29:42 ubuntu kernel: [    0.617936] Key type encrypted registered
Jan  7 21:29:42 ubuntu kernel: [    0.620991]   Magic number: 14:647:499
Jan  7 21:29:42 ubuntu kernel: [    0.621134] rtc_cmos 00:06: setting system clock to 2014-01-07 21:28:52 UTC (1389130132)
Jan  7 21:29:42 ubuntu kernel: [    0.621914] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jan  7 21:29:42 ubuntu kernel: [    0.621917] EDD information not available.
Jan  7 21:29:42 ubuntu kernel: [    0.756635] ata1.00: ATA-7: ST980811AS, 3.CDD, max UDMA/133
Jan  7 21:29:42 ubuntu kernel: [    0.756640] ata1.00: 156301488 sectors, multi 8: LBA48 NCQ (depth 0/32)
Jan  7 21:29:42 ubuntu kernel: [    0.764405] ata2.00: ATAPI: CD-RW/DVD-ROM DW224EV, D.CF, max UDMA/33
Jan  7 21:29:42 ubuntu kernel: [    0.773301] ata1.00: configured for UDMA/133
Jan  7 21:29:42 ubuntu kernel: [    0.780298] ata2.00: configured for UDMA/33
Jan  7 21:29:42 ubuntu kernel: [    0.914581] isapnp: No Plug & Play device found
Jan  7 21:29:42 ubuntu kernel: [    0.914795] scsi 0:0:0:0: Direct-Access     ATA      ST980811AS       3.CD PQ: 0 ANSI: 5
Jan  7 21:29:42 ubuntu kernel: [    0.914984] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
Jan  7 21:29:42 ubuntu kernel: [    0.915027] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jan  7 21:29:42 ubuntu kernel: [    0.915056] sd 0:0:0:0: [sda] Write Protect is off
Jan  7 21:29:42 ubuntu kernel: [    0.915061] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jan  7 21:29:42 ubuntu dbus[521]: [system] Activating service name='org.freedesktop.PolicyKit1' (using servicehelper)
Jan  7 21:29:42 ubuntu kernel: [    0.915092] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jan  7 21:29:42 ubuntu kernel: [    1.029258]  sda: sda1 sda2 sda3 sda4 < sda5 >
Jan  7 21:29:42 ubuntu kernel: [    1.029963] sd 0:0:0:0: [sda] Attached SCSI disk
Jan  7 21:29:42 ubuntu kernel: [    1.031555] scsi 1:0:0:0: CD-ROM            TEAC     CDRWDVD DW224EV  D.CF PQ: 0 ANSI: 5
Jan  7 21:29:42 ubuntu kernel: [    1.033710] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
Jan  7 21:29:42 ubuntu kernel: [    1.033714] cdrom: Uniform CD-ROM driver Revision: 3.20
Jan  7 21:29:42 ubuntu kernel: [    1.033885] sr 1:0:0:0: Attached scsi CD-ROM sr0
Jan  7 21:29:42 ubuntu kernel: [    1.034050] sr 1:0:0:0: Attached scsi generic sg1 type 5
Jan  7 21:29:42 ubuntu kernel: [    1.034310] Freeing unused kernel memory: 764k freed
Jan  7 21:29:42 ubuntu kernel: [    1.034813] Write protecting the kernel text: 6064k
Jan  7 21:29:42 ubuntu kernel: [    1.034851] Write protecting the kernel read-only data: 2480k
Jan  7 21:29:42 ubuntu kernel: [    1.034853] NX-protecting the kernel data: 4176k
Jan  7 21:29:42 ubuntu kernel: [    1.148221] ssb: Found chip with id 0x4311, rev 0x01 and package 0x00
Jan  7 21:29:42 ubuntu kernel: [    1.148242] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x11, vendor 0x4243)
Jan  7 21:29:42 ubuntu kernel: [    1.148256] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0A, vendor 0x4243)
Jan  7 21:29:42 ubuntu kernel: [    1.148270] ssb: Core 2 found: USB 1.1 Host (cc 0x817, rev 0x03, vendor 0x4243)
Jan  7 21:29:42 ubuntu kernel: [    1.148280] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x01, vendor 0x4243)
Jan  7 21:29:42 ubuntu kernel: [    1.156071] usb 2-1: new low-speed USB device number 2 using uhci_hcd
Jan  7 21:29:42 ubuntu kernel: [    1.184640] sdhci: Secure Digital Host Controller Interface driver
Jan  7 21:29:42 ubuntu kernel: [    1.184646] sdhci: Copyright(c) Pierre Ossman
Jan  7 21:29:42 ubuntu kernel: [    1.212591] ssb: Sonics Silicon Backplane found on PCI device 0000:0b:00.0
Jan  7 21:29:42 ubuntu kernel: [    1.236240] firewire_ohci 0000:03:01.0: added OHCI v1.10 device as card 0, 4 IR + 4 IT contexts, quirks 0x11
Jan  7 21:29:42 ubuntu kernel: [    1.236489] sdhci-pci 0000:03:01.1: SDHCI controller found [1180:0822] (rev 19)
Jan  7 21:29:42 ubuntu kernel: [    1.237576] mmc0: no vmmc regulator found
Jan  7 21:29:42 ubuntu kernel: [    1.238617] Registered led device: mmc0::
Jan  7 21:29:42 ubuntu kernel: [    1.268068] mmc0: SDHCI controller on PCI [0000:03:01.1] using DMA
Jan  7 21:29:42 ubuntu kernel: [    1.296063] ssb: Found chip with id 0x4401, rev 0x02 and package 0x00
Jan  7 21:29:42 ubuntu kernel: [    1.296076] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243)
Jan  7 21:29:42 ubuntu kernel: [    1.296084] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243)
Jan  7 21:29:42 ubuntu kernel: [    1.296092] ssb: Core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243)
Jan  7 21:29:42 ubuntu kernel: [    1.327610] usb 2-1: New USB device found, idVendor=1d57, idProduct=0008
Jan  7 21:29:42 ubuntu kernel: [    1.327617] usb 2-1: New USB device strings: Mfr=0, Product=1, SerialNumber=0
Jan  7 21:29:42 ubuntu kernel: [    1.327621] usb 2-1: Product: 2.4G Wireless Optical Mouse
Jan  7 21:29:42 ubuntu kernel: [    1.336697] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
Jan  7 21:29:42 ubuntu kernel: [    1.336934] b44: Broadcom 44xx/47xx 10/100 PCI ethernet driver version 2.0
Jan  7 21:29:42 ubuntu kernel: [    1.349617] usbcore: registered new interface driver usbhid
Jan  7 21:29:42 ubuntu kernel: [    1.349620] usbhid: USB HID core driver
Jan  7 21:29:42 ubuntu kernel: [    1.359086] input: 2.4G Wireless Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input4
Jan  7 21:29:42 ubuntu kernel: [    1.359386] hid-generic 0003:1D57:0008.0001: input,hidraw0: USB HID v1.10 Mouse [2.4G Wireless Optical Mouse] on usb-0000:00:1d.0-1/input0
Jan  7 21:29:42 ubuntu kernel: [    1.360111] b44 ssb1:0: eth0: Broadcom 44xx/47xx 10/100 PCI ethernet driver 00:19:b9:71:50:70
Jan  7 21:29:42 ubuntu kernel: [    1.572058] usb 3-1: new low-speed USB device number 2 using uhci_hcd
Jan  7 21:29:42 ubuntu kernel: [    1.736209] firewire_core 0000:03:01.0: created device fw0: GUID 324fc00003a87961, S400
Jan  7 21:29:42 ubuntu kernel: [    1.741998] usb 3-1: New USB device found, idVendor=17ef, idProduct=600e
Jan  7 21:29:42 ubuntu kernel: [    1.742003] usb 3-1: New USB device strings: Mfr=0, Product=2, SerialNumber=0
Jan  7 21:29:42 ubuntu kernel: [    1.742006] usb 3-1: Product: Lenovo Optical Mouse
Jan  7 21:29:42 ubuntu kernel: [    1.770065] input: Lenovo Optical Mouse as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input5
Jan  7 21:29:42 ubuntu kernel: [    1.770264] hid-generic 0003:17EF:600E.0002: input,hidraw1: USB HID v1.11 Mouse [Lenovo Optical Mouse] on usb-0000:00:1d.1-1/input0
Jan  7 21:29:42 ubuntu kernel: [    3.038783] EXT3-fs (loop0): recovery required on readonly filesystem
Jan  7 21:29:42 ubuntu kernel: [    3.038790] EXT3-fs (loop0): write access will be enabled during recovery
Jan  7 21:29:42 ubuntu kernel: [    9.297236] kjournald starting.  Commit interval 5 seconds
Jan  7 21:29:42 ubuntu kernel: [    9.297410] EXT3-fs (loop0): orphan cleanup on readonly fs
Jan  7 21:29:42 ubuntu kernel: [    9.297420] ext3_orphan_cleanup: deleting unreferenced inode 591722
Jan  7 21:29:42 ubuntu kernel: [    9.297467] ext3_orphan_cleanup: deleting unreferenced inode 597907
Jan  7 21:29:42 ubuntu kernel: [    9.297488] ext3_orphan_cleanup: deleting unreferenced inode 591720
Jan  7 21:29:42 ubuntu kernel: [    9.297503] ext3_orphan_cleanup: deleting unreferenced inode 627764
Jan  7 21:29:42 ubuntu kernel: [    9.297526] EXT3-fs (loop0): 4 orphan inodes deleted
Jan  7 21:29:42 ubuntu kernel: [    9.388128] EXT3-fs (loop0): recovery complete
Jan  7 21:29:42 ubuntu kernel: [    9.388133] EXT3-fs (loop0): mounted filesystem with ordered data mode
Jan  7 21:29:42 ubuntu kernel: [   49.290924] Adding 262140k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:1 across:262140k 
Jan  7 21:29:42 ubuntu kernel: [   49.302268] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Jan  7 21:29:42 ubuntu kernel: [   49.360198] EXT3-fs (loop0): using internal journal
Jan  7 21:29:42 ubuntu kernel: [   50.310110] type=1400 audit(1389148182.183:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=656 comm="apparmor_parser"
Jan  7 21:29:42 ubuntu kernel: [   50.310129] type=1400 audit(1389148182.183:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=658 comm="apparmor_parser"
Jan  7 21:29:42 ubuntu kernel: [   50.310750] type=1400 audit(1389148182.183:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=656 comm="apparmor_parser"
Jan  7 21:29:42 ubuntu kernel: [   50.310763] type=1400 audit(1389148182.183:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=658 comm="apparmor_parser"
Jan  7 21:29:42 ubuntu kernel: [   50.311110] type=1400 audit(1389148182.183:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=656 comm="apparmor_parser"
Jan  7 21:29:42 ubuntu kernel: [   50.311124] type=1400 audit(1389148182.183:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=658 comm="apparmor_parser"
Jan  7 21:29:42 ubuntu kernel: [   50.680095] type=1400 audit(1389148182.555:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=754 comm="apparmor_parser"
Jan  7 21:29:42 ubuntu kernel: [   50.680756] type=1400 audit(1389148182.555:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=754 comm="apparmor_parser"
Jan  7 21:29:42 ubuntu kernel: [   50.680861] type=1400 audit(1389148182.555:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=753 comm="apparmor_parser"
Jan  7 21:29:42 ubuntu kernel: [   50.681124] type=1400 audit(1389148182.555:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=754 comm="apparmor_parser"
Jan  7 21:29:42 ubuntu polkitd[778]: started daemon version 0.104 using authority implementation `local' version `0.104'
Jan  7 21:29:42 ubuntu dbus[521]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'
Jan  7 21:29:42 ubuntu NetworkManager[726]:    SCPlugin-Ifupdown: init!
Jan  7 21:29:42 ubuntu NetworkManager[726]:    SCPlugin-Ifupdown: update_system_hostname
Jan  7 21:29:42 ubuntu NetworkManager[726]:    SCPluginIfupdown: management mode: unmanaged
Jan  7 21:29:42 ubuntu NetworkManager[726]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:03:00.0/ssb1:0/net/eth0, iface: eth0)
Jan  7 21:29:42 ubuntu NetworkManager[726]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:03:00.0/ssb1:0/net/eth0, iface: eth0): no ifupdown configuration found.
Jan  7 21:29:42 ubuntu NetworkManager[726]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Jan  7 21:29:42 ubuntu NetworkManager[726]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Jan  7 21:29:42 ubuntu NetworkManager[726]:    SCPlugin-Ifupdown: end _init.
Jan  7 21:29:42 ubuntu NetworkManager[726]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Jan  7 21:29:42 ubuntu NetworkManager[726]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Jan  7 21:29:42 ubuntu NetworkManager[726]:    Ifupdown: get unmanaged devices count: 0
Jan  7 21:29:42 ubuntu NetworkManager[726]:    SCPlugin-Ifupdown: (144771128) ... get_connections.
Jan  7 21:29:42 ubuntu NetworkManager[726]:    SCPlugin-Ifupdown: (144771128) ... get_connections (managed=false): return empty list.
Jan  7 21:29:42 ubuntu NetworkManager[726]:    keyfile: parsing 07FX09042629 1 ... 
Jan  7 21:29:42 ubuntu NetworkManager[726]:    keyfile:     read connection '07FX09042629 1'
Jan  7 21:29:42 ubuntu NetworkManager[726]:    keyfile: parsing 8LGL3 ... 
Jan  7 21:29:42 ubuntu NetworkManager[726]:    keyfile:     read connection '8LGL3'
Jan  7 21:29:42 ubuntu NetworkManager[726]:    keyfile: parsing SecurityKiss ... 
Jan  7 21:29:42 ubuntu NetworkManager[726]:    keyfile:     read connection 'SecurityKiss'
Jan  7 21:29:42 ubuntu NetworkManager[726]:    keyfile: parsing VAGE1 ... 
Jan  7 21:29:43 ubuntu NetworkManager[726]:    keyfile:     read connection 'VAGE1'
Jan  7 21:29:43 ubuntu NetworkManager[726]:    keyfile: parsing MQZ-Wireless ... 
Jan  7 21:29:43 ubuntu NetworkManager[726]:    keyfile:     read connection 'MQZ-Wireless'
Jan  7 21:29:43 ubuntu NetworkManager[726]:    keyfile: parsing Galaxy S III_5339 ... 
Jan  7 21:29:43 ubuntu NetworkManager[726]:    keyfile:     read connection 'Galaxy S III_5339'
Jan  7 21:29:43 ubuntu NetworkManager[726]:    Ifupdown: get unmanaged devices count: 0
Jan  7 21:29:43 ubuntu NetworkManager[726]: <info> modem-manager is now available
Jan  7 21:29:43 ubuntu NetworkManager[726]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jan  7 21:29:43 ubuntu NetworkManager[726]: <info> WiFi enabled by radio killswitch; enabled by state file
Jan  7 21:29:43 ubuntu NetworkManager[726]: <info> WWAN enabled by radio killswitch; enabled by state file
Jan  7 21:29:43 ubuntu NetworkManager[726]: <info> WiMAX enabled by radio killswitch; enabled by state file
Jan  7 21:29:43 ubuntu NetworkManager[726]: <info> Networking is enabled by state file
Jan  7 21:29:43 ubuntu NetworkManager[726]: <warn> failed to allocate link cache: (-10) Operation not supported
Jan  7 21:29:43 ubuntu NetworkManager[726]: <info> (eth0): carrier is OFF
Jan  7 21:29:43 ubuntu NetworkManager[726]: <info> (eth0): new Ethernet device (driver: 'b44' ifindex: 2)
Jan  7 21:29:43 ubuntu NetworkManager[726]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Jan  7 21:29:43 ubuntu NetworkManager[726]: <info> (eth0): now managed
Jan  7 21:29:43 ubuntu NetworkManager[726]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jan  7 21:29:43 ubuntu NetworkManager[726]: <info> (eth0): bringing up device.
Jan  7 21:29:43 ubuntu NetworkManager[726]: <info> (eth0): preparing device.
Jan  7 21:29:43 ubuntu NetworkManager[726]: <info> (eth0): deactivating device (reason 'managed') [2]
Jan  7 21:29:43 ubuntu NetworkManager[726]: <info> Added default wired connection 'Wired connection 1' for /sys/devices/pci0000:00/0000:00:1e.0/0000:03:00.0/ssb1:0/net/eth0
Jan  7 21:29:43 ubuntu kernel: [   51.714158] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Jan  7 21:29:43 ubuntu kernel: [   51.714677] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Jan  7 21:29:44 ubuntu kernel: [   52.373707] wmi: Mapper loaded
Jan  7 21:29:44 ubuntu cron[804]: (CRON) INFO (pidfile fd = 3)
Jan  7 21:29:44 ubuntu anacron[864]: Anacron 2.3 started on 2014-01-07
Jan  7 21:29:44 ubuntu acpid: starting up with proc fs
Jan  7 21:29:44 ubuntu acpid: 35 rules loaded
Jan  7 21:29:44 ubuntu acpid: waiting for events: event logging is off
Jan  7 21:29:45 ubuntu kernel: [   53.189605] microcode: CPU0 sig=0x6ec, pf=0x80, revision=0x59
Jan  7 21:29:45 ubuntu kernel: [   53.451637] Bluetooth: Core ver 2.16
Jan  7 21:29:45 ubuntu kernel: [   53.451678] NET: Registered protocol family 31
Jan  7 21:29:45 ubuntu kernel: [   53.451680] Bluetooth: HCI device and connection manager initialized
Jan  7 21:29:45 ubuntu kernel: [   53.451683] Bluetooth: HCI socket layer initialized
Jan  7 21:29:45 ubuntu kernel: [   53.451686] Bluetooth: L2CAP socket layer initialized
Jan  7 21:29:45 ubuntu kernel: [   53.451692] Bluetooth: SCO socket layer initialized
Jan  7 21:29:45 ubuntu bluetoothd[639]: Failed to init alert plugin
Jan  7 21:29:45 ubuntu bluetoothd[639]: Failed to init time plugin
Jan  7 21:29:45 ubuntu bluetoothd[639]: Failed to init proximity plugin
Jan  7 21:29:45 ubuntu cron[887]: (CRON) STARTUP (fork ok)
Jan  7 21:29:45 ubuntu kernel: [   53.527713] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
Jan  7 21:29:45 ubuntu kernel: [   53.554609] acpi device:23: registered as cooling_device2
Jan  7 21:29:45 ubuntu kernel: [   53.555834] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
Jan  7 21:29:45 ubuntu kernel: [   53.556265] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:20/LNXVIDEO:00/input/input6
Jan  7 21:29:45 ubuntu kernel: [   53.556504] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
Jan  7 21:29:45 ubuntu cron[887]: (CRON) INFO (Running @reboot jobs)
Jan  7 21:29:46 ubuntu kernel: [   54.767389] input: Dell WMI hotkeys as /devices/virtual/input/input7
Jan  7 21:29:48 ubuntu anacron[864]: Will run job `cron.daily' in 5 min.
Jan  7 21:29:48 ubuntu anacron[864]: Jobs will be executed sequentially
Jan  7 21:29:48 ubuntu bluetoothd[639]: Failed to init gatt_example plugin
Jan  7 21:29:48 ubuntu kernel: [   56.269642] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Jan  7 21:29:48 ubuntu kernel: [   56.269648] Bluetooth: BNEP filters: protocol multicast
Jan  7 21:29:48 ubuntu kernel: [   56.271271] r592 0000:03:01.2: setting latency timer to 64
Jan  7 21:29:48 ubuntu kernel: [   56.273997] r592: driver successfully loaded
Jan  7 21:29:48 ubuntu kernel: [   56.392156] Bluetooth: RFCOMM TTY layer initialized
Jan  7 21:29:48 ubuntu kernel: [   56.392172] Bluetooth: RFCOMM socket layer initialized
Jan  7 21:29:48 ubuntu kernel: [   56.392174] Bluetooth: RFCOMM ver 1.11
Jan  7 21:29:48 ubuntu kernel: [   56.912166] psmouse serio1: synaptics: Touchpad model: 1, fw: 6.2, id: 0x180b1, caps: 0xa04713/0x200000/0x0
Jan  7 21:29:48 ubuntu kernel: [   56.948315] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
Jan  7 21:29:49 ubuntu kernel: [   57.967871] microcode: CPU1 sig=0x6ec, pf=0x80, revision=0x59
Jan  7 21:29:49 ubuntu acpid: client connected from 889[0:0]
Jan  7 21:29:49 ubuntu acpid: 1 client rule loaded
Jan  7 21:29:49 ubuntu kernel: [   57.972845] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
Jan  7 21:29:49 ubuntu kernel: [   57.980780] intel_rng: FWH not detected
Jan  7 21:29:49 ubuntu udev-configure-printer: add /module/lp
Jan  7 21:29:49 ubuntu udev-configure-printer: Failed to get parent
Jan  7 21:29:49 ubuntu kernel: [   58.109416] lp: driver loaded but no devices found
Jan  7 21:29:50 ubuntu kernel: [   58.151347] cfg80211: Calling CRDA to update world regulatory domain
Jan  7 21:29:50 ubuntu kernel: [   58.160720] cfg80211: World regulatory domain updated:
Jan  7 21:29:50 ubuntu kernel: [   58.160727] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jan  7 21:29:50 ubuntu kernel: [   58.160730] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  7 21:29:50 ubuntu kernel: [   58.160734] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jan  7 21:29:50 ubuntu kernel: [   58.160737] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jan  7 21:29:50 ubuntu kernel: [   58.160740] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  7 21:29:50 ubuntu kernel: [   58.160743] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  7 21:29:50 ubuntu kernel: [   58.167745] ppdev: user-space parallel port driver
Jan  7 21:29:50 ubuntu kernel: [   58.748073] ACPI Warning: 0xf400b410-0xf400b414 SystemMemory conflicts with Region \RCRB 1 (20120320/utaddress-251)
Jan  7 21:29:50 ubuntu kernel: [   58.748086] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Jan  7 21:29:50 ubuntu kernel: [   58.748089] lpc_ich: Resource conflict(s) found affecting iTCO_wdt
Jan  7 21:29:50 ubuntu kernel: [   58.768655] audit_printk_skb: 42 callbacks suppressed
Jan  7 21:29:50 ubuntu kernel: [   58.768661] type=1400 audit(1389148190.643:26): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1071 comm="apparmor_parser"
Jan  7 21:29:50 ubuntu kernel: [   58.769452] type=1400 audit(1389148190.643:27): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1071 comm="apparmor_parser"
Jan  7 21:29:50 ubuntu udev-configure-printer: add /module/lpc_ich
Jan  7 21:29:50 ubuntu udev-configure-printer: Failed to get parent
Jan  7 21:29:50 ubuntu udev-configure-printer: add /bus/pci/drivers/lpc_ich
Jan  7 21:29:50 ubuntu udev-configure-printer: Failed to get parent
Jan  7 21:29:50 ubuntu kernel: [   58.865969] r852 0000:03:01.3: setting latency timer to 64
Jan  7 21:29:50 ubuntu kernel: [   58.866356] r852: Non dma capable device detected, dma disabled
Jan  7 21:29:50 ubuntu kernel: [   58.866377] r852: driver loaded successfully
Jan  7 21:29:50 ubuntu kernel: [   58.974507] [drm] Initialized drm 1.1.0 20060810
Jan  7 21:29:50 ubuntu kernel: [   59.038141] leds_ss4200: no LED devices found
Jan  7 21:29:51 ubuntu kernel: [   59.309061] gpio_ich: GPIO from 206 to 255 on gpio_ich
Jan  7 21:29:51 ubuntu kernel: [   59.631979] snd_hda_intel 0000:00:1b.0: irq 43 for MSI/MSI-X
Jan  7 21:29:51 ubuntu kernel: [   59.639530] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
Jan  7 21:29:51 ubuntu kernel: [   59.641599] [drm] radeon defaulting to kernel modesetting.
Jan  7 21:29:51 ubuntu kernel: [   59.641604] [drm] radeon kernel modesetting enabled.
Jan  7 21:29:51 ubuntu kernel: [   59.642201] [drm] initializing kernel modesetting (RV515 0x1002:0x7145 0x1028:0x2003).
Jan  7 21:29:51 ubuntu kernel: [   59.642225] [drm] register mmio base: 0xEFDF0000
Jan  7 21:29:51 ubuntu kernel: [   59.642227] [drm] register mmio size: 65536
Jan  7 21:29:51 ubuntu kernel: [   59.642373] ATOM BIOS: M54P
Jan  7 21:29:51 ubuntu kernel: [   59.642398] [drm] Generation 2 PCI interface, using max accessible memory
Jan  7 21:29:51 ubuntu kernel: [   59.642406] radeon 0000:01:00.0: VRAM: 256M 0x0000000000000000 - 0x000000000FFFFFFF (128M used)
Jan  7 21:29:51 ubuntu kernel: [   59.642411] radeon 0000:01:00.0: GTT: 512M 0x0000000010000000 - 0x000000002FFFFFFF
Jan  7 21:29:51 ubuntu kernel: [   59.643092] [drm] Detected VRAM RAM=256M, BAR=256M
Jan  7 21:29:51 ubuntu kernel: [   59.643098] [drm] RAM width 64bits DDR
Jan  7 21:29:51 ubuntu kernel: [   59.643218] [TTM] Zone  kernel: Available graphics memory: 435614 kiB
Jan  7 21:29:51 ubuntu kernel: [   59.643221] [TTM] Zone highmem: Available graphics memory: 1551176 kiB
Jan  7 21:29:51 ubuntu kernel: [   59.643223] [TTM] Initializing pool allocator
Jan  7 21:29:51 ubuntu kernel: [   59.643230] [TTM] Initializing DMA pool allocator
Jan  7 21:29:51 ubuntu kernel: [   59.643268] [drm] radeon: 128M of VRAM memory ready
Jan  7 21:29:51 ubuntu kernel: [   59.643271] [drm] radeon: 512M of GTT memory ready.
Jan  7 21:29:51 ubuntu kernel: [   59.643300] [drm] GART: num cpu pages 131072, num gpu pages 131072
Jan  7 21:29:51 ubuntu kernel: [   59.645794] [drm] radeon: 1 quad pipes, 1 z pipes initialized.
Jan  7 21:29:51 ubuntu kernel: [   59.647543] [drm] PCIE GART of 512M enabled (table at 0x0000000000040000).
Jan  7 21:29:51 ubuntu kernel: [   59.647589] radeon 0000:01:00.0: WB enabled
Jan  7 21:29:51 ubuntu kernel: [   59.647596] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000010000000 and cpu addr 0xffd2a000
Jan  7 21:29:51 ubuntu kernel: [   59.647600] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
Jan  7 21:29:51 ubuntu kernel: [   59.647602] [drm] Driver supports precise vblank timestamp query.
Jan  7 21:29:51 ubuntu kernel: [   59.647638] [drm] radeon: irq initialized.
Jan  7 21:29:51 ubuntu kernel: [   59.648497] [drm] Loading R500 Microcode
Jan  7 21:29:51 ubuntu kernel: [   59.654693] [drm] radeon: ring at 0x0000000010001000
Jan  7 21:29:51 ubuntu kernel: [   59.654734] [drm] ring test succeeded in 9 usecs
Jan  7 21:29:51 ubuntu kernel: [   59.655001] [drm] ib test succeeded in 0 usecs
Jan  7 21:29:51 ubuntu kernel: [   59.656452] [drm] radeon atom DIG backlight initialized
Jan  7 21:29:51 ubuntu kernel: [   59.656456] [drm] Radeon Display Connectors
Jan  7 21:29:51 ubuntu kernel: [   59.656459] [drm] Connector 0:
Jan  7 21:29:51 ubuntu kernel: [   59.656461] [drm]   VGA-1
Jan  7 21:29:51 ubuntu kernel: [   59.656465] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
Jan  7 21:29:51 ubuntu kernel: [   59.656467] [drm]   Encoders:
Jan  7 21:29:51 ubuntu kernel: [   59.656470] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
Jan  7 21:29:51 ubuntu kernel: [   59.656472] [drm] Connector 1:
Jan  7 21:29:51 ubuntu kernel: [   59.656474] [drm]   LVDS-1
Jan  7 21:29:51 ubuntu kernel: [   59.656478] [drm]   DDC: 0x7e30 0x7e30 0x7e34 0x7e34 0x7e38 0x7e38 0x7e3c 0x7e3c
Jan  7 21:29:51 ubuntu kernel: [   59.656480] [drm]   Encoders:
Jan  7 21:29:51 ubuntu kernel: [   59.656482] [drm]     LCD1: INTERNAL_LVTM1
Jan  7 21:29:51 ubuntu kernel: [   59.656484] [drm] Connector 2:
Jan  7 21:29:51 ubuntu kernel: [   59.656486] [drm]   SVIDEO-1
Jan  7 21:29:51 ubuntu kernel: [   59.656488] [drm]   Encoders:
Jan  7 21:29:51 ubuntu kernel: [   59.656490] [drm]     TV1: INTERNAL_KLDSCP_DAC2
Jan  7 21:29:51 ubuntu kernel: [   59.656515] [drm] radeon: power management initialized
Jan  7 21:29:51 ubuntu kernel: [   59.693324] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
Jan  7 21:29:51 ubuntu kernel: [   59.693575] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
Jan  7 21:29:51 ubuntu kernel: [   59.711584] Broadcom 43xx driver loaded [ Features: PNL ]
Jan  7 21:29:51 ubuntu kernel: [   59.751381] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
Jan  7 21:29:51 ubuntu kernel: [   59.751387] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  7 21:29:51 ubuntu kernel: [   59.751390] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
Jan  7 21:29:51 ubuntu kernel: [   59.751394] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  7 21:29:51 ubuntu kernel: [   59.751396] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
Jan  7 21:29:51 ubuntu kernel: [   59.751400] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  7 21:29:51 ubuntu kernel: [   59.751402] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
Jan  7 21:29:51 ubuntu kernel: [   59.751406] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  7 21:29:51 ubuntu kernel: [   59.751409] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
Jan  7 21:29:51 ubuntu kernel: [   59.751412] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  7 21:29:51 ubuntu kernel: [   59.751415] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
Jan  7 21:29:51 ubuntu kernel: [   59.751418] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  7 21:29:51 ubuntu kernel: [   59.751421] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
Jan  7 21:29:51 ubuntu kernel: [   59.751424] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  7 21:29:51 ubuntu kernel: [   59.751427] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
Jan  7 21:29:51 ubuntu kernel: [   59.751430] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  7 21:29:51 ubuntu kernel: [   59.751433] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
Jan  7 21:29:51 ubuntu kernel: [   59.751436] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  7 21:29:51 ubuntu kernel: [   59.751439] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
Jan  7 21:29:51 ubuntu kernel: [   59.751442] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  7 21:29:51 ubuntu kernel: [   59.751445] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
Jan  7 21:29:51 ubuntu kernel: [   59.751448] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  7 21:29:51 ubuntu kernel: [   59.751451] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
Jan  7 21:29:51 ubuntu kernel: [   59.751454] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jan  7 21:29:51 ubuntu kernel: [   59.751457] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
Jan  7 21:29:51 ubuntu kernel: [   59.751460] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jan  7 21:29:51 ubuntu kernel: [   59.751463] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
Jan  7 21:29:51 ubuntu kernel: [   59.751466] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jan  7 21:29:51 ubuntu NetworkManager[726]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:1c.0/0000:0b:00.0/ssb0:0/ieee80211/phy0/rfkill0) (driver (unknown))
Jan  7 21:29:51 ubuntu udev-configure-printer: add /module/lp
Jan  7 21:29:51 ubuntu udev-configure-printer: Failed to get parent
Jan  7 21:29:51 ubuntu udev-configure-printer: add /module/lpc_ich
Jan  7 21:29:51 ubuntu udev-configure-printer: Failed to get parent
Jan  7 21:29:51 ubuntu kernel: [   59.800229] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
Jan  7 21:29:51 ubuntu kernel: [   59.800664] Registered led device: b43-phy0::tx
Jan  7 21:29:51 ubuntu kernel: [   59.800695] Registered led device: b43-phy0::rx
Jan  7 21:29:51 ubuntu kernel: [   59.800725] Registered led device: b43-phy0::radio
Jan  7 21:29:51 ubuntu NetworkManager[726]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:0b:00.0/ssb0:0/net/wlan0, iface: wlan0)
Jan  7 21:29:51 ubuntu NetworkManager[726]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:0b:00.0/ssb0:0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jan  7 21:29:51 ubuntu NetworkManager[726]: <info> (wlan0): using nl80211 for WiFi device control
Jan  7 21:29:51 ubuntu NetworkManager[726]: <warn> (wlan0): driver supports Access Point (AP) mode
Jan  7 21:29:51 ubuntu NetworkManager[726]: <info> (wlan0): new 802.11 WiFi device (driver: 'b43' ifindex: 3)
Jan  7 21:29:51 ubuntu NetworkManager[726]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Jan  7 21:29:51 ubuntu NetworkManager[726]: <info> (wlan0): now managed
Jan  7 21:29:51 ubuntu NetworkManager[726]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jan  7 21:29:51 ubuntu NetworkManager[726]: <info> (wlan0): bringing up device.
Jan  7 21:29:51 ubuntu kernel: [   59.972078] b43-phy0: Loading firmware version 508.1084 (2009-01-14 01:32:01)
Jan  7 21:29:51 ubuntu kernel: [   60.045640] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan  7 21:29:51 ubuntu NetworkManager[726]: <info> (wlan0): preparing device.
Jan  7 21:29:51 ubuntu NetworkManager[726]: <info> (wlan0): deactivating device (reason 'managed') [2]
Jan  7 21:29:51 ubuntu kernel: [   60.050015] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan  7 21:29:51 ubuntu dbus[521]: [system] Activating service name='fi.w1.wpa_supplicant1' (using servicehelper)
Jan  7 21:29:51 ubuntu dbus[521]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'
Jan  7 21:29:51 ubuntu NetworkManager[726]: <info> wpa_supplicant started
Jan  7 21:29:51 ubuntu NetworkManager[726]: <info> (wlan0): supplicant interface state: starting -> ready
Jan  7 21:29:51 ubuntu NetworkManager[726]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jan  7 21:29:51 ubuntu NetworkManager[726]: <info> (wlan0): supplicant interface state: ready -> inactive
Jan  7 21:29:51 ubuntu NetworkManager[726]: <warn> Trying to remove a non-existant call id.
Jan  7 21:29:52 ubuntu kernel: [   60.122833] [drm] fb mappable at 0xD00C0000
Jan  7 21:29:52 ubuntu kernel: [   60.122838] [drm] vram apper at 0xD0000000
Jan  7 21:29:52 ubuntu kernel: [   60.122841] [drm] size 4096000
Jan  7 21:29:52 ubuntu kernel: [   60.122843] [drm] fb depth is 24
Jan  7 21:29:52 ubuntu kernel: [   60.122845] [drm]    pitch is 5120
Jan  7 21:29:52 ubuntu kernel: [   60.123095] fbcon: radeondrmfb (fb0) is primary device
Jan  7 21:29:52 ubuntu kernel: [   60.123384] Console: switching to colour frame buffer device 160x50
Jan  7 21:29:52 ubuntu kernel: [   60.123397] fb0: radeondrmfb frame buffer device
Jan  7 21:29:52 ubuntu kernel: [   60.123400] drm: registered panic notifier
Jan  7 21:29:52 ubuntu kernel: [   60.123421] [drm] Initialized radeon 2.18.0 20080528 for 0000:01:00.0 on minor 0
Jan  7 21:29:52 ubuntu dbus[521]: [system] Activating service name='org.freedesktop.Accounts' (using servicehelper)
Jan  7 21:29:52 ubuntu dbus[521]: [system] Successfully activated service 'org.freedesktop.Accounts'
Jan  7 21:29:52 ubuntu accounts-daemon[1151]: started daemon version 0.6.15
Jan  7 21:29:52 ubuntu dbus[521]: [system] Activating service name='org.freedesktop.ConsoleKit' (using servicehelper)
Jan  7 21:29:52 ubuntu dbus[521]: [system] Successfully activated service 'org.freedesktop.ConsoleKit'
Jan  7 21:29:53 ubuntu NetworkManager[726]: <info> Auto-activating connection '8LGL3'.
Jan  7 21:29:53 ubuntu NetworkManager[726]: <info> Activation (wlan0) starting connection '8LGL3'
Jan  7 21:29:53 ubuntu NetworkManager[726]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jan  7 21:29:53 ubuntu NetworkManager[726]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jan  7 21:29:53 ubuntu NetworkManager[726]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jan  7 21:29:53 ubuntu NetworkManager[726]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jan  7 21:29:53 ubuntu NetworkManager[726]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jan  7 21:29:53 ubuntu NetworkManager[726]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jan  7 21:29:53 ubuntu NetworkManager[726]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jan  7 21:29:53 ubuntu NetworkManager[726]: <info> Activation (wlan0/wireless): connection '8LGL3' has security, and secrets exist.  No new secrets needed.
Jan  7 21:29:53 ubuntu NetworkManager[726]: <info> Config: added 'ssid' value '8LGL3'
Jan  7 21:29:53 ubuntu NetworkManager[726]: <info> Config: added 'scan_ssid' value '1'
Jan  7 21:29:53 ubuntu NetworkManager[726]: <info> Config: added 'key_mgmt' value 'NONE'
Jan  7 21:29:53 ubuntu NetworkManager[726]: <info> Config: added 'wep_key0' value '<omitted>'
Jan  7 21:29:53 ubuntu NetworkManager[726]: <info> Config: added 'wep_tx_keyidx' value '0'
Jan  7 21:29:53 ubuntu NetworkManager[726]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jan  7 21:29:53 ubuntu NetworkManager[726]: <info> Config: set interface ap_scan to 1
Jan  7 21:29:53 ubuntu NetworkManager[726]: <info> (wlan0): supplicant interface state: inactive -> scanning
Jan  7 21:29:54 ubuntu dbus[521]: [system] Activating service name='org.freedesktop.UPower' (using servicehelper)
Jan  7 21:29:54 ubuntu dbus[521]: [system] Successfully activated service 'org.freedesktop.UPower'
Jan  7 21:29:55 ubuntu wpa_supplicant[1134]: Trying to authenticate with 00:26:62:5c:2a:41 (SSID='8LGL3' freq=2412 MHz)
Jan  7 21:29:55 ubuntu kernel: [   63.188935] wlan0: authenticate with 00:26:62:5c:2a:41
Jan  7 21:29:55 ubuntu NetworkManager[726]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jan  7 21:29:55 ubuntu wpa_supplicant[1134]: Trying to associate with 00:26:62:5c:2a:41 (SSID='8LGL3' freq=2412 MHz)
Jan  7 21:29:55 ubuntu kernel: [   63.208375] wlan0: send auth to 00:26:62:5c:2a:41 (try 1/3)
Jan  7 21:29:55 ubuntu kernel: [   63.210854] wlan0: authenticated
Jan  7 21:29:55 ubuntu kernel: [   63.212273] wlan0: associate with 00:26:62:5c:2a:41 (try 1/3)
Jan  7 21:29:55 ubuntu kernel: [   63.214888] wlan0: RX AssocResp from 00:26:62:5c:2a:41 (capab=0x431 status=0 aid=2)
Jan  7 21:29:55 ubuntu kernel: [   63.215383] wlan0: associated
Jan  7 21:29:55 ubuntu kernel: [   63.215599] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jan  7 21:29:55 ubuntu kernel: [   63.215681] cfg80211: Calling CRDA for country: US
Jan  7 21:29:55 ubuntu wpa_supplicant[1134]: Associated with 00:26:62:5c:2a:41
Jan  7 21:29:55 ubuntu wpa_supplicant[1134]: CTRL-EVENT-CONNECTED - Connection to 00:26:62:5c:2a:41 completed (auth) [id=0 id_str=]
Jan  7 21:29:55 ubuntu NetworkManager[726]: <info> (wlan0): supplicant interface state: authenticating -> completed
Jan  7 21:29:55 ubuntu NetworkManager[726]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network '8LGL3'.
Jan  7 21:29:55 ubuntu NetworkManager[726]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Jan  7 21:29:55 ubuntu NetworkManager[726]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Jan  7 21:29:55 ubuntu NetworkManager[726]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Jan  7 21:29:55 ubuntu NetworkManager[726]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jan  7 21:29:55 ubuntu NetworkManager[726]: <info> dhclient started with pid 1425
Jan  7 21:29:55 ubuntu NetworkManager[726]: <info> Activation (wlan0) Beginning IP6 addrconf.
Jan  7 21:29:55 ubuntu NetworkManager[726]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jan  7 21:29:55 ubuntu kernel: [   63.222245] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
Jan  7 21:29:55 ubuntu kernel: [   63.222252] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jan  7 21:29:55 ubuntu kernel: [   63.222256] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
Jan  7 21:29:55 ubuntu kernel: [   63.222259] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jan  7 21:29:55 ubuntu kernel: [   63.222262] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
Jan  7 21:29:55 ubuntu kernel: [   63.222265] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jan  7 21:29:55 ubuntu kernel: [   63.222268] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
Jan  7 21:29:55 ubuntu kernel: [   63.222271] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jan  7 21:29:55 ubuntu kernel: [   63.222274] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
Jan  7 21:29:55 ubuntu kernel: [   63.222277] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jan  7 21:29:55 ubuntu kernel: [   63.222280] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
Jan  7 21:29:55 ubuntu kernel: [   63.222283] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jan  7 21:29:55 ubuntu kernel: [   63.222286] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
Jan  7 21:29:55 ubuntu kernel: [   63.222289] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jan  7 21:29:55 ubuntu kernel: [   63.222292] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
Jan  7 21:29:55 ubuntu kernel: [   63.222295] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jan  7 21:29:55 ubuntu kernel: [   63.222298] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
Jan  7 21:29:55 ubuntu kernel: [   63.222301] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jan  7 21:29:55 ubuntu kernel: [   63.222304] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
Jan  7 21:29:55 ubuntu kernel: [   63.222307] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jan  7 21:29:55 ubuntu kernel: [   63.222310] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
Jan  7 21:29:55 ubuntu kernel: [   63.222314] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jan  7 21:29:55 ubuntu kernel: [   63.222316] cfg80211: Disabling freq 2467 MHz
Jan  7 21:29:55 ubuntu kernel: [   63.222318] cfg80211: Disabling freq 2472 MHz
Jan  7 21:29:55 ubuntu kernel: [   63.222321] cfg80211: Disabling freq 2484 MHz
Jan  7 21:29:55 ubuntu kernel: [   63.222325] cfg80211: Regulatory domain changed to country: US
Jan  7 21:29:55 ubuntu kernel: [   63.222327] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jan  7 21:29:55 ubuntu kernel: [   63.222330] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jan  7 21:29:55 ubuntu kernel: [   63.222334] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
Jan  7 21:29:55 ubuntu kernel: [   63.222337] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  7 21:29:55 ubuntu kernel: [   63.222340] cfg80211:   (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  7 21:29:55 ubuntu kernel: [   63.222343] cfg80211:   (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  7 21:29:55 ubuntu kernel: [   63.222346] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
Jan  7 21:29:55 ubuntu dhclient: Internet Systems Consortium DHCP Client 4.1-ESV-R4
Jan  7 21:29:55 ubuntu dhclient: Copyright 2004-2011 Internet Systems Consortium.
Jan  7 21:29:55 ubuntu dhclient: All rights reserved.
Jan  7 21:29:55 ubuntu dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Jan  7 21:29:55 ubuntu dhclient: 
Jan  7 21:29:55 ubuntu NetworkManager[726]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Jan  7 21:29:55 ubuntu dhclient: Listening on LPF/wlan0/00:19:7e:66:cd:ee
Jan  7 21:29:55 ubuntu dhclient: Sending on   LPF/wlan0/00:19:7e:66:cd:ee
Jan  7 21:29:55 ubuntu dhclient: Sending on   Socket/fallback
Jan  7 21:29:55 ubuntu dhclient: DHCPREQUEST of 192.168.1.2 on wlan0 to 255.255.255.255 port 67
Jan  7 21:29:55 ubuntu dhclient: DHCPACK of 192.168.1.2 from 192.168.1.1
Jan  7 21:29:55 ubuntu NetworkManager[726]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Jan  7 21:29:55 ubuntu NetworkManager[726]: <info>   address 192.168.1.2
Jan  7 21:29:55 ubuntu NetworkManager[726]: <info>   prefix 24 (255.255.255.0)
Jan  7 21:29:55 ubuntu NetworkManager[726]: <info>   gateway 192.168.1.1
Jan  7 21:29:55 ubuntu NetworkManager[726]: <info>   hostname 'ubuntu'
Jan  7 21:29:55 ubuntu NetworkManager[726]: <info>   nameserver '192.168.1.1'
Jan  7 21:29:55 ubuntu NetworkManager[726]: <info>   domain name 'home'
Jan  7 21:29:55 ubuntu NetworkManager[726]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Jan  7 21:29:55 ubuntu NetworkManager[726]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Jan  7 21:29:55 ubuntu dhclient: bound to 192.168.1.2 -- renewal in 42681 seconds.
Jan  7 21:29:56 ubuntu NetworkManager[726]: <info> DNS: starting dnsmasq...
Jan  7 21:29:56 ubuntu NetworkManager[726]: <error> [1389148196.154483] [nm-dns-dnsmasq.c:393] update(): dnsmasq not available on the bus, can't update servers.
Jan  7 21:29:56 ubuntu NetworkManager[726]: <error> [1389148196.154564] [nm-dns-dnsmasq.c:395] update(): dnsmasq owner not found on bus: Could not get owner of name 'uk.org.thekelleys.dnsmasq': no such name
Jan  7 21:29:56 ubuntu NetworkManager[726]: <warn> DNS: plugin dnsmasq update failed
Jan  7 21:29:56 ubuntu NetworkManager[726]: <info> (wlan0): writing resolv.conf to /sbin/resolvconf
Jan  7 21:29:56 ubuntu dnsmasq[1429]: started, version 2.59 cache disabled
Jan  7 21:29:56 ubuntu dnsmasq[1429]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
Jan  7 21:29:56 ubuntu dnsmasq[1429]: DBus support enabled: connected to system bus
Jan  7 21:29:56 ubuntu dnsmasq[1429]: warning: no upstream servers configured
Jan  7 21:29:56 ubuntu NetworkManager[726]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Jan  7 21:29:56 ubuntu NetworkManager[726]: <info> Policy set '8LGL3' (wlan0) as default for IPv4 routing and DNS.
Jan  7 21:29:56 ubuntu NetworkManager[726]: <info> Activation (wlan0) successful, device activated.
Jan  7 21:29:56 ubuntu NetworkManager[726]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Jan  7 21:29:56 ubuntu NetworkManager[726]: <warn> dnsmasq appeared on DBus: :1.22
Jan  7 21:29:56 ubuntu dbus[521]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Jan  7 21:29:56 ubuntu dnsmasq[1429]: setting upstream servers from DBus
Jan  7 21:29:56 ubuntu dnsmasq[1429]: using nameserver 192.168.1.1#53
Jan  7 21:29:56 ubuntu NetworkManager[726]: <info> (wlan0): writing resolv.conf to /sbin/resolvconf
Jan  7 21:29:56 ubuntu dbus[521]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jan  7 21:29:57 ubuntu acpid: client 889[0:0] has disconnected
Jan  7 21:29:57 ubuntu acpid: client connected from 1538[0:0]
Jan  7 21:29:57 ubuntu acpid: 1 client rule loaded
Jan  7 21:30:06 ubuntu ntpdate[1614]: step time server 91.189.89.199 offset -1.299796 sec
Jan  7 21:30:13 ubuntu NetworkManager[726]: <info> (wlan0): IP6 addrconf timed out or failed.
Jan  7 21:30:13 ubuntu NetworkManager[726]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Jan  7 21:30:13 ubuntu NetworkManager[726]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Jan  7 21:30:13 ubuntu NetworkManager[726]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Jan  7 21:33:54 ubuntu kernel: imklog 5.8.6, log source = /proc/kmsg started.
Jan  7 21:33:54 ubuntu rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="554" x-info="http://www.rsyslog.com"] start
Jan  7 21:33:54 ubuntu rsyslogd: rsyslogd's groupid changed to 103
Jan  7 21:33:55 ubuntu rsyslogd: rsyslogd's userid changed to 101
Jan  7 21:33:54 ubuntu rsyslogd-2039: Could not open output pipe '/dev/xconsole' [try [http://www.rsyslog.com/e/2039](http://www.rsyslog.com/e/2039) ]
Jan  7 21:33:55 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpuset
Jan  7 21:33:55 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpu
Jan  7 21:33:55 ubuntu kernel: [    0.000000] Linux version 3.5.0-45-generic (buildd@allspice) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #68~precise1-Ubuntu SMP Wed Dec 4 16:19:28 UTC 2013 (Ubuntu 3.5.0-45.68~precise1-generic 3.5.7.26)
Jan  7 21:33:55 ubuntu kernel: [    0.000000] KERNEL supported cpus:
Jan  7 21:33:55 ubuntu kernel: [    0.000000]   Intel GenuineIntel
Jan  7 21:33:55 ubuntu kernel: [    0.000000]   AMD AuthenticAMD
Jan  7 21:33:55 ubuntu kernel: [    0.000000]   NSC Geode by NSC
Jan  7 21:33:55 ubuntu kernel: [    0.000000]   Cyrix CyrixInstead
Jan  7 21:33:55 ubuntu kernel: [    0.000000]   Centaur CentaurHauls
Jan  7 21:33:55 ubuntu kernel: [    0.000000]   Transmeta GenuineTMx86
Jan  7 21:33:55 ubuntu kernel: [    0.000000]   Transmeta TransmetaCPU
Jan  7 21:33:55 ubuntu kernel: [    0.000000]   UMC UMC UMC UMC
Jan  7 21:33:55 ubuntu kernel: [    0.000000] Disabled fast string operations
Jan  7 21:33:55 ubuntu kernel: [    0.000000] e820: BIOS-provided physical RAM map:
Jan  7 21:33:55 ubuntu kernel: [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009efff] usable
Jan  7 21:33:55 ubuntu kernel: [    0.000000] BIOS-e820: [mem 0x000000000009f000-0x000000000009ffff] reserved
Jan  7 21:33:55 ubuntu kernel: [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000bfed33ff] usable
Jan  7 21:33:55 ubuntu kernel: [    0.000000] BIOS-e820: [mem 0x00000000bfed3400-0x00000000bfffffff] reserved
Jan  7 21:33:55 ubuntu kernel: [    0.000000] BIOS-e820: [mem 0x00000000f0000000-0x00000000f4006fff] reserved
Jan  7 21:33:55 ubuntu kernel: [    0.000000] BIOS-e820: [mem 0x00000000f4008000-0x00000000f400bfff] reserved
Jan  7 21:33:55 ubuntu kernel: [    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec0ffff] reserved
Jan  7 21:33:55 ubuntu kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed20000-0x00000000fed9ffff] reserved
Jan  7 21:33:55 ubuntu kernel: [    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee0ffff] reserved
Jan  7 21:33:55 ubuntu kernel: [    0.000000] BIOS-e820: [mem 0x00000000ffb00000-0x00000000ffffffff] reserved
Jan  7 21:33:55 ubuntu kernel: [    0.000000] NX (Execute Disable) protection: active
Jan  7 21:33:55 ubuntu kernel: [    0.000000] SMBIOS 2.4 present.
Jan  7 21:33:55 ubuntu kernel: [    0.000000] DMI: Dell Inc. MM061                           /0XD720, BIOS A17 06/13/2007
Jan  7 21:33:55 ubuntu kernel: [    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
Jan  7 21:33:55 ubuntu kernel: [    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
Jan  7 21:33:55 ubuntu kernel: [    0.000000] e820: last_pfn = 0xbfed3 max_arch_pfn = 0x1000000
Jan  7 21:33:55 ubuntu kernel: [    0.000000] MTRR default type: uncachable
Jan  7 21:33:55 ubuntu kernel: [    0.000000] MTRR fixed ranges enabled:
Jan  7 21:33:55 ubuntu kernel: [    0.000000]   00000-9FFFF write-back
Jan  7 21:33:55 ubuntu kernel: [    0.000000]   A0000-BFFFF uncachable
Jan  7 21:33:55 ubuntu kernel: [    0.000000]   C0000-CFFFF write-protect
Jan  7 21:33:55 ubuntu kernel: [    0.000000]   D0000-EFFFF uncachable
Jan  7 21:33:55 ubuntu kernel: [    0.000000]   F0000-FFFFF write-protect
Jan  7 21:33:55 ubuntu kernel: [    0.000000] MTRR variable ranges enabled:
Jan  7 21:33:55 ubuntu kernel: [    0.000000]   0 base 000000000 mask F80000000 write-back
Jan  7 21:33:55 ubuntu kernel: [    0.000000]   1 base 080000000 mask FC0000000 write-back
Jan  7 21:33:55 ubuntu kernel: [    0.000000]   2 base 0BFF00000 mask FFFF00000 uncachable
Jan  7 21:33:55 ubuntu kernel: [    0.000000]   3 disabled
Jan  7 21:33:55 ubuntu kernel: [    0.000000]   4 disabled
Jan  7 21:33:55 ubuntu kernel: [    0.000000]   5 disabled
Jan  7 21:33:55 ubuntu kernel: [    0.000000]   6 disabled
Jan  7 21:33:55 ubuntu kernel: [    0.000000]   7 disabled
Jan  7 21:33:55 ubuntu kernel: [    0.000000] PAT not supported by CPU.
Jan  7 21:33:55 ubuntu kernel: [    0.000000] original variable MTRRs
Jan  7 21:33:55 ubuntu kernel: [    0.000000] reg 0, base: 0GB, range: 2GB, type WB
Jan  7 21:33:55 ubuntu kernel: [    0.000000] reg 1, base: 2GB, range: 1GB, type WB
Jan  7 21:33:55 ubuntu kernel: [    0.000000] reg 2, base: 3071MB, range: 1MB, type UC
Jan  7 21:33:55 ubuntu kernel: [    0.000000] total RAM covered: 3071M
Jan  7 21:33:55 ubuntu kernel: [    0.000000] Found optimal setting for mtrr clean up
Jan  7 21:33:55 ubuntu kernel: [    0.000000]  gran_size: 64K 	chunk_size: 2M 	num_reg: 3  	lose cover RAM: 0G
Jan  7 21:33:55 ubuntu kernel: [    0.000000] New variable MTRRs
Jan  7 21:33:55 ubuntu kernel: [    0.000000] reg 0, base: 0GB, range: 2GB, type WB
Jan  7 21:33:55 ubuntu kernel: [    0.000000] reg 1, base: 2GB, range: 1GB, type WB
Jan  7 21:33:55 ubuntu kernel: [    0.000000] reg 2, base: 3071MB, range: 1MB, type UC
Jan  7 21:33:55 ubuntu kernel: [    0.000000] initial memory mapped: [mem 0x00000000-0x01ffffff]
Jan  7 21:33:55 ubuntu kernel: [    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
Jan  7 21:33:55 ubuntu kernel: [    0.000000] init_memory_mapping: [mem 0x00000000-0x37bfdfff]
Jan  7 21:33:55 ubuntu kernel: [    0.000000]  [mem 0x00000000-0x001fffff] page 4k
Jan  7 21:33:55 ubuntu kernel: [    0.000000]  [mem 0x00200000-0x379fffff] page 2M
Jan  7 21:33:55 ubuntu kernel: [    0.000000]  [mem 0x37a00000-0x37bfdfff] page 4k
Jan  7 21:33:55 ubuntu kernel: [    0.000000] kernel direct mapping tables up to 0x37bfdfff @ [mem 0x01ffa000-0x01ffffff]
Jan  7 21:33:55 ubuntu kernel: [    0.000000] RAMDISK: [mem 0x36248000-0x3711bfff]
Jan  7 21:33:55 ubuntu kernel: [    0.000000] ACPI: RSDP 000fc1d0 00014 (v00 DELL  )
Jan  7 21:33:55 ubuntu kernel: [    0.000000] ACPI: RSDT bfed39cd 00040 (v01 DELL    M07     27D7060D ASL  00000061)
Jan  7 21:33:55 ubuntu kernel: [    0.000000] ACPI: FACP bfed4800 00074 (v01 DELL    M07     27D7060D ASL  00000061)
Jan  7 21:33:55 ubuntu kernel: [    0.000000] ACPI: DSDT bfed5400 04766 (v01 INT430 SYSFexxx 00001001 INTL 20050624)
Jan  7 21:33:55 ubuntu kernel: [    0.000000] ACPI: FACS bfee3c00 00040
Jan  7 21:33:55 ubuntu kernel: [    0.000000] ACPI: HPET bfed4f00 00038 (v01 DELL    M07     00000001 ASL  00000061)
Jan  7 21:33:55 ubuntu kernel: [    0.000000] ACPI: APIC bfed5000 00068 (v01 DELL    M07     27D7060D ASL  00000047)
Jan  7 21:33:55 ubuntu kernel: [    0.000000] ACPI: MCFG bfed4fc0 0003E (v16 DELL    M07     27D7060D ASL  00000061)
Jan  7 21:33:55 ubuntu kernel: [    0.000000] ACPI: SLIC bfed509c 00176 (v01 DELL    M07     27D7060D ASL  00000061)
Jan  7 21:33:55 ubuntu kernel: [    0.000000] ACPI: BOOT bfed4bc0 00028 (v01 DELL    M07     27D7060D ASL  00000061)
Jan  7 21:33:55 ubuntu kernel: [    0.000000] ACPI: SSDT bfed3a0d 004DC (v01  PmRef    CpuPm 00003000 INTL 20050624)
Jan  7 21:33:55 ubuntu kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jan  7 21:33:55 ubuntu kernel: [    0.000000] 2178MB HIGHMEM available.
Jan  7 21:33:55 ubuntu kernel: [    0.000000] 891MB LOWMEM available.
Jan  7 21:33:55 ubuntu kernel: [    0.000000]   mapped low ram: 0 - 37bfe000
Jan  7 21:33:55 ubuntu kernel: [    0.000000]   low ram: 0 - 37bfe000
Jan  7 21:33:55 ubuntu kernel: [    0.000000] Zone ranges:
Jan  7 21:33:55 ubuntu kernel: [    0.000000]   DMA      [mem 0x00010000-0x00ffffff]
Jan  7 21:33:55 ubuntu kernel: [    0.000000]   Normal   [mem 0x01000000-0x37bfdfff]
Jan  7 21:33:55 ubuntu kernel: [    0.000000]   HighMem  [mem 0x37bfe000-0xbfed2fff]
Jan  7 21:33:55 ubuntu kernel: [    0.000000] Movable zone start for each node
Jan  7 21:33:55 ubuntu kernel: [    0.000000] Early memory node ranges
Jan  7 21:33:55 ubuntu kernel: [    0.000000]   node   0: [mem 0x00010000-0x0009efff]
Jan  7 21:33:55 ubuntu kernel: [    0.000000]   node   0: [mem 0x00100000-0xbfed2fff]
Jan  7 21:33:55 ubuntu kernel: [    0.000000] On node 0 totalpages: 786018
Jan  7 21:33:55 ubuntu kernel: [    0.000000] free_area_init_node: node 0, pgdat c18c85c0, node_mem_map f4a48200
Jan  7 21:33:55 ubuntu kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Jan  7 21:33:55 ubuntu kernel: [    0.000000]   DMA zone: 0 pages reserved
Jan  7 21:33:55 ubuntu kernel: [    0.000000]   DMA zone: 3951 pages, LIFO batch:0
Jan  7 21:33:55 ubuntu kernel: [    0.000000]   Normal zone: 1752 pages used for memmap
Jan  7 21:33:55 ubuntu kernel: [    0.000000]   Normal zone: 222502 pages, LIFO batch:31
Jan  7 21:33:55 ubuntu kernel: [    0.000000]   HighMem zone: 4358 pages used for memmap
Jan  7 21:33:55 ubuntu kernel: [    0.000000]   HighMem zone: 553423 pages, LIFO batch:31
Jan  7 21:33:55 ubuntu kernel: [    0.000000] Using APIC driver default
Jan  7 21:33:55 ubuntu kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Jan  7 21:33:55 ubuntu kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jan  7 21:33:55 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jan  7 21:33:55 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Jan  7 21:33:55 ubuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Jan  7 21:33:55 ubuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Jan  7 21:33:55 ubuntu kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Jan  7 21:33:55 ubuntu kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Jan  7 21:33:55 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jan  7 21:33:55 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jan  7 21:33:55 ubuntu kernel: [    0.000000] ACPI: IRQ0 used by override.
Jan  7 21:33:55 ubuntu kernel: [    0.000000] ACPI: IRQ2 used by override.
Jan  7 21:33:55 ubuntu kernel: [    0.000000] ACPI: IRQ9 used by override.
Jan  7 21:33:55 ubuntu kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jan  7 21:33:55 ubuntu kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Jan  7 21:33:55 ubuntu kernel: [    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
Jan  7 21:33:55 ubuntu kernel: [    0.000000] nr_irqs_gsi: 40
Jan  7 21:33:55 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jan  7 21:33:55 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 0000000000100000
Jan  7 21:33:55 ubuntu kernel: [    0.000000] e820: [mem 0xc0000000-0xefffffff] available for PCI devices
Jan  7 21:33:55 ubuntu kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Jan  7 21:33:55 ubuntu kernel: [    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
Jan  7 21:33:55 ubuntu kernel: [    0.000000] PERCPU: Embedded 14 pages/cpu @f7bcf000 s34176 r0 d23168 u57344
Jan  7 21:33:55 ubuntu kernel: [    0.000000] pcpu-alloc: s34176 r0 d23168 u57344 alloc=14*4096
Jan  7 21:33:55 ubuntu kernel: [    0.000000] pcpu-alloc: [0] 0 [0] 1 
Jan  7 21:33:55 ubuntu kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 779876
Jan  7 21:33:55 ubuntu kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-45-generic root=UUID=00D2D857D2D85290 loop=/ubuntu/disks/root.disk ro quiet splash vt.handoff=7
Jan  7 21:33:55 ubuntu kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Jan  7 21:33:55 ubuntu kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Jan  7 21:33:55 ubuntu kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Jan  7 21:33:55 ubuntu kernel: [    0.000000] __ex_table already sorted, skipping sort
Jan  7 21:33:55 ubuntu kernel: [    0.000000] Initializing CPU#0
Jan  7 21:33:55 ubuntu kernel: [    0.000000] allocated 6288920 bytes of page_cgroup
Jan  7 21:33:55 ubuntu kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Jan  7 21:33:55 ubuntu kernel: [    0.000000] Initializing HighMem for node 0 (00037bfe:000bfed3)
Jan  7 21:33:55 ubuntu kernel: [    0.000000] Memory: 3086404k/3144524k available (6061k kernel code, 57668k reserved, 2983k data, 764k init, 2231124k highmem)
Jan  7 21:33:55 ubuntu kernel: [    0.000000] virtual kernel memory layout:
Jan  7 21:33:55 ubuntu kernel: [    0.000000]     fixmap  : 0xfff15000 - 0xfffff000   ( 936 kB)
Jan  7 21:33:55 ubuntu kernel: [    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
Jan  7 21:33:55 ubuntu kernel: [    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
Jan  7 21:33:55 ubuntu kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
Jan  7 21:33:55 ubuntu kernel: [    0.000000]       .init : 0xc18d6000 - 0xc1995000   ( 764 kB)
Jan  7 21:33:55 ubuntu kernel: [    0.000000]       .data : 0xc15eb595 - 0xc18d54c0   (2983 kB)
Jan  7 21:33:55 ubuntu kernel: [    0.000000]       .text : 0xc1000000 - 0xc15eb595   (6061 kB)
Jan  7 21:33:55 ubuntu kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Jan  7 21:33:55 ubuntu kernel: [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Jan  7 21:33:55 ubuntu kernel: [    0.000000] Hierarchical RCU implementation.
Jan  7 21:33:55 ubuntu kernel: [    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
Jan  7 21:33:55 ubuntu kernel: [    0.000000] NR_IRQS:2304 nr_irqs:512 16
Jan  7 21:33:55 ubuntu kernel: [    0.000000] CPU 0 irqstacks, hard=f4408000 soft=f440a000
Jan  7 21:33:55 ubuntu kernel: [    0.000000] vt handoff: transparent VT on vt#7
Jan  7 21:33:55 ubuntu kernel: [    0.000000] Console: colour dummy device 80x25
Jan  7 21:33:55 ubuntu kernel: [    0.000000] console [tty0] enabled
Jan  7 21:33:55 ubuntu kernel: [    0.000000] hpet clockevent registered
Jan  7 21:33:55 ubuntu kernel: [    0.000000] Fast TSC calibration using PIT
Jan  7 21:33:55 ubuntu kernel: [    0.000000] Detected 1729.040 MHz processor.
Jan  7 21:33:55 ubuntu kernel: [    0.004003] Calibrating delay loop (skipped), value calculated using timer frequency.. 3458.08 BogoMIPS (lpj=6916160)
Jan  7 21:33:55 ubuntu kernel: [    0.004008] pid_max: default: 32768 minimum: 301
Jan  7 21:33:55 ubuntu kernel: [    0.004041] Security Framework initialized
Jan  7 21:33:55 ubuntu kernel: [    0.004063] AppArmor: AppArmor initialized
Jan  7 21:33:55 ubuntu kernel: [    0.004065] Yama: becoming mindful.
Jan  7 21:33:55 ubuntu kernel: [    0.004166] Mount-cache hash table entries: 512
Jan  7 21:33:55 ubuntu kernel: [    0.004527] Initializing cgroup subsys cpuacct
Jan  7 21:33:55 ubuntu kernel: [    0.004532] Initializing cgroup subsys memory
Jan  7 21:33:55 ubuntu kernel: [    0.004545] Initializing cgroup subsys devices
Jan  7 21:33:55 ubuntu kernel: [    0.004549] Initializing cgroup subsys freezer
Jan  7 21:33:55 ubuntu kernel: [    0.004552] Initializing cgroup subsys blkio
Jan  7 21:33:55 ubuntu kernel: [    0.004555] Initializing cgroup subsys perf_event
Jan  7 21:33:55 ubuntu kernel: [    0.004595] Disabled fast string operations
Jan  7 21:33:55 ubuntu kernel: [    0.004601] CPU: Physical Processor ID: 0
Jan  7 21:33:55 ubuntu kernel: [    0.004604] CPU: Processor Core ID: 0
Jan  7 21:33:55 ubuntu kernel: [    0.004608] mce: CPU supports 6 MCE banks
Jan  7 21:33:55 ubuntu kernel: [    0.004620] CPU0: Thermal monitoring enabled (TM2)
Jan  7 21:33:55 ubuntu kernel: [    0.004624] using mwait in idle threads.
Jan  7 21:33:55 ubuntu kernel: [    0.008904] ACPI: Core revision 20120320
Jan  7 21:33:55 ubuntu kernel: [    0.013869] ftrace: allocating 27163 entries in 54 pages
Jan  7 21:33:55 ubuntu kernel: [    0.032032] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Jan  7 21:33:55 ubuntu kernel: [    0.032516] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Jan  7 21:33:55 ubuntu kernel: [    0.072216] CPU0: Genuine Intel(R) CPU           T2080  @ 1.73GHz stepping 0c
Jan  7 21:33:55 ubuntu kernel: [    0.076004] Performance Events: Core events, core PMU driver.
Jan  7 21:33:55 ubuntu kernel: [    0.076004] ... version:                1
Jan  7 21:33:55 ubuntu kernel: [    0.076004] ... bit width:              40
Jan  7 21:33:55 ubuntu kernel: [    0.076004] ... generic registers:      2
Jan  7 21:33:55 ubuntu kernel: [    0.076004] ... value mask:             000000ffffffffff
Jan  7 21:33:55 ubuntu kernel: [    0.076004] ... max period:             000000007fffffff
Jan  7 21:33:55 ubuntu kernel: [    0.076004] ... fixed-purpose events:   0
Jan  7 21:33:55 ubuntu kernel: [    0.076004] ... event mask:             0000000000000003
Jan  7 21:33:55 ubuntu kernel: [    0.076004] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
Jan  7 21:33:55 ubuntu kernel: [    0.076004] CPU 1 irqstacks, hard=f44c8000 soft=f44ca000
Jan  7 21:33:55 ubuntu kernel: [    0.076004] Booting Node   0, Processors  #1 Ok.
Jan  7 21:33:55 ubuntu kernel: [    0.008000] Initializing CPU#1
Jan  7 21:33:55 ubuntu kernel: [    0.008000] Disabled fast string operations
Jan  7 21:33:55 ubuntu kernel: [    0.084004] TSC synchronization [CPU#0 -> CPU#1]:
Jan  7 21:33:55 ubuntu kernel: [    0.084004] Measured 3493309287 cycles TSC warp between CPUs, turning off TSC clock.
Jan  7 21:33:55 ubuntu kernel: [    0.084004] Marking TSC unstable due to check_tsc_sync_source failed
Jan  7 21:33:55 ubuntu kernel: [    0.084108] Brought up 2 CPUs
Jan  7 21:33:55 ubuntu kernel: [    0.084112] Total of 2 processors activated (6916.16 BogoMIPS).
Jan  7 21:33:55 ubuntu kernel: [    0.085228] devtmpfs: initialized
Jan  7 21:33:55 ubuntu kernel: [    0.085228] EVM: security.selinux
Jan  7 21:33:55 ubuntu kernel: [    0.085228] EVM: security.SMACK64
Jan  7 21:33:55 ubuntu kernel: [    0.085228] EVM: security.capability
Jan  7 21:33:55 ubuntu kernel: [    0.088868] dummy: 
Jan  7 21:33:55 ubuntu kernel: [    0.088916] RTC time: 21:33:06, date: 01/07/14
Jan  7 21:33:55 ubuntu kernel: [    0.088979] NET: Registered protocol family 16
Jan  7 21:33:55 ubuntu kernel: [    0.088996] Trying to unpack rootfs image as initramfs...
Jan  7 21:33:55 ubuntu kernel: [    0.089227] EISA bus registered
Jan  7 21:33:55 ubuntu kernel: [    0.089359] ACPI: bus type pci registered
Jan  7 21:33:55 ubuntu kernel: [    0.089458] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf0000000-0xf3ffffff] (base 0xf0000000)
Jan  7 21:33:55 ubuntu kernel: [    0.089463] PCI: MMCONFIG at [mem 0xf0000000-0xf3ffffff] reserved in E820
Jan  7 21:33:55 ubuntu kernel: [    0.089465] PCI: Using MMCONFIG for extended config space
Jan  7 21:33:55 ubuntu kernel: [    0.089468] PCI: Using configuration type 1 for base access
Jan  7 21:33:55 ubuntu kernel: [    0.089482] dmi type 0xB1 record - unknown flag
Jan  7 21:33:55 ubuntu kernel: [    0.104182] bio: create slab <bio-0> at 0
Jan  7 21:33:55 ubuntu kernel: [    0.104324] ACPI: Added _OSI(Module Device)
Jan  7 21:33:55 ubuntu kernel: [    0.104328] ACPI: Added _OSI(Processor Device)
Jan  7 21:33:55 ubuntu kernel: [    0.104331] ACPI: Added _OSI(3.0 _SCP Extensions)
Jan  7 21:33:55 ubuntu kernel: [    0.104334] ACPI: Added _OSI(Processor Aggregator Device)
Jan  7 21:33:55 ubuntu kernel: [    0.106005] ACPI: EC: Look up EC in DSDT
Jan  7 21:33:55 ubuntu kernel: [    0.113934] ACPI: SSDT bfed4134 00244 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
Jan  7 21:33:55 ubuntu kernel: [    0.114359] ACPI: Dynamic OEM Table Load:
Jan  7 21:33:55 ubuntu kernel: [    0.114364] ACPI: SSDT   (null) 00244 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
Jan  7 21:33:55 ubuntu kernel: [    0.114509] ACPI: SSDT bfed3ee9 001C6 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
Jan  7 21:33:55 ubuntu kernel: [    0.114904] ACPI: Dynamic OEM Table Load:
Jan  7 21:33:55 ubuntu kernel: [    0.114908] ACPI: SSDT   (null) 001C6 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
Jan  7 21:33:55 ubuntu kernel: [    0.115222] ACPI: SSDT bfed4378 000C4 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
Jan  7 21:33:55 ubuntu kernel: [    0.115630] ACPI: Dynamic OEM Table Load:
Jan  7 21:33:55 ubuntu kernel: [    0.116013] ACPI: SSDT   (null) 000C4 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
Jan  7 21:33:55 ubuntu kernel: [    0.116141] ACPI: SSDT bfed40af 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
Jan  7 21:33:55 ubuntu kernel: [    0.116539] ACPI: Dynamic OEM Table Load:
Jan  7 21:33:55 ubuntu kernel: [    0.116543] ACPI: SSDT   (null) 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
Jan  7 21:33:55 ubuntu kernel: [    0.116807] ACPI: Interpreter enabled
Jan  7 21:33:55 ubuntu kernel: [    0.116820] ACPI: (supports S0 S3 S4 S5)
Jan  7 21:33:55 ubuntu kernel: [    0.116847] ACPI: Using IOAPIC for interrupt routing
Jan  7 21:33:55 ubuntu kernel: [    0.142393] ACPI: No dock devices found.
Jan  7 21:33:55 ubuntu kernel: [    0.142410] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
Jan  7 21:33:55 ubuntu kernel: [    0.149610] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Jan  7 21:33:55 ubuntu kernel: [    0.163773] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
Jan  7 21:33:55 ubuntu kernel: [    0.163780] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
Jan  7 21:33:55 ubuntu kernel: [    0.163784] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
Jan  7 21:33:55 ubuntu kernel: [    0.163788] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff] (ignored)
Jan  7 21:33:55 ubuntu kernel: [    0.163792] pci_root PNP0A03:00: host bridge window [mem 0xc0000000-0xefffffff] (ignored)
Jan  7 21:33:55 ubuntu kernel: [    0.163796] pci_root PNP0A03:00: host bridge window [mem 0xf4007000-0xf4007fff] (ignored)
Jan  7 21:33:55 ubuntu kernel: [    0.163800] pci_root PNP0A03:00: host bridge window [mem 0xf400c000-0xfebfffff] (ignored)
Jan  7 21:33:55 ubuntu kernel: [    0.163804] pci_root PNP0A03:00: host bridge window [mem 0xfec10000-0xfecfffff] (ignored)
Jan  7 21:33:55 ubuntu kernel: [    0.163808] pci_root PNP0A03:00: host bridge window [mem 0xfed00400-0xfed1ffff] (ignored)
Jan  7 21:33:55 ubuntu kernel: [    0.163812] pci_root PNP0A03:00: host bridge window [mem 0xfee10000-0xffafffff] (ignored)
Jan  7 21:33:55 ubuntu kernel: [    0.163816] PCI: root bus 00: using default resources
Jan  7 21:33:55 ubuntu kernel: [    0.163895] PCI host bridge to bus 0000:00
Jan  7 21:33:55 ubuntu kernel: [    0.163900] pci_bus 0000:00: root bus resource [io  0x0000-0xffff]
Jan  7 21:33:55 ubuntu kernel: [    0.163904] pci_bus 0000:00: root bus resource [mem 0x00000000-0xffffffff]
Jan  7 21:33:55 ubuntu kernel: [    0.163923] pci 0000:00:00.0: [8086:27a0] type 00 class 0x060000
Jan  7 21:33:55 ubuntu kernel: [    0.163996] pci 0000:00:01.0: [8086:27a1] type 01 class 0x060400
Jan  7 21:33:55 ubuntu kernel: [    0.164076] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
Jan  7 21:33:55 ubuntu kernel: [    0.164159] pci 0000:00:1b.0: [8086:27d8] type 00 class 0x040300
Jan  7 21:33:55 ubuntu kernel: [    0.164188] pci 0000:00:1b.0: reg 10: [mem 0xefffc000-0xefffffff 64bit]
Jan  7 21:33:55 ubuntu kernel: [    0.164312] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Jan  7 21:33:55 ubuntu kernel: [    0.164351] pci 0000:00:1c.0: [8086:27d0] type 01 class 0x060400
Jan  7 21:33:55 ubuntu kernel: [    0.164480] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Jan  7 21:33:55 ubuntu kernel: [    0.164527] pci 0000:00:1c.3: [8086:27d6] type 01 class 0x060400
Jan  7 21:33:55 ubuntu kernel: [    0.164657] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
Jan  7 21:33:55 ubuntu kernel: [    0.164701] pci 0000:00:1d.0: [8086:27c8] type 00 class 0x0c0300
Jan  7 21:33:55 ubuntu kernel: [    0.164768] pci 0000:00:1d.0: reg 20: [io  0xbf80-0xbf9f]
Jan  7 21:33:55 ubuntu kernel: [    0.164819] pci 0000:00:1d.1: [8086:27c9] type 00 class 0x0c0300
Jan  7 21:33:55 ubuntu kernel: [    0.164884] pci 0000:00:1d.1: reg 20: [io  0xbf60-0xbf7f]
Jan  7 21:33:55 ubuntu kernel: [    0.164935] pci 0000:00:1d.2: [8086:27ca] type 00 class 0x0c0300
Jan  7 21:33:55 ubuntu kernel: [    0.165003] pci 0000:00:1d.2: reg 20: [io  0xbf40-0xbf5f]
Jan  7 21:33:55 ubuntu kernel: [    0.165055] pci 0000:00:1d.3: [8086:27cb] type 00 class 0x0c0300
Jan  7 21:33:55 ubuntu kernel: [    0.165121] pci 0000:00:1d.3: reg 20: [io  0xbf20-0xbf3f]
Jan  7 21:33:55 ubuntu kernel: [    0.165186] pci 0000:00:1d.7: [8086:27cc] type 00 class 0x0c0320
Jan  7 21:33:55 ubuntu kernel: [    0.165215] pci 0000:00:1d.7: reg 10: [mem 0xffa80000-0xffa803ff]
Jan  7 21:33:55 ubuntu kernel: [    0.165339] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Jan  7 21:33:55 ubuntu kernel: [    0.165371] pci 0000:00:1e.0: [8086:2448] type 01 class 0x060401
Jan  7 21:33:55 ubuntu kernel: [    0.165484] pci 0000:00:1f.0: [8086:27b9] type 00 class 0x060100
Jan  7 21:33:55 ubuntu kernel: [    0.165615] pci 0000:00:1f.0: quirk: [io  0x1000-0x107f] claimed by ICH6 ACPI/GPIO/TCO
Jan  7 21:33:55 ubuntu kernel: [    0.165624] pci 0000:00:1f.0: quirk: [io  0x1080-0x10bf] claimed by ICH6 GPIO
Jan  7 21:33:55 ubuntu kernel: [    0.165630] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0900 (mask 007f)
Jan  7 21:33:55 ubuntu kernel: [    0.165638] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 0c80 (mask 003f)
Jan  7 21:33:55 ubuntu kernel: [    0.165715] pci 0000:00:1f.2: [8086:27c4] type 00 class 0x010180
Jan  7 21:33:55 ubuntu kernel: [    0.165741] pci 0000:00:1f.2: reg 10: [io  0x01f0-0x01f7]
Jan  7 21:33:55 ubuntu kernel: [    0.165756] pci 0000:00:1f.2: reg 14: [io  0x03f4-0x03f7]
Jan  7 21:33:55 ubuntu kernel: [    0.165771] pci 0000:00:1f.2: reg 18: [io  0x0170-0x0177]
Jan  7 21:33:55 ubuntu kernel: [    0.165786] pci 0000:00:1f.2: reg 1c: [io  0x0374-0x0377]
Jan  7 21:33:55 ubuntu kernel: [    0.165801] pci 0000:00:1f.2: reg 20: [io  0xbfa0-0xbfaf]
Jan  7 21:33:55 ubuntu kernel: [    0.165867] pci 0000:00:1f.2: PME# supported from D3hot
Jan  7 21:33:55 ubuntu kernel: [    0.165893] pci 0000:00:1f.3: [8086:27da] type 00 class 0x0c0500
Jan  7 21:33:55 ubuntu kernel: [    0.165977] pci 0000:00:1f.3: reg 20: [io  0x10c0-0x10df]
Jan  7 21:33:55 ubuntu kernel: [    0.166096] pci 0000:01:00.0: [1002:7145] type 00 class 0x030000
Jan  7 21:33:55 ubuntu kernel: [    0.166114] pci 0000:01:00.0: reg 10: [mem 0xd0000000-0xdfffffff pref]

---

### Post by Bucky Ball on 2014-01-07
*Thread moved to **General Help**.*

Wubi is no longer supported and there are not many users here that know much about it (not used much as not considered a permanent solution but a 'try before you install' option). 

Having said that, good luck with it, but you would have better luck with a dual-boot (Ubuntu and Win on separate partitions). ;)

---

