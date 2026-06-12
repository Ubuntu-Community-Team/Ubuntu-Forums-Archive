---
title: "Slow Boot and Blackscreen since Chrome (attempted) download"
date: 2015-02-19
forum: General Help
---

### Post by teknohippie on 2015-02-19
So Ive been searching for solutions to a slow boot sequence. My screen goes black right before the "registered by..." screen which is fine, as it comes back up relatively quickly. Once I enter my login information however, it takes a considerable amount of time to bring up unity, the toolbar, etc. even though I can see the toolbar is loaded behind the login screen. I have a .txt file from dmesg and also my bootchart .png both of which I will be attaching. Secondy, I noticed that this began when I attempted (and apparently failed) to install Google Chrome. I have since used sudo autoremove google-chrome-stable and sudo purge google-chrome-stable but there seems to be some residual problems. For instance, when I attempted to go to the google chrome webpage to re-download the install package it would send me to blackscreen. Note that this is all while using Firefox. I have since reconfigured my Firefox browser to delete cookies upon closing, and have not yet attempted to revisit the Chrome download page. I assume that deleting the cookies would help and I will attempt returning to the download page after I post this. So to sum it up, here are my two questions:
1. Does anyone see anything in my dmesg or bootchart that is easily fixable to restore my boot time?
2. Has anyone run into similar problems with downloading Chrome.
  2a. Have I sufficiently removed all of Chrome's files and would it be worthwhile to reattempt an installation?

dmesg.txt```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.13.0-45-generic (buildd@phianna) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #74-Ubuntu SMP Tue Jan 13 19:36:28 UTC 2015 (Ubuntu 3.13.0-45.74-generic 3.13.11-ckt13)
[    0.000000] Command line: BOOT_IMAGE=/vmlinuz-3.13.0-45-generic root=/dev/mapper/ubuntu--vg-root ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009f7ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009f800-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000dc000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000bf6cffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bf6d0000-0x00000000bf6e2fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bf6e3000-0x00000000bfffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec0ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed003ff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed14000-0x00000000fed19fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed8ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000013fffffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.4 present.
[    0.000000] DMI: Dell Inc. Vostro1510/0M277C, BIOS A12 09/10/2008
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x140000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0C0000000 mask FC0000000 uncachable
[    0.000000]   1 base 000000000 mask F00000000 write-back
[    0.000000]   2 base 100000000 mask FC0000000 write-back
[    0.000000]   3 base 0BF700000 mask FFFF00000 uncachable
[    0.000000]   4 base 0BF800000 mask FFF800000 uncachable
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 3GB, range: 1GB, type UC
[    0.000000] reg 1, base: 0GB, range: 4GB, type WB
[    0.000000] reg 2, base: 4GB, range: 1GB, type WB
[    0.000000] reg 3, base: 3063MB, range: 1MB, type UC
[    0.000000] reg 4, base: 3064MB, range: 8MB, type UC
[    0.000000] total RAM covered: 4087M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 16M     num_reg: 5      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3063MB, range: 1MB, type UC
[    0.000000] reg 3, base: 3064MB, range: 8MB, type UC
[    0.000000] reg 4, base: 4GB, range: 1GB, type WB
[    0.000000] e820: update [mem 0xbf700000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xbf6d0 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000f76f0-0x000f76ff] mapped at [ffff8800000f76f0]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01fe1000, 0x01fe1fff] PGTABLE
[    0.000000] BRK [0x01fe2000, 0x01fe2fff] PGTABLE
[    0.000000] BRK [0x01fe3000, 0x01fe3fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x13fe00000-0x13fffffff]
[    0.000000]  [mem 0x13fe00000-0x13fffffff] page 2M
[    0.000000] BRK [0x01fe4000, 0x01fe4fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x13c000000-0x13fdfffff]
[    0.000000]  [mem 0x13c000000-0x13fdfffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x100000000-0x13bffffff]
[    0.000000]  [mem 0x100000000-0x13bffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0xbf6cffff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0xbf5fffff] page 2M
[    0.000000]  [mem 0xbf600000-0xbf6cffff] page 4k
[    0.000000] RAMDISK: [mem 0x359c6000-0x36cdafff]
[    0.000000] ACPI: RSDP 00000000000f7670 000024 (v02 DELL  )
[    0.000000] ACPI: XSDT 00000000bf6d6873 000094 (v01 DELL    M08     06040000  LTP 00000000)
[    0.000000] ACPI: FACP 00000000bf6decd6 0000F4 (v03 TOSCPL CRESTLNE 06040000 ALAN 00000001)
[    0.000000] ACPI: DSDT 00000000bf6d7db1 006EB1 (v02 TOSCPL CRESTLNE 06040000 INTL 20060608)
[    0.000000] ACPI: FACS 00000000bf6e2fc0 000040
[    0.000000] ACPI: APIC 00000000bf6dedca 000068 (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: HPET 00000000bf6dee32 000038 (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: MCFG 00000000bf6dee6a 00003C (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: TCPA 00000000bf6deea6 000032 (v01 Intel  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: TMOR 00000000bf6deed8 000026 (v01 PTLTD           06040000 PTL  00000003)
[    0.000000] ACPI: OSFR 00000000bf6deefe 000072 (v01 TOSHIB A+2nd ID 06040000 TASM 04010000)
[    0.000000] ACPI: APIC 00000000bf6def70 000068 (v01 PTLTD  ? APIC   06040000  LTP 00000000)
[    0.000000] ACPI: BOOT 00000000bf6defd8 000028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: SSDT 00000000bf6d7b04 0002AD (v01 SataRe SataAhci 00001000 INTL 20061109)
[    0.000000] ACPI: SSDT 00000000bf6d7a61 0000A3 (v01 BrtRef  DD01BRT 00001000 INTL 20061109)
[    0.000000] ACPI: SSDT 00000000bf6d6e93 00025F (v01  PmRef  Cpu0Tst 00003000 INTL 20061109)
[    0.000000] ACPI: SSDT 00000000bf6d6ded 0000A6 (v01  PmRef  Cpu1Tst 00003000 INTL 20061109)
[    0.000000] ACPI: SSDT 00000000bf6d6907 0004E6 (v01  PmRef    CpuPm 00003000 INTL 20061109)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify linux-acpi@vger.kernel.org
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000013fffffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x13fffffff]
[    0.000000]   NODE_DATA [mem 0x13fff8000-0x13fffcfff]
[    0.000000]  [ffffea0000000000-ffffea0004ffffff] PMD -> [ffff88013b600000-ffff88013f5fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x13fffffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009efff]
[    0.000000]   node   0: [mem 0x00100000-0xbf6cffff]
[    0.000000]   node   0: [mem 0x100000000-0x13fffffff]
[    0.000000] On node 0 totalpages: 1046126
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3998 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 12188 pages used for memmap
[    0.000000]   DMA32 zone: 779984 pages, LIFO batch:31
[    0.000000]   Normal zone: 4096 pages used for memmap
[    0.000000]   Normal zone: 262144 pages, LIFO batch:31
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
[    0.000000] smpboot: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dbfff]
[    0.000000] PM: Registered nosave memory: [mem 0x000dc000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xbf6d0000-0xbf6e2fff]
[    0.000000] PM: Registered nosave memory: [mem 0xbf6e3000-0xbfffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xc0000000-0xdfffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec0ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec10000-0xfecfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed00000-0xfed13fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed14000-0xfed19fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1a000-0xfed1bfff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed8ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed90000-0xfedfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xfeffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xff000000-0xffffffff]
[    0.000000] e820: [mem 0xc0000000-0xdfffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88013fc00000 s82368 r8192 d24128 u1048576
[    0.000000] pcpu-alloc: s82368 r8192 d24128 u1048576 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1029757
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-3.13.0-45-generic root=/dev/mapper/ubuntu--vg-root ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 4016500K/4184504K available (7383K kernel code, 1145K rwdata, 3408K rodata, 1336K init, 1444K bss, 168004K reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=2.
[    0.000000]     Offload RCU callbacks from all CPUs
[    0.000000]     Offload RCU callbacks from CPUs: 0-1.
[    0.000000] NR_IRQS:16640 nr_irqs:512 16
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 16777216 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 1795.447 MHz processor
[    0.004004] Calibrating delay loop (skipped), value calculated using timer frequency.. 3590.89 BogoMIPS (lpj=7181788)
[    0.004009] pid_max: default: 32768 minimum: 301
[    0.004054] Security Framework initialized
[    0.004081] AppArmor: AppArmor initialized
[    0.004082] Yama: becoming mindful.
[    0.004577] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.009003] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.010101] Mount-cache hash table entries: 8192 (order: 4, 65536 bytes)
[    0.010114] Mountpoint-cache hash table entries: 8192 (order: 4, 65536 bytes)
[    0.010482] Initializing cgroup subsys memory
[    0.010495] Initializing cgroup subsys devices
[    0.010498] Initializing cgroup subsys freezer
[    0.010501] Initializing cgroup subsys blkio
[    0.010503] Initializing cgroup subsys perf_event
[    0.010506] Initializing cgroup subsys hugetlb
[    0.010535] CPU: Physical Processor ID: 0
[    0.010537] CPU: Processor Core ID: 0
[    0.010540] mce: CPU supports 6 MCE banks
[    0.010548] CPU0: Thermal monitoring handled by SMI
[    0.010558] Last level iTLB entries: 4KB 128, 2MB 4, 4MB 4
[    0.010558] Last level dTLB entries: 4KB 256, 2MB 0, 4MB 32
[    0.010558] tlb_flushall_shift: -1
[    0.010680] Freeing SMP alternatives memory: 32K (ffffffff81e6e000 - ffffffff81e76000)
[    0.012497] ACPI: Core revision 20131115
[    0.017309] ACPI: All ACPI Tables successfully acquired
[    0.020013] ftrace: allocating 28554 entries in 112 pages
[    0.032565] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.075806] smpboot: CPU0: Intel(R) Core(TM)2 Duo CPU     T5670  @ 1.80GHz (fam: 06, model: 0f, stepping: 0d)
[    0.076000] Performance Events: PEBS fmt0+, 4-deep LBR, Core2 events, Intel PMU driver.
[    0.076000] perf_event_intel: PEBS disabled due to CPU errata
[    0.076000] ... version:                2
[    0.076000] ... bit width:              40
[    0.076000] ... generic registers:      2
[    0.076000] ... value mask:             000000ffffffffff
[    0.076000] ... max period:             000000007fffffff
[    0.076000] ... fixed-purpose events:   3
[    0.076000] ... event mask:             0000000700000003
[    0.076000] x86: Booting SMP configuration:
[    0.076000] CPU1: Thermal monitoring handled by SMI
[    0.076000] .... node  #0, CPUs:      #1
[    0.087606] x86: Booted up 1 node, 2 CPUs
[    0.087611] smpboot: Total of 2 processors activated (7181.78 BogoMIPS)
[    0.087708] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.088163] devtmpfs: initialized
[    0.095534] EVM: security.selinux
[    0.095537] EVM: security.SMACK64
[    0.095539] EVM: security.ima
[    0.095540] EVM: security.capability
[    0.096036] PM: Registering ACPI NVS region [mem 0xbf6d0000-0xbf6e2fff] (77824 bytes)
[    0.097025] pinctrl core: initialized pinctrl subsystem
[    0.097122] regulator-dummy: no parameters
[    0.097167] RTC time: 21:35:47, date: 02/19/15
[    0.097219] NET: Registered protocol family 16
[    0.097388] cpuidle: using governor ladder
[    0.097391] cpuidle: using governor menu
[    0.097443] ACPI: bus type PCI registered
[    0.097445] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.097523] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.097527] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.122507] PCI: Using configuration type 1 for base access
[    0.122515] dmi type 0xB1 record - unknown flag
[    0.124084] bio: create slab <bio-0> at 0
[    0.124111] ACPI: Added _OSI(Module Device)
[    0.124114] ACPI: Added _OSI(Processor Device)
[    0.124116] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.124118] ACPI: Added _OSI(Processor Aggregator Device)
[    0.140025] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.140634] ACPI: SSDT 00000000bf6d7761 000238 (v01  PmRef  Cpu0Ist 00003000 INTL 20061109)
[    0.141005] ACPI: Dynamic OEM Table Load:
[    0.141009] ACPI: SSDT           (null) 000238 (v01  PmRef  Cpu0Ist 00003000 INTL 20061109)
[    0.141137] ACPI: SSDT 00000000bf6d70f2 0005EA (v01  PmRef  Cpu0Cst 00003001 INTL 20061109)
[    0.141487] ACPI: Dynamic OEM Table Load:
[    0.141490] ACPI: SSDT           (null) 0005EA (v01  PmRef  Cpu0Cst 00003001 INTL 20061109)
[    0.141732] ACPI: SSDT 00000000bf6d7999 0000C8 (v01  PmRef  Cpu1Ist 00003000 INTL 20061109)
[    0.142092] ACPI: Dynamic OEM Table Load:
[    0.142095] ACPI: SSDT           (null) 0000C8 (v01  PmRef  Cpu1Ist 00003000 INTL 20061109)
[    0.142181] ACPI: SSDT 00000000bf6d76dc 000085 (v01  PmRef  Cpu1Cst 00003000 INTL 20061109)
[    0.142534] ACPI: Dynamic OEM Table Load:
[    0.142537] ACPI: SSDT           (null) 000085 (v01  PmRef  Cpu1Cst 00003000 INTL 20061109)
[    0.142871] ACPI: Interpreter enabled
[    0.142879] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20131115/hwxface-580)
[    0.142885] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)
[    0.142902] ACPI: (supports S0 S3 S4 S5)
[    0.142905] ACPI: Using IOAPIC for interrupt routing
[    0.142932] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.143096] ACPI: No dock devices found.
[    0.253275] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.253284] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.253291] acpi PNP0A08:00: _OSC failed (AE_NOT_FOUND); disabling ASPM
[    0.254195] PCI host bridge to bus 0000:00
[    0.254200] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.254203] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.254207] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.254210] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.254212] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff]
[    0.254215] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
[    0.254218] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
[    0.254221] pci_bus 0000:00: root bus resource [mem 0xc0000000-0xdfffffff]
[    0.254224] pci_bus 0000:00: root bus resource [mem 0xf0000000-0xfebfffff]
[    0.254236] pci 0000:00:00.0: [8086:2a00] type 00 class 0x060000
[    0.254367] pci 0000:00:02.0: [8086:2a02] type 00 class 0x030000
[    0.254384] pci 0000:00:02.0: reg 0x10: [mem 0xf8000000-0xf80fffff 64bit]
[    0.254395] pci 0000:00:02.0: reg 0x18: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.254402] pci 0000:00:02.0: reg 0x20: [io  0x1800-0x1807]
[    0.254518] pci 0000:00:02.1: [8086:2a03] type 00 class 0x038000
[    0.254532] pci 0000:00:02.1: reg 0x10: [mem 0xf8100000-0xf81fffff 64bit]
[    0.254697] pci 0000:00:1a.0: [8086:2834] type 00 class 0x0c0300
[    0.254759] pci 0000:00:1a.0: reg 0x20: [io  0x1820-0x183f]
[    0.256244] pci 0000:00:1a.0: System wakeup disabled by ACPI
[    0.256289] pci 0000:00:1a.1: [8086:2835] type 00 class 0x0c0300
[    0.256352] pci 0000:00:1a.1: reg 0x20: [io  0x1840-0x185f]
[    0.260243] pci 0000:00:1a.1: System wakeup disabled by ACPI
[    0.260305] pci 0000:00:1a.7: [8086:283a] type 00 class 0x0c0320
[    0.260333] pci 0000:00:1a.7: reg 0x10: [mem 0xf8504800-0xf8504bff]
[    0.260449] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.260521] pci 0000:00:1a.7: System wakeup disabled by ACPI
[    0.260577] pci 0000:00:1b.0: [8086:284b] type 00 class 0x040300
[    0.260602] pci 0000:00:1b.0: reg 0x10: [mem 0xf8500000-0xf8503fff 64bit]
[    0.260716] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.260783] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    0.260837] pci 0000:00:1c.0: [8086:283f] type 01 class 0x060400
[    0.260957] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.261073] pci 0000:00:1c.1: [8086:2841] type 01 class 0x060400
[    0.261192] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.261308] pci 0000:00:1c.3: [8086:2845] type 01 class 0x060400
[    0.261427] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.261541] pci 0000:00:1c.4: [8086:2847] type 01 class 0x060400
[    0.261659] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.261771] pci 0000:00:1d.0: [8086:2830] type 00 class 0x0c0300
[    0.261833] pci 0000:00:1d.0: reg 0x20: [io  0x1860-0x187f]
[    0.261934] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.261978] pci 0000:00:1d.1: [8086:2831] type 00 class 0x0c0300
[    0.262041] pci 0000:00:1d.1: reg 0x20: [io  0x1880-0x189f]
[    0.264243] pci 0000:00:1d.1: System wakeup disabled by ACPI
[    0.264288] pci 0000:00:1d.2: [8086:2832] type 00 class 0x0c0300
[    0.264350] pci 0000:00:1d.2: reg 0x20: [io  0x18a0-0x18bf]
[    0.268244] pci 0000:00:1d.2: System wakeup disabled by ACPI
[    0.268304] pci 0000:00:1d.7: [8086:2836] type 00 class 0x0c0320
[    0.268331] pci 0000:00:1d.7: reg 0x10: [mem 0xf8504c00-0xf8504fff]
[    0.268448] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.268521] pci 0000:00:1d.7: System wakeup disabled by ACPI
[    0.268571] pci 0000:00:1e.0: [8086:2448] type 01 class 0x060401
[    0.268749] pci 0000:00:1f.0: [8086:2815] type 00 class 0x060100
[    0.268870] pci 0000:00:1f.0: address space collision: [io  0x1000-0x107f] conflicts with ACPI CPU throttle [??? 0x00001010-0x00001015 flags 0x80000000]
[    0.268878] pci 0000:00:1f.0: quirk: [io  0x1180-0x11bf] claimed by ICH6 GPIO
[    0.268884] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0680 (mask 007f)
[    0.268889] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 1640 (mask 007f)
[    0.269023] pci 0000:00:1f.1: [8086:2850] type 00 class 0x01018a
[    0.269043] pci 0000:00:1f.1: reg 0x10: [io  0x0000-0x0007]
[    0.269057] pci 0000:00:1f.1: reg 0x14: [io  0x0000-0x0003]
[    0.269070] pci 0000:00:1f.1: reg 0x18: [io  0x0000-0x0007]
[    0.269084] pci 0000:00:1f.1: reg 0x1c: [io  0x0000-0x0003]
[    0.269098] pci 0000:00:1f.1: reg 0x20: [io  0x1810-0x181f]
[    0.269234] pci 0000:00:1f.2: [8086:2829] type 00 class 0x010601
[    0.269264] pci 0000:00:1f.2: reg 0x10: [io  0x1c00-0x1c07]
[    0.269278] pci 0000:00:1f.2: reg 0x14: [io  0x18d4-0x18d7]
[    0.269292] pci 0000:00:1f.2: reg 0x18: [io  0x18d8-0x18df]
[    0.269305] pci 0000:00:1f.2: reg 0x1c: [io  0x18d0-0x18d3]
[    0.269319] pci 0000:00:1f.2: reg 0x20: [io  0x18e0-0x18ff]
[    0.269333] pci 0000:00:1f.2: reg 0x24: [mem 0xf8504000-0xf85047ff]
[    0.269405] pci 0000:00:1f.2: PME# supported from D3hot
[    0.269506] pci 0000:00:1f.3: [8086:283e] type 00 class 0x0c0500
[    0.269525] pci 0000:00:1f.3: reg 0x10: [mem 0x00000000-0x000000ff]
[    0.269571] pci 0000:00:1f.3: reg 0x20: [io  0x1c20-0x1c3f]
[    0.269789] acpiphp: Slot [1] registered
[    0.269798] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.269805] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.269811] pci 0000:00:1c.0:   bridge window [mem 0xc4000000-0xc7ffffff]
[    0.269820] pci 0000:00:1c.0:   bridge window [mem 0xcc000000-0xcdffffff 64bit pref]
[    0.269916] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    0.269922] pci 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
[    0.269928] pci 0000:00:1c.1:   bridge window [mem 0xf0000000-0xf3ffffff]
[    0.269937] pci 0000:00:1c.1:   bridge window [mem 0xfa000000-0xfbffffff 64bit pref]
[    0.270291] pci 0000:06:00.0: [14e4:4315] type 00 class 0x028000
[    0.270364] pci 0000:06:00.0: reg 0x10: [mem 0xf4000000-0xf4003fff 64bit]
[    0.270757] pci 0000:06:00.0: supports D1 D2
[    0.270760] pci 0000:06:00.0: PME# supported from D0 D3hot D3cold
[    0.270976] pci 0000:00:1c.3: PCI bridge to [bus 06]
[    0.270982] pci 0000:00:1c.3:   bridge window [io  0x4000-0x4fff]
[    0.270988] pci 0000:00:1c.3:   bridge window [mem 0xf4000000-0xf7ffffff]
[    0.270997] pci 0000:00:1c.3:   bridge window [mem 0xfc000000-0xfdffffff 64bit pref]
[    0.271173] pci 0000:07:00.0: [10ec:8168] type 00 class 0x020000
[    0.271236] pci 0000:07:00.0: reg 0x10: [io  0x5000-0x50ff]
[    0.271352] pci 0000:07:00.0: reg 0x18: [mem 0xf8610000-0xf8610fff 64bit pref]
[    0.271425] pci 0000:07:00.0: reg 0x20: [mem 0xf8600000-0xf860ffff 64bit pref]
[    0.271473] pci 0000:07:00.0: reg 0x30: [mem 0x00000000-0x0000ffff pref]
[    0.272049] pci 0000:07:00.0: supports D1 D2
[    0.272052] pci 0000:07:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.272182] pci 0000:07:00.0: System wakeup disabled by ACPI
[    0.272280] pci 0000:00:1c.4: PCI bridge to [bus 07]
[    0.272287] pci 0000:00:1c.4:   bridge window [io  0x5000-0x5fff]
[    0.272299] pci 0000:00:1c.4:   bridge window [mem 0xf8600000-0xf86fffff 64bit pref]
[    0.272373] pci 0000:08:05.0: [1217:00f7] type 00 class 0x0c0010
[    0.272398] pci 0000:08:05.0: reg 0x10: [mem 0xf8200000-0xf8200fff]
[    0.272412] pci 0000:08:05.0: reg 0x14: [mem 0xf8202000-0xf82027ff]
[    0.272504] pci 0000:08:05.0: supports D1 D2
[    0.272507] pci 0000:08:05.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.272572] pci 0000:08:05.2: [1217:7120] type 00 class 0x080501
[    0.272601] pci 0000:08:05.2: reg 0x10: [mem 0xf8202800-0xf82028ff]
[    0.272727] pci 0000:08:05.2: supports D1 D2
[    0.272730] pci 0000:08:05.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.272794] pci 0000:08:05.3: [1217:7130] type 00 class 0x018000
[    0.272822] pci 0000:08:05.3: reg 0x10: [mem 0xf8201000-0xf8201fff]
[    0.272946] pci 0000:08:05.3: supports D1 D2
[    0.272949] pci 0000:08:05.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.273056] pci 0000:00:1e.0: PCI bridge to [bus 08] (subtractive decode)
[    0.273065] pci 0000:00:1e.0:   bridge window [mem 0xf8200000-0xf82fffff]
[    0.273074] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.273078] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.273081] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.273083] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
[    0.273086] pci 0000:00:1e.0:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.273089] pci 0000:00:1e.0:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.273092] pci 0000:00:1e.0:   bridge window [mem 0xc0000000-0xdfffffff] (subtractive decode)
[    0.273095] pci 0000:00:1e.0:   bridge window [mem 0xf0000000-0xfebfffff] (subtractive decode)
[    0.273649] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)
[    0.273723] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.273794] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.273866] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.273936] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.274007] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.274083] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.274153] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.304239] ACPI: Enabled 3 GPEs in block 00 to 1F
[    0.304251] ACPI: \_SB_.PCI0: notify handler is installed
[    0.304307] Found 1 acpi root devices
[    0.304357] ACPI : EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[    0.304461] vgaarb: setting as boot device: PCI:0000:00:02.0
[    0.304461] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.304461] vgaarb: loaded
[    0.304461] vgaarb: bridge control possible 0000:00:02.0
[    0.304461] SCSI subsystem initialized
[    0.304461] libata version 3.00 loaded.
[    0.304461] ACPI: bus type USB registered
[    0.304461] usbcore: registered new interface driver usbfs
[    0.304461] usbcore: registered new interface driver hub
[    0.304461] usbcore: registered new device driver usb
[    0.304461] PCI: Using ACPI for IRQ routing
[    0.316628] PCI: pci_cache_line_size set to 64 bytes
[    0.317120] e820: reserve RAM buffer [mem 0x0009f800-0x0009ffff]
[    0.317123] e820: reserve RAM buffer [mem 0xbf6d0000-0xbfffffff]
[    0.317244] NetLabel: Initializing
[    0.317247] NetLabel:  domain hash size = 128
[    0.317248] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.317268] NetLabel:  unlabeled traffic allowed by default
[    0.317284] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.317284] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.13.0-45-generic (buildd@phianna) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #74-Ubuntu SMP Tue Jan 13 19:36:28 UTC 2015 (Ubuntu 3.13.0-45.74-generic 3.13.11-ckt13)
[    0.000000] Command line: BOOT_IMAGE=/vmlinuz-3.13.0-45-generic root=/dev/mapper/ubuntu--vg-root ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009f7ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009f800-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000dc000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000bf6cffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bf6d0000-0x00000000bf6e2fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bf6e3000-0x00000000bfffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec0ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed003ff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed14000-0x00000000fed19fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed8ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000013fffffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.4 present.
[    0.000000] DMI: Dell Inc. Vostro1510/0M277C, BIOS A12 09/10/2008
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x140000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0C0000000 mask FC0000000 uncachable
[    0.000000]   1 base 000000000 mask F00000000 write-back
[    0.000000]   2 base 100000000 mask FC0000000 write-back
[    0.000000]   3 base 0BF700000 mask FFFF00000 uncachable
[    0.000000]   4 base 0BF800000 mask FFF800000 uncachable
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 3GB, range: 1GB, type UC
[    0.000000] reg 1, base: 0GB, range: 4GB, type WB
[    0.000000] reg 2, base: 4GB, range: 1GB, type WB
[    0.000000] reg 3, base: 3063MB, range: 1MB, type UC
[    0.000000] reg 4, base: 3064MB, range: 8MB, type UC
[    0.000000] total RAM covered: 4087M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 16M     num_reg: 5      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3063MB, range: 1MB, type UC
[    0.000000] reg 3, base: 3064MB, range: 8MB, type UC
[    0.000000] reg 4, base: 4GB, range: 1GB, type WB
[    0.000000] e820: update [mem 0xbf700000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xbf6d0 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000f76f0-0x000f76ff] mapped at [ffff8800000f76f0]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01fe1000, 0x01fe1fff] PGTABLE
[    0.000000] BRK [0x01fe2000, 0x01fe2fff] PGTABLE
[    0.000000] BRK [0x01fe3000, 0x01fe3fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x13fe00000-0x13fffffff]
[    0.000000]  [mem 0x13fe00000-0x13fffffff] page 2M
[    0.000000] BRK [0x01fe4000, 0x01fe4fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x13c000000-0x13fdfffff]
[    0.000000]  [mem 0x13c000000-0x13fdfffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x100000000-0x13bffffff]
[    0.000000]  [mem 0x100000000-0x13bffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0xbf6cffff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0xbf5fffff] page 2M
[    0.000000]  [mem 0xbf600000-0xbf6cffff] page 4k
[    0.000000] RAMDISK: [mem 0x359c6000-0x36cdafff]
[    0.000000] ACPI: RSDP 00000000000f7670 000024 (v02 DELL  )
[    0.000000] ACPI: XSDT 00000000bf6d6873 000094 (v01 DELL    M08     06040000  LTP 00000000)
[    0.000000] ACPI: FACP 00000000bf6decd6 0000F4 (v03 TOSCPL CRESTLNE 06040000 ALAN 00000001)
[    0.000000] ACPI: DSDT 00000000bf6d7db1 006EB1 (v02 TOSCPL CRESTLNE 06040000 INTL 20060608)
[    0.000000] ACPI: FACS 00000000bf6e2fc0 000040
[    0.000000] ACPI: APIC 00000000bf6dedca 000068 (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: HPET 00000000bf6dee32 000038 (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: MCFG 00000000bf6dee6a 00003C (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: TCPA 00000000bf6deea6 000032 (v01 Intel  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: TMOR 00000000bf6deed8 000026 (v01 PTLTD           06040000 PTL  00000003)
[    0.000000] ACPI: OSFR 00000000bf6deefe 000072 (v01 TOSHIB A+2nd ID 06040000 TASM 04010000)
[    0.000000] ACPI: APIC 00000000bf6def70 000068 (v01 PTLTD  ? APIC   06040000  LTP 00000000)
[    0.000000] ACPI: BOOT 00000000bf6defd8 000028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: SSDT 00000000bf6d7b04 0002AD (v01 SataRe SataAhci 00001000 INTL 20061109)
[    0.000000] ACPI: SSDT 00000000bf6d7a61 0000A3 (v01 BrtRef  DD01BRT 00001000 INTL 20061109)
[    0.000000] ACPI: SSDT 00000000bf6d6e93 00025F (v01  PmRef  Cpu0Tst 00003000 INTL 20061109)
[    0.000000] ACPI: SSDT 00000000bf6d6ded 0000A6 (v01  PmRef  Cpu1Tst 00003000 INTL 20061109)
[    0.000000] ACPI: SSDT 00000000bf6d6907 0004E6 (v01  PmRef    CpuPm 00003000 INTL 20061109)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify linux-acpi@vger.kernel.org
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000013fffffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x13fffffff]
[    0.000000]   NODE_DATA [mem 0x13fff8000-0x13fffcfff]
[    0.000000]  [ffffea0000000000-ffffea0004ffffff] PMD -> [ffff88013b600000-ffff88013f5fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x13fffffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009efff]
[    0.000000]   node   0: [mem 0x00100000-0xbf6cffff]
[    0.000000]   node   0: [mem 0x100000000-0x13fffffff]
[    0.000000] On node 0 totalpages: 1046126
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3998 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 12188 pages used for memmap
[    0.000000]   DMA32 zone: 779984 pages, LIFO batch:31
[    0.000000]   Normal zone: 4096 pages used for memmap
[    0.000000]   Normal zone: 262144 pages, LIFO batch:31
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
[    0.000000] smpboot: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dbfff]
[    0.000000] PM: Registered nosave memory: [mem 0x000dc000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xbf6d0000-0xbf6e2fff]
[    0.000000] PM: Registered nosave memory: [mem 0xbf6e3000-0xbfffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xc0000000-0xdfffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec0ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec10000-0xfecfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed00000-0xfed13fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed14000-0xfed19fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1a000-0xfed1bfff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed8ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed90000-0xfedfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xfeffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xff000000-0xffffffff]
[    0.000000] e820: [mem 0xc0000000-0xdfffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88013fc00000 s82368 r8192 d24128 u1048576
[    0.000000] pcpu-alloc: s82368 r8192 d24128 u1048576 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1029757
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-3.13.0-45-generic root=/dev/mapper/ubuntu--vg-root ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 4016500K/4184504K available (7383K kernel code, 1145K rwdata, 3408K rodata, 1336K init, 1444K bss, 168004K reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=2.
[    0.000000]     Offload RCU callbacks from all CPUs
[    0.000000]     Offload RCU callbacks from CPUs: 0-1.
[    0.000000] NR_IRQS:16640 nr_irqs:512 16
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 16777216 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 1795.447 MHz processor
[    0.004004] Calibrating delay loop (skipped), value calculated using timer frequency.. 3590.89 BogoMIPS (lpj=7181788)
[    0.004009] pid_max: default: 32768 minimum: 301
[    0.004054] Security Framework initialized
[    0.004081] AppArmor: AppArmor initialized
[    0.004082] Yama: becoming mindful.
[    0.004577] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.009003] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.010101] Mount-cache hash table entries: 8192 (order: 4, 65536 bytes)
[    0.010114] Mountpoint-cache hash table entries: 8192 (order: 4, 65536 bytes)
[    0.010482] Initializing cgroup subsys memory
[    0.010495] Initializing cgroup subsys devices
[    0.010498] Initializing cgroup subsys freezer
[    0.010501] Initializing cgroup subsys blkio
[    0.010503] Initializing cgroup subsys perf_event
[    0.010506] Initializing cgroup subsys hugetlb
[    0.010535] CPU: Physical Processor ID: 0
[    0.010537] CPU: Processor Core ID: 0
[    0.010540] mce: CPU supports 6 MCE banks
[    0.010548] CPU0: Thermal monitoring handled by SMI
[    0.010558] Last level iTLB entries: 4KB 128, 2MB 4, 4MB 4
[    0.010558] Last level dTLB entries: 4KB 256, 2MB 0, 4MB 32
[    0.010558] tlb_flushall_shift: -1
[    0.010680] Freeing SMP alternatives memory: 32K (ffffffff81e6e000 - ffffffff81e76000)
[    0.012497] ACPI: Core revision 20131115
[    0.017309] ACPI: All ACPI Tables successfully acquired
[    0.020013] ftrace: allocating 28554 entries in 112 pages
[    0.032565] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.075806] smpboot: CPU0: Intel(R) Core(TM)2 Duo CPU     T5670  @ 1.80GHz (fam: 06, model: 0f, stepping: 0d)
[    0.076000] Performance Events: PEBS fmt0+, 4-deep LBR, Core2 events, Intel PMU driver.
[    0.076000] perf_event_intel: PEBS disabled due to CPU errata
[    0.076000] ... version:                2
[    0.076000] ... bit width:              40
[    0.076000] ... generic registers:      2
[    0.076000] ... value mask:             000000ffffffffff
[    0.076000] ... max period:             000000007fffffff
[    0.076000] ... fixed-purpose events:   3
[    0.076000] ... event mask:             0000000700000003
[    0.076000] x86: Booting SMP configuration:
[    0.076000] CPU1: Thermal monitoring handled by SMI
[    0.076000] .... node  #0, CPUs:      #1
[    0.087606] x86: Booted up 1 node, 2 CPUs
[    0.087611] smpboot: Total of 2 processors activated (7181.78 BogoMIPS)
[    0.087708] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.088163] devtmpfs: initialized
[    0.095534] EVM: security.selinux
[    0.095537] EVM: security.SMACK64
[    0.095539] EVM: security.ima
[    0.095540] EVM: security.capability
[    0.096036] PM: Registering ACPI NVS region [mem 0xbf6d0000-0xbf6e2fff] (77824 bytes)
[    0.097025] pinctrl core: initialized pinctrl subsystem
[    0.097122] regulator-dummy: no parameters
[    0.097167] RTC time: 21:35:47, date: 02/19/15
[    0.097219] NET: Registered protocol family 16
[    0.097388] cpuidle: using governor ladder
[    0.097391] cpuidle: using governor menu
[    0.097443] ACPI: bus type PCI registered
[    0.097445] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.097523] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.097527] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.122507] PCI: Using configuration type 1 for base access
[    0.122515] dmi type 0xB1 record - unknown flag
[    0.124084] bio: create slab <bio-0> at 0
[    0.124111] ACPI: Added _OSI(Module Device)
[    0.124114] ACPI: Added _OSI(Processor Device)
[    0.124116] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.124118] ACPI: Added _OSI(Processor Aggregator Device)
[    0.140025] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.140634] ACPI: SSDT 00000000bf6d7761 000238 (v01  PmRef  Cpu0Ist 00003000 INTL 20061109)
[    0.141005] ACPI: Dynamic OEM Table Load:
[    0.141009] ACPI: SSDT           (null) 000238 (v01  PmRef  Cpu0Ist 00003000 INTL 20061109)
[    0.141137] ACPI: SSDT 00000000bf6d70f2 0005EA (v01  PmRef  Cpu0Cst 00003001 INTL 20061109)
[    0.141487] ACPI: Dynamic OEM Table Load:
[    0.141490] ACPI: SSDT           (null) 0005EA (v01  PmRef  Cpu0Cst 00003001 INTL 20061109)
[    0.141732] ACPI: SSDT 00000000bf6d7999 0000C8 (v01  PmRef  Cpu1Ist 00003000 INTL 20061109)
[    0.142092] ACPI: Dynamic OEM Table Load:
[    0.142095] ACPI: SSDT           (null) 0000C8 (v01  PmRef  Cpu1Ist 00003000 INTL 20061109)
[    0.142181] ACPI: SSDT 00000000bf6d76dc 000085 (v01  PmRef  Cpu1Cst 00003000 INTL 20061109)
[    0.142534] ACPI: Dynamic OEM Table Load:
[    0.142537] ACPI: SSDT           (null) 000085 (v01  PmRef  Cpu1Cst 00003000 INTL 20061109)
[    0.142871] ACPI: Interpreter enabled
[    0.142879] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20131115/hwxface-580)
[    0.142885] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)
[    0.142902] ACPI: (supports S0 S3 S4 S5)
[    0.142905] ACPI: Using IOAPIC for interrupt routing
[    0.142932] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.143096] ACPI: No dock devices found.
[    0.253275] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.253284] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.253291] acpi PNP0A08:00: _OSC failed (AE_NOT_FOUND); disabling ASPM
[    0.254195] PCI host bridge to bus 0000:00
[    0.254200] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.254203] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.254207] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.254210] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.254212] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff]
[    0.254215] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
[    0.254218] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
[    0.254221] pci_bus 0000:00: root bus resource [mem 0xc0000000-0xdfffffff]
[    0.254224] pci_bus 0000:00: root bus resource [mem 0xf0000000-0xfebfffff]
[    0.254236] pci 0000:00:00.0: [8086:2a00] type 00 class 0x060000
[    0.254367] pci 0000:00:02.0: [8086:2a02] type 00 class 0x030000
[    0.254384] pci 0000:00:02.0: reg 0x10: [mem 0xf8000000-0xf80fffff 64bit]
[    0.254395] pci 0000:00:02.0: reg 0x18: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.254402] pci 0000:00:02.0: reg 0x20: [io  0x1800-0x1807]
[    0.254518] pci 0000:00:02.1: [8086:2a03] type 00 class 0x038000
[    0.254532] pci 0000:00:02.1: reg 0x10: [mem 0xf8100000-0xf81fffff 64bit]
[    0.254697] pci 0000:00:1a.0: [8086:2834] type 00 class 0x0c0300
[    0.254759] pci 0000:00:1a.0: reg 0x20: [io  0x1820-0x183f]
[    0.256244] pci 0000:00:1a.0: System wakeup disabled by ACPI
[    0.256289] pci 0000:00:1a.1: [8086:2835] type 00 class 0x0c0300
[    0.256352] pci 0000:00:1a.1: reg 0x20: [io  0x1840-0x185f]
[    0.260243] pci 0000:00:1a.1: System wakeup disabled by ACPI
[    0.260305] pci 0000:00:1a.7: [8086:283a] type 00 class 0x0c0320
[    0.260333] pci 0000:00:1a.7: reg 0x10: [mem 0xf8504800-0xf8504bff]
[    0.260449] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.260521] pci 0000:00:1a.7: System wakeup disabled by ACPI
[    0.260577] pci 0000:00:1b.0: [8086:284b] type 00 class 0x040300
[    0.260602] pci 0000:00:1b.0: reg 0x10: [mem 0xf8500000-0xf8503fff 64bit]
[    0.260716] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.260783] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    0.260837] pci 0000:00:1c.0: [8086:283f] type 01 class 0x060400
[    0.260957] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.261073] pci 0000:00:1c.1: [8086:2841] type 01 class 0x060400
[    0.261192] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.261308] pci 0000:00:1c.3: [8086:2845] type 01 class 0x060400
[    0.261427] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.261541] pci 0000:00:1c.4: [8086:2847] type 01 class 0x060400
[    0.261659] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.261771] pci 0000:00:1d.0: [8086:2830] type 00 class 0x0c0300
[    0.261833] pci 0000:00:1d.0: reg 0x20: [io  0x1860-0x187f]
[    0.261934] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.261978] pci 0000:00:1d.1: [8086:2831] type 00 class 0x0c0300
[    0.262041] pci 0000:00:1d.1: reg 0x20: [io  0x1880-0x189f]
[    0.264243] pci 0000:00:1d.1: System wakeup disabled by ACPI
[    0.264288] pci 0000:00:1d.2: [8086:2832] type 00 class 0x0c0300
[    0.264350] pci 0000:00:1d.2: reg 0x20: [io  0x18a0-0x18bf]
[    0.268244] pci 0000:00:1d.2: System wakeup disabled by ACPI
[    0.268304] pci 0000:00:1d.7: [8086:2836] type 00 class 0x0c0320
[    0.268331] pci 0000:00:1d.7: reg 0x10: [mem 0xf8504c00-0xf8504fff]
[    0.268448] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.268521] pci 0000:00:1d.7: System wakeup disabled by ACPI
[    0.268571] pci 0000:00:1e.0: [8086:2448] type 01 class 0x060401
[    0.268749] pci 0000:00:1f.0: [8086:2815] type 00 class 0x060100
[    0.268870] pci 0000:00:1f.0: address space collision: [io  0x1000-0x107f] conflicts with ACPI CPU throttle [??? 0x00001010-0x00001015 flags 0x80000000]
[    0.268878] pci 0000:00:1f.0: quirk: [io  0x1180-0x11bf] claimed by ICH6 GPIO
[    0.268884] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0680 (mask 007f)
[    0.268889] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 1640 (mask 007f)
[    0.269023] pci 0000:00:1f.1: [8086:2850] type 00 class 0x01018a
[    0.269043] pci 0000:00:1f.1: reg 0x10: [io  0x0000-0x0007]
[    0.269057] pci 0000:00:1f.1: reg 0x14: [io  0x0000-0x0003]
[    0.269070] pci 0000:00:1f.1: reg 0x18: [io  0x0000-0x0007]
[    0.269084] pci 0000:00:1f.1: reg 0x1c: [io  0x0000-0x0003]
[    0.269098] pci 0000:00:1f.1: reg 0x20: [io  0x1810-0x181f]
[    0.269234] pci 0000:00:1f.2: [8086:2829] type 00 class 0x010601
[    0.269264] pci 0000:00:1f.2: reg 0x10: [io  0x1c00-0x1c07]
[    0.269278] pci 0000:00:1f.2: reg 0x14: [io  0x18d4-0x18d7]
[    0.269292] pci 0000:00:1f.2: reg 0x18: [io  0x18d8-0x18df]
[    0.269305] pci 0000:00:1f.2: reg 0x1c: [io  0x18d0-0x18d3]
[    0.269319] pci 0000:00:1f.2: reg 0x20: [io  0x18e0-0x18ff]
[    0.269333] pci 0000:00:1f.2: reg 0x24: [mem 0xf8504000-0xf85047ff]
[    0.269405] pci 0000:00:1f.2: PME# supported from D3hot
[    0.269506] pci 0000:00:1f.3: [8086:283e] type 00 class 0x0c0500
[    0.269525] pci 0000:00:1f.3: reg 0x10: [mem 0x00000000-0x000000ff]
[    0.269571] pci 0000:00:1f.3: reg 0x20: [io  0x1c20-0x1c3f]
[    0.269789] acpiphp: Slot [1] registered
[    0.269798] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.269805] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.269811] pci 0000:00:1c.0:   bridge window [mem 0xc4000000-0xc7ffffff]
[    0.269820] pci 0000:00:1c.0:   bridge window [mem 0xcc000000-0xcdffffff 64bit pref]
[    0.269916] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    0.269922] pci 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
[    0.269928] pci 0000:00:1c.1:   bridge window [mem 0xf0000000-0xf3ffffff]
[    0.269937] pci 0000:00:1c.1:   bridge window [mem 0xfa000000-0xfbffffff 64bit pref]
[    0.270291] pci 0000:06:00.0: [14e4:4315] type 00 class 0x028000
[    0.270364] pci 0000:06:00.0: reg 0x10: [mem 0xf4000000-0xf4003fff 64bit]
[    0.270757] pci 0000:06:00.0: supports D1 D2
[    0.270760] pci 0000:06:00.0: PME# supported from D0 D3hot D3cold
[    0.270976] pci 0000:00:1c.3: PCI bridge to [bus 06]
[    0.270982] pci 0000:00:1c.3:   bridge window [io  0x4000-0x4fff]
[    0.270988] pci 0000:00:1c.3:   bridge window [mem 0xf4000000-0xf7ffffff]
[    0.270997] pci 0000:00:1c.3:   bridge window [mem 0xfc000000-0xfdffffff 64bit pref]
[    0.271173] pci 0000:07:00.0: [10ec:8168] type 00 class 0x020000
[    0.271236] pci 0000:07:00.0: reg 0x10: [io  0x5000-0x50ff]
[    0.271352] pci 0000:07:00.0: reg 0x18: [mem 0xf8610000-0xf8610fff 64bit pref]
[    0.271425] pci 0000:07:00.0: reg 0x20: [mem 0xf8600000-0xf860ffff 64bit pref]
[    0.271473] pci 0000:07:00.0: reg 0x30: [mem 0x00000000-0x0000ffff pref]
[    0.272049] pci 0000:07:00.0: supports D1 D2
[    0.272052] pci 0000:07:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.272182] pci 0000:07:00.0: System wakeup disabled by ACPI
[    0.272280] pci 0000:00:1c.4: PCI bridge to [bus 07]
[    0.272287] pci 0000:00:1c.4:   bridge window [io  0x5000-0x5fff]
[    0.272299] pci 0000:00:1c.4:   bridge window [mem 0xf8600000-0xf86fffff 64bit pref]
[    0.272373] pci 0000:08:05.0: [1217:00f7] type 00 class 0x0c0010
[    0.272398] pci 0000:08:05.0: reg 0x10: [mem 0xf8200000-0xf8200fff]
[    0.272412] pci 0000:08:05.0: reg 0x14: [mem 0xf8202000-0xf82027ff]
[    0.272504] pci 0000:08:05.0: supports D1 D2
[    0.272507] pci 0000:08:05.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.272572] pci 0000:08:05.2: [1217:7120] type 00 class 0x080501
[    0.272601] pci 0000:08:05.2: reg 0x10: [mem 0xf8202800-0xf82028ff]
[    0.272727] pci 0000:08:05.2: supports D1 D2
[    0.272730] pci 0000:08:05.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.272794] pci 0000:08:05.3: [1217:7130] type 00 class 0x018000
[    0.272822] pci 0000:08:05.3: reg 0x10: [mem 0xf8201000-0xf8201fff]
[    0.272946] pci 0000:08:05.3: supports D1 D2
[    0.272949] pci 0000:08:05.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.273056] pci 0000:00:1e.0: PCI bridge to [bus 08] (subtractive decode)
[    0.273065] pci 0000:00:1e.0:   bridge window [mem 0xf8200000-0xf82fffff]
[    0.273074] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.273078] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.273081] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.273083] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
[    0.273086] pci 0000:00:1e.0:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.273089] pci 0000:00:1e.0:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.273092] pci 0000:00:1e.0:   bridge window [mem 0xc0000000-0xdfffffff] (subtractive decode)
[    0.273095] pci 0000:00:1e.0:   bridge window [mem 0xf0000000-0xfebfffff] (subtractive decode)
[    0.273649] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)
[    0.273723] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.273794] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.273866] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.273936] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.274007] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.274083] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.274153] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.304239] ACPI: Enabled 3 GPEs in block 00 to 1F
[    0.304251] ACPI: \_SB_.PCI0: notify handler is installed
[    0.304307] Found 1 acpi root devices
[    0.304357] ACPI : EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[    0.304461] vgaarb: setting as boot device: PCI:0000:00:02.0
[    0.304461] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.304461] vgaarb: loaded
[    0.304461] vgaarb: bridge control possible 0000:00:02.0
[    0.304461] SCSI subsystem initialized
[    0.304461] libata version 3.00 loaded.
[    0.304461] ACPI: bus type USB registered
[    0.304461] usbcore: registered new interface driver usbfs
[    0.304461] usbcore: registered new interface driver hub
[    0.304461] usbcore: registered new device driver usb
[    0.304461] PCI: Using ACPI for IRQ routing
[    0.316628] PCI: pci_cache_line_size set to 64 bytes
[    0.317120] e820: reserve RAM buffer [mem 0x0009f800-0x0009ffff]
[    0.317123] e820: reserve RAM buffer [mem 0xbf6d0000-0xbfffffff]
[    0.317244] NetLabel: Initializing
[    0.317247] NetLabel:  domain hash size = 128
[    0.317248] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.317268] NetLabel:  unlabeled traffic allowed by default
[    0.317284] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.317284] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.317284] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.318084] Switched to clocksource hpet
[    0.325220] AppArmor: AppArmor Filesystem Enabled
[    0.325268] pnp: PnP ACPI init
[    0.325290] ACPI: bus type PNP registered
[    0.325537] system 00:00: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.325541] system 00:00: [mem 0xfed14000-0xfed17fff] has been reserved
[    0.325544] system 00:00: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.325547] system 00:00: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.325551] system 00:00: [mem 0xe0000000-0xefffffff] has been reserved
[    0.325554] system 00:00: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.325557] system 00:00: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.325560] system 00:00: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.325565] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.325796] pnp 00:01: [dma 4]
[    0.325837] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.325880] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
[    0.326011] system 00:03: [mem 0xfed00000-0xfed003ff] has been reserved
[    0.326015] system 00:03: Plug and Play ACPI device, IDs PNP0103 PNP0c01 (active)
[    0.326076] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.326153] system 00:05: [io  0x0680-0x069f] has been reserved
[    0.326157] system 00:05: [io  0x0800-0x080f] has been reserved
[    0.326161] system 00:05: [io  0x1000-0x107f] could not be reserved
[    0.326164] system 00:05: [io  0x1180-0x11bf] has been reserved
[    0.326167] system 00:05: [io  0xfe00] has been reserved
[    0.326173] system 00:05: [io  0xff00-0xff7f] has been reserved
[    0.326177] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.326228] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.356087] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.356148] pnp 00:08: Plug and Play ACPI device, IDs SYN0705 SYN0700 SYN0002 PNP0f13 (active)
[    0.356173] pnp: PnP ACPI: found 9 devices
[    0.356175] ACPI: bus type PNP unregistered
[    0.363509] pci 0000:00:1c.4: bridge window [mem 0x00100000-0x001fffff] to [bus 07] add_size 400000
[    0.363528] pci 0000:00:1f.0: BAR 13: [io  0x1000-0x107f] has bogus alignment
[    0.363533] pci 0000:00:1c.4: res[14]=[mem 0x00100000-0x001fffff] get_res_add_size add_size 400000
[    0.363540] pci 0000:00:1c.4: BAR 14: assigned [mem 0xc0000000-0xc04fffff]
[    0.363544] pci 0000:00:1f.3: BAR 0: assigned [mem 0xc0500000-0xc05000ff]
[    0.363552] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.363556] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.363564] pci 0000:00:1c.0:   bridge window [mem 0xc4000000-0xc7ffffff]
[    0.363570] pci 0000:00:1c.0:   bridge window [mem 0xcc000000-0xcdffffff 64bit pref]
[    0.363579] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    0.363583] pci 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
[    0.363591] pci 0000:00:1c.1:   bridge window [mem 0xf0000000-0xf3ffffff]
[    0.363597] pci 0000:00:1c.1:   bridge window [mem 0xfa000000-0xfbffffff 64bit pref]
[    0.363606] pci 0000:00:1c.3: PCI bridge to [bus 06]
[    0.363610] pci 0000:00:1c.3:   bridge window [io  0x4000-0x4fff]
[    0.363617] pci 0000:00:1c.3:   bridge window [mem 0xf4000000-0xf7ffffff]
[    0.363623] pci 0000:00:1c.3:   bridge window [mem 0xfc000000-0xfdffffff 64bit pref]
[    0.363633] pci 0000:07:00.0: BAR 6: assigned [mem 0xf8620000-0xf862ffff pref]
[    0.363636] pci 0000:00:1c.4: PCI bridge to [bus 07]
[    0.363640] pci 0000:00:1c.4:   bridge window [io  0x5000-0x5fff]
[    0.363648] pci 0000:00:1c.4:   bridge window [mem 0xc0000000-0xc04fffff]
[    0.363654] pci 0000:00:1c.4:   bridge window [mem 0xf8600000-0xf86fffff 64bit pref]
[    0.363663] pci 0000:00:1e.0: PCI bridge to [bus 08]
[    0.363670] pci 0000:00:1e.0:   bridge window [mem 0xf8200000-0xf82fffff]
[    0.363683] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.363686] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.363689] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.363692] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.363695] pci_bus 0000:00: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.363697] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.363700] pci_bus 0000:00: resource 10 [mem 0xc0000000-0xdfffffff]
[    0.363703] pci_bus 0000:00: resource 11 [mem 0xf0000000-0xfebfffff]
[    0.363706] pci_bus 0000:02: resource 0 [io  0x2000-0x2fff]
[    0.363709] pci_bus 0000:02: resource 1 [mem 0xc4000000-0xc7ffffff]
[    0.363712] pci_bus 0000:02: resource 2 [mem 0xcc000000-0xcdffffff 64bit pref]
[    0.363715] pci_bus 0000:03: resource 0 [io  0x3000-0x3fff]
[    0.363718] pci_bus 0000:03: resource 1 [mem 0xf0000000-0xf3ffffff]
[    0.363721] pci_bus 0000:03: resource 2 [mem 0xfa000000-0xfbffffff 64bit pref]
[    0.363723] pci_bus 0000:06: resource 0 [io  0x4000-0x4fff]
[    0.363726] pci_bus 0000:06: resource 1 [mem 0xf4000000-0xf7ffffff]
[    0.363729] pci_bus 0000:06: resource 2 [mem 0xfc000000-0xfdffffff 64bit pref]
[    0.363732] pci_bus 0000:07: resource 0 [io  0x5000-0x5fff]
[    0.363735] pci_bus 0000:07: resource 1 [mem 0xc0000000-0xc04fffff]
[    0.363738] pci_bus 0000:07: resource 2 [mem 0xf8600000-0xf86fffff 64bit pref]
[    0.363741] pci_bus 0000:08: resource 1 [mem 0xf8200000-0xf82fffff]
[    0.363744] pci_bus 0000:08: resource 4 [io  0x0000-0x0cf7]
[    0.363746] pci_bus 0000:08: resource 5 [io  0x0d00-0xffff]
[    0.363749] pci_bus 0000:08: resource 6 [mem 0x000a0000-0x000bffff]
[    0.363752] pci_bus 0000:08: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.363755] pci_bus 0000:08: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.363757] pci_bus 0000:08: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.363760] pci_bus 0000:08: resource 10 [mem 0xc0000000-0xdfffffff]
[    0.363763] pci_bus 0000:08: resource 11 [mem 0xf0000000-0xfebfffff]
[    0.363808] NET: Registered protocol family 2
[    0.364090] TCP established hash table entries: 32768 (order: 6, 262144 bytes)
[    0.364263] TCP bind hash table entries: 32768 (order: 7, 524288 bytes)
[    0.364487] TCP: Hash tables configured (established 32768 bind 32768)
[    0.364544] TCP: reno registered
[    0.364555] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.364594] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.364691] NET: Registered protocol family 1
[    0.364712] pci 0000:00:02.0: Video device with shadowed ROM
[    0.366982] PCI: CLS 64 bytes, default 64
[    0.367079] Trying to unpack rootfs image as initramfs...
[    0.844829] Freeing initrd memory: 19540K (ffff8800359c6000 - ffff880036cdb000)
[    0.844839] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.844843] software IO TLB [mem 0xbb6d0000-0xbf6d0000] (64MB) mapped at [ffff8800bb6d0000-ffff8800bf6cffff]
[    0.844949] Simple Boot Flag at 0x36 set to 0x1
[    0.845126] microcode: CPU0 sig=0x6fd, pf=0x80, revision=0xa1
[    0.845139] microcode: CPU1 sig=0x6fd, pf=0x80, revision=0xa1
[    0.845226] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.845229] Scanning for low memory corruption every 60 seconds
[    0.845520] Initialise system trusted keyring
[    0.845587] audit: initializing netlink socket (disabled)
[    0.845606] type=2000 audit(1424381747.844:1): initialized
[    0.885551] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.887266] zbud: loaded
[    0.887451] VFS: Disk quotas dquot_6.5.2
[    0.887508] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.888184] fuse init (API version 7.22)
[    0.888290] msgmni has been set to 7882
[    0.888366] Key type big_key registered
[    0.888842] Key type asymmetric registered
[    0.888845] Asymmetric key parser 'x509' registered
[    0.888891] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.888931] io scheduler noop registered
[    0.888934] io scheduler deadline registered (default)
[    0.888970] io scheduler cfq registered
[    0.889301] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.889558] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.889801] pcieport 0000:00:1c.3: irq 42 for MSI/MSI-X
[    0.890044] pcieport 0000:00:1c.4: irq 43 for MSI/MSI-X
[    0.890153] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.890173] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.890239] vesafb: mode is 1280x800x32, linelength=5120, pages=0
[    0.890241] vesafb: scrolling: redraw
[    0.890244] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    0.890701] vesafb: framebuffer at 0xd0000000, mapped to 0xffffc90010780000, using 4032k, total 4032k
[    0.921951] Console: switching to colour frame buffer device 160x50
[    0.953093] fb0: VESA VGA frame buffer device
[    0.953130] intel_idle: does not run on family 6 model 15
[    0.953139] ipmi message handler version 39.2
[    0.956640] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.959322] ACPI: AC Adapter [ACAD] (on-line)
[    0.959426] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.959452] ACPI: Lid Switch [LID0]
[    0.959500] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.959505] ACPI: Power Button [PWRB]
[    0.959550] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.959554] ACPI: Sleep Button [SLPB]
[    0.959616] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.959620] ACPI: Power Button [PWRF]
[    0.962194] Monitor-Mwait will be used to enter C-1 state
[    0.962212] Monitor-Mwait will be used to enter C-2 state
[    0.962228] Monitor-Mwait will be used to enter C-3 state
[    0.962240] tsc: Marking TSC unstable due to TSC halts in idle
[    0.962256] ACPI: acpi_idle registered with cpuidle
[    0.966870] GHES: HEST is not enabled!
[    0.966985] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.203520] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.203531] ACPI: Battery Slot [BAT1] (battery present)
[    1.203681] Linux agpgart interface v0.103
[    1.203777] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
[    1.203848] agpgart-intel 0000:00:00.0: detected gtt size: 524288K total, 262144K mappable
[    1.204444] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    1.204661] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    1.206816] brd: module loaded
[    1.207883] loop: module loaded
[    1.208077] ata_piix 0000:00:1f.1: version 2.13
[    1.209001] scsi0 : ata_piix
[    1.209127] scsi1 : ata_piix
[    1.209171] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[    1.209174] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[    1.209573] libphy: Fixed MDIO Bus: probed
[    1.209687] tun: Universal TUN/TAP device driver, 1.6
[    1.209689] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.209776] PPP generic driver version 2.4.2
[    1.209837] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.209848] ehci-pci: EHCI PCI platform driver
[    1.210056] ehci-pci 0000:00:1a.7: EHCI Host Controller
[    1.210065] ehci-pci 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    1.210084] ehci-pci 0000:00:1a.7: debug port 1
[    1.214016] ehci-pci 0000:00:1a.7: cache line size of 64 is not supported
[    1.214036] ehci-pci 0000:00:1a.7: irq 18, io mem 0xf8504800
[    1.224053] ehci-pci 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    1.224131] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.224136] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.224140] usb usb1: Product: EHCI Host Controller
[    1.224145] usb usb1: Manufacturer: Linux 3.13.0-45-generic ehci_hcd
[    1.224149] usb usb1: SerialNumber: 0000:00:1a.7
[    1.224347] hub 1-0:1.0: USB hub found
[    1.224357] hub 1-0:1.0: 4 ports detected
[    1.224706] ehci-pci 0000:00:1d.7: EHCI Host Controller
[    1.224717] ehci-pci 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    1.224732] ehci-pci 0000:00:1d.7: debug port 1
[    1.228635] ehci-pci 0000:00:1d.7: cache line size of 64 is not supported
[    1.228652] ehci-pci 0000:00:1d.7: irq 23, io mem 0xf8504c00
[    1.240105] ehci-pci 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.240177] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.240182] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.240186] usb usb2: Product: EHCI Host Controller
[    1.240191] usb usb2: Manufacturer: Linux 3.13.0-45-generic ehci_hcd
[    1.240195] usb usb2: SerialNumber: 0000:00:1d.7
[    1.240375] hub 2-0:1.0: USB hub found
[    1.240384] hub 2-0:1.0: 6 ports detected
[    1.240626] ehci-platform: EHCI generic platform driver
[    1.240637] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.240639] ohci-pci: OHCI PCI platform driver
[    1.240652] ohci-platform: OHCI generic platform driver
[    1.240660] uhci_hcd: USB Universal Host Controller Interface driver
[    1.240814] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    1.240824] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    1.240865] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001820
[    1.240922] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    1.240925] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.240927] usb usb3: Product: UHCI Host Controller
[    1.240930] usb usb3: Manufacturer: Linux 3.13.0-45-generic uhci_hcd
[    1.240932] usb usb3: SerialNumber: 0000:00:1a.0
[    1.241080] hub 3-0:1.0: USB hub found
[    1.241090] hub 3-0:1.0: 2 ports detected
[    1.241333] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    1.241340] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    1.241381] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001840
[    1.241435] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    1.241438] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.241441] usb usb4: Product: UHCI Host Controller
[    1.241443] usb usb4: Manufacturer: Linux 3.13.0-45-generic uhci_hcd
[    1.241446] usb usb4: SerialNumber: 0000:00:1a.1
[    1.241591] hub 4-0:1.0: USB hub found
[    1.241603] hub 4-0:1.0: 2 ports detected
[    1.241848] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.241855] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    1.241882] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001860
[    1.241938] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    1.241941] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.241944] usb usb5: Product: UHCI Host Controller
[    1.241947] usb usb5: Manufacturer: Linux 3.13.0-45-generic uhci_hcd
[    1.241949] usb usb5: SerialNumber: 0000:00:1d.0
[    1.242099] hub 5-0:1.0: USB hub found
[    1.242109] hub 5-0:1.0: 2 ports detected
[    1.242351] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.242358] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    1.242396] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001880
[    1.242453] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
[    1.242456] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.242459] usb usb6: Product: UHCI Host Controller
[    1.242461] usb usb6: Manufacturer: Linux 3.13.0-45-generic uhci_hcd
[    1.242464] usb usb6: SerialNumber: 0000:00:1d.1
[    1.242603] hub 6-0:1.0: USB hub found
[    1.242612] hub 6-0:1.0: 2 ports detected
[    1.242858] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.242866] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    1.242896] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018a0
[    1.242952] usb usb7: New USB device found, idVendor=1d6b, idProduct=0001
[    1.242955] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.242957] usb usb7: Product: UHCI Host Controller
[    1.242960] usb usb7: Manufacturer: Linux 3.13.0-45-generic uhci_hcd
[    1.242962] usb usb7: SerialNumber: 0000:00:1d.2
[    1.243097] hub 7-0:1.0: USB hub found
[    1.243106] hub 7-0:1.0: 2 ports detected
[    1.243287] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.263992] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.264000] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.264221] mousedev: PS/2 mouse device common for all mice
[    1.266862] rtc_cmos 00:06: RTC can wake from S4
[    1.267043] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    1.267079] rtc_cmos 00:06: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.267172] device-mapper: uevent: version 1.0.3
[    1.267283] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
[    1.267292] ledtrig-cpu: registered to indicate activity on CPUs
[    1.267429] TCP: cubic registered
[    1.267542] NET: Registered protocol family 10
[    1.267760] NET: Registered protocol family 17
[    1.267772] Key type dns_resolver registered
[    1.268142] Loading compiled-in X.509 certificates
[    1.269503] Loaded X.509 cert 'Magrathea: Glacier signing key: 34992139f3da40b620bd5517597ba85af5797c9a'
[    1.269521] registered taskstats version 1
[    1.272613] Key type trusted registered
[    1.275167] Key type encrypted registered
[    1.277779] AppArmor: AppArmor sha1 policy hashing enabled
[    1.277783] IMA: No TPM chip found, activating TPM-bypass!
[    1.278521] regulator-dummy: disabling
[    1.278605]   Magic number: 3:660:601
[    1.278762] rtc_cmos 00:06: setting system clock to 2015-02-19 21:35:49 UTC (1424381749)
[    1.279327] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.279329] EDD information not available.
[    1.279380] PM: Hibernation image not present or could not be loaded.
[    1.299344] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.380602] ata1.00: ATAPI: MATSHITA DVD+/-RW UJ-875S, D200, max UDMA/33
[    1.396486] ata1.00: configured for UDMA/33
[    1.399138] scsi 0:0:0:0: CD-ROM            MATSHITA DVD+-RW UJ-875S  D200 PQ: 0 ANSI: 5
[    1.401569] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda caddy
[    1.401574] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.401785] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.401947] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.404032] Freeing unused kernel memory: 1336K (ffffffff81d20000 - ffffffff81e6e000)
[    1.404049] Write protecting the kernel read-only data: 12288k
[    1.407119] Freeing unused kernel memory: 796K (ffff880001739000 - ffff880001800000)
[    1.409774] Freeing unused kernel memory: 688K (ffff880001b54000 - ffff880001c00000)
[    1.437369] systemd-udevd[121]: starting version 204
[    1.490329] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.490344] r8169 0000:07:00.0: can't disable ASPM; OS doesn't have ASPM control
[    1.490683] r8169 0000:07:00.0: irq 44 for MSI/MSI-X
[    1.490912] r8169 0000:07:00.0 eth0: RTL8168c/8111c at 0xffffc90000676000, 00:21:70:cf:f0:dd, XID 1c4000c0 IRQ 44
[    1.490916] r8169 0000:07:00.0 eth0: jumbo features [frames: 6128 bytes, tx checksumming: ko]
[    1.495064] sdhci: Secure Digital Host Controller Interface driver
[    1.495067] sdhci: Copyright(c) Pierre Ossman
[    1.499318] sdhci-pci 0000:08:05.2: SDHCI controller found [1217:7120] (rev 2)
[    1.499518] sdhci-pci 0000:08:05.2: dummy supplies not allowed
[    1.499521] mmc0: no vqmmc regulator found
[    1.499524] sdhci-pci 0000:08:05.2: dummy supplies not allowed
[    1.499525] mmc0: no vmmc regulator found
[    1.499634] mmc0: SDHCI controller on PCI [0000:08:05.2] using DMA
[    1.506832] ahci 0000:00:1f.2: version 3.0
[    1.507070] ahci 0000:00:1f.2: irq 45 for MSI/MSI-X
[    1.507148] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
[    1.507152] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ccc 
[    1.512953] scsi2 : ahci
[    1.514515] scsi3 : ahci
[    1.514845] scsi4 : ahci
[    1.514902] ata3: SATA max UDMA/133 abar m2048@0xf8504000 port 0xf8504100 irq 45
[    1.514906] ata4: SATA max UDMA/133 abar m2048@0xf8504000 port 0xf8504180 irq 45
[    1.514910] ata5: SATA max UDMA/133 abar m2048@0xf8504000 port 0xf8504200 irq 45
[    1.556111] firewire_ohci 0000:08:05.0: added OHCI v1.10 device as card 0, 8 IR + 8 IT contexts, quirks 0x10
[    1.832060] ata4: SATA link down (SStatus 0 SControl 300)
[    1.832098] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.832947] ata5: SATA link down (SStatus 0 SControl 300)
[    1.833457] ata3.00: unexpected _GTF length (8)
[    1.833594] ata3.00: ATA-8: WDC WD3200BEVT-60A23T0, 02.01A02, max UDMA/100
[    1.833599] ata3.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.835001] ata3.00: unexpected _GTF length (8)
[    1.835132] ata3.00: configured for UDMA/100
[    1.835386] scsi 2:0:0:0: Direct-Access     ATA      WDC WD3200BEVT-6 02.0 PQ: 0 ANSI: 5
[    1.835679] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    1.835686] sd 2:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.835779] sd 2:0:0:0: [sda] Write Protect is off
[    1.835783] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.835821] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.871058]  sda: sda1 sda2 < sda5 >
[    1.871582] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.997557] random: lvm urandom read with 40 bits of entropy available
[    2.035365] bio: create slab <bio-1> at 1
[    2.056274] firewire_core 0000:08:05.0: created device fw0: GUID 0000c010a000b000, S400
[    2.961832] input: ALPS PS/2 Device as /devices/platform/i8042/serio1/input/input7
[    3.005421] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input6
[    4.465511] EXT4-fs (dm-0): mounted filesystem with ordered data mode. Opts: (null)
[    4.968590] random: nonblocking pool is initialized
[    8.076087] Adding 4182012k swap on /dev/mapper/ubuntu--vg-swap_1.  Priority:-1 extents:1 across:4182012k FS
[    8.743968] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
[    8.984960] EXT4-fs (sda1): mounting ext2 file system using the ext4 subsystem
[    9.027864] EXT4-fs (sda1): mounted filesystem without journal. Opts: (null)
[    9.631079] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   10.643860] systemd-udevd[365]: starting version 204
[   12.405529] lp: driver loaded but no devices found
[   12.529432] ppdev: user-space parallel port driver
[   15.751923] init: avahi-cups-reload main process (450) terminated with status 1
[   16.355130] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   16.671370] wmi: Mapper loaded
[   16.789116] ACPI Warning: 0x0000000000001028-0x000000000000102f SystemIO conflicts with Region \PMIO 1 (20131115/utaddress-251)
[   16.789126] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   16.789131] ACPI Warning: 0x00000000000011b0-0x00000000000011bf SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
[   16.789136] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   16.789138] ACPI Warning: 0x0000000000001180-0x00000000000011af SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
[   16.789143] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   16.789145] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   17.043511] Bluetooth: Core ver 2.17
[   17.043566] NET: Registered protocol family 31
[   17.043569] Bluetooth: HCI device and connection manager initialized
[   17.043582] Bluetooth: HCI socket layer initialized
[   17.043586] Bluetooth: L2CAP socket layer initialized
[   17.043592] Bluetooth: SCO socket layer initialized
[   17.078013] cfg80211: Calling CRDA to update world regulatory domain
[   17.079823] [drm] Initialized drm 1.1.0 20060810
[   17.127296] lib80211: common routines for IEEE802.11 drivers
[   17.127301] lib80211_crypt: registered algorithm 'NULL'
[   17.444626] type=1400 audit(1424381765.663:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=543 comm="apparmor_parser"
[   17.444636] type=1400 audit(1424381765.663:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=543 comm="apparmor_parser"
[   17.444643] type=1400 audit(1424381765.663:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=543 comm="apparmor_parser"
[   17.444655] type=1400 audit(1424381765.663:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=508 comm="apparmor_parser"
[   17.444665] type=1400 audit(1424381765.663:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=508 comm="apparmor_parser"
[   17.444672] type=1400 audit(1424381765.663:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=508 comm="apparmor_parser"
[   17.445218] type=1400 audit(1424381765.663:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=543 comm="apparmor_parser"
[   17.445225] type=1400 audit(1424381765.663:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=543 comm="apparmor_parser"
[   17.445255] type=1400 audit(1424381765.663:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=508 comm="apparmor_parser"
[   17.445262] type=1400 audit(1424381765.663:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=508 comm="apparmor_parser"
[   17.501910] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   17.501914] Bluetooth: BNEP filters: protocol multicast
[   17.501926] Bluetooth: BNEP socket layer initialized
[   17.600677] [drm] Memory usable by graphics device = 512M
[   17.600683] checking generic (d0000000 3f0000) vs hw (d0000000 10000000)
[   17.600686] fb: conflicting fb hw usage inteldrmfb vs VESA VGA - removing generic driver
[   17.600745] Console: switching to colour dummy device 80x25
[   17.640416] Bluetooth: RFCOMM TTY layer initialized
[   17.640434] Bluetooth: RFCOMM socket layer initialized
[   17.640447] Bluetooth: RFCOMM ver 1.11
[   17.664332] i915 0000:00:02.0: irq 46 for MSI/MSI-X
[   17.664351] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[   17.664353] [drm] Driver supports precise vblank timestamp query.
[   17.664440] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   17.716868] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   17.754648] [drm] initialized overlay support
[   17.902136] fbcon: inteldrmfb (fb0) is primary device
[   18.168193] wl: module license 'MIXED/Proprietary' taints kernel.
[   18.168194] Disabling lock debugging due to kernel taint
[   18.173676] wl: module verification failed: signature and/or  required key missing - tainting kernel
[   18.203007] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[   18.238813] lib80211_crypt: registered algorithm 'TKIP'
[   18.573059] wlan0: Broadcom BCM4315 802.11 Hybrid Wireless Controller 6.30.223.141 (r415941)
[   18.574398] input: Dell WMI hotkeys as /devices/virtual/input/input8
[   18.593215] Console: switching to colour frame buffer device 160x50
[   18.596880] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   18.596882] i915 0000:00:02.0: registered panic notifier
[   18.628733] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   18.644299] acpi device:08: registered as cooling_device2
[   18.644402] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input9
[   18.645548] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   18.645882] snd_hda_intel 0000:00:1b.0: irq 47 for MSI/MSI-X
[   18.705209] autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[   18.705210]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   18.705212]    hp_outs=1 (0x15/0x0/0x0/0x0/0x0)
[   18.705212]    mono: mono_out=0x0
[   18.705213]    inputs:
[   18.705215]      Mic=0x18
[   18.705216] realtek: No valid SSID, checking pincfg 0x4015822d for NID 0x1d
[   18.705217] realtek: Enabling init ASM_ID=0x822d CODEC_ID=10ec0268
[   18.722196] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   18.723203] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   19.025712] ip_tables: (C) 2000-2006 Netfilter Core Team
[   19.703178] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   19.896308] cfg80211: World regulatory domain updated:
[   19.896312] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   19.896316] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.896318] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.896321] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   19.896324] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.896326] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.641245] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   20.795306] init: failsafe main process (582) killed by TERM signal
[   26.487887] audit_printk_skb: 15 callbacks suppressed
[   26.487891] type=1400 audit(1424381774.704:17): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cups-browsed" pid=902 comm="apparmor_parser"
[   29.760160] type=1400 audit(1424381777.980:18): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=1010 comm="apparmor_parser"
[   29.760172] type=1400 audit(1424381777.980:19): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1010 comm="apparmor_parser"
[   29.760180] type=1400 audit(1424381777.980:20): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1010 comm="apparmor_parser"
[   29.760770] type=1400 audit(1424381777.980:21): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1010 comm="apparmor_parser"
[   29.760777] type=1400 audit(1424381777.980:22): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1010 comm="apparmor_parser"
[   29.761074] type=1400 audit(1424381777.980:23): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1010 comm="apparmor_parser"
[   30.014921] type=1400 audit(1424381778.232:24): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=1009 comm="apparmor_parser"
[   30.014933] type=1400 audit(1424381778.232:25): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=1009 comm="apparmor_parser"
[   30.015286] type=1400 audit(1424381778.232:26): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="chromium" pid=1009 comm="apparmor_parser"
[   30.133298] r8169 0000:07:00.0 eth0: link down
[   30.133387] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   30.133792] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   33.035881] vboxdrv: Found 2 processor cores.
[   33.037032] vboxdrv: fAsync=0 offMin=0x1c2 offMax=0x77d
[   33.037168] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   33.037170] vboxdrv: Successfully loaded version 4.3.20 (interface 0x001a0008).
[   33.586465] vboxpci: IOMMU not found (not registered)
[   33.651625] nf_conntrack: automatic helper assignment is deprecated and it will be removed soon. Use the iptables CT target to attach helpers instead.
[   34.060507] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:a8:bb:cf:21:a7:66:08:00 SRC=192.168.1.152 DST=224.0.0.1 LEN=44 TOS=0x00 PREC=0x00 TTL=1 ID=62789 PROTO=UDP SPT=51572 DPT=8612 LEN=24 
[   35.702175] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:28:cf:e9:57:7e:79:08:00 SRC=192.168.1.3 DST=224.0.0.1 LEN=44 TOS=0x00 PREC=0x00 TTL=1 ID=56597 PROTO=UDP SPT=62169 DPT=8612 LEN=24 
[   40.409518] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:60:c5:47:0c:fe:2a:08:00 SRC=192.168.1.156 DST=224.0.0.1 LEN=44 TOS=0x00 PREC=0x00 TTL=1 ID=20980 PROTO=UDP SPT=50805 DPT=8612 LEN=24 
[   40.411229] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:f8:1e:df:ee:7f:df:08:00 SRC=192.168.1.7 DST=224.0.0.1 LEN=44 TOS=0x00 PREC=0x00 TTL=1 ID=58202 PROTO=UDP SPT=53251 DPT=8612 LEN=24 
[   40.820398] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:88:65:37:cf:d0:08:00 SRC=192.168.1.119 DST=224.0.0.1 LEN=44 TOS=0x00 PREC=0x00 TTL=1 ID=41557 PROTO=UDP SPT=53723 DPT=8612 LEN=24 
[   41.024200] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:90:27:e4:f6:01:e4:08:00 SRC=192.168.1.73 DST=224.0.0.1 LEN=44 TOS=0x00 PREC=0x00 TTL=1 ID=33328 PROTO=UDP SPT=57025 DPT=8612 LEN=24 
[   41.027048] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:a8:bb:cf:21:a7:66:08:00 SRC=192.168.1.152 DST=224.0.0.1 LEN=44 TOS=0x00 PREC=0x00 TTL=1 ID=15141 PROTO=UDP SPT=51732 DPT=8612 LEN=24 
[   41.426820] init: plymouth-upstart-bridge main process ended, respawning
[   41.449307] init: plymouth-upstart-bridge main process ended, respawning
[   47.576176] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:60:c5:47:0c:fe:2a:08:00 SRC=192.168.1.156 DST=224.0.0.1 LEN=44 TOS=0x00 PREC=0x00 TTL=1 ID=58640 PROTO=UDP SPT=55391 DPT=8612 LEN=24 
[   47.578717] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:f8:1e:df:ee:7f:df:08:00 SRC=192.168.1.7 DST=224.0.0.1 LEN=44 TOS=0x00 PREC=0x00 TTL=1 ID=29869 PROTO=UDP SPT=53286 DPT=8612 LEN=24 
[   47.784994] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:88:65:37:cf:d0:08:00 SRC=192.168.1.119 DST=224.0.0.1 LEN=44 TOS=0x00 PREC=0x00 TTL=1 ID=57143 PROTO=UDP SPT=62300 DPT=8612 LEN=24 
[   54.743874] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:60:c5:47:0c:fe:2a:08:00 SRC=192.168.1.156 DST=224.0.0.1 LEN=44 TOS=0x00 PREC=0x00 TTL=1 ID=12057 PROTO=UDP SPT=60781 DPT=8612 LEN=24 
[   75.829939] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:f8:1e:df:ee:7f:df:08:00 SRC=192.168.1.7 DST=224.0.0.1 LEN=44 TOS=0x00 PREC=0x00 TTL=1 ID=40024 PROTO=UDP SPT=61248 DPT=8612 LEN=24 
[   97.117242] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:f8:1e:df:ee:7f:df:08:00 SRC=192.168.1.7 DST=224.0.0.1 LEN=44 TOS=0x00 PREC=0x00 TTL=1 ID=44619 PROTO=UDP SPT=61530 DPT=8612 LEN=24 
[  118.408995] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:f8:1e:df:ee:7f:df:08:00 SRC=192.168.1.7 DST=224.0.0.1 LEN=44 TOS=0x00 PREC=0x00 TTL=1 ID=21208 PROTO=UDP SPT=60423 DPT=8612 LEN=24 
[  134.787936] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:28:cf:e9:57:7e:79:08:00 SRC=192.168.1.3 DST=224.0.0.1 LEN=44 TOS=0x00 PREC=0x00 TTL=1 ID=43364 PROTO=UDP SPT=56847 DPT=8612 LEN=24 
[  154.436624] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:90:27:e4:f6:01:e4:08:00 SRC=192.168.1.73 DST=224.0.0.1 LEN=44 TOS=0x00 PREC=0x00 TTL=1 ID=20120 PROTO=UDP SPT=58616 DPT=8612 LEN=24 
[  174.908274] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:f8:1e:df:ee:7f:df:08:00 SRC=192.168.1.7 DST=224.0.0.1 LEN=44 TOS=0x00 PREC=0x00 TTL=1 ID=20344 PROTO=UDP SPT=53918 DPT=8612 LEN=24 
[    0.317284] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.318084] Switched to clocksource hpet
[    0.325220] AppArmor: AppArmor Filesystem Enabled
[    0.325268] pnp: PnP ACPI init
[    0.325290] ACPI: bus type PNP registered
[    0.325537] system 00:00: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.325541] system 00:00: [mem 0xfed14000-0xfed17fff] has been reserved
[    0.325544] system 00:00: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.325547] system 00:00: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.325551] system 00:00: [mem 0xe0000000-0xefffffff] has been reserved
[    0.325554] system 00:00: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.325557] system 00:00: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.325560] system 00:00: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.325565] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.325796] pnp 00:01: [dma 4]
[    0.325837] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.325880] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
[    0.326011] system 00:03: [mem 0xfed00000-0xfed003ff] has been reserved
[    0.326015] system 00:03: Plug and Play ACPI device, IDs PNP0103 PNP0c01 (active)
[    0.326076] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.326153] system 00:05: [io  0x0680-0x069f] has been reserved
[    0.326157] system 00:05: [io  0x0800-0x080f] has been reserved
[    0.326161] system 00:05: [io  0x1000-0x107f] could not be reserved
[    0.326164] system 00:05: [io  0x1180-0x11bf] has been reserved
[    0.326167] system 00:05: [io  0xfe00] has been reserved
[    0.326173] system 00:05: [io  0xff00-0xff7f] has been reserved
[    0.326177] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.326228] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.356087] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.356148] pnp 00:08: Plug and Play ACPI device, IDs SYN0705 SYN0700 SYN0002 PNP0f13 (active)
[    0.356173] pnp: PnP ACPI: found 9 devices
[    0.356175] ACPI: bus type PNP unregistered
[    0.363509] pci 0000:00:1c.4: bridge window [mem 0x00100000-0x001fffff] to [bus 07] add_size 400000
[    0.363528] pci 0000:00:1f.0: BAR 13: [io  0x1000-0x107f] has bogus alignment
[    0.363533] pci 0000:00:1c.4: res[14]=[mem 0x00100000-0x001fffff] get_res_add_size add_size 400000
[    0.363540] pci 0000:00:1c.4: BAR 14: assigned [mem 0xc0000000-0xc04fffff]
[    0.363544] pci 0000:00:1f.3: BAR 0: assigned [mem 0xc0500000-0xc05000ff]
[    0.363552] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.363556] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.363564] pci 0000:00:1c.0:   bridge window [mem 0xc4000000-0xc7ffffff]
[    0.363570] pci 0000:00:1c.0:   bridge window [mem 0xcc000000-0xcdffffff 64bit pref]
[    0.363579] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    0.363583] pci 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
[    0.363591] pci 0000:00:1c.1:   bridge window [mem 0xf0000000-0xf3ffffff]
[    0.363597] pci 0000:00:1c.1:   bridge window [mem 0xfa000000-0xfbffffff 64bit pref]
[    0.363606] pci 0000:00:1c.3: PCI bridge to [bus 06]
[    0.363610] pci 0000:00:1c.3:   bridge window [io  0x4000-0x4fff]
[    0.363617] pci 0000:00:1c.3:   bridge window [mem 0xf4000000-0xf7ffffff]
[    0.363623] pci 0000:00:1c.3:   bridge window [mem 0xfc000000-0xfdffffff 64bit pref]
[    0.363633] pci 0000:07:00.0: BAR 6: assigned [mem 0xf8620000-0xf862ffff pref]
[    0.363636] pci 0000:00:1c.4: PCI bridge to [bus 07]
[    0.363640] pci 0000:00:1c.4:   bridge window [io  0x5000-0x5fff]
[    0.363648] pci 0000:00:1c.4:   bridge window [mem 0xc0000000-0xc04fffff]
[    0.363654] pci 0000:00:1c.4:   bridge window [mem 0xf8600000-0xf86fffff 64bit pref]
[    0.363663] pci 0000:00:1e.0: PCI bridge to [bus 08]
[    0.363670] pci 0000:00:1e.0:   bridge window [mem 0xf8200000-0xf82fffff]
[    0.363683] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.363686] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.363689] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.363692] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.363695] pci_bus 0000:00: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.363697] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.363700] pci_bus 0000:00: resource 10 [mem 0xc0000000-0xdfffffff]
[    0.363703] pci_bus 0000:00: resource 11 [mem 0xf0000000-0xfebfffff]
[    0.363706] pci_bus 0000:02: resource 0 [io  0x2000-0x2fff]
[    0.363709] pci_bus 0000:02: resource 1 [mem 0xc4000000-0xc7ffffff]
[    0.363712] pci_bus 0000:02: resource 2 [mem 0xcc000000-0xcdffffff 64bit pref]
[    0.363715] pci_bus 0000:03: resource 0 [io  0x3000-0x3fff]
[    0.363718] pci_bus 0000:03: resource 1 [mem 0xf0000000-0xf3ffffff]
[    0.363721] pci_bus 0000:03: resource 2 [mem 0xfa000000-0xfbffffff 64bit pref]
[    0.363723] pci_bus 0000:06: resource 0 [io  0x4000-0x4fff]
[    0.363726] pci_bus 0000:06: resource 1 [mem 0xf4000000-0xf7ffffff]
[    0.363729] pci_bus 0000:06: resource 2 [mem 0xfc000000-0xfdffffff 64bit pref]
[    0.363732] pci_bus 0000:07: resource 0 [io  0x5000-0x5fff]
[    0.363735] pci_bus 0000:07: resource 1 [mem 0xc0000000-0xc04fffff]
[    0.363738] pci_bus 0000:07: resource 2 [mem 0xf8600000-0xf86fffff 64bit pref]
[    0.363741] pci_bus 0000:08: resource 1 [mem 0xf8200000-0xf82fffff]
[    0.363744] pci_bus 0000:08: resource 4 [io  0x0000-0x0cf7]
[    0.363746] pci_bus 0000:08: resource 5 [io  0x0d00-0xffff]
[    0.363749] pci_bus 0000:08: resource 6 [mem 0x000a0000-0x000bffff]
[    0.363752] pci_bus 0000:08: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.363755] pci_bus 0000:08: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.363757] pci_bus 0000:08: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.363760] pci_bus 0000:08: resource 10 [mem 0xc0000000-0xdfffffff]
[    0.363763] pci_bus 0000:08: resource 11 [mem 0xf0000000-0xfebfffff]
[    0.363808] NET: Registered protocol family 2
[    0.364090] TCP established hash table entries: 32768 (order: 6, 262144 bytes)
[    0.364263] TCP bind hash table entries: 32768 (order: 7, 524288 bytes)
[    0.364487] TCP: Hash tables configured (established 32768 bind 32768)
[    0.364544] TCP: reno registered
[    0.364555] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.364594] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.364691] NET: Registered protocol family 1
[    0.364712] pci 0000:00:02.0: Video device with shadowed ROM
[    0.366982] PCI: CLS 64 bytes, default 64
[    0.367079] Trying to unpack rootfs image as initramfs...
[    0.844829] Freeing initrd memory: 19540K (ffff8800359c6000 - ffff880036cdb000)
[    0.844839] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.844843] software IO TLB [mem 0xbb6d0000-0xbf6d0000] (64MB) mapped at [ffff8800bb6d0000-ffff8800bf6cffff]
[    0.844949] Simple Boot Flag at 0x36 set to 0x1
[    0.845126] microcode: CPU0 sig=0x6fd, pf=0x80, revision=0xa1
[    0.845139] microcode: CPU1 sig=0x6fd, pf=0x80, revision=0xa1
[    0.845226] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.845229] Scanning for low memory corruption every 60 seconds
[    0.845520] Initialise system trusted keyring
[    0.845587] audit: initializing netlink socket (disabled)
[    0.845606] type=2000 audit(1424381747.844:1): initialized
[    0.885551] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.887266] zbud: loaded
[    0.887451] VFS: Disk quotas dquot_6.5.2
[    0.887508] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.888184] fuse init (API version 7.22)
[    0.888290] msgmni has been set to 7882
[    0.888366] Key type big_key registered
[    0.888842] Key type asymmetric registered
[    0.888845] Asymmetric key parser 'x509' registered
[    0.888891] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.888931] io scheduler noop registered
[    0.888934] io scheduler deadline registered (default)
[    0.888970] io scheduler cfq registered
[    0.889301] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.889558] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.889801] pcieport 0000:00:1c.3: irq 42 for MSI/MSI-X
[    0.890044] pcieport 0000:00:1c.4: irq 43 for MSI/MSI-X
[    0.890153] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.890173] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.890239] vesafb: mode is 1280x800x32, linelength=5120, pages=0
[    0.890241] vesafb: scrolling: redraw
[    0.890244] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    0.890701] vesafb: framebuffer at 0xd0000000, mapped to 0xffffc90010780000, using 4032k, total 4032k
[    0.921951] Console: switching to colour frame buffer device 160x50
[    0.953093] fb0: VESA VGA frame buffer device
[    0.953130] intel_idle: does not run on family 6 model 15
[    0.953139] ipmi message handler version 39.2
[    0.956640] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.959322] ACPI: AC Adapter [ACAD] (on-line)
[    0.959426] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.959452] ACPI: Lid Switch [LID0]
[    0.959500] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.959505] ACPI: Power Button [PWRB]
[    0.959550] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.959554] ACPI: Sleep Button [SLPB]
[    0.959616] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.959620] ACPI: Power Button [PWRF]
[    0.962194] Monitor-Mwait will be used to enter C-1 state
[    0.962212] Monitor-Mwait will be used to enter C-2 state
[    0.962228] Monitor-Mwait will be used to enter C-3 state
[    0.962240] tsc: Marking TSC unstable due to TSC halts in idle
[    0.962256] ACPI: acpi_idle registered with cpuidle
[    0.966870] GHES: HEST is not enabled!
[    0.966985] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.203520] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.203531] ACPI: Battery Slot [BAT1] (battery present)
[    1.203681] Linux agpgart interface v0.103
[    1.203777] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
[    1.203848] agpgart-intel 0000:00:00.0: detected gtt size: 524288K total, 262144K mappable
[    1.204444] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    1.204661] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    1.206816] brd: module loaded
[    1.207883] loop: module loaded
[    1.208077] ata_piix 0000:00:1f.1: version 2.13
[    1.209001] scsi0 : ata_piix
[    1.209127] scsi1 : ata_piix
[    1.209171] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[    1.209174] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[    1.209573] libphy: Fixed MDIO Bus: probed
[    1.209687] tun: Universal TUN/TAP device driver, 1.6
[    1.209689] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.209776] PPP generic driver version 2.4.2
[    1.209837] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.209848] ehci-pci: EHCI PCI platform driver
[    1.210056] ehci-pci 0000:00:1a.7: EHCI Host Controller
[    1.210065] ehci-pci 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    1.210084] ehci-pci 0000:00:1a.7: debug port 1
[    1.214016] ehci-pci 0000:00:1a.7: cache line size of 64 is not supported
[    1.214036] ehci-pci 0000:00:1a.7: irq 18, io mem 0xf8504800
[    1.224053] ehci-pci 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    1.224131] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.224136] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.224140] usb usb1: Product: EHCI Host Controller
[    1.224145] usb usb1: Manufacturer: Linux 3.13.0-45-generic ehci_hcd
[    1.224149] usb usb1: SerialNumber: 0000:00:1a.7
[    1.224347] hub 1-0:1.0: USB hub found
[    1.224357] hub 1-0:1.0: 4 ports detected
[    1.224706] ehci-pci 0000:00:1d.7: EHCI Host Controller
[    1.224717] ehci-pci 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    1.224732] ehci-pci 0000:00:1d.7: debug port 1
[    1.228635] ehci-pci 0000:00:1d.7: cache line size of 64 is not supported
[    1.228652] ehci-pci 0000:00:1d.7: irq 23, io mem 0xf8504c00
[    1.240105] ehci-pci 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.240177] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.240182] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.240186] usb usb2: Product: EHCI Host Controller
[    1.240191] usb usb2: Manufacturer: Linux 3.13.0-45-generic ehci_hcd
[    1.240195] usb usb2: SerialNumber: 0000:00:1d.7
[    1.240375] hub 2-0:1.0: USB hub found
[    1.240384] hub 2-0:1.0: 6 ports detected
[    1.240626] ehci-platform: EHCI generic platform driver
[    1.240637] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.240639] ohci-pci: OHCI PCI platform driver
[    1.240652] ohci-platform: OHCI generic platform driver
[    1.240660] uhci_hcd: USB Universal Host Controller Interface driver
[    1.240814] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    1.240824] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    1.240865] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001820
[    1.240922] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    1.240925] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.240927] usb usb3: Product: UHCI Host Controller
[    1.240930] usb usb3: Manufacturer: Linux 3.13.0-45-generic uhci_hcd
[    1.240932] usb usb3: SerialNumber: 0000:00:1a.0
[    1.241080] hub 3-0:1.0: USB hub found
[    1.241090] hub 3-0:1.0: 2 ports detected
[    1.241333] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    1.241340] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    1.241381] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001840
[    1.241435] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    1.241438] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.241441] usb usb4: Product: UHCI Host Controller
[    1.241443] usb usb4: Manufacturer: Linux 3.13.0-45-generic uhci_hcd
[    1.241446] usb usb4: SerialNumber: 0000:00:1a.1
[    1.241591] hub 4-0:1.0: USB hub found
[    1.241603] hub 4-0:1.0: 2 ports detected
[    1.241848] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.241855] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    1.241882] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001860
[    1.241938] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    1.241941] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.241944] usb usb5: Product: UHCI Host Controller
[    1.241947] usb usb5: Manufacturer: Linux 3.13.0-45-generic uhci_hcd
[    1.241949] usb usb5: SerialNumber: 0000:00:1d.0
[    1.242099] hub 5-0:1.0: USB hub found
[    1.242109] hub 5-0:1.0: 2 ports detected
[    1.242351] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.242358] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    1.242396] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001880
[    1.242453] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
[    1.242456] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.242459] usb usb6: Product: UHCI Host Controller
[    1.242461] usb usb6: Manufacturer: Linux 3.13.0-45-generic uhci_hcd
[    1.242464] usb usb6: SerialNumber: 0000:00:1d.1
[    1.242603] hub 6-0:1.0: USB hub found
[    1.242612] hub 6-0:1.0: 2 ports detected
[    1.242858] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.242866] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    1.242896] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018a0
[    1.242952] usb usb7: New USB device found, idVendor=1d6b, idProduct=0001
[    1.242955] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.242957] usb usb7: Product: UHCI Host Controller
[    1.242960] usb usb7: Manufacturer: Linux 3.13.0-45-generic uhci_hcd
[    1.242962] usb usb7: SerialNumber: 0000:00:1d.2
[    1.243097] hub 7-0:1.0: USB hub found
[    1.243106] hub 7-0:1.0: 2 ports detected
[    1.243287] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.263992] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.264000] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.264221] mousedev: PS/2 mouse device common for all mice
[    1.266862] rtc_cmos 00:06: RTC can wake from S4
[    1.267043] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    1.267079] rtc_cmos 00:06: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.267172] device-mapper: uevent: version 1.0.3
[    1.267283] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
[    1.267292] ledtrig-cpu: registered to indicate activity on CPUs
[    1.267429] TCP: cubic registered
[    1.267542] NET: Registered protocol family 10
[    1.267760] NET: Registered protocol family 17
[    1.267772] Key type dns_resolver registered
[    1.268142] Loading compiled-in X.509 certificates
[    1.269503] Loaded X.509 cert 'Magrathea: Glacier signing key: 34992139f3da40b620bd5517597ba85af5797c9a'
[    1.269521] registered taskstats version 1
[    1.272613] Key type trusted registered
[    1.275167] Key type encrypted registered
[    1.277779] AppArmor: AppArmor sha1 policy hashing enabled
[    1.277783] IMA: No TPM chip found, activating TPM-bypass!
[    1.278521] regulator-dummy: disabling
[    1.278605]   Magic number: 3:660:601
[    1.278762] rtc_cmos 00:06: setting system clock to 2015-02-19 21:35:49 UTC (1424381749)
[    1.279327] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.279329] EDD information not available.
[    1.279380] PM: Hibernation image not present or could not be loaded.
[    1.299344] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.380602] ata1.00: ATAPI: MATSHITA DVD+/-RW UJ-875S, D200, max UDMA/33
[    1.396486] ata1.00: configured for UDMA/33
[    1.399138] scsi 0:0:0:0: CD-ROM            MATSHITA DVD+-RW UJ-875S  D200 PQ: 0 ANSI: 5
[    1.401569] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda caddy
[    1.401574] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.401785] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.401947] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.404032] Freeing unused kernel memory: 1336K (ffffffff81d20000 - ffffffff81e6e000)
[    1.404049] Write protecting the kernel read-only data: 12288k
[    1.407119] Freeing unused kernel memory: 796K (ffff880001739000 - ffff880001800000)
[    1.409774] Freeing unused kernel memory: 688K (ffff880001b54000 - ffff880001c00000)
[    1.437369] systemd-udevd[121]: starting version 204
[    1.490329] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.490344] r8169 0000:07:00.0: can't disable ASPM; OS doesn't have ASPM control
[    1.490683] r8169 0000:07:00.0: irq 44 for MSI/MSI-X
[    1.490912] r8169 0000:07:00.0 eth0: RTL8168c/8111c at 0xffffc90000676000, 00:21:70:cf:f0:dd, XID 1c4000c0 IRQ 44
[    1.490916] r8169 0000:07:00.0 eth0: jumbo features [frames: 6128 bytes, tx checksumming: ko]
[    1.495064] sdhci: Secure Digital Host Controller Interface driver
[    1.495067] sdhci: Copyright(c) Pierre Ossman
[    1.499318] sdhci-pci 0000:08:05.2: SDHCI controller found [1217:7120] (rev 2)
[    1.499518] sdhci-pci 0000:08:05.2: dummy supplies not allowed
[    1.499521] mmc0: no vqmmc regulator found
[    1.499524] sdhci-pci 0000:08:05.2: dummy supplies not allowed
[    1.499525] mmc0: no vmmc regulator found
[    1.499634] mmc0: SDHCI controller on PCI [0000:08:05.2] using DMA
[    1.506832] ahci 0000:00:1f.2: version 3.0
[    1.507070] ahci 0000:00:1f.2: irq 45 for MSI/MSI-X
[    1.507148] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
[    1.507152] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ccc 
[    1.512953] scsi2 : ahci
[    1.514515] scsi3 : ahci
[    1.514845] scsi4 : ahci
[    1.514902] ata3: SATA max UDMA/133 abar m2048@0xf8504000 port 0xf8504100 irq 45
[    1.514906] ata4: SATA max UDMA/133 abar m2048@0xf8504000 port 0xf8504180 irq 45
[    1.514910] ata5: SATA max UDMA/133 abar m2048@0xf8504000 port 0xf8504200 irq 45
[    1.556111] firewire_ohci 0000:08:05.0: added OHCI v1.10 device as card 0, 8 IR + 8 IT contexts, quirks 0x10
[    1.832060] ata4: SATA link down (SStatus 0 SControl 300)
[    1.832098] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.832947] ata5: SATA link down (SStatus 0 SControl 300)
[    1.833457] ata3.00: unexpected _GTF length (8)
[    1.833594] ata3.00: ATA-8: WDC WD3200BEVT-60A23T0, 02.01A02, max UDMA/100
[    1.833599] ata3.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.835001] ata3.00: unexpected _GTF length (8)
[    1.835132] ata3.00: configured for UDMA/100
[    1.835386] scsi 2:0:0:0: Direct-Access     ATA      WDC WD3200BEVT-6 02.0 PQ: 0 ANSI: 5
[    1.835679] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    1.835686] sd 2:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.835779] sd 2:0:0:0: [sda] Write Protect is off
[    1.835783] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.835821] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.871058]  sda: sda1 sda2 < sda5 >
[    1.871582] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.997557] random: lvm urandom read with 40 bits of entropy available
[    2.035365] bio: create slab <bio-1> at 1
[    2.056274] firewire_core 0000:08:05.0: created device fw0: GUID 0000c010a000b000, S400
[    2.961832] input: ALPS PS/2 Device as /devices/platform/i8042/serio1/input/input7
[    3.005421] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input6
[    4.465511] EXT4-fs (dm-0): mounted filesystem with ordered data mode. Opts: (null)
[    4.968590] random: nonblocking pool is initialized
[    8.076087] Adding 4182012k swap on /dev/mapper/ubuntu--vg-swap_1.  Priority:-1 extents:1 across:4182012k FS
[    8.743968] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
[    8.984960] EXT4-fs (sda1): mounting ext2 file system using the ext4 subsystem
[    9.027864] EXT4-fs (sda1): mounted filesystem without journal. Opts: (null)
[    9.631079] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   10.643860] systemd-udevd[365]: starting version 204
[   12.405529] lp: driver loaded but no devices found
[   12.529432] ppdev: user-space parallel port driver
[   15.751923] init: avahi-cups-reload main process (450) terminated with status 1
[   16.355130] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   16.671370] wmi: Mapper loaded
[   16.789116] ACPI Warning: 0x0000000000001028-0x000000000000102f SystemIO conflicts with Region \PMIO 1 (20131115/utaddress-251)
[   16.789126] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   16.789131] ACPI Warning: 0x00000000000011b0-0x00000000000011bf SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
[   16.789136] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   16.789138] ACPI Warning: 0x0000000000001180-0x00000000000011af SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
[   16.789143] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   16.789145] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   17.043511] Bluetooth: Core ver 2.17
[   17.043566] NET: Registered protocol family 31
[   17.043569] Bluetooth: HCI device and connection manager initialized
[   17.043582] Bluetooth: HCI socket layer initialized
[   17.043586] Bluetooth: L2CAP socket layer initialized
[   17.043592] Bluetooth: SCO socket layer initialized
[   17.078013] cfg80211: Calling CRDA to update world regulatory domain
[   17.079823] [drm] Initialized drm 1.1.0 20060810
[   17.127296] lib80211: common routines for IEEE802.11 drivers
[   17.127301] lib80211_crypt: registered algorithm 'NULL'
[   17.444626] type=1400 audit(1424381765.663:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=543 comm="apparmor_parser"
[   17.444636] type=1400 audit(1424381765.663:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=543 comm="apparmor_parser"
[   17.444643] type=1400 audit(1424381765.663:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=543 comm="apparmor_parser"
[   17.444655] type=1400 audit(1424381765.663:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=508 comm="apparmor_parser"
[   17.444665] type=1400 audit(1424381765.663:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=508 comm="apparmor_parser"
[   17.444672] type=1400 audit(1424381765.663:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=508 comm="apparmor_parser"
[   17.445218] type=1400 audit(1424381765.663:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=543 comm="apparmor_parser"
[   17.445225] type=1400 audit(1424381765.663:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=543 comm="apparmor_parser"
[   17.445255] type=1400 audit(1424381765.663:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=508 comm="apparmor_parser"
[   17.445262] type=1400 audit(1424381765.663:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=508 comm="apparmor_parser"
[   17.501910] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   17.501914] Bluetooth: BNEP filters: protocol multicast
[   17.501926] Bluetooth: BNEP socket layer initialized
[   17.600677] [drm] Memory usable by graphics device = 512M
[   17.600683] checking generic (d0000000 3f0000) vs hw (d0000000 10000000)
[   17.600686] fb: conflicting fb hw usage inteldrmfb vs VESA VGA - removing generic driver
[   17.600745] Console: switching to colour dummy device 80x25
[   17.640416] Bluetooth: RFCOMM TTY layer initialized
[   17.640434] Bluetooth: RFCOMM socket layer initialized
[   17.640447] Bluetooth: RFCOMM ver 1.11
[   17.664332] i915 0000:00:02.0: irq 46 for MSI/MSI-X
[   17.664351] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[   17.664353] [drm] Driver supports precise vblank timestamp query.
[   17.664440] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   17.716868] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   17.754648] [drm] initialized overlay support
[   17.902136] fbcon: inteldrmfb (fb0) is primary device
[   18.168193] wl: module license 'MIXED/Proprietary' taints kernel.
[   18.168194] Disabling lock debugging due to kernel taint
[   18.173676] wl: module verification failed: signature and/or  required key missing - tainting kernel
[   18.203007] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[   18.238813] lib80211_crypt: registered algorithm 'TKIP'
[   18.573059] wlan0: Broadcom BCM4315 802.11 Hybrid Wireless Controller 6.30.223.141 (r415941)
[   18.574398] input: Dell WMI hotkeys as /devices/virtual/input/input8
[   18.593215] Console: switching to colour frame buffer device 160x50
[   18.596880] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   18.596882] i915 0000:00:02.0: registered panic notifier
[   18.628733] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   18.644299] acpi device:08: registered as cooling_device2
[   18.644402] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input9
[   18.645548] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   18.645882] snd_hda_intel 0000:00:1b.0: irq 47 for MSI/MSI-X
[   18.705209] autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[   18.705210]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   18.705212]    hp_outs=1 (0x15/0x0/0x0/0x0/0x0)
[   18.705212]    mono: mono_out=0x0
[   18.705213]    inputs:
[   18.705215]      Mic=0x18
[   18.705216] realtek: No valid SSID, checking pincfg 0x4015822d for NID 0x1d
[   18.705217] realtek: Enabling init ASM_ID=0x822d CODEC_ID=10ec0268
[   18.722196] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   18.723203] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   19.025712] ip_tables: (C) 2000-2006 Netfilter Core Team
[   19.703178] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   19.896308] cfg80211: World regulatory domain updated:
[   19.896312] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   19.896316] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.896318] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.896321] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   19.896324] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.896326] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.641245] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   20.795306] init: failsafe main process (582) killed by TERM signal
[   26.487887] audit_printk_skb: 15 callbacks suppressed
[   26.487891] type=1400 audit(1424381774.704:17): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cups-browsed" pid=902 comm="apparmor_parser"
[   29.760160] type=1400 audit(1424381777.980:18): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=1010 comm="apparmor_parser"
[   29.760172] type=1400 audit(1424381777.980:19): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1010 comm="apparmor_parser"
[   29.760180] type=1400 audit(1424381777.980:20): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1010 comm="apparmor_parser"
[   29.760770] type=1400 audit(1424381777.980:21): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1010 comm="apparmor_parser"
[   29.760777] type=1400 audit(1424381777.980:22): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1010 comm="apparmor_parser"
[   29.761074] type=1400 audit(1424381777.980:23): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1010 comm="apparmor_parser"
[   30.014921] type=1400 audit(1424381778.232:24): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=1009 comm="apparmor_parser"
[   30.014933] type=1400 audit(1424381778.232:25): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=1009 comm="apparmor_parser"
[   30.015286] type=1400 audit(1424381778.232:26): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="chromium" pid=1009 comm="apparmor_parser"
[   30.133298] r8169 0000:07:00.0 eth0: link down
[   30.133387] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   30.133792] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   33.035881] vboxdrv: Found 2 processor cores.
[   33.037032] vboxdrv: fAsync=0 offMin=0x1c2 offMax=0x77d
[   33.037168] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   33.037170] vboxdrv: Successfully loaded version 4.3.20 (interface 0x001a0008).
[   33.586465] vboxpci: IOMMU not found (not registered)
[   33.651625] nf_conntrack: automatic helper assignment is deprecated and it will be removed soon. Use the iptables CT target to attach helpers instead.
[   34.060507] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:a8:bb:cf:21:a7:66:08:00 SRC=192.168.1.152 DST=224.0.0.1 LEN=44 TOS=0x00 PREC=0x00 TTL=1 ID=62789 PROTO=UDP SPT=51572 DPT=8612 LEN=24 
[   35.702175] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:28:cf:e9:57:7e:79:08:00 SRC=192.168.1.3 DST=224.0.0.1 LEN=44 TOS=0x00 PREC=0x00 TTL=1 ID=56597 PROTO=UDP SPT=62169 DPT=8612 LEN=24 
[   40.409518] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:60:c5:47:0c:fe:2a:08:00 SRC=192.168.1.156 DST=224.0.0.1 LEN=44 TOS=0x00 PREC=0x00 TTL=1 ID=20980 PROTO=UDP SPT=50805 DPT=8612 LEN=24 
[   40.411229] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:f8:1e:df:ee:7f:df:08:00 SRC=192.168.1.7 DST=224.0.0.1 LEN=44 TOS=0x00 PREC=0x00 TTL=1 ID=58202 PROTO=UDP SPT=53251 DPT=8612 LEN=24 
[   40.820398] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:88:65:37:cf:d0:08:00 SRC=192.168.1.119 DST=224.0.0.1 LEN=44 TOS=0x00 PREC=0x00 TTL=1 ID=41557 PROTO=UDP SPT=53723 DPT=8612 LEN=24 
[   41.024200] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:90:27:e4:f6:01:e4:08:00 SRC=192.168.1.73 DST=224.0.0.1 LEN=44 TOS=0x00 PREC=0x00 TTL=1 ID=33328 PROTO=UDP SPT=57025 DPT=8612 LEN=24 
[   41.027048] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:a8:bb:cf:21:a7:66:08:00 SRC=192.168.1.152 DST=224.0.0.1 LEN=44 TOS=0x00 PREC=0x00 TTL=1 ID=15141 PROTO=UDP SPT=51732 DPT=8612 LEN=24 
[   41.426820] init: plymouth-upstart-bridge main process ended, respawning
[   41.449307] init: plymouth-upstart-bridge main process ended, respawning
[   47.576176] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:60:c5:47:0c:fe:2a:08:00 SRC=192.168.1.156 DST=224.0.0.1 LEN=44 TOS=0x00 PREC=0x00 TTL=1 ID=58640 PROTO=UDP SPT=55391 DPT=8612 LEN=24 
[   47.578717] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:f8:1e:df:ee:7f:df:08:00 SRC=192.168.1.7 DST=224.0.0.1 LEN=44 TOS=0x00 PREC=0x00 TTL=1 ID=29869 PROTO=UDP SPT=53286 DPT=8612 LEN=24 
[   47.784994] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:88:65:37:cf:d0:08:00 SRC=192.168.1.119 DST=224.0.0.1 LEN=44 TOS=0x00 PREC=0x00 TTL=1 ID=57143 PROTO=UDP SPT=62300 DPT=8612 LEN=24 
[   54.743874] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:60:c5:47:0c:fe:2a:08:00 SRC=192.168.1.156 DST=224.0.0.1 LEN=44 TOS=0x00 PREC=0x00 TTL=1 ID=12057 PROTO=UDP SPT=60781 DPT=8612 LEN=24 
[   75.829939] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:f8:1e:df:ee:7f:df:08:00 SRC=192.168.1.7 DST=224.0.0.1 LEN=44 TOS=0x00 PREC=0x00 TTL=1 ID=40024 PROTO=UDP SPT=61248 DPT=8612 LEN=24 
[   97.117242] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:f8:1e:df:ee:7f:df:08:00 SRC=192.168.1.7 DST=224.0.0.1 LEN=44 TOS=0x00 PREC=0x00 TTL=1 ID=44619 PROTO=UDP SPT=61530 DPT=8612 LEN=24 
[  118.408995] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:f8:1e:df:ee:7f:df:08:00 SRC=192.168.1.7 DST=224.0.0.1 LEN=44 TOS=0x00 PREC=0x00 TTL=1 ID=21208 PROTO=UDP SPT=60423 DPT=8612 LEN=24 
[  134.787936] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:28:cf:e9:57:7e:79:08:00 SRC=192.168.1.3 DST=224.0.0.1 LEN=44 TOS=0x00 PREC=0x00 TTL=1 ID=43364 PROTO=UDP SPT=56847 DPT=8612 LEN=24 
[  154.436624] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:90:27:e4:f6:01:e4:08:00 SRC=192.168.1.73 DST=224.0.0.1 LEN=44 TOS=0x00 PREC=0x00 TTL=1 ID=20120 PROTO=UDP SPT=58616 DPT=8612 LEN=24 
[  174.908274] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:f8:1e:df:ee:7f:df:08:00 SRC=192.168.1.7 DST=224.0.0.1 LEN=44 TOS=0x00 PREC=0x00 TTL=1 ID=20344 PROTO=UDP SPT=53918 DPT=8612 LEN=24 
```
[ATTACH=CONFIG]260095[/ATTACH]

---

### Post by teknohippie on 2015-02-19
I attempted to go to [www.google.com/chrome](www.google.com/chrome) to which I was again thrown into blackscreen. I attempted to Ctrl+Alt+Bkspc which did take me to the login page (I heard the login noise) but my screen remained black. I shut my lid to hibernate, when I reopened the lid the graphics came back but when I logged in the screen began glitching terribly and nothing (Unity, etc.) would load.

---

### Post by teknohippie on 2015-02-19
Also when I attempted to install Chrome through Ubuntu Tweak just now, the following error appeard: 
```
Failed to fetch http://dl.google.com/linux/chrome/deb/pool/main/g/google-chrome-stable/google-chrome-stable_40.0.2214.111-1_amd64.deb 404  Not Found [IP: 173.194.204.91 80]
```

---

