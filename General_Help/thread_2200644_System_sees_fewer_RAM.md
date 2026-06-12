---
title: "System sees fewer RAM"
date: 2014-01-20
forum: General Help
---

### Post by michael95 on 2014-01-20
Hi everyone i am new at the forums of ubuntu
thanks for giving me the oppurtunity to discuss with u a weird 
problem with my computer 

Cause of the weird nature of the problem i really dont know which sub-forum was the 
correct in order to post
so if i am in wrong sub-forum please inform me 

i will try to explain to you the problem
i want to be patience thanks

I have in my system 4 GB memory ram installed
the BIOS UEFI one sees 4096 which is the correct number
of the total amount of memory 

and here the weird thing begins

My Windows (windows 8.1) and Linux 12.04 LTS x64bit sees that i lose about 32 MB of memory 
without knowing where it goes at all

I have done the following

1)Updating Bios at the latest one Motherboard is P8Z68-V Pro/Gen3
2)I have reset the bios by removing the battery and setting everything to default
3)I have remove the vga card (Nvidia GTX 650 Ti) and checking the onboard card which works
4)i have test if computer get confused between the vga cards by increasing the size of the onboard card but no problem with this
5)I have removing and resitting the RAM modules in a different positions with no luck

The computer is open a lot of hours and had not crash i have stress it with heavy multiplayer games
for about 2-3 days nothing suspicious 

here are some output from the terminal
A)Free -M command
```

:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3921       2054       1866          0         52        883
-/+ buffers/cache:       1119       2802
Swap:         4060          0       4060
:~$ 

```

B)Dmesg output

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.8.0-29-generic (buildd@panlong) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #42~precise1-Ubuntu SMP Wed Aug 14 16:19:23 UTC 2013 (Ubuntu 3.8.0-29.42~precise1-generic 3.8.13.5)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-29-generic root=UUID=01383357-1a1e-49b8-8829-b7b712c7132e ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009ebff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009ec00-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000deb8ffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000deb90000-0x00000000dedf6fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000dedf7000-0x00000000dee7afff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000dee7b000-0x00000000df13ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000df140000-0x00000000df384fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000df385000-0x00000000df392fff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000df393000-0x00000000df3bffff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000df3c0000-0x00000000df3c4fff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000df3c5000-0x00000000df407fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000df408000-0x00000000df7fffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed03fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000011effffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.6 present.
[    0.000000] DMI: System manufacturer System Product Name/P8Z68-V PRO GEN3, BIOS 3603 11/09/2012
[    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x11f000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-E7FFF uncachable
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F00000000 write-back
[    0.000000]   1 base 100000000 mask FF0000000 write-back
[    0.000000]   2 base 110000000 mask FF8000000 write-back
[    0.000000]   3 base 118000000 mask FFC000000 write-back
[    0.000000]   4 base 11C000000 mask FFE000000 write-back
[    0.000000]   5 base 11E000000 mask FFF000000 write-back
[    0.000000]   6 base 0E0000000 mask FE0000000 uncachable
[    0.000000]   7 disabled
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 4GB, type WB
[    0.000000] reg 1, base: 4GB, range: 256MB, type WB
[    0.000000] reg 2, base: 4352MB, range: 128MB, type WB
[    0.000000] reg 3, base: 4480MB, range: 64MB, type WB
[    0.000000] reg 4, base: 4544MB, range: 32MB, type WB
[    0.000000] reg 5, base: 4576MB, range: 16MB, type WB
[    0.000000] reg 6, base: 3584MB, range: 512MB, type UC
[    0.000000] total RAM covered: 4080M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 32M     num_reg: 5      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 512MB, type WB
[    0.000000] reg 3, base: 4GB, range: 512MB, type WB
[    0.000000] reg 4, base: 4592MB, range: 16MB, type UC
[    0.000000] e820: update [mem 0xe0000000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xdf800 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000fcd90-0x000fcd9f] mapped at [ffff8800000fcd90]
[    0.000000] initial memory mapped: [mem 0x00000000-0x1fffffff]
[    0.000000] Base memory trampoline at [ffff880000098000] 98000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0xdf7fffff]
[    0.000000]  [mem 0x00000000-0xdf7fffff] page 2M
[    0.000000] kernel direct mapping tables up to 0xdf7fffff @ [mem 0x1fffb000-0x1fffffff]
[    0.000000] init_memory_mapping: [mem 0x100000000-0x11effffff]
[    0.000000]  [mem 0x100000000-0x11effffff] page 2M
[    0.000000] kernel direct mapping tables up to 0x11effffff @ [mem 0xdf7fe000-0xdf7fffff]
[    0.000000] RAMDISK: [mem 0x36104000-0x37079fff]
[    0.000000] ACPI: RSDP 00000000000f0450 00024 (v02 ALASKA)
[    0.000000] ACPI: XSDT 00000000df385078 0006C (v01 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: FACP 00000000df390c80 000F4 (v04 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: DSDT 00000000df385180 0BAFE (v02 ALASKA    A M I 00000015 INTL 20051117)
[    0.000000] ACPI: FACS 00000000df3bef80 00040
[    0.000000] ACPI: APIC 00000000df390d78 00072 (v03 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: MCFG 00000000df390df0 0003C (v01 ALASKA    A M I 01072009 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000df390e30 00038 (v01 ALASKA    A M I 01072009 AMI. 00000005)
[    0.000000] ACPI: SSDT 00000000df390e68 00460 (v01 IdeRef IdeTable 00001000 INTL 20091112)
[    0.000000] ACPI: SSDT 00000000df3912c8 009AA (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.000000] ACPI: SSDT 00000000df391c78 00A92 (v01  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: DMAR 00000000df392710 00078 (v01 INTEL      SNB  00000001 INTL 00000001)
[    0.000000] ACPI: BGRT 00000000df3927e0 00038 (v00 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000011effffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x11effffff]
[    0.000000]   NODE_DATA [mem 0x11effb000-0x11effffff]
[    0.000000]  [ffffea0000000000-ffffea00047fffff] PMD -> [ffff88011a600000-ffff88011e5fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00010000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x11effffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00010000-0x0009dfff]
[    0.000000]   node   0: [mem 0x00100000-0xdeb8ffff]
[    0.000000]   node   0: [mem 0xdf408000-0xdf7fffff]
[    0.000000]   node   0: [mem 0x100000000-0x11effffff]
[    0.000000] On node 0 totalpages: 1040150
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 6 pages reserved
[    0.000000]   DMA zone: 3912 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14207 pages used for memmap
[    0.000000]   DMA32 zone: 894985 pages, LIFO batch:31
[    0.000000]   Normal zone: 1984 pages used for memmap
[    0.000000]   Normal zone: 124992 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
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
[    0.000000] smpboot: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000deb90000 - 00000000dedf7000
[    0.000000] PM: Registered nosave memory: 00000000dedf7000 - 00000000dee7b000
[    0.000000] PM: Registered nosave memory: 00000000dee7b000 - 00000000df140000
[    0.000000] PM: Registered nosave memory: 00000000df140000 - 00000000df385000
[    0.000000] PM: Registered nosave memory: 00000000df385000 - 00000000df393000
[    0.000000] PM: Registered nosave memory: 00000000df393000 - 00000000df3c0000
[    0.000000] PM: Registered nosave memory: 00000000df3c0000 - 00000000df3c5000
[    0.000000] PM: Registered nosave memory: 00000000df3c5000 - 00000000df408000
[    0.000000] PM: Registered nosave memory: 00000000df800000 - 00000000f8000000
[    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000fc000000
[    0.000000] PM: Registered nosave memory: 00000000fc000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
[    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fed00000
[    0.000000] PM: Registered nosave memory: 00000000fed00000 - 00000000fed04000
[    0.000000] PM: Registered nosave memory: 00000000fed04000 - 00000000fed1c000
[    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
[    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ff000000
[    0.000000] PM: Registered nosave memory: 00000000ff000000 - 0000000100000000
[    0.000000] e820: [mem 0xdf800000-0xf7ffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88011ec00000 s85056 r8192 d21440 u524288
[    0.000000] pcpu-alloc: s85056 r8192 d21440 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1023889
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-29-generic root=UUID=01383357-1a1e-49b8-8829-b7b712c7132e ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] __ex_table already sorted, skipping sort
[    0.000000] xsave: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 3996884k/4702208k available (7170k kernel code, 541608k absent, 163716k reserved, 6073k data, 1012k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
[    0.000000] NR_IRQS:16640 nr_irqs:712 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 16777216 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.004000] tsc: Detected 3310.813 MHz processor
[    0.000001] Calibrating delay loop (skipped), value calculated using timer frequency.. 6621.62 BogoMIPS (lpj=13243252)
[    0.000003] pid_max: default: 32768 minimum: 301
[    0.000018] Security Framework initialized
[    0.000026] AppArmor: AppArmor initialized
[    0.000027] Yama: becoming mindful.
[    0.000234] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.000827] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.001123] Mount-cache hash table entries: 256
[    0.001240] Initializing cgroup subsys cpuacct
[    0.001241] Initializing cgroup subsys memory
[    0.001245] Initializing cgroup subsys devices
[    0.001246] Initializing cgroup subsys freezer
[    0.001247] Initializing cgroup subsys blkio
[    0.001248] Initializing cgroup subsys perf_event
[    0.001250] Initializing cgroup subsys hugetlb
[    0.001268] CPU: Physical Processor ID: 0
[    0.001268] CPU: Processor Core ID: 0
[    0.001272] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.001272] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.001274] mce: CPU supports 9 MCE banks
[    0.001284] CPU0: Thermal monitoring enabled (TM1)
[    0.001289] process: using mwait in idle threads
[    0.001291] Last level iTLB entries: 4KB 512, 2MB 0, 4MB 0
[    0.001291] Last level dTLB entries: 4KB 512, 2MB 32, 4MB 32
[    0.001291] tlb_flushall_shift: 5
[    0.001387] Freeing SMP alternatives: 24k freed
[    0.003223] ACPI: Core revision 20121018
[    0.229890] ftrace: allocating 29358 entries in 115 pages
[    0.240340] dmar: Host address width 36
[    0.240342] dmar: DRHD base: 0x000000fed90000 flags: 0x1
[    0.240351] dmar: IOMMU 0: reg_base_addr fed90000 ver 1:0 cap c9008020660262 ecap f0105a
[    0.240352] dmar: RMRR base: 0x000000df0c2000 end: 0x000000df0d3fff
[    0.240422] IOAPIC id 2 under DRHD base  0xfed90000 IOMMU 0
[    0.240423] HPET id 0 under DRHD base 0xfed90000
[    0.240496] Enabled IRQ remapping in x2apic mode
[    0.240497] Enabling x2apic
[    0.240498] Enabled x2apic
[    0.240504] Switched APIC routing to cluster x2apic.
[    0.240928] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.280574] smpboot: CPU0: Intel(R) Core(TM) i5-2500 CPU @ 3.30GHz (fam: 06, model: 2a, stepping: 07)
[    0.280580] TSC deadline timer enabled
[    0.280583] Performance Events: PEBS fmt1+, 16-deep LBR, SandyBridge events, Intel PMU driver.
[    0.280589] ... version:                3
[    0.280590] ... bit width:              48
[    0.280591] ... generic registers:      8
[    0.280592] ... value mask:             0000ffffffffffff
[    0.280592] ... max period:             000000007fffffff
[    0.280593] ... fixed-purpose events:   3
[    0.280594] ... event mask:             00000007000000ff
[    0.294442] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.281368] smpboot: Booting Node   0, Processors  #1 #2 #3 OK
[    0.320629] Brought up 4 CPUs
[    0.320632] smpboot: Total of 4 processors activated (26486.50 BogoMIPS)
[    0.323259] devtmpfs: initialized
[    0.323815] EVM: security.selinux
[    0.323816] EVM: security.SMACK64
[    0.323817] EVM: security.capability
[    0.323843] PM: Registering ACPI NVS region [mem 0xdedf7000-0xdee7afff] (540672 bytes)
[    0.323849] PM: Registering ACPI NVS region [mem 0xdf140000-0xdf384fff] (2379776 bytes)
[    0.323872] PM: Registering ACPI NVS region [mem 0xdf393000-0xdf3bffff] (184320 bytes)
[    0.323875] PM: Registering ACPI NVS region [mem 0xdf3c5000-0xdf407fff] (274432 bytes)
[    0.324383] regulator-dummy: no parameters
[    0.324413] NET: Registered protocol family 16
[    0.324506] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.324507] ACPI: bus type pci registered
[    0.324542] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.324544] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.329483] PCI: Using configuration type 1 for base access
[    0.330058] bio: create slab <bio-0> at 0
[    0.330118] ACPI: Added _OSI(Module Device)
[    0.330119] ACPI: Added _OSI(Processor Device)
[    0.330120] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.330121] ACPI: Added _OSI(Processor Aggregator Device)
[    0.331258] ACPI: EC: Look up EC in DSDT
[    0.332360] ACPI: Executed 1 blocks of module-level executable AML code
[    0.334744] ACPI: SSDT 00000000df0f1018 0083B (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.335031] ACPI: Dynamic OEM Table Load:
[    0.335033] ACPI: SSDT           (null) 0083B (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.335226] ACPI: SSDT 00000000df0f2a98 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.335532] ACPI: Dynamic OEM Table Load:
[    0.335534] ACPI: SSDT           (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.335630] ACPI: SSDT 00000000df0f0d98 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.335914] ACPI: Dynamic OEM Table Load:
[    0.335915] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.336320] ACPI: Interpreter enabled
[    0.336323] ACPI: (supports S0 S1 S3 S4 S5)
[    0.336338] ACPI: Using IOAPIC for interrupt routing
[    0.339946] ACPI: Power Resource [FN00] (off)
[    0.339992] ACPI: Power Resource [FN01] (off)
[    0.340036] ACPI: Power Resource [FN02] (off)
[    0.340079] ACPI: Power Resource [FN03] (off)
[    0.340122] ACPI: Power Resource [FN04] (off)
[    0.340323] ACPI: EC: GPE = 0x18, I/O: command/status = 0x66, data = 0x62
[    0.340437] ACPI: No dock devices found.
[    0.340440] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.340598] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    0.340600] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.340708] \_SB_.PCI0:_OSC invalid UUID
[    0.340708] _OSC request data:1 8 0 
[    0.341005] PCI host bridge to bus 0000:00
[    0.341007] pci_bus 0000:00: root bus resource [bus 00-3e]
[    0.341008] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.341010] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.341011] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.341012] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff]
[    0.341013] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
[    0.341015] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
[    0.341016] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff]
[    0.341017] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000e3fff]
[    0.341018] pci_bus 0000:00: root bus resource [mem 0x000e4000-0x000e7fff]
[    0.341020] pci_bus 0000:00: root bus resource [mem 0xe0000000-0xfeafffff]
[    0.341026] pci 0000:00:00.0: [8086:0100] type 00 class 0x060000
[    0.341054] pci 0000:00:01.0: [8086:0101] type 01 class 0x060400
[    0.341077] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.341115] pci 0000:00:16.0: [8086:1c3a] type 00 class 0x078000
[    0.341138] pci 0000:00:16.0: reg 10: [mem 0xf732b000-0xf732b00f 64bit]
[    0.341208] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.341237] pci 0000:00:19.0: [8086:1503] type 00 class 0x020000
[    0.341254] pci 0000:00:19.0: reg 10: [mem 0xf7300000-0xf731ffff]
[    0.341262] pci 0000:00:19.0: reg 14: [mem 0xf7328000-0xf7328fff]
[    0.341270] pci 0000:00:19.0: reg 18: [io  0xf020-0xf03f]
[    0.341328] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.341353] pci 0000:00:1a.0: [8086:1c2d] type 00 class 0x0c0320
[    0.341373] pci 0000:00:1a.0: reg 10: [mem 0xf7327000-0xf73273ff]
[    0.341458] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.341483] pci 0000:00:1b.0: [8086:1c20] type 00 class 0x040300
[    0.341496] pci 0000:00:1b.0: reg 10: [mem 0xf7320000-0xf7323fff 64bit]
[    0.341559] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.341580] pci 0000:00:1c.0: [8086:1c10] type 01 class 0x060400
[    0.341654] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.341677] pci 0000:00:1c.1: [8086:1c12] type 01 class 0x060400
[    0.341751] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.341776] pci 0000:00:1c.4: [8086:1c18] type 01 class 0x060400
[    0.341850] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.341874] pci 0000:00:1c.6: [8086:244e] type 01 class 0x060401
[    0.341948] pci 0000:00:1c.6: PME# supported from D0 D3hot D3cold
[    0.341975] pci 0000:00:1d.0: [8086:1c26] type 00 class 0x0c0320
[    0.341994] pci 0000:00:1d.0: reg 10: [mem 0xf7326000-0xf73263ff]
[    0.342078] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.342103] pci 0000:00:1f.0: [8086:1c44] type 00 class 0x060100
[    0.342218] pci 0000:00:1f.2: [8086:1c00] type 00 class 0x01018f
[    0.342232] pci 0000:00:1f.2: reg 10: [io  0xf0f0-0xf0f7]
[    0.342239] pci 0000:00:1f.2: reg 14: [io  0xf0e0-0xf0e3]
[    0.342246] pci 0000:00:1f.2: reg 18: [io  0xf0d0-0xf0d7]
[    0.342253] pci 0000:00:1f.2: reg 1c: [io  0xf0c0-0xf0c3]
[    0.342260] pci 0000:00:1f.2: reg 20: [io  0xf0b0-0xf0bf]
[    0.342267] pci 0000:00:1f.2: reg 24: [io  0xf0a0-0xf0af]
[    0.342309] pci 0000:00:1f.3: [8086:1c22] type 00 class 0x0c0500
[    0.342323] pci 0000:00:1f.3: reg 10: [mem 0xf7325000-0xf73250ff 64bit]
[    0.342342] pci 0000:00:1f.3: reg 20: [io  0xf000-0xf01f]
[    0.342373] pci 0000:00:1f.5: [8086:1c08] type 00 class 0x010185
[    0.342387] pci 0000:00:1f.5: reg 10: [io  0xf090-0xf097]
[    0.342394] pci 0000:00:1f.5: reg 14: [io  0xf080-0xf083]
[    0.342401] pci 0000:00:1f.5: reg 18: [io  0xf070-0xf077]
[    0.342408] pci 0000:00:1f.5: reg 1c: [io  0xf060-0xf063]
[    0.342415] pci 0000:00:1f.5: reg 20: [io  0xf050-0xf05f]
[    0.342422] pci 0000:00:1f.5: reg 24: [io  0xf040-0xf04f]
[    0.342484] pci 0000:01:00.0: [10de:11c6] type 00 class 0x030000
[    0.342493] pci 0000:01:00.0: reg 10: [mem 0xf6000000-0xf6ffffff]
[    0.342502] pci 0000:01:00.0: reg 14: [mem 0xe8000000-0xefffffff 64bit pref]
[    0.342511] pci 0000:01:00.0: reg 1c: [mem 0xf0000000-0xf1ffffff 64bit pref]
[    0.342518] pci 0000:01:00.0: reg 24: [io  0xe000-0xe07f]
[    0.342524] pci 0000:01:00.0: reg 30: [mem 0xf7000000-0xf707ffff pref]
[    0.342576] pci 0000:01:00.1: [10de:0e0b] type 00 class 0x040300
[    0.342584] pci 0000:01:00.1: reg 10: [mem 0xf7080000-0xf7083fff]
[    0.351093] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.351097] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.351101] pci 0000:00:01.0:   bridge window [mem 0xf6000000-0xf70fffff]
[    0.351106] pci 0000:00:01.0:   bridge window [mem 0xe8000000-0xf1ffffff 64bit pref]
[    0.351182] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.351259] pci 0000:03:00.0: [1b21:1042] type 00 class 0x0c0330
[    0.351287] pci 0000:03:00.0: reg 10: [mem 0xf7200000-0xf7207fff 64bit]
[    0.351432] pci 0000:03:00.0: PME# supported from D3hot D3cold
[    0.359092] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    0.359101] pci 0000:00:1c.1:   bridge window [mem 0xf7200000-0xf72fffff]
[    0.359209] pci 0000:04:00.0: [1b21:1042] type 00 class 0x0c0330
[    0.359237] pci 0000:04:00.0: reg 10: [mem 0xf7100000-0xf7107fff 64bit]
[    0.359381] pci 0000:04:00.0: PME# supported from D3hot D3cold
[    0.367087] pci 0000:00:1c.4: PCI bridge to [bus 04]
[    0.367096] pci 0000:00:1c.4:   bridge window [mem 0xf7100000-0xf71fffff]
[    0.367191] pci 0000:05:00.0: [1b21:1080] type 01 class 0x060401
[    0.367307] pci 0000:00:1c.6: PCI bridge to [bus 05-06] (subtractive decode)
[    0.367317] pci 0000:00:1c.6:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.367318] pci 0000:00:1c.6:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.367319] pci 0000:00:1c.6:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.367320] pci 0000:00:1c.6:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
[    0.367322] pci 0000:00:1c.6:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.367323] pci 0000:00:1c.6:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.367324] pci 0000:00:1c.6:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
[    0.367325] pci 0000:00:1c.6:   bridge window [mem 0x000e0000-0x000e3fff] (subtractive decode)
[    0.367326] pci 0000:00:1c.6:   bridge window [mem 0x000e4000-0x000e7fff] (subtractive decode)
[    0.367328] pci 0000:00:1c.6:   bridge window [mem 0xe0000000-0xfeafffff] (subtractive decode)
[    0.367439] pci 0000:05:00.0: PCI bridge to [bus 06] (subtractive decode)
[    0.367461] pci 0000:05:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
[    0.367462] pci 0000:05:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
[    0.367463] pci 0000:05:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
[    0.367465] pci 0000:05:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
[    0.367466] pci 0000:05:00.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.367467] pci 0000:05:00.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.367468] pci 0000:05:00.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.367469] pci 0000:05:00.0:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
[    0.367471] pci 0000:05:00.0:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.367472] pci 0000:05:00.0:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.367473] pci 0000:05:00.0:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
[    0.367474] pci 0000:05:00.0:   bridge window [mem 0x000e0000-0x000e3fff] (subtractive decode)
[    0.367475] pci 0000:05:00.0:   bridge window [mem 0x000e4000-0x000e7fff] (subtractive decode)
[    0.367477] pci 0000:05:00.0:   bridge window [mem 0xe0000000-0xfeafffff] (subtractive decode)
[    0.367523] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.367547] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.367571] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
[    0.367593] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEG0._PRT]
[    0.367618] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP07._PRT]
[    0.367637] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP07.PXSX._PRT]
[    0.367711] \_SB_.PCI0:_OSC invalid UUID
[    0.367712] _OSC request data:1 1f 0 
[    0.367714]  pci0000:00: ACPI _OSC support notification failed, disabling PCIe ASPM
[    0.367715]  pci0000:00: Unable to request _OSC control (_OSC support mask: 0x08)
[    0.368304] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.368337] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 *10 11 12 14 15)
[    0.368366] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 10 11 12 14 15)
[    0.368396] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 10 11 12 14 15)
[    0.368427] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 *4 5 6 10 11 12 14 15)
[    0.368457] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.368487] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.368516] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *10 11 12 14 15)
[    0.368579] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.368581] vgaarb: loaded
[    0.368581] vgaarb: bridge control possible 0000:01:00.0
[    0.368682] SCSI subsystem initialized
[    0.368683] ACPI: bus type scsi registered
[    0.368703] libata version 3.00 loaded.
[    0.368715] ACPI: bus type usb registered
[    0.368724] usbcore: registered new interface driver usbfs
[    0.368730] usbcore: registered new interface driver hub
[    0.368741] usbcore: registered new device driver usb
[    0.368794] PCI: Using ACPI for IRQ routing
[    0.370181] PCI: pci_cache_line_size set to 64 bytes
[    0.370239] e820: reserve RAM buffer [mem 0x0009ec00-0x0009ffff]
[    0.370240] e820: reserve RAM buffer [mem 0xdeb90000-0xdfffffff]
[    0.370241] e820: reserve RAM buffer [mem 0xdf800000-0xdfffffff]
[    0.370242] e820: reserve RAM buffer [mem 0x11f000000-0x11fffffff]
[    0.370294] NetLabel: Initializing
[    0.370295] NetLabel:  domain hash size = 128
[    0.370295] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.370302] NetLabel:  unlabeled traffic allowed by default
[    0.370333] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.370337] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.372347] Switching to clocksource hpet
[    0.375601] AppArmor: AppArmor Filesystem Enabled
[    0.375620] pnp: PnP ACPI init
[    0.375628] ACPI: bus type pnp registered
[    0.375687] system 00:00: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.375690] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.375699] pnp 00:01: [dma 4]
[    0.375710] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.375721] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
[    0.375784] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.375810] system 00:04: [io  0x0680-0x069f] has been reserved
[    0.375811] system 00:04: [io  0x0200-0x020f] has been reserved
[    0.375813] system 00:04: [io  0xffff] has been reserved
[    0.375814] system 00:04: [io  0xffff] has been reserved
[    0.375815] system 00:04: [io  0x0400-0x0453] has been reserved
[    0.375817] system 00:04: [io  0x0458-0x047f] has been reserved
[    0.375818] system 00:04: [io  0x0500-0x057f] has been reserved
[    0.375819] system 00:04: [io  0x164e-0x164f] has been reserved
[    0.375821] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.375844] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.375873] system 00:06: [io  0x0454-0x0457] has been reserved
[    0.375875] system 00:06: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.375930] system 00:07: [io  0x0290-0x029f] has been reserved
[    0.375932] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.375962] system 00:08: [io  0x04d0-0x04d1] has been reserved
[    0.375964] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.375981] pnp 00:09: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.376183] system 00:0a: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.376184] system 00:0a: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.376186] system 00:0a: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.376187] system 00:0a: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.376188] system 00:0a: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.376190] system 00:0a: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.376191] system 00:0a: [mem 0xfed90000-0xfed93fff] could not be reserved
[    0.376193] system 00:0a: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.376194] system 00:0a: [mem 0xff000000-0xffffffff] has been reserved
[    0.376195] system 00:0a: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.376197] system 00:0a: [mem 0xe0000000-0xe0000fff] has been reserved
[    0.376199] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.376286] pnp: PnP ACPI: found 11 devices
[    0.376287] ACPI: ACPI bus type pnp unregistered
[    0.381935] pci 0000:00:1c.0: bridge window [io  0x1000-0x0fff] to [bus 02] add_size 1000
[    0.381938] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 02] add_size 200000
[    0.381939] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff] to [bus 02] add_size 200000
[    0.381975] pci 0000:00:1c.0: res[14]=[mem 0x00100000-0x000fffff] get_res_add_size add_size 200000
[    0.381977] pci 0000:00:1c.0: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.381978] pci 0000:00:1c.0: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.381982] pci 0000:00:1c.0: BAR 14: assigned [mem 0xe0100000-0xe02fffff]
[    0.381984] pci 0000:00:1c.0: BAR 15: assigned [mem 0xe0300000-0xe04fffff 64bit pref]
[    0.381986] pci 0000:00:1c.0: BAR 13: assigned [io  0x2000-0x2fff]
[    0.381988] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.381990] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.381992] pci 0000:00:01.0:   bridge window [mem 0xf6000000-0xf70fffff]
[    0.381994] pci 0000:00:01.0:   bridge window [mem 0xe8000000-0xf1ffffff 64bit pref]
[    0.381997] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.381999] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.382004] pci 0000:00:1c.0:   bridge window [mem 0xe0100000-0xe02fffff]
[    0.382008] pci 0000:00:1c.0:   bridge window [mem 0xe0300000-0xe04fffff 64bit pref]
[    0.382013] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    0.382018] pci 0000:00:1c.1:   bridge window [mem 0xf7200000-0xf72fffff]
[    0.382026] pci 0000:00:1c.4: PCI bridge to [bus 04]
[    0.382030] pci 0000:00:1c.4:   bridge window [mem 0xf7100000-0xf71fffff]
[    0.382038] pci 0000:05:00.0: PCI bridge to [bus 06]
[    0.382057] pci 0000:00:1c.6: PCI bridge to [bus 05-06]
[    0.382104] pci 0000:05:00.0: setting latency timer to 64
[    0.382109] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.382110] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.382111] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.382112] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.382114] pci_bus 0000:00: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.382115] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.382116] pci_bus 0000:00: resource 10 [mem 0x000dc000-0x000dffff]
[    0.382117] pci_bus 0000:00: resource 11 [mem 0x000e0000-0x000e3fff]
[    0.382118] pci_bus 0000:00: resource 12 [mem 0x000e4000-0x000e7fff]
[    0.382120] pci_bus 0000:00: resource 13 [mem 0xe0000000-0xfeafffff]
[    0.382121] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.382122] pci_bus 0000:01: resource 1 [mem 0xf6000000-0xf70fffff]
[    0.382123] pci_bus 0000:01: resource 2 [mem 0xe8000000-0xf1ffffff 64bit pref]
[    0.382125] pci_bus 0000:02: resource 0 [io  0x2000-0x2fff]
[    0.382126] pci_bus 0000:02: resource 1 [mem 0xe0100000-0xe02fffff]
[    0.382127] pci_bus 0000:02: resource 2 [mem 0xe0300000-0xe04fffff 64bit pref]
[    0.382129] pci_bus 0000:03: resource 1 [mem 0xf7200000-0xf72fffff]
[    0.382130] pci_bus 0000:04: resource 1 [mem 0xf7100000-0xf71fffff]
[    0.382131] pci_bus 0000:05: resource 4 [io  0x0000-0x0cf7]
[    0.382132] pci_bus 0000:05: resource 5 [io  0x0d00-0xffff]
[    0.382134] pci_bus 0000:05: resource 6 [mem 0x000a0000-0x000bffff]
[    0.382135] pci_bus 0000:05: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.382136] pci_bus 0000:05: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.382137] pci_bus 0000:05: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.382139] pci_bus 0000:05: resource 10 [mem 0x000dc000-0x000dffff]
[    0.382140] pci_bus 0000:05: resource 11 [mem 0x000e0000-0x000e3fff]
[    0.382141] pci_bus 0000:05: resource 12 [mem 0x000e4000-0x000e7fff]
[    0.382142] pci_bus 0000:05: resource 13 [mem 0xe0000000-0xfeafffff]
[    0.382144] pci_bus 0000:06: resource 8 [io  0x0000-0x0cf7]
[    0.382145] pci_bus 0000:06: resource 9 [io  0x0d00-0xffff]
[    0.382146] pci_bus 0000:06: resource 10 [mem 0x000a0000-0x000bffff]
[    0.382147] pci_bus 0000:06: resource 11 [mem 0x000d0000-0x000d3fff]
[    0.382148] pci_bus 0000:06: resource 12 [mem 0x000d4000-0x000d7fff]
[    0.382149] pci_bus 0000:06: resource 13 [mem 0x000d8000-0x000dbfff]
[    0.382151] pci_bus 0000:06: resource 14 [mem 0x000dc000-0x000dffff]
[    0.382152] pci_bus 0000:06: resource 15 [mem 0x000e0000-0x000e3fff]
[    0.382153] pci_bus 0000:06: resource 16 [mem 0x000e4000-0x000e7fff]
[    0.382154] pci_bus 0000:06: resource 17 [mem 0xe0000000-0xfeafffff]
[    0.382172] NET: Registered protocol family 2
[    0.382271] TCP established hash table entries: 32768 (order: 7, 524288 bytes)
[    0.382353] TCP bind hash table entries: 32768 (order: 7, 524288 bytes)
[    0.382412] TCP: Hash tables configured (established 32768 bind 32768)
[    0.382426] TCP: reno registered
[    0.382432] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.382443] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.382479] NET: Registered protocol family 1
[    0.382570] pci 0000:01:00.0: Boot video device
[    0.382654] PCI: CLS 64 bytes, default 64
[    0.382682] Trying to unpack rootfs image as initramfs...
[    0.563146] Freeing initrd memory: 15832k freed
[    0.564675] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.564680] software IO TLB [mem 0xdab90000-0xdeb90000] (64MB) mapped at [ffff8800dab90000-ffff8800deb8ffff]
[    0.564991] Initialise module verification
[    0.565024] audit: initializing netlink socket (disabled)
[    0.565036] type=2000 audit(1390235031.340:1): initialized
[    0.584867] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.585741] VFS: Disk quotas dquot_6.5.2
[    0.585766] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.586049] fuse init (API version 7.20)
[    0.586095] msgmni has been set to 7837
[    0.586386] Key type asymmetric registered
[    0.586388] Asymmetric key parser 'x509' registered
[    0.586406] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.586425] io scheduler noop registered
[    0.586426] io scheduler deadline registered (default)
[    0.586429] io scheduler cfq registered
[    0.586502] pcieport 0000:00:01.0: irq 41 for MSI/MSI-X
[    0.586642] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.586651] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.586676] intel_idle: MWAIT substates: 0x1120
[    0.586677] intel_idle: v0.4 model 0x2A
[    0.586677] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.586736] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.586740] ACPI: Power Button [PWRB]
[    0.586760] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.586762] ACPI: Power Button [PWRF]
[    0.586814] ACPI: Fan [FAN0] (off)
[    0.586830] ACPI: Fan [FAN1] (off)
[    0.586846] ACPI: Fan [FAN2] (off)
[    0.586861] ACPI: Fan [FAN3] (off)
[    0.586875] ACPI: Fan [FAN4] (off)
[    0.586914] ACPI: Requesting acpi_cpufreq
[    0.589675] thermal LNXTHERM:00: registered as thermal_zone0
[    0.589677] ACPI: Thermal Zone [TZ00] (28 C)
[    0.589814] thermal LNXTHERM:01: registered as thermal_zone1
[    0.589816] ACPI: Thermal Zone [TZ01] (30 C)
[    0.589848] GHES: HEST is not enabled!
[    0.589891] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.590667] Linux agpgart interface v0.103
[    0.591354] brd: module loaded
[    0.591702] loop: module loaded
[    0.591758] ata_piix 0000:00:1f.2: version 2.13
[    0.591774] ata_piix 0000:00:1f.2: MAP [
[    0.591775]  P0 P2 P1 P3 ]
[    0.744025] ata_piix 0000:00:1f.2: SCR access via SIDPR is available but doesn't work
[    0.744036] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.744195] scsi0 : ata_piix
[    0.744252] scsi1 : ata_piix
[    0.744290] ata1: SATA max UDMA/133 cmd 0xf0f0 ctl 0xf0e0 bmdma 0xf0b0 irq 19
[    0.744291] ata2: SATA max UDMA/133 cmd 0xf0d0 ctl 0xf0c0 bmdma 0xf0b8 irq 19
[    0.744304] ata_piix 0000:00:1f.5: MAP [
[    0.744305]  P0 -- P1 -- ]
[    0.899885] ata_piix 0000:00:1f.5: SCR access via SIDPR is available but doesn't work
[    0.899894] ata_piix 0000:00:1f.5: setting latency timer to 64
[    0.900014] scsi2 : ata_piix
[    0.900075] scsi3 : ata_piix
[    0.900097] ata3: SATA max UDMA/133 cmd 0xf090 ctl 0xf080 bmdma 0xf050 irq 19
[    0.900098] ata4: SATA max UDMA/133 cmd 0xf070 ctl 0xf060 bmdma 0xf058 irq 19
[    0.900239] libphy: Fixed MDIO Bus: probed
[    0.900272] tun: Universal TUN/TAP device driver, 1.6
[    0.900273] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.900347] PPP generic driver version 2.4.2
[    0.900370] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.900371] ehci-pci: EHCI PCI platform driver
[    0.911169] ehci-pci 0000:00:1a.0: setting latency timer to 64
[    0.911172] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    0.911176] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    0.911194] ehci-pci 0000:00:1a.0: debug port 2
[    0.915097] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    0.915107] ehci-pci 0000:00:1a.0: irq 16, io mem 0xf7327000
[    0.923848] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    0.923871] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.923873] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.923876] usb usb1: Product: EHCI Host Controller
[    0.923878] usb usb1: Manufacturer: Linux 3.8.0-29-generic ehci_hcd
[    0.923881] usb usb1: SerialNumber: 0000:00:1a.0
[    0.923966] hub 1-0:1.0: USB hub found
[    0.923969] hub 1-0:1.0: 2 ports detected
[    0.924045] ehci-pci 0000:00:1d.0: setting latency timer to 64
[    0.924048] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    0.924051] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.924061] ehci-pci 0000:00:1d.0: debug port 2
[    0.927962] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    0.927973] ehci-pci 0000:00:1d.0: irq 23, io mem 0xf7326000
[    0.939838] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    0.939854] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    0.939856] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.939859] usb usb2: Product: EHCI Host Controller
[    0.939861] usb usb2: Manufacturer: Linux 3.8.0-29-generic ehci_hcd
[    0.939864] usb usb2: SerialNumber: 0000:00:1d.0
[    0.939946] hub 2-0:1.0: USB hub found
[    0.939948] hub 2-0:1.0: 2 ports detected
[    0.939992] ehci-platform: EHCI generic platform driver
[    0.939997] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.940005] uhci_hcd: USB Universal Host Controller Interface driver
[    0.940033] xhci_hcd 0000:03:00.0: xHCI Host Controller
[    0.940036] xhci_hcd 0000:03:00.0: new USB bus registered, assigned bus number 3
[    0.956530] ata1.01: ATA-7: ST3500830AS, 3.AFD, max UDMA/133
[    0.956532] ata1.01: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.001148] xhci_hcd 0000:03:00.0: irq 42 for MSI/MSI-X
[    1.001152] xhci_hcd 0000:03:00.0: irq 43 for MSI/MSI-X
[    1.001157] xhci_hcd 0000:03:00.0: irq 44 for MSI/MSI-X
[    1.001161] xhci_hcd 0000:03:00.0: irq 45 for MSI/MSI-X
[    1.001165] xhci_hcd 0000:03:00.0: irq 46 for MSI/MSI-X
[    1.001252] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    1.001254] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.001255] usb usb3: Product: xHCI Host Controller
[    1.001256] usb usb3: Manufacturer: Linux 3.8.0-29-generic xhci_hcd
[    1.001257] usb usb3: SerialNumber: 0000:03:00.0
[    1.001296] xHCI xhci_add_endpoint called for root hub
[    1.001298] xHCI xhci_check_bandwidth called for root hub
[    1.001309] hub 3-0:1.0: USB hub found
[    1.001315] hub 3-0:1.0: 2 ports detected
[    1.001355] xhci_hcd 0000:03:00.0: xHCI Host Controller
[    1.001357] xhci_hcd 0000:03:00.0: new USB bus registered, assigned bus number 4
[    1.001385] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
[    1.001386] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.001387] usb usb4: Product: xHCI Host Controller
[    1.001388] usb usb4: Manufacturer: Linux 3.8.0-29-generic xhci_hcd
[    1.001390] usb usb4: SerialNumber: 0000:03:00.0
[    1.001423] xHCI xhci_add_endpoint called for root hub
[    1.001424] xHCI xhci_check_bandwidth called for root hub
[    1.001434] hub 4-0:1.0: USB hub found
[    1.001439] hub 4-0:1.0: 2 ports detected
[    1.001527] xhci_hcd 0000:04:00.0: xHCI Host Controller
[    1.001531] xhci_hcd 0000:04:00.0: new USB bus registered, assigned bus number 5
[    1.023107] ata1.01: configured for UDMA/133
[    1.023176] scsi 0:0:1:0: Direct-Access     ATA      ST3500830AS      3.AF PQ: 0 ANSI: 5
[    1.023245] sd 0:0:1:0: Attached scsi generic sg0 type 0
[    1.023273] sd 0:0:1:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.023295] sd 0:0:1:0: [sda] Write Protect is off
[    1.023296] sd 0:0:1:0: [sda] Mode Sense: 00 3a 00 00
[    1.023306] sd 0:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.062646] xhci_hcd 0000:04:00.0: irq 47 for MSI/MSI-X
[    1.062651] xhci_hcd 0000:04:00.0: irq 48 for MSI/MSI-X
[    1.062656] xhci_hcd 0000:04:00.0: irq 49 for MSI/MSI-X
[    1.062660] xhci_hcd 0000:04:00.0: irq 50 for MSI/MSI-X
[    1.062664] xhci_hcd 0000:04:00.0: irq 51 for MSI/MSI-X
[    1.062757] usb usb5: New USB device found, idVendor=1d6b, idProduct=0002
[    1.062758] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.062759] usb usb5: Product: xHCI Host Controller
[    1.062761] usb usb5: Manufacturer: Linux 3.8.0-29-generic xhci_hcd
[    1.062762] usb usb5: SerialNumber: 0000:04:00.0
[    1.062804] xHCI xhci_add_endpoint called for root hub
[    1.062805] xHCI xhci_check_bandwidth called for root hub
[    1.062818] hub 5-0:1.0: USB hub found
[    1.062824] hub 5-0:1.0: 2 ports detected
[    1.062863] xhci_hcd 0000:04:00.0: xHCI Host Controller
[    1.062865] xhci_hcd 0000:04:00.0: new USB bus registered, assigned bus number 6
[    1.062893] usb usb6: New USB device found, idVendor=1d6b, idProduct=0003
[    1.062894] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.062895] usb usb6: Product: xHCI Host Controller
[    1.062897] usb usb6: Manufacturer: Linux 3.8.0-29-generic xhci_hcd
[    1.062898] usb usb6: SerialNumber: 0000:04:00.0
[    1.062937] xHCI xhci_add_endpoint called for root hub
[    1.062938] xHCI xhci_check_bandwidth called for root hub
[    1.062948] hub 6-0:1.0: USB hub found
[    1.062953] hub 6-0:1.0: 2 ports detected
[    1.079800] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    1.082657] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.082661] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.082730] mousedev: PS/2 mouse device common for all mice
[    1.082818] rtc_cmos 00:05: RTC can wake from S4
[    1.082920] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.082945] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.082976]  sda: sda1 sda2 sda3 < sda5 sda6 >
[    1.083012] device-mapper: uevent: version 1.0.3
[    1.083055] device-mapper: ioctl: 4.23.1-ioctl (2012-12-18) initialised: dm-devel@redhat.com
[    1.083101] cpuidle: using governor ladder
[    1.083158] cpuidle: using governor menu
[    1.083160] ledtrig-cpu: registered to indicate activity on CPUs
[    1.083161] EFI Variables Facility v0.08 2004-May-17
[    1.083177] sd 0:0:1:0: [sda] Attached SCSI disk
[    1.083269] ashmem: initialized
[    1.083343] TCP: cubic registered
[    1.083400] NET: Registered protocol family 10
[    1.083496] NET: Registered protocol family 17
[    1.083502] Key type dns_resolver registered
[    1.083638] Loading module verification certificates
[    1.084283] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: 38550890b1fce75cc801d8fb942703db919b9386'
[    1.084291] registered taskstats version 1
[    1.086095] Key type trusted registered
[    1.087473] Key type encrypted registered
[    1.089318] rtc_cmos 00:05: setting system clock to 2014-01-20 16:23:52 UTC (1390235032)
[    1.089935] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.089936] EDD information not available.
[    1.090977] Freeing unused kernel memory: 1012k freed
[    1.091063] Write protecting the kernel read-only data: 12288k
[    1.093112] Freeing unused kernel memory: 1012k freed
[    1.095076] Freeing unused kernel memory: 1008k freed
[    1.105046] udevd[116]: starting version 175
[    1.121434] Disabling lock debugging due to kernel taint
[    1.121841] e1000e: Intel(R) PRO/1000 Network Driver - 2.1.4-k
[    1.121842] e1000e: Copyright(c) 1999 - 2012 Intel Corporation.
[    1.121877] e1000e 0000:00:19.0: setting latency timer to 64
[    1.121928] e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    1.121958] e1000e 0000:00:19.0: irq 52 for MSI/MSI-X
[    1.235561] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.367909] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
[    1.367911] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.368181] hub 1-1:1.0: USB hub found
[    1.368346] hub 1-1:1.0: 6 ports detected
[    1.385698] e1000e 0000:00:19.0 eth0: (PCI Express:2.5GT/s:Width x1) c8:60:00:75:b0:10
[    1.385700] e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
[    1.385754] e1000e 0000:00:19.0 eth0: MAC: 10, PHY: 11, PBA No: FFFFFF-0FF
[    1.479331] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    1.563269] tsc: Refined TSC clocksource calibration: 3310.800 MHz
[    1.563275] Switching to clocksource tsc
[    1.611507] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
[    1.611510] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.611755] hub 2-1:1.0: USB hub found
[    1.611885] hub 2-1:1.0: 8 ports detected
[    1.779055] usb 5-1: new full-speed USB device number 2 using xhci_hcd
[    1.798666] usb 5-1: New USB device found, idVendor=045e, idProduct=0724
[    1.798671] usb 5-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.798675] usb 5-1: Product: SideWinder\xffffffe2\xffffff84\xffffffa2\xffffff84\xffffffa2 Mouse
[    1.798677] usb 5-1: Manufacturer: Microsoft
[    1.805649] usbcore: registered new interface driver usbhid
[    1.805652] usbhid: USB HID core driver
[    1.806984] input: Microsoft SideWinder\xffffffe2\xffffff84\xffffffa2\xffffff84\xffffffa2 Mouse as /devices/pci0000:00/0000:00:1c.4/0000:04:00.0/usb5/5-1/5-1:1.0/input/input2
[    1.807057] hid-generic 0003:045E:0724.0001: input,hidraw0: USB HID v1.11 Mouse [Microsoft SideWinder\xffffffe2\xffffff84\xffffffa2\xffffff84\xffffffa2 Mouse] on usb-0000:04:00.0-1/input0
[    1.878092] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[    1.883109] usb 2-1.2: new full-speed USB device number 3 using ehci-pci
[    1.978561] usb 2-1.2: New USB device found, idVendor=1532, idProduct=011a
[    1.978566] usb 2-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.978569] usb 2-1.2: Product: Razer BlackWidow Ultimate 2013
[    1.978571] usb 2-1.2: Manufacturer: Razer
[    1.979663] input: Razer Razer BlackWidow Ultimate 2013 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input3
[    1.979797] hid-generic 0003:1532:011A.0002: input,hidraw1: USB HID v1.11 Keyboard [Razer Razer BlackWidow Ultimate 2013] on usb-0000:00:1d.0-1.2/input0
[    1.983119] input: Razer Razer BlackWidow Ultimate 2013 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.1/input/input4
[    1.983264] hid-generic 0003:1532:011A.0003: input,hidraw2: USB HID v1.11 Keyboard [Razer Razer BlackWidow Ultimate 2013] on usb-0000:00:1d.0-1.2/input1
[    1.985300] input: Razer Razer BlackWidow Ultimate 2013 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.2/input/input5
[    1.985471] hid-generic 0003:1532:011A.0004: input,hidraw3: USB HID v1.11 Mouse [Razer Razer BlackWidow Ultimate 2013] on usb-0000:00:1d.0-1.2/input2
[    2.054974] usb 2-1.4: new high-speed USB device number 4 using ehci-pci
[    2.148300] usb 2-1.4: New USB device found, idVendor=152e, idProduct=1640
[    2.148305] usb 2-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.148308] usb 2-1.4: Product: SuperMulti RW   
[    2.148311] usb 2-1.4: Manufacturer: HLDS Inc
[    2.148313] usb 2-1.4: SerialNumber: 00101016400026695
[    3.129821] init: ureadahead main process (290) terminated with status 5
[    4.181115] Adding 4158460k swap on /dev/sda5.  Priority:-1 extents:1 across:4158460k 
[    5.283420] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    5.483128] udevd[365]: starting version 175
[    6.551881] lp: driver loaded but no devices found
[    6.798750] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[    7.099835] wmi: Mapper loaded
[    7.166074] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20121018/utaddress-251)
[    7.166079] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    7.166082] ACPI Warning: 0x0000000000000540-0x000000000000054f SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
[    7.166084] ACPI Warning: 0x0000000000000540-0x000000000000054f SystemIO conflicts with Region \_SB_.PCI0.LPCB.GPBX 2 (20121018/utaddress-251)
[    7.166086] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    7.166087] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
[    7.166089] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \_SB_.PCI0.LPCB.GPBX 2 (20121018/utaddress-251)
[    7.166091] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    7.166092] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
[    7.166094] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \_SB_.PCI0.LPCB.GPBX 2 (20121018/utaddress-251)
[    7.166096] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    7.166096] lpc_ich: Resource conflict(s) found affecting gpio_ich
[    7.282343] microcode: CPU0 sig=0x206a7, pf=0x2, revision=0x28
[    7.287610] mei 0000:00:16.0: setting latency timer to 64
[    7.287661] mei 0000:00:16.0: irq 53 for MSI/MSI-X
[    7.315882] asus_wmi: ASUS WMI generic driver loaded
[    7.469845] asus_wmi: Initialization: 0x0asus_wmi: BIOS WMI version: 0.9
[    7.469885] asus_wmi: SFUN value: 0x0<6>[    7.470061] input: Eee PC WMI hotkeys as /devices/platform/eeepc-wmi/input/input6
[    7.470519] asus_wmi: Disabling ACPI video driver
[    7.636841] [drm] Initialized drm 1.1.0 20060810
[    7.729602] microcode: CPU1 sig=0x206a7, pf=0x2, revision=0x28
[    7.730355] microcode: CPU2 sig=0x206a7, pf=0x2, revision=0x28
[    7.731032] microcode: CPU3 sig=0x206a7, pf=0x2, revision=0x28
[    7.731717] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    8.291396] Initializing USB Mass Storage driver...
[    8.291498] scsi4 : usb-storage 2-1.4:1.0
[    8.291569] usbcore: registered new interface driver usb-storage
[    8.291570] USB Mass Storage support registered.
[    9.248180] snd_hda_intel 0000:00:1b.0: irq 54 for MSI/MSI-X
[    9.290326] scsi 4:0:0:0: CD-ROM            HL-DT-ST DVDRAM GE20LU10  FE05 PQ: 0 ANSI: 0
[    9.296315] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    9.296317] cdrom: Uniform CD-ROM driver Revision: 3.20
[    9.296398] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    9.296446] sr 4:0:0:0: Attached scsi generic sg1 type 5
[    9.374651] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[    9.374699] input: HDA Intel PCH Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[    9.374732] input: HDA Intel PCH Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[    9.374767] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[    9.374799] input: HDA Intel PCH Line Out Side as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[    9.374831] input: HDA Intel PCH Line Out CLFE as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[    9.374862] input: HDA Intel PCH Line Out Surround as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[    9.374892] input: HDA Intel PCH Line Out Front as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[    9.375028] hda_intel: Disabling MSI
[    9.375033] hda-intel 0000:01:00.1: Handle VGA-switcheroo audio client
[    9.907479] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input15
[    9.907570] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input16
[    9.907646] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input17
[   11.085186] type=1400 audit(1390227842.502:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=701 comm="apparmor_parser"
[   11.085198] type=1400 audit(1390227842.502:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=702 comm="apparmor_parser"
[   11.085403] type=1400 audit(1390227842.502:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=701 comm="apparmor_parser"
[   11.085416] type=1400 audit(1390227842.502:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=702 comm="apparmor_parser"
[   11.085525] type=1400 audit(1390227842.502:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=701 comm="apparmor_parser"
[   11.085539] type=1400 audit(1390227842.502:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=702 comm="apparmor_parser"
[   11.525077] nvidia: module license 'NVIDIA' taints kernel.
[   11.530270] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   11.530391] [drm] Initialized nvidia-drm 0.0.0 20130102 for 0000:01:00.0 on minor 0
[   11.530396] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  319.32  Wed Jun 19 15:51:20 PDT 2013
[   11.674341] init: failsafe main process (813) killed by TERM signal
[   12.855870] type=1400 audit(1390227844.274:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=894 comm="apparmor_parser"
[   12.856108] type=1400 audit(1390227844.274:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=894 comm="apparmor_parser"
[   12.856239] type=1400 audit(1390227844.274:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=894 comm="apparmor_parser"
[   13.242266] type=1400 audit(1390227844.662:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=897 comm="apparmor_parser"
[   15.014659] ppdev: user-space parallel port driver
[   16.170945] Bluetooth: Core ver 2.16
[   16.170958] NET: Registered protocol family 31
[   16.170959] Bluetooth: HCI device and connection manager initialized
[   16.170966] Bluetooth: HCI socket layer initialized
[   16.170967] Bluetooth: L2CAP socket layer initialized
[   16.170970] Bluetooth: SCO socket layer initialized
[   16.360203] Bluetooth: RFCOMM TTY layer initialized
[   16.360212] Bluetooth: RFCOMM socket layer initialized
[   16.360214] Bluetooth: RFCOMM ver 1.11
[   16.663892] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.663896] Bluetooth: BNEP filters: protocol multicast
[   16.663903] Bluetooth: BNEP socket layer initialized
[   17.908832] init: udev-fallback-graphics main process (1150) terminated with status 1
[   18.311468] init: gdm main process (1207) killed by TERM signal
[   18.312576] init: kdm main process (1217) killed by TERM signal
[   20.253591] e1000e 0000:00:19.0: irq 52 for MSI/MSI-X
[   20.353656] e1000e 0000:00:19.0: irq 52 for MSI/MSI-X
[   20.353753] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.353933] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.878986] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
[   21.878991] e1000e 0000:00:19.0 eth0: 10/100 speed: disabling TSO
[   21.879023] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   53.535799] audit_printk_skb: 54 callbacks suppressed
[   53.535810] type=1400 audit(1390227884.983:30): apparmor="DENIED" operation="capable" parent=1 profile="/usr/sbin/cupsd" pid=1030 comm="cupsd" pid=1030 comm="cupsd" capability=36  capname="block_suspend"
[  982.037103] type=1400 audit(1390228813.962:31): apparmor="DENIED" operation="capable" parent=1 profile="/usr/sbin/cupsd" pid=1030 comm="cupsd" pid=1030 comm="cupsd" capability=36  capname="block_suspend"

```

C)Grep MemTotal
```

:~$ grep MemTotal /proc/meminfo
MemTotal:        4015772 kB

```

D)Cat Meminfo
```

:~$ cat /proc/meminfo
MemTotal:        4015772 kB
MemFree:         1984656 kB
Buffers:           54220 kB
Cached:           906720 kB
SwapCached:            0 kB
Active:          1137976 kB
Inactive:         690220 kB
Active(anon):     868056 kB
Inactive(anon):     1948 kB
Active(file):     269920 kB
Inactive(file):   688272 kB
Unevictable:           0 kB
Mlocked:               0 kB
SwapTotal:       4158460 kB
SwapFree:        4158460 kB
Dirty:                 8 kB
Writeback:             0 kB
AnonPages:        867332 kB
Mapped:           219964 kB
Shmem:              2752 kB
Slab:              76168 kB
SReclaimable:      48028 kB
SUnreclaim:        28140 kB
KernelStack:        3584 kB
PageTables:        25440 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     6166344 kB
Committed_AS:    2966412 kB
VmallocTotal:   34359738367 kB
VmallocUsed:      117336 kB
VmallocChunk:   34359612924 kB
HardwareCorrupted:     0 kB
AnonHugePages:         0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:      145408 kB
DirectMap2M:     4024320 kB

```

Thanks everyone :)

---

### Post by btindie on 2014-01-20
That'll be in use for shadowing the BIOS / for your on board graphics card, you never get the full amount. You can see how much is installed with
```
sudo dmidecode -t memory | egrep -o 'Size: [0-9]+ .*'
```

---

### Post by grahammechanical on 2014-01-20
I suspect that this apparent loss of RAM is due to differences in presenting the size of the units that RAM is measured in. Please read the heading Unit Multiples in this link

[http://en.wikipedia.org/wiki/Byte](http://en.wikipedia.org/wiki/Byte)

I admit that I do not understand this myself. I take it to mean that manufacturers use a slightly different system of measurement than computer developers. The Manufacturers choose to use a method that makes it seem that we are getting something larger than the computer experts would say we have. It is the difference between using Decimal and Binary as the measuring stick. For Example.

1000 Kilo Bytes in Decimal is the same actual size as 1024 Kilo Bytes in Binary. If a utility says we have 1000 Kilo Bytes when we are told elsewhere that we have 1024 Kilo Bytes we think we have lost 24 Kilo Bytes somewhere. We have not. When we get to Giga Bytes the differences amount to Mega Bytes.

I did say that I did not understand this, did I not? 

Regards.

---

### Post by michael95 on 2014-01-20
> **btindie said:**
> That'll be in use for shadowing the BIOS / for your on board graphics card, you never get the full amount. You can see how much is installed with
```
sudo dmidecode -t memory | egrep -o 'Size: [0-9]+ .*'
```

> **grahammechanical said:**
> I suspect that this apparent loss of RAM is due to differences in presenting the size of the units that RAM is measured in. Please read the heading Unit Multiples in this link

[http://en.wikipedia.org/wiki/Byte](http://en.wikipedia.org/wiki/Byte)

I admit that I do not understand this myself. I take it to mean that manufacturers use a slightly different system of measurement than computer developers. The Manufacturers choose to use a method that makes it seem that we are getting something larger than the computer experts would say we have. It is the difference between using Decimal and Binary as the measuring stick. For Example.

1000 Kilo Bytes in Decimal is the same actual size as 1024 Kilo Bytes in Binary. If a utility says we have 1000 Kilo Bytes when we are told elsewhere that we have 1024 Kilo Bytes we think we have lost 24 Kilo Bytes somewhere. We have not. When we get to Giga Bytes the differences amount to Mega Bytes.

I did say that I did not understand this, did I not? 

Regards.

@btindie: yes Windows OS said that Bios Reversed Memory is 32,9 and in Resource Monitor Says 33MB i just noticed the whole thing when i run a game which complain to me with this error but still it weird cause i am running non-onboard VGA Card

and the two other computers i have says Bios Reversed Memory :2 MB each one of them 

Also Ubuntu System Monitor Says : 3.8GiB


@grahammechanical : Thanks for the link i will give it a shot :D 


So my system is ok nothing to worry about i can update the system 
with more memory and an SSD i want to? :) 


thanks at both of u for ur information i appreciate it

---

### Post by mcduck on 2014-01-20
Luckily the memory multiplier difference (1Gib = 1024Mib versus 1GB = 1000MB) only applies to hard drives, when it comes to memory such approach would be impossible (or at least horribly impractical) due to how computers work and therefore 1024 is the only multiplier ever used (regardless if it's presented using GiB or GB as the unit).

Anyway, the difference between available and installed memory comes from multiple things, the already mentioned BIOS reserved memory used for communication between the computer's various components etc, any RAM that might be shared with the graphics card, and finally the space Linux kernel itself takes in the memory once the system is booted.

---

### Post by 1clue on 2014-01-20
My linux boxes usually report a bigger difference than that.  How much difference depends on your hardware.  It's not wasted, but also not reported.

You should be able to add RAM up to the limits of your motherboard and budget, whichever is smaller.  I can personally vouch for 64-bit installs up to 32g without trouble.

---

### Post by michael95 on 2014-01-21
ok guys thanks 
everyone 
for ensuring me
that this is normal

i mark the thread as Solved 

thanks again :D

---

