---
title: "Lubuntu 14.04 20 mins boot time even with new Bhodi Linux dual boot. dmes"
date: 2016-03-05
forum: General Help
---

### Post by cheapodonuts on 2016-03-05
I've been having blank black screen slow boot issues on my tower PC for several months with Lubuntu 14.04, this is always after the PC being powered down over night or for more than approx 60 mins. Booting after a few mins powered down or even up to around one hour is no problem and usually takes less than 90 seconds to full desktop functionality . The long boot did somewhat improve once or twice with regular updates, but soon slowed down again. It's been 20 mins or so recently and I usually just leave it and go feed the cat and prepare my meal/make my ablutions/drive to Brazil via Sydney and back, ;) just to give it time. 
 Sometimes I will try hard resets, which used to work after one or three, but even that takes many trys now, up to nearly ten minutes.
 I installed Bhodi linux yesterday off a live disc purchades from the Linux Shop. Bhodi worked ok after install. But next morning and evening the 20 minute boot was back, even though Bhodi now shows on the system choices list, which eventually shows up.

Thanks in advance for any help guys. :)

```
-Computer-
Processor        : 2x AMD Athlon(tm) 64 X2 Dual Core Processor 4600+
Memory        : 1933MB (679MB used)
Operating System        : Ubuntu 14.04.4 LTS
User Name        : cheapo (cheapo)
Date/Time        : Sat 05 Mar 2016 23:10:31 GMT
-Display-
Resolution        : 1280x960 pixels
OpenGL Renderer        : Unknown
X11 Vendor        : The X.Org Foundation
-Multimedia-
Audio Adapter        : HDA-Intel - HDA NVidia
-Input Devices-
 Power Button
 Power Button
 AT Translated Set 2 keyboard
 Microsoft Microsoft Trackball Explorer®
 HDA NVidia Front Headphone
 HDA NVidia Line Out Side
 HDA NVidia Line Out CLFE
 HDA NVidia Line Out Surround
 HDA NVidia Line Out Front
 HDA NVidia Line
 HDA NVidia Rear Mic
 HDA NVidia Front Mic
-Printers (CUPS)-
HP-Deskjet-2050-J510-series        : <i>Default</i>
-SCSI Disks-
ATA WDC WD3200AAJS-6
TSSTcorp CDDVDW TS-H653Q
Generic USB SD Reader
Generic USB CF Reader
Generic USB SM Reader 
Generic USB MS Reader
```

dsmeg result

```
cheapo@cheapo-KX733AA-ABU-a6511-uk:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.13.0-80-generic (buildd@lgw01-42) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #124-Ubuntu SMP Tue Feb 23 02:25:15 UTC 2016 (Ubuntu 3.13.0-80.124-generic 3.13.11-ckt35)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009efff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009f000-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000f0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x0000000077edffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000077ee0000-0x0000000077ee2fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x0000000077ee3000-0x0000000077eeffff] ACPI data
[    0.000000] BIOS-e820: [mem 0x0000000077ef0000-0x0000000077efffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000078000000-0x000000007fffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000f0000000-0x00000000f3ffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000ffffffff] reserved
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 0.4 present.
[    0.000000] DMI: HP-Pavilion KX733AA-ABU a6511.uk/NARRA3, BIOS  5.14 06/20/2008
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0x77ee0 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FF80000000 write-back
[    0.000000]   1 disabled
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] found SMP MP-table at [mem 0x000f55f0-0x000f55ff] mapped at [c00f55f0]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] initial memory mapped: [mem 0x00000000-0x01ffffff]
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x37800000-0x379fffff]
[    0.000000]  [mem 0x37800000-0x379fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x34000000-0x377fffff]
[    0.000000]  [mem 0x34000000-0x377fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0x33ffffff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x33ffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x37a00000-0x37bfdfff]
[    0.000000]  [mem 0x37a00000-0x37bfdfff] page 4k
[    0.000000] BRK [0x01b9f000, 0x01b9ffff] PGTABLE
[    0.000000] RAMDISK: [mem 0x35c1c000-0x36e05fff]
[    0.000000] ACPI: RSDP 000f7740 000024 (v02 HPQOEM)
[    0.000000] ACPI: XSDT 77ee3100 000054 (v01 HPQOEM SLIC-CPC 42302E31 AWRD 00000000)
[    0.000000] ACPI: FACP 77ee7f40 0000F4 (v03 HPQOEM SLIC-CPC 42302E31 AWRD 00000000)
[    0.000000] ACPI: DSDT 77ee32c0 004C2F (v01 HPQOEM SLIC-CPC 00001000 MSFT 03000000)
[    0.000000] ACPI: FACS 77ee0000 000040
[    0.000000] ACPI: SLIC 77ee8180 000176 (v01 HPQOEM SLIC-CPC 42302E31 AWRD 00000000)
[    0.000000] ACPI: SSDT 77ee8340 000248 (v01 HPQOEM SLIC-CPC 00000001  LTP 00000001)
[    0.000000] ACPI: HPET 77ee8600 000038 (v01 HPQOEM SLIC-CPC 42302E31 AWRD 00000098)
[    0.000000] ACPI: MCFG 77ee8680 00003C (v01 HPQOEM SLIC-CPC 42302E31 AWRD 00000000)
[    0.000000] ACPI: APIC 77ee8080 000098 (v01 HPQOEM SLIC-CPC 42302E31 AWRD 00000000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1026MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] BRK [0x01ba0000, 0x01ba0fff] PGTABLE
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   Normal   [mem 0x01000000-0x37bfdfff]
[    0.000000]   HighMem  [mem 0x37bfe000-0x77edffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009efff]
[    0.000000]   node   0: [mem 0x00100000-0x77edffff]
[    0.000000] On node 0 totalpages: 491134
[    0.000000] free_area_init_node: node 0, pgdat c19a5880, node_mem_map f4d1c020
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3998 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 224254 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2054 pages used for memmap
[    0.000000]   HighMem zone: 262882 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfefff000
[    0.000000] smpboot: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000effff]
[    0.000000] PM: Registered nosave memory: [mem 0x000f0000-0x000fffff]
[    0.000000] e820: [mem 0x80000000-0xefffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @f7bba000 s35520 r0 d21824 u57344
[    0.000000] pcpu-alloc: s35520 r0 d21824 u57344 alloc=14*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 [0] 2 [0] 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 489350
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-80-generic root=UUID=b1e11c23-0ecc-4713-b2e7-3d47795907e2 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 3929848 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:00077ee0)
[    0.000000] Memory: 1913940K/1964536K available (6564K kernel code, 645K rwdata, 2776K rodata, 880K init, 924K bss, 50596K reserved, 1051528K highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff14000 - 0xfffff000   ( 940 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc19c3000 - 0xc1a9f000   ( 880 kB)
[    0.000000]       .data : 0xc1669740 - 0xc19c2740   (3428 kB)
[    0.000000]       .text : 0xc1000000 - 0xc1669740   (6565 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=8 to nr_cpu_ids=4.
[    0.000000] NR_IRQS:2304 nr_irqs:712 16
[    0.000000] CPU 0 irqstacks, hard=f7008000 soft=f700a000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 2411.114 MHz processor
[    0.000000] tsc: Marking TSC unstable due to TSCs unsynchronized
[    0.004005] Calibrating delay loop (skipped), value calculated using timer frequency.. 4822.22 BogoMIPS (lpj=9644456)
[    0.004008] pid_max: default: 32768 minimum: 301
[    0.004051] Security Framework initialized
[    0.004070] AppArmor: AppArmor initialized
[    0.004072] Yama: becoming mindful.
[    0.004131] Mount-cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.004133] Mountpoint-cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.004385] Initializing cgroup subsys memory
[    0.004393] Initializing cgroup subsys devices
[    0.004396] Initializing cgroup subsys freezer
[    0.004399] Initializing cgroup subsys blkio
[    0.004401] Initializing cgroup subsys perf_event
[    0.004404] Initializing cgroup subsys hugetlb
[    0.004431] CPU: Physical Processor ID: 0
[    0.004433] CPU: Processor Core ID: 0
[    0.004436] mce: CPU supports 5 MCE banks
[    0.004444] LVT offset 0 assigned for vector 0xf9
[    0.004448] process: using AMD E400 aware idle routine
[    0.004456] Last level iTLB entries: 4KB 512, 2MB 8, 4MB 4
[    0.004456] Last level dTLB entries: 4KB 512, 2MB 8, 4MB 4
[    0.004456] tlb_flushall_shift: 4
[    0.004753] Freeing SMP alternatives memory: 32K (c1a9f000 - c1aa7000)
[    0.005809] ACPI: Core revision 20131115
[    0.012324] ACPI: All ACPI Tables successfully acquired
[    0.016019] ftrace: allocating 27898 entries in 55 pages
[    0.028107] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.028645] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.070983] smpboot: CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 4600+ (fam: 0f, model: 6b, stepping: 02)
[    0.072000] Performance Events: AMD PMU driver.
[    0.072000] ... version:                0
[    0.072000] ... bit width:              48
[    0.072000] ... generic registers:      4
[    0.072000] ... value mask:             0000ffffffffffff
[    0.072000] ... max period:             00007fffffffffff
[    0.072000] ... fixed-purpose events:   0
[    0.072000] ... event mask:             000000000000000f
[    0.072000] CPU 1 irqstacks, hard=f7100000 soft=f7102000
[    0.072000] x86: Booting SMP configuration:
[    0.008000] Initializing CPU#1
[    0.080998] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.072000] .... node  #0, CPUs:      #1
[    0.160053] x86: Booted up 1 node, 2 CPUs
[    0.160056] smpboot: Total of 2 processors activated (9644.19 BogoMIPS)
[    0.160639] devtmpfs: initialized
[    0.160639] EVM: security.selinux
[    0.160639] EVM: security.SMACK64
[    0.160639] EVM: security.ima
[    0.160639] EVM: security.capability
[    0.160639] PM: Registering ACPI NVS region [mem 0x77ee0000-0x77ee2fff] (12288 bytes)
[    0.161427] pinctrl core: initialized pinctrl subsystem
[    0.161523] regulator-dummy: no parameters
[    0.161564] RTC time: 14:33:20, date: 03/05/16
[    0.161612] NET: Registered protocol family 16
[    0.161772] EISA bus registered
[    0.161774] cpuidle: using governor ladder
[    0.161775] cpuidle: using governor menu
[    0.161780] node 0 link 0: io port [8000, ffff]
[    0.161783] TOM: 0000000080000000 aka 2048M
[    0.161786] node 0 link 0: mmio [a0000, bffff]
[    0.161789] node 0 link 0: mmio [80000000, efffffff]
[    0.161791] node 0 link 0: mmio [f4000000, fe02ffff]
[    0.161794] node 0 link 0: mmio [f0000000, f04fffff]
[    0.161797] bus: [bus 00-04] on node 0 link 0
[    0.161799] bus: 00 [io  0x0000-0xffff]
[    0.161801] bus: 00 [mem 0x000a0000-0x000bffff]
[    0.161802] bus: 00 [mem 0x80000000-0xf3ffffff]
[    0.161804] bus: 00 [mem 0xf4000000-0xfcffffffff]
[    0.161855] ACPI: bus type PCI registered
[    0.161857] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.161937] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf0000000-0xf3ffffff] (base 0xf0000000)
[    0.161940] PCI: MMCONFIG at [mem 0xf0000000-0xf3ffffff] reserved in E820
[    0.161942] PCI: Using MMCONFIG for extended config space
[    0.161943] PCI: Using configuration type 1 for base access
[    0.162039] mtrr: your CPUs had inconsistent variable MTRR settings
[    0.162040] mtrr: probably your BIOS does not setup all CPUs.
[    0.162041] mtrr: corrected configuration.
[    0.164207] bio: create slab <bio-0> at 0
[    0.164207] ACPI: Added _OSI(Module Device)
[    0.164207] ACPI: Added _OSI(Processor Device)
[    0.164207] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.164207] ACPI: Added _OSI(Processor Aggregator Device)
[    0.169547] ACPI: Interpreter enabled
[    0.169561] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)
[    0.169576] ACPI: (supports S0 S1 S3 S4 S5)
[    0.169578] ACPI: Using IOAPIC for interrupt routing
[    0.169605] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.169749] ACPI: No dock devices found.
[    0.175885] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.175892] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.175898] acpi PNP0A08:00: _OSC failed (AE_NOT_FOUND); disabling ASPM
[    0.175988] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-3f] only partially covers this bridge
[    0.176179] PCI host bridge to bus 0000:00
[    0.176183] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.176186] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.176188] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.176191] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.176193] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000dffff]
[    0.176196] pci_bus 0000:00: root bus resource [mem 0x80000000-0xfebfffff]
[    0.176220] pci 0000:00:00.0: [10de:03ea] type 00 class 0x050000
[    0.176471] pci 0000:00:01.0: [10de:03e0] type 00 class 0x060100
[    0.176587] pci 0000:00:01.1: [10de:03eb] type 00 class 0x0c0500
[    0.176599] pci 0000:00:01.1: reg 0x10: [io  0xfc00-0xfc3f]
[    0.176614] pci 0000:00:01.1: reg 0x20: [io  0x1c00-0x1c3f]
[    0.176620] pci 0000:00:01.1: reg 0x24: [io  0x1c40-0x1c7f]
[    0.176648] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.176742] pci 0000:00:01.2: [10de:03f5] type 00 class 0x050000
[    0.176851] pci 0000:00:02.0: [10de:03f1] type 00 class 0x0c0310
[    0.176861] pci 0000:00:02.0: reg 0x10: [mem 0xfe02f000-0xfe02ffff]
[    0.176894] pci 0000:00:02.0: supports D1 D2
[    0.176897] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.176960] pci 0000:00:02.0: System wakeup disabled by ACPI
[    0.176996] pci 0000:00:02.1: [10de:03f2] type 00 class 0x0c0320
[    0.177007] pci 0000:00:02.1: reg 0x10: [mem 0xfe02e000-0xfe02e0ff]
[    0.177047] pci 0000:00:02.1: supports D1 D2
[    0.177049] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.177128] pci 0000:00:02.1: System wakeup disabled by ACPI
[    0.177172] pci 0000:00:04.0: [10de:03f3] type 01 class 0x060401
[    0.177262] pci 0000:00:04.0: System wakeup disabled by ACPI
[    0.177300] pci 0000:00:05.0: [10de:03f0] type 00 class 0x040300
[    0.177311] pci 0000:00:05.0: reg 0x10: [mem 0xfe024000-0xfe027fff]
[    0.177352] pci 0000:00:05.0: PME# supported from D3hot D3cold
[    0.177448] pci 0000:00:06.0: [10de:03ec] type 00 class 0x01018a
[    0.177470] pci 0000:00:06.0: reg 0x20: [io  0xf000-0xf00f]
[    0.177578] pci 0000:00:07.0: [10de:03ef] type 00 class 0x068000
[    0.177589] pci 0000:00:07.0: reg 0x10: [mem 0xfe02d000-0xfe02dfff]
[    0.177594] pci 0000:00:07.0: reg 0x14: [io  0xec00-0xec07]
[    0.177628] pci 0000:00:07.0: supports D1 D2
[    0.177630] pci 0000:00:07.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.177696] pci 0000:00:07.0: System wakeup disabled by ACPI
[    0.177735] pci 0000:00:08.0: [10de:03f6] type 00 class 0x010185
[    0.177744] pci 0000:00:08.0: reg 0x10: [io  0x09f0-0x09f7]
[    0.177749] pci 0000:00:08.0: reg 0x14: [io  0x0bf0-0x0bf3]
[    0.177753] pci 0000:00:08.0: reg 0x18: [io  0x0970-0x0977]
[    0.177758] pci 0000:00:08.0: reg 0x1c: [io  0x0b70-0x0b73]
[    0.177763] pci 0000:00:08.0: reg 0x20: [io  0xd800-0xd80f]
[    0.177768] pci 0000:00:08.0: reg 0x24: [mem 0xfe02c000-0xfe02cfff]
[    0.177871] pci 0000:00:08.1: [10de:03f6] type 00 class 0x010185
[    0.177880] pci 0000:00:08.1: reg 0x10: [io  0x09e0-0x09e7]
[    0.177884] pci 0000:00:08.1: reg 0x14: [io  0x0be0-0x0be3]
[    0.177889] pci 0000:00:08.1: reg 0x18: [io  0x0960-0x0967]
[    0.177894] pci 0000:00:08.1: reg 0x1c: [io  0x0b60-0x0b63]
[    0.177898] pci 0000:00:08.1: reg 0x20: [io  0xc400-0xc40f]
[    0.177903] pci 0000:00:08.1: reg 0x24: [mem 0xfe02b000-0xfe02bfff]
[    0.178015] pci 0000:00:09.0: [10de:03e8] type 01 class 0x060400
[    0.178043] pci 0000:00:09.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.178109] pci 0000:00:09.0: System wakeup disabled by ACPI
[    0.178152] pci 0000:00:0b.0: [10de:03e9] type 01 class 0x060400
[    0.178178] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.178241] pci 0000:00:0b.0: System wakeup disabled by ACPI
[    0.178279] pci 0000:00:0c.0: [10de:03e9] type 01 class 0x060400
[    0.178305] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.178368] pci 0000:00:0c.0: System wakeup disabled by ACPI
[    0.178402] pci 0000:00:0d.0: [10de:03d0] type 00 class 0x030000
[    0.178410] pci 0000:00:0d.0: reg 0x10: [mem 0xfb000000-0xfbffffff]
[    0.178416] pci 0000:00:0d.0: reg 0x14: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.178422] pci 0000:00:0d.0: reg 0x1c: [mem 0xfc000000-0xfcffffff 64bit]
[    0.178428] pci 0000:00:0d.0: reg 0x30: [mem 0x00000000-0x0001ffff pref]
[    0.178527] pci 0000:00:18.0: [1022:1100] type 00 class 0x060000
[    0.178620] pci 0000:00:18.1: [1022:1101] type 00 class 0x060000
[    0.178707] pci 0000:00:18.2: [1022:1102] type 00 class 0x060000
[    0.178797] pci 0000:00:18.3: [1022:1103] type 00 class 0x060000
[    0.178929] pci 0000:01:05.0: [11c1:5811] type 00 class 0x0c0010
[    0.178942] pci 0000:01:05.0: reg 0x10: [mem 0xfd7ff000-0xfd7fffff]
[    0.178993] pci 0000:01:05.0: supports D1 D2
[    0.178995] pci 0000:01:05.0: PME# supported from D0 D1 D2 D3hot
[    0.179053] pci 0000:00:04.0: PCI bridge to [bus 01] (subtractive decode)
[    0.179057] pci 0000:00:04.0:   bridge window [io  0xb000-0xbfff]
[    0.179061] pci 0000:00:04.0:   bridge window [mem 0xfd700000-0xfd7fffff]
[    0.179064] pci 0000:00:04.0:   bridge window [mem 0xfde00000-0xfdefffff pref]
[    0.179067] pci 0000:00:04.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.179070] pci 0000:00:04.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.179072] pci 0000:00:04.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.179075] pci 0000:00:04.0:   bridge window [mem 0x000c0000-0x000dffff] (subtractive decode)
[    0.179078] pci 0000:00:04.0:   bridge window [mem 0x80000000-0xfebfffff] (subtractive decode)
[    0.179111] pci 0000:00:09.0: PCI bridge to [bus 02]
[    0.179115] pci 0000:00:09.0:   bridge window [io  0xa000-0xafff]
[    0.179118] pci 0000:00:09.0:   bridge window [mem 0xfdd00000-0xfddfffff]
[    0.179122] pci 0000:00:09.0:   bridge window [mem 0xfdc00000-0xfdcfffff 64bit pref]
[    0.179156] pci 0000:00:0b.0: PCI bridge to [bus 03]
[    0.179160] pci 0000:00:0b.0:   bridge window [io  0x9000-0x9fff]
[    0.179163] pci 0000:00:0b.0:   bridge window [mem 0xfdb00000-0xfdbfffff]
[    0.179167] pci 0000:00:0b.0:   bridge window [mem 0xfda00000-0xfdafffff 64bit pref]
[    0.179199] pci 0000:00:0c.0: PCI bridge to [bus 04]
[    0.179202] pci 0000:00:0c.0:   bridge window [io  0x8000-0x8fff]
[    0.179205] pci 0000:00:0c.0:   bridge window [mem 0xfd900000-0xfd9fffff]
[    0.179209] pci 0000:00:0c.0:   bridge window [mem 0xfd800000-0xfd8fffff 64bit pref]
[    0.179218] pci_bus 0000:00: on NUMA node 0
[    0.179541] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.179594] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.179647] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.179702] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 *7 9 10 11 14 15)
[    0.179754] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.179805] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.179858] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.179910] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.179964] ACPI: PCI Interrupt Link [LIGP] (IRQs 5 *7 9 10 11 14 15)
[    0.180019] ACPI: PCI Interrupt Link [LP2P] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.180074] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 *10 11 14 15)
[    0.180128] ACPI: PCI Interrupt Link [LMAC] (IRQs *5 7 9 10 11 14 15)
[    0.180189] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 *11 14 15)
[    0.180242] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.180296] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 *7 9 10 11 14 15)
[    0.180356] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 10 *11 14 15)
[    0.180408] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.180463] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
[    0.180522] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 *10 11 14 15)
[    0.180622] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[    0.180710] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[    0.180797] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[    0.180883] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0
[    0.180969] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
[    0.181056] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
[    0.181147] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
[    0.181234] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
[    0.181321] ACPI: PCI Interrupt Link [AIGP] (IRQs 22 23) *0
[    0.181408] ACPI: PCI Interrupt Link [APCF] (IRQs 22 23) *0
[    0.181495] ACPI: PCI Interrupt Link [APCH] (IRQs 22 23) *0
[    0.181583] ACPI: PCI Interrupt Link [APMU] (IRQs 22 23) *0, disabled.
[    0.181670] ACPI: PCI Interrupt Link [AAZA] (IRQs 22 23) *0
[    0.181757] ACPI: PCI Interrupt Link [APCS] (IRQs 22 23) *0
[    0.181844] ACPI: PCI Interrupt Link [APCL] (IRQs 22 23) *0
[    0.181930] ACPI: PCI Interrupt Link [APCM] (IRQs 22 23) *0, disabled.
[    0.182018] ACPI: PCI Interrupt Link [APCZ] (IRQs 22 23) *0, disabled.
[    0.182106] ACPI: PCI Interrupt Link [APSI] (IRQs 20) *0
[    0.182192] ACPI: PCI Interrupt Link [APSJ] (IRQs 21) *0
[    0.182337] ACPI: \_SB_.PCI0: notify handler is installed
[    0.182383] Found 1 acpi root devices
[    0.182508] vgaarb: setting as boot device: PCI:0000:00:0d.0
[    0.182508] vgaarb: device added: PCI:0000:00:0d.0,decodes=io+mem,owns=io+mem,locks=none
[    0.182508] vgaarb: loaded
[    0.182508] vgaarb: bridge control possible 0000:00:0d.0
[    0.182508] SCSI subsystem initialized
[    0.182508] libata version 3.00 loaded.
[    0.182508] ACPI: bus type USB registered
[    0.182508] usbcore: registered new interface driver usbfs
[    0.182508] usbcore: registered new interface driver hub
[    0.182508] usbcore: registered new device driver usb
[    0.182508] PCI: Using ACPI for IRQ routing
[    0.184666] PCI: pci_cache_line_size set to 64 bytes
[    0.184708] e820: reserve RAM buffer [mem 0x0009f000-0x0009ffff]
[    0.184711] e820: reserve RAM buffer [mem 0x77ee0000-0x77ffffff]
[    0.184828] NetLabel: Initializing
[    0.184829] NetLabel:  domain hash size = 128
[    0.184831] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.184844] NetLabel:  unlabeled traffic allowed by default
[    0.184861] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.184861] hpet0: at MMIO 0xfefff000, IRQs 2, 8, 31
[    0.184861] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
[    0.186099] Switched to clocksource hpet
[    0.191174] AppArmor: AppArmor Filesystem Enabled
[    0.191215] pnp: PnP ACPI init
[    0.191235] ACPI: bus type PNP registered
[    0.191383] system 00:00: [io  0x1000-0x107f] has been reserved
[    0.191386] system 00:00: [io  0x1080-0x10ff] has been reserved
[    0.191389] system 00:00: [io  0x1400-0x147f] has been reserved
[    0.191392] system 00:00: [io  0x1480-0x14ff] has been reserved
[    0.191394] system 00:00: [io  0x1800-0x187f] has been reserved
[    0.191397] system 00:00: [io  0x1880-0x18ff] has been reserved
[    0.191402] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.191504] system 00:01: [io  0x04d0-0x04d1] has been reserved
[    0.191507] system 00:01: [io  0x0800-0x087f] has been reserved
[    0.191510] system 00:01: [io  0x0294-0x0297] has been reserved
[    0.191513] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.191526] pnp 00:02: [dma 4]
[    0.191548] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.191640] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.191690] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.191718] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.191753] pnp 00:06: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.191894] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.192540] system 00:08: [mem 0xf0000000-0xf3ffffff] has been reserved
[    0.192543] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.192561] ACPI Error: Field [ASSM] at 524320 exceeds Buffer [BUF0] size 880 (bits) (20131115/dsopcode-236)
[    0.192567] ACPI Error: Method parse/execution failed [\_SB_.MEM_._CRS] (Node f702d0a8), AE_AML_BUFFER_LIMIT (20131115/psparse-536)
[    0.192574] ACPI Error: Method execution failed [\_SB_.MEM_._CRS] (Node f702d0a8), AE_AML_BUFFER_LIMIT (20131115/uteval-103)
[    0.192580] pnp 00:09: can't evaluate _CRS: 12298
[    0.192623] system 00:09: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.192633] pnp: PnP ACPI: found 10 devices
[    0.192634] ACPI: bus type PNP unregistered
[    0.192638] PnPBIOS: Disabled by ACPI PNP
[    0.229842] pci 0000:00:0d.0: BAR 6: assigned [mem 0x80000000-0x8001ffff pref]
[    0.229847] pci 0000:00:04.0: PCI bridge to [bus 01]
[    0.229851] pci 0000:00:04.0:   bridge window [io  0xb000-0xbfff]
[    0.229854] pci 0000:00:04.0:   bridge window [mem 0xfd700000-0xfd7fffff]
[    0.229858] pci 0000:00:04.0:   bridge window [mem 0xfde00000-0xfdefffff pref]
[    0.229862] pci 0000:00:09.0: PCI bridge to [bus 02]
[    0.229865] pci 0000:00:09.0:   bridge window [io  0xa000-0xafff]
[    0.229868] pci 0000:00:09.0:   bridge window [mem 0xfdd00000-0xfddfffff]
[    0.229872] pci 0000:00:09.0:   bridge window [mem 0xfdc00000-0xfdcfffff 64bit pref]
[    0.229875] pci 0000:00:0b.0: PCI bridge to [bus 03]
[    0.229878] pci 0000:00:0b.0:   bridge window [io  0x9000-0x9fff]
[    0.229881] pci 0000:00:0b.0:   bridge window [mem 0xfdb00000-0xfdbfffff]
[    0.229884] pci 0000:00:0b.0:   bridge window [mem 0xfda00000-0xfdafffff 64bit pref]
[    0.229888] pci 0000:00:0c.0: PCI bridge to [bus 04]
[    0.229891] pci 0000:00:0c.0:   bridge window [io  0x8000-0x8fff]
[    0.229894] pci 0000:00:0c.0:   bridge window [mem 0xfd900000-0xfd9fffff]
[    0.229897] pci 0000:00:0c.0:   bridge window [mem 0xfd800000-0xfd8fffff 64bit pref]
[    0.229901] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.229904] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.229907] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.229909] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000dffff]
[    0.229912] pci_bus 0000:00: resource 8 [mem 0x80000000-0xfebfffff]
[    0.229915] pci_bus 0000:01: resource 0 [io  0xb000-0xbfff]
[    0.229918] pci_bus 0000:01: resource 1 [mem 0xfd700000-0xfd7fffff]
[    0.229920] pci_bus 0000:01: resource 2 [mem 0xfde00000-0xfdefffff pref]
[    0.229923] pci_bus 0000:01: resource 4 [io  0x0000-0x0cf7]
[    0.229926] pci_bus 0000:01: resource 5 [io  0x0d00-0xffff]
[    0.229928] pci_bus 0000:01: resource 6 [mem 0x000a0000-0x000bffff]
[    0.229931] pci_bus 0000:01: resource 7 [mem 0x000c0000-0x000dffff]
[    0.229934] pci_bus 0000:01: resource 8 [mem 0x80000000-0xfebfffff]
[    0.229936] pci_bus 0000:02: resource 0 [io  0xa000-0xafff]
[    0.229939] pci_bus 0000:02: resource 1 [mem 0xfdd00000-0xfddfffff]
[    0.229942] pci_bus 0000:02: resource 2 [mem 0xfdc00000-0xfdcfffff 64bit pref]
[    0.229945] pci_bus 0000:03: resource 0 [io  0x9000-0x9fff]
[    0.229947] pci_bus 0000:03: resource 1 [mem 0xfdb00000-0xfdbfffff]
[    0.229950] pci_bus 0000:03: resource 2 [mem 0xfda00000-0xfdafffff 64bit pref]
[    0.229953] pci_bus 0000:04: resource 0 [io  0x8000-0x8fff]
[    0.229955] pci_bus 0000:04: resource 1 [mem 0xfd900000-0xfd9fffff]
[    0.229958] pci_bus 0000:04: resource 2 [mem 0xfd800000-0xfd8fffff 64bit pref]
[    0.229999] NET: Registered protocol family 2
[    0.230224] TCP established hash table entries: 8192 (order: 3, 32768 bytes)
[    0.230246] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.230286] TCP: Hash tables configured (established 8192 bind 8192)
[    0.230322] TCP: reno registered
[    0.230325] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.230336] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.230402] NET: Registered protocol family 1
[    0.230687] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 23
[    0.230960] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
[    0.231079] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.231126] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.231182] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.231236] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.231291] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.231349] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.231411] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.231476] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.231483] pci 0000:00:0d.0: Video device with shadowed ROM
[    0.231493] PCI: CLS 32 bytes, default 64
[    0.231560] Trying to unpack rootfs image as initramfs...
[    0.620958] Freeing initrd memory: 18344K (f5c1c000 - f6e06000)
[    0.621156] microcode: AMD CPU family 0xf not supported
[    0.621158] Scanning for low memory corruption every 60 seconds
[    0.621459] Initialise system trusted keyring
[    0.621512] audit: initializing netlink socket (disabled)
[    0.621528] type=2000 audit(1457188400.620:1): initialized
[    0.645443] bounce pool size: 64 pages
[    0.645460] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.646884] zbud: loaded
[    0.646982] VFS: Disk quotas dquot_6.5.2
[    0.647035] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.647588] fuse init (API version 7.22)
[    0.647694] msgmni has been set to 1720
[    0.647775] Key type big_key registered
[    0.648305] Key type asymmetric registered
[    0.648308] Asymmetric key parser 'x509' registered
[    0.648348] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.648393] io scheduler noop registered
[    0.648395] io scheduler deadline registered (default)
[    0.648424] io scheduler cfq registered
[    0.648562] pcieport 0000:00:09.0: irq 40 for MSI/MSI-X
[    0.648616] pcieport 0000:00:0b.0: irq 41 for MSI/MSI-X
[    0.648659] pcieport 0000:00:0c.0: irq 42 for MSI/MSI-X
[    0.648722] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.648744] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.648813] ipmi message handler version 39.2
[    0.648902] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.648907] ACPI: Power Button [PWRB]
[    0.648963] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.648966] ACPI: Power Button [PWRF]
[    0.649015] ACPI: Fan [FAN] (on)
[    0.649289] ACPI: [Package] has zero elements (f7397840)
[    0.649291] ACPI: Invalid passive threshold
[    0.649503] thermal LNXTHERM:00: registered as thermal_zone0
[    0.649505] ACPI: Thermal Zone [THRM] (23 C)
[    0.649542] GHES: HEST is not enabled!
[    0.649611] isapnp: Scanning for PnP cards...
[    0.649647] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.651035] Linux agpgart interface v0.103
[    0.652635] brd: module loaded
[    0.653379] loop: module loaded
[    0.653931] libphy: Fixed MDIO Bus: probed
[    0.654062] tun: Universal TUN/TAP device driver, 1.6
[    0.654064] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.654101] PPP generic driver version 2.4.2
[    0.654145] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.654149] ehci-pci: EHCI PCI platform driver
[    0.654301] ehci-pci 0000:00:02.1: EHCI Host Controller
[    0.654308] ehci-pci 0000:00:02.1: new USB bus registered, assigned bus number 1
[    0.654318] ehci-pci 0000:00:02.1: debug port 1
[    0.654353] ehci-pci 0000:00:02.1: cache line size of 32 is not supported
[    0.654379] ehci-pci 0000:00:02.1: irq 22, io mem 0xfe02e000
[    0.664020] ehci-pci 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    0.664077] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.664079] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.664082] usb usb1: Product: EHCI Host Controller
[    0.664084] usb usb1: Manufacturer: Linux 3.13.0-80-generic ehci_hcd
[    0.664086] usb usb1: SerialNumber: 0000:00:02.1
[    0.664190] hub 1-0:1.0: USB hub found
[    0.664198] hub 1-0:1.0: 10 ports detected
[    0.664397] ehci-platform: EHCI generic platform driver
[    0.664408] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.664410] ohci-pci: OHCI PCI platform driver
[    0.664507] ohci-pci 0000:00:02.0: OHCI PCI host controller
[    0.664515] ohci-pci 0000:00:02.0: new USB bus registered, assigned bus number 2
[    0.664543] ohci-pci 0000:00:02.0: irq 23, io mem 0xfe02f000
[    0.722033] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    0.722036] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.722038] usb usb2: Product: OHCI PCI host controller
[    0.722040] usb usb2: Manufacturer: Linux 3.13.0-80-generic ohci_hcd
[    0.722042] usb usb2: SerialNumber: 0000:00:02.0
[    0.722136] hub 2-0:1.0: USB hub found
[    0.722144] hub 2-0:1.0: 10 ports detected
[    0.722318] ohci-platform: OHCI generic platform driver
[    0.722328] uhci_hcd: USB Universal Host Controller Interface driver
[    0.722411] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    0.722413] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    0.723049] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.723140] mousedev: PS/2 mouse device common for all mice
[    0.723263] rtc_cmos 00:04: RTC can wake from S4
[    0.723412] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.723451] rtc_cmos 00:04: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    0.723535] device-mapper: uevent: version 1.0.3
[    0.723599] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    0.723622] platform eisa.0: Probing EISA bus 0
[    0.723625] platform eisa.0: EISA: Cannot allocate resource for mainboard
[    0.723628] platform eisa.0: Cannot allocate resource for EISA slot 1
[    0.723631] platform eisa.0: Cannot allocate resource for EISA slot 2
[    0.723634] platform eisa.0: Cannot allocate resource for EISA slot 3
[    0.723636] platform eisa.0: Cannot allocate resource for EISA slot 4
[    0.723639] platform eisa.0: Cannot allocate resource for EISA slot 5
[    0.723641] platform eisa.0: Cannot allocate resource for EISA slot 6
[    0.723644] platform eisa.0: Cannot allocate resource for EISA slot 7
[    0.723647] platform eisa.0: Cannot allocate resource for EISA slot 8
[    0.723649] platform eisa.0: EISA: Detected 0 cards
[    0.723657] cpufreq-nforce2: No nForce2 chipset.
[    0.723662] ledtrig-cpu: registered to indicate activity on CPUs
[    0.723802] TCP: cubic registered
[    0.723910] NET: Registered protocol family 10
[    0.724137] NET: Registered protocol family 17
[    0.724152] Key type dns_resolver registered
[    0.724295] Using IPI No-Shortcut mode
[    0.724375] Loading compiled-in X.509 certificates
[    0.727945] Loaded X.509 cert 'Magrathea: Glacier signing key: 51477ef18c3c0a02fafa5c316e6d3b52bce57f82'
[    0.727959] registered taskstats version 1
[    0.743067] Key type trusted registered
[    0.746559] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    0.754171] Key type encrypted registered
[    0.754178] AppArmor: AppArmor sha1 policy hashing enabled
[    0.754181] IMA: No TPM chip found, activating TPM-bypass!
[    0.754406] regulator-dummy: disabling
[    0.754448]   Magic number: 8:868:585
[    0.754561] rtc_cmos 00:04: setting system clock to 2016-03-05 14:33:20 UTC (1457188400)
[    0.754705] powernow-k8: fid 0x10 (2400 MHz), vid 0xa
[    0.754706] powernow-k8: fid 0xe (2200 MHz), vid 0xc
[    0.754708] powernow-k8: fid 0xc (2000 MHz), vid 0xe
[    0.754710] powernow-k8: fid 0xa (1800 MHz), vid 0x10
[    0.754711] powernow-k8: fid 0x2 (1000 MHz), vid 0x12
[    0.754737] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 4600+ (2 cpu cores) (version 2.20.00)
[    0.754742] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.754743] EDD information not available.
[    0.754777] PM: Hibernation image not present or could not be loaded.
[    1.003479] isapnp: No Plug & Play device found
[    1.004050] Freeing unused kernel memory: 880K (c19c3000 - c1a9f000)
[    1.004097] Write protecting the kernel text: 6568k
[    1.004174] Write protecting the kernel read-only data: 2780k
[    1.004176] NX-protecting the kernel data: 5720k
[    1.020108] systemd-udevd[97]: starting version 204
[    1.032048] usb 1-5: new high-speed USB device number 3 using ehci-pci
[    1.060485] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.060749] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
[    1.082775] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[    1.136074] firewire_ohci 0000:01:05.0: added OHCI v1.0 device as card 0, 8 IR + 8 IT contexts, quirks 0x0
[    1.165524] usb 1-5: New USB device found, idVendor=22b8, idProduct=2e82
[    1.165527] usb 1-5: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.165530] usb 1-5: Product: XT1021
[    1.165532] usb 1-5: Manufacturer: motorola
[    1.165534] usb 1-5: SerialNumber: xxxxxxxxxx
[    1.276018] usb 1-6: new high-speed USB device number 4 using ehci-pci
[    1.409772] usb 1-6: New USB device found, idVendor=13fe, idProduct=3100
[    1.409775] usb 1-6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.409777] usb 1-6: Product: USB DISK 2.0
[    1.409779] usb 1-6: Manufacturer:         
[    1.409781] usb 1-6: SerialNumber: xxxxxxxxxx
[    1.520017] usb 1-8: new high-speed USB device number 5 using ehci-pci
[    1.584717] forcedeth 0000:00:07.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:22:15:25:dc:0a
[    1.584721] forcedeth 0000:00:07.0: highdma pwrctl mgmt lnktim msi desc-v3
[    1.584757] sata_nv 0000:00:08.0: version 3.5
[    1.585018] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 20
[    1.585410] scsi0 : sata_nv
[    1.585505] scsi1 : sata_nv
[    1.585546] ata1: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd800 irq 20
[    1.585548] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd808 irq 20
[    1.585817] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 21
[    1.586132] scsi2 : sata_nv
[    1.586203] scsi3 : sata_nv
[    1.586243] ata3: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xc400 irq 21
[    1.586245] ata4: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xc408 irq 21
[    1.586279] pata_amd 0000:00:06.0: version 0.4.1
[    1.586872] scsi4 : pata_amd
[    1.586943] scsi5 : pata_amd
[    1.586985] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    1.586987] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    1.636116] firewire_core 0000:01:05.0: created device fw0: GUID 001e8c00014ecccf, S400
[    1.653898] usb 1-8: New USB device found, idVendor=058f, idProduct=6377
[    1.653901] usb 1-8: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.653903] usb 1-8: Product: Mass Storage Device
[    1.653905] usb 1-8: Manufacturer: Generic
[    1.653908] usb 1-8: SerialNumber: xxxxxxxxxx
[    1.788989] usb-storage 1-6:1.0: USB Mass Storage device detected
[    1.789086] scsi6 : usb-storage 1-6:1.0
[    1.789170] usb-storage 1-8:1.0: USB Mass Storage device detected
[    1.789223] scsi7 : usb-storage 1-8:1.0
[    1.789295] usbcore: registered new interface driver usb-storage
[    1.906242] ata3: SATA link down (SStatus 0 SControl 300)
[    1.964023] usb 2-2: new low-speed USB device number 2 using ohci-pci
[    2.052038] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.060123] ata1.00: ATA-8: WDC WD3200AAJS-65B4A0, 01.03A01, max UDMA/133
[    2.060127] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.076119] ata1.00: configured for UDMA/133
[    2.076292] scsi 0:0:0:0: Direct-Access     ATA      WDC WD3200AAJS-6 01.0 PQ: 0 ANSI: 5
[    2.076529] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.076546] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    2.076650] sd 0:0:0:0: [sda] Write Protect is off
[    2.076653] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.076694] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.162645]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 sda9 >
[    2.163227] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.187035] usb 2-2: New USB device found, idVendor=045e, idProduct=0024
[    2.187038] usb 2-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.187041] usb 2-2: Product: Microsoft Trackball Explorer\xffffffc2\xffffffae\xffffffae
[    2.187043] usb 2-2: Manufacturer: Microsoft
[    2.198702] hidraw: raw HID events driver (C) Jiri Kosina
[    2.213540] usbcore: registered new interface driver usbhid
[    2.213544] usbhid: USB HID core driver
[    2.218301] input: Microsoft Microsoft Trackball Explorer\xffffffc2\xffffffae\xffffffae as /devices/pci0000:00/0000:00:02.0/usb2/2-2/2-2:1.0/input/input3
[    2.218420] hid-generic 0003:045E:0024.0001: input,hidraw0: USB HID v1.00 Mouse [Microsoft Microsoft Trackball Explorer\xffffffc2\xffffffae\xffffffae] on usb-0000:00:02.0-2/input0
[    2.544037] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.552126] ata2.00: ATAPI: TSSTcorp CDDVDW TS-H653Q, 0303, max UDMA/33
[    2.568117] ata2.00: configured for UDMA/33
[    2.569037] scsi 1:0:0:0: CD-ROM            TSSTcorp CDDVDW TS-H653Q  0303 PQ: 0 ANSI: 5
[    2.572572] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.572575] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.572701] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.572792] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.788800] scsi 6:0:0:0: Direct-Access              USB DISK 2.0     PMAP PQ: 0 ANSI: 0 CCS
[    2.788807] scsi 7:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[    2.789101] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    2.789599] scsi 7:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[    2.790307] scsi 7:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[    2.790551] sd 6:0:0:0: [sdb] 7823360 512-byte logical blocks: (4.00 GB/3.73 GiB)
[    2.790928] scsi 7:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[    2.791212] sd 6:0:0:0: [sdb] Write Protect is off
[    2.791216] sd 6:0:0:0: [sdb] Mode Sense: 23 00 00 00
[    2.791229] sd 7:0:0:0: Attached scsi generic sg3 type 0
[    2.791422] sd 7:0:0:1: Attached scsi generic sg4 type 0
[    2.791612] sd 7:0:0:2: Attached scsi generic sg5 type 0
[    2.791799] sd 7:0:0:3: Attached scsi generic sg6 type 0
[    2.791964] sd 6:0:0:0: [sdb] No Caching mode page found
[    2.791969] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    2.798298] sd 6:0:0:0: [sdb] No Caching mode page found
[    2.798303] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    2.799780]  sdb: sdb1
[    2.802540] sd 6:0:0:0: [sdb] No Caching mode page found
[    2.802546] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    2.802551] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[    2.806672] sd 7:0:0:0: [sdc] Attached SCSI removable disk
[    2.809805] sd 7:0:0:1: [sdd] Attached SCSI removable disk
[    2.811046] sd 7:0:0:3: [sdf] Attached SCSI removable disk
[    2.811668] sd 7:0:0:2: [sde] Attached SCSI removable disk
[    2.894257] ata4: SATA link down (SStatus 0 SControl 300)
[    2.894333] ata6: port disabled--ignoring
[    3.961291] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    4.072494] random: nonblocking pool is initialized
[   14.249767] Adding 1963004k swap on /dev/sda5.  Priority:-1 extents:1 across:1963004k FS
[   14.352954] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.466030] systemd-udevd[284]: starting version 204
[   14.699018] lp: driver loaded but no devices found
[   14.713908] ppdev: user-space parallel port driver
[   14.790304] i2c i2c-0: nForce2 SMBus adapter at 0x1c00
[   14.790338] i2c i2c-1: nForce2 SMBus adapter at 0x1c40
[   14.866484] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   14.887853] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   14.888785] nvidia: module license 'NVIDIA' taints kernel.
[   14.888791] Disabling lock debugging due to kernel taint
[   14.917048] nvidia: module verification failed: signature and/or  required key missing - tainting kernel
[   15.043246] type=1400 audit(1457188414.785:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=345 comm="apparmor_parser"
[   15.043256] type=1400 audit(1457188414.785:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=345 comm="apparmor_parser"
[   15.043262] type=1400 audit(1457188414.785:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=345 comm="apparmor_parser"
[   15.043815] type=1400 audit(1457188414.785:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=345 comm="apparmor_parser"
[   15.043823] type=1400 audit(1457188414.785:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=345 comm="apparmor_parser"
[   15.044136] type=1400 audit(1457188414.789:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=345 comm="apparmor_parser"
[   15.079491] type=1400 audit(1457188414.821:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/ntpd" pid=354 comm="apparmor_parser"
[   15.147501] kvm: disabled by bios
[   15.174449] ACPI: PCI Interrupt Link [AIGP] enabled at IRQ 22
[   15.174465] vgaarb: device changed decodes: PCI:0000:00:0d.0,olddecodes=io+mem,decodes=none:owns=none
[   15.174698] NVRM: loading NVIDIA UNIX x86 Kernel Module  173.14.39  Wed Nov 27 14:55:50 PST 2013
[   15.192723] kvm: disabled by bios
[   15.386171] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 23
[   15.386181] hda_intel: Disabling MSI
[   15.386207] hda-intel 0000:00:05.0: Disabling 64bit DMA
[   15.416624] hda-intel 0000:00:05.0: Enable delay in RIRB handling
[   15.557844] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   16.048026] hda_codec: ALC1200: SKU not ready 0x411111f0
[   16.120022] autoconfig: line_outs=4 (0x14/0x15/0x16/0x17/0x0) type:line
[   16.120027]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   16.120029]    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[   16.120031]    mono: mono_out=0x0
[   16.120032]    dig-out=0x1e/0x0
[   16.120034]    inputs:
[   16.120036]      Front Mic=0x19
[   16.120037]      Rear Mic=0x18
[   16.120039]      Line=0x1c
[   16.120041] realtek: No valid SSID, checking pincfg 0x411111f0 for NID 0x1d
[   16.120043] realtek: Enable default setup for auto mode as fallback
[   16.393398] init: failsafe main process (551) killed by TERM signal
[   17.281647] type=1400 audit(1457188417.025:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=647 comm="apparmor_parser"
[   17.281660] type=1400 audit(1457188417.025:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=647 comm="apparmor_parser"
[   17.282215] type=1400 audit(1457188417.025:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=647 comm="apparmor_parser"
[   17.711947] Bluetooth: Core ver 2.17
[   17.711981] NET: Registered protocol family 31
[   17.711983] Bluetooth: HCI device and connection manager initialized
[   17.711994] Bluetooth: HCI socket layer initialized
[   17.711998] Bluetooth: L2CAP socket layer initialized
[   17.712052] Bluetooth: SCO socket layer initialized
[   17.722963] Bluetooth: RFCOMM TTY layer initialized
[   17.722978] Bluetooth: RFCOMM socket layer initialized
[   17.722985] Bluetooth: RFCOMM ver 1.11
[   17.940254] input: HDA NVidia Front Headphone as /devices/pci0000:00/0000:00:05.0/sound/card0/input11
[   17.940462] input: HDA NVidia Line Out Side as /devices/pci0000:00/0000:00:05.0/sound/card0/input10
[   17.940632] input: HDA NVidia Line Out CLFE as /devices/pci0000:00/0000:00:05.0/sound/card0/input9
[   17.940804] input: HDA NVidia Line Out Surround as /devices/pci0000:00/0000:00:05.0/sound/card0/input8
[   17.940983] input: HDA NVidia Line Out Front as /devices/pci0000:00/0000:00:05.0/sound/card0/input7
[   17.941149] input: HDA NVidia Line as /devices/pci0000:00/0000:00:05.0/sound/card0/input6
[   17.941315] input: HDA NVidia Rear Mic as /devices/pci0000:00/0000:00:05.0/sound/card0/input5
[   17.941481] input: HDA NVidia Front Mic as /devices/pci0000:00/0000:00:05.0/sound/card0/input4
[   17.999197] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   17.999202] Bluetooth: BNEP filters: protocol multicast
[   17.999212] Bluetooth: BNEP socket layer initialized
[   19.816439] forcedeth 0000:00:07.0: irq 43 for MSI/MSI-X
[   19.816474] forcedeth 0000:00:07.0 eth0: MSI enabled
[   20.609287] init: samba-ad-dc main process (769) terminated with status 1
[   23.478718] init: plymouth-upstart-bridge main process ended, respawning
[   36.514429] init: plymouth-stop pre-start process (1768) terminated with status 1
[   39.323723] FAT-fs (sdb1): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.
[  678.573115] usb 1-6: USB disconnect, device number 4
[  678.708093] usb 1-5: USB disconnect, device number 3
[  678.948050] usb 1-5: new high-speed USB device number 6 using ehci-pci
[  679.081298] usb 1-5: New USB device found, idVendor=22b8, idProduct=2e82
[  679.081306] usb 1-5: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  679.081310] usb 1-5: Product: XT1021
[  679.081313] usb 1-5: Manufacturer: motorola
[  679.081315] usb 1-5: SerialNumber: xxxxxxxxxx
[ 1151.439111] audit_printk_skb: 105 callbacks suppressed
[ 1151.439117] type=1400 audit(1457189551.535:47): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=2581 comm="apparmor_parser"
[ 1151.439126] type=1400 audit(1457189551.535:48): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2581 comm="apparmor_parser"
[ 1151.446136] type=1400 audit(1457189551.543:49): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2581 comm="apparmor_parser"
[ 6047.155528] perf samples too long (2501 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
[18761.816400] usb 1-5: USB disconnect, device number 6
[22314.156054] usb 1-5: new high-speed USB device number 7 using ehci-pci
[22314.289333] usb 1-5: New USB device found, idVendor=22b8, idProduct=2e82
[22314.289340] usb 1-5: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[22314.289343] usb 1-5: Product: XT1021
[22314.289346] usb 1-5: Manufacturer: motorola
[22314.289348] usb 1-5: SerialNumber: xxxxxxxxxx
[22339.501561] usb 1-5: USB disconnect, device number 7
[22339.776065] usb 1-5: new high-speed USB device number 8 using ehci-pci
[22339.910875] usb 1-5: New USB device found, idVendor=22b8, idProduct=2e24
[22339.910884] usb 1-5: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[22339.910888] usb 1-5: Product: XT1021
[22339.910891] usb 1-5: Manufacturer: motorola
[22339.910894] usb 1-5: SerialNumber: xxxxxxxxxx
[22340.079714] usbcore: registered new interface driver cdc_ether
[22340.094116] rndis_host 1-5:1.0 usb0: register 'rndis_host' at usb-0000:00:02.1-5, RNDIS device, 02:6e:6d:6b:70:7c
[22340.096254] usbcore: registered new interface driver rndis_host
[29712.105109] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[29725.438219] EXT4-fs (sda9): mounted filesystem with ordered data mode. Opts: (null)
[31283.881424] usb 1-5: USB disconnect, device number 8
[31283.883727] rndis_host 1-5:1.0 usb0: unregister 'rndis_host' usb-0000:00:02.1-5, RNDIS device
```

This was only vaguely solved by installing 14.04 fresh and wiping the HD. With Lubuntu as new all was ok. But after I allowed it to fully update itself, the next day's first boot was 20mins again!!! A couple of days later and it's only, (hah, only) about 5 mins to boot. But I'm also having graphics crashes and system freezes. So a new 15.04 is going in next. If I still get long boots I'll moan about it here and post a new thread about that.

---

### Post by Bucky Ball on 2016-03-12
I would wonder if this has anything to do with software and may be a hardware issue or a log or a memory leak or something other than the version of Ubuntu you are using. Curious to know if you get the same result in 15.10. If that is the case I would be looking in places other than the OS version/release. 

Old machine? Old PSU? RAM? If a desktop, see anything untoward like bulging capacitors on the motherboard? Near the RAM slots?

---

### Post by ajgreeny on 2016-03-12
Lubuntu 15.04 is now dead so there is no point installing that as you will be unable to add any applications to it.

Either choose 15.10 or wait a month or slightly more for April 21, I think, and try 16.04, the next long term support (LTS) version.

This sounds rather like a hardware problem, possibly the graphic card which is listed as unknown,
What is the output of ```
lspci | grep -i vga
``` in terminal

---

### Post by efflandt on 2016-03-12
You are using a very old nvidia driver. Have you tried the default nouveau driver to see if it happens with that? Maybe the video card needs to be reseated or is failing.

But the only lag in the logs appears to be related to your USB connected phone. Did you connect that after you booted or was that connected during boot?

---

### Post by cheapodonuts on 2016-03-12
> **ajgreeny said:**
> Lubuntu 15.04 is now dead so there is no point installing that as you will be unable to add any applications to it.

Either choose 15.10 or wait a month or slightly more for April 21, I think, and try 16.04, the next long term support (LTS) version.

This sounds rather like a hardware problem, possibly the graphic card which is listed as unknown,
What is the output of ```
lspci | grep -i vga
``` in terminal

cheapo@cheapo-KX733AA-ABU-a6511-uk:~$ lspci | grep -i vga
00:0d.0 VGA compatible controller: NVIDIA Corporation C61 [GeForce 6150SE nForce 430] (rev a2)
cheapo@cheapo-KX733AA-ABU-a6511-uk:~$

> **efflandt said:**
> You are using a very old nvidia driver. Have you tried the default nouveau driver to see if it happens with that? Maybe the video card needs to be reseated or is failing.

But the only lag in the logs appears to be related to your USB connected phone. Did you connect that after you booted or was that connected during boot?

Thanx for the help efflandt.

I just checked the additional drivers and it says it's already using the xorg nouveau one. I also checked just previously that the system hadn't cured it. Graphics crashed immediately when I tried to open a second Firefox. Had to reboot.

I'll admit I do get forgetful and leave the phone plugged in sometimes, but I probably would have noticed if it only delayed the boot if the phone was connected during start up. I did notice that just having the cable plugged in registered it as a phone. When I shut down this evening, I'll leave nothing plugged it at the front. So I'll report tomorrow regarding the first boot time. At the moment it re-boots in about 30 seconds.

Oh yes, I did two of Apt-get updates yesterday. Just because I recalled that someone suggested it yonks ago when we used to do the multimedia upgrade malarkey by following a sticky on the forums.

Hard shut down and second boot after black screen delayed start in the morning now results in a normal boot time. But the delayed boot was still happening after long shutdowns.

---

### Post by Bucky Ball on 2016-03-12
Does this give anything to autoremove?

> sudo apt-get autoremove

?

---

### Post by cheapodonuts on 2016-03-13
Yeap,

```
cheapo@cheapo-KX733AA-ABU-a6511-uk:~$ 
cheapo@cheapo-KX733AA-ABU-a6511-uk:~$ sudo apt-get autoremove
[sudo] password for cheapo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  dolphin kfind libbaloowidgets4 libkfilemetadata4 libkonq-common
  libkonq5-templates libkonq5abi1 libkonqsidebarplugin4a libruby1.9.1
  libyaml-0-2 ruby ruby1.9.1
0 to upgrade, 0 to newly install, 12 to remove and 5 not to upgrade.
After this operation, 18.2 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 150129 files and directories currently installed.)
Removing dolphin (4:4.13.3-0ubuntu0.1) ...
Removing kfind (4:4.13.3-0ubuntu0.1) ...
Removing libbaloowidgets4 (4:4.13.3-0ubuntu0.1) ...
Removing libkfilemetadata4 (4:4.13.3-0ubuntu0.2) ...
Removing libkonq5abi1 (4:4.13.3-0ubuntu0.1) ...
Removing libkonq-common (4:4.13.3-0ubuntu0.1) ...
Removing libkonq5-templates (4:4.13.3-0ubuntu0.1) ...
Removing libkonqsidebarplugin4a (4:4.13.3-0ubuntu0.1) ...
Removing libruby1.9.1 (1.9.3.484-2ubuntu1.2) ...
Removing ruby1.9.1 (1.9.3.484-2ubuntu1.2) ...
Removing ruby (1:1.9.3.4) ...
Removing libyaml-0-2:i386 (0.1.4-3ubuntu3.1) ...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.7) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
cheapo@cheapo-KX733AA-ABU-a6511-uk:~$ 
cheapo@cheapo-KX733AA-ABU-a6511-uk:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 to upgrade, 0 to newly install, 0 to remove and 5 not to upgrade.
cheapo@cheapo-KX733AA-ABU-a6511-uk:~$ 
```

---------------------

Then the system had a problem as soon as I tried to copy the terminal
 Here's the crash info screen (attached images)

I'm going to reboot and post another dmesg

```
cheapo@cheapo-KX733AA-ABU-a6511-uk:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.13.0-79-generic (buildd@lcy01-11) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #123-Ubuntu SMP Fri Feb 19 14:28:32 UTC 2016 (Ubuntu 3.13.0-79.123-generic 3.13.11-ckt33)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009efff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009f000-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000f0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x0000000077edffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000077ee0000-0x0000000077ee2fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x0000000077ee3000-0x0000000077eeffff] ACPI data
[    0.000000] BIOS-e820: [mem 0x0000000077ef0000-0x0000000077efffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000078000000-0x000000007fffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000f0000000-0x00000000f3ffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000ffffffff] reserved
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 0.4 present.
[    0.000000] DMI: HP-Pavilion KX733AA-ABU a6511.uk/NARRA3, BIOS  5.14 06/20/2008
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0x77ee0 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FF80000000 write-back
[    0.000000]   1 disabled
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] found SMP MP-table at [mem 0x000f55f0-0x000f55ff] mapped at [c00f55f0]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] initial memory mapped: [mem 0x00000000-0x01ffffff]
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x37800000-0x379fffff]
[    0.000000]  [mem 0x37800000-0x379fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x34000000-0x377fffff]
[    0.000000]  [mem 0x34000000-0x377fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0x33ffffff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x33ffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x37a00000-0x37bfdfff]
[    0.000000]  [mem 0x37a00000-0x37bfdfff] page 4k
[    0.000000] BRK [0x01b9f000, 0x01b9ffff] PGTABLE
[    0.000000] RAMDISK: [mem 0x35c1c000-0x36e05fff]
[    0.000000] ACPI: RSDP 000f7740 000024 (v02 HPQOEM)
[    0.000000] ACPI: XSDT 77ee3100 000054 (v01 HPQOEM SLIC-CPC 42302E31 AWRD 00000000)
[    0.000000] ACPI: FACP 77ee7f40 0000F4 (v03 HPQOEM SLIC-CPC 42302E31 AWRD 00000000)
[    0.000000] ACPI: DSDT 77ee32c0 004C2F (v01 HPQOEM SLIC-CPC 00001000 MSFT 03000000)
[    0.000000] ACPI: FACS 77ee0000 000040
[    0.000000] ACPI: SLIC 77ee8180 000176 (v01 HPQOEM SLIC-CPC 42302E31 AWRD 00000000)
[    0.000000] ACPI: SSDT 77ee8340 000248 (v01 HPQOEM SLIC-CPC 00000001  LTP 00000001)
[    0.000000] ACPI: HPET 77ee8600 000038 (v01 HPQOEM SLIC-CPC 42302E31 AWRD 00000098)
[    0.000000] ACPI: MCFG 77ee8680 00003C (v01 HPQOEM SLIC-CPC 42302E31 AWRD 00000000)
[    0.000000] ACPI: APIC 77ee8080 000098 (v01 HPQOEM SLIC-CPC 42302E31 AWRD 00000000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1026MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] BRK [0x01ba0000, 0x01ba0fff] PGTABLE
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   Normal   [mem 0x01000000-0x37bfdfff]
[    0.000000]   HighMem  [mem 0x37bfe000-0x77edffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009efff]
[    0.000000]   node   0: [mem 0x00100000-0x77edffff]
[    0.000000] On node 0 totalpages: 491134
[    0.000000] free_area_init_node: node 0, pgdat c19a5880, node_mem_map f4d1c020
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3998 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 224254 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2054 pages used for memmap
[    0.000000]   HighMem zone: 262882 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfefff000
[    0.000000] smpboot: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000effff]
[    0.000000] PM: Registered nosave memory: [mem 0x000f0000-0x000fffff]
[    0.000000] e820: [mem 0x80000000-0xefffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @f7bba000 s35520 r0 d21824 u57344
[    0.000000] pcpu-alloc: s35520 r0 d21824 u57344 alloc=14*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 [0] 2 [0] 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 489350
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-79-generic root=UUID=c668fab8-baa1-4850-891c-31b491ca61f8 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 3929848 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:00077ee0)
[    0.000000] Memory: 1913940K/1964536K available (6564K kernel code, 645K rwdata, 2776K rodata, 880K init, 924K bss, 50596K reserved, 1051528K highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff14000 - 0xfffff000   ( 940 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc19c3000 - 0xc1a9f000   ( 880 kB)
[    0.000000]       .data : 0xc1669600 - 0xc19c2740   (3428 kB)
[    0.000000]       .text : 0xc1000000 - 0xc1669600   (6565 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=8 to nr_cpu_ids=4.
[    0.000000] NR_IRQS:2304 nr_irqs:712 16
[    0.000000] CPU 0 irqstacks, hard=f7008000 soft=f700a000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 2411.017 MHz processor
[    0.000000] tsc: Marking TSC unstable due to TSCs unsynchronized
[    0.004005] Calibrating delay loop (skipped), value calculated using timer frequency.. 4822.03 BogoMIPS (lpj=9644068)
[    0.004008] pid_max: default: 32768 minimum: 301
[    0.004051] Security Framework initialized
[    0.004071] AppArmor: AppArmor initialized
[    0.004073] Yama: becoming mindful.
[    0.004131] Mount-cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.004134] Mountpoint-cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.004384] Initializing cgroup subsys memory
[    0.004393] Initializing cgroup subsys devices
[    0.004395] Initializing cgroup subsys freezer
[    0.004398] Initializing cgroup subsys blkio
[    0.004400] Initializing cgroup subsys perf_event
[    0.004404] Initializing cgroup subsys hugetlb
[    0.004431] CPU: Physical Processor ID: 0
[    0.004432] CPU: Processor Core ID: 0
[    0.004436] mce: CPU supports 5 MCE banks
[    0.004443] LVT offset 0 assigned for vector 0xf9
[    0.004447] process: using AMD E400 aware idle routine
[    0.004455] Last level iTLB entries: 4KB 512, 2MB 8, 4MB 4
[    0.004455] Last level dTLB entries: 4KB 512, 2MB 8, 4MB 4
[    0.004455] tlb_flushall_shift: 4
[    0.004755] Freeing SMP alternatives memory: 32K (c1a9f000 - c1aa7000)
[    0.008054] ACPI: Core revision 20131115
[    0.012395] ACPI: All ACPI Tables successfully acquired
[    0.016019] ftrace: allocating 27897 entries in 55 pages
[    0.028108] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.028645] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.071097] smpboot: CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 4600+ (fam: 0f, model: 6b, stepping: 02)
[    0.072000] Performance Events: AMD PMU driver.
[    0.072000] ... version:                0
[    0.072000] ... bit width:              48
[    0.072000] ... generic registers:      4
[    0.072000] ... value mask:             0000ffffffffffff
[    0.072000] ... max period:             00007fffffffffff
[    0.072000] ... fixed-purpose events:   0
[    0.072000] ... event mask:             000000000000000f
[    0.072000] CPU 1 irqstacks, hard=f7100000 soft=f7102000
[    0.072000] x86: Booting SMP configuration:
[    0.008000] Initializing CPU#1
[    0.080998] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.072000] .... node  #0, CPUs:      #1
[    0.160061] x86: Booted up 1 node, 2 CPUs
[    0.160063] smpboot: Total of 2 processors activated (9644.00 BogoMIPS)
[    0.160649] devtmpfs: initialized
[    0.160649] EVM: security.selinux
[    0.160649] EVM: security.SMACK64
[    0.160649] EVM: security.ima
[    0.160649] EVM: security.capability
[    0.160649] PM: Registering ACPI NVS region [mem 0x77ee0000-0x77ee2fff] (12288 bytes)
[    0.161433] pinctrl core: initialized pinctrl subsystem
[    0.161527] regulator-dummy: no parameters
[    0.161569] RTC time:  9:21:11, date: 03/13/16
[    0.161616] NET: Registered protocol family 16
[    0.161780] EISA bus registered
[    0.161782] cpuidle: using governor ladder
[    0.161784] cpuidle: using governor menu
[    0.161788] node 0 link 0: io port [8000, ffff]
[    0.161792] TOM: 0000000080000000 aka 2048M
[    0.161794] node 0 link 0: mmio [a0000, bffff]
[    0.161798] node 0 link 0: mmio [80000000, efffffff]
[    0.161800] node 0 link 0: mmio [f4000000, fe02ffff]
[    0.161802] node 0 link 0: mmio [f0000000, f04fffff]
[    0.161805] bus: [bus 00-04] on node 0 link 0
[    0.161807] bus: 00 [io  0x0000-0xffff]
[    0.161809] bus: 00 [mem 0x000a0000-0x000bffff]
[    0.161811] bus: 00 [mem 0x80000000-0xf3ffffff]
[    0.161813] bus: 00 [mem 0xf4000000-0xfcffffffff]
[    0.161870] ACPI: bus type PCI registered
[    0.161873] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.161953] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf0000000-0xf3ffffff] (base 0xf0000000)
[    0.161956] PCI: MMCONFIG at [mem 0xf0000000-0xf3ffffff] reserved in E820
[    0.161958] PCI: Using MMCONFIG for extended config space
[    0.161959] PCI: Using configuration type 1 for base access
[    0.162061] mtrr: your CPUs had inconsistent variable MTRR settings
[    0.162063] mtrr: probably your BIOS does not setup all CPUs.
[    0.162064] mtrr: corrected configuration.
[    0.164259] bio: create slab <bio-0> at 0
[    0.164259] ACPI: Added _OSI(Module Device)
[    0.164259] ACPI: Added _OSI(Processor Device)
[    0.164259] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.164259] ACPI: Added _OSI(Processor Aggregator Device)
[    0.169528] ACPI: Interpreter enabled
[    0.169542] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)
[    0.169557] ACPI: (supports S0 S1 S3 S4 S5)
[    0.169559] ACPI: Using IOAPIC for interrupt routing
[    0.169586] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.169710] ACPI: No dock devices found.
[    0.175898] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.175905] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.175911] acpi PNP0A08:00: _OSC failed (AE_NOT_FOUND); disabling ASPM
[    0.175998] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-3f] only partially covers this bridge
[    0.176168] PCI host bridge to bus 0000:00
[    0.176172] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.176174] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.176177] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.176179] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.176182] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000dffff]
[    0.176185] pci_bus 0000:00: root bus resource [mem 0x80000000-0xfebfffff]
[    0.176208] pci 0000:00:00.0: [10de:03ea] type 00 class 0x050000
[    0.176454] pci 0000:00:01.0: [10de:03e0] type 00 class 0x060100
[    0.176561] pci 0000:00:01.1: [10de:03eb] type 00 class 0x0c0500
[    0.176573] pci 0000:00:01.1: reg 0x10: [io  0xfc00-0xfc3f]
[    0.176588] pci 0000:00:01.1: reg 0x20: [io  0x1c00-0x1c3f]
[    0.176594] pci 0000:00:01.1: reg 0x24: [io  0x1c40-0x1c7f]
[    0.176622] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.176706] pci 0000:00:01.2: [10de:03f5] type 00 class 0x050000
[    0.176806] pci 0000:00:02.0: [10de:03f1] type 00 class 0x0c0310
[    0.176816] pci 0000:00:02.0: reg 0x10: [mem 0xfe02f000-0xfe02ffff]
[    0.176850] pci 0000:00:02.0: supports D1 D2
[    0.176852] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.176908] pci 0000:00:02.0: System wakeup disabled by ACPI
[    0.176941] pci 0000:00:02.1: [10de:03f2] type 00 class 0x0c0320
[    0.176952] pci 0000:00:02.1: reg 0x10: [mem 0xfe02e000-0xfe02e0ff]
[    0.176992] pci 0000:00:02.1: supports D1 D2
[    0.176995] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.177065] pci 0000:00:02.1: System wakeup disabled by ACPI
[    0.177107] pci 0000:00:04.0: [10de:03f3] type 01 class 0x060401
[    0.177189] pci 0000:00:04.0: System wakeup disabled by ACPI
[    0.177225] pci 0000:00:05.0: [10de:03f0] type 00 class 0x040300
[    0.177237] pci 0000:00:05.0: reg 0x10: [mem 0xfe024000-0xfe027fff]
[    0.177278] pci 0000:00:05.0: PME# supported from D3hot D3cold
[    0.177365] pci 0000:00:06.0: [10de:03ec] type 00 class 0x01018a
[    0.177387] pci 0000:00:06.0: reg 0x20: [io  0xf000-0xf00f]
[    0.177487] pci 0000:00:07.0: [10de:03ef] type 00 class 0x068000
[    0.177497] pci 0000:00:07.0: reg 0x10: [mem 0xfe02d000-0xfe02dfff]
[    0.177502] pci 0000:00:07.0: reg 0x14: [io  0xec00-0xec07]
[    0.177535] pci 0000:00:07.0: supports D1 D2
[    0.177538] pci 0000:00:07.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.177595] pci 0000:00:07.0: System wakeup disabled by ACPI
[    0.177635] pci 0000:00:08.0: [10de:03f6] type 00 class 0x010185
[    0.177644] pci 0000:00:08.0: reg 0x10: [io  0x09f0-0x09f7]
[    0.177649] pci 0000:00:08.0: reg 0x14: [io  0x0bf0-0x0bf3]
[    0.177653] pci 0000:00:08.0: reg 0x18: [io  0x0970-0x0977]
[    0.177658] pci 0000:00:08.0: reg 0x1c: [io  0x0b70-0x0b73]
[    0.177663] pci 0000:00:08.0: reg 0x20: [io  0xd800-0xd80f]
[    0.177667] pci 0000:00:08.0: reg 0x24: [mem 0xfe02c000-0xfe02cfff]
[    0.177762] pci 0000:00:08.1: [10de:03f6] type 00 class 0x010185
[    0.177771] pci 0000:00:08.1: reg 0x10: [io  0x09e0-0x09e7]
[    0.177776] pci 0000:00:08.1: reg 0x14: [io  0x0be0-0x0be3]
[    0.177780] pci 0000:00:08.1: reg 0x18: [io  0x0960-0x0967]
[    0.177785] pci 0000:00:08.1: reg 0x1c: [io  0x0b60-0x0b63]
[    0.177790] pci 0000:00:08.1: reg 0x20: [io  0xc400-0xc40f]
[    0.177795] pci 0000:00:08.1: reg 0x24: [mem 0xfe02b000-0xfe02bfff]
[    0.177897] pci 0000:00:09.0: [10de:03e8] type 01 class 0x060400
[    0.177925] pci 0000:00:09.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.177983] pci 0000:00:09.0: System wakeup disabled by ACPI
[    0.178024] pci 0000:00:0b.0: [10de:03e9] type 01 class 0x060400
[    0.178050] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.178104] pci 0000:00:0b.0: System wakeup disabled by ACPI
[    0.178141] pci 0000:00:0c.0: [10de:03e9] type 01 class 0x060400
[    0.178167] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.178223] pci 0000:00:0c.0: System wakeup disabled by ACPI
[    0.178257] pci 0000:00:0d.0: [10de:03d0] type 00 class 0x030000
[    0.178264] pci 0000:00:0d.0: reg 0x10: [mem 0xfb000000-0xfbffffff]
[    0.178271] pci 0000:00:0d.0: reg 0x14: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.178276] pci 0000:00:0d.0: reg 0x1c: [mem 0xfc000000-0xfcffffff 64bit]
[    0.178283] pci 0000:00:0d.0: reg 0x30: [mem 0x00000000-0x0001ffff pref]
[    0.178373] pci 0000:00:18.0: [1022:1100] type 00 class 0x060000
[    0.178459] pci 0000:00:18.1: [1022:1101] type 00 class 0x060000
[    0.178537] pci 0000:00:18.2: [1022:1102] type 00 class 0x060000
[    0.178619] pci 0000:00:18.3: [1022:1103] type 00 class 0x060000
[    0.178743] pci 0000:01:05.0: [11c1:5811] type 00 class 0x0c0010
[    0.178756] pci 0000:01:05.0: reg 0x10: [mem 0xfd7ff000-0xfd7fffff]
[    0.178806] pci 0000:01:05.0: supports D1 D2
[    0.178809] pci 0000:01:05.0: PME# supported from D0 D1 D2 D3hot
[    0.178866] pci 0000:00:04.0: PCI bridge to [bus 01] (subtractive decode)
[    0.178869] pci 0000:00:04.0:   bridge window [io  0xb000-0xbfff]
[    0.178873] pci 0000:00:04.0:   bridge window [mem 0xfd700000-0xfd7fffff]
[    0.178876] pci 0000:00:04.0:   bridge window [mem 0xfde00000-0xfdefffff pref]
[    0.178879] pci 0000:00:04.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.178882] pci 0000:00:04.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.178884] pci 0000:00:04.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.178887] pci 0000:00:04.0:   bridge window [mem 0x000c0000-0x000dffff] (subtractive decode)
[    0.178890] pci 0000:00:04.0:   bridge window [mem 0x80000000-0xfebfffff] (subtractive decode)
[    0.178923] pci 0000:00:09.0: PCI bridge to [bus 02]
[    0.178927] pci 0000:00:09.0:   bridge window [io  0xa000-0xafff]
[    0.178930] pci 0000:00:09.0:   bridge window [mem 0xfdd00000-0xfddfffff]
[    0.178934] pci 0000:00:09.0:   bridge window [mem 0xfdc00000-0xfdcfffff 64bit pref]
[    0.178968] pci 0000:00:0b.0: PCI bridge to [bus 03]
[    0.178972] pci 0000:00:0b.0:   bridge window [io  0x9000-0x9fff]
[    0.178975] pci 0000:00:0b.0:   bridge window [mem 0xfdb00000-0xfdbfffff]
[    0.178979] pci 0000:00:0b.0:   bridge window [mem 0xfda00000-0xfdafffff 64bit pref]
[    0.179010] pci 0000:00:0c.0: PCI bridge to [bus 04]
[    0.179014] pci 0000:00:0c.0:   bridge window [io  0x8000-0x8fff]
[    0.179017] pci 0000:00:0c.0:   bridge window [mem 0xfd900000-0xfd9fffff]
[    0.179021] pci 0000:00:0c.0:   bridge window [mem 0xfd800000-0xfd8fffff 64bit pref]
[    0.179030] pci_bus 0000:00: on NUMA node 0
[    0.179345] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.179399] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.179452] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.179507] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 *7 9 10 11 14 15)
[    0.179560] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.179612] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.179665] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.179718] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.179773] ACPI: PCI Interrupt Link [LIGP] (IRQs 5 *7 9 10 11 14 15)
[    0.179826] ACPI: PCI Interrupt Link [LP2P] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.179880] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 *10 11 14 15)
[    0.179934] ACPI: PCI Interrupt Link [LMAC] (IRQs *5 7 9 10 11 14 15)
[    0.179997] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 *11 14 15)
[    0.180052] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.180107] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 *7 9 10 11 14 15)
[    0.180166] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 10 *11 14 15)
[    0.180219] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.180273] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
[    0.180333] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 *10 11 14 15)
[    0.180432] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[    0.180520] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[    0.180607] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[    0.180692] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0
[    0.180777] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
[    0.180863] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
[    0.180952] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
[    0.181038] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
[    0.181124] ACPI: PCI Interrupt Link [AIGP] (IRQs 22 23) *0
[    0.181209] ACPI: PCI Interrupt Link [APCF] (IRQs 22 23) *0
[    0.181295] ACPI: PCI Interrupt Link [APCH] (IRQs 22 23) *0
[    0.181382] ACPI: PCI Interrupt Link [APMU] (IRQs 22 23) *0, disabled.
[    0.181468] ACPI: PCI Interrupt Link [AAZA] (IRQs 22 23) *0
[    0.181554] ACPI: PCI Interrupt Link [APCS] (IRQs 22 23) *0
[    0.181641] ACPI: PCI Interrupt Link [APCL] (IRQs 22 23) *0
[    0.181726] ACPI: PCI Interrupt Link [APCM] (IRQs 22 23) *0, disabled.
[    0.181813] ACPI: PCI Interrupt Link [APCZ] (IRQs 22 23) *0, disabled.
[    0.181899] ACPI: PCI Interrupt Link [APSI] (IRQs 20) *0
[    0.181984] ACPI: PCI Interrupt Link [APSJ] (IRQs 21) *0
[    0.182153] ACPI: \_SB_.PCI0: notify handler is installed
[    0.182199] Found 1 acpi root devices
[    0.182325] vgaarb: setting as boot device: PCI:0000:00:0d.0
[    0.182325] vgaarb: device added: PCI:0000:00:0d.0,decodes=io+mem,owns=io+mem,locks=none
[    0.182325] vgaarb: loaded
[    0.182325] vgaarb: bridge control possible 0000:00:0d.0
[    0.182325] SCSI subsystem initialized
[    0.182325] libata version 3.00 loaded.
[    0.182325] ACPI: bus type USB registered
[    0.182325] usbcore: registered new interface driver usbfs
[    0.182325] usbcore: registered new interface driver hub
[    0.182325] usbcore: registered new device driver usb
[    0.182325] PCI: Using ACPI for IRQ routing
[    0.184477] PCI: pci_cache_line_size set to 64 bytes
[    0.184518] e820: reserve RAM buffer [mem 0x0009f000-0x0009ffff]
[    0.184521] e820: reserve RAM buffer [mem 0x77ee0000-0x77ffffff]
[    0.184640] NetLabel: Initializing
[    0.184642] NetLabel:  domain hash size = 128
[    0.184643] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.184657] NetLabel:  unlabeled traffic allowed by default
[    0.184674] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.184674] hpet0: at MMIO 0xfefff000, IRQs 2, 8, 31
[    0.184674] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
[    0.186107] Switched to clocksource hpet
[    0.191015] AppArmor: AppArmor Filesystem Enabled
[    0.191054] pnp: PnP ACPI init
[    0.191074] ACPI: bus type PNP registered
[    0.191222] system 00:00: [io  0x1000-0x107f] has been reserved
[    0.191225] system 00:00: [io  0x1080-0x10ff] has been reserved
[    0.191228] system 00:00: [io  0x1400-0x147f] has been reserved
[    0.191231] system 00:00: [io  0x1480-0x14ff] has been reserved
[    0.191233] system 00:00: [io  0x1800-0x187f] has been reserved
[    0.191236] system 00:00: [io  0x1880-0x18ff] has been reserved
[    0.191241] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.191337] system 00:01: [io  0x04d0-0x04d1] has been reserved
[    0.191340] system 00:01: [io  0x0800-0x087f] has been reserved
[    0.191343] system 00:01: [io  0x0294-0x0297] has been reserved
[    0.191347] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.191359] pnp 00:02: [dma 4]
[    0.191381] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.191472] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.191520] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.191548] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.191584] pnp 00:06: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.191721] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.192336] system 00:08: [mem 0xf0000000-0xf3ffffff] has been reserved
[    0.192340] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.192357] ACPI Error: Field [ASSM] at 524320 exceeds Buffer [BUF0] size 880 (bits) (20131115/dsopcode-236)
[    0.192363] ACPI Error: Method parse/execution failed [\_SB_.MEM_._CRS] (Node f702d0a8), AE_AML_BUFFER_LIMIT (20131115/psparse-536)
[    0.192370] ACPI Error: Method execution failed [\_SB_.MEM_._CRS] (Node f702d0a8), AE_AML_BUFFER_LIMIT (20131115/uteval-103)
[    0.192376] pnp 00:09: can't evaluate _CRS: 12298
[    0.192419] system 00:09: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.192428] pnp: PnP ACPI: found 10 devices
[    0.192429] ACPI: bus type PNP unregistered
[    0.192432] PnPBIOS: Disabled by ACPI PNP
[    0.229645] pci 0000:00:0d.0: BAR 6: assigned [mem 0x80000000-0x8001ffff pref]
[    0.229650] pci 0000:00:04.0: PCI bridge to [bus 01]
[    0.229653] pci 0000:00:04.0:   bridge window [io  0xb000-0xbfff]
[    0.229657] pci 0000:00:04.0:   bridge window [mem 0xfd700000-0xfd7fffff]
[    0.229661] pci 0000:00:04.0:   bridge window [mem 0xfde00000-0xfdefffff pref]
[    0.229665] pci 0000:00:09.0: PCI bridge to [bus 02]
[    0.229668] pci 0000:00:09.0:   bridge window [io  0xa000-0xafff]
[    0.229671] pci 0000:00:09.0:   bridge window [mem 0xfdd00000-0xfddfffff]
[    0.229674] pci 0000:00:09.0:   bridge window [mem 0xfdc00000-0xfdcfffff 64bit pref]
[    0.229678] pci 0000:00:0b.0: PCI bridge to [bus 03]
[    0.229681] pci 0000:00:0b.0:   bridge window [io  0x9000-0x9fff]
[    0.229684] pci 0000:00:0b.0:   bridge window [mem 0xfdb00000-0xfdbfffff]
[    0.229687] pci 0000:00:0b.0:   bridge window [mem 0xfda00000-0xfdafffff 64bit pref]
[    0.229691] pci 0000:00:0c.0: PCI bridge to [bus 04]
[    0.229693] pci 0000:00:0c.0:   bridge window [io  0x8000-0x8fff]
[    0.229697] pci 0000:00:0c.0:   bridge window [mem 0xfd900000-0xfd9fffff]
[    0.229700] pci 0000:00:0c.0:   bridge window [mem 0xfd800000-0xfd8fffff 64bit pref]
[    0.229704] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.229707] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.229710] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.229712] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000dffff]
[    0.229715] pci_bus 0000:00: resource 8 [mem 0x80000000-0xfebfffff]
[    0.229718] pci_bus 0000:01: resource 0 [io  0xb000-0xbfff]
[    0.229721] pci_bus 0000:01: resource 1 [mem 0xfd700000-0xfd7fffff]
[    0.229723] pci_bus 0000:01: resource 2 [mem 0xfde00000-0xfdefffff pref]
[    0.229726] pci_bus 0000:01: resource 4 [io  0x0000-0x0cf7]
[    0.229729] pci_bus 0000:01: resource 5 [io  0x0d00-0xffff]
[    0.229732] pci_bus 0000:01: resource 6 [mem 0x000a0000-0x000bffff]
[    0.229734] pci_bus 0000:01: resource 7 [mem 0x000c0000-0x000dffff]
[    0.229737] pci_bus 0000:01: resource 8 [mem 0x80000000-0xfebfffff]
[    0.229740] pci_bus 0000:02: resource 0 [io  0xa000-0xafff]
[    0.229742] pci_bus 0000:02: resource 1 [mem 0xfdd00000-0xfddfffff]
[    0.229745] pci_bus 0000:02: resource 2 [mem 0xfdc00000-0xfdcfffff 64bit pref]
[    0.229748] pci_bus 0000:03: resource 0 [io  0x9000-0x9fff]
[    0.229750] pci_bus 0000:03: resource 1 [mem 0xfdb00000-0xfdbfffff]
[    0.229753] pci_bus 0000:03: resource 2 [mem 0xfda00000-0xfdafffff 64bit pref]
[    0.229756] pci_bus 0000:04: resource 0 [io  0x8000-0x8fff]
[    0.229759] pci_bus 0000:04: resource 1 [mem 0xfd900000-0xfd9fffff]
[    0.229762] pci_bus 0000:04: resource 2 [mem 0xfd800000-0xfd8fffff 64bit pref]
[    0.229803] NET: Registered protocol family 2
[    0.230027] TCP established hash table entries: 8192 (order: 3, 32768 bytes)
[    0.230050] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.230090] TCP: Hash tables configured (established 8192 bind 8192)
[    0.230125] TCP: reno registered
[    0.230128] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.230139] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.230205] NET: Registered protocol family 1
[    0.230493] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 23
[    0.230766] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
[    0.230884] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.230931] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.230987] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.231040] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.231094] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.231152] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.231213] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.231278] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.231285] pci 0000:00:0d.0: Video device with shadowed ROM
[    0.231295] PCI: CLS 32 bytes, default 64
[    0.231360] Trying to unpack rootfs image as initramfs...
[    0.621159] Freeing initrd memory: 18344K (f5c1c000 - f6e06000)
[    0.621336] microcode: AMD CPU family 0xf not supported
[    0.621339] Scanning for low memory corruption every 60 seconds
[    0.621640] Initialise system trusted keyring
[    0.621690] audit: initializing netlink socket (disabled)
[    0.621706] type=2000 audit(1457860870.620:1): initialized
[    0.645641] bounce pool size: 64 pages
[    0.645658] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.647077] zbud: loaded
[    0.647174] VFS: Disk quotas dquot_6.5.2
[    0.647228] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.647780] fuse init (API version 7.22)
[    0.647886] msgmni has been set to 1720
[    0.647965] Key type big_key registered
[    0.648601] Key type asymmetric registered
[    0.648604] Asymmetric key parser 'x509' registered
[    0.648645] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.648693] io scheduler noop registered
[    0.648695] io scheduler deadline registered (default)
[    0.648727] io scheduler cfq registered
[    0.648862] pcieport 0000:00:09.0: irq 40 for MSI/MSI-X
[    0.648916] pcieport 0000:00:0b.0: irq 41 for MSI/MSI-X
[    0.648960] pcieport 0000:00:0c.0: irq 42 for MSI/MSI-X
[    0.649021] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.649042] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.649093] vesafb: mode is 640x480x32, linelength=2560, pages=0
[    0.649095] vesafb: scrolling: redraw
[    0.649098] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    0.649476] vesafb: framebuffer at 0xe0000000, mapped to 0xf8480000, using 1216k, total 1216k
[    0.651535] Console: switching to colour frame buffer device 80x30
[    0.653469] fb0: VESA VGA frame buffer device
[    0.653504] ipmi message handler version 39.2
[    0.653593] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.653598] ACPI: Power Button [PWRB]
[    0.653652] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.653655] ACPI: Power Button [PWRF]
[    0.653702] ACPI: Fan [FAN] (on)
[    0.653963] ACPI: [Package] has zero elements (f7397540)
[    0.653965] ACPI: Invalid passive threshold
[    0.654176] thermal LNXTHERM:00: registered as thermal_zone0
[    0.654177] ACPI: Thermal Zone [THRM] (47 C)
[    0.654209] GHES: HEST is not enabled!
[    0.654316] isapnp: Scanning for PnP cards...
[    0.660068] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.661444] Linux agpgart interface v0.103
[    0.663018] brd: module loaded
[    0.663762] loop: module loaded
[    0.664362] libphy: Fixed MDIO Bus: probed
[    0.664497] tun: Universal TUN/TAP device driver, 1.6
[    0.664498] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.664543] PPP generic driver version 2.4.2
[    0.664585] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.664589] ehci-pci: EHCI PCI platform driver
[    0.664744] ehci-pci 0000:00:02.1: EHCI Host Controller
[    0.664752] ehci-pci 0000:00:02.1: new USB bus registered, assigned bus number 1
[    0.664761] ehci-pci 0000:00:02.1: debug port 1
[    0.664796] ehci-pci 0000:00:02.1: cache line size of 32 is not supported
[    0.664822] ehci-pci 0000:00:02.1: irq 22, io mem 0xfe02e000
[    0.676020] ehci-pci 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    0.676069] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.676071] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.676074] usb usb1: Product: EHCI Host Controller
[    0.676076] usb usb1: Manufacturer: Linux 3.13.0-79-generic ehci_hcd
[    0.676078] usb usb1: SerialNumber: 0000:00:02.1
[    0.676179] hub 1-0:1.0: USB hub found
[    0.676187] hub 1-0:1.0: 10 ports detected
[    0.676394] ehci-platform: EHCI generic platform driver
[    0.676404] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.676406] ohci-pci: OHCI PCI platform driver
[    0.676499] ohci-pci 0000:00:02.0: OHCI PCI host controller
[    0.676507] ohci-pci 0000:00:02.0: new USB bus registered, assigned bus number 2
[    0.676533] ohci-pci 0000:00:02.0: irq 23, io mem 0xfe02f000
[    0.734055] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    0.734058] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.734060] usb usb2: Product: OHCI PCI host controller
[    0.734063] usb usb2: Manufacturer: Linux 3.13.0-79-generic ohci_hcd
[    0.734065] usb usb2: SerialNumber: 0000:00:02.0
[    0.734182] hub 2-0:1.0: USB hub found
[    0.734192] hub 2-0:1.0: 10 ports detected
[    0.734391] ohci-platform: OHCI generic platform driver
[    0.734405] uhci_hcd: USB Universal Host Controller Interface driver
[    0.734486] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    0.734488] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    0.735129] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.735226] mousedev: PS/2 mouse device common for all mice
[    0.735349] rtc_cmos 00:04: RTC can wake from S4
[    0.735496] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.735534] rtc_cmos 00:04: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    0.735614] device-mapper: uevent: version 1.0.3
[    0.735681] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: [email]dm-devel@redhat.com[/email]
[    0.735701] platform eisa.0: Probing EISA bus 0
[    0.735705] platform eisa.0: EISA: Cannot allocate resource for mainboard
[    0.735708] platform eisa.0: Cannot allocate resource for EISA slot 1
[    0.735710] platform eisa.0: Cannot allocate resource for EISA slot 2
[    0.735713] platform eisa.0: Cannot allocate resource for EISA slot 3
[    0.735715] platform eisa.0: Cannot allocate resource for EISA slot 4
[    0.735718] platform eisa.0: Cannot allocate resource for EISA slot 5
[    0.735720] platform eisa.0: Cannot allocate resource for EISA slot 6
[    0.735723] platform eisa.0: Cannot allocate resource for EISA slot 7
[    0.735725] platform eisa.0: Cannot allocate resource for EISA slot 8
[    0.735728] platform eisa.0: EISA: Detected 0 cards
[    0.735735] cpufreq-nforce2: No nForce2 chipset.
[    0.735740] ledtrig-cpu: registered to indicate activity on CPUs
[    0.735882] TCP: cubic registered
[    0.735990] NET: Registered protocol family 10
[    0.736210] NET: Registered protocol family 17
[    0.736222] Key type dns_resolver registered
[    0.736376] Using IPI No-Shortcut mode
[    0.736447] Loading compiled-in X.509 certificates
[    0.740012] Loaded X.509 cert 'Magrathea: Glacier signing key: 68f8aeeaaf3565b11909193bdb8fb7424dd71170'
[    0.740029] registered taskstats version 1
[    0.753222] Key type trusted registered
[    0.757511] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    0.781066] Key type encrypted registered
[    0.781073] AppArmor: AppArmor sha1 policy hashing enabled
[    0.781075] IMA: No TPM chip found, activating TPM-bypass!
[    0.781289] regulator-dummy: disabling
[    0.781336]   Magic number: 8:732:373
[    0.781384] vc vcsa1: hash matches
[    0.781453] rtc_cmos 00:04: setting system clock to 2016-03-13 09:21:11 UTC (1457860871)
[    0.781596] powernow-k8: fid 0x10 (2400 MHz), vid 0xa
[    0.781598] powernow-k8: fid 0xe (2200 MHz), vid 0xc
[    0.781600] powernow-k8: fid 0xc (2000 MHz), vid 0xe
[    0.781602] powernow-k8: fid 0xa (1800 MHz), vid 0x10
[    0.781603] powernow-k8: fid 0x2 (1000 MHz), vid 0x12
[    0.781632] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 4600+ (2 cpu cores) (version 2.20.00)
[    0.781636] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.781638] EDD information not available.
[    0.781669] PM: Hibernation image not present or could not be loaded.
[    0.964867] isapnp: No Plug & Play device found
[    0.965411] Freeing unused kernel memory: 880K (c19c3000 - c1a9f000)
[    0.965459] Write protecting the kernel text: 6568k
[    0.965536] Write protecting the kernel read-only data: 2780k
[    0.965538] NX-protecting the kernel data: 5720k
[    0.981290] systemd-udevd[96]: starting version 204
[    1.009733] pata_amd 0000:00:06.0: version 0.4.1
[    1.010389] scsi0 : pata_amd
[    1.016064] scsi1 : pata_amd
[    1.016142] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    1.016144] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    1.016587] sata_nv 0000:00:08.0: version 3.5
[    1.016823] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 20
[    1.019304] scsi2 : sata_nv
[    1.020969] scsi3 : sata_nv
[    1.021035] ata3: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd800 irq 20
[    1.021038] ata4: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd808 irq 20
[    1.021292] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 21
[    1.023126] scsi4 : sata_nv
[    1.024377] scsi5 : sata_nv
[    1.024442] ata5: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xc400 irq 21
[    1.024445] ata6: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xc408 irq 21
[    1.032412] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.032672] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
[    1.045343] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[    1.100083] firewire_ohci 0000:01:05.0: added OHCI v1.0 device as card 0, 8 IR + 8 IT contexts, quirks 0x0
[    1.132020] usb 1-8: new high-speed USB device number 3 using ehci-pci
[    1.183017] ata2: port disabled--ignoring
[    1.265842] usb 1-8: New USB device found, idVendor=058f, idProduct=6377
[    1.265846] usb 1-8: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.265848] usb 1-8: Product: Mass Storage Device
[    1.265850] usb 1-8: Manufacturer: Generic
[    1.265853] usb 1-8: SerialNumber: 920321111113
[    1.350229] ata5: SATA link down (SStatus 0 SControl 300)
[    1.400555] usb-storage 1-8:1.0: USB Mass Storage device detected
[    1.400656] scsi6 : usb-storage 1-8:1.0
[    1.400742] usbcore: registered new interface driver usb-storage
[    1.492040] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.500126] ata3.00: ATA-8: WDC WD3200AAJS-65B4A0, 01.03A01, max UDMA/133
[    1.500130] ata3.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.516117] ata3.00: configured for UDMA/133
[    1.516286] scsi 2:0:0:0: Direct-Access     ATA      WDC WD3200AAJS-6 01.0 PQ: 0 ANSI: 5
[    1.516494] sd 2:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.516495] sd 2:0:0:0: Attached scsi generic sg0 type 0
[    1.516554] sd 2:0:0:0: [sda] Write Protect is off
[    1.516557] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.516604] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.556742] forcedeth 0000:00:07.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:22:15:25:dc:0a
[    1.556747] forcedeth 0000:00:07.0: highdma pwrctl mgmt lnktim msi desc-v3
[    1.568042] usb 2-2: new low-speed USB device number 2 using ohci-pci
[    1.574655]  sda: sda1 sda2 < sda5 >
[    1.575148] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.600121] firewire_core 0000:01:05.0: created device fw0: GUID 001e8c00014ecccf, S400
[    1.790065] usb 2-2: New USB device found, idVendor=045e, idProduct=0024
[    1.790068] usb 2-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.790071] usb 2-2: Product: Microsoft Trackball Explorer\xffffffc2\xffffffae\xffffffae
[    1.790073] usb 2-2: Manufacturer: Microsoft
[    1.801806] hidraw: raw HID events driver (C) Jiri Kosina
[    1.818562] usbcore: registered new interface driver usbhid
[    1.818566] usbhid: USB HID core driver
[    1.823424] input: Microsoft Microsoft Trackball Explorer\xffffffc2\xffffffae\xffffffae as /devices/pci0000:00/0000:00:02.0/usb2/2-2/2-2:1.0/input/input3
[    1.823891] hid-generic 0003:045E:0024.0001: input,hidraw0: USB HID v1.00 Mouse [Microsoft Microsoft Trackball Explorer\xffffffc2\xffffffae\xffffffae] on usb-0000:00:02.0-2/input0
[    1.984038] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.992124] ata4.00: ATAPI: TSSTcorp CDDVDW TS-H653Q, 0303, max UDMA/33
[    2.008118] ata4.00: configured for UDMA/33
[    2.009034] scsi 3:0:0:0: CD-ROM            TSSTcorp CDDVDW TS-H653Q  0303 PQ: 0 ANSI: 5
[    2.012567] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.012570] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.012693] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    2.012787] sr 3:0:0:0: Attached scsi generic sg1 type 5
[    2.334230] ata6: SATA link down (SStatus 0 SControl 300)
[    2.400867] scsi 6:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[    2.401488] scsi 6:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[    2.402111] scsi 6:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[    2.402736] scsi 6:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[    2.403035] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    2.403200] sd 6:0:0:1: Attached scsi generic sg3 type 0
[    2.403363] sd 6:0:0:2: Attached scsi generic sg4 type 0
[    2.403522] sd 6:0:0:3: Attached scsi generic sg5 type 0
[    2.416993] sd 6:0:0:1: [sdc] Attached SCSI removable disk
[    2.418873] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[    2.420741] sd 6:0:0:3: [sde] Attached SCSI removable disk
[    2.421370] sd 6:0:0:2: [sdd] Attached SCSI removable disk
[    2.620135] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    3.285380] random: init urandom read with 92 bits of entropy available
[    4.328115] random: nonblocking pool is initialized
[   10.030020] Adding 1963004k swap on /dev/sda5.  Priority:-1 extents:1 across:1963004k FS
[   10.084873] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   10.234901] systemd-udevd[275]: starting version 204
[   10.393337] i2c i2c-0: nForce2 SMBus adapter at 0x1c00
[   10.393368] i2c i2c-1: nForce2 SMBus adapter at 0x1c40
[   10.407642] lp: driver loaded but no devices found
[   10.429203] ppdev: user-space parallel port driver
[   10.534036] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   10.574588] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   10.624516] [drm] Initialized drm 1.1.0 20060810
[   10.693993] kvm: disabled by bios
[   10.714372] kvm: disabled by bios
[   10.719813] wmi: Mapper loaded
[   10.792379] checking generic (e0000000 130000) vs hw (e0000000 10000000)
[   10.792384] fb: conflicting fb hw usage nouveaufb vs VESA VGA - removing generic driver
[   10.792421] Console: switching to colour dummy device 80x25
[   10.806655] ACPI: PCI Interrupt Link [AIGP] enabled at IRQ 22
[   10.808968] [drm] hdmi device  not found 0 13 1
[   10.810695] nouveau  [  DEVICE][0000:00:0d.0] BOOT0  : 0x04c000a2
[   10.810701] nouveau  [  DEVICE][0000:00:0d.0] Chipset: C61 (NV4C)
[   10.810703] nouveau  [  DEVICE][0000:00:0d.0] Family : NV40
[   10.813940] type=1400 audit(1457860881.527:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=341 comm="apparmor_parser"
[   10.813950] type=1400 audit(1457860881.527:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=341 comm="apparmor_parser"
[   10.813956] type=1400 audit(1457860881.527:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=341 comm="apparmor_parser"
[   10.814503] type=1400 audit(1457860881.527:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=341 comm="apparmor_parser"
[   10.814510] type=1400 audit(1457860881.527:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=341 comm="apparmor_parser"
[   10.814799] type=1400 audit(1457860881.527:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=341 comm="apparmor_parser"
[   10.817066] type=1400 audit(1457860881.531:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=353 comm="apparmor_parser"
[   10.817078] type=1400 audit(1457860881.531:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=353 comm="apparmor_parser"
[   10.817083] type=1400 audit(1457860881.531:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=353 comm="apparmor_parser"
[   10.817645] type=1400 audit(1457860881.531:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=353 comm="apparmor_parser"
[   10.820120] nouveau  [   VBIOS][0000:00:0d.0] checking PRAMIN for image...
[   10.879022] nouveau  [   VBIOS][0000:00:0d.0] ... appears to be valid
[   10.879027] nouveau  [   VBIOS][0000:00:0d.0] using image from PRAMIN
[   10.879198] nouveau  [   VBIOS][0000:00:0d.0] BIT signature found
[   10.879202] nouveau  [   VBIOS][0000:00:0d.0] version 05.61.32.25.02
[   10.897507] nouveau 0000:00:0d.0: irq 43 for MSI/MSI-X
[   10.897522] nouveau  [     PMC][0000:00:0d.0] MSI interrupts enabled
[   10.897551] nouveau  [     PFB][0000:00:0d.0] RAM type: unknown
[   10.897553] nouveau  [     PFB][0000:00:0d.0] RAM size: 128 MiB
[   10.897555] nouveau  [     PFB][0000:00:0d.0]    ZCOMP: 0 tags
[   10.999104] nouveau  [  PTHERM][0000:00:0d.0] FAN control: none / external
[   10.999120] nouveau  [  PTHERM][0000:00:0d.0] fan management: automatic
[   10.999123] nouveau  [  PTHERM][0000:00:0d.0] internal sensor: no
[   11.021442] nouveau  [     CLK][0000:00:0d.0] 20: core 425 MHz shader 425 MHz 
[   11.021456] nouveau  [     CLK][0000:00:0d.0] --:   
[   11.021547] [TTM] Zone  kernel: Available graphics memory: 440834 kiB
[   11.021549] [TTM] Zone highmem: Available graphics memory: 966598 kiB
[   11.021550] [TTM] Initializing pool allocator
[   11.021555] [TTM] Initializing DMA pool allocator
[   11.021568] nouveau  [     DRM] VRAM: 125 MiB
[   11.021570] nouveau  [     DRM] GART: 512 MiB
[   11.021574] nouveau  [     DRM] TMDS table version 1.1
[   11.021577] nouveau  [     DRM] DCB version 3.0
[   11.021580] nouveau  [     DRM] DCB outp 00: 01000310 00000023
[   11.021583] nouveau  [     DRM] DCB outp 01: 00110204 98830003
[   11.021585] nouveau  [     DRM] DCB conn 00: 0000
[   11.021588] nouveau  [     DRM] DCB conn 01: 1131
[   11.021590] nouveau  [     DRM] DCB conn 02: 0110
[   11.021592] nouveau  [     DRM] DCB conn 03: 0111
[   11.021594] nouveau  [     DRM] DCB conn 04: 0113
[   11.022387] nouveau W[     DRM] DCB type 4 not known
[   11.022391] nouveau W[     DRM] Unknown-1 has no encoders, removing
[   11.023307] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[   11.023309] [drm] No driver support for vblank timestamp query.
[   11.026943] nouveau  [     DRM] MM: using M2MF for buffer copies
[   11.058426] nouveau  [     DRM] allocated 1280x1024 fb: 0x9000, bo f2f08800
[   11.058800] fbcon: nouveaufb (fb0) is primary device
[   11.132877] Console: switching to colour frame buffer device 160x64
[   11.134749] nouveau 0000:00:0d.0: fb0: nouveaufb frame buffer device
[   11.134752] nouveau 0000:00:0d.0: registered panic notifier
[   11.134764] [drm] Initialized nouveau 1.1.2 20120801 for 0000:00:0d.0 on minor 0
[   11.135980] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 23
[   11.135994] hda_intel: Disabling MSI
[   11.136048] hda-intel 0000:00:05.0: Disabling 64bit DMA
[   11.144093] hda-intel 0000:00:05.0: Enable delay in RIRB handling
[   11.788032] hda_codec: ALC1200: SKU not ready 0x411111f0
[   11.860020] autoconfig: line_outs=4 (0x14/0x15/0x16/0x17/0x0) type:line
[   11.860025]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   11.860027]    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[   11.860028]    mono: mono_out=0x0
[   11.860030]    dig-out=0x1e/0x0
[   11.860031]    inputs:
[   11.860033]      Front Mic=0x19
[   11.860035]      Rear Mic=0x18
[   11.860037]      Line=0x1c
[   11.860039] realtek: No valid SSID, checking pincfg 0x411111f0 for NID 0x1d
[   11.860041] realtek: Enable default setup for auto mode as fallback
[   12.848843] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   13.403317] init: failsafe main process (566) killed by TERM signal
[   13.654874] Bluetooth: Core ver 2.17
[   13.654900] NET: Registered protocol family 31
[   13.654902] Bluetooth: HCI device and connection manager initialized
[   13.655152] Bluetooth: HCI socket layer initialized
[   13.655157] Bluetooth: L2CAP socket layer initialized
[   13.655163] Bluetooth: SCO socket layer initialized
[   13.676510] input: HDA NVidia Front Headphone as /devices/pci0000:00/0000:00:05.0/sound/card0/input11
[   13.679909] input: HDA NVidia Line Out Side as /devices/pci0000:00/0000:00:05.0/sound/card0/input10
[   13.680090] input: HDA NVidia Line Out CLFE as /devices/pci0000:00/0000:00:05.0/sound/card0/input9
[   13.680215] input: HDA NVidia Line Out Surround as /devices/pci0000:00/0000:00:05.0/sound/card0/input8
[   13.680336] input: HDA NVidia Line Out Front as /devices/pci0000:00/0000:00:05.0/sound/card0/input7
[   13.680456] input: HDA NVidia Line as /devices/pci0000:00/0000:00:05.0/sound/card0/input6
[   13.680581] input: HDA NVidia Rear Mic as /devices/pci0000:00/0000:00:05.0/sound/card0/input5
[   13.680710] input: HDA NVidia Front Mic as /devices/pci0000:00/0000:00:05.0/sound/card0/input4
[   13.687576] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   13.687581] Bluetooth: BNEP filters: protocol multicast
[   13.687594] Bluetooth: BNEP socket layer initialized
[   13.710412] Bluetooth: RFCOMM TTY layer initialized
[   13.710430] Bluetooth: RFCOMM socket layer initialized
[   13.710437] Bluetooth: RFCOMM ver 1.11
[   16.162246] forcedeth 0000:00:07.0: irq 44 for MSI/MSI-X
[   16.162284] forcedeth 0000:00:07.0 eth0: MSI enabled
[   17.865994] nouveau E[    PBUS][0000:00:0d.0] MMIO write of 0x00a40001 FAULT at 0x00b000
[   18.040186] init: plymouth-upstart-bridge main process ended, respawning
[   18.054217] init: plymouth-upstart-bridge main process ended, respawning
cheapo@cheapo-KX733AA-ABU-a6511-uk:~$
```

I've only just realized that the first dmesg I posted was incomplete. Oops. :?

I also need an upgrade in my brain.
 The graphics on this machine are built in, no PCI cards of anything else of that nature plugged in.

Anyhoo, still getting freez-ups when trying to open multiple Firefoxes.

Ok, Lubuntu 15.10 is going in alongside 14.04 . Catch you later.

15.10 is looking all good so far. I have three web browsers open and three different videos playing, including on the BBC after I installed the flash plugin installer.

So I'll be going out for a couple of hours later and post the result of another boot later. :)

---

### Post by cheapodonuts on 2016-03-13
Well, 15.10 seems to work, but boot time was around three donuts. Still, I'm not disappointed as I can open several different browsers concurrently. 
Sorry Trusty, but you're goin bye bye. :)

Thanx for all the help anyhoo you guys. Have some donuts.

[[IMG]http://i81.photobucket.com/albums/j226/chashugh/donuts-3.jpg[/IMG]](http://s81.photobucket.com/user/chashugh/media/donuts-3.jpg.html)

---

### Post by Bucky Ball on 2016-03-13
Yum. Please see the first link in my signature to mark the thread as solved. Happy baking. :)

---

### Post by cheapodonuts on 2016-03-16
Yah, I've done that. I actually had it marked as solved for a short while before, but I felt it wasn't solved in a way that will help anyone who sees the title and comes to find a solution. And it's not really solved anyhow. As my new install of 15.10 has a long boot time and graphics hang-ups too. But, I'm off to the "Installation" section to complain over there. :rolleyes:

---

### Post by Bucky Ball on 2016-03-16
Marking as solved will save people time (they won't waste time coming here to help you) and, even though you didn't fix the original problem, you found a 'workaround', so to speak, even if it was a rather radical one. 

In the absence of 'resolved' or closing threads, 'solved' it is. Thanks.

---

