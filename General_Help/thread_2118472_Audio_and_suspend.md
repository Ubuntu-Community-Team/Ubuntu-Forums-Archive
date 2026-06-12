---
title: "Audio and suspend"
date: 2013-02-21
forum: General Help
---

### Post by Fr333 on 2013-02-21
On Xubuntu 12.10:
can't hear the input of my audio in, though I see it on the sound configuration panel.
and overall..can't suspend/hybernate: all the times it reboots and then send crash report
any hints?

maybe I shoul have made two posts?

---

### Post by LewisTM on 2013-02-21
It could be that you have HDMI selected as output instead of the built-in audio. You might even have to disable the HDMI in the Configuration tab if Xubuntu keeps defaulting to it.
If that's not it, you can experiment with the settings in xfce4-mixer, see if anything is muted.

Dunno about suspend, will definitely need more hardware info. Did you install proprietary display drivers?

Cheers!

---

### Post by Fr333 on 2013-02-21
Well, thanks for the reply!

Actually I'm using a USB card. but the issue is that I don't see any button/option to enable/disable the audio coming from line-in/mic: I see the levels when audio comes in but can't hear it!

For suspend..it's an old ATI 9600, with the only supported driver natively loaded..there's any log to post?

---

### Post by Fr333 on 2013-02-24
Here's dmesg:
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.5.0-25-generic (buildd@allspice) (gcc version 4.7.2 (Ubuntu/Linaro 4.7.2-2ubuntu1) ) #38-Ubuntu SMP Mon Feb 18 23:27:42 UTC 2013 (Ubuntu 3.5.0-25.38-generic 3.5.7.4)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-25-generic root=UUID=72941664-dc19-4032-aa5d-04c26d277150 ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009fbff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009fc00-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e4000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000007ff3ffff] usable
[    0.000000] BIOS-e820: [mem 0x000000007ff40000-0x000000007ff4ffff] ACPI data
[    0.000000] BIOS-e820: [mem 0x000000007ff50000-0x000000007fffffff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed003ff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff380000-0x00000000ffffffff] reserved
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.3 present.
[    0.000000] DMI:          ConRoe865PE/ConRoe865PE, BIOS P1.60 12/26/2006
[    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] AGP bridge at 00:00:00
[    0.000000] Aperture from AGP @ e0000000 old size 32 MB
[    0.000000] Aperture size 4096 MB (APSIZE 0) is not right, using settings from NB
[    0.000000] Aperture from AGP @ e0000000 size 32 MB (APSIZE 0)
[    0.000000] e820: last_pfn = 0x7ff40 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-DFFFF uncachable
[    0.000000]   E0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 disabled
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] initial memory mapped: [mem 0x00000000-0x1fffffff]
[    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0x7ff3ffff]
[    0.000000]  [mem 0x00000000-0x7fdfffff] page 2M
[    0.000000]  [mem 0x7fe00000-0x7ff3ffff] page 4k
[    0.000000] kernel direct mapping tables up to 0x7ff3ffff @ [mem 0x1fffc000-0x1fffffff]
[    0.000000] RAMDISK: [mem 0x362dc000-0x37165fff]
[    0.000000] ACPI: RSDP 00000000000fa4e0 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 000000007ff40000 00034 (v01 A_M_I  OEMRSDT  12000626 MSFT 00000097)
[    0.000000] ACPI: FACP 000000007ff40200 00081 (v02 A_M_I  OEMFACP  12000626 MSFT 00000097)
[    0.000000] ACPI: DSDT 000000007ff40370 04338 (v01  CR65E CR65E155 00000155 INTL 02002026)
[    0.000000] ACPI: FACS 000000007ff50000 00040
[    0.000000] ACPI: APIC 000000007ff40300 0006C (v01 A_M_I  OEMAPIC  12000626 MSFT 00000097)
[    0.000000] ACPI: OEMB 000000007ff50040 0003F (v01 A_M_I  OEMBIOS  12000626 MSFT 00000097)
[    0.000000] ACPI: HPET 000000007ff446b0 00038 (v01 A_M_I  OEMHPET  12000626 MSFT 00000097)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000007ff3ffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x7ff3ffff]
[    0.000000]   NODE_DATA [mem 0x7ff3c000-0x7ff3ffff]
[    0.000000]  [ffffea0000000000-ffffea0001ffffff] PMD -> [ffff88007d600000-ffff88007f5fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00010000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   empty
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00010000-0x0009efff]
[    0.000000]   node   0: [mem 0x00100000-0x7ff3ffff]
[    0.000000] On node 0 totalpages: 523983
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 6 pages reserved
[    0.000000]   DMA zone: 3913 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 8125 pages used for memmap
[    0.000000]   DMA32 zone: 511875 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a202 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] e820: [mem 0x80000000-0xfecfffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88007fc00000 s83584 r8192 d22912 u524288
[    0.000000] pcpu-alloc: s83584 r8192 d22912 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 515788
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-25-generic root=UUID=72941664-dc19-4032-aa5d-04c26d277150 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] __ex_table already sorted, skipping sort
[    0.000000] Checking aperture...
[    0.000000] AGP bridge at 00:00:00
[    0.000000] Aperture from AGP @ e0000000 old size 32 MB
[    0.000000] Aperture size 4096 MB (APSIZE 0) is not right, using settings from NB
[    0.000000] Aperture from AGP @ e0000000 size 32 MB (APSIZE 0)
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 2031976k/2096384k available (6722k kernel code, 452k absent, 63956k reserved, 6448k data, 932k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:712 16
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 8388608 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1867.519 MHz processor.
[    0.004008] Calibrating delay loop (skipped), value calculated using timer frequency.. 3735.03 BogoMIPS (lpj=7470076)
[    0.004014] pid_max: default: 32768 minimum: 301
[    0.004054] Security Framework initialized
[    0.004082] AppArmor: AppArmor initialized
[    0.004084] Yama: becoming mindful.
[    0.004407] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.006123] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.007213] Mount-cache hash table entries: 256
[    0.007565] Initializing cgroup subsys cpuacct
[    0.007572] Initializing cgroup subsys memory
[    0.007588] Initializing cgroup subsys devices
[    0.007591] Initializing cgroup subsys freezer
[    0.007593] Initializing cgroup subsys blkio
[    0.007595] Initializing cgroup subsys perf_event
[    0.008047] CPU: Physical Processor ID: 0
[    0.008049] CPU: Processor Core ID: 0
[    0.008052] mce: CPU supports 6 MCE banks
[    0.008064] CPU0: Thermal monitoring enabled (TM2)
[    0.008071] using mwait in idle threads.
[    0.008700] CPU0: Core temperature above threshold, cpu clock throttled (total events = 1)
[    0.009190] CPU0: Core temperature/speed normal
[    0.011633] ACPI: Core revision 20120320
[    0.016012] ftrace: allocating 25149 entries in 99 pages
[    0.028465] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.071777] CPU0: Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz stepping 06
[    0.072003] Performance Events: PEBS fmt0-, 4-deep LBR, Core2 events, Intel PMU driver.
[    0.072003] PEBS disabled due to CPU errata.
[    0.072003] ... version:                2
[    0.072003] ... bit width:              40
[    0.072003] ... generic registers:      2
[    0.072003] ... value mask:             000000ffffffffff
[    0.072003] ... max period:             000000007fffffff
[    0.072003] ... fixed-purpose events:   3
[    0.072003] ... event mask:             0000000700000003
[    0.072003] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.072003] Booting Node   0, Processors  #1
[    0.080111] Brought up 2 CPUs
[    0.080118] Total of 2 processors activated (7470.07 BogoMIPS).
[    0.081644] devtmpfs: initialized
[    0.081644] EVM: security.selinux
[    0.081644] EVM: security.SMACK64
[    0.081644] EVM: security.capability
[    0.084033] PM: Registering ACPI NVS region [mem 0x7ff50000-0x7fffffff] (720896 bytes)
[    0.085112] dummy: 
[    0.085142] RTC time: 13:43:34, date: 02/24/13
[    0.085197] NET: Registered protocol family 16
[    0.085211] Trying to unpack rootfs image as initramfs...
[    0.085452] ACPI: bus type pci registered
[    0.085531] PCI: Using configuration type 1 for base access
[    0.085676] mtrr: your CPUs had inconsistent variable MTRR settings
[    0.085678] mtrr: probably your BIOS does not setup all CPUs.
[    0.085680] mtrr: corrected configuration.
[    0.086993] bio: create slab <bio-0> at 0
[    0.087127] ACPI: Added _OSI(Module Device)
[    0.087130] ACPI: Added _OSI(Processor Device)
[    0.087133] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.087136] ACPI: Added _OSI(Processor Aggregator Device)
[    0.089079] ACPI: EC: Look up EC in DSDT
[    0.090446] ACPI: Executed 1 blocks of module-level executable AML code
[    0.092284] ACPI: SSDT 000000007ff50080 001D2 (v01    AMI   CPU1PM 00000001 INTL 20051117)
[    0.092564] ACPI: Dynamic OEM Table Load:
[    0.092569] ACPI: SSDT           (null) 001D2 (v01    AMI   CPU1PM 00000001 INTL 20051117)
[    0.092773] ACPI: SSDT 000000007ff50260 00143 (v01    AMI   CPU2PM 00000001 INTL 20051117)
[    0.093046] ACPI: Dynamic OEM Table Load:
[    0.093050] ACPI: SSDT           (null) 00143 (v01    AMI   CPU2PM 00000001 INTL 20051117)
[    0.093386] ACPI: Interpreter enabled
[    0.093392] ACPI: (supports S0 S1 S3 S4 S5)
[    0.093419] ACPI: Using IOAPIC for interrupt routing
[    0.098893] ACPI: No dock devices found.
[    0.098901] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.098978] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.099092] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.099097] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.099101] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.099105] pci_root PNP0A03:00: host bridge window [mem 0x80000000-0xffefffff] (ignored)
[    0.099107] PCI: root bus 00: using default resources
[    0.099151] PCI host bridge to bus 0000:00
[    0.099156] pci_bus 0000:00: root bus resource [io  0x0000-0xffff]
[    0.099160] pci_bus 0000:00: root bus resource [mem 0x00000000-0xfffffffff]
[    0.099177] pci 0000:00:00.0: [8086:2570] type 00 class 0x060000
[    0.099183] pci 0000:00:00.0: Enabling MCH 'Overflow' Device
[    0.099192] pci 0000:00:00.0: reg 10: [mem 0xe0000000-0xefffffff pref]
[    0.099263] pci 0000:00:01.0: [8086:2571] type 01 class 0x060400
[    0.099302] pci 0000:00:06.0: [8086:2576] type 00 class 0x088000
[    0.099313] pci 0000:00:06.0: reg 10: [mem 0xfecf0000-0xfecf0fff]
[    0.099389] pci 0000:00:1d.0: [8086:24d2] type 00 class 0x0c0300
[    0.099434] pci 0000:00:1d.0: reg 20: [io  0xe000-0xe01f]
[    0.099471] pci 0000:00:1d.1: [8086:24d4] type 00 class 0x0c0300
[    0.099516] pci 0000:00:1d.1: reg 20: [io  0xe400-0xe41f]
[    0.099555] pci 0000:00:1d.2: [8086:24d7] type 00 class 0x0c0300
[    0.099601] pci 0000:00:1d.2: reg 20: [io  0xe800-0xe81f]
[    0.099639] pci 0000:00:1d.3: [8086:24de] type 00 class 0x0c0300
[    0.099685] pci 0000:00:1d.3: reg 20: [io  0xec00-0xec1f]
[    0.099735] pci 0000:00:1d.7: [8086:24dd] type 00 class 0x0c0320
[    0.099758] pci 0000:00:1d.7: reg 10: [mem 0xff2ffc00-0xff2fffff]
[    0.099875] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.099897] pci 0000:00:1e.0: [8086:244e] type 01 class 0x060400
[    0.099943] pci 0000:00:1f.0: [8086:24d0] type 00 class 0x060100
[    0.100089] pci 0000:00:1f.1: [8086:24db] type 00 class 0x01018a
[    0.100105] pci 0000:00:1f.1: reg 10: [io  0x0000-0x0007]
[    0.100116] pci 0000:00:1f.1: reg 14: [io  0x0000-0x0003]
[    0.100127] pci 0000:00:1f.1: reg 18: [io  0x0000-0x0007]
[    0.100138] pci 0000:00:1f.1: reg 1c: [io  0x0000-0x0003]
[    0.100149] pci 0000:00:1f.1: reg 20: [io  0xfc00-0xfc0f]
[    0.100160] pci 0000:00:1f.1: reg 24: [mem 0x00000000-0x000003ff]
[    0.100190] pci 0000:00:1f.2: [8086:24d1] type 00 class 0x01018f
[    0.100203] pci 0000:00:1f.2: reg 10: [io  0xd400-0xd407]
[    0.100213] pci 0000:00:1f.2: reg 14: [io  0xd000-0xd003]
[    0.100224] pci 0000:00:1f.2: reg 18: [io  0xcc00-0xcc07]
[    0.100234] pci 0000:00:1f.2: reg 1c: [io  0xc800-0xc803]
[    0.100245] pci 0000:00:1f.2: reg 20: [io  0xc400-0xc40f]
[    0.100280] pci 0000:00:1f.3: [8086:24d3] type 00 class 0x0c0500
[    0.100325] pci 0000:00:1f.3: reg 20: [io  0x0400-0x041f]
[    0.100366] pci 0000:00:1f.5: [8086:24d5] type 00 class 0x040100
[    0.100383] pci 0000:00:1f.5: reg 10: [io  0xd800-0xd8ff]
[    0.100393] pci 0000:00:1f.5: reg 14: [io  0xdc00-0xdc3f]
[    0.100403] pci 0000:00:1f.5: reg 18: [mem 0xff2ff800-0xff2ff9ff]
[    0.100413] pci 0000:00:1f.5: reg 1c: [mem 0xff2ff400-0xff2ff4ff]
[    0.100460] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[    0.100511] pci 0000:01:00.0: [1002:4150] type 00 class 0x030000
[    0.100528] pci 0000:01:00.0: reg 10: [mem 0xc0000000-0xcfffffff pref]
[    0.100537] pci 0000:01:00.0: reg 14: [io  0xa800-0xa8ff]
[    0.100546] pci 0000:01:00.0: reg 18: [mem 0xff0f0000-0xff0fffff]
[    0.100571] pci 0000:01:00.0: reg 30: [mem 0xff0c0000-0xff0dffff pref]
[    0.100602] pci 0000:01:00.0: supports D1 D2
[    0.100621] pci 0000:01:00.1: [1002:4170] type 00 class 0x038000
[    0.100635] pci 0000:01:00.1: reg 10: [mem 0xb0000000-0xbfffffff pref]
[    0.100645] pci 0000:01:00.1: reg 14: [mem 0xff0e0000-0xff0effff]
[    0.100696] pci 0000:01:00.1: supports D1 D2
[    0.100738] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.100743] pci 0000:00:01.0:   bridge window [io  0xa000-0xafff]
[    0.100749] pci 0000:00:01.0:   bridge window [mem 0xff000000-0xff0fffff]
[    0.100754] pci 0000:00:01.0:   bridge window [mem 0x9fe00000-0xdfdfffff pref]
[    0.100781] pci 0000:02:01.0: [109e:036e] type 00 class 0x040000
[    0.100800] pci 0000:02:01.0: reg 10: [mem 0xdfefe000-0xdfefefff pref]
[    0.100894] pci 0000:02:01.1: [109e:0878] type 00 class 0x048000
[    0.100912] pci 0000:02:01.1: reg 10: [mem 0xdfeff000-0xdfefffff pref]
[    0.101010] pci 0000:02:02.0: [1106:3044] type 00 class 0x0c0010
[    0.101028] pci 0000:02:02.0: reg 10: [mem 0xff1ff800-0xff1fffff]
[    0.101039] pci 0000:02:02.0: reg 14: [io  0xbc00-0xbc7f]
[    0.101106] pci 0000:02:02.0: supports D2
[    0.101110] pci 0000:02:02.0: PME# supported from D2 D3hot D3cold
[    0.101153] pci 0000:00:1e.0: PCI bridge to [bus 02-02] (subtractive decode)
[    0.101159] pci 0000:00:1e.0:   bridge window [io  0xb000-0xbfff]
[    0.101165] pci 0000:00:1e.0:   bridge window [mem 0xff100000-0xff1fffff]
[    0.101170] pci 0000:00:1e.0:   bridge window [mem 0xdfe00000-0xdfefffff pref]
[    0.101174] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.101177] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xfffffffff] (subtractive decode)
[    0.101192] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.101256] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.101405]  pci0000:00: Unable to request _OSC control (_OSC support mask: 0x1e)
[    0.105972] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.106035] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.106094] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.106153] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11 12 14 *15)
[    0.106212] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.106272] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.106332] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.106391] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.106569] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.106576] vgaarb: loaded
[    0.106578] vgaarb: bridge control possible 0000:01:00.0
[    0.106866] SCSI subsystem initialized
[    0.106975] libata version 3.00 loaded.
[    0.107006] ACPI: bus type usb registered
[    0.107040] usbcore: registered new interface driver usbfs
[    0.107056] usbcore: registered new interface driver hub
[    0.107093] usbcore: registered new device driver usb
[    0.107205] PCI: Using ACPI for IRQ routing
[    0.107209] PCI: pci_cache_line_size set to 64 bytes
[    0.107298] e820: reserve RAM buffer [mem 0x0009fc00-0x0009ffff]
[    0.107301] e820: reserve RAM buffer [mem 0x7ff40000-0x7fffffff]
[    0.107461] NetLabel: Initializing
[    0.107464] NetLabel:  domain hash size = 128
[    0.107465] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.107502] NetLabel:  unlabeled traffic allowed by default
[    0.107583] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.107588] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.107595] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.112327] Switching to clocksource hpet
[    0.124299] AppArmor: AppArmor Filesystem Enabled
[    0.124362] pnp: PnP ACPI init
[    0.124390] ACPI: bus type pnp registered
[    0.124554] pnp 00:00: [bus 00-ff]
[    0.124559] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.124563] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.124567] pnp 00:00: [io  0x0d00-0xffff window]
[    0.124571] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.124574] pnp 00:00: [mem 0x00000000 window]
[    0.124577] pnp 00:00: [mem 0x80000000-0xffefffff window]
[    0.124651] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.124723] pnp 00:01: [dma 4]
[    0.124727] pnp 00:01: [io  0x0000-0x000f]
[    0.124730] pnp 00:01: [io  0x0081-0x0083]
[    0.124733] pnp 00:01: [io  0x0087]
[    0.124736] pnp 00:01: [io  0x0089-0x008b]
[    0.124739] pnp 00:01: [io  0x008f]
[    0.124742] pnp 00:01: [io  0x00c0-0x00df]
[    0.124778] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.124792] pnp 00:02: [io  0x0070-0x0071]
[    0.124814] pnp 00:02: [irq 8]
[    0.124853] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.124865] pnp 00:03: [io  0x0061]
[    0.124900] pnp 00:03: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.124913] pnp 00:04: [io  0x00f0-0x00ff]
[    0.124921] pnp 00:04: [irq 13]
[    0.124968] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.125544] pnp 00:05: [io  0x0010-0x001f]
[    0.125549] pnp 00:05: [io  0x0022-0x003f]
[    0.125552] pnp 00:05: [io  0x0044-0x005f]
[    0.125555] pnp 00:05: [io  0x0062-0x0063]
[    0.125558] pnp 00:05: [io  0x0065-0x006f]
[    0.125569] pnp 00:05: [io  0x0072-0x007f]
[    0.125572] pnp 00:05: [io  0x0080]
[    0.125575] pnp 00:05: [io  0x0084-0x0086]
[    0.125578] pnp 00:05: [io  0x0088]
[    0.125582] pnp 00:05: [io  0x008c-0x008e]
[    0.125585] pnp 00:05: [io  0x0090-0x009f]
[    0.125588] pnp 00:05: [io  0x00a2-0x00bf]
[    0.125591] pnp 00:05: [io  0x00e0-0x00ef]
[    0.125594] pnp 00:05: [io  0x04d0-0x04d1]
[    0.125597] pnp 00:05: [io  0x0800-0x087f]
[    0.125600] pnp 00:05: [io  0x0000-0xffffffffffffffff disabled]
[    0.125604] pnp 00:05: [io  0x0480-0x04bf]
[    0.125607] pnp 00:05: [io  0x0900-0x090f]
[    0.125610] pnp 00:05: [mem 0xfed20000-0xfed8ffff]
[    0.125613] pnp 00:05: [mem 0xff380000-0xffefffff]
[    0.125732] system 00:05: [io  0x04d0-0x04d1] has been reserved
[    0.125736] system 00:05: [io  0x0800-0x087f] has been reserved
[    0.125740] system 00:05: [io  0x0480-0x04bf] has been reserved
[    0.125744] system 00:05: [io  0x0900-0x090f] has been reserved
[    0.125750] system 00:05: [mem 0xfed20000-0xfed8ffff] has been reserved
[    0.125754] system 00:05: [mem 0xff380000-0xffefffff] has been reserved
[    0.125759] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.125819] pnp 00:06: [mem 0xfec00000-0xfec00fff]
[    0.125823] pnp 00:06: [mem 0xfee00000-0xfee00fff]
[    0.125881] system 00:06: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.125885] system 00:06: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.125890] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.125926] pnp 00:07: [io  0x0060]
[    0.125929] pnp 00:07: [io  0x0064]
[    0.125937] pnp 00:07: [irq 1]
[    0.125988] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.126200] pnp 00:08: [io  0x0000-0xffffffffffffffff disabled]
[    0.126204] pnp 00:08: [io  0x0000-0xffffffffffffffff disabled]
[    0.126208] pnp 00:08: [io  0x0290-0x029f]
[    0.126273] system 00:08: [io  0x0290-0x029f] has been reserved
[    0.126278] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.126326] pnp 00:09: [mem 0xfed00000-0xfed003ff]
[    0.126366] pnp 00:09: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.126479] pnp 00:0a: [mem 0x00000000-0x0009ffff]
[    0.126483] pnp 00:0a: [mem 0x000c0000-0x000dffff]
[    0.126487] pnp 00:0a: [mem 0x000e0000-0x000fffff]
[    0.126490] pnp 00:0a: [mem 0x00100000-0x7fffffff]
[    0.126493] pnp 00:0a: [mem 0xfff00000-0xffffffff]
[    0.126566] system 00:0a: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.126570] system 00:0a: [mem 0x000c0000-0x000dffff] could not be reserved
[    0.126574] system 00:0a: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.126578] system 00:0a: [mem 0x00100000-0x7fffffff] could not be reserved
[    0.126583] system 00:0a: [mem 0xfff00000-0xffffffff] has been reserved
[    0.126587] system 00:0a: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.126753] pnp: PnP ACPI: found 11 devices
[    0.126755] ACPI: ACPI bus type pnp unregistered
[    0.133645] pci 0000:00:1f.1: BAR 5: assigned [mem 0x80000000-0x800003ff]
[    0.133655] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.133659] pci 0000:00:01.0:   bridge window [io  0xa000-0xafff]
[    0.133665] pci 0000:00:01.0:   bridge window [mem 0xff000000-0xff0fffff]
[    0.133670] pci 0000:00:01.0:   bridge window [mem 0x9fe00000-0xdfdfffff pref]
[    0.133678] pci 0000:00:1e.0: PCI bridge to [bus 02-02]
[    0.133682] pci 0000:00:1e.0:   bridge window [io  0xb000-0xbfff]
[    0.133689] pci 0000:00:1e.0:   bridge window [mem 0xff100000-0xff1fffff]
[    0.133694] pci 0000:00:1e.0:   bridge window [mem 0xdfe00000-0xdfefffff pref]
[    0.133716] pci 0000:00:1e.0: setting latency timer to 64
[    0.133724] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
[    0.133727] pci_bus 0000:00: resource 5 [mem 0x00000000-0xfffffffff]
[    0.133731] pci_bus 0000:01: resource 0 [io  0xa000-0xafff]
[    0.133734] pci_bus 0000:01: resource 1 [mem 0xff000000-0xff0fffff]
[    0.133738] pci_bus 0000:01: resource 2 [mem 0x9fe00000-0xdfdfffff pref]
[    0.133742] pci_bus 0000:02: resource 0 [io  0xb000-0xbfff]
[    0.133745] pci_bus 0000:02: resource 1 [mem 0xff100000-0xff1fffff]
[    0.133749] pci_bus 0000:02: resource 2 [mem 0xdfe00000-0xdfefffff pref]
[    0.133752] pci_bus 0000:02: resource 4 [io  0x0000-0xffff]
[    0.133755] pci_bus 0000:02: resource 5 [mem 0x00000000-0xfffffffff]
[    0.133817] NET: Registered protocol family 2
[    0.133969] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.134766] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.138785] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.139845] TCP: Hash tables configured (established 262144 bind 65536)
[    0.139848] TCP: reno registered
[    0.139859] UDP hash table entries: 1024 (order: 3, 32768 bytes)
[    0.139900] UDP-Lite hash table entries: 1024 (order: 3, 32768 bytes)
[    0.140172] NET: Registered protocol family 1
[    0.140429] pci 0000:01:00.0: Boot video device
[    0.140445] PCI: CLS 32 bytes, default 64
[    0.141121] audit: initializing netlink socket (disabled)
[    0.141139] type=2000 audit(1361713414.140:1): initialized
[    0.172827] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.175196] VFS: Disk quotas dquot_6.5.2
[    0.175262] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.175992] fuse init (API version 7.19)
[    0.176126] msgmni has been set to 3968
[    0.176564] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.176603] io scheduler noop registered
[    0.176606] io scheduler deadline registered (default)
[    0.176647] io scheduler cfq registered
[    0.176841] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.176866] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.176934] intel_idle: does not run on family 6 model 15
[    0.177047] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.177055] ACPI: Power Button [PWRB]
[    0.177115] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.177119] ACPI: Power Button [PWRF]
[    0.177235] ACPI: Requesting acpi_cpufreq
[    0.467675] Freeing initrd memory: 14888k freed
[    0.480641] GHES: HEST is not enabled!
[    0.480777] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.482431] Linux agpgart interface v0.103
[    0.482693] agpgart-intel 0000:00:00.0: Intel 865 Chipset
[    0.490506] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
[    0.492201] brd: module loaded
[    0.493144] loop: module loaded
[    0.493315] ata_piix 0000:00:1f.1: version 2.13
[    0.493367] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.493708] scsi0 : ata_piix
[    0.493802] scsi1 : ata_piix
[    0.494922] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
[    0.494926] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
[    0.494978] ata_piix 0000:00:1f.2: MAP [
[    0.494981]  P0 -- P1 -- ]
[    0.495016] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.495091] ata2: port disabled--ignoring
[    0.495305] scsi2 : ata_piix
[    0.495388] scsi3 : ata_piix
[    0.495443] ata3: SATA max UDMA/133 cmd 0xd400 ctl 0xd000 bmdma 0xc400 irq 18
[    0.495447] ata4: SATA max UDMA/133 cmd 0xcc00 ctl 0xc800 bmdma 0xc408 irq 18
[    0.495846] Fixed MDIO Bus: probed
[    0.495904] tun: Universal TUN/TAP device driver, 1.6
[    0.495906] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.496019] PPP generic driver version 2.4.2
[    0.496083] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.496130] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.496135] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.496147] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.496179] ehci_hcd 0000:00:1d.7: debug port 1
[    0.500079] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.500099] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xff2ffc00
[    0.512013] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.512041] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.512045] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.512048] usb usb1: Product: EHCI Host Controller
[    0.512051] usb usb1: Manufacturer: Linux 3.5.0-25-generic ehci_hcd
[    0.512053] usb usb1: SerialNumber: 0000:00:1d.7
[    0.512186] hub 1-0:1.0: USB hub found
[    0.512193] hub 1-0:1.0: 8 ports detected
[    0.512295] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.512318] uhci_hcd: USB Universal Host Controller Interface driver
[    0.512346] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.512351] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.512359] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.512390] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000e000
[    0.512430] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    0.512434] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.512437] usb usb2: Product: UHCI Host Controller
[    0.512441] usb usb2: Manufacturer: Linux 3.5.0-25-generic uhci_hcd
[    0.512444] usb usb2: SerialNumber: 0000:00:1d.0
[    0.512559] hub 2-0:1.0: USB hub found
[    0.512566] hub 2-0:1.0: 2 ports detected
[    0.512649] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.512654] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.512661] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.512692] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000e400
[    0.512729] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    0.512733] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.512737] usb usb3: Product: UHCI Host Controller
[    0.512740] usb usb3: Manufacturer: Linux 3.5.0-25-generic uhci_hcd
[    0.512744] usb usb3: SerialNumber: 0000:00:1d.1
[    0.512855] hub 3-0:1.0: USB hub found
[    0.512871] hub 3-0:1.0: 2 ports detected
[    0.512956] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.512961] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.512968] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.512990] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e800
[    0.513027] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    0.513030] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.513034] usb usb4: Product: UHCI Host Controller
[    0.513037] usb usb4: Manufacturer: Linux 3.5.0-25-generic uhci_hcd
[    0.513041] usb usb4: SerialNumber: 0000:00:1d.2
[    0.513168] hub 4-0:1.0: USB hub found
[    0.513173] hub 4-0:1.0: 2 ports detected
[    0.513252] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.513257] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.513267] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.513288] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000ec00
[    0.513332] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    0.513336] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.513339] usb usb5: Product: UHCI Host Controller
[    0.513343] usb usb5: Manufacturer: Linux 3.5.0-25-generic uhci_hcd
[    0.513346] usb usb5: SerialNumber: 0000:00:1d.3
[    0.513459] hub 5-0:1.0: USB hub found
[    0.513464] hub 5-0:1.0: 2 ports detected
[    0.513578] usbcore: registered new interface driver libusual
[    0.513617] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    0.513619] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    0.514351] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.514461] mousedev: PS/2 mouse device common for all mice
[    0.514641] rtc_cmos 00:02: RTC can wake from S4
[    0.514759] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.514781] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
[    0.514884] device-mapper: uevent: version 1.0.3
[    0.514965] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    0.514977] cpuidle: using governor ladder
[    0.514979] cpuidle: using governor menu
[    0.514982] EFI Variables Facility v0.08 2004-May-17
[    0.515265] ashmem: initialized
[    0.515423] TCP: cubic registered
[    0.515562] NET: Registered protocol family 10
[    0.515843] NET: Registered protocol family 17
[    0.515861] Key type dns_resolver registered
[    0.516075] PM: Hibernation image not present or could not be loaded.
[    0.516094] registered taskstats version 1
[    0.519209] Key type trusted registered
[    0.521804] Key type encrypted registered
[    0.524654]   Magic number: 1:840:736
[    0.524797] rtc_cmos 00:02: setting system clock to 2013-02-24 13:43:34 UTC (1361713414)
[    0.525181] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.525184] EDD information not available.
[    0.543682] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    0.656504] ata3.00: ATA-8: Hitachi HDS721010CLA332, JP4OA3EA, max UDMA/133
[    0.656508] ata3.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    0.656978] ata4.00: ATA-8: ST9250315AS, 0002BSM1, max UDMA/133
[    0.656983] ata4.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    0.664323] ata1.00: ATAPI: _NEC DVD_RW ND-3520A, 1.04, max UDMA/33
[    0.664532] ata1.01: ATA-6: ST340810A, 3.39, max UDMA/100
[    0.664535] ata1.01: 78165360 sectors, multi 16: LBA 
[    0.672409] ata3.00: configured for UDMA/133
[    0.672609] ata4.00: configured for UDMA/133
[    0.680181] ata1.00: configured for UDMA/33
[    0.696325] ata1.01: configured for UDMA/100
[    0.699351] scsi 0:0:0:0: CD-ROM            _NEC     DVD_RW ND-3520A  1.04 PQ: 0 ANSI: 5
[    0.701108] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    0.701112] cdrom: Uniform CD-ROM driver Revision: 3.20
[    0.701243] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    0.701383] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    0.701838] scsi 0:0:1:0: Direct-Access     ATA      ST340810A        3.39 PQ: 0 ANSI: 5
[    0.701987] sd 0:0:1:0: [sda] 78165360 512-byte logical blocks: (40.0 GB/37.2 GiB)
[    0.702010] sd 0:0:1:0: Attached scsi generic sg1 type 0
[    0.702073] sd 0:0:1:0: [sda] Write Protect is off
[    0.702078] sd 0:0:1:0: [sda] Mode Sense: 00 3a 00 00
[    0.702116] sd 0:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.704283]  sda: sda1
[    0.704573] sd 0:0:1:0: [sda] Attached SCSI disk
[    0.704667] scsi 2:0:0:0: Direct-Access     ATA      Hitachi HDS72101 JP4O PQ: 0 ANSI: 5
[    0.704790] sd 2:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    0.704823] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    0.704853] sd 2:0:0:0: [sdb] Write Protect is off
[    0.704868] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    0.704910] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.731408]  sdb: sdb1 sdb2 sdb3 < sdb5 sdb6 > sdb4
[    0.731915] sd 2:0:0:0: [sdb] Attached SCSI disk
[    0.732021] scsi 3:0:0:0: Direct-Access     ATA      ST9250315AS      0002 PQ: 0 ANSI: 5
[    0.732149] sd 3:0:0:0: [sdc] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    0.732193] sd 3:0:0:0: Attached scsi generic sg3 type 0
[    0.732222] sd 3:0:0:0: [sdc] Write Protect is off
[    0.732227] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    0.732261] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.768428]  sdc: sdc1
[    0.768671] sd 3:0:0:0: [sdc] Attached SCSI disk
[    0.770440] Freeing unused kernel memory: 932k freed
[    0.770741] Write protecting the kernel read-only data: 12288k
[    0.776699] Freeing unused kernel memory: 1460k freed
[    0.784599] Freeing unused kernel memory: 1120k freed
[    0.807228] udevd[99]: starting version 175
[    0.936073] usb 1-3: new high-speed USB device number 3 using ehci_hcd
[    0.976059] firewire_ohci 0000:02:02.0: added OHCI v1.10 device as card 0, 4 IR + 8 IT contexts, quirks 0x11
[    1.068802] usb 1-3: New USB device found, idVendor=0cde, idProduct=001a
[    1.068810] usb 1-3: New USB device strings: Mfr=16, Product=32, SerialNumber=0
[    1.068814] usb 1-3: Product: USB Device
[    1.068817] usb 1-3: Manufacturer: ZyDAS
[    1.140029] Refined TSC clocksource calibration: 1867.567 MHz.
[    1.140038] Switching to clocksource tsc
[    1.389686] EXT4-fs (sdb5): INFO: recovery required on readonly filesystem
[    1.389693] EXT4-fs (sdb5): write access will be enabled during recovery
[    1.420024] usb 2-1: new full-speed USB device number 2 using uhci_hcd
[    1.548151] firewire_core 0000:02:02.0: created device fw0: GUID 00110666455560e6, S400
[    1.589261] usb 2-1: New USB device found, idVendor=058f, idProduct=9254
[    1.589268] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.589272] usb 2-1: Product: Generic USB Hub
[    1.589276] usb 2-1: Manufacturer: ALCOR
[    1.592319] hub 2-1:1.0: USB hub found
[    1.594254] hub 2-1:1.0: 4 ports detected
[    1.840014] usb 3-2: new full-speed USB device number 2 using uhci_hcd
[    2.047378] EXT4-fs (sdb5): orphan cleanup on readonly fs
[    2.047389] EXT4-fs (sdb5): ext4_orphan_cleanup: deleting unreferenced inode 2636316
[    2.052703] EXT4-fs (sdb5): ext4_orphan_cleanup: deleting unreferenced inode 1053018
[    2.063468] usb 3-2: New USB device found, idVendor=0ccd, idProduct=0012
[    2.063472] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=4
[    2.063475] usb 3-2: Product: PHASE 26 USB(24/48)
[    2.063478] usb 3-2: Manufacturer: TerraTec
[    2.063481] usb 3-2: SerialNumber: 11001
[    2.065084] EXT4-fs (sdb5): ext4_orphan_cleanup: deleting unreferenced inode 1048589
[    2.072827] EXT4-fs (sdb5): 3 orphan inodes deleted
[    2.072833] EXT4-fs (sdb5): recovery complete
[    2.170532] EXT4-fs (sdb5): mounted filesystem with ordered data mode. Opts: (null)
[    2.401121] usb 2-1.1: new low-speed USB device number 3 using uhci_hcd
[    2.537094] usb 2-1.1: New USB device found, idVendor=1c4f, idProduct=0003
[    2.537100] usb 2-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.537104] usb 2-1.1: Product: Usb Mouse
[    2.537107] usb 2-1.1: Manufacturer: SIGMACHIP
[    4.803735] usb 2-1.1: USB disconnect, device number 3
[    6.157496] usb 2-1.1: new low-speed USB device number 4 using uhci_hcd
[    6.293468] usb 2-1.1: New USB device found, idVendor=1c4f, idProduct=0003
[    6.293473] usb 2-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    6.293477] usb 2-1.1: Product: Usb Mouse
[    6.293480] usb 2-1.1: Manufacturer: SIGMACHIP
[   10.046250] Adding 4883452k swap on /dev/sdb6.  Priority:-1 extents:1 across:4883452k 
[   10.117220] udevd[368]: starting version 175
[   10.216023] lp: driver loaded but no devices found
[   10.278046] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   10.284007] EXT4-fs (sdb5): re-mounted. Opts: errors=remount-ro
[   10.508619] intel_rng: FWH not detected
[   10.572560] cfg80211: Calling CRDA to update world regulatory domain
[   10.618331] ACPI Warning: 0x0000000000000830-0x0000000000000833 SystemIO conflicts with Region \SMIE 1 (20120320/utaddress-251)
[   10.618343] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   10.618346] lpc_ich: Resource conflict(s) found affecting iTCO_wdt
[   10.618357] lpc_ich 0000:00:1f.0: I/O space for GPIO uninitialized
[   10.628192] cfg80211: World regulatory domain updated:
[   10.628198] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   10.628201] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.628204] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.628207] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.628209] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.628212] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.690586] usbcore: registered new interface driver usbhid
[   10.690591] usbhid: USB HID core driver
[   10.692884] [drm] Initialized drm 1.1.0 20060810
[   10.863125] microcode: CPU0 sig=0x6f6, pf=0x1, revision=0x44
[   10.885464] Linux video capture interface: v2.00
[   10.890384] bt87x0: Using board 1, analog, digital (rate 32000 Hz)
[   10.891464] type=1400 audit(1361709824.863:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=588 comm="apparmor_parser"
[   10.892078] type=1400 audit(1361709824.867:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=588 comm="apparmor_parser"
[   10.892412] type=1400 audit(1361709824.867:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=588 comm="apparmor_parser"
[   10.897894] microcode: CPU1 sig=0x6f6, pf=0x1, revision=0x44
[   10.921442] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   10.997908] input: SIGMACHIP Usb Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.0/input/input3
[   11.002350] hid-generic 0003:1C4F:0003.0001: input,hidraw0: USB HID v1.10 Mouse [SIGMACHIP Usb Mouse] on usb-0000:00:1d.0-1.1/input0
[   11.022542] snd_intel8x0 0000:00:1f.5: setting latency timer to 64
[   11.023125] init: failsafe main process (709) killed by TERM signal
[   11.238906] type=1400 audit(1361709825.211:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=794 comm="apparmor_parser"
[   11.241947] type=1400 audit(1361709825.215:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=793 comm="apparmor_parser"
[   11.242414] type=1400 audit(1361709825.215:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=793 comm="apparmor_parser"
[   11.243686] type=1400 audit(1361709825.215:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=794 comm="apparmor_parser"
[   11.244030] type=1400 audit(1361709825.219:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=794 comm="apparmor_parser"
[   11.263400] type=1400 audit(1361709825.235:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=795 comm="apparmor_parser"
[   11.268146] type=1400 audit(1361709825.243:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=797 comm="apparmor_parser"
[   11.343605] Bluetooth: Core ver 2.16
[   11.343644] NET: Registered protocol family 31
[   11.343647] Bluetooth: HCI device and connection manager initialized
[   11.343651] Bluetooth: HCI socket layer initialized
[   11.343653] Bluetooth: L2CAP socket layer initialized
[   11.343671] Bluetooth: SCO socket layer initialized
[   11.348035] intel8x0_measure_ac97_clock: measured 54935 usecs (2647 samples)
[   11.348044] intel8x0: clocking to 48000
[   11.380066] usb 1-3: reset high-speed USB device number 3 using ehci_hcd
[   11.386774] ppdev: user-space parallel port driver
[   11.420377] Bluetooth: RFCOMM TTY layer initialized
[   11.420387] Bluetooth: RFCOMM socket layer initialized
[   11.420390] Bluetooth: RFCOMM ver 1.11
[   11.424662] [drm] radeon defaulting to kernel modesetting.
[   11.424668] [drm] radeon kernel modesetting enabled.
[   11.427142] [drm] initializing kernel modesetting (RV350 0x1002:0x4150 0x174B:0x0200).
[   11.427185] [drm] register mmio base: 0xFF0F0000
[   11.427188] [drm] register mmio size: 65536
[   11.428153] agpgart-intel 0000:00:00.0: AGP 3.0 bridge
[   11.428206] agpgart-intel 0000:00:00.0: putting AGP V3 device into 8x mode
[   11.428247] radeon 0000:01:00.0: putting AGP V3 device into 8x mode
[   11.428276] radeon 0000:01:00.0: GTT: 256M 0xE0000000 - 0xEFFFFFFF
[   11.428280] [drm] Generation 2 PCI interface, using max accessible memory
[   11.428285] radeon 0000:01:00.0: VRAM: 256M 0x00000000C0000000 - 0x00000000CFFFFFFF (256M used)
[   11.428296] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   11.428298] [drm] Driver supports precise vblank timestamp query.
[   11.428310] [drm] radeon: irq initialized.
[   11.429455] [drm] Detected VRAM RAM=256M, BAR=256M
[   11.429460] [drm] RAM width 128bits DDR
[   11.429561] [TTM] Zone  kernel: Available graphics memory: 1025188 kiB
[   11.429564] [TTM] Initializing pool allocator
[   11.429571] [TTM] Initializing DMA pool allocator
[   11.429607] [drm] radeon: 256M of VRAM memory ready
[   11.429610] [drm] radeon: 256M of GTT memory ready.
[   11.429669] [drm] radeon: 1 quad pipes, 1 Z pipes initialized.
[   11.431870] radeon 0000:01:00.0: WB disabled
[   11.431875] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x00000000e0000000 and cpu addr 0xffffc90000a9a000
[   11.432215] [drm] Loading R300 Microcode
[   11.438751] [drm] radeon: ring at 0x00000000E0001000
[   11.438777] [drm] ring test succeeded in 0 usecs
[   11.441391] [drm] ib test succeeded in 0 usecs
[   11.443587] [drm] Radeon Display Connectors
[   11.443593] [drm] Connector 0:
[   11.443595] [drm]   VGA-1
[   11.443599] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
[   11.443601] [drm]   Encoders:
[   11.443603] [drm]     CRT1: INTERNAL_DAC1
[   11.443606] [drm] Connector 1:
[   11.443608] [drm]   DVI-I-1
[   11.443611] [drm]   HPD1
[   11.443615] [drm]   DDC: 0x64 0x64 0x64 0x64 0x64 0x64 0x64 0x64
[   11.443617] [drm]   Encoders:
[   11.443619] [drm]     CRT2: INTERNAL_DAC2
[   11.443621] [drm]     DFP1: INTERNAL_TMDS1
[   11.443623] [drm] Connector 2:
[   11.443626] [drm]   SVIDEO-1
[   11.443627] [drm]   Encoders:
[   11.443629] [drm]     TV1: INTERNAL_DAC2
[   11.451142] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   11.451149] Bluetooth: BNEP filters: protocol multicast
[   11.458601] usbcore: registered new interface driver snd-usb-audio
[   11.481612] bttv: driver version 0.9.19 loaded
[   11.481620] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   11.482353] bttv: Bt8xx card found (0)
[   11.482383] bttv: 0: Bt878 (rev 17) at 0000:02:01.0, irq: 22, latency: 32, mmio: 0xdfefe000
[   11.482983] bttv: 0: detected: Pinnacle PCTV [card=39], PCI subsystem ID is 11bd:0012
[   11.482987] bttv: 0: using: Pinnacle PCTV Studio/Rave [card=39,autodetected]
[   11.483128] bttv: 0: i2c: checking for MSP34xx @ 0x80... not found
[   11.483768] bttv: 0: pinnacle/mt: id=1 info="PAL / mono" radio=no
[   11.483771] bttv: 0: tuner type=33
[   11.525579] coretemp coretemp.0: Using relative temperature scale!
[   11.525611] coretemp coretemp.0: Using relative temperature scale!
[   11.552408] [drm] fb mappable at 0xC0040000
[   11.552414] [drm] vram apper at 0xC0000000
[   11.552425] [drm] size 3145728
[   11.552428] [drm] fb depth is 24
[   11.552430] [drm]    pitch is 4096
[   11.555590] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   11.555598] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.555601] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   11.555604] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.555607] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   11.555610] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.555613] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   11.555616] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.555619] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   11.555622] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.555624] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   11.555628] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.555630] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   11.555634] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.555636] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   11.555639] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.555642] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   11.555645] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.555648] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   11.555651] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.555654] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   11.555657] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.555660] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   11.555663] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   11.555666] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   11.555669] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   11.555671] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   11.555675] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   11.557375] fbcon: radeondrmfb (fb0) is primary device
[   11.561646] Console: switching to colour frame buffer device 100x37
[   11.561682] fb0: radeondrmfb frame buffer device
[   11.561685] drm: registered panic notifier
[   11.561700] [drm] Initialized radeon 2.18.0 20080528 for 0000:01:00.0 on minor 0
[   11.613805] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   11.614545] zd1211rw 1-3:1.0: phy0
[   11.614614] usbcore: registered new interface driver zd1211rw
[   11.769120] bttv: 0: audio absent, no audio device found!
[   11.901265] zd1211rw 1-3:1.0: firmware version 4725
[   11.941251] zd1211rw 1-3:1.0: zd1211b chip 0cde:001a v4810 high 00-60-b3 AL2230_RF pa0 g--NS
[   11.943965] cfg80211: Calling CRDA for country: DE
[   11.978019] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   11.978403] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   11.998382] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   11.998389] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   11.998392] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   11.998395] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   11.998398] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   11.998401] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   11.998404] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   11.998407] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   11.998410] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   11.998413] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   11.998415] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   11.998418] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   11.998421] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   11.998424] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   11.998427] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   11.998430] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   11.998432] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   11.998435] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   11.998438] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   11.998441] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   11.998444] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   11.998447] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   11.998450] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   11.998453] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   11.998456] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   11.998459] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   11.998462] cfg80211: Disabling freq 2484 MHz
[   11.998465] cfg80211: Regulatory domain changed to country: DE
[   11.998467] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   11.998470] cfg80211:   (2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   11.998473] cfg80211:   (5150000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   11.998476] cfg80211:   (5250000 KHz - 5350000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   11.998479] cfg80211:   (5470000 KHz - 5725000 KHz @ 40000 KHz), (N/A, 2698 mBm)
[   12.174838] tda9887 3-0043: creating new instance
[   12.174847] tda9887 3-0043: tda988[5/6/7] found
[   12.175513] tuner 3-0043: Tuner 74 found with type(s) Radio TV.
[   12.206778] Chip ID is not zero. It is not a TEA5767
[   12.206793] tuner 3-0060: Tuner -1 found with type(s) Radio TV.
[   12.245797] mt20xx 3-0060: microtune: companycode=4d54 part=04 rev=04
[   12.328559] mt20xx 3-0060: microtune MT2032 found, OK
[   12.352267] bttv: 0: registered device video0
[   12.352434] bttv: 0: registered device vbi0
[   12.352456] bttv: 0: Setting PLL: 28636363 => 35468950 (needs up to 100ms)
[   12.385063] bttv: PLL set ok
[   12.878068] [drm] crtc 1 is connected to a TV
[   13.793523] wlan1: authenticate with 00:90:a2:44:07:47
[   13.817542] wlan1: send auth to 00:90:a2:44:07:47 (try 1/3)
[   13.819865] wlan1: authenticated
[   13.832056] wlan1: associate with 00:90:a2:44:07:47 (try 1/3)
[   13.836288] wlan1: RX AssocResp from 00:90:a2:44:07:47 (capab=0x431 status=0 aid=2)
[   13.837042] wlan1: associated
[   13.837435] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[   13.837534] cfg80211: Calling CRDA for country: IT
[   13.845760] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   13.845769] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   13.845773] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   13.845776] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   13.845778] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   13.845782] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   13.845784] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   13.845787] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   13.845790] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   13.845793] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   13.845796] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   13.845799] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   13.845802] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   13.845805] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   13.845807] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   13.845810] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   13.845813] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   13.845819] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   13.845821] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   13.845825] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   13.845827] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   13.845830] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   13.845833] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   13.845836] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   13.845839] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   13.845842] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   13.845844] cfg80211: Disabling freq 2484 MHz
[   13.845848] cfg80211: Regulatory domain changed to country: IT
[   13.845850] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   13.845853] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   13.845856] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   13.845859] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   13.845861] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[   13.925396] [drm] not detecting due to 00000004
[   13.928668] [drm] not detecting due to 00000004
[   14.117067] [drm] not detecting due to 00000004
[   14.118111] [drm] not detecting due to 00000004
[   14.165309] [drm] not detecting due to 00000004
[   14.166375] [drm] not detecting due to 00000004
[   14.261729] [drm] not detecting due to 00000004
[   14.262764] [drm] not detecting due to 00000004
[   14.314582] [drm] not detecting due to 00000004
[   14.315616] [drm] not detecting due to 00000004
[   14.487327] [drm] not detecting due to 00000004
[  299.816014] [Hardware Error]: Machine check events logged

```

Please..hints?

---

### Post by Fr333 on 2013-02-24
and when I press

lshw -c display | grep driver

it stucks displaying "PCI (sysfs)"

---

