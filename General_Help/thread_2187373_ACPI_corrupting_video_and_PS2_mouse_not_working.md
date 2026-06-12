---
title: "ACPI corrupting video and PS/2 mouse not working"
date: 2013-11-11
forum: General Help
---

### Post by violinuxer on 2013-11-11
Hello all!

I have a bit of an interesting problem with regards to a computer I am resurrecting as one of my pet projects. It's a dinosaur, a dell Inspiron 2600 with 128MB of ram and a 1.6 Ghz processor and a gigantic 20Gig hard drive that I decided to revive as a somewhat dumb serial terminal just for fun. After a several hour install process, I managed to get the complete barebones command line version of ubuntu running on the machine (from the minimal install iso).

After first boot, the keyboard and mouse to work. They worked up through grub and in bios, but as soon as control reached the kernel, the operating system would fail to initialize the PS/2 controller, giving a message in the syslog that explaining that the i8042 driver "couldn't read CTR" and therefore failed to initialize. Occasionally, however, it would initialize and the internal mouse and keyboard would work.

After a bit of research on the forums, I found some posts claiming that ACPI would conflict with the PS/2 driver. I disabled ACPI in the grub command line "acpi=off" and the keyboard and mouse began to work. On the next reboot however, the real problems began. Instead of displaying the kernel messages, all that appeared was a bunch of white rectangles where the characters should have been. It then switched to a screen with a white background with somewhat-klingon looking symbols on the screen. On further examination, the symbols could be seen to be parts of the characters, somehow flipped backwards.

However, if I boot via the grub menu, go to edit the command line, and then boot from there by hitting F10 or Ctrl-x, the screen works fine.

Take a look at the highlighted sections below. At first it has trouble trying to allocate a framebuffer, and then has issues further down and leaves sone kind of stack trace. Whats going on?

Does anyone know what might be going on or how I should go about fixing it?

Thanks so much!

violinuxer

Heres the dmesg output of a boot where the video fails:

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.8.0-27-generic (buildd@akateko) (gcc version 4.7.3 (Ubuntu/Linaro 4.7.3-1ubuntu1) ) #40-Ubuntu SMP Tue Jul 9 00:19:35 UTC 2013 (Ubuntu 3.8.0-27.40-generic 3.8.13.4)
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
[    0.000000] BIOS-e820: [mem 0x00000000000ce000-0x00000000000cffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000d8000-0x00000000000dffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e4000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000076effff] usable
[    0.000000] BIOS-e820: [mem 0x00000000076f0000-0x00000000076fefff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000076ff000-0x00000000076fffff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x0000000007700000-0x000000000777ffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000007780000-0x0000000007ffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffb80000-0x00000000ffbfffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fff00000-0x00000000ffffffff] reserved
[    0.000000] Notice: NX (Execute Disable) protection missing in CPU!
[    0.000000] SMBIOS 2.3 present.
[    0.000000] DMI: Dell Computer Corporation Inspiron 2600/Inspiron 2600, BIOS A09 02/24/2003
[    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0x7780 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FF8000000 write-back
[    0.000000]   1 base 007F80000 mask FFFF80000 uncachable
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] PAT not supported by CPU.
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 128MB, type WB
[    0.000000] reg 1, base: 130560KB, range: 512KB, type UC
[    0.000000] total RAM covered: 127M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 1M     num_reg: 2      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 128MB, type WB
[    0.000000] reg 1, base: 130560KB, range: 512KB, type UC
[    0.000000] initial memory mapped: [mem 0x00000000-0x01ffffff]
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: [mem 0x00000000-0x0777ffff]
[    0.000000]  [mem 0x00000000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x075fffff] page 2M
[    0.000000]  [mem 0x07600000-0x0777ffff] page 4k
[    0.000000] kernel direct mapping tables up to 0x777ffff @ [mem 0x01ffa000-0x01ffffff]
[    0.000000] RAMDISK: [mem 0x06c76000-0x06eb8fff]
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 119MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 07780000
[    0.000000]   low ram: 0 - 07780000
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00010000-0x00ffffff]
[    0.000000]   Normal   [mem 0x01000000-0x0777ffff]
[    0.000000]   HighMem  empty
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00010000-0x0009efff]
[    0.000000]   node   0: [mem 0x00100000-0x076effff]
[    0.000000]   node   0: [mem 0x07700000-0x0777ffff]
[    0.000000] On node 0 totalpages: 30463
[    0.000000] free_area_init_node: node 0, pgdat c18f7f00, node_mem_map c7600200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 207 pages used for memmap
[    0.000000]   Normal zone: 26273 pages, LIFO batch:7
[    0.000000] Using APIC driver default
[    0.000000] SFI: Simple Firmware Interface v0.81 http://simplefirmware.org
[    0.000000] smpboot: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] APIC: disable apic facility
[    0.000000] APIC: switched to apic NOOP
[    0.000000] nr_irqs_gsi: 16
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000ce000
[    0.000000] PM: Registered nosave memory: 00000000000ce000 - 00000000000d0000
[    0.000000] PM: Registered nosave memory: 00000000000d0000 - 00000000000d8000
[    0.000000] PM: Registered nosave memory: 00000000000d8000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000076f0000 - 00000000076ff000
[    0.000000] PM: Registered nosave memory: 00000000076ff000 - 0000000007700000
[    0.000000] e820: [mem 0x08000000-0xffb7ffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c776e000 s35008 r0 d22336 u57344
[    0.000000] pcpu-alloc: s35008 r0 d22336 u57344 alloc=14*4096
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 30224
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-27-generic root=UUID=39c090ff-b959-494f-a7e7-ff48056a9e42 ro acpi=off
[    0.000000] PID hash table entries: 512 (order: -1, 2048 bytes)
[    0.000000] Dentry cache hash table entries: 16384 (order: 4, 65536 bytes)
[    0.000000] Inode-cache hash table entries: 8192 (order: 3, 32768 bytes)
[    0.000000] __ex_table already sorted, skipping sort
[    0.000000] Initializing CPU#0
[    0.000000] allocated 244608 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00000000:00000000)
[    0.000000] Memory: 107152k/122368k available (6257k kernel code, 14700k reserved, 2975k data, 788k init, 0k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff14000 - 0xfffff000   ( 940 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xc7f80000 - 0xffbfe000   ( 892 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xc7780000   ( 119 MB)
[    0.000000]       .init : 0xc1905000 - 0xc19ca000   ( 788 kB)
[    0.000000]       .data : 0xc161c470 - 0xc1904240   (2975 kB)
[    0.000000]       .text : 0xc1000000 - 0xc161c470   (6257 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=8 to nr_cpu_ids=1.
[    0.000000] NR_IRQS:2304 nr_irqs:256 16
[    0.000000] CPU 0 irqstacks, hard=c7006000 soft=c7008000
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 1196.136 MHz processor
[    0.004004] Calibrating delay loop (skipped), value calculated using timer frequency.. 2392.27 BogoMIPS (lpj=4784544)
[    0.004027] pid_max: default: 32768 minimum: 301
[    0.004112] Security Framework initialized
[    0.004153] AppArmor: AppArmor initialized
[    0.004164] Yama: becoming mindful.
[    0.004333] Mount-cache hash table entries: 512
[    0.008193] Initializing cgroup subsys cpuacct
[    0.008211] Initializing cgroup subsys memory
[    0.008241] Initializing cgroup subsys devices
[    0.008254] Initializing cgroup subsys freezer
[    0.008266] Initializing cgroup subsys blkio
[    0.008278] Initializing cgroup subsys perf_event
[    0.008293] Initializing cgroup subsys hugetlb
[    0.008378] mce: CPU supports 5 MCE banks
[    0.008429] Last level iTLB entries: 4KB 32, 2MB 0, 4MB 2
[    0.008429] Last level dTLB entries: 4KB 64, 2MB 0, 4MB 8
[    0.008429] tlb_flushall_shift: 6
[    0.020432] Freeing SMP alternatives: 24k freed
[    0.026084] ftrace: allocating 26135 entries in 52 pages
[    0.044386] smpboot: weird, boot CPU (#0) not listed by the BIOS
[    0.044426] smpboot: SMP motherboard not detected
[    0.044436] smpboot: Local APIC not detected. Using dummy APIC emulation.
[    0.044447] smpboot: SMP disabled
[    0.044456] Performance Events: 
[    0.044468] no APIC, boot with the "lapic" boot parameter to force-enable it.
[    0.044481] no hardware sampling interrupt available.
[    0.044493] p6 PMU driver.
[    0.044504] ... version:                0
[    0.044512] ... bit width:              32
[    0.044520] ... generic registers:      2
[    0.044529] ... value mask:             00000000ffffffff
[    0.044539] ... max period:             000000007fffffff
[    0.044548] ... fixed-purpose events:   0
[    0.044556] ... event mask:             0000000000000003
[    0.048894] Brought up 1 CPUs
[    0.048929] smpboot: Total of 1 processors activated (2392.27 BogoMIPS)
[    0.049126] NMI watchdog: disabled (cpu0): not supported (no LAPIC?)
[    0.049552] devtmpfs: initialized
[    0.050026] EVM: security.selinux
[    0.050037] EVM: security.SMACK64
[    0.050046] EVM: security.capability
[    0.050267] PM: Registering ACPI NVS region [mem 0x076ff000-0x076fffff] (4096 bytes)
[    0.053332] regulator-dummy: no parameters
[    0.053531] NET: Registered protocol family 16
[    0.053889] EISA bus registered
[    0.072391] PCI: PCI BIOS revision 2.10 entry at 0xfd9ca, last bus=2
[    0.072408] PCI: Using configuration type 1 for base access
[    0.075348] bio: create slab <bio-0> at 0
[    0.075657] ACPI: Interpreter disabled.
[    0.075904] vgaarb: loaded
[    0.076543] SCSI subsystem initialized
[    0.076711] libata version 3.00 loaded.
[    0.076836] usbcore: registered new interface driver usbfs
[    0.076874] usbcore: registered new interface driver hub
[    0.076958] usbcore: registered new device driver usb
[    0.077272] PCI: Probing PCI hardware
[    0.077291] PCI: root bus 00: using default resources
[    0.077296] PCI: Probing PCI hardware (bus 00)
[    0.077366] PCI host bridge to bus 0000:00
[    0.077384] pci_bus 0000:00: root bus resource [io  0x0000-0xffff]
[    0.077398] pci_bus 0000:00: root bus resource [mem 0x00000000-0xfffffffff]
[    0.077412] pci_bus 0000:00: No busn resource found for root bus, will use [bus 00-ff]
[    0.077450] pci 0000:00:00.0: [8086:3575] type 00 class 0x060000
[    0.077533] pci 0000:00:02.0: [8086:3577] type 00 class 0x030000
[    0.077553] pci 0000:00:02.0: reg 10: [mem 0xe8000000-0xefffffff pref]
[    0.077565] pci 0000:00:02.0: reg 14: [mem 0xe0000000-0xe007ffff]
[    0.077617] pci 0000:00:02.0: supports D1
[    0.077638] pci 0000:00:02.1: [8086:3577] type 00 class 0x038000
[    0.077655] pci 0000:00:02.1: reg 10: [mem 0xf0000000-0xf7ffffff pref]
[    0.077667] pci 0000:00:02.1: reg 14: [mem 0xe0080000-0xe00fffff]
[    0.077718] pci 0000:00:02.1: supports D1
[    0.077781] pci 0000:00:1d.0: [8086:2482] type 00 class 0x0c0300
[    0.077833] pci 0000:00:1d.0: reg 20: [io  0x1800-0x181f]
[    0.077881] pci 0000:00:1d.1: [8086:2484] type 00 class 0x0c0300
[    0.077934] pci 0000:00:1d.1: reg 20: [io  0x1820-0x183f]
[    0.077995] pci 0000:00:1e.0: [8086:2448] type 01 class 0x060400
[    0.078054] pci 0000:00:1f.0: [8086:248c] type 00 class 0x060100
[    0.078135] pci 0000:00:1f.0: quirk: [io  0x1000-0x107f] claimed by ICH4 ACPI/GPIO/TCO
[    0.078156] pci 0000:00:1f.0: quirk: [io  0x1180-0x11bf] claimed by ICH4 GPIO
[    0.078190] pci 0000:00:1f.1: [8086:248a] type 00 class 0x01018a
[    0.078212] pci 0000:00:1f.1: reg 10: [io  0x01f0-0x01f7]
[    0.078227] pci 0000:00:1f.1: reg 14: [io  0x03f4-0x03f7]
[    0.078242] pci 0000:00:1f.1: reg 18: [io  0x0170-0x0177]
[    0.078257] pci 0000:00:1f.1: reg 1c: [io  0x0374-0x0377]
[    0.078272] pci 0000:00:1f.1: reg 20: [io  0x1860-0x186f]
[    0.078287] pci 0000:00:1f.1: reg 24: [mem 0xe0100000-0xe01003ff]
[    0.078330] pci 0000:00:1f.3: [8086:2483] type 00 class 0x0c0500
[    0.078383] pci 0000:00:1f.3: reg 20: [io  0x1880-0x189f]
[    0.078432] pci 0000:00:1f.5: [8086:2485] type 00 class 0x040100
[    0.078452] pci 0000:00:1f.5: reg 10: [io  0x1c00-0x1cff]
[    0.078467] pci 0000:00:1f.5: reg 14: [io  0x18c0-0x18ff]
[    0.078539] pci 0000:00:1f.6: [8086:2486] type 00 class 0x070300
[    0.078559] pci 0000:00:1f.6: reg 10: [io  0x2400-0x24ff]
[    0.078574] pci 0000:00:1f.6: reg 14: [io  0x2000-0x207f]
[    0.078669] pci 0000:02:01.0: [10b7:9200] type 00 class 0x020000
[    0.078692] pci 0000:02:01.0: reg 10: [io  0x3000-0x307f]
[    0.078706] pci 0000:02:01.0: reg 14: [mem 0xe0200000-0xe020007f]
[    0.078752] pci 0000:02:01.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.078785] pci 0000:02:01.0: supports D1 D2
[    0.078791] pci 0000:02:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.078823] pci 0000:02:04.0: [1217:6972] type 02 class 0x060700
[    0.078846] pci 0000:02:04.0: reg 10: [mem 0x00000000-0x00000fff]
[    0.078882] pci 0000:02:04.0: supports D1 D2
[    0.078888] pci 0000:02:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.078938] pci 0000:00:1e.0: PCI bridge to [bus 02] (subtractive decode)
[    0.078955] pci 0000:00:1e.0:   bridge window [io  0x3000-0x3fff]
[    0.078964] pci 0000:00:1e.0:   bridge window [mem 0xe0200000-0xe02fffff]
[    0.078974] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.078980] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xfffffffff] (subtractive decode)
[    0.078988] pci 0000:02:04.0: bridge configuration invalid ([bus 00-00]), reconfiguring
[    0.079039] pci_bus 0000:03: busn_res: can not insert [bus 03-ff] under [bus 02] (conflicts with (null) [bus 02])
[    0.079050] pci_bus 0000:03: busn_res: [bus 03-ff] end is updated to 06
[    0.079058] pci_bus 0000:03: busn_res: can not insert [bus 03-06] under [bus 02] (conflicts with (null) [bus 02])
[    0.079068] pci_bus 0000:03: [bus 03-06] partially hidden behind transparent bridge 0000:02 [bus 02]
[    0.079095] pci_bus 0000:00: busn_res: [bus 00-ff] end is updated to 06
[    0.079223] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.080088] pci 0000:00:1f.0: PIIX/ICH IRQ router [8086:248c]
[    0.080131] PCI: setting IRQ 11 as level-triggered
[    0.080139] pci 0000:00:1f.1: found PCI INT A -> IRQ 11
[    0.080179] PCI: pci_cache_line_size set to 32 bytes
[    0.080251] e820: reserve RAM buffer [mem 0x0009f000-0x0009ffff]
[    0.080259] e820: reserve RAM buffer [mem 0x076f0000-0x07ffffff]
[    0.080264] e820: reserve RAM buffer [mem 0x07780000-0x07ffffff]
[    0.080573] NetLabel: Initializing
[    0.080587] NetLabel:  domain hash size = 128
[    0.080595] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.080629] NetLabel:  unlabeled traffic allowed by default
[    0.080910] Switching to clocksource pit
[    0.103728] AppArmor: AppArmor Filesystem Enabled
[    0.103828] pnp: PnP ACPI: disabled
[    0.103845] PnPBIOS: Scanning system for PnP BIOS support...
[    0.103917] PnPBIOS: Found PnP BIOS installation structure at 0xc00f6970
[    0.103937] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0x9b8c, dseg 0x400
[    0.104410] pnp 00:00: [io  0x0010-0x001f]
[    0.104420] pnp 00:00: [io  0x0024-0x0025]
[    0.104426] pnp 00:00: [io  0x0028-0x0029]
[    0.104432] pnp 00:00: [io  0x002c-0x002d]
[    0.104438] pnp 00:00: [io  0x0030-0x0031]
[    0.104444] pnp 00:00: [io  0x0034-0x0035]
[    0.104450] pnp 00:00: [io  0x0038-0x0039]
[    0.104455] pnp 00:00: [io  0x003c-0x003d]
[    0.104461] pnp 00:00: [io  0x0050-0x0053]
[    0.104467] pnp 00:00: [io  0x0072-0x0073]
[    0.104473] pnp 00:00: [io  0x0074-0x0075]
[    0.104479] pnp 00:00: [io  0x0076-0x0077]
[    0.104485] pnp 00:00: [io  0x0080]
[    0.104491] pnp 00:00: [io  0x0090-0x0091]
[    0.104496] pnp 00:00: [io  0x0092]
[    0.104502] pnp 00:00: [io  0x0093-0x009f]
[    0.104508] pnp 00:00: [io  0x00a4-0x00a5]
[    0.104514] pnp 00:00: [io  0x00a8-0x00a9]
[    0.104520] pnp 00:00: [io  0x00ac-0x00ad]
[    0.104526] pnp 00:00: [io  0x00b0-0x00b1]
[    0.104532] pnp 00:00: [io  0x00b2-0x00b3]
[    0.104537] pnp 00:00: [io  0x00b4-0x00b5]
[    0.104550] pnp 00:00: [io  0x00b8-0x00b9]
[    0.104556] pnp 00:00: [io  0x00bc-0x00bd]
[    0.104564] pnp 00:00: [mem 0xfffffffffff00000-0xffffffffffffffff]
[    0.104707] system 00:00: [mem 0xfffffffffff00000-0xffffffffffffffff] could not be reserved
[    0.104740] system 00:00: Plug and Play BIOS device, IDs PNP0c02 (active)
[    0.104761] pnp 00:01: [mem 0x00000000-0x0009ffff]
[    0.104768] pnp 00:01: [mem 0x000e4000-0x000fffff]
[    0.104774] pnp 00:01: [mem 0x00100000-0x075fffff]
[    0.104836] system 00:01: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.104854] system 00:01: [mem 0x000e4000-0x000fffff] could not be reserved
[    0.104869] system 00:01: [mem 0x00100000-0x075fffff] could not be reserved
[    0.104885] system 00:01: Plug and Play BIOS device, IDs PNP0c01 (active)
[    0.104901] pnp 00:02: [io  0x0000-0x000f]
[    0.104908] pnp 00:02: [io  0x0081-0x008f]
[    0.104914] pnp 00:02: [io  0x00c0-0x00df]
[    0.104920] pnp 00:02: [dma 4]
[    0.104957] pnp 00:02: Plug and Play BIOS device, IDs PNP0200 (active)
[    0.104973] pnp 00:03: [io  0x0020-0x0021]
[    0.104979] pnp 00:03: [io  0x00a0-0x00a1]
[    0.104986] pnp 00:03: [irq 2]
[    0.105031] pnp 00:03: Plug and Play BIOS device, IDs PNP0000 (active)
[    0.105048] pnp 00:04: [io  0x0040-0x0043]
[    0.105054] pnp 00:04: [irq 0]
[    0.105090] pnp 00:04: Plug and Play BIOS device, IDs PNP0100 (active)
[    0.105112] pnp 00:05: [io  0x0070-0x0071]
[    0.105118] pnp 00:05: [irq 8]
[    0.105154] pnp 00:05: Plug and Play BIOS device, IDs PNP0b00 (active)
[    0.105170] pnp 00:06: [io  0x0060]
[    0.105177] pnp 00:06: [io  0x0064]
[    0.105183] pnp 00:06: [irq 1]
[    0.105218] pnp 00:06: Plug and Play BIOS device, IDs PNP0303 (active)
[    0.105235] pnp 00:07: [io  0x00f0-0x00ff]
[    0.105241] pnp 00:07: [irq 13]
[    0.105283] pnp 00:07: Plug and Play BIOS device, IDs PNP0c04 (active)
[    0.105299] pnp 00:08: [io  0x0061]
[    0.105335] pnp 00:08: Plug and Play BIOS device, IDs PNP0800 (active)
[    0.105352] pnp 00:09: [io  0x0cf8-0x0cff]
[    0.105388] pnp 00:09: Plug and Play BIOS device, IDs PNP0a03 (active)
[    0.105405] pnp 00:0a: [io  0x04d0-0x04d1]
[    0.105412] pnp 00:0a: [io  0x1000-0x105f]
[    0.105418] pnp 00:0a: [io  0x1060-0x107f]
[    0.105424] pnp 00:0a: [io  0x1180-0x11bf]
[    0.105443] pnp 00:0a: disabling [io  0x1000-0x105f] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.105463] pnp 00:0a: disabling [io  0x1060-0x107f] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.105527] system 00:0a: [io  0x04d0-0x04d1] has been reserved
[    0.105543] system 00:0a: [io  0x1180-0x11bf] has been reserved
[    0.105559] system 00:0a: Plug and Play BIOS device, IDs PNP0c02 (active)
[    0.105583] pnp 00:0b: [mem 0xffffffffffb80000-0xffffffffffbfffff]
[    0.105590] pnp 00:0b: [mem 0xffffffffffb00000-0xffffffffffb7ffff]
[    0.105597] pnp 00:0b: [mem 0xffffffffffa80000-0xffffffffffafffff]
[    0.105603] pnp 00:0b: [mem 0xffffffffffa00000-0xffffffffffa7ffff]
[    0.105610] pnp 00:0b: [mem 0xffffffffff980000-0xffffffffff9fffff]
[    0.105617] pnp 00:0b: [mem 0xffffffffff900000-0xffffffffff97ffff]
[    0.105623] pnp 00:0b: [mem 0xffffffffff880000-0xffffffffff8fffff]
[    0.105630] pnp 00:0b: [mem 0xffffffffff800000-0xffffffffff87ffff]
[    0.105636] pnp 00:0b: [mem 0xffffffffff000000-0xffffffffff07ffff]
[    0.105682] pnp 00:0b: Plug and Play BIOS device, IDs INT0800 (active)
[    0.105708] pnp 00:0c: [mem 0x000dc000-0x000dffff]
[    0.105763] system 00:0c: [mem 0x000dc000-0x000dffff] could not be reserved
[    0.105783] system 00:0c: Plug and Play BIOS device, IDs PNP0c02 (active)
[    0.105808] pnp 00:0d: [mem 0x000d8000-0x000dbfff]
[    0.105866] system 00:0d: [mem 0x000d8000-0x000dbfff] could not be reserved
[    0.105884] system 00:0d: Plug and Play BIOS device, IDs PNP0c02 (active)
[    0.106079] pnp 00:0f: [mem 0x000cd800-0x000cffff]
[    0.106132] system 00:0f: [mem 0x000cd800-0x000cffff] could not be reserved
[    0.106149] system 00:0f: Plug and Play BIOS device, IDs PNP0c02 (active)
[    0.106651] pnp 00:12: [io  0x0378-0x037f]
[    0.106657] pnp 00:12: [io  0x0778-0x077f]
[    0.106664] pnp 00:12: [irq 7]
[    0.106670] pnp 00:12: [dma 3]
[    0.106818] pnp 00:12: Plug and Play BIOS device, IDs PNP0401 (active)
[    0.107128] pnp 00:13: [irq 12]
[    0.107173] pnp 00:13: Plug and Play BIOS device, IDs PNP0f13 (active)
[    0.107456] pnp 00:15: [io  0x03f0-0x03f5]
[    0.107463] pnp 00:15: [io  0x03f7]
[    0.107469] pnp 00:15: [irq 6]
[    0.107474] pnp 00:15: [dma 2]
[    0.107545] pnp 00:15: Plug and Play BIOS device, IDs PNP0700 (active)
[    0.107559] PnPBIOS: 18 nodes reported by PnP BIOS; 18 recorded by driver
[    0.112027] pci 0000:02:04.0: res[15]=[mem 0x04000000-0x03ffffff pref] get_res_add_size add_size 4000000
[    0.112047] pci 0000:00:1e.0: bridge window [mem 0x02000000-0x03ffffff pref] to [bus 02] add_size 4000000
[    0.112068] pci 0000:00:1e.0: res[15]=[mem 0x02000000-0x03ffffff pref] get_res_add_size add_size 4000000
[    0.112089] pci 0000:00:1e.0: BAR 15: assigned [mem 0x08000000-0x0dffffff pref]
[    0.112126] pci 0000:02:04.0: res[15]=[mem 0x04000000-0x03ffffff pref] get_res_add_size add_size 4000000
[    0.112134] pci 0000:02:04.0: res[16]=[mem 0x04000000-0x03ffffff] get_res_add_size add_size 4000000
[    0.112141] pci 0000:02:04.0: res[13]=[io  0x0100-0x00ff] get_res_add_size add_size 100
[    0.112148] pci 0000:02:04.0: res[14]=[io  0x0100-0x00ff] get_res_add_size add_size 100
[    0.112159] pci 0000:02:04.0: BAR 0: assigned [mem 0x10000000-0x10000fff]
[    0.112180] pci 0000:02:04.0: BAR 15: assigned [mem 0x08000000-0x0bffffff pref]
[    0.112201] pci 0000:02:04.0: BAR 16: assigned [mem 0x14000000-0x17ffffff]
[    0.112217] pci 0000:02:01.0: BAR 6: assigned [mem 0x0c000000-0x0c01ffff pref]
[    0.112234] pci 0000:02:04.0: BAR 13: assigned [io  0x3400-0x34ff]
[    0.112248] pci 0000:02:04.0: BAR 14: assigned [io  0x3800-0x38ff]
[    0.112263] pci 0000:02:04.0: CardBus bridge to [bus 03-06]
[    0.112276] pci 0000:02:04.0:   bridge window [io  0x3400-0x34ff]
[    0.112291] pci 0000:02:04.0:   bridge window [io  0x3800-0x38ff]
[    0.112307] pci 0000:02:04.0:   bridge window [mem 0x08000000-0x0bffffff pref]
[    0.112325] pci 0000:02:04.0:   bridge window [mem 0x14000000-0x17ffffff]
[    0.112340] pci 0000:00:1e.0: PCI bridge to [bus 02]
[    0.112354] pci 0000:00:1e.0:   bridge window [io  0x3000-0x3fff]
[    0.112370] pci 0000:00:1e.0:   bridge window [mem 0xe0200000-0xe02fffff]
[    0.112387] pci 0000:00:1e.0:   bridge window [mem 0x08000000-0x0dffffff pref]
[    0.112419] pci 0000:00:1e.0: setting latency timer to 64
[    0.112436] PCI: setting IRQ 10 as level-triggered
[    0.112443] pci 0000:02:04.0: found PCI INT A -> IRQ 10
[    0.112459] pci 0000:02:04.0: sharing IRQ 10 with 0000:00:02.0
[    0.112474] pci 0000:02:04.0: sharing IRQ 10 with 0000:00:1d.0
[    0.112506] pci 0000:02:04.0: setting latency timer to 64
[    0.112515] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
[    0.112522] pci_bus 0000:00: resource 5 [mem 0x00000000-0xfffffffff]
[    0.112529] pci_bus 0000:02: resource 0 [io  0x3000-0x3fff]
[    0.112535] pci_bus 0000:02: resource 1 [mem 0xe0200000-0xe02fffff]
[    0.112542] pci_bus 0000:02: resource 2 [mem 0x08000000-0x0dffffff pref]
[    0.112548] pci_bus 0000:02: resource 4 [io  0x0000-0xffff]
[    0.112555] pci_bus 0000:02: resource 5 [mem 0x00000000-0xfffffffff]
[    0.112561] pci_bus 0000:03: resource 0 [io  0x3400-0x34ff]
[    0.112568] pci_bus 0000:03: resource 1 [io  0x3800-0x38ff]
[    0.112574] pci_bus 0000:03: resource 2 [mem 0x08000000-0x0bffffff pref]
[    0.112581] pci_bus 0000:03: resource 3 [mem 0x14000000-0x17ffffff]
[    0.112707] NET: Registered protocol family 2
[    0.113102] TCP established hash table entries: 1024 (order: 1, 8192 bytes)
[    0.113141] TCP bind hash table entries: 1024 (order: 1, 8192 bytes)
[    0.113171] TCP: Hash tables configured (established 1024 bind 1024)
[    0.113240] TCP: reno registered
[    0.113258] UDP hash table entries: 256 (order: 1, 8192 bytes)
[    0.113287] UDP-Lite hash table entries: 256 (order: 1, 8192 bytes)
[    0.113471] NET: Registered protocol family 1
[    0.113534] pci 0000:00:02.0: Boot video device
[    0.113564] pci 0000:00:1d.0: found PCI INT A -> IRQ 10
[    0.113580] pci 0000:00:1d.0: sharing IRQ 10 with 0000:00:02.0
[    0.113616] pci 0000:00:1d.0: sharing IRQ 10 with 0000:02:04.0
[    0.113657] pci 0000:00:1d.1: found PCI INT B -> IRQ 11
[    0.113734] PCI: CLS 32 bytes, default 32
[    0.113883] Trying to unpack rootfs image as initramfs...
[    0.239373] Freeing initrd memory: 2316k freed
[    0.245827] Initialise module verification
[    0.245988] audit: initializing netlink socket (disabled)
[    0.246036] type=2000 audit(1384205740.240:1): initialized
[    0.293454] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.297327] VFS: Disk quotas dquot_6.5.2
[    0.297502] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.299212] fuse init (API version 7.20)
[    0.299485] msgmni has been set to 213
[    0.300561] Key type asymmetric registered
[    0.300588] Asymmetric key parser 'x509' registered
[    0.300740] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.300871] io scheduler noop registered
[    0.300885] io scheduler deadline registered (default)
[    0.300923] io scheduler cfq registered
[    0.301239] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.301299] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[COLOR=#ffff00][    0.301538] efifb: probing for efifb
[    0.301554] efifb: cannot reserve video memory at 0xa6d60
[    0.301570] efifb: framebuffer at 0xa6d60, mapped to 0xc00a6d60, using 56k, total 64k
[    0.301585] efifb: mode is 640x350x1, linelength=80, pages=1
[    0.301594] efifb: scrolling: redraw
[    0.301605] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0[/COLOR]
[    0.305807] Console: switching to colour frame buffer device 80x43
[    0.309640] fb0: EFI VGA frame buffer device
[    0.309745] intel_idle: does not run on family 6 model 11
[    0.310173] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.311307] isapnp: Scanning for PnP cards...
[    0.319394] serial 0000:00:1f.6: found PCI INT B -> IRQ 10
[    0.319552] serial 0000:00:1f.6: sharing IRQ 10 with 0000:00:1f.3
[    0.319657] serial 0000:00:1f.6: sharing IRQ 10 with 0000:00:1f.5
[    0.319774] serial 0000:00:1f.6: sharing IRQ 10 with 0000:02:01.0
[    0.320320] Linux agpgart interface v0.103
[    0.320559] agpgart-intel 0000:00:00.0: Intel 830M Chipset
[    0.320735] agpgart-intel 0000:00:00.0: detected gtt size: 131072K total, 131072K mappable
[    0.321200] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    0.321661] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xe8000000
[    0.369139] brd: module loaded
[    0.414940] loop: module loaded
[    0.415503] ata_piix 0000:00:1f.1: version 2.13
[    0.415529] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[    0.415670] ata_piix 0000:00:1f.1: found PCI INT A -> IRQ 11
[    0.415917] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.416604] scsi0 : ata_piix
[    0.419518] scsi1 : ata_piix
[    0.425777] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1860 irq 14
[    0.428457] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1868 irq 15
[    0.435823] libphy: Fixed MDIO Bus: probed
[    0.486706] tun: Universal TUN/TAP device driver, 1.6
[    0.489199] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.491766] PPP generic driver version 2.4.2
[    0.497887] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.500409] ehci-pci: EHCI PCI platform driver
[    0.506654] ehci-platform: EHCI generic platform driver
[    0.509228] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.511701] uhci_hcd: USB Universal Host Controller Interface driver
[    0.517772] uhci_hcd 0000:00:1d.0: found PCI INT A -> IRQ 10
[    0.520231] uhci_hcd 0000:00:1d.0: sharing IRQ 10 with 0000:00:02.0
[    0.526724] uhci_hcd 0000:00:1d.0: sharing IRQ 10 with 0000:02:04.0
[    0.528663] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.528672] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.578585] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    0.582747] uhci_hcd 0000:00:1d.0: irq 10, io base 0x00001800
[    0.585314] usb usb1: New USB device found, idVendor=1d6b, idProduct=0001
[    0.587637] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.591641] usb usb1: Product: UHCI Host Controller
[    0.598007] usb usb1: Manufacturer: Linux 3.8.0-27-generic uhci_hcd
[    0.599995] usb usb1: SerialNumber: 0000:00:1d.0
[    0.606643] hub 1-0:1.0: USB hub found
[    0.608639] hub 1-0:1.0: 2 ports detected
[    0.615104] uhci_hcd 0000:00:1d.1: found PCI INT B -> IRQ 11
[    0.665172] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.665181] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.667463] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    0.672168] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001820
[    0.722541] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    0.725223] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.729916] usb usb2: Product: UHCI Host Controller
[    0.732091] usb usb2: Manufacturer: Linux 3.8.0-27-generic uhci_hcd
[    0.738741] usb usb2: SerialNumber: 0000:00:1d.1
[    0.741615] ata1.00: ATA-5: IC25N020ATCS04-0, CA2OA72A, max UDMA/100
[    0.743847] ata1.00: 39070080 sectors, multi 16: LBA 
[    0.750637] hub 2-0:1.0: USB hub found
[    0.796953] hub 2-0:1.0: 2 ports detected
[    0.803533] ata1.00: configured for UDMA/100
[    0.810280] i8042: PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[    0.821348] ata2.00: ATAPI: SAMSUNG CD-ROM SN-124, N102, max UDMA/33
[    0.868439] isapnp: No Plug & Play device found
[    0.875131] scsi 0:0:0:0: Direct-Access     ATA      IC25N020ATCS04-0 CA2O PQ: 0 ANSI: 5
[    0.885410] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.888670] sd 0:0:0:0: [sda] 39070080 512-byte logical blocks: (20.0 GB/18.6 GiB)
[    0.894257] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.897481] sd 0:0:0:0: [sda] Write Protect is off
[    0.900128] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.900145] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.903411] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.909575] mousedev: PS/2 mouse device common for all mice
[    0.912919] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    0.917032] rtc0: alarms up to one day, 114 bytes nvram
[    0.920627] device-mapper: uevent: version 1.0.3
[    0.923704] device-mapper: ioctl: 4.23.1-ioctl (2012-12-18) initialised: dm-devel@redhat.com
[    0.929687] EISA: Probing bus 0 at eisa.0
[    0.933289] Cannot allocate resource for EISA slot 1
[    0.935969] Cannot allocate resource for EISA slot 2
[    0.942951] Cannot allocate resource for EISA slot 3
[    0.945877] EISA: Detected 0 cards.
[    0.948388] cpufreq-nforce2: No nForce2 chipset.
[    0.951366]  sda: sda1 sda2 < sda5 >
[    0.958087] ata2.00: configured for UDMA/33
[    0.961323] cpuidle: using governor ladder
[    0.964711] scsi 1:0:0:0: CD-ROM            SAMSUNG  CD-ROM SN-124    N102 PQ: 0 ANSI: 5
[    0.970839] sd 0:0:0:0: [sda] Attached SCSI disk
[    0.973345] cpuidle: using governor menu
[    0.976526] ledtrig-cpu: registered to indicate activity on CPUs
[    0.983040] EFI Variables Facility v0.08 2004-May-17
[    0.986746] ashmem: initialized
[    0.989645] sr0: scsi3-mmc drive: 24x/24x cd/rw xa/form2 cdda tray
[    0.992110] cdrom: Uniform CD-ROM driver Revision: 3.20
[    0.999268] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    0.999606] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.006470] TCP: cubic registered
[    1.009651] NET: Registered protocol family 10
[    1.012318] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input0
[    1.018917] NET: Registered protocol family 17
[    1.021468] Key type dns_resolver registered
[    1.025018] Using IPI No-Shortcut mode
[    1.027666] Loading module verification certificates
[    1.047526] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: 8f5f30c1088782cc8401b78bb07901c48bf1679c'
[    1.052174] registered taskstats version 1
[    1.064872] Key type trusted registered
[    1.076903] Key type encrypted registered
[    1.089548] rtc_cmos 00:05: setting system clock to 2013-11-11 21:35:42 UTC (1384205742)
[    1.093867] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.096301] EDD information not available.
[    1.102982] Freeing unused kernel memory: 788k freed
[    1.106627] Write protecting the kernel text: 6260k
[    1.109172] Write protecting the kernel read-only data: 2436k
[    1.167497] udevd[93]: starting version 175
[    1.173881] usb 2-1: new low-speed USB device number 2 using uhci_hcd
[    1.243239] Switching to clocksource tsc
[    1.353463] usb 2-1: New USB device found, idVendor=046d, idProduct=c517
[    1.359715] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.366186] usb 2-1: Product: USB Receiver
[    1.372603] usb 2-1: Manufacturer: Logitech
[    2.810409] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    2.816938] EXT4-fs (sda1): write access will be enabled during recovery
[    3.620243] EXT4-fs (sda1): recovery complete
[    3.628758] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   10.056290] Adding 241660k swap on /dev/sda5.  Priority:-1 extents:1 across:241660k 
[   10.325675] udevd[292]: starting version 175
[   10.431633] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   10.445989] Disabling lock debugging due to kernel taint
[   10.485199] lp: driver loaded but no devices found
[   10.815167] intel_rng: FWH not detected
[   10.863933] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   10.998565] ACPI Exception: AE_BAD_PARAMETER, Thread 3334550336 could not acquire Mutex [0x1] (20121018/utmutex-278)
[   10.998598] lpc_ich 0000:00:1f.0: I/O space for GPIO uninitialized
[   11.270240] [drm] Initialized drm 1.1.0 20060810
[   11.356178] 3c59x 0000:02:01.0: found PCI INT A -> IRQ 10
[   11.356209] 3c59x 0000:02:01.0: sharing IRQ 10 with 0000:00:1f.3
[   11.356217] 3c59x 0000:02:01.0: sharing IRQ 10 with 0000:00:1f.5
[   11.356225] 3c59x 0000:02:01.0: sharing IRQ 10 with 0000:00:1f.6
[   11.356264] 3c59x: Donald Becker and others.
[   11.356294] 0000:02:01.0: 3Com PCI 3c905C Tornado at c7f96000.
[   11.392105] usbcore: registered new interface driver usbhid
[   11.392118] usbhid: USB HID core driver
[COLOR=#ff0000][   11.501777] ------------[ cut here ]------------
[   11.501805] WARNING: at /build/buildd/linux-3.8.0/fs/sysfs/dir.c:536 sysfs_add_one+0xb6/0xf0()
[   11.501809] Hardware name: Inspiron 2600
[   11.501813] sysfs: cannot create duplicate filename '/module/video'
[   11.501817] Modules linked in: video(F+) serio_raw(F+) snd_pcm(F+) drm_kms_helper snd_page_alloc(F) 3c59x(+) pcmcia_rsrc snd_timer(F) snd(F) usbhid soundcore(F) pcmcia_core drm hid lpc_ich shpchp i2c_algo_bit lp(F) parport(F) pata_acpi
[   11.501850] Pid: 310, comm: modprobe Tainted: GF            3.8.0-27-generic #40-Ubuntu
[   11.501854] Call Trace:
[   11.501872]  [<c104a502>] warn_slowpath_common+0x72/0xa0
[   11.501880]  [<c11c1076>] ? sysfs_add_one+0xb6/0xf0
[   11.501887]  [<c11c1076>] ? sysfs_add_one+0xb6/0xf0
[   11.501895]  [<c104a5d3>] warn_slowpath_fmt+0x33/0x40
[   11.501902]  [<c11c1076>] sysfs_add_one+0xb6/0xf0
[   11.501910]  [<c11c1248>] create_dir+0x58/0xa0
[   11.501918]  [<c11c153b>] sysfs_create_dir+0x7b/0xd0
[   11.501928]  [<c12e91f3>] kobject_add_internal+0x83/0x200
[   11.501936]  [<c12f44a6>] ? kvasprintf+0x46/0x60
[   11.501943]  [<c12e95c2>] ? kobject_set_name_vargs+0x42/0x60
[   11.501950]  [<c12e9759>] kobject_init_and_add+0x39/0x60
[   11.501963]  [<c10ac89e>] load_module+0xebe/0x18f0
[   11.501974]  [<c10ad348>] sys_init_module+0x78/0xb0
[   11.501989]  [<c161afcd>] sysenter_do_call+0x12/0x28
[   11.501995] ---[ end trace 78392c460d1747f2 ]---
[   11.502003] ------------[ cut here ]------------
[   11.502010] WARNING: at /build/buildd/linux-3.8.0/lib/kobject.c:196 kobject_add_internal+0x1ea/0x200()
[   11.502013] Hardware name: Inspiron 2600
[   11.502018] kobject_add_internal failed for video with -EEXIST, don't try to register things with the same name in the same directory.
[   11.502021] Modules linked in: video(F+) serio_raw(F+) snd_pcm(F+) drm_kms_helper snd_page_alloc(F) 3c59x(+) pcmcia_rsrc snd_timer(F) snd(F) usbhid soundcore(F) pcmcia_core drm hid lpc_ich shpchp i2c_algo_bit lp(F) parport(F) pata_acpi
[   11.502050] Pid: 310, comm: modprobe Tainted: GF       W    3.8.0-27-generic #40-Ubuntu
[   11.502054] Call Trace:
[   11.502062]  [<c104a502>] warn_slowpath_common+0x72/0xa0
[   11.502070]  [<c12e935a>] ? kobject_add_internal+0x1ea/0x200
[   11.502077]  [<c12e935a>] ? kobject_add_internal+0x1ea/0x200
[   11.502084]  [<c104a5d3>] warn_slowpath_fmt+0x33/0x40
[   11.502092]  [<c12e935a>] kobject_add_internal+0x1ea/0x200
[   11.502099]  [<c12e95c2>] ? kobject_set_name_vargs+0x42/0x60
[   11.502106]  [<c12e9759>] kobject_init_and_add+0x39/0x60
[   11.502114]  [<c10ac89e>] load_module+0xebe/0x18f0
[   11.502125]  [<c10ad348>] sys_init_module+0x78/0xb0
[   11.502136]  [<c161afcd>] sysenter_do_call+0x12/0x28
[   11.502140] ---[ end trace 78392c460d1747f3 ]---[/COLOR]
[   11.655573] yenta_cardbus 0000:02:04.0: CardBus bridge found [1028:00b8]
[   11.655597] yenta_cardbus 0000:02:04.0: O2: enabling read prefetch/write burst. If you experience problems or performance issues, use the yenta_socket parameter 'o2_speedup=off'
[   11.788214] yenta_cardbus 0000:02:04.0: ISA IRQ mask 0x02b8, PCI irq 10
[   11.788227] yenta_cardbus 0000:02:04.0: Socket status: 30000007
[   11.788236] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #02 to #06
[   11.796660] yenta_cardbus 0000:02:04.0: pcmcia: parent PCI bridge window: [io  0x3000-0x3fff]
[   11.796676] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3000-0x3fff:
[   11.797938]  excluding 0x3000-0x307f 0x3400-0x34ff 0x3800-0x38ff
[   11.935737] yenta_cardbus 0000:02:04.0: pcmcia: parent PCI bridge window: [mem 0xe0200000-0xe02fffff]
[   11.935796] pcmcia_socket pcmcia_socket0: cs: memory probe 0xe0200000-0xe02fffff:
[   12.053707]  excluding 0xe0200000-0xe020ffff
[   12.053752] yenta_cardbus 0000:02:04.0: pcmcia: parent PCI bridge window: [mem 0x08000000-0x0dffffff pref]
[   12.053764] pcmcia_socket pcmcia_socket0: cs: memory probe 0x8000000-0xdffffff:
[   12.053791]  excluding 0x8000000-0xdffffff
[   12.152865] i915: Unknown symbol acpi_video_unregister (err 0)
[   12.154070] i915: Unknown symbol acpi_video_register (err 0)
[   12.199869] snd_intel8x0 0000:00:1f.5: found PCI INT B -> IRQ 10
[   12.199901] snd_intel8x0 0000:00:1f.5: sharing IRQ 10 with 0000:00:1f.3
[   12.199910] snd_intel8x0 0000:00:1f.5: sharing IRQ 10 with 0000:00:1f.6
[   12.199919] snd_intel8x0 0000:00:1f.5: sharing IRQ 10 with 0000:02:01.0
[   12.200021] snd_intel8x0 0000:00:1f.5: setting latency timer to 64
[   12.274065] microcode: CPU0 sig=0x6b1, pf=0x20, revision=0x1d
[   12.567770] psmouse serio1: synaptics: Touchpad model: 1, fw: 5.9, id: 0x254ab1, caps: 0x804713/0x0/0x0, board id: 3655, fw id: 4797542
[   12.623075] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input1
[   12.750690] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   12.828169] intel8x0_measure_ac97_clock: measured 54864 usecs (2636 samples)
[   12.828180] intel8x0: clocking to 48000
[   12.943212] type=1400 audit(1384205754.350:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=463 comm="apparmor_parser"
[   12.947056] type=1400 audit(1384205754.354:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=463 comm="apparmor_parser"
[   12.947740] type=1400 audit(1384205754.354:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=463 comm="apparmor_parser"
[   13.784018] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb2/2-1/2-1:1.0/input/input2
[   13.792426] logitech 0003:046D:C517.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.1-1/input0
[   13.796271] logitech 0003:046D:C517.0002: fixing up Logitech keyboard report descriptor
[   13.808350] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   13.855936] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af:
[   13.861264]  excluding 0x170-0x177 0x1f0-0x1f7 0x370-0x37f
[   13.862129] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff:
[   13.862499]  excluding 0x3f0-0x3f7 0x4d0-0x4d7
[   13.862867] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff:
[   13.863435]  clean.
[   13.863473] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7:
[   13.926049]  clean.
[   13.926227] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff:
[   13.926238]  excluding 0xc0000-0xc7fff 0xcc000-0xcffff 0xd8000-0xdffff 0xe4000-0xfffff
[   13.926304] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff:
[   13.926335]  clean.
[   13.926376] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff:
[   13.926407]  clean.
[   13.926446] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff:
[   13.927095]  clean.
[   13.938377] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb2/2-1/2-1:1.1/input/input3
[   13.950366] logitech 0003:046D:C517.0002: input,hiddev0,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.1-1/input1
[   13.953603] eth0:  setting half-duplex.
[   13.954251] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[  133.411606] type=1400 audit(1384205874.818:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=599 comm="apparmor_parser"
[  133.412942] type=1400 audit(1384205874.818:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=599 comm="apparmor_parser"
[  133.413672] type=1400 audit(1384205874.818:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=599 comm="apparmor_parser"
[  133.426473] type=1400 audit(1384205874.830:8): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=601 comm="apparmor_parser"


```

---

