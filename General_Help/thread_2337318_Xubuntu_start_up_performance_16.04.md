---
title: "Xubuntu start up performance 16.04"
date: 2016-09-16
forum: General Help
---

### Post by sean45xubu on 2016-09-16
Hi,

I upgraded to 16.04 a while back when it was released and have noticed the startup time is now much longer (Though it was never that fast). 

I know a few bits about linux but unsure where to start....

My laptop is quite decent but a little older, Core i7, 8GB ram, no SSD. Still i feel the boot time should be faster??

systemd-analyze plot > filenamexxx.svg

[http://imgh.us/filenamexxx.svg](http://imgh.us/filenamexxx.svg)

Dmesg:

```



[ 0.000000] PM: Registered nosave memory: [mem 0x9a3bf000-0x9aebefff][ 0.000000] PM: Registered nosave memory: [mem 0x9aebf000-0x9afbefff]
[ 0.000000] PM: Registered nosave memory: [mem 0x9afbf000-0x9affefff]
[ 0.000000] PM: Registered nosave memory: [mem 0x9b000000-0x9f9fffff]
[ 0.000000] PM: Registered nosave memory: [mem 0x9fa00000-0xdfffffff]
[ 0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
[ 0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfeafffff]
[ 0.000000] PM: Registered nosave memory: [mem 0xfeb00000-0xfeb03fff]
[ 0.000000] PM: Registered nosave memory: [mem 0xfeb04000-0xfebfffff]
[ 0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
[ 0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfed0ffff]
[ 0.000000] PM: Registered nosave memory: [mem 0xfed10000-0xfed19fff]
[ 0.000000] PM: Registered nosave memory: [mem 0xfed1a000-0xfed1bfff]
[ 0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff]
[ 0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff]
[ 0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
[ 0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xffb7ffff]
[ 0.000000] PM: Registered nosave memory: [mem 0xffb80000-0xffffffff]
[ 0.000000] e820: [mem 0x9fa00000-0xdfffffff] available for PCI devices
[ 0.000000] Booting paravirtualized kernel on bare hardware
[ 0.000000] clocksource: refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645519600211568 ns
[ 0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[ 0.000000] PERCPU: Embedded 33 pages/cpu @ffff88025f200000 s98008 r8192 d28968 u262144
[ 0.000000] pcpu-alloc: s98008 r8192 d28968 u262144 alloc=1*2097152
[ 0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[ 0.000000] Built 1 zonelists in Node order, mobility grouping on. Total pages: 2032951
[ 0.000000] Policy zone: Normal
[ 0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-36-generic root=UUID=571f07f2-fe1f-4c77-a667-5f63f1ce8e01 ro quiet splash radeon.runpm=0 modeset=1 vt.handoff=7
[ 0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[ 0.000000] Calgary: detecting Calgary via BIOS EBDA area
[ 0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[ 0.000000] Memory: 8008380K/8260972K available (8394K kernel code, 1282K rwdata, 3944K rodata, 1480K init, 1292K bss, 252592K reserved, 0K cma-reserved)
[ 0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[ 0.000000] Hierarchical RCU implementation.
[ 0.000000]     Build-time adjustment of leaf fanout to 64.
[ 0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[ 0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=64, nr_cpu_ids=8
[ 0.000000] NR_IRQS:16640 nr_irqs:488 16
[ 0.000000] vt handoff: transparent VT on vt#7
[ 0.000000] Console: colour dummy device 80x25
[ 0.000000] console [tty0] enabled
[ 0.000000] clocksource: hpet: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 133484882848 ns
[ 0.000000] hpet clockevent registered
[ 0.000000] tsc: Fast TSC calibration using PIT
[ 0.000000] tsc: Detected 2095.143 MHz processor
[ 0.000041] Calibrating delay loop (skipped), value calculated using timer frequency.. 4190.28 BogoMIPS (lpj=8380572)
[ 0.000043] pid_max: default: 32768 minimum: 301
[ 0.000050] ACPI: Core revision 20150930
[ 0.008127] ACPI: 5 ACPI AML tables successfully acquired and loaded
[ 0.008152] Security Framework initialized
[ 0.008154] Yama: becoming mindful.
[ 0.008170] AppArmor: AppArmor initialized
[ 0.008726] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[ 0.011026] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[ 0.012067] Mount-cache hash table entries: 16384 (order: 5, 131072 bytes)
[ 0.012078] Mountpoint-cache hash table entries: 16384 (order: 5, 131072 bytes)
[ 0.012304] Initializing cgroup subsys io
[ 0.012308] Initializing cgroup subsys memory
[ 0.012314] Initializing cgroup subsys devices
[ 0.012316] Initializing cgroup subsys freezer
[ 0.012318] Initializing cgroup subsys net_cls
[ 0.012320] Initializing cgroup subsys perf_event
[ 0.012322] Initializing cgroup subsys net_prio
[ 0.012325] Initializing cgroup subsys hugetlb
[ 0.012328] Initializing cgroup subsys pids
[ 0.012352] CPU: Physical Processor ID: 0
[ 0.012353] CPU: Processor Core ID: 0
[ 0.012359] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[ 0.012360] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[ 0.012782] mce: CPU supports 9 MCE banks
[ 0.012797] CPU0: Thermal monitoring enabled (TM1)
[ 0.012804] process: using mwait in idle threads
[ 0.012807] Last level iTLB entries: 4KB 512, 2MB 8, 4MB 8
[ 0.012808] Last level dTLB entries: 4KB 512, 2MB 32, 4MB 32, 1GB 0
[ 0.013294] Freeing SMP alternatives memory: 28K (ffffffff820b4000 - ffffffff820bb000)
[ 0.028639] ftrace: allocating 31996 entries in 125 pages
[ 0.045294] smpboot: Max logical packages: 2
[ 0.045296] smpboot: APIC(0) Converting physical 0 to logical package 0
[ 0.045371] x2apic: IRQ remapping doesn't support X2APIC mode
[ 0.045827] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[ 0.085515] TSC deadline timer enabled
[ 0.085519] smpboot: CPU0: Intel(R) Core(TM) i7-3612QM CPU @ 2.10GHz (family: 0x6, model: 0x3a, stepping: 0x9)
[ 0.085536] Performance Events: PEBS fmt1+, 16-deep LBR, IvyBridge events, full-width counters, Intel PMU driver.
[ 0.085559] ... version: 3
[ 0.085560] ... bit width: 48
[ 0.085561] ... generic registers: 4
[ 0.085562] ... value mask: 0000ffffffffffff
[ 0.085563] ... max period: 0000ffffffffffff
[ 0.085564] ... fixed-purpose events: 3
[ 0.085565] ... event mask: 000000070000000f
[ 0.086458] x86: Booting SMP configuration:
[ 0.086460] .... node #0, CPUs: #1
[ 0.089529] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[ 0.089616] #2
[ 0.090388] microcode: CPU2 microcode updated early to revision 0x1c, date = 2015-02-26
[ 0.092989] #3
[ 0.095895] #4
[ 0.096628] microcode: CPU4 microcode updated early to revision 0x1c, date = 2015-02-26
[ 0.099236] #5
[ 0.102157] #6
[ 0.102990] microcode: CPU6 microcode updated early to revision 0x1c, date = 2015-02-26
[ 0.105619] #7
[ 0.108477] x86: Booted up 1 node, 8 CPUs
[ 0.108481] smpboot: Total of 8 processors activated (33522.28 BogoMIPS)
[ 0.116449] devtmpfs: initialized
[ 0.120935] evm: security.selinux
[ 0.120937] evm: security.SMACK64
[ 0.120938] evm: security.SMACK64EXEC
[ 0.120939] evm: security.SMACK64TRANSMUTE
[ 0.120939] evm: security.SMACK64MMAP
[ 0.120940] evm: security.ima
[ 0.120941] evm: security.capability
[ 0.121029] PM: Registering ACPI NVS region [mem 0x9aebf000-0x9afbefff] (1048576 bytes)
[ 0.121140] clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
[ 0.121242] pinctrl core: initialized pinctrl subsystem
[ 0.121357] RTC time: 12:01:32, date: 09/17/16
[ 0.121477] NET: Registered protocol family 16
[ 0.144243] cpuidle: using governor ladder
[ 0.156250] cpuidle: using governor menu
[ 0.156257] PCCT header not found.
[ 0.156326] Simple Boot Flag at 0x44 set to 0x1
[ 0.156358] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[ 0.156360] ACPI: bus type PCI registered
[ 0.156362] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[ 0.156440] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[ 0.156443] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[ 0.156456] PCI: Using configuration type 1 for base access
[ 0.156464] dmi type 0xB1 record - unknown flag
[ 0.156516] core: PMU erratum BJ122, BV98, HSD29 worked around, HT is on
[ 0.172640] ACPI: Added _OSI(Module Device)
[ 0.172642] ACPI: Added _OSI(Processor Device)
[ 0.172643] ACPI: Added _OSI(3.0 _SCP Extensions)
[ 0.172645] ACPI: Added _OSI(Processor Aggregator Device)
[ 0.175329] ACPI: Executed 1 blocks of module-level executable AML code
[ 0.178207] ACPI: Dynamic OEM Table Load:
[ 0.178217] ACPI: SSDT 0xFFFF88025574C000 00083B (v01 PmRef Cpu0Cst 00003001 INTL 20121220)
[ 0.178774] ACPI: Dynamic OEM Table Load:
[ 0.178780] ACPI: SSDT 0xFFFF8802556F6400 000303 (v01 PmRef ApIst 00003000 INTL 20121220)
[ 0.179253] ACPI: Dynamic OEM Table Load:
[ 0.179258] ACPI: SSDT 0xFFFF8802556EEE00 000119 (v01 PmRef ApCst 00003000 INTL 20121220)
[ 0.180798] ACPI : EC: EC started
[ 0.180902] ACPI: Interpreter enabled
[ 0.180909] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20150930/hwxface-580)
[ 0.180914] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20150930/hwxface-580)
[ 0.180929] ACPI: (supports S0 S3 S4 S5)
[ 0.180930] ACPI: Using IOAPIC for interrupt routing
[ 0.180956] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[ 0.328513] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[ 0.328519] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[ 0.328646] \_SB_.PCI0:_OSC invalid UUID
[ 0.328647] _OSC request data:1 1f 0 
[ 0.328651] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM
[ 0.329063] PCI host bridge to bus 0000:00
[ 0.329066] pci_bus 0000:00: root bus resource [io 0x0000-0x0cf7 window]
[ 0.329068] pci_bus 0000:00: root bus resource [io 0x0d00-0xffff window]
[ 0.329070] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff window]
[ 0.329072] pci_bus 0000:00: root bus resource [mem 0x9fa00000-0xfeafffff window]
[ 0.329074] pci_bus 0000:00: root bus resource [bus 00-fe]
[ 0.329082] pci 0000:00:00.0: [8086:0154] type 00 class 0x060000
[ 0.329168] pci 0000:00:01.0: [8086:0151] type 01 class 0x060400
[ 0.329204] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[ 0.329238] pci 0000:00:01.0: System wakeup disabled by ACPI
[ 0.329282] pci 0000:00:02.0: [8086:0166] type 00 class 0x030000
[ 0.329296] pci 0000:00:02.0: reg 0x10: [mem 0xc1000000-0xc13fffff 64bit]
[ 0.329302] pci 0000:00:02.0: reg 0x18: [mem 0xb0000000-0xbfffffff 64bit pref]
[ 0.329307] pci 0000:00:02.0: reg 0x20: [io 0x4000-0x403f]
[ 0.329423] pci 0000:00:14.0: [8086:1e31] type 00 class 0x0c0330
[ 0.329456] pci 0000:00:14.0: reg 0x10: [mem 0xc1600000-0xc160ffff 64bit]
[ 0.329520] pci 0000:00:14.0: PME# supported from D3hot D3cold
[ 0.329564] pci 0000:00:14.0: System wakeup disabled by ACPI
[ 0.329607] pci 0000:00:16.0: [8086:1e3a] type 00 class 0x078000
[ 0.329637] pci 0000:00:16.0: reg 0x10: [mem 0xc1614000-0xc161400f 64bit]
[ 0.329696] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[ 0.329775] pci 0000:00:1a.0: [8086:1e2d] type 00 class 0x0c0320
[ 0.329805] pci 0000:00:1a.0: reg 0x10: [mem 0xc1619000-0xc16193ff]
[ 0.329883] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[ 0.329959] pci 0000:00:1b.0: [8086:1e20] type 00 class 0x040300
[ 0.329988] pci 0000:00:1b.0: reg 0x10: [mem 0xc1610000-0xc1613fff 64bit]
[ 0.330054] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[ 0.330130] pci 0000:00:1c.0: [8086:1e10] type 01 class 0x060400
[ 0.330211] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[ 0.330258] pci 0000:00:1c.0: System wakeup disabled by ACPI
[ 0.330301] pci 0000:00:1c.1: [8086:1e12] type 01 class 0x060400
[ 0.330381] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[ 0.330419] pci 0000:00:1c.1: System wakeup disabled by ACPI
[ 0.330469] pci 0000:00:1d.0: [8086:1e26] type 00 class 0x0c0320
[ 0.330499] pci 0000:00:1d.0: reg 0x10: [mem 0xc1618000-0xc16183ff]
[ 0.330577] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[ 0.330626] pci 0000:00:1d.0: System wakeup disabled by ACPI
[ 0.330669] pci 0000:00:1f.0: [8086:1e57] type 00 class 0x060100
[ 0.330841] pci 0000:00:1f.2: [8086:1e03] type 00 class 0x010601
[ 0.330867] pci 0000:00:1f.2: reg 0x10: [io 0x4088-0x408f]
[ 0.330875] pci 0000:00:1f.2: reg 0x14: [io 0x4094-0x4097]
[ 0.330884] pci 0000:00:1f.2: reg 0x18: [io 0x4080-0x4087]
[ 0.330892] pci 0000:00:1f.2: reg 0x1c: [io 0x4090-0x4093]
[ 0.330901] pci 0000:00:1f.2: reg 0x20: [io 0x4060-0x407f]
[ 0.330910] pci 0000:00:1f.2: reg 0x24: [mem 0xc1617000-0xc16177ff]
[ 0.330945] pci 0000:00:1f.2: PME# supported from D3hot
[ 0.331014] pci 0000:00:1f.3: [8086:1e22] type 00 class 0x0c0500
[ 0.331033] pci 0000:00:1f.3: reg 0x10: [mem 0xc1615000-0xc16150ff 64bit]
[ 0.331055] pci 0000:00:1f.3: reg 0x20: [io 0x4040-0x405f]
[ 0.331195] pci 0000:01:00.0: [1002:682f] type 00 class 0x030000
[ 0.331213] pci 0000:01:00.0: reg 0x10: [mem 0xa0000000-0xafffffff 64bit pref]
[ 0.331220] pci 0000:01:00.0: reg 0x18: [mem 0xc0000000-0xc003ffff 64bit]
[ 0.331224] pci 0000:01:00.0: reg 0x20: [io 0x3000-0x30ff]
[ 0.331232] pci 0000:01:00.0: reg 0x30: [mem 0xfffe0000-0xffffffff pref]
[ 0.331254] pci 0000:01:00.0: supports D1 D2
[ 0.331256] pci 0000:01:00.0: PME# supported from D1 D2 D3hot
[ 0.331331] pci 0000:01:00.0: System wakeup disabled by ACPI
[ 0.336373] pci 0000:00:01.0: PCI bridge to [bus 01-06]
[ 0.336378] pci 0000:00:01.0: bridge window [io 0x3000-0x3fff]
[ 0.336391] pci 0000:00:01.0: bridge window [mem 0xc0000000-0xc0ffffff]
[ 0.336395] pci 0000:00:01.0: bridge window [mem 0xa0000000-0xafffffff 64bit pref]
[ 0.336528] pci 0000:07:00.0: [10ec:8168] type 00 class 0x020000
[ 0.336706] pci 0000:07:00.0: reg 0x10: [io 0x2000-0x20ff]
[ 0.336830] pci 0000:07:00.0: reg 0x18: [mem 0xc1404000-0xc1404fff 64bit pref]
[ 0.336907] pci 0000:07:00.0: reg 0x20: [mem 0xc1400000-0xc1403fff 64bit pref]
[ 0.337205] pci 0000:07:00.0: supports D1 D2
[ 0.337207] pci 0000:07:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[ 0.344427] pci 0000:00:1c.0: PCI bridge to [bus 07]
[ 0.344432] pci 0000:00:1c.0: bridge window [io 0x2000-0x2fff]
[ 0.344441] pci 0000:00:1c.0: bridge window [mem 0xc1400000-0xc14fffff 64bit pref]
[ 0.344556] pci 0000:08:00.0: [8086:0887] type 00 class 0x028000
[ 0.344645] pci 0000:08:00.0: reg 0x10: [mem 0xc1500000-0xc1501fff 64bit]
[ 0.344875] pci 0000:08:00.0: PME# supported from D0 D3hot D3cold
[ 0.352451] pci 0000:00:1c.1: PCI bridge to [bus 08]
[ 0.352458] pci 0000:00:1c.1: bridge window [mem 0xc1500000-0xc15fffff]
[ 0.424692] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 10 11 12 14 15) *7
[ 0.424747] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 10 *11 12 14 15)
[ 0.424799] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[ 0.424851] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 *10 11 12 14 15)
[ 0.424901] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[ 0.424952] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 10 11 12 14 15) *7
[ 0.425003] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 *10 11 12 14 15)
[ 0.425055] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 10 *11 12 14 15)
[ 0.425184] ACPI: Enabled 5 GPEs in block 00 to 3F
[ 0.425221] ACPI : EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[ 0.425320] vgaarb: setting as boot device: PCI:0000:00:02.0
[ 0.425323] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[ 0.425327] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=none,locks=none
[ 0.425328] vgaarb: loaded
[ 0.425329] vgaarb: bridge control possible 0000:01:00.0
[ 0.425330] vgaarb: no bridge control possible 0000:00:02.0
[ 0.425600] SCSI subsystem initialized
[ 0.425641] libata version 3.00 loaded.
[ 0.425663] ACPI: bus type USB registered
[ 0.425680] usbcore: registered new interface driver usbfs
[ 0.425689] usbcore: registered new interface driver hub
[ 0.425713] usbcore: registered new device driver usb
[ 0.425866] PCI: Using ACPI for IRQ routing
[ 0.432639] PCI: pci_cache_line_size set to 64 bytes
[ 0.432736] e820: reserve RAM buffer [mem 0x0009d400-0x0009ffff]
[ 0.432738] e820: reserve RAM buffer [mem 0x40004000-0x43ffffff]
[ 0.432739] e820: reserve RAM buffer [mem 0x8ffb0000-0x8fffffff]
[ 0.432741] e820: reserve RAM buffer [mem 0x9a3bf000-0x9bffffff]
[ 0.432742] e820: reserve RAM buffer [mem 0x9b000000-0x9bffffff]
[ 0.432744] e820: reserve RAM buffer [mem 0x25f600000-0x25fffffff]
[ 0.432861] NetLabel: Initializing
[ 0.432862] NetLabel: domain hash size = 128
[ 0.432863] NetLabel: protocols = UNLABELED CIPSOv4
[ 0.432877] NetLabel: unlabeled traffic allowed by default
[ 0.432965] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[ 0.432970] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[ 0.434981] amd_nb: Cannot enumerate AMD northbridges
[ 0.434998] clocksource: Switched to clocksource hpet
[ 0.441182] AppArmor: AppArmor Filesystem Enabled
[ 0.441249] pnp: PnP ACPI init
[ 0.441380] system 00:00: [io 0x0680-0x069f] has been reserved
[ 0.441382] system 00:00: [io 0x1000-0x100f] has been reserved
[ 0.441384] system 00:00: [io 0xffff] has been reserved
[ 0.441386] system 00:00: [io 0xffff] has been reserved
[ 0.441388] system 00:00: [io 0x0400-0x0453] could not be reserved
[ 0.441390] system 00:00: [io 0x0458-0x047f] has been reserved
[ 0.441392] system 00:00: [io 0x0500-0x057f] has been reserved
[ 0.441394] system 00:00: [io 0x164e-0x164f] has been reserved
[ 0.441396] system 00:00: [io 0xfd60-0xfd63] has been reserved
[ 0.441400] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[ 0.441428] pnp 00:01: Plug and Play ACPI device, IDs PNP0b00 (active)
[ 0.441480] system 00:02: [io 0x0454-0x0457] has been reserved
[ 0.441483] system 00:02: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[ 0.441515] pnp 00:03: Plug and Play ACPI device, IDs PNP0303 (active)
[ 0.441544] pnp 00:04: Plug and Play ACPI device, IDs DLL0572 PNP0f13 (active)
[ 0.511164] system 00:05: [mem 0xfed1c000-0xfed1ffff] has been reserved
[ 0.511167] system 00:05: [mem 0xfed10000-0xfed17fff] has been reserved
[ 0.511170] system 00:05: [mem 0xfed18000-0xfed18fff] has been reserved
[ 0.511172] system 00:05: [mem 0xfed19000-0xfed19fff] has been reserved
[ 0.511174] system 00:05: [mem 0xe0000000-0xefffffff] has been reserved
[ 0.511176] system 00:05: [mem 0xfed20000-0xfed3ffff] has been reserved
[ 0.511177] system 00:05: [mem 0xfed90000-0xfed93fff] has been reserved
[ 0.511179] system 00:05: [mem 0xff000000-0xff000fff] has been reserved
[ 0.511182] system 00:05: [mem 0xff010000-0xffffffff] could not be reserved
[ 0.511184] system 00:05: [mem 0xfee00000-0xfeefffff] could not be reserved
[ 0.511186] system 00:05: [mem 0x9fa00000-0x9fa00fff] has been reserved
[ 0.511189] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[ 0.511505] system 00:06: [mem 0x20000000-0x201fffff] has been reserved
[ 0.511508] system 00:06: [mem 0x40004000-0x40004fff] has been reserved
[ 0.511510] system 00:06: Plug and Play ACPI device, IDs PNP0c01 (active)
[ 0.511527] pnp: PnP ACPI: found 7 devices
[ 0.517948] clocksource: acpi_pm: mask: 0xffffff max_cycles: 0xffffff, max_idle_ns: 2085701024 ns
[ 0.517956] pci 0000:01:00.0: can't claim BAR 6 [mem 0xfffe0000-0xffffffff pref]: no compatible bridge window
[ 0.517984] pci 0000:01:00.0: BAR 6: assigned [mem 0xc0040000-0xc005ffff pref]
[ 0.517987] pci 0000:00:01.0: PCI bridge to [bus 01-06]
[ 0.517989] pci 0000:00:01.0: bridge window [io 0x3000-0x3fff]
[ 0.517993] pci 0000:00:01.0: bridge window [mem 0xc0000000-0xc0ffffff]
[ 0.517995] pci 0000:00:01.0: bridge window [mem 0xa0000000-0xafffffff 64bit pref]
[ 0.517999] pci 0000:00:1c.0: PCI bridge to [bus 07]
[ 0.518002] pci 0000:00:1c.0: bridge window [io 0x2000-0x2fff]
[ 0.518010] pci 0000:00:1c.0: bridge window [mem 0xc1400000-0xc14fffff 64bit pref]
[ 0.518017] pci 0000:00:1c.1: PCI bridge to [bus 08]
[ 0.518022] pci 0000:00:1c.1: bridge window [mem 0xc1500000-0xc15fffff]
[ 0.518033] pci_bus 0000:00: resource 4 [io 0x0000-0x0cf7 window]
[ 0.518035] pci_bus 0000:00: resource 5 [io 0x0d00-0xffff window]
[ 0.518037] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff window]
[ 0.518038] pci_bus 0000:00: resource 7 [mem 0x9fa00000-0xfeafffff window]
[ 0.518040] pci_bus 0000:01: resource 0 [io 0x3000-0x3fff]
[ 0.518042] pci_bus 0000:01: resource 1 [mem 0xc0000000-0xc0ffffff]
[ 0.518044] pci_bus 0000:01: resource 2 [mem 0xa0000000-0xafffffff 64bit pref]
[ 0.518046] pci_bus 0000:07: resource 0 [io 0x2000-0x2fff]
[ 0.518047] pci_bus 0000:07: resource 2 [mem 0xc1400000-0xc14fffff 64bit pref]
[ 0.518049] pci_bus 0000:08: resource 1 [mem 0xc1500000-0xc15fffff]
[ 0.518084] NET: Registered protocol family 2
[ 0.518249] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
[ 0.518388] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[ 0.518513] TCP: Hash tables configured (established 65536 bind 65536)
[ 0.518537] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[ 0.518564] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[ 0.518626] NET: Registered protocol family 1
[ 0.518644] pci 0000:00:02.0: Video device with shadowed ROM
[ 0.551143] PCI: CLS 64 bytes, default 64
[ 0.551195] Trying to unpack rootfs image as initramfs...
[ 1.162980] Freeing initrd memory: 35560K (ffff880033a7c000 - ffff880035d36000)
[ 1.163015] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[ 1.163017] software IO TLB [mem 0x963bf000-0x9a3bf000] (64MB) mapped at [ffff8800963bf000-ffff88009a3befff]
[ 1.163120] RAPL PMU detected, API unit is 2^-32 Joules, 3 fixed counters 163840 ms ovfl timer
[ 1.163122] hw unit of domain pp0-core 2^-16 Joules
[ 1.163123] hw unit of domain package 2^-16 Joules
[ 1.163124] hw unit of domain pp1-gpu 2^-16 Joules
[ 1.163312] Scanning for low memory corruption every 60 seconds
[ 1.163693] futex hash table entries: 2048 (order: 5, 131072 bytes)
[ 1.163730] audit: initializing netlink subsys (disabled)
[ 1.163744] audit: type=2000 audit(1474113693.140:1): initialized
[ 1.164248] Initialise system trusted keyring
[ 1.164383] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[ 1.165915] zbud: loaded
[ 1.166134] VFS: Disk quotas dquot_6.6.0
[ 1.166168] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[ 1.166435] squashfs: version 4.0 (2009/01/31) Phillip Lougher
[ 1.166676] fuse init (API version 7.23)
[ 1.166819] Key type big_key registered
[ 1.166850] Allocating IMA MOK and blacklist keyrings.
[ 1.167310] Key type asymmetric registered
[ 1.167312] Asymmetric key parser 'x509' registered
[ 1.167348] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 249)
[ 1.167392] io scheduler noop registered
[ 1.167395] io scheduler deadline registered (default)
[ 1.167425] io scheduler cfq registered
[ 1.167894] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[ 1.167903] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[ 1.167932] vesafb: mode is 1920x1080x32, linelength=7680, pages=0
[ 1.167933] vesafb: scrolling: redraw
[ 1.167935] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[ 1.167946] vesafb: framebuffer at 0xb0000000, mapped to 0xffffc90001000000, using 8128k, total 8128k
[ 1.168055] Console: switching to colour frame buffer device 240x67
[ 1.168086] fb0: VESA VGA frame buffer device
[ 1.168104] intel_idle: MWAIT substates: 0x21120
[ 1.168106] intel_idle: v0.4.1 model 0x3A
[ 1.168107] intel_idle: lapic_timer_reliable_states 0xffffffff
[ 1.168475] ACPI: AC Adapter [ACAD] (on-line)
[ 1.168540] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0C:00/input/input0
[ 1.168544] ACPI: Power Button [PWRB]
[ 1.168588] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[ 1.168609] ACPI: Lid Switch [LID0]
[ 1.168646] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[ 1.168648] ACPI: Power Button [PWRF]
[ 1.169167] GHES: HEST is not enabled!
[ 1.169296] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[ 1.407068] ACPI: Battery Slot [BAT1] (battery present)
[ 1.407329] Linux agpgart interface v0.103
[ 1.411270] brd: module loaded
[ 1.413083] loop: module loaded
[ 1.413306] libphy: Fixed MDIO Bus: probed
[ 1.413309] tun: Universal TUN/TAP device driver, 1.6
[ 1.413310] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[ 1.413359] PPP generic driver version 2.4.2
[ 1.413422] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[ 1.413427] ehci-pci: EHCI PCI platform driver
[ 1.413542] ehci-pci 0000:00:1a.0: EHCI Host Controller
[ 1.413548] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[ 1.413561] ehci-pci 0000:00:1a.0: debug port 2
[ 1.417452] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[ 1.417464] ehci-pci 0000:00:1a.0: irq 16, io mem 0xc1619000
[ 1.427063] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[ 1.427107] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[ 1.427109] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[ 1.427111] usb usb1: Product: EHCI Host Controller
[ 1.427112] usb usb1: Manufacturer: Linux 4.4.0-36-generic ehci_hcd
[ 1.427114] usb usb1: SerialNumber: 0000:00:1a.0
[ 1.427265] hub 1-0:1.0: USB hub found
[ 1.427271] hub 1-0:1.0: 2 ports detected
[ 1.427468] ehci-pci 0000:00:1d.0: EHCI Host Controller
[ 1.427473] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[ 1.427485] ehci-pci 0000:00:1d.0: debug port 2
[ 1.431398] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[ 1.431409] ehci-pci 0000:00:1d.0: irq 23, io mem 0xc1618000
[ 1.443059] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[ 1.443100] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[ 1.443102] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[ 1.443104] usb usb2: Product: EHCI Host Controller
[ 1.443106] usb usb2: Manufacturer: Linux 4.4.0-36-generic ehci_hcd
[ 1.443107] usb usb2: SerialNumber: 0000:00:1d.0
[ 1.443286] hub 2-0:1.0: USB hub found
[ 1.443294] hub 2-0:1.0: 2 ports detected
[ 1.443404] ehci-platform: EHCI generic platform driver
[ 1.443416] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[ 1.443422] ohci-pci: OHCI PCI platform driver
[ 1.443432] ohci-platform: OHCI generic platform driver
[ 1.443440] uhci_hcd: USB Universal Host Controller Interface driver
[ 1.443565] xhci_hcd 0000:00:14.0: xHCI Host Controller
[ 1.443570] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
[ 1.444661] xhci_hcd 0000:00:14.0: hcc params 0x20007181 hci version 0x100 quirks 0x0000b930
[ 1.444667] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[ 1.444748] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[ 1.444750] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[ 1.444751] usb usb3: Product: xHCI Host Controller
[ 1.444753] usb usb3: Manufacturer: Linux 4.4.0-36-generic xhci-hcd
[ 1.444755] usb usb3: SerialNumber: 0000:00:14.0
[ 1.444938] hub 3-0:1.0: USB hub found
[ 1.444951] hub 3-0:1.0: 4 ports detected
[ 1.445301] xhci_hcd 0000:00:14.0: xHCI Host Controller
[ 1.445306] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 4
[ 1.445339] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
[ 1.445341] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[ 1.445343] usb usb4: Product: xHCI Host Controller
[ 1.445344] usb usb4: Manufacturer: Linux 4.4.0-36-generic xhci-hcd
[ 1.445346] usb usb4: SerialNumber: 0000:00:14.0
[ 1.445528] hub 4-0:1.0: USB hub found
[ 1.445540] hub 4-0:1.0: 4 ports detected
[ 1.445949] i8042: PNP: PS/2 Controller [PNP0303S2K,PNP0f13S2M] at 0x60,0x64 irq 1,12
[ 1.458266] serio: i8042 KBD port at 0x60,0x64 irq 1
[ 1.458472] mousedev: PS/2 mouse device common for all mice
[ 1.460910] rtc_cmos 00:01: RTC can wake from S4
[ 1.461118] rtc_cmos 00:01: rtc core: registered rtc_cmos as rtc0
[ 1.461151] rtc_cmos 00:01: alarms up to one month, 242 bytes nvram, hpet irqs
[ 1.461163] i2c /dev entries driver
[ 1.461225] device-mapper: uevent: version 1.0.3
[ 1.461353] device-mapper: ioctl: 4.34.0-ioctl (2015-10-28) initialised: [email]dm-devel@redhat.com[/email]
[ 1.461375] Intel P-state driver initializing.
[ 1.474783] ledtrig-cpu: registered to indicate activity on CPUs
[ 1.475743] NET: Registered protocol family 10
[ 1.476108] NET: Registered protocol family 17
[ 1.476153] Key type dns_resolver registered
[ 1.479094] microcode: CPU0 sig=0x306a9, pf=0x10, revision=0x1c
[ 1.479111] microcode: CPU1 sig=0x306a9, pf=0x10, revision=0x1c
[ 1.479120] microcode: CPU2 sig=0x306a9, pf=0x10, revision=0x1c
[ 1.479139] microcode: CPU3 sig=0x306a9, pf=0x10, revision=0x1c
[ 1.479188] microcode: CPU4 sig=0x306a9, pf=0x10, revision=0x1c
[ 1.479197] microcode: CPU5 sig=0x306a9, pf=0x10, revision=0x1c
[ 1.479225] microcode: CPU6 sig=0x306a9, pf=0x10, revision=0x1c
[ 1.479234] microcode: CPU7 sig=0x306a9, pf=0x10, revision=0x1c
[ 1.479320] microcode: Microcode Update Driver: v2.01 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[ 1.479818] registered taskstats version 1
[ 1.479844] Loading compiled-in X.509 certificates
[ 1.481617] Loaded X.509 cert 'Build time autogenerated kernel key: 181cd957879f68b474ab1d0c92722cd44e756f77'
[ 1.481660] zswap: loaded using pool lzo/zbud
[ 1.484408] Key type trusted registered
[ 1.487783] Key type encrypted registered
[ 1.487790] AppArmor: AppArmor sha1 policy hashing enabled
[ 1.487794] ima: No TPM chip found, activating TPM-bypass!
[ 1.487814] evm: HMAC attrs: 0x1
[ 1.488129] Magic number: 0:529:26
[ 1.488170] memory memory66: hash matches
[ 1.488232] rtc_cmos 00:01: setting system clock to 2016-09-17 12:01:33 UTC (1474113693)
[ 1.488292] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[ 1.488293] EDD information not available.
[ 1.488360] PM: Hibernation image not present or could not be loaded.
[ 1.489374] Freeing unused kernel memory: 1480K (ffffffff81f42000 - ffffffff820b4000)
[ 1.489375] Write protecting the kernel read-only data: 14336k
[ 1.489822] Freeing unused kernel memory: 1832K (ffff880001836000 - ffff880001a00000)
[ 1.490151] Freeing unused kernel memory: 152K (ffff880001dda000 - ffff880001e00000)
[ 1.499595] random: systemd-udevd urandom read with 8 bits of entropy available
[ 1.512734] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[ 1.520206] FUJITSU Extended Socket Network Device Driver - version 1.0 - Copyright (c) 2015 FUJITSU LIMITED
[ 1.527135] wmi: Mapper loaded
[ 1.532116] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[ 1.532125] r8169 0000:07:00.0: can't disable ASPM; OS doesn't have ASPM control
[ 1.532177] [drm] Initialized drm 1.1.0 20060810
[ 1.532703] r8169 0000:07:00.0 eth0: RTL8168evl/8111evl at 0xffffc90000c6c000, d4:be:d9:58:71:1c, XID 0c900800 IRQ 26
[ 1.532706] r8169 0000:07:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[ 1.533228] ahci 0000:00:1f.2: version 3.0
[ 1.547406] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x5 impl SATA mode
[ 1.547411] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part ems apst 
[ 1.552070] r8169 0000:07:00.0 enp7s0: renamed from eth0
[ 1.555800] scsi host0: ahci
[ 1.555926] scsi host1: ahci
[ 1.556034] scsi host2: ahci
[ 1.556141] scsi host3: ahci
[ 1.556247] scsi host4: ahci
[ 1.556352] scsi host5: ahci
[ 1.556413] ata1: SATA max UDMA/133 abar m2048@0xc1617000 port 0xc1617100 irq 27
[ 1.556415] ata2: DUMMY
[ 1.556418] ata3: SATA max UDMA/133 abar m2048@0xc1617000 port 0xc1617200 irq 27
[ 1.556419] ata4: DUMMY
[ 1.556420] ata5: DUMMY
[ 1.556422] ata6: DUMMY
[ 1.557235] [drm] Memory usable by graphics device = 2048M
[ 1.557239] checking generic (b0000000 7f0000) vs hw (b0000000 10000000)
[ 1.557240] fb: switching to inteldrmfb from VESA VGA
[ 1.557263] Console: switching to colour dummy device 80x25
[ 1.557326] [drm] Replacing VGA console driver
[ 1.558371] [drm] radeon kernel modesetting enabled.
[ 1.558379] vga_switcheroo: detected switching method \_SB_.PCI0.GFX0.ATPX handle
[ 1.560251] AMD IOMMUv2 driver by Joerg Roedel <jroedel@suse.de>
[ 1.560253] AMD IOMMUv2 functionality not available on this system
[ 1.562692] CRAT table not found
[ 1.562694] Finished initializing topology ret=0
[ 1.562743] kfd kfd: Initialized module
[ 1.562931] radeon 0000:01:00.0: enabling device (0000 -> 0003)
[ 1.563178] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[ 1.563179] [drm] Driver supports precise vblank timestamp query.
[ 1.563561] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=nonewns=io+mem
[ 1.583239] [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS
[ 1.583731] ACPI: Video Device [PEGP] (multi-head: yes rom: no post: no)
[ 1.583860] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:2b/LNXVIDEO:00/input/input5
[ 1.583950] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[ 1.584419] ACPI: Video Device [GFX0] (multi-head: yes rom: no post: no)
[ 1.584510] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:02/input/input6
[ 1.584594] [drm] Initialized i915 1.6.0 20151010 for 0000:00:02.0 on minor 0
[ 1.584747] [drm] initializing kernel modesetting (VERDE 0x1002:0x682F 0x1028:0x0572).
[ 1.584759] [drm] register mmio base: 0xC0000000
[ 1.584760] [drm] register mmio size: 262144
[ 1.584762] vga_switcheroo: enabled
[ 1.584832] ATPX version 1, functions 0x00000033
[ 1.592918] ATOM BIOS: Dell/Compal
[ 1.593043] radeon 0000:01:00.0: VRAM: 2048M 0x0000000000000000 - 0x000000007FFFFFFF (2048M used)
[ 1.593044] radeon 0000:01:00.0: GTT: 2048M 0x0000000080000000 - 0x00000000FFFFFFFF
[ 1.593046] [drm] Detected VRAM RAM=2048M, BAR=256M
[ 1.593046] [drm] RAM width 128bits DDR
[ 1.593148] [TTM] Zone kernel: Available graphics memory: 4023716 kiB
[ 1.593149] [TTM] Zone dma32: Available graphics memory: 2097152 kiB
[ 1.593150] [TTM] Initializing pool allocator
[ 1.593155] [TTM] Initializing DMA pool allocator
[ 1.593177] [drm] radeon: 2048M of VRAM memory ready
[ 1.593177] [drm] radeon: 2048M of GTT memory ready.
[ 1.593185] [drm] Loading verde Microcode
[ 1.593278] [drm] Internal thermal controller with fan control
[ 1.593330] [drm] probing gen 2 caps for device 8086:151 = 261ac83/e
[ 1.599517] [drm] radeon: dpm initialized
[ 1.601413] [drm] Found VCE firmware/feedback version 50.0.1 / 17!
[ 1.601419] [drm] GART: num cpu pages 524288, num gpu pages 524288
[ 1.602268] [drm] probing gen 2 caps for device 8086:151 = 261ac83/e
[ 1.602272] [drm] enabling PCIE gen 3 link speeds, disable with radeon.pcie_gen2=0
[ 1.719535] fbcon: inteldrmfb (fb0) is primary device
[ 1.719614] Console: switching to colour frame buffer device 240x67
[ 1.719654] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[ 1.739093] usb 1-1: new high-speed USB device number 2 using ehci-pci
[ 1.755093] usb 2-1: new high-speed USB device number 2 using ehci-pci
[ 1.871430] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
[ 1.871432] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[ 1.871711] hub 1-1:1.0: USB hub found
[ 1.871774] hub 1-1:1.0: 6 ports detected
[ 1.875104] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 1.875128] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 1.877571] ata3.00: ATAPI: PLDS DVDRW/BDROM DS-6E2SH, CD12, max UDMA/100
[ 1.879203] ata3.00: configured for UDMA/100
[ 1.881363] ata1.00: ATA-8: ST1000LM024 HN-M101MBB, 2AR20002, max UDMA/133
[ 1.881365] ata1.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[ 1.887428] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
[ 1.887431] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[ 1.887637] ata1.00: configured for UDMA/133
[ 1.887744] hub 2-1:1.0: USB hub found
[ 1.887894] scsi 0:0:0:0: Direct-Access ATA ST1000LM024 HN-M 0002 PQ: 0 ANSI: 5
[ 1.887919] hub 2-1:1.0: 8 ports detected
[ 1.888161] sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/932 GiB)
[ 1.888245] sd 0:0:0:0: [sda] Write Protect is off
[ 1.888248] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 1.888306] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1.888335] sd 0:0:0:0: Attached scsi generic sg0 type 0
[ 1.898529] scsi 2:0:0:0: CD-ROM PLDS DVDRWBD DS-6E2SH CD12 PQ: 0 ANSI: 5
[ 1.926310] sr 2:0:0:0: [sr0] scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[ 1.926312] cdrom: Uniform CD-ROM driver Revision: 3.20
[ 1.926456] sr 2:0:0:0: Attached scsi CD-ROM sr0
[ 1.926515] sr 2:0:0:0: Attached scsi generic sg1 type 5
[ 1.952543] sda: sda1 sda2 < sda5 >
[ 1.953175] sd 0:0:0:0: [sda] Attached SCSI disk
[ 2.088872] [drm:intel_set_pch_fifo_underrun_reporting [i915]] *ERROR* uncleared pch fifo underrun on pch transcoder A
[ 2.088900] [drm:intel_pch_fifo_underrun_irq_handler [i915]] *ERROR* PCH transcoder A FIFO underrun
[ 2.143100] usb 1-1.3: new high-speed USB device number 3 using ehci-pci
[ 2.159110] usb 2-1.5: new full-speed USB device number 3 using ehci-pci
[ 2.235910] usb 1-1.3: New USB device found, idVendor=0bda, idProduct=0129
[ 2.235912] usb 1-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 2.235914] usb 1-1.3: Product: USB2.0-CRW
[ 2.235916] usb 1-1.3: Manufacturer: Generic
[ 2.235917] usb 1-1.3: SerialNumber: 20100201396000000
[ 2.240476] usbcore: registered new interface driver rtsx_usb
[ 2.255695] usb 2-1.5: New USB device found, idVendor=8087, idProduct=07da
[ 2.255698] usb 2-1.5: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[ 2.307110] usb 1-1.5: new high-speed USB device number 4 using ehci-pci
[ 2.476670] usb 1-1.5: New USB device found, idVendor=0c45, idProduct=644a
[ 2.476673] usb 1-1.5: New USB device strings: Mfr=2, Product=1, SerialNumber=0
[ 2.476675] usb 1-1.5: Product: Laptop_Integrated_Webcam_HD
[ 2.476676] usb 1-1.5: Manufacturer: CN00YCD67248727A1664A01
[ 2.833658] tsc: Refined TSC clocksource calibration: 2095.241 MHz
[ 2.833662] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x1e33a0d0b4e, max_idle_ns: 440795276795 ns
[ 2.836287] [drm] PCIE GART of 2048M enabled (table at 0x00000000002E8000).
[ 2.836390] radeon 0000:01:00.0: WB enabled
[ 2.836393] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000080000c00 and cpu addr 0xffff88003587dc00
[ 2.836394] radeon 0000:01:00.0: fence driver on ring 1 use gpu addr 0x0000000080000c04 and cpu addr 0xffff88003587dc04
[ 2.836395] radeon 0000:01:00.0: fence driver on ring 2 use gpu addr 0x0000000080000c08 and cpu addr 0xffff88003587dc08
[ 2.836397] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000080000c0c and cpu addr 0xffff88003587dc0c
[ 2.836398] radeon 0000:01:00.0: fence driver on ring 4 use gpu addr 0x0000000080000c10 and cpu addr 0xffff88003587dc10
[ 2.837173] radeon 0000:01:00.0: fence driver on ring 5 use gpu addr 0x0000000000075a18 and cpu addr 0xffffc90001435a18
[ 2.857215] radeon 0000:01:00.0: fence driver on ring 6 use gpu addr 0x0000000080000c18 and cpu addr 0xffff88003587dc18
[ 2.857217] radeon 0000:01:00.0: fence driver on ring 7 use gpu addr 0x0000000080000c1c and cpu addr 0xffff88003587dc1c
[ 2.857278] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[ 2.857280] [drm] Driver supports precise vblank timestamp query.
[ 2.857282] radeon 0000:01:00.0: radeon: MSI limited to 32-bit
[ 2.857319] radeon 0000:01:00.0: radeon: using MSI.
[ 2.857344] [drm] radeon: irq initialized.
[ 3.307309] [drm] ring test on 0 succeeded in 1 usecs
[ 3.307314] [drm] ring test on 1 succeeded in 1 usecs
[ 3.307318] [drm] ring test on 2 succeeded in 1 usecs
[ 3.307330] [drm] ring test on 3 succeeded in 9 usecs
[ 3.307335] [drm] ring test on 4 succeeded in 3 usecs
[ 3.483013] [drm] ring test on 5 succeeded in 2 usecs
[ 3.483017] [drm] UVD initialized successfully.
[ 3.592206] [drm] ring test on 6 succeeded in 20 usecs
[ 3.592217] [drm] ring test on 7 succeeded in 4 usecs
[ 3.592218] [drm] VCE initialized successfully.
[ 3.592402] [drm] ib test on ring 0 succeeded in 0 usecs
[ 3.592433] [drm] ib test on ring 1 succeeded in 0 usecs
[ 3.592460] [drm] ib test on ring 2 succeeded in 0 usecs
[ 3.592505] [drm] ib test on ring 3 succeeded in 0 usecs
[ 3.592550] [drm] ib test on ring 4 succeeded in 0 usecs
[ 3.831503] clocksource: Switched to clocksource tsc
[ 4.239318] [drm] ib test on ring 5 succeeded
[ 4.739353] [drm] ib test on ring 6 succeeded
[ 5.239366] [drm] ib test on ring 7 succeeded
[ 5.240728] [drm] Radeon Display Connectors
[ 5.249273] [drm] Initialized radeon 2.43.0 20080528 for 0000:01:00.0 on minor 1
[ 5.410730] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[ 5.654873] random: nonblocking pool is initialized
[ 6.760905] systemd[1]: systemd 229 running in system mode. (+PAM +AUDIT +SELINUX +IMA +APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT +GNUTLS +ACL +XZ -LZ4 +SECCOMP +BLKID +ELFUTILS +KMOD -IDN)
[ 6.761053] systemd[1]: Detected architecture x86-64.
[ 6.771318] systemd[1]: Set hostname to <sean-laptop>.
[ 8.866260] systemd[1]: Listening on Journal Socket (/dev/log).
[ 8.866304] systemd[1]: Reached target User and Group Name Lookups.
[ 8.866327] systemd[1]: Listening on /dev/initctl Compatibility Named Pipe.
[ 8.866353] systemd[1]: Started Forward Password Requests to Wall Directory Watch.
[ 8.866380] systemd[1]: Listening on udev Control Socket.
[ 8.866432] systemd[1]: Listening on Journal Audit Socket.
[ 8.866459] systemd[1]: Listening on Journal Socket.
[ 8.866472] systemd[1]: Reached target Encrypted Volumes.
[ 8.866569] systemd[1]: Set up automount Arbitrary Executable File Formats File System Automount Point.
[ 8.866637] systemd[1]: Created slice User and Session Slice.
[ 8.866645] systemd[1]: Reached target Remote File Systems (Pre).
[ 8.866651] systemd[1]: Reached target Remote File Systems.
[ 8.866670] systemd[1]: Listening on Syslog Socket.
[ 8.866718] systemd[1]: Created slice System Slice.
[ 8.875711] systemd[1]: Starting Uncomplicated firewall...
[ 8.876333] systemd[1]: Mounting POSIX Message Queue File System...
[ 8.876772] systemd[1]: Mounting Huge Pages File System...
[ 8.876798] systemd[1]: Reached target Slices.
[ 8.877157] systemd[1]: Starting Create list of required static device nodes for the current kernel...
[ 8.877533] systemd[1]: Started Braille Device Support.
[ 9.107571] systemd[1]: Starting Journal Service...
[ 9.107628] systemd[1]: Listening on fsck to fsckd communication Socket.
[ 9.108037] systemd[1]: Starting Set console keymap...
[ 9.108077] systemd[1]: Listening on udev Kernel Socket.
[ 9.108420] systemd[1]: Started Read required files in advance.
[ 9.227587] systemd[1]: Starting Load Kernel Modules...
[ 9.228198] systemd[1]: Mounting Debug File System...
[ 9.229311] systemd[1]: Started Uncomplicated firewall.
[ 9.364898] systemd[1]: Mounted Debug File System.
[ 9.364930] systemd[1]: Mounted POSIX Message Queue File System.
[ 9.364942] systemd[1]: Mounted Huge Pages File System.
[ 9.494138] systemd[1]: Started Create list of required static device nodes for the current kernel.
[ 9.507661] systemd[1]: Starting Create Static Device Nodes in /dev...
[ 10.576367] systemd[1]: Started Journal Service.
[ 11.252137] lp: driver loaded but no devices found
[ 11.277662] ppdev: user-space parallel port driver
[ 15.360691] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[ 15.828155] systemd-journald[286]: Received request to flush runtime journal from PID 1
[ 17.895444] ACPI Warning: SystemIO range 0x0000000000000428-0x000000000000042F conflicts with OpRegion 0x0000000000000400-0x000000000000047F (\PMIO) (20150930/utaddress-254)
[ 17.895450] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[ 17.895453] ACPI Warning: SystemIO range 0x0000000000000540-0x000000000000054F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20150930/utaddress-254)
[ 17.895456] ACPI Warning: SystemIO range 0x0000000000000540-0x000000000000054F conflicts with OpRegion 0x0000000000000500-0x000000000000055F (\_SB_.PCI0.PEG0.PEGP.GPIO) (20150930/utaddress-254)
[ 17.895459] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[ 17.895460] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20150930/utaddress-254)
[ 17.895462] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053F conflicts with OpRegion 0x0000000000000500-0x000000000000055F (\_SB_.PCI0.PEG0.PEGP.GPIO) (20150930/utaddress-254)
[ 17.895464] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[ 17.895465] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20150930/utaddress-254)
[ 17.895467] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052F conflicts with OpRegion 0x0000000000000500-0x000000000000055F (\_SB_.PCI0.PEG0.PEGP.GPIO) (20150930/utaddress-254)
[ 17.895470] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[ 17.895470] lpc_ich: Resource conflict(s) found affecting gpio_ich
[ 17.959061] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[ 17.998993] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[ 18.170107] AVX version of gcm_enc/dec engaged.
[ 18.170109] AES CTR mode by8 optimization enabled
[ 18.761125] input: Dell WMI hotkeys as /devices/virtual/input/input7
[ 20.167913] Intel(R) Wireless WiFi driver for Linux
[ 20.167916] Copyright(c) 2003- 2015 Intel Corporation
[ 20.168090] iwlwifi 0000:08:00.0: can't disable ASPM; OS doesn't have ASPM control
[ 21.271870] intel_rapl: Found RAPL domain package
[ 21.271873] intel_rapl: Found RAPL domain core
[ 21.271874] intel_rapl: Found RAPL domain uncore
[ 21.271878] intel_rapl: RAPL package 0 domain package locked by BIOS
[ 21.285827] media: Linux media interface: v0.10
[ 21.566782] Bluetooth: Core ver 2.21
[ 21.566795] NET: Registered protocol family 31
[ 21.566796] Bluetooth: HCI device and connection manager initialized
[ 21.566799] Bluetooth: HCI socket layer initialized
[ 21.566801] Bluetooth: L2CAP socket layer initialized
[ 21.566805] Bluetooth: SCO socket layer initialized
[ 21.571751] Linux video capture interface: v2.00
[ 21.621089] iwlwifi 0000:08:00.0: loaded firmware version 18.168.6.1 op_mode iwldvm
[ 21.981023] snd_hda_codec_conexant hdaudioC0D0: CX20590: BIOS auto-probing.
[ 21.981496] snd_hda_codec_conexant hdaudioC0D0: autoconfig for CX20590: line_outs=1 (0x1f/0x0/0x0/0x0/0x0) type:speaker
[ 21.981499] snd_hda_codec_conexant hdaudioC0D0: speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[ 21.981500] snd_hda_codec_conexant hdaudioC0D0: hp_outs=1 (0x19/0x0/0x0/0x0/0x0)
[ 21.981501] snd_hda_codec_conexant hdaudioC0D0: mono: mono_out=0x0
[ 21.981503] snd_hda_codec_conexant hdaudioC0D0: inputs:
[ 21.981504] snd_hda_codec_conexant hdaudioC0D0: Internal Mic=0x23
[ 21.981506] snd_hda_codec_conexant hdaudioC0D0: Mic=0x1a
[ 21.982574] snd_hda_codec_conexant hdaudioC0D0: Enable sync_write for stable communication
[ 22.410241] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[ 22.410292] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[ 22.410339] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[ 22.412595] usbcore: registered new interface driver btusb
[ 23.587306] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_HD (0c45:644a)
[ 23.599186] iwlwifi 0000:08:00.0: CONFIG_IWLWIFI_DEBUG disabled
[ 23.599188] iwlwifi 0000:08:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[ 23.599190] iwlwifi 0000:08:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[ 23.599191] iwlwifi 0000:08:00.0: Detected Intel(R) Centrino(R) Wireless-N 2230 BGN, REV=0xC8
[ 23.599285] iwlwifi 0000:08:00.0: L1 Enabled - LTR Disabled
[ 23.613493] input: Laptop_Integrated_Webcam_HD as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.0/input/input11
[ 23.613557] usbcore: registered new interface driver uvcvideo
[ 23.613559] USB Video Class driver (1.1.1)
[ 23.737323] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[ 23.756334] iwlwifi 0000:08:00.0 wlp8s0: renamed from wlan0
[ 23.786482] cfg80211: World regulatory domain updated:
[ 23.786487] cfg80211: DFS Master region: unset
[ 23.786488] cfg80211: (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[ 23.786490] cfg80211: (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[ 23.786492] cfg80211: (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[ 23.786493] cfg80211: (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
[ 23.786494] cfg80211: (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
[ 23.786496] cfg80211: (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
[ 23.786497] cfg80211: (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
[ 23.786498] cfg80211: (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
[ 23.786499] cfg80211: (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
[ 25.635567] audit: type=1400 audit(1474113717.639:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/snapd/snap-confine" pid=785 comm="apparmor_parser"
[ 25.675287] audit: type=1400 audit(1474113717.679:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/ippusbxd" pid=788 comm="apparmor_parser"
[ 25.808323] audit: type=1400 audit(1474113717.815:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/tcpdump" pid=790 comm="apparmor_parser"
[ 25.821541] audit: type=1400 audit(1474113717.827:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cups-browsed" pid=786 comm="apparmor_parser"
[ 25.822313] audit: type=1400 audit(1474113717.827:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=782 comm="apparmor_parser"
[ 25.822333] audit: type=1400 audit(1474113717.827:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=782 comm="apparmor_parser"
[ 25.822340] audit: type=1400 audit(1474113717.827:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=782 comm="apparmor_parser"
[ 25.822348] audit: type=1400 audit(1474113717.827:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=782 comm="apparmor_parser"
[ 25.892887] audit: type=1400 audit(1474113717.899:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=781 comm="apparmor_parser"
[ 25.892899] audit: type=1400 audit(1474113717.899:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session//chromium" pid=781 comm="apparmor_parser"
[ 29.843141] Adding 8259580k swap on /dev/sda5. Priority:-1 extents:1 across:8259580k FS
[ 32.180337] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[ 32.180339] Bluetooth: BNEP filters: protocol multicast
[ 32.180343] Bluetooth: BNEP socket layer initialized
[ 36.239570] IPv6: ADDRCONF(NETDEV_UP): wlp8s0: link is not ready
[ 36.239698] iwlwifi 0000:08:00.0: L1 Enabled - LTR Disabled
[ 36.247421] iwlwifi 0000:08:00.0: L1 Enabled - LTR Disabled
[ 36.247509] iwlwifi 0000:08:00.0: Radio type=0x2-0x0-0x0
[ 36.491808] iwlwifi 0000:08:00.0: L1 Enabled - LTR Disabled
[ 36.499567] iwlwifi 0000:08:00.0: L1 Enabled - LTR Disabled
[ 36.499653] iwlwifi 0000:08:00.0: Radio type=0x2-0x0-0x0
[ 36.556698] IPv6: ADDRCONF(NETDEV_UP): wlp8s0: link is not ready
[ 36.560251] IPv6: ADDRCONF(NETDEV_UP): enp7s0: link is not ready
[ 36.798878] r8169 0000:07:00.0 enp7s0: link down
[ 36.798931] IPv6: ADDRCONF(NETDEV_UP): enp7s0: link is not ready
[ 38.114181] IPv6: ADDRCONF(NETDEV_UP): wlp8s0: link is not ready
[ 38.382226] vboxdrv: module verification failed: signature and/or required key missing - tainting kernel
[ 38.385364] vboxdrv: Found 8 processor cores
[ 38.401242] vboxdrv: TSC mode is Invariant, tentative frequency 2095239740 Hz
[ 38.401245] vboxdrv: Successfully loaded version 5.0.24_Ubuntu (interface 0x00240000)
[ 38.404936] VBoxNetFlt: Successfully started.
[ 38.407967] VBoxNetAdp: Successfully started.
[ 38.411397] VBoxPciLinuxInit
[ 38.413392] vboxpci: IOMMU not found (not registered)
[ 38.745010] wlp8s0: authenticate with c8:91:f9:5c:bc:0a
[ 38.749034] wlp8s0: send auth to c8:91:f9:5c:bc:0a (try 1/3)
[ 38.750858] wlp8s0: authenticated
[ 38.752820] wlp8s0: associate with c8:91:f9:5c:bc:0a (try 1/3)
[ 38.756207] wlp8s0: RX AssocResp from c8:91:f9:5c:bc:0a (capab=0x431 status=0 aid=58)
[ 38.758671] wlp8s0: associated
[ 38.758724] IPv6: ADDRCONF(NETDEV_CHANGE): wlp8s0: link becomes ready
[ 38.779306] cfg80211: Regulatory domain changed to country: GB
[ 38.779309] cfg80211: DFS Master region: ETSI
[ 38.779310] cfg80211: (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[ 38.779312] cfg80211: (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[ 38.779313] cfg80211: (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
[ 38.779315] cfg80211: (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
[ 38.779316] cfg80211: (5490000 KHz - 5710000 KHz @ 160000 KHz), (N/A, 2700 mBm), (0 s)
[ 38.779317] cfg80211: (57000000 KHz - 66000000 KHz @ 2160000 KHz), (N/A, 4000 mBm), (N/A)
[ 79.580375] Bluetooth: RFCOMM TTY layer initialized
[ 79.580384] Bluetooth: RFCOMM socket layer initialized
[ 79.580390] Bluetooth: RFCOMM ver 1.11





```

---

### Post by ajgreeny on 2016-09-16
Please do not use large images inline in your post. Either use the URL of an image online as I have done for you or use the paperclip icon in the toolbar of the text entry box and navigate to an image on your disk to upload it.  That will show a thumbnail in your post which can be clicked to see the full size image.

I'm afraid your image was not much use as it is far too small to see any detail at all.  I can not even see how long you think is too long a boot-up time.

Give us more detail if possible
You can also hit "e" at the grub menu and navigate to the words "quiet splash" and delete them then Ctrl+X to boot, and for just that one boot you will see text only which may give you some clues about the cause of the delay.
Similarly you may find some useful info by running command ```
dmesg
``` immediately after booting and looking for any obvious long delays showing in the time at the start of each line.

---

### Post by sean45xubu on 2016-09-17
Hi thanks for the reply. Having problems replying so have modified my first post to contain a better image and dmesg output.

Sorry for the lack of quality in the first message!

---

### Post by Keith_Helms on 2016-09-17
I'm assuming you logged in somewhere around 36 seconds after startup, since that's when the wifi starts trying to connect to something.  My laptop is only 18 months old and my Xubuntu 16.04 system got to the same point at around 37 seconds.  I'm also assuming that the bluetooth initialization is going on asynchronously in the background.  I don't use bluetooth and have it disabled on my system.

Anyway, unless you're experiencing something significantly longer than 35 to 40 seconds real time, it doesn't sound bad to me.

---

### Post by ajgreeny on 2016-09-17
Please use **Code-Tags** for terminal output, not quote tags as you did in your edit of post #1. See my signature below for a **How-to**

---

### Post by him610 on 2016-09-17
sean45xubu,

Did you initially establish a benchmark time-to-start? If so, what was it? 
You need the benchmarked time for comparison purposes - before and after.
From where in the boot process did you begin and end your time measurements?
Do you actually view the displayed, scrolling messages while booting, or just look at the Ubuntu screen with the advancing dots (not much info there?)
What did you use to measure the elapsed time with?
What did the logs record? Added: check > /var/log/syslog each line has the time on it.

Good luck,

---

### Post by DrRus on 2016-09-17
> **Keith_Helms said:**
> I'm assuming you logged in somewhere around 36 seconds after startup, since that's when the wifi starts trying to connect to something.  My laptop is only 18 months old and my Xubuntu 16.04 system got to the same point at around 37 seconds.  I'm also assuming that the bluetooth initialization is going on asynchronously in the background.  I don't use bluetooth and have it disabled on my system.

Anyway, unless you're experiencing something significantly longer than 35 to 40 seconds real time, it doesn't sound bad to me.

Wow, I guess comes to show you what a difference an SSD can make. I would kill myself if I had to wait 40sec. on a computer to boot, even with Windows :)

My non-virtual Ubuntu is on a PC with an 8-core AMD (a tad faster than the i7 in his laptop, same number of threads), but I boot in 6.6sec, that's when the IPv6 connection is established. Of course, I run on SSD.

---

OP: looking at the log and the image, a few times you have chunks of 4sec where nothing happens. I'm only guessing, but it seems that a few processes take too long to activate, so others are waiting for them, before they could start. 
Again, just a guess, hopefully someone with actual knowledge would solve this mystery. 

But i7 with 8GB of ram? No way I'd be happy with 40 sec after POST...

---

### Post by Keith_Helms on 2016-09-18
> **DrRus said:**
> Wow, I guess comes to show you what a difference an SSD can make. I would kill myself if I had to wait 40sec. on a computer to boot, even with Windows :)


I guess ignorance is bliss.  ;)

---

### Post by sean45xubu on 2016-09-18
Thanks for the replies so far.  Here's the syslog:
 [https://goo.gl/xkU7vH](https://goo.gl/xkU7vH)

 Couldn't see the ouput during boot, just get a black screen even with quiet splash removed. Any ideas?
Is 40sec reasonable for non-SSD? Note this is Xubuntu not Ubuntu so would have expected better??
I kind of expected it to be better than 40sec (and thought it was much faster before 20sec) but I dont use my laptop that often so maybe its just my bad memory.
If there's any improvements anyone can see i'd like to try and make it faster.

having lots of problems posting on these forums :(

---

### Post by DrRus on 2016-09-18
Well, I just dusted an old machine just to compare. 
Here are the specs: Intel Core 2 with 1.86GHz per core, 4 GB of RAM, 250GB HDD 7200rpm, integrated graphics...REALLY OLD :)

Fresh Ubuntu 16.04 install, boot time - 20.8 sec.

For what is worth, 
dev-sda1.device activates in 5.4 sec on mine and 11.2 sec on yours
apparmor.service activates in 5.4sec on mine and 9.7sec on yours

overall most of the services on my archaic machine activate around twice as fast as yours. Like grub-common.service is 5.8sec on mine, 9.4sec on yours, etc.

Again, I am with a dual core 1.86GHz processor. At this point I would say it must be a hardware problem, no?

---

### Post by ian-weisser on 2016-09-18
40 seconds seems reasonable for non-SSD.
That's a big improvement. Back in 2010, boots were 90 seconds or so.

A great deal of work in ureadahead and systemd were intended to speed up boot and optimize disk head movement during boot.

---

### Post by sean45xubu on 2016-09-18
So i did a test with interesting results:

From a live USB stick (Ubuntu 16.04) time from pressing power button to seeing desktop: 43sec
My current install from installed OS (Xubuntu 16.04): 1min 20sec

This seems really crazy, unless anyone has any ideas, i'll be wiping and reinstalling tomorrow!

Could be a hard disk problem i guess, but feel like the only way to know will be to reinstall...

---

### Post by ian-weisser on 2016-09-18
'To seeing desktop' may be an inconsistent measure. We don't know what customizations, saved sessions, or autostart changes you may have made.

Better is 'To login screen'

---

### Post by DrRus on 2016-09-18
> **sean45xubu said:**
> 

This seems really crazy, unless anyone has any ideas, i'll be wiping and reinstalling tomorrow!


I would, but it'd be nice (if you can) to flash the BIOS beforehand, just to cover all bases.

---

### Post by sean45xubu on 2016-09-18
> **ian-weisser said:**
> 'To seeing desktop' may be an inconsistent measure. We don't know what customizations, saved sessions, or autostart changes you may have made.

Better is 'To login screen'

Apologies yes I did mean "to login screen" on my install. On live usb there's no login screen so on that it was to the desktop.

---

### Post by ian-weisser on 2016-09-18
LiveUSB boot is very different from an installed system boot, and the times are not usefully comparable.
LiveUSB will be very fast, for example, on USB3 hardware and port.

LiveUSB is highly optimized to do only two things very well. There are many threads in this forum who quickly reached the limits of their LiveUSB system capabilities. A fast boot is an unsurprising byproduct of that optimization.

---

