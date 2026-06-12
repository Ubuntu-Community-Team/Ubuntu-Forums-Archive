---
title: "Gets stuck when suspending"
date: 2013-02-13
forum: General Help
---

### Post by TheHimself on 2013-02-13
I have Xubuntu Precise on a Lenovo X61 and when I want to suspend the computer, it gets stuck. It writes on the (blank) screen something like "Cannot evaluate the USB device at port...". But I don't have any USB devised attached. I have to force it shot down which is annoying.

---

### Post by dino99 on 2013-02-13
[http://superuser.com/questions/147844/how-to-troubleshoot-suspend-and-hibernate-in-ubuntu](http://superuser.com/questions/147844/how-to-troubleshoot-suspend-and-hibernate-in-ubuntu)

[https://wiki.ubuntu.com/DebuggingKernelSuspend](https://wiki.ubuntu.com/DebuggingKernelSuspend)

---

### Post by TheHimself on 2013-02-20
Here is the output of dmesg after restarting the computer after a crash. I don't understand much from it. Why don't they, instead of producing a new version of Ubuntu every six months and developing mobile versions, try to make sure that it works on a simple laptop?


```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-23-generic (buildd@crested) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu4) ) #36-Ubuntu SMP Tue Apr 10 20:39:51 UTC 2012 (Ubuntu 3.2.0-23.36-generic 3.2.14)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-23-generic root=UUID=3f4d097d-1f87-49c5-b85c-7a9b411f0e29 ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d800 (usable)
[    0.000000]  BIOS-e820: 000000000009d800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bf6b0000 (usable)
[    0.000000]  BIOS-e820: 00000000bf6b0000 - 00000000bf6cc000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bf6cc000 - 00000000bf700000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bf700000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 000000013c000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI present.
[    0.000000] DMI: LENOVO 776702U/776702U, BIOS 7SET33WW (1.19 ) 07/01/2008
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x13c000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0C0000000 mask FC0000000 uncachable
[    0.000000]   1 base 13C000000 mask FFC000000 uncachable
[    0.000000]   2 base 000000000 mask F00000000 write-back
[    0.000000]   3 base 100000000 mask FC0000000 write-back
[    0.000000]   4 base 0BF700000 mask FFFF00000 uncachable
[    0.000000]   5 base 0BF800000 mask FFF800000 uncachable
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 3GB, range: 1GB, type UC
[    0.000000] reg 1, base: 5056MB, range: 64MB, type UC
[    0.000000] reg 2, base: 0GB, range: 4GB, type WB
[    0.000000] reg 3, base: 4GB, range: 1GB, type WB
[    0.000000] reg 4, base: 3063MB, range: 1MB, type UC
[    0.000000] reg 5, base: 3064MB, range: 8MB, type UC
[    0.000000] total RAM covered: 4023M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K 	chunk_size: 128M 	num_reg: 6  	lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3063MB, range: 1MB, type UC
[    0.000000] reg 3, base: 3064MB, range: 8MB, type UC
[    0.000000] reg 4, base: 4GB, range: 1GB, type WB
[    0.000000] reg 5, base: 5056MB, range: 64MB, type UC
[    0.000000] e820 update range: 00000000bf700000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xbf6b0 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [ffff8800000f6980] f6980
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Base memory trampoline at [ffff880000098000] 98000 size 20480
[    0.000000] init_memory_mapping: 0000000000000000-00000000bf6b0000
[    0.000000]  0000000000 - 00bf600000 page 2M
[    0.000000]  00bf600000 - 00bf6b0000 page 4k
[    0.000000] kernel direct mapping tables up to bf6b0000 @ 1fffb000-20000000
[    0.000000] init_memory_mapping: 0000000100000000-000000013c000000
[    0.000000]  0100000000 - 013c000000 page 2M
[    0.000000] kernel direct mapping tables up to 13c000000 @ bf6aa000-bf6b0000
[    0.000000] RAMDISK: 355d0000 - 36ae0000
[    0.000000] ACPI: RSDP 00000000000f6950 00024 (v02 LENOVO)
[    0.000000] ACPI: XSDT 00000000bf6bce64 00094 (v01 LENOVO TP-7S    00001190  LTP 00000000)
[    0.000000] ACPI: FACP 00000000bf6bd000 000F4 (v03 LENOVO TP-7S    00001190 LNVO 00000001)
[    0.000000] ACPI Warning: 32/64X length mismatch in Gpe1Block: 0/32 (20110623/tbfadt-529)
[    0.000000] ACPI Warning: Optional field Gpe1Block has zero address or length: 0x000000000000102C/0x0 (20110623/tbfadt-560)
[    0.000000] ACPI: DSDT 00000000bf6bd3db 0E82E (v01 LENOVO TP-7S    00001190 MSFT 03000000)
[    0.000000] ACPI: FACS 00000000bf6e4000 00040
[    0.000000] ACPI: SSDT 00000000bf6bd1b4 00227 (v01 LENOVO TP-7S    00001190 MSFT 03000000)
[    0.000000] ACPI: ECDT 00000000bf6cbc09 00052 (v01 LENOVO TP-7S    00001190 LNVO 00000001)
[    0.000000] ACPI: TCPA 00000000bf6cbc5b 00032 (v02 LENOVO TP-7S    00001190 LNVO 00000001)
[    0.000000] ACPI: APIC 00000000bf6cbc8d 00068 (v01 LENOVO TP-7S    00001190 LNVO 00000001)
[    0.000000] ACPI: MCFG 00000000bf6cbcf5 0003C (v01 LENOVO TP-7S    00001190 LNVO 00000001)
[    0.000000] ACPI: HPET 00000000bf6cbd31 00038 (v01 LENOVO TP-7S    00001190 LNVO 00000001)
[    0.000000] ACPI: SLIC 00000000bf6cbdf0 00176 (v01 LENOVO TP-7S    00001190  LTP 00000000)
[    0.000000] ACPI: BOOT 00000000bf6cbf66 00028 (v01 LENOVO TP-7S    00001190  LTP 00000001)
[    0.000000] ACPI: ASF! 00000000bf6cbf8e 00072 (v16 LENOVO TP-7S    00001190 PTL  00000001)
[    0.000000] ACPI: SSDT 00000000bf6e2697 0025F (v01 LENOVO TP-7S    00001190 INTL 20050513)
[    0.000000] ACPI: SSDT 00000000bf6e28f6 000A6 (v01 LENOVO TP-7S    00001190 INTL 20050513)
[    0.000000] ACPI: SSDT 00000000bf6e299c 004F7 (v01 LENOVO TP-7S    00001190 INTL 20050513)
[    0.000000] ACPI: SSDT 00000000bf6e2e93 001D8 (v01 LENOVO TP-7S    00001190 INTL 20050513)
[    0.000000] ACPI: DMI detected: Lenovo ThinkPad X61
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000013c000000
[    0.000000] Initmem setup node 0 0000000000000000-000000013c000000
[    0.000000]   NODE_DATA [000000013bffb000 - 000000013bffffff]
[    0.000000]  [ffffea0000000000-ffffea0004ffffff] PMD -> [ffff880137600000-ffff88013b5fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x0013c000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x000bf6b0
[    0.000000]     0: 0x00100000 -> 0x0013c000
[    0.000000] On node 0 totalpages: 1029693
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 5 pages reserved
[    0.000000]   DMA zone: 3912 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 16320 pages used for memmap
[    0.000000]   DMA32 zone: 763632 pages, LIFO batch:31
[    0.000000]   Normal zone: 3840 pages used for memmap
[    0.000000]   Normal zone: 241920 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
[    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
[    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000bf6b0000 - 00000000bf6cc000
[    0.000000] PM: Registered nosave memory: 00000000bf6cc000 - 00000000bf700000
[    0.000000] PM: Registered nosave memory: 00000000bf700000 - 00000000c0000000
[    0.000000] PM: Registered nosave memory: 00000000c0000000 - 00000000f0000000
[    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000f4000000
[    0.000000] PM: Registered nosave memory: 00000000f4000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec10000
[    0.000000] PM: Registered nosave memory: 00000000fec10000 - 00000000fed00000
[    0.000000] PM: Registered nosave memory: 00000000fed00000 - 00000000fed14000
[    0.000000] PM: Registered nosave memory: 00000000fed14000 - 00000000fed1a000
[    0.000000] PM: Registered nosave memory: 00000000fed1a000 - 00000000fed1c000
[    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed90000
[    0.000000] PM: Registered nosave memory: 00000000fed90000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ff000000
[    0.000000] PM: Registered nosave memory: 00000000ff000000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:30000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88013bc00000 s83072 r8192 d23424 u1048576
[    0.000000] pcpu-alloc: s83072 r8192 d23424 u1048576 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1009464
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-23-generic root=UUID=3f4d097d-1f87-49c5-b85c-7a9b411f0e29 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 3949556k/5177344k available (6566k kernel code, 1058572k absent, 169216k reserved, 6637k data, 920k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:512 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 33554432 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1596.001 MHz processor.
[    0.004009] Calibrating delay loop (skipped), value calculated using timer frequency.. 3192.00 BogoMIPS (lpj=6384004)
[    0.004022] pid_max: default: 32768 minimum: 301
[    0.004090] Security Framework initialized
[    0.004136] AppArmor: AppArmor initialized
[    0.004141] Yama: becoming mindful.
[    0.008585] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.013872] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.016377] Mount-cache hash table entries: 256
[    0.016760] Initializing cgroup subsys cpuacct
[    0.016776] Initializing cgroup subsys memory
[    0.016798] Initializing cgroup subsys devices
[    0.016804] Initializing cgroup subsys freezer
[    0.016810] Initializing cgroup subsys blkio
[    0.016827] Initializing cgroup subsys perf_event
[    0.016915] CPU: Physical Processor ID: 0
[    0.016920] CPU: Processor Core ID: 0
[    0.016927] mce: CPU supports 6 MCE banks
[    0.016948] CPU0: Thermal monitoring enabled (TM2)
[    0.016959] using mwait in idle threads.
[    0.023937] ACPI: Core revision 20110623
[    0.048037] ftrace: allocating 27049 entries in 107 pages
[    0.052692] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.093059] CPU0: Intel(R) Core(TM)2 Duo CPU     L7500  @ 1.60GHz stepping 0b
[    0.096005] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
[    0.096005] PEBS disabled due to CPU errata.
[    0.096005] ... version:                2
[    0.096005] ... bit width:              40
[    0.096005] ... generic registers:      2
[    0.096005] ... value mask:             000000ffffffffff
[    0.096005] ... max period:             000000007fffffff
[    0.096005] ... fixed-purpose events:   3
[    0.096005] ... event mask:             0000000700000003
[    0.096005] NMI watchdog enabled, takes one hw-pmu counter.
[    0.096005] Booting Node   0, Processors  #1 Ok.
[    0.096005] smpboot cpu 1: start_ip = 98000
[    0.188011] TSC synchronization [CPU#0 -> CPU#1]:
[    0.188011] Measured 825832 cycles TSC warp between CPUs, turning off TSC clock.
[    0.188011] Marking TSC unstable due to check_tsc_sync_source failed
[    0.188068] NMI watchdog enabled, takes one hw-pmu counter.
[    0.188151] Brought up 2 CPUs
[    0.188158] Total of 2 processors activated (6384.05 BogoMIPS).
[    0.192224] devtmpfs: initialized
[    0.196573] EVM: security.selinux
[    0.196578] EVM: security.SMACK64
[    0.196582] EVM: security.capability
[    0.196610] PM: Registering ACPI NVS region at bf6cc000 (212992 bytes)
[    0.198149] print_constraints: dummy: 
[    0.198220] RTC time: 11:12:32, date: 02/20/13
[    0.198306] NET: Registered protocol family 16
[    0.198378] Trying to unpack rootfs image as initramfs...
[    0.198677] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.198685] ACPI: bus type pci registered
[    0.198857] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf0000000-0xf3ffffff] (base 0xf0000000)
[    0.198867] PCI: MMCONFIG at [mem 0xf0000000-0xf3ffffff] reserved in E820
[    0.235129] PCI: Using configuration type 1 for base access
[    0.238169] bio: create slab <bio-0> at 0
[    0.238406] ACPI: Added _OSI(Module Device)
[    0.238413] ACPI: Added _OSI(Processor Device)
[    0.238418] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.238424] ACPI: Added _OSI(Processor Aggregator Device)
[    0.238430] ACPI: Added _OSI(Linux)
[    0.244456] ACPI: EC: EC description table is found, configuring boot EC
[    0.259664] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query honored via DMI
[    0.275215] ACPI: SSDT 00000000bf6e1d72 00282 (v01  PmRef  Cpu0Ist 00000100 INTL 20050513)
[    0.277236] ACPI: Dynamic OEM Table Load:
[    0.277246] ACPI: SSDT           (null) 00282 (v01  PmRef  Cpu0Ist 00000100 INTL 20050513)
[    0.277565] ACPI: SSDT 00000000bf6e2079 0061E (v01  PmRef  Cpu0Cst 00000100 INTL 20050513)
[    0.279100] ACPI: Dynamic OEM Table Load:
[    0.279109] ACPI: SSDT           (null) 0061E (v01  PmRef  Cpu0Cst 00000100 INTL 20050513)
[    0.312615] ACPI: SSDT 00000000bf6e1caa 000C8 (v01  PmRef  Cpu1Ist 00000100 INTL 20050513)
[    0.314114] ACPI: Dynamic OEM Table Load:
[    0.314123] ACPI: SSDT           (null) 000C8 (v01  PmRef  Cpu1Ist 00000100 INTL 20050513)
[    0.314340] ACPI: SSDT 00000000bf6e1ff4 00085 (v01  PmRef  Cpu1Cst 00000100 INTL 20050513)
[    0.315813] ACPI: Dynamic OEM Table Load:
[    0.315822] ACPI: SSDT           (null) 00085 (v01  PmRef  Cpu1Cst 00000100 INTL 20050513)
[    0.344574] ACPI: Interpreter enabled
[    0.344585] ACPI: (supports S0 S3 S4 S5)
[    0.344636] ACPI: Using IOAPIC for interrupt routing
[    0.351618] ACPI: Power Resource [PUBS] (on)
[    0.361013] ACPI: EC: GPE = 0x12, I/O: command/status = 0x66, data = 0x62
[    0.362051] ACPI: ACPI Dock Station Driver: 3 docks/bays found
[    0.362051] HEST: Table not found.
[    0.362051] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.364448] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.364612] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.364620] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.364628] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.364636] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    0.364643] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    0.364650] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000dffff]
[    0.364658] pci_root PNP0A08:00: host bridge window [mem 0xc0000000-0xfebfffff]
[    0.364665] pci_root PNP0A08:00: host bridge window [mem 0xfed40000-0xfed4bfff]
[    0.364701] pci 0000:00:00.0: [8086:2a00] type 0 class 0x000600
[    0.364820] pci 0000:00:02.0: [8086:2a02] type 0 class 0x000300
[    0.364854] pci 0000:00:02.0: reg 10: [mem 0xf8100000-0xf81fffff 64bit]
[    0.364877] pci 0000:00:02.0: reg 18: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.364894] pci 0000:00:02.0: reg 20: [io  0x1800-0x1807]
[    0.364990] pci 0000:00:02.1: [8086:2a03] type 0 class 0x000380
[    0.365019] pci 0000:00:02.1: reg 10: [mem 0xf8200000-0xf82fffff 64bit]
[    0.365288] pci 0000:00:19.0: [8086:1049] type 0 class 0x000200
[    0.365364] pci 0000:00:19.0: reg 10: [mem 0xfe000000-0xfe01ffff]
[    0.365404] pci 0000:00:19.0: reg 14: [mem 0xfe025000-0xfe025fff]
[    0.365443] pci 0000:00:19.0: reg 18: [io  0x1840-0x185f]
[    0.365722] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.365738] pci 0000:00:19.0: PME# disabled
[    0.365801] pci 0000:00:1a.0: [8086:2834] type 0 class 0x000c03
[    0.365984] pci 0000:00:1a.0: reg 20: [io  0x1860-0x187f]
[    0.366118] pci 0000:00:1a.1: [8086:2835] type 0 class 0x000c03
[    0.366298] pci 0000:00:1a.1: reg 20: [io  0x1880-0x189f]
[    0.366469] pci 0000:00:1a.7: [8086:283a] type 0 class 0x000c03
[    0.366535] pci 0000:00:1a.7: reg 10: [mem 0xfe226c00-0xfe226fff]
[    0.366838] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.366855] pci 0000:00:1a.7: PME# disabled
[    0.366939] pci 0000:00:1b.0: [8086:284b] type 0 class 0x000403
[    0.367010] pci 0000:00:1b.0: reg 10: [mem 0xfe020000-0xfe023fff 64bit]
[    0.367345] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.367360] pci 0000:00:1b.0: PME# disabled
[    0.367454] pci 0000:00:1c.0: [8086:283f] type 1 class 0x000604
[    0.367806] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.367821] pci 0000:00:1c.0: PME# disabled
[    0.367922] pci 0000:00:1c.1: [8086:2841] type 1 class 0x000604
[    0.368286] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.368301] pci 0000:00:1c.1: PME# disabled
[    0.368413] pci 0000:00:1d.0: [8086:2830] type 0 class 0x000c03
[    0.368596] pci 0000:00:1d.0: reg 20: [io  0x18a0-0x18bf]
[    0.368730] pci 0000:00:1d.1: [8086:2831] type 0 class 0x000c03
[    0.368912] pci 0000:00:1d.1: reg 20: [io  0x18c0-0x18df]
[    0.369098] pci 0000:00:1d.7: [8086:2836] type 0 class 0x000c03
[    0.369174] pci 0000:00:1d.7: reg 10: [mem 0xfe227000-0xfe2273ff]
[    0.369516] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.369531] pci 0000:00:1d.7: PME# disabled
[    0.369602] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
[    0.369905] pci 0000:00:1f.0: [8086:2811] type 0 class 0x000601
[    0.370212] pci 0000:00:1f.0: quirk: [io  0x1000-0x107f] claimed by ICH6 ACPI/GPIO/TCO
[    0.370230] pci 0000:00:1f.0: quirk: [io  0x1180-0x11bf] claimed by ICH6 GPIO
[    0.370243] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 1600 (mask 007f)
[    0.370255] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 15e0 (mask 000f)
[    0.370266] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 1680 (mask 001f)
[    0.370425] pci 0000:00:1f.1: [8086:2850] type 0 class 0x000101
[    0.370478] pci 0000:00:1f.1: reg 10: [io  0x0000-0x0007]
[    0.370517] pci 0000:00:1f.1: reg 14: [io  0x0000-0x0003]
[    0.370556] pci 0000:00:1f.1: reg 18: [io  0x0000-0x0007]
[    0.370594] pci 0000:00:1f.1: reg 1c: [io  0x0000-0x0003]
[    0.370633] pci 0000:00:1f.1: reg 20: [io  0x18e0-0x18ef]
[    0.370804] pci 0000:00:1f.2: [8086:2829] type 0 class 0x000106
[    0.370889] pci 0000:00:1f.2: reg 10: [io  0x1c30-0x1c37]
[    0.370928] pci 0000:00:1f.2: reg 14: [io  0x1c24-0x1c27]
[    0.370966] pci 0000:00:1f.2: reg 18: [io  0x1c28-0x1c2f]
[    0.371005] pci 0000:00:1f.2: reg 1c: [io  0x1c20-0x1c23]
[    0.371044] pci 0000:00:1f.2: reg 20: [io  0x1c00-0x1c1f]
[    0.371083] pci 0000:00:1f.2: reg 24: [mem 0xfe226000-0xfe2267ff]
[    0.371294] pci 0000:00:1f.2: PME# supported from D3hot
[    0.371309] pci 0000:00:1f.2: PME# disabled
[    0.371376] pci 0000:00:1f.3: [8086:283e] type 0 class 0x000c05
[    0.371429] pci 0000:00:1f.3: reg 10: [mem 0xfe227400-0xfe2274ff]
[    0.371565] pci 0000:00:1f.3: reg 20: [io  0x1c40-0x1c5f]
[    0.371880] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.371895] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.371910] pci 0000:00:1c.0:   bridge window [mem 0xfc000000-0xfdffffff]
[    0.371935] pci 0000:00:1c.0:   bridge window [mem 0xf8000000-0xf80fffff 64bit pref]
[    0.372264] pci 0000:03:00.0: [8086:4227] type 0 class 0x000280
[    0.372333] pci 0000:03:00.0: reg 10: [mem 0xdfcff000-0xdfcfffff]
[    0.372834] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[    0.372853] pci 0000:03:00.0: PME# disabled
[    0.380130] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    0.380141] pci 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
[    0.380152] pci 0000:00:1c.1:   bridge window [mem 0xdc100000-0xdfcfffff]
[    0.380169] pci 0000:00:1c.1:   bridge window [mem 0xdfe00000-0xdfefffff 64bit pref]
[    0.380295] pci 0000:05:00.0: [1180:0476] type 2 class 0x000607
[    0.380374] pci 0000:05:00.0: reg 10: [mem 0xf8300000-0xf8300fff]
[    0.380494] pci 0000:05:00.0: supports D1 D2
[    0.380500] pci 0000:05:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.380517] pci 0000:05:00.0: PME# disabled
[    0.380590] pci 0000:05:00.1: [1180:0832] type 0 class 0x000c00
[    0.380663] pci 0000:05:00.1: reg 10: [mem 0xf8301000-0xf83017ff]
[    0.380998] pci 0000:05:00.1: supports D1 D2
[    0.381004] pci 0000:05:00.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.381020] pci 0000:05:00.1: PME# disabled
[    0.381087] pci 0000:05:00.2: [1180:0822] type 0 class 0x000805
[    0.381160] pci 0000:05:00.2: reg 10: [mem 0xf8301800-0xf83018ff]
[    0.381494] pci 0000:05:00.2: supports D1 D2
[    0.381499] pci 0000:05:00.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.381515] pci 0000:05:00.2: PME# disabled
[    0.381726] pci 0000:00:1e.0: PCI bridge to [bus 05-08] (subtractive decode)
[    0.381742] pci 0000:00:1e.0:   bridge window [io  0x4000-0x7fff]
[    0.381757] pci 0000:00:1e.0:   bridge window [mem 0xf8300000-0xfbffffff]
[    0.381782] pci 0000:00:1e.0:   bridge window [mem 0xf4000000-0xf7ffffff 64bit pref]
[    0.381790] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.381798] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.381805] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.381813] pci 0000:00:1e.0:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.381820] pci 0000:00:1e.0:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.381827] pci 0000:00:1e.0:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
[    0.381835] pci 0000:00:1e.0:   bridge window [mem 0xc0000000-0xfebfffff] (subtractive decode)
[    0.381842] pci 0000:00:1e.0:   bridge window [mem 0xfed40000-0xfed4bfff] (subtractive decode)
[    0.382059] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.382318] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP0._PRT]
[    0.382392] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[    0.382480] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    0.383129]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.383934]  pci0000:00: ACPI _OSC control (0x1d) granted
[    0.394897] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 *10 11)
[    0.395080] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)
[    0.395256] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)
[    0.395431] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
[    0.395603] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11)
[    0.395776] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11)
[    0.395947] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 *11)
[    0.396145] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11)
[    0.396469] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.396501] vgaarb: loaded
[    0.396505] vgaarb: bridge control possible 0000:00:02.0
[    0.396809] i2c-core: driver [aat2870] using legacy suspend method
[    0.396814] i2c-core: driver [aat2870] using legacy resume method
[    0.396998] SCSI subsystem initialized
[    0.397147] libata version 3.00 loaded.
[    0.397287] usbcore: registered new interface driver usbfs
[    0.397317] usbcore: registered new interface driver hub
[    0.397396] usbcore: registered new device driver usb
[    0.397643] PCI: Using ACPI for IRQ routing
[    0.401777] PCI: pci_cache_line_size set to 64 bytes
[    0.402005] reserve RAM buffer: 000000000009d800 - 000000000009ffff 
[    0.402013] reserve RAM buffer: 00000000bf6b0000 - 00000000bfffffff 
[    0.402282] NetLabel: Initializing
[    0.402287] NetLabel:  domain hash size = 128
[    0.402291] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.402320] NetLabel:  unlabeled traffic allowed by default
[    0.402455] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.402468] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.402481] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.412369] Switching to clocksource hpet
[    0.433004] AppArmor: AppArmor Filesystem Enabled
[    0.433082] pnp: PnP ACPI init
[    0.433126] ACPI: bus type pnp registered
[    0.434167] pnp 00:00: [mem 0x00000000-0x0009ffff]
[    0.434175] pnp 00:00: [mem 0x000c0000-0x000c3fff]
[    0.434181] pnp 00:00: [mem 0x000c4000-0x000c7fff]
[    0.434186] pnp 00:00: [mem 0x000c8000-0x000cbfff]
[    0.434192] pnp 00:00: [mem 0x000cc000-0x000cffff]
[    0.434197] pnp 00:00: [mem 0x000d0000-0x000d3fff]
[    0.434203] pnp 00:00: [mem 0x000d4000-0x000d3fff disabled]
[    0.434209] pnp 00:00: [mem 0x000d8000-0x000d7fff disabled]
[    0.434215] pnp 00:00: [mem 0x000dc000-0x000dbfff disabled]
[    0.434221] pnp 00:00: [mem 0x000e0000-0x000e3fff]
[    0.434227] pnp 00:00: [mem 0x000e4000-0x000e7fff]
[    0.434232] pnp 00:00: [mem 0x000e8000-0x000ebfff]
[    0.434238] pnp 00:00: [mem 0x000ec000-0x000effff]
[    0.434244] pnp 00:00: [mem 0x000f0000-0x000fffff]
[    0.434250] pnp 00:00: [mem 0x00100000-0xbfffffff]
[    0.434256] pnp 00:00: [mem 0xfec00000-0xfed3ffff]
[    0.434262] pnp 00:00: [mem 0xfed4c000-0xffffffff]
[    0.434462] system 00:00: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.434472] system 00:00: [mem 0x000c0000-0x000c3fff] could not be reserved
[    0.434480] system 00:00: [mem 0x000c4000-0x000c7fff] could not be reserved
[    0.434488] system 00:00: [mem 0x000c8000-0x000cbfff] has been reserved
[    0.434495] system 00:00: [mem 0x000cc000-0x000cffff] has been reserved
[    0.434503] system 00:00: [mem 0x000d0000-0x000d3fff] could not be reserved
[    0.434511] system 00:00: [mem 0x000e0000-0x000e3fff] could not be reserved
[    0.434518] system 00:00: [mem 0x000e4000-0x000e7fff] could not be reserved
[    0.434526] system 00:00: [mem 0x000e8000-0x000ebfff] could not be reserved
[    0.434533] system 00:00: [mem 0x000ec000-0x000effff] could not be reserved
[    0.434541] system 00:00: [mem 0x000f0000-0x000fffff] could not be reserved
[    0.434548] system 00:00: [mem 0x00100000-0xbfffffff] could not be reserved
[    0.434557] system 00:00: [mem 0xfec00000-0xfed3ffff] could not be reserved
[    0.434564] system 00:00: [mem 0xfed4c000-0xffffffff] could not be reserved
[    0.434575] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.434635] pnp 00:01: [bus 00-ff]
[    0.434641] pnp 00:01: [io  0x0cf8-0x0cff]
[    0.434648] pnp 00:01: [io  0x0000-0x0cf7 window]
[    0.434654] pnp 00:01: [io  0x0d00-0xffff window]
[    0.434660] pnp 00:01: [mem 0x000a0000-0x000bffff window]
[    0.434666] pnp 00:01: [mem 0x000c0000-0x000c3fff window]
[    0.434673] pnp 00:01: [mem 0x000c4000-0x000c7fff window]
[    0.434679] pnp 00:01: [mem 0x000c8000-0x000cbfff window]
[    0.434685] pnp 00:01: [mem 0x000cc000-0x000cffff window]
[    0.434691] pnp 00:01: [mem 0x000d0000-0x000d3fff window]
[    0.434697] pnp 00:01: [mem 0x000d4000-0x000d7fff window]
[    0.434703] pnp 00:01: [mem 0x000d8000-0x000dbfff window]
[    0.434709] pnp 00:01: [mem 0x000dc000-0x000dffff window]
[    0.434716] pnp 00:01: [mem 0x000e0000-0x000e3fff window]
[    0.434722] pnp 00:01: [mem 0x000e4000-0x000e7fff window]
[    0.434728] pnp 00:01: [mem 0x000e8000-0x000ebfff window]
[    0.434741] pnp 00:01: [mem 0x000ec000-0x000effff window]
[    0.434748] pnp 00:01: [mem 0xc0000000-0xfebfffff window]
[    0.434754] pnp 00:01: [mem 0xfed40000-0xfed4bfff window]
[    0.434900] pnp 00:01: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.435011] pnp 00:02: [io  0x0010-0x001f]
[    0.435017] pnp 00:02: [io  0x0090-0x009f]
[    0.435022] pnp 00:02: [io  0x0024-0x0025]
[    0.435027] pnp 00:02: [io  0x0028-0x0029]
[    0.435032] pnp 00:02: [io  0x002c-0x002d]
[    0.435038] pnp 00:02: [io  0x0030-0x0031]
[    0.435043] pnp 00:02: [io  0x0034-0x0035]
[    0.435048] pnp 00:02: [io  0x0038-0x0039]
[    0.435053] pnp 00:02: [io  0x003c-0x003d]
[    0.435058] pnp 00:02: [io  0x00a4-0x00a5]
[    0.435064] pnp 00:02: [io  0x00a8-0x00a9]
[    0.435069] pnp 00:02: [io  0x00ac-0x00ad]
[    0.435074] pnp 00:02: [io  0x00b0-0x00b5]
[    0.435079] pnp 00:02: [io  0x00b8-0x00b9]
[    0.435084] pnp 00:02: [io  0x00bc-0x00bd]
[    0.435089] pnp 00:02: [io  0x0050-0x0053]
[    0.435094] pnp 00:02: [io  0x0072-0x0077]
[    0.435099] pnp 00:02: [io  0x164e-0x164f]
[    0.435104] pnp 00:02: [io  0x002e-0x002f]
[    0.435110] pnp 00:02: [io  0x1000-0x107f]
[    0.435115] pnp 00:02: [io  0x1180-0x11bf]
[    0.435120] pnp 00:02: [io  0x0800-0x080f]
[    0.435125] pnp 00:02: [io  0x15e0-0x15ef]
[    0.435130] pnp 00:02: [io  0x1600-0x165f]
[    0.435136] pnp 00:02: [mem 0xf0000000-0xf3ffffff]
[    0.435142] pnp 00:02: [mem 0xfed1c000-0xfed1ffff]
[    0.435147] pnp 00:02: [mem 0xfed14000-0xfed17fff]
[    0.435153] pnp 00:02: [mem 0xfed18000-0xfed18fff]
[    0.435158] pnp 00:02: [mem 0xfed19000-0xfed19fff]
[    0.435164] pnp 00:02: [mem 0xfed45000-0xfed4bfff]
[    0.435385] system 00:02: [io  0x164e-0x164f] has been reserved
[    0.435393] system 00:02: [io  0x1000-0x107f] has been reserved
[    0.435401] system 00:02: [io  0x1180-0x11bf] has been reserved
[    0.435411] system 00:02: [io  0x0800-0x080f] has been reserved
[    0.435418] system 00:02: [io  0x15e0-0x15ef] has been reserved
[    0.435425] system 00:02: [io  0x1600-0x165f] could not be reserved
[    0.435434] system 00:02: [mem 0xf0000000-0xf3ffffff] has been reserved
[    0.435442] system 00:02: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.435450] system 00:02: [mem 0xfed14000-0xfed17fff] has been reserved
[    0.435457] system 00:02: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.435465] system 00:02: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.435473] system 00:02: [mem 0xfed45000-0xfed4bfff] has been reserved
[    0.435482] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.435580] pnp 00:03: [mem 0xfed00000-0xfed003ff]
[    0.435657] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.435683] pnp 00:04: [io  0x0000-0x000f]
[    0.435689] pnp 00:04: [io  0x0080-0x008f]
[    0.435694] pnp 00:04: [io  0x00c0-0x00df]
[    0.435700] pnp 00:04: [dma 4]
[    0.435779] pnp 00:04: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.435802] pnp 00:05: [io  0x0061]
[    0.435880] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.435906] pnp 00:06: [io  0x00f0]
[    0.435938] pnp 00:06: [irq 13]
[    0.436043] pnp 00:06: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.436068] pnp 00:07: [io  0x0070-0x0071]
[    0.436088] pnp 00:07: [irq 8]
[    0.436169] pnp 00:07: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.436195] pnp 00:08: [io  0x0060]
[    0.436200] pnp 00:08: [io  0x0064]
[    0.436212] pnp 00:08: [irq 1]
[    0.436294] pnp 00:08: Plug and Play ACPI device, IDs LEN0003 PNP0303 (active)
[    0.436326] pnp 00:09: [irq 12]
[    0.436404] pnp 00:09: Plug and Play ACPI device, IDs IBM3780 PNP0f13 (active)
[    0.436934] pnp 00:0a: Plug and Play ACPI device, IDs WACf004 (disabled)
[    0.437003] pnp 00:0b: [mem 0xfed40000-0xfed44fff]
[    0.437094] pnp 00:0b: Plug and Play ACPI device, IDs ATM1200 PNP0c31 (active)
[    0.438285] pnp: PnP ACPI: found 12 devices
[    0.438291] ACPI: ACPI bus type pnp unregistered
[    0.447979] PCI: max bus depth: 2 pci_try_num: 3
[    0.448084] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.448094] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.448109] pci 0000:00:1c.0:   bridge window [mem 0xfc000000-0xfdffffff]
[    0.448120] pci 0000:00:1c.0:   bridge window [mem 0xf8000000-0xf80fffff 64bit pref]
[    0.448137] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    0.448146] pci 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
[    0.448159] pci 0000:00:1c.1:   bridge window [mem 0xdc100000-0xdfcfffff]
[    0.448171] pci 0000:00:1c.1:   bridge window [mem 0xdfe00000-0xdfefffff 64bit pref]
[    0.448198] pci 0000:05:00.0: BAR 16: assigned [mem 0xc0000000-0xc3ffffff]
[    0.448207] pci 0000:05:00.0: BAR 15: assigned [mem 0xf4000000-0xf7ffffff pref]
[    0.448215] pci 0000:05:00.0: BAR 14: assigned [io  0x4000-0x40ff]
[    0.448222] pci 0000:05:00.0: BAR 13: assigned [io  0x4400-0x44ff]
[    0.448229] pci 0000:05:00.0: CardBus bridge to [bus 06-07]
[    0.448235] pci 0000:05:00.0:   bridge window [io  0x4400-0x44ff]
[    0.448247] pci 0000:05:00.0:   bridge window [io  0x4000-0x40ff]
[    0.448259] pci 0000:05:00.0:   bridge window [mem 0xf4000000-0xf7ffffff pref]
[    0.448271] pci 0000:05:00.0:   bridge window [mem 0xc0000000-0xc3ffffff]
[    0.448283] pci 0000:00:1e.0: PCI bridge to [bus 05-08]
[    0.448291] pci 0000:00:1e.0:   bridge window [io  0x4000-0x7fff]
[    0.448304] pci 0000:00:1e.0:   bridge window [mem 0xf8300000-0xfbffffff]
[    0.448315] pci 0000:00:1e.0:   bridge window [mem 0xf4000000-0xf7ffffff 64bit pref]
[    0.448366] pci 0000:00:1c.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.448382] pci 0000:00:1c.0: setting latency timer to 64
[    0.448411] pci 0000:00:1c.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.448422] pci 0000:00:1c.1: setting latency timer to 64
[    0.448436] pci 0000:00:1e.0: enabling device (0005 -> 0007)
[    0.448449] pci 0000:00:1e.0: setting latency timer to 64
[    0.448474] pci 0000:05:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.448489] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.448495] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.448502] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.448508] pci_bus 0000:00: resource 7 [mem 0x000d4000-0x000d7fff]
[    0.448515] pci_bus 0000:00: resource 8 [mem 0x000d8000-0x000dbfff]
[    0.448521] pci_bus 0000:00: resource 9 [mem 0x000dc000-0x000dffff]
[    0.448528] pci_bus 0000:00: resource 10 [mem 0xc0000000-0xfebfffff]
[    0.448534] pci_bus 0000:00: resource 11 [mem 0xfed40000-0xfed4bfff]
[    0.448542] pci_bus 0000:02: resource 0 [io  0x2000-0x2fff]
[    0.448550] pci_bus 0000:02: resource 1 [mem 0xfc000000-0xfdffffff]
[    0.448559] pci_bus 0000:02: resource 2 [mem 0xf8000000-0xf80fffff 64bit pref]
[    0.448568] pci_bus 0000:03: resource 0 [io  0x3000-0x3fff]
[    0.448576] pci_bus 0000:03: resource 1 [mem 0xdc100000-0xdfcfffff]
[    0.448585] pci_bus 0000:03: resource 2 [mem 0xdfe00000-0xdfefffff 64bit pref]
[    0.448595] pci_bus 0000:05: resource 0 [io  0x4000-0x7fff]
[    0.448603] pci_bus 0000:05: resource 1 [mem 0xf8300000-0xfbffffff]
[    0.448612] pci_bus 0000:05: resource 2 [mem 0xf4000000-0xf7ffffff 64bit pref]
[    0.448622] pci_bus 0000:05: resource 4 [io  0x0000-0x0cf7]
[    0.448630] pci_bus 0000:05: resource 5 [io  0x0d00-0xffff]
[    0.448638] pci_bus 0000:05: resource 6 [mem 0x000a0000-0x000bffff]
[    0.448647] pci_bus 0000:05: resource 7 [mem 0x000d4000-0x000d7fff]
[    0.448655] pci_bus 0000:05: resource 8 [mem 0x000d8000-0x000dbfff]
[    0.448664] pci_bus 0000:05: resource 9 [mem 0x000dc000-0x000dffff]
[    0.448673] pci_bus 0000:05: resource 10 [mem 0xc0000000-0xfebfffff]
[    0.448681] pci_bus 0000:05: resource 11 [mem 0xfed40000-0xfed4bfff]
[    0.448690] pci_bus 0000:06: resource 0 [io  0x4400-0x44ff]
[    0.448696] pci_bus 0000:06: resource 1 [io  0x4000-0x40ff]
[    0.448702] pci_bus 0000:06: resource 2 [mem 0xf4000000-0xf7ffffff pref]
[    0.448709] pci_bus 0000:06: resource 3 [mem 0xc0000000-0xc3ffffff]
[    0.448813] NET: Registered protocol family 2
[    0.449197] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.452205] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.461961] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.463191] TCP: Hash tables configured (established 524288 bind 65536)
[    0.463197] TCP reno registered
[    0.463222] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.463323] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.463671] NET: Registered protocol family 1
[    0.463723] pci 0000:00:02.0: Boot video device
[    0.463767] pci 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.463802] pci 0000:00:1a.0: PCI INT A disabled
[    0.463827] pci 0000:00:1a.1: power state changed by ACPI to D0
[    0.463835] pci 0000:00:1a.1: power state changed by ACPI to D0
[    0.463846] pci 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.463876] pci 0000:00:1a.1: PCI INT B disabled
[    0.463895] pci 0000:00:1a.7: power state changed by ACPI to D0
[    0.463906] pci 0000:00:1a.7: power state changed by ACPI to D0
[    0.463942] pci 0000:00:1a.7: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.464080] pci 0000:00:1a.7: PCI INT C disabled
[    0.464116] pci 0000:00:1d.0: power state changed by ACPI to D0
[    0.464123] pci 0000:00:1d.0: power state changed by ACPI to D0
[    0.464134] pci 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.464164] pci 0000:00:1d.0: PCI INT A disabled
[    0.464200] pci 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.464233] pci 0000:00:1d.1: PCI INT B disabled
[    0.464254] pci 0000:00:1d.7: power state changed by ACPI to D0
[    0.464265] pci 0000:00:1d.7: power state changed by ACPI to D0
[    0.464287] pci 0000:00:1d.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.464330] pci 0000:00:1d.7: PCI INT D disabled
[    0.464396] PCI: CLS 64 bytes, default 64
[    0.464403] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.464410] Placing 64MB software IO TLB between ffff8800bb6aa000 - ffff8800bf6aa000
[    0.464416] software IO TLB at phys 0xbb6aa000 - 0xbf6aa000
[    0.464435] Simple Boot Flag at 0x35 set to 0x1
[    0.465332] audit: initializing netlink socket (disabled)
[    0.465357] type=2000 audit(1361358752.460:1): initialized
[    0.554862] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.609605] VFS: Disk quotas dquot_6.5.2
[    0.609773] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.611150] fuse init (API version 7.17)
[    0.611394] msgmni has been set to 7713
[    0.612228] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.612297] io scheduler noop registered
[    0.612303] io scheduler deadline registered
[    0.612398] io scheduler cfq registered (default)
[    0.612705] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.612815] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.613067] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.613164] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.613462] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
[    0.613475] pcie_pme 0000:00:1c.0:pcie01: service driver pcie_pme loaded
[    0.613525] pcieport 0000:00:1c.1: Signaling PME through PCIe PME interrupt
[    0.613532] pci 0000:03:00.0: Signaling PME through PCIe PME interrupt
[    0.613543] pcie_pme 0000:00:1c.1:pcie01: service driver pcie_pme loaded
[    0.613596] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.613701] pciehp 0000:00:1c.0:pcie04: HPC vendor_id 8086 device_id 283f ss_vid 17aa ss_did 20ad
[    0.613752] pciehp 0000:00:1c.0:pcie04: service driver pciehp loaded
[    0.613780] pciehp 0000:00:1c.1:pcie04: HPC vendor_id 8086 device_id 2841 ss_vid 17aa ss_did 20ad
[    0.613825] pciehp 0000:00:1c.1:pcie04: service driver pciehp loaded
[    0.613844] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.614009] intel_idle: MWAIT substates: 0x22220
[    0.614014] intel_idle: does not run on family 6 model 15
[    0.614290] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.614523] ACPI: AC Adapter [AC] (off-line)
[    0.614707] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.614946] ACPI: Lid Switch [LID]
[    0.615252] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    0.615264] ACPI: Sleep Button [SLPB]
[    0.615407] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.615416] ACPI: Power Button [PWRF]
[    0.624486] Monitor-Mwait will be used to enter C-1 state
[    0.624566] Monitor-Mwait will be used to enter C-2 state
[    0.624628] Monitor-Mwait will be used to enter C-3 state
[    0.624657] ACPI: acpi_idle registered with cpuidle
[    0.641762] thermal LNXTHERM:00: registered as thermal_zone0
[    0.641770] ACPI: Thermal Zone [THM0] (50 C)
[    0.643374] thermal LNXTHERM:01: registered as thermal_zone1
[    0.643381] ACPI: Thermal Zone [THM1] (49 C)
[    0.643440] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.643464] ACPI: Battery Slot [BAT0] (battery present)
[    0.643586] ERST: Table is not found!
[    0.643591] GHES: HEST is not enabled!
[    0.643796] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.659706] ACPI: Battery Slot [BAT0] (battery present)
[    1.357090] Freeing initrd memory: 21568k freed
[    1.412301] serial 00:0a: [io  0x0200-0x0207]
[    1.412459] serial 00:0a: [irq 5]
[    1.413037] serial 00:0a: activated
[    1.413317] 00:0a: ttyS4 at I/O 0x200 (irq = 5) is a NS16550A
[    1.428606] Linux agpgart interface v0.103
[    1.428819] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
[    1.429199] agpgart-intel 0000:00:00.0: detected gtt size: 524288K total, 262144K mappable
[    1.432460] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    1.432723] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
[    1.436760] brd: module loaded
[    1.438887] loop: module loaded
[    1.439239] ahci 0000:00:1f.2: version 3.0
[    1.439268] ahci 0000:00:1f.2: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    1.439379] ahci 0000:00:1f.2: irq 42 for MSI/MSI-X
[    1.439477] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 1.5 Gbps 0x1 impl SATA mode
[    1.439487] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ccc 
[    1.439500] ahci 0000:00:1f.2: setting latency timer to 64
[    1.440430] scsi0 : ahci
[    1.440671] scsi1 : ahci
[    1.440874] scsi2 : ahci
[    1.441100] ata1: SATA max UDMA/133 abar m2048@0xfe226000 port 0xfe226100 irq 42
[    1.441107] ata2: DUMMY
[    1.441111] ata3: DUMMY
[    1.441309] ata_piix 0000:00:1f.1: version 2.13
[    1.441329] ata_piix 0000:00:1f.1: PCI INT C -> GSI 16 (level, low) -> IRQ 16
[    1.441397] ata_piix 0000:00:1f.1: setting latency timer to 64
[    1.442197] scsi3 : ata_piix
[    1.442385] scsi4 : ata_piix
[    1.443102] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x18e0 irq 14
[    1.443110] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18e8 irq 15
[    1.443293] ata5: port disabled--ignoring
[    1.444112] Fixed MDIO Bus: probed
[    1.444169] tun: Universal TUN/TAP device driver, 1.6
[    1.444175] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.444415] PPP generic driver version 2.4.2
[    1.444699] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.444733] ehci_hcd 0000:00:1a.7: power state changed by ACPI to D0
[    1.444746] ehci_hcd 0000:00:1a.7: power state changed by ACPI to D0
[    1.444762] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    1.444799] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    1.444808] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    1.444928] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    1.448882] ehci_hcd 0000:00:1a.7: cache line size of 64 is not supported
[    1.448915] ehci_hcd 0000:00:1a.7: irq 22, io mem 0xfe226c00
[    1.464036] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    1.464361] hub 1-0:1.0: USB hub found
[    1.464373] hub 1-0:1.0: 4 ports detected
[    1.464551] ehci_hcd 0000:00:1d.7: power state changed by ACPI to D0
[    1.464563] ehci_hcd 0000:00:1d.7: power state changed by ACPI to D0
[    1.464579] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    1.464610] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.464619] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.464733] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    1.464791] ehci_hcd 0000:00:1d.7: debug port 1
[    1.468686] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    1.468723] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xfe227000
[    1.484036] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.484345] hub 2-0:1.0: USB hub found
[    1.484357] hub 2-0:1.0: 4 ports detected
[    1.484539] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.484574] uhci_hcd: USB Universal Host Controller Interface driver
[    1.484612] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.484629] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.484637] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    1.484759] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    1.484822] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00001860
[    1.485149] hub 3-0:1.0: USB hub found
[    1.485161] hub 3-0:1.0: 2 ports detected
[    1.485319] uhci_hcd 0000:00:1a.1: power state changed by ACPI to D0
[    1.485328] uhci_hcd 0000:00:1a.1: power state changed by ACPI to D0
[    1.485340] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.485357] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    1.485365] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    1.485482] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    1.485543] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001880
[    1.485873] hub 4-0:1.0: USB hub found
[    1.485884] hub 4-0:1.0: 2 ports detected
[    1.486043] uhci_hcd 0000:00:1d.0: power state changed by ACPI to D0
[    1.486053] uhci_hcd 0000:00:1d.0: power state changed by ACPI to D0
[    1.486065] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.486082] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.486090] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.486217] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    1.486286] uhci_hcd 0000:00:1d.0: irq 16, io base 0x000018a0
[    1.486612] hub 5-0:1.0: USB hub found
[    1.486624] hub 5-0:1.0: 2 ports detected
[    1.486782] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.486799] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.486807] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.486924] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    1.486985] uhci_hcd 0000:00:1d.1: irq 17, io base 0x000018c0
[    1.487319] hub 6-0:1.0: USB hub found
[    1.487331] hub 6-0:1.0: 2 ports detected
[    1.487628] usbcore: registered new interface driver libusual
[    1.487734] i8042: PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    1.497902] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.497919] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.498258] mousedev: PS/2 mouse device common for all mice
[    1.498714] rtc_cmos 00:07: RTC can wake from S4
[    1.498948] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    1.499002] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.499206] device-mapper: uevent: version 1.0.3
[    1.499395] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    1.499592] cpuidle: using governor ladder
[    1.499845] cpuidle: using governor menu
[    1.499851] EFI Variables Facility v0.08 2004-May-17
[    1.500517] TCP cubic registered
[    1.500810] NET: Registered protocol family 10
[    1.502055] NET: Registered protocol family 17
[    1.502094] Registering the dns_resolver key type
[    1.502517] PM: Hibernation image not present or could not be loaded.
[    1.502546] registered taskstats version 1
[    1.527506] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.542584]   Magic number: 1:810:226
[    1.542798] rtc_cmos 00:07: setting system clock to 2013-02-20 11:12:34 UTC (1361358754)
[    1.544619] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.544623] EDD information not available.
[    1.760050] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.760674] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[    1.760682] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    1.760818] ata1.00: ACPI cmd ef/5f:00:00:00:00:a0 (SET FEATURES) succeeded
[    1.760826] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    1.761431] ata1.00: ATA-8: FUJITSU MHZ2120BH G1, 0084000A, max UDMA/100
[    1.761437] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.762145] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[    1.762151] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    1.762281] ata1.00: ACPI cmd ef/5f:00:00:00:00:a0 (SET FEATURES) succeeded
[    1.762288] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    1.762862] ata1.00: configured for UDMA/100
[    1.763051] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHZ2120B 0084 PQ: 0 ANSI: 5
[    1.763218] sd 0:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[    1.763245] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.763286] sd 0:0:0:0: [sda] Write Protect is off
[    1.763290] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.763319] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.857062]  sda: sda1 sda3 < sda5 sda6 sda7 > sda4
[    1.857927] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.860225] Freeing unused kernel memory: 920k freed
[    1.860525] Write protecting the kernel read-only data: 12288k
[    1.868309] Freeing unused kernel memory: 1608k freed
[    1.873934] Freeing unused kernel memory: 1196k freed
[    1.897530] zram: module is from the staging directory, the quality is unknown, you have been warned.
[    1.897846] zram: num_devices not specified. Using default: 1
[    1.897849] zram: Creating 1 devices ...
[    1.902577] udevd[108]: starting version 175
[    1.975257] e1000e: Intel(R) PRO/1000 Network Driver - 1.5.1-k
[    1.975261] e1000e: Copyright(c) 1999 - 2011 Intel Corporation.
[    1.975306] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.975322] e1000e 0000:00:19.0: setting latency timer to 64
[    1.975491] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[    2.000875] [drm] Initialized drm 1.1.0 20060810
[    2.029286] sdhci: Secure Digital Host Controller Interface driver
[    2.029290] sdhci: Copyright(c) Pierre Ossman
[    2.036088] sdhci-pci 0000:05:00.2: SDHCI controller found [1180:0822] (rev 21)
[    2.036123] sdhci-pci 0000:05:00.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.037154] sdhci-pci 0000:05:00.2: Will use DMA mode even though HW doesn't fully claim to support it.
[    2.037164] sdhci-pci 0000:05:00.2: setting latency timer to 64
[    2.039461] mmc0: no vmmc regulator found
[    2.043641] Registered led device: mmc0::
[    2.047067] mmc0: SDHCI controller on PCI [0000:05:00.2] using DMA
[    2.047108] firewire_ohci 0000:05:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    2.063063] Adding 1987420k swap on /dev/zram0.  Priority:100 extents:1 across:1987420k SS
[    2.108063] firewire_ohci: Added fw-ohci device 0000:05:00.1, OHCI v1.10, 4 IR + 4 IT contexts, quirks 0x11
[    2.292046] usb 3-2: new full-speed USB device number 2 using uhci_hcd
[    2.322488] e1000e 0000:00:19.0: eth0: (PCI Express:2.5GT/s:Width x1) 00:1d:72:8e:d2:89
[    2.322494] e1000e 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    2.322521] e1000e 0000:00:19.0: eth0: MAC: 6, PHY: 6, PBA No: 1008FF-0FF
[    2.322598] i915 0000:00:02.0: power state changed by ACPI to D0
[    2.322605] i915 0000:00:02.0: power state changed by ACPI to D0
[    2.322615] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.322621] i915 0000:00:02.0: setting latency timer to 64
[    2.415832] i915 0000:00:02.0: irq 44 for MSI/MSI-X
[    2.415839] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    2.415842] [drm] Driver supports precise vblank timestamp query.
[    2.468333] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    2.608188] firewire_core: created device fw0: GUID 001d72ff8ed289ff, S400
[    2.712060] hub 1-0:1.0: unable to enumerate USB device on port 1
[    2.816919] [drm] initialized overlay support
[    2.828505] fbcon: inteldrmfb (fb0) is primary device
[    2.828573] Console: switching to colour frame buffer device 128x48
[    2.828600] fb0: inteldrmfb frame buffer device
[    2.828602] drm: registered panic notifier
[    2.841608] acpi device:02: registered as cooling_device2
[    2.841879] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input4
[    2.841951] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[    2.842014] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    3.124051] usb 3-1: new full-speed USB device number 3 using uhci_hcd
[    3.666590] Btrfs loaded
[    3.672126] usb 3-1: USB disconnect, device number 3
[    3.673780] xor: automatically using best checksumming function: generic_sse
[    3.692019]    generic_sse:  5930.000 MB/sec
[    3.692022] xor: using function: generic_sse (5930.000 MB/sec)
[    3.692728] device-mapper: dm-raid45: initialized v0.2594b
[    3.916061] usb 3-1: new full-speed USB device number 4 using uhci_hcd
[    3.962146] EXT4-fs (sda5): INFO: recovery required on readonly filesystem
[    3.962150] EXT4-fs (sda5): write access will be enabled during recovery
[    4.416089] usb 3-1: USB disconnect, device number 4
[    4.656054] usb 3-1: new full-speed USB device number 5 using uhci_hcd
[    4.902221] EXT4-fs (sda5): orphan cleanup on readonly fs
[    4.902231] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 131181
[    4.902304] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 132561
[    4.902325] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 132359
[    4.902344] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 132332
[    4.902362] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 132292
[    4.902380] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 131545
[    4.902398] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 131439
[    4.902416] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 131423
[    4.902435] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 2751
[    4.902451] EXT4-fs (sda5): 9 orphan inodes deleted
[    4.902454] EXT4-fs (sda5): recovery complete
[    5.156109] usb 3-1: USB disconnect, device number 5
[    5.396042] usb 3-1: new full-speed USB device number 6 using uhci_hcd
[    5.796663] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[    5.896128] usb 3-1: USB disconnect, device number 6
[    6.136052] usb 3-1: new full-speed USB device number 7 using uhci_hcd
[    6.352074] usb 3-1: USB disconnect, device number 7
[    7.088070] usb 3-1: new full-speed USB device number 8 using uhci_hcd
[    7.144070] hub 3-0:1.0: unable to enumerate USB device on port 1
[    7.628054] usb 3-1: new full-speed USB device number 9 using uhci_hcd
[    7.840071] usb 3-1: USB disconnect, device number 9
[    8.576089] usb 3-1: new full-speed USB device number 10 using uhci_hcd
[    8.640089] hub 3-0:1.0: unable to enumerate USB device on port 1
[    9.120061] usb 3-1: new full-speed USB device number 11 using uhci_hcd
[    9.328099] usb 3-1: USB disconnect, device number 11
[   10.064048] usb 3-1: new full-speed USB device number 12 using uhci_hcd
[   10.128097] hub 3-0:1.0: unable to enumerate USB device on port 1
[   10.608046] usb 3-1: new full-speed USB device number 13 using uhci_hcd
[   10.816114] usb 3-1: USB disconnect, device number 13
[   11.552047] usb 3-1: new full-speed USB device number 14 using uhci_hcd
[   11.616075] hub 3-0:1.0: unable to enumerate USB device on port 1
[   12.096046] usb 3-1: new full-speed USB device number 15 using uhci_hcd
[   12.304070] usb 3-1: USB disconnect, device number 15
[   13.040051] usb 3-1: new full-speed USB device number 16 using uhci_hcd
[   13.104073] hub 3-0:1.0: unable to enumerate USB device on port 1
[   13.584033] usb 3-1: new full-speed USB device number 17 using uhci_hcd
[   13.792071] usb 3-1: USB disconnect, device number 17
[   14.528056] usb 3-1: new full-speed USB device number 18 using uhci_hcd
[   14.592096] hub 3-0:1.0: unable to enumerate USB device on port 1
[   15.072044] usb 3-1: new full-speed USB device number 19 using uhci_hcd
[   15.256901] usb 3-1: can't set config #1, error -71
[   15.280094] usb 3-1: USB disconnect, device number 19
[   16.016050] usb 3-1: new full-speed USB device number 20 using uhci_hcd
[   16.080070] hub 3-0:1.0: unable to enumerate USB device on port 1
[   16.560057] usb 3-1: new full-speed USB device number 21 using uhci_hcd
[   16.738905] usb 3-1: can't set config #1, error -71
[   16.768074] usb 3-1: USB disconnect, device number 21
[   17.504066] usb 3-1: new full-speed USB device number 22 using uhci_hcd
[   17.568095] hub 3-0:1.0: unable to enumerate USB device on port 1
[   18.048043] usb 3-1: new full-speed USB device number 23 using uhci_hcd
[   18.228906] usb 3-1: can't set config #1, error -71
[   18.256067] usb 3-1: USB disconnect, device number 23
[   18.992048] usb 3-1: new full-speed USB device number 24 using uhci_hcd
[   19.056076] hub 3-0:1.0: unable to enumerate USB device on port 1
[   19.536042] usb 3-1: new full-speed USB device number 25 using uhci_hcd
[   19.711904] usb 3-1: can't set config #1, error -71
[   19.980082] usb 3-1: USB disconnect, device number 25
[   20.220043] usb 3-1: new full-speed USB device number 26 using uhci_hcd
[   20.720075] usb 3-1: USB disconnect, device number 26
[   20.960043] usb 3-1: new full-speed USB device number 27 using uhci_hcd
[   21.464072] usb 3-1: USB disconnect, device number 27
[   21.704042] usb 3-1: new full-speed USB device number 28 using uhci_hcd
[   22.204080] usb 3-1: USB disconnect, device number 28
[   22.444048] usb 3-1: new full-speed USB device number 29 using uhci_hcd
[   22.944074] usb 3-1: USB disconnect, device number 29
[   23.184047] usb 3-1: new full-speed USB device number 30 using uhci_hcd
[   23.684074] usb 3-1: USB disconnect, device number 30
[   23.924066] usb 3-1: new full-speed USB device number 31 using uhci_hcd
[   24.428089] usb 3-1: USB disconnect, device number 31
[   24.668049] usb 3-1: new full-speed USB device number 32 using uhci_hcd
[   25.168074] usb 3-1: USB disconnect, device number 32
[   25.408045] usb 3-1: new full-speed USB device number 33 using uhci_hcd
[   25.908079] usb 3-1: USB disconnect, device number 33
[   26.148045] usb 3-1: new full-speed USB device number 34 using uhci_hcd
[   26.652083] usb 3-1: USB disconnect, device number 34
[   26.892061] usb 3-1: new full-speed USB device number 35 using uhci_hcd
[   27.392089] usb 3-1: USB disconnect, device number 35
[   27.632041] usb 3-1: new full-speed USB device number 36 using uhci_hcd
[   28.132089] usb 3-1: USB disconnect, device number 36
[   28.372044] usb 3-1: new full-speed USB device number 37 using uhci_hcd
[   28.876094] usb 3-1: USB disconnect, device number 37
[   29.116042] usb 3-1: new full-speed USB device number 38 using uhci_hcd
[   29.266789] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   29.278532] udevd[452]: starting version 175
[   29.333344] lp: driver loaded but no devices found
[   29.461903] Adding 2634624k swap on /dev/sda6.  Priority:-1 extents:1 across:2634624k 
[   29.480196] tpm_tis 00:0b: 1.2 TPM (device-id 0x3203, rev-id 9)
[   29.503251] EXT4-fs (sda5): warning: maximal mount count reached, running e2fsck is recommended
[   29.519387] Non-volatile memory driver v1.3
[   29.521098] type=1400 audit(1361355182.477:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=577 comm="apparmor_parser"
[   29.521662] type=1400 audit(1361355182.477:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=577 comm="apparmor_parser"
[   29.521991] type=1400 audit(1361355182.477:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=577 comm="apparmor_parser"
[   29.522808] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   29.527461] type=1400 audit(1361355182.481:5): apparmor="STATUS" operation="profile_load" name="/usr/sbin/ntpd" pid=586 comm="apparmor_parser"
[   29.546819] Bluetooth: Core ver 2.16
[   29.546871] NET: Registered protocol family 31
[   29.546875] Bluetooth: HCI device and connection manager initialized
[   29.546878] Bluetooth: HCI socket layer initialized
[   29.546881] Bluetooth: L2CAP socket layer initialized
[   29.546889] Bluetooth: SCO socket layer initialized
[   29.547322] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   29.549256] usbcore: registered new interface driver btusb
[   29.604486] cfg80211: Calling CRDA to update world regulatory domain
[   29.616085] usb 3-1: USB disconnect, device number 38
[   29.644823] yenta_cardbus 0000:05:00.0: CardBus bridge found [17aa:20c6]
[   29.648530] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   29.648534] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   29.648609] iwl3945 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   29.648625] iwl3945 0000:03:00.0: setting latency timer to 64
[   29.665707] thinkpad_acpi: ThinkPad ACPI Extras v0.24
[   29.665711] thinkpad_acpi: http://ibm-acpi.sf.net/
[   29.665713] thinkpad_acpi: ThinkPad BIOS 7SET33WW (1.19 ), EC 7RHT16WW-1.02
[   29.665716] thinkpad_acpi: Lenovo ThinkPad X61 Tablet, model 776702U
[   29.673702] thinkpad_acpi: detected a 8-level brightness capable ThinkPad
[   29.673889] thinkpad_acpi: radio switch found; radios are enabled
[   29.674082] thinkpad_acpi: possible tablet mode switch found; ThinkPad in laptop mode
[   29.677389] thinkpad_acpi: rfkill switch tpacpi_bluetooth_sw: radio is unblocked
[   29.677850] Registered led device: tpacpi::thinklight
[   29.677889] Registered led device: tpacpi::power
[   29.677918] Registered led device: tpacpi::standby
[   29.677946] Registered led device: tpacpi::thinkvantage
[   29.681603] thinkpad_acpi: Standard ACPI backlight interface available, not loading native one
[   29.681708] thinkpad_acpi: Console audio control enabled, mode: monitor (read only)
[   29.683825] input: ThinkPad Extra Buttons as /devices/platform/thinkpad_acpi/input/input5
[   29.707394] iwl3945 0000:03:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   29.707400] iwl3945 0000:03:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   29.707560] iwl3945 0000:03:00.0: irq 45 for MSI/MSI-X
[   29.707868] Registered led device: phy0-led
[   29.707910] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   29.723503] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   29.740067] device-mapper: multipath: version 1.3.0 loaded
[   29.811647] yenta_cardbus 0000:05:00.0: ISA IRQ mask 0x0cb8, PCI irq 16
[   29.811653] yenta_cardbus 0000:05:00.0: Socket status: 30000006
[   29.814002] yenta_cardbus 0000:05:00.0: pcmcia: parent PCI bridge window: [io  0x4000-0x7fff]
[   29.814007] yenta_cardbus 0000:05:00.0: pcmcia: parent PCI bridge window: [mem 0xf8300000-0xfbffffff]
[   29.814012] pcmcia_socket pcmcia_socket0: cs: memory probe 0xf8300000-0xfbffffff: excluding 0xf8300000-0xf86cffff
[   29.814031] yenta_cardbus 0000:05:00.0: pcmcia: parent PCI bridge window: [mem 0xf4000000-0xf7ffffff 64bit pref]
[   29.814035] pcmcia_socket pcmcia_socket0: cs: memory probe 0xf4000000-0xf7ffffff: excluding 0xf4000000-0xf7ffffff
[   29.856089] usb 3-1: new full-speed USB device number 39 using uhci_hcd
[   29.940770] snd_hda_intel 0000:00:1b.0: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   29.940776] hda_intel: probe_mask set to 0x1 for device 17aa:20ac
[   29.940857] snd_hda_intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[   29.940936] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   29.997049] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   29.997055] cfg80211: World regulatory domain updated:
[   29.997057] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   29.997061] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.997065] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   29.997069] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   29.997072] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.997076] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   30.033833] EXT4-fs (sda4): warning: maximal mount count reached, running e2fsck is recommended
[   30.034651] EXT4-fs (sda4): recovery complete
[   30.034657] EXT4-fs (sda4): mounted filesystem with ordered data mode. Opts: (null)
[   30.077900] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xd3fff 0xe0000-0xfffff
[   30.077943] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: excluding 0xa0000000-0xa0ffffff
[   30.077979] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: excluding 0x60000000-0x60ffffff
[   30.089555] RPC: Registered named UNIX socket transport module.
[   30.089559] RPC: Registered udp transport module.
[   30.089561] RPC: Registered tcp transport module.
[   30.089564] RPC: Registered tcp NFSv4.1 backchannel transport module.
[   30.095920] FS-Cache: Loaded
[   30.108607] FS-Cache: Netfs 'nfs' registered for caching
[   30.115940] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   30.164390] init: failsafe main process (866) killed by TERM signal
[   30.220583] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   30.240341] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/input/input6
[   30.301946] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   30.301950] Bluetooth: BNEP filters: protocol multicast
[   30.317833] ppdev: user-space parallel port driver
[   30.323958] Bluetooth: RFCOMM TTY layer initialized
[   30.323966] Bluetooth: RFCOMM socket layer initialized
[   30.323969] Bluetooth: RFCOMM ver 1.11
[   30.356096] usb 3-1: USB disconnect, device number 39
[   30.361639] type=1400 audit(1361355183.317:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=998 comm="apparmor_parser"
[   30.365040] type=1400 audit(1361355183.321:7): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=998 comm="apparmor_parser"
[   30.394228] type=1400 audit(1361355183.349:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1011 comm="apparmor_parser"
[   30.405006] type=1400 audit(1361355183.361:9): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1012 comm="apparmor_parser"
[   30.413676] type=1400 audit(1361355183.369:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1012 comm="apparmor_parser"
[   30.414028] type=1400 audit(1361355183.369:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1012 comm="apparmor_parser"
[   30.604050] usb 3-1: new full-speed USB device number 40 using uhci_hcd
[   31.100090] usb 3-1: USB disconnect, device number 40
[   31.265821] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   31.280889] NFSD: starting 90-second grace period
[   31.340055] usb 3-1: new full-speed USB device number 41 using uhci_hcd
[   31.433680] init: lightdm main process (1280) killed by TERM signal
[   31.448302] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[   31.504112] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[   31.504783] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   31.505209] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   31.534870] iwl3945 0000:03:00.0: loaded firmware version 15.32.2.9
[   31.619428] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   31.619745] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   31.844093] usb 3-1: USB disconnect, device number 41
[   32.088051] usb 3-1: new full-speed USB device number 42 using uhci_hcd
[   32.248081] init: plymouth-stop pre-start process (1569) terminated with status 1
[   32.584077] usb 3-1: USB disconnect, device number 42
[   32.832124] usb 3-1: new full-speed USB device number 43 using uhci_hcd
[   33.109475] e1000e 0000:00:19.0: PCI INT A disabled
[   33.109490] e1000e 0000:00:19.0: PME# enabled
[   33.324142] usb 3-1: USB disconnect, device number 43
[   33.568053] usb 3-1: new full-speed USB device number 44 using uhci_hcd
[   34.064074] usb 3-1: USB disconnect, device number 44
[   34.304047] usb 3-1: new full-speed USB device number 45 using uhci_hcd
[   34.804093] usb 3-1: USB disconnect, device number 45
[   35.048046] usb 3-1: new full-speed USB device number 46 using uhci_hcd
[   35.544096] usb 3-1: USB disconnect, device number 46
[   35.784052] usb 3-1: new full-speed USB device number 47 using uhci_hcd
[   36.288072] usb 3-1: USB disconnect, device number 47
[   36.528050] usb 3-1: new full-speed USB device number 48 using uhci_hcd
[   37.028092] usb 3-1: USB disconnect, device number 48
[   37.268056] usb 3-1: new full-speed USB device number 49 using uhci_hcd
[   37.768087] usb 3-1: USB disconnect, device number 49
[   38.008054] usb 3-1: new full-speed USB device number 50 using uhci_hcd
[   38.243097] usb 3-1: can't set config #1, error -71
[   38.512100] usb 3-1: USB disconnect, device number 50
[   38.752069] usb 3-1: new full-speed USB device number 51 using uhci_hcd
[   39.252087] usb 3-1: USB disconnect, device number 51
[   39.492049] usb 3-1: new full-speed USB device number 52 using uhci_hcd
[   39.627909] show_signal_msg: 36 callbacks suppressed
[   39.627915] xfce4-power-man[1835]: segfault at a8000000a0 ip 00007f7265c55bd0 sp 00007fffd13223e8 error 4 in libICE.so.6.3.0[7f7265c4c000+16000]
[   39.992087] usb 3-1: USB disconnect, device number 52
[   40.236051] usb 3-1: new full-speed USB device number 53 using uhci_hcd
[   40.732114] usb 3-1: USB disconnect, device number 53
[   40.972046] usb 3-1: new full-speed USB device number 54 using uhci_hcd
[   41.476217] usb 3-1: USB disconnect, device number 54
[   41.716036] usb 3-1: new full-speed USB device number 55 using uhci_hcd
[   41.959758] type=1701 audit(1361355194.909:24): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=2255 comm="chrome" reason="seccomp" sig=0 syscall=39 compat=0 ip=0x7f26c45ed6d9 code=0x50001
[   42.216078] usb 3-1: USB disconnect, device number 55
[   42.456079] usb 3-1: new full-speed USB device number 56 using uhci_hcd
[   42.956094] usb 3-1: USB disconnect, device number 56
[   43.196037] usb 3-1: new full-speed USB device number 57 using uhci_hcd
[   43.700072] usb 3-1: USB disconnect, device number 57
[   43.940032] usb 3-1: new full-speed USB device number 58 using uhci_hcd
[   44.440073] usb 3-1: USB disconnect, device number 58
[   44.680030] usb 3-1: new full-speed USB device number 59 using uhci_hcd
[   45.180073] usb 3-1: USB disconnect, device number 59
[   45.420029] usb 3-1: new full-speed USB device number 60 using uhci_hcd
[   45.924070] usb 3-1: USB disconnect, device number 60
[   46.164066] usb 3-1: new full-speed USB device number 61 using uhci_hcd
[   46.664112] usb 3-1: USB disconnect, device number 61
[   46.904035] usb 3-1: new full-speed USB device number 62 using uhci_hcd
[   47.404073] usb 3-1: USB disconnect, device number 62
[   47.644028] usb 3-1: new full-speed USB device number 63 using uhci_hcd
[   48.144078] usb 3-1: USB disconnect, device number 63
[   48.384030] usb 3-1: new full-speed USB device number 64 using uhci_hcd
[   48.888089] usb 3-1: USB disconnect, device number 64
[   49.128047] usb 3-1: new full-speed USB device number 65 using uhci_hcd
[   49.628126] usb 3-1: USB disconnect, device number 65
[   49.868094] usb 3-1: new full-speed USB device number 66 using uhci_hcd
[   50.368083] usb 3-1: USB disconnect, device number 66
[   50.608081] usb 3-1: new full-speed USB device number 67 using uhci_hcd
[   51.112080] usb 3-1: USB disconnect, device number 67
[   51.352039] usb 3-1: new full-speed USB device number 68 using uhci_hcd
[   51.852141] usb 3-1: USB disconnect, device number 68
[   52.092063] usb 3-1: new full-speed USB device number 69 using uhci_hcd
[   52.596082] usb 3-1: USB disconnect, device number 69
[   52.836039] usb 3-1: new full-speed USB device number 70 using uhci_hcd
[   53.344075] usb 3-1: USB disconnect, device number 70
[   53.584051] usb 3-1: new full-speed USB device number 71 using uhci_hcd
[   54.076101] usb 3-1: USB disconnect, device number 71
[   54.316062] usb 3-1: new full-speed USB device number 72 using uhci_hcd
[   54.816093] usb 3-1: USB disconnect, device number 72
[   55.056041] usb 3-1: new full-speed USB device number 73 using uhci_hcd
[   55.556085] usb 3-1: USB disconnect, device number 73
[   55.852046] usb 3-1: new full-speed USB device number 74 using uhci_hcd
[   56.428039] usb 3-1: device not accepting address 74, error -71
[   56.484111] hub 3-0:1.0: unable to enumerate USB device on port 1
[   56.542615] type=1701 audit(1361355209.493:25): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=2613 comm="chrome" reason="seccomp" sig=0 syscall=4 compat=0 ip=0x7f26c45e3a05 code=0x50002
[   56.542628] type=1701 audit(1361355209.493:26): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=2613 comm="chrome" reason="seccomp" sig=0 syscall=4 compat=0 ip=0x7f26c45e3a05 code=0x50002
[   56.542639] type=1701 audit(1361355209.493:27): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=2613 comm="chrome" reason="seccomp" sig=0 syscall=4 compat=0 ip=0x7f26c45e3a05 code=0x50002
[   56.542649] type=1701 audit(1361355209.493:28): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=2613 comm="chrome" reason="seccomp" sig=0 syscall=4 compat=0 ip=0x7f26c45e3a05 code=0x50002
[   56.542659] type=1701 audit(1361355209.493:29): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=2613 comm="chrome" reason="seccomp" sig=0 syscall=4 compat=0 ip=0x7f26c45e3a05 code=0x50002
[   56.546329] type=1701 audit(1361355209.497:30): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=2619 comm="chrome" reason="seccomp" sig=0 syscall=4 compat=0 ip=0x7f26c45e3a05 code=0x50002
[   56.546342] type=1701 audit(1361355209.497:31): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=2619 comm="chrome" reason="seccomp" sig=0 syscall=4 compat=0 ip=0x7f26c45e3a05 code=0x50002
[   56.546352] type=1701 audit(1361355209.497:32): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=2619 comm="chrome" reason="seccomp" sig=0 syscall=4 compat=0 ip=0x7f26c45e3a05 code=0x50002
[   56.546363] type=1701 audit(1361355209.497:33): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=2619 comm="chrome" reason="seccomp" sig=0 syscall=4 compat=0 ip=0x7f26c45e3a05 code=0x50002
[   56.546373] type=1701 audit(1361355209.497:34): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=2619 comm="chrome" reason="seccomp" sig=0 syscall=4 compat=0 ip=0x7f26c45e3a05 code=0x50002
[   57.432042] usb 3-1: new full-speed USB device number 76 using uhci_hcd
[   57.952036] usb 3-1: device not accepting address 76, error -71
[   58.008078] hub 3-0:1.0: unable to enumerate USB device on port 1
[   58.248057] hub 1-0:1.0: unable to enumerate USB device on port 1
[   58.764038] usb 3-1: new full-speed USB device number 78 using uhci_hcd
[   59.264084] usb 3-1: USB disconnect, device number 78
[   59.504044] usb 3-1: new full-speed USB device number 79 using uhci_hcd
[   60.004083] usb 3-1: USB disconnect, device number 79
[   60.244041] usb 3-1: new full-speed USB device number 80 using uhci_hcd
[   60.748074] usb 3-1: USB disconnect, device number 80
[   60.988043] usb 3-1: new full-speed USB device number 81 using uhci_hcd
[   61.488086] usb 3-1: USB disconnect, device number 81
[   61.728093] usb 3-1: new full-speed USB device number 82 using uhci_hcd
[   62.228098] usb 3-1: USB disconnect, device number 82
[   62.468042] usb 3-1: new full-speed USB device number 83 using uhci_hcd
[   62.972081] usb 3-1: USB disconnect, device number 83
[   63.212050] usb 3-1: new full-speed USB device number 84 using uhci_hcd
[   63.712080] usb 3-1: USB disconnect, device number 84
[   63.952040] usb 3-1: new full-speed USB device number 85 using uhci_hcd
[   64.452072] usb 3-1: USB disconnect, device number 85
[   64.692046] usb 3-1: new full-speed USB device number 86 using uhci_hcd
[   65.192080] usb 3-1: USB disconnect, device number 86
[   65.432040] usb 3-1: new full-speed USB device number 87 using uhci_hcd
[   65.936086] usb 3-1: USB disconnect, device number 87
[   66.176035] usb 3-1: new full-speed USB device number 88 using uhci_hcd
[   66.676083] usb 3-1: USB disconnect, device number 88
[   66.916044] usb 3-1: new full-speed USB device number 89 using uhci_hcd
[   67.416075] usb 3-1: USB disconnect, device number 89
[   67.656038] usb 3-1: new full-speed USB device number 90 using uhci_hcd
[   68.160077] usb 3-1: USB disconnect, device number 90
[   68.400043] usb 3-1: new full-speed USB device number 91 using uhci_hcd
[   68.900079] usb 3-1: USB disconnect, device number 91
[   69.140044] usb 3-1: new full-speed USB device number 92 using uhci_hcd
[   69.640095] usb 3-1: USB disconnect, device number 92
[   69.880049] usb 3-1: new full-speed USB device number 93 using uhci_hcd
[   70.384096] usb 3-1: USB disconnect, device number 93
[   70.624048] usb 3-1: new full-speed USB device number 94 using uhci_hcd
[   71.124081] usb 3-1: USB disconnect, device number 94
[   71.364081] usb 3-1: new full-speed USB device number 95 using uhci_hcd
[   71.864085] usb 3-1: USB disconnect, device number 95
[   72.104038] usb 3-1: new full-speed USB device number 96 using uhci_hcd
[   72.320063] usb 3-1: USB disconnect, device number 96
[   73.056037] usb 3-1: new full-speed USB device number 97 using uhci_hcd
[   73.116069] hub 3-0:1.0: unable to enumerate USB device on port 1
[   73.652046] usb 3-1: new full-speed USB device number 98 using uhci_hcd
[   74.232041] usb 3-1: device not accepting address 98, error -71
[   74.288072] hub 3-0:1.0: unable to enumerate USB device on port 1
[   75.288042] usb 3-1: new full-speed USB device number 100 using uhci_hcd
[   75.352070] hub 3-0:1.0: unable to enumerate USB device on port 1
[   75.832034] usb 3-1: new full-speed USB device number 101 using uhci_hcd
[   76.040111] usb 3-1: USB disconnect, device number 101
[   76.776045] usb 3-1: new full-speed USB device number 102 using uhci_hcd
[   76.840074] hub 3-0:1.0: unable to enumerate USB device on port 1
[   77.320045] usb 3-1: new full-speed USB device number 103 using uhci_hcd
[   77.528065] usb 3-1: USB disconnect, device number 103
[   78.264033] usb 3-1: new full-speed USB device number 104 using uhci_hcd
[   78.328066] hub 3-0:1.0: unable to enumerate USB device on port 1
[   78.808039] usb 3-1: new full-speed USB device number 105 using uhci_hcd
[   79.016066] usb 3-1: USB disconnect, device number 105
[   79.752046] usb 3-1: new full-speed USB device number 106 using uhci_hcd
[   79.816084] hub 3-0:1.0: unable to enumerate USB device on port 1
[   80.296044] usb 3-1: new full-speed USB device number 107 using uhci_hcd
[   80.474272] usb 3-1: can't set config #1, error -84
[   80.504065] usb 3-1: USB disconnect, device number 107
[   81.240037] usb 3-1: new full-speed USB device number 108 using uhci_hcd
[   81.304072] hub 3-0:1.0: unable to enumerate USB device on port 1
[   81.784053] usb 3-1: new full-speed USB device number 109 using uhci_hcd
[   81.965310] usb 3-1: can't set config #1, error -71
[   81.992063] usb 3-1: USB disconnect, device number 109
[   82.728038] usb 3-1: new full-speed USB device number 110 using uhci_hcd
[   82.792068] hub 3-0:1.0: unable to enumerate USB device on port 1
[   83.272063] usb 3-1: new full-speed USB device number 111 using uhci_hcd
[   83.454353] usb 3-1: can't set config #1, error -71
[   83.480061] usb 3-1: USB disconnect, device number 111
[   84.216057] usb 3-1: new full-speed USB device number 112 using uhci_hcd
[   84.280083] hub 3-0:1.0: unable to enumerate USB device on port 1
[   84.760051] usb 3-1: new full-speed USB device number 113 using uhci_hcd
[   84.937776] usb 3-1: can't set config #1, error -71
[   84.969259] usb 3-1: USB disconnect, device number 113
[   85.704045] usb 3-1: new full-speed USB device number 114 using uhci_hcd
[   85.768065] hub 3-0:1.0: unable to enumerate USB device on port 1
[   86.248044] usb 3-1: new full-speed USB device number 115 using uhci_hcd
[   86.409428] usb 3-1: string descriptor 0 read error: -71
[   86.416115] usb 3-1: can't set config #1, error -71
[   86.692078] usb 3-1: USB disconnect, device number 115
[   86.932035] usb 3-1: new full-speed USB device number 116 using uhci_hcd
[   87.432085] usb 3-1: USB disconnect, device number 116
[   87.672043] usb 3-1: new full-speed USB device number 117 using uhci_hcd
[   88.172081] usb 3-1: USB disconnect, device number 117
[   88.412037] usb 3-1: new full-speed USB device number 118 using uhci_hcd
[   88.912075] usb 3-1: USB disconnect, device number 118
[   89.152050] usb 3-1: new full-speed USB device number 119 using uhci_hcd
[   89.652082] usb 3-1: USB disconnect, device number 119
[   89.892035] usb 3-1: new full-speed USB device number 120 using uhci_hcd
[   90.396080] usb 3-1: USB disconnect, device number 120
[   90.636042] usb 3-1: new full-speed USB device number 121 using uhci_hcd
[   91.136094] usb 3-1: USB disconnect, device number 121
[   91.376037] usb 3-1: new full-speed USB device number 122 using uhci_hcd
[   91.876085] usb 3-1: USB disconnect, device number 122
[   92.116041] usb 3-1: new full-speed USB device number 123 using uhci_hcd
[   92.620084] usb 3-1: USB disconnect, device number 123
[   92.860048] usb 3-1: new full-speed USB device number 124 using uhci_hcd
[   93.360089] usb 3-1: USB disconnect, device number 124
[   93.600039] usb 3-1: new full-speed USB device number 125 using uhci_hcd
[   94.100082] usb 3-1: USB disconnect, device number 125
[   94.340060] usb 3-1: new full-speed USB device number 126 using uhci_hcd
[   94.844093] usb 3-1: USB disconnect, device number 126
[   95.084063] usb 3-1: new full-speed USB device number 127 using uhci_hcd
[   95.588101] usb 3-1: USB disconnect, device number 127
[   95.828045] usb 3-1: new full-speed USB device number 3 using uhci_hcd
[   96.324091] usb 3-1: USB disconnect, device number 3
[   96.564051] usb 3-1: new full-speed USB device number 4 using uhci_hcd
[   97.064099] usb 3-1: USB disconnect, device number 4
[   97.304058] usb 3-1: new full-speed USB device number 5 using uhci_hcd
[   97.808109] usb 3-1: USB disconnect, device number 5
[   98.048071] usb 3-1: new full-speed USB device number 6 using uhci_hcd
[   98.548085] usb 3-1: USB disconnect, device number 6
[   98.788048] usb 3-1: new full-speed USB device number 7 using uhci_hcd
[   99.288093] usb 3-1: USB disconnect, device number 7
[   99.528050] usb 3-1: new full-speed USB device number 8 using uhci_hcd
[  100.032087] usb 3-1: USB disconnect, device number 8
[  100.272059] usb 3-1: new full-speed USB device number 9 using uhci_hcd
[  100.772084] usb 3-1: USB disconnect, device number 9
[  101.012057] usb 3-1: new full-speed USB device number 10 using uhci_hcd
[  101.512084] usb 3-1: USB disconnect, device number 10
[  101.752059] usb 3-1: new full-speed USB device number 11 using uhci_hcd
[  102.256098] usb 3-1: USB disconnect, device number 11
[  102.496043] usb 3-1: new full-speed USB device number 12 using uhci_hcd
[  102.996097] usb 3-1: USB disconnect, device number 12
[  103.236054] usb 3-1: new full-speed USB device number 13 using uhci_hcd
[  103.736086] usb 3-1: USB disconnect, device number 13
[  103.976053] usb 3-1: new full-speed USB device number 14 using uhci_hcd
[  104.476072] usb 3-1: USB disconnect, device number 14
[  104.716066] usb 3-1: new full-speed USB device number 15 using uhci_hcd
[  105.220088] usb 3-1: USB disconnect, device number 15
[  105.460071] usb 3-1: new full-speed USB device number 16 using uhci_hcd
[  105.960105] usb 3-1: USB disconnect, device number 16
[  106.200044] usb 3-1: new full-speed USB device number 17 using uhci_hcd
[  106.700089] usb 3-1: USB disconnect, device number 17
[  106.940060] usb 3-1: new full-speed USB device number 18 using uhci_hcd
[  107.444090] usb 3-1: USB disconnect, device number 18
[  107.684049] usb 3-1: new full-speed USB device number 19 using uhci_hcd
[  108.184089] usb 3-1: USB disconnect, device number 19
[  108.424036] usb 3-1: new full-speed USB device number 20 using uhci_hcd
[  108.924071] usb 3-1: USB disconnect, device number 20
[  109.164052] usb 3-1: new full-speed USB device number 21 using uhci_hcd
[  109.668089] usb 3-1: USB disconnect, device number 21
[  109.964045] usb 3-1: new full-speed USB device number 22 using uhci_hcd
[  110.139270] usb 3-1: can't set config #1, error -71
[  110.408082] usb 3-1: USB disconnect, device number 22
[  110.648049] usb 3-1: new full-speed USB device number 23 using uhci_hcd
[  111.148086] usb 3-1: USB disconnect, device number 23
[  111.388082] usb 3-1: new full-speed USB device number 24 using uhci_hcd
[  111.892094] usb 3-1: USB disconnect, device number 24
[  112.132048] usb 3-1: new full-speed USB device number 25 using uhci_hcd
[  112.632087] usb 3-1: USB disconnect, device number 25
[  112.872049] usb 3-1: new full-speed USB device number 26 using uhci_hcd
[  113.372085] usb 3-1: USB disconnect, device number 26
[  113.612037] usb 3-1: new full-speed USB device number 27 using uhci_hcd
[  114.112082] usb 3-1: USB disconnect, device number 27
[  114.352053] usb 3-1: new full-speed USB device number 28 using uhci_hcd
[  114.856088] usb 3-1: USB disconnect, device number 28
[  115.096052] usb 3-1: new full-speed USB device number 29 using uhci_hcd
[  115.596090] usb 3-1: USB disconnect, device number 29
[  115.836085] usb 3-1: new full-speed USB device number 30 using uhci_hcd

```

---

