---
title: "[Headless] Ubuntu keeps resetting at boot"
date: 2013-03-20
forum: General Help
---

### Post by TheForumTroll on 2013-03-20
My headless Ubuntu server keeps resetting at boot, like 4 out of 5 times, but when it does boot, it is stable - also under full load. I have tried to re-install with no change. I can't find any hardware faults, but of course that doesn't mean that there aren't any that is only triggered at boot...

Here are the last three dmesg logs:

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.5.0-22-generic (buildd@komainu) (gcc version 4.7.2 (Ubuntu/Linaro 4.7.2-2ubuntu1) ) #34-Ubuntu SMP Tue Jan 8 21:47:00 UTC 2013 (Ubuntu 3.5.0-22.34-generic 3.5.7.2)
[    0.000000] Command line: BOOT_IMAGE=/vmlinuz-3.5.0-22-generic root=UUID=ff204e15-e503-4ac9-aef0-28a8513a8e7c ro
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] Disabled fast string operations
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000008efff] usable
[    0.000000] BIOS-e820: [mem 0x000000000008f000-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000007f526fff] usable
[    0.000000] BIOS-e820: [mem 0x000000007f527000-0x000000007f52efff] reserved
[    0.000000] BIOS-e820: [mem 0x000000007f52f000-0x000000007f5befff] usable
[    0.000000] BIOS-e820: [mem 0x000000007f5bf000-0x000000007f5c2fff] reserved
[    0.000000] BIOS-e820: [mem 0x000000007f5c3000-0x000000007f65ffff] usable
[    0.000000] BIOS-e820: [mem 0x000000007f660000-0x000000007f6effff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000007f6f0000-0x000000007f6f1fff] usable
[    0.000000] BIOS-e820: [mem 0x000000007f6f2000-0x000000007f6fefff] ACPI data
[    0.000000] BIOS-e820: [mem 0x000000007f6ff000-0x000000007f6fffff] usable
[    0.000000] BIOS-e820: [mem 0x000000007f700000-0x000000007fffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000f0000000-0x00000000ffffffff] reserved
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.4 present.
[    0.000000] DMI:                  /D945GCLF2, BIOS LF94510J.86A.0171.2009.0403.0118 04/03/2009
[    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x7f700 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-DFFFF uncachable
[    0.000000]   E0000-E0FFF write-protect
[    0.000000]   E1000-E7FFF uncachable
[    0.000000]   E8000-E8FFF write-protect
[    0.000000]   E9000-EFFFF uncachable
[    0.000000]   F0000-F0FFF write-protect
[    0.000000]   F1000-F7FFF uncachable
[    0.000000]   F8000-F8FFF write-protect
[    0.000000]   F9000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask 080000000 write-back
[    0.000000]   1 base 07F800000 mask 0FF800000 uncachable
[    0.000000]   2 base 07F700000 mask 0FFF00000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2040MB, range: 8MB, type UC
[    0.000000] reg 2, base: 2039MB, range: 1MB, type UC
[    0.000000] total RAM covered: 2039M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K 	chunk_size: 16M 	num_reg: 3  	lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2039MB, range: 1MB, type UC
[    0.000000] reg 2, base: 2040MB, range: 8MB, type UC
[    0.000000] found SMP MP-table at [mem 0x000fe200-0x000fe20f] mapped at [ffff8800000fe200]
[    0.000000] initial memory mapped: [mem 0x00000000-0x1fffffff]
[    0.000000] Base memory trampoline at [ffff880000089000] 89000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0x7f6fffff]
[    0.000000]  [mem 0x00000000-0x7f5fffff] page 2M
[    0.000000]  [mem 0x7f600000-0x7f6fffff] page 4k
[    0.000000] kernel direct mapping tables up to 0x7f6fffff @ [mem 0x1fffc000-0x1fffffff]
[    0.000000] RAMDISK: [mem 0x362e2000-0x37168fff]
[    0.000000] ACPI: RSDP 00000000000fe020 00014 (v00 INTEL )
[    0.000000] ACPI: RSDT 000000007f6fd038 0003C (v01 INTEL  D945GLF2 000000AB      01000013)
[    0.000000] ACPI: FACP 000000007f6fc000 00074 (v01 INTEL  D945GLF2 000000AB MSFT 01000013)
[    0.000000] ACPI: DSDT 000000007f6f7000 045EC (v01 INTEL  D945GLF2 000000AB MSFT 01000013)
[    0.000000] ACPI: FACS 000000007f6a3000 00040
[    0.000000] ACPI: APIC 000000007f6f6000 00078 (v01 INTEL  D945GLF2 000000AB MSFT 01000013)
[    0.000000] ACPI: WDDT 000000007f6f5000 00040 (v01 INTEL  D945GLF2 000000AB MSFT 01000013)
[    0.000000] ACPI: MCFG 000000007f6f4000 0003C (v01 INTEL  D945GLF2 000000AB MSFT 01000013)
[    0.000000] ACPI: ASF! 000000007f6f3000 000A6 (v32 INTEL  D945GLF2 000000AB MSFT 01000013)
[    0.000000] ACPI: HPET 000000007f6f2000 00038 (v01 INTEL  D945GLF2 000000AB MSFT 01000013)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000007f6fffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x7f6fffff]
[    0.000000]   NODE_DATA [mem 0x7f65c000-0x7f65ffff]
[    0.000000]  [ffffea0000000000-ffffea0001ffffff] PMD -> [ffff88007cc00000-ffff88007ebfffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00010000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   empty
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00010000-0x0008efff]
[    0.000000]   node   0: [mem 0x00100000-0x7f526fff]
[    0.000000]   node   0: [mem 0x7f52f000-0x7f5befff]
[    0.000000]   node   0: [mem 0x7f5c3000-0x7f65ffff]
[    0.000000]   node   0: [mem 0x7f6f0000-0x7f6f1fff]
[    0.000000]   node   0: [mem 0x7f6ff000-0x7f6fffff]
[    0.000000] On node 0 totalpages: 521686
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 6 pages reserved
[    0.000000]   DMA zone: 3897 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 8092 pages used for memmap
[    0.000000]   DMA32 zone: 509627 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000008f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 000000007f527000 - 000000007f52f000
[    0.000000] PM: Registered nosave memory: 000000007f5bf000 - 000000007f5c3000
[    0.000000] PM: Registered nosave memory: 000000007f660000 - 000000007f6f0000
[    0.000000] PM: Registered nosave memory: 000000007f6f2000 - 000000007f6ff000
[    0.000000] e820: [mem 0x80000000-0xefffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88007f200000 s83584 r8192 d22912 u524288
[    0.000000] pcpu-alloc: s83584 r8192 d22912 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 513524
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-3.5.0-22-generic root=UUID=ff204e15-e503-4ac9-aef0-28a8513a8e7c ro
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] __ex_table already sorted, skipping sort
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 2022804k/2087936k available (6719k kernel code, 1192k absent, 63940k reserved, 6451k data, 932k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:712 16
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 8388608 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1595.957 MHz processor.
[    0.004009] Calibrating delay loop (skipped), value calculated using timer frequency.. 3191.91 BogoMIPS (lpj=6383828)
[    0.004033] pid_max: default: 32768 minimum: 301
[    0.004115] Security Framework initialized
[    0.004168] AppArmor: AppArmor initialized
[    0.004178] Yama: becoming mindful.
[    0.004723] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.006800] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.008687] Mount-cache hash table entries: 256
[    0.009275] Initializing cgroup subsys cpuacct
[    0.009297] Initializing cgroup subsys memory
[    0.009328] Initializing cgroup subsys devices
[    0.009340] Initializing cgroup subsys freezer
[    0.009350] Initializing cgroup subsys blkio
[    0.009361] Initializing cgroup subsys perf_event
[    0.009439] Disabled fast string operations
[    0.009456] CPU: Physical Processor ID: 0
[    0.009465] CPU: Processor Core ID: 0
[    0.009474] mce: CPU supports 5 MCE banks
[    0.009495] CPU0: Thermal monitoring enabled (TM1)
[    0.009510] using mwait in idle threads.
[    0.012656] ACPI: Core revision 20120320
[    0.020031] ftrace: allocating 25143 entries in 99 pages
[    0.040404] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.080121] CPU0: Intel(R) Atom(TM) CPU  330   @ 1.60GHz stepping 02
[    0.084004] APIC calibration not consistent with PM-Timer: 103ms instead of 100ms
[    0.084004] APIC delta adjusted to PM-Timer: 831251 (864490)
[    0.084004] Performance Events: PEBS fmt0+, LBR disabled due to erratumAtom events, Intel PMU driver.
[    0.084004] ... version:                3
[    0.084004] ... bit width:              40
[    0.084004] ... generic registers:      2
[    0.084004] ... value mask:             000000ffffffffff
[    0.084004] ... max period:             000000007fffffff
[    0.084004] ... fixed-purpose events:   3
[    0.084004] ... event mask:             0000000700000003
[    0.084004] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.008000] Disabled fast string operations
[    0.084004] Booting Node   0, Processors  #1
[    0.094190] TSC synchronization [CPU#0 -> CPU#1]:
[    0.094209] Measured 108 cycles TSC warp between CPUs, turning off TSC clock.
[    0.094218] Marking TSC unstable due to check_tsc_sync_source failed
[    0.008000] Disabled fast string operations
[    0.094577]  #2 #3 Ok.
[    0.008000] Disabled fast string operations
[    0.117168] Brought up 4 CPUs
[    0.117188] Total of 4 processors activated (12767.65 BogoMIPS).
[    0.119080] devtmpfs: initialized
[    0.123577] EVM: security.selinux
[    0.123589] EVM: security.SMACK64
[    0.123596] EVM: security.capability
[    0.123650] PM: Registering ACPI NVS region [mem 0x7f660000-0x7f6effff] (589824 bytes)
[    0.126263] dummy: 
[    0.126328] RTC time: 13:59:16, date: 02/06/13
[    0.126448] NET: Registered protocol family 16
[    0.126491] Trying to unpack rootfs image as initramfs...
[    0.127172] ACPI: bus type pci registered
[    0.127413] PCI: MMCONFIG for domain 0000 [bus 00-7f] at [mem 0xf0000000-0xf7ffffff] (base 0xf0000000)
[    0.127437] PCI: MMCONFIG at [mem 0xf0000000-0xf7ffffff] reserved in E820
[    0.152420] PCI: Using configuration type 1 for base access
[    0.156835] bio: create slab <bio-0> at 0
[    0.157652] ACPI: Added _OSI(Module Device)
[    0.157652] ACPI: Added _OSI(Processor Device)
[    0.157652] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.157652] ACPI: Added _OSI(Processor Aggregator Device)
[    0.162339] ACPI: EC: Look up EC in DSDT
[    0.168767] ACPI: Interpreter enabled
[    0.168799] ACPI: (supports S0 S1 S3 S4 S5)
[    0.168904] ACPI: Using IOAPIC for interrupt routing
[    0.182830] ACPI: No dock devices found.
[    0.182862] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.185616] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.190771] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
[    0.190799] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
[    0.190817] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.190836] pci_root PNP0A03:00: host bridge window [mem 0x000e0000-0x000effff]
[    0.190856] pci_root PNP0A03:00: host bridge window [mem 0xf8000000-0xfebfffff]
[    0.190875] pci_root PNP0A03:00: host bridge window [mem 0x80000000-0xf0000000]
[    0.191043] PCI host bridge to bus 0000:00
[    0.191062] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.191079] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.191096] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.191113] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000effff]
[    0.191130] pci_bus 0000:00: root bus resource [mem 0xf8000000-0xfebfffff]
[    0.191148] pci_bus 0000:00: root bus resource [mem 0x80000000-0xf0000000]
[    0.191192] pci 0000:00:00.0: [8086:2770] type 00 class 0x060000
[    0.191293] pci 0000:00:02.0: [8086:2772] type 00 class 0x030000
[    0.191323] pci 0000:00:02.0: reg 10: [mem 0x88300000-0x8837ffff]
[    0.191342] pci 0000:00:02.0: reg 14: [io  0x30e0-0x30e7]
[    0.191360] pci 0000:00:02.0: reg 18: [mem 0x80000000-0x87ffffff pref]
[    0.191380] pci 0000:00:02.0: reg 1c: [mem 0x88380000-0x8839ffff]
[    0.191506] pci 0000:00:1c.0: [8086:27d0] type 01 class 0x060400
[    0.191620] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.191669] pci 0000:00:1c.2: [8086:27d4] type 01 class 0x060400
[    0.191780] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.191837] pci 0000:00:1c.3: [8086:27d6] type 01 class 0x060400
[    0.191960] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.192061] pci 0000:00:1d.0: [8086:27c8] type 00 class 0x0c0300
[    0.192129] pci 0000:00:1d.0: reg 20: [io  0x3080-0x309f]
[    0.192192] pci 0000:00:1d.1: [8086:27c9] type 00 class 0x0c0300
[    0.192253] pci 0000:00:1d.1: reg 20: [io  0x3060-0x307f]
[    0.192314] pci 0000:00:1d.2: [8086:27ca] type 00 class 0x0c0300
[    0.192375] pci 0000:00:1d.2: reg 20: [io  0x3040-0x305f]
[    0.192435] pci 0000:00:1d.3: [8086:27cb] type 00 class 0x0c0300
[    0.192496] pci 0000:00:1d.3: reg 20: [io  0x3020-0x303f]
[    0.192568] pci 0000:00:1d.7: [8086:27cc] type 00 class 0x0c0320
[    0.192601] pci 0000:00:1d.7: reg 10: [mem 0x883a0000-0x883a03ff]
[    0.192729] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.192772] pci 0000:00:1e.0: [8086:244e] type 01 class 0x060401
[    0.192879] pci 0000:00:1f.0: [8086:27b8] type 00 class 0x060100
[    0.192994] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0680 (mask 007f)
[    0.193094] pci 0000:00:1f.1: [8086:27df] type 00 class 0x01018a
[    0.193120] pci 0000:00:1f.1: reg 10: [io  0x30d8-0x30df]
[    0.193141] pci 0000:00:1f.1: reg 14: [io  0x30f4-0x30f7]
[    0.193165] pci 0000:00:1f.1: reg 18: [io  0x30d0-0x30d7]
[    0.193187] pci 0000:00:1f.1: reg 1c: [io  0x30f0-0x30f3]
[    0.193208] pci 0000:00:1f.1: reg 20: [io  0x30b0-0x30bf]
[    0.193285] pci 0000:00:1f.2: [8086:27c0] type 00 class 0x01018f
[    0.193315] pci 0000:00:1f.2: reg 10: [io  0x30c8-0x30cf]
[    0.193333] pci 0000:00:1f.2: reg 14: [io  0x30ec-0x30ef]
[    0.193350] pci 0000:00:1f.2: reg 18: [io  0x30c0-0x30c7]
[    0.193366] pci 0000:00:1f.2: reg 1c: [io  0x30e8-0x30eb]
[    0.193383] pci 0000:00:1f.2: reg 20: [io  0x30a0-0x30af]
[    0.193444] pci 0000:00:1f.2: PME# supported from D3hot
[    0.193479] pci 0000:00:1f.3: [8086:27da] type 00 class 0x0c0500
[    0.193552] pci 0000:00:1f.3: reg 20: [io  0x3000-0x301f]
[    0.193706] pci 0000:01:00.0: [10ec:8168] type 00 class 0x020000
[    0.193736] pci 0000:01:00.0: reg 10: [io  0x2000-0x20ff]
[    0.193780] pci 0000:01:00.0: reg 18: [mem 0x88200000-0x88200fff 64bit]
[    0.193810] pci 0000:01:00.0: reg 20: [mem 0x88000000-0x8800ffff 64bit pref]
[    0.193832] pci 0000:01:00.0: reg 30: [mem 0xfffe0000-0xffffffff pref]
[    0.193925] pci 0000:01:00.0: supports D1 D2
[    0.193934] pci 0000:01:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.200092] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    0.200125] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.200137] pci 0000:00:1c.0:   bridge window [mem 0x88200000-0x882fffff]
[    0.200151] pci 0000:00:1c.0:   bridge window [mem 0x88000000-0x880fffff 64bit pref]
[    0.200228] pci 0000:00:1c.2: PCI bridge to [bus 02-02]
[    0.200315] pci 0000:00:1c.3: PCI bridge to [bus 03-03]
[    0.200398] pci 0000:04:00.0: [105a:3570] type 00 class 0x010400
[    0.200438] pci 0000:04:00.0: reg 10: [io  0x1400-0x147f]
[    0.200474] pci 0000:04:00.0: reg 18: [io  0x1000-0x10ff]
[    0.200496] pci 0000:04:00.0: reg 1c: [mem 0x88120000-0x88120fff]
[    0.200516] pci 0000:04:00.0: reg 20: [mem 0x88100000-0x8811ffff]
[    0.200546] pci 0000:04:00.0: reg 30: [mem 0xffff0000-0xffffffff pref]
[    0.200600] pci 0000:04:00.0: supports D1
[    0.200673] pci 0000:00:1e.0: PCI bridge to [bus 04-04] (subtractive decode)
[    0.200696] pci 0000:00:1e.0:   bridge window [io  0x1000-0x1fff]
[    0.200706] pci 0000:00:1e.0:   bridge window [mem 0x88100000-0x881fffff]
[    0.200721] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.200729] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.200738] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.200747] pci 0000:00:1e.0:   bridge window [mem 0x000e0000-0x000effff] (subtractive decode)
[    0.200755] pci 0000:00:1e.0:   bridge window [mem 0xf8000000-0xfebfffff] (subtractive decode)
[    0.200764] pci 0000:00:1e.0:   bridge window [mem 0x80000000-0xf0000000] (subtractive decode)
[    0.200812] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.201332] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P32_._PRT]
[    0.201893] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    0.202070] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX2._PRT]
[    0.202227] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX3._PRT]
[    0.202544]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.202571]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.202589] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.215557] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
[    0.215829] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.216115] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12)
[    0.216360] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 *10 11 12)
[    0.216602] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.216866] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 *9 10 11 12)
[    0.217097] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.217346] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 *9 10 11 12)
[    0.217715] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.217715] vgaarb: loaded
[    0.217715] vgaarb: bridge control possible 0000:00:02.0
[    0.217715] SCSI subsystem initialized
[    0.217715] libata version 3.00 loaded.
[    0.217715] ACPI: bus type usb registered
[    0.217715] usbcore: registered new interface driver usbfs
[    0.217715] usbcore: registered new interface driver hub
[    0.217715] usbcore: registered new device driver usb
[    0.217715] PCI: Using ACPI for IRQ routing
[    0.223699] PCI: pci_cache_line_size set to 64 bytes
[    0.223851] Expanded resource reserved due to conflict with PCI Bus 0000:00
[    0.223873] e820: reserve RAM buffer [mem 0x0008f000-0x0008ffff]
[    0.223881] e820: reserve RAM buffer [mem 0x7f527000-0x7fffffff]
[    0.223890] e820: reserve RAM buffer [mem 0x7f5bf000-0x7fffffff]
[    0.223897] e820: reserve RAM buffer [mem 0x7f660000-0x7fffffff]
[    0.223904] e820: reserve RAM buffer [mem 0x7f6f2000-0x7fffffff]
[    0.223911] e820: reserve RAM buffer [mem 0x7f700000-0x7fffffff]
[    0.224357] NetLabel: Initializing
[    0.224376] NetLabel:  domain hash size = 128
[    0.224386] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.224437] NetLabel:  unlabeled traffic allowed by default
[    0.224544] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.224544] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.224544] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.236123] Switching to clocksource hpet
[    0.263189] AppArmor: AppArmor Filesystem Enabled
[    0.263314] pnp: PnP ACPI init
[    0.263368] ACPI: bus type pnp registered
[    0.265252] pnp 00:00: [bus 00-ff]
[    0.265261] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.265268] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.265274] pnp 00:00: [io  0x0d00-0xffff window]
[    0.265280] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.265287] pnp 00:00: [mem 0x000e0000-0x000effff window]
[    0.265293] pnp 00:00: [mem 0xf8000000-0xfebfffff window]
[    0.265299] pnp 00:00: [mem 0x80000000-0xf0000000 window]
[    0.265420] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.265459] pnp 00:01: [mem 0xf0000000-0xf3ffffff]
[    0.265465] pnp 00:01: [mem 0xfed13000-0xfed13fff]
[    0.265471] pnp 00:01: [mem 0xfed14000-0xfed17fff]
[    0.265476] pnp 00:01: [mem 0xfed18000-0xfed18fff]
[    0.265482] pnp 00:01: [mem 0xfed19000-0xfed19fff]
[    0.265487] pnp 00:01: [mem 0xfed1c000-0xfed1ffff]
[    0.265493] pnp 00:01: [mem 0xfed20000-0xfed3ffff]
[    0.265499] pnp 00:01: [mem 0xfed45000-0xfed99fff]
[    0.265504] pnp 00:01: [mem 0x000c0000-0x000dffff]
[    0.265510] pnp 00:01: [mem 0x000e0000-0x000fffff]
[    0.265649] system 00:01: [mem 0xf0000000-0xf3ffffff] could not be reserved
[    0.265669] system 00:01: [mem 0xfed13000-0xfed13fff] has been reserved
[    0.265682] system 00:01: [mem 0xfed14000-0xfed17fff] has been reserved
[    0.265694] system 00:01: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.265706] system 00:01: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.265719] system 00:01: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.265738] system 00:01: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.265752] system 00:01: [mem 0xfed45000-0xfed99fff] has been reserved
[    0.265764] system 00:01: [mem 0x000c0000-0x000dffff] could not be reserved
[    0.265777] system 00:01: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.265793] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.266142] pnp 00:02: [io  0x0000-0x000f]
[    0.266150] pnp 00:02: [io  0x0081-0x0083]
[    0.266156] pnp 00:02: [io  0x0087]
[    0.266170] pnp 00:02: [io  0x0089-0x008b]
[    0.266175] pnp 00:02: [io  0x008f]
[    0.266181] pnp 00:02: [io  0x00c0-0x00df]
[    0.266187] pnp 00:02: [dma 4]
[    0.266266] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.266299] pnp 00:03: [io  0x0070-0x0071]
[    0.266305] pnp 00:03: [io  0x0074-0x0077]
[    0.266332] pnp 00:03: [irq 8]
[    0.266401] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.266436] pnp 00:04: [io  0x00f0]
[    0.266452] pnp 00:04: [irq 13]
[    0.266530] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.266565] pnp 00:05: [io  0x0061]
[    0.266636] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.266670] pnp 00:06: [io  0x0500-0x053f]
[    0.266677] pnp 00:06: [io  0x0400-0x047f]
[    0.266682] pnp 00:06: [io  0x0092]
[    0.266687] pnp 00:06: [io  0x0680-0x06ff]
[    0.266693] pnp 00:06: [io  0x0010-0x001f]
[    0.266698] pnp 00:06: [io  0x0072-0x0073]
[    0.266703] pnp 00:06: [io  0x0080]
[    0.266708] pnp 00:06: [io  0x0084-0x0086]
[    0.266714] pnp 00:06: [io  0x0088]
[    0.266719] pnp 00:06: [io  0x008c-0x008e]
[    0.266724] pnp 00:06: [io  0x0090-0x009f]
[    0.266850] system 00:06: [io  0x0500-0x053f] has been reserved
[    0.266866] system 00:06: [io  0x0400-0x047f] has been reserved
[    0.266878] system 00:06: [io  0x0680-0x06ff] has been reserved
[    0.266894] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.267020] pnp 00:07: [io  0x0060]
[    0.267027] pnp 00:07: [io  0x0064]
[    0.267133] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.267551] pnp 00:08: [io  0x03f0-0x03f5]
[    0.267558] pnp 00:08: [io  0x03f0]
[    0.267576] pnp 00:08: [irq 6]
[    0.267582] pnp 00:08: [dma 2]
[    0.267730] pnp 00:08: Plug and Play ACPI device, IDs PNP0700 (active)
[    0.268361] pnp 00:09: [mem 0xfec00000-0xfec000ff]
[    0.268446] pnp 00:09: Plug and Play ACPI device, IDs PNP0003 (active)
[    0.268511] pnp 00:0a: [mem 0xfed00000-0xfed003ff]
[    0.268608] pnp 00:0a: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.268699] pnp: PnP ACPI: found 11 devices
[    0.268710] ACPI: ACPI bus type pnp unregistered
[    0.280109] pci 0000:01:00.0: no compatible bridge window for [mem 0xfffe0000-0xffffffff pref]
[    0.280138] pci 0000:04:00.0: no compatible bridge window for [mem 0xffff0000-0xffffffff pref]
[    0.280208] pci 0000:00:1c.2: bridge window [io  0x1000-0x0fff] to [bus 02-02] add_size 1000
[    0.280219] pci 0000:00:1c.2: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 02-02] add_size 200000
[    0.280227] pci 0000:00:1c.2: bridge window [mem 0x00100000-0x000fffff] to [bus 02-02] add_size 200000
[    0.280242] pci 0000:00:1c.3: bridge window [io  0x1000-0x0fff] to [bus 03-03] add_size 1000
[    0.280250] pci 0000:00:1c.3: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 03-03] add_size 200000
[    0.280258] pci 0000:00:1c.3: bridge window [mem 0x00100000-0x000fffff] to [bus 03-03] add_size 200000
[    0.280295] pci 0000:00:1c.2: res[14]=[mem 0x00100000-0x000fffff] get_res_add_size add_size 200000
[    0.280302] pci 0000:00:1c.2: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.280309] pci 0000:00:1c.3: res[14]=[mem 0x00100000-0x000fffff] get_res_add_size add_size 200000
[    0.280317] pci 0000:00:1c.3: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.280324] pci 0000:00:1c.2: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.280331] pci 0000:00:1c.3: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.280345] pci 0000:00:1c.2: BAR 14: assigned [mem 0x88400000-0x885fffff]
[    0.280363] pci 0000:00:1c.2: BAR 15: assigned [mem 0x88600000-0x887fffff 64bit pref]
[    0.280379] pci 0000:00:1c.3: BAR 14: assigned [mem 0x88800000-0x889fffff]
[    0.280394] pci 0000:00:1c.3: BAR 15: assigned [mem 0x88a00000-0x88bfffff 64bit pref]
[    0.280411] pci 0000:00:1e.0: BAR 15: assigned [mem 0x88c00000-0x88cfffff pref]
[    0.280428] pci 0000:00:1c.2: BAR 13: assigned [io  0x4000-0x4fff]
[    0.280442] pci 0000:00:1c.3: BAR 13: assigned [io  0x5000-0x5fff]
[    0.280458] pci 0000:01:00.0: BAR 6: assigned [mem 0x88020000-0x8803ffff pref]
[    0.280474] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    0.280487] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.280502] pci 0000:00:1c.0:   bridge window [mem 0x88200000-0x882fffff]
[    0.280516] pci 0000:00:1c.0:   bridge window [mem 0x88000000-0x880fffff 64bit pref]
[    0.280534] pci 0000:00:1c.2: PCI bridge to [bus 02-02]
[    0.280546] pci 0000:00:1c.2:   bridge window [io  0x4000-0x4fff]
[    0.280560] pci 0000:00:1c.2:   bridge window [mem 0x88400000-0x885fffff]
[    0.280574] pci 0000:00:1c.2:   bridge window [mem 0x88600000-0x887fffff 64bit pref]
[    0.280592] pci 0000:00:1c.3: PCI bridge to [bus 03-03]
[    0.280603] pci 0000:00:1c.3:   bridge window [io  0x5000-0x5fff]
[    0.280618] pci 0000:00:1c.3:   bridge window [mem 0x88800000-0x889fffff]
[    0.280632] pci 0000:00:1c.3:   bridge window [mem 0x88a00000-0x88bfffff 64bit pref]
[    0.280653] pci 0000:04:00.0: BAR 6: assigned [mem 0x88c00000-0x88c0ffff pref]
[    0.280667] pci 0000:00:1e.0: PCI bridge to [bus 04-04]
[    0.280679] pci 0000:00:1e.0:   bridge window [io  0x1000-0x1fff]
[    0.280694] pci 0000:00:1e.0:   bridge window [mem 0x88100000-0x881fffff]
[    0.280708] pci 0000:00:1e.0:   bridge window [mem 0x88c00000-0x88cfffff pref]
[    0.280816] pci 0000:00:1e.0: setting latency timer to 64
[    0.280826] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.280832] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.280839] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.280845] pci_bus 0000:00: resource 7 [mem 0x000e0000-0x000effff]
[    0.280851] pci_bus 0000:00: resource 8 [mem 0xf8000000-0xfebfffff]
[    0.280857] pci_bus 0000:00: resource 9 [mem 0x80000000-0xf0000000]
[    0.280864] pci_bus 0000:01: resource 0 [io  0x2000-0x2fff]
[    0.280870] pci_bus 0000:01: resource 1 [mem 0x88200000-0x882fffff]
[    0.280877] pci_bus 0000:01: resource 2 [mem 0x88000000-0x880fffff 64bit pref]
[    0.280883] pci_bus 0000:02: resource 0 [io  0x4000-0x4fff]
[    0.280889] pci_bus 0000:02: resource 1 [mem 0x88400000-0x885fffff]
[    0.280896] pci_bus 0000:02: resource 2 [mem 0x88600000-0x887fffff 64bit pref]
[    0.280902] pci_bus 0000:03: resource 0 [io  0x5000-0x5fff]
[    0.280908] pci_bus 0000:03: resource 1 [mem 0x88800000-0x889fffff]
[    0.280914] pci_bus 0000:03: resource 2 [mem 0x88a00000-0x88bfffff 64bit pref]
[    0.280921] pci_bus 0000:04: resource 0 [io  0x1000-0x1fff]
[    0.280927] pci_bus 0000:04: resource 1 [mem 0x88100000-0x881fffff]
[    0.280933] pci_bus 0000:04: resource 2 [mem 0x88c00000-0x88cfffff pref]
[    0.280939] pci_bus 0000:04: resource 4 [io  0x0000-0x0cf7]
[    0.280945] pci_bus 0000:04: resource 5 [io  0x0d00-0xffff]
[    0.280951] pci_bus 0000:04: resource 6 [mem 0x000a0000-0x000bffff]
[    0.280957] pci_bus 0000:04: resource 7 [mem 0x000e0000-0x000effff]
[    0.280963] pci_bus 0000:04: resource 8 [mem 0xf8000000-0xfebfffff]
[    0.280970] pci_bus 0000:04: resource 9 [mem 0x80000000-0xf0000000]
[    0.281070] NET: Registered protocol family 2
[    0.281318] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.282983] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.287146] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.288253] TCP: Hash tables configured (established 262144 bind 65536)
[    0.288274] TCP: reno registered
[    0.288324] UDP hash table entries: 1024 (order: 3, 32768 bytes)
[    0.288372] UDP-Lite hash table entries: 1024 (order: 3, 32768 bytes)
[    0.288612] NET: Registered protocol family 1
[    0.288704] pci 0000:00:02.0: Boot video device
[    0.289079] PCI: CLS mismatch (64 != 4), using 64 bytes
[    0.290441] audit: initializing netlink socket (disabled)
[    0.290490] type=2000 audit(1360159156.288:1): initialized
[    0.334641] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.339526] VFS: Disk quotas dquot_6.5.2
[    0.339669] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.341263] fuse init (API version 7.19)
[    0.341539] msgmni has been set to 3950
[    0.342928] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.343042] io scheduler noop registered
[    0.343055] io scheduler deadline registered (default)
[    0.343143] io scheduler cfq registered
[    0.343486] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.343671] pcieport 0000:00:1c.2: irq 41 for MSI/MSI-X
[    0.343832] pcieport 0000:00:1c.3: irq 42 for MSI/MSI-X
[    0.344001] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.344133] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.344341] intel_idle: MWAIT substates: 0x10
[    0.344371] intel_idle: v0.4 model 0x1C
[    0.344375] intel_idle: lapic_timer_reliable_states 0x2
[    0.344594] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input0
[    0.344619] ACPI: Sleep Button [SLPB]
[    0.344748] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.344766] ACPI: Power Button [PWRF]
[    0.350837] GHES: HEST is not enabled!
[    0.351084] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.355075] Linux agpgart interface v0.103
[    0.355199] agpgart-intel 0000:00:00.0: Intel 945G Chipset
[    0.355314] agpgart-intel 0000:00:00.0: detected gtt size: 131072K total, 131072K mappable
[    0.355678] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    0.355987] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0x80000000
[    0.360466] brd: module loaded
[    0.362753] loop: module loaded
[    0.363142] ata_piix 0000:00:1f.1: version 2.13
[    0.363263] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.364193] scsi0 : ata_piix
[    0.364517] scsi1 : ata_piix
[    0.365293] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x30b0 irq 14
[    0.365308] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x30b8 irq 15
[    0.365391] ata_piix 0000:00:1f.2: MAP [
[    0.365402]  P0 P2 P1 P3 ]
[    0.365784] ata2: port disabled--ignoring
[    0.520087] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.521108] scsi2 : ata_piix
[    0.521395] scsi3 : ata_piix
[    0.521915] ata3: SATA max UDMA/133 cmd 0x30c8 ctl 0x30ec bmdma 0x30a0 irq 19
[    0.521933] ata4: SATA max UDMA/133 cmd 0x30c0 ctl 0x30e8 bmdma 0x30a8 irq 19
[    0.522987] Fixed MDIO Bus: probed
[    0.523171] tun: Universal TUN/TAP device driver, 1.6
[    0.523184] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.523474] PPP generic driver version 2.4.2
[    0.523664] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.523826] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.523837] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.523870] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.523932] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.523962] ehci_hcd 0000:00:1d.7: debug port 1
[    0.527874] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    0.527927] ehci_hcd 0000:00:1d.7: irq 23, io mem 0x883a0000
[    0.536049] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.536156] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.536177] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.536198] usb usb1: Product: EHCI Host Controller
[    0.536214] usb usb1: Manufacturer: Linux 3.5.0-22-generic ehci_hcd
[    0.536231] usb usb1: SerialNumber: 0000:00:1d.7
[    0.536592] hub 1-0:1.0: USB hub found
[    0.536630] hub 1-0:1.0: 8 ports detected
[    0.536833] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.536903] uhci_hcd: USB Universal Host Controller Interface driver
[    0.536973] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.536982] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.537004] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.537057] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00003080
[    0.537159] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    0.537173] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.537186] usb usb2: Product: UHCI Host Controller
[    0.537196] usb usb2: Manufacturer: Linux 3.5.0-22-generic uhci_hcd
[    0.537207] usb usb2: SerialNumber: 0000:00:1d.0
[    0.537516] hub 2-0:1.0: USB hub found
[    0.537535] hub 2-0:1.0: 2 ports detected
[    0.537706] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.537714] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.537735] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.537785] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00003060
[    0.537882] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    0.537897] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.537909] usb usb3: Product: UHCI Host Controller
[    0.537919] usb usb3: Manufacturer: Linux 3.5.0-22-generic uhci_hcd
[    0.537930] usb usb3: SerialNumber: 0000:00:1d.1
[    0.538214] hub 3-0:1.0: USB hub found
[    0.538235] hub 3-0:1.0: 2 ports detected
[    0.538416] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.538424] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.538446] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.538525] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00003040
[    0.538627] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    0.538641] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.538654] usb usb4: Product: UHCI Host Controller
[    0.538664] usb usb4: Manufacturer: Linux 3.5.0-22-generic uhci_hcd
[    0.538674] usb usb4: SerialNumber: 0000:00:1d.2
[    0.538956] hub 4-0:1.0: USB hub found
[    0.538976] hub 4-0:1.0: 2 ports detected
[    0.539143] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.539152] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.539173] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.539240] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00003020
[    0.539332] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    0.539346] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.539359] usb usb5: Product: UHCI Host Controller
[    0.539369] usb usb5: Manufacturer: Linux 3.5.0-22-generic uhci_hcd
[    0.539380] usb usb5: SerialNumber: 0000:00:1d.3
[    0.539671] hub 5-0:1.0: USB hub found
[    0.539691] hub 5-0:1.0: 2 ports detected
[    0.540073] usbcore: registered new interface driver libusual
[    0.540234] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    0.543428] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.543480] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.544110] mousedev: PS/2 mouse device common for all mice
[    0.544676] rtc_cmos 00:03: RTC can wake from S4
[    0.544936] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.545007] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
[    0.545306] device-mapper: uevent: version 1.0.3
[    0.545612] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    0.545776] cpuidle: using governor ladder
[    0.545970] cpuidle: using governor menu
[    0.545989] EFI Variables Facility v0.08 2004-May-17
[    0.546851] ashmem: initialized
[    0.547266] TCP: cubic registered
[    0.547694] NET: Registered protocol family 10
[    0.548497] NET: Registered protocol family 17
[    0.548559] Key type dns_resolver registered
[    0.549207] PM: Hibernation image not present or could not be loaded.
[    0.549251] registered taskstats version 1
[    0.687356] ata4.00: ATA-8: WDC WD3202ABYS-01B7A0, 02.03B02, max UDMA/133
[    0.687375] ata4.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    0.693316] ata4.00: configured for UDMA/133
[    0.693893] scsi 3:0:0:0: Direct-Access     ATA      WDC WD3202ABYS-0 02.0 PQ: 0 ANSI: 5
[    0.694473] sd 3:0:0:0: Attached scsi generic sg0 type 0
[    0.694491] sd 3:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    0.694803] sd 3:0:0:0: [sda] Write Protect is off
[    0.694832] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.694943] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.715548]  sda: sda1 sda2 sda3
[    0.716939] sd 3:0:0:0: [sda] Attached SCSI disk
[    0.804437] Freeing initrd memory: 14876k freed
[    0.825811] Key type trusted registered
[    0.832058] Key type encrypted registered
[    0.838859]   Magic number: 1:246:988
[    0.838972] machinecheck machinecheck1: hash matches
[    0.839125] rtc_cmos 00:03: setting system clock to 2013-02-06 13:59:17 UTC (1360159157)
[    0.839361] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.839374] EDD information not available.
[    0.843522] Freeing unused kernel memory: 932k freed
[    0.844335] Write protecting the kernel read-only data: 12288k
[    0.848096] usb 1-1: new high-speed USB device number 2 using ehci_hcd
[    0.856572] Freeing unused kernel memory: 1464k freed
[    0.866705] Freeing unused kernel memory: 1120k freed
[    0.923831] udevd[107]: starting version 175
[    0.981906] usb 1-1: New USB device found, idVendor=0bda, idProduct=8176
[    0.981939] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    0.981960] usb 1-1: Product: 802.11n WLAN Adapter
[    0.981978] usb 1-1: Manufacturer: Realtek
[    0.981994] usb 1-1: SerialNumber: 00e04c000001
[    1.039420] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.039683] r8169 0000:01:00.0: irq 43 for MSI/MSI-X
[    1.040822] r8169 0000:01:00.0: eth0: RTL8168c/8111c at 0xffffc90000362000, 00:1c:c0:d0:e0:27, XID 1c4000c0 IRQ 43
[    1.040865] r8169 0000:01:00.0: eth0: jumbo features [frames: 6128 bytes, tx checksumming: ko]
[    1.102420] FDC 0 is a post-1991 82077
[    1.112683] sata_promise 0000:04:00.0: version 2.12
[    1.118687] scsi4 : sata_promise
[    1.119746] scsi5 : sata_promise
[    1.124113] scsi6 : sata_promise
[    1.124413] ata5: SATA max UDMA/133 mmio m4096@0x88120000 ata 0x88120200 irq 21
[    1.124442] ata6: SATA max UDMA/133 mmio m4096@0x88120000 ata 0x88120280 irq 21
[    1.124461] ata7: PATA max UDMA/133 mmio m4096@0x88120000 ata 0x88120300 irq 21
[    1.408057] usb 5-2: new low-speed USB device number 2 using uhci_hcd
[    1.443489] EXT4-fs (sda3): mounted filesystem with ordered data mode. Opts: (null)
[    1.584346] usb 5-2: New USB device found, idVendor=046d, idProduct=c315
[    1.584368] usb 5-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.584381] usb 5-2: Product: Logitech USB Keyboard
[    1.584391] usb 5-2: Manufacturer: Logitech
[    1.600082] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.608496] ata5.00: ATA-7: SAMSUNG HD103UJ, 1AA01118, max UDMA7
[    1.608510] ata5.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 0/32)
[    1.616492] ata5.00: configured for UDMA/133
[    1.616864] scsi 4:0:0:0: Direct-Access     ATA      SAMSUNG HD103UJ  1AA0 PQ: 0 ANSI: 5
[    1.617488] sd 4:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.617527] sd 4:0:0:0: Attached scsi generic sg1 type 0
[    1.617794] sd 4:0:0:0: [sdb] Write Protect is off
[    1.617815] sd 4:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.618047] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.633356]  sdb: sdb1
[    1.634308] sd 4:0:0:0: [sdb] Attached SCSI disk
[    2.148066] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.175889] ata6.00: ATA-8: WDC WD10EADS-00L5B1, 01.01A01, max UDMA/133
[    2.175903] ata6.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 0/32)
[    2.185092] ata6.00: configured for UDMA/133
[    2.185414] scsi 5:0:0:0: Direct-Access     ATA      WDC WD10EADS-00L 01.0 PQ: 0 ANSI: 5
[    2.185875] sd 5:0:0:0: [sdc] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    2.185936] sd 5:0:0:0: Attached scsi generic sg2 type 0
[    2.186225] sd 5:0:0:0: [sdc] Write Protect is off
[    2.186252] sd 5:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    2.186379] sd 5:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.206856]  sdc: sdc2
[    2.207668] sd 5:0:0:0: [sdc] Attached SCSI disk
[    6.421997] Adding 3906556k swap on /dev/sda2.  Priority:-1 extents:1 across:3906556k 
[    6.448329] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    6.504860] udevd[315]: starting version 175
[    6.547586] lp: driver loaded but no devices found
[    6.695007] [drm] Initialized drm 1.1.0 20060810
[    6.722746] i915 0000:00:02.0: setting latency timer to 64
[    6.754991] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    6.755003] [drm] Driver supports precise vblank timestamp query.
[    6.755715] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    6.763758] type=1400 audit(1360159163.419:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=350 comm="apparmor_parser"
[    6.767149] type=1400 audit(1360159163.423:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=350 comm="apparmor_parser"
[    6.768513] type=1400 audit(1360159163.427:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=350 comm="apparmor_parser"
[    6.772115] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro
[    6.878892] r8169 0000:01:00.0: eth0: link down
[    6.878953] r8169 0000:01:00.0: eth0: link down
[    6.880282] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    6.898853] intel_rng: Firmware space is locked read-only. If you can't or
[    6.898853] intel_rng: don't want to disable this in firmware setup, and if
[    6.898853] intel_rng: you are certain that your system has a functional
[    6.898853] intel_rng: RNG, try using the 'no_fwh_detect' option.
[    7.126549] usbcore: registered new interface driver usbhid
[    7.126562] usbhid: USB HID core driver
[    7.132998] cfg80211: Calling CRDA to update world regulatory domain
[    7.173138] microcode: CPU0 sig=0x106c2, pf=0x8, revision=0x213
[    7.467399] kjournald starting.  Commit interval 5 seconds
[    7.467858] EXT3-fs (sda1): using internal journal
[    7.467878] EXT3-fs (sda1): mounted filesystem with ordered data mode
[    7.563800] rtl8192cu: Chip version 0x10
[    7.669889] EXT4-fs (sdb1): warning: maximal mount count reached, running e2fsck is recommended
[    7.747277] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[    7.857487] kjournald starting.  Commit interval 5 seconds
[    7.858468] EXT3-fs (sdc2): warning: maximal mount count reached, running e2fsck is recommended
[    7.859502] EXT3-fs (sdc2): using internal journal
[    7.859517] EXT3-fs (sdc2): mounted filesystem with ordered data mode
[    7.891021] rtl8192cu: MAC address: 64:70:02:1a:a4:63
[    7.891040] rtl8192cu: Board Type 0
[    7.891274] rtlwifi: rx_max_size 15360, rx_urb_num 8, in_ep 1
[    7.891293] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[    7.891302] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    7.891309] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[    7.891315] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    7.891321] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[    7.891327] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    7.891333] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[    7.891340] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    7.891345] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[    7.891352] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    7.891358] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[    7.891365] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    7.891370] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[    7.891376] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    7.891381] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[    7.891387] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    7.891392] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[    7.891398] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    7.891403] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[    7.891409] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    7.891414] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[    7.891421] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    7.891427] cfg80211: Disabling freq 2467 MHz as custom regd has no rule that fits a 20 MHz wide channel
[    7.891434] cfg80211: Disabling freq 2472 MHz as custom regd has no rule that fits a 20 MHz wide channel
[    7.891440] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
[    7.891475] cfg80211: Pending regulatory request, waiting for it to be processed...
[    7.892821] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw.bin
[    7.893870] usbcore: registered new interface driver rtl8192cu
[    7.901413] [drm] initialized overlay support
[    7.938126] input: Logitech Logitech USB Keyboard as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.0/input/input2
[    7.958156] hid-generic 0003:046D:C315.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech Logitech USB Keyboard] on usb-0000:00:1d.3-2/input0
[    8.081809] init: failsafe main process (647) killed by TERM signal
[    8.174282] microcode: CPU1 sig=0x106c2, pf=0x8, revision=0x213
[    8.186354] microcode: CPU2 sig=0x106c2, pf=0x8, revision=0x213
[    8.198480] microcode: CPU3 sig=0x106c2, pf=0x8, revision=0x213
[    8.205013] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    8.270466] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[    8.344730] type=1400 audit(1360159165.003:5): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=756 comm="apparmor_parser"
[    8.347010] type=1400 audit(1360159165.003:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=754 comm="apparmor_parser"
[    8.349239] type=1400 audit(1360159165.007:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=754 comm="apparmor_parser"
[    8.350382] type=1400 audit(1360159165.007:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=754 comm="apparmor_parser"
[    8.422526] fbcon: inteldrmfb (fb0) is primary device
[    8.427766] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[    8.427770] cfg80211: World regulatory domain updated:
[    8.427772] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    8.427779] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.427782] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    8.427786] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    8.427789] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.427793] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.427832] cfg80211: Calling CRDA for country: US
[    8.445503] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    8.447267] rtlwifi: wireless switch is on
[    8.451835] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[    8.451841] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[    8.451846] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[    8.451850] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[    8.451853] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[    8.451856] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[    8.451860] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[    8.451863] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[    8.451867] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[    8.451871] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[    8.451874] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[    8.451878] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[    8.451882] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[    8.451885] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[    8.451889] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[    8.451892] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[    8.451895] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[    8.451899] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[    8.451902] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[    8.451906] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[    8.451909] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[    8.451913] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[    8.451915] cfg80211: Disabling freq 2467 MHz
[    8.451918] cfg80211: Disabling freq 2472 MHz
[    8.451920] cfg80211: Disabling freq 2484 MHz
[    8.451926] cfg80211: Regulatory domain changed to country: US
[    8.451928] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    8.451932] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[    8.451936] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[    8.451940] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.451944] cfg80211:   (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.451947] cfg80211:   (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.451951] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[    8.476969] Console: switching to colour frame buffer device 240x67
[    8.502867] fb0: inteldrmfb frame buffer device
[    8.502872] drm: registered panic notifier
[    8.504339] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    8.504488] ACPI Warning: 0x00000000fed1f410-0x00000000fed1f414 SystemMemory conflicts with Region \_SB_.PCI0.SRCR 1 (20120320/utaddress-251)
[    8.504509] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    8.504516] lpc_ich: Resource conflict(s) found affecting iTCO_wdt
[    8.504526] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \GPE0 1 (20120320/utaddress-251)
[    8.504543] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    8.504555] ACPI Warning: 0x0000000000000500-0x000000000000053f SystemIO conflicts with Region \IGPO 1 (20120320/utaddress-251)
[    8.504571] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    8.504577] lpc_ich: Resource conflict(s) found affecting gpio_ich
[    8.506107] leds_ss4200: no LED devices found
[    8.847665] vesafb: mode is 1280x1024x32, linelength=5120, pages=0
[    8.847678] vesafb: scrolling: redraw
[    8.847687] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    8.849625] vesafb: framebuffer at 0x80000000, mapped to 0xffffc90011480000, using 5120k, total 5120k
[    8.853843] fb1: VESA VGA frame buffer device

```

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.5.0-22-generic (buildd@komainu) (gcc version 4.7.2 (Ubuntu/Linaro 4.7.2-2ubuntu1) ) #34-Ubuntu SMP Tue Jan 8 21:47:00 UTC 2013 (Ubuntu 3.5.0-22.34-generic 3.5.7.2)
[    0.000000] Command line: BOOT_IMAGE=/vmlinuz-3.5.0-22-generic root=UUID=ff204e15-e503-4ac9-aef0-28a8513a8e7c ro
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] Disabled fast string operations
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000008efff] usable
[    0.000000] BIOS-e820: [mem 0x000000000008f000-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000007f526fff] usable
[    0.000000] BIOS-e820: [mem 0x000000007f527000-0x000000007f52efff] reserved
[    0.000000] BIOS-e820: [mem 0x000000007f52f000-0x000000007f5befff] usable
[    0.000000] BIOS-e820: [mem 0x000000007f5bf000-0x000000007f5c2fff] reserved
[    0.000000] BIOS-e820: [mem 0x000000007f5c3000-0x000000007f65ffff] usable
[    0.000000] BIOS-e820: [mem 0x000000007f660000-0x000000007f6effff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000007f6f0000-0x000000007f6f1fff] usable
[    0.000000] BIOS-e820: [mem 0x000000007f6f2000-0x000000007f6fefff] ACPI data
[    0.000000] BIOS-e820: [mem 0x000000007f6ff000-0x000000007f6fffff] usable
[    0.000000] BIOS-e820: [mem 0x000000007f700000-0x000000007fffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000f0000000-0x00000000ffffffff] reserved
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.4 present.
[    0.000000] DMI:                  /D945GCLF2, BIOS LF94510J.86A.0171.2009.0403.0118 04/03/2009
[    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x7f700 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-DFFFF uncachable
[    0.000000]   E0000-E0FFF write-protect
[    0.000000]   E1000-E7FFF uncachable
[    0.000000]   E8000-E8FFF write-protect
[    0.000000]   E9000-EFFFF uncachable
[    0.000000]   F0000-F0FFF write-protect
[    0.000000]   F1000-F7FFF uncachable
[    0.000000]   F8000-F8FFF write-protect
[    0.000000]   F9000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask 080000000 write-back
[    0.000000]   1 base 07F800000 mask 0FF800000 uncachable
[    0.000000]   2 base 07F700000 mask 0FFF00000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2040MB, range: 8MB, type UC
[    0.000000] reg 2, base: 2039MB, range: 1MB, type UC
[    0.000000] total RAM covered: 2039M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K 	chunk_size: 16M 	num_reg: 3  	lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2039MB, range: 1MB, type UC
[    0.000000] reg 2, base: 2040MB, range: 8MB, type UC
[    0.000000] found SMP MP-table at [mem 0x000fe200-0x000fe20f] mapped at [ffff8800000fe200]
[    0.000000] initial memory mapped: [mem 0x00000000-0x1fffffff]
[    0.000000] Base memory trampoline at [ffff880000089000] 89000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0x7f6fffff]
[    0.000000]  [mem 0x00000000-0x7f5fffff] page 2M
[    0.000000]  [mem 0x7f600000-0x7f6fffff] page 4k
[    0.000000] kernel direct mapping tables up to 0x7f6fffff @ [mem 0x1fffc000-0x1fffffff]
[    0.000000] RAMDISK: [mem 0x362e2000-0x37168fff]
[    0.000000] ACPI: RSDP 00000000000fe020 00014 (v00 INTEL )
[    0.000000] ACPI: RSDT 000000007f6fd038 0003C (v01 INTEL  D945GLF2 000000AB      01000013)
[    0.000000] ACPI: FACP 000000007f6fc000 00074 (v01 INTEL  D945GLF2 000000AB MSFT 01000013)
[    0.000000] ACPI: DSDT 000000007f6f7000 045EC (v01 INTEL  D945GLF2 000000AB MSFT 01000013)
[    0.000000] ACPI: FACS 000000007f6a3000 00040
[    0.000000] ACPI: APIC 000000007f6f6000 00078 (v01 INTEL  D945GLF2 000000AB MSFT 01000013)
[    0.000000] ACPI: WDDT 000000007f6f5000 00040 (v01 INTEL  D945GLF2 000000AB MSFT 01000013)
[    0.000000] ACPI: MCFG 000000007f6f4000 0003C (v01 INTEL  D945GLF2 000000AB MSFT 01000013)
[    0.000000] ACPI: ASF! 000000007f6f3000 000A6 (v32 INTEL  D945GLF2 000000AB MSFT 01000013)
[    0.000000] ACPI: HPET 000000007f6f2000 00038 (v01 INTEL  D945GLF2 000000AB MSFT 01000013)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000007f6fffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x7f6fffff]
[    0.000000]   NODE_DATA [mem 0x7f65c000-0x7f65ffff]
[    0.000000]  [ffffea0000000000-ffffea0001ffffff] PMD -> [ffff88007cc00000-ffff88007ebfffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00010000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   empty
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00010000-0x0008efff]
[    0.000000]   node   0: [mem 0x00100000-0x7f526fff]
[    0.000000]   node   0: [mem 0x7f52f000-0x7f5befff]
[    0.000000]   node   0: [mem 0x7f5c3000-0x7f65ffff]
[    0.000000]   node   0: [mem 0x7f6f0000-0x7f6f1fff]
[    0.000000]   node   0: [mem 0x7f6ff000-0x7f6fffff]
[    0.000000] On node 0 totalpages: 521686
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 6 pages reserved
[    0.000000]   DMA zone: 3897 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 8092 pages used for memmap
[    0.000000]   DMA32 zone: 509627 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000008f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 000000007f527000 - 000000007f52f000
[    0.000000] PM: Registered nosave memory: 000000007f5bf000 - 000000007f5c3000
[    0.000000] PM: Registered nosave memory: 000000007f660000 - 000000007f6f0000
[    0.000000] PM: Registered nosave memory: 000000007f6f2000 - 000000007f6ff000
[    0.000000] e820: [mem 0x80000000-0xefffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88007f200000 s83584 r8192 d22912 u524288
[    0.000000] pcpu-alloc: s83584 r8192 d22912 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 513524
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-3.5.0-22-generic root=UUID=ff204e15-e503-4ac9-aef0-28a8513a8e7c ro
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] __ex_table already sorted, skipping sort
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 2022804k/2087936k available (6719k kernel code, 1192k absent, 63940k reserved, 6451k data, 932k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:712 16
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 8388608 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1596.166 MHz processor.
[    0.004009] Calibrating delay loop (skipped), value calculated using timer frequency.. 3192.33 BogoMIPS (lpj=6384664)
[    0.004102] pid_max: default: 32768 minimum: 301
[    0.004218] Security Framework initialized
[    0.004306] AppArmor: AppArmor initialized
[    0.004350] Yama: becoming mindful.
[    0.004923] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.008072] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.009061] Mount-cache hash table entries: 256
[    0.009688] Initializing cgroup subsys cpuacct
[    0.009746] Initializing cgroup subsys memory
[    0.009813] Initializing cgroup subsys devices
[    0.009860] Initializing cgroup subsys freezer
[    0.009904] Initializing cgroup subsys blkio
[    0.009950] Initializing cgroup subsys perf_event
[    0.010067] Disabled fast string operations
[    0.010120] CPU: Physical Processor ID: 0
[    0.010163] CPU: Processor Core ID: 0
[    0.010207] mce: CPU supports 5 MCE banks
[    0.010261] CPU0: Thermal monitoring enabled (TM1)
[    0.010313] using mwait in idle threads.
[    0.013584] ACPI: Core revision 20120320
[    0.020034] ftrace: allocating 25143 entries in 99 pages
[    0.040588] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.081762] CPU0: Intel(R) Atom(TM) CPU  330   @ 1.60GHz stepping 02
[    0.084004] Performance Events: PEBS fmt0+, LBR disabled due to erratumAtom events, Intel PMU driver.
[    0.084004] ... version:                3
[    0.084004] ... bit width:              40
[    0.084004] ... generic registers:      2
[    0.084004] ... value mask:             000000ffffffffff
[    0.084004] ... max period:             000000007fffffff
[    0.084004] ... fixed-purpose events:   3
[    0.084004] ... event mask:             0000000700000003
[    0.084004] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.008000] Disabled fast string operations
[    0.084004] Booting Node   0, Processors  #1
[    0.094693] TSC synchronization [CPU#0 -> CPU#1]:
[    0.094812] Measured 120 cycles TSC warp between CPUs, turning off TSC clock.
[    0.094859] Marking TSC unstable due to check_tsc_sync_source failed
[    0.008000] Disabled fast string operations
[    0.095263]  #2 #3 Ok.
[    0.008000] Disabled fast string operations
[    0.117943] Brought up 4 CPUs
[    0.118033] Total of 4 processors activated (12769.32 BogoMIPS).
[    0.120285] devtmpfs: initialized
[    0.124575] EVM: security.selinux
[    0.124621] EVM: security.SMACK64
[    0.124662] EVM: security.capability
[    0.124749] PM: Registering ACPI NVS region [mem 0x7f660000-0x7f6effff] (589824 bytes)
[    0.126598] dummy: 
[    0.126697] RTC time: 13:53:17, date: 02/06/13
[    0.126855] NET: Registered protocol family 16
[    0.126934] Trying to unpack rootfs image as initramfs...
[    0.128465] ACPI: bus type pci registered
[    0.128739] PCI: MMCONFIG for domain 0000 [bus 00-7f] at [mem 0xf0000000-0xf7ffffff] (base 0xf0000000)
[    0.128812] PCI: MMCONFIG at [mem 0xf0000000-0xf7ffffff] reserved in E820
[    0.153732] PCI: Using configuration type 1 for base access
[    0.160074] bio: create slab <bio-0> at 0
[    0.160306] ACPI: Added _OSI(Module Device)
[    0.160362] ACPI: Added _OSI(Processor Device)
[    0.160411] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.160460] ACPI: Added _OSI(Processor Aggregator Device)
[    0.163194] ACPI: EC: Look up EC in DSDT
[    0.170394] ACPI: Interpreter enabled
[    0.170461] ACPI: (supports S0 S1 S3 S4 S5)
[    0.170715] ACPI: Using IOAPIC for interrupt routing
[    0.184796] ACPI: No dock devices found.
[    0.184871] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.187664] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.192907] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
[    0.192984] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
[    0.193040] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.193105] pci_root PNP0A03:00: host bridge window [mem 0x000e0000-0x000effff]
[    0.193170] pci_root PNP0A03:00: host bridge window [mem 0xf8000000-0xfebfffff]
[    0.193902] pci_root PNP0A03:00: host bridge window [mem 0x80000000-0xf0000000]
[    0.194128] PCI host bridge to bus 0000:00
[    0.194194] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.194250] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.194303] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.194363] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000effff]
[    0.194419] pci_bus 0000:00: root bus resource [mem 0xf8000000-0xfebfffff]
[    0.194472] pci_bus 0000:00: root bus resource [mem 0x80000000-0xf0000000]
[    0.194550] pci 0000:00:00.0: [8086:2770] type 00 class 0x060000
[    0.194644] pci 0000:00:02.0: [8086:2772] type 00 class 0x030000
[    0.194672] pci 0000:00:02.0: reg 10: [mem 0x88300000-0x8837ffff]
[    0.194694] pci 0000:00:02.0: reg 14: [io  0x30e0-0x30e7]
[    0.194714] pci 0000:00:02.0: reg 18: [mem 0x80000000-0x87ffffff pref]
[    0.194732] pci 0000:00:02.0: reg 1c: [mem 0x88380000-0x8839ffff]
[    0.194866] pci 0000:00:1c.0: [8086:27d0] type 01 class 0x060400
[    0.194982] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.195032] pci 0000:00:1c.2: [8086:27d4] type 01 class 0x060400
[    0.195142] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.195200] pci 0000:00:1c.3: [8086:27d6] type 01 class 0x060400
[    0.195311] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.195359] pci 0000:00:1d.0: [8086:27c8] type 00 class 0x0c0300
[    0.195421] pci 0000:00:1d.0: reg 20: [io  0x3080-0x309f]
[    0.195484] pci 0000:00:1d.1: [8086:27c9] type 00 class 0x0c0300
[    0.195556] pci 0000:00:1d.1: reg 20: [io  0x3060-0x307f]
[    0.195619] pci 0000:00:1d.2: [8086:27ca] type 00 class 0x0c0300
[    0.195681] pci 0000:00:1d.2: reg 20: [io  0x3040-0x305f]
[    0.195740] pci 0000:00:1d.3: [8086:27cb] type 00 class 0x0c0300
[    0.195801] pci 0000:00:1d.3: reg 20: [io  0x3020-0x303f]
[    0.195874] pci 0000:00:1d.7: [8086:27cc] type 00 class 0x0c0320
[    0.195908] pci 0000:00:1d.7: reg 10: [mem 0x883a0000-0x883a03ff]
[    0.196068] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.196111] pci 0000:00:1e.0: [8086:244e] type 01 class 0x060401
[    0.196235] pci 0000:00:1f.0: [8086:27b8] type 00 class 0x060100
[    0.196360] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0680 (mask 007f)
[    0.196509] pci 0000:00:1f.1: [8086:27df] type 00 class 0x01018a
[    0.196536] pci 0000:00:1f.1: reg 10: [io  0x30d8-0x30df]
[    0.196555] pci 0000:00:1f.1: reg 14: [io  0x30f4-0x30f7]
[    0.196573] pci 0000:00:1f.1: reg 18: [io  0x30d0-0x30d7]
[    0.196590] pci 0000:00:1f.1: reg 1c: [io  0x30f0-0x30f3]
[    0.196608] pci 0000:00:1f.1: reg 20: [io  0x30b0-0x30bf]
[    0.196677] pci 0000:00:1f.2: [8086:27c0] type 00 class 0x01018f
[    0.196704] pci 0000:00:1f.2: reg 10: [io  0x30c8-0x30cf]
[    0.196721] pci 0000:00:1f.2: reg 14: [io  0x30ec-0x30ef]
[    0.196738] pci 0000:00:1f.2: reg 18: [io  0x30c0-0x30c7]
[    0.196756] pci 0000:00:1f.2: reg 1c: [io  0x30e8-0x30eb]
[    0.196773] pci 0000:00:1f.2: reg 20: [io  0x30a0-0x30af]
[    0.196834] pci 0000:00:1f.2: PME# supported from D3hot
[    0.196867] pci 0000:00:1f.3: [8086:27da] type 00 class 0x0c0500
[    0.196939] pci 0000:00:1f.3: reg 20: [io  0x3000-0x301f]
[    0.197102] pci 0000:01:00.0: [10ec:8168] type 00 class 0x020000
[    0.197136] pci 0000:01:00.0: reg 10: [io  0x2000-0x20ff]
[    0.197178] pci 0000:01:00.0: reg 18: [mem 0x88200000-0x88200fff 64bit]
[    0.197208] pci 0000:01:00.0: reg 20: [mem 0x88000000-0x8800ffff 64bit pref]
[    0.197230] pci 0000:01:00.0: reg 30: [mem 0xfffe0000-0xffffffff pref]
[    0.197325] pci 0000:01:00.0: supports D1 D2
[    0.197333] pci 0000:01:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.204095] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    0.204164] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.204176] pci 0000:00:1c.0:   bridge window [mem 0x88200000-0x882fffff]
[    0.204190] pci 0000:00:1c.0:   bridge window [mem 0x88000000-0x880fffff 64bit pref]
[    0.204267] pci 0000:00:1c.2: PCI bridge to [bus 02-02]
[    0.204391] pci 0000:00:1c.3: PCI bridge to [bus 03-03]
[    0.204527] pci 0000:04:00.0: [105a:3570] type 00 class 0x010400
[    0.204564] pci 0000:04:00.0: reg 10: [io  0x1400-0x147f]
[    0.204595] pci 0000:04:00.0: reg 18: [io  0x1000-0x10ff]
[    0.204615] pci 0000:04:00.0: reg 1c: [mem 0x88120000-0x88120fff]
[    0.204635] pci 0000:04:00.0: reg 20: [mem 0x88100000-0x8811ffff]
[    0.204666] pci 0000:04:00.0: reg 30: [mem 0xffff0000-0xffffffff pref]
[    0.204720] pci 0000:04:00.0: supports D1
[    0.204793] pci 0000:00:1e.0: PCI bridge to [bus 04-04] (subtractive decode)
[    0.204853] pci 0000:00:1e.0:   bridge window [io  0x1000-0x1fff]
[    0.204864] pci 0000:00:1e.0:   bridge window [mem 0x88100000-0x881fffff]
[    0.204879] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.204888] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.204896] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.204905] pci 0000:00:1e.0:   bridge window [mem 0x000e0000-0x000effff] (subtractive decode)
[    0.204914] pci 0000:00:1e.0:   bridge window [mem 0xf8000000-0xfebfffff] (subtractive decode)
[    0.204923] pci 0000:00:1e.0:   bridge window [mem 0x80000000-0xf0000000] (subtractive decode)
[    0.204969] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.205490] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P32_._PRT]
[    0.206015] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    0.206187] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX2._PRT]
[    0.206351] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX3._PRT]
[    0.206653]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.206715]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.206779] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.219816] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
[    0.220406] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.220988] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12)
[    0.221514] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 *10 11 12)
[    0.222037] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.222631] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 *9 10 11 12)
[    0.223152] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.223797] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 *9 10 11 12)
[    0.224477] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.224477] vgaarb: loaded
[    0.224477] vgaarb: bridge control possible 0000:00:02.0
[    0.225031] SCSI subsystem initialized
[    0.225310] libata version 3.00 loaded.
[    0.225408] ACPI: bus type usb registered
[    0.225541] usbcore: registered new interface driver usbfs
[    0.225641] usbcore: registered new interface driver hub
[    0.225776] usbcore: registered new device driver usb
[    0.225776] PCI: Using ACPI for IRQ routing
[    0.230900] PCI: pci_cache_line_size set to 64 bytes
[    0.231093] Expanded resource reserved due to conflict with PCI Bus 0000:00
[    0.231156] e820: reserve RAM buffer [mem 0x0008f000-0x0008ffff]
[    0.231164] e820: reserve RAM buffer [mem 0x7f527000-0x7fffffff]
[    0.231172] e820: reserve RAM buffer [mem 0x7f5bf000-0x7fffffff]
[    0.231180] e820: reserve RAM buffer [mem 0x7f660000-0x7fffffff]
[    0.231187] e820: reserve RAM buffer [mem 0x7f6f2000-0x7fffffff]
[    0.231193] e820: reserve RAM buffer [mem 0x7f700000-0x7fffffff]
[    0.231583] NetLabel: Initializing
[    0.231634] NetLabel:  domain hash size = 128
[    0.231679] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.231771] NetLabel:  unlabeled traffic allowed by default
[    0.232101] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.232161] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.232313] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.244124] Switching to clocksource hpet
[    0.271709] AppArmor: AppArmor Filesystem Enabled
[    0.271857] pnp: PnP ACPI init
[    0.271952] ACPI: bus type pnp registered
[    0.273873] pnp 00:00: [bus 00-ff]
[    0.273882] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.273889] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.273895] pnp 00:00: [io  0x0d00-0xffff window]
[    0.273902] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.273908] pnp 00:00: [mem 0x000e0000-0x000effff window]
[    0.273914] pnp 00:00: [mem 0xf8000000-0xfebfffff window]
[    0.273920] pnp 00:00: [mem 0x80000000-0xf0000000 window]
[    0.274043] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.274082] pnp 00:01: [mem 0xf0000000-0xf3ffffff]
[    0.274089] pnp 00:01: [mem 0xfed13000-0xfed13fff]
[    0.274094] pnp 00:01: [mem 0xfed14000-0xfed17fff]
[    0.274100] pnp 00:01: [mem 0xfed18000-0xfed18fff]
[    0.274106] pnp 00:01: [mem 0xfed19000-0xfed19fff]
[    0.274111] pnp 00:01: [mem 0xfed1c000-0xfed1ffff]
[    0.274117] pnp 00:01: [mem 0xfed20000-0xfed3ffff]
[    0.274123] pnp 00:01: [mem 0xfed45000-0xfed99fff]
[    0.274128] pnp 00:01: [mem 0x000c0000-0x000dffff]
[    0.274134] pnp 00:01: [mem 0x000e0000-0x000fffff]
[    0.274266] system 00:01: [mem 0xf0000000-0xf3ffffff] could not be reserved
[    0.274323] system 00:01: [mem 0xfed13000-0xfed13fff] has been reserved
[    0.274374] system 00:01: [mem 0xfed14000-0xfed17fff] has been reserved
[    0.274424] system 00:01: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.274477] system 00:01: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.274535] system 00:01: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.274593] system 00:01: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.274648] system 00:01: [mem 0xfed45000-0xfed99fff] has been reserved
[    0.274699] system 00:01: [mem 0x000c0000-0x000dffff] could not be reserved
[    0.274750] system 00:01: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.274805] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.275154] pnp 00:02: [io  0x0000-0x000f]
[    0.275162] pnp 00:02: [io  0x0081-0x0083]
[    0.275167] pnp 00:02: [io  0x0087]
[    0.275180] pnp 00:02: [io  0x0089-0x008b]
[    0.275186] pnp 00:02: [io  0x008f]
[    0.275192] pnp 00:02: [io  0x00c0-0x00df]
[    0.275198] pnp 00:02: [dma 4]
[    0.275277] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.275311] pnp 00:03: [io  0x0070-0x0071]
[    0.275317] pnp 00:03: [io  0x0074-0x0077]
[    0.275343] pnp 00:03: [irq 8]
[    0.275412] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.275447] pnp 00:04: [io  0x00f0]
[    0.275463] pnp 00:04: [irq 13]
[    0.275540] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.275575] pnp 00:05: [io  0x0061]
[    0.275645] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.275680] pnp 00:06: [io  0x0500-0x053f]
[    0.275687] pnp 00:06: [io  0x0400-0x047f]
[    0.275692] pnp 00:06: [io  0x0092]
[    0.275697] pnp 00:06: [io  0x0680-0x06ff]
[    0.275703] pnp 00:06: [io  0x0010-0x001f]
[    0.275708] pnp 00:06: [io  0x0072-0x0073]
[    0.275713] pnp 00:06: [io  0x0080]
[    0.275719] pnp 00:06: [io  0x0084-0x0086]
[    0.275724] pnp 00:06: [io  0x0088]
[    0.275729] pnp 00:06: [io  0x008c-0x008e]
[    0.275734] pnp 00:06: [io  0x0090-0x009f]
[    0.275871] system 00:06: [io  0x0500-0x053f] has been reserved
[    0.275924] system 00:06: [io  0x0400-0x047f] has been reserved
[    0.275972] system 00:06: [io  0x0680-0x06ff] has been reserved
[    0.276083] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.276214] pnp 00:07: [io  0x0060]
[    0.276221] pnp 00:07: [io  0x0064]
[    0.276327] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.276746] pnp 00:08: [io  0x03f0-0x03f5]
[    0.276754] pnp 00:08: [io  0x03f0]
[    0.276771] pnp 00:08: [irq 6]
[    0.276778] pnp 00:08: [dma 2]
[    0.276930] pnp 00:08: Plug and Play ACPI device, IDs PNP0700 (active)
[    0.277492] pnp 00:09: [mem 0xfec00000-0xfec000ff]
[    0.277577] pnp 00:09: Plug and Play ACPI device, IDs PNP0003 (active)
[    0.277646] pnp 00:0a: [mem 0xfed00000-0xfed003ff]
[    0.277736] pnp 00:0a: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.277828] pnp: PnP ACPI: found 11 devices
[    0.277875] ACPI: ACPI bus type pnp unregistered
[    0.289410] pci 0000:01:00.0: no compatible bridge window for [mem 0xfffe0000-0xffffffff pref]
[    0.289486] pci 0000:04:00.0: no compatible bridge window for [mem 0xffff0000-0xffffffff pref]
[    0.289601] pci 0000:00:1c.2: bridge window [io  0x1000-0x0fff] to [bus 02-02] add_size 1000
[    0.289612] pci 0000:00:1c.2: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 02-02] add_size 200000
[    0.289620] pci 0000:00:1c.2: bridge window [mem 0x00100000-0x000fffff] to [bus 02-02] add_size 200000
[    0.289637] pci 0000:00:1c.3: bridge window [io  0x1000-0x0fff] to [bus 03-03] add_size 1000
[    0.289645] pci 0000:00:1c.3: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 03-03] add_size 200000
[    0.289652] pci 0000:00:1c.3: bridge window [mem 0x00100000-0x000fffff] to [bus 03-03] add_size 200000
[    0.289690] pci 0000:00:1c.2: res[14]=[mem 0x00100000-0x000fffff] get_res_add_size add_size 200000
[    0.289698] pci 0000:00:1c.2: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.289705] pci 0000:00:1c.3: res[14]=[mem 0x00100000-0x000fffff] get_res_add_size add_size 200000
[    0.289712] pci 0000:00:1c.3: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.289719] pci 0000:00:1c.2: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.289725] pci 0000:00:1c.3: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.289739] pci 0000:00:1c.2: BAR 14: assigned [mem 0x88400000-0x885fffff]
[    0.289796] pci 0000:00:1c.2: BAR 15: assigned [mem 0x88600000-0x887fffff 64bit pref]
[    0.289859] pci 0000:00:1c.3: BAR 14: assigned [mem 0x88800000-0x889fffff]
[    0.289911] pci 0000:00:1c.3: BAR 15: assigned [mem 0x88a00000-0x88bfffff 64bit pref]
[    0.289975] pci 0000:00:1e.0: BAR 15: assigned [mem 0x88c00000-0x88cfffff pref]
[    0.290037] pci 0000:00:1c.2: BAR 13: assigned [io  0x4000-0x4fff]
[    0.290088] pci 0000:00:1c.3: BAR 13: assigned [io  0x5000-0x5fff]
[    0.290140] pci 0000:01:00.0: BAR 6: assigned [mem 0x88020000-0x8803ffff pref]
[    0.290202] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    0.290250] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.290300] pci 0000:00:1c.0:   bridge window [mem 0x88200000-0x882fffff]
[    0.290356] pci 0000:00:1c.0:   bridge window [mem 0x88000000-0x880fffff 64bit pref]
[    0.290420] pci 0000:00:1c.2: PCI bridge to [bus 02-02]
[    0.290467] pci 0000:00:1c.2:   bridge window [io  0x4000-0x4fff]
[    0.290518] pci 0000:00:1c.2:   bridge window [mem 0x88400000-0x885fffff]
[    0.290568] pci 0000:00:1c.2:   bridge window [mem 0x88600000-0x887fffff 64bit pref]
[    0.290632] pci 0000:00:1c.3: PCI bridge to [bus 03-03]
[    0.290681] pci 0000:00:1c.3:   bridge window [io  0x5000-0x5fff]
[    0.290732] pci 0000:00:1c.3:   bridge window [mem 0x88800000-0x889fffff]
[    0.290783] pci 0000:00:1c.3:   bridge window [mem 0x88a00000-0x88bfffff 64bit pref]
[    0.290858] pci 0000:04:00.0: BAR 6: assigned [mem 0x88c00000-0x88c0ffff pref]
[    0.290920] pci 0000:00:1e.0: PCI bridge to [bus 04-04]
[    0.290967] pci 0000:00:1e.0:   bridge window [io  0x1000-0x1fff]
[    0.291018] pci 0000:00:1e.0:   bridge window [mem 0x88100000-0x881fffff]
[    0.291069] pci 0000:00:1e.0:   bridge window [mem 0x88c00000-0x88cfffff pref]
[    0.291230] pci 0000:00:1e.0: setting latency timer to 64
[    0.291241] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.291248] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.291254] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.291260] pci_bus 0000:00: resource 7 [mem 0x000e0000-0x000effff]
[    0.291266] pci_bus 0000:00: resource 8 [mem 0xf8000000-0xfebfffff]
[    0.291272] pci_bus 0000:00: resource 9 [mem 0x80000000-0xf0000000]
[    0.291279] pci_bus 0000:01: resource 0 [io  0x2000-0x2fff]
[    0.291285] pci_bus 0000:01: resource 1 [mem 0x88200000-0x882fffff]
[    0.291291] pci_bus 0000:01: resource 2 [mem 0x88000000-0x880fffff 64bit pref]
[    0.291298] pci_bus 0000:02: resource 0 [io  0x4000-0x4fff]
[    0.291304] pci_bus 0000:02: resource 1 [mem 0x88400000-0x885fffff]
[    0.291310] pci_bus 0000:02: resource 2 [mem 0x88600000-0x887fffff 64bit pref]
[    0.291316] pci_bus 0000:03: resource 0 [io  0x5000-0x5fff]
[    0.291322] pci_bus 0000:03: resource 1 [mem 0x88800000-0x889fffff]
[    0.291329] pci_bus 0000:03: resource 2 [mem 0x88a00000-0x88bfffff 64bit pref]
[    0.291335] pci_bus 0000:04: resource 0 [io  0x1000-0x1fff]
[    0.291341] pci_bus 0000:04: resource 1 [mem 0x88100000-0x881fffff]
[    0.291347] pci_bus 0000:04: resource 2 [mem 0x88c00000-0x88cfffff pref]
[    0.291353] pci_bus 0000:04: resource 4 [io  0x0000-0x0cf7]
[    0.291359] pci_bus 0000:04: resource 5 [io  0x0d00-0xffff]
[    0.291365] pci_bus 0000:04: resource 6 [mem 0x000a0000-0x000bffff]
[    0.291371] pci_bus 0000:04: resource 7 [mem 0x000e0000-0x000effff]
[    0.291377] pci_bus 0000:04: resource 8 [mem 0xf8000000-0xfebfffff]
[    0.291383] pci_bus 0000:04: resource 9 [mem 0x80000000-0xf0000000]
[    0.291484] NET: Registered protocol family 2
[    0.291785] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.293598] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.297741] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.298732] TCP: Hash tables configured (established 262144 bind 65536)
[    0.298785] TCP: reno registered
[    0.298870] UDP hash table entries: 1024 (order: 3, 32768 bytes)
[    0.298972] UDP-Lite hash table entries: 1024 (order: 3, 32768 bytes)
[    0.299259] NET: Registered protocol family 1
[    0.299371] pci 0000:00:02.0: Boot video device
[    0.299756] PCI: CLS mismatch (64 != 4), using 64 bytes
[    0.301210] audit: initializing netlink socket (disabled)
[    0.301288] type=2000 audit(1360158796.296:1): initialized
[    0.345519] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.350545] VFS: Disk quotas dquot_6.5.2
[    0.350722] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.352400] fuse init (API version 7.19)
[    0.352717] msgmni has been set to 3950
[    0.354230] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.354400] io scheduler noop registered
[    0.354448] io scheduler deadline registered (default)
[    0.354576] io scheduler cfq registered
[    0.354948] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.355145] pcieport 0000:00:1c.2: irq 41 for MSI/MSI-X
[    0.355303] pcieport 0000:00:1c.3: irq 42 for MSI/MSI-X
[    0.355479] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.355578] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.355772] intel_idle: MWAIT substates: 0x10
[    0.355808] intel_idle: v0.4 model 0x1C
[    0.355812] intel_idle: lapic_timer_reliable_states 0x2
[    0.356084] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input0
[    0.356189] ACPI: Sleep Button [SLPB]
[    0.356402] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.356470] ACPI: Power Button [PWRF]
[    0.362560] GHES: HEST is not enabled!
[    0.362855] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.366910] Linux agpgart interface v0.103
[    0.367082] agpgart-intel 0000:00:00.0: Intel 945G Chipset
[    0.367233] agpgart-intel 0000:00:00.0: detected gtt size: 131072K total, 131072K mappable
[    0.367619] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    0.368038] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0x80000000
[    0.372530] brd: module loaded
[    0.374882] loop: module loaded
[    0.375301] ata_piix 0000:00:1f.1: version 2.13
[    0.375412] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.376347] scsi0 : ata_piix
[    0.376637] scsi1 : ata_piix
[    0.377457] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x30b0 irq 14
[    0.377508] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x30b8 irq 15
[    0.377631] ata_piix 0000:00:1f.2: MAP [
[    0.377685]  P0 P2 P1 P3 ]
[    0.377998] ata2: port disabled--ignoring
[    0.532076] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.543811] scsi2 : ata_piix
[    0.544201] scsi3 : ata_piix
[    0.544681] ata3: SATA max UDMA/133 cmd 0x30c8 ctl 0x30ec bmdma 0x30a0 irq 19
[    0.544733] ata4: SATA max UDMA/133 cmd 0x30c0 ctl 0x30e8 bmdma 0x30a8 irq 19
[    0.545650] Fixed MDIO Bus: probed
[    0.545819] tun: Universal TUN/TAP device driver, 1.6
[    0.545865] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.546103] PPP generic driver version 2.4.2
[    0.546283] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.546457] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.546466] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.546526] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.546630] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.546689] ehci_hcd 0000:00:1d.7: debug port 1
[    0.550620] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    0.550668] ehci_hcd 0000:00:1d.7: irq 23, io mem 0x883a0000
[    0.560057] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.560170] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.560226] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.560288] usb usb1: Product: EHCI Host Controller
[    0.560333] usb usb1: Manufacturer: Linux 3.5.0-22-generic ehci_hcd
[    0.560381] usb usb1: SerialNumber: 0000:00:1d.7
[    0.560786] hub 1-0:1.0: USB hub found
[    0.560842] hub 1-0:1.0: 8 ports detected
[    0.561067] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.561174] uhci_hcd: USB Universal Host Controller Interface driver
[    0.561278] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.561287] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.561344] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.562088] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00003080
[    0.562234] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    0.562286] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.562347] usb usb2: Product: UHCI Host Controller
[    0.562393] usb usb2: Manufacturer: Linux 3.5.0-22-generic uhci_hcd
[    0.562440] usb usb2: SerialNumber: 0000:00:1d.0
[    0.562810] hub 2-0:1.0: USB hub found
[    0.562866] hub 2-0:1.0: 2 ports detected
[    0.563079] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.563087] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.563143] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.563246] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00003060
[    0.563376] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    0.563429] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.563488] usb usb3: Product: UHCI Host Controller
[    0.563534] usb usb3: Manufacturer: Linux 3.5.0-22-generic uhci_hcd
[    0.563582] usb usb3: SerialNumber: 0000:00:1d.1
[    0.563922] hub 3-0:1.0: USB hub found
[    0.563978] hub 3-0:1.0: 2 ports detected
[    0.564285] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.564295] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.564354] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.564477] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00003040
[    0.564611] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    0.564661] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.564722] usb usb4: Product: UHCI Host Controller
[    0.564774] usb usb4: Manufacturer: Linux 3.5.0-22-generic uhci_hcd
[    0.564830] usb usb4: SerialNumber: 0000:00:1d.2
[    0.565206] hub 4-0:1.0: USB hub found
[    0.565262] hub 4-0:1.0: 2 ports detected
[    0.565473] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.565482] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.565541] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.565666] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00003020
[    0.565801] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    0.565853] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.565913] usb usb5: Product: UHCI Host Controller
[    0.565962] usb usb5: Manufacturer: Linux 3.5.0-22-generic uhci_hcd
[    0.566012] usb usb5: SerialNumber: 0000:00:1d.3
[    0.566357] hub 5-0:1.0: USB hub found
[    0.566411] hub 5-0:1.0: 2 ports detected
[    0.566757] usbcore: registered new interface driver libusual
[    0.566897] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    0.570168] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.570256] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.570851] mousedev: PS/2 mouse device common for all mice
[    0.571414] rtc_cmos 00:03: RTC can wake from S4
[    0.571777] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.571892] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
[    0.572284] device-mapper: uevent: version 1.0.3
[    0.572622] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    0.572854] cpuidle: using governor ladder
[    0.573075] cpuidle: using governor menu
[    0.573125] EFI Variables Facility v0.08 2004-May-17
[    0.574002] ashmem: initialized
[    0.574490] TCP: cubic registered
[    0.574940] NET: Registered protocol family 10
[    0.575667] NET: Registered protocol family 17
[    0.575758] Key type dns_resolver registered
[    0.576432] PM: Hibernation image not present or could not be loaded.
[    0.576485] registered taskstats version 1
[    0.716936] ata4.00: ATA-8: WDC WD3202ABYS-01B7A0, 02.03B02, max UDMA/133
[    0.717014] ata4.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    0.724976] ata4.00: configured for UDMA/133
[    0.725395] scsi 3:0:0:0: Direct-Access     ATA      WDC WD3202ABYS-0 02.0 PQ: 0 ANSI: 5
[    0.725865] sd 3:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    0.725963] sd 3:0:0:0: Attached scsi generic sg0 type 0
[    0.726204] sd 3:0:0:0: [sda] Write Protect is off
[    0.726262] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.726371] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.746360]  sda: sda1 sda2 sda3
[    0.747478] sd 3:0:0:0: [sda] Attached SCSI disk
[    0.808245] Freeing initrd memory: 14876k freed
[    0.830128] Key type trusted registered
[    0.836426] Key type encrypted registered
[    0.843280]   Magic number: 1:143:887
[    0.843472] pci 0000:00:1f.0: hash matches
[    0.843622] rtc_cmos 00:03: setting system clock to 2013-02-06 13:53:17 UTC (1360158797)
[    0.843898] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.843948] EDD information not available.
[    0.848231] Freeing unused kernel memory: 932k freed
[    0.848959] Write protecting the kernel read-only data: 12288k
[    0.861149] Freeing unused kernel memory: 1464k freed
[    0.871566] Freeing unused kernel memory: 1120k freed
[    0.872123] usb 1-1: new high-speed USB device number 2 using ehci_hcd
[    0.929946] udevd[105]: starting version 175
[    1.006048] usb 1-1: New USB device found, idVendor=0bda, idProduct=8176
[    1.006128] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.006194] usb 1-1: Product: 802.11n WLAN Adapter
[    1.006258] usb 1-1: Manufacturer: Realtek
[    1.006320] usb 1-1: SerialNumber: 00e04c000001
[    1.040697] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.041010] r8169 0000:01:00.0: irq 43 for MSI/MSI-X
[    1.042729] r8169 0000:01:00.0: eth0: RTL8168c/8111c at 0xffffc90000362000, 00:1c:c0:d0:e0:27, XID 1c4000c0 IRQ 43
[    1.042850] r8169 0000:01:00.0: eth0: jumbo features [frames: 6128 bytes, tx checksumming: ko]
[    1.110442] FDC 0 is a post-1991 82077
[    1.113266] sata_promise 0000:04:00.0: version 2.12
[    1.120166] scsi4 : sata_promise
[    1.123792] scsi5 : sata_promise
[    1.126229] scsi6 : sata_promise
[    1.126557] ata5: SATA max UDMA/133 mmio m4096@0x88120000 ata 0x88120200 irq 21
[    1.126648] ata6: SATA max UDMA/133 mmio m4096@0x88120000 ata 0x88120280 irq 21
[    1.126725] ata7: PATA max UDMA/133 mmio m4096@0x88120000 ata 0x88120300 irq 21
[    1.319776] EXT4-fs (sda3): INFO: recovery required on readonly filesystem
[    1.319835] EXT4-fs (sda3): write access will be enabled during recovery
[    1.428054] usb 5-2: new low-speed USB device number 2 using uhci_hcd
[    1.432705] EXT4-fs (sda3): recovery complete
[    1.433093] EXT4-fs (sda3): mounted filesystem with ordered data mode. Opts: (null)
[    1.600086] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.604815] usb 5-2: New USB device found, idVendor=046d, idProduct=c315
[    1.604874] usb 5-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.604924] usb 5-2: Product: Logitech USB Keyboard
[    1.604969] usb 5-2: Manufacturer: Logitech
[    1.608521] ata5.00: ATA-7: SAMSUNG HD103UJ, 1AA01118, max UDMA7
[    1.608573] ata5.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 0/32)
[    1.616496] ata5.00: configured for UDMA/133
[    1.616855] scsi 4:0:0:0: Direct-Access     ATA      SAMSUNG HD103UJ  1AA0 PQ: 0 ANSI: 5
[    1.617408] sd 4:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.617454] sd 4:0:0:0: Attached scsi generic sg1 type 0
[    1.617955] sd 4:0:0:0: [sdb] Write Protect is off
[    1.618010] sd 4:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.618128] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.628679]  sdb: sdb1
[    1.629659] sd 4:0:0:0: [sdb] Attached SCSI disk
[    2.148067] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.182787] ata6.00: ATA-8: WDC WD10EADS-00L5B1, 01.01A01, max UDMA/133
[    2.182838] ata6.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 0/32)
[    2.189139] ata6.00: configured for UDMA/133
[    2.189501] scsi 5:0:0:0: Direct-Access     ATA      WDC WD10EADS-00L 01.0 PQ: 0 ANSI: 5
[    2.190056] sd 5:0:0:0: [sdc] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    2.190157] sd 5:0:0:0: Attached scsi generic sg2 type 0
[    2.190398] sd 5:0:0:0: [sdc] Write Protect is off
[    2.190472] sd 5:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    2.190591] sd 5:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.202656]  sdc: sdc2
[    2.203504] sd 5:0:0:0: [sdc] Attached SCSI disk
[    6.444257] Adding 3906556k swap on /dev/sda2.  Priority:-1 extents:1 across:3906556k 
[    6.471668] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    6.519001] udevd[313]: starting version 175
[    6.563099] lp: driver loaded but no devices found
[    6.625462] [drm] Initialized drm 1.1.0 20060810
[    6.662410] i915 0000:00:02.0: setting latency timer to 64
[    6.689818] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    6.689829] [drm] Driver supports precise vblank timestamp query.
[    6.690446] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    6.767643] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro
[    6.869313] type=1400 audit(1360158803.521:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=357 comm="apparmor_parser"
[    6.871576] type=1400 audit(1360158803.521:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=357 comm="apparmor_parser"
[    6.872916] type=1400 audit(1360158803.525:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=357 comm="apparmor_parser"
[    6.924690] intel_rng: Firmware space is locked read-only. If you can't or
[    6.924690] intel_rng: don't want to disable this in firmware setup, and if
[    6.924690] intel_rng: you are certain that your system has a functional
[    6.924690] intel_rng: RNG, try using the 'no_fwh_detect' option.
[    6.976257] r8169 0000:01:00.0: eth0: link down
[    6.976523] r8169 0000:01:00.0: eth0: link down
[    6.983827] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    7.163473] cfg80211: Calling CRDA to update world regulatory domain
[    7.184404] usbcore: registered new interface driver usbhid
[    7.184415] usbhid: USB HID core driver
[    7.222225] microcode: CPU0 sig=0x106c2, pf=0x8, revision=0x213
[    7.712767] EXT4-fs (sdb1): warning: maximal mount count reached, running e2fsck is recommended
[    7.729519] rtl8192cu: Chip version 0x10
[    7.777084] EXT4-fs (sdb1): recovery complete
[    7.777104] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[    7.799125] input: Logitech Logitech USB Keyboard as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.0/input/input2
[    7.803997] hid-generic 0003:046D:C315.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech Logitech USB Keyboard] on usb-0000:00:1d.3-2/input0
[    7.883031] rtl8192cu: MAC address: 64:70:02:1a:a4:63
[    7.883044] rtl8192cu: Board Type 0
[    7.883284] rtlwifi: rx_max_size 15360, rx_urb_num 8, in_ep 1
[    7.883296] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[    7.883303] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    7.883309] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[    7.883315] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    7.883320] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[    7.883327] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    7.883332] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[    7.883338] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    7.883343] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[    7.883349] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    7.883354] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[    7.883360] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    7.883365] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[    7.883371] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    7.883376] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[    7.883382] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    7.883387] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[    7.883393] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    7.883399] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[    7.883405] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    7.883433] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[    7.883440] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    7.883445] cfg80211: Disabling freq 2467 MHz as custom regd has no rule that fits a 20 MHz wide channel
[    7.883450] cfg80211: Disabling freq 2472 MHz as custom regd has no rule that fits a 20 MHz wide channel
[    7.883456] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
[    7.883482] cfg80211: Pending regulatory request, waiting for it to be processed...
[    7.883539] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw.bin
[    7.884131] usbcore: registered new interface driver rtl8192cu
[    7.887510] [drm] initialized overlay support
[    7.895959] microcode: CPU1 sig=0x106c2, pf=0x8, revision=0x213
[    7.903912] microcode: CPU2 sig=0x106c2, pf=0x8, revision=0x213
[    7.910419] microcode: CPU3 sig=0x106c2, pf=0x8, revision=0x213
[    7.914780] kjournald starting.  Commit interval 5 seconds
[    7.915528] EXT3-fs (sdc2): warning: maximal mount count reached, running e2fsck is recommended
[    7.916412] EXT3-fs (sdc2): using internal journal
[    7.916430] EXT3-fs (sdc2): recovery complete
[    7.916436] EXT3-fs (sdc2): mounted filesystem with ordered data mode
[    7.918962] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    7.951521] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[    8.069349] kjournald starting.  Commit interval 5 seconds
[    8.075026] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    8.076051] rtlwifi: wireless switch is on
[    8.085142] EXT3-fs (sda1): using internal journal
[    8.085156] EXT3-fs (sda1): mounted filesystem with ordered data mode
[    8.099788] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[    8.099803] cfg80211: World regulatory domain updated:
[    8.099809] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    8.099819] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.099826] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    8.099833] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    8.099840] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.099847] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.099906] cfg80211: Calling CRDA for country: US
[    8.115178] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[    8.115191] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[    8.115198] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[    8.115204] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[    8.115210] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[    8.115216] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[    8.115222] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[    8.115228] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[    8.115234] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[    8.115240] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[    8.115246] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[    8.115252] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[    8.115258] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[    8.115264] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[    8.115270] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[    8.115276] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[    8.115281] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[    8.115287] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[    8.115293] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[    8.115299] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[    8.115305] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[    8.115311] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[    8.115316] cfg80211: Disabling freq 2467 MHz
[    8.115320] cfg80211: Disabling freq 2472 MHz
[    8.115324] cfg80211: Disabling freq 2484 MHz
[    8.115333] cfg80211: Regulatory domain changed to country: US
[    8.115337] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    8.115343] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[    8.115349] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[    8.115356] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.115362] cfg80211:   (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.115368] cfg80211:   (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.115374] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[    8.402674] init: failsafe main process (714) killed by TERM signal
[    8.439733] fbcon: inteldrmfb (fb0) is primary device
[    8.513827] Console: switching to colour frame buffer device 240x67
[    8.538895] fb0: inteldrmfb frame buffer device
[    8.538898] drm: registered panic notifier
[    8.538933] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    8.539084] ACPI Warning: 0x00000000fed1f410-0x00000000fed1f414 SystemMemory conflicts with Region \_SB_.PCI0.SRCR 1 (20120320/utaddress-251)
[    8.539106] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    8.539114] lpc_ich: Resource conflict(s) found affecting iTCO_wdt
[    8.539125] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \GPE0 1 (20120320/utaddress-251)
[    8.539140] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    8.539151] ACPI Warning: 0x0000000000000500-0x000000000000053f SystemIO conflicts with Region \IGPO 1 (20120320/utaddress-251)
[    8.539165] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    8.539170] lpc_ich: Resource conflict(s) found affecting gpio_ich
[    8.541018] leds_ss4200: no LED devices found
[    8.765156] init: udev-fallback-graphics main process (812) terminated with status 1
[    8.916316] type=1400 audit(1360158805.569:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=920 comm="apparmor_parser"
[    8.917467] type=1400 audit(1360158805.569:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=922 comm="apparmor_parser"
[    8.918513] type=1400 audit(1360158805.569:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=920 comm="apparmor_parser"
[    8.919848] type=1400 audit(1360158805.569:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=920 comm="apparmor_parser"
[    9.079111] r8169 0000:01:00.0: eth0: link up
[    9.079901] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

```

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.5.0-22-generic (buildd@komainu) (gcc version 4.7.2 (Ubuntu/Linaro 4.7.2-2ubuntu1) ) #34-Ubuntu SMP Tue Jan 8 21:47:00 UTC 2013 (Ubuntu 3.5.0-22.34-generic 3.5.7.2)
[    0.000000] Command line: BOOT_IMAGE=/vmlinuz-3.5.0-22-generic root=UUID=ff204e15-e503-4ac9-aef0-28a8513a8e7c ro
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] Disabled fast string operations
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000008efff] usable
[    0.000000] BIOS-e820: [mem 0x000000000008f000-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000007f526fff] usable
[    0.000000] BIOS-e820: [mem 0x000000007f527000-0x000000007f52efff] reserved
[    0.000000] BIOS-e820: [mem 0x000000007f52f000-0x000000007f5befff] usable
[    0.000000] BIOS-e820: [mem 0x000000007f5bf000-0x000000007f5c2fff] reserved
[    0.000000] BIOS-e820: [mem 0x000000007f5c3000-0x000000007f65ffff] usable
[    0.000000] BIOS-e820: [mem 0x000000007f660000-0x000000007f6effff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000007f6f0000-0x000000007f6f1fff] usable
[    0.000000] BIOS-e820: [mem 0x000000007f6f2000-0x000000007f6fefff] ACPI data
[    0.000000] BIOS-e820: [mem 0x000000007f6ff000-0x000000007f6fffff] usable
[    0.000000] BIOS-e820: [mem 0x000000007f700000-0x000000007fffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000f0000000-0x00000000ffffffff] reserved
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.4 present.
[    0.000000] DMI:                  /D945GCLF2, BIOS LF94510J.86A.0171.2009.0403.0118 04/03/2009
[    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x7f700 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-DFFFF uncachable
[    0.000000]   E0000-E0FFF write-protect
[    0.000000]   E1000-E7FFF uncachable
[    0.000000]   E8000-E8FFF write-protect
[    0.000000]   E9000-EFFFF uncachable
[    0.000000]   F0000-F0FFF write-protect
[    0.000000]   F1000-F7FFF uncachable
[    0.000000]   F8000-F8FFF write-protect
[    0.000000]   F9000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask 080000000 write-back
[    0.000000]   1 base 07F800000 mask 0FF800000 uncachable
[    0.000000]   2 base 07F700000 mask 0FFF00000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2040MB, range: 8MB, type UC
[    0.000000] reg 2, base: 2039MB, range: 1MB, type UC
[    0.000000] total RAM covered: 2039M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K 	chunk_size: 16M 	num_reg: 3  	lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2039MB, range: 1MB, type UC
[    0.000000] reg 2, base: 2040MB, range: 8MB, type UC
[    0.000000] found SMP MP-table at [mem 0x000fe200-0x000fe20f] mapped at [ffff8800000fe200]
[    0.000000] initial memory mapped: [mem 0x00000000-0x1fffffff]
[    0.000000] Base memory trampoline at [ffff880000089000] 89000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0x7f6fffff]
[    0.000000]  [mem 0x00000000-0x7f5fffff] page 2M
[    0.000000]  [mem 0x7f600000-0x7f6fffff] page 4k
[    0.000000] kernel direct mapping tables up to 0x7f6fffff @ [mem 0x1fffc000-0x1fffffff]
[    0.000000] RAMDISK: [mem 0x362e2000-0x37168fff]
[    0.000000] ACPI: RSDP 00000000000fe020 00014 (v00 INTEL )
[    0.000000] ACPI: RSDT 000000007f6fd038 0003C (v01 INTEL  D945GLF2 000000AB      01000013)
[    0.000000] ACPI: FACP 000000007f6fc000 00074 (v01 INTEL  D945GLF2 000000AB MSFT 01000013)
[    0.000000] ACPI: DSDT 000000007f6f7000 045EC (v01 INTEL  D945GLF2 000000AB MSFT 01000013)
[    0.000000] ACPI: FACS 000000007f6a3000 00040
[    0.000000] ACPI: APIC 000000007f6f6000 00078 (v01 INTEL  D945GLF2 000000AB MSFT 01000013)
[    0.000000] ACPI: WDDT 000000007f6f5000 00040 (v01 INTEL  D945GLF2 000000AB MSFT 01000013)
[    0.000000] ACPI: MCFG 000000007f6f4000 0003C (v01 INTEL  D945GLF2 000000AB MSFT 01000013)
[    0.000000] ACPI: ASF! 000000007f6f3000 000A6 (v32 INTEL  D945GLF2 000000AB MSFT 01000013)
[    0.000000] ACPI: HPET 000000007f6f2000 00038 (v01 INTEL  D945GLF2 000000AB MSFT 01000013)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000007f6fffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x7f6fffff]
[    0.000000]   NODE_DATA [mem 0x7f65c000-0x7f65ffff]
[    0.000000]  [ffffea0000000000-ffffea0001ffffff] PMD -> [ffff88007cc00000-ffff88007ebfffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00010000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   empty
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00010000-0x0008efff]
[    0.000000]   node   0: [mem 0x00100000-0x7f526fff]
[    0.000000]   node   0: [mem 0x7f52f000-0x7f5befff]
[    0.000000]   node   0: [mem 0x7f5c3000-0x7f65ffff]
[    0.000000]   node   0: [mem 0x7f6f0000-0x7f6f1fff]
[    0.000000]   node   0: [mem 0x7f6ff000-0x7f6fffff]
[    0.000000] On node 0 totalpages: 521686
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 6 pages reserved
[    0.000000]   DMA zone: 3897 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 8092 pages used for memmap
[    0.000000]   DMA32 zone: 509627 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000008f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 000000007f527000 - 000000007f52f000
[    0.000000] PM: Registered nosave memory: 000000007f5bf000 - 000000007f5c3000
[    0.000000] PM: Registered nosave memory: 000000007f660000 - 000000007f6f0000
[    0.000000] PM: Registered nosave memory: 000000007f6f2000 - 000000007f6ff000
[    0.000000] e820: [mem 0x80000000-0xefffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88007f200000 s83584 r8192 d22912 u524288
[    0.000000] pcpu-alloc: s83584 r8192 d22912 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 513524
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-3.5.0-22-generic root=UUID=ff204e15-e503-4ac9-aef0-28a8513a8e7c ro
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] __ex_table already sorted, skipping sort
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 2022804k/2087936k available (6719k kernel code, 1192k absent, 63940k reserved, 6451k data, 932k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:712 16
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 8388608 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1596.022 MHz processor.
[    0.004009] Calibrating delay loop (skipped), value calculated using timer frequency.. 3192.04 BogoMIPS (lpj=6384088)
[    0.004102] pid_max: default: 32768 minimum: 301
[    0.004218] Security Framework initialized
[    0.004304] AppArmor: AppArmor initialized
[    0.004348] Yama: becoming mindful.
[    0.004923] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.008076] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.009063] Mount-cache hash table entries: 256
[    0.009699] Initializing cgroup subsys cpuacct
[    0.009759] Initializing cgroup subsys memory
[    0.009826] Initializing cgroup subsys devices
[    0.009873] Initializing cgroup subsys freezer
[    0.009917] Initializing cgroup subsys blkio
[    0.009963] Initializing cgroup subsys perf_event
[    0.010081] Disabled fast string operations
[    0.010133] CPU: Physical Processor ID: 0
[    0.010175] CPU: Processor Core ID: 0
[    0.010219] mce: CPU supports 5 MCE banks
[    0.010275] CPU0: Thermal monitoring enabled (TM1)
[    0.010325] using mwait in idle threads.
[    0.013600] ACPI: Core revision 20120320
[    0.020033] ftrace: allocating 25143 entries in 99 pages
[    0.040588] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.081668] CPU0: Intel(R) Atom(TM) CPU  330   @ 1.60GHz stepping 02
[    0.084004] Performance Events: PEBS fmt0+, LBR disabled due to erratumAtom events, Intel PMU driver.
[    0.084004] ... version:                3
[    0.084004] ... bit width:              40
[    0.084004] ... generic registers:      2
[    0.084004] ... value mask:             000000ffffffffff
[    0.084004] ... max period:             000000007fffffff
[    0.084004] ... fixed-purpose events:   3
[    0.084004] ... event mask:             0000000700000003
[    0.084004] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.008000] Disabled fast string operations
[    0.084004] Booting Node   0, Processors  #1
[    0.094691] TSC synchronization [CPU#0 -> CPU#1]:
[    0.094811] Measured 108 cycles TSC warp between CPUs, turning off TSC clock.
[    0.094859] Marking TSC unstable due to check_tsc_sync_source failed
[    0.008000] Disabled fast string operations
[    0.095260]  #2 #3 Ok.
[    0.008000] Disabled fast string operations
[    0.117945] Brought up 4 CPUs
[    0.118035] Total of 4 processors activated (12768.17 BogoMIPS).
[    0.120288] devtmpfs: initialized
[    0.124597] EVM: security.selinux
[    0.124643] EVM: security.SMACK64
[    0.124683] EVM: security.capability
[    0.124770] PM: Registering ACPI NVS region [mem 0x7f660000-0x7f6effff] (589824 bytes)
[    0.126593] dummy: 
[    0.126693] RTC time: 13:11:50, date: 02/05/13
[    0.126851] NET: Registered protocol family 16
[    0.126930] Trying to unpack rootfs image as initramfs...
[    0.128485] ACPI: bus type pci registered
[    0.128761] PCI: MMCONFIG for domain 0000 [bus 00-7f] at [mem 0xf0000000-0xf7ffffff] (base 0xf0000000)
[    0.128834] PCI: MMCONFIG at [mem 0xf0000000-0xf7ffffff] reserved in E820
[    0.153752] PCI: Using configuration type 1 for base access
[    0.160071] bio: create slab <bio-0> at 0
[    0.160301] ACPI: Added _OSI(Module Device)
[    0.160357] ACPI: Added _OSI(Processor Device)
[    0.160405] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.160452] ACPI: Added _OSI(Processor Aggregator Device)
[    0.163183] ACPI: EC: Look up EC in DSDT
[    0.170387] ACPI: Interpreter enabled
[    0.170449] ACPI: (supports S0 S1 S3 S4 S5)
[    0.170701] ACPI: Using IOAPIC for interrupt routing
[    0.184579] ACPI: No dock devices found.
[    0.184648] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.187461] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.192657] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
[    0.192721] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
[    0.192783] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.192858] pci_root PNP0A03:00: host bridge window [mem 0x000e0000-0x000effff]
[    0.192933] pci_root PNP0A03:00: host bridge window [mem 0xf8000000-0xfebfffff]
[    0.193638] pci_root PNP0A03:00: host bridge window [mem 0x80000000-0xf0000000]
[    0.193846] PCI host bridge to bus 0000:00
[    0.193900] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.193954] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.194006] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.194060] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000effff]
[    0.194125] pci_bus 0000:00: root bus resource [mem 0xf8000000-0xfebfffff]
[    0.194188] pci_bus 0000:00: root bus resource [mem 0x80000000-0xf0000000]
[    0.194264] pci 0000:00:00.0: [8086:2770] type 00 class 0x060000
[    0.194361] pci 0000:00:02.0: [8086:2772] type 00 class 0x030000
[    0.194386] pci 0000:00:02.0: reg 10: [mem 0x88300000-0x8837ffff]
[    0.194402] pci 0000:00:02.0: reg 14: [io  0x30e0-0x30e7]
[    0.194419] pci 0000:00:02.0: reg 18: [mem 0x80000000-0x87ffffff pref]
[    0.194433] pci 0000:00:02.0: reg 1c: [mem 0x88380000-0x8839ffff]
[    0.194554] pci 0000:00:1c.0: [8086:27d0] type 01 class 0x060400
[    0.194672] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.194729] pci 0000:00:1c.2: [8086:27d4] type 01 class 0x060400
[    0.194849] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.194910] pci 0000:00:1c.3: [8086:27d6] type 01 class 0x060400
[    0.195024] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.195072] pci 0000:00:1d.0: [8086:27c8] type 00 class 0x0c0300
[    0.195135] pci 0000:00:1d.0: reg 20: [io  0x3080-0x309f]
[    0.195196] pci 0000:00:1d.1: [8086:27c9] type 00 class 0x0c0300
[    0.195260] pci 0000:00:1d.1: reg 20: [io  0x3060-0x307f]
[    0.195320] pci 0000:00:1d.2: [8086:27ca] type 00 class 0x0c0300
[    0.195381] pci 0000:00:1d.2: reg 20: [io  0x3040-0x305f]
[    0.195443] pci 0000:00:1d.3: [8086:27cb] type 00 class 0x0c0300
[    0.195516] pci 0000:00:1d.3: reg 20: [io  0x3020-0x303f]
[    0.195592] pci 0000:00:1d.7: [8086:27cc] type 00 class 0x0c0320
[    0.195625] pci 0000:00:1d.7: reg 10: [mem 0x883a0000-0x883a03ff]
[    0.195745] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.195785] pci 0000:00:1e.0: [8086:244e] type 01 class 0x060401
[    0.195893] pci 0000:00:1f.0: [8086:27b8] type 00 class 0x060100
[    0.196052] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0680 (mask 007f)
[    0.196217] pci 0000:00:1f.1: [8086:27df] type 00 class 0x01018a
[    0.196251] pci 0000:00:1f.1: reg 10: [io  0x30d8-0x30df]
[    0.196273] pci 0000:00:1f.1: reg 14: [io  0x30f4-0x30f7]
[    0.196292] pci 0000:00:1f.1: reg 18: [io  0x30d0-0x30d7]
[    0.196310] pci 0000:00:1f.1: reg 1c: [io  0x30f0-0x30f3]
[    0.196327] pci 0000:00:1f.1: reg 20: [io  0x30b0-0x30bf]
[    0.196396] pci 0000:00:1f.2: [8086:27c0] type 00 class 0x01018f
[    0.196422] pci 0000:00:1f.2: reg 10: [io  0x30c8-0x30cf]
[    0.196439] pci 0000:00:1f.2: reg 14: [io  0x30ec-0x30ef]
[    0.196457] pci 0000:00:1f.2: reg 18: [io  0x30c0-0x30c7]
[    0.196473] pci 0000:00:1f.2: reg 1c: [io  0x30e8-0x30eb]
[    0.196490] pci 0000:00:1f.2: reg 20: [io  0x30a0-0x30af]
[    0.196551] pci 0000:00:1f.2: PME# supported from D3hot
[    0.196585] pci 0000:00:1f.3: [8086:27da] type 00 class 0x0c0500
[    0.196658] pci 0000:00:1f.3: reg 20: [io  0x3000-0x301f]
[    0.196803] pci 0000:01:00.0: [10ec:8168] type 00 class 0x020000
[    0.196833] pci 0000:01:00.0: reg 10: [io  0x2000-0x20ff]
[    0.196876] pci 0000:01:00.0: reg 18: [mem 0x88200000-0x88200fff 64bit]
[    0.196906] pci 0000:01:00.0: reg 20: [mem 0x88000000-0x8800ffff 64bit pref]
[    0.196928] pci 0000:01:00.0: reg 30: [mem 0xfffe0000-0xffffffff pref]
[    0.197031] pci 0000:01:00.0: supports D1 D2
[    0.197042] pci 0000:01:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.204089] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    0.204160] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.204172] pci 0000:00:1c.0:   bridge window [mem 0x88200000-0x882fffff]
[    0.204187] pci 0000:00:1c.0:   bridge window [mem 0x88000000-0x880fffff 64bit pref]
[    0.204265] pci 0000:00:1c.2: PCI bridge to [bus 02-02]
[    0.204400] pci 0000:00:1c.3: PCI bridge to [bus 03-03]
[    0.204521] pci 0000:04:00.0: [105a:3570] type 00 class 0x010400
[    0.204556] pci 0000:04:00.0: reg 10: [io  0x1400-0x147f]
[    0.204587] pci 0000:04:00.0: reg 18: [io  0x1000-0x10ff]
[    0.204608] pci 0000:04:00.0: reg 1c: [mem 0x88120000-0x88120fff]
[    0.204628] pci 0000:04:00.0: reg 20: [mem 0x88100000-0x8811ffff]
[    0.204659] pci 0000:04:00.0: reg 30: [mem 0xffff0000-0xffffffff pref]
[    0.204715] pci 0000:04:00.0: supports D1
[    0.204787] pci 0000:00:1e.0: PCI bridge to [bus 04-04] (subtractive decode)
[    0.204845] pci 0000:00:1e.0:   bridge window [io  0x1000-0x1fff]
[    0.204856] pci 0000:00:1e.0:   bridge window [mem 0x88100000-0x881fffff]
[    0.204872] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.204880] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.204889] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.204898] pci 0000:00:1e.0:   bridge window [mem 0x000e0000-0x000effff] (subtractive decode)
[    0.204907] pci 0000:00:1e.0:   bridge window [mem 0xf8000000-0xfebfffff] (subtractive decode)
[    0.204915] pci 0000:00:1e.0:   bridge window [mem 0x80000000-0xf0000000] (subtractive decode)
[    0.204963] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.205484] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P32_._PRT]
[    0.206013] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    0.206191] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX2._PRT]
[    0.206365] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX3._PRT]
[    0.206654]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.206726]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.206795] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.219853] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
[    0.220427] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.221024] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12)
[    0.221537] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 *10 11 12)
[    0.222051] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.222687] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 *9 10 11 12)
[    0.223192] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.223835] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 *9 10 11 12)
[    0.224534] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.224534] vgaarb: loaded
[    0.224534] vgaarb: bridge control possible 0000:00:02.0
[    0.225049] SCSI subsystem initialized
[    0.225242] libata version 3.00 loaded.
[    0.225242] ACPI: bus type usb registered
[    0.225242] usbcore: registered new interface driver usbfs
[    0.225242] usbcore: registered new interface driver hub
[    0.225242] usbcore: registered new device driver usb
[    0.225242] PCI: Using ACPI for IRQ routing
[    0.230984] PCI: pci_cache_line_size set to 64 bytes
[    0.231141] Expanded resource reserved due to conflict with PCI Bus 0000:00
[    0.231203] e820: reserve RAM buffer [mem 0x0008f000-0x0008ffff]
[    0.231211] e820: reserve RAM buffer [mem 0x7f527000-0x7fffffff]
[    0.231219] e820: reserve RAM buffer [mem 0x7f5bf000-0x7fffffff]
[    0.231227] e820: reserve RAM buffer [mem 0x7f660000-0x7fffffff]
[    0.231234] e820: reserve RAM buffer [mem 0x7f6f2000-0x7fffffff]
[    0.231240] e820: reserve RAM buffer [mem 0x7f700000-0x7fffffff]
[    0.231639] NetLabel: Initializing
[    0.231698] NetLabel:  domain hash size = 128
[    0.231745] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.231834] NetLabel:  unlabeled traffic allowed by default
[    0.232141] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.232211] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.232366] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.244120] Switching to clocksource hpet
[    0.271640] AppArmor: AppArmor Filesystem Enabled
[    0.271790] pnp: PnP ACPI init
[    0.271881] ACPI: bus type pnp registered
[    0.273804] pnp 00:00: [bus 00-ff]
[    0.273815] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.273822] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.273828] pnp 00:00: [io  0x0d00-0xffff window]
[    0.273835] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.273841] pnp 00:00: [mem 0x000e0000-0x000effff window]
[    0.273847] pnp 00:00: [mem 0xf8000000-0xfebfffff window]
[    0.273853] pnp 00:00: [mem 0x80000000-0xf0000000 window]
[    0.273978] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.274017] pnp 00:01: [mem 0xf0000000-0xf3ffffff]
[    0.274023] pnp 00:01: [mem 0xfed13000-0xfed13fff]
[    0.274029] pnp 00:01: [mem 0xfed14000-0xfed17fff]
[    0.274035] pnp 00:01: [mem 0xfed18000-0xfed18fff]
[    0.274040] pnp 00:01: [mem 0xfed19000-0xfed19fff]
[    0.274046] pnp 00:01: [mem 0xfed1c000-0xfed1ffff]
[    0.274052] pnp 00:01: [mem 0xfed20000-0xfed3ffff]
[    0.274057] pnp 00:01: [mem 0xfed45000-0xfed99fff]
[    0.274063] pnp 00:01: [mem 0x000c0000-0x000dffff]
[    0.274069] pnp 00:01: [mem 0x000e0000-0x000fffff]
[    0.274204] system 00:01: [mem 0xf0000000-0xf3ffffff] could not be reserved
[    0.274261] system 00:01: [mem 0xfed13000-0xfed13fff] has been reserved
[    0.274311] system 00:01: [mem 0xfed14000-0xfed17fff] has been reserved
[    0.274360] system 00:01: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.274412] system 00:01: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.274470] system 00:01: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.274528] system 00:01: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.274582] system 00:01: [mem 0xfed45000-0xfed99fff] has been reserved
[    0.274634] system 00:01: [mem 0x000c0000-0x000dffff] could not be reserved
[    0.274685] system 00:01: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.274738] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.275090] pnp 00:02: [io  0x0000-0x000f]
[    0.275097] pnp 00:02: [io  0x0081-0x0083]
[    0.275103] pnp 00:02: [io  0x0087]
[    0.275118] pnp 00:02: [io  0x0089-0x008b]
[    0.275123] pnp 00:02: [io  0x008f]
[    0.275129] pnp 00:02: [io  0x00c0-0x00df]
[    0.275135] pnp 00:02: [dma 4]
[    0.275217] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.275250] pnp 00:03: [io  0x0070-0x0071]
[    0.275257] pnp 00:03: [io  0x0074-0x0077]
[    0.275285] pnp 00:03: [irq 8]
[    0.275355] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.275390] pnp 00:04: [io  0x00f0]
[    0.275406] pnp 00:04: [irq 13]
[    0.275482] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.275517] pnp 00:05: [io  0x0061]
[    0.275588] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.275623] pnp 00:06: [io  0x0500-0x053f]
[    0.275630] pnp 00:06: [io  0x0400-0x047f]
[    0.275635] pnp 00:06: [io  0x0092]
[    0.275640] pnp 00:06: [io  0x0680-0x06ff]
[    0.275646] pnp 00:06: [io  0x0010-0x001f]
[    0.275651] pnp 00:06: [io  0x0072-0x0073]
[    0.275656] pnp 00:06: [io  0x0080]
[    0.275662] pnp 00:06: [io  0x0084-0x0086]
[    0.275667] pnp 00:06: [io  0x0088]
[    0.275672] pnp 00:06: [io  0x008c-0x008e]
[    0.275678] pnp 00:06: [io  0x0090-0x009f]
[    0.275814] system 00:06: [io  0x0500-0x053f] has been reserved
[    0.275868] system 00:06: [io  0x0400-0x047f] has been reserved
[    0.275916] system 00:06: [io  0x0680-0x06ff] has been reserved
[    0.275968] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.276161] pnp 00:07: [io  0x0060]
[    0.276168] pnp 00:07: [io  0x0064]
[    0.276276] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.276934] pnp 00:08: [mem 0xfec00000-0xfec000ff]
[    0.277028] pnp 00:08: Plug and Play ACPI device, IDs PNP0003 (active)
[    0.277095] pnp 00:09: [mem 0xfed00000-0xfed003ff]
[    0.277175] pnp 00:09: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.277269] pnp: PnP ACPI: found 10 devices
[    0.277315] ACPI: ACPI bus type pnp unregistered
[    0.288829] pci 0000:01:00.0: no compatible bridge window for [mem 0xfffe0000-0xffffffff pref]
[    0.288910] pci 0000:04:00.0: no compatible bridge window for [mem 0xffff0000-0xffffffff pref]
[    0.289021] pci 0000:00:1c.2: bridge window [io  0x1000-0x0fff] to [bus 02-02] add_size 1000
[    0.289031] pci 0000:00:1c.2: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 02-02] add_size 200000
[    0.289039] pci 0000:00:1c.2: bridge window [mem 0x00100000-0x000fffff] to [bus 02-02] add_size 200000
[    0.289056] pci 0000:00:1c.3: bridge window [io  0x1000-0x0fff] to [bus 03-03] add_size 1000
[    0.289064] pci 0000:00:1c.3: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 03-03] add_size 200000
[    0.289072] pci 0000:00:1c.3: bridge window [mem 0x00100000-0x000fffff] to [bus 03-03] add_size 200000
[    0.289123] pci 0000:00:1c.2: res[14]=[mem 0x00100000-0x000fffff] get_res_add_size add_size 200000
[    0.289131] pci 0000:00:1c.2: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.289138] pci 0000:00:1c.3: res[14]=[mem 0x00100000-0x000fffff] get_res_add_size add_size 200000
[    0.289145] pci 0000:00:1c.3: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.289152] pci 0000:00:1c.2: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.289158] pci 0000:00:1c.3: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.289171] pci 0000:00:1c.2: BAR 14: assigned [mem 0x88400000-0x885fffff]
[    0.289226] pci 0000:00:1c.2: BAR 15: assigned [mem 0x88600000-0x887fffff 64bit pref]
[    0.289290] pci 0000:00:1c.3: BAR 14: assigned [mem 0x88800000-0x889fffff]
[    0.289343] pci 0000:00:1c.3: BAR 15: assigned [mem 0x88a00000-0x88bfffff 64bit pref]
[    0.289407] pci 0000:00:1e.0: BAR 15: assigned [mem 0x88c00000-0x88cfffff pref]
[    0.289471] pci 0000:00:1c.2: BAR 13: assigned [io  0x4000-0x4fff]
[    0.289522] pci 0000:00:1c.3: BAR 13: assigned [io  0x5000-0x5fff]
[    0.289584] pci 0000:01:00.0: BAR 6: assigned [mem 0x88020000-0x8803ffff pref]
[    0.289649] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    0.289700] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.289751] pci 0000:00:1c.0:   bridge window [mem 0x88200000-0x882fffff]
[    0.289802] pci 0000:00:1c.0:   bridge window [mem 0x88000000-0x880fffff 64bit pref]
[    0.289866] pci 0000:00:1c.2: PCI bridge to [bus 02-02]
[    0.289913] pci 0000:00:1c.2:   bridge window [io  0x4000-0x4fff]
[    0.289964] pci 0000:00:1c.2:   bridge window [mem 0x88400000-0x885fffff]
[    0.290015] pci 0000:00:1c.2:   bridge window [mem 0x88600000-0x887fffff 64bit pref]
[    0.290079] pci 0000:00:1c.3: PCI bridge to [bus 03-03]
[    0.290126] pci 0000:00:1c.3:   bridge window [io  0x5000-0x5fff]
[    0.290176] pci 0000:00:1c.3:   bridge window [mem 0x88800000-0x889fffff]
[    0.290227] pci 0000:00:1c.3:   bridge window [mem 0x88a00000-0x88bfffff 64bit pref]
[    0.290299] pci 0000:04:00.0: BAR 6: assigned [mem 0x88c00000-0x88c0ffff pref]
[    0.290360] pci 0000:00:1e.0: PCI bridge to [bus 04-04]
[    0.290407] pci 0000:00:1e.0:   bridge window [io  0x1000-0x1fff]
[    0.290457] pci 0000:00:1e.0:   bridge window [mem 0x88100000-0x881fffff]
[    0.290508] pci 0000:00:1e.0:   bridge window [mem 0x88c00000-0x88cfffff pref]
[    0.290659] pci 0000:00:1e.0: setting latency timer to 64
[    0.290669] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.290675] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.290681] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.290687] pci_bus 0000:00: resource 7 [mem 0x000e0000-0x000effff]
[    0.290693] pci_bus 0000:00: resource 8 [mem 0xf8000000-0xfebfffff]
[    0.290699] pci_bus 0000:00: resource 9 [mem 0x80000000-0xf0000000]
[    0.290706] pci_bus 0000:01: resource 0 [io  0x2000-0x2fff]
[    0.290712] pci_bus 0000:01: resource 1 [mem 0x88200000-0x882fffff]
[    0.290718] pci_bus 0000:01: resource 2 [mem 0x88000000-0x880fffff 64bit pref]
[    0.290725] pci_bus 0000:02: resource 0 [io  0x4000-0x4fff]
[    0.290731] pci_bus 0000:02: resource 1 [mem 0x88400000-0x885fffff]
[    0.290737] pci_bus 0000:02: resource 2 [mem 0x88600000-0x887fffff 64bit pref]
[    0.290744] pci_bus 0000:03: resource 0 [io  0x5000-0x5fff]
[    0.290750] pci_bus 0000:03: resource 1 [mem 0x88800000-0x889fffff]
[    0.290756] pci_bus 0000:03: resource 2 [mem 0x88a00000-0x88bfffff 64bit pref]
[    0.290763] pci_bus 0000:04: resource 0 [io  0x1000-0x1fff]
[    0.290769] pci_bus 0000:04: resource 1 [mem 0x88100000-0x881fffff]
[    0.290775] pci_bus 0000:04: resource 2 [mem 0x88c00000-0x88cfffff pref]
[    0.290781] pci_bus 0000:04: resource 4 [io  0x0000-0x0cf7]
[    0.290787] pci_bus 0000:04: resource 5 [io  0x0d00-0xffff]
[    0.290793] pci_bus 0000:04: resource 6 [mem 0x000a0000-0x000bffff]
[    0.290799] pci_bus 0000:04: resource 7 [mem 0x000e0000-0x000effff]
[    0.290805] pci_bus 0000:04: resource 8 [mem 0xf8000000-0xfebfffff]
[    0.290811] pci_bus 0000:04: resource 9 [mem 0x80000000-0xf0000000]
[    0.290912] NET: Registered protocol family 2
[    0.291226] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.293094] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.297255] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.298263] TCP: Hash tables configured (established 262144 bind 65536)
[    0.298314] TCP: reno registered
[    0.298394] UDP hash table entries: 1024 (order: 3, 32768 bytes)
[    0.298485] UDP-Lite hash table entries: 1024 (order: 3, 32768 bytes)
[    0.298767] NET: Registered protocol family 1
[    0.298884] pci 0000:00:02.0: Boot video device
[    0.299279] PCI: CLS mismatch (64 != 4), using 64 bytes
[    0.300727] audit: initializing netlink socket (disabled)
[    0.300807] type=2000 audit(1360069910.296:1): initialized
[    0.345044] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.350048] VFS: Disk quotas dquot_6.5.2
[    0.350230] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.351871] fuse init (API version 7.19)
[    0.352235] msgmni has been set to 3950
[    0.353759] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.353944] io scheduler noop registered
[    0.353993] io scheduler deadline registered (default)
[    0.354119] io scheduler cfq registered
[    0.354495] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.354674] pcieport 0000:00:1c.2: irq 41 for MSI/MSI-X
[    0.354850] pcieport 0000:00:1c.3: irq 42 for MSI/MSI-X
[    0.355024] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.355129] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.355319] intel_idle: MWAIT substates: 0x10
[    0.355356] intel_idle: v0.4 model 0x1C
[    0.355360] intel_idle: lapic_timer_reliable_states 0x2
[    0.355561] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input0
[    0.355634] ACPI: Sleep Button [SLPB]
[    0.355802] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.355868] ACPI: Power Button [PWRF]
[    0.362150] GHES: HEST is not enabled!
[    0.362433] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.366480] Linux agpgart interface v0.103
[    0.366652] agpgart-intel 0000:00:00.0: Intel 945G Chipset
[    0.366806] agpgart-intel 0000:00:00.0: detected gtt size: 131072K total, 131072K mappable
[    0.367191] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    0.367586] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0x80000000
[    0.371959] brd: module loaded
[    0.374437] loop: module loaded
[    0.374879] ata_piix 0000:00:1f.1: version 2.13
[    0.374986] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.375843] scsi0 : ata_piix
[    0.376199] scsi1 : ata_piix
[    0.377016] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x30b0 irq 14
[    0.377069] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x30b8 irq 15
[    0.377201] ata_piix 0000:00:1f.2: MAP [
[    0.377256]  P0 P2 P1 P3 ]
[    0.377584] ata2: port disabled--ignoring
[    0.532093] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.533007] scsi2 : ata_piix
[    0.533270] scsi3 : ata_piix
[    0.533698] ata3: SATA max UDMA/133 cmd 0x30c8 ctl 0x30ec bmdma 0x30a0 irq 19
[    0.533750] ata4: SATA max UDMA/133 cmd 0x30c0 ctl 0x30e8 bmdma 0x30a8 irq 19
[    0.534677] Fixed MDIO Bus: probed
[    0.534870] tun: Universal TUN/TAP device driver, 1.6
[    0.534915] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.535129] PPP generic driver version 2.4.2
[    0.535317] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.535477] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.535487] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.535547] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.535651] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.535712] ehci_hcd 0000:00:1d.7: debug port 1
[    0.539649] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    0.539699] ehci_hcd 0000:00:1d.7: irq 23, io mem 0x883a0000
[    0.548058] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.548212] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.548282] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.548345] usb usb1: Product: EHCI Host Controller
[    0.548393] usb usb1: Manufacturer: Linux 3.5.0-22-generic ehci_hcd
[    0.548447] usb usb1: SerialNumber: 0000:00:1d.7
[    0.548832] hub 1-0:1.0: USB hub found
[    0.548909] hub 1-0:1.0: 8 ports detected
[    0.549152] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.549250] uhci_hcd: USB Universal Host Controller Interface driver
[    0.549359] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.549367] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.549426] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.550206] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00003080
[    0.550345] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    0.550396] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.550458] usb usb2: Product: UHCI Host Controller
[    0.550507] usb usb2: Manufacturer: Linux 3.5.0-22-generic uhci_hcd
[    0.550556] usb usb2: SerialNumber: 0000:00:1d.0
[    0.550905] hub 2-0:1.0: USB hub found
[    0.550960] hub 2-0:1.0: 2 ports detected
[    0.551178] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.551186] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.551246] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.551346] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00003060
[    0.551481] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    0.551537] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.551601] usb usb3: Product: UHCI Host Controller
[    0.551650] usb usb3: Manufacturer: Linux 3.5.0-22-generic uhci_hcd
[    0.551698] usb usb3: SerialNumber: 0000:00:1d.1
[    0.552076] hub 3-0:1.0: USB hub found
[    0.552158] hub 3-0:1.0: 2 ports detected
[    0.552419] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.552429] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.552488] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.552620] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00003040
[    0.552754] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    0.552805] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.552866] usb usb4: Product: UHCI Host Controller
[    0.552914] usb usb4: Manufacturer: Linux 3.5.0-22-generic uhci_hcd
[    0.552964] usb usb4: SerialNumber: 0000:00:1d.2
[    0.553320] hub 4-0:1.0: USB hub found
[    0.553376] hub 4-0:1.0: 2 ports detected
[    0.553589] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.553598] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.553655] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.553774] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00003020
[    0.553904] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    0.553954] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.554021] usb usb5: Product: UHCI Host Controller
[    0.554067] usb usb5: Manufacturer: Linux 3.5.0-22-generic uhci_hcd
[    0.554120] usb usb5: SerialNumber: 0000:00:1d.3
[    0.554464] hub 5-0:1.0: USB hub found
[    0.554519] hub 5-0:1.0: 2 ports detected
[    0.554879] usbcore: registered new interface driver libusual
[    0.555018] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    0.558245] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.558331] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.558961] mousedev: PS/2 mouse device common for all mice
[    0.559528] rtc_cmos 00:03: RTC can wake from S4
[    0.559890] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.560001] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
[    0.560370] device-mapper: uevent: version 1.0.3
[    0.560744] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    0.560978] cpuidle: using governor ladder
[    0.561226] cpuidle: using governor menu
[    0.561283] EFI Variables Facility v0.08 2004-May-17
[    0.562227] ashmem: initialized
[    0.562682] TCP: cubic registered
[    0.563166] NET: Registered protocol family 10
[    0.563921] NET: Registered protocol family 17
[    0.564091] Key type dns_resolver registered
[    0.564734] PM: Hibernation image not present or could not be loaded.
[    0.564797] registered taskstats version 1
[    0.699223] ata4.00: ATA-8: WDC WD3202ABYS-01B7A0, 02.03B02, max UDMA/133
[    0.699289] ata4.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    0.705336] ata4.00: configured for UDMA/133
[    0.705786] scsi 3:0:0:0: Direct-Access     ATA      WDC WD3202ABYS-0 02.0 PQ: 0 ANSI: 5
[    0.706253] sd 3:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    0.706329] sd 3:0:0:0: Attached scsi generic sg0 type 0
[    0.706589] sd 3:0:0:0: [sda] Write Protect is off
[    0.706647] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.706756] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.727342]  sda: sda1 sda2 sda3
[    0.728587] sd 3:0:0:0: [sda] Attached SCSI disk
[    0.806374] Freeing initrd memory: 14876k freed
[    0.827866] Key type trusted registered
[    0.834313] Key type encrypted registered
[    0.841261]   Magic number: 1:344:179
[    0.841465] acpi device:0f: hash matches
[    0.841603] rtc_cmos 00:03: setting system clock to 2013-02-05 13:11:51 UTC (1360069911)
[    0.841895] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.841946] EDD information not available.
[    0.846113] Freeing unused kernel memory: 932k freed
[    0.846820] Write protecting the kernel read-only data: 12288k
[    0.859151] Freeing unused kernel memory: 1464k freed
[    0.869471] Freeing unused kernel memory: 1120k freed
[    0.927428] udevd[105]: starting version 175
[    1.039587] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.039937] r8169 0000:01:00.0: irq 43 for MSI/MSI-X
[    1.040696] r8169 0000:01:00.0: eth0: RTL8168c/8111c at 0xffffc90000362000, 00:1c:c0:d0:e0:27, XID 1c4000c0 IRQ 43
[    1.040804] r8169 0000:01:00.0: eth0: jumbo features [frames: 6128 bytes, tx checksumming: ko]
[    1.100898] sata_promise 0000:04:00.0: version 2.12
[    1.102988] scsi4 : sata_promise
[    1.103669] scsi5 : sata_promise
[    1.105142] scsi6 : sata_promise
[    1.105478] ata5: SATA max UDMA/133 mmio m4096@0x88120000 ata 0x88120200 irq 21
[    1.105571] ata6: SATA max UDMA/133 mmio m4096@0x88120000 ata 0x88120280 irq 21
[    1.105652] ata7: PATA max UDMA/133 mmio m4096@0x88120000 ata 0x88120300 irq 21
[    1.172122] usb 4-1: new low-speed USB device number 2 using uhci_hcd
[    1.348765] usb 4-1: New USB device found, idVendor=046d, idProduct=c315
[    1.348824] usb 4-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.348874] usb 4-1: Product: Logitech USB Keyboard
[    1.348919] usb 4-1: Manufacturer: Logitech
[    1.471952] EXT4-fs (sda3): mounted filesystem with ordered data mode. Opts: (null)
[    1.580090] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.588515] ata5.00: ATA-7: SAMSUNG HD103UJ, 1AA01118, max UDMA7
[    1.588572] ata5.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 0/32)
[    1.596490] ata5.00: configured for UDMA/133
[    1.596861] scsi 4:0:0:0: Direct-Access     ATA      SAMSUNG HD103UJ  1AA0 PQ: 0 ANSI: 5
[    1.597507] sd 4:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.597611] sd 4:0:0:0: Attached scsi generic sg1 type 0
[    1.597863] sd 4:0:0:0: [sdb] Write Protect is off
[    1.597941] sd 4:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.598147] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.616365]  sdb: sdb1
[    1.617305] sd 4:0:0:0: [sdb] Attached SCSI disk
[    2.128067] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.156565] ata6.00: ATA-8: WDC WD10EADS-00L5B1, 01.01A01, max UDMA/133
[    2.156616] ata6.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 0/32)
[    2.165137] ata6.00: configured for UDMA/133
[    2.165481] scsi 5:0:0:0: Direct-Access     ATA      WDC WD10EADS-00L 01.0 PQ: 0 ANSI: 5
[    2.166014] sd 5:0:0:0: [sdc] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    2.166150] sd 5:0:0:0: Attached scsi generic sg2 type 0
[    2.166533] sd 5:0:0:0: [sdc] Write Protect is off
[    2.166593] sd 5:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    2.166708] sd 5:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.187546]  sdc: sdc2
[    2.188346] sd 5:0:0:0: [sdc] Attached SCSI disk
[    2.335956] usbcore: registered new interface driver usbhid
[    2.336057] usbhid: USB HID core driver
[    4.124711] Adding 3906556k swap on /dev/sda2.  Priority:-1 extents:1 across:3906556k 
[    4.892394] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    5.077373] udevd[315]: starting version 175
[    5.807972] lp: driver loaded but no devices found
[    6.220714] microcode: CPU0 sig=0x106c2, pf=0x8, revision=0x213
[    6.243129] input: Logitech Logitech USB Keyboard as /devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0/input/input2
[    6.276375] hid-generic 0003:046D:C315.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech Logitech USB Keyboard] on usb-0000:00:1d.2-1/input0
[    6.552773] intel_rng: Firmware space is locked read-only. If you can't or
[    6.552773] intel_rng: don't want to disable this in firmware setup, and if
[    6.552773] intel_rng: you are certain that your system has a functional
[    6.552773] intel_rng: RNG, try using the 'no_fwh_detect' option.
[    6.795190] ACPI Warning: 0x00000000fed1f410-0x00000000fed1f414 SystemMemory conflicts with Region \_SB_.PCI0.SRCR 1 (20120320/utaddress-251)
[    6.795212] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    6.795220] lpc_ich: Resource conflict(s) found affecting iTCO_wdt
[    6.795230] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \GPE0 1 (20120320/utaddress-251)
[    6.795245] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    6.795255] ACPI Warning: 0x0000000000000500-0x000000000000053f SystemIO conflicts with Region \IGPO 1 (20120320/utaddress-251)
[    6.795268] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    6.795273] lpc_ich: Resource conflict(s) found affecting gpio_ich
[    6.852671] microcode: CPU1 sig=0x106c2, pf=0x8, revision=0x213
[    6.858854] microcode: CPU2 sig=0x106c2, pf=0x8, revision=0x213
[    6.865739] microcode: CPU3 sig=0x106c2, pf=0x8, revision=0x213
[    6.871336] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    6.971437] leds_ss4200: no LED devices found
[    7.092450] [drm] Initialized drm 1.1.0 20060810
[    7.302380] i915 0000:00:02.0: setting latency timer to 64
[    7.322976] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    7.322985] [drm] Driver supports precise vblank timestamp query.
[    7.323477] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    7.581105] type=1400 audit(1360069918.236:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=464 comm="apparmor_parser"
[    7.581132] type=1400 audit(1360069918.236:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=463 comm="apparmor_parser"
[    7.583679] type=1400 audit(1360069918.236:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=464 comm="apparmor_parser"
[    7.583705] type=1400 audit(1360069918.236:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=463 comm="apparmor_parser"
[    7.585148] type=1400 audit(1360069918.240:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=464 comm="apparmor_parser"
[    7.585229] type=1400 audit(1360069918.240:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=463 comm="apparmor_parser"
[    7.883976] [drm] initialized overlay support
[    8.038283] r8169 0000:01:00.0: eth0: link down
[    8.038331] r8169 0000:01:00.0: eth0: link down
[    8.039213] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    8.391637] fbcon: inteldrmfb (fb0) is primary device
[    8.470194] Console: switching to colour frame buffer device 240x67
[    8.472887] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro
[    8.498938] fb0: inteldrmfb frame buffer device
[    8.498945] drm: registered panic notifier
[    8.498975] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    8.755004] kjournald starting.  Commit interval 5 seconds
[    8.755738] EXT3-fs (sdc2): warning: maximal mount count reached, running e2fsck is recommended
[    8.756528] EXT3-fs (sdc2): using internal journal
[    8.756539] EXT3-fs (sdc2): recovery complete
[    8.756544] EXT3-fs (sdc2): mounted filesystem with ordered data mode
[    8.808983] EXT4-fs (sdb1): warning: maximal mount count reached, running e2fsck is recommended
[    8.858930] EXT4-fs (sdb1): recovery complete
[    8.858948] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[    9.666076] kjournald starting.  Commit interval 5 seconds
[    9.666442] EXT3-fs (sda1): using internal journal
[    9.666454] EXT3-fs (sda1): mounted filesystem with ordered data mode
[   10.085961] r8169 0000:01:00.0: eth0: link up
[   10.086745] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   10.166186] init: failsafe main process (681) killed by TERM signal
[   11.568992] type=1400 audit(1360069922.224:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=773 comm="apparmor_parser"
[   11.571196] type=1400 audit(1360069922.224:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=773 comm="apparmor_parser"
[   11.572971] type=1400 audit(1360069922.228:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=773 comm="apparmor_parser"
[   11.681656] type=1400 audit(1360069922.336:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=775 comm="apparmor_parser"

```

I have run a filesystem check with no errors. RAM and disks seem fine too. I don't know if the ACPI error is the problem but I would guess not since it skips past it in log 3 and still reset. 

The system is an Intel LittleFalls 2 board with an integrated dual-core Atom CPU, a Corsair HX Series PSU with plenty of power and a RAID controller. That is it I think, besides the disks that is.

---

### Post by TheForumTroll on 2013-03-23
:confused:

---

### Post by TheForumTroll on 2013-03-25
Anyone :?:

---

### Post by dino99 on 2013-03-25
how is it formated ?
but i'm not sure about what you mean by "resetting at boot" : is it ending the boot process normally, then reset itself, or else ?

to put my two cents here, i propose to install 3.8 kernel instead of 3.5 or 3.7, as it works way better (see ubuntu-x-swat/r-lts-backport ppa)

---

