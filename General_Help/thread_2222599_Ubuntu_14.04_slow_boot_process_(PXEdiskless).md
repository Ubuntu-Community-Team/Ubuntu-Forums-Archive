---
title: "Ubuntu 14.04 slow boot process (PXE/diskless)"
date: 2014-05-07
forum: General Help
---

### Post by matand2 on 2014-05-07
Hello,

I've been using a diskless installation of Ubuntu for our department up until Ubuntu 13.04, without any major issues so far.

However, with 14.04, something weird is happening in the boot process (which takes almost forever to finish.)

Looking at the dmesg log, it looks like the problem is related to the initialization of "urandom" and the "nonblocking pool". Any ideas why this would take several minutes when booting on the network (using NFS)?

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.13.0-24-generic (buildd@batsu) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #47-Ubuntu SMP Fri May 2 23:30:00 UTC 2014 (Ubuntu 3.13.0-24.47-generic 3.13.9)
[    0.000000] Command line: root=/dev/nfs initrd=ubuntu/14.04-desktop/initrd.img nfsroot=/netboot/ubuntu/14.04-desktop ip=dhcp rw debug=1 BOOT_IMAGE=ubuntu/14.04-desktop/vmlinuz 
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009fbff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009fc00-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000f0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000651effff] usable
[    0.000000] BIOS-e820: [mem 0x00000000651f0000-0x00000000651fffff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000fffc0000-0x00000000ffffffff] reserved
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.5 present.
[    0.000000] DMI: innotek GmbH VirtualBox/VirtualBox, BIOS VirtualBox 12/01/2006
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x651f0 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR variable ranges disabled:
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] CPU MTRRs all blank - virtualized system.
[    0.000000] found SMP MP-table at [mem 0x0009fff0-0x0009ffff] mapped at [ffff88000009fff0]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01fdd000, 0x01fddfff] PGTABLE
[    0.000000] BRK [0x01fde000, 0x01fdefff] PGTABLE
[    0.000000] BRK [0x01fdf000, 0x01fdffff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x64200000-0x643fffff]
[    0.000000]  [mem 0x64200000-0x643fffff] page 2M
[    0.000000] BRK [0x01fe0000, 0x01fe0fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x64000000-0x641fffff]
[    0.000000]  [mem 0x64000000-0x641fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x60000000-0x63ffffff]
[    0.000000]  [mem 0x60000000-0x63ffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0x5fffffff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x5fffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x64400000-0x651effff]
[    0.000000]  [mem 0x64400000-0x64ffffff] page 2M
[    0.000000]  [mem 0x65000000-0x651effff] page 4k
[    0.000000] BRK [0x01fe1000, 0x01fe1fff] PGTABLE
[    0.000000] RAMDISK: [mem 0x64530000-0x651cefff]
[    0.000000] ACPI: RSDP 00000000000e0000 000024 (v02 VBOX  )
[    0.000000] ACPI: XSDT 00000000651f0030 00003C (v01 VBOX   VBOXXSDT 00000001 ASL  00000061)
[    0.000000] ACPI: FACP 00000000651f00f0 0000F4 (v04 VBOX   VBOXFACP 00000001 ASL  00000061)
[    0.000000] ACPI: DSDT 00000000651f0470 001B96 (v01 VBOX   VBOXBIOS 00000002 INTL 20100528)
[    0.000000] ACPI: FACS 00000000651f0200 000040
[    0.000000] ACPI: APIC 00000000651f0240 000054 (v02 VBOX   VBOXAPIC 00000001 ASL  00000061)
[    0.000000] ACPI: SSDT 00000000651f02a0 0001CC (v01 VBOX   VBOXCPUT 00000002 INTL 20100528)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x00000000651effff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x651effff]
[    0.000000]   NODE_DATA [mem 0x651eb000-0x651effff]
[    0.000000]  [ffffea0000000000-ffffea00019fffff] PMD -> [ffff880062200000-ffff880063bfffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   empty
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009efff]
[    0.000000]   node   0: [mem 0x00100000-0x651effff]
[    0.000000] On node 0 totalpages: 414094
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3998 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 6408 pages used for memmap
[    0.000000]   DMA32 zone: 410096 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] smpboot: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000effff]
[    0.000000] PM: Registered nosave memory: [mem 0x000f0000-0x000fffff]
[    0.000000] e820: [mem 0x65200000-0xfffbffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 29 pages/cpu @ffff880064200000 s86336 r8192 d24256 u2097152
[    0.000000] pcpu-alloc: s86336 r8192 d24256 u2097152 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 407601
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: root=/dev/nfs initrd=ubuntu/14.04-desktop/initrd.img nfsroot=/netboot/ubuntu/14.04-desktop ip=dhcp rw debug=1 BOOT_IMAGE=ubuntu/14.04-desktop/vmlinuz 
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 1600096K/1656376K available (7338K kernel code, 1138K rwdata, 3388K rodata, 1332K init, 1440K bss, 56280K reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=1.
[    0.000000]     Offload RCU callbacks from all CPUs
[    0.000000]     Offload RCU callbacks from CPUs: 0.
[    0.000000] NR_IRQS:16640 nr_irqs:256 16
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 6815744 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] tsc: Fast TSC calibration failed
[    0.000000] tsc: Unable to calibrate against PIT
[    0.000000] tsc: using PMTIMER reference calibration
[    0.000000] tsc: Detected 2633.187 MHz processor
[    0.016002] Calibrating delay loop (skipped), value calculated using timer frequency.. 5266.37 BogoMIPS (lpj=10532748)
[    0.020006] pid_max: default: 32768 minimum: 301
[    0.020572] Security Framework initialized
[    0.021099] AppArmor: AppArmor initialized
[    0.021603] Yama: becoming mindful.
[    0.024012] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.024974] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.025732] Mount-cache hash table entries: 4096 (order: 3, 32768 bytes)
[    0.026723] Mountpoint-cache hash table entries: 4096 (order: 3, 32768 bytes)
[    0.028161] Initializing cgroup subsys memory
[    0.028678] Initializing cgroup subsys devices
[    0.029209] Initializing cgroup subsys freezer
[    0.029729] Initializing cgroup subsys blkio
[    0.030233] Initializing cgroup subsys perf_event
[    0.030755] Initializing cgroup subsys hugetlb
[    0.031382] mce: CPU supports 0 MCE banks
[    0.032032] Last level iTLB entries: 4KB 512, 2MB 7, 4MB 7
[    0.032032] Last level dTLB entries: 4KB 512, 2MB 32, 4MB 32
[    0.032032] tlb_flushall_shift: 6
[    0.058949] Freeing SMP alternatives memory: 32K (ffffffff81e6b000 - ffffffff81e73000)
[    0.069236] ACPI: Core revision 20131115
[    0.070407] ACPI: All ACPI Tables successfully acquired
[    0.071177] ftrace: allocating 28408 entries in 111 pages
[    0.084347] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.126674] smpboot: CPU0: Intel(R) Core(TM) i5 CPU         750  @ 2.67GHz (fam: 06, model: 1e, stepping: 05)
[    0.139672] Performance Events: unsupported p6 CPU model 30 no PMU driver, software events only.
[    0.141946] x86: Booted up 1 node, 1 CPUs
[    0.142449] smpboot: Total of 1 processors activated (5266.37 BogoMIPS)
[    0.143468] NMI watchdog: disabled (cpu0): hardware events not enabled
[    0.144076] devtmpfs: initialized
[    0.146511] EVM: security.selinux
[    0.146994] EVM: security.SMACK64
[    0.147464] EVM: security.ima
[    0.148002] EVM: security.capability
[    0.149272] pinctrl core: initialized pinctrl subsystem
[    0.149876] regulator-dummy: no parameters
[    0.150461] RTC time: 12:11:19, date: 05/07/14
[    0.151013] NET: Registered protocol family 16
[    0.151652] cpuidle: using governor ladder
[    0.152007] cpuidle: using governor menu
[    0.152543] ACPI: bus type PCI registered
[    0.153043] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.153743] PCI: Using configuration type 1 for base access
[    0.155057] bio: create slab <bio-0> at 0
[    0.155707] ACPI: Added _OSI(Module Device)
[    0.156007] ACPI: Added _OSI(Processor Device)
[    0.156529] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.157072] ACPI: Added _OSI(Processor Aggregator Device)
[    0.158204] ACPI: Executed 1 blocks of module-level executable AML code
[    0.161319] ACPI: Interpreter enabled
[    0.161812] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20131115/hwxface-580)
[    0.162959] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)
[    0.164004] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S3_] (20131115/hwxface-580)
[    0.165782] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S4_] (20131115/hwxface-580)
[    0.166938] ACPI: (supports S0 S5)
[    0.167421] ACPI: Using IOAPIC for interrupt routing
[    0.168194] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.169265] ACPI: No dock devices found.
[    0.172472] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.173161] acpi PNP0A03:00: _OSC: OS supports [ASPM ClockPM Segments MSI]
[    0.174035] acpi PNP0A03:00: _OSC failed (AE_NOT_FOUND); disabling ASPM
[    0.174522] acpi PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.174595] acpi PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.175083] acpi PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.176005] acpi PNP0A03:00: host bridge window [mem 0x65200000-0xffdfffff] (ignored)
[    0.177044] PCI: root bus 00: using default resources
[    0.177653] acpi PNP0A03:00: fail to add MMCONFIG information, can't access extended PCI configuration space under this bridge.
[    0.178934] PCI host bridge to bus 0000:00
[    0.180004] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.180571] pci_bus 0000:00: root bus resource [io  0x0000-0xffff]
[    0.181162] pci_bus 0000:00: root bus resource [mem 0x00000000-0xfffffffff]
[    0.181840] pci 0000:00:00.0: [8086:1237] type 00 class 0x060000
[    0.184135] pci 0000:00:01.0: [8086:7000] type 00 class 0x060100
[    0.185506] pci 0000:00:01.1: [8086:7111] type 00 class 0x01018a
[    0.186545] pci 0000:00:01.1: reg 0x20: [io  0xd000-0xd00f]
[    0.187542] pci 0000:00:02.0: [80ee:beef] type 00 class 0x030000
[    0.189475] pci 0000:00:02.0: reg 0x10: [mem 0xe0000000-0xe0ffffff pref]
[    0.195725] pci 0000:00:03.0: [1022:2000] type 00 class 0x020000
[    0.197028] pci 0000:00:03.0: reg 0x10: [io  0xd020-0xd03f]
[    0.198643] pci 0000:00:03.0: reg 0x14: [mem 0xf0000000-0xf0000fff]
[    0.202583] pci 0000:00:04.0: [80ee:cafe] type 00 class 0x088000
[    0.203799] pci 0000:00:04.0: reg 0x10: [io  0xd040-0xd05f]
[    0.204593] pci 0000:00:04.0: reg 0x14: [mem 0xf0400000-0xf07fffff]
[    0.205814] pci 0000:00:04.0: reg 0x18: [mem 0xf0800000-0xf0803fff pref]
[    0.209572] pci 0000:00:06.0: [106b:003f] type 00 class 0x0c0310
[    0.210790] pci 0000:00:06.0: reg 0x10: [mem 0xf0804000-0xf0804fff]
[    0.215181] pci 0000:00:07.0: [8086:7113] type 00 class 0x068000
[    0.217128] pci 0000:00:0b.0: [8086:265c] type 00 class 0x0c0320
[    0.218707] pci 0000:00:0b.0: reg 0x10: [mem 0xf0805000-0xf0805fff]
[    0.222791] pci 0000:00:0d.0: [8086:2829] type 00 class 0x010601
[    0.224149] pci 0000:00:0d.0: reg 0x10: [io  0xd060-0xd067]
[    0.225892] pci 0000:00:0d.0: reg 0x18: [io  0xd070-0xd077]
[    0.228685] pci 0000:00:0d.0: reg 0x20: [io  0xd080-0xd08f]
[    0.229863] pci 0000:00:0d.0: reg 0x24: [mem 0xf0806000-0xf0807fff]
[    0.232582] ACPI: PCI Interrupt Link [LNKA] (IRQs 5 9 10 *11)
[    0.233915] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 9 10 *11)
[    0.235181] ACPI: PCI Interrupt Link [LNKC] (IRQs 5 9 *10 11)
[    0.236101] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 *9 10 11)
[    0.237741] ACPI: Enabled 1 GPEs in block 00 to 07
[    0.238471] ACPI: \_SB_.PCI0: notify handler is installed
[    0.239035] Found 1 acpi root devices
[    0.240044] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.240978] vgaarb: loaded
[    0.241424] vgaarb: bridge control possible 0000:00:02.0
[    0.242155] SCSI subsystem initialized
[    0.242708] libata version 3.00 loaded.
[    0.243224] ACPI: bus type USB registered
[    0.243760] usbcore: registered new interface driver usbfs
[    0.244010] usbcore: registered new interface driver hub
[    0.244659] usbcore: registered new device driver usb
[    0.245294] PCI: Using ACPI for IRQ routing
[    0.245816] PCI: pci_cache_line_size set to 64 bytes
[    0.246571] e820: reserve RAM buffer [mem 0x0009fc00-0x0009ffff]
[    0.247147] e820: reserve RAM buffer [mem 0x651f0000-0x67ffffff]
[    0.248108] NetLabel: Initializing
[    0.248591] NetLabel:  domain hash size = 128
[    0.249112] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.249676] NetLabel:  unlabeled traffic allowed by default
[    0.250379] Switched to clocksource refined-jiffies
[    0.259034] AppArmor: AppArmor Filesystem Enabled
[    0.259600] pnp: PnP ACPI init
[    0.260016] ACPI: bus type PNP registered
[    0.260607] pnp 00:00: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.261228] pnp 00:01: [dma 4]
[    0.261709] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.262398] pnp 00:02: Plug and Play ACPI device, IDs PNP0f03 (active)
[    0.263047] pnp 00:03: Plug and Play ACPI device, IDs PNP0400 (active)
[    0.264411] pnp: PnP ACPI: found 4 devices
[    0.265018] ACPI: bus type PNP unregistered
[    0.272906] Switched to clocksource acpi_pm
[    0.273432] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
[    0.274081] pci_bus 0000:00: resource 5 [mem 0x00000000-0xfffffffff]
[    0.274697] NET: Registered protocol family 2
[    0.275353] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.276001] TCP bind hash table entries: 16384 (order: 6, 262144 bytes)
[    0.276528] TCP: Hash tables configured (established 16384 bind 16384)
[    0.277168] TCP: reno registered
[    0.277638] UDP hash table entries: 1024 (order: 3, 32768 bytes)
[    0.278231] UDP-Lite hash table entries: 1024 (order: 3, 32768 bytes)
[    0.278878] NET: Registered protocol family 1
[    0.279422] pci 0000:00:00.0: Limiting direct PCI/PCI transfers
[    0.280097] pci 0000:00:01.0: Activating ISA DMA hang workarounds
[    0.280715] pci 0000:00:02.0: Boot video device
[    0.283252] PCI: CLS 0 bytes, default 64
[    0.283837] Trying to unpack rootfs image as initramfs...
[    0.504412] Freeing initrd memory: 12924K (ffff880064530000 - ffff8800651cf000)
[    0.505453] platform rtc_cmos: registered platform RTC device (no PNP device found)
[    0.506926] microcode: CPU0 sig=0x106e5, pf=0x4, revision=0x616
[    0.507553] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.508555] Scanning for low memory corruption every 60 seconds
[    0.509374] Initialise system trusted keyring
[    0.509963] audit: initializing netlink socket (disabled)
[    0.510531] type=2000 audit(1399464679.507:1): initialized
[    0.534547] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.536054] VFS: Disk quotas dquot_6.5.2
[    0.536589] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.537523] fuse init (API version 7.22)
[    0.538074] msgmni has been set to 3150
[    0.538626] Key type big_key registered
[    0.539369] Key type asymmetric registered
[    0.539952] Asymmetric key parser 'x509' registered
[    0.540622] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.541550] io scheduler noop registered
[    0.542055] io scheduler deadline registered (default)
[    0.542611] io scheduler cfq registered
[    0.543179] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.543839] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.544551] ipmi message handler version 39.2
[    0.545219] ACPI: AC Adapter [AC] (on-line)
[    0.545851] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.546742] ACPI: Power Button [PWRF]
[    0.547283] input: Sleep Button as /devices/LNXSYSTM:00/LNXSLPBN:00/input/input1
[    0.548570] ACPI: Sleep Button [SLPF]
[    0.549186] GHES: HEST is not enabled!
[    0.549787] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.552645] Linux agpgart interface v0.103
[    0.554112] brd: module loaded
[    0.555061] loop: module loaded
[    0.555600] ata_piix 0000:00:01.1: version 2.13
[    0.556615] scsi0 : ata_piix
[    0.557156] scsi1 : ata_piix
[    0.557649] ata1: PATA max UDMA/33 cmd 0x1f0 ctl 0x3f6 bmdma 0xd000 irq 14
[    0.558260] ata2: PATA max UDMA/33 cmd 0x170 ctl 0x376 bmdma 0xd008 irq 15
[    0.559396] libphy: Fixed MDIO Bus: probed
[    0.559968] tun: Universal TUN/TAP device driver, 1.6
[    0.560550] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.561221] PPP generic driver version 2.4.2
[    0.561755] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.562346] ehci-pci: EHCI PCI platform driver
[    0.563462] ehci-pci 0000:00:0b.0: EHCI Host Controller
[    0.565214] ehci-pci 0000:00:0b.0: new USB bus registered, assigned bus number 1
[    0.566342] ehci-pci 0000:00:0b.0: irq 19, io mem 0xf0805000
[    0.577526] ehci-pci 0000:00:0b.0: USB 2.0 started, EHCI 1.00
[    0.578219] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.578881] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.579841] usb usb1: Product: EHCI Host Controller
[    0.580483] usb usb1: Manufacturer: Linux 3.13.0-24-generic ehci_hcd
[    0.581077] usb usb1: SerialNumber: 0000:00:0b.0
[    0.581713] hub 1-0:1.0: USB hub found
[    0.582221] hub 1-0:1.0: 8 ports detected
[    0.582948] ehci-platform: EHCI generic platform driver
[    0.583578] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.584288] ohci-pci: OHCI PCI platform driver
[    0.585297] ohci-pci 0000:00:06.0: OHCI PCI host controller
[    0.585865] ohci-pci 0000:00:06.0: new USB bus registered, assigned bus number 2
[    0.586815] ohci-pci 0000:00:06.0: irq 22, io mem 0xf0804000
[    0.641300] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    0.641915] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.642812] usb usb2: Product: OHCI PCI host controller
[    0.644425] usb usb2: Manufacturer: Linux 3.13.0-24-generic ohci_hcd
[    0.645988] usb usb2: SerialNumber: 0000:00:06.0
[    0.647630] hub 2-0:1.0: USB hub found
[    0.649068] hub 2-0:1.0: 8 ports detected
[    0.651040] ohci-platform: OHCI generic platform driver
[    0.652613] uhci_hcd: USB Universal Host Controller Interface driver
[    0.654362] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    0.661775] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.663179] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.665144] mousedev: PS/2 mouse device common for all mice
[    0.667995] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    0.671286] rtc_cmos rtc_cmos: rtc core: registered rtc_cmos as rtc0
[    0.673069] rtc_cmos rtc_cmos: alarms up to one day, 114 bytes nvram
[    0.673819] device-mapper: uevent: version 1.0.3
[    0.674832] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    0.675786] ledtrig-cpu: registered to indicate activity on CPUs
[    0.676483] TCP: cubic registered
[    0.677030] NET: Registered protocol family 10
[    0.677707] NET: Registered protocol family 17
[    0.678232] Key type dns_resolver registered
[    0.678879] Loading compiled-in X.509 certificates
[    0.680762] Loaded X.509 cert 'Magrathea: Glacier signing key: 69b0d0a79b85d90621706e8d06604d730b359fc0'
[    0.681803] registered taskstats version 1
[    0.684382] Key type trusted registered
[    0.686511] Key type encrypted registered
[    0.688743] AppArmor: AppArmor sha1 policy hashing enabled
[    0.689332] IMA: No TPM chip found, activating TPM-bypass!
[    0.690127] regulator-dummy: disabling
[    0.690667]   Magic number: 14:406:177
[    0.691276] rtc_cmos rtc_cmos: setting system clock to 2014-05-07 12:11:20 UTC (1399464680)
[    0.692400] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.692988] EDD information not available.
[    0.720523] ata2.00: ATAPI: VBOX CD-ROM, 1.0, max UDMA/133
[    0.721531] ata2.00: configured for UDMA/33
[    0.722821] scsi 1:0:0:0: CD-ROM            VBOX     CD-ROM           1.0  PQ: 0 ANSI: 5
[    0.726062] sr0: scsi3-mmc drive: 32x/32x xa/form2 tray
[    0.726617] cdrom: Uniform CD-ROM driver Revision: 3.20
[    0.727224] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    0.728169] sr 1:0:0:0: Attached scsi generic sg0 type 5
[    1.057128] usb 2-1: new full-speed USB device number 2 using ohci-pci
[    1.315728] usb 2-1: New USB device found, idVendor=80ee, idProduct=0021
[    1.317564] usb 2-1: New USB device strings: Mfr=1, Product=3, SerialNumber=0
[    1.319214] usb 2-1: Product: USB Tablet
[    1.320602] usb 2-1: Manufacturer: VirtualBox
[    1.504308] tsc: Refined TSC clocksource calibration: 2633.384 MHz
[    2.504285] Switched to clocksource tsc
[   12.740205] PM: Hibernation image not present or could not be loaded.
[   12.744443] Freeing unused kernel memory: 1332K (ffffffff81d1e000 - ffffffff81e6b000)
[   12.746917] Write protecting the kernel read-only data: 12288k
[   12.753331] Freeing unused kernel memory: 844K (ffff88000172d000 - ffff880001800000)
[   12.761115] Freeing unused kernel memory: 708K (ffff880001b4f000 - ffff880001c00000)
[   12.805421] systemd-udevd[94]: starting version 204
[   12.835119] pcnet32: pcnet32.c:v1.35 21.Apr.2008 [EMAIL="tsbogend@alpha.franken.de"]tsbogend@alpha.franken.de[/EMAIL]
[   12.835739] pcnet32: PCnet/FAST III 79C973 at 0xd020, 08:00:27:eb:e5:7b assigned IRQ 19
[   12.835768] pcnet32: Found PHY 0022:561b at address 0
[   12.840181] pcnet32: eth0: registered as PCnet/FAST III 79C973
[   12.840208] pcnet32: 1 cards_found
[   12.854750] hidraw: raw HID events driver (C) Jiri Kosina
[   12.884436] usbcore: registered new interface driver usbhid
[   12.885035] usbhid: USB HID core driver
[   12.970946] FS-Cache: Loaded
[   12.974171] input: VirtualBox USB Tablet as /devices/pci0000:00/0000:00:06.0/usb2/2-1/2-1:1.0/input/input4
[   12.977221] hid-generic 0003:80EE:0021.0001: input,hidraw0: USB HID v1.10 Mouse [VirtualBox USB Tablet] on usb-0000:00:06.0-1/input0
[   12.983148] RPC: Registered named UNIX socket transport module.
[   12.983732] RPC: Registered udp transport module.
[   12.984294] RPC: Registered tcp transport module.
[   12.984871] RPC: Registered tcp NFSv4.1 backchannel transport module.
[   12.996479] FS-Cache: Netfs 'nfs' registered for caching
[   13.013388] pcnet32 0000:00:03.0 eth0: link up, 100Mbps, full-duplex
[   13.863447] random: init urandom read with 44 bits of entropy available
[   75.338950] random: nonblocking pool is initialized
[  115.543026] init: plymouth-upstart-bridge main process (139) terminated with status 1
[  115.551323] init: plymouth-upstart-bridge main process ended, respawning
[  155.826797] init: plymouth-upstart-bridge main process (149) terminated with status 1
[  155.827871] init: plymouth-upstart-bridge main process ended, respawning
[  155.863568] init: plymouth-upstart-bridge main process (152) terminated with status 1
[  155.865184] init: plymouth-upstart-bridge main process ended, respawning
[  155.884975] init: plymouth-upstart-bridge main process (156) terminated with status 1
[  155.886498] init: plymouth-upstart-bridge main process ended, respawning
[  158.202482] systemd-udevd[320]: starting version 204
[  158.528424] Installing knfsd (copyright (C) 1996 [EMAIL="okir@monad.swb.de"]okir@monad.swb.de[/EMAIL]).
[  159.029684] lp: driver loaded but no devices found
[  159.407313] ppdev: user-space parallel port driver
[  159.509568] parport_pc 00:03: reported by Plug and Play ACPI
[  159.558934] vboxguest: module verification failed: signature and/or  required key missing - tainting kernel
[  159.570225] piix4_smbus 0000:00:07.0: SMBus base address uninitialized - upgrade BIOS or use force_addr=0xaddr
[  159.585916] input: Unspecified device as /devices/pci0000:00/0000:00:04.0/input/input5
[  159.586129] vboxguest: major 0, IRQ 20, I/O port d040, MMIO at 00000000f0400000 (size 0x400000)
[  159.586131] vboxguest: Successfully loaded version 4.3.10 (interface 0x00010004)
[  159.728905] ahci 0000:00:0d.0: version 3.0
[  159.729562] ahci 0000:00:0d.0: SSS flag set, parallel bus scan disabled
[  159.729727] ahci 0000:00:0d.0: AHCI 0001.0100 32 slots 1 ports 3 Gbps 0x1 impl SATA mode
[  159.729730] ahci 0000:00:0d.0: flags: 64bit ncq stag only ccc 
[  159.750670] scsi2 : ahci
[  159.758609] ata3: SATA max UDMA/133 abar m8192@0xf0806000 port 0xf0806100 irq 21
[  159.857743] [drm] Initialized drm 1.1.0 20060810
[  159.880912] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[  159.880915] [drm] No driver support for vblank timestamp query.
[  159.880917] [drm] Initialized vboxvideo 1.0.0 20090303 for 0000:00:02.0 on minor 0
[  160.035867] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input6
[  160.065371] type=1400 audit(1399464839.869:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=411 comm="apparmor_parser"
[  160.065377] type=1400 audit(1399464839.869:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=411 comm="apparmor_parser"
[  160.065381] type=1400 audit(1399464839.869:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=411 comm="apparmor_parser"
[  160.065772] type=1400 audit(1399464839.869:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=411 comm="apparmor_parser"
[  160.065777] type=1400 audit(1399464839.869:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=411 comm="apparmor_parser"
[  160.065971] type=1400 audit(1399464839.869:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=411 comm="apparmor_parser"
[  160.081335] ata3: SATA link down (SStatus 0 SControl 300)
[  160.318287] Bluetooth: Core ver 2.17
[  160.336052] NET: Registered protocol family 31
[  160.336056] Bluetooth: HCI device and connection manager initialized
[  160.336065] Bluetooth: HCI socket layer initialized
[  160.336067] Bluetooth: L2CAP socket layer initialized
[  160.336073] Bluetooth: SCO socket layer initialized
[  160.438495] Bluetooth: RFCOMM TTY layer initialized
[  160.438505] Bluetooth: RFCOMM socket layer initialized
[  160.438509] Bluetooth: RFCOMM ver 1.11
[  160.509303] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  160.509306] Bluetooth: BNEP filters: protocol multicast
[  160.509314] Bluetooth: BNEP socket layer initialized
[  160.541800] type=1400 audit(1399464840.345:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=470 comm="apparmor_parser"
[  160.541807] type=1400 audit(1399464840.345:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=470 comm="apparmor_parser"
[  160.542204] type=1400 audit(1399464840.345:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=470 comm="apparmor_parser"
[  162.034013] init: cups main process (489) killed by HUP signal
[  162.034024] init: cups main process ended, respawning
[  162.456769] init: failsafe main process (496) killed by TERM signal
[  162.782571] init: Failed to obtain startpar-bridge instance: Unknown parameter: INSTANCE
[  163.627791] init: udev-fallback-graphics main process (645) terminated with status 1
[  163.974568] type=1400 audit(1399464843.777:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=704 comm="apparmor_parser"
[  165.873099] init: alsa-restore main process (871) terminated with status 19

```

---

### Post by Thomas_Robert on 2014-05-07
I might be due to you network issue. is everything fine with the Network Cables.

---

### Post by Danger_Monkey on 2014-05-07
I would check to see if there is a random and urandom special file.  

```

ls /dev/random
ls /dev/urandom

```

If they aren there, you can create them using these commands:

```

mknod -m 644 /dev/random c 1 8
mknod -m 644 /dev/urandom c 1 9
chown root:root /dev/random /dev/urandom

```

It is trying to create entropy, and it might be getting stuck there.

---

### Post by matand2 on 2014-05-13
> **Danger_Monkey said:**
> I would check to see if there is a random and urandom special file.  

```

ls /dev/random
ls /dev/urandom

```

Both of them already existed.

> 
If they aren there, you can create them using these commands:

```

mknod -m 644 /dev/random c 1 8
mknod -m 644 /dev/urandom c 1 9
chown root:root /dev/random /dev/urandom

```

It is trying to create entropy, and it might be getting stuck there.
I recreated the files, but the problem still remains.

---

