---
title: "Many Dmesg errors, how to fix"
date: 2014-08-10
forum: General Help
---

### Post by geemac2 on 2014-08-10
Hello,

I was wondering if there is anyone that can help with this mess.  My Ubuntu 14.04 is working fine and tweaked to where I want it.  I am using the LXDE desktop interface instead of the Unity mess.
I finally have my TV tuners working but can't seem to get the ATI RF remote working (noted as X10 remote) Not a major issue though.
The items that are noted below that show during boot is the most annoying thing when booting up my HTPC to watch a movie or TV.
I have Grub in Quiet but this shows after the Grub boot.  Is there any way of turning that off? 
The soc_camera, mx1_camera and mx2_camera apparently started after I installed V4L2. The camera message shows with or without the USB camera plugged in.  The camera messages shows right after Grub is done.
And then this **_*[COLOR=#000080]appamor [/COLOR]*_**mess,  is that normal?

Any help would be greatly appreciated... Thanks in advance.
*GEEMac*

[SIZE=2][COLOR=#008000]**Somewhat Solved with some good input and advice below...**[/COLOR][/SIZE]

```

**dmesg**
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.13.0-24-generic (buildd@batsu) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #47-Ubuntu SMP Fri May 2 23:30:00 UTC 2014 (Ubuntu 3.13.0-24.47-generic 3.13.9)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic root=UUID=8dec5fcf-a135-4805-9d2c-7699da53325a ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009fbff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009fc00-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000007bfaffff] usable
[    0.000000] BIOS-e820: [mem 0x000000007bfb0000-0x000000007bfbdfff] ACPI data
[    0.000000] BIOS-e820: [mem 0x000000007bfbe000-0x000000007bfeffff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000007bff0000-0x000000007bffdfff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000feefffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fff00000-0x00000000ffffffff] reserved
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.5 present.
[    0.000000] DMI: MSI MS-7349/MS-7349, BIOS CaptiveWorks CW-3000HD V2.37 03/19/2008
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x7bfb0 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
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
[    0.000000] found SMP MP-table at [mem 0x000ff780-0x000ff78f] mapped at [ffff8800000ff780]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01fdd000, 0x01fddfff] PGTABLE
[    0.000000] BRK [0x01fde000, 0x01fdefff] PGTABLE
[    0.000000] BRK [0x01fdf000, 0x01fdffff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x7bc00000-0x7bdfffff]
[    0.000000]  [mem 0x7bc00000-0x7bdfffff] page 2M
[    0.000000] BRK [0x01fe0000, 0x01fe0fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x78000000-0x7bbfffff]
[    0.000000]  [mem 0x78000000-0x7bbfffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0x77ffffff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x77ffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x7be00000-0x7bfaffff]
[    0.000000]  [mem 0x7be00000-0x7bfaffff] page 4k
[    0.000000] BRK [0x01fe1000, 0x01fe1fff] PGTABLE
[    0.000000] RAMDISK: [mem 0x36d91000-0x37feffff]
[    0.000000] ACPI: RSDP 00000000000f9c30 000014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 000000007bfb0000 000040 (v01 031908 RSDT1457 20080319 MSFT 00000097)
[    0.000000] ACPI: FACP 000000007bfb0200 000084 (v02 031908 FACP1457 20080319 MSFT 00000097)
[    0.000000] ACPI: DSDT 000000007bfb0440 005476 (v01  1ADQX 1ADQX003 00000003 INTL 20051117)
[    0.000000] ACPI: FACS 000000007bfbe000 000040
[    0.000000] ACPI: APIC 000000007bfb0390 000070 (v01 031908 APIC1457 20080319 MSFT 00000097)
[    0.000000] ACPI: MCFG 000000007bfb0400 00003C (v01 031908 OEMMCFG  20080319 MSFT 00000097)
[    0.000000] ACPI: OEMB 000000007bfbe040 000071 (v01 031908 OEMB1457 20080319 MSFT 00000097)
[    0.000000] ACPI: HPET 000000007bfb58c0 000038 (v01 031908 OEMHPET0 20080319 MSFT 00000097)
[    0.000000] ACPI: NVHD 000000007bfbe0c0 000554 (v01 031908  NVHDCP  20080319 MSFT 00000097)
[    0.000000] ACPI: SSDT 000000007bfb5900 000206 (v01 A M I  POWERNOW 00000001 AMD  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000007bfaffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x7bfaffff]
[    0.000000]   NODE_DATA [mem 0x7bfab000-0x7bfaffff]
[    0.000000]  [ffffea0000000000-ffffea0001ffffff] PMD -> [ffff880079600000-ffff88007b5fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   empty
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009efff]
[    0.000000]   node   0: [mem 0x00100000-0x7bfaffff]
[    0.000000] On node 0 totalpages: 507726
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3998 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 7871 pages used for memmap
[    0.000000]   DMA32 zone: 503728 pages, LIFO batch:31
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x2008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
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
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
[    0.000000] smpboot: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
[    0.000000] e820: [mem 0x7bffe000-0xfebfffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 29 pages/cpu @ffff88007bc00000 s86336 r8192 d24256 u1048576
[    0.000000] pcpu-alloc: s86336 r8192 d24256 u1048576 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 499770
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic root=UUID=8dec5fcf-a135-4805-9d2c-7699da53325a ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Node 0: aperture @ f204000000 size 32 MB
[    0.000000] Aperture beyond 4GB. Ignoring.
[    0.000000] Memory: 1962468K/2030904K available (7338K kernel code, 1138K rwdata, 3388K rodata, 1332K init, 1440K bss, 68436K reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=2.
[    0.000000]     Offload RCU callbacks from all CPUs
[    0.000000]     Offload RCU callbacks from CPUs: 0-1.
[    0.000000] NR_IRQS:16640 nr_irqs:512 16
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 8388608 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 2092.529 MHz processor
[    0.000000] tsc: Marking TSC unstable due to TSCs unsynchronized
[    0.004006] Calibrating delay loop (skipped), value calculated using timer frequency.. 4185.05 BogoMIPS (lpj=8370116)
[    0.004010] pid_max: default: 32768 minimum: 301
[    0.004045] Security Framework initialized
[    0.004073] AppArmor: AppArmor initialized
[    0.004074] Yama: becoming mindful.
[    0.004361] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.005786] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.006496] Mount-cache hash table entries: 4096 (order: 3, 32768 bytes)
[    0.006503] Mountpoint-cache hash table entries: 4096 (order: 3, 32768 bytes)
[    0.006850] Initializing cgroup subsys memory
[    0.006861] Initializing cgroup subsys devices
[    0.006864] Initializing cgroup subsys freezer
[    0.006867] Initializing cgroup subsys blkio
[    0.006870] Initializing cgroup subsys perf_event
[    0.006873] Initializing cgroup subsys hugetlb
[    0.006899] tseg: 0000000000
[    0.006908] CPU: Physical Processor ID: 0
[    0.006909] CPU: Processor Core ID: 0
[    0.006912] mce: CPU supports 5 MCE banks
[    0.006920] LVT offset 0 assigned for vector 0xf9
[    0.006925] process: using AMD E400 aware idle routine
[    0.006928] Last level iTLB entries: 4KB 512, 2MB 8, 4MB 4
[    0.006928] Last level dTLB entries: 4KB 512, 2MB 8, 4MB 4
[    0.006928] tlb_flushall_shift: 4
[    0.007076] Freeing SMP alternatives memory: 32K (ffffffff81e6b000 - ffffffff81e73000)
[    0.008320] ACPI: Core revision 20131115
[    0.011793] ACPI: All ACPI Tables successfully acquired
[    0.012020] ftrace: allocating 28408 entries in 111 pages
[    0.024802] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.065306] smpboot: CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 4000+ (fam: 0f, model: 6b, stepping: 01)
[    0.070079] Performance Events: AMD PMU driver.
[    0.070087] ... version:                0
[    0.070089] ... bit width:              48
[    0.070091] ... generic registers:      4
[    0.070092] ... value mask:             0000ffffffffffff
[    0.070094] ... max period:             00007fffffffffff
[    0.070095] ... fixed-purpose events:   0
[    0.070097] ... event mask:             000000000000000f
[    0.072591] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.072816] x86: Booting SMP configuration:
[    0.072819] .... node  #0, CPUs:      #1
[    0.160144] x86: Booted up 1 node, 2 CPUs
[    0.160148] smpboot: Total of 2 processors activated (8369.85 BogoMIPS)
[    0.160854] devtmpfs: initialized
[    0.165808] EVM: security.selinux
[    0.165810] EVM: security.SMACK64
[    0.165812] EVM: security.ima
[    0.165813] EVM: security.capability
[    0.165857] PM: Registering ACPI NVS region [mem 0x7bfbe000-0x7bfeffff] (204800 bytes)
[    0.165857] pinctrl core: initialized pinctrl subsystem
[    0.165857] regulator-dummy: no parameters
[    0.165865] RTC time: 21:39:57, date: 08/10/14
[    0.165933] NET: Registered protocol family 16
[    0.166112] cpuidle: using governor ladder
[    0.166114] cpuidle: using governor menu
[    0.166121] node 0 link 0: io port [1000, ffffff]
[    0.166124] node 0 link 0: io port [2000, 2fff]
[    0.166127] TOM: 0000000080000000 aka 2048M
[    0.168011] node 0 link 0: mmio [e0000000, efffffff]
[    0.168018] node 0 link 0: mmio [a0000, bffff]
[    0.168020] node 0 link 0: mmio [80000000, fe0bffff]
[    0.168024] bus: [bus 00-ff] on node 0 link 0
[    0.168026] bus: 00 [io  0x0000-0xffff]
[    0.168029] bus: 00 [mem 0x80000000-0xfcffffffff]
[    0.168031] bus: 00 [mem 0x000a0000-0x000bffff]
[    0.168083] ACPI: bus type PCI registered
[    0.168086] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.168175] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.168178] PCI: not using MMCONFIG
[    0.168181] PCI: Using configuration type 1 for base access
[    0.169700] bio: create slab <bio-0> at 0
[    0.169700] ACPI: Added _OSI(Module Device)
[    0.169700] ACPI: Added _OSI(Processor Device)
[    0.169700] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.169700] ACPI: Added _OSI(Processor Aggregator Device)
[    0.172576] ACPI: Executed 1 blocks of module-level executable AML code
[    0.175975] ACPI: Interpreter enabled
[    0.175988] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)
[    0.176004] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S3_] (20131115/hwxface-580)
[    0.176019] ACPI: (supports S0 S1 S4 S5)
[    0.176021] ACPI: Using IOAPIC for interrupt routing
[    0.176053] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.177512] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.187912] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.188154] ACPI: No dock devices found.
[    0.197876] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.197886] acpi PNP0A03:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.198235] acpi PNP0A03:00: _OSC: OS now controls [PCIeHotplug PME AER PCIeCapability]
[    0.198697] PCI host bridge to bus 0000:00
[    0.198701] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.198704] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.198707] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.198711] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.198714] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000dffff]
[    0.198717] pci_bus 0000:00: root bus resource [mem 0x80000000-0xdfffffff]
[    0.198720] pci_bus 0000:00: root bus resource [mem 0xf0000000-0xfebfffff]
[    0.198745] pci 0000:00:00.0: [10de:0547] type 00 class 0x050000
[    0.199017] pci 0000:00:01.0: [10de:0548] type 00 class 0x060100
[    0.199027] pci 0000:00:01.0: reg 0x10: [io  0x2f00-0x2fff]
[    0.199151] pci 0000:00:01.1: [10de:0542] type 00 class 0x0c0500
[    0.199165] pci 0000:00:01.1: reg 0x10: [io  0xdc00-0xdc3f]
[    0.199185] pci 0000:00:01.1: reg 0x20: [io  0x2d00-0x2d3f]
[    0.199192] pci 0000:00:01.1: reg 0x24: [io  0x2e00-0x2e3f]
[    0.199226] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.199287] pci 0000:00:01.1: System wakeup disabled by ACPI
[    0.199338] pci 0000:00:02.0: [10de:055e] type 00 class 0x0c0310
[    0.199350] pci 0000:00:02.0: reg 0x10: [mem 0xfbfff000-0xfbffffff]
[    0.199394] pci 0000:00:02.0: supports D1 D2
[    0.199397] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.199454] pci 0000:00:02.0: System wakeup disabled by ACPI
[    0.199502] pci 0000:00:02.1: [10de:055f] type 00 class 0x0c0320
[    0.199516] pci 0000:00:02.1: reg 0x10: [mem 0xfbffec00-0xfbffecff]
[    0.199569] pci 0000:00:02.1: supports D1 D2
[    0.199571] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.199629] pci 0000:00:02.1: System wakeup disabled by ACPI
[    0.199679] pci 0000:00:04.0: [10de:055e] type 00 class 0x0c0310
[    0.199691] pci 0000:00:04.0: reg 0x10: [mem 0xfbffd000-0xfbffdfff]
[    0.199736] pci 0000:00:04.0: supports D1 D2
[    0.199739] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.199797] pci 0000:00:04.0: System wakeup disabled by ACPI
[    0.199842] pci 0000:00:04.1: [10de:055f] type 00 class 0x0c0320
[    0.199856] pci 0000:00:04.1: reg 0x10: [mem 0xfbffe800-0xfbffe8ff]
[    0.199909] pci 0000:00:04.1: supports D1 D2
[    0.199912] pci 0000:00:04.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.199969] pci 0000:00:04.1: System wakeup disabled by ACPI
[    0.200031] pci 0000:00:06.0: [10de:0560] type 00 class 0x01018a
[    0.200059] pci 0000:00:06.0: reg 0x20: [io  0xffa0-0xffaf]
[    0.200182] pci 0000:00:07.0: [10de:055c] type 00 class 0x040300
[    0.200197] pci 0000:00:07.0: reg 0x10: [mem 0xfbff8000-0xfbffbfff]
[    0.200251] pci 0000:00:07.0: PME# supported from D3hot D3cold
[    0.200309] pci 0000:00:07.0: System wakeup disabled by ACPI
[    0.200359] pci 0000:00:08.0: [10de:0561] type 01 class 0x060401
[    0.200452] pci 0000:00:08.0: System wakeup disabled by ACPI
[    0.200498] pci 0000:00:09.0: [10de:0550] type 00 class 0x010185
[    0.200510] pci 0000:00:09.0: reg 0x10: [io  0xd480-0xd487]
[    0.200516] pci 0000:00:09.0: reg 0x14: [io  0xd400-0xd403]
[    0.200523] pci 0000:00:09.0: reg 0x18: [io  0xd080-0xd087]
[    0.200529] pci 0000:00:09.0: reg 0x1c: [io  0xd000-0xd003]
[    0.200535] pci 0000:00:09.0: reg 0x20: [io  0xcc00-0xcc0f]
[    0.200542] pci 0000:00:09.0: reg 0x24: [mem 0xfbff6000-0xfbff7fff]
[    0.200660] pci 0000:00:0a.0: [10de:054c] type 00 class 0x020000
[    0.200675] pci 0000:00:0a.0: reg 0x10: [mem 0xfbffc000-0xfbffcfff]
[    0.200682] pci 0000:00:0a.0: reg 0x14: [io  0xc880-0xc887]
[    0.200688] pci 0000:00:0a.0: reg 0x18: [mem 0xfbffe400-0xfbffe4ff]
[    0.200695] pci 0000:00:0a.0: reg 0x1c: [mem 0xfbffe000-0xfbffe00f]
[    0.200738] pci 0000:00:0a.0: supports D1 D2
[    0.200741] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.200801] pci 0000:00:0a.0: System wakeup disabled by ACPI
[    0.200849] pci 0000:00:0b.0: [10de:0562] type 01 class 0x060400
[    0.200887] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.200957] pci 0000:00:0b.0: System wakeup disabled by ACPI
[    0.201002] pci 0000:00:0c.0: [10de:0563] type 01 class 0x060400
[    0.201040] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.201103] pci 0000:00:0c.0: System wakeup disabled by ACPI
[    0.201149] pci 0000:00:0d.0: [10de:0563] type 01 class 0x060400
[    0.201186] pci 0000:00:0d.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.201251] pci 0000:00:0d.0: System wakeup disabled by ACPI
[    0.201297] pci 0000:00:0e.0: [10de:0563] type 01 class 0x060400
[    0.201335] pci 0000:00:0e.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.201398] pci 0000:00:0e.0: System wakeup disabled by ACPI
[    0.201445] pci 0000:00:0f.0: [10de:0563] type 01 class 0x060400
[    0.201483] pci 0000:00:0f.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.201546] pci 0000:00:0f.0: System wakeup disabled by ACPI
[    0.201594] pci 0000:00:10.0: [10de:0563] type 01 class 0x060400
[    0.201632] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.201695] pci 0000:00:10.0: System wakeup disabled by ACPI
[    0.201741] pci 0000:00:11.0: [10de:0563] type 01 class 0x060400
[    0.201779] pci 0000:00:11.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.201842] pci 0000:00:11.0: System wakeup disabled by ACPI
[    0.201886] pci 0000:00:12.0: [10de:053a] type 00 class 0x030000
[    0.201897] pci 0000:00:12.0: reg 0x10: [mem 0xfa000000-0xfaffffff]
[    0.201905] pci 0000:00:12.0: reg 0x14: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.201914] pci 0000:00:12.0: reg 0x1c: [mem 0xf9000000-0xf9ffffff 64bit]
[    0.201924] pci 0000:00:12.0: reg 0x30: [mem 0xfbfc0000-0xfbfdffff pref]
[    0.202039] pci 0000:00:18.0: [1022:1100] type 00 class 0x060000
[    0.202134] pci 0000:00:18.1: [1022:1101] type 00 class 0x060000
[    0.202223] pci 0000:00:18.2: [1022:1102] type 00 class 0x060000
[    0.202313] pci 0000:00:18.3: [1022:1103] type 00 class 0x060000
[    0.202467] pci 0000:01:07.0: [1106:3044] type 00 class 0x0c0010
[    0.202483] pci 0000:01:07.0: reg 0x10: [mem 0xfebff800-0xfebfffff]
[    0.202492] pci 0000:01:07.0: reg 0x14: [io  0xec00-0xec7f]
[    0.202552] pci 0000:01:07.0: supports D2
[    0.202554] pci 0000:01:07.0: PME# supported from D2 D3hot D3cold
[    0.202607] pci 0000:01:08.0: [1131:7133] type 00 class 0x048000
[    0.202623] pci 0000:01:08.0: reg 0x10: [mem 0xfebff000-0xfebff7ff]
[    0.202685] pci 0000:01:08.0: supports D1 D2
[    0.202734] pci 0000:01:09.0: [14f1:8800] type 00 class 0x040000
[    0.202750] pci 0000:01:09.0: reg 0x10: [mem 0xfd000000-0xfdffffff]
[    0.202863] pci 0000:01:09.2: [14f1:8802] type 00 class 0x048000
[    0.202878] pci 0000:01:09.2: reg 0x10: [mem 0xfc000000-0xfcffffff]
[    0.203002] pci 0000:00:08.0: PCI bridge to [bus 01] (subtractive decode)
[    0.203006] pci 0000:00:08.0:   bridge window [io  0xe000-0xefff]
[    0.203010] pci 0000:00:08.0:   bridge window [mem 0xfc000000-0xfebfffff]
[    0.203015] pci 0000:00:08.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.203017] pci 0000:00:08.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.203020] pci 0000:00:08.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.203023] pci 0000:00:08.0:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.203026] pci 0000:00:08.0:   bridge window [mem 0x80000000-0xdfffffff] (subtractive decode)
[    0.203029] pci 0000:00:08.0:   bridge window [mem 0xf0000000-0xfebfffff] (subtractive decode)
[    0.203077] pci 0000:00:0b.0: PCI bridge to [bus 02]
[    0.203125] pci 0000:00:0c.0: PCI bridge to [bus 03]
[    0.203174] pci 0000:00:0d.0: PCI bridge to [bus 04]
[    0.203221] pci 0000:00:0e.0: PCI bridge to [bus 05]
[    0.203271] pci 0000:00:0f.0: PCI bridge to [bus 06]
[    0.203323] pci 0000:00:10.0: PCI bridge to [bus 07]
[    0.203375] pci 0000:00:11.0: PCI bridge to [bus 08]
[    0.204446] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *10
[    0.204597] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *10
[    0.204742] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *0, disabled.
[    0.204891] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *10
[    0.205035] ACPI: PCI Interrupt Link [LNEA] (IRQs 16 17 18 19) *0, disabled.
[    0.205181] ACPI: PCI Interrupt Link [LNEB] (IRQs 16 17 18 19) *0, disabled.
[    0.205326] ACPI: PCI Interrupt Link [LNEC] (IRQs 16 17 18 19) *0, disabled.
[    0.205471] ACPI: PCI Interrupt Link [LNED] (IRQs 16 17 18 19) *0, disabled.
[    0.205620] ACPI: PCI Interrupt Link [LUB0] (IRQs 20 21 22 23) *10
[    0.205769] ACPI: PCI Interrupt Link [LUB2] (IRQs 20 21 22 23) *11
[    0.205917] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *11
[    0.206065] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *10
[    0.206213] ACPI: PCI Interrupt Link [SGRU] (IRQs 20 21 22 23) *10
[    0.206360] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *11
[    0.206514] ACPI: PCI Interrupt Link [LPMU] (IRQs 20 21 22 23) *0, disabled.
[    0.206662] ACPI: PCI Interrupt Link [LSA0] (IRQs 20 21 22 23) *5
[    0.206820] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.
[    0.206961] ACPI: PCI Interrupt Link [UB11] (IRQs 20 21 22 23) *10
[    0.207100] ACPI: PCI Interrupt Link [UB12] (IRQs 20 21 22 23) *10
[    0.207244] ACPI: \_SB_.PCI0: notify handler is installed
[    0.207296] Found 1 acpi root devices
[    0.207451] vgaarb: device added: PCI:0000:00:12.0,decodes=io+mem,owns=io+mem,locks=none
[    0.207451] vgaarb: loaded
[    0.207451] vgaarb: bridge control possible 0000:00:12.0
[    0.208121] SCSI subsystem initialized
[    0.208151] libata version 3.00 loaded.
[    0.208151] ACPI: bus type USB registered
[    0.208163] usbcore: registered new interface driver usbfs
[    0.208180] usbcore: registered new interface driver hub
[    0.208193] usbcore: registered new device driver usb
[    0.208193] PCI: Using ACPI for IRQ routing
[    0.215831] PCI: pci_cache_line_size set to 64 bytes
[    0.215895] e820: reserve RAM buffer [mem 0x0009fc00-0x0009ffff]
[    0.215899] e820: reserve RAM buffer [mem 0x7bfb0000-0x7bffffff]
[    0.216105] NetLabel: Initializing
[    0.216107] NetLabel:  domain hash size = 128
[    0.216108] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.216138] NetLabel:  unlabeled traffic allowed by default
[    0.216171] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.216171] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[    0.216171] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
[    0.218120] Switched to clocksource hpet
[    0.240299] AppArmor: AppArmor Filesystem Enabled
[    0.240366] pnp: PnP ACPI init
[    0.240398] ACPI: bus type PNP registered
[    0.240466] pnp 00:00: [dma 4]
[    0.240521] pnp 00:00: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.240577] pnp 00:01: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.240650] pnp 00:02: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.241010] pnp 00:03: [dma 0 disabled]
[    0.241100] pnp 00:03: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.242059] system 00:04: [io  0x04d0-0x04d1] has been reserved
[    0.242064] system 00:04: [io  0x0800-0x080f] has been reserved
[    0.242069] system 00:04: [io  0x2000-0x207f] could not be reserved
[    0.242074] system 00:04: [io  0x2080-0x20ff] has been reserved
[    0.242078] system 00:04: [io  0x2400-0x247f] has been reserved
[    0.242083] system 00:04: [io  0x2480-0x24ff] has been reserved
[    0.242088] system 00:04: [io  0x2800-0x287f] has been reserved
[    0.242092] system 00:04: [io  0x2880-0x28ff] has been reserved
[    0.242097] system 00:04: [io  0x2c00-0x2c7f] has been reserved
[    0.242101] system 00:04: [io  0x2c80-0x2cff] has been reserved
[    0.242107] system 00:04: [mem 0x000d0000-0x000d3fff window] has been reserved
[    0.242111] system 00:04: [mem 0x000d4000-0x000d7fff window] has been reserved
[    0.242116] system 00:04: [mem 0x000de000-0x000dffff window] has been reserved
[    0.242121] system 00:04: [mem 0xfefe0000-0xfefe01ff] has been reserved
[    0.242125] system 00:04: [mem 0xfefe1000-0xfefe1fff] has been reserved
[    0.242130] system 00:04: [mem 0xfee01000-0xfeefffff] has been reserved
[    0.242136] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.242269] pnp 00:05: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.242349] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.242466] system 00:07: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.242471] system 00:07: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.242477] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.242689] system 00:08: [io  0x0a00-0x0adf] has been reserved
[    0.242694] system 00:08: [io  0x0ae0-0x0aef] has been reserved
[    0.242699] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.242828] system 00:09: [mem 0xe0000000-0xefffffff] has been reserved
[    0.242834] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.243119] system 00:0a: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.243124] system 00:0a: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.243128] system 00:0a: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.243133] system 00:0a: [mem 0x00100000-0x7fffffff] could not be reserved
[    0.243138] system 00:0a: [mem 0xfec00000-0xffffffff] could not be reserved
[    0.243143] system 00:0a: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.243513] pnp: PnP ACPI: found 11 devices
[    0.243515] ACPI: bus type PNP unregistered
[    0.251965] pci 0000:00:08.0: PCI bridge to [bus 01]
[    0.251971] pci 0000:00:08.0:   bridge window [io  0xe000-0xefff]
[    0.251976] pci 0000:00:08.0:   bridge window [mem 0xfc000000-0xfebfffff]
[    0.251983] pci 0000:00:0b.0: PCI bridge to [bus 02]
[    0.251990] pci 0000:00:0c.0: PCI bridge to [bus 03]
[    0.251997] pci 0000:00:0d.0: PCI bridge to [bus 04]
[    0.252017] pci 0000:00:0e.0: PCI bridge to [bus 05]
[    0.252024] pci 0000:00:0f.0: PCI bridge to [bus 06]
[    0.252031] pci 0000:00:10.0: PCI bridge to [bus 07]
[    0.252038] pci 0000:00:11.0: PCI bridge to [bus 08]
[    0.252045] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.252048] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.252051] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.252054] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.252057] pci_bus 0000:00: resource 8 [mem 0x80000000-0xdfffffff]
[    0.252060] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfebfffff]
[    0.252063] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.252066] pci_bus 0000:01: resource 1 [mem 0xfc000000-0xfebfffff]
[    0.252068] pci_bus 0000:01: resource 4 [io  0x0000-0x0cf7]
[    0.252071] pci_bus 0000:01: resource 5 [io  0x0d00-0xffff]
[    0.252074] pci_bus 0000:01: resource 6 [mem 0x000a0000-0x000bffff]
[    0.252077] pci_bus 0000:01: resource 7 [mem 0x000d0000-0x000dffff]
[    0.252080] pci_bus 0000:01: resource 8 [mem 0x80000000-0xdfffffff]
[    0.252082] pci_bus 0000:01: resource 9 [mem 0xf0000000-0xfebfffff]
[    0.252143] NET: Registered protocol family 2
[    0.252392] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.252514] TCP bind hash table entries: 16384 (order: 6, 262144 bytes)
[    0.252677] TCP: Hash tables configured (established 16384 bind 16384)
[    0.252766] TCP: reno registered
[    0.252777] UDP hash table entries: 1024 (order: 3, 32768 bytes)
[    0.252811] UDP-Lite hash table entries: 1024 (order: 3, 32768 bytes)
[    0.252967] NET: Registered protocol family 1
[    0.253594] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 23
[    0.324805] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 22
[    0.325590] ACPI: PCI Interrupt Link [UB11] enabled at IRQ 21
[    0.396789] ACPI: PCI Interrupt Link [UB12] enabled at IRQ 20
[    0.397175] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.397234] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.397309] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.397383] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.397464] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.397550] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.397642] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.397740] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.397844] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.397954] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.397963] pci 0000:00:12.0: Boot video device
[    0.397985] PCI: CLS 64 bytes, default 64
[    0.398190] Trying to unpack rootfs image as initramfs...
[    0.978552] Freeing initrd memory: 18812K (ffff880036d91000 - ffff880037ff0000)
[    0.979082] microcode: AMD CPU family 0xf not supported
[    0.979086] Scanning for low memory corruption every 60 seconds
[    0.979603] Initialise system trusted keyring
[    0.979699] audit: initializing netlink socket (disabled)
[    0.979727] type=2000 audit(1407706796.976:1): initialized
[    1.013587] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.016587] VFS: Disk quotas dquot_6.5.2
[    1.016675] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.017771] fuse init (API version 7.22)
[    1.017900] msgmni has been set to 3869
[    1.017989] Key type big_key registered
[    1.018665] Key type asymmetric registered
[    1.018667] Asymmetric key parser 'x509' registered
[    1.018714] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    1.018763] io scheduler noop registered
[    1.018765] io scheduler deadline registered (default)
[    1.018803] io scheduler cfq registered
[    1.018974] pcieport 0000:00:0b.0: irq 40 for MSI/MSI-X
[    1.019060] pcieport 0000:00:0c.0: irq 41 for MSI/MSI-X
[    1.019133] pcieport 0000:00:0d.0: irq 42 for MSI/MSI-X
[    1.019205] pcieport 0000:00:0e.0: irq 43 for MSI/MSI-X
[    1.019278] pcieport 0000:00:0f.0: irq 44 for MSI/MSI-X
[    1.019346] pcieport 0000:00:10.0: irq 45 for MSI/MSI-X
[    1.019419] pcieport 0000:00:11.0: irq 46 for MSI/MSI-X
[    1.019519] pcieport 0000:00:0b.0: Signaling PME through PCIe PME interrupt
[    1.019523] pcie_pme 0000:00:0b.0:pcie01: service driver pcie_pme loaded
[    1.019541] pcieport 0000:00:0c.0: Signaling PME through PCIe PME interrupt
[    1.019545] pcie_pme 0000:00:0c.0:pcie01: service driver pcie_pme loaded
[    1.019562] pcieport 0000:00:0d.0: Signaling PME through PCIe PME interrupt
[    1.019566] pcie_pme 0000:00:0d.0:pcie01: service driver pcie_pme loaded
[    1.019583] pcieport 0000:00:0e.0: Signaling PME through PCIe PME interrupt
[    1.019587] pcie_pme 0000:00:0e.0:pcie01: service driver pcie_pme loaded
[    1.019608] pcieport 0000:00:0f.0: Signaling PME through PCIe PME interrupt
[    1.019611] pcie_pme 0000:00:0f.0:pcie01: service driver pcie_pme loaded
[    1.019627] pcieport 0000:00:10.0: Signaling PME through PCIe PME interrupt
[    1.019631] pcie_pme 0000:00:10.0:pcie01: service driver pcie_pme loaded
[    1.019648] pcieport 0000:00:11.0: Signaling PME through PCIe PME interrupt
[    1.019652] pcie_pme 0000:00:11.0:pcie01: service driver pcie_pme loaded
[    1.019672] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.019695] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.019773] ipmi message handler version 39.2
[    1.019860] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    1.019867] ACPI: Power Button [PWRB]
[    1.019923] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.019927] ACPI: Power Button [PWRF]
[    1.020103] GHES: HEST is not enabled!
[    1.020275] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.040691] 00:03: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
[    1.043358] Linux agpgart interface v0.103
[    1.045668] brd: module loaded
[    1.046909] loop: module loaded
[    1.047576] libphy: Fixed MDIO Bus: probed
[    1.047725] tun: Universal TUN/TAP device driver, 1.6
[    1.047727] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.047825] PPP generic driver version 2.4.2
[    1.047906] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.047920] ehci-pci: EHCI PCI platform driver
[    1.048189] ehci-pci 0000:00:02.1: EHCI Host Controller
[    1.048201] ehci-pci 0000:00:02.1: new USB bus registered, assigned bus number 1
[    1.048213] ehci-pci 0000:00:02.1: debug port 1
[    1.048250] ehci-pci 0000:00:02.1: cache line size of 64 is not supported
[    1.048281] ehci-pci 0000:00:02.1: irq 22, io mem 0xfbffec00
[    1.060024] ehci-pci 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    1.060113] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.060116] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.060119] usb usb1: Product: EHCI Host Controller
[    1.060121] usb usb1: Manufacturer: Linux 3.13.0-24-generic ehci_hcd
[    1.060124] usb usb1: SerialNumber: 0000:00:02.1
[    1.060338] hub 1-0:1.0: USB hub found
[    1.060351] hub 1-0:1.0: 6 ports detected
[    1.060716] ehci-pci 0000:00:04.1: EHCI Host Controller
[    1.060723] ehci-pci 0000:00:04.1: new USB bus registered, assigned bus number 2
[    1.060733] ehci-pci 0000:00:04.1: debug port 1
[    1.060767] ehci-pci 0000:00:04.1: cache line size of 64 is not supported
[    1.060792] ehci-pci 0000:00:04.1: irq 20, io mem 0xfbffe800
[    1.072023] ehci-pci 0000:00:04.1: USB 2.0 started, EHCI 1.00
[    1.072092] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.072095] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.072098] usb usb2: Product: EHCI Host Controller
[    1.072101] usb usb2: Manufacturer: Linux 3.13.0-24-generic ehci_hcd
[    1.072103] usb usb2: SerialNumber: 0000:00:04.1
[    1.072267] hub 2-0:1.0: USB hub found
[    1.072281] hub 2-0:1.0: 6 ports detected
[    1.072463] ehci-platform: EHCI generic platform driver
[    1.072478] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.072480] ohci-pci: OHCI PCI platform driver
[    1.072647] ohci-pci 0000:00:02.0: OHCI PCI host controller
[    1.072655] ohci-pci 0000:00:02.0: new USB bus registered, assigned bus number 3
[    1.072696] ohci-pci 0000:00:02.0: irq 23, io mem 0xfbfff000
[    1.130057] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    1.130060] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.130062] usb usb3: Product: OHCI PCI host controller
[    1.130065] usb usb3: Manufacturer: Linux 3.13.0-24-generic ohci_hcd
[    1.130068] usb usb3: SerialNumber: 0000:00:02.0
[    1.130247] hub 3-0:1.0: USB hub found
[    1.130260] hub 3-0:1.0: 6 ports detected
[    1.130594] ohci-pci 0000:00:04.0: OHCI PCI host controller
[    1.130601] ohci-pci 0000:00:04.0: new USB bus registered, assigned bus number 4
[    1.130633] ohci-pci 0000:00:04.0: irq 21, io mem 0xfbffd000
[    1.186047] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    1.186050] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.186053] usb usb4: Product: OHCI PCI host controller
[    1.186055] usb usb4: Manufacturer: Linux 3.13.0-24-generic ohci_hcd
[    1.186058] usb usb4: SerialNumber: 0000:00:04.0
[    1.186231] hub 4-0:1.0: USB hub found
[    1.186243] hub 4-0:1.0: 6 ports detected
[    1.186419] ohci-platform: OHCI generic platform driver
[    1.186433] uhci_hcd: USB Universal Host Controller Interface driver
[    1.186529] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    1.188937] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.188944] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.189150] mousedev: PS/2 mouse device common for all mice
[    1.189394] rtc_cmos 00:06: RTC can wake from S4
[    1.189596] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    1.189642] rtc_cmos 00:06: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    1.189741] device-mapper: uevent: version 1.0.3
[    1.189863] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
[    1.189872] ledtrig-cpu: registered to indicate activity on CPUs
[    1.190027] TCP: cubic registered
[    1.190162] NET: Registered protocol family 10
[    1.190421] NET: Registered protocol family 17
[    1.190435] Key type dns_resolver registered
[    1.190832] Loading compiled-in X.509 certificates
[    1.192193] Loaded X.509 cert 'Magrathea: Glacier signing key: 69b0d0a79b85d90621706e8d06604d730b359fc0'
[    1.192212] registered taskstats version 1
[    1.196464] Key type trusted registered
[    1.205670] Key type encrypted registered
[    1.214684] AppArmor: AppArmor sha1 policy hashing enabled
[    1.214688] IMA: No TPM chip found, activating TPM-bypass!
[    1.215074] regulator-dummy: disabling
[    1.215160]   Magic number: 10:125:702
[    1.215299] rtc_cmos 00:06: setting system clock to 2014-08-10 21:39:58 UTC (1407706798)
[    1.215510] powernow-k8: fid 0xd (2100 MHz), vid 0xa
[    1.215512] powernow-k8: fid 0xc (2000 MHz), vid 0xb
[    1.215514] powernow-k8: fid 0xa (1800 MHz), vid 0xd
[    1.215516] powernow-k8: fid 0x2 (1000 MHz), vid 0x12
[    1.215555] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 4000+ (2 cpu cores) (version 2.20.00)
[    1.215564] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.215566] EDD information not available.
[    1.215611] PM: Hibernation image not present or could not be loaded.
[    1.218055] Freeing unused kernel memory: 1332K (ffffffff81d1e000 - ffffffff81e6b000)
[    1.218061] Write protecting the kernel read-only data: 12288k
[    1.221786] Freeing unused kernel memory: 844K (ffff88000172d000 - ffff880001800000)
[    1.224862] Freeing unused kernel memory: 708K (ffff880001b4f000 - ffff880001c00000)
[    1.276462] systemd-udevd[114]: starting version 204
[    1.311893] pata_amd 0000:00:06.0: version 0.4.1
[    1.317002] scsi0 : pata_amd
[    1.317108] scsi1 : pata_amd
[    1.317157] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    1.317159] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    1.356130] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.356502] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 23
[    1.363285] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 19
[    1.416106] firewire_ohci 0000:01:07.0: added OHCI v1.10 device as card 0, 4 IR + 8 IT contexts, quirks 0x11
[    1.496352] ata1.00: ATAPI: Optiarc DVD RW AD-7190A, 1.02, max UDMA/66
[    1.496365] ata1: nv_mode_filter: 0x1f39f&0x1f39f->0x1f39f, BIOS=0x1f000 (0xc5000000) ACPI=0x1f01f (30:900:0x11)
[    1.528266] ata1.00: configured for UDMA/66
[    1.530424] scsi 0:0:0:0: CD-ROM            Optiarc  DVD RW AD-7190A  1.02 PQ: 0 ANSI: 5
[    1.533751] sr0: scsi3-mmc drive: 48x/12x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.533755] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.533912] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.534074] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.534308] ata2: port disabled--ignoring
[    1.688051] usb 2-4: new high-speed USB device number 3 using ehci-pci
[    1.835324] usb 2-4: New USB device found, idVendor=0aec, idProduct=3260
[    1.835331] usb 2-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.835334] usb 2-4: Product: USB Storage Device
[    1.835337] usb 2-4: Manufacturer: GENERIC
[    1.835339] usb 2-4: SerialNumber: 1234567890ABCDEND
[    1.839980] usb-storage 2-4:1.0: USB Mass Storage device detected
[    1.840150] scsi2 : usb-storage 2-4:1.0
[    1.840290] usbcore: registered new interface driver usb-storage
[    1.881017] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:1d:92:2c:87:41
[    1.881024] forcedeth 0000:00:0a.0: highdma pwrctl mgmt gbit lnktim msi desc-v3
[    1.881070] ahci 0000:00:09.0: version 3.0
[    1.881442] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 22
[    1.881480] ahci 0000:00:09.0: controller can't do PMP, turning off CAP_PMP
[    1.881541] ahci 0000:00:09.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl IDE mode
[    1.881545] ahci 0000:00:09.0: flags: 64bit ncq sntf led clo pio 
[    1.882423] scsi3 : ahci
[    1.882526] scsi4 : ahci
[    1.882620] scsi5 : ahci
[    1.882707] scsi6 : ahci
[    1.882762] ata3: SATA max UDMA/133 abar m8192@0xfbff6000 port 0xfbff6100 irq 22
[    1.882765] ata4: SATA max UDMA/133 abar m8192@0xfbff6000 port 0xfbff6180 irq 22
[    1.882767] ata5: SATA max UDMA/133 abar m8192@0xfbff6000 port 0xfbff6200 irq 22
[    1.882770] ata6: SATA max UDMA/133 abar m8192@0xfbff6000 port 0xfbff6280 irq 22
[    1.916159] firewire_core 0000:01:07.0: created device fw0: GUID 00110666013ae4f9, S400
[    2.192032] usb 4-1: new low-speed USB device number 2 using ohci-pci
[    2.200033] ata5: SATA link down (SStatus 0 SControl 300)
[    2.200056] ata4: SATA link down (SStatus 0 SControl 300)
[    2.200081] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.204025] ata6: SATA link down (SStatus 0 SControl 300)
[    2.238311] ata3.00: ATA-7: MAXTOR STM3320620AS, 3.AAE, max UDMA/133
[    2.238314] ata3.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.296613] ata3.00: configured for UDMA/133
[    2.296840] scsi 3:0:0:0: Direct-Access     ATA      MAXTOR STM332062 3.AA PQ: 0 ANSI: 5
[    2.297092] sd 3:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    2.297165] sd 3:0:0:0: [sda] Write Protect is off
[    2.297168] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.297190] sd 3:0:0:0: Attached scsi generic sg1 type 0
[    2.297200] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.358942]  sda: sda1 sda2 < sda5 >
[    2.359647] sd 3:0:0:0: [sda] Attached SCSI disk
[    2.407050] usb 4-1: New USB device found, idVendor=0bc7, idProduct=0004
[    2.407056] usb 4-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.407059] usb 4-1: Product: USB Receiver
[    2.407062] usb 4-1: Manufacturer: X10 Wireless Technology Inc
[    2.712056] usb 4-5: new low-speed USB device number 3 using ohci-pci
[    2.844729] scsi 2:0:0:0: Direct-Access     GENERIC  USB Storage-CFC  I20B PQ: 0 ANSI: 0 CCS
[    2.848716] scsi 2:0:0:1: Direct-Access     GENERIC  USB Storage-SDC  I20B PQ: 0 ANSI: 0 CCS
[    2.852712] scsi 2:0:0:2: Direct-Access     GENERIC  USB Storage-SMC  I20B PQ: 0 ANSI: 0 CCS
[    2.856723] scsi 2:0:0:3: Direct-Access     GENERIC  USB Storage-MSC  I20B PQ: 0 ANSI: 0 CCS
[    2.857082] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    2.857292] sd 2:0:0:1: Attached scsi generic sg3 type 0
[    2.857503] sd 2:0:0:2: Attached scsi generic sg4 type 0
[    2.857702] sd 2:0:0:3: Attached scsi generic sg5 type 0
[    2.866092] sd 2:0:0:0: [sdb] 7928928 512-byte logical blocks: (4.05 GB/3.78 GiB)
[    2.869967] sd 2:0:0:0: [sdb] Write Protect is off
[    2.869972] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[    2.872960] sd 2:0:0:0: [sdb] No Caching mode page found
[    2.872964] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    2.876226] sd 2:0:0:1: [sdc] Attached SCSI removable disk
[    2.876974] sd 2:0:0:2: [sdd] Attached SCSI removable disk
[    2.877711] sd 2:0:0:3: [sde] Attached SCSI removable disk
[    2.880973] sd 2:0:0:0: [sdb] No Caching mode page found
[    2.880979] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    2.883388]  sdb: sdb1
[    2.888982] sd 2:0:0:0: [sdb] No Caching mode page found
[    2.888991] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    2.888996] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[    2.924042] usb 4-5: New USB device found, idVendor=099a, idProduct=7202
[    2.924048] usb 4-5: New USB device strings: Mfr=0, Product=2, SerialNumber=0
[    2.924051] usb 4-5: Product: Wireless Keyboard/Mouse
[    2.931855] hidraw: raw HID events driver (C) Jiri Kosina
[    2.953031] usbcore: registered new interface driver usbhid
[    2.953038] usbhid: USB HID core driver
[    2.958261] input: Wireless Keyboard/Mouse as /devices/pci0000:00/0000:00:04.0/usb4/4-5/4-5:1.0/input/input5
[    2.959128] hid-generic 0003:099A:7202.0001: input,hidraw0: USB HID v1.11 Keyboard [Wireless Keyboard/Mouse] on usb-0000:00:04.0-5/input0
[    2.960849] input: Wireless Keyboard/Mouse as /devices/pci0000:00/0000:00:04.0/usb4/4-5/4-5:1.1/input/input6
[    2.963606] hid-generic 0003:099A:7202.0002: input,hiddev0,hidraw1: USB HID v1.11 Mouse [Wireless Keyboard/Mouse] on usb-0000:00:04.0-5/input1
[    3.228057] usb 3-5: new full-speed USB device number 2 using ohci-pci
[    3.361511] random: nonblocking pool is initialized
[    3.440062] usb 3-5: New USB device found, idVendor=04fc, idProduct=0561
[    3.440068] usb 3-5: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    3.440071] usb 3-5: Product: Generic Digital camera
[    3.440074] usb 3-5: Manufacturer: Sunplus Technology Co., Ltd.
[    3.619714] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)

[CENTER]_***[SIZE=4][COLOR=#B22222]1...&#8582;[/COLOR][COLOR=#b22222] This is where it apparently starts to hit the fan with errors [/COLOR][COLOR=#B22222]&#8582;[/COLOR][/SIZE]***_[/CENTER]

[COLOR=#b22222][    5.262843] init: plymouth-upstart-bridge main process (238) terminated with status 1
[    5.262879] init: plymouth-upstart-bridge main process ended, respawning
[    5.269888] init: plymouth-upstart-bridge main process (249) terminated with status 1
[    5.269925] init: plymouth-upstart-bridge main process ended, respawning
[    5.276603] init: plymouth-upstart-bridge main process (251) terminated with status 1
[    5.276641] init: plymouth-upstart-bridge main process ended, respawning
[    5.285314] init: plymouth-upstart-bridge main process (252) terminated with status 1
[    5.285339] init: plymouth-upstart-bridge main process ended, respawning
[    5.290726] init: plymouth-upstart-bridge main process (254) terminated with status 1
[    5.290746] init: plymouth-upstart-bridge main process ended, respawning
[    5.299768] init: plymouth-upstart-bridge main process (255) terminated with status 1
[    5.299803] init: plymouth-upstart-bridge main process ended, respawning
[    5.305520] init: plymouth-upstart-bridge main process (257) terminated with status 1
[    5.305552] init: plymouth-upstart-bridge main process ended, respawning
[    5.313601] init: plymouth-upstart-bridge main process (258) terminated with status 1
[    5.313634] init: plymouth-upstart-bridge main process ended, respawning
[    5.325261] init: plymouth-upstart-bridge main process (260) terminated with status 1
[    5.325301] init: plymouth-upstart-bridge main process ended, respawning
[    5.333197] init: plymouth-upstart-bridge main process (262) terminated with status 1
[    5.333222] init: plymouth-upstart-bridge main process ended, respawning
[    5.338353] init: plymouth-upstart-bridge main process (264) terminated with status 1
[    5.338383] init: plymouth-upstart-bridge respawning too fast, stopped[/COLOR]
[   16.095657] Adding 2029564k swap on /dev/sda5.  Priority:-1 extents:1 across:2029564k FS
[   16.528111] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.879717] systemd-udevd[366]: starting version 204
[   17.351824] lp: driver loaded but no devices found

[CENTER]_***[SIZE=4][COLOR=#B22222]2...&#8582; [/COLOR][COLOR=#b22222]This section here shows during boot-up, quite annoying... &#8582;[/COLOR][/SIZE]***_[/CENTER]

[COLOR=#b22222][   17.496372] media: module verification failed: signature and/or  required key missing - tainting kernel
[   17.496702] media: Linux media interface: v0.10
[   17.541370] videodev: module has bad taint, not creating trace events
[   17.541502] Linux video capture interface: v2.00
[   17.541506] WARNING: You are using an experimental version of the media stack.
[   17.541506]     As the driver is backported to an older kernel, it doesn't offer
[   17.541506]     enough quality for its usage in production.
[   17.541506]     Use it with care.
[   17.541506] Latest git patches (needed if you report a bug to linux-media@vger.kernel.org):
[   17.541506]     5ea878796f0a1d9649fe43a6a09df53d3915c0ef [media] V4L2: soc_camera: Add run-time dependencies to sh_mobile drivers
[   17.541506]     52e1473a58b6ea5d9b4ea3d4a0af8b59166aab42 [media] media: mx2_camera: Change Kconfig dependency
[   17.541506]     58be734f53089525224abc2e8ef75d1e9574a423 [media] media: mx1_camera: Remove driver
[   17.746968] WARNING: You are using an experimental version of the media stack.
[   17.746968]     As the driver is backported to an older kernel, it doesn't offer
[   17.746968]     enough quality for its usage in production.
[   17.746968]     Use it with care.
[   17.746968] Latest git patches (needed if you report a bug to linux-media@vger.kernel.org):
[   17.746968]     5ea878796f0a1d9649fe43a6a09df53d3915c0ef [media] V4L2: soc_camera: Add run-time dependencies to sh_mobile drivers
[   17.746968]     52e1473a58b6ea5d9b4ea3d4a0af8b59166aab42 [media] media: mx2_camera: Change Kconfig dependency
[   17.746968]     58be734f53089525224abc2e8ef75d1e9574a423 [media] media: mx1_camera: Remove driver[/COLOR]
[   17.977075] saa7130/34: v4l2 driver version 0, 2, 17 loaded
[   17.977463] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 18
[   17.977497] saa7133[0]: found at 0000:01:08.0, rev: 209, irq: 18, latency: 32, mmio: 0xfebff000
[   17.977504] saa7133[0]: subsystem: 1400:1044, board: AVerMedia AVerTVHD MCE A180 [card=75,insmod option]
[   17.977529] saa7133[0]: board init: gpio is 10400
[   18.128023] saa7133[0]: i2c eeprom 00: 00 14 44 10 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   18.128037] saa7133[0]: i2c eeprom 10: 00 ff 86 0f ff 20 00 00 00 00 00 00 00 00 00 00
[   18.128046] saa7133[0]: i2c eeprom 20: 01 40 01 02 02 ff 01 03 06 ff 01 11 00 00 00 00
[   18.128056] saa7133[0]: i2c eeprom 30: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   18.128065] saa7133[0]: i2c eeprom 40: ff 64 00 c2 14 16 ff ff 00 00 00 00 00 00 00 00
[   18.128074] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   18.128083] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   18.128093] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   18.128102] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   18.128111] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   18.128120] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   18.128130] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   18.128139] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   18.128148] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   18.128157] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   18.128167] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   18.128815] saa7133[0]: registered device video0 [v4l2]
[   18.128876] saa7133[0]: registered device vbi0
[CENTER]_***[COLOR=#b22222][SIZE=4]2a...&#8582; And again... &#8582;[/SIZE][/COLOR]***_[/CENTER]

[COLOR=#b22222][   18.295797] WARNING: You are using an experimental version of the media stack.
[   18.295797]     As the driver is backported to an older kernel, it doesn't offer
[   18.295797]     enough quality for its usage in production.
[   18.295797]     Use it with care.
[   18.295797] Latest git patches (needed if you report a bug to linux-media@vger.kernel.org):
[   18.295797]     5ea878796f0a1d9649fe43a6a09df53d3915c0ef [media] V4L2: soc_camera: Add run-time dependencies to sh_mobile drivers
[   18.295797]     52e1473a58b6ea5d9b4ea3d4a0af8b59166aab42 [media] media: mx2_camera: Change Kconfig dependency
[   18.295797]     58be734f53089525224abc2e8ef75d1e9574a423 [media] media: mx1_camera: Remove driver[/COLOR]
[   18.399299] dvb_init() allocating 1 frontend
[   18.524027] nxt200x: NXT2004 Detected
[   18.640697] DVB: registering new adapter (saa7133[0])
[   18.640709] saa7134 0000:01:08.0: DVB: registering adapter 0 frontend 0 (Nextwave NXT200X VSB/QAM frontend)...
[   18.801823] saa7134 ALSA driver for DMA sound loaded
[   18.801888] saa7133[0]/alsa: saa7133[0] at 0xfebff000 irq 18 registered as card -2
[   18.949866] ppdev: user-space parallel port driver
[   20.332030] nxt200x: nxt2004_init: Firmware upload complete
[   20.477331] i2c i2c-1: nForce2 SMBus adapter at 0x2d00
[   20.477431] i2c i2c-2: nForce2 SMBus adapter at 0x2e00
[   20.486308] wmi: Mapper loaded
[   20.916952] MCE: In-kernel MCE decoding enabled.
[   20.970421] device-mapper: multipath: version 1.6.0 loaded
[   20.974334] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   21.005251] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 21
[   21.005266] hda_intel: Disabling MSI
[   21.005298] hda-intel 0000:00:07.0: Disabling 64bit DMA
[   21.009319] hda-intel 0000:00:07.0: Enable delay in RIRB handling
[   21.209170] EDAC MC: Ver: 3.0.0
[   21.225354] AMD64 EDAC driver v3.4.0
[   21.232604] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 17
[   21.236827] cx88[0]: subsystem: 19b8:0462, board: DViCO FusionHDTV 5 Gold [card=31,insmod option], frontend(s): 1
[   21.367636] cx88[0]: i2c scan: found device @ 0x1c  [lgdt330x]
[   21.407355] cx88[0]: i2c scan: found device @ 0x86  [tda9887/cx22702]
[   21.416673] cx88[0]: i2c scan: found device @ 0xa0  [eeprom]
[   21.416860] cx88[0]: i2c scan: found device @ 0xa2  [???]
[   21.417046] cx88[0]: i2c scan: found device @ 0xa4  [???]
[   21.417233] cx88[0]: i2c scan: found device @ 0xa6  [???]
[   21.417421] cx88[0]: i2c scan: found device @ 0xa8  [???]
[   21.417607] cx88[0]: i2c scan: found device @ 0xaa  [???]
[   21.417794] cx88[0]: i2c scan: found device @ 0xac  [???]
[   21.417980] cx88[0]: i2c scan: found device @ 0xae  [???]
[   21.425014] cx88[0]: i2c scan: found device @ 0xc2  [tuner (analog/dvb)]
[   21.959692] tda9887 3-0043: creating new instance
[   21.959698] tda9887 3-0043: tda988[5/6/7] found
[   21.960529] tuner 3-0043: Tuner 74 found with type(s) Radio TV.
[   21.965771] tuner 3-0061: Tuner -1 found with type(s) Radio TV.
[   22.005189] tda9887 3-0061: creating new instance
[   22.005195] tda9887 3-0061: tda988[5/6/7] found
[   22.012619] cx88[0]/0: found at 0000:01:09.0, rev: 5, irq: 17, latency: 32, mmio: 0xfd000000
[   22.056039] SKU: Nid=0x1d sku_cfg=0x4007f603
[   22.056044] SKU: port_connectivity=0x1
[   22.056046] SKU: enable_pcbeep=0x0
[   22.056048] SKU: check_sum=0x00000007
[   22.056049] SKU: customization=0x000000f6
[   22.056051] SKU: external_amp=0x0
[   22.056052] SKU: platform_type=0x0
[   22.056053] SKU: swap=0x1
[   22.056054] SKU: override=0x1
[   22.068518] kvm: Nested Virtualization enabled
[   22.133004] autoconfig: line_outs=4 (0x14/0x15/0x16/0x17/0x0) type:line
[   22.133011]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   22.133013]    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[   22.133015]    mono: mono_out=0x0
[   22.133017]    dig-out=0x1e/0x0
[   22.133018]    inputs:
[   22.133021]      Front Mic=0x19
[   22.133023]      Rear Mic=0x18
[   22.133024]      Line=0x1a
[   22.133027] realtek: No valid SSID, checking pincfg 0x4007f603 for NID 0x1d
[   22.133030] realtek: Enabling init ASM_ID=0xf603 CODEC_ID=10ec0888
[   22.440339] cx88[0]/0: registered device video1 [v4l2]
[   22.440381] cx88[0]/0: registered device vbi1
[   22.440592] cx88[0]/2: cx2388x 8802 Driver Manager
[   22.440798] cx88[0]/2: found at 0000:01:09.2, rev: 5, irq: 17, latency: 32, mmio: 0xfc000000
[   22.527258] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   22.575331] cx88/2: cx2388x dvb driver version 0.0.9 loaded
[   22.575337] cx88/2: registering cx8802 driver, type: dvb access: shared
[   22.575341] cx88[0]/2: subsystem: 19b8:0462, board: DViCO FusionHDTV 5 Gold [card=31]
[   22.575344] cx88[0]/2: cx2388x based DVB/ATSC card
[   22.575346] cx8802_alloc_frontends() allocating 1 frontend(s)
[   23.038391] tuner-simple 3-0061: creating new instance
[   23.038399] tuner-simple 3-0061: type set to 64 (LG TDVS-H06xF)
[   23.038410] tda9887 3-0043: attaching existing instance
[   23.040244] DVB: registering new adapter (cx88[0])
[   23.040253] cx88-mpeg driver manager 0000:01:09.2: DVB: registering adapter 1 frontend 0 (LG Electronics LGDT3303 VSB/QAM Frontend)...
[   23.196088] gspca_main: v2.14.0 registered
[   23.286073] gspca_main: spca561-2.14.0 probing 04fc:0561

[CENTER][COLOR=#008000]_***[SIZE=4]3...&#8582;[/SIZE] I never could get this remote to work in Linux, only Win...[SIZE=4]&#8582;[/SIZE]***_[/COLOR][/CENTER]

[COLOR=#008000][   23.448040] Registered IR keymap rc-ati-x10
[   23.448261] input: X10 Wireless Technology Inc USB Receiver as /devices/pci0000:00/0000:00:04.0/usb4/4-1/4-1:1.0/rc/rc0/input8
[   23.448528] rc0: X10 Wireless Technology Inc USB Receiver as /devices/pci0000:00/0000:00:04.0/usb4/4-1/4-1:1.0/rc/rc0
[   23.448589] input: X10 Wireless Technology Inc USB Receiver mouse as /devices/pci0000:00/0000:00:04.0/usb4/4-1/4-1:1.0/input/input9
[   23.448899] usbcore: registered new interface driver ati_remote[/COLOR]
[   23.843162] input: spca561 as /devices/pci0000:00/0000:00:02.0/usb3/3-5/input/input10
[   23.843628] usbcore: registered new interface driver spca561

[CENTER][COLOR=#0000cd]**_*[SIZE=4]4...&#8582;[/SIZE] I tried to find information on this mess. May not be an error or warning, not sure [SIZE=4]&#8582;[/SIZE]*_**[/COLOR][/CENTER]

[COLOR=#000080][   23.927003] type=1400 audit(1407706821.204:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=567 comm="apparmor_parser"
[   23.927015] type=1400 audit(1407706821.204:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=567 comm="apparmor_parser"
[   23.927021] type=1400 audit(1407706821.204:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=567 comm="apparmor_parser"
[   23.927074] type=1400 audit(1407706821.204:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=470 comm="apparmor_parser"
[   23.927091] type=1400 audit(1407706821.204:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=470 comm="apparmor_parser"
[   23.927100] type=1400 audit(1407706821.204:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=470 comm="apparmor_parser"
[   23.927673] type=1400 audit(1407706821.204:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=567 comm="apparmor_parser"
[   23.927681] type=1400 audit(1407706821.204:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=567 comm="apparmor_parser"
[   23.927779] type=1400 audit(1407706821.204:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=470 comm="apparmor_parser"
[   23.927790] type=1400 audit(1407706821.204:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=470 comm="apparmor_parser"[/COLOR]
[   24.104064] nvidia: module license 'NVIDIA' taints kernel.
[   24.104071] Disabling lock debugging due to kernel taint
[   24.200189] input: HDA NVidia HDMI/DP,pcm=3 Phantom as /devices/pci0000:00/0000:00:07.0/sound/card0/input19
[   24.200342] input: HDA NVidia Front Headphone as /devices/pci0000:00/0000:00:07.0/sound/card0/input18
[   24.200471] input: HDA NVidia Line Out Side as /devices/pci0000:00/0000:00:07.0/sound/card0/input17
[   24.200586] input: HDA NVidia Line Out CLFE as /devices/pci0000:00/0000:00:07.0/sound/card0/input16
[   24.200704] input: HDA NVidia Line Out Surround as /devices/pci0000:00/0000:00:07.0/sound/card0/input15
[   24.200828] input: HDA NVidia Line Out Front as /devices/pci0000:00/0000:00:07.0/sound/card0/input14
[   24.200949] input: HDA NVidia Line as /devices/pci0000:00/0000:00:07.0/sound/card0/input13
[   24.201079] input: HDA NVidia Rear Mic as /devices/pci0000:00/0000:00:07.0/sound/card0/input12
[   24.201193] input: HDA NVidia Front Mic as /devices/pci0000:00/0000:00:07.0/sound/card0/input11
[   24.201939] EDAC amd64: DRAM ECC disabled.
[   24.201954] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   24.201954]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   24.201954]  (Note that use of the override may cause unknown side effects.)
[   24.203821] ACPI: PCI Interrupt Link [SGRU] enabled at IRQ 20
[   24.203844] vgaarb: device changed decodes: PCI:0000:00:12.0,olddecodes=io+mem,decodes=none:owns=none
[   24.204205] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  304.117  Tue Nov 26 21:25:36 PST 2013
[   25.475513] init: udev-fallback-graphics main process (842) terminated with status 1
[   25.825760] init: failsafe main process (789) killed by TERM signal
[   27.542875] init: avahi-cups-reload main process (1054) terminated with status 1
[   28.084614] Bluetooth: Core ver 2.17
[   28.084650] NET: Registered protocol family 31
[   28.084652] Bluetooth: HCI device and connection manager initialized
[   28.084666] Bluetooth: HCI socket layer initialized
[   28.084670] Bluetooth: L2CAP socket layer initialized
[   28.084676] Bluetooth: SCO socket layer initialized
[   28.294408] Bluetooth: RFCOMM TTY layer initialized
[   28.294433] Bluetooth: RFCOMM socket layer initialized
[   28.294455] Bluetooth: RFCOMM ver 1.11
[   28.683758] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   28.683764] Bluetooth: BNEP filters: protocol multicast
[   28.683778] Bluetooth: BNEP socket layer initialized
[   30.142460] audit_printk_skb: 21 callbacks suppressed

[CENTER][COLOR=#0000ff]_***[SIZE=4]4a...&#8582; And again... &#8582;[/SIZE]***_[/COLOR][/CENTER]

[COLOR=#000080][   30.142466] type=1400 audit(1407706827.420:19): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=1140 comm="apparmor_parser"
[   30.142477] type=1400 audit(1407706827.420:20): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1140 comm="apparmor_parser"
[   30.142484] type=1400 audit(1407706827.420:21): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1140 comm="apparmor_parser"
[   30.143139] type=1400 audit(1407706827.420:22): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1140 comm="apparmor_parser"
[   30.143145] type=1400 audit(1407706827.420:23): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1140 comm="apparmor_parser"
[   30.143488] type=1400 audit(1407706827.420:24): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1140 comm="apparmor_parser"
[   30.551074] type=1400 audit(1407706827.828:25): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=1139 comm="apparmor_parser"
[   30.551089] type=1400 audit(1407706827.828:26): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=1139 comm="apparmor_parser"
[   30.551516] type=1400 audit(1407706827.828:27): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="chromium" pid=1139 comm="apparmor_parser"
[   30.648186] forcedeth 0000:00:0a.0: irq 47 for MSI/MSI-X
[   30.648249] forcedeth 0000:00:0a.0 eth0: MSI enabled
[   30.736507] type=1400 audit(1407706828.016:28): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/telepathy/mission-control-5" pid=1143 comm="apparmor_parser"[/COLOR]
[   33.373234] vboxdrv: Found 2 processor cores.
[   33.373618] vboxdrv: fAsync=1 offMin=0x8ff7 offMax=0x8ff7
[   33.373799] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.
[   33.373802] vboxdrv: Successfully loaded version 4.3.10_Ubuntu (interface 0x001a0007).
[   33.530450] init: lxdm main process (1215) killed by TERM signal
[   34.145704] vboxpci: IOMMU not found (not registered)
[   35.551453] init: plymouth main process (267) killed by SEGV signal
[   41.664539] Non-volatile memory driver v1.3
[   57.936057] usb 2-4: reset high-speed USB device number 3 using ehci-pci
[   58.084137] sd 2:0:0:0: Device offlined - not ready after error recovery
[   58.084159] sd 2:0:0:0: rejecting I/O to offline device
[   58.084163] sd 2:0:0:0: killing request
[   58.084168] usb 2-4: USB disconnect, device number 3
[   58.652058] usb 2-4: new high-speed USB device number 5 using ehci-pci
[   58.799361] usb 2-4: New USB device found, idVendor=0aec, idProduct=3260
[   58.799367] usb 2-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[   58.799370] usb 2-4: Product: USB Storage Device
[   58.799373] usb 2-4: Manufacturer: GENERIC
[   58.799376] usb 2-4: SerialNumber: 1234567890ABCDEND
[   58.799875] usb-storage 2-4:1.0: USB Mass Storage device detected
[   58.800224] scsi7 : usb-storage 2-4:1.0
[   59.804988] scsi 7:0:0:0: Direct-Access     GENERIC  USB Storage-CFC  I20B PQ: 0 ANSI: 0 CCS
[   59.809101] scsi 7:0:0:1: Direct-Access     GENERIC  USB Storage-SDC  I20B PQ: 0 ANSI: 0 CCS
[   59.813087] scsi 7:0:0:2: Direct-Access     GENERIC  USB Storage-SMC  I20B PQ: 0 ANSI: 0 CCS
[   59.817106] scsi 7:0:0:3: Direct-Access     GENERIC  USB Storage-MSC  I20B PQ: 0 ANSI: 0 CCS
[   59.819202] sd 7:0:0:0: [sdb] 7928928 512-byte logical blocks: (4.05 GB/3.78 GiB)
[   59.820110] sd 7:0:0:0: Attached scsi generic sg2 type 0
[   59.820480] sd 7:0:0:1: Attached scsi generic sg3 type 0
[   59.820810] sd 7:0:0:0: [sdb] Write Protect is off
[   59.820820] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[   59.821094] sd 7:0:0:2: Attached scsi generic sg4 type 0
[   59.823858] sd 7:0:0:3: Attached scsi generic sg5 type 0
[   59.826224] sd 7:0:0:0: [sdb] No Caching mode page found
[   59.826232] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[   59.831210] sd 7:0:0:1: [sdc] Attached SCSI removable disk
[   59.831953] sd 7:0:0:2: [sdd] Attached SCSI removable disk
[   59.833332] sd 7:0:0:3: [sde] Attached SCSI removable disk
[   59.836379] sd 7:0:0:0: [sdb] No Caching mode page found
[   59.836386] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[   59.838528]  sdb: sdb1
[   59.843646] sd 7:0:0:0: [sdb] No Caching mode page found
[   59.843655] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[   59.843661] sd 7:0:0:0: [sdb] Attached SCSI removable disk
[   60.235765] init: plymouth-stop pre-start process (2735) terminated with status 1
[CENTER]***[FONT=book antiqua][COLOR=#daa520][SIZE=5]FINI[/SIZE][/COLOR][/FONT]***[/CENTER]

```

---

### Post by nerdtron on 2014-08-10
Did you do something on your network configuration? Static addressing? Editing the /etc/network/interfaces file?

Anyway, I think those errors are nothing to be scared about. If you don't have any issues on the normal operation of your computer, then it's fine.

---

### Post by geemac2 on 2014-08-11
Hi Nerdtron,

Thanks for the quick response to the above mess.

I am not too worried about the errors, but the ugly mess scrolling on my home theatre TV screen after the gnome menu, it just looks sloppy.
The only thing I should be seeing is the gnome menu at boot-up just incase I have an issue and can recover from it.

If there is a way to keep those errors from scrolling on my TV at boot-up, that would be great. There shouldn't be any errors at all anyway, but I can live with them since things are working. The only a minor issue is the remote not working.

There is an odd issue with the memory slowly rising to roughly 1.7 gig after just idling that I can't seem to put a finger on.  This is not good since I have only 2gig installed.  This is what had me looking in the Dmesg in the first place.  I thought I would look there after watching the task manager memory usage.  I thought it could be something with one of  the issues highlighted in the Dmesg.   It looks as if it is a memory leak, but it is not showing where it is coming from.


This is from the **/etc/network/interfaces** file.  I haven't touched this file.

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

Thanks again
*GEEMac*

---

### Post by geemac2 on 2014-08-13
[COLOR=#b22222][SIZE=3]***In a nutshell...***[/SIZE][/COLOR]

I want to stop Dmesg from scrolling on screen after the Grub menu and before Plymouth (animated dots with Ubuntu text)

I have nothing here to take a video of this to show how ugly this looks on a nicely put together Home Theatre System.

Quiet and Quiet Splash in grub does not stop the ugly Dmesg screen. I even tried another suggestion of redirecting the text to TTY 12.
The above Dmesg is like watching the Bios/DOS boot in windows, but dragged out for a longer since it feels like it did not get it's messages across. I never had this in 12.04.
And yes, I'm picky... 

Thanks in advance
*GEEMac*

---

### Post by geemac2 on 2014-09-26
Sort of a Bump...

Thanks Nerdtron...

Still having these error messages scrolling up my screen at boot up.
Please scroll through my posted and color coded Dmesg above.
The color coded sections should explain what is going on here.

Anyone else??

---

### Post by tgalati4 on 2014-09-26
You shouldn't have to boot that often.  If you put your system to sleep and wake it with your phone (using Wake-on-Lan) then it powers up in 3 to 8 seconds with no messages.

If you have to boot, then try to, carefully, remove plymouth or modify its scripts to send errors to > /dev/nul.

For the video driver errors, either use the standard drivers or compile the latest drivers on your system with an appropriate build environment.  The drivers that you are using appear to be backported and may cause kernel panics because they don't have all the hooks needed to adequately control the drivers and the errors they output.

You can remove *apparmor*.

Did X10 ever work?

---

### Post by geemac2 on 2014-09-26
Thanks for the quick response Tgalit4

I live in Florida, also known as the Lightning Capital of the US.  I have to shut this HTPC down when not in use since we have so many power outages.   A UPS is one thing I don't have on this system yet.  I need a pretty hefty one for all this home theatre stuff.
As for Plymouth, I'll look into that.   I am also now getting the Start/Stop [OK] messages streaming down the screen.   That just started not to long ago after a update.
As for the soc_camera,  mx1_camera and mx2_camera errors,  those errors started after I installed V4L2 so I can run a TV tuner.  These items are not even in the PC.

The X10 issue is a RF wireless remote...  That is something that has been driving me crazy for some time now.
**See Post:** [http://ubuntuforums.org/showthread.php?t=2184364](http://ubuntuforums.org/showthread.php?t=2184364)


:) Re Latin.
Yes, Every thing can be repaired if you have a big enough hammer.   I do believe in that minus the hammer. 
And I always thought the saying was Patientia sit virgo

---

### Post by tgalati4 on 2014-09-26
My Latin was from high school, many, many years ago, so I used google translate:  Patience is key as opposed to Patience is a virtue.

My only remote experience is with a Microsoft Multimedia Center remote (which looks similar), and I was able to get most of it to work with *lirc* and related libraries.  Have you tried setting up with *lirc*?  This is really old documentation, but most of the steps are applicable:  [https://help.ubuntu.com/community/InstallLirc/Hardy](https://help.ubuntu.com/community/InstallLirc/Hardy)  Your hardware is recognized as an input device.  You just need to assign the buttons to different functions with a configuration file.

With your remote plugged in and with fresh batteries, what is the output of:

```
xinput --list
```

Use *xev* to see the keycodes as you press the remote buttons.  Once you have the keycodes, you can assign them to different functions.

---

### Post by geemac2 on 2014-09-27
Thanks again for the help.

Here is the results from 

```

**xinput --list**

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Wireless Keyboard/Mouse                     id=9    [slave  pointer  (2)]
&#9116;   &#8627; X10 Wireless Technology Inc USB Receiver mouse    id=10    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Wireless Keyboard/Mouse                     id=8    [slave  keyboard (3)]
    &#8627; X10 Wireless Technology Inc USB Receiver    id=11    [slave  keyboard (3)]

```


```

**xev**

***No keys pressed at this time.***

Outer window is 0x3800001, inner window is 0x3800002

PropertyNotify event, serial 8, synthetic NO, window 0x3800001,
    atom 0x27 (WM_NAME), time 679877, state PropertyNewValue

PropertyNotify event, serial 9, synthetic NO, window 0x3800001,
    atom 0x22 (WM_COMMAND), time 679877, state PropertyNewValue

PropertyNotify event, serial 10, synthetic NO, window 0x3800001,
    atom 0x28 (WM_NORMAL_HINTS), time 679877, state PropertyNewValue

CreateNotify event, serial 11, synthetic NO, window 0x3800001,
    parent 0x3800001, window 0x3800002, (10,10), width 50, height 50
border_width 4, override NO

PropertyNotify event, serial 14, synthetic NO, window 0x3800001,
    atom 0x12b (WM_PROTOCOLS), time 679878, state PropertyNewValue

MapNotify event, serial 15, synthetic NO, window 0x3800001,
    event 0x3800001, window 0x3800002, override NO

ConfigureNotify event, serial 18, synthetic NO, window 0x3800001,
    event 0x3800001, window 0x3800001, (0,0), width 178, height 178,
    border_width 0, above 0x24002fd, override NO

PropertyNotify event, serial 18, synthetic NO, window 0x3800001,
    atom 0x1c3 (_NET_WM_ALLOWED_ACTIONS), time 679880, state PropertyNewValue

PropertyNotify event, serial 18, synthetic NO, window 0x3800001,
    atom 0x1c3 (_NET_WM_ALLOWED_ACTIONS), time 679880, state PropertyNewValue

ReparentNotify event, serial 18, synthetic NO, window 0x3800001,
    event 0x3800001, window 0x3800001, parent 0x120040f,
    (0,0), override NO

PropertyNotify event, serial 18, synthetic NO, window 0x3800001,
    atom 0x133 (_NET_WM_DESKTOP), time 679883, state PropertyNewValue

PropertyNotify event, serial 18, synthetic NO, window 0x3800001,
    atom 0x133 (_NET_WM_DESKTOP), time 679883, state PropertyNewValue

PropertyNotify event, serial 18, synthetic NO, window 0x3800001,
    atom 0x130 (_NET_FRAME_EXTENTS), time 679883, state PropertyNewValue

ConfigureNotify event, serial 18, synthetic NO, window 0x3800001,
    event 0x3800001, window 0x3800001, (1,34), width 178, height 178,
    border_width 0, above 0x0, override NO

PropertyNotify event, serial 18, synthetic NO, window 0x3800001,
    atom 0x1a6 (WM_STATE), time 679883, state PropertyNewValue

PropertyNotify event, serial 18, synthetic NO, window 0x3800001,
    atom 0x139 (_NET_WM_STATE), time 679884, state PropertyNewValue

ConfigureNotify event, serial 30, synthetic YES, window 0x3800001,
    event 0x3800001, window 0x3800001, (-1,525), width 178, height 178,
    border_width 2, above 0x0, override NO

MapNotify event, serial 30, synthetic NO, window 0x3800001,
    event 0x3800001, window 0x3800001, override NO

VisibilityNotify event, serial 30, synthetic NO, window 0x3800001,
    state VisibilityUnobscured

Expose event, serial 30, synthetic NO, window 0x3800001,
    (0,0), width 178, height 10, count 3

Expose event, serial 30, synthetic NO, window 0x3800001,
    (0,10), width 10, height 58, count 2

Expose event, serial 30, synthetic NO, window 0x3800001,
    (68,10), width 110, height 58, count 1

Expose event, serial 30, synthetic NO, window 0x3800001,
    (0,68), width 178, height 110, count 0

PropertyNotify event, serial 30, synthetic NO, window 0x3800001,
    atom 0x139 (_NET_WM_STATE), time 679899, state PropertyNewValue

PropertyNotify event, serial 33, synthetic NO, window 0x3800001,
    atom 0x1be (_NET_WM_ICON_GEOMETRY), time 679945, state PropertyNewValue

PropertyNotify event, serial 34, synthetic NO, window 0x3800001,
    atom 0x1be (_NET_WM_ICON_GEOMETRY), time 679986, state PropertyNewValue

VisibilityNotify event, serial 34, synthetic NO, window 0x3800001,
    state VisibilityFullyObscured
_______________________________________________________________________

***#1 key pressed***

I fill the rest after the storm here.







```

---

### Post by tgalati4 on 2014-09-28
You don't need to post the *xev* output.  Just make sure the mouse cursor is inside the *xev* window.  Press each key on the remote and look for a keycode and an event.  You should get two events for each:  A Press Event and a Release Event.  Take a notepad and write down the keycode values.

Study the *xmodmap* utility for assigning keycodes to functions.  There is probably a generic remote control layout that you can use as a starter file.  There may be a better way to do it.  I would search on the XBMC forums since they have an interest in remote control functions.

---

### Post by geemac2 on 2014-09-28
OK...  I see what is making the changes in the terminal it is the remote mouse and keyboard not the X10 Wireless Technology Inc USB Receiver as in the list.
Apparently the X10 receiver (ATI Remote Wonder) is showing up but there is no input from the remote control.
There was some odd tweaking of the scripts or drivers that had to be done to make the remote work and I guess I did not follow it properly.
The reason I was trying to get this remote working is that it is brand new.  I had it sitting in a box in the closet for years.  It works with Win 7, it's just Linux is being the bugger to get it working and it is listed as a remote that will work with Linux.
Just my luck...  Only my Linux install it does not work in.

*By the way*, as for the messages scrolling after the grub menu, I turned off Plymouth and it was still showing the dmesg referring to the those drivers and now along with the items starting and stopping with the [OK].  I have searched for weeks and I still can't find a way to turn that junk off.
It is mostly aesthetics here, it just looks bad when your showing someone your Home Theater that is all nice and shiny and then all those nonsense errors scroll on by that have nothing to do with the setup.

Thanks

---

### Post by tgalati4 on 2014-09-28
Try following these instructions and pretend that it is a Microsoft Media Center remote:  [http://ubuntuforums.org/showthread.php?t=1536520](http://ubuntuforums.org/showthread.php?t=1536520)

Plymouth is the kernel mode setting (kms) framework that allows the video mode to change and display fancy graphics during boot.  Before plymouth, it was dark and cold and text-based during boot--with lots of annoying flashes.  Now it is shiny and mac-like.  Obviously, because of the hardware that you have, the kernel hooks used for mode-setting are having an issue and thus you get messages displayed.  Turning off plymouth does not turn off the kernel checking and choking on the hardware.

I would get an UPS and just put the machine to sleep.  The boot process was not designed to impress your friends--unless they are developers, then they may be impressed--but definitely not friendly.

---

### Post by geemac2 on 2014-10-02
Thanks again,

Guess I will have to deal with the scrolling garbage on the screen until I can afford the proper UPS for everything here.
If I am going to get one it will be for the whole home theatre package not just the computer.  I want a **[[COLOR=#008000]*line interactive UPS*[/COLOR]]("http://www.apcmedia.com/salestools/SADE-5TNM3Y/SADE-5TNM3Y_R7_EN.pdf")**  ([COLOR=#006400]**sometimes called a Smart UPS**[/COLOR]) with a *pure sign wave* filtered output when it switches over.  No spike and no noise at switchover and a clean AC out when it is running the system when needed.  No noise on a AC line is best for sensitive electronics.  I'm looking at roughly $300 US or better for the UPS.
I could get into a :popcorn: moment here with all the techie info on UPS systems concerning a HTPC system.  I did type it out, but I'll save it for another day in a hardware forum when it comes to UPS systems or if someone has a cup of coffee and time to read. The green text is linked.
I am a former Broadcast Engineer of 30+ years and I can get pretty techie when it comes to hardware.  As for programming I am usually lost most of the time.:-s


Thanks again for your input
TC
GEE

---

### Post by tgalati4 on 2014-10-03
Yes, better UPS's will give you cleaner power, but the purpose of the UPS is to keep your system protected from voltage spikes and not to watch TV when the power goes out.  So, although you can spend a lot on an UPS, you can also get an old, metal-case APC SmartUPS, and replace the batteries ($15 for the used UPS, $150 for the batteries) and have decent protection with telemetry, autoshutdown, and email/text message alerts.  Check craigslist for decent, used, enterprise-class UPS's.

The alternative is to design a delay circuit to keep the TV turned off until the system is fully booted.  You could have a script to change TV sources to a USB thumbdrive (family pictures) and then switch to the HTPC source after a few minutes.  If your HTPC is asleep and you wake it, most TV's will automatically switch to the acive video source.  No text messages, just whatever background screen or video player you set up.

---

### Post by kelt65 on 2015-04-05
I would not let it get to you. The last thing you want is to *not* see those messages when something's wrong and the system doesn't boot correctly. If you really like, adding "-quiet" in the grub boot command that launches the kernel will get rid of them in place of a nice blank screen for you.
The relevant configuation file is ```
/etc/default/grub
``` and the relevant setting is:

```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

```

then run:
```

sudo update-grub2

```

Although these have been the default settings in Ubuntu since forever. Are you using some variant that has disabled this?

---

