---
title: "Swap takes a long time to mount, SSD disk"
date: 2014-10-12
forum: General Help
---

### Post by Goettschwan on 2014-10-12
Hi, 
I have installed Ubuntu 14.04LTS, fresh install (but copied over some things in home from the old install to save time). I have two disks SDA an SSD disk that has root and home inside one partition, and a separate partition for swap. SDB a big conventional disc which is plugged into home/pictures home /music home/documents on several partitions. For SDA this is the way the ubuntu installer chose to do it, since i had only one disc attached under the install. 

Now, the system boots fine and would probably start up into x much faster, if it would not take something like fourteen seconds for the swap to mount. The ubuntu installer chose to make a 16 Gigabyte swap partition, isn't this a bit big? It is clearly bigger than the ones I had in previous Ubuntu and Suse installs. 

here is the entire dmesg output. note the fourteen seconds jump when adding swap. Can I do something about this? 


```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.13.0-36-generic (buildd@toyol) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #63-Ubuntu SMP Wed Sep 3 21:30:07 UTC 2014 (Ubuntu 3.13.0-36.63-generic 3.13.11.6)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-36-generic root=UUID=91af8f15-8417-4e8e-b890-bae091cd5072 ro
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009d7ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009d800-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000af101fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000af102000-0x00000000af108fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000af109000-0x00000000af561fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000af562000-0x00000000af9c3fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000af9c4000-0x00000000cdbb8fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000cdbb9000-0x00000000cddc8fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000cddc9000-0x00000000cdde9fff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000cddea000-0x00000000ce312fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000ce313000-0x00000000ceffefff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000cefff000-0x00000000ceffffff] usable[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.13.0-36-generic (buildd@toyol) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #63-Ubuntu SMP Wed Sep 3 21:30:07 UTC 2014 (Ubuntu 3.13.0-36.63-generic 3.13.11.6)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-36-generic root=UUID=91af8f15-8417-4e8e-b890-bae091cd5072 ro
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009d7ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009d800-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000af101fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000af102000-0x00000000af108fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000af109000-0x00000000af561fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000af562000-0x00000000af9c3fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000af9c4000-0x00000000cdbb8fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000cdbb9000-0x00000000cddc8fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000cddc9000-0x00000000cdde9fff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000cddea000-0x00000000ce312fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000ce313000-0x00000000ceffefff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000cefff000-0x00000000ceffffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed03fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000042effffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.8 present.
[    0.000000] DMI: ASUS All Series/Z97-AR, BIOS 0702 04/23/2014
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x42f000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-E7FFF uncachable
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask 7C00000000 write-back
[    0.000000]   1 base 0400000000 mask 7FE0000000 write-back
[    0.000000]   2 base 0420000000 mask 7FF8000000 write-back
[    0.000000]   3 base 0428000000 mask 7FFC000000 write-back
[    0.000000]   4 base 042C000000 mask 7FFE000000 write-back
[    0.000000]   5 base 042E000000 mask 7FFF000000 write-back
[    0.000000]   6 base 00E0000000 mask 7FE0000000 uncachable
[    0.000000]   7 base 00D0000000 mask 7FF0000000 uncachable
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 16GB, type WB
[    0.000000] reg 1, base: 16GB, range: 512MB, type WB
[    0.000000] reg 2, base: 16896MB, range: 128MB, type WB
[    0.000000] reg 3, base: 17024MB, range: 64MB, type WB
[    0.000000] reg 4, base: 17088MB, range: 32MB, type WB
[    0.000000] reg 5, base: 17120MB, range: 16MB, type WB
[    0.000000] reg 6, base: 3584MB, range: 512MB, type UC
[    0.000000] reg 7, base: 3328MB, range: 256MB, type UC
[    0.000000] total RAM covered: 16368M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 32M     num_reg: 8      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 256MB, type WB
[    0.000000] reg 3, base: 4GB, range: 4GB, type WB
[    0.000000] reg 4, base: 8GB, range: 8GB, type WB
[    0.000000] reg 5, base: 16GB, range: 512MB, type WB
[    0.000000] reg 6, base: 16896MB, range: 256MB, type WB
[    0.000000] reg 7, base: 17136MB, range: 16MB, type UC
[    0.000000] e820: update [mem 0xd0000000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xcf000 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000fd8c0-0x000fd8cf] mapped at [ffff8800000fd8c0]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000097000] 97000 size 24576
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01fdf000, 0x01fdffff] PGTABLE
[    0.000000] BRK [0x01fe0000, 0x01fe0fff] PGTABLE
[    0.000000] BRK [0x01fe1000, 0x01fe1fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x42ee00000-0x42effffff]
[    0.000000]  [mem 0x42ee00000-0x42effffff] page 2M
[    0.000000] BRK [0x01fe2000, 0x01fe2fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x42c000000-0x42edfffff]
[    0.000000]  [mem 0x42c000000-0x42edfffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x400000000-0x42bffffff]
[    0.000000]  [mem 0x400000000-0x42bffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0xaf101fff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x3fffffff] page 2M
[    0.000000]  [mem 0x40000000-0x7fffffff] page 1G
[    0.000000]  [mem 0x80000000-0xaeffffff] page 2M
[    0.000000]  [mem 0xaf000000-0xaf101fff] page 4k
[    0.000000] init_memory_mapping: [mem 0xaf109000-0xaf561fff]
[    0.000000]  [mem 0xaf109000-0xaf1fffff] page 4k
[    0.000000]  [mem 0xaf200000-0xaf3fffff] page 2M
[    0.000000]  [mem 0xaf400000-0xaf561fff] page 4k
[    0.000000] BRK [0x01fe3000, 0x01fe3fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0xaf9c4000-0xcdbb8fff]
[    0.000000]  [mem 0xaf9c4000-0xaf9fffff] page 4k
[    0.000000]  [mem 0xafa00000-0xcd9fffff] page 2M
[    0.000000]  [mem 0xcda00000-0xcdbb8fff] page 4k
[    0.000000] BRK [0x01fe4000, 0x01fe4fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0xcefff000-0xceffffff]
[    0.000000]  [mem 0xcefff000-0xceffffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x100000000-0x3ffffffff]
[    0.000000]  [mem 0x100000000-0x3ffffffff] page 1G
[    0.000000] RAMDISK: [mem 0x35b5c000-0x36da5fff]
[    0.000000] ACPI: RSDP 00000000000f04a0 000024 (v02 ALASKA)
[    0.000000] ACPI: XSDT 00000000cddcf080 000074 (v01 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: FACP 00000000cdde1ae0 00010C (v05 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: DSDT 00000000cddcf188 012951 (v02 ALASKA    A M I 00000006 INTL 20120711)
[    0.000000] ACPI: FACS 00000000ce312f80 000040
[    0.000000] ACPI: APIC 00000000cdde1bf0 000092 (v03 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: FPDT 00000000cdde1c88 000044 (v01 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: SSDT 00000000cdde1cd0 000BEE (v01 Ther_R Ther_Rvp 00001000 INTL 20120711)
[    0.000000] ACPI: SSDT 00000000cdde28c0 000539 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.000000] ACPI: SSDT 00000000cdde2e00 000B74 (v01 CpuRef  CpuSsdt 00003000 INTL 20051117)
[    0.000000] ACPI: MCFG 00000000cdde3978 00003C (v01 ALASKA    A M I 01072009 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000cdde39b8 000038 (v01 ALASKA    A M I 01072009 AMI. 00000005)
[    0.000000] ACPI: SSDT 00000000cdde39f0 00036D (v01 SataRe SataTabl 00001000 INTL 20120711)
[    0.000000] ACPI: SSDT 00000000cdde3d60 005B5E (v01 SaSsdt  SaSsdt  00003000 INTL 20120711)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000042effffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x42effffff]
[    0.000000]   NODE_DATA [mem 0x42eff6000-0x42effafff]
[    0.000000]  [ffffea0000000000-ffffea0010bfffff] PMD -> [ffff88041e600000-ffff88042e5fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x42effffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009cfff]
[    0.000000]   node   0: [mem 0x00100000-0xaf101fff]
[    0.000000]   node   0: [mem 0xaf109000-0xaf561fff]
[    0.000000]   node   0: [mem 0xaf9c4000-0xcdbb8fff]
[    0.000000]   node   0: [mem 0xcefff000-0xceffffff]
[    0.000000]   node   0: [mem 0x100000000-0x42effffff]
[    0.000000] On node 0 totalpages: 4179693
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3996 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 13086 pages used for memmap
[    0.000000]   DMA32 zone: 837457 pages, LIFO batch:31
[    0.000000]   Normal zone: 52160 pages used for memmap
[    0.000000]   Normal zone: 3338240 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x1808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 8, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] smpboot: Allowing 8 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: [mem 0x0009d000-0x0009dfff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xaf102000-0xaf108fff]
[    0.000000] PM: Registered nosave memory: [mem 0xaf562000-0xaf9c3fff]
[    0.000000] PM: Registered nosave memory: [mem 0xcdbb9000-0xcddc8fff]
[    0.000000] PM: Registered nosave memory: [mem 0xcddc9000-0xcdde9fff]
[    0.000000] PM: Registered nosave memory: [mem 0xcddea000-0xce312fff]
[    0.000000] PM: Registered nosave memory: [mem 0xce313000-0xceffefff]
[    0.000000] PM: Registered nosave memory: [mem 0xcf000000-0xdfffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfecfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed00000-0xfed03fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed04000-0xfed1bfff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xfeffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xff000000-0xffffffff]
[    0.000000] e820: [mem 0xcf000000-0xdfffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 29 pages/cpu @ffff88042ec00000 s86336 r8192 d24256 u262144
[    0.000000] pcpu-alloc: s86336 r8192 d24256 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 4114362
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-36-generic root=UUID=91af8f15-8417-4e8e-b890-bae091cd5072 ro
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 16354264K/16718772K available (7373K kernel code, 1144K rwdata, 3404K rodata, 1336K init, 1440K bss, 364508K reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000]     Offload RCU callbacks from all CPUs
[    0.000000]     Offload RCU callbacks from CPUs: 0-7.
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 67108864 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.004000] tsc: Detected 3598.200 MHz processor
[    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 7196.40 BogoMIPS (lpj=14392800)
[    0.000129] pid_max: default: 32768 minimum: 301
[    0.000206] Security Framework initialized
[    0.000282] AppArmor: AppArmor initialized
[    0.000343] Yama: becoming mindful.
[    0.001070] Dentry cache hash table entries: 2097152 (order: 12, 16777216 bytes)
[    0.004295] Inode-cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.005793] Mount-cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.005870] Mountpoint-cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.006160] Initializing cgroup subsys memory
[    0.006225] Initializing cgroup subsys devices
[    0.006287] Initializing cgroup subsys freezer
[    0.006348] Initializing cgroup subsys blkio
[    0.006410] Initializing cgroup subsys perf_event
[    0.006472] Initializing cgroup subsys hugetlb
[    0.006547] CPU: Physical Processor ID: 0
[    0.006607] CPU: Processor Core ID: 0
[    0.006670] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.006670] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.007457] mce: CPU supports 9 MCE banks
[    0.007526] CPU0: Thermal monitoring enabled (TM1)
[    0.007596] Last level iTLB entries: 4KB 0, 2MB 0, 4MB 0
[    0.007596] Last level dTLB entries: 4KB 64, 2MB 0, 4MB 0
[    0.007596] tlb_flushall_shift: 6
[    0.007767] Freeing SMP alternatives memory: 32K (ffffffff81e6d000 - ffffffff81e75000)
[    0.008481] ACPI: Core revision 20131115
[    0.015763] ACPI: All ACPI Tables successfully acquired
[    0.031522] ftrace: allocating 28537 entries in 112 pages
[    0.039815] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=0 pin2=0
[    0.079618] smpboot: CPU0: Intel(R) Core(TM) i7-4790 CPU @ 3.60GHz (fam: 06, model: 3c, stepping: 03)
[    0.084955] TSC deadline timer enabled
[    0.084960] Performance Events: PEBS fmt2+, 16-deep LBR, Haswell events, full-width counters, Intel PMU driver.
[    0.085259] ... version:                3
[    0.085319] ... bit width:              48
[    0.085379] ... generic registers:      4
[    0.085439] ... value mask:             0000ffffffffffff
[    0.085501] ... max period:             0000ffffffffffff
[    0.085563] ... fixed-purpose events:   3
[    0.085623] ... event mask:             000000070000000f
[    0.086708] x86: Booting SMP configuration:
[    0.100807] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.086769] .... node  #0, CPUs:      #1 #2 #3 #4 #5 #6 #7
[    0.184516] x86: Booted up 1 node, 8 CPUs
[    0.184633] smpboot: Total of 8 processors activated (57571.20 BogoMIPS)
[    0.191152] devtmpfs: initialized
[    0.192871] EVM: security.selinux
[    0.192931] EVM: security.SMACK64
[    0.192989] EVM: security.ima
[    0.193049] EVM: security.capability
[    0.193128] PM: Registering ACPI NVS region [mem 0xaf102000-0xaf108fff] (28672 bytes)
[    0.193205] PM: Registering ACPI NVS region [mem 0xcddea000-0xce312fff] (5410816 bytes)
[    0.193775] pinctrl core: initialized pinctrl subsystem
[    0.193871] regulator-dummy: no parameters
[    0.193954] RTC time:  9:45:50, date: 10/12/14
[    0.194035] NET: Registered protocol family 16
[    0.194151] cpuidle: using governor ladder
[    0.194211] cpuidle: using governor menu
[    0.194288] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.194364] ACPI: bus type PCI registered
[    0.194424] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.194523] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.194602] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.210065] PCI: Using configuration type 1 for base access
[    0.210723] bio: create slab <bio-0> at 0
[    0.210878] ACPI: Added _OSI(Module Device)
[    0.210939] ACPI: Added _OSI(Processor Device)
[    0.211001] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.211063] ACPI: Added _OSI(Processor Aggregator Device)
[    0.214139] ACPI: Executed 15 blocks of module-level executable AML code
[    0.223170] ACPI: SSDT 00000000cdd77c18 0003D3 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.223691] ACPI: Dynamic OEM Table Load:
[    0.223840] ACPI: SSDT           (null) 0003D3 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.227238] ACPI: SSDT 00000000cdd77618 0005AA (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.227798] ACPI: Dynamic OEM Table Load:
[    0.227945] ACPI: SSDT           (null) 0005AA (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.231155] ACPI: SSDT 00000000cdd76d98 000119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.231672] ACPI: Dynamic OEM Table Load:
[    0.231821] ACPI: SSDT           (null) 000119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.236091] ACPI: Interpreter enabled
[    0.236156] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20131115/hwxface-580)
[    0.236323] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)
[    0.236499] ACPI: (supports S0 S3 S4 S5)
[    0.236559] ACPI: Using IOAPIC for interrupt routing
[    0.236637] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.236855] ACPI: No dock devices found.
[    0.237149] ACPI: Power Resource [PG00] (on)
[    0.239292] ACPI: Power Resource [PG01] (on)
[    0.243265] ACPI: Power Resource [PG02] (on)
[    0.251741] ACPI: Power Resource [FN00] (off)
[    0.251840] ACPI: Power Resource [FN01] (off)
[    0.251937] ACPI: Power Resource [FN02] (off)
[    0.252033] ACPI: Power Resource [FN03] (off)
[    0.252129] ACPI: Power Resource [FN04] (off)
[    0.252726] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[    0.252792] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.252999] acpi PNP0A08:00: _OSC: platform does not support [PCIeHotplug PME]
[    0.253150] acpi PNP0A08:00: _OSC: OS now controls [AER PCIeCapability]
[    0.253557] PCI host bridge to bus 0000:00
[    0.253618] pci_bus 0000:00: root bus resource [bus 00-fe]
[    0.253680] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.253744] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.253807] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.253871] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff]
[    0.253935] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
[    0.253999] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
[    0.254063] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff]
[    0.254128] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000e3fff]
[    0.254192] pci_bus 0000:00: root bus resource [mem 0x000e4000-0x000e7fff]
[    0.254256] pci_bus 0000:00: root bus resource [mem 0xd0000000-0xfeafffff]
[    0.254324] pci 0000:00:00.0: [8086:0c00] type 00 class 0x060000
[    0.254379] pci 0000:00:01.0: [8086:0c01] type 01 class 0x060400
[    0.254401] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.254436] pci 0000:00:01.0: System wakeup disabled by ACPI
[    0.254537] pci 0000:00:14.0: [8086:8cb1] type 00 class 0x0c0330
[    0.254552] pci 0000:00:14.0: reg 0x10: [mem 0xdf120000-0xdf12ffff 64bit]
[    0.254601] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    0.254638] pci 0000:00:14.0: System wakeup disabled by ACPI
[    0.254718] pci 0000:00:16.0: [8086:8cba] type 00 class 0x078000
[    0.254734] pci 0000:00:16.0: reg 0x10: [mem 0xdf13a000-0xdf13a00f 64bit]
[    0.254786] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.254839] pci 0000:00:19.0: [8086:15a1] type 00 class 0x020000
[    0.254852] pci 0000:00:19.0: reg 0x10: [mem 0xdf100000-0xdf11ffff]
[    0.254858] pci 0000:00:19.0: reg 0x14: [mem 0xdf138000-0xdf138fff]
[    0.254865] pci 0000:00:19.0: reg 0x18: [io  0xf040-0xf05f]
[    0.254913] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.254949] pci 0000:00:19.0: System wakeup disabled by ACPI
[    0.255031] pci 0000:00:1a.0: [8086:8cad] type 00 class 0x0c0320
[    0.255047] pci 0000:00:1a.0: reg 0x10: [mem 0xdf137000-0xdf1373ff]
[    0.255122] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.255163] pci 0000:00:1a.0: System wakeup disabled by ACPI
[    0.255244] pci 0000:00:1b.0: [8086:8ca0] type 00 class 0x040300
[    0.255255] pci 0000:00:1b.0: reg 0x10: [mem 0xdf130000-0xdf133fff 64bit]
[    0.255307] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.255343] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    0.255420] pci 0000:00:1c.0: [8086:8c90] type 01 class 0x060400
[    0.255472] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.255505] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.255585] pci 0000:00:1c.3: [8086:244e] type 01 class 0x060401
[    0.255637] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.255669] pci 0000:00:1c.3: System wakeup disabled by ACPI
[    0.255757] pci 0000:00:1d.0: [8086:8ca6] type 00 class 0x0c0320
[    0.255773] pci 0000:00:1d.0: reg 0x10: [mem 0xdf136000-0xdf1363ff]
[    0.255847] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.255885] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.255965] pci 0000:00:1f.0: [8086:8cc4] type 00 class 0x060100
[    0.256096] pci 0000:00:1f.2: [8086:8c82] type 00 class 0x010601
[    0.256108] pci 0000:00:1f.2: reg 0x10: [io  0xf090-0xf097]
[    0.256113] pci 0000:00:1f.2: reg 0x14: [io  0xf080-0xf083]
[    0.256118] pci 0000:00:1f.2: reg 0x18: [io  0xf070-0xf077]
[    0.256124] pci 0000:00:1f.2: reg 0x1c: [io  0xf060-0xf063]
[    0.256129] pci 0000:00:1f.2: reg 0x20: [io  0xf020-0xf03f]
[    0.256135] pci 0000:00:1f.2: reg 0x24: [mem 0xdf135000-0xdf1357ff]
[    0.256164] pci 0000:00:1f.2: PME# supported from D3hot
[    0.256205] pci 0000:00:1f.3: [8086:8ca2] type 00 class 0x0c0500
[    0.256216] pci 0000:00:1f.3: reg 0x10: [mem 0xdf134000-0xdf1340ff 64bit]
[    0.256232] pci 0000:00:1f.3: reg 0x20: [io  0xf000-0xf01f]
[    0.256309] pci 0000:01:00.0: [10de:1184] type 00 class 0x030000
[    0.256317] pci 0000:01:00.0: reg 0x10: [mem 0xde000000-0xdeffffff]
[    0.256326] pci 0000:01:00.0: reg 0x14: [mem 0xd0000000-0xd7ffffff 64bit pref]
[    0.256334] pci 0000:01:00.0: reg 0x1c: [mem 0xd8000000-0xd9ffffff 64bit pref]
[    0.256340] pci 0000:01:00.0: reg 0x24: [io  0xe000-0xe07f]
[    0.256346] pci 0000:01:00.0: reg 0x30: [mem 0xdf000000-0xdf07ffff pref]
[    0.256389] pci 0000:01:00.0: System wakeup disabled by ACPI
[    0.256470] pci 0000:01:00.1: [10de:0e0a] type 00 class 0x040300
[    0.256477] pci 0000:01:00.1: reg 0x10: [mem 0xdf080000-0xdf083fff]
[    0.263181] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.263243] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.263245] pci 0000:00:01.0:   bridge window [mem 0xde000000-0xdf0fffff]
[    0.263247] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xd9ffffff 64bit pref]
[    0.263300] acpiphp: Slot [1] registered
[    0.263363] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.263478] pci 0000:03:00.0: [1b21:1080] type 01 class 0x060401
[    0.263570] pci 0000:03:00.0: System wakeup disabled by ACPI
[    0.263646] pci 0000:00:1c.3: PCI bridge to [bus 03-04] (subtractive decode)
[    0.263716] pci 0000:00:1c.3:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.263717] pci 0000:00:1c.3:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.263718] pci 0000:00:1c.3:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.263718] pci 0000:00:1c.3:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
[    0.263719] pci 0000:00:1c.3:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.263720] pci 0000:00:1c.3:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.263721] pci 0000:00:1c.3:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
[    0.263722] pci 0000:00:1c.3:   bridge window [mem 0x000e0000-0x000e3fff] (subtractive decode)
[    0.263723] pci 0000:00:1c.3:   bridge window [mem 0x000e4000-0x000e7fff] (subtractive decode)
[    0.263724] pci 0000:00:1c.3:   bridge window [mem 0xd0000000-0xfeafffff] (subtractive decode)
[    0.263813] pci 0000:03:00.0: PCI bridge to [bus 04] (subtractive decode)
[    0.263892] pci 0000:03:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
[    0.263893] pci 0000:03:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
[    0.263894] pci 0000:03:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
[    0.263895] pci 0000:03:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
[    0.263896] pci 0000:03:00.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.263897] pci 0000:03:00.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.263898] pci 0000:03:00.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.263898] pci 0000:03:00.0:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
[    0.263899] pci 0000:03:00.0:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.263900] pci 0000:03:00.0:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.263901] pci 0000:03:00.0:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
[    0.263902] pci 0000:03:00.0:   bridge window [mem 0x000e0000-0x000e3fff] (subtractive decode)
[    0.263903] pci 0000:03:00.0:   bridge window [mem 0x000e4000-0x000e7fff] (subtractive decode)
[    0.263904] pci 0000:03:00.0:   bridge window [mem 0xd0000000-0xfeafffff] (subtractive decode)
[    0.263923] acpi PNP0A08:00: Disabling ASPM (FADT indicates it is unsupported)
[    0.264529] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.265147] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.265764] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 *6 7 10 11 12 14 15)
[    0.266378] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.266993] ACPI: PCI Interrupt Link [LNKE] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.267609] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 *15)
[    0.268222] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 *4 5 6 7 10 11 12 14 15)
[    0.268837] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 *14 15)
[    0.269674] ACPI: Enabled 6 GPEs in block 00 to 3F
[    0.269827] ACPI: \_SB_.PCI0: notify handler is installed
[    0.269877] Found 1 acpi root devices
[    0.269886] ACPI : EC: GPE = 0x1e, I/O: command/status = 0x66, data = 0x62
[    0.270000] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.270077] vgaarb: loaded
[    0.270135] vgaarb: bridge control possible 0000:01:00.0
[    0.270285] SCSI subsystem initialized
[    0.270368] libata version 3.00 loaded.
[    0.270378] ACPI: bus type USB registered
[    0.270446] usbcore: registered new interface driver usbfs
[    0.270512] usbcore: registered new interface driver hub
[    0.270598] usbcore: registered new device driver usb
[    0.270718] PCI: Using ACPI for IRQ routing
[    0.275709] PCI: pci_cache_line_size set to 64 bytes
[    0.275745] e820: reserve RAM buffer [mem 0x0009d800-0x0009ffff]
[    0.275746] e820: reserve RAM buffer [mem 0xaf102000-0xafffffff]
[    0.275747] e820: reserve RAM buffer [mem 0xaf562000-0xafffffff]
[    0.275748] e820: reserve RAM buffer [mem 0xcdbb9000-0xcfffffff]
[    0.275748] e820: reserve RAM buffer [mem 0xcf000000-0xcfffffff]
[    0.275749] e820: reserve RAM buffer [mem 0x42f000000-0x42fffffff]
[    0.275791] NetLabel: Initializing
[    0.275851] NetLabel:  domain hash size = 128
[    0.275911] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.275978] NetLabel:  unlabeled traffic allowed by default
[    0.276063] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.276523] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.278607] Switched to clocksource hpet
[    0.281462] AppArmor: AppArmor Filesystem Enabled
[    0.281530] pnp: PnP ACPI init
[    0.281598] ACPI: bus type PNP registered
[    0.281713] system 00:00: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.281778] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.281786] pnp 00:01: [dma 4]
[    0.281795] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.281804] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
[    0.281859] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.281881] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.281905] system 00:05: [io  0x0800-0x087f] has been reserved
[    0.281968] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.281980] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.281998] system 00:07: [io  0x1854-0x1857] has been reserved
[    0.282062] system 00:07: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.282112] system 00:08: [io  0x0290-0x029f] has been reserved
[    0.282175] system 00:08: [io  0x02a0-0x02af] has been reserved
[    0.282238] system 00:08: [io  0x0a00-0x0aff] has been reserved
[    0.282302] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.282332] system 00:09: [io  0x04d0-0x04d1] has been reserved
[    0.282395] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.282751] system 00:0a: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.282815] system 00:0a: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.282880] system 00:0a: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.282944] system 00:0a: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.283009] system 00:0a: [mem 0xe0000000-0xefffffff] has been reserved
[    0.283073] system 00:0a: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.283137] system 00:0a: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.283201] system 00:0a: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.283265] system 00:0a: [mem 0xff000000-0xffffffff] has been reserved
[    0.283329] system 00:0a: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.283393] system 00:0a: [mem 0xdffe0000-0xdffeffff] has been reserved
[    0.283458] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.283551] pnp: PnP ACPI: found 11 devices
[    0.283611] ACPI: bus type PNP unregistered
[    0.289142] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.289205] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.289269] pci 0000:00:01.0:   bridge window [mem 0xde000000-0xdf0fffff]
[    0.289334] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xd9ffffff 64bit pref]
[    0.289412] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.289480] pci 0000:03:00.0: PCI bridge to [bus 04]
[    0.289556] pci 0000:00:1c.3: PCI bridge to [bus 03-04]
[    0.289625] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.289626] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.289627] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.289627] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.289628] pci_bus 0000:00: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.289629] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.289630] pci_bus 0000:00: resource 10 [mem 0x000dc000-0x000dffff]
[    0.289631] pci_bus 0000:00: resource 11 [mem 0x000e0000-0x000e3fff]
[    0.289632] pci_bus 0000:00: resource 12 [mem 0x000e4000-0x000e7fff]
[    0.289633] pci_bus 0000:00: resource 13 [mem 0xd0000000-0xfeafffff]
[    0.289633] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.289634] pci_bus 0000:01: resource 1 [mem 0xde000000-0xdf0fffff]
[    0.289635] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xd9ffffff 64bit pref]
[    0.289636] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    0.289637] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
[    0.289638] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    0.289639] pci_bus 0000:03: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.289640] pci_bus 0000:03: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.289640] pci_bus 0000:03: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.289641] pci_bus 0000:03: resource 10 [mem 0x000dc000-0x000dffff]
[    0.289642] pci_bus 0000:03: resource 11 [mem 0x000e0000-0x000e3fff]
[    0.289643] pci_bus 0000:03: resource 12 [mem 0x000e4000-0x000e7fff]
[    0.289644] pci_bus 0000:03: resource 13 [mem 0xd0000000-0xfeafffff]
[    0.289645] pci_bus 0000:04: resource 8 [io  0x0000-0x0cf7]
[    0.289645] pci_bus 0000:04: resource 9 [io  0x0d00-0xffff]
[    0.289646] pci_bus 0000:04: resource 10 [mem 0x000a0000-0x000bffff]
[    0.289647] pci_bus 0000:04: resource 11 [mem 0x000d0000-0x000d3fff]
[    0.289648] pci_bus 0000:04: resource 12 [mem 0x000d4000-0x000d7fff]
[    0.289649] pci_bus 0000:04: resource 13 [mem 0x000d8000-0x000dbfff]
[    0.289650] pci_bus 0000:04: resource 14 [mem 0x000dc000-0x000dffff]
[    0.289650] pci_bus 0000:04: resource 15 [mem 0x000e0000-0x000e3fff]
[    0.289651] pci_bus 0000:04: resource 16 [mem 0x000e4000-0x000e7fff]
[    0.289652] pci_bus 0000:04: resource 17 [mem 0xd0000000-0xfeafffff]
[    0.289672] NET: Registered protocol family 2
[    0.289847] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.290126] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.290359] TCP: Hash tables configured (established 131072 bind 65536)
[    0.290436] TCP: reno registered
[    0.290507] UDP hash table entries: 8192 (order: 6, 262144 bytes)
[    0.290622] UDP-Lite hash table entries: 8192 (order: 6, 262144 bytes)
[    0.290771] NET: Registered protocol family 1
[    0.326740] pci 0000:01:00.0: Boot video device
[    0.326751] PCI: CLS 64 bytes, default 64
[    0.326780] Trying to unpack rootfs image as initramfs...
[    0.513280] Freeing initrd memory: 18728K (ffff880035b5c000 - ffff880036da6000)
[    0.513359] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.513424] software IO TLB [mem 0xc9bb9000-0xcdbb9000] (64MB) mapped at [ffff8800c9bb9000-ffff8800cdbb8fff]
[    0.513661] microcode: CPU0 sig=0x306c3, pf=0x2, revision=0x17
[    0.513728] microcode: CPU1 sig=0x306c3, pf=0x2, revision=0x17
[    0.513795] microcode: CPU2 sig=0x306c3, pf=0x2, revision=0x17
[    0.513860] microcode: CPU3 sig=0x306c3, pf=0x2, revision=0x17
[    0.513927] microcode: CPU4 sig=0x306c3, pf=0x2, revision=0x17
[    0.513993] microcode: CPU5 sig=0x306c3, pf=0x2, revision=0x17
[    0.514059] microcode: CPU6 sig=0x306c3, pf=0x2, revision=0x17
[    0.514125] microcode: CPU7 sig=0x306c3, pf=0x2, revision=0x17
[    0.514215] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.514293] Scanning for low memory corruption every 60 seconds
[    0.514534] Initialise system trusted keyring
[    0.514621] audit: initializing netlink socket (disabled)
[    0.514689] type=2000 audit(1413107150.484:1): initialized
[    0.531232] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.532005] zbud: loaded
[    0.532145] VFS: Disk quotas dquot_6.5.2
[    0.532231] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.532524] fuse init (API version 7.22)
[    0.532622] msgmni has been set to 31978
[    0.532713] Key type big_key registered
[    0.533052] Key type asymmetric registered
[    0.533114] Asymmetric key parser 'x509' registered
[    0.533189] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.533296] io scheduler noop registered
[    0.533358] io scheduler deadline registered (default)
[    0.533431] io scheduler cfq registered
[    0.533606] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.533702] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.533772] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.533856] intel_idle: MWAIT substates: 0x42120
[    0.533857] intel_idle: v0.4 model 0x3C
[    0.533857] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.533969] ipmi message handler version 39.2
[    0.534075] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.534154] ACPI: Power Button [PWRB]
[    0.534230] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.534306] ACPI: Power Button [PWRF]
[    0.534397] ACPI: Fan [FAN0] (off)
[    0.534469] ACPI: Fan [FAN1] (off)
[    0.534540] ACPI: Fan [FAN2] (off)
[    0.534612] ACPI: Fan [FAN3] (off)
[    0.534681] ACPI: Fan [FAN4] (off)
[    0.534999] thermal LNXTHERM:00: registered as thermal_zone0
[    0.535062] ACPI: Thermal Zone [TZ00] (28 C)
[    0.535231] thermal LNXTHERM:01: registered as thermal_zone1
[    0.535294] ACPI: Thermal Zone [TZ01] (30 C)
[    0.535367] GHES: HEST is not enabled!
[    0.535478] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.536341] Linux agpgart interface v0.103
[    0.537079] brd: module loaded
[    0.537477] loop: module loaded
[    0.537727] libphy: Fixed MDIO Bus: probed
[    0.537830] tun: Universal TUN/TAP device driver, 1.6
[    0.537892] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.537973] PPP generic driver version 2.4.2
[    0.538057] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.538122] ehci-pci: EHCI PCI platform driver
[    0.538245] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    0.538310] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    0.538394] ehci-pci 0000:00:1a.0: debug port 2
[    0.542342] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    0.542352] ehci-pci 0000:00:1a.0: irq 16, io mem 0xdf137000
[    0.550988] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    0.551073] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.551137] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.551212] usb usb1: Product: EHCI Host Controller
[    0.551273] usb usb1: Manufacturer: Linux 3.13.0-36-generic ehci_hcd
[    0.551337] usb usb1: SerialNumber: 0000:00:1a.0
[    0.551452] hub 1-0:1.0: USB hub found
[    0.551514] hub 1-0:1.0: 2 ports detected
[    0.551678] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    0.551742] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.551825] ehci-pci 0000:00:1d.0: debug port 2
[    0.555787] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    0.555799] ehci-pci 0000:00:1d.0: irq 23, io mem 0xdf136000
[    0.567010] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    0.567090] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    0.567154] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.567230] usb usb2: Product: EHCI Host Controller
[    0.567291] usb usb2: Manufacturer: Linux 3.13.0-36-generic ehci_hcd
[    0.567355] usb usb2: SerialNumber: 0000:00:1d.0
[    0.567479] hub 2-0:1.0: USB hub found
[    0.567541] hub 2-0:1.0: 2 ports detected
[    0.567653] ehci-platform: EHCI generic platform driver
[    0.567718] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.567781] ohci-pci: OHCI PCI platform driver
[    0.567845] ohci-platform: OHCI generic platform driver
[    0.567909] uhci_hcd: USB Universal Host Controller Interface driver
[    0.568040] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.568103] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
[    0.568251] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    0.568264] xhci_hcd 0000:00:14.0: irq 41 for MSI/MSI-X
[    0.568300] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    0.568364] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.568440] usb usb3: Product: xHCI Host Controller
[    0.568501] usb usb3: Manufacturer: Linux 3.13.0-36-generic xhci_hcd
[    0.568564] usb usb3: SerialNumber: 0000:00:14.0
[    0.568684] hub 3-0:1.0: USB hub found
[    0.568757] hub 3-0:1.0: 14 ports detected
[    0.570979] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.571048] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 4
[    0.571149] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
[    0.571213] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.571288] usb usb4: Product: xHCI Host Controller
[    0.571350] usb usb4: Manufacturer: Linux 3.13.0-36-generic xhci_hcd
[    0.571413] usb usb4: SerialNumber: 0000:00:14.0
[    0.571532] hub 4-0:1.0: USB hub found
[    0.571602] hub 4-0:1.0: 6 ports detected
[    0.579063] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    0.581547] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.581615] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.581779] mousedev: PS/2 mouse device common for all mice
[    0.582024] rtc_cmos 00:06: RTC can wake from S4
[    0.582208] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.582294] rtc_cmos 00:06: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.582410] device-mapper: uevent: version 1.0.3
[    0.582536] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
[    0.582618] ledtrig-cpu: registered to indicate activity on CPUs
[    0.582743] TCP: cubic registered
[    0.582855] NET: Registered protocol family 10
[    0.583029] NET: Registered protocol family 17
[    0.583096] Key type dns_resolver registered
[    0.583353] Loading compiled-in X.509 certificates
[    0.583912] Loaded X.509 cert 'Magrathea: Glacier signing key: 38f3b6c63a85affdfbbe0e53339df8e0c6b6c9d5'
[    0.583997] registered taskstats version 1
[    0.585426] Key type trusted registered
[    0.586616] Key type encrypted registered
[    0.587802] AppArmor: AppArmor sha1 policy hashing enabled
[    0.587866] IMA: No TPM chip found, activating TPM-bypass!
[    0.588159] regulator-dummy: disabling
[    0.588298]   Magic number: 2:116:778
[    0.588452] rtc_cmos 00:06: setting system clock to 2014-10-12 09:45:50 UTC (1413107150)
[    0.589362] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.589425] EDD information not available.
[    0.589508] PM: Hibernation image not present or could not be loaded.
[    0.590004] Freeing unused kernel memory: 1336K (ffffffff81d1f000 - ffffffff81e6d000)
[    0.590081] Write protecting the kernel read-only data: 12288k
[    0.591366] Freeing unused kernel memory: 808K (ffff880001736000 - ffff880001800000)
[    0.592375] Freeing unused kernel memory: 692K (ffff880001b53000 - ffff880001c00000)
[    0.598748] systemd-udevd[144]: starting version 204
[    0.611252] pps_core: LinuxPPS API ver. 1 registered
[    0.611320] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
[    0.612459] PTP clock support registered
[    0.612605] ahci 0000:00:1f.2: version 3.0
[    0.612783] ahci 0000:00:1f.2: irq 42 for MSI/MSI-X
[    0.612829] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0xa impl SATA mode
[    0.612916] ahci 0000:00:1f.2: flags: 64bit ncq led clo pio slum part ems apst 
[    0.616129] e1000e: Intel(R) PRO/1000 Network Driver - 2.3.2-k
[    0.616206] e1000e: Copyright(c) 1999 - 2013 Intel Corporation.
[    0.619573] scsi0 : ahci
[    0.619700] scsi1 : ahci
[    0.619816] scsi2 : ahci
[    0.619966] scsi3 : ahci
[    0.620120] scsi4 : ahci
[    0.620240] scsi5 : ahci
[    0.620331] ata1: DUMMY
[    0.620398] ata2: SATA max UDMA/133 abar m2048@0xdf135000 port 0xdf135180 irq 42
[    0.620481] ata3: DUMMY
[    0.620548] ata4: SATA max UDMA/133 abar m2048@0xdf135000 port 0xdf135280 irq 42
[    0.625717] ata5: DUMMY
[    0.625775] ata6: DUMMY
[    0.626014] e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    0.626119] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[    0.791797] e1000e 0000:00:19.0 eth0: registered PHC clock
[    0.791863] e1000e 0000:00:19.0 eth0: (PCI Express:2.5GT/s:Width x1) 10:c3:7b:6c:40:28
[    0.791939] e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
[    0.792025] e1000e 0000:00:19.0 eth0: MAC: 11, PHY: 12, PBA No: FFFFFF-0FF
[    0.863450] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    0.943550] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    0.943628] ata4: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    0.944798] ata4.00: ATA-8: ST3000DM001-1CH166, CC24, max UDMA/133
[    0.944863] ata4.00: 5860533168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    0.945795] ata4.00: configured for UDMA/133
[    0.984973] ata2.00: ATA-8: WDC WD1600BEVT-22ZCT0, 11.01A11, max UDMA/133
[    0.985038] ata2.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    0.986484] ata2.00: configured for UDMA/133
[    0.986652] scsi 1:0:0:0: Direct-Access     ATA      WDC WD1600BEVT-2 11.0 PQ: 0 ANSI: 5
[    0.986814] sd 1:0:0:0: Attached scsi generic sg0 type 0
[    0.986850] sd 1:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    0.987013] sd 1:0:0:0: [sda] Write Protect is off
[    0.987092] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.987119] scsi 3:0:0:0: Direct-Access     ATA      ST3000DM001-1CH1 CC24 PQ: 0 ANSI: 5
[    0.987133] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.987384] sd 3:0:0:0: [sdb] 5860533168 512-byte logical blocks: (3.00 TB/2.72 TiB)
[    0.987392] sd 3:0:0:0: Attached scsi generic sg1 type 0
[    0.987544] sd 3:0:0:0: [sdb] 4096-byte physical blocks
[    0.987701] sd 3:0:0:0: [sdb] Write Protect is off
[    0.987764] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    0.987787] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.995962] usb 1-1: New USB device found, idVendor=8087, idProduct=8009
[    0.996027] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    0.996233] hub 1-1:1.0: USB hub found
[    0.996338] hub 1-1:1.0: 6 ports detected
[    1.022133]  sda: sda1 sda2 < sda5 >
[    1.022563] sd 1:0:0:0: [sda] Attached SCSI disk
[    1.042649]  sdb: sdb1 sdb2 sdb3
[    1.043085] sd 3:0:0:0: [sdb] Attached SCSI disk
[    1.107782] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    1.240282] usb 2-1: New USB device found, idVendor=8087, idProduct=8001
[    1.240347] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.240562] hub 2-1:1.0: USB hub found
[    1.240658] hub 2-1:1.0: 8 ports detected
[    1.344536] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    1.408198] usb 3-13: new low-speed USB device number 2 using xhci_hcd
[    1.429688] usb 3-13: New USB device found, idVendor=046d, idProduct=c31d
[    1.429754] usb 3-13: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.429829] usb 3-13: Product: USB Keyboard
[    1.429890] usb 3-13: Manufacturer: Logitech
[    1.430016] usb 3-13: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[    1.430095] usb 3-13: ep 0x82 - rounding interval to 1024 microframes, ep desc says 2040 microframes
[    1.512321] tsc: Refined TSC clocksource calibration: 3597.915 MHz
[    1.600457] usb 3-14: new low-speed USB device number 3 using xhci_hcd
[    1.621640] usb 3-14: New USB device found, idVendor=045e, idProduct=077d
[    1.621706] usb 3-14: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.621782] usb 3-14: Product: Comfort Mouse 6000
[    1.621843] usb 3-14: Manufacturer: Microsoft
[    1.621968] usb 3-14: ep 0x83 - rounding interval to 64 microframes, ep desc says 80 microframes
[    1.897796] random: nonblocking pool is initialized
[    2.513777] Switched to clocksource tsc
[   16.367542] Adding 16717820k swap on /dev/sda5.  Priority:-1 extents:1 across:16717820k FS
[   16.504592] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.577299] systemd-udevd[349]: starting version 204
[   16.813918] lp: driver loaded but no devices found
[   16.816462] ppdev: user-space parallel port driver
[   16.821525] wmi: Mapper loaded
[   16.836120] [drm] Initialized drm 1.1.0 20060810
[   16.836231] mei_me 0000:00:16.0: irq 44 for MSI/MSI-X
[   16.840559] nvidia: module license 'NVIDIA' taints kernel.
[   16.840561] Disabling lock debugging due to kernel taint
[   16.845055] nvidia: module verification failed: signature and/or  required key missing - tainting kernel
[   16.848690] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=none
[   16.849044] [drm] Initialized nvidia-drm 0.0.0 20130102 for 0000:01:00.0 on minor 0
[   16.849050] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  343.22  Thu Sep 11 16:27:43 PDT 2014
[   16.849503] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   16.859797] SKU: Nid=0x1d sku_cfg=0x4047e629
[   16.859798] SKU: port_connectivity=0x1
[   16.859799] SKU: enable_pcbeep=0x0
[   16.859799] SKU: check_sum=0x00000007
[   16.859800] SKU: customization=0x000000e6
[   16.859800] SKU: external_amp=0x5
[   16.859801] SKU: platform_type=0x0
[   16.859801] SKU: swap=0x0
[   16.859802] SKU: override=0x1
[   16.860207] autoconfig: line_outs=3 (0x14/0x15/0x16/0x0/0x0) type:line
[   16.860207]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   16.860208]    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[   16.860208]    mono: mono_out=0x0
[   16.860209]    dig-out=0x11/0x1e
[   16.860209]    inputs:
[   16.860210]      Front Mic=0x19
[   16.860211]      Rear Mic=0x18
[   16.860212]      Line=0x1a
[   16.860212] realtek: No valid SSID, checking pincfg 0x4047e629 for NID 0x1d
[   16.860213] realtek: Enabling init ASM_ID=0xe629 CODEC_ID=10ec0892
[   16.868204] systemd-udevd[380]: renamed network interface eth0 to eth1
[   16.869870] kvm: disabled by bios
[   16.876324] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   16.876540] input: HDA Intel PCH Line Out CLFE as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   16.876594] input: HDA Intel PCH Line Out Surround as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   16.876639] input: HDA Intel PCH Line Out Front as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   16.876711] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   16.876899] input: HDA Intel PCH Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   16.877110] input: HDA Intel PCH Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
[   16.877413] hda_intel: Disabling MSI
[   16.877419] hda-intel 0000:01:00.1: Handle VGA-switcheroo audio client
[   16.877448] hda-intel 0000:01:00.1: Disabling 64bit DMA
[   16.881599] hda-intel 0000:01:00.1: Enable delay in RIRB handling
[   16.885782] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   16.896326] type=1400 audit(1413107166.779:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=468 comm="apparmor_parser"
[   16.896328] type=1400 audit(1413107166.779:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=468 comm="apparmor_parser"
[   16.896330] type=1400 audit(1413107166.779:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=468 comm="apparmor_parser"
[   16.896530] type=1400 audit(1413107166.779:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=468 comm="apparmor_parser"
[   16.896532] type=1400 audit(1413107166.779:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=468 comm="apparmor_parser"
[   16.896634] type=1400 audit(1413107166.779:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=468 comm="apparmor_parser"
[   16.900448] asus_wmi: ASUS WMI generic driver loaded
[   16.901832] asus_wmi: Initialization: 0x0
[   16.901842] asus_wmi: BIOS WMI version: 0.9
[   16.901860] asus_wmi: SFUN value: 0x0
[   16.902025] input: Eee PC WMI hotkeys as /devices/platform/eeepc-wmi/input/input12
[   16.902558] asus_wmi: Disabling ACPI video driver
[   16.960071] hidraw: raw HID events driver (C) Jiri Kosina
[   16.971794] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[   16.975830] usbcore: registered new interface driver usbhid
[   16.975832] usbhid: USB HID core driver
[   16.976998] input: Logitech USB Keyboard as /devices/pci0000:00/0000:00:14.0/usb3/3-13/3-13:1.0/input/input13
[   16.977054] hid-generic 0003:046D:C31D.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Keyboard] on usb-0000:00:14.0-13/input0
[   16.978393] input: Logitech USB Keyboard as /devices/pci0000:00/0000:00:14.0/usb3/3-13/3-13:1.1/input/input14
[   16.978495] hid-generic 0003:046D:C31D.0002: input,hidraw1: USB HID v1.10 Device [Logitech USB Keyboard] on usb-0000:00:14.0-13/input1
[   16.978678] input: Microsoft Comfort Mouse 6000 as /devices/pci0000:00/0000:00:14.0/usb3/3-14/3-14:1.0/input/input15
[   16.978745] hid-generic 0003:045E:077D.0003: input,hidraw2: USB HID v1.11 Mouse [Microsoft Comfort Mouse 6000] on usb-0000:00:14.0-14/input0
[   17.049559] EXT4-fs (sdb3): mounted filesystem with ordered data mode. Opts: (null)
[   17.097572] EXT4-fs (sdb2): warning: maximal mount count reached, running e2fsck is recommended
[   17.099009] EXT4-fs (sdb2): mounted filesystem with ordered data mode. Opts: (null)
[   17.189575] init: failsafe main process (636) killed by TERM signal
[   17.318013] type=1400 audit(1413107167.203:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=821 comm="apparmor_parser"
[   17.318018] type=1400 audit(1413107167.203:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=821 comm="apparmor_parser"
[   17.318020] type=1400 audit(1413107167.203:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=821 comm="apparmor_parser"
[   17.318235] type=1400 audit(1413107167.203:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=821 comm="apparmor_parser"
[   17.350086] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input19
[   17.350146] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input18
[   17.350189] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input17
[   17.350231] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input16
[   17.879967] Bluetooth: Core ver 2.17
[   17.879988] NET: Registered protocol family 31
[   17.879989] Bluetooth: HCI device and connection manager initialized
[   17.879995] Bluetooth: HCI socket layer initialized
[   17.879997] Bluetooth: L2CAP socket layer initialized
[   17.880009] Bluetooth: SCO socket layer initialized
[   17.881406] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   17.881408] Bluetooth: BNEP filters: protocol multicast
[   17.881411] Bluetooth: BNEP socket layer initialized
[   17.882041] Bluetooth: RFCOMM TTY layer initialized
[   17.882044] Bluetooth: RFCOMM socket layer initialized
[   17.882047] Bluetooth: RFCOMM ver 1.11
[   17.984484] init: cups main process (892) killed by HUP signal
[   17.984489] init: cups main process ended, respawning
[   19.821524] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[   19.925620] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[   19.925694] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   19.925814] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   20.187572] init: samba-ad-dc main process (1174) terminated with status 1
[   20.571423] init: udev-fallback-graphics main process (1194) terminated with status 1
[   21.453264] e1000e: eth1 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
[   21.453268] e1000e 0000:00:19.0 eth1: 10/100 speed: disabling TSO
[   21.453294] IPv6: ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   21.944947] nvidia 0000:01:00.0: irq 46 for MSI/MSI-X
[   22.767087] init: plymouth-upstart-bridge main process ended, respawning
[   48.032986] audit_printk_skb: 150 callbacks suppressed
[   48.032988] type=1400 audit(1413107197.884:62): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=2326 comm="apparmor_parser"
[   48.032991] type=1400 audit(1413107197.884:63): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2326 comm="apparmor_parser"
[   48.033182] type=1400 audit(1413107197.884:64): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2326 comm="apparmor_parser"
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed03fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000042effffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.8 present.
[    0.000000] DMI: ASUS All Series/Z97-AR, BIOS 0702 04/23/2014
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x42f000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-E7FFF uncachable
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask 7C00000000 write-back
[    0.000000]   1 base 0400000000 mask 7FE0000000 write-back
[    0.000000]   2 base 0420000000 mask 7FF8000000 write-back
[    0.000000]   3 base 0428000000 mask 7FFC000000 write-back
[    0.000000]   4 base 042C000000 mask 7FFE000000 write-back
[    0.000000]   5 base 042E000000 mask 7FFF000000 write-back
[    0.000000]   6 base 00E0000000 mask 7FE0000000 uncachable
[    0.000000]   7 base 00D0000000 mask 7FF0000000 uncachable
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 16GB, type WB
[    0.000000] reg 1, base: 16GB, range: 512MB, type WB
[    0.000000] reg 2, base: 16896MB, range: 128MB, type WB
[    0.000000] reg 3, base: 17024MB, range: 64MB, type WB
[    0.000000] reg 4, base: 17088MB, range: 32MB, type WB
[    0.000000] reg 5, base: 17120MB, range: 16MB, type WB
[    0.000000] reg 6, base: 3584MB, range: 512MB, type UC
[    0.000000] reg 7, base: 3328MB, range: 256MB, type UC
[    0.000000] total RAM covered: 16368M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 32M     num_reg: 8      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 256MB, type WB
[    0.000000] reg 3, base: 4GB, range: 4GB, type WB
[    0.000000] reg 4, base: 8GB, range: 8GB, type WB
[    0.000000] reg 5, base: 16GB, range: 512MB, type WB
[    0.000000] reg 6, base: 16896MB, range: 256MB, type WB
[    0.000000] reg 7, base: 17136MB, range: 16MB, type UC
[    0.000000] e820: update [mem 0xd0000000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xcf000 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000fd8c0-0x000fd8cf] mapped at [ffff8800000fd8c0]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000097000] 97000 size 24576
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01fdf000, 0x01fdffff] PGTABLE
[    0.000000] BRK [0x01fe0000, 0x01fe0fff] PGTABLE
[    0.000000] BRK [0x01fe1000, 0x01fe1fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x42ee00000-0x42effffff]
[    0.000000]  [mem 0x42ee00000-0x42effffff] page 2M
[    0.000000] BRK [0x01fe2000, 0x01fe2fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x42c000000-0x42edfffff]
[    0.000000]  [mem 0x42c000000-0x42edfffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x400000000-0x42bffffff]
[    0.000000]  [mem 0x400000000-0x42bffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0xaf101fff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x3fffffff] page 2M
[    0.000000]  [mem 0x40000000-0x7fffffff] page 1G
[    0.000000]  [mem 0x80000000-0xaeffffff] page 2M
[    0.000000]  [mem 0xaf000000-0xaf101fff] page 4k
[    0.000000] init_memory_mapping: [mem 0xaf109000-0xaf561fff]
[    0.000000]  [mem 0xaf109000-0xaf1fffff] page 4k
[    0.000000]  [mem 0xaf200000-0xaf3fffff] page 2M
[    0.000000]  [mem 0xaf400000-0xaf561fff] page 4k
[    0.000000] BRK [0x01fe3000, 0x01fe3fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0xaf9c4000-0xcdbb8fff]
[    0.000000]  [mem 0xaf9c4000-0xaf9fffff] page 4k
[    0.000000]  [mem 0xafa00000-0xcd9fffff] page 2M
[    0.000000]  [mem 0xcda00000-0xcdbb8fff] page 4k
[    0.000000] BRK [0x01fe4000, 0x01fe4fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0xcefff000-0xceffffff]
[    0.000000]  [mem 0xcefff000-0xceffffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x100000000-0x3ffffffff]
[    0.000000]  [mem 0x100000000-0x3ffffffff] page 1G
[    0.000000] RAMDISK: [mem 0x35b5c000-0x36da5fff]
[    0.000000] ACPI: RSDP 00000000000f04a0 000024 (v02 ALASKA)
[    0.000000] ACPI: XSDT 00000000cddcf080 000074 (v01 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: FACP 00000000cdde1ae0 00010C (v05 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: DSDT 00000000cddcf188 012951 (v02 ALASKA    A M I 00000006 INTL 20120711)
[    0.000000] ACPI: FACS 00000000ce312f80 000040
[    0.000000] ACPI: APIC 00000000cdde1bf0 000092 (v03 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: FPDT 00000000cdde1c88 000044 (v01 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: SSDT 00000000cdde1cd0 000BEE (v01 Ther_R Ther_Rvp 00001000 INTL 20120711)
[    0.000000] ACPI: SSDT 00000000cdde28c0 000539 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.000000] ACPI: SSDT 00000000cdde2e00 000B74 (v01 CpuRef  CpuSsdt 00003000 INTL 20051117)
[    0.000000] ACPI: MCFG 00000000cdde3978 00003C (v01 ALASKA    A M I 01072009 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000cdde39b8 000038 (v01 ALASKA    A M I 01072009 AMI. 00000005)
[    0.000000] ACPI: SSDT 00000000cdde39f0 00036D (v01 SataRe SataTabl 00001000 INTL 20120711)
[    0.000000] ACPI: SSDT 00000000cdde3d60 005B5E (v01 SaSsdt  SaSsdt  00003000 INTL 20120711)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000042effffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x42effffff]
[    0.000000]   NODE_DATA [mem 0x42eff6000-0x42effafff]
[    0.000000]  [ffffea0000000000-ffffea0010bfffff] PMD -> [ffff88041e600000-ffff88042e5fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x42effffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009cfff]
[    0.000000]   node   0: [mem 0x00100000-0xaf101fff]
[    0.000000]   node   0: [mem 0xaf109000-0xaf561fff]
[    0.000000]   node   0: [mem 0xaf9c4000-0xcdbb8fff]
[    0.000000]   node   0: [mem 0xcefff000-0xceffffff]
[    0.000000]   node   0: [mem 0x100000000-0x42effffff]
[    0.000000] On node 0 totalpages: 4179693
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3996 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 13086 pages used for memmap
[    0.000000]   DMA32 zone: 837457 pages, LIFO batch:31
[    0.000000]   Normal zone: 52160 pages used for memmap
[    0.000000]   Normal zone: 3338240 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x1808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 8, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] smpboot: Allowing 8 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: [mem 0x0009d000-0x0009dfff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xaf102000-0xaf108fff]
[    0.000000] PM: Registered nosave memory: [mem 0xaf562000-0xaf9c3fff]
[    0.000000] PM: Registered nosave memory: [mem 0xcdbb9000-0xcddc8fff]
[    0.000000] PM: Registered nosave memory: [mem 0xcddc9000-0xcdde9fff]
[    0.000000] PM: Registered nosave memory: [mem 0xcddea000-0xce312fff]
[    0.000000] PM: Registered nosave memory: [mem 0xce313000-0xceffefff]
[    0.000000] PM: Registered nosave memory: [mem 0xcf000000-0xdfffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfecfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed00000-0xfed03fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed04000-0xfed1bfff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xfeffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xff000000-0xffffffff]
[    0.000000] e820: [mem 0xcf000000-0xdfffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 29 pages/cpu @ffff88042ec00000 s86336 r8192 d24256 u262144
[    0.000000] pcpu-alloc: s86336 r8192 d24256 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 4114362
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-36-generic root=UUID=91af8f15-8417-4e8e-b890-bae091cd5072 ro
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 16354264K/16718772K available (7373K kernel code, 1144K rwdata, 3404K rodata, 1336K init, 1440K bss, 364508K reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000]     Offload RCU callbacks from all CPUs
[    0.000000]     Offload RCU callbacks from CPUs: 0-7.
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 67108864 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.004000] tsc: Detected 3598.200 MHz processor
[    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 7196.40 BogoMIPS (lpj=14392800)
[    0.000129] pid_max: default: 32768 minimum: 301
[    0.000206] Security Framework initialized
[    0.000282] AppArmor: AppArmor initialized
[    0.000343] Yama: becoming mindful.
[    0.001070] Dentry cache hash table entries: 2097152 (order: 12, 16777216 bytes)
[    0.004295] Inode-cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.005793] Mount-cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.005870] Mountpoint-cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.006160] Initializing cgroup subsys memory
[    0.006225] Initializing cgroup subsys devices
[    0.006287] Initializing cgroup subsys freezer
[    0.006348] Initializing cgroup subsys blkio
[    0.006410] Initializing cgroup subsys perf_event
[    0.006472] Initializing cgroup subsys hugetlb
[    0.006547] CPU: Physical Processor ID: 0
[    0.006607] CPU: Processor Core ID: 0
[    0.006670] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.006670] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.007457] mce: CPU supports 9 MCE banks
[    0.007526] CPU0: Thermal monitoring enabled (TM1)
[    0.007596] Last level iTLB entries: 4KB 0, 2MB 0, 4MB 0
[    0.007596] Last level dTLB entries: 4KB 64, 2MB 0, 4MB 0
[    0.007596] tlb_flushall_shift: 6
[    0.007767] Freeing SMP alternatives memory: 32K (ffffffff81e6d000 - ffffffff81e75000)
[    0.008481] ACPI: Core revision 20131115
[    0.015763] ACPI: All ACPI Tables successfully acquired
[    0.031522] ftrace: allocating 28537 entries in 112 pages
[    0.039815] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=0 pin2=0
[    0.079618] smpboot: CPU0: Intel(R) Core(TM) i7-4790 CPU @ 3.60GHz (fam: 06, model: 3c, stepping: 03)
[    0.084955] TSC deadline timer enabled
[    0.084960] Performance Events: PEBS fmt2+, 16-deep LBR, Haswell events, full-width counters, Intel PMU driver.
[    0.085259] ... version:                3
[    0.085319] ... bit width:              48
[    0.085379] ... generic registers:      4
[    0.085439] ... value mask:             0000ffffffffffff
[    0.085501] ... max period:             0000ffffffffffff
[    0.085563] ... fixed-purpose events:   3
[    0.085623] ... event mask:             000000070000000f
[    0.086708] x86: Booting SMP configuration:
[    0.100807] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.086769] .... node  #0, CPUs:      #1 #2 #3 #4 #5 #6 #7
[    0.184516] x86: Booted up 1 node, 8 CPUs
[    0.184633] smpboot: Total of 8 processors activated (57571.20 BogoMIPS)
[    0.191152] devtmpfs: initialized
[    0.192871] EVM: security.selinux
[    0.192931] EVM: security.SMACK64
[    0.192989] EVM: security.ima
[    0.193049] EVM: security.capability
[    0.193128] PM: Registering ACPI NVS region [mem 0xaf102000-0xaf108fff] (28672 bytes)
[    0.193205] PM: Registering ACPI NVS region [mem 0xcddea000-0xce312fff] (5410816 bytes)
[    0.193775] pinctrl core: initialized pinctrl subsystem
[    0.193871] regulator-dummy: no parameters
[    0.193954] RTC time:  9:45:50, date: 10/12/14
[    0.194035] NET: Registered protocol family 16
[    0.194151] cpuidle: using governor ladder
[    0.194211] cpuidle: using governor menu
[    0.194288] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.194364] ACPI: bus type PCI registered
[    0.194424] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.194523] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.194602] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.210065] PCI: Using configuration type 1 for base access
[    0.210723] bio: create slab <bio-0> at 0
[    0.210878] ACPI: Added _OSI(Module Device)
[    0.210939] ACPI: Added _OSI(Processor Device)
[    0.211001] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.211063] ACPI: Added _OSI(Processor Aggregator Device)
[    0.214139] ACPI: Executed 15 blocks of module-level executable AML code
[    0.223170] ACPI: SSDT 00000000cdd77c18 0003D3 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.223691] ACPI: Dynamic OEM Table Load:
[    0.223840] ACPI: SSDT           (null) 0003D3 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.227238] ACPI: SSDT 00000000cdd77618 0005AA (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.227798] ACPI: Dynamic OEM Table Load:
[    0.227945] ACPI: SSDT           (null) 0005AA (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.231155] ACPI: SSDT 00000000cdd76d98 000119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.231672] ACPI: Dynamic OEM Table Load:
[    0.231821] ACPI: SSDT           (null) 000119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.236091] ACPI: Interpreter enabled
[    0.236156] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20131115/hwxface-580)
[    0.236323] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)
[    0.236499] ACPI: (supports S0 S3 S4 S5)
[    0.236559] ACPI: Using IOAPIC for interrupt routing
[    0.236637] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.236855] ACPI: No dock devices found.
[    0.237149] ACPI: Power Resource [PG00] (on)
[    0.239292] ACPI: Power Resource [PG01] (on)
[    0.243265] ACPI: Power Resource [PG02] (on)
[    0.251741] ACPI: Power Resource [FN00] (off)
[    0.251840] ACPI: Power Resource [FN01] (off)
[    0.251937] ACPI: Power Resource [FN02] (off)
[    0.252033] ACPI: Power Resource [FN03] (off)
[    0.252129] ACPI: Power Resource [FN04] (off)
[    0.252726] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[    0.252792] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.252999] acpi PNP0A08:00: _OSC: platform does not support [PCIeHotplug PME]
[    0.253150] acpi PNP0A08:00: _OSC: OS now controls [AER PCIeCapability]
[    0.253557] PCI host bridge to bus 0000:00
[    0.253618] pci_bus 0000:00: root bus resource [bus 00-fe]
[    0.253680] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.253744] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.253807] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.253871] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff]
[    0.253935] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
[    0.253999] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
[    0.254063] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff]
[    0.254128] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000e3fff]
[    0.254192] pci_bus 0000:00: root bus resource [mem 0x000e4000-0x000e7fff]
[    0.254256] pci_bus 0000:00: root bus resource [mem 0xd0000000-0xfeafffff]
[    0.254324] pci 0000:00:00.0: [8086:0c00] type 00 class 0x060000
[    0.254379] pci 0000:00:01.0: [8086:0c01] type 01 class 0x060400
[    0.254401] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.254436] pci 0000:00:01.0: System wakeup disabled by ACPI
[    0.254537] pci 0000:00:14.0: [8086:8cb1] type 00 class 0x0c0330
[    0.254552] pci 0000:00:14.0: reg 0x10: [mem 0xdf120000-0xdf12ffff 64bit]
[    0.254601] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    0.254638] pci 0000:00:14.0: System wakeup disabled by ACPI
[    0.254718] pci 0000:00:16.0: [8086:8cba] type 00 class 0x078000
[    0.254734] pci 0000:00:16.0: reg 0x10: [mem 0xdf13a000-0xdf13a00f 64bit]
[    0.254786] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.254839] pci 0000:00:19.0: [8086:15a1] type 00 class 0x020000
[    0.254852] pci 0000:00:19.0: reg 0x10: [mem 0xdf100000-0xdf11ffff]
[    0.254858] pci 0000:00:19.0: reg 0x14: [mem 0xdf138000-0xdf138fff]
[    0.254865] pci 0000:00:19.0: reg 0x18: [io  0xf040-0xf05f]
[    0.254913] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.254949] pci 0000:00:19.0: System wakeup disabled by ACPI
[    0.255031] pci 0000:00:1a.0: [8086:8cad] type 00 class 0x0c0320
[    0.255047] pci 0000:00:1a.0: reg 0x10: [mem 0xdf137000-0xdf1373ff]
[    0.255122] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.255163] pci 0000:00:1a.0: System wakeup disabled by ACPI
[    0.255244] pci 0000:00:1b.0: [8086:8ca0] type 00 class 0x040300
[    0.255255] pci 0000:00:1b.0: reg 0x10: [mem 0xdf130000-0xdf133fff 64bit]
[    0.255307] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.255343] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    0.255420] pci 0000:00:1c.0: [8086:8c90] type 01 class 0x060400
[    0.255472] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.255505] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.255585] pci 0000:00:1c.3: [8086:244e] type 01 class 0x060401
[    0.255637] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.255669] pci 0000:00:1c.3: System wakeup disabled by ACPI
[    0.255757] pci 0000:00:1d.0: [8086:8ca6] type 00 class 0x0c0320
[    0.255773] pci 0000:00:1d.0: reg 0x10: [mem 0xdf136000-0xdf1363ff]
[    0.255847] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.255885] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.255965] pci 0000:00:1f.0: [8086:8cc4] type 00 class 0x060100
[    0.256096] pci 0000:00:1f.2: [8086:8c82] type 00 class 0x010601
[    0.256108] pci 0000:00:1f.2: reg 0x10: [io  0xf090-0xf097]
[    0.256113] pci 0000:00:1f.2: reg 0x14: [io  0xf080-0xf083]
[    0.256118] pci 0000:00:1f.2: reg 0x18: [io  0xf070-0xf077]
[    0.256124] pci 0000:00:1f.2: reg 0x1c: [io  0xf060-0xf063]
[    0.256129] pci 0000:00:1f.2: reg 0x20: [io  0xf020-0xf03f]
[    0.256135] pci 0000:00:1f.2: reg 0x24: [mem 0xdf135000-0xdf1357ff]
[    0.256164] pci 0000:00:1f.2: PME# supported from D3hot
[    0.256205] pci 0000:00:1f.3: [8086:8ca2] type 00 class 0x0c0500
[    0.256216] pci 0000:00:1f.3: reg 0x10: [mem 0xdf134000-0xdf1340ff 64bit]
[    0.256232] pci 0000:00:1f.3: reg 0x20: [io  0xf000-0xf01f]
[    0.256309] pci 0000:01:00.0: [10de:1184] type 00 class 0x030000
[    0.256317] pci 0000:01:00.0: reg 0x10: [mem 0xde000000-0xdeffffff]
[    0.256326] pci 0000:01:00.0: reg 0x14: [mem 0xd0000000-0xd7ffffff 64bit pref]
[    0.256334] pci 0000:01:00.0: reg 0x1c: [mem 0xd8000000-0xd9ffffff 64bit pref]
[    0.256340] pci 0000:01:00.0: reg 0x24: [io  0xe000-0xe07f]
[    0.256346] pci 0000:01:00.0: reg 0x30: [mem 0xdf000000-0xdf07ffff pref]
[    0.256389] pci 0000:01:00.0: System wakeup disabled by ACPI
[    0.256470] pci 0000:01:00.1: [10de:0e0a] type 00 class 0x040300
[    0.256477] pci 0000:01:00.1: reg 0x10: [mem 0xdf080000-0xdf083fff]
[    0.263181] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.263243] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.263245] pci 0000:00:01.0:   bridge window [mem 0xde000000-0xdf0fffff]
[    0.263247] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xd9ffffff 64bit pref]
[    0.263300] acpiphp: Slot [1] registered
[    0.263363] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.263478] pci 0000:03:00.0: [1b21:1080] type 01 class 0x060401
[    0.263570] pci 0000:03:00.0: System wakeup disabled by ACPI
[    0.263646] pci 0000:00:1c.3: PCI bridge to [bus 03-04] (subtractive decode)
[    0.263716] pci 0000:00:1c.3:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.263717] pci 0000:00:1c.3:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.263718] pci 0000:00:1c.3:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.263718] pci 0000:00:1c.3:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
[    0.263719] pci 0000:00:1c.3:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.263720] pci 0000:00:1c.3:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.263721] pci 0000:00:1c.3:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
[    0.263722] pci 0000:00:1c.3:   bridge window [mem 0x000e0000-0x000e3fff] (subtractive decode)
[    0.263723] pci 0000:00:1c.3:   bridge window [mem 0x000e4000-0x000e7fff] (subtractive decode)
[    0.263724] pci 0000:00:1c.3:   bridge window [mem 0xd0000000-0xfeafffff] (subtractive decode)
[    0.263813] pci 0000:03:00.0: PCI bridge to [bus 04] (subtractive decode)
[    0.263892] pci 0000:03:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
[    0.263893] pci 0000:03:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
[    0.263894] pci 0000:03:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
[    0.263895] pci 0000:03:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
[    0.263896] pci 0000:03:00.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.263897] pci 0000:03:00.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.263898] pci 0000:03:00.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.263898] pci 0000:03:00.0:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
[    0.263899] pci 0000:03:00.0:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.263900] pci 0000:03:00.0:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.263901] pci 0000:03:00.0:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
[    0.263902] pci 0000:03:00.0:   bridge window [mem 0x000e0000-0x000e3fff] (subtractive decode)
[    0.263903] pci 0000:03:00.0:   bridge window [mem 0x000e4000-0x000e7fff] (subtractive decode)
[    0.263904] pci 0000:03:00.0:   bridge window [mem 0xd0000000-0xfeafffff] (subtractive decode)
[    0.263923] acpi PNP0A08:00: Disabling ASPM (FADT indicates it is unsupported)
[    0.264529] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.265147] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.265764] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 *6 7 10 11 12 14 15)
[    0.266378] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.266993] ACPI: PCI Interrupt Link [LNKE] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.267609] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 *15)
[    0.268222] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 *4 5 6 7 10 11 12 14 15)
[    0.268837] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 *14 15)
[    0.269674] ACPI: Enabled 6 GPEs in block 00 to 3F
[    0.269827] ACPI: \_SB_.PCI0: notify handler is installed
[    0.269877] Found 1 acpi root devices
[    0.269886] ACPI : EC: GPE = 0x1e, I/O: command/status = 0x66, data = 0x62
[    0.270000] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.270077] vgaarb: loaded
[    0.270135] vgaarb: bridge control possible 0000:01:00.0
[    0.270285] SCSI subsystem initialized
[    0.270368] libata version 3.00 loaded.
[    0.270378] ACPI: bus type USB registered
[    0.270446] usbcore: registered new interface driver usbfs
[    0.270512] usbcore: registered new interface driver hub
[    0.270598] usbcore: registered new device driver usb
[    0.270718] PCI: Using ACPI for IRQ routing
[    0.275709] PCI: pci_cache_line_size set to 64 bytes
[    0.275745] e820: reserve RAM buffer [mem 0x0009d800-0x0009ffff]
[    0.275746] e820: reserve RAM buffer [mem 0xaf102000-0xafffffff]
[    0.275747] e820: reserve RAM buffer [mem 0xaf562000-0xafffffff]
[    0.275748] e820: reserve RAM buffer [mem 0xcdbb9000-0xcfffffff]
[    0.275748] e820: reserve RAM buffer [mem 0xcf000000-0xcfffffff]
[    0.275749] e820: reserve RAM buffer [mem 0x42f000000-0x42fffffff]
[    0.275791] NetLabel: Initializing
[    0.275851] NetLabel:  domain hash size = 128
[    0.275911] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.275978] NetLabel:  unlabeled traffic allowed by default
[    0.276063] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.276523] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.278607] Switched to clocksource hpet
[    0.281462] AppArmor: AppArmor Filesystem Enabled
[    0.281530] pnp: PnP ACPI init
[    0.281598] ACPI: bus type PNP registered
[    0.281713] system 00:00: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.281778] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.281786] pnp 00:01: [dma 4]
[    0.281795] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.281804] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
[    0.281859] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.281881] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.281905] system 00:05: [io  0x0800-0x087f] has been reserved
[    0.281968] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.281980] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.281998] system 00:07: [io  0x1854-0x1857] has been reserved
[    0.282062] system 00:07: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.282112] system 00:08: [io  0x0290-0x029f] has been reserved
[    0.282175] system 00:08: [io  0x02a0-0x02af] has been reserved
[    0.282238] system 00:08: [io  0x0a00-0x0aff] has been reserved
[    0.282302] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.282332] system 00:09: [io  0x04d0-0x04d1] has been reserved
[    0.282395] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.282751] system 00:0a: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.282815] system 00:0a: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.282880] system 00:0a: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.282944] system 00:0a: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.283009] system 00:0a: [mem 0xe0000000-0xefffffff] has been reserved
[    0.283073] system 00:0a: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.283137] system 00:0a: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.283201] system 00:0a: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.283265] system 00:0a: [mem 0xff000000-0xffffffff] has been reserved
[    0.283329] system 00:0a: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.283393] system 00:0a: [mem 0xdffe0000-0xdffeffff] has been reserved
[    0.283458] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.283551] pnp: PnP ACPI: found 11 devices
[    0.283611] ACPI: bus type PNP unregistered
[    0.289142] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.289205] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.289269] pci 0000:00:01.0:   bridge window [mem 0xde000000-0xdf0fffff]
[    0.289334] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xd9ffffff 64bit pref]
[    0.289412] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.289480] pci 0000:03:00.0: PCI bridge to [bus 04]
[    0.289556] pci 0000:00:1c.3: PCI bridge to [bus 03-04]
[    0.289625] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.289626] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.289627] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.289627] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.289628] pci_bus 0000:00: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.289629] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.289630] pci_bus 0000:00: resource 10 [mem 0x000dc000-0x000dffff]
[    0.289631] pci_bus 0000:00: resource 11 [mem 0x000e0000-0x000e3fff]
[    0.289632] pci_bus 0000:00: resource 12 [mem 0x000e4000-0x000e7fff]
[    0.289633] pci_bus 0000:00: resource 13 [mem 0xd0000000-0xfeafffff]
[    0.289633] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.289634] pci_bus 0000:01: resource 1 [mem 0xde000000-0xdf0fffff]
[    0.289635] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xd9ffffff 64bit pref]
[    0.289636] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    0.289637] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
[    0.289638] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    0.289639] pci_bus 0000:03: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.289640] pci_bus 0000:03: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.289640] pci_bus 0000:03: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.289641] pci_bus 0000:03: resource 10 [mem 0x000dc000-0x000dffff]
[    0.289642] pci_bus 0000:03: resource 11 [mem 0x000e0000-0x000e3fff]
[    0.289643] pci_bus 0000:03: resource 12 [mem 0x000e4000-0x000e7fff]
[    0.289644] pci_bus 0000:03: resource 13 [mem 0xd0000000-0xfeafffff]
[    0.289645] pci_bus 0000:04: resource 8 [io  0x0000-0x0cf7]
[    0.289645] pci_bus 0000:04: resource 9 [io  0x0d00-0xffff]
[    0.289646] pci_bus 0000:04: resource 10 [mem 0x000a0000-0x000bffff]
[    0.289647] pci_bus 0000:04: resource 11 [mem 0x000d0000-0x000d3fff]
[    0.289648] pci_bus 0000:04: resource 12 [mem 0x000d4000-0x000d7fff]
[    0.289649] pci_bus 0000:04: resource 13 [mem 0x000d8000-0x000dbfff]
[    0.289650] pci_bus 0000:04: resource 14 [mem 0x000dc000-0x000dffff]
[    0.289650] pci_bus 0000:04: resource 15 [mem 0x000e0000-0x000e3fff]
[    0.289651] pci_bus 0000:04: resource 16 [mem 0x000e4000-0x000e7fff]
[    0.289652] pci_bus 0000:04: resource 17 [mem 0xd0000000-0xfeafffff]
[    0.289672] NET: Registered protocol family 2
[    0.289847] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.290126] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.290359] TCP: Hash tables configured (established 131072 bind 65536)
[    0.290436] TCP: reno registered
[    0.290507] UDP hash table entries: 8192 (order: 6, 262144 bytes)
[    0.290622] UDP-Lite hash table entries: 8192 (order: 6, 262144 bytes)
[    0.290771] NET: Registered protocol family 1
[    0.326740] pci 0000:01:00.0: Boot video device
[    0.326751] PCI: CLS 64 bytes, default 64
[    0.326780] Trying to unpack rootfs image as initramfs...
[    0.513280] Freeing initrd memory: 18728K (ffff880035b5c000 - ffff880036da6000)
[    0.513359] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.513424] software IO TLB [mem 0xc9bb9000-0xcdbb9000] (64MB) mapped at [ffff8800c9bb9000-ffff8800cdbb8fff]
[    0.513661] microcode: CPU0 sig=0x306c3, pf=0x2, revision=0x17
[    0.513728] microcode: CPU1 sig=0x306c3, pf=0x2, revision=0x17
[    0.513795] microcode: CPU2 sig=0x306c3, pf=0x2, revision=0x17
[    0.513860] microcode: CPU3 sig=0x306c3, pf=0x2, revision=0x17
[    0.513927] microcode: CPU4 sig=0x306c3, pf=0x2, revision=0x17
[    0.513993] microcode: CPU5 sig=0x306c3, pf=0x2, revision=0x17
[    0.514059] microcode: CPU6 sig=0x306c3, pf=0x2, revision=0x17
[    0.514125] microcode: CPU7 sig=0x306c3, pf=0x2, revision=0x17
[    0.514215] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.514293] Scanning for low memory corruption every 60 seconds
[    0.514534] Initialise system trusted keyring
[    0.514621] audit: initializing netlink socket (disabled)
[    0.514689] type=2000 audit(1413107150.484:1): initialized
[    0.531232] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.532005] zbud: loaded
[    0.532145] VFS: Disk quotas dquot_6.5.2
[    0.532231] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.532524] fuse init (API version 7.22)
[    0.532622] msgmni has been set to 31978
[    0.532713] Key type big_key registered
[    0.533052] Key type asymmetric registered
[    0.533114] Asymmetric key parser 'x509' registered
[    0.533189] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.533296] io scheduler noop registered
[    0.533358] io scheduler deadline registered (default)
[    0.533431] io scheduler cfq registered
[    0.533606] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.533702] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.533772] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.533856] intel_idle: MWAIT substates: 0x42120
[    0.533857] intel_idle: v0.4 model 0x3C
[    0.533857] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.533969] ipmi message handler version 39.2
[    0.534075] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.534154] ACPI: Power Button [PWRB]
[    0.534230] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.534306] ACPI: Power Button [PWRF]
[    0.534397] ACPI: Fan [FAN0] (off)
[    0.534469] ACPI: Fan [FAN1] (off)
[    0.534540] ACPI: Fan [FAN2] (off)
[    0.534612] ACPI: Fan [FAN3] (off)
[    0.534681] ACPI: Fan [FAN4] (off)
[    0.534999] thermal LNXTHERM:00: registered as thermal_zone0
[    0.535062] ACPI: Thermal Zone [TZ00] (28 C)
[    0.535231] thermal LNXTHERM:01: registered as thermal_zone1
[    0.535294] ACPI: Thermal Zone [TZ01] (30 C)
[    0.535367] GHES: HEST is not enabled!
[    0.535478] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.536341] Linux agpgart interface v0.103
[    0.537079] brd: module loaded
[    0.537477] loop: module loaded
[    0.537727] libphy: Fixed MDIO Bus: probed
[    0.537830] tun: Universal TUN/TAP device driver, 1.6
[    0.537892] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.537973] PPP generic driver version 2.4.2
[    0.538057] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.538122] ehci-pci: EHCI PCI platform driver
[    0.538245] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    0.538310] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    0.538394] ehci-pci 0000:00:1a.0: debug port 2
[    0.542342] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    0.542352] ehci-pci 0000:00:1a.0: irq 16, io mem 0xdf137000
[    0.550988] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    0.551073] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.551137] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.551212] usb usb1: Product: EHCI Host Controller
[    0.551273] usb usb1: Manufacturer: Linux 3.13.0-36-generic ehci_hcd
[    0.551337] usb usb1: SerialNumber: 0000:00:1a.0
[    0.551452] hub 1-0:1.0: USB hub found
[    0.551514] hub 1-0:1.0: 2 ports detected
[    0.551678] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    0.551742] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.551825] ehci-pci 0000:00:1d.0: debug port 2
[    0.555787] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    0.555799] ehci-pci 0000:00:1d.0: irq 23, io mem 0xdf136000
[    0.567010] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    0.567090] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    0.567154] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.567230] usb usb2: Product: EHCI Host Controller
[    0.567291] usb usb2: Manufacturer: Linux 3.13.0-36-generic ehci_hcd
[    0.567355] usb usb2: SerialNumber: 0000:00:1d.0
[    0.567479] hub 2-0:1.0: USB hub found
[    0.567541] hub 2-0:1.0: 2 ports detected
[    0.567653] ehci-platform: EHCI generic platform driver
[    0.567718] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.567781] ohci-pci: OHCI PCI platform driver
[    0.567845] ohci-platform: OHCI generic platform driver
[    0.567909] uhci_hcd: USB Universal Host Controller Interface driver
[    0.568040] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.568103] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
[    0.568251] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    0.568264] xhci_hcd 0000:00:14.0: irq 41 for MSI/MSI-X
[    0.568300] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    0.568364] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.568440] usb usb3: Product: xHCI Host Controller
[    0.568501] usb usb3: Manufacturer: Linux 3.13.0-36-generic xhci_hcd
[    0.568564] usb usb3: SerialNumber: 0000:00:14.0
[    0.568684] hub 3-0:1.0: USB hub found
[    0.568757] hub 3-0:1.0: 14 ports detected
[    0.570979] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.571048] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 4
[    0.571149] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
[    0.571213] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.571288] usb usb4: Product: xHCI Host Controller
[    0.571350] usb usb4: Manufacturer: Linux 3.13.0-36-generic xhci_hcd
[    0.571413] usb usb4: SerialNumber: 0000:00:14.0
[    0.571532] hub 4-0:1.0: USB hub found
[    0.571602] hub 4-0:1.0: 6 ports detected
[    0.579063] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    0.581547] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.581615] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.581779] mousedev: PS/2 mouse device common for all mice
[    0.582024] rtc_cmos 00:06: RTC can wake from S4
[    0.582208] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.582294] rtc_cmos 00:06: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.582410] device-mapper: uevent: version 1.0.3
[    0.582536] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
[    0.582618] ledtrig-cpu: registered to indicate activity on CPUs
[    0.582743] TCP: cubic registered
[    0.582855] NET: Registered protocol family 10
[    0.583029] NET: Registered protocol family 17
[    0.583096] Key type dns_resolver registered
[    0.583353] Loading compiled-in X.509 certificates
[    0.583912] Loaded X.509 cert 'Magrathea: Glacier signing key: 38f3b6c63a85affdfbbe0e53339df8e0c6b6c9d5'
[    0.583997] registered taskstats version 1
[    0.585426] Key type trusted registered
[    0.586616] Key type encrypted registered
[    0.587802] AppArmor: AppArmor sha1 policy hashing enabled
[    0.587866] IMA: No TPM chip found, activating TPM-bypass!
[    0.588159] regulator-dummy: disabling
[    0.588298]   Magic number: 2:116:778
[    0.588452] rtc_cmos 00:06: setting system clock to 2014-10-12 09:45:50 UTC (1413107150)
[    0.589362] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.589425] EDD information not available.
[    0.589508] PM: Hibernation image not present or could not be loaded.
[    0.590004] Freeing unused kernel memory: 1336K (ffffffff81d1f000 - ffffffff81e6d000)
[    0.590081] Write protecting the kernel read-only data: 12288k
[    0.591366] Freeing unused kernel memory: 808K (ffff880001736000 - ffff880001800000)
[    0.592375] Freeing unused kernel memory: 692K (ffff880001b53000 - ffff880001c00000)
[    0.598748] systemd-udevd[144]: starting version 204
[    0.611252] pps_core: LinuxPPS API ver. 1 registered
[    0.611320] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
[    0.612459] PTP clock support registered
[    0.612605] ahci 0000:00:1f.2: version 3.0
[    0.612783] ahci 0000:00:1f.2: irq 42 for MSI/MSI-X
[    0.612829] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0xa impl SATA mode
[    0.612916] ahci 0000:00:1f.2: flags: 64bit ncq led clo pio slum part ems apst 
[    0.616129] e1000e: Intel(R) PRO/1000 Network Driver - 2.3.2-k
[    0.616206] e1000e: Copyright(c) 1999 - 2013 Intel Corporation.
[    0.619573] scsi0 : ahci
[    0.619700] scsi1 : ahci
[    0.619816] scsi2 : ahci
[    0.619966] scsi3 : ahci
[    0.620120] scsi4 : ahci
[    0.620240] scsi5 : ahci
[    0.620331] ata1: DUMMY
[    0.620398] ata2: SATA max UDMA/133 abar m2048@0xdf135000 port 0xdf135180 irq 42
[    0.620481] ata3: DUMMY
[    0.620548] ata4: SATA max UDMA/133 abar m2048@0xdf135000 port 0xdf135280 irq 42
[    0.625717] ata5: DUMMY
[    0.625775] ata6: DUMMY
[    0.626014] e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    0.626119] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[    0.791797] e1000e 0000:00:19.0 eth0: registered PHC clock
[    0.791863] e1000e 0000:00:19.0 eth0: (PCI Express:2.5GT/s:Width x1) 10:c3:7b:6c:40:28
[    0.791939] e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
[    0.792025] e1000e 0000:00:19.0 eth0: MAC: 11, PHY: 12, PBA No: FFFFFF-0FF
[    0.863450] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    0.943550] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    0.943628] ata4: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    0.944798] ata4.00: ATA-8: ST3000DM001-1CH166, CC24, max UDMA/133
[    0.944863] ata4.00: 5860533168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    0.945795] ata4.00: configured for UDMA/133
[    0.984973] ata2.00: ATA-8: WDC WD1600BEVT-22ZCT0, 11.01A11, max UDMA/133
[    0.985038] ata2.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    0.986484] ata2.00: configured for UDMA/133
[    0.986652] scsi 1:0:0:0: Direct-Access     ATA      WDC WD1600BEVT-2 11.0 PQ: 0 ANSI: 5
[    0.986814] sd 1:0:0:0: Attached scsi generic sg0 type 0
[    0.986850] sd 1:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    0.987013] sd 1:0:0:0: [sda] Write Protect is off
[    0.987092] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.987119] scsi 3:0:0:0: Direct-Access     ATA      ST3000DM001-1CH1 CC24 PQ: 0 ANSI: 5
[    0.987133] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.987384] sd 3:0:0:0: [sdb] 5860533168 512-byte logical blocks: (3.00 TB/2.72 TiB)
[    0.987392] sd 3:0:0:0: Attached scsi generic sg1 type 0
[    0.987544] sd 3:0:0:0: [sdb] 4096-byte physical blocks
[    0.987701] sd 3:0:0:0: [sdb] Write Protect is off
[    0.987764] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    0.987787] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.995962] usb 1-1: New USB device found, idVendor=8087, idProduct=8009
[    0.996027] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    0.996233] hub 1-1:1.0: USB hub found
[    0.996338] hub 1-1:1.0: 6 ports detected
[    1.022133]  sda: sda1 sda2 < sda5 >
[    1.022563] sd 1:0:0:0: [sda] Attached SCSI disk
[    1.042649]  sdb: sdb1 sdb2 sdb3
[    1.043085] sd 3:0:0:0: [sdb] Attached SCSI disk
[    1.107782] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    1.240282] usb 2-1: New USB device found, idVendor=8087, idProduct=8001
[    1.240347] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.240562] hub 2-1:1.0: USB hub found
[    1.240658] hub 2-1:1.0: 8 ports detected
[    1.344536] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    1.408198] usb 3-13: new low-speed USB device number 2 using xhci_hcd
[    1.429688] usb 3-13: New USB device found, idVendor=046d, idProduct=c31d
[    1.429754] usb 3-13: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.429829] usb 3-13: Product: USB Keyboard
[    1.429890] usb 3-13: Manufacturer: Logitech
[    1.430016] usb 3-13: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[    1.430095] usb 3-13: ep 0x82 - rounding interval to 1024 microframes, ep desc says 2040 microframes
[    1.512321] tsc: Refined TSC clocksource calibration: 3597.915 MHz
[    1.600457] usb 3-14: new low-speed USB device number 3 using xhci_hcd
[    1.621640] usb 3-14: New USB device found, idVendor=045e, idProduct=077d
[    1.621706] usb 3-14: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.621782] usb 3-14: Product: Comfort Mouse 6000
[    1.621843] usb 3-14: Manufacturer: Microsoft
[    1.621968] usb 3-14: ep 0x83 - rounding interval to 64 microframes, ep desc says 80 microframes
[    1.897796] random: nonblocking pool is initialized
[    2.513777] Switched to clocksource tsc
[   16.367542] Adding 16717820k swap on /dev/sda5.  Priority:-1 extents:1 across:16717820k FS
[   16.504592] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.577299] systemd-udevd[349]: starting version 204
[   16.813918] lp: driver loaded but no devices found
[   16.816462] ppdev: user-space parallel port driver
[   16.821525] wmi: Mapper loaded
[   16.836120] [drm] Initialized drm 1.1.0 20060810
[   16.836231] mei_me 0000:00:16.0: irq 44 for MSI/MSI-X
[   16.840559] nvidia: module license 'NVIDIA' taints kernel.
[   16.840561] Disabling lock debugging due to kernel taint
[   16.845055] nvidia: module verification failed: signature and/or  required key missing - tainting kernel
[   16.848690] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=none
[   16.849044] [drm] Initialized nvidia-drm 0.0.0 20130102 for 0000:01:00.0 on minor 0
[   16.849050] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  343.22  Thu Sep 11 16:27:43 PDT 2014
[   16.849503] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   16.859797] SKU: Nid=0x1d sku_cfg=0x4047e629
[   16.859798] SKU: port_connectivity=0x1
[   16.859799] SKU: enable_pcbeep=0x0
[   16.859799] SKU: check_sum=0x00000007
[   16.859800] SKU: customization=0x000000e6
[   16.859800] SKU: external_amp=0x5
[   16.859801] SKU: platform_type=0x0
[   16.859801] SKU: swap=0x0
[   16.859802] SKU: override=0x1
[   16.860207] autoconfig: line_outs=3 (0x14/0x15/0x16/0x0/0x0) type:line
[   16.860207]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   16.860208]    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[   16.860208]    mono: mono_out=0x0
[   16.860209]    dig-out=0x11/0x1e
[   16.860209]    inputs:
[   16.860210]      Front Mic=0x19
[   16.860211]      Rear Mic=0x18
[   16.860212]      Line=0x1a
[   16.860212] realtek: No valid SSID, checking pincfg 0x4047e629 for NID 0x1d
[   16.860213] realtek: Enabling init ASM_ID=0xe629 CODEC_ID=10ec0892
[   16.868204] systemd-udevd[380]: renamed network interface eth0 to eth1
[   16.869870] kvm: disabled by bios
[   16.876324] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   16.876540] input: HDA Intel PCH Line Out CLFE as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   16.876594] input: HDA Intel PCH Line Out Surround as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   16.876639] input: HDA Intel PCH Line Out Front as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   16.876711] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   16.876899] input: HDA Intel PCH Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   16.877110] input: HDA Intel PCH Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
[   16.877413] hda_intel: Disabling MSI
[   16.877419] hda-intel 0000:01:00.1: Handle VGA-switcheroo audio client
[   16.877448] hda-intel 0000:01:00.1: Disabling 64bit DMA
[   16.881599] hda-intel 0000:01:00.1: Enable delay in RIRB handling
[   16.885782] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   16.896326] type=1400 audit(1413107166.779:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=468 comm="apparmor_parser"
[   16.896328] type=1400 audit(1413107166.779:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=468 comm="apparmor_parser"
[   16.896330] type=1400 audit(1413107166.779:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=468 comm="apparmor_parser"
[   16.896530] type=1400 audit(1413107166.779:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=468 comm="apparmor_parser"
[   16.896532] type=1400 audit(1413107166.779:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=468 comm="apparmor_parser"
[   16.896634] type=1400 audit(1413107166.779:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=468 comm="apparmor_parser"
[   16.900448] asus_wmi: ASUS WMI generic driver loaded
[   16.901832] asus_wmi: Initialization: 0x0
[   16.901842] asus_wmi: BIOS WMI version: 0.9
[   16.901860] asus_wmi: SFUN value: 0x0
[   16.902025] input: Eee PC WMI hotkeys as /devices/platform/eeepc-wmi/input/input12
[   16.902558] asus_wmi: Disabling ACPI video driver
[   16.960071] hidraw: raw HID events driver (C) Jiri Kosina
[   16.971794] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[   16.975830] usbcore: registered new interface driver usbhid
[   16.975832] usbhid: USB HID core driver
[   16.976998] input: Logitech USB Keyboard as /devices/pci0000:00/0000:00:14.0/usb3/3-13/3-13:1.0/input/input13
[   16.977054] hid-generic 0003:046D:C31D.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Keyboard] on usb-0000:00:14.0-13/input0
[   16.978393] input: Logitech USB Keyboard as /devices/pci0000:00/0000:00:14.0/usb3/3-13/3-13:1.1/input/input14
[   16.978495] hid-generic 0003:046D:C31D.0002: input,hidraw1: USB HID v1.10 Device [Logitech USB Keyboard] on usb-0000:00:14.0-13/input1
[   16.978678] input: Microsoft Comfort Mouse 6000 as /devices/pci0000:00/0000:00:14.0/usb3/3-14/3-14:1.0/input/input15
[   16.978745] hid-generic 0003:045E:077D.0003: input,hidraw2: USB HID v1.11 Mouse [Microsoft Comfort Mouse 6000] on usb-0000:00:14.0-14/input0
[   17.049559] EXT4-fs (sdb3): mounted filesystem with ordered data mode. Opts: (null)
[   17.097572] EXT4-fs (sdb2): warning: maximal mount count reached, running e2fsck is recommended
[   17.099009] EXT4-fs (sdb2): mounted filesystem with ordered data mode. Opts: (null)
[   17.189575] init: failsafe main process (636) killed by TERM signal
[   17.318013] type=1400 audit(1413107167.203:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=821 comm="apparmor_parser"
[   17.318018] type=1400 audit(1413107167.203:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=821 comm="apparmor_parser"
[   17.318020] type=1400 audit(1413107167.203:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=821 comm="apparmor_parser"
[   17.318235] type=1400 audit(1413107167.203:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=821 comm="apparmor_parser"
[   17.350086] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input19
[   17.350146] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input18
[   17.350189] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input17
[   17.350231] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input16
[   17.879967] Bluetooth: Core ver 2.17
[   17.879988] NET: Registered protocol family 31
[   17.879989] Bluetooth: HCI device and connection manager initialized
[   17.879995] Bluetooth: HCI socket layer initialized
[   17.879997] Bluetooth: L2CAP socket layer initialized
[   17.880009] Bluetooth: SCO socket layer initialized
[   17.881406] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   17.881408] Bluetooth: BNEP filters: protocol multicast
[   17.881411] Bluetooth: BNEP socket layer initialized
[   17.882041] Bluetooth: RFCOMM TTY layer initialized
[   17.882044] Bluetooth: RFCOMM socket layer initialized
[   17.882047] Bluetooth: RFCOMM ver 1.11
[   17.984484] init: cups main process (892) killed by HUP signal
[   17.984489] init: cups main process ended, respawning
[   19.821524] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[   19.925620] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[   19.925694] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   19.925814] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   20.187572] init: samba-ad-dc main process (1174) terminated with status 1
[   20.571423] init: udev-fallback-graphics main process (1194) terminated with status 1
[   21.453264] e1000e: eth1 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
[   21.453268] e1000e 0000:00:19.0 eth1: 10/100 speed: disabling TSO
[   21.453294] IPv6: ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   21.944947] nvidia 0000:01:00.0: irq 46 for MSI/MSI-X
[   22.767087] init: plymouth-upstart-bridge main process ended, respawning
[   48.032986] audit_printk_skb: 150 callbacks suppressed
[   48.032988] type=1400 audit(1413107197.884:62): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=2326 comm="apparmor_parser"
[   48.032991] type=1400 audit(1413107197.884:63): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2326 comm="apparmor_parser"
[   48.033182] type=1400 audit(1413107197.884:64): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2326 comm="apparmor_parser"

```

---

### Post by buzzingrobot on 2014-10-12
I'd suspect that the delay isn't caused by activating swap, but by the previous entry: "Switched to clocksource tsc". A quick search will find many similar reports and a fair number of kernel bug reports.

---

### Post by tgalati4 on 2014-10-12
I agree with the buzzingrobot.  The real action in many log entries is the line before the one that you think is the problem.  Do a search with your motherboard model to see what comes up.

You can shrink swap to 1.1X RAM, 2XRAM, 4XRAM.  I don't think it will make a difference.  Only if you hibernate--put your machine to sleep and the contents of RAM gets written to swap.  It can take a long time to read during boot--almost as much time as a cold boot--so I never use it.  You can install *bootchart* and see a finer-grained boot-up sequence.

> tgalati4@Mint14-Extensa ~ $ apt-cache search bootchart
bootchart - boot sequence auditing
pybootchartgui - boot sequence visualisation

---

### Post by Goettschwan on 2014-10-14
Right, so what you want to say is that the time is "beginning this operation" ? I always thought it was "finished this operation". So in my case, the operation "switching to clocksource tsc" takes about fourteen seconds. 
I admit that this is a bit beyond my understanding of the system. 
Based on several bug reports out there, I have tried to load the system with several different parameters :
"hpet=off" "hpet=force clocksource=hpet" "noapci" "tpm_tis.force=1" to no different result. 
I tried "acpi=off" this results in a very different boot and a "kernel panic" message after a very short time. 

I have tried booting in recovery mode, and the clocksource tsc bug is not appearing there. I will try and go through the different kernels installed to see if there are any without this problem.

---

### Post by Goettschwan on 2014-10-14
Please see the attached bootchart pic. The delay seems to be caused by activity of ureadahead ?
[ATTACH=CONFIG]257217[/ATTACH]

---

### Post by Goettschwan on 2014-10-14
I have tried through the kernels installed on the machine by selecting them in grub, all (.24 .35 and .36) exhibit the same problem. The .36 recovery mode consistently boots much slower, but without this problem.
See attached log. Notice that it "switching to clocksource hpet" which I have previously tried to force with "hpet=force clocksource=hpet", is this a wrong command? It did not make a difference in booting. 


```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.13.0-36-generic (buildd@toyol) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #63-Ubuntu SMP Wed Sep 3 21:30:07 UTC 2014 (Ubuntu 3.13.0-36.63-generic 3.13.11.6)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-36-generic root=UUID=91af8f15-8417-4e8e-b890-bae091cd5072 ro recovery nomodeset
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009d7ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009d800-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000af101fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000af102000-0x00000000af108fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000af109000-0x00000000af561fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000af562000-0x00000000af9c3fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000af9c4000-0x00000000cdbb8fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000cdbb9000-0x00000000cddc8fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000cddc9000-0x00000000cdde9fff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000cddea000-0x00000000ce312fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000ce313000-0x00000000ceffefff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000cefff000-0x00000000ceffffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed03fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000042effffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.8 present.
[    0.000000] DMI: ASUS All Series/Z97-AR, BIOS 0702 04/23/2014
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x42f000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-E7FFF uncachable
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask 7C00000000 write-back
[    0.000000]   1 base 0400000000 mask 7FE0000000 write-back
[    0.000000]   2 base 0420000000 mask 7FF8000000 write-back
[    0.000000]   3 base 0428000000 mask 7FFC000000 write-back
[    0.000000]   4 base 042C000000 mask 7FFE000000 write-back
[    0.000000]   5 base 042E000000 mask 7FFF000000 write-back
[    0.000000]   6 base 00E0000000 mask 7FE0000000 uncachable
[    0.000000]   7 base 00D0000000 mask 7FF0000000 uncachable
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 16GB, type WB
[    0.000000] reg 1, base: 16GB, range: 512MB, type WB
[    0.000000] reg 2, base: 16896MB, range: 128MB, type WB
[    0.000000] reg 3, base: 17024MB, range: 64MB, type WB
[    0.000000] reg 4, base: 17088MB, range: 32MB, type WB
[    0.000000] reg 5, base: 17120MB, range: 16MB, type WB
[    0.000000] reg 6, base: 3584MB, range: 512MB, type UC
[    0.000000] reg 7, base: 3328MB, range: 256MB, type UC
[    0.000000] total RAM covered: 16368M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 32M     num_reg: 8      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 256MB, type WB
[    0.000000] reg 3, base: 4GB, range: 4GB, type WB
[    0.000000] reg 4, base: 8GB, range: 8GB, type WB
[    0.000000] reg 5, base: 16GB, range: 512MB, type WB
[    0.000000] reg 6, base: 16896MB, range: 256MB, type WB
[    0.000000] reg 7, base: 17136MB, range: 16MB, type UC
[    0.000000] e820: update [mem 0xd0000000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xcf000 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000fd8c0-0x000fd8cf] mapped at [ffff8800000fd8c0]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000097000] 97000 size 24576
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01fdf000, 0x01fdffff] PGTABLE
[    0.000000] BRK [0x01fe0000, 0x01fe0fff] PGTABLE
[    0.000000] BRK [0x01fe1000, 0x01fe1fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x42ee00000-0x42effffff]
[    0.000000]  [mem 0x42ee00000-0x42effffff] page 2M
[    0.000000] BRK [0x01fe2000, 0x01fe2fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x42c000000-0x42edfffff]
[    0.000000]  [mem 0x42c000000-0x42edfffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x400000000-0x42bffffff]
[    0.000000]  [mem 0x400000000-0x42bffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0xaf101fff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x3fffffff] page 2M
[    0.000000]  [mem 0x40000000-0x7fffffff] page 1G
[    0.000000]  [mem 0x80000000-0xaeffffff] page 2M
[    0.000000]  [mem 0xaf000000-0xaf101fff] page 4k
[    0.000000] init_memory_mapping: [mem 0xaf109000-0xaf561fff]
[    0.000000]  [mem 0xaf109000-0xaf1fffff] page 4k
[    0.000000]  [mem 0xaf200000-0xaf3fffff] page 2M
[    0.000000]  [mem 0xaf400000-0xaf561fff] page 4k
[    0.000000] BRK [0x01fe3000, 0x01fe3fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0xaf9c4000-0xcdbb8fff]
[    0.000000]  [mem 0xaf9c4000-0xaf9fffff] page 4k
[    0.000000]  [mem 0xafa00000-0xcd9fffff] page 2M
[    0.000000]  [mem 0xcda00000-0xcdbb8fff] page 4k
[    0.000000] BRK [0x01fe4000, 0x01fe4fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0xcefff000-0xceffffff]
[    0.000000]  [mem 0xcefff000-0xceffffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x100000000-0x3ffffffff]
[    0.000000]  [mem 0x100000000-0x3ffffffff] page 1G
[    0.000000] RAMDISK: [mem 0x35b5a000-0x36da4fff]
[    0.000000] ACPI: RSDP 00000000000f04a0 000024 (v02 ALASKA)
[    0.000000] ACPI: XSDT 00000000cddcf080 000074 (v01 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: FACP 00000000cdde1ae0 00010C (v05 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: DSDT 00000000cddcf188 012951 (v02 ALASKA    A M I 00000006 INTL 20120711)
[    0.000000] ACPI: FACS 00000000ce312f80 000040
[    0.000000] ACPI: APIC 00000000cdde1bf0 000092 (v03 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: FPDT 00000000cdde1c88 000044 (v01 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: SSDT 00000000cdde1cd0 000BEE (v01 Ther_R Ther_Rvp 00001000 INTL 20120711)
[    0.000000] ACPI: SSDT 00000000cdde28c0 000539 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.000000] ACPI: SSDT 00000000cdde2e00 000B74 (v01 CpuRef  CpuSsdt 00003000 INTL 20051117)
[    0.000000] ACPI: MCFG 00000000cdde3978 00003C (v01 ALASKA    A M I 01072009 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000cdde39b8 000038 (v01 ALASKA    A M I 01072009 AMI. 00000005)
[    0.000000] ACPI: SSDT 00000000cdde39f0 00036D (v01 SataRe SataTabl 00001000 INTL 20120711)
[    0.000000] ACPI: SSDT 00000000cdde3d60 005B5E (v01 SaSsdt  SaSsdt  00003000 INTL 20120711)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000042effffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x42effffff]
[    0.000000]   NODE_DATA [mem 0x42eff6000-0x42effafff]
[    0.000000]  [ffffea0000000000-ffffea0010bfffff] PMD -> [ffff88041e600000-ffff88042e5fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x42effffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009cfff]
[    0.000000]   node   0: [mem 0x00100000-0xaf101fff]
[    0.000000]   node   0: [mem 0xaf109000-0xaf561fff]
[    0.000000]   node   0: [mem 0xaf9c4000-0xcdbb8fff]
[    0.000000]   node   0: [mem 0xcefff000-0xceffffff]
[    0.000000]   node   0: [mem 0x100000000-0x42effffff]
[    0.000000] On node 0 totalpages: 4179693
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3996 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 13086 pages used for memmap
[    0.000000]   DMA32 zone: 837457 pages, LIFO batch:31
[    0.000000]   Normal zone: 52160 pages used for memmap
[    0.000000]   Normal zone: 3338240 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x1808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 8, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] smpboot: Allowing 8 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: [mem 0x0009d000-0x0009dfff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xaf102000-0xaf108fff]
[    0.000000] PM: Registered nosave memory: [mem 0xaf562000-0xaf9c3fff]
[    0.000000] PM: Registered nosave memory: [mem 0xcdbb9000-0xcddc8fff]
[    0.000000] PM: Registered nosave memory: [mem 0xcddc9000-0xcdde9fff]
[    0.000000] PM: Registered nosave memory: [mem 0xcddea000-0xce312fff]
[    0.000000] PM: Registered nosave memory: [mem 0xce313000-0xceffefff]
[    0.000000] PM: Registered nosave memory: [mem 0xcf000000-0xdfffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfecfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed00000-0xfed03fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed04000-0xfed1bfff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xfeffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xff000000-0xffffffff]
[    0.000000] e820: [mem 0xcf000000-0xdfffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 29 pages/cpu @ffff88042ec00000 s86336 r8192 d24256 u262144
[    0.000000] pcpu-alloc: s86336 r8192 d24256 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 4114362
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-36-generic root=UUID=91af8f15-8417-4e8e-b890-bae091cd5072 ro recovery nomodeset
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 16354260K/16718772K available (7373K kernel code, 1144K rwdata, 3404K rodata, 1336K init, 1440K bss, 364512K reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000]     Offload RCU callbacks from all CPUs
[    0.000000]     Offload RCU callbacks from CPUs: 0-7.
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 67108864 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.004000] tsc: Detected 3597.818 MHz processor
[    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 7195.63 BogoMIPS (lpj=14391272)
[    0.000129] pid_max: default: 32768 minimum: 301
[    0.000206] Security Framework initialized
[    0.000283] AppArmor: AppArmor initialized
[    0.000344] Yama: becoming mindful.
[    0.001071] Dentry cache hash table entries: 2097152 (order: 12, 16777216 bytes)
[    0.004303] Inode-cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.005803] Mount-cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.005879] Mountpoint-cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.006168] Initializing cgroup subsys memory
[    0.006233] Initializing cgroup subsys devices
[    0.006295] Initializing cgroup subsys freezer
[    0.006357] Initializing cgroup subsys blkio
[    0.006418] Initializing cgroup subsys perf_event
[    0.006481] Initializing cgroup subsys hugetlb
[    0.006556] CPU: Physical Processor ID: 0
[    0.006636] CPU: Processor Core ID: 0
[    0.006699] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.006699] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.007464] mce: CPU supports 9 MCE banks
[    0.007535] CPU0: Thermal monitoring enabled (TM1)
[    0.007604] Last level iTLB entries: 4KB 0, 2MB 0, 4MB 0
[    0.007604] Last level dTLB entries: 4KB 64, 2MB 0, 4MB 0
[    0.007604] tlb_flushall_shift: 6
[    0.007774] Freeing SMP alternatives memory: 32K (ffffffff81e6d000 - ffffffff81e75000)
[    0.008494] ACPI: Core revision 20131115
[    0.015787] ACPI: All ACPI Tables successfully acquired
[    0.031569] ftrace: allocating 28537 entries in 112 pages
[    0.039881] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=0 pin2=0
[    0.079681] smpboot: CPU0: Intel(R) Core(TM) i7-4790 CPU @ 3.60GHz (fam: 06, model: 3c, stepping: 03)
[    0.085004] TSC deadline timer enabled
[    0.085010] Performance Events: PEBS fmt2+, 16-deep LBR, Haswell events, full-width counters, Intel PMU driver.
[    0.085311] ... version:                3
[    0.085371] ... bit width:              48
[    0.085431] ... generic registers:      4
[    0.085491] ... value mask:             0000ffffffffffff
[    0.085553] ... max period:             0000ffffffffffff
[    0.085615] ... fixed-purpose events:   3
[    0.085675] ... event mask:             000000070000000f
[    0.086759] x86: Booting SMP configuration:
[    0.100857] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.086820] .... node  #0, CPUs:      #1 #2 #3 #4 #5 #6 #7
[    0.184656] x86: Booted up 1 node, 8 CPUs
[    0.184773] smpboot: Total of 8 processors activated (57565.08 BogoMIPS)
[    0.191295] devtmpfs: initialized
[    0.193009] EVM: security.selinux
[    0.193068] EVM: security.SMACK64
[    0.193127] EVM: security.ima
[    0.193187] EVM: security.capability
[    0.193270] PM: Registering ACPI NVS region [mem 0xaf102000-0xaf108fff] (28672 bytes)
[    0.193347] PM: Registering ACPI NVS region [mem 0xcddea000-0xce312fff] (5410816 bytes)
[    0.193916] pinctrl core: initialized pinctrl subsystem
[    0.194012] regulator-dummy: no parameters
[    0.194096] RTC time: 19:47:49, date: 10/14/14
[    0.194176] NET: Registered protocol family 16
[    0.194297] cpuidle: using governor ladder
[    0.194357] cpuidle: using governor menu
[    0.194438] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.194514] ACPI: bus type PCI registered
[    0.194574] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.194673] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.194753] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.210214] PCI: Using configuration type 1 for base access
[    0.210870] bio: create slab <bio-0> at 0
[    0.211026] ACPI: Added _OSI(Module Device)
[    0.211087] ACPI: Added _OSI(Processor Device)
[    0.211150] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.211211] ACPI: Added _OSI(Processor Aggregator Device)
[    0.214286] ACPI: Executed 15 blocks of module-level executable AML code
[    0.223268] ACPI: SSDT 00000000cdd77c18 0003D3 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.223790] ACPI: Dynamic OEM Table Load:
[    0.223940] ACPI: SSDT           (null) 0003D3 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.227336] ACPI: SSDT 00000000cdd77618 0005AA (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.227897] ACPI: Dynamic OEM Table Load:
[    0.228046] ACPI: SSDT           (null) 0005AA (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.235263] ACPI: SSDT 00000000cdd76d98 000119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.235780] ACPI: Dynamic OEM Table Load:
[    0.235930] ACPI: SSDT           (null) 000119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.240202] ACPI: Interpreter enabled
[    0.240266] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20131115/hwxface-580)
[    0.240435] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)
[    0.240612] ACPI: (supports S0 S3 S4 S5)
[    0.240672] ACPI: Using IOAPIC for interrupt routing
[    0.240751] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.240968] ACPI: No dock devices found.
[    0.241262] ACPI: Power Resource [PG00] (on)
[    0.243404] ACPI: Power Resource [PG01] (on)
[    0.247378] ACPI: Power Resource [PG02] (on)
[    0.255858] ACPI: Power Resource [FN00] (off)
[    0.255958] ACPI: Power Resource [FN01] (off)
[    0.256055] ACPI: Power Resource [FN02] (off)
[    0.256151] ACPI: Power Resource [FN03] (off)
[    0.256248] ACPI: Power Resource [FN04] (off)
[    0.256846] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[    0.256912] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.257118] acpi PNP0A08:00: _OSC: platform does not support [PCIeHotplug PME]
[    0.257270] acpi PNP0A08:00: _OSC: OS now controls [AER PCIeCapability]
[    0.257678] PCI host bridge to bus 0000:00
[    0.257739] pci_bus 0000:00: root bus resource [bus 00-fe]
[    0.257802] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.257865] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.257929] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.257993] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff]
[    0.258057] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
[    0.258121] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
[    0.258186] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff]
[    0.258250] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000e3fff]
[    0.258314] pci_bus 0000:00: root bus resource [mem 0x000e4000-0x000e7fff]
[    0.258379] pci_bus 0000:00: root bus resource [mem 0xd0000000-0xfeafffff]
[    0.258447] pci 0000:00:00.0: [8086:0c00] type 00 class 0x060000
[    0.258503] pci 0000:00:01.0: [8086:0c01] type 01 class 0x060400
[    0.258524] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.258559] pci 0000:00:01.0: System wakeup disabled by ACPI
[    0.258660] pci 0000:00:14.0: [8086:8cb1] type 00 class 0x0c0330
[    0.258675] pci 0000:00:14.0: reg 0x10: [mem 0xdf120000-0xdf12ffff 64bit]
[    0.258724] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    0.258761] pci 0000:00:14.0: System wakeup disabled by ACPI
[    0.258842] pci 0000:00:16.0: [8086:8cba] type 00 class 0x078000
[    0.258858] pci 0000:00:16.0: reg 0x10: [mem 0xdf13a000-0xdf13a00f 64bit]
[    0.258910] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.258964] pci 0000:00:19.0: [8086:15a1] type 00 class 0x020000
[    0.258977] pci 0000:00:19.0: reg 0x10: [mem 0xdf100000-0xdf11ffff]
[    0.258983] pci 0000:00:19.0: reg 0x14: [mem 0xdf138000-0xdf138fff]
[    0.258989] pci 0000:00:19.0: reg 0x18: [io  0xf040-0xf05f]
[    0.259038] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.259074] pci 0000:00:19.0: System wakeup disabled by ACPI
[    0.259157] pci 0000:00:1a.0: [8086:8cad] type 00 class 0x0c0320
[    0.259174] pci 0000:00:1a.0: reg 0x10: [mem 0xdf137000-0xdf1373ff]
[    0.259248] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.259287] pci 0000:00:1a.0: System wakeup disabled by ACPI
[    0.259371] pci 0000:00:1b.0: [8086:8ca0] type 00 class 0x040300
[    0.259382] pci 0000:00:1b.0: reg 0x10: [mem 0xdf130000-0xdf133fff 64bit]
[    0.259435] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.259470] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    0.259548] pci 0000:00:1c.0: [8086:8c90] type 01 class 0x060400
[    0.259600] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.259633] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.259713] pci 0000:00:1c.3: [8086:244e] type 01 class 0x060401
[    0.259766] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.259798] pci 0000:00:1c.3: System wakeup disabled by ACPI
[    0.259886] pci 0000:00:1d.0: [8086:8ca6] type 00 class 0x0c0320
[    0.259903] pci 0000:00:1d.0: reg 0x10: [mem 0xdf136000-0xdf1363ff]
[    0.259979] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.260016] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.260097] pci 0000:00:1f.0: [8086:8cc4] type 00 class 0x060100
[    0.260227] pci 0000:00:1f.2: [8086:8c82] type 00 class 0x010601
[    0.260239] pci 0000:00:1f.2: reg 0x10: [io  0xf090-0xf097]
[    0.260245] pci 0000:00:1f.2: reg 0x14: [io  0xf080-0xf083]
[    0.260250] pci 0000:00:1f.2: reg 0x18: [io  0xf070-0xf077]
[    0.260255] pci 0000:00:1f.2: reg 0x1c: [io  0xf060-0xf063]
[    0.260261] pci 0000:00:1f.2: reg 0x20: [io  0xf020-0xf03f]
[    0.260266] pci 0000:00:1f.2: reg 0x24: [mem 0xdf135000-0xdf1357ff]
[    0.260296] pci 0000:00:1f.2: PME# supported from D3hot
[    0.260337] pci 0000:00:1f.3: [8086:8ca2] type 00 class 0x0c0500
[    0.260348] pci 0000:00:1f.3: reg 0x10: [mem 0xdf134000-0xdf1340ff 64bit]
[    0.260364] pci 0000:00:1f.3: reg 0x20: [io  0xf000-0xf01f]
[    0.260442] pci 0000:01:00.0: [10de:1184] type 00 class 0x030000
[    0.260450] pci 0000:01:00.0: reg 0x10: [mem 0xde000000-0xdeffffff]
[    0.260458] pci 0000:01:00.0: reg 0x14: [mem 0xd0000000-0xd7ffffff 64bit pref]
[    0.260467] pci 0000:01:00.0: reg 0x1c: [mem 0xd8000000-0xd9ffffff 64bit pref]
[    0.260472] pci 0000:01:00.0: reg 0x24: [io  0xe000-0xe07f]
[    0.260478] pci 0000:01:00.0: reg 0x30: [mem 0xdf000000-0xdf07ffff pref]
[    0.260521] pci 0000:01:00.0: System wakeup disabled by ACPI
[    0.260602] pci 0000:01:00.1: [10de:0e0a] type 00 class 0x040300
[    0.260610] pci 0000:01:00.1: reg 0x10: [mem 0xdf080000-0xdf083fff]
[    0.267373] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.267435] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.267437] pci 0000:00:01.0:   bridge window [mem 0xde000000-0xdf0fffff]
[    0.267439] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xd9ffffff 64bit pref]
[    0.267492] acpiphp: Slot [1] registered
[    0.267555] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.267671] pci 0000:03:00.0: [1b21:1080] type 01 class 0x060401
[    0.267763] pci 0000:03:00.0: System wakeup disabled by ACPI
[    0.267838] pci 0000:00:1c.3: PCI bridge to [bus 03-04] (subtractive decode)
[    0.267909] pci 0000:00:1c.3:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.267910] pci 0000:00:1c.3:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.267911] pci 0000:00:1c.3:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.267912] pci 0000:00:1c.3:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
[    0.267913] pci 0000:00:1c.3:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.267913] pci 0000:00:1c.3:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.267914] pci 0000:00:1c.3:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
[    0.267915] pci 0000:00:1c.3:   bridge window [mem 0x000e0000-0x000e3fff] (subtractive decode)
[    0.267916] pci 0000:00:1c.3:   bridge window [mem 0x000e4000-0x000e7fff] (subtractive decode)
[    0.267917] pci 0000:00:1c.3:   bridge window [mem 0xd0000000-0xfeafffff] (subtractive decode)
[    0.268006] pci 0000:03:00.0: PCI bridge to [bus 04] (subtractive decode)
[    0.268085] pci 0000:03:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
[    0.268086] pci 0000:03:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
[    0.268087] pci 0000:03:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
[    0.268088] pci 0000:03:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
[    0.268089] pci 0000:03:00.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.268090] pci 0000:03:00.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.268091] pci 0000:03:00.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.268092] pci 0000:03:00.0:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
[    0.268092] pci 0000:03:00.0:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.268093] pci 0000:03:00.0:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.268094] pci 0000:03:00.0:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
[    0.268095] pci 0000:03:00.0:   bridge window [mem 0x000e0000-0x000e3fff] (subtractive decode)
[    0.268096] pci 0000:03:00.0:   bridge window [mem 0x000e4000-0x000e7fff] (subtractive decode)
[    0.268097] pci 0000:03:00.0:   bridge window [mem 0xd0000000-0xfeafffff] (subtractive decode)
[    0.268116] acpi PNP0A08:00: Disabling ASPM (FADT indicates it is unsupported)
[    0.268723] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.269343] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.269961] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 *6 7 10 11 12 14 15)
[    0.270578] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.271196] ACPI: PCI Interrupt Link [LNKE] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.271817] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 *15)
[    0.272435] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 *4 5 6 7 10 11 12 14 15)
[    0.273052] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 *14 15)
[    0.273892] ACPI: Enabled 6 GPEs in block 00 to 3F
[    0.274045] ACPI: \_SB_.PCI0: notify handler is installed
[    0.274095] Found 1 acpi root devices
[    0.274104] ACPI : EC: GPE = 0x1e, I/O: command/status = 0x66, data = 0x62
[    0.274220] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.274297] vgaarb: loaded
[    0.274355] vgaarb: bridge control possible 0000:01:00.0
[    0.274506] SCSI subsystem initialized
[    0.274590] libata version 3.00 loaded.
[    0.274600] ACPI: bus type USB registered
[    0.274668] usbcore: registered new interface driver usbfs
[    0.274734] usbcore: registered new interface driver hub
[    0.274820] usbcore: registered new device driver usb
[    0.274940] PCI: Using ACPI for IRQ routing
[    0.279943] PCI: pci_cache_line_size set to 64 bytes
[    0.279979] e820: reserve RAM buffer [mem 0x0009d800-0x0009ffff]
[    0.279980] e820: reserve RAM buffer [mem 0xaf102000-0xafffffff]
[    0.279981] e820: reserve RAM buffer [mem 0xaf562000-0xafffffff]
[    0.279981] e820: reserve RAM buffer [mem 0xcdbb9000-0xcfffffff]
[    0.279982] e820: reserve RAM buffer [mem 0xcf000000-0xcfffffff]
[    0.279983] e820: reserve RAM buffer [mem 0x42f000000-0x42fffffff]
[    0.280025] NetLabel: Initializing
[    0.280085] NetLabel:  domain hash size = 128
[    0.280145] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.280213] NetLabel:  unlabeled traffic allowed by default
[    0.280301] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.280763] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.282847] Switched to clocksource hpet
[    0.285702] AppArmor: AppArmor Filesystem Enabled
[    0.285771] pnp: PnP ACPI init
[    0.285839] ACPI: bus type PNP registered
[    0.285955] system 00:00: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.286020] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.286027] pnp 00:01: [dma 4]
[    0.286037] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.286046] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
[    0.286101] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.286123] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.286147] system 00:05: [io  0x0800-0x087f] has been reserved
[    0.286210] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.286222] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.286240] system 00:07: [io  0x1854-0x1857] has been reserved
[    0.286304] system 00:07: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.286354] system 00:08: [io  0x0290-0x029f] has been reserved
[    0.286417] system 00:08: [io  0x02a0-0x02af] has been reserved
[    0.286480] system 00:08: [io  0x0a00-0x0aff] has been reserved
[    0.286544] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.286574] system 00:09: [io  0x04d0-0x04d1] has been reserved
[    0.286637] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.286994] system 00:0a: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.287058] system 00:0a: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.287122] system 00:0a: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.287186] system 00:0a: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.287251] system 00:0a: [mem 0xe0000000-0xefffffff] has been reserved
[    0.287319] system 00:0a: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.287383] system 00:0a: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.287447] system 00:0a: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.287511] system 00:0a: [mem 0xff000000-0xffffffff] has been reserved
[    0.287575] system 00:0a: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.287640] system 00:0a: [mem 0xdffe0000-0xdffeffff] has been reserved
[    0.287704] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.287798] pnp: PnP ACPI: found 11 devices
[    0.287859] ACPI: bus type PNP unregistered
[    0.293390] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.293453] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.293518] pci 0000:00:01.0:   bridge window [mem 0xde000000-0xdf0fffff]
[    0.293583] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xd9ffffff 64bit pref]
[    0.293661] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.293729] pci 0000:03:00.0: PCI bridge to [bus 04]
[    0.293805] pci 0000:00:1c.3: PCI bridge to [bus 03-04]
[    0.293874] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.293875] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.293876] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.293877] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.293878] pci_bus 0000:00: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.293879] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.293880] pci_bus 0000:00: resource 10 [mem 0x000dc000-0x000dffff]
[    0.293881] pci_bus 0000:00: resource 11 [mem 0x000e0000-0x000e3fff]
[    0.293881] pci_bus 0000:00: resource 12 [mem 0x000e4000-0x000e7fff]
[    0.293882] pci_bus 0000:00: resource 13 [mem 0xd0000000-0xfeafffff]
[    0.293883] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.293884] pci_bus 0000:01: resource 1 [mem 0xde000000-0xdf0fffff]
[    0.293885] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xd9ffffff 64bit pref]
[    0.293886] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    0.293887] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
[    0.293888] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    0.293888] pci_bus 0000:03: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.293889] pci_bus 0000:03: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.293890] pci_bus 0000:03: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.293891] pci_bus 0000:03: resource 10 [mem 0x000dc000-0x000dffff]
[    0.293892] pci_bus 0000:03: resource 11 [mem 0x000e0000-0x000e3fff]
[    0.293893] pci_bus 0000:03: resource 12 [mem 0x000e4000-0x000e7fff]
[    0.293893] pci_bus 0000:03: resource 13 [mem 0xd0000000-0xfeafffff]
[    0.293894] pci_bus 0000:04: resource 8 [io  0x0000-0x0cf7]
[    0.293895] pci_bus 0000:04: resource 9 [io  0x0d00-0xffff]
[    0.293896] pci_bus 0000:04: resource 10 [mem 0x000a0000-0x000bffff]
[    0.293897] pci_bus 0000:04: resource 11 [mem 0x000d0000-0x000d3fff]
[    0.293898] pci_bus 0000:04: resource 12 [mem 0x000d4000-0x000d7fff]
[    0.293898] pci_bus 0000:04: resource 13 [mem 0x000d8000-0x000dbfff]
[    0.293899] pci_bus 0000:04: resource 14 [mem 0x000dc000-0x000dffff]
[    0.293900] pci_bus 0000:04: resource 15 [mem 0x000e0000-0x000e3fff]
[    0.293901] pci_bus 0000:04: resource 16 [mem 0x000e4000-0x000e7fff]
[    0.293902] pci_bus 0000:04: resource 17 [mem 0xd0000000-0xfeafffff]
[    0.293922] NET: Registered protocol family 2
[    0.294097] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.294376] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.294610] TCP: Hash tables configured (established 131072 bind 65536)
[    0.294687] TCP: reno registered
[    0.294758] UDP hash table entries: 8192 (order: 6, 262144 bytes)
[    0.294877] UDP-Lite hash table entries: 8192 (order: 6, 262144 bytes)
[    0.295023] NET: Registered protocol family 1
[    0.330979] pci 0000:01:00.0: Boot video device
[    0.330989] PCI: CLS 64 bytes, default 64
[    0.331019] Trying to unpack rootfs image as initramfs...
[    0.517571] Freeing initrd memory: 18732K (ffff880035b5a000 - ffff880036da5000)
[    0.517651] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.517715] software IO TLB [mem 0xc9bb9000-0xcdbb9000] (64MB) mapped at [ffff8800c9bb9000-ffff8800cdbb8fff]
[    0.517958] microcode: CPU0 sig=0x306c3, pf=0x2, revision=0x17
[    0.518026] microcode: CPU1 sig=0x306c3, pf=0x2, revision=0x17
[    0.518093] microcode: CPU2 sig=0x306c3, pf=0x2, revision=0x17
[    0.518159] microcode: CPU3 sig=0x306c3, pf=0x2, revision=0x17
[    0.518226] microcode: CPU4 sig=0x306c3, pf=0x2, revision=0x17
[    0.518292] microcode: CPU5 sig=0x306c3, pf=0x2, revision=0x17
[    0.518358] microcode: CPU6 sig=0x306c3, pf=0x2, revision=0x17
[    0.518425] microcode: CPU7 sig=0x306c3, pf=0x2, revision=0x17
[    0.518515] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.518593] Scanning for low memory corruption every 60 seconds
[    0.518831] Initialise system trusted keyring
[    0.518918] audit: initializing netlink socket (disabled)
[    0.518986] type=2000 audit(1413316069.488:1): initialized
[    0.535578] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.536350] zbud: loaded
[    0.536491] VFS: Disk quotas dquot_6.5.2
[    0.536577] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.536874] fuse init (API version 7.22)
[    0.536973] msgmni has been set to 31978
[    0.537066] Key type big_key registered
[    0.537405] Key type asymmetric registered
[    0.537466] Asymmetric key parser 'x509' registered
[    0.537542] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.537650] io scheduler noop registered
[    0.537712] io scheduler deadline registered (default)
[    0.537785] io scheduler cfq registered
[    0.537961] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.538056] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.538127] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.538212] intel_idle: MWAIT substates: 0x42120
[    0.538213] intel_idle: v0.4 model 0x3C
[    0.538214] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.538322] ipmi message handler version 39.2
[    0.538428] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.538507] ACPI: Power Button [PWRB]
[    0.538583] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.538660] ACPI: Power Button [PWRF]
[    0.538750] ACPI: Fan [FAN0] (off)
[    0.538822] ACPI: Fan [FAN1] (off)
[    0.538893] ACPI: Fan [FAN2] (off)
[    0.538966] ACPI: Fan [FAN3] (off)
[    0.539035] ACPI: Fan [FAN4] (off)
[    0.539355] thermal LNXTHERM:00: registered as thermal_zone0
[    0.539418] ACPI: Thermal Zone [TZ00] (28 C)
[    0.539587] thermal LNXTHERM:01: registered as thermal_zone1
[    0.539649] ACPI: Thermal Zone [TZ01] (30 C)
[    0.539723] GHES: HEST is not enabled!
[    0.539833] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.540706] Linux agpgart interface v0.103
[    0.541443] brd: module loaded
[    0.541839] loop: module loaded
[    0.542089] libphy: Fixed MDIO Bus: probed
[    0.542193] tun: Universal TUN/TAP device driver, 1.6
[    0.542254] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.542335] PPP generic driver version 2.4.2
[    0.542420] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.542486] ehci-pci: EHCI PCI platform driver
[    0.542609] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    0.542674] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    0.542758] ehci-pci 0000:00:1a.0: debug port 2
[    0.546733] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    0.546743] ehci-pci 0000:00:1a.0: irq 16, io mem 0xdf137000
[    0.555229] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    0.555314] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.555378] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.555454] usb usb1: Product: EHCI Host Controller
[    0.555515] usb usb1: Manufacturer: Linux 3.13.0-36-generic ehci_hcd
[    0.555579] usb usb1: SerialNumber: 0000:00:1a.0
[    0.555691] hub 1-0:1.0: USB hub found
[    0.555754] hub 1-0:1.0: 2 ports detected
[    0.555917] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    0.555981] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.556065] ehci-pci 0000:00:1d.0: debug port 2
[    0.560027] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    0.560037] ehci-pci 0000:00:1d.0: irq 23, io mem 0xdf136000
[    0.571250] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    0.571331] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    0.571395] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.571471] usb usb2: Product: EHCI Host Controller
[    0.571532] usb usb2: Manufacturer: Linux 3.13.0-36-generic ehci_hcd
[    0.571595] usb usb2: SerialNumber: 0000:00:1d.0
[    0.571718] hub 2-0:1.0: USB hub found
[    0.571780] hub 2-0:1.0: 2 ports detected
[    0.571891] ehci-platform: EHCI generic platform driver
[    0.571956] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.572019] ohci-pci: OHCI PCI platform driver
[    0.572083] ohci-platform: OHCI generic platform driver
[    0.572147] uhci_hcd: USB Universal Host Controller Interface driver
[    0.572278] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.572341] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
[    0.572489] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    0.572501] xhci_hcd 0000:00:14.0: irq 41 for MSI/MSI-X
[    0.572538] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    0.572602] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.572678] usb usb3: Product: xHCI Host Controller
[    0.572739] usb usb3: Manufacturer: Linux 3.13.0-36-generic xhci_hcd
[    0.572803] usb usb3: SerialNumber: 0000:00:14.0
[    0.572924] hub 3-0:1.0: USB hub found
[    0.572997] hub 3-0:1.0: 14 ports detected
[    0.575216] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.575287] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 4
[    0.575388] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
[    0.575452] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.575528] usb usb4: Product: xHCI Host Controller
[    0.575589] usb usb4: Manufacturer: Linux 3.13.0-36-generic xhci_hcd
[    0.575653] usb usb4: SerialNumber: 0000:00:14.0
[    0.575772] hub 4-0:1.0: USB hub found
[    0.575843] hub 4-0:1.0: 6 ports detected
[    0.583304] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    0.585887] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.585955] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.586125] mousedev: PS/2 mouse device common for all mice
[    0.586366] rtc_cmos 00:06: RTC can wake from S4
[    0.586550] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.586636] rtc_cmos 00:06: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.586750] device-mapper: uevent: version 1.0.3
[    0.586875] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
[    0.586957] ledtrig-cpu: registered to indicate activity on CPUs
[    0.587081] TCP: cubic registered
[    0.587188] NET: Registered protocol family 10
[    0.587355] NET: Registered protocol family 17
[    0.587420] Key type dns_resolver registered
[    0.587679] Loading compiled-in X.509 certificates
[    0.588239] Loaded X.509 cert 'Magrathea: Glacier signing key: 38f3b6c63a85affdfbbe0e53339df8e0c6b6c9d5'
[    0.588324] registered taskstats version 1
[    0.589849] Key type trusted registered
[    0.591075] Key type encrypted registered
[    0.592226] AppArmor: AppArmor sha1 policy hashing enabled
[    0.592291] IMA: No TPM chip found, activating TPM-bypass!
[    0.592583] regulator-dummy: disabling
[    0.592720]   Magic number: 2:329:799
[    0.592812] ec PNP0C09:00: hash matches
[    0.592935] rtc_cmos 00:06: setting system clock to 2014-10-14 19:47:50 UTC (1413316070)
[    0.593921] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.594004] EDD information not available.
[    0.594083] PM: Hibernation image not present or could not be loaded.
[    0.594619] Freeing unused kernel memory: 1336K (ffffffff81d1f000 - ffffffff81e6d000)
[    0.594696] Write protecting the kernel read-only data: 12288k
[    0.595976] Freeing unused kernel memory: 808K (ffff880001736000 - ffff880001800000)
[    0.596989] Freeing unused kernel memory: 692K (ffff880001b53000 - ffff880001c00000)
[    0.607034] systemd-udevd[160]: starting version 204
[    0.618822] pps_core: LinuxPPS API ver. 1 registered
[    0.618888] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
[    0.619801] PTP clock support registered
[    0.621038] ahci 0000:00:1f.2: version 3.0
[    0.621152] ahci 0000:00:1f.2: irq 42 for MSI/MSI-X
[    0.621191] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0xa impl SATA mode
[    0.621282] ahci 0000:00:1f.2: flags: 64bit ncq led clo pio slum part ems apst 
[    0.622160] e1000e: Intel(R) PRO/1000 Network Driver - 2.3.2-k
[    0.622232] e1000e: Copyright(c) 1999 - 2013 Intel Corporation.
[    0.627804] scsi0 : ahci
[    0.627944] scsi1 : ahci
[    0.628069] scsi2 : ahci
[    0.628176] scsi3 : ahci
[    0.628301] scsi4 : ahci
[    0.628412] scsi5 : ahci
[    0.628519] ata1: DUMMY
[    0.628588] ata2: SATA max UDMA/133 abar m2048@0xdf135000 port 0xdf135180 irq 42
[    0.628669] ata3: DUMMY
[    0.633720] ata4: SATA max UDMA/133 abar m2048@0xdf135000 port 0xdf135280 irq 42
[    0.633796] ata5: DUMMY
[    0.633854] ata6: DUMMY
[    0.634079] e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    0.634211] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[    0.800027] e1000e 0000:00:19.0 eth0: registered PHC clock
[    0.800094] e1000e 0000:00:19.0 eth0: (PCI Express:2.5GT/s:Width x1) 10:c3:7b:6c:40:28
[    0.800171] e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
[    0.800257] e1000e 0000:00:19.0 eth0: MAC: 11, PHY: 12, PBA No: FFFFFF-0FF
[    0.867695] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    0.951796] ata4: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    0.951873] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    0.952489] ata4.00: ATA-8: ST3000DM001-1CH166, CC24, max UDMA/133
[    0.952554] ata4.00: 5860533168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    0.953250] ata4.00: configured for UDMA/133
[    1.000217] usb 1-1: New USB device found, idVendor=8087, idProduct=8009
[    1.000283] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.000490] hub 1-1:1.0: USB hub found
[    1.000603] hub 1-1:1.0: 6 ports detected
[    1.001345] ata2.00: ATA-8: WDC WD1600BEVT-22ZCT0, 11.01A11, max UDMA/133
[    1.001412] ata2.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.002849] ata2.00: configured for UDMA/133
[    1.003016] scsi 1:0:0:0: Direct-Access     ATA      WDC WD1600BEVT-2 11.0 PQ: 0 ANSI: 5
[    1.003191] sd 1:0:0:0: Attached scsi generic sg0 type 0
[    1.003194] sd 1:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.003340] sd 1:0:0:0: [sda] Write Protect is off
[    1.003341] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.003399] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.003608] scsi 3:0:0:0: Direct-Access     ATA      ST3000DM001-1CH1 CC24 PQ: 0 ANSI: 5
[    1.003760] sd 3:0:0:0: Attached scsi generic sg1 type 0
[    1.003799] sd 3:0:0:0: [sdb] 5860533168 512-byte logical blocks: (3.00 TB/2.72 TiB)
[    1.003800] sd 3:0:0:0: [sdb] 4096-byte physical blocks
[    1.003915] sd 3:0:0:0: [sdb] Write Protect is off
[    1.003916] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.003949] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.038563]  sda: sda1 sda2 < sda5 >
[    1.038741]  sdb: sdb1 sdb2 sdb3
[    1.039037] sd 1:0:0:0: [sda] Attached SCSI disk
[    1.039164] sd 3:0:0:0: [sdb] Attached SCSI disk
[    1.116023] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    1.252570] usb 2-1: New USB device found, idVendor=8087, idProduct=8001
[    1.252635] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.252840] hub 2-1:1.0: USB hub found
[    1.252936] hub 2-1:1.0: 8 ports detected
[    1.361045] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    1.420466] usb 3-13: new low-speed USB device number 2 using xhci_hcd
[    1.442007] usb 3-13: New USB device found, idVendor=046d, idProduct=c31d
[    1.442072] usb 3-13: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.442148] usb 3-13: Product: USB Keyboard
[    1.442208] usb 3-13: Manufacturer: Logitech
[    1.442327] usb 3-13: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[    1.442406] usb 3-13: ep 0x82 - rounding interval to 1024 microframes, ep desc says 2040 microframes
[    1.516561] tsc: Refined TSC clocksource calibration: 3597.915 MHz
[    1.612724] usb 3-14: new low-speed USB device number 3 using xhci_hcd
[    1.633971] usb 3-14: New USB device found, idVendor=045e, idProduct=077d
[    1.634037] usb 3-14: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.634113] usb 3-14: Product: Comfort Mouse 6000
[    1.634175] usb 3-14: Manufacturer: Microsoft
[    1.634300] usb 3-14: ep 0x83 - rounding interval to 64 microframes, ep desc says 80 microframes
[    1.969375] random: nonblocking pool is initialized
[    2.518026] Switched to clocksource tsc
[    3.798283] systemd-udevd[293]: starting version 204
[    4.463009] wmi: Mapper loaded
[    4.532764] systemd-udevd[302]: renamed network interface eth0 to eth1
[    4.993390] mei_me 0000:00:16.0: irq 44 for MSI/MSI-X
[    5.135540] asus_wmi: ASUS WMI generic driver loaded
[    5.150525] kvm: disabled by bios
[    5.191877] [drm] Initialized drm 1.1.0 20060810
[    5.214750] asus_wmi: Initialization: 0x0
[    5.214821] asus_wmi: BIOS WMI version: 0.9
[    5.214898] asus_wmi: SFUN value: 0x0
[    5.215104] input: Eee PC WMI hotkeys as /devices/platform/eeepc-wmi/input/input5
[    5.215737] asus_wmi: Disabling ACPI video driver
[    5.520991] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[    5.691535] SKU: Nid=0x1d sku_cfg=0x4047e629
[    5.691600] SKU: port_connectivity=0x1
[    5.691659] SKU: enable_pcbeep=0x0
[    5.691719] SKU: check_sum=0x00000007
[    5.691778] SKU: customization=0x000000e6
[    5.691838] SKU: external_amp=0x5
[    5.691897] SKU: platform_type=0x0
[    5.691956] SKU: swap=0x0
[    5.692013] SKU: override=0x1
[    5.692445] autoconfig: line_outs=3 (0x14/0x15/0x16/0x0/0x0) type:line
[    5.692508]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    5.692570]    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[    5.692638]    mono: mono_out=0x0
[    5.692697]    dig-out=0x11/0x1e
[    5.692756]    inputs:
[    5.692814]      Front Mic=0x19
[    5.692873]      Rear Mic=0x18
[    5.692932]      Line=0x1a
[    5.692990] realtek: No valid SSID, checking pincfg 0x4047e629 for NID 0x1d
[    5.693054] realtek: Enabling init ASM_ID=0xe629 CODEC_ID=10ec0892
[    5.703490] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[    5.703615] input: HDA Intel PCH Line Out CLFE as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[    5.703727] input: HDA Intel PCH Line Out Surround as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[    5.703837] input: HDA Intel PCH Line Out Front as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[    5.703948] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[    5.704056] input: HDA Intel PCH Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[    5.704166] input: HDA Intel PCH Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[    5.704445] hda_intel: Disabling MSI
[    5.704509] hda-intel 0000:01:00.1: Handle VGA-switcheroo audio client
[    5.704595] hda-intel 0000:01:00.1: Disabling 64bit DMA
[    5.707908] hda-intel 0000:01:00.1: Enable delay in RIRB handling
[    6.144025] nvidia: module license 'NVIDIA' taints kernel.
[    6.144091] Disabling lock debugging due to kernel taint
[    6.147490] nvidia: module verification failed: signature and/or  required key missing - tainting kernel
[    6.194029] hidraw: raw HID events driver (C) Jiri Kosina
[    6.243329] usbcore: registered new interface driver usbhid
[    6.243392] usbhid: USB HID core driver
[    6.259094] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input16
[    6.259244] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input15
[    6.259391] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input14
[    6.259532] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input13
[    6.259909] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=none
[    6.263080] [drm] Initialized nvidia-drm 0.0.0 20130102 for 0000:01:00.0 on minor 0
[    6.263162] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  343.22  Thu Sep 11 16:27:43 PDT 2014
[    6.274859] input: Logitech USB Keyboard as /devices/pci0000:00/0000:00:14.0/usb3/3-13/3-13:1.0/input/input17
[    6.274997] hid-generic 0003:046D:C31D.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Keyboard] on usb-0000:00:14.0-13/input0
[    6.276343] input: Logitech USB Keyboard as /devices/pci0000:00/0000:00:14.0/usb3/3-13/3-13:1.1/input/input18
[    6.276550] hid-generic 0003:046D:C31D.0002: input,hidraw1: USB HID v1.10 Device [Logitech USB Keyboard] on usb-0000:00:14.0-13/input1
[    6.276807] input: Microsoft Comfort Mouse 6000 as /devices/pci0000:00/0000:00:14.0/usb3/3-14/3-14:1.0/input/input19
[    6.276970] hid-generic 0003:045E:077D.0003: input,hidraw2: USB HID v1.11 Mouse [Microsoft Comfort Mouse 6000] on usb-0000:00:14.0-14/input0
[    6.811665] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   11.185360] init: plymouth-upstart-bridge main process (695) terminated with status 1
[   11.185366] init: plymouth-upstart-bridge main process ended, respawning
[   11.191315] init: plymouth-upstart-bridge main process (712) terminated with status 1
[   11.191321] init: plymouth-upstart-bridge main process ended, respawning
[   11.195582] init: plymouth-upstart-bridge main process (728) terminated with status 1
[   11.195589] init: plymouth-upstart-bridge main process ended, respawning
[   11.200391] init: plymouth-upstart-bridge main process (743) terminated with status 1
[   11.200399] init: plymouth-upstart-bridge main process ended, respawning
[   11.204127] init: plymouth-upstart-bridge main process (745) terminated with status 1
[   11.204134] init: plymouth-upstart-bridge main process ended, respawning
[   11.207159] init: plymouth-upstart-bridge main process (748) terminated with status 1
[   11.207167] init: plymouth-upstart-bridge main process ended, respawning
[   11.212026] init: plymouth-upstart-bridge main process (755) terminated with status 1
[   11.212033] init: plymouth-upstart-bridge main process ended, respawning
[   11.215668] init: plymouth-upstart-bridge main process (759) terminated with status 1
[   11.215675] init: plymouth-upstart-bridge main process ended, respawning
[   11.219372] init: plymouth-upstart-bridge main process (761) terminated with status 1
[   11.219379] init: plymouth-upstart-bridge main process ended, respawning
[   11.221258] kvm: disabled by bios
[   11.223419] init: plymouth-upstart-bridge main process (764) terminated with status 1
[   11.223426] init: plymouth-upstart-bridge main process ended, respawning
[   11.227817] init: plymouth-upstart-bridge main process (766) terminated with status 1
[   11.227823] init: plymouth-upstart-bridge respawning too fast, stopped
[   11.414143] lp: driver loaded but no devices found
[   11.425628] ppdev: user-space parallel port driver
[   12.537899] init: udev-fallback-graphics main process (834) terminated with status 1
[   23.487375] Adding 16717820k swap on /dev/sda5.  Priority:-1 extents:1 across:16717820k FS
[   23.754956] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   23.804081] EXT4-fs (sdb2): warning: maximal mount count reached, running e2fsck is recommended
[   23.805547] EXT4-fs (sdb2): recovery complete
[   23.805549] EXT4-fs (sdb2): mounted filesystem with ordered data mode. Opts: (null)
[   23.819412] EXT4-fs (sdb1): recovery complete
[   23.819414] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[   23.878984] EXT4-fs (sdb3): recovery complete
[   23.878987] EXT4-fs (sdb3): mounted filesystem with ordered data mode. Opts: (null)
[   24.204694] init: friendly-recovery post-stop process (689) terminated with status 1
[   24.204850] init: failsafe main process (1041) killed by TERM signal
[   25.135923] type=1400 audit(1413316095.004:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=1141 comm="apparmor_parser"
[   25.135926] type=1400 audit(1413316095.004:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1141 comm="apparmor_parser"
[   25.135928] type=1400 audit(1413316095.004:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1141 comm="apparmor_parser"
[   25.136118] type=1400 audit(1413316095.004:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1141 comm="apparmor_parser"
[   25.136120] type=1400 audit(1413316095.004:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1141 comm="apparmor_parser"
[   25.136218] type=1400 audit(1413316095.004:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1141 comm="apparmor_parser"
[   25.137705] type=1400 audit(1413316095.008:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cups-browsed" pid=1145 comm="apparmor_parser"
[   25.138286] type=1400 audit(1413316095.008:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=1146 comm="apparmor_parser"
[   25.138290] type=1400 audit(1413316095.008:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=1146 comm="apparmor_parser"
[   25.138484] type=1400 audit(1413316095.008:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1146 comm="apparmor_parser"
[   27.375963] Bluetooth: Core ver 2.17
[   27.375973] NET: Registered protocol family 31
[   27.375973] Bluetooth: HCI device and connection manager initialized
[   27.375979] Bluetooth: HCI socket layer initialized
[   27.375980] Bluetooth: L2CAP socket layer initialized
[   27.375983] Bluetooth: SCO socket layer initialized
[   27.432611] Bluetooth: RFCOMM TTY layer initialized
[   27.432619] Bluetooth: RFCOMM socket layer initialized
[   27.432622] Bluetooth: RFCOMM ver 1.11
[   27.656914] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   27.656915] Bluetooth: BNEP filters: protocol multicast
[   27.656922] Bluetooth: BNEP socket layer initialized
[   29.700353] init: samba-ad-dc main process (1443) terminated with status 1
[   29.767401] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[   29.871450] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[   29.871527] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   29.871656] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   31.399082] e1000e: eth1 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
[   31.399085] e1000e 0000:00:19.0 eth1: 10/100 speed: disabling TSO
[   31.399112] IPv6: ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   32.517048] nvidia 0000:01:00.0: irq 46 for MSI/MSI-X
```

---

