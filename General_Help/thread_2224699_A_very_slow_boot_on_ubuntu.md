---
title: "A very slow boot on ubuntu"
date: 2014-05-17
forum: General Help
---

### Post by mikesgoacademy on 2014-05-17
I am having a very slow boot on my asus G60jx, its a gaming laptop with an i5 and 4 gigs of ram 
I am running ubuntu 14.04.
Here is my dmesg:

```

[    0.000000] Initializing cgroup subsys cpuset[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.11.0-18-generic (buildd@toyol) (gcc version 4.8.1 (Ubuntu/Linaro 4.8.1-10ubuntu8) ) #32-Ubuntu SMP Tue Feb 18 21:11:14 UTC 2014 (Ubuntu 3.11.0-18.32-generic 3.11.10.4)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.11.0-18-generic root=UUID=7a756733-0980-49cd-95d6-f227c8a5f2cf ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009fbff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009fc00-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000df593fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000df594000-0x00000000df5e4fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000df5e5000-0x00000000df5fbfff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000df5fc000-0x00000000df603fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000df604000-0x00000000df61bfff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000df61c000-0x00000000df61cfff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000df61d000-0x00000000df62bfff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000df62c000-0x00000000df630fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000df631000-0x00000000df633fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000df634000-0x00000000df634fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000df635000-0x00000000df638fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000df639000-0x00000000df63bfff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000df63c000-0x00000000df63ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000df640000-0x00000000df64efff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000df64f000-0x00000000df66dfff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000df66e000-0x00000000df66efff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000df66f000-0x00000000dfffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed10000-0x00000000fed13fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed18000-0x00000000fed19fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffa00000-0x00000000ffbfffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffe00000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x0000000117ffffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.6 present.
[    0.000000] DMI: ASUSTek Computer Inc. G60JX/G60JX, BIOS 203 12/10/2009
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x118000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FC0000000 write-back
[    0.000000]   2 base 0C0000000 mask FE0000000 write-back
[    0.000000]   3 base 100000000 mask FE0000000 write-back
[    0.000000]   4 base 118000000 mask FF8000000 uncachable
[    0.000000]   5 base 0FFE00000 mask FFFE00000 write-protect
[    0.000000]   6 base 0F1000000 mask FFF000000 write-combining
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820: last_pfn = 0xdf594 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000fca60-0x000fca6f] mapped at [ffff8800000fca60]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01fd1000, 0x01fd1fff] PGTABLE
[    0.000000] BRK [0x01fd2000, 0x01fd2fff] PGTABLE
[    0.000000] BRK [0x01fd3000, 0x01fd3fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x117e00000-0x117ffffff]
[    0.000000]  [mem 0x117e00000-0x117ffffff] page 2M
[    0.000000] BRK [0x01fd4000, 0x01fd4fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x114000000-0x117dfffff]
[    0.000000]  [mem 0x114000000-0x117dfffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x100000000-0x113ffffff]
[    0.000000]  [mem 0x100000000-0x113ffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0xdf593fff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0xdf3fffff] page 2M
[    0.000000]  [mem 0xdf400000-0xdf593fff] page 4k
[    0.000000] RAMDISK: [mem 0x35e26000-0x36f0afff]
[    0.000000] ACPI: RSDP 00000000000f0410 00024 (v02   PEGA)
[    0.000000] ACPI: XSDT 00000000df63ae18 0005C (v01 _ASUS_ Notebook 00000001 MSFT 00010013)
[    0.000000] ACPI: FACP 00000000df61cc18 000F4 (v04   PEGA   PEGANB 00000001 MSFT 00010013)
[    0.000000] ACPI Warning: 32/64 FACS address mismatch in FADT - two FACS tables! (20130517/tbfadt-395)
[    0.000000] ACPI BIOS Warning (bug): 32/64X FACS address mismatch in FADT - 0xDF64BF40/0x00000000DF64ED40, using 32 (20130517/tbfadt-522)
[    0.000000] ACPI: DSDT 00000000df5d4018 10AC9 (v01   PEGA   PEGANB 00000001 INTL 20051117)
[    0.000000] ACPI: FACS 00000000df64bf40 00040
[    0.000000] ACPI: APIC 00000000df639f18 0008C (v02   PEGA   PEGANB 00000001 MSFT 00010013)
[    0.000000] ACPI: ECDT 00000000df64eb18 000C1 (v01   PEGA   PEGANB 00000001 AMI. 00000003)
[    0.000000] ACPI: SLIC 00000000df646c18 00176 (v01 _ASUS_ Notebook 00000001 MSFT 00000001)
[    0.000000] ACPI: MCFG 00000000df64dd18 0003C (v01   PEGA   PEGANB 00000001 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000df64dc98 00038 (v01   PEGA   PEGANB 00000001 AMI. 00000003)
[    0.000000] ACPI: SSDT 00000000df634018 009F1 (v01  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x0000000117ffffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x117ffffff]
[    0.000000]   NODE_DATA [mem 0x117ff7000-0x117ffbfff]
[    0.000000]  [ffffea0000000000-ffffea00045fffff] PMD -> [ffff880113800000-ffff8801175fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x117ffffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009efff]
[    0.000000]   node   0: [mem 0x00100000-0xdf593fff]
[    0.000000]   node   0: [mem 0x100000000-0x117ffffff]
[    0.000000] On node 0 totalpages: 1013042
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3998 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14231 pages used for memmap
[    0.000000]   DMA32 zone: 910740 pages, LIFO batch:31
[    0.000000]   Normal zone: 1536 pages used for memmap
[    0.000000]   Normal zone: 98304 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x04] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x05] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x06] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] smpboot: Allowing 8 CPUs, 4 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xdf594000-0xdf5e4fff]
[    0.000000] PM: Registered nosave memory: [mem 0xdf5e5000-0xdf5fbfff]
[    0.000000] PM: Registered nosave memory: [mem 0xdf5fc000-0xdf603fff]
[    0.000000] PM: Registered nosave memory: [mem 0xdf604000-0xdf61bfff]
[    0.000000] PM: Registered nosave memory: [mem 0xdf61c000-0xdf61cfff]
[    0.000000] PM: Registered nosave memory: [mem 0xdf61d000-0xdf62bfff]
[    0.000000] PM: Registered nosave memory: [mem 0xdf62c000-0xdf630fff]
[    0.000000] PM: Registered nosave memory: [mem 0xdf631000-0xdf633fff]
[    0.000000] PM: Registered nosave memory: [mem 0xdf634000-0xdf634fff]
[    0.000000] PM: Registered nosave memory: [mem 0xdf635000-0xdf638fff]
[    0.000000] PM: Registered nosave memory: [mem 0xdf639000-0xdf63bfff]
[    0.000000] PM: Registered nosave memory: [mem 0xdf63c000-0xdf63ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xdf640000-0xdf64efff]
[    0.000000] PM: Registered nosave memory: [mem 0xdf64f000-0xdf66dfff]
[    0.000000] PM: Registered nosave memory: [mem 0xdf66e000-0xdf66efff]
[    0.000000] PM: Registered nosave memory: [mem 0xdf66f000-0xdfffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xf7ffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf8000000-0xfbffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfc000000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfed0ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed10000-0xfed13fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed14000-0xfed17fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed18000-0xfed19fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1a000-0xfed1bfff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xff9fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xffa00000-0xffbfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xffc00000-0xffdfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xffe00000-0xffffffff]
[    0.000000] e820: [mem 0xe0000000-0xf7ffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 29 pages/cpu @ffff880117c00000 s86720 r8192 d23872 u262144
[    0.000000] pcpu-alloc: s86720 r8192 d23872 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 997190
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.11.0-18-generic root=UUID=7a756733-0980-49cd-95d6-f227c8a5f2cf ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 3887808K/4052168K available (7154K kernel code, 1083K rwdata, 3312K rodata, 1364K init, 1420K bss, 164360K reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000] 	Offload RCU callbacks from all CPUs
[    0.000000] 	Offload RCU callbacks from CPUs: 0-255.
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 16252928 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.004000] tsc: Detected 2266.701 MHz processor
[    0.000003] Calibrating delay loop (skipped), value calculated using timer frequency.. 4533.40 BogoMIPS (lpj=9066804)
[    0.000006] pid_max: default: 32768 minimum: 301
[    0.000032] Security Framework initialized
[    0.000053] AppArmor: AppArmor initialized
[    0.000054] Yama: becoming mindful.
[    0.000346] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.001333] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.001734] Mount-cache hash table entries: 256
[    0.001926] Initializing cgroup subsys memory
[    0.001937] Initializing cgroup subsys devices
[    0.001938] Initializing cgroup subsys freezer
[    0.001940] Initializing cgroup subsys blkio
[    0.001942] Initializing cgroup subsys perf_event
[    0.001944] Initializing cgroup subsys hugetlb
[    0.001964] CPU: Physical Processor ID: 0
[    0.001965] CPU: Processor Core ID: 0
[    0.001971] mce: CPU supports 9 MCE banks
[    0.001982] CPU0: Thermal monitoring enabled (TM1)
[    0.001992] Last level iTLB entries: 4KB 512, 2MB 7, 4MB 7
[    0.001992] Last level dTLB entries: 4KB 512, 2MB 32, 4MB 32
[    0.001992] tlb_flushall_shift: 6
[    0.002095] Freeing SMP alternatives memory: 28K (ffffffff81e65000 - ffffffff81e6c000)
[    0.004335] ACPI: Core revision 20130517
[    0.012512] ACPI: All ACPI Tables successfully acquired
[    0.015976] ftrace: allocating 27858 entries in 109 pages
[    0.030761] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=0 pin2=0
[    0.070469] smpboot: CPU0: Intel(R) Core(TM) i5 CPU       M 430  @ 2.27GHz (fam: 06, model: 25, stepping: 02)
[    0.175891] Performance Events: PEBS fmt1+, 16-deep LBR, Westmere events, Intel PMU driver.
[    0.175898] perf_event_intel: CPUID marked event: 'bus cycles' unavailable
[    0.175901] ... version:                3
[    0.175902] ... bit width:              48
[    0.175903] ... generic registers:      4
[    0.175904] ... value mask:             0000ffffffffffff
[    0.175905] ... max period:             000000007fffffff
[    0.175906] ... fixed-purpose events:   3
[    0.175907] ... event mask:             000000070000000f
[    0.190843] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.177561] smpboot: Booting Node   0, Processors  #1 #2 #3
[    0.217414] Brought up 4 CPUs
[    0.217420] smpboot: Total of 4 processors activated (18133.60 BogoMIPS)
[    0.220002] devtmpfs: initialized
[    0.221024] EVM: security.selinux
[    0.221026] EVM: security.SMACK64
[    0.221027] EVM: security.capability
[    0.221078] PM: Registering ACPI NVS region [mem 0xdf594000-0xdf5e4fff] (331776 bytes)
[    0.221084] PM: Registering ACPI NVS region [mem 0xdf5fc000-0xdf603fff] (32768 bytes)
[    0.221086] PM: Registering ACPI NVS region [mem 0xdf61c000-0xdf61cfff] (4096 bytes)
[    0.221087] PM: Registering ACPI NVS region [mem 0xdf62c000-0xdf630fff] (20480 bytes)
[    0.221089] PM: Registering ACPI NVS region [mem 0xdf634000-0xdf634fff] (4096 bytes)
[    0.221091] PM: Registering ACPI NVS region [mem 0xdf640000-0xdf64efff] (61440 bytes)
[    0.221093] PM: Registering ACPI NVS region [mem 0xdf66e000-0xdf66efff] (4096 bytes)
[    0.222032] regulator-dummy: no parameters
[    0.222065] RTC time: 18:55:47, date: 05/17/14
[    0.222102] NET: Registered protocol family 16
[    0.222229] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.222232] ACPI: bus type PCI registered
[    0.222234] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.222299] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.222303] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.227436] PCI: Using configuration type 1 for base access
[    0.228288] bio: create slab <bio-0> at 0
[    0.228458] ACPI: Added _OSI(Module Device)
[    0.228460] ACPI: Added _OSI(Processor Device)
[    0.228461] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.228463] ACPI: Added _OSI(Processor Aggregator Device)
[    0.230821] ACPI: EC: EC description table is found, configuring boot EC
[    0.233218] ACPI: Executed 1 blocks of module-level executable AML code
[    0.236495] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.401258] ACPI: SSDT 00000000df638c18 003A9 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.401816] ACPI: Dynamic OEM Table Load:
[    0.401819] ACPI: SSDT           (null) 003A9 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.401921] ACPI: SSDT 00000000df636698 005EB (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.402472] ACPI: Dynamic OEM Table Load:
[    0.402474] ACPI: SSDT           (null) 005EB (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.411106] ACPI: SSDT 00000000df637a98 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.411709] ACPI: Dynamic OEM Table Load:
[    0.411711] ACPI: SSDT           (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.414980] ACPI: SSDT 00000000df635d98 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.415549] ACPI: Dynamic OEM Table Load:
[    0.415551] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.419436] ACPI: Interpreter enabled
[    0.419443] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20130517/hwxface-571)
[    0.419447] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20130517/hwxface-571)
[    0.419462] ACPI: (supports S0 S3 S4 S5)
[    0.419463] ACPI: Using IOAPIC for interrupt routing
[    0.419493] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.419679] ACPI: No dock devices found.
[    0.440921] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    0.441046] acpi PNP0A08:00: Requesting ACPI _OSC control (0x1d)
[    0.441294] acpi PNP0A08:00: ACPI _OSC control (0x1d) granted
[    0.441897] PCI host bridge to bus 0000:00
[    0.441900] pci_bus 0000:00: root bus resource [bus 00-3e]
[    0.441902] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.441904] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.441905] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.441907] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff]
[    0.441909] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
[    0.441910] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
[    0.441912] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff]
[    0.441914] pci_bus 0000:00: root bus resource [mem 0xe0000000-0xfeafffff]
[    0.441922] pci 0000:00:00.0: [8086:0044] type 00 class 0x060000
[    0.441940] DMAR: BIOS has allocated no shadow GTT; disabling IOMMU for graphics
[    0.442018] pci 0000:00:01.0: [8086:0045] type 01 class 0x060400
[    0.442051] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.442157] pci 0000:00:16.0: [8086:3b64] type 00 class 0x078000
[    0.442188] pci 0000:00:16.0: reg 0x10: [mem 0xf4909000-0xf490900f 64bit]
[    0.442282] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.442380] pci 0000:00:1a.0: [8086:3b3c] type 00 class 0x0c0320
[    0.442406] pci 0000:00:1a.0: reg 0x10: [mem 0xf4907000-0xf49073ff]
[    0.442516] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.442573] pci 0000:00:1a.0: System wakeup disabled by ACPI
[    0.442613] pci 0000:00:1b.0: [8086:3b56] type 00 class 0x040300
[    0.442634] pci 0000:00:1b.0: reg 0x10: [mem 0xf4900000-0xf4903fff 64bit]
[    0.442731] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.442790] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    0.442824] pci 0000:00:1c.0: [8086:3b42] type 01 class 0x060400
[    0.442924] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.442984] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.443018] pci 0000:00:1c.1: [8086:3b44] type 01 class 0x060400
[    0.443117] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.443178] pci 0000:00:1c.1: System wakeup disabled by ACPI
[    0.443211] pci 0000:00:1c.2: [8086:3b46] type 01 class 0x060400
[    0.443311] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.443370] pci 0000:00:1c.2: System wakeup disabled by ACPI
[    0.443408] pci 0000:00:1c.4: [8086:3b4a] type 01 class 0x060400
[    0.443509] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.443569] pci 0000:00:1c.4: System wakeup disabled by ACPI
[    0.443602] pci 0000:00:1c.5: [8086:3b4c] type 01 class 0x060400
[    0.443703] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.443764] pci 0000:00:1c.5: System wakeup disabled by ACPI
[    0.443804] pci 0000:00:1d.0: [8086:3b34] type 00 class 0x0c0320
[    0.443829] pci 0000:00:1d.0: reg 0x10: [mem 0xf4906000-0xf49063ff]
[    0.443938] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.443996] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.444030] pci 0000:00:1e.0: [8086:2448] type 01 class 0x060401
[    0.444149] pci 0000:00:1e.0: System wakeup disabled by ACPI
[    0.444181] pci 0000:00:1f.0: [8086:3b09] type 00 class 0x060100
[    0.444366] pci 0000:00:1f.2: [8086:3b28] type 00 class 0x01018f
[    0.444388] pci 0000:00:1f.2: reg 0x10: [io  0xe0d0-0xe0d7]
[    0.444399] pci 0000:00:1f.2: reg 0x14: [io  0xe0c0-0xe0c3]
[    0.444411] pci 0000:00:1f.2: reg 0x18: [io  0xe0b0-0xe0b7]
[    0.444422] pci 0000:00:1f.2: reg 0x1c: [io  0xe0a0-0xe0a3]
[    0.444433] pci 0000:00:1f.2: reg 0x20: [io  0xe090-0xe09f]
[    0.444444] pci 0000:00:1f.2: reg 0x24: [io  0xe080-0xe08f]
[    0.444566] pci 0000:00:1f.3: [8086:3b30] type 00 class 0x0c0500
[    0.444587] pci 0000:00:1f.3: reg 0x10: [mem 0xf4905000-0xf49050ff 64bit]
[    0.444617] pci 0000:00:1f.3: reg 0x20: [io  0xe000-0xe01f]
[    0.444719] pci 0000:00:1f.5: [8086:3b2d] type 00 class 0x010185
[    0.444741] pci 0000:00:1f.5: reg 0x10: [io  0xe070-0xe077]
[    0.444752] pci 0000:00:1f.5: reg 0x14: [io  0xe060-0xe063]
[    0.444763] pci 0000:00:1f.5: reg 0x18: [io  0xe050-0xe057]
[    0.444774] pci 0000:00:1f.5: reg 0x1c: [io  0xe040-0xe043]
[    0.444785] pci 0000:00:1f.5: reg 0x20: [io  0xe030-0xe03f]
[    0.444796] pci 0000:00:1f.5: reg 0x24: [io  0xe020-0xe02f]
[    0.444926] pci 0000:00:1f.6: [8086:3b32] type 00 class 0x118000
[    0.444955] pci 0000:00:1f.6: reg 0x10: [mem 0xf4904000-0xf4904fff 64bit]
[    0.445157] pci 0000:01:00.0: [10de:0cb1] type 00 class 0x030000
[    0.445167] pci 0000:01:00.0: reg 0x10: [mem 0xf2000000-0xf2ffffff]
[    0.445176] pci 0000:01:00.0: reg 0x14: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.445186] pci 0000:01:00.0: reg 0x1c: [mem 0xf0000000-0xf1ffffff 64bit pref]
[    0.445192] pci 0000:01:00.0: reg 0x24: [io  0xd000-0xd07f]
[    0.445199] pci 0000:01:00.0: reg 0x30: [mem 0xf3000000-0xf307ffff pref]
[    0.445272] pci 0000:01:00.1: [10de:0be4] type 00 class 0x040300
[    0.445281] pci 0000:01:00.1: reg 0x10: [mem 0xf3080000-0xf3083fff]
[    0.445385] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.445387] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    0.445390] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xf30fffff]
[    0.445460] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.445558] pci 0000:03:00.0: [168c:002b] type 00 class 0x028000
[    0.445582] pci 0000:03:00.0: reg 0x10: [mem 0xf4800000-0xf480ffff 64bit]
[    0.445690] pci 0000:03:00.0: supports D1
[    0.445691] pci 0000:03:00.0: PME# supported from D0 D1 D3hot D3cold
[    0.445722] pci 0000:03:00.0: System wakeup disabled by ACPI
[    0.452241] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    0.452253] pci 0000:00:1c.1:   bridge window [mem 0xf4800000-0xf48fffff]
[    0.452407] pci 0000:00:1c.2: PCI bridge to [bus 04-05]
[    0.452412] pci 0000:00:1c.2:   bridge window [io  0xc000-0xcfff]
[    0.452417] pci 0000:00:1c.2:   bridge window [mem 0xf3200000-0xf45fffff]
[    0.452520] pci 0000:06:00.0: [1180:e822] type 00 class 0x080500
[    0.452537] pci 0000:06:00.0: MMC controller base frequency changed to 50Mhz.
[    0.452548] pci 0000:06:00.0: proprietary Ricoh MMC controller disabled (via firewire function)
[    0.452550] pci 0000:06:00.0: MMC cards are now supported by standard SDHCI controller
[    0.452571] pci 0000:06:00.0: reg 0x10: [mem 0xf4703000-0xf47030ff]
[    0.452735] pci 0000:06:00.0: supports D1 D2
[    0.452736] pci 0000:06:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.452814] pci 0000:06:00.1: [1180:e230] type 00 class 0x088000
[    0.452837] pci 0000:06:00.1: reg 0x10: [mem 0xf4702000-0xf47020ff]
[    0.452998] pci 0000:06:00.1: supports D1 D2
[    0.453000] pci 0000:06:00.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.453078] pci 0000:06:00.3: [1180:e832] type 00 class 0x0c0010
[    0.453101] pci 0000:06:00.3: reg 0x10: [mem 0xf4700000-0xf47007ff]
[    0.453263] pci 0000:06:00.3: supports D1 D2
[    0.453265] pci 0000:06:00.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.460266] pci 0000:00:1c.4: PCI bridge to [bus 06]
[    0.460278] pci 0000:00:1c.4:   bridge window [mem 0xf4700000-0xf47fffff]
[    0.460399] pci 0000:07:00.0: [1969:1063] type 00 class 0x020000
[    0.460426] pci 0000:07:00.0: reg 0x10: [mem 0xf4600000-0xf463ffff 64bit]
[    0.460439] pci 0000:07:00.0: reg 0x18: [io  0xb000-0xb07f]
[    0.460565] pci 0000:07:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.460600] pci 0000:07:00.0: System wakeup disabled by ACPI
[    0.468249] pci 0000:00:1c.5: PCI bridge to [bus 07]
[    0.468257] pci 0000:00:1c.5:   bridge window [io  0xb000-0xbfff]
[    0.468264] pci 0000:00:1c.5:   bridge window [mem 0xf4600000-0xf46fffff]
[    0.468381] pci 0000:00:1e.0: PCI bridge to [bus 08] (subtractive decode)
[    0.468394] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.468396] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.468397] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.468399] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
[    0.468400] pci 0000:00:1e.0:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.468402] pci 0000:00:1e.0:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.468404] pci 0000:00:1e.0:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
[    0.468405] pci 0000:00:1e.0:   bridge window [mem 0xe0000000-0xfeafffff] (subtractive decode)
[    0.468443] acpi PNP0A08:00: Disabling ASPM (FADT indicates it is unsupported)
[    0.475029] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.475083] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.475135] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 *4 5 6 7 10 12 14 15)
[    0.475187] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[    0.475238] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.475289] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    0.475342] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 *3 4 5 6 7 10 12 14 15)
[    0.475393] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.475441] ACPI: PCI Root Bridge [CPBG] (domain 0000 [bus 3f])
[    0.475444] acpi PNP0A03:00: ACPI _OSC support notification failed, disabling PCIe ASPM
[    0.475446] acpi PNP0A03:00: Unable to request _OSC control (_OSC support mask: 0x08)
[    0.475505] PCI host bridge to bus 0000:3f
[    0.475508] pci_bus 0000:3f: root bus resource [bus 3f]
[    0.475513] pci 0000:3f:00.0: [8086:2c62] type 00 class 0x060000
[    0.475551] pci 0000:3f:00.1: [8086:2d01] type 00 class 0x060000
[    0.475591] pci 0000:3f:02.0: [8086:2d10] type 00 class 0x060000
[    0.475626] pci 0000:3f:02.1: [8086:2d11] type 00 class 0x060000
[    0.475661] pci 0000:3f:02.2: [8086:2d12] type 00 class 0x060000
[    0.475696] pci 0000:3f:02.3: [8086:2d13] type 00 class 0x060000
[    0.476041] ACPI: Enabled 1 GPEs in block 00 to 3F
[    0.476048] ACPI: \_SB_.PCI0: notify handler is installed
[    0.476101] ACPI: \_SB_.CPBG: notify handler is installed
[    0.476113] Found 2 acpi root devices
[    0.476178] ACPI: EC: GPE = 0x1b, I/O: command/status = 0x66, data = 0x62
[    0.476287] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.476290] vgaarb: loaded
[    0.476291] vgaarb: bridge control possible 0000:01:00.0
[    0.476449] SCSI subsystem initialized
[    0.476452] ACPI: bus type ATA registered
[    0.476521] libata version 3.00 loaded.
[    0.476550] ACPI: bus type USB registered
[    0.476566] usbcore: registered new interface driver usbfs
[    0.476574] usbcore: registered new interface driver hub
[    0.476602] usbcore: registered new device driver usb
[    0.476706] PCI: Using ACPI for IRQ routing
[    0.478891] PCI: pci_cache_line_size set to 64 bytes
[    0.478973] e820: reserve RAM buffer [mem 0x0009fc00-0x0009ffff]
[    0.478975] e820: reserve RAM buffer [mem 0xdf594000-0xdfffffff]
[    0.479069] NetLabel: Initializing
[    0.479071] NetLabel:  domain hash size = 128
[    0.479072] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.479082] NetLabel:  unlabeled traffic allowed by default
[    0.479151] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.479156] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.481186] Switched to clocksource hpet
[    0.485919] AppArmor: AppArmor Filesystem Enabled
[    0.485955] pnp: PnP ACPI init
[    0.485971] ACPI: bus type PNP registered
[    0.486031] pnp 00:00: [dma 4]
[    0.486057] pnp 00:00: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.486077] pnp 00:01: Plug and Play ACPI device, IDs INT0800 (active)
[    0.486200] pnp 00:02: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.486234] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.486295] system 00:04: [io  0x0680-0x069f] has been reserved
[    0.486298] system 00:04: [io  0xff00-0xff0f] has been reserved
[    0.486300] system 00:04: [io  0xffff] has been reserved
[    0.486302] system 00:04: [io  0xffff] has been reserved
[    0.486304] system 00:04: [io  0x0400-0x047f] could not be reserved
[    0.486306] system 00:04: [io  0x0500-0x057f] has been reserved
[    0.486308] system 00:04: [io  0x164e-0x164f] has been reserved
[    0.486311] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.486337] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.486410] system 00:06: [io  0x025d] has been reserved
[    0.486412] system 00:06: [io  0x025c] has been reserved
[    0.486418] system 00:06: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.486420] system 00:06: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.486422] system 00:06: [mem 0xfec10000-0xfec17fff] has been reserved
[    0.486424] system 00:06: [mem 0xfec18000-0xfec1ffff] has been reserved
[    0.486426] system 00:06: [mem 0xfec20000-0xfec27fff] has been reserved
[    0.486427] system 00:06: [mem 0xfec30000-0xfec37fff] has been reserved
[    0.486429] system 00:06: [mem 0xfec38000-0xfec3ffff] has been reserved
[    0.486431] system 00:06: [mem 0xff000000-0xffffffff] could not be reserved
[    0.486434] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.486471] system 00:07: [io  0x0240-0x0259] has been reserved
[    0.486474] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.486533] pnp 00:08: Plug and Play ACPI device, IDs SYN0a06 SYN1d00 SYN0002 PNP0f13 (active)
[    0.486582] pnp 00:09: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.486660] system 00:0a: [io  0x04d0-0x04d1] has been reserved
[    0.486663] system 00:0a: [io  0x0400-0x047f] could not be reserved
[    0.486665] system 00:0a: [io  0x0500-0x057f] has been reserved
[    0.486667] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.486724] system 00:0b: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.486727] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.489531] system 00:0c: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.489534] system 00:0c: [mem 0xfed10000-0xfed13fff] has been reserved
[    0.489536] system 00:0c: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.489538] system 00:0c: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.489540] system 00:0c: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.489542] system 00:0c: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.489543] system 00:0c: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.489546] system 00:0c: [mem 0xff000000-0xffffffff] could not be reserved
[    0.489548] system 00:0c: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.489550] system 00:0c: [mem 0xfff9f000-0xfff9ffff] has been reserved
[    0.489552] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.489753] system 00:0d: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.489756] system 00:0d: [mem 0x000c0000-0x000dffff] could not be reserved
[    0.489758] system 00:0d: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.489760] system 00:0d: [mem 0x00100000-0xdfffffff] could not be reserved
[    0.489763] system 00:0d: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.489782] pnp: PnP ACPI: found 14 devices
[    0.489783] ACPI: bus type PNP unregistered
[    0.496689] pci 0000:00:1c.2: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 04-05] add_size 200000
[    0.496721] pci 0000:00:1c.2: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.496726] pci 0000:00:1c.2: BAR 15: assigned [mem 0xf4a00000-0xf4bfffff 64bit pref]
[    0.496729] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.496732] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    0.496735] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xf30fffff]
[    0.496740] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.496754] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    0.496760] pci 0000:00:1c.1:   bridge window [mem 0xf4800000-0xf48fffff]
[    0.496770] pci 0000:00:1c.2: PCI bridge to [bus 04-05]
[    0.496773] pci 0000:00:1c.2:   bridge window [io  0xc000-0xcfff]
[    0.496779] pci 0000:00:1c.2:   bridge window [mem 0xf3200000-0xf45fffff]
[    0.496784] pci 0000:00:1c.2:   bridge window [mem 0xf4a00000-0xf4bfffff 64bit pref]
[    0.496792] pci 0000:00:1c.4: PCI bridge to [bus 06]
[    0.496797] pci 0000:00:1c.4:   bridge window [mem 0xf4700000-0xf47fffff]
[    0.496807] pci 0000:00:1c.5: PCI bridge to [bus 07]
[    0.496811] pci 0000:00:1c.5:   bridge window [io  0xb000-0xbfff]
[    0.496817] pci 0000:00:1c.5:   bridge window [mem 0xf4600000-0xf46fffff]
[    0.496827] pci 0000:00:1e.0: PCI bridge to [bus 08]
[    0.497314] pci 0000:00:1e.0: setting latency timer to 64
[    0.497320] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.497321] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.497323] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.497325] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.497326] pci_bus 0000:00: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.497328] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.497330] pci_bus 0000:00: resource 10 [mem 0x000dc000-0x000dffff]
[    0.497331] pci_bus 0000:00: resource 11 [mem 0xe0000000-0xfeafffff]
[    0.497333] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    0.497335] pci_bus 0000:01: resource 1 [mem 0xe0000000-0xf30fffff]
[    0.497337] pci_bus 0000:03: resource 1 [mem 0xf4800000-0xf48fffff]
[    0.497339] pci_bus 0000:04: resource 0 [io  0xc000-0xcfff]
[    0.497341] pci_bus 0000:04: resource 1 [mem 0xf3200000-0xf45fffff]
[    0.497343] pci_bus 0000:04: resource 2 [mem 0xf4a00000-0xf4bfffff 64bit pref]
[    0.497344] pci_bus 0000:06: resource 1 [mem 0xf4700000-0xf47fffff]
[    0.497347] pci_bus 0000:07: resource 0 [io  0xb000-0xbfff]
[    0.497348] pci_bus 0000:07: resource 1 [mem 0xf4600000-0xf46fffff]
[    0.497350] pci_bus 0000:08: resource 4 [io  0x0000-0x0cf7]
[    0.497352] pci_bus 0000:08: resource 5 [io  0x0d00-0xffff]
[    0.497353] pci_bus 0000:08: resource 6 [mem 0x000a0000-0x000bffff]
[    0.497355] pci_bus 0000:08: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.497357] pci_bus 0000:08: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.497358] pci_bus 0000:08: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.497360] pci_bus 0000:08: resource 10 [mem 0x000dc000-0x000dffff]
[    0.497362] pci_bus 0000:08: resource 11 [mem 0xe0000000-0xfeafffff]
[    0.497398] NET: Registered protocol family 2
[    0.497570] TCP established hash table entries: 32768 (order: 7, 524288 bytes)
[    0.497749] TCP bind hash table entries: 32768 (order: 7, 524288 bytes)
[    0.497900] TCP: Hash tables configured (established 32768 bind 32768)
[    0.497931] TCP: reno registered
[    0.497938] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.497970] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.498057] NET: Registered protocol family 1
[    0.498453] pci 0000:01:00.0: Boot video device
[    0.498486] PCI: CLS 64 bytes, default 64
[    0.498530] Trying to unpack rootfs image as initramfs...
[    0.790124] Freeing initrd memory: 17300K (ffff880035e26000 - ffff880036f0b000)
[    0.790131] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.790134] software IO TLB [mem 0xdb594000-0xdf594000] (64MB) mapped at [ffff8800db594000-ffff8800df593fff]
[    0.790357] Scanning for low memory corruption every 60 seconds
[    0.790678] Initialise module verification
[    0.790724] audit: initializing netlink socket (disabled)
[    0.790736] type=2000 audit(1400352947.540:1): initialized
[    0.815591] bounce pool size: 64 pages
[    0.815602] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.816719] zbud: loaded
[    0.816858] VFS: Disk quotas dquot_6.5.2
[    0.816898] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.817402] fuse init (API version 7.22)
[    0.817485] msgmni has been set to 7627
[    0.818143] Key type asymmetric registered
[    0.818147] Asymmetric key parser 'x509' registered
[    0.818180] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.818225] io scheduler noop registered
[    0.818228] io scheduler deadline registered (default)
[    0.818255] io scheduler cfq registered
[    0.818365] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.818436] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    0.818524] pcieport 0000:00:1c.1: irq 42 for MSI/MSI-X
[    0.818616] pcieport 0000:00:1c.2: irq 43 for MSI/MSI-X
[    0.818712] pcieport 0000:00:1c.4: irq 44 for MSI/MSI-X
[    0.818800] pcieport 0000:00:1c.5: irq 45 for MSI/MSI-X
[    0.818886] pcieport 0000:00:01.0: Signaling PME through PCIe PME interrupt
[    0.818888] pci 0000:01:00.0: Signaling PME through PCIe PME interrupt
[    0.818890] pci 0000:01:00.1: Signaling PME through PCIe PME interrupt
[    0.818893] pcie_pme 0000:00:01.0:pcie01: service driver pcie_pme loaded
[    0.818912] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
[    0.818917] pcie_pme 0000:00:1c.0:pcie01: service driver pcie_pme loaded
[    0.818935] pcieport 0000:00:1c.1: Signaling PME through PCIe PME interrupt
[    0.818937] pci 0000:03:00.0: Signaling PME through PCIe PME interrupt
[    0.818942] pcie_pme 0000:00:1c.1:pcie01: service driver pcie_pme loaded
[    0.818960] pcieport 0000:00:1c.2: Signaling PME through PCIe PME interrupt
[    0.818965] pcie_pme 0000:00:1c.2:pcie01: service driver pcie_pme loaded
[    0.818983] pcieport 0000:00:1c.4: Signaling PME through PCIe PME interrupt
[    0.818985] pci 0000:06:00.0: Signaling PME through PCIe PME interrupt
[    0.818986] pci 0000:06:00.1: Signaling PME through PCIe PME interrupt
[    0.818988] pci 0000:06:00.3: Signaling PME through PCIe PME interrupt
[    0.818993] pcie_pme 0000:00:1c.4:pcie01: service driver pcie_pme loaded
[    0.819013] pcieport 0000:00:1c.5: Signaling PME through PCIe PME interrupt
[    0.819014] pci 0000:07:00.0: Signaling PME through PCIe PME interrupt
[    0.819019] pcie_pme 0000:00:1c.5:pcie01: service driver pcie_pme loaded
[    0.819030] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.819088] pciehp 0000:00:1c.2:pcie04: HPC vendor_id 8086 device_id 3b46 ss_vid 1043 ss_did 1f47
[    0.819124] pciehp 0000:00:1c.2:pcie04: service driver pciehp loaded
[    0.819129] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.819180] intel_idle: MWAIT substates: 0x1120
[    0.819182] intel_idle: v0.4 model 0x25
[    0.819183] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.819312] ACPI: AC Adapter [AC0] (on-line)
[    0.819400] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.821347] ACPI: Lid Switch [LID]
[    0.821405] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    0.821410] ACPI: Sleep Button [SLPB]
[    0.821439] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.821442] ACPI: Power Button [PWRF]
[    0.821507] ACPI: Requesting acpi_cpufreq
[    0.826250] thermal LNXTHERM:00: registered as thermal_zone0
[    0.826253] ACPI: Thermal Zone [THRM] (63 C)
[    0.826276] GHES: HEST is not enabled!
[    0.826360] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.827996] Linux agpgart interface v0.103
[    0.829583] brd: module loaded
[    0.830512] loop: module loaded
[    0.830628] ata_piix 0000:00:1f.2: version 2.13
[    0.830783] ata_piix 0000:00:1f.2: MAP [
[    0.830785]  P0 P2 P1 P3 ]
[    0.855653] ACPI: Battery Slot [BAT0] (battery present)
[    0.985484] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.985698] scsi0 : ata_piix
[    0.985944] scsi1 : ata_piix
[    0.986141] ata1: SATA max UDMA/133 cmd 0xe0d0 ctl 0xe0c0 bmdma 0xe090 irq 19
[    0.986148] ata2: SATA max UDMA/133 cmd 0xe0b0 ctl 0xe0a0 bmdma 0xe098 irq 19
[    0.986263] ata_piix 0000:00:1f.5: MAP [
[    0.986265]  P0 -- P1 -- ]
[    1.141551] ata_piix 0000:00:1f.5: SCR access via SIDPR is available but doesn't work
[    1.141560] ata_piix 0000:00:1f.5: setting latency timer to 64
[    1.141720] scsi2 : ata_piix
[    1.141951] scsi3 : ata_piix
[    1.142135] ata3: SATA max UDMA/133 cmd 0xe070 ctl 0xe060 bmdma 0xe030 irq 19
[    1.142137] ata4: SATA max UDMA/133 cmd 0xe050 ctl 0xe040 bmdma 0xe038 irq 19
[    1.142410] libphy: Fixed MDIO Bus: probed
[    1.142481] tun: Universal TUN/TAP device driver, 1.6
[    1.142482] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.142538] PPP generic driver version 2.4.2
[    1.142590] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.142592] ehci-pci: EHCI PCI platform driver
[    1.142696] ehci-pci 0000:00:1a.0: setting latency timer to 64
[    1.142710] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    1.142716] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.142731] ehci-pci 0000:00:1a.0: debug port 2
[    1.146659] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    1.146675] ehci-pci 0000:00:1a.0: irq 16, io mem 0xf4907000
[    1.157555] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.157578] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.157579] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.157581] usb usb1: Product: EHCI Host Controller
[    1.157583] usb usb1: Manufacturer: Linux 3.11.0-18-generic ehci_hcd
[    1.157584] usb usb1: SerialNumber: 0000:00:1a.0
[    1.157691] hub 1-0:1.0: USB hub found
[    1.157696] hub 1-0:1.0: 2 ports detected
[    1.157852] ehci-pci 0000:00:1d.0: setting latency timer to 64
[    1.157860] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    1.157866] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.157880] ehci-pci 0000:00:1d.0: debug port 2
[    1.161804] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    1.161818] ehci-pci 0000:00:1d.0: irq 23, io mem 0xf4906000
[    1.173563] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.173574] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.173576] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.173578] usb usb2: Product: EHCI Host Controller
[    1.173579] usb usb2: Manufacturer: Linux 3.11.0-18-generic ehci_hcd
[    1.173581] usb usb2: SerialNumber: 0000:00:1d.0
[    1.173675] hub 2-0:1.0: USB hub found
[    1.173679] hub 2-0:1.0: 2 ports detected
[    1.173747] ehci-platform: EHCI generic platform driver
[    1.173753] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.173755] ohci-pci: OHCI PCI platform driver
[    1.173762] ohci-platform: OHCI generic platform driver
[    1.173767] uhci_hcd: USB Universal Host Controller Interface driver
[    1.173822] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.177543] i8042: Detected active multiplexing controller, rev 1.1
[    1.179021] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.179026] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.179047] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.179066] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.179080] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.179194] mousedev: PS/2 mouse device common for all mice
[    1.179392] rtc_cmos 00:05: RTC can wake from S4
[    1.179534] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.179567] rtc_cmos 00:05: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    1.179622] device-mapper: uevent: version 1.0.3
[    1.179689] device-mapper: ioctl: 4.25.0-ioctl (2013-06-26) initialised: dm-devel@redhat.com
[    1.179756] cpuidle: using governor ladder
[    1.179843] cpuidle: using governor menu
[    1.179852] ledtrig-cpu: registered to indicate activity on CPUs
[    1.179936] TCP: cubic registered
[    1.180017] NET: Registered protocol family 10
[    1.180205] NET: Registered protocol family 17
[    1.180214] Key type dns_resolver registered
[    1.180472] PM: Hibernation image not present or could not be loaded.
[    1.180476] Loading module verification certificates
[    1.181429] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: 9d94dc8d073854d044b3fa3652786ac75597c2f5'
[    1.181443] registered taskstats version 1
[    1.184546] Key type trusted registered
[    1.187911] Key type encrypted registered
[    1.191278] AppArmor: AppArmor sha1 policy hashing enabled
[    1.191984]   Magic number: 14:72:949
[    1.191999] mdio_bus fixed-0: hash matches
[    1.192048] tty tty6: hash matches
[    1.192110] memory memory2: hash matches
[    1.192183] rtc_cmos 00:05: setting system clock to 2014-05-17 18:55:48 UTC (1400352948)
[    1.193437] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.193439] EDD information not available.
[    1.219038] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.469800] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.602286] usb 1-1: New USB device found, idVendor=8087, idProduct=0020
[    1.602291] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.602574] hub 1-1:1.0: USB hub found
[    1.602772] hub 1-1:1.0: 6 ports detected
[    1.713927] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    1.789961] tsc: Refined TSC clocksource calibration: 2266.666 MHz
[    1.846406] usb 2-1: New USB device found, idVendor=8087, idProduct=0020
[    1.846411] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.846816] hub 2-1:1.0: USB hub found
[    1.847017] hub 2-1:1.0: 8 ports detected
[    1.918225] usb 1-1.6: new high-speed USB device number 3 using ehci-pci
[    2.054532] usb 1-1.6: New USB device found, idVendor=04f2, idProduct=b071
[    2.054539] usb 1-1.6: New USB device strings: Mfr=2, Product=1, SerialNumber=3
[    2.054542] usb 1-1.6: Product: CNF7129
[    2.054546] usb 1-1.6: Manufacturer: Chicony Electronics Co., Ltd.
[    2.054549] usb 1-1.6: SerialNumber: SN0001
[    2.334247] ata1.01: failed to resume link (SControl 0)
[    2.346251] ata2.01: failed to resume link (SControl 0)
[    2.490413] ata1.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.490434] ata1.01: SATA link down (SStatus 0 SControl 0)
[    2.502405] ata2.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.502430] ata2.01: SATA link down (SStatus 0 SControl 0)
[    2.502453] ata2.01: link offline, clearing class 3 to NONE
[    2.510623] ata2.00: ATAPI: HL-DT-STDVDRAM GT30N, AS02, max UDMA/100
[    2.526630] ata2.00: configured for UDMA/100
[    2.542568] ata1.00: ATA-8: ST9500420AS, 0002SDM1, max UDMA/133
[    2.542573] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.559142] ata1.00: configured for UDMA/133
[    2.559486] scsi 0:0:0:0: Direct-Access     ATA      ST9500420AS      0002 PQ: 0 ANSI: 5
[    2.559670] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    2.559680] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.559767] sd 0:0:0:0: [sda] Write Protect is off
[    2.559771] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.559900] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.562189] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GT30N     AS02 PQ: 0 ANSI: 5
[    2.566442] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.566447] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.566824] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.567050] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.609376]  sda: sda1 sda2 sda3 < sda5 sda6 >
[    2.610152] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.611096] Freeing unused kernel memory: 1364K (ffffffff81d10000 - ffffffff81e65000)
[    2.611099] Write protecting the kernel read-only data: 12288k
[    2.613321] Freeing unused kernel memory: 1028K (ffff8800016ff000 - ffff880001800000)
[    2.614944] Freeing unused kernel memory: 784K (ffff880001b3c000 - ffff880001c00000)
[    2.628538] systemd-udevd[133]: starting version 204
[    2.657318] sdhci: Secure Digital Host Controller Interface driver
[    2.657322] sdhci: Copyright(c) Pierre Ossman
[    2.658839] sdhci-pci 0000:06:00.0: SDHCI controller found [1180:e822] (rev 1)
[    2.658969] sdhci-pci 0000:06:00.0: Will use DMA mode even though HW doesn't fully claim to support it.
[    2.658978] mmc0: no vqmmc regulator found
[    2.658980] mmc0: no vmmc regulator found
[    2.659069] mmc0: SDHCI controller on PCI [0000:06:00.0] using DMA
[    2.686918] atl1c 0000:07:00.0: version 1.0.1.1-NAPI
[    2.734533] firewire_ohci 0000:06:00.3: added OHCI v1.0 device as card 0, 4 IR + 4 IT contexts, quirks 0x11
[    2.794585] Switched to clocksource tsc
[    3.234952] firewire_core 0000:06:00.3: created device fw0: GUID 001e8c0000c4ea68, S400
[    3.507245] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[    3.517410] psmouse serio4: synaptics: Touchpad model: 1, fw: 7.0, id: 0x1c0b3, caps: 0xd04711/0xa00000/0x20000, board id: 3655, fw id: 594499
[    3.556572] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input4
[   22.076435] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   22.153834] systemd-udevd[299]: starting version 204
[   22.342190] lp: driver loaded but no devices found
[   22.347611] ppdev: user-space parallel port driver
[   22.363529] asus_laptop: Asus Laptop Support version 0.42
[   22.363716] asus_laptop: BSTS called, 0x742f returned
[   22.363732] asus_laptop:    model detected
[   22.369971] asus_laptop: Backlight controlled by ACPI video driver
[   22.370044] input: Asus Laptop extra buttons as /devices/platform/asus_laptop/input/input5
[   22.393136] acpi device:47: registered as cooling_device4
[   22.393203] ACPI: Video Device [VGA1] (multi-head: yes  rom: no  post: no)
[   22.393308] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:44/LNXVIDEO:01/input/input6
[   22.397138] mei_me 0000:00:16.0: setting latency timer to 64
[   22.397187] mei_me 0000:00:16.0: irq 46 for MSI/MSI-X
[   22.422357] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \GPIS 1 (20130517/utaddress-251)
[   22.422365] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIX 2 (20130517/utaddress-251)
[   22.422370] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 3 (20130517/utaddress-251)
[   22.422375] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   22.422379] ACPI Warning: 0x0000000000000540-0x000000000000054f SystemIO conflicts with Region \GPXX 1 (20130517/utaddress-251)
[   22.422384] ACPI Warning: 0x0000000000000540-0x000000000000054f SystemIO conflicts with Region \GPIO 2 (20130517/utaddress-251)
[   22.422388] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   22.422390] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPXX 1 (20130517/utaddress-251)
[   22.422394] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 2 (20130517/utaddress-251)
[   22.422398] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   22.422400] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPXX 1 (20130517/utaddress-251)
[   22.422404] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 2 (20130517/utaddress-251)
[   22.422408] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   22.422410] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   22.430944] cfg80211: Calling CRDA to update world regulatory domain
[   22.445712] intel ips 0000:00:1f.6: CPU TDP doesn't match expected value (found 25, expected 29)
[   22.445826] [drm] Initialized drm 1.1.0 20060810
[   22.445968] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled until i915 loads
[   22.449021] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 90
[   22.455693] nvidia: module license 'NVIDIA' taints kernel.
[   22.455700] Disabling lock debugging due to kernel taint
[   22.464215] nvidia: module verification failed: signature and/or required key missing - tainting kernel
[   22.472526] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   22.474587] [drm] Initialized nvidia-drm 0.0.0 20130102 for 0000:01:00.0 on minor 0
[   22.474603] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  331.38  Wed Jan  8 19:32:30 PST 2014
[   22.488089] microcode: CPU0 sig=0x20652, pf=0x10, revision=0x9
[   22.532870] ath: EEPROM regdomain: 0x60
[   22.532875] ath: EEPROM indicates we should expect a direct regpair map
[   22.532878] ath: Country alpha2 being used: 00
[   22.532880] ath: Regpair used: 0x60
[   22.543639] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   22.544063] ieee80211 phy0: Atheros AR9285 Rev:2 mem=0xffffc900047e0000, irq=17
[   22.553816] snd_hda_intel 0000:00:1b.0: irq 47 for MSI/MSI-X
[   22.565350] SKU: Nid=0x1d sku_cfg=0x40178e2d
[   22.565353] SKU: port_connectivity=0x1
[   22.565355] SKU: enable_pcbeep=0x1
[   22.565356] SKU: check_sum=0x00000007
[   22.565357] SKU: customization=0x0000008e
[   22.565358] SKU: external_amp=0x5
[   22.565358] SKU: platform_type=0x1
[   22.565359] SKU: swap=0x0
[   22.565360] SKU: override=0x1
[   22.565637] autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[   22.565639]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   22.565640]    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
[   22.565641]    mono: mono_out=0x0
[   22.565642]    dig-out=0x1e/0x0
[   22.565642]    inputs:
[   22.565644]      Internal Mic=0x19
[   22.565646]      Mic=0x18
[   22.565647]      Line=0x1a
[   22.565648] realtek: No valid SSID, checking pincfg 0x40178e2d for NID 0x1d
[   22.565649] realtek: Enabling init ASM_ID=0x8e2d CODEC_ID=10ec0663
[   22.574993] input: HDA Intel MID Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   22.575074] input: HDA Intel MID Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   22.575126] input: HDA Intel MID Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   22.575426] hda_intel: Disabling MSI
[   22.575436] hda-intel 0000:01:00.1: Handle VGA-switcheroo audio client
[   22.575467] hda-intel 0000:01:00.1: Disabling 64bit DMA
[   22.578745] hda-intel 0000:01:00.1: Enable delay in RIRB handling
[   22.605471] type=1400 audit(1400352969.898:2): apparmor="STATUS" operation="profile_load" parent=364 profile="unconfined" name="/sbin/dhclient" pid=374 comm="apparmor_parser"
[   22.605481] type=1400 audit(1400352969.898:3): apparmor="STATUS" operation="profile_load" parent=364 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=374 comm="apparmor_parser"
[   22.605488] type=1400 audit(1400352969.898:4): apparmor="STATUS" operation="profile_load" parent=364 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=374 comm="apparmor_parser"
[   22.606136] type=1400 audit(1400352969.898:5): apparmor="STATUS" operation="profile_replace" parent=364 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=374 comm="apparmor_parser"
[   22.606145] type=1400 audit(1400352969.898:6): apparmor="STATUS" operation="profile_replace" parent=364 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=374 comm="apparmor_parser"
[   22.606470] type=1400 audit(1400352969.898:7): apparmor="STATUS" operation="profile_replace" parent=364 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=374 comm="apparmor_parser"
[   22.609113] type=1400 audit(1400352969.902:8): apparmor="STATUS" operation="profile_load" parent=364 profile="unconfined" name="/usr/sbin/ntpd" pid=414 comm="apparmor_parser"
[   22.609171] Linux video capture interface: v2.00
[   22.617765] uvcvideo: Found UVC 1.00 device CNF7129 (04f2:b071)
[   22.640565] input: CNF7129 as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/input/input10
[   22.640654] usbcore: registered new interface driver uvcvideo
[   22.640656] USB Video Class driver (1.1.1)
[   22.790437] microcode: CPU1 sig=0x20652, pf=0x10, revision=0x9
[   22.791964] microcode: CPU2 sig=0x20652, pf=0x10, revision=0x9
[   22.792513] microcode: CPU3 sig=0x20652, pf=0x10, revision=0x9
[   22.793204] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   22.828616] kvm: VM_EXIT_LOAD_IA32_PERF_GLOBAL_CTRL does not work properly. Using workaround
[   22.952465] cfg80211: World regulatory domain updated:
[   22.952469] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   22.952471] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.952473] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.952474] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   22.952476] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.952477] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   23.243188] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[   23.401304] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input11
[   23.401592] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input12
[   23.401773] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input13
[   23.401957] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input14
[   23.807700] init: failsafe main process (612) killed by TERM signal
[   24.438327] Bluetooth: Core ver 2.16
[   24.438359] NET: Registered protocol family 31
[   24.438361] Bluetooth: HCI device and connection manager initialized
[   24.438374] Bluetooth: HCI socket layer initialized
[   24.438377] Bluetooth: L2CAP socket layer initialized
[   24.438384] Bluetooth: SCO socket layer initialized
[   24.443276] Bluetooth: RFCOMM TTY layer initialized
[   24.443293] Bluetooth: RFCOMM socket layer initialized
[   24.443294] Bluetooth: RFCOMM ver 1.11
[   24.445408] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   24.445413] Bluetooth: BNEP filters: protocol multicast
[   24.445424] Bluetooth: BNEP socket layer initialized
[   24.455796] type=1400 audit(1400352971.746:9): apparmor="STATUS" operation="profile_load" parent=688 profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=698 comm="apparmor_parser"
[   24.455806] type=1400 audit(1400352971.746:10): apparmor="STATUS" operation="profile_load" parent=688 profile="unconfined" name="/usr/sbin/cupsd" pid=698 comm="apparmor_parser"
[   24.456237] type=1400 audit(1400352971.746:11): apparmor="STATUS" operation="profile_replace" parent=688 profile="unconfined" name="/usr/sbin/cupsd" pid=698 comm="apparmor_parser"
[   24.916213] init: cups main process (707) killed by HUP signal
[   24.916225] init: cups main process ended, respawning
[   26.129738] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   26.130634] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   26.135664] atl1c 0000:07:00.0: irq 48 for MSI/MSI-X
[   26.151129] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   26.152435] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   27.124270] init: samba-ad-dc main process (1077) terminated with status 1
[   27.348150] wlan0: authenticate with ac:f1:df:9d:50:b9
[   27.364912] wlan0: send auth to ac:f1:df:9d:50:b9 (try 1/3)
[   27.366920] wlan0: authenticated
[   27.367918] init: udev-fallback-graphics main process (1096) terminated with status 1
[   27.371302] wlan0: associate with ac:f1:df:9d:50:b9 (try 1/3)
[   27.375820] wlan0: RX AssocResp from ac:f1:df:9d:50:b9 (capab=0x401 status=0 aid=1)
[   27.375881] wlan0: associated
[   27.375913] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   27.589371] init: plymouth-upstart-bridge main process ended, respawning
[   27.940360] nvidia 0000:01:00.0: irq 49 for MSI/MSI-X
[   31.548228] init: plymouth-stop pre-start process (1446) terminated with status 1
[   34.755275] hda-codec: out of range cmd 0:5:707:ffffffbf
[   54.645759] audit_printk_skb: 183 callbacks suppressed
[   54.645763] type=1400 audit(1400353001.926:73): apparmor="STATUS" operation="profile_replace" parent=2456 profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=2460 comm="apparmor_parser"
[   54.645773] type=1400 audit(1400353001.926:74): apparmor="STATUS" operation="profile_replace" parent=2456 profile="unconfined" name="/usr/sbin/cupsd" pid=2460 comm="apparmor_parser"
[   54.646242] type=1400 audit(1400353001.930:75): apparmor="STATUS" operation="profile_replace" parent=2456 profile="unconfined" name="/usr/sbin/cupsd" pid=2460 comm="apparmor_parser"
[  184.027280] usb 2-1.2: new low-speed USB device number 3 using ehci-pci
[  184.099323] usb 2-1.2: device descriptor read/64, error -32
[  184.275291] usb 2-1.2: device descriptor read/64, error -32
[  184.451381] usb 2-1.2: new low-speed USB device number 4 using ehci-pci
[  184.523287] usb 2-1.2: device descriptor read/64, error -32
[  184.699437] usb 2-1.2: device descriptor read/64, error -32
[  184.875308] usb 2-1.2: new low-speed USB device number 5 using ehci-pci
[  185.283197] usb 2-1.2: device not accepting address 5, error -32
[  185.355334] usb 2-1.2: new low-speed USB device number 6 using ehci-pci
[  185.763212] usb 2-1.2: device not accepting address 6, error -32
[  185.763454] hub 2-1:1.0: unable to enumerate USB device on port 2

```

here is my sudo lsusb -v:

```


Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         1 Single TT
  bMaxPacketSize0        64
  idVendor           0x8087 Intel Corp.
  idProduct          0x0020 Integrated Rate Matching Hub
  bcdDevice            0.00
  iManufacturer           0 
  iProduct                0 
  iSerial                 0 
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
        bInterval              12
Hub Descriptor:
  bLength              11
  bDescriptorType      41
  nNbrPorts             8
  wHubCharacteristic 0x0089
    Per-port power switching
    Per-port overcurrent protection
    TT think time 8 FS bits
    Port indicators
  bPwrOn2PwrGood       50 * 2 milli seconds
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
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0001
  Self Powered


Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
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
  bcdDevice            3.11
  iManufacturer           3 Linux 3.11.0-18-generic ehci_hcd
  iProduct                2 EHCI Host Controller
  iSerial                 1 0000:00:1d.0
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
  bLength               9
  bDescriptorType      41
  nNbrPorts             2
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood       10 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0507 highspeed power suspend enable connect
   Port 2: 0000.0100 power
Device Status:     0x0001
  Self Powered


Bus 001 Device 003: ID 04f2:b071 Chicony Electronics Co., Ltd 2.0M UVC Webcam / CNF7129
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          239 Miscellaneous Device
  bDeviceSubClass         2 ?
  bDeviceProtocol         1 Interface Association
  bMaxPacketSize0        64
  idVendor           0x04f2 Chicony Electronics Co., Ltd
  idProduct          0xb071 2.0M UVC Webcam / CNF7129
  bcdDevice           15.15
  iManufacturer           2 Chicony Electronics Co., Ltd.
  iProduct                1 CNF7129
  iSerial                 3 SN0001
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          592
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Association:
      bLength                 8
      bDescriptorType        11
      bFirstInterface         0
      bInterfaceCount         2
      bFunctionClass         14 Video
      bFunctionSubClass       3 Video Interface Collection
      bFunctionProtocol       0 
      iFunction               5 USB2.0 1.3M UVC WebCam
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      1 Video Control
      bInterfaceProtocol      0 
      iInterface              5 USB2.0 1.3M UVC WebCam
      VideoControl Interface Descriptor:
        bLength                13
        bDescriptorType        36
        bDescriptorSubtype      1 (HEADER)
        bcdUVC               1.00
        wTotalLength          104
        dwClockFrequency       15.000000MHz
        bInCollection           1
        baInterfaceNr( 0)       1
      VideoControl Interface Descriptor:
        bLength                 9
        bDescriptorType        36
        bDescriptorSubtype      3 (OUTPUT_TERMINAL)
        bTerminalID             2
        wTerminalType      0x0101 USB Streaming
        bAssocTerminal          0
        bSourceID               5
        iTerminal               0 
      VideoControl Interface Descriptor:
        bLength                26
        bDescriptorType        36
        bDescriptorSubtype      6 (EXTENSION_UNIT)
        bUnitID                 4
        guidExtensionCode         {7033f028-1163-2e4a-ba2c-6890eb334016}
        bNumControl             8
        bNrPins                 1
        baSourceID( 0)          3
        bControlSize            1
        bmControls( 0)       0x0f
        iExtension              0 
      VideoControl Interface Descriptor:
        bLength                26
        bDescriptorType        36
        bDescriptorSubtype      6 (EXTENSION_UNIT)
        bUnitID                 5
        guidExtensionCode         {3fae1228-d7bc-114e-a357-6f1edef7d61d}
        bNumControl             8
        bNrPins                 1
        baSourceID( 0)          4
        bControlSize            1
        bmControls( 0)       0xff
        iExtension              0 
      VideoControl Interface Descriptor:
        bLength                18
        bDescriptorType        36
        bDescriptorSubtype      2 (INPUT_TERMINAL)
        bTerminalID             1
        wTerminalType      0x0201 Camera Sensor
        bAssocTerminal          0
        iTerminal               0 
        wObjectiveFocalLengthMin      0
        wObjectiveFocalLengthMax      0
        wOcularFocalLength            0
        bControlSize                  3
        bmControls           0x00000000
      VideoControl Interface Descriptor:
        bLength                12
        bDescriptorType        36
        bDescriptorSubtype      5 (PROCESSING_UNIT)
      Warning: Descriptor too short
        bUnitID                 3
        bSourceID               1
        wMaxMultiplier          0
        bControlSize            3
        bmControls     0x0000377f
          Brightness
          Contrast
          Hue
          Saturation
          Sharpness
          Gamma
          White Balance Temperature
          Backlight Compensation
          Gain
          Power Line Frequency
          White Balance Temperature, Auto
          White Balance Component, Auto
        iProcessing             0 
        bmVideoStandards     0x41
          None
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               6
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      VideoStreaming Interface Descriptor:
        bLength                            14
        bDescriptorType                    36
        bDescriptorSubtype                  1 (INPUT_HEADER)
        bNumFormats                         1
        wTotalLength                      345
        bEndPointAddress                  129
        bmInfo                              0
        bTerminalLink                       2
        bStillCaptureMethod                 0
        bTriggerSupport                     1
        bTriggerUsage                       0
        bControlSize                        1
        bmaControls( 0)                    27
      VideoStreaming Interface Descriptor:
        bLength                            27
        bDescriptorType                    36
        bDescriptorSubtype                  4 (FORMAT_UNCOMPRESSED)
        bFormatIndex                        1
        bNumFrameDescriptors                7
        guidFormat                            {59555932-0000-1000-8000-00aa00389b71}
        bBitsPerPixel                      16
        bDefaultFrameIndex                  1
        bAspectRatioX                       0
        bAspectRatioY                       0
        bmInterlaceFlags                 0x00
          Interlaced stream or variable: No
          Fields per frame: 2 fields
          Field 1 first: No
          Field pattern: Field 1 only
          bCopyProtect                      0
      VideoStreaming Interface Descriptor:
        bLength                            46
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         1
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            640
        wHeight                           480
        dwMinBitRate                  3072000
        dwMaxBitRate                 18432000
        dwMaxVideoFrameBufferSize      614400
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  5
        dwFrameInterval( 0)            333333
        dwFrameInterval( 1)            500000
        dwFrameInterval( 2)            666666
        dwFrameInterval( 3)           1000000
        dwFrameInterval( 4)           2000000
      VideoStreaming Interface Descriptor:
        bLength                            46
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         2
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            352
        wHeight                           288
        dwMinBitRate                  1013760
        dwMaxBitRate                  6082560
        dwMaxVideoFrameBufferSize      202752
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  5
        dwFrameInterval( 0)            333333
        dwFrameInterval( 1)            500000
        dwFrameInterval( 2)            666666
        dwFrameInterval( 3)           1000000
        dwFrameInterval( 4)           2000000
      VideoStreaming Interface Descriptor:
        bLength                            46
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         3
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            320
        wHeight                           240
        dwMinBitRate                   768000
        dwMaxBitRate                  4608000
        dwMaxVideoFrameBufferSize      153600
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  5
        dwFrameInterval( 0)            333333
        dwFrameInterval( 1)            500000
        dwFrameInterval( 2)            666666
        dwFrameInterval( 3)           1000000
        dwFrameInterval( 4)           2000000
      VideoStreaming Interface Descriptor:
        bLength                            46
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         4
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            176
        wHeight                           144
        dwMinBitRate                   253440
        dwMaxBitRate                  1520640
        dwMaxVideoFrameBufferSize       50688
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  5
        dwFrameInterval( 0)            333333
        dwFrameInterval( 1)            500000
        dwFrameInterval( 2)            666666
        dwFrameInterval( 3)           1000000
        dwFrameInterval( 4)           2000000
      VideoStreaming Interface Descriptor:
        bLength                            46
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         5
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            160
        wHeight                           120
        dwMinBitRate                   192000
        dwMaxBitRate                  1152000
        dwMaxVideoFrameBufferSize       38400
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  5
        dwFrameInterval( 0)            333333
        dwFrameInterval( 1)            500000
        dwFrameInterval( 2)            666666
        dwFrameInterval( 3)           1000000
        dwFrameInterval( 4)           2000000
      VideoStreaming Interface Descriptor:
        bLength                            34
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         6
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                           1280
        wHeight                           800
        dwMinBitRate                 10240000
        dwMaxBitRate                 14336000
        dwMaxVideoFrameBufferSize     2048000
        dwDefaultFrameInterval        1428571
        bFrameIntervalType                  2
        dwFrameInterval( 0)           1428571
        dwFrameInterval( 1)           2000000
      VideoStreaming Interface Descriptor:
        bLength                            34
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         7
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                           1280
        wHeight                          1024
        dwMinBitRate                 13107200
        dwMaxBitRate                 18350080
        dwMaxVideoFrameBufferSize     2621440
        dwDefaultFrameInterval        1428571
        bFrameIntervalType                  2
        dwFrameInterval( 0)           1428571
        dwFrameInterval( 1)           2000000
      VideoStreaming Interface Descriptor:
        bLength                             6
        bDescriptorType                    36
        bDescriptorSubtype                 13 (COLORFORMAT)
        bColorPrimaries                     1 (BT.709,sRGB)
        bTransferCharacteristics            1 (BT.709)
        bMatrixCoefficients                 4 (SMPTE 170M (BT.601))
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       1
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x0080  1x 128 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       2
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x0100  1x 256 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       3
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x0320  1x 800 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       4
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x0b20  2x 800 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       5
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x1320  3x 800 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       6
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x1400  3x 1024 bytes
        bInterval               1
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass          239 Miscellaneous Device
  bDeviceSubClass         2 ?
  bDeviceProtocol         1 Interface Association
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0002
  (Bus Powered)
  Remote Wakeup Enabled


Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         1 Single TT
  bMaxPacketSize0        64
  idVendor           0x8087 Intel Corp.
  idProduct          0x0020 Integrated Rate Matching Hub
  bcdDevice            0.00
  iManufacturer           0 
  iProduct                0 
  iSerial                 0 
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
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval              12
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             6
  wHubCharacteristic 0x0089
    Per-port power switching
    Per-port overcurrent protection
    TT think time 8 FS bits
    Port indicators
  bPwrOn2PwrGood       50 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
   Port 4: 0000.0100 power
   Port 5: 0000.0100 power
   Port 6: 0000.0503 highspeed power enable connect
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0001
  Self Powered


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
  bcdDevice            3.11
  iManufacturer           3 Linux 3.11.0-18-generic ehci_hcd
  iProduct                2 EHCI Host Controller
  iSerial                 1 0000:00:1a.0
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
  bLength               9
  bDescriptorType      41
  nNbrPorts             2
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood       10 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0503 highspeed power enable connect
   Port 2: 0000.0100 power
Device Status:     0x0001
  Self Powered

```

---

