---
title: "startx causes system crash"
date: 2013-01-14
forum: General Help
---

### Post by MaximKat2 on 2013-01-14
Hi all,

I have a new desktop with Celeron G550 and Intel HD Graphics. 

First trouble has started when the live  CD refused to load and the system would just reboot before getting to the screen where you're supposed to choose before live mode or install mode. I was able to install it using the alternate installer.

However, Ubuntu still doesn't work. It only loads in the console using "nomodeset text" options in Grub. Any attempt to use 'startx', 'service lightdm start' or 'service gdm start' just crashes the system completely (see attachments). It either freezes on this purplish static screen or reboots by itself after a few seconds. Same result if I just try to boot without "nomodeset". 

During the boot process the message "Starting load fallback graphics devices [fail]" appears. I tried to dpkg-reconfigure various xserver related packages to no effect. There is no xorg.conf. No X server logs are generated in the process. The system just dies. If I connect via ssh, there is no output in dmesg during the attempt to start the X server locally, it just boots me out immediately.

```

misha@ubuntu:~$ lspci | grep VGA
VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)

misha@ubuntu:~$ sudo lshw -C video
  *-display UNCLAIMED
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64)

```

```

misha@ubuntu:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-29-generic-pae (buildd@roseapple) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #46-Ubuntu SMP Fri Jul 27 17:25:43 UTC 2012 (Ubuntu 3.2.0-29.46-generic-pae 3.2.24)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d800 (usable)
[    0.000000]  BIOS-e820: 000000000009d800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000020000000 (usable)
[    0.000000]  BIOS-e820: 0000000020000000 - 0000000020200000 (reserved)
[    0.000000]  BIOS-e820: 0000000020200000 - 0000000040000000 (usable)
[    0.000000]  BIOS-e820: 0000000040000000 - 0000000040200000 (reserved)
[    0.000000]  BIOS-e820: 0000000040200000 - 00000000d9fec000 (usable)
[    0.000000]  BIOS-e820: 00000000d9fec000 - 00000000da5de000 (reserved)
[    0.000000]  BIOS-e820: 00000000da5de000 - 00000000da85e000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000da85e000 - 00000000da863000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000da863000 - 00000000da8a6000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000da8a6000 - 00000000dae2f000 (usable)
[    0.000000]  BIOS-e820: 00000000dae2f000 - 00000000daff2000 (reserved)
[    0.000000]  BIOS-e820: 00000000daff2000 - 00000000db000000 (usable)
[    0.000000]  BIOS-e820: 00000000db800000 - 00000000dfa00000 (reserved)
[    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed04000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 000000011f600000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.7 present.
[    0.000000] DMI: BIOSTAR Group H61MLV2/H61MLV2, BIOS 4.6.5 04/19/2012
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x11f600 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-E7FFF uncachable
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F00000000 write-back
[    0.000000]   1 base 100000000 mask FE0000000 write-back
[    0.000000]   2 base 0E0000000 mask FE0000000 uncachable
[    0.000000]   3 base 0DC000000 mask FFC000000 uncachable
[    0.000000]   4 base 0DB800000 mask FFF800000 uncachable
[    0.000000]   5 base 11F800000 mask FFF800000 uncachable
[    0.000000]   6 base 11F600000 mask FFFE00000 uncachable
[    0.000000]   7 disabled
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 4GB, type WB
[    0.000000] reg 1, base: 4GB, range: 512MB, type WB
[    0.000000] reg 2, base: 3584MB, range: 512MB, type UC
[    0.000000] reg 3, base: 3520MB, range: 64MB, type UC
[    0.000000] reg 4, base: 3512MB, range: 8MB, type UC
[    0.000000] reg 5, base: 4600MB, range: 8MB, type UC
[    0.000000] reg 6, base: 4598MB, range: 2MB, type UC
[    0.000000] total RAM covered: 4014M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K 	chunk_size: 128M 	num_reg: 8  	lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 512MB, type WB
[    0.000000] reg 3, base: 3512MB, range: 8MB, type UC
[    0.000000] reg 4, base: 3520MB, range: 64MB, type UC
[    0.000000] reg 5, base: 4GB, range: 512MB, type WB
[    0.000000] reg 6, base: 4598MB, range: 2MB, type UC
[    0.000000] reg 7, base: 4600MB, range: 8MB, type UC
[    0.000000] e820 update range: 00000000db800000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] found SMP MP-table at [c00fcb90] fcb90
[    0.000000] initial memory mapped : 0 - 02000000
[    0.000000] Base memory trampoline at [c0099000] 99000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-0000000037bfe000
[    0.000000]  0000000000 - 0000200000 page 4k
[    0.000000]  0000200000 - 0037a00000 page 2M
[    0.000000]  0037a00000 - 0037bfe000 page 4k
[    0.000000] kernel direct mapping tables up to 37bfe000 @ 1ffb000-2000000
[    0.000000] RAMDISK: 364ee000 - 3726f000
[    0.000000] ACPI: RSDP 000f0450 00024 (v02 ALASKA)
[    0.000000] ACPI: XSDT da842070 0005C (v01 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: FACP da84b498 000F4 (v04 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: DSDT da842160 09334 (v02 ALASKA    A M I 00000015 INTL 20051117)
[    0.000000] ACPI: FACS da85cf80 00040
[    0.000000] ACPI: APIC da84b590 00062 (v03 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: MCFG da84b5f8 0003C (v01 ALASKA    A M I 01072009 MSFT 00000097)
[    0.000000] ACPI: HPET da84b638 00038 (v01 ALASKA    A M I 01072009 AMI. 00000005)
[    0.000000] ACPI: SSDT da84b670 0036D (v01 SataRe SataTabl 00001000 INTL 20091112)
[    0.000000] ACPI: SSDT da84b9e0 00860 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.000000] ACPI: SSDT da84c240 00A92 (v01  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 3706MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00037bfe
[    0.000000]   HighMem  0x00037bfe -> 0x0011f600
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[7] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x00020000
[    0.000000]     0: 0x00020200 -> 0x00040000
[    0.000000]     0: 0x00040200 -> 0x000d9fec
[    0.000000]     0: 0x000da8a6 -> 0x000dae2f
[    0.000000]     0: 0x000daff2 -> 0x000db000
[    0.000000]     0: 0x00100000 -> 0x0011f600
[    0.000000] On node 0 totalpages: 1021712
[    0.000000] free_area_init_node: node 0, pgdat c1866a40, node_mem_map f40fe200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3949 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 221990 pages, LIFO batch:31
[    0.000000]   HighMem zone: 7413 pages used for memmap
[    0.000000]   HighMem zone: 786576 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000020200000
[    0.000000] Allocating PCI resources starting at dfa00000 (gap: dfa00000:18600000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @f7bcf000 s34240 r0 d23104 u57344
[    0.000000] pcpu-alloc: s34240 r0 d23104 u57344 alloc=14*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1012515
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-29-generic-pae root=UUID=352ee80c-fd17-4e1c-94fd-395248df0889 ro nomodeset text
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
[    0.000000] allocated 18833152 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:0011f600)
[    0.000000] Memory: 4006472k/4708352k available (5814k kernel code, 80376k reserved, 2841k data, 740k init, 3175956k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc1875000 - 0xc192e000   ( 740 kB)
[    0.000000]       .data : 0xc15adb64 - 0xc1874240   (2841 kB)
[    0.000000]       .text : 0xc1000000 - 0xc15adb64   (5814 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:512 16
[    0.000000] CPU 0 irqstacks, hard=f7408000 soft=f740a000
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.004000] Detected 2594.235 MHz processor.
[    0.000001] Calibrating delay loop (skipped), value calculated using timer frequency.. 5188.47 BogoMIPS (lpj=10376940)
[    0.000072] pid_max: default: 32768 minimum: 301
[    0.000121] Security Framework initialized
[    0.000165] AppArmor: AppArmor initialized
[    0.000198] Yama: becoming mindful.
[    0.000268] Mount-cache hash table entries: 512
[    0.000398] Initializing cgroup subsys cpuacct
[    0.000436] Initializing cgroup subsys memory
[    0.000474] Initializing cgroup subsys devices
[    0.000508] Initializing cgroup subsys freezer
[    0.000542] Initializing cgroup subsys blkio
[    0.000579] Initializing cgroup subsys perf_event
[    0.000633] CPU: Physical Processor ID: 0
[    0.000666] CPU: Processor Core ID: 0
[    0.000701] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.000702] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.000777] mce: CPU supports 7 MCE banks
[    0.000819] CPU0: Thermal monitoring enabled (TM1)
[    0.000859] using mwait in idle threads.
[    0.002872] ACPI: Core revision 20110623
[    0.008339] ftrace: allocating 26545 entries in 52 pages
[    0.017184] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.017622] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.057268] CPU0: Intel(R) Celeron(R) CPU G550 @ 2.60GHz stepping 07
[    0.163993] Performance Events: PEBS fmt1+, SandyBridge events, Intel PMU driver.
[    0.164091] PEBS disabled due to CPU errata.
[    0.164125] ... version:                3
[    0.164158] ... bit width:              48
[    0.164191] ... generic registers:      8
[    0.164224] ... value mask:             0000ffffffffffff
[    0.164259] ... max period:             000000007fffffff
[    0.164294] ... fixed-purpose events:   3
[    0.164328] ... event mask:             00000007000000ff
[    0.164458] NMI watchdog enabled, takes one hw-pmu counter.
[    0.164556] CPU 1 irqstacks, hard=f74ea000 soft=f74ec000
[    0.164557] Booting Node   0, Processors  #1 Ok.
[    0.164607] smpboot cpu 1: start_ip = 99000
[    0.174758] Initializing CPU#1
[    0.271913] NMI watchdog enabled, takes one hw-pmu counter.
[    0.272005] Brought up 2 CPUs
[    0.272037] Total of 2 processors activated (10376.44 BogoMIPS).
[    0.273380] devtmpfs: initialized
[    0.273510] EVM: security.selinux
[    0.273542] EVM: security.SMACK64
[    0.273574] EVM: security.capability
[    0.273625] PM: Registering ACPI NVS region at da5de000 (2621440 bytes)
[    0.273710] PM: Registering ACPI NVS region at da863000 (274432 bytes)
[    0.274505] print_constraints: dummy: 
[    0.274566] RTC time:  2:43:50, date: 11/15/13
[    0.274626] NET: Registered protocol family 16
[    0.274715] Trying to unpack rootfs image as initramfs...
[    0.274750] EISA bus registered
[    0.274787] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.274838] ACPI: bus type pci registered
[    0.274920] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.274974] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.275011] PCI: Using MMCONFIG for extended config space
[    0.275047] PCI: Using configuration type 1 for base access
[    0.276415] bio: create slab <bio-0> at 0
[    0.276509] ACPI: Added _OSI(Module Device)
[    0.276543] ACPI: Added _OSI(Processor Device)
[    0.276577] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.276612] ACPI: Added _OSI(Processor Aggregator Device)
[    0.278190] ACPI: EC: Look up EC in DSDT
[    0.279839] ACPI: Executed 1 blocks of module-level executable AML code
[    0.320207] ACPI: SSDT da58b018 0083B (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.320691] ACPI: Dynamic OEM Table Load:
[    0.320755] ACPI: SSDT   (null) 0083B (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.351996] ACPI: SSDT da58ca98 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.352509] ACPI: Dynamic OEM Table Load:
[    0.352572] ACPI: SSDT   (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.383802] ACPI: SSDT da58dc18 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.384278] ACPI: Dynamic OEM Table Load:
[    0.384342] ACPI: SSDT   (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.391903] ACPI: Interpreter enabled
[    0.391945] ACPI: (supports S0 S1 S4 S5)
[    0.392057] ACPI: Using IOAPIC for interrupt routing
[    0.397560] ACPI: Power Resource [FN00] (off)
[    0.397666] ACPI: Power Resource [FN01] (off)
[    0.397768] ACPI: Power Resource [FN02] (off)
[    0.397869] ACPI: Power Resource [FN03] (off)
[    0.397969] ACPI: Power Resource [FN04] (off)
[    0.398463] ACPI: No dock devices found.
[    0.398496] HEST: Table not found.
[    0.398531] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.398878] \_SB_.PCI0:_OSC invalid UUID
[    0.398880] _OSC request data:1 8 1f 
[    0.398883] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    0.399397] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.399435] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.399473] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.399523] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d3fff]
[    0.399573] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    0.399623] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    0.399676] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000dffff]
[    0.399726] pci_root PNP0A08:00: host bridge window [mem 0x000e0000-0x000e3fff]
[    0.399776] pci_root PNP0A08:00: host bridge window [mem 0x000e4000-0x000e7fff]
[    0.399826] pci_root PNP0A08:00: host bridge window [mem 0xdfa00000-0xfeafffff]
[    0.399876] pci_root PNP0A08:00: host bridge window [mem 0x11f600000-0xfffffffff]
[    0.399937] pci 0000:00:00.0: [8086:0100] type 0 class 0x000600
[    0.399975] pci 0000:00:02.0: [8086:0102] type 0 class 0x000300
[    0.399986] pci 0000:00:02.0: reg 10: [mem 0xf7800000-0xf7bfffff 64bit]
[    0.399992] pci 0000:00:02.0: reg 18: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.399996] pci 0000:00:02.0: reg 20: [io  0xf000-0xf03f]
[    0.400051] pci 0000:00:16.0: [8086:1c3a] type 0 class 0x000780
[    0.400074] pci 0000:00:16.0: reg 10: [mem 0xf7d0a000-0xf7d0a00f 64bit]
[    0.400151] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.400156] pci 0000:00:16.0: PME# disabled
[    0.400189] pci 0000:00:1a.0: [8086:1c2d] type 0 class 0x000c03
[    0.400210] pci 0000:00:1a.0: reg 10: [mem 0xf7d08000-0xf7d083ff]
[    0.400304] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.400308] pci 0000:00:1a.0: PME# disabled
[    0.400333] pci 0000:00:1b.0: [8086:1c20] type 0 class 0x000403
[    0.400349] pci 0000:00:1b.0: reg 10: [mem 0xf7d00000-0xf7d03fff 64bit]
[    0.400420] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.400424] pci 0000:00:1b.0: PME# disabled
[    0.400446] pci 0000:00:1c.0: [8086:1c10] type 1 class 0x000604
[    0.400530] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.400533] pci 0000:00:1c.0: PME# disabled
[    0.400557] pci 0000:00:1c.1: [8086:1c12] type 1 class 0x000604
[    0.400638] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.400642] pci 0000:00:1c.1: PME# disabled
[    0.400675] pci 0000:00:1d.0: [8086:1c26] type 0 class 0x000c03
[    0.400697] pci 0000:00:1d.0: reg 10: [mem 0xf7d07000-0xf7d073ff]
[    0.400791] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.400795] pci 0000:00:1d.0: PME# disabled
[    0.400820] pci 0000:00:1f.0: [8086:1c5c] type 0 class 0x000601
[    0.400947] pci 0000:00:1f.2: [8086:1c02] type 0 class 0x000106
[    0.400966] pci 0000:00:1f.2: reg 10: [io  0xf0b0-0xf0b7]
[    0.400974] pci 0000:00:1f.2: reg 14: [io  0xf0a0-0xf0a3]
[    0.400983] pci 0000:00:1f.2: reg 18: [io  0xf090-0xf097]
[    0.400991] pci 0000:00:1f.2: reg 1c: [io  0xf080-0xf083]
[    0.400999] pci 0000:00:1f.2: reg 20: [io  0xf060-0xf07f]
[    0.401007] pci 0000:00:1f.2: reg 24: [mem 0xf7d06000-0xf7d067ff]
[    0.401054] pci 0000:00:1f.2: PME# supported from D3hot
[    0.401057] pci 0000:00:1f.2: PME# disabled
[    0.401074] pci 0000:00:1f.3: [8086:1c22] type 0 class 0x000c05
[    0.401089] pci 0000:00:1f.3: reg 10: [mem 0xf7d05000-0xf7d050ff 64bit]
[    0.401111] pci 0000:00:1f.3: reg 20: [io  0xf040-0xf05f]
[    0.401185] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    0.401296] pci 0000:02:00.0: [1969:2062] type 0 class 0x000200
[    0.401325] pci 0000:02:00.0: reg 10: [mem 0xf7c00000-0xf7c3ffff 64bit]
[    0.401341] pci 0000:02:00.0: reg 18: [io  0xe000-0xe07f]
[    0.401472] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.401478] pci 0000:02:00.0: PME# disabled
[    0.407670] pci 0000:00:1c.1: PCI bridge to [bus 02-02]
[    0.407711] pci 0000:00:1c.1:   bridge window [io  0xe000-0xefff]
[    0.407714] pci 0000:00:1c.1:   bridge window [mem 0xf7c00000-0xf7cfffff]
[    0.407733] pci_bus 0000:00: on NUMA node 0
[    0.407737] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.407913] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.407948] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.408068] \_SB_.PCI0:_OSC invalid UUID
[    0.408069] _OSC request data:1 1f 1f 
[    0.408073]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.408149] \_SB_.PCI0:_OSC invalid UUID
[    0.408150] _OSC request data:1 0 1d 
[    0.408154]  pci0000:00: ACPI _OSC request failed (AE_ERROR), returned control mask: 0x1d
[    0.408205] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.411290] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.411555] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.411820] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.412080] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 *10 11 12 14 15)
[    0.412325] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.412630] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.412933] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.413191] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.413503] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.413558] vgaarb: loaded
[    0.413589] vgaarb: bridge control possible 0000:00:02.0
[    0.413707] i2c-core: driver [aat2870] using legacy suspend method
[    0.413743] i2c-core: driver [aat2870] using legacy resume method
[    0.413846] SCSI subsystem initialized
[    0.413919] libata version 3.00 loaded.
[    0.413953] usbcore: registered new interface driver usbfs
[    0.413996] usbcore: registered new interface driver hub
[    0.414050] usbcore: registered new device driver usb
[    0.414151] PCI: Using ACPI for IRQ routing
[    0.415829] PCI: pci_cache_line_size set to 64 bytes
[    0.415881] reserve RAM buffer: 000000000009d800 - 000000000009ffff 
[    0.415884] reserve RAM buffer: 00000000d9fec000 - 00000000dbffffff 
[    0.415887] reserve RAM buffer: 00000000dae2f000 - 00000000dbffffff 
[    0.415889] reserve RAM buffer: 00000000db000000 - 00000000dbffffff 
[    0.415891] reserve RAM buffer: 000000011f600000 - 000000011fffffff 
[    0.415968] NetLabel: Initializing
[    0.416001] NetLabel:  domain hash size = 128
[    0.416035] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.416077] NetLabel:  unlabeled traffic allowed by default
[    0.416151] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.416327] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.418372] Switching to clocksource hpet
[    0.424337] AppArmor: AppArmor Filesystem Enabled
[    0.424397] pnp: PnP ACPI init
[    0.424440] ACPI: bus type pnp registered
[    0.424742] pnp 00:00: [bus 00-3e]
[    0.424745] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.424746] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.424748] pnp 00:00: [io  0x0d00-0xffff window]
[    0.424750] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.424752] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    0.424754] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    0.424755] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    0.424757] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    0.424759] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    0.424761] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    0.424762] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    0.424764] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    0.424766] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    0.424767] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    0.424769] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    0.424771] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    0.424772] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    0.424774] pnp 00:00: [mem 0xdfa00000-0xfeafffff window]
[    0.424776] pnp 00:00: [mem 0x11f600000-0xfffffffff window]
[    0.424838] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.424856] pnp 00:01: [mem 0xfed40000-0xfed44fff]
[    0.424895] system 00:01: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.424935] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.424945] pnp 00:02: [io  0x0000-0x001f]
[    0.424946] pnp 00:02: [io  0x0081-0x0091]
[    0.424948] pnp 00:02: [io  0x0093-0x009f]
[    0.424949] pnp 00:02: [io  0x00c0-0x00df]
[    0.424951] pnp 00:02: [dma 4]
[    0.424969] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.424975] pnp 00:03: [mem 0xff000000-0xffffffff]
[    0.424992] pnp 00:03: Plug and Play ACPI device, IDs INT0800 (active)
[    0.425050] pnp 00:04: [mem 0xfed00000-0xfed003ff]
[    0.425070] pnp 00:04: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.425081] pnp 00:05: [io  0x002e-0x002f]
[    0.425082] pnp 00:05: [io  0x004e-0x004f]
[    0.425083] pnp 00:05: [io  0x0061]
[    0.425085] pnp 00:05: [io  0x0063]
[    0.425086] pnp 00:05: [io  0x0065]
[    0.425088] pnp 00:05: [io  0x0067]
[    0.425090] pnp 00:05: [io  0x0070]
[    0.425091] pnp 00:05: [io  0x0080]
[    0.425092] pnp 00:05: [io  0x0092]
[    0.425094] pnp 00:05: [io  0x00b2-0x00b3]
[    0.425095] pnp 00:05: [io  0x0680-0x069f]
[    0.425097] pnp 00:05: [io  0x0200-0x020f]
[    0.425098] pnp 00:05: [io  0xffff]
[    0.425101] pnp 00:05: [io  0xffff]
[    0.425102] pnp 00:05: [io  0x0400-0x0453]
[    0.425103] pnp 00:05: [io  0x0458-0x047f]
[    0.425105] pnp 00:05: [io  0x0500-0x057f]
[    0.425106] pnp 00:05: [io  0x164e-0x164f]
[    0.425137] system 00:05: [io  0x0680-0x069f] has been reserved
[    0.425174] system 00:05: [io  0x0200-0x020f] has been reserved
[    0.425211] system 00:05: [io  0xffff] has been reserved
[    0.425247] system 00:05: [io  0xffff] has been reserved
[    0.425283] system 00:05: [io  0x0400-0x0453] has been reserved
[    0.425319] system 00:05: [io  0x0458-0x047f] has been reserved
[    0.425356] system 00:05: [io  0x0500-0x057f] has been reserved
[    0.425393] system 00:05: [io  0x164e-0x164f] has been reserved
[    0.425430] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.425437] pnp 00:06: [io  0x0070-0x0077]
[    0.425447] pnp 00:06: [irq 8]
[    0.425466] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.425488] pnp 00:07: [io  0x0454-0x0457]
[    0.425515] system 00:07: [io  0x0454-0x0457] has been reserved
[    0.425552] system 00:07: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.425638] pnp 00:08: [io  0x0000-0xffffffffffffffff disabled]
[    0.425640] pnp 00:08: [io  0x0a00-0x0a1f]
[    0.425641] pnp 00:08: [io  0x0a20-0x0a2f]
[    0.425642] pnp 00:08: [io  0x0a30-0x0a3f]
[    0.425671] system 00:08: [io  0x0a00-0x0a1f] has been reserved
[    0.425708] system 00:08: [io  0x0a20-0x0a2f] has been reserved
[    0.425745] system 00:08: [io  0x0a30-0x0a3f] has been reserved
[    0.425782] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.425800] pnp 00:09: [io  0x0060]
[    0.425801] pnp 00:09: [io  0x0064]
[    0.425806] pnp 00:09: [irq 1]
[    0.425833] pnp 00:09: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.425859] pnp 00:0a: [irq 12]
[    0.425883] pnp 00:0a: Plug and Play ACPI device, IDs PNP0f03 PNP0f13 (active)
[    0.426017] pnp 00:0b: [io  0x03f8-0x03ff]
[    0.426021] pnp 00:0b: [irq 4]
[    0.426023] pnp 00:0b: [dma 0 disabled]
[    0.426074] pnp 00:0b: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.426092] pnp 00:0c: [io  0x0010-0x001f]
[    0.426094] pnp 00:0c: [io  0x0022-0x003f]
[    0.426095] pnp 00:0c: [io  0x0044-0x005f]
[    0.426096] pnp 00:0c: [io  0x0062-0x0063]
[    0.426098] pnp 00:0c: [io  0x0065-0x006f]
[    0.426099] pnp 00:0c: [io  0x0072-0x007f]
[    0.426101] pnp 00:0c: [io  0x0080]
[    0.426102] pnp 00:0c: [io  0x0084-0x0086]
[    0.426103] pnp 00:0c: [io  0x0088]
[    0.426105] pnp 00:0c: [io  0x008c-0x008e]
[    0.426106] pnp 00:0c: [io  0x0090-0x009f]
[    0.426107] pnp 00:0c: [io  0x00a2-0x00bf]
[    0.426109] pnp 00:0c: [io  0x00e0-0x00ef]
[    0.426110] pnp 00:0c: [io  0x04d0-0x04d1]
[    0.426141] system 00:0c: [io  0x04d0-0x04d1] has been reserved
[    0.426179] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.426186] pnp 00:0d: [io  0x00f0-0x00ff]
[    0.426190] pnp 00:0d: [irq 13]
[    0.426212] pnp 00:0d: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.426402] pnp 00:0e: [mem 0xfed1c000-0xfed1ffff]
[    0.426405] pnp 00:0e: [mem 0xfed10000-0xfed17fff]
[    0.426407] pnp 00:0e: [mem 0xfed18000-0xfed18fff]
[    0.426408] pnp 00:0e: [mem 0xfed19000-0xfed19fff]
[    0.426410] pnp 00:0e: [mem 0xf8000000-0xfbffffff]
[    0.426411] pnp 00:0e: [mem 0xfed20000-0xfed3ffff]
[    0.426413] pnp 00:0e: [mem 0xfed90000-0xfed93fff]
[    0.426414] pnp 00:0e: [mem 0xfed45000-0xfed8ffff]
[    0.426416] pnp 00:0e: [mem 0xff000000-0xffffffff]
[    0.426417] pnp 00:0e: [mem 0xfee00000-0xfeefffff]
[    0.426419] pnp 00:0e: [mem 0xdfa00000-0xdfa00fff]
[    0.426488] system 00:0e: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.426527] system 00:0e: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.426565] system 00:0e: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.426603] system 00:0e: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.426641] system 00:0e: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.426679] system 00:0e: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.426718] system 00:0e: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.426756] system 00:0e: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.426794] system 00:0e: [mem 0xff000000-0xffffffff] has been reserved
[    0.426832] system 00:0e: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.426870] system 00:0e: [mem 0xdfa00000-0xdfa00fff] has been reserved
[    0.426910] system 00:0e: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.427031] pnp 00:0f: [mem 0x20000000-0x201fffff]
[    0.427033] pnp 00:0f: [mem 0x40000000-0x401fffff]
[    0.427081] system 00:0f: [mem 0x20000000-0x201fffff] has been reserved
[    0.427121] system 00:0f: [mem 0x40000000-0x401fffff] has been reserved
[    0.427159] system 00:0f: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.427179] pnp: PnP ACPI: found 16 devices
[    0.427212] ACPI: ACPI bus type pnp unregistered
[    0.427248] PnPBIOS: Disabled by ACPI PNP
[    0.462939] PCI: max bus depth: 1 pci_try_num: 2
[    0.462975] pci 0000:00:1c.0: BAR 14: assigned [mem 0xdfb00000-0xdfcfffff]
[    0.463019] pci 0000:00:1c.0: BAR 15: assigned [mem 0xdfd00000-0xdfefffff 64bit pref]
[    0.463072] pci 0000:00:1c.0: BAR 13: assigned [io  0x2000-0x2fff]
[    0.463110] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    0.463147] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.463187] pci 0000:00:1c.0:   bridge window [mem 0xdfb00000-0xdfcfffff]
[    0.463228] pci 0000:00:1c.0:   bridge window [mem 0xdfd00000-0xdfefffff 64bit pref]
[    0.463283] pci 0000:00:1c.1: PCI bridge to [bus 02-02]
[    0.463320] pci 0000:00:1c.1:   bridge window [io  0xe000-0xefff]
[    0.463360] pci 0000:00:1c.1:   bridge window [mem 0xf7c00000-0xf7cfffff]
[    0.463420] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.463461] pci 0000:00:1c.0: setting latency timer to 64
[    0.463471] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.463511] pci 0000:00:1c.1: setting latency timer to 64
[    0.463515] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.463517] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.463519] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.463520] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.463522] pci_bus 0000:00: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.463524] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.463526] pci_bus 0000:00: resource 10 [mem 0x000dc000-0x000dffff]
[    0.463527] pci_bus 0000:00: resource 11 [mem 0x000e0000-0x000e3fff]
[    0.463529] pci_bus 0000:00: resource 12 [mem 0x000e4000-0x000e7fff]
[    0.463531] pci_bus 0000:00: resource 13 [mem 0xdfa00000-0xfeafffff]
[    0.463533] pci_bus 0000:00: resource 14 [mem 0x11f600000-0xfffffffff]
[    0.463535] pci_bus 0000:01: resource 0 [io  0x2000-0x2fff]
[    0.463536] pci_bus 0000:01: resource 1 [mem 0xdfb00000-0xdfcfffff]
[    0.463538] pci_bus 0000:01: resource 2 [mem 0xdfd00000-0xdfefffff 64bit pref]
[    0.463540] pci_bus 0000:02: resource 0 [io  0xe000-0xefff]
[    0.463542] pci_bus 0000:02: resource 1 [mem 0xf7c00000-0xf7cfffff]
[    0.463569] NET: Registered protocol family 2
[    0.463644] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.463805] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.464098] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.464264] TCP: Hash tables configured (established 131072 bind 65536)
[    0.464303] TCP reno registered
[    0.464336] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.464378] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.464469] NET: Registered protocol family 1
[    0.465005] pci 0000:00:02.0: BIOS left Intel GPU interrupts enabled; disabling
[    0.465300] pci 0000:00:02.0: Boot video device
[    0.465313] pci 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.482393] pci 0000:00:1a.0: PCI INT A disabled
[    0.482460] pci 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.502347] pci 0000:00:1d.0: PCI INT A disabled
[    0.502399] PCI: CLS 64 bytes, default 64
[    0.502692] audit: initializing netlink socket (disabled)
[    0.502735] type=2000 audit(1384483429.376:1): initialized
[    0.525572] highmem bounce pool size: 64 pages
[    0.525611] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.535409] VFS: Disk quotas dquot_6.5.2
[    0.535499] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.535922] fuse init (API version 7.17)
[    0.535992] Freeing initrd memory: 13828k freed
[    0.536021] msgmni has been set to 1622
[    0.536284] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.536413] io scheduler noop registered
[    0.536450] io scheduler deadline registered
[    0.536506] io scheduler cfq registered (default)
[    0.536853] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.536941] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.537095] intel_idle: MWAIT substates: 0x1120
[    0.537100] intel_idle: v0.4 model 0x2A
[    0.537101] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.537278] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.537353] ACPI: Power Button [PWRB]
[    0.537474] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.537533] ACPI: Power Button [PWRF]
[    0.537754] ACPI: Fan [FAN0] (off)
[    0.537847] ACPI: Fan [FAN1] (off)
[    0.537937] ACPI: Fan [FAN2] (off)
[    0.538039] ACPI: Fan [FAN3] (off)
[    0.538142] ACPI: Fan [FAN4] (off)
[    0.554462] thermal LNXTHERM:00: registered as thermal_zone0
[    0.554500] ACPI: Thermal Zone [TZ00] (28 C)
[    0.555208] thermal LNXTHERM:01: registered as thermal_zone1
[    0.555244] ACPI: Thermal Zone [TZ01] (30 C)
[    0.555447] thermal LNXTHERM:02: registered as thermal_zone2
[    0.555483] ACPI: Thermal Zone [THRM] (39 C)
[    0.555551] ERST: Table is not found!
[    0.555584] GHES: HEST is not enabled!
[    0.555637] isapnp: Scanning for PnP cards...
[    0.555687] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.576099] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.908406] isapnp: No Plug & Play device found
[    0.974008] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.989642] Linux agpgart interface v0.103
[    0.989737] agpgart-intel 0000:00:00.0: Intel Sandybridge Chipset
[    0.989835] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    0.990404] agpgart-intel 0000:00:00.0: detected 65536K stolen memory
[    0.990539] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
[    0.991627] brd: module loaded
[    0.992202] loop: module loaded
[    0.992333] ahci 0000:00:1f.2: version 3.0
[    0.992350] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.992426] ahci 0000:00:1f.2: irq 40 for MSI/MSI-X
[    1.005395] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 4 ports 3 Gbps 0x33 impl SATA mode
[    1.005467] ahci 0000:00:1f.2: flags: 64bit ncq led clo pio slum part ems apst 
[    1.005519] ahci 0000:00:1f.2: setting latency timer to 64
[    1.029756] scsi0 : ahci
[    1.029864] scsi1 : ahci
[    1.029956] scsi2 : ahci
[    1.030045] scsi3 : ahci
[    1.030133] scsi4 : ahci
[    1.030220] scsi5 : ahci
[    1.030516] ata1: SATA max UDMA/133 abar m2048@0xf7d06000 port 0xf7d06100 irq 40
[    1.030566] ata2: SATA max UDMA/133 abar m2048@0xf7d06000 port 0xf7d06180 irq 40
[    1.030616] ata3: DUMMY
[    1.030646] ata4: DUMMY
[    1.030678] ata5: SATA max UDMA/133 abar m2048@0xf7d06000 port 0xf7d06300 irq 40
[    1.030728] ata6: SATA max UDMA/133 abar m2048@0xf7d06000 port 0xf7d06380 irq 40
[    1.031094] Fixed MDIO Bus: probed
[    1.031139] tun: Universal TUN/TAP device driver, 1.6
[    1.031174] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.031253] PPP generic driver version 2.4.2
[    1.031372] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.031422] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.031473] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.031476] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    1.031541] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.031612] ehci_hcd 0000:00:1a.0: debug port 2
[    1.035508] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    1.035524] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xf7d08000
[    1.049299] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.049457] hub 1-0:1.0: USB hub found
[    1.049492] hub 1-0:1.0: 2 ports detected
[    1.049572] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.049622] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.049625] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    1.049693] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.049761] ehci_hcd 0000:00:1d.0: debug port 2
[    1.053662] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    1.053674] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xf7d07000
[    1.069261] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.069402] hub 2-0:1.0: USB hub found
[    1.069436] hub 2-0:1.0: 2 ports detected
[    1.069513] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.069558] uhci_hcd: USB Universal Host Controller Interface driver
[    1.069629] usbcore: registered new interface driver libusual
[    1.069707] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.070155] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.070193] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.070324] mousedev: PS/2 mouse device common for all mice
[    1.070463] rtc_cmos 00:06: RTC can wake from S4
[    1.070593] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    1.070655] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.070736] device-mapper: uevent: version 1.0.3
[    1.070820] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    1.070893] EISA: Probing bus 0 at eisa.0
[    1.070927] EISA: Cannot allocate resource for mainboard
[    1.070962] Cannot allocate resource for EISA slot 1
[    1.070997] Cannot allocate resource for EISA slot 2
[    1.071031] Cannot allocate resource for EISA slot 3
[    1.071066] Cannot allocate resource for EISA slot 4
[    1.071100] Cannot allocate resource for EISA slot 5
[    1.071135] Cannot allocate resource for EISA slot 6
[    1.071170] Cannot allocate resource for EISA slot 7
[    1.071205] Cannot allocate resource for EISA slot 8
[    1.071239] EISA: Detected 0 cards.
[    1.071277] cpufreq-nforce2: No nForce2 chipset.
[    1.071354] cpuidle: using governor ladder
[    1.071456] cpuidle: using governor menu
[    1.071489] EFI Variables Facility v0.08 2004-May-17
[    1.071668] TCP cubic registered
[    1.071789] NET: Registered protocol family 10
[    1.072148] NET: Registered protocol family 17
[    1.072184] Registering the dns_resolver key type
[    1.072234] Using IPI No-Shortcut mode
[    1.072429] PM: Hibernation image not present or could not be loaded.
[    1.072440] registered taskstats version 1
[    1.081956]   Magic number: 5:52:713
[    1.082074] rtc_cmos 00:06: setting system clock to 2013-11-15 02:43:51 UTC (1384483431)
[    1.082425] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.082462] EDD information not available.
[    1.090180] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    1.348772] ata5: SATA link down (SStatus 0 SControl 300)
[    1.348847] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.348904] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.349868] ata2.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    1.349874] ata2.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    1.349944] ata2.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    1.350889] ata2.00: ATA-8: Hitachi HDS721050CLA360, JP2OA50E, max UDMA/133
[    1.350940] ata2.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.351923] ata1.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    1.351929] ata1.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    1.351995] ata1.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    1.352056] ata2.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    1.352060] ata2.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    1.352113] ata2.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    1.353039] ata2.00: configured for UDMA/133
[    1.355372] ata1.00: ATAPI: HL-DT-ST DVDRAM GH24NS95, RN00, max UDMA/133
[    1.356726] ata6: SATA link down (SStatus 0 SControl 300)
[    1.359409] ata1.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    1.359414] ata1.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    1.359486] ata1.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    1.360733] usb 1-1: new high-speed USB device number 2 using ehci_hcd
[    1.362607] ata1.00: configured for UDMA/133
[    1.371638] scsi 0:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH24NS95  RN00 PQ: 0 ANSI: 5
[    1.379002] sr0: scsi3-mmc drive: 48x/12x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.379072] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.379296] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.379428] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.379749] scsi 1:0:0:0: Direct-Access     ATA      Hitachi HDS72105 JP2O PQ: 0 ANSI: 5
[    1.379925] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    1.380010] sd 1:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.380098] sd 1:0:0:0: [sda] Write Protect is off
[    1.380138] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.380202] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.415041]  sda: sda1 sda2 < sda5 >
[    1.415909] sd 1:0:0:0: [sda] Attached SCSI disk
[    1.416047] Freeing unused kernel memory: 740k freed
[    1.416251] Write protecting the kernel text: 5816k
[    1.416298] Write protecting the kernel read-only data: 2376k
[    1.416335] NX-protecting the kernel data: 4424k
[    1.428781] udevd[96]: starting version 175
[    1.463731] atl1c 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.463783] atl1c 0000:02:00.0: setting latency timer to 64
[    1.493018] hub 1-1:1.0: USB hub found
[    1.493111] hub 1-1:1.0: 4 ports detected
[    1.516428] Refined TSC clocksource calibration: 2594.106 MHz.
[    1.516480] Switching to clocksource tsc
[    1.588866] atl1c 0000:02:00.0: version 1.0.1.0-NAPI
[    1.604264] usb 2-1: new high-speed USB device number 2 using ehci_hcd
[    1.679635] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    1.679676] EXT4-fs (sda1): write access will be enabled during recovery
[    1.736832] hub 2-1:1.0: USB hub found
[    1.737020] hub 2-1:1.0: 6 ports detected
[    1.738194] EXT4-fs (sda1): recovery complete
[    1.738469] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    5.485537] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    5.529071] udevd[352]: starting version 175
[    5.942013] Adding 4084732k swap on /dev/sda5.  Priority:-1 extents:1 across:4084732k 
[    6.647892] lp: driver loaded but no devices found
[    6.648108] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[    8.373764] mei: module is from the staging directory, the quality is unknown, you have been warned.
[    8.374025] mei 0000:00:16.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.374031] mei 0000:00:16.0: setting latency timer to 64
[    8.374087] mei 0000:00:16.0: irq 41 for MSI/MSI-X
[    8.833044] [drm] Initialized drm 1.1.0 20060810
[    9.323069] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input3
[    9.441671] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.441675] pci 0000:00:02.0: setting latency timer to 64
[    9.458379] pci 0000:00:02.0: irq 42 for MSI/MSI-X
[    9.458384] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    9.458386] [drm] No driver support for vblank timestamp query.
[    9.477885] acpi device:4a: registered as cooling_device7
[    9.478535] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input4
[    9.478618] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    9.478646] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   11.172018] type=1400 audit(1384483441.605:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=654 comm="apparmor_parser"
[   11.172081] type=1400 audit(1384483441.605:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=655 comm="apparmor_parser"
[   11.172392] type=1400 audit(1384483441.605:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=654 comm="apparmor_parser"
[   11.172449] type=1400 audit(1384483441.605:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=655 comm="apparmor_parser"
[   11.172598] type=1400 audit(1384483441.605:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=654 comm="apparmor_parser"
[   11.172657] type=1400 audit(1384483441.605:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=655 comm="apparmor_parser"
[   11.636273] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   11.636324] snd_hda_intel 0000:00:1b.0: irq 43 for MSI/MSI-X
[   11.636350] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   12.819644] ppdev: user-space parallel port driver
[   13.274776] type=1400 audit(1384483443.713:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=752 comm="apparmor_parser"
[   13.277015] type=1400 audit(1384483443.713:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=752 comm="apparmor_parser"
[   13.454236] init: failsafe main process (679) killed by TERM signal
[   13.754889] Bluetooth: Core ver 2.16
[   13.754904] NET: Registered protocol family 31
[   13.754905] Bluetooth: HCI device and connection manager initialized
[   13.754908] Bluetooth: HCI socket layer initialized
[   13.754909] Bluetooth: L2CAP socket layer initialized
[   13.754913] Bluetooth: SCO socket layer initialized
[   13.960019] Bluetooth: RFCOMM TTY layer initialized
[   13.960023] Bluetooth: RFCOMM socket layer initialized
[   13.960025] Bluetooth: RFCOMM ver 1.11
[   14.109547] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   14.109549] Bluetooth: BNEP filters: protocol multicast
[   15.430269] init: udev-fallback-graphics main process (801) terminated with status 1
[   16.461224] atl1c 0000:02:00.0: irq 44 for MSI/MSI-X
[   16.461342] atl1c 0000:02:00.0: atl1c: eth0 NIC Link is Up<100 Mbps Full Duplex>
[   16.485679] type=1400 audit(1384483446.929:10): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=853 comm="apparmor_parser"
[   16.486058] type=1400 audit(1384483446.929:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=853 comm="apparmor_parser"
[   16.486265] type=1400 audit(1384483446.929:12): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=853 comm="apparmor_parser"
[   16.545060] type=1400 audit(1384483446.989:13): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=852 comm="apparmor_parser"
[   16.659757] type=1400 audit(1384483447.101:14): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=854 comm="apparmor_parser"
[   16.664471] type=1400 audit(1384483447.109:15): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince//launchpad_integration" pid=854 comm="apparmor_parser"
[   16.665367] type=1400 audit(1384483447.109:16): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince//sanitized_helper" pid=854 comm="apparmor_parser"
[   16.666066] type=1400 audit(1384483447.109:17): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=854 comm="apparmor_parser"
[   16.668820] type=1400 audit(1384483447.113:18): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer//launchpad_integration" pid=854 comm="apparmor_parser"
[   16.669640] type=1400 audit(1384483447.113:19): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer//sanitized_helper" pid=854 comm="apparmor_parser"
[   18.212527] init: plymouth-upstart-bridge main process (714) killed by TERM signal
[   18.214577] init: lightdm main process (955) killed by TERM signal
[   19.619114] init: plymouth-stop pre-start process (1104) terminated with status 1
[   27.423706] eth0: no IPv6 routers present

```

---

