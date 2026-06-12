---
title: "Very slow boot"
date: 2014-04-19
forum: General Help
---

### Post by Jonathan_Traill on 2014-04-19
About a month ago I switched from Ubuntu 12.04 to Lubuntu 12.04, then upgradeed to Lubuntu 13.10.  This was all done via upgrades and downgrades, not installs from disc.  Somewhere along the line, my very old but swift emachines E625 started booting very slowly - over a minute.  I hoped a fresh install of Lubuntu 14.04 would help, but it didn't.  Still getting the same delay.  Immediately after the bios screen, everything goes black.  The disc light stays resolutely unlit.  then after about 30 seconds, it flickers.  Then more nothing.  Then finally Plymouth!  And then everything is okay.

So I ran dmesg to find out what was going on.  And even an idiot such as I can see the massive time-out after three seconds, and almost nothing happening until almost a full minute has elapsed.

So this confirms I ma not imagining it.  But what is causing it?

> [    3.071384] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.074568] scsi 2:0:0:0: CD-ROM            HL-DT-ST DVDRAM GT20N     CP02 PQ: 0 ANSI: 5
[    3.079514] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.079518] cdrom: Uniform CD-ROM driver Revision: 3.20
[    3.079947] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    3.080130] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    3.085656]  sda: sda1 sda2 < sda5 >
[    3.086039] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.285587] random: lvm urandom read with 42 bits of entropy available
[    3.327504] bio: create slab <bio-1> at 1
[    3.638912] EXT4-fs (dm-0): mounted filesystem with ordered data mode. Opts: (null)
[   17.432038] usb 1-10: device descriptor read/64, error -110
[   32.648035] usb 1-10: device descriptor read/64, error -110
[   32.864039] usb 1-10: new high-speed USB device number 3 using ehci-pci
[   47.976038] usb 1-10: device descriptor read/64, error -110
[   61.917187] random: nonblocking pool is initialized
[   63.192034] usb 1-10: device descriptor read/64, error -110
[   63.408035] usb 1-10: new high-speed USB device number 4 using ehci-pci
[   68.428247] usb 1-10: device descriptor read/8, error -110
[   73.528841] Adding 3932156k swap on /dev/mapper/lubuntu--vg-swap_1.  Priority:-1 extents:1 across:3932156k FS
[   73.548297] usb 1-10: device descriptor read/8, error -110
[   73.618261] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready

---

### Post by Jonathan_Traill on 2014-04-19
Here's the full log for the first 75 (!!!!) seconds:

```
[    0.000000] Initializing cgroup subsys cpuset[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.13.0-24-generic (buildd@roseapple) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #46-Ubuntu SMP Thu Apr 10 19:08:14 UTC 2014 (Ubuntu 3.13.0-24.46-generic 3.13.9)
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
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009dbff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009dc00-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000d0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000bfe7ffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bfe80000-0x00000000bfe90fff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000bfe91000-0x00000000bfe92fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bfe93000-0x00000000cfffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec0ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fff00000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000012fffffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.4 present.
[    0.000000] DMI: eMachines        eMachines E625  /HM50-YK    , BIOS V1.10     04/21/2009
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0x130000 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FF80000000 write-back
[    0.000000]   1 base 0080000000 mask FFC0000000 write-back
[    0.000000]   2 base 00C0000000 mask FFF0000000 write-back
[    0.000000]   3 base 0100000000 mask FFE0000000 write-back
[    0.000000]   4 base 0120000000 mask FFF0000000 write-back
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 0000000130000000 aka 4864M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820: update [mem 0xd0000000-0xffffffff] usable ==> reserved
[    0.000000] found SMP MP-table at [mem 0x000f7bc0-0x000f7bcf] mapped at [c00f7bc0]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] initial memory mapped: [mem 0x00000000-0x01ffffff]
[    0.000000] Base memory trampoline at [c0099000] 99000 size 16384
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
[    0.000000] BRK [0x01b88000, 0x01b88fff] PGTABLE
[    0.000000] RAMDISK: [mem 0x35af2000-0x36d70fff]
[    0.000000] ACPI: RSDP 000f7b00 000024 (v02 ACRSYS)
[    0.000000] ACPI: XSDT bfe880f1 000054 (v01 ACRSYS ACRPRDCT 06040000  LTP 00000000)
[    0.000000] ACPI: FACP bfe90b95 0000F4 (v03 ATI    Herring  06040000 ATI  000F4240)
[    0.000000] ACPI: DSDT bfe88145 008A50 (v01 ACRSYS ACRPRDCT 06040000 MSFT 03000000)
[    0.000000] ACPI: FACS bfe92fc0 000040
[    0.000000] ACPI: SLIC bfe90cfd 000176 (v01 ACRSYS ACRPRDCT 06040000 LOHR 00000000)
[    0.000000] ACPI: SSDT bfe90e73 0000D3 (v01 PTLTD  POWERNOW 06040000  LTP 00000001)
[    0.000000] ACPI: APIC bfe90f46 000046 (v01 PTLTD  ? APIC   06040000  LTP 00000000)
[    0.000000] ACPI: MCFG bfe90f8c 00003C (v01 PTLTD    MCFG   06040000  LTP 00000000)
[    0.000000] ACPI: HPET bfe90fc8 000038 (v01 PTLTD  HPETTBL  06040000  LTP 00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 3972MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] BRK [0x01b89000, 0x01b89fff] PGTABLE
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   Normal   [mem 0x01000000-0x37bfdfff]
[    0.000000]   HighMem  [mem 0x37bfe000-0x2fffffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009cfff]
[    0.000000]   node   0: [mem 0x00100000-0xbfe7ffff]
[    0.000000]   node   0: [mem 0x00000000-0x2fffffff]
[    0.000000] On node 0 totalpages: 982556
[    0.000000] free_area_init_node: node 0, pgdat c1990a80, node_mem_map f34f2020
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3996 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 224254 pages, LIFO batch:31
[    0.000000]   HighMem zone: 7945 pages used for memmap
[    0.000000]   HighMem zone: 754306 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x43538301 base: 0xfed00000
[    0.000000] smpboot: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: [mem 0x0009d000-0x0009dfff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000cffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000d0000-0x000fffff]
[    0.000000] e820: [mem 0xd0000000-0xdfffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @f7bde000 s36096 r0 d21248 u57344
[    0.000000] pcpu-alloc: s36096 r0 d21248 u57344 alloc=14*4096
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 980772
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-3.13.0-24-generic root=/dev/mapper/lubuntu--vg-root ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 9961464 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:00130000)
[    0.000000] Memory: 3849828K/3930224K available (6507K kernel code, 641K rwdata, 2752K rodata, 872K init, 924K bss, 80396K reserved, 3017224K highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff14000 - 0xfffff000   ( 940 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc19ae000 - 0xc1a88000   ( 872 kB)
[    0.000000]       .data : 0xc165b0b2 - 0xc19ad4c0   (3401 kB)
[    0.000000]       .text : 0xc1000000 - 0xc165b0b2   (6508 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=8 to nr_cpu_ids=1.
[    0.000000] NR_IRQS:2304 nr_irqs:256 16
[    0.000000] CPU 0 irqstacks, hard=f3008000 soft=f300a000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 1596.117 MHz processor
[    0.004002] Calibrating delay loop (skipped), value calculated using timer frequency.. 3192.23 BogoMIPS (lpj=6384468)
[    0.004008] pid_max: default: 32768 minimum: 301
[    0.004054] Security Framework initialized
[    0.004076] AppArmor: AppArmor initialized
[    0.004078] Yama: becoming mindful.
[    0.004160] Mount-cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.004164] Mountpoint-cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.004500] Initializing cgroup subsys memory
[    0.004509] Initializing cgroup subsys devices
[    0.004513] Initializing cgroup subsys freezer
[    0.004517] Initializing cgroup subsys blkio
[    0.004520] Initializing cgroup subsys perf_event
[    0.004524] Initializing cgroup subsys hugetlb
[    0.004563] mce: CPU supports 5 MCE banks
[    0.004575] LVT offset 0 assigned for vector 0xf9
[    0.004580] process: using AMD E400 aware idle routine
[    0.004591] Last level iTLB entries: 4KB 512, 2MB 8, 4MB 4
[    0.004591] Last level dTLB entries: 4KB 512, 2MB 8, 4MB 4
[    0.004591] tlb_flushall_shift: 4
[    0.021252] Freeing SMP alternatives memory: 32K (c1a88000 - c1a90000)
[    0.022811] ACPI: Core revision 20131115
[    0.031054] ACPI: All ACPI Tables successfully acquired
[    0.032015] ftrace: allocating 27695 entries in 55 pages
[    0.044124] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.044506] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.048000] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[    0.048000] ...trying to set up timer (IRQ0) through the 8259A ...
[    0.048000] ..... (found apic 0 pin 0) ...
[    0.089833] ....... works.
[    0.089835] smpboot: CPU0: AMD Athlon(tm) Processor TF-20 (fam: 0f, model: 7c, stepping: 02)
[    0.092000] Performance Events: AMD PMU driver.
[    0.092000] ... version:                0
[    0.092000] ... bit width:              48
[    0.092000] ... generic registers:      4
[    0.092000] ... value mask:             0000ffffffffffff
[    0.092000] ... max period:             00007fffffffffff
[    0.092000] ... fixed-purpose events:   0
[    0.092000] ... event mask:             000000000000000f
[    0.093170] x86: Booted up 1 node, 1 CPUs
[    0.093175] smpboot: Total of 1 processors activated (3192.23 BogoMIPS)
[    0.093565] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.093761] devtmpfs: initialized
[    0.094036] EVM: security.selinux
[    0.094039] EVM: security.SMACK64
[    0.094041] EVM: security.ima
[    0.094043] EVM: security.capability
[    0.094145] PM: Registering ACPI NVS region [mem 0xbfe91000-0xbfe92fff] (8192 bytes)
[    0.096089] pinctrl core: initialized pinctrl subsystem
[    0.096197] regulator-dummy: no parameters
[    0.096239] RTC time:  6:31:15, date: 04/19/14
[    0.096299] NET: Registered protocol family 16
[    0.096516] EISA bus registered
[    0.096520] cpuidle: using governor ladder
[    0.096522] cpuidle: using governor menu
[    0.096530] node 0 link 0: io port [1000, fffff]
[    0.096534] TOM: 00000000d0000000 aka 3328M
[    0.096538] node 0 link 0: mmio [f0100000, ffffffff]
[    0.096543] node 0 link 0: mmio [e0000000, dfffffff]
[    0.096546] node 0 link 0: mmio [a0000, bffff]
[    0.096550] node 0 link 0: mmio [f0000000, f00fffff]
[    0.096553] node 0 link 0: mmio [e0000000, efffffff]
[    0.096557] node 0 link 0: mmio [d0000000, dfffffff]
[    0.096560] TOM2: 0000000130000000 aka 4864M
[    0.096564] bus: [bus 00-ff] on node 0 link 0
[    0.096567] bus: 00 [io  0x0000-0xffff]
[    0.096570] bus: 00 [mem 0xd0000000-0xffffffff]
[    0.096572] bus: 00 [mem 0x000a0000-0x000bffff]
[    0.096575] bus: 00 [mem 0x130000000-0xfcffffffff]
[    0.096658] ACPI: bus type PCI registered
[    0.096661] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.096762] PCI: MMCONFIG for domain 0000 [bus 00-09] at [mem 0xe0000000-0xe09fffff] (base 0xe0000000)
[    0.096766] PCI: MMCONFIG at [mem 0xe0000000-0xe09fffff] reserved in E820
[    0.096768] PCI: Using MMCONFIG for extended config space
[    0.096771] PCI: Using configuration type 1 for base access
[    0.098625] bio: create slab <bio-0> at 0
[    0.098850] ACPI: Added _OSI(Module Device)
[    0.098853] ACPI: Added _OSI(Processor Device)
[    0.098855] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.098858] ACPI: Added _OSI(Processor Aggregator Device)
[    0.104672] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.108518] ACPI: Interpreter enabled
[    0.108533] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20131115/hwxface-580)
[    0.108540] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)
[    0.108560] ACPI: (supports S0 S3 S4 S5)
[    0.108563] ACPI: Using IOAPIC for interrupt routing
[    0.108656] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.108826] ACPI: No dock devices found.
[    0.221710] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.221720] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.221898] acpi PNP0A08:00: _OSC: platform does not support [PCIeHotplug PME AER PCIeCapability]
[    0.221903] acpi PNP0A08:00: _OSC: not requesting control; platform does not support [PCIeCapability]
[    0.221908] acpi PNP0A08:00: _OSC: OS requested [PCIeHotplug PME AER PCIeCapability]
[    0.221911] acpi PNP0A08:00: _OSC: platform willing to grant []
[    0.221915] acpi PNP0A08:00: _OSC failed (AE_SUPPORT); disabling ASPM
[    0.223917] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-09] only partially covers this bridge
[    0.224182] PCI host bridge to bus 0000:00
[    0.224187] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.224191] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.224195] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d1fff]
[    0.224199] pci_bus 0000:00: root bus resource [mem 0x000d2000-0x000d3fff]
[    0.224203] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d5fff]
[    0.224206] pci_bus 0000:00: root bus resource [mem 0x000d6000-0x000d7fff]
[    0.224210] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000d9fff]
[    0.224214] pci_bus 0000:00: root bus resource [mem 0x000da000-0x000dbfff]
[    0.224218] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000ddfff]
[    0.224222] pci_bus 0000:00: root bus resource [mem 0x000de000-0x000dffff]
[    0.224226] pci_bus 0000:00: root bus resource [mem 0xd0000000-0xdfffffff]
[    0.224229] pci_bus 0000:00: root bus resource [mem 0xf0000000-0xffffffff]
[    0.224233] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.224237] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.224249] pci 0000:00:00.0: [1002:7910] type 00 class 0x060000
[    0.224363] pci 0000:00:01.0: [1002:7912] type 01 class 0x060400
[    0.224489] pci 0000:00:06.0: [1002:7916] type 01 class 0x060400
[    0.224530] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.224630] pci 0000:00:07.0: [1002:7917] type 01 class 0x060400
[    0.224670] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
[    0.224729] pci 0000:00:07.0: System wakeup disabled by ACPI
[    0.224796] pci 0000:00:12.0: [1002:4380] type 00 class 0x010601
[    0.224818] pci 0000:00:12.0: reg 0x10: [io  0x8440-0x8447]
[    0.224832] pci 0000:00:12.0: reg 0x14: [io  0x8434-0x8437]
[    0.224845] pci 0000:00:12.0: reg 0x18: [io  0x8438-0x843f]
[    0.224858] pci 0000:00:12.0: reg 0x1c: [io  0x8430-0x8433]
[    0.224870] pci 0000:00:12.0: reg 0x20: [io  0x8400-0x840f]
[    0.224884] pci 0000:00:12.0: reg 0x24: [mem 0xf0607000-0xf06073ff]
[    0.225021] pci 0000:00:13.0: [1002:4387] type 00 class 0x0c0310
[    0.225038] pci 0000:00:13.0: reg 0x10: [mem 0xf0404000-0xf0404fff]
[    0.225156] pci 0000:00:13.0: System wakeup disabled by ACPI
[    0.225208] pci 0000:00:13.1: [1002:4388] type 00 class 0x0c0310
[    0.225226] pci 0000:00:13.1: reg 0x10: [mem 0xf0405000-0xf0405fff]
[    0.225342] pci 0000:00:13.1: System wakeup disabled by ACPI
[    0.225394] pci 0000:00:13.4: [1002:438b] type 00 class 0x0c0310
[    0.225412] pci 0000:00:13.4: reg 0x10: [mem 0xf0406000-0xf0406fff]
[    0.225574] pci 0000:00:13.5: [1002:4386] type 00 class 0x0c0320
[    0.225598] pci 0000:00:13.5: reg 0x10: [mem 0xf0607400-0xf06074ff]
[    0.225696] pci 0000:00:13.5: supports D1 D2
[    0.225699] pci 0000:00:13.5: PME# supported from D0 D1 D2 D3hot
[    0.225760] pci 0000:00:13.5: System wakeup disabled by ACPI
[    0.225818] pci 0000:00:14.0: [1002:4385] type 00 class 0x0c0500
[    0.225845] pci 0000:00:14.0: reg 0x10: [io  0x8410-0x841f]
[    0.226019] pci 0000:00:14.1: [1002:438c] type 00 class 0x01018a
[    0.226035] pci 0000:00:14.1: reg 0x10: [io  0x01f0-0x01f7]
[    0.226045] pci 0000:00:14.1: reg 0x14: [io  0x03f4-0x03f7]
[    0.226055] pci 0000:00:14.1: reg 0x18: [io  0x0000-0x0007]
[    0.226066] pci 0000:00:14.1: reg 0x1c: [io  0x0000-0x0003]
[    0.226077] pci 0000:00:14.1: reg 0x20: [io  0x8420-0x842f]
[    0.226198] pci 0000:00:14.2: [1002:4383] type 00 class 0x040300
[    0.226225] pci 0000:00:14.2: reg 0x10: [mem 0xf0400000-0xf0403fff 64bit]
[    0.226304] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.226363] pci 0000:00:14.2: System wakeup disabled by ACPI
[    0.226413] pci 0000:00:14.3: [1002:438d] type 00 class 0x060100
[    0.226580] pci 0000:00:14.4: [1002:4384] type 01 class 0x060401
[    0.226671] pci 0000:00:14.4: System wakeup disabled by ACPI
[    0.226724] pci 0000:00:18.0: [1022:1100] type 00 class 0x060000
[    0.226825] pci 0000:00:18.1: [1022:1101] type 00 class 0x060000
[    0.226922] pci 0000:00:18.2: [1022:1102] type 00 class 0x060000
[    0.227021] pci 0000:00:18.3: [1022:1103] type 00 class 0x060000
[    0.227187] pci 0000:01:05.0: [1002:791f] type 00 class 0x030000
[    0.227201] pci 0000:01:05.0: reg 0x10: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.227211] pci 0000:01:05.0: reg 0x18: [mem 0xf0100000-0xf010ffff 64bit]
[    0.227218] pci 0000:01:05.0: reg 0x20: [io  0x9000-0x90ff]
[    0.227226] pci 0000:01:05.0: reg 0x24: [mem 0xf0000000-0xf00fffff]
[    0.227248] pci 0000:01:05.0: supports D1 D2
[    0.227302] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.227308] pci 0000:00:01.0:   bridge window [io  0x9000-0x9fff]
[    0.227313] pci 0000:00:01.0:   bridge window [mem 0xf0000000-0xf01fffff]
[    0.227319] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.227427] pci 0000:02:00.0: [14e4:4315] type 00 class 0x028000
[    0.227449] pci 0000:02:00.0: reg 0x10: [mem 0xf0300000-0xf0303fff 64bit]
[    0.227547] pci 0000:02:00.0: supports D1 D2
[    0.227550] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
[    0.232055] pci 0000:00:06.0: PCI bridge to [bus 02-04]
[    0.232061] pci 0000:00:06.0:   bridge window [mem 0xf0300000-0xf03fffff]
[    0.232136] pci 0000:05:00.0: [1969:1062] type 00 class 0x020000
[    0.232160] pci 0000:05:00.0: reg 0x10: [mem 0xf0200000-0xf023ffff 64bit]
[    0.232174] pci 0000:05:00.0: reg 0x18: [io  0xa000-0xa07f]
[    0.232273] pci 0000:05:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.240015] pci 0000:00:07.0: PCI bridge to [bus 05-07]
[    0.240021] pci 0000:00:07.0:   bridge window [io  0xa000-0xafff]
[    0.240026] pci 0000:00:07.0:   bridge window [mem 0xf0200000-0xf02fffff]
[    0.240124] pci 0000:00:14.4: PCI bridge to [bus 08-0a] (subtractive decode)
[    0.240136] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.240140] pci 0000:00:14.4:   bridge window [mem 0x000d0000-0x000d1fff] (subtractive decode)
[    0.240143] pci 0000:00:14.4:   bridge window [mem 0x000d2000-0x000d3fff] (subtractive decode)
[    0.240147] pci 0000:00:14.4:   bridge window [mem 0x000d4000-0x000d5fff] (subtractive decode)
[    0.240150] pci 0000:00:14.4:   bridge window [mem 0x000d6000-0x000d7fff] (subtractive decode)
[    0.240154] pci 0000:00:14.4:   bridge window [mem 0x000d8000-0x000d9fff] (subtractive decode)
[    0.240158] pci 0000:00:14.4:   bridge window [mem 0x000da000-0x000dbfff] (subtractive decode)
[    0.240161] pci 0000:00:14.4:   bridge window [mem 0x000dc000-0x000ddfff] (subtractive decode)
[    0.240165] pci 0000:00:14.4:   bridge window [mem 0x000de000-0x000dffff] (subtractive decode)
[    0.240169] pci 0000:00:14.4:   bridge window [mem 0xd0000000-0xdfffffff] (subtractive decode)
[    0.240172] pci 0000:00:14.4:   bridge window [mem 0xf0000000-0xffffffff] (subtractive decode)
[    0.240176] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.240179] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.240241] pci_bus 0000:00: on NUMA node 0
[    0.240770] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[    0.240846] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[    0.240921] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[    0.240995] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[    0.241069] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[    0.241142] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[    0.241216] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[    0.241290] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[    0.276135] ACPI: Enabled 3 GPEs in block 00 to 1F
[    0.276150] ACPI: \_SB_.PCI0: notify handler is installed
[    0.276199] Found 1 acpi root devices
[    0.276252] ACPI : EC: GPE = 0x10, I/O: command/status = 0x66, data = 0x62
[    0.276437] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
[    0.276440] vgaarb: loaded
[    0.276441] vgaarb: bridge control possible 0000:01:05.0
[    0.276803] SCSI subsystem initialized
[    0.276884] libata version 3.00 loaded.
[    0.276926] ACPI: bus type USB registered
[    0.276957] usbcore: registered new interface driver usbfs
[    0.276972] usbcore: registered new interface driver hub
[    0.277005] usbcore: registered new device driver usb
[    0.277187] PCI: Using ACPI for IRQ routing
[    0.277441] PCI: pci_cache_line_size set to 64 bytes
[    0.277589] e820: reserve RAM buffer [mem 0x0009dc00-0x0009ffff]
[    0.277593] e820: reserve RAM buffer [mem 0xbfe80000-0xbfffffff]
[    0.277730] NetLabel: Initializing
[    0.277733] NetLabel:  domain hash size = 128
[    0.277735] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.277753] NetLabel:  unlabeled traffic allowed by default
[    0.277885] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.277891] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    0.279943] Switched to clocksource hpet
[    0.284398] AppArmor: AppArmor Filesystem Enabled
[    0.284442] pnp: PnP ACPI init
[    0.284463] ACPI: bus type PNP registered
[    0.284656] system 00:00: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.284662] system 00:00: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.284668] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.285154] pnp 00:01: [dma 4]
[    0.285193] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.285248] pnp 00:02: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.285297] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.285340] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.285413] pnp 00:05: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.285534] pnp 00:06: Plug and Play ACPI device, IDs SYN1b1d SYN1b00 SYN0002 PNP0f13 (active)
[    0.285647] system 00:07: [io  0x1080] has been reserved
[    0.285653] system 00:07: [io  0x0220-0x022f] has been reserved
[    0.285657] system 00:07: [io  0x040b] has been reserved
[    0.285661] system 00:07: [io  0x04d0-0x04d1] has been reserved
[    0.285666] system 00:07: [io  0x04d6] has been reserved
[    0.285670] system 00:07: [io  0x0530-0x0537] has been reserved
[    0.285675] system 00:07: [io  0x0c00-0x0c01] has been reserved
[    0.285679] system 00:07: [io  0x0c14] has been reserved
[    0.285683] system 00:07: [io  0x0c50-0x0c52] has been reserved
[    0.285688] system 00:07: [io  0x0c6c] has been reserved
[    0.285692] system 00:07: [io  0x0c6f] has been reserved
[    0.285697] system 00:07: [io  0x0cd0-0x0cd1] has been reserved
[    0.285701] system 00:07: [io  0x0cd2-0x0cd3] has been reserved
[    0.285706] system 00:07: [io  0x0cd4-0x0cd5] has been reserved
[    0.285710] system 00:07: [io  0x0cd6-0x0cd7] has been reserved
[    0.285715] system 00:07: [io  0x0cd8-0x0cdf] has been reserved
[    0.285719] system 00:07: [io  0x8000-0x805f] could not be reserved
[    0.285724] system 00:07: [io  0x8100-0x81ff window] has been reserved
[    0.285728] system 00:07: [io  0x8200-0x82ff window] has been reserved
[    0.285733] system 00:07: [io  0x0f40-0x0f47] has been reserved
[    0.285737] system 00:07: [io  0x087f] has been reserved
[    0.285742] system 00:07: [io  0xfd60-0xfd63] has been reserved
[    0.285747] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.285855] system 00:08: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.285860] system 00:08: [mem 0xfff00000-0xffffffff] has been reserved
[    0.285865] system 00:08: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.286020] pnp 00:09: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.320050] pnp: PnP ACPI: found 10 devices
[    0.320052] ACPI: bus type PNP unregistered
[    0.320056] PnPBIOS: Disabled by ACPI PNP
[    0.356794] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.356801] pci 0000:00:01.0:   bridge window [io  0x9000-0x9fff]
[    0.356806] pci 0000:00:01.0:   bridge window [mem 0xf0000000-0xf01fffff]
[    0.356812] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.356818] pci 0000:00:06.0: PCI bridge to [bus 02-04]
[    0.356823] pci 0000:00:06.0:   bridge window [mem 0xf0300000-0xf03fffff]
[    0.356829] pci 0000:00:07.0: PCI bridge to [bus 05-07]
[    0.356833] pci 0000:00:07.0:   bridge window [io  0xa000-0xafff]
[    0.356838] pci 0000:00:07.0:   bridge window [mem 0xf0200000-0xf02fffff]
[    0.356845] pci 0000:00:14.4: PCI bridge to [bus 08-0a]
[    0.356864] pci_bus 0000:00: resource 4 [mem 0x000a0000-0x000bffff]
[    0.356868] pci_bus 0000:00: resource 5 [mem 0x000d0000-0x000d1fff]
[    0.356872] pci_bus 0000:00: resource 6 [mem 0x000d2000-0x000d3fff]
[    0.356876] pci_bus 0000:00: resource 7 [mem 0x000d4000-0x000d5fff]
[    0.356879] pci_bus 0000:00: resource 8 [mem 0x000d6000-0x000d7fff]
[    0.356883] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000d9fff]
[    0.356887] pci_bus 0000:00: resource 10 [mem 0x000da000-0x000dbfff]
[    0.356891] pci_bus 0000:00: resource 11 [mem 0x000dc000-0x000ddfff]
[    0.356895] pci_bus 0000:00: resource 12 [mem 0x000de000-0x000dffff]
[    0.356899] pci_bus 0000:00: resource 13 [mem 0xd0000000-0xdfffffff]
[    0.356903] pci_bus 0000:00: resource 14 [mem 0xf0000000-0xffffffff]
[    0.356907] pci_bus 0000:00: resource 15 [io  0x0000-0x0cf7]
[    0.356910] pci_bus 0000:00: resource 16 [io  0x0d00-0xffff]
[    0.356915] pci_bus 0000:01: resource 0 [io  0x9000-0x9fff]
[    0.356918] pci_bus 0000:01: resource 1 [mem 0xf0000000-0xf01fffff]
[    0.356923] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.356927] pci_bus 0000:02: resource 1 [mem 0xf0300000-0xf03fffff]
[    0.356931] pci_bus 0000:05: resource 0 [io  0xa000-0xafff]
[    0.356935] pci_bus 0000:05: resource 1 [mem 0xf0200000-0xf02fffff]
[    0.356939] pci_bus 0000:08: resource 4 [mem 0x000a0000-0x000bffff]
[    0.356943] pci_bus 0000:08: resource 5 [mem 0x000d0000-0x000d1fff]
[    0.356947] pci_bus 0000:08: resource 6 [mem 0x000d2000-0x000d3fff]
[    0.356950] pci_bus 0000:08: resource 7 [mem 0x000d4000-0x000d5fff]
[    0.356954] pci_bus 0000:08: resource 8 [mem 0x000d6000-0x000d7fff]
[    0.356958] pci_bus 0000:08: resource 9 [mem 0x000d8000-0x000d9fff]
[    0.356962] pci_bus 0000:08: resource 10 [mem 0x000da000-0x000dbfff]
[    0.356966] pci_bus 0000:08: resource 11 [mem 0x000dc000-0x000ddfff]
[    0.356970] pci_bus 0000:08: resource 12 [mem 0x000de000-0x000dffff]
[    0.356973] pci_bus 0000:08: resource 13 [mem 0xd0000000-0xdfffffff]
[    0.356977] pci_bus 0000:08: resource 14 [mem 0xf0000000-0xffffffff]
[    0.356981] pci_bus 0000:08: resource 15 [io  0x0000-0x0cf7]
[    0.356985] pci_bus 0000:08: resource 16 [io  0x0d00-0xffff]
[    0.357034] NET: Registered protocol family 2
[    0.357273] TCP established hash table entries: 8192 (order: 3, 32768 bytes)
[    0.357306] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.357357] TCP: Hash tables configured (established 8192 bind 8192)
[    0.357405] TCP: reno registered
[    0.357410] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.357424] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.357506] NET: Registered protocol family 1
[    0.358279] pci 0000:01:05.0: Boot video device
[    0.358327] PCI: CLS 32 bytes, default 64
[    0.358404] Trying to unpack rootfs image as initramfs...
[    0.957884] Freeing initrd memory: 18940K (f5af2000 - f6d71000)
[    0.958079] microcode: AMD CPU family 0xf not supported
[    0.958082] Scanning for low memory corruption every 60 seconds
[    0.958439] Initialise system trusted keyring
[    0.958505] audit: initializing netlink socket (disabled)
[    0.958525] type=2000 audit(1397889074.956:1): initialized
[    0.994295] bounce pool size: 64 pages
[    0.994318] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.996491] VFS: Disk quotas dquot_6.5.2
[    0.996560] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.997236] fuse init (API version 7.22)
[    0.997345] msgmni has been set to 1663
[    0.997443] Key type big_key registered
[    0.997800] Key type asymmetric registered
[    0.997803] Asymmetric key parser 'x509' registered
[    0.997855] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.997895] io scheduler noop registered
[    0.997898] io scheduler deadline registered (default)
[    0.997941] io scheduler cfq registered
[    0.998121] pcieport 0000:00:06.0: irq 40 for MSI/MSI-X
[    0.998198] pcieport 0000:00:07.0: irq 41 for MSI/MSI-X
[    0.998275] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.998302] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.998363] vesafb: mode is 1024x768x32, linelength=4096, pages=0
[    0.998365] vesafb: scrolling: redraw
[    0.998369] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[    0.998628] vesafb: framebuffer at 0xd0000000, mapped to 0xf8480000, using 3072k, total 3072k
[    1.107069] Console: switching to colour frame buffer device 128x48
[    1.215400] fb0: VESA VGA frame buffer device
[    1.215478] ipmi message handler version 39.2
[    1.236161] ACPI: AC Adapter [ACAD] (on-line)
[    1.236233] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    1.236239] ACPI: Power Button [PWRB]
[    1.236290] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    1.236294] ACPI: Sleep Button [SLPB]
[    1.236345] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[    1.236375] ACPI: Lid Switch [LID]
[    1.236444] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    1.236448] ACPI: Power Button [PWRF]
[    1.236497] tsc: Marking TSC unstable due to TSC halts in idle
[    1.236508] ACPI: acpi_idle registered with cpuidle
[    1.256185] ACPI: Invalid active0 threshold
[    1.300049] thermal LNXTHERM:00: registered as thermal_zone0
[    1.300052] ACPI: Thermal Zone [THRM] (41 C)
[    1.300155] GHES: HEST is not enabled!
[    1.300345] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.302154] isapnp: Scanning for PnP cards...
[    1.615642] isapnp: No Plug & Play device found
[    1.992155] ACPI: Battery Slot [BAT1] (battery present)
[    1.992313] Linux agpgart interface v0.103
[    1.994434] brd: module loaded
[    1.995435] loop: module loaded
[    1.996241] libphy: Fixed MDIO Bus: probed
[    1.996426] tun: Universal TUN/TAP device driver, 1.6
[    1.996429] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.996503] PPP generic driver version 2.4.2
[    1.996562] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.996567] ehci-pci: EHCI PCI platform driver
[    1.996743] ehci-pci 0000:00:13.5: EHCI Host Controller
[    1.996755] ehci-pci 0000:00:13.5: new USB bus registered, assigned bus number 1
[    1.996764] ehci-pci 0000:00:13.5: applying AMD SB600/SB700 USB freeze workaround
[    1.996781] ehci-pci 0000:00:13.5: debug port 1
[    1.996844] ehci-pci 0000:00:13.5: irq 19, io mem 0xf0607400
[    2.008045] ehci-pci 0000:00:13.5: USB 2.0 started, EHCI 1.00
[    2.008142] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    2.008146] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.008149] usb usb1: Product: EHCI Host Controller
[    2.008153] usb usb1: Manufacturer: Linux 3.13.0-24-generic ehci_hcd
[    2.008156] usb usb1: SerialNumber: 0000:00:13.5
[    2.008293] hub 1-0:1.0: USB hub found
[    2.008304] hub 1-0:1.0: 10 ports detected
[    2.008573] ehci-platform: EHCI generic platform driver
[    2.008587] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.008590] ohci-pci: OHCI PCI platform driver
[    2.008713] ohci-pci 0000:00:13.0: OHCI PCI host controller
[    2.008720] ohci-pci 0000:00:13.0: new USB bus registered, assigned bus number 2
[    2.008756] ohci-pci 0000:00:13.0: irq 16, io mem 0xf0404000
[    2.064091] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    2.064095] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.064098] usb usb2: Product: OHCI PCI host controller
[    2.064101] usb usb2: Manufacturer: Linux 3.13.0-24-generic ohci_hcd
[    2.064104] usb usb2: SerialNumber: 0000:00:13.0
[    2.064226] hub 2-0:1.0: USB hub found
[    2.064241] hub 2-0:1.0: 2 ports detected
[    2.064433] ohci-pci 0000:00:13.1: OHCI PCI host controller
[    2.064440] ohci-pci 0000:00:13.1: new USB bus registered, assigned bus number 3
[    2.064471] ohci-pci 0000:00:13.1: irq 17, io mem 0xf0405000
[    2.120090] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    2.120094] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.120097] usb usb3: Product: OHCI PCI host controller
[    2.120101] usb usb3: Manufacturer: Linux 3.13.0-24-generic ohci_hcd
[    2.120104] usb usb3: SerialNumber: 0000:00:13.1
[    2.120221] hub 3-0:1.0: USB hub found
[    2.120236] hub 3-0:1.0: 2 ports detected
[    2.120430] ohci-pci 0000:00:13.4: OHCI PCI host controller
[    2.120438] ohci-pci 0000:00:13.4: new USB bus registered, assigned bus number 4
[    2.120469] ohci-pci 0000:00:13.4: irq 18, io mem 0xf0406000
[    2.176088] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    2.176092] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.176095] usb usb4: Product: OHCI PCI host controller
[    2.176098] usb usb4: Manufacturer: Linux 3.13.0-24-generic ohci_hcd
[    2.176101] usb usb4: SerialNumber: 0000:00:13.4
[    2.176225] hub 4-0:1.0: USB hub found
[    2.176241] hub 4-0:1.0: 2 ports detected
[    2.176351] ohci-platform: OHCI generic platform driver
[    2.176365] uhci_hcd: USB Universal Host Controller Interface driver
[    2.176476] i8042: PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSS0] at 0x60,0x64 irq 1,12
[    2.199679] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.199711] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.199859] mousedev: PS/2 mouse device common for all mice
[    2.200256] rtc_cmos 00:03: RTC can wake from S4
[    2.200394] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    2.200432] rtc_cmos 00:03: alarms up to one month, 114 bytes nvram, hpet irqs
[    2.200526] device-mapper: uevent: version 1.0.3
[    2.200601] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    2.200631] platform eisa.0: Probing EISA bus 0
[    2.200636] platform eisa.0: EISA: Cannot allocate resource for mainboard
[    2.200640] platform eisa.0: Cannot allocate resource for EISA slot 1
[    2.200644] platform eisa.0: Cannot allocate resource for EISA slot 2
[    2.200648] platform eisa.0: Cannot allocate resource for EISA slot 3
[    2.200652] platform eisa.0: Cannot allocate resource for EISA slot 4
[    2.200656] platform eisa.0: Cannot allocate resource for EISA slot 5
[    2.200660] platform eisa.0: Cannot allocate resource for EISA slot 6
[    2.200663] platform eisa.0: Cannot allocate resource for EISA slot 7
[    2.200667] platform eisa.0: Cannot allocate resource for EISA slot 8
[    2.200671] platform eisa.0: EISA: Detected 0 cards
[    2.200679] cpufreq-nforce2: No nForce2 chipset.
[    2.200684] ledtrig-cpu: registered to indicate activity on CPUs
[    2.200886] TCP: cubic registered
[    2.201027] NET: Registered protocol family 10
[    2.201294] NET: Registered protocol family 17
[    2.201310] Key type dns_resolver registered
[    2.201497] Using IPI No-Shortcut mode
[    2.201593] Loading compiled-in X.509 certificates
[    2.206981] Loaded X.509 cert 'Magrathea: Glacier signing key: 77d70e1df42996dc92b01d759d3e8562ea32a1c7'
[    2.206999] registered taskstats version 1
[    2.210782] Key type trusted registered
[    2.213899] Key type encrypted registered
[    2.216985] AppArmor: AppArmor sha1 policy hashing enabled
[    2.216991] IMA: No TPM chip found, activating TPM-bypass!
[    2.217299] regulator-dummy: disabling
[    2.217357]   Magic number: 10:526:519
[    2.217474] rtc_cmos 00:03: setting system clock to 2014-04-19 06:31:17 UTC (1397889077)
[    2.217620] powernow-k8: fid 0x8 (1600 MHz), vid 0x16
[    2.217623] powernow-k8: fid 0x0 (800 MHz), vid 0x16
[    2.217656] powernow-k8: Found 1 AMD Athlon(tm) Processor TF-20 (1 cpu cores) (version 2.20.00)
[    2.217662] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.217664] EDD information not available.
[    2.217715] PM: Hibernation image not present or could not be loaded.
[    2.218424] Freeing unused kernel memory: 872K (c19ae000 - c1a88000)
[    2.218477] Write protecting the kernel text: 6512k
[    2.218571] Write protecting the kernel read-only data: 2756k
[    2.218573] NX-protecting the kernel data: 5776k
[    2.224672] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    2.248285] systemd-udevd[91]: starting version 204
[    2.320877] usb 1-10: new high-speed USB device number 2 using ehci-pci
[    2.322419] ahci 0000:00:12.0: version 3.0
[    2.322596] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit
[    2.322735] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    2.322740] ahci 0000:00:12.0: flags: ncq sntf ilck led clo pmp pio ccc 
[    2.352582] scsi0 : ahci
[    2.355811] scsi1 : ahci
[    2.356406] scsi2 : ahci
[    2.356544] scsi3 : ahci
[    2.356607] ata1: SATA max UDMA/133 abar m1024@0xf0607000 port 0xf0607100 irq 22
[    2.356612] ata2: SATA max UDMA/133 abar m1024@0xf0607000 port 0xf0607180 irq 22
[    2.356616] ata3: SATA max UDMA/133 abar m1024@0xf0607000 port 0xf0607200 irq 22
[    2.356620] ata4: SATA max UDMA/133 abar m1024@0xf0607000 port 0xf0607280 irq 22
[    2.356711] pata_atiixp 0000:00:14.1: enabling device (0014 -> 0015)
[    2.357710] scsi4 : pata_atiixp
[    2.357800] scsi5 : pata_atiixp
[    2.357863] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x8420 irq 14
[    2.357866] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x8428 irq 15
[    2.368469] atl1c 0000:05:00.0: version 1.0.1.1-NAPI
[    2.676066] ata4: SATA link down (SStatus 0 SControl 300)
[    2.676126] ata2: SATA link down (SStatus 0 SControl 300)
[    2.848029] ata3: softreset failed (device not ready)
[    2.848033] ata3: applying PMP SRST workaround and retrying
[    2.848051] ata1: softreset failed (device not ready)
[    2.848054] ata1: applying PMP SRST workaround and retrying
[    3.020033] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.020064] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.024101] ata3.00: ATAPI: HL-DT-ST DVDRAM GT20N, CP02, max UDMA/133
[    3.024106] ata3.00: SB600 AHCI: limiting to 255 sectors per cmd
[    3.028987] ata3.00: SB600 AHCI: limiting to 255 sectors per cmd
[    3.028991] ata3.00: configured for UDMA/133
[    3.068809] ata1.00: ATA-8: WDC WD1600BEVT-22ZCT0, 11.01A11, max UDMA/133
[    3.068813] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    3.068818] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[    3.070200] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[    3.070203] ata1.00: configured for UDMA/133
[    3.070363] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600BEVT-2 11.0 PQ: 0 ANSI: 5
[    3.070834] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    3.070909] sd 0:0:0:0: [sda] Write Protect is off
[    3.070914] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.070946] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.071384] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.074568] scsi 2:0:0:0: CD-ROM            HL-DT-ST DVDRAM GT20N     CP02 PQ: 0 ANSI: 5
[    3.079514] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.079518] cdrom: Uniform CD-ROM driver Revision: 3.20
[    3.079947] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    3.080130] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    3.085656]  sda: sda1 sda2 < sda5 >
[    3.086039] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.285587] random: lvm urandom read with 42 bits of entropy available
[    3.327504] bio: create slab <bio-1> at 1
[    3.638912] EXT4-fs (dm-0): mounted filesystem with ordered data mode. Opts: (null)
[   17.432038] usb 1-10: device descriptor read/64, error -110
[   32.648035] usb 1-10: device descriptor read/64, error -110
[   32.864039] usb 1-10: new high-speed USB device number 3 using ehci-pci
[   47.976038] usb 1-10: device descriptor read/64, error -110
[   61.917187] random: nonblocking pool is initialized
[   63.192034] usb 1-10: device descriptor read/64, error -110
[   63.408035] usb 1-10: new high-speed USB device number 4 using ehci-pci
[   68.428247] usb 1-10: device descriptor read/8, error -110
[   73.528841] Adding 3932156k swap on /dev/mapper/lubuntu--vg-swap_1.  Priority:-1 extents:1 across:3932156k FS
[   73.548297] usb 1-10: device descriptor read/8, error -110
[   73.618261] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   73.764075] usb 1-10: new high-speed USB device number 5 using ehci-pci
[   73.891713] systemd-udevd[289]: starting version 204
[   73.990415] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
[   74.118582] lp: driver loaded but no devices found
[   74.158138] ppdev: user-space parallel port driver
[   74.449614] EXT4-fs (sda1): mounting ext2 file system using the ext4 subsystem
[   74.461426] EXT4-fs (sda1): mounted filesystem without journal. Opts: (null)
[   74.684613] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   74.780735] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   74.847130] wmi: Mapper loaded
```

---

### Post by ajgreeny on 2014-04-19
It looks as if this a problem with one or more usb peripherals that is causing the delay.
```
[    3.638912] EXT4-fs (dm-0): mounted filesystem with ordered data mode. Opts: (null)
[   17.432038] usb 1-10: device descriptor read/64, error -110
[   32.648035] usb 1-10: device descriptor read/64, error -110
[   32.864039] usb 1-10: new high-speed USB device number 3 using ehci-pci
[   47.976038] usb 1-10: device descriptor read/64, error -110
[   61.917187] random: nonblocking pool is initialized
[   63.192034] usb 1-10: device descriptor read/64, error -110
[   63.408035] usb 1-10: new high-speed USB device number 4 using ehci-pci
[   68.428247] usb 1-10: device descriptor read/8, error -110
[   73.528841] Adding 3932156k swap on /dev/mapper/lubuntu--vg-swap_1.  Priority:-1 extents:1 across:3932156k FS
[   73.548297] usb 1-10: device descriptor read/8, error -110
[   73.618261] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   73.764075] usb 1-10: new high-speed USB device number 5 using ehci-pci
[   73.891713] systemd-udevd[289]: starting version 204
[   73.990415] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
[   74.118582] lp: driver loaded but no devices found
[   74.158138] ppdev: user-space parallel port driver
[   74.449614] EXT4-fs (sda1): mounting ext2 file system using the ext4 subsystem
[   74.461426] EXT4-fs (sda1): mounted filesystem without journal. Opts: (null)
[   74.684613] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   74.780735] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   74.847130] wmi: Mapper loaded
```
Detach any usb items that you have and see if the problem is overcome, then reattach one by one to try to find the problem item.

PS:
For the sort of codeor text that you showed, it is much easier to read if you use the code tags, not quote tags.  Highlight the text you have copied and then click the # icon in the toolbar of the advanced post/reply box.

---

### Post by Jonathan_Traill on 2014-04-19
The only USB device is a fan and I've tried booting without it attached - no difference.

BUT ... I did think last night that I've been experiencing trouble getting flash drives to mount on this machine.  Plug 'em in, and it takes a while for the computer to notice them.  Then they mount okay.  This has been ongoing for a while, can't say if it started about the same time as the slow boot or not - I just assumed it was my computer getting old.  But if there is some USB type issue, could this be a pointer?

---

### Post by ajgreeny on 2014-04-19
Once the machine has successfully booted to Lubuntu run the command **lsusb** and post the output back here with code tags again.

PS: Thanks for your edit to use code tags; much better now to read the thread.

---

### Post by Jonathan_Traill on 2014-04-19
Results of lsusb:

```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

I think we were both hoping for something more?

---

### Post by Jonathan_Traill on 2014-04-20
Bump.

Anyone got tha think as to what to do now?

---

### Post by Jonathan_Traill on 2014-04-21
Now this might be interesting.  The issue that **may** be causing my boot/loading problems seems to be "usb 1-10: device descriptor read/64, error -110," which kicks in at about 3 seconds, leaving the system hanging.  After much googling, I seem to have [stumbled upon an explanation of what this might mean]("http://superuser.com/questions/719302/trying-to-restore-data-usb-drive-not-properly-detected"):

> [COLOR=#000000][FONT=Arial]USB error -110 means [/FONT][/COLOR]**power exceeded**[COLOR=#000000][FONT=Arial], the computer sys could not provide enough power for the pendirve to operate. Thus the device can not provide any data i.e device descriptor thus the computer cannot identify it.
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]Your motherboard is probably not getting enough power, or too many devices connected. Unplug[/FONT][/COLOR]**everything**[COLOR=#000000][FONT=Arial] and unplug the computer from wall for ~3 min for Mb to drain. Restart and try again with absolute minimal things plugged in.[/FONT][/COLOR]

Already tried booting without anything plugged in (only thing I have is the fan), but let's see how we go after a few minutes 'draining.'

EDIT - Nope, no difference ](*,)

---

### Post by Jonathan_Traill on 2014-04-21
[SIZE=3][FONT=arial][SIZE=2]Results of tail -f /var/log/syslog[/SIZE]
[/FONT][/SIZE]
```
Apr 21 22:07:52 Sinbad kernel: [  160.972414] usb 4-2: device descriptor read/8, error -110Apr 21 22:07:54 Sinbad kernel: [  162.758234] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:08:86:3b:d9:86:80:08:00 SRC=192.168.2.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
Apr 21 22:07:57 Sinbad kernel: [  166.092437] usb 4-2: device descriptor read/8, error -110
Apr 21 22:07:57 Sinbad kernel: [  166.196148] hub 4-0:1.0: unable to enumerate USB device on port 2
Apr 21 22:07:58 Sinbad anacron[1660]: Anacron 2.3 started on 2014-04-21
Apr 21 22:07:58 Sinbad anacron[1660]: Normal exit (0 jobs run)
Apr 21 22:09:59 Sinbad kernel: [  287.789363] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:08:86:3b:d9:86:80:08:00 SRC=192.168.2.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
Apr 21 22:12:04 Sinbad kernel: [  412.819180] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:08:86:3b:d9:86:80:08:00 SRC=192.168.2.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
Apr 21 22:14:09 Sinbad kernel: [  537.847874] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:08:86:3b:d9:86:80:08:00 SRC=192.168.2.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
Apr 21 22:16:14 Sinbad kernel: [  662.877241] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:08:86:3b:d9:86:80:08:00 SRC=192.168.2.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
Apr 21 22:17:01 Sinbad CRON[1906]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
```

Which means nothing to me but might mean something to yawl out there ...

---

### Post by Jonathan_Traill on 2014-04-22
Tonight's cunning plan was to install a completely different distro in place of Lubuntu (Slitaz, as I happened to have an old disk lying about) and then re-install Lubuntu ... The idea being that the hang up in loading might be corrupted files from upgrades / downgrades since I installed 12.04, and which may not have been corrected when I did the fresh install of 14.04.  After all,  don't go about reinventing the wheel every day, so why would my computer if it found a whole bunch of files already present?

Anyway, it made no difference except that I'm a couple of hours older and grumpier.  Still getting the 60-70 second hang.

Interstingly, the same thing happened with Slitaz - it also screeched to a stop and - as Slitaz runs screeds of text during loading, it told me what the problem was: ""Detecting USB devices Kernal modes."  Took it ages.  Which, taken with the information upthread, means it looks like some sort of problem with the USB ports talking to the rest of the computer, rather than some vile corruption in Lubuntu.

So, anyone got any bright ideas, other than buying a new laptop?  Are there any work arounds for dodgy USB ports?

---

### Post by sitro on 2014-04-22
hi,
I suppose that this is a mobile computer, probably you have more usb device than you see in the command "lsusb" like webcam, maybe wi-fi etc...
you can have a look with the command lsusb, usb-device,  usbview ... for each command you can launch :
man <command> .example : man lsusb (this is the help on the command) or info lsusb
you can too launch each command with the option /? or -h or --help
example : lsusb -h and you will see that you have a verbose mode for the command lsusb : lsusb -v

to take a tour of your hardware you can too launch : "lspci"

The verbose mode of lsusb show the power consomtion of the device. it can help you.

Maybe if it is a old computer it has a bios mode that you can access when the computer start (F1 or F2 or F10 or DELL or something else . See the manual of the computer)
Once you have entered in the Bios try to see the flag around the usb devices : may be you can disconnect them in the Bios and see what's happenning. try one by one.

---

### Post by oldfred on 2014-04-22
Several years ago a user had a floppy drive enabled in BIOS and had slow boot. But he had no floppy drive.
Do you have anything in BIOS enabled that does not exist?

---

### Post by Jonathan_Traill on 2014-04-22
Results of [COLOR=#000000]lspci:
[/COLOR]
```
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD/ATI] RS690 Host Bridge00:01.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RS690 PCI to PCI Bridge (Internal gfx)
00:06.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RS690 PCI to PCI Bridge (PCI Express Port 2)
00:07.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: Advanced Micro Devices, Inc. [AMD/ATI] SB600 Non-Raid-5 SATA
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB600 USB (OHCI0)
00:13.1 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB600 USB (OHCI1)
00:13.4 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB600 USB (OHCI4)
00:13.5 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB600 USB Controller (EHCI)
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] SB600 IDE
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB600 PCI to LPC Bridge
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RS690M [Radeon Xpress 1200/1250/1270]
02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
05:00.0 Ethernet controller: Qualcomm Atheros AR8132 Fast Ethernet (rev c0)
```

lsusb -v gives us:

```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0002 2.0 root hub
  bcdDevice            3.13
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12


Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            3.13
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255


Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            3.13
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255


Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            3.13
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
```

That's a lot of code, and frankly means little to me.  How does it relate to what seems to be our choke point, the "usb 1-10: device descriptor read/64, error -110" message at about 3 seconds into loading?

Thank you massively for taking an interest.

---

### Post by sitro on 2014-04-23
First Il read il tne second line of the output this : "[COLOR=#000000][FONT=Ubuntu Mono]Couldn't open device, some information will be missing"
[/FONT][/COLOR]This is because you don't have super privilege when you launch the command lsusb.
So to have complete information you may launch with super privilege : you type "sudo" before the command for that.
example : sudo lsusb 
Anyway, it seems that you don't have any usb device except root hub usb but have an error message around the usb device.
probably you have 4 usb  on the hub, one in 2.0 and 3 in 1.1. 

First step :
to be sure post the output of the commands :
sudo lspci -v |grep -C8 USB #print 8 lines from the line where the chain "USB" is present. increase the numbers of line if you don't have all the information about usb.
sudo lsusb -v 

Second step :
If you have a CDROM reader : eject CDROM in case.
Same for usb stick : eject stick.



third step : go in the BIOS. (you didn't tell us what you make about, even if you did)
To acces the Bios system follow this : 
[COLOR=#000000][FONT=Georgia]Wait for the Emachines logo to appear on the screen as the computer begins booting up again. Press the "Tab" key when the logo appears and see if the computer switches to the BIOS menu.[/FONT][/COLOR][FONT=inherit][FONT=inherit][FONT=Georgia]Press the "Escape," "Delete," or "F2" keys if the "Tab" key doesn't take you to the BIOS menu screen.[FONT=Arial]Read more: [/FONT][http://www.ehow.com/how_5402600_access-bios-settings-emachine.html]("http://www.ehow.com/how_5402600_access-bios-settings-emachine.html#ixzz2zhL3zLf3")[/FONT]
[/FONT]
[/FONT]

Of course, you cannot post screen of the BIOS except if you have a camera. but may be you can make an adventure to look inside and before change anything in the Bios, for each option bios, try to understand them. anyway if you change something, when you leave the bios, it ask you to accept the change or leave without change.
In the bios, you have to look after the USB system and often it is possible to disconnect it.
If you can do it (disconnect the USB in the Bios) try to restart et see if you have always the problem.

Four : 
google "code error usb 110[COLOR=#000000]"
[/COLOR]and you will find many answers, sometimes "SOLVED"
For example these :
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/54273](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/54273)
[http://ubuntuforums.org/showthread.php?t=1610142](http://ubuntuforums.org/showthread.php?t=1610142)

...

---

### Post by Jonathan_Traill on 2014-04-23
Results of sudo lspci -v |grep -C8 USB #:

```
I/O ports at 8434 [size=4]    I/O ports at 8438 [size=8]
    I/O ports at 8430 [size=4]
    I/O ports at 8400 [size=16]
    Memory at f0607000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [60] Power Management version 2
    Kernel driver in use: ahci


00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB600 USB (OHCI0) (prog-if 10 [OHCI])
    Subsystem: Acer Incorporated [ALI] Device 0213
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
    Memory at f0404000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci-pci


00:13.1 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB600 USB (OHCI1) (prog-if 10 [OHCI])
    Subsystem: Acer Incorporated [ALI] Device 0213
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at f0405000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci-pci


00:13.4 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB600 USB (OHCI4) (prog-if 10 [OHCI])
    Subsystem: Acer Incorporated [ALI] Device 0213
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at f0406000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci-pci


00:13.5 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB600 USB Controller (EHCI) (prog-if 20 [EHCI])
    Subsystem: Acer Incorporated [ALI] Device 0213
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
    Memory at f0607400 (32-bit, non-prefetchable) [size=256]
    Capabilities: [c0] Power Management version 2
    Capabilities: [e4] Debug port: BAR=1 offset=00e0
    Kernel driver in use: ehci-pci


00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 14)
```

Results of [COLOR=#000000]sudo lsusb -v:[/COLOR]
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0002 2.0 root hub
  bcdDevice            3.13
  iManufacturer           3 Linux 3.13.0-24-generic ehci_hcd
  iProduct                2 EHCI Host Controller
  iSerial                 1 0000:00:13.5
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12
Hub Descriptor:
  bLength              11
  bDescriptorType      41
  nNbrPorts            10
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood       10 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00 0x00
  PortPwrCtrlMask    0xff 0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
   Port 4: 0000.0100 power
   Port 5: 0000.0100 power
   Port 6: 0000.0100 power
   Port 7: 0000.0100 power
   Port 8: 0000.0100 power
   Port 9: 0000.0100 power
   Port 10: 0000.0100 power
Device Status:     0x0001
  Self Powered


Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

Nothing in the bios immediately looks suspicious.  I've reset everything in the bios to standard to be on the safe side.

As for searching for other threads ... there are a few out there, but many are just left unsolved (presumably the problem was sorted out) or solved without a clear chain of actions to get to the solution.  The best lead I've come up with suggested it might be a power issue but gave no clue to a solution.

From my google bashing, here's the results of sudo egrep -i 'error|warning' /var/log/*log:

```
/var/log/auth.log:Apr 23 00:47:44 Sinbad dbus[428]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.11" (uid=0 pid=660 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.4" (uid=0 pid=636 comm="NetworkManager ")
/var/log/auth.log:Apr 23 08:54:36 Sinbad dbus[391]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.10" (uid=0 pid=771 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.5" (uid=0 pid=635 comm="NetworkManager ")
/var/log/auth.log:Apr 23 10:19:08 Sinbad dbus[421]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.27" (uid=0 pid=1690 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.5" (uid=0 pid=700 comm="NetworkManager ")
/var/log/auth.log:Apr 23 12:14:43 Sinbad dbus[431]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.10" (uid=0 pid=862 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.5" (uid=0 pid=699 comm="NetworkManager ")
/var/log/auth.log:Apr 23 12:54:36 Sinbad dbus[445]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.10" (uid=0 pid=866 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.5" (uid=0 pid=701 comm="NetworkManager ")
/var/log/auth.log:Apr 23 13:35:26 Sinbad dbus[448]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.26" (uid=0 pid=1423 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.5" (uid=0 pid=688 comm="NetworkManager ")
/var/log/auth.log:Apr 23 14:58:19 Sinbad dbus[444]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.10" (uid=0 pid=875 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.5" (uid=0 pid=698 comm="NetworkManager ")
/var/log/auth.log:Apr 23 16:11:44 Sinbad dbus[445]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.10" (uid=0 pid=881 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.5" (uid=0 pid=698 comm="NetworkManager ")
/var/log/auth.log:Apr 23 16:13:10 Sinbad dbus[445]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.10" (uid=0 pid=881 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.5" (uid=0 pid=698 comm="NetworkManager ")
/var/log/auth.log:Apr 23 16:15:03 Sinbad dbus[445]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.10" (uid=0 pid=881 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.5" (uid=0 pid=698 comm="NetworkManager ")
/var/log/auth.log:Apr 23 16:17:16 Sinbad dbus[445]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.10" (uid=0 pid=881 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.5" (uid=0 pid=698 comm="NetworkManager ")
/var/log/auth.log:Apr 23 16:20:01 Sinbad dbus[399]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.14" (uid=0 pid=1078 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.5" (uid=0 pid=701 comm="NetworkManager ")
/var/log/auth.log:Apr 23 16:44:11 Sinbad dbus[397]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.14" (uid=0 pid=1079 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.5" (uid=0 pid=679 comm="NetworkManager ")
/var/log/auth.log:Apr 23 17:13:41 Sinbad dbus[375]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.14" (uid=0 pid=1080 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.5" (uid=0 pid=653 comm="NetworkManager ")
/var/log/auth.log:Apr 23 19:51:17 Sinbad dbus[389]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.14" (uid=0 pid=1080 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.5" (uid=0 pid=682 comm="NetworkManager ")
/var/log/auth.log:Apr 24 08:46:11 Sinbad dbus[431]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.14" (uid=0 pid=1098 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.5" (uid=0 pid=672 comm="NetworkManager ")
/var/log/auth.log:Apr 24 10:19:50 Sinbad dbus[392]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.14" (uid=0 pid=985 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.5" (uid=0 pid=622 comm="NetworkManager ")
/var/log/auth.log:Apr 24 10:47:19 Sinbad sudo:       jt : TTY=pts/1 ; PWD=/home/jt ; USER=root ; COMMAND=/bin/egrep -i error|warning /var/log/alternatives.log /var/log/apport.log /var/log/auth.log /var/log/boot.log /var/log/bootstrap.log /var/log/dpkg.log /var/log/faillog /var/log/fontconfig.log /var/log/gpu-manager.log /var/log/kern.log /var/log/lastlog /var/log/pm-powersave.log /var/log/syslog /var/log/wvdialconf.log /var/log/Xorg.0.log
/var/log/bootstrap.log:dpkg: warning: parsing file '/var/lib/dpkg/status' near line 4 package 'dpkg':
/var/log/bootstrap.log:dpkg: warning: parsing file '/var/lib/dpkg/status' near line 4 package 'dpkg':
/var/log/bootstrap.log:dpkg: warning: parsing file '/var/lib/dpkg/status' near line 4 package 'dpkg':
/var/log/bootstrap.log:dpkg: warning: parsing file '/var/lib/dpkg/status' near line 23 package 'dpkg':
/var/log/bootstrap.log:dpkg: warning: parsing file '/var/lib/dpkg/status' near line 23 package 'dpkg':
/var/log/bootstrap.log:dpkg: warning: parsing file '/var/lib/dpkg/status' near line 23 package 'dpkg':
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: parsing file '/var/lib/dpkg/status' near line 56 package 'dpkg':
/var/log/bootstrap.log:dpkg: warning: parsing file '/var/lib/dpkg/status' near line 56 package 'dpkg':
/var/log/bootstrap.log:dpkg: warning: parsing file '/var/lib/dpkg/status' near line 56 package 'dpkg':
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: error: --compare-versions takes three arguments: <version> <relation> <version>
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:Preparing to unpack .../libgpg-error0_1.12-0.2ubuntu1_i386.deb ...
/var/log/bootstrap.log:Unpacking libgpg-error0:i386 (1.12-0.2ubuntu1) ...
/var/log/bootstrap.log:Setting up libgpg-error0:i386 (1.12-0.2ubuntu1) ...
/var/log/dpkg.log:2014-04-16 19:31:27 install libgpg-error0:i386 <none> 1.12-0.2ubuntu1
/var/log/dpkg.log:2014-04-16 19:31:27 status half-installed libgpg-error0:i386 1.12-0.2ubuntu1
/var/log/dpkg.log:2014-04-16 19:31:27 status unpacked libgpg-error0:i386 1.12-0.2ubuntu1
/var/log/dpkg.log:2014-04-16 19:31:27 status unpacked libgpg-error0:i386 1.12-0.2ubuntu1
/var/log/dpkg.log:2014-04-16 19:31:31 configure libgpg-error0:i386 1.12-0.2ubuntu1 <none>
/var/log/dpkg.log:2014-04-16 19:31:31 status unpacked libgpg-error0:i386 1.12-0.2ubuntu1
/var/log/dpkg.log:2014-04-16 19:31:31 status half-configured libgpg-error0:i386 1.12-0.2ubuntu1
/var/log/dpkg.log:2014-04-16 19:31:31 status installed libgpg-error0:i386 1.12-0.2ubuntu1
/var/log/kern.log:Apr 23 00:47:35 Sinbad kernel: [   17.440036] usb 1-10: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 00:47:35 Sinbad kernel: [   32.656033] usb 1-10: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 00:47:35 Sinbad kernel: [   47.984035] usb 1-10: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 00:47:35 Sinbad kernel: [   63.200036] usb 1-10: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 00:47:35 Sinbad kernel: [   67.153707] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Apr 23 00:47:35 Sinbad kernel: [   68.441731] usb 1-10: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 00:47:35 Sinbad kernel: [   71.081329] b43 ssb0:0: Direct firmware load failed with error -2
/var/log/kern.log:Apr 23 00:47:35 Sinbad kernel: [   71.493010] b43 ssb0:0: Direct firmware load failed with error -2
/var/log/kern.log:Apr 23 00:47:36 Sinbad kernel: [   71.588148] b43 ssb0:0: Direct firmware load failed with error -2
/var/log/kern.log:Apr 23 00:47:36 Sinbad kernel: [   71.589603] b43 ssb0:0: Direct firmware load failed with error -2
/var/log/kern.log:Apr 23 00:47:36 Sinbad kernel: [   71.591526] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
/var/log/kern.log:Apr 23 00:47:36 Sinbad kernel: [   71.591528] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
/var/log/kern.log:Apr 23 00:47:36 Sinbad kernel: [   71.591530] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
/var/log/kern.log:Apr 23 00:47:37 Sinbad kernel: [   73.560638] usb 1-10: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 00:47:43 Sinbad kernel: [   78.796238] usb 1-10: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 00:47:48 Sinbad kernel: [   83.916923] usb 1-10: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 00:48:03 Sinbad kernel: [   99.452103] usb 4-2: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 00:48:18 Sinbad kernel: [  114.692047] usb 4-2: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 00:48:34 Sinbad kernel: [  130.068051] usb 4-2: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 00:48:49 Sinbad kernel: [  145.312129] usb 4-2: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 00:48:54 Sinbad kernel: [  150.573025] usb 4-2: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 00:48:59 Sinbad kernel: [  155.692586] usb 4-2: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 00:49:05 Sinbad kernel: [  160.952214] usb 4-2: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 00:49:10 Sinbad kernel: [  166.072751] usb 4-2: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 08:54:30 Sinbad kernel: [   17.440038] usb 1-10: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 08:54:30 Sinbad kernel: [   32.656036] usb 1-10: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 08:54:30 Sinbad kernel: [   47.984039] usb 1-10: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 08:54:30 Sinbad kernel: [   63.200036] usb 1-10: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 08:54:30 Sinbad kernel: [   68.436240] usb 1-10: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 08:54:30 Sinbad kernel: [   73.444629] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Apr 23 08:54:30 Sinbad kernel: [   73.556292] usb 1-10: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 08:54:31 Sinbad kernel: [   76.453113] b43 ssb0:0: Direct firmware load failed with error -2
/var/log/kern.log:Apr 23 08:54:33 Sinbad kernel: [   77.856438] b43 ssb0:0: Direct firmware load failed with error -2
/var/log/kern.log:Apr 23 08:54:33 Sinbad kernel: [   78.039528] b43 ssb0:0: Direct firmware load failed with error -2
/var/log/kern.log:Apr 23 08:54:33 Sinbad kernel: [   78.054988] b43 ssb0:0: Direct firmware load failed with error -2
/var/log/kern.log:Apr 23 08:54:33 Sinbad kernel: [   78.068826] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
/var/log/kern.log:Apr 23 08:54:33 Sinbad kernel: [   78.068940] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
/var/log/kern.log:Apr 23 08:54:33 Sinbad kernel: [   78.069049] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
/var/log/kern.log:Apr 23 08:54:34 Sinbad kernel: [   78.804244] usb 1-10: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 08:54:39 Sinbad kernel: [   83.924305] usb 1-10: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 08:54:54 Sinbad kernel: [   99.492031] usb 4-2: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 08:55:10 Sinbad kernel: [  114.732032] usb 4-2: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 08:55:25 Sinbad kernel: [  130.108038] usb 4-2: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 08:55:40 Sinbad kernel: [  145.352109] usb 4-2: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 08:55:45 Sinbad kernel: [  150.616603] usb 4-2: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 08:55:51 Sinbad kernel: [  155.737031] usb 4-2: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 08:55:56 Sinbad kernel: [  160.996418] usb 4-2: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 08:56:01 Sinbad kernel: [  166.116859] usb 4-2: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 10:12:50 Sinbad kernel: [   17.444036] usb 1-10: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 10:12:50 Sinbad kernel: [   32.660032] usb 1-10: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 10:12:50 Sinbad kernel: [   47.988036] usb 1-10: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 10:12:50 Sinbad kernel: [   63.204028] usb 1-10: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 10:12:50 Sinbad kernel: [   68.440363] usb 1-10: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 10:12:50 Sinbad kernel: [   73.085398] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Apr 23 10:12:50 Sinbad kernel: [   73.560291] usb 1-10: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 10:12:51 Sinbad kernel: [   75.822380] b43 ssb0:0: Direct firmware load failed with error -2
/var/log/kern.log:Apr 23 10:12:52 Sinbad kernel: [   77.166631] b43 ssb0:0: Direct firmware load failed with error -2
/var/log/kern.log:Apr 23 10:12:52 Sinbad kernel: [   77.269295] b43 ssb0:0: Direct firmware load failed with error -2
/var/log/kern.log:Apr 23 10:12:52 Sinbad kernel: [   77.270926] b43 ssb0:0: Direct firmware load failed with error -2
/var/log/kern.log:Apr 23 10:12:52 Sinbad kernel: [   77.272813] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
/var/log/kern.log:Apr 23 10:12:52 Sinbad kernel: [   77.272925] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
/var/log/kern.log:Apr 23 10:12:52 Sinbad kernel: [   77.273033] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
/var/log/kern.log:Apr 23 10:12:54 Sinbad kernel: [   78.804272] usb 1-10: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 10:12:59 Sinbad kernel: [   83.924328] usb 1-10: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 10:13:14 Sinbad kernel: [   99.444037] usb 4-2: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 10:13:29 Sinbad kernel: [  114.684040] usb 4-2: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 10:13:45 Sinbad kernel: [  130.060047] usb 4-2: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 10:14:00 Sinbad kernel: [  145.300088] usb 4-2: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 10:14:05 Sinbad kernel: [  150.560533] usb 4-2: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 10:14:10 Sinbad kernel: [  155.680534] usb 4-2: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 10:14:16 Sinbad kernel: [  160.940582] usb 4-2: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 10:14:21 Sinbad kernel: [  166.060681] usb 4-2: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 12:14:38 Sinbad kernel: [   17.440036] usb 1-10: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 12:14:38 Sinbad kernel: [   32.656035] usb 1-10: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 12:14:38 Sinbad kernel: [   47.984038] usb 1-10: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 12:14:38 Sinbad kernel: [   63.200036] usb 1-10: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 12:14:38 Sinbad kernel: [   68.436242] usb 1-10: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 12:14:38 Sinbad kernel: [   73.547413] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Apr 23 12:14:38 Sinbad kernel: [   73.556287] usb 1-10: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 12:14:39 Sinbad kernel: [   76.023376] b43 ssb0:0: Direct firmware load failed with error -2
/var/log/kern.log:Apr 23 12:14:40 Sinbad kernel: [   77.713106] b43 ssb0:0: Direct firmware load failed with error -2
/var/log/kern.log:Apr 23 12:14:41 Sinbad kernel: [   77.872529] b43 ssb0:0: Direct firmware load failed with error -2
/var/log/kern.log:Apr 23 12:14:41 Sinbad kernel: [   77.874556] b43 ssb0:0: Direct firmware load failed with error -2
/var/log/kern.log:Apr 23 12:14:41 Sinbad kernel: [   77.876497] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
/var/log/kern.log:Apr 23 12:14:41 Sinbad kernel: [   77.876609] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
/var/log/kern.log:Apr 23 12:14:41 Sinbad kernel: [   77.876717] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
/var/log/kern.log:Apr 23 12:14:42 Sinbad kernel: [   78.792236] usb 1-10: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 12:14:47 Sinbad kernel: [   83.912315] usb 1-10: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 12:15:02 Sinbad kernel: [   99.460065] usb 4-2: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 12:15:17 Sinbad kernel: [  114.700086] usb 4-2: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 12:15:33 Sinbad kernel: [  130.076069] usb 4-2: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 12:15:48 Sinbad kernel: [  145.324056] usb 4-2: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 12:15:53 Sinbad kernel: [  150.588645] usb 4-2: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 12:15:58 Sinbad kernel: [  155.708236] usb 4-2: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 12:16:04 Sinbad kernel: [  160.968903] usb 4-2: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 12:16:09 Sinbad kernel: [  166.088489] usb 4-2: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 12:54:31 Sinbad kernel: [   17.436036] usb 1-10: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 12:54:31 Sinbad kernel: [   32.652033] usb 1-10: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 12:54:31 Sinbad kernel: [   47.980039] usb 1-10: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 12:54:31 Sinbad kernel: [   63.196033] usb 1-10: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 12:54:31 Sinbad kernel: [   68.432315] usb 1-10: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 12:54:31 Sinbad kernel: [   72.874247] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Apr 23 12:54:31 Sinbad kernel: [   73.553947] usb 1-10: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 12:54:31 Sinbad kernel: [   75.688526] b43 ssb0:0: Direct firmware load failed with error -2
/var/log/kern.log:Apr 23 12:54:33 Sinbad kernel: [   77.108119] b43 ssb0:0: Direct firmware load failed with error -2
/var/log/kern.log:Apr 23 12:54:33 Sinbad kernel: [   77.184195] b43 ssb0:0: Direct firmware load failed with error -2
/var/log/kern.log:Apr 23 12:54:33 Sinbad kernel: [   77.185606] b43 ssb0:0: Direct firmware load failed with error -2
/var/log/kern.log:Apr 23 12:54:33 Sinbad kernel: [   77.189968] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
/var/log/kern.log:Apr 23 12:54:33 Sinbad kernel: [   77.190081] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
/var/log/kern.log:Apr 23 12:54:33 Sinbad kernel: [   77.190189] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
/var/log/kern.log:Apr 23 12:54:35 Sinbad kernel: [   78.788583] usb 1-10: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 12:54:40 Sinbad kernel: [   83.908281] usb 1-10: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 13:34:44 Sinbad kernel: [   17.440038] usb 1-10: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 13:34:44 Sinbad kernel: [   32.656035] usb 1-10: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 13:34:44 Sinbad kernel: [   47.984039] usb 1-10: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 13:34:44 Sinbad kernel: [   63.200034] usb 1-10: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 13:34:44 Sinbad kernel: [   68.436237] usb 1-10: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 13:34:44 Sinbad kernel: [   73.393201] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Apr 23 13:34:44 Sinbad kernel: [   73.556380] usb 1-10: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 13:34:44 Sinbad kernel: [   75.613359] b43 ssb0:0: Direct firmware load failed with error -2
/var/log/kern.log:Apr 23 13:34:46 Sinbad kernel: [   77.248865] b43 ssb0:0: Direct firmware load failed with error -2
/var/log/kern.log:Apr 23 13:34:46 Sinbad kernel: [   77.402213] b43 ssb0:0: Direct firmware load failed with error -2
/var/log/kern.log:Apr 23 13:34:46 Sinbad kernel: [   77.410880] b43 ssb0:0: Direct firmware load failed with error -2
/var/log/kern.log:Apr 23 13:34:46 Sinbad kernel: [   77.431086] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
/var/log/kern.log:Apr 23 13:34:46 Sinbad kernel: [   77.431200] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
/var/log/kern.log:Apr 23 13:34:46 Sinbad kernel: [   77.431308] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
/var/log/kern.log:Apr 23 13:34:48 Sinbad kernel: [   78.792255] usb 1-10: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 13:34:53 Sinbad kernel: [   83.912200] usb 1-10: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 13:35:08 Sinbad kernel: [   99.476049] usb 4-2: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 13:35:23 Sinbad kernel: [  114.716050] usb 4-2: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 13:35:39 Sinbad kernel: [  130.092037] usb 4-2: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 13:35:54 Sinbad kernel: [  145.344118] usb 4-2: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 13:35:59 Sinbad kernel: [  150.604595] usb 4-2: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 13:36:05 Sinbad kernel: [  155.725069] usb 4-2: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 13:36:10 Sinbad kernel: [  160.988460] usb 4-2: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 13:36:15 Sinbad kernel: [  166.108931] usb 4-2: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 14:58:14 Sinbad kernel: [   17.440036] usb 1-10: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 14:58:14 Sinbad kernel: [   32.656034] usb 1-10: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 14:58:14 Sinbad kernel: [   47.984039] usb 1-10: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 14:58:14 Sinbad kernel: [   63.200033] usb 1-10: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 14:58:14 Sinbad kernel: [   68.436255] usb 1-10: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 14:58:14 Sinbad kernel: [   73.556293] usb 1-10: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 14:58:14 Sinbad kernel: [   73.714274] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Apr 23 14:58:15 Sinbad kernel: [   76.015976] b43 ssb0:0: Direct firmware load failed with error -2
/var/log/kern.log:Apr 23 14:58:16 Sinbad kernel: [   77.702756] b43 ssb0:0: Direct firmware load failed with error -2
/var/log/kern.log:Apr 23 14:58:17 Sinbad kernel: [   77.803127] b43 ssb0:0: Direct firmware load failed with error -2
/var/log/kern.log:Apr 23 14:58:17 Sinbad kernel: [   77.849551] b43 ssb0:0: Direct firmware load failed with error -2
/var/log/kern.log:Apr 23 14:58:17 Sinbad kernel: [   77.881523] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
/var/log/kern.log:Apr 23 14:58:17 Sinbad kernel: [   77.881534] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
/var/log/kern.log:Apr 23 14:58:17 Sinbad kernel: [   77.881540] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
/var/log/kern.log:Apr 23 14:58:18 Sinbad kernel: [   78.796239] usb 1-10: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 14:58:23 Sinbad kernel: [   83.916299] usb 1-10: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 14:58:40 Sinbad kernel: [   99.480067] usb 4-2: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 14:58:56 Sinbad kernel: [  114.732051] usb 4-2: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 14:59:11 Sinbad kernel: [  130.108039] usb 4-2: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 14:59:26 Sinbad kernel: [  145.352109] usb 4-2: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 14:59:32 Sinbad kernel: [  150.620586] usb 4-2: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 14:59:37 Sinbad kernel: [  155.740616] usb 4-2: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 14:59:42 Sinbad kernel: [  161.016643] usb 4-2: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 14:59:47 Sinbad kernel: [  166.136685] usb 4-2: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 16:11:39 Sinbad kernel: [   17.440036] usb 1-10: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 16:11:39 Sinbad kernel: [   32.656033] usb 1-10: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 16:11:39 Sinbad kernel: [   47.984038] usb 1-10: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 16:11:39 Sinbad kernel: [   63.200030] usb 1-10: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 16:11:39 Sinbad kernel: [   68.436242] usb 1-10: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 16:11:39 Sinbad kernel: [   73.500234] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Apr 23 16:11:39 Sinbad kernel: [   73.556291] usb 1-10: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 16:11:40 Sinbad kernel: [   76.465405] b43 ssb0:0: Direct firmware load failed with error -2
/var/log/kern.log:Apr 23 16:11:41 Sinbad kernel: [   77.519226] b43 ssb0:0: Direct firmware load failed with error -2
/var/log/kern.log:Apr 23 16:11:41 Sinbad kernel: [   77.594837] b43 ssb0:0: Direct firmware load failed with error -2
/var/log/kern.log:Apr 23 16:11:41 Sinbad kernel: [   77.605527] b43 ssb0:0: Direct firmware load failed with error -2
/var/log/kern.log:Apr 23 16:11:41 Sinbad kernel: [   77.619491] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
/var/log/kern.log:Apr 23 16:11:41 Sinbad kernel: [   77.620826] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
/var/log/kern.log:Apr 23 16:11:41 Sinbad kernel: [   77.622210] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
/var/log/kern.log:Apr 23 16:11:43 Sinbad kernel: [   78.792245] usb 1-10: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 16:11:48 Sinbad kernel: [   83.912303] usb 1-10: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 16:12:05 Sinbad kernel: [   99.464050] usb 4-2: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 16:12:20 Sinbad kernel: [  114.704037] usb 4-2: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 16:12:36 Sinbad kernel: [  130.080057] usb 4-2: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 16:12:51 Sinbad kernel: [  145.320073] usb 4-2: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 16:12:56 Sinbad kernel: [  150.580772] usb 4-2: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 16:13:01 Sinbad kernel: [  155.700800] usb 4-2: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 16:13:07 Sinbad kernel: [  160.960831] usb 4-2: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 16:13:12 Sinbad kernel: [  166.080861] usb 4-2: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 16:19:54 Sinbad kernel: [   17.440036] usb 1-10: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 16:19:54 Sinbad kernel: [   32.656036] usb 1-10: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 16:19:54 Sinbad kernel: [   47.984037] usb 1-10: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 16:19:54 Sinbad kernel: [   63.200036] usb 1-10: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 16:19:54 Sinbad kernel: [   68.436255] usb 1-10: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 16:19:54 Sinbad kernel: [   73.556295] usb 1-10: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 16:19:54 Sinbad kernel: [   73.782355] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Apr 23 16:19:57 Sinbad kernel: [   78.796244] usb 1-10: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 16:20:02 Sinbad kernel: [   83.916318] usb 1-10: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 16:20:17 Sinbad kernel: [   99.456066] usb 4-2: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 16:20:32 Sinbad kernel: [  114.708112] usb 4-2: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 16:20:48 Sinbad kernel: [  130.104066] usb 4-2: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 16:21:03 Sinbad kernel: [  145.344057] usb 4-2: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 16:21:08 Sinbad kernel: [  150.605098] usb 4-2: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 16:21:14 Sinbad kernel: [  155.724569] usb 4-2: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 16:21:19 Sinbad kernel: [  160.996979] usb 4-2: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 16:21:24 Sinbad kernel: [  166.116451] usb 4-2: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 16:44:04 Sinbad kernel: [   17.440038] usb 1-10: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 16:44:04 Sinbad kernel: [   32.656035] usb 1-10: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 16:44:04 Sinbad kernel: [   47.984039] usb 1-10: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 16:44:04 Sinbad kernel: [   63.200036] usb 1-10: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 16:44:04 Sinbad kernel: [   68.436244] usb 1-10: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 16:44:04 Sinbad kernel: [   73.047366] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Apr 23 16:44:04 Sinbad kernel: [   73.557133] usb 1-10: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 16:44:08 Sinbad kernel: [   78.792247] usb 1-10: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 16:44:13 Sinbad kernel: [   83.912223] usb 1-10: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 16:44:28 Sinbad kernel: [   99.428091] usb 4-2: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 16:44:43 Sinbad kernel: [  114.668062] usb 4-2: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 16:44:59 Sinbad kernel: [  130.044065] usb 4-2: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 16:45:14 Sinbad kernel: [  145.284112] usb 4-2: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 16:45:19 Sinbad kernel: [  150.544971] usb 4-2: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 16:45:24 Sinbad kernel: [  155.664538] usb 4-2: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 16:45:30 Sinbad kernel: [  160.924196] usb 4-2: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 16:45:35 Sinbad kernel: [  166.044887] usb 4-2: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 17:13:34 Sinbad kernel: [   17.440038] usb 1-10: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 17:13:34 Sinbad kernel: [   32.656035] usb 1-10: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 17:13:34 Sinbad kernel: [   47.984038] usb 1-10: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 17:13:34 Sinbad kernel: [   63.200036] usb 1-10: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 17:13:34 Sinbad kernel: [   68.436240] usb 1-10: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 17:13:34 Sinbad kernel: [   72.793206] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Apr 23 17:13:34 Sinbad kernel: [   73.556297] usb 1-10: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 17:13:38 Sinbad kernel: [   78.796262] usb 1-10: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 17:13:43 Sinbad kernel: [   83.916200] usb 1-10: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 17:13:58 Sinbad kernel: [   99.432120] usb 4-2: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 17:14:13 Sinbad kernel: [  114.672046] usb 4-2: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 17:14:29 Sinbad kernel: [  130.048044] usb 4-2: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 17:14:44 Sinbad kernel: [  145.288335] usb 4-2: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 17:14:49 Sinbad kernel: [  150.552443] usb 4-2: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 17:14:54 Sinbad kernel: [  155.673045] usb 4-2: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 17:15:00 Sinbad kernel: [  160.932716] usb 4-2: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 17:15:05 Sinbad kernel: [  166.052300] usb 4-2: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 19:51:10 Sinbad kernel: [   17.440035] usb 1-10: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 19:51:10 Sinbad kernel: [   32.656033] usb 1-10: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 19:51:10 Sinbad kernel: [   47.984038] usb 1-10: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 19:51:10 Sinbad kernel: [   63.200036] usb 1-10: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 19:51:10 Sinbad kernel: [   68.436327] usb 1-10: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 19:51:10 Sinbad kernel: [   73.556369] usb 1-10: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 19:51:10 Sinbad kernel: [   73.660052] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Apr 23 19:51:14 Sinbad kernel: [   78.792318] usb 1-10: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 19:51:19 Sinbad kernel: [   83.912273] usb 1-10: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 19:51:36 Sinbad kernel: [   99.436069] usb 4-2: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 19:51:52 Sinbad kernel: [  114.676054] usb 4-2: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 19:52:07 Sinbad kernel: [  130.052042] usb 4-2: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 19:52:22 Sinbad kernel: [  145.292068] usb 4-2: device descriptor read/64, error -110
/var/log/kern.log:Apr 23 19:52:28 Sinbad kernel: [  150.552576] usb 4-2: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 19:52:33 Sinbad kernel: [  155.672609] usb 4-2: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 19:52:38 Sinbad kernel: [  160.932635] usb 4-2: device descriptor read/8, error -110
/var/log/kern.log:Apr 23 19:52:43 Sinbad kernel: [  166.052653] usb 4-2: device descriptor read/8, error -110
/var/log/kern.log:Apr 24 08:46:03 Sinbad kernel: [   17.440038] usb 1-10: device descriptor read/64, error -110
/var/log/kern.log:Apr 24 08:46:03 Sinbad kernel: [   32.656035] usb 1-10: device descriptor read/64, error -110
/var/log/kern.log:Apr 24 08:46:03 Sinbad kernel: [   47.984039] usb 1-10: device descriptor read/64, error -110
/var/log/kern.log:Apr 24 08:46:03 Sinbad kernel: [   63.200036] usb 1-10: device descriptor read/64, error -110
/var/log/kern.log:Apr 24 08:46:03 Sinbad kernel: [   68.436256] usb 1-10: device descriptor read/8, error -110
/var/log/kern.log:Apr 24 08:46:03 Sinbad kernel: [   73.548124] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Apr 24 08:46:03 Sinbad kernel: [   73.556292] usb 1-10: device descriptor read/8, error -110
/var/log/kern.log:Apr 24 08:46:07 Sinbad kernel: [   78.793155] usb 1-10: device descriptor read/8, error -110
/var/log/kern.log:Apr 24 08:46:12 Sinbad kernel: [   83.912318] usb 1-10: device descriptor read/8, error -110
/var/log/kern.log:Apr 24 08:46:29 Sinbad kernel: [   99.492034] usb 4-2: device descriptor read/64, error -110
/var/log/kern.log:Apr 24 08:46:44 Sinbad kernel: [  114.732035] usb 4-2: device descriptor read/64, error -110
/var/log/kern.log:Apr 24 08:47:00 Sinbad kernel: [  130.108034] usb 4-2: device descriptor read/64, error -110
/var/log/kern.log:Apr 24 08:47:15 Sinbad kernel: [  145.348159] usb 4-2: device descriptor read/64, error -110
/var/log/kern.log:Apr 24 08:47:20 Sinbad kernel: [  150.612569] usb 4-2: device descriptor read/8, error -110
/var/log/kern.log:Apr 24 08:47:25 Sinbad kernel: [  155.732594] usb 4-2: device descriptor read/8, error -110
/var/log/kern.log:Apr 24 08:47:31 Sinbad kernel: [  160.992633] usb 4-2: device descriptor read/8, error -110
/var/log/kern.log:Apr 24 08:47:36 Sinbad kernel: [  166.112659] usb 4-2: device descriptor read/8, error -110
/var/log/kern.log:Apr 24 10:19:43 Sinbad kernel: [   17.432038] usb 1-10: device descriptor read/64, error -110
/var/log/kern.log:Apr 24 10:19:43 Sinbad kernel: [   32.648035] usb 1-10: device descriptor read/64, error -110
/var/log/kern.log:Apr 24 10:19:43 Sinbad kernel: [   47.976038] usb 1-10: device descriptor read/64, error -110
/var/log/kern.log:Apr 24 10:19:43 Sinbad kernel: [   63.192034] usb 1-10: device descriptor read/64, error -110
/var/log/kern.log:Apr 24 10:19:43 Sinbad kernel: [   68.428256] usb 1-10: device descriptor read/8, error -110
/var/log/kern.log:Apr 24 10:19:43 Sinbad kernel: [   73.174115] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Apr 24 10:19:43 Sinbad kernel: [   73.548311] usb 1-10: device descriptor read/8, error -110
/var/log/kern.log:Apr 24 10:19:47 Sinbad kernel: [   78.784256] usb 1-10: device descriptor read/8, error -110
/var/log/kern.log:Apr 24 10:19:52 Sinbad kernel: [   83.904326] usb 1-10: device descriptor read/8, error -110
/var/log/kern.log:Apr 24 10:20:10 Sinbad kernel: [   99.480045] usb 4-2: device descriptor read/64, error -110
/var/log/kern.log:Apr 24 10:20:25 Sinbad kernel: [  114.720047] usb 4-2: device descriptor read/64, error -110
/var/log/kern.log:Apr 24 10:20:40 Sinbad kernel: [  130.096037] usb 4-2: device descriptor read/64, error -110
/var/log/kern.log:Apr 24 10:20:56 Sinbad kernel: [  145.336087] usb 4-2: device descriptor read/64, error -110
/var/log/kern.log:Apr 24 10:21:01 Sinbad kernel: [  150.596384] usb 4-2: device descriptor read/8, error -110
/var/log/kern.log:Apr 24 10:21:06 Sinbad kernel: [  155.716399] usb 4-2: device descriptor read/8, error -110
/var/log/kern.log:Apr 24 10:21:11 Sinbad kernel: [  160.988430] usb 4-2: device descriptor read/8, error -110
/var/log/kern.log:Apr 24 10:21:16 Sinbad kernel: [  166.108442] usb 4-2: device descriptor read/8, error -110
/var/log/kern.log:Apr 24 10:39:03 Sinbad kernel: [ 1232.792069] usb 4-2: device descriptor read/64, error -110
/var/log/kern.log:Apr 24 10:39:18 Sinbad kernel: [ 1248.032119] usb 4-2: device descriptor read/64, error -110
/var/log/kern.log:Apr 24 10:39:34 Sinbad kernel: [ 1263.416058] usb 4-2: device descriptor read/64, error -110
/var/log/kern.log:Apr 24 10:39:49 Sinbad kernel: [ 1278.656094] usb 4-2: device descriptor read/64, error -110
/var/log/kern.log:Apr 24 10:39:54 Sinbad kernel: [ 1283.916783] usb 4-2: device descriptor read/8, error -110
/var/log/kern.log:Apr 24 10:39:59 Sinbad kernel: [ 1289.036761] usb 4-2: device descriptor read/8, error -110
/var/log/kern.log:Apr 24 10:40:05 Sinbad kernel: [ 1294.300762] usb 4-2: device descriptor read/8, error -110
/var/log/kern.log:Apr 24 10:40:10 Sinbad kernel: [ 1299.420775] usb 4-2: device descriptor read/8, error -110
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/syslog:Apr 24 10:19:43 Sinbad kernel: [   17.432038] usb 1-10: device descriptor read/64, error -110
/var/log/syslog:Apr 24 10:19:43 Sinbad kernel: [   32.648035] usb 1-10: device descriptor read/64, error -110
/var/log/syslog:Apr 24 10:19:43 Sinbad kernel: [   47.976038] usb 1-10: device descriptor read/64, error -110
/var/log/syslog:Apr 24 10:19:43 Sinbad kernel: [   63.192034] usb 1-10: device descriptor read/64, error -110
/var/log/syslog:Apr 24 10:19:43 Sinbad kernel: [   68.428256] usb 1-10: device descriptor read/8, error -110
/var/log/syslog:Apr 24 10:19:43 Sinbad kernel: [   73.174115] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
/var/log/syslog:Apr 24 10:19:43 Sinbad kernel: [   73.548311] usb 1-10: device descriptor read/8, error -110
/var/log/syslog:Apr 24 10:19:47 Sinbad kernel: [   78.784256] usb 1-10: device descriptor read/8, error -110
/var/log/syslog:Apr 24 10:19:50 Sinbad NetworkManager[622]: <error> [1398291590.595995] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
/var/log/syslog:Apr 24 10:19:50 Sinbad dnsmasq[985]: warning: no upstream servers configured
/var/log/syslog:Apr 24 10:19:52 Sinbad kernel: [   83.904326] usb 1-10: device descriptor read/8, error -110
/var/log/syslog:Apr 24 10:20:10 Sinbad kernel: [   99.480045] usb 4-2: device descriptor read/64, error -110
/var/log/syslog:Apr 24 10:20:25 Sinbad kernel: [  114.720047] usb 4-2: device descriptor read/64, error -110
/var/log/syslog:Apr 24 10:20:40 Sinbad kernel: [  130.096037] usb 4-2: device descriptor read/64, error -110
/var/log/syslog:Apr 24 10:20:56 Sinbad kernel: [  145.336087] usb 4-2: device descriptor read/64, error -110
/var/log/syslog:Apr 24 10:21:01 Sinbad kernel: [  150.596384] usb 4-2: device descriptor read/8, error -110
/var/log/syslog:Apr 24 10:21:06 Sinbad kernel: [  155.716399] usb 4-2: device descriptor read/8, error -110
/var/log/syslog:Apr 24 10:21:11 Sinbad kernel: [  160.988430] usb 4-2: device descriptor read/8, error -110
/var/log/syslog:Apr 24 10:21:16 Sinbad kernel: [  166.108442] usb 4-2: device descriptor read/8, error -110
/var/log/syslog:Apr 24 10:39:03 Sinbad kernel: [ 1232.792069] usb 4-2: device descriptor read/64, error -110
/var/log/syslog:Apr 24 10:39:18 Sinbad kernel: [ 1248.032119] usb 4-2: device descriptor read/64, error -110
/var/log/syslog:Apr 24 10:39:34 Sinbad kernel: [ 1263.416058] usb 4-2: device descriptor read/64, error -110
/var/log/syslog:Apr 24 10:39:49 Sinbad kernel: [ 1278.656094] usb 4-2: device descriptor read/64, error -110
/var/log/syslog:Apr 24 10:39:54 Sinbad kernel: [ 1283.916783] usb 4-2: device descriptor read/8, error -110
/var/log/syslog:Apr 24 10:39:59 Sinbad kernel: [ 1289.036761] usb 4-2: device descriptor read/8, error -110
/var/log/syslog:Apr 24 10:40:05 Sinbad kernel: [ 1294.300762] usb 4-2: device descriptor read/8, error -110
/var/log/syslog:Apr 24 10:40:10 Sinbad kernel: [ 1299.420775] usb 4-2: device descriptor read/8, error -110
/var/log/Xorg.0.log:    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
/var/log/Xorg.0.log:[    82.523] (WW) Warning, couldn't open module fglrx
/var/log/Xorg.0.log:[    82.538] (WW) Warning, couldn't open module fglrx
```

Which tends to confirm the idea that there is something very unwell with the USBs, but which ones and how to fix?

---

### Post by sitro on 2014-04-24
the result of "sudo lsusb -v" is not complete

---

### Post by sitro on 2014-04-24
in the log, I see you have two problem : one around the USB, that we don't know howto solve for the moment an other around the wireless card (BCM43)

put aside for the moment the problem of the usb and focuse on the wireless card.
You see it there in the short display of lspci :
```

[COLOR=#000000][FONT=Ubuntu Mono]02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)

```
[/FONT][/COLOR]and in the log :
```

/var/log/kern.log:Apr 23 00:47:35 Sinbad kernel: [   71.081329] b43 ssb0:0: Direct firmware load failed with error -2
/var/log/kern.log:Apr 23 00:47:35 Sinbad kernel: [   71.493010] b43 ssb0:0: Direct firmware load failed with error -2
/var/log/kern.log:Apr 23 00:47:36 Sinbad kernel: [   71.588148] b43 ssb0:0: Direct firmware load failed with error -2
/var/log/kern.log:Apr 23 00:47:36 Sinbad kernel: [   71.589603] b43 ssb0:0: Direct firmware load failed with error -2
/var/log/kern.log:Apr 23 00:47:36 Sinbad kernel: [   71.591526] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
/var/log/kern.log:Apr 23 00:47:36 Sinbad kernel: [   71.591528] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
/var/log/kern.log:Apr 23 00:47:36 Sinbad kernel: [   71.591530] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.

```
In the past I had a laptop with this kind of card, and the boot was slow until I install the correct firmware.
So there are many website that explain how-to install the firmware 
The first step is to have the identifier of the card. this is done with the command :
lspci -vvnn |grep -i Network
According to the ID card, you will install the right firmware. 
and the wireless card will work and solve one problem.

---

### Post by Jonathan_Traill on 2014-04-24
Oh, Lord, please not the wireless drivers again.  You have NO IDEA how much blood, sweat and tears have been expended over getting wireless to work.  I thought it was a miracle when I installed 14.04 and wireless started as soon as I selected the ST driver identified on the Preferences.

Still, I'm always happy to mess up my system beyond all recognition - learning through error is my preferred style - so here goes ...

---

### Post by sitro on 2014-04-24
ok, but I'm surprise that your wireless card is working because of the error message in your kernel log ; unless you installed it in the meantime.

So for the USB problem. In your place I'll try this:

have one eye on the clock during the process.
1- shutdown the laptop
2- unplug the power cord
3- unplug the battery
4- wait 5 minutes
5- put the battery in the laptop
6- start the computer
7- watch le last message of syslog and look after the same error message around usb
8- if there is no error message : catch the display of the command lsusb and post it.
9- else if there is the same error message in the last boot :
10- shutdown the computer , wait 20 seconds.
11- plug the power cord and go to step 6 till 8.

---

### Post by Jonathan_Traill on 2014-04-24
Well, I switched off the STA drivers, went to the website and followed the instructions and my wireless is still working, which makes me feel like some sort of genius (Hey!  I can follow instructions!  I can copy and paste!).  That said, not sure this has actually changed anything as still gives us this:

```
/var/log/kern.log:Apr 24 21:41:00 Sinbad kernel: [   17.432036] usb 1-10: device descriptor read/64, error -110/var/log/kern.log:Apr 24 21:41:00 Sinbad kernel: [   32.648035] usb 1-10: device descriptor read/64, error -110
/var/log/kern.log:Apr 24 21:41:00 Sinbad kernel: [   47.976038] usb 1-10: device descriptor read/64, error -110
/var/log/kern.log:Apr 24 21:41:00 Sinbad kernel: [   63.192037] usb 1-10: device descriptor read/64, error -110
/var/log/kern.log:Apr 24 21:41:00 Sinbad kernel: [   68.428335] usb 1-10: device descriptor read/8, error -110
/var/log/kern.log:Apr 24 21:41:00 Sinbad kernel: [   73.203115] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Apr 24 21:41:00 Sinbad kernel: [   73.548248] usb 1-10: device descriptor read/8, error -110
/var/log/kern.log:Apr 24 21:41:04 Sinbad kernel: [   78.785139] usb 1-10: device descriptor read/8, error -110
/var/log/kern.log:Apr 24 21:41:09 Sinbad kernel: [   83.904261] usb 1-10: device descriptor read/8, error -110
/var/log/kern.log:Apr 24 21:41:25 Sinbad kernel: [   99.460068] usb 4-2: device descriptor read/64, error -110
/var/log/kern.log:Apr 24 21:41:40 Sinbad kernel: [  114.700074] usb 4-2: device descriptor read/64, error -110
/var/log/kern.log:Apr 24 21:41:56 Sinbad kernel: [  130.076117] usb 4-2: device descriptor read/64, error -110
/var/log/kern.log:Apr 24 21:42:11 Sinbad kernel: [  145.328071] usb 4-2: device descriptor read/64, error -110
/var/log/kern.log:Apr 24 21:42:16 Sinbad kernel: [  150.596328] usb 4-2: device descriptor read/8, error -110
/var/log/kern.log:Apr 24 21:42:21 Sinbad kernel: [  155.716343] usb 4-2: device descriptor read/8, error -110
/var/log/kern.log:Apr 24 21:42:27 Sinbad kernel: [  160.976363] usb 4-2: device descriptor read/8, error -110
/var/log/kern.log:Apr 24 21:42:32 Sinbad kernel: [  166.096362] usb 4-2: device descriptor read/8, error -110
/var/log/kern.log:Apr 24 21:49:28 Sinbad kernel: [   17.440036] usb 1-10: device descriptor read/64, error -110
/var/log/kern.log:Apr 24 21:49:28 Sinbad kernel: [   32.656035] usb 1-10: device descriptor read/64, error -110
/var/log/kern.log:Apr 24 21:49:28 Sinbad kernel: [   47.984039] usb 1-10: device descriptor read/64, error -110
/var/log/kern.log:Apr 24 21:49:28 Sinbad kernel: [   63.200036] usb 1-10: device descriptor read/64, error -110
/var/log/kern.log:Apr 24 21:49:28 Sinbad kernel: [   68.436237] usb 1-10: device descriptor read/8, error -110
/var/log/kern.log:Apr 24 21:49:28 Sinbad kernel: [   72.916847] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Apr 24 21:49:28 Sinbad kernel: [   73.556293] usb 1-10: device descriptor read/8, error -110
**/var/log/kern.log:Apr 24 21:49:28 Sinbad kernel: [   75.533987] b43 ssb0:0: Direct firmware load failed with error -2**
**/var/log/kern.log:Apr 24 21:49:30 Sinbad kernel: [   76.957900] b43 ssb0:0: Direct firmware load failed with error -2**
**/var/log/kern.log:Apr 24 21:49:30 Sinbad kernel: [   77.109822] b43 ssb0:0: Direct firmware load failed with error -2**
**/var/log/kern.log:Apr 24 21:49:30 Sinbad kernel: [   77.139503] b43 ssb0:0: Direct firmware load failed with error -2**
**/var/log/kern.log:Apr 24 21:49:30 Sinbad kernel: [   77.157178] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found**
**/var/log/kern.log:Apr 24 21:49:30 Sinbad kernel: [   77.157293] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found**
**/var/log/kern.log:Apr 24 21:49:30 Sinbad kernel: [   77.157400] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.**
/var/log/kern.log:Apr 24 21:49:32 Sinbad kernel: [   78.804243] usb 1-10: device descriptor read/8, error -110
/var/log/kern.log:Apr 24 21:49:37 Sinbad kernel: [   83.924312] usb 1-10: device descriptor read/8, error -110
/var/log/kern.log:Apr 24 21:49:52 Sinbad kernel: [   99.468070] usb 4-2: device descriptor read/64, error -110
/var/log/kern.log:Apr 24 21:50:07 Sinbad kernel: [  114.708040] usb 4-2: device descriptor read/64, error -110
/var/log/kern.log:Apr 24 21:50:24 Sinbad kernel: [  130.084058] usb 4-2: device descriptor read/64, error -110
/var/log/kern.log:Apr 24 21:50:39 Sinbad kernel: [  145.324120] usb 4-2: device descriptor read/64, error -110
/var/log/kern.log:Apr 24 21:50:44 Sinbad kernel: [  150.596286] usb 4-2: device descriptor read/8, error -110
/var/log/kern.log:Apr 24 21:50:49 Sinbad kernel: [  155.716297] usb 4-2: device descriptor read/8, error -110
/var/log/kern.log:Apr 24 21:50:54 Sinbad kernel: [  160.980310] usb 4-2: device descriptor read/8, error -110
/var/log/kern.log:Apr 24 21:51:00 Sinbad kernel: [  166.100318] usb 4-2: device descriptor read/8, error -110
/var/log/kern.log:Apr 24 22:12:05 Sinbad kernel: [   17.440038] usb 1-10: device descriptor read/64, error -110
/var/log/kern.log:Apr 24 22:12:05 Sinbad kernel: [   32.656035] usb 1-10: device descriptor read/64, error -110
/var/log/kern.log:Apr 24 22:12:05 Sinbad kernel: [   47.984036] usb 1-10: device descriptor read/64, error -110
/var/log/kern.log:Apr 24 22:12:05 Sinbad kernel: [   63.200031] usb 1-10: device descriptor read/64, error -110
/var/log/kern.log:Apr 24 22:12:05 Sinbad kernel: [   68.436319] usb 1-10: device descriptor read/8, error -110
/var/log/kern.log:Apr 24 22:12:05 Sinbad kernel: [   72.661422] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Apr 24 22:12:05 Sinbad kernel: [   73.556248] usb 1-10: device descriptor read/8, error -110
/var/log/kern.log:Apr 24 22:12:09 Sinbad kernel: [   78.792401] usb 1-10: device descriptor read/8, error -110
/var/log/kern.log:Apr 24 22:12:14 Sinbad kernel: [   83.912262] usb 1-10: device descriptor read/8, error -110
/var/log/kern.log:Apr 24 22:12:29 Sinbad kernel: [   99.480048] usb 4-2: device descriptor read/64, error -110
/var/log/kern.log:Apr 24 22:12:45 Sinbad kernel: [  114.724128] usb 4-2: device descriptor read/64, error -110
/var/log/kern.log:Apr 24 22:12:59 Sinbad kernel: [  129.112069] usb 4-2: device descriptor read/64, error -110
/var/log/kern.log:Apr 24 22:13:14 Sinbad kernel: [  144.352092] usb 4-2: device descriptor read/64, error -110
/var/log/kern.log:Apr 24 22:13:19 Sinbad kernel: [  149.624857] usb 4-2: device descriptor read/8, error -110
/var/log/kern.log:Apr 24 22:13:25 Sinbad kernel: [  154.744314] usb 4-2: device descriptor read/8, error -110
/var/log/kern.log:Apr 24 22:13:30 Sinbad kernel: [  160.004689] usb 4-2: device descriptor read/8, error -110
/var/log/kern.log:Apr 24 22:13:35 Sinbad kernel: [  165.124134] usb 4-2: device descriptor read/8, error -110
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/pm-powersave.log:sh: echo: I/O error
/var/log/syslog:Apr 24 10:19:43 Sinbad kernel: [   17.432038] usb 1-10: device descriptor read/64, error -110
/var/log/syslog:Apr 24 10:19:43 Sinbad kernel: [   32.648035] usb 1-10: device descriptor read/64, error -110
/var/log/syslog:Apr 24 10:19:43 Sinbad kernel: [   47.976038] usb 1-10: device descriptor read/64, error -110
/var/log/syslog:Apr 24 10:19:43 Sinbad kernel: [   63.192034] usb 1-10: device descriptor read/64, error -110
/var/log/syslog:Apr 24 10:19:43 Sinbad kernel: [   68.428256] usb 1-10: device descriptor read/8, error -110
/var/log/syslog:Apr 24 10:19:43 Sinbad kernel: [   73.174115] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
/var/log/syslog:Apr 24 10:19:43 Sinbad kernel: [   73.548311] usb 1-10: device descriptor read/8, error -110
/var/log/syslog:Apr 24 10:19:47 Sinbad kernel: [   78.784256] usb 1-10: device descriptor read/8, error -110
/var/log/syslog:Apr 24 10:19:50 Sinbad NetworkManager[622]: <error> [1398291590.595995] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
/var/log/syslog:Apr 24 10:19:50 Sinbad dnsmasq[985]: warning: no upstream servers configured
/var/log/syslog:Apr 24 10:19:52 Sinbad kernel: [   83.904326] usb 1-10: device descriptor read/8, error -110
/var/log/syslog:Apr 24 10:20:10 Sinbad kernel: [   99.480045] usb 4-2: device descriptor read/64, error -110
/var/log/syslog:Apr 24 10:20:25 Sinbad kernel: [  114.720047] usb 4-2: device descriptor read/64, error -110
/var/log/syslog:Apr 24 10:20:40 Sinbad kernel: [  130.096037] usb 4-2: device descriptor read/64, error -110
/var/log/syslog:Apr 24 10:20:56 Sinbad kernel: [  145.336087] usb 4-2: device descriptor read/64, error -110
/var/log/syslog:Apr 24 10:21:01 Sinbad kernel: [  150.596384] usb 4-2: device descriptor read/8, error -110
/var/log/syslog:Apr 24 10:21:06 Sinbad kernel: [  155.716399] usb 4-2: device descriptor read/8, error -110
/var/log/syslog:Apr 24 10:21:11 Sinbad kernel: [  160.988430] usb 4-2: device descriptor read/8, error -110
/var/log/syslog:Apr 24 10:21:16 Sinbad kernel: [  166.108442] usb 4-2: device descriptor read/8, error -110
/var/log/syslog:Apr 24 10:39:03 Sinbad kernel: [ 1232.792069] usb 4-2: device descriptor read/64, error -110
/var/log/syslog:Apr 24 10:39:18 Sinbad kernel: [ 1248.032119] usb 4-2: device descriptor read/64, error -110
/var/log/syslog:Apr 24 10:39:34 Sinbad kernel: [ 1263.416058] usb 4-2: device descriptor read/64, error -110
/var/log/syslog:Apr 24 10:39:49 Sinbad kernel: [ 1278.656094] usb 4-2: device descriptor read/64, error -110
/var/log/syslog:Apr 24 10:39:54 Sinbad kernel: [ 1283.916783] usb 4-2: device descriptor read/8, error -110
/var/log/syslog:Apr 24 10:39:59 Sinbad kernel: [ 1289.036761] usb 4-2: device descriptor read/8, error -110
/var/log/syslog:Apr 24 10:40:05 Sinbad kernel: [ 1294.300762] usb 4-2: device descriptor read/8, error -110
/var/log/syslog:Apr 24 10:40:10 Sinbad kernel: [ 1299.420775] usb 4-2: device descriptor read/8, error -110
/var/log/syslog:Apr 24 12:06:44 Sinbad kernel: [   17.444036] usb 1-10: device descriptor read/64, error -110
/var/log/syslog:Apr 24 12:06:44 Sinbad kernel: [   32.660033] usb 1-10: device descriptor read/64, error -110
/var/log/syslog:Apr 24 12:06:44 Sinbad kernel: [   47.988038] usb 1-10: device descriptor read/64, error -110
/var/log/syslog:Apr 24 12:06:44 Sinbad kernel: [   63.204033] usb 1-10: device descriptor read/64, error -110
/var/log/syslog:Apr 24 12:06:44 Sinbad kernel: [   68.440256] usb 1-10: device descriptor read/8, error -110
/var/log/syslog:Apr 24 12:06:44 Sinbad kernel: [   73.418335] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
/var/log/syslog:Apr 24 12:06:44 Sinbad kernel: [   73.560300] usb 1-10: device descriptor read/8, error -110
/var/log/syslog:Apr 24 12:06:48 Sinbad kernel: [   78.796273] usb 1-10: device descriptor read/8, error -110
/var/log/syslog:Apr 24 12:06:51 Sinbad NetworkManager[715]: <error> [1398298011.558101] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
/var/log/syslog:Apr 24 12:06:51 Sinbad dnsmasq[1086]: warning: no upstream servers configured
/var/log/syslog:Apr 24 12:06:53 Sinbad kernel: [   83.916315] usb 1-10: device descriptor read/8, error -110
/var/log/syslog:Apr 24 12:07:08 Sinbad kernel: [   99.476060] usb 4-2: device descriptor read/64, error -110
/var/log/syslog:Apr 24 12:07:23 Sinbad kernel: [  114.716064] usb 4-2: device descriptor read/64, error -110
/var/log/syslog:Apr 24 12:07:39 Sinbad kernel: [  130.096089] usb 4-2: device descriptor read/64, error -110
/var/log/syslog:Apr 24 12:07:54 Sinbad kernel: [  145.336096] usb 4-2: device descriptor read/64, error -110
/var/log/syslog:Apr 24 12:07:59 Sinbad kernel: [  150.596778] usb 4-2: device descriptor read/8, error -110
/var/log/syslog:Apr 24 12:08:04 Sinbad kernel: [  155.716349] usb 4-2: device descriptor read/8, error -110
/var/log/syslog:Apr 24 12:08:10 Sinbad kernel: [  160.976995] usb 4-2: device descriptor read/8, error -110
/var/log/syslog:Apr 24 12:08:15 Sinbad kernel: [  166.096574] usb 4-2: device descriptor read/8, error -110
/var/log/syslog:Apr 24 13:23:14 Sinbad kernel: [   17.440036] usb 1-10: device descriptor read/64, error -110
/var/log/syslog:Apr 24 13:23:14 Sinbad kernel: [   32.656033] usb 1-10: device descriptor read/64, error -110
/var/log/syslog:Apr 24 13:23:14 Sinbad kernel: [   47.984039] usb 1-10: device descriptor read/64, error -110
/var/log/syslog:Apr 24 13:23:14 Sinbad kernel: [   63.200036] usb 1-10: device descriptor read/64, error -110
/var/log/syslog:Apr 24 13:23:14 Sinbad kernel: [   68.436383] usb 1-10: device descriptor read/8, error -110
/var/log/syslog:Apr 24 13:23:14 Sinbad kernel: [   72.790284] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
/var/log/syslog:Apr 24 13:23:14 Sinbad kernel: [   73.556296] usb 1-10: device descriptor read/8, error -110
/var/log/syslog:Apr 24 13:23:18 Sinbad kernel: [   78.796369] usb 1-10: device descriptor read/8, error -110
/var/log/syslog:Apr 24 13:23:21 Sinbad NetworkManager[659]: <error> [1398302601.208709] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
/var/log/syslog:Apr 24 13:23:21 Sinbad dnsmasq[1079]: warning: no upstream servers configured
/var/log/syslog:Apr 24 13:23:23 Sinbad kernel: [   83.916193] usb 1-10: device descriptor read/8, error -110
/var/log/syslog:Apr 24 13:23:38 Sinbad kernel: [   99.460050] usb 4-2: device descriptor read/64, error -110
/var/log/syslog:Apr 24 13:23:53 Sinbad kernel: [  114.700062] usb 4-2: device descriptor read/64, error -110
/var/log/syslog:Apr 24 13:24:09 Sinbad kernel: [  130.088066] usb 4-2: device descriptor read/64, error -110
/var/log/syslog:Apr 24 13:24:24 Sinbad kernel: [  145.332326] usb 4-2: device descriptor read/64, error -110
/var/log/syslog:Apr 24 13:24:29 Sinbad kernel: [  150.596779] usb 4-2: device descriptor read/8, error -110
/var/log/syslog:Apr 24 13:24:34 Sinbad kernel: [  155.717342] usb 4-2: device descriptor read/8, error -110
/var/log/syslog:Apr 24 13:24:40 Sinbad kernel: [  160.989010] usb 4-2: device descriptor read/8, error -110
/var/log/syslog:Apr 24 13:24:45 Sinbad kernel: [  166.108583] usb 4-2: device descriptor read/8, error -110
/var/log/syslog:Apr 24 14:11:38 Sinbad kernel: [   17.444038] usb 1-10: device descriptor read/64, error -110
/var/log/syslog:Apr 24 14:11:38 Sinbad kernel: [   32.660035] usb 1-10: device descriptor read/64, error -110
/var/log/syslog:Apr 24 14:11:38 Sinbad kernel: [   47.988038] usb 1-10: device descriptor read/64, error -110
/var/log/syslog:Apr 24 14:11:38 Sinbad kernel: [   63.204036] usb 1-10: device descriptor read/64, error -110
/var/log/syslog:Apr 24 14:11:38 Sinbad kernel: [   68.440226] usb 1-10: device descriptor read/8, error -110
/var/log/syslog:Apr 24 14:11:38 Sinbad kernel: [   73.219890] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
/var/log/syslog:Apr 24 14:11:38 Sinbad kernel: [   73.560280] usb 1-10: device descriptor read/8, error -110
/var/log/syslog:Apr 24 14:11:42 Sinbad kernel: [   78.820245] usb 1-10: device descriptor read/8, error -110
/var/log/syslog:Apr 24 14:11:45 Sinbad NetworkManager[724]: <error> [1398305505.249616] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
/var/log/syslog:Apr 24 14:11:45 Sinbad dnsmasq[1087]: warning: no upstream servers configured
/var/log/syslog:Apr 24 14:11:47 Sinbad kernel: [   83.940308] usb 1-10: device descriptor read/8, error -110
/var/log/syslog:Apr 24 14:12:03 Sinbad kernel: [   99.480034] usb 4-2: device descriptor read/64, error -110
/var/log/syslog:Apr 24 14:12:18 Sinbad kernel: [  114.720040] usb 4-2: device descriptor read/64, error -110
/var/log/syslog:Apr 24 14:12:33 Sinbad kernel: [  130.096035] usb 4-2: device descriptor read/64, error -110
/var/log/syslog:Apr 24 14:12:49 Sinbad kernel: [  145.336098] usb 4-2: device descriptor read/64, error -110
/var/log/syslog:Apr 24 14:12:54 Sinbad kernel: [  150.596379] usb 4-2: device descriptor read/8, error -110
/var/log/syslog:Apr 24 14:12:59 Sinbad kernel: [  155.716390] usb 4-2: device descriptor read/8, error -110
/var/log/syslog:Apr 24 14:13:04 Sinbad kernel: [  160.976414] usb 4-2: device descriptor read/8, error -110
/var/log/syslog:Apr 24 14:13:09 Sinbad kernel: [  166.096431] usb 4-2: device descriptor read/8, error -110
/var/log/syslog:Apr 24 15:29:00 Sinbad kernel: [   17.436039] usb 1-10: device descriptor read/64, error -110
/var/log/syslog:Apr 24 15:29:00 Sinbad kernel: [   32.652035] usb 1-10: device descriptor read/64, error -110
/var/log/syslog:Apr 24 15:29:00 Sinbad kernel: [   47.980038] usb 1-10: device descriptor read/64, error -110
/var/log/syslog:Apr 24 15:29:00 Sinbad kernel: [   63.196036] usb 1-10: device descriptor read/64, error -110
/var/log/syslog:Apr 24 15:29:00 Sinbad kernel: [   68.432255] usb 1-10: device descriptor read/8, error -110
/var/log/syslog:Apr 24 15:29:00 Sinbad kernel: [   73.465532] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
/var/log/syslog:Apr 24 15:29:00 Sinbad kernel: [   73.552295] usb 1-10: device descriptor read/8, error -110
/var/log/syslog:Apr 24 15:29:04 Sinbad kernel: [   78.788241] usb 1-10: device descriptor read/8, error -110
/var/log/syslog:Apr 24 15:29:06 Sinbad NetworkManager[683]: <error> [1398310146.653597] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
/var/log/syslog:Apr 24 15:29:06 Sinbad dnsmasq[1094]: warning: no upstream servers configured
/var/log/syslog:Apr 24 15:29:09 Sinbad kernel: [   83.908193] usb 1-10: device descriptor read/8, error -110
/var/log/syslog:Apr 24 15:29:26 Sinbad kernel: [   99.424035] usb 4-2: device descriptor read/64, error -110
/var/log/syslog:Apr 24 15:29:42 Sinbad kernel: [  114.664048] usb 4-2: device descriptor read/64, error -110
/var/log/syslog:Apr 24 15:29:57 Sinbad kernel: [  130.044073] usb 4-2: device descriptor read/64, error -110
/var/log/syslog:Apr 24 15:30:12 Sinbad kernel: [  145.284071] usb 4-2: device descriptor read/64, error -110
/var/log/syslog:Apr 24 15:30:18 Sinbad kernel: [  150.552361] usb 4-2: device descriptor read/8, error -110
/var/log/syslog:Apr 24 15:30:23 Sinbad kernel: [  155.672400] usb 4-2: device descriptor read/8, error -110
/var/log/syslog:Apr 24 15:30:28 Sinbad kernel: [  160.932396] usb 4-2: device descriptor read/8, error -110
/var/log/syslog:Apr 24 15:30:33 Sinbad kernel: [  166.052436] usb 4-2: device descriptor read/8, error -110
/var/log/syslog:Apr 24 16:02:50 Sinbad kernel: [   17.432038] usb 1-10: device descriptor read/64, error -110
/var/log/syslog:Apr 24 16:02:50 Sinbad kernel: [   32.648035] usb 1-10: device descriptor read/64, error -110
/var/log/syslog:Apr 24 16:02:50 Sinbad kernel: [   47.976038] usb 1-10: device descriptor read/64, error -110
/var/log/syslog:Apr 24 16:02:50 Sinbad kernel: [   63.192032] usb 1-10: device descriptor read/64, error -110
/var/log/syslog:Apr 24 16:02:50 Sinbad kernel: [   68.428233] usb 1-10: device descriptor read/8, error -110
/var/log/syslog:Apr 24 16:02:50 Sinbad kernel: [   72.845578] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
/var/log/syslog:Apr 24 16:02:50 Sinbad kernel: [   73.548288] usb 1-10: device descriptor read/8, error -110
/var/log/syslog:Apr 24 16:02:54 Sinbad kernel: [   78.784233] usb 1-10: device descriptor read/8, error -110
/var/log/syslog:Apr 24 16:02:57 Sinbad NetworkManager[692]: <error> [1398312177.207403] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
/var/log/syslog:Apr 24 16:02:57 Sinbad dnsmasq[1083]: warning: no upstream servers configured
/var/log/syslog:Apr 24 16:02:59 Sinbad kernel: [   83.904303] usb 1-10: device descriptor read/8, error -110
/var/log/syslog:Apr 24 16:03:17 Sinbad kernel: [   99.480067] usb 4-2: device descriptor read/64, error -110
/var/log/syslog:Apr 24 16:03:32 Sinbad kernel: [  114.720130] usb 4-2: device descriptor read/64, error -110
/var/log/syslog:Apr 24 16:03:47 Sinbad kernel: [  130.100036] usb 4-2: device descriptor read/64, error -110
/var/log/syslog:Apr 24 16:04:03 Sinbad kernel: [  145.340125] usb 4-2: device descriptor read/64, error -110
/var/log/syslog:Apr 24 16:04:08 Sinbad kernel: [  150.600375] usb 4-2: device descriptor read/8, error -110
/var/log/syslog:Apr 24 16:04:13 Sinbad kernel: [  155.720396] usb 4-2: device descriptor read/8, error -110
/var/log/syslog:Apr 24 16:04:18 Sinbad kernel: [  160.980420] usb 4-2: device descriptor read/8, error -110
/var/log/syslog:Apr 24 16:04:23 Sinbad kernel: [  166.100430] usb 4-2: device descriptor read/8, error -110
/var/log/syslog:Apr 24 19:21:40 Sinbad kernel: [   17.436038] usb 1-10: device descriptor read/64, error -110
/var/log/syslog:Apr 24 19:21:40 Sinbad kernel: [   32.652035] usb 1-10: device descriptor read/64, error -110
/var/log/syslog:Apr 24 19:21:40 Sinbad kernel: [   47.980038] usb 1-10: device descriptor read/64, error -110
/var/log/syslog:Apr 24 19:21:40 Sinbad kernel: [   63.196036] usb 1-10: device descriptor read/64, error -110
/var/log/syslog:Apr 24 19:21:40 Sinbad kernel: [   68.432239] usb 1-10: device descriptor read/8, error -110
/var/log/syslog:Apr 24 19:21:40 Sinbad kernel: [   73.552115] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
/var/log/syslog:Apr 24 19:21:40 Sinbad kernel: [   73.552291] usb 1-10: device descriptor read/8, error -110
/var/log/syslog:Apr 24 19:21:44 Sinbad kernel: [   78.788245] usb 1-10: device descriptor read/8, error -110
/var/log/syslog:Apr 24 19:21:47 Sinbad NetworkManager[696]: <error> [1398324107.190046] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
/var/log/syslog:Apr 24 19:21:47 Sinbad dnsmasq[1077]: warning: no upstream servers configured
/var/log/syslog:Apr 24 19:21:49 Sinbad kernel: [   83.908307] usb 1-10: device descriptor read/8, error -110
/var/log/syslog:Apr 24 19:22:04 Sinbad kernel: [   99.472042] usb 4-2: device descriptor read/64, error -110
/var/log/syslog:Apr 24 19:22:19 Sinbad kernel: [  114.712052] usb 4-2: device descriptor read/64, error -110
/var/log/syslog:Apr 24 19:22:35 Sinbad kernel: [  130.092057] usb 4-2: device descriptor read/64, error -110
/var/log/syslog:Apr 24 19:22:47 Sinbad kernel: [  141.788111] usb 4-2: device descriptor read/64, error -62
/var/log/syslog:Apr 24 19:22:52 Sinbad kernel: [  147.048983] usb 4-2: device descriptor read/8, error -110
/var/log/syslog:Apr 24 19:22:57 Sinbad kernel: [  152.168558] usb 4-2: device descriptor read/8, error -110
/var/log/syslog:Apr 24 19:23:02 Sinbad kernel: [  157.428199] usb 4-2: device descriptor read/8, error -110
/var/log/syslog:Apr 24 19:23:07 Sinbad kernel: [  162.548775] usb 4-2: device descriptor read/8, error -110
/var/log/syslog:Apr 24 19:48:59 Sinbad kernel: [ 1713.800082] usb 1-10: device descriptor read/64, error -110
/var/log/syslog:Apr 24 19:49:14 Sinbad kernel: [ 1729.016084] usb 1-10: device descriptor read/64, error -110
/var/log/syslog:Apr 24 19:49:29 Sinbad kernel: [ 1744.344106] usb 1-10: device descriptor read/64, error -110
/var/log/syslog:Apr 24 19:49:45 Sinbad kernel: [ 1759.560082] usb 1-10: device descriptor read/64, error -110
/var/log/syslog:Apr 24 19:49:50 Sinbad kernel: [ 1764.796273] usb 1-10: device descriptor read/8, error -110
/var/log/syslog:Apr 24 19:49:55 Sinbad kernel: [ 1769.916257] usb 1-10: device descriptor read/8, error -110
/var/log/syslog:Apr 24 19:50:00 Sinbad kernel: [ 1775.152252] usb 1-10: device descriptor read/8, error -110
/var/log/syslog:Apr 24 19:50:05 Sinbad kernel: [ 1780.272231] usb 1-10: device descriptor read/8, error -110
/var/log/syslog:Apr 24 19:50:21 Sinbad kernel: [ 1795.788095] usb 4-2: device descriptor read/64, error -110
/var/log/syslog:Apr 24 19:50:36 Sinbad kernel: [ 1811.028206] usb 4-2: device descriptor read/64, error -110
/var/log/syslog:Apr 24 19:50:51 Sinbad kernel: [ 1826.404069] usb 4-2: device descriptor read/64, error -110
/var/log/syslog:Apr 24 19:51:07 Sinbad kernel: [ 1841.644137] usb 4-2: device descriptor read/64, error -110
/var/log/syslog:Apr 24 19:51:12 Sinbad kernel: [ 1846.904925] usb 4-2: device descriptor read/8, error -110
/var/log/syslog:Apr 24 19:51:17 Sinbad kernel: [ 1852.024866] usb 4-2: device descriptor read/8, error -110
/var/log/syslog:Apr 24 19:51:22 Sinbad kernel: [ 1857.284790] usb 4-2: device descriptor read/8, error -110
/var/log/syslog:Apr 24 19:51:27 Sinbad kernel: [ 1862.404707] usb 4-2: device descriptor read/8, error -110
/var/log/syslog:Apr 24 20:06:49 Sinbad kernel: [   17.440035] usb 1-10: device descriptor read/64, error -110
/var/log/syslog:Apr 24 20:06:49 Sinbad kernel: [   32.656035] usb 1-10: device descriptor read/64, error -110
/var/log/syslog:Apr 24 20:06:49 Sinbad kernel: [   47.984035] usb 1-10: device descriptor read/64, error -110
/var/log/syslog:Apr 24 20:06:49 Sinbad kernel: [   63.200036] usb 1-10: device descriptor read/64, error -110
/var/log/syslog:Apr 24 20:06:49 Sinbad kernel: [   68.436248] usb 1-10: device descriptor read/8, error -110
/var/log/syslog:Apr 24 20:06:49 Sinbad kernel: [   72.813339] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
/var/log/syslog:Apr 24 20:06:49 Sinbad kernel: [   73.556285] usb 1-10: device descriptor read/8, error -110
/var/log/syslog:Apr 24 20:06:53 Sinbad kernel: [   78.792232] usb 1-10: device descriptor read/8, error -110
/var/log/syslog:Apr 24 20:06:56 Sinbad NetworkManager[710]: <error> [1398326816.538085] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
/var/log/syslog:Apr 24 20:06:56 Sinbad dnsmasq[1081]: warning: no upstream servers configured
/var/log/syslog:Apr 24 20:06:58 Sinbad kernel: [   83.912303] usb 1-10: device descriptor read/8, error -110
/var/log/syslog:Apr 24 20:07:16 Sinbad kernel: [   99.484129] usb 4-2: device descriptor read/64, error -110
/var/log/syslog:Apr 24 20:07:31 Sinbad kernel: [  114.728104] usb 4-2: device descriptor read/64, error -110
/var/log/syslog:Apr 24 20:07:47 Sinbad kernel: [  130.112073] usb 4-2: device descriptor read/64, error -110
/var/log/syslog:Apr 24 20:08:02 Sinbad kernel: [  145.364075] usb 4-2: device descriptor read/64, error -110
/var/log/syslog:Apr 24 20:08:07 Sinbad kernel: [  150.628324] usb 4-2: device descriptor read/8, error -110
/var/log/syslog:Apr 24 20:08:12 Sinbad kernel: [  155.748340] usb 4-2: device descriptor read/8, error -110
/var/log/syslog:Apr 24 20:08:18 Sinbad kernel: [  161.009381] usb 4-2: device descriptor read/8, error -110
/var/log/syslog:Apr 24 20:08:23 Sinbad kernel: [  166.128454] usb 4-2: device descriptor read/8, error -110
/var/log/syslog:Apr 24 21:41:00 Sinbad kernel: [   17.432036] usb 1-10: device descriptor read/64, error -110
/var/log/syslog:Apr 24 21:41:00 Sinbad kernel: [   32.648035] usb 1-10: device descriptor read/64, error -110
/var/log/syslog:Apr 24 21:41:00 Sinbad kernel: [   47.976038] usb 1-10: device descriptor read/64, error -110
/var/log/syslog:Apr 24 21:41:00 Sinbad kernel: [   63.192037] usb 1-10: device descriptor read/64, error -110
/var/log/syslog:Apr 24 21:41:00 Sinbad kernel: [   68.428335] usb 1-10: device descriptor read/8, error -110
/var/log/syslog:Apr 24 21:41:00 Sinbad kernel: [   73.203115] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
/var/log/syslog:Apr 24 21:41:00 Sinbad kernel: [   73.548248] usb 1-10: device descriptor read/8, error -110
/var/log/syslog:Apr 24 21:41:04 Sinbad kernel: [   78.785139] usb 1-10: device descriptor read/8, error -110
/var/log/syslog:Apr 24 21:41:07 Sinbad NetworkManager[697]: <error> [1398332467.194359] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
/var/log/syslog:Apr 24 21:41:07 Sinbad dnsmasq[1078]: warning: no upstream servers configured
/var/log/syslog:Apr 24 21:41:09 Sinbad kernel: [   83.904261] usb 1-10: device descriptor read/8, error -110
/var/log/syslog:Apr 24 21:41:25 Sinbad kernel: [   99.460068] usb 4-2: device descriptor read/64, error -110
/var/log/syslog:Apr 24 21:41:40 Sinbad kernel: [  114.700074] usb 4-2: device descriptor read/64, error -110
/var/log/syslog:Apr 24 21:41:56 Sinbad kernel: [  130.076117] usb 4-2: device descriptor read/64, error -110
/var/log/syslog:Apr 24 21:42:11 Sinbad kernel: [  145.328071] usb 4-2: device descriptor read/64, error -110
/var/log/syslog:Apr 24 21:42:16 Sinbad kernel: [  150.596328] usb 4-2: device descriptor read/8, error -110
/var/log/syslog:Apr 24 21:42:21 Sinbad kernel: [  155.716343] usb 4-2: device descriptor read/8, error -110
/var/log/syslog:Apr 24 21:42:27 Sinbad kernel: [  160.976363] usb 4-2: device descriptor read/8, error -110
/var/log/syslog:Apr 24 21:42:32 Sinbad kernel: [  166.096362] usb 4-2: device descriptor read/8, error -110
/var/log/syslog:Apr 24 21:49:28 Sinbad kernel: [   17.440036] usb 1-10: device descriptor read/64, error -110
/var/log/syslog:Apr 24 21:49:28 Sinbad kernel: [   32.656035] usb 1-10: device descriptor read/64, error -110
/var/log/syslog:Apr 24 21:49:28 Sinbad kernel: [   47.984039] usb 1-10: device descriptor read/64, error -110
/var/log/syslog:Apr 24 21:49:28 Sinbad kernel: [   63.200036] usb 1-10: device descriptor read/64, error -110
/var/log/syslog:Apr 24 21:49:28 Sinbad kernel: [   68.436237] usb 1-10: device descriptor read/8, error -110
/var/log/syslog:Apr 24 21:49:28 Sinbad kernel: [   72.916847] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
/var/log/syslog:Apr 24 21:49:28 Sinbad kernel: [   73.556293] usb 1-10: device descriptor read/8, error -110
**/var/log/syslog:Apr 24 21:49:28 Sinbad kernel: [   75.533987] b43 ssb0:0: Direct firmware load failed with error -2**
**/var/log/syslog:Apr 24 21:49:30 Sinbad kernel: [   76.957900] b43 ssb0:0: Direct firmware load failed with error -2**
**/var/log/syslog:Apr 24 21:49:30 Sinbad kernel: [   77.109822] b43 ssb0:0: Direct firmware load failed with error -2**
**/var/log/syslog:Apr 24 21:49:30 Sinbad kernel: [   77.139503] b43 ssb0:0: Direct firmware load failed with error -2**
**/var/log/syslog:Apr 24 21:49:30 Sinbad kernel: [   77.157178] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found**
**/var/log/syslog:Apr 24 21:49:30 Sinbad kernel: [   77.157293] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found**
**/var/log/syslog:Apr 24 21:49:30 Sinbad kernel: [   77.157400] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.**
/var/log/syslog:Apr 24 21:49:32 Sinbad kernel: [   78.804243] usb 1-10: device descriptor read/8, error -110
/var/log/syslog:Apr 24 21:49:37 Sinbad kernel: [   83.924312] usb 1-10: device descriptor read/8, error -110
/var/log/syslog:Apr 24 21:49:52 Sinbad kernel: [   99.468070] usb 4-2: device descriptor read/64, error -110
/var/log/syslog:Apr 24 21:50:07 Sinbad NetworkManager[669]: <error> [1398333007.177136] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
/var/log/syslog:Apr 24 21:50:07 Sinbad dnsmasq[1419]: warning: no upstream servers configured
/var/log/syslog:Apr 24 21:50:07 Sinbad kernel: [  114.708040] usb 4-2: device descriptor read/64, error -110
/var/log/syslog:Apr 24 21:50:24 Sinbad kernel: [  130.084058] usb 4-2: device descriptor read/64, error -110
/var/log/syslog:Apr 24 21:50:39 Sinbad kernel: [  145.324120] usb 4-2: device descriptor read/64, error -110
/var/log/syslog:Apr 24 21:50:44 Sinbad kernel: [  150.596286] usb 4-2: device descriptor read/8, error -110
/var/log/syslog:Apr 24 21:50:49 Sinbad kernel: [  155.716297] usb 4-2: device descriptor read/8, error -110
/var/log/syslog:Apr 24 21:50:54 Sinbad kernel: [  160.980310] usb 4-2: device descriptor read/8, error -110
/var/log/syslog:Apr 24 21:51:00 Sinbad kernel: [  166.100318] usb 4-2: device descriptor read/8, error -110
/var/log/syslog:Apr 24 22:07:02 Sinbad NetworkManager[669]: <error> [1398334022.302611] [nm-system.c:768] nm_system_iface_get_flags(): (unknown): failed to get interface link object
/var/log/syslog:Apr 24 22:07:02 Sinbad NetworkManager[669]: <error> [1398334022.329826] [nm-system.c:768] nm_system_iface_get_flags(): (unknown): failed to get interface link object
/var/log/syslog:Apr 24 22:12:05 Sinbad kernel: [   17.440038] usb 1-10: device descriptor read/64, error -110
/var/log/syslog:Apr 24 22:12:05 Sinbad kernel: [   32.656035] usb 1-10: device descriptor read/64, error -110
/var/log/syslog:Apr 24 22:12:05 Sinbad kernel: [   47.984036] usb 1-10: device descriptor read/64, error -110
/var/log/syslog:Apr 24 22:12:05 Sinbad kernel: [   63.200031] usb 1-10: device descriptor read/64, error -110
/var/log/syslog:Apr 24 22:12:05 Sinbad kernel: [   68.436319] usb 1-10: device descriptor read/8, error -110
/var/log/syslog:Apr 24 22:12:05 Sinbad kernel: [   72.661422] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
/var/log/syslog:Apr 24 22:12:05 Sinbad kernel: [   73.556248] usb 1-10: device descriptor read/8, error -110
/var/log/syslog:Apr 24 22:12:09 Sinbad kernel: [   78.792401] usb 1-10: device descriptor read/8, error -110
/var/log/syslog:Apr 24 22:12:12 Sinbad NetworkManager[648]: <error> [1398334332.224246] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
/var/log/syslog:Apr 24 22:12:12 Sinbad dnsmasq[996]: warning: no upstream servers configured
/var/log/syslog:Apr 24 22:12:14 Sinbad kernel: [   83.912262] usb 1-10: device descriptor read/8, error -110
/var/log/syslog:Apr 24 22:12:29 Sinbad kernel: [   99.480048] usb 4-2: device descriptor read/64, error -110
/var/log/syslog:Apr 24 22:12:45 Sinbad kernel: [  114.724128] usb 4-2: device descriptor read/64, error -110
/var/log/syslog:Apr 24 22:12:59 Sinbad kernel: [  129.112069] usb 4-2: device descriptor read/64, error -110
/var/log/syslog:Apr 24 22:13:14 Sinbad kernel: [  144.352092] usb 4-2: device descriptor read/64, error -110
/var/log/syslog:Apr 24 22:13:19 Sinbad kernel: [  149.624857] usb 4-2: device descriptor read/8, error -110
/var/log/syslog:Apr 24 22:13:25 Sinbad kernel: [  154.744314] usb 4-2: device descriptor read/8, error -110
/var/log/syslog:Apr 24 22:13:30 Sinbad kernel: [  160.004689] usb 4-2: device descriptor read/8, error -110
/var/log/syslog:Apr 24 22:13:35 Sinbad kernel: [  165.124134] usb 4-2: device descriptor read/8, error -110
/var/log/Xorg.0.log:	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
/var/log/Xorg.0.log:[    82.072] (WW) Warning, couldn't open module fglrx
/var/log/Xorg.0.log:[    82.098] (WW) Warning, couldn't open module fglrx
```

Still, I messed with my wireless, and it still works.  That's good!

---

### Post by sitro on 2014-04-24
For me your wireless card cannot be active. but I am willing to believe if you post the result of the commands : "iwconfig" and "ifconfig".

then, as ask you previously, you can post the complete result of the command : "sudo lsusb -v"
then, as ask you previously, can you say if in the bios of the computer, is there a switch to enable/disable the usb port.
then in subsidiary, as ask you previously, can you try the step by step the process of plug/unplug the power.

---

### Post by Jonathan_Traill on 2014-05-03
Wireless is definitely working, no matter what the error messages may say.

iwconfig gives:


```
wlan0     IEEE 802.11abg  ESSID:"belkin.680"            Mode:Managed  Frequency:2.412 GHz  Access Point: 08:86:3B:D9:86:80   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.


eth0      no wireless extensions.
```

ifconfig gives:

```
eth0      Link encap:Ethernet  HWaddr 00:23:5a:df:8b:f7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2920 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2920 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:289803 (289.8 KB)  TX bytes:289803 (289.8 KB)


wlan0     Link encap:Ethernet  HWaddr 00:25:56:28:c3:8c  
          inet addr:192.168.2.5  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::225:56ff:fe28:c38c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:89099 errors:0 dropped:0 overruns:0 frame:97932
          TX packets:63044 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:111223936 (111.2 MB)  TX bytes:7300579 (7.3 MB)
          Interrupt:18 
```

I posted everything sudo lsusb -v gave previously, but here it is again. 

```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0002 2.0 root hub
  bcdDevice            3.13
  iManufacturer           3 Linux 3.13.0-24-generic ehci_hcd
  iProduct                2 EHCI Host Controller
  iSerial                 1 0000:00:13.5
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12
Hub Descriptor:
  bLength              11
  bDescriptorType      41
  nNbrPorts            10
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood       10 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00 0x00
  PortPwrCtrlMask    0xff 0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
   Port 4: 0000.0100 power
   Port 5: 0000.0100 power
   Port 6: 0000.0100 power
   Port 7: 0000.0100 power
   Port 8: 0000.0100 power
   Port 9: 0000.0100 power
   Port 10: 0000.0100 power
Device Status:     0x0001
  Self Powered


Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

[COLOR=#000000]I have never seen any switch in the bios to enable/disable the usb port.[/COLOR]

Plugging and unplugging, removing battery etc as described made no difference.

Interestingly, I tried to set up Skype tonight and my integrated webcam - which used to work - does not function.  I installed cheese to test it and it did not find a device.  Could this be USB device causing such problems.

I haven't used the webcam for years so I could not say if it stopped functioning at the same time the boot slowed down.

---

### Post by Jonathan_Traill on 2014-05-17
I'm going to mark this as solved as I have found a solution that works for me - I have reinstalled Ubuntu 12.04, which loads promptly.  I think the problem I was experiencing with Lubuntu must lie deep in that system, one of many little glitches I have encountered with that distro.  Which is a shame as otherwise I do like Lubuntu.

---

