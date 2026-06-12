---
title: "Ubuntu Server 14.04 crash on resume/suspend"
date: 2014-07-10
forum: General Help
---

### Post by rikki2 on 2014-07-10
I'm experiencing an intermittent problem with suspend/resume using powernap on ubuntu 14.04 server with XFCE and xbmc. Seemingly randomly the system will not resume from suspend and requires a hard reboot. This causes the RAID arrays to rebuild each time. It seems like the system crashes on suspend since when I enter the room the PC is in, it is usually powered up rather than in suspend state. I have WOL configured, but I only send magic packets manually so there won't have been any requests to wake the machine. Plus the top line of the susres crash states that the error was from previous suspend.

The system is an [MSI j1900l]("http://www.msi.com/product/mb/J1900I.html#hero-overview") although I've had this problem before using an AMD Athlon X2 CPU on a different board. Two 2TB HDs are setup with RAID/LVM where /boot is on it's own RAID1, /root in LVM on RAID0 and /home on LVM in RAID1. Kernel is 3.13.0-30-generic.

I can't reproduce this manually- when I use pm-suspend or suspend within xbmc all works well. It's only when left unattended for a few hours or overnight that this problem manifests. I have an rdiff-backup that runs nightly via ssh on my work PC which didn't run on this occasion (there was no new data or this PC had already crashed).

I've only ever had ubuntu 14.04 on this machine and the problem has persisted ever since I set up powernap. Sometimes it works fine, sometimes it doesn't.

I've exhausted my google-fu and would appreciate any insights the ubuntu forums community may have. I've tried to include some useful log files/ info below. Please let me know if I've missed anything out and I'll post it.



**dmesg after reboot from crash:**
```
[    0.000000] Initializing cgroup subsys cpuset[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.13.0-30-generic (buildd@kissel) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #55-Ubuntu SMP Fri Jul 4 21:40:53 UTC 2014 (Ubuntu 3.13.0-30.55-generic 3.13.11.2)
[    0.000000] Command line: BOOT_IMAGE=/vmlinuz-3.13.0-30-generic root=/dev/mapper/stripe-root ro quiet splash nomdmonddf nomdmonisw nomdmonddf nomdmonisw
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000008d7ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000008d800-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000001fffffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000020000000-0x00000000200fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000020100000-0x000000009d6d3fff] usable
[    0.000000] BIOS-e820: [mem 0x000000009d6d4000-0x000000009d703fff] reserved
[    0.000000] BIOS-e820: [mem 0x000000009d704000-0x000000009d713fff] ACPI data
[    0.000000] BIOS-e820: [mem 0x000000009d714000-0x000000009d858fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000009d859000-0x000000009db72fff] reserved
[    0.000000] BIOS-e820: [mem 0x000000009db73000-0x000000009db73fff] usable
[    0.000000] BIOS-e820: [mem 0x000000009db74000-0x000000009dbb5fff] reserved
[    0.000000] BIOS-e820: [mem 0x000000009dbb6000-0x000000009dd24fff] usable
[    0.000000] BIOS-e820: [mem 0x000000009dd25000-0x000000009dff9fff] reserved
[    0.000000] BIOS-e820: [mem 0x000000009dffa000-0x000000009dffffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000e00f8000-0x00000000e00f8fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed01000-0x00000000fed01fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffb00000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000013fffffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.8 present.
[    0.000000] DMI: MSI MS-7877/J1900I, BIOS V1.2 03/25/2014
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x140000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-E7FFF write-through
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FE0000000 write-back
[    0.000000]   2 base 09E000000 mask FFE000000 uncachable
[    0.000000]   3 base 100000000 mask FC0000000 write-back
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 512MB, type WB
[    0.000000] reg 2, base: 2528MB, range: 32MB, type UC
[    0.000000] reg 3, base: 4GB, range: 1GB, type WB
[    0.000000] total RAM covered: 3552M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K 	chunk_size: 64M 	num_reg: 4  	lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 512MB, type WB
[    0.000000] reg 2, base: 2528MB, range: 32MB, type UC
[    0.000000] reg 3, base: 4GB, range: 1GB, type WB
[    0.000000] e820: update [mem 0x9e000000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0x9e000 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000fd670-0x000fd67f] mapped at [ffff8800000fd670]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000087000] 87000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01fde000, 0x01fdefff] PGTABLE
[    0.000000] BRK [0x01fdf000, 0x01fdffff] PGTABLE
[    0.000000] BRK [0x01fe0000, 0x01fe0fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x13fe00000-0x13fffffff]
[    0.000000]  [mem 0x13fe00000-0x13fffffff] page 2M
[    0.000000] BRK [0x01fe1000, 0x01fe1fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x13c000000-0x13fdfffff]
[    0.000000]  [mem 0x13c000000-0x13fdfffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x100000000-0x13bffffff]
[    0.000000]  [mem 0x100000000-0x13bffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0x1fffffff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x1fffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x20100000-0x9d6d3fff]
[    0.000000]  [mem 0x20100000-0x201fffff] page 4k
[    0.000000]  [mem 0x20200000-0x9d5fffff] page 2M
[    0.000000]  [mem 0x9d600000-0x9d6d3fff] page 4k
[    0.000000] BRK [0x01fe2000, 0x01fe2fff] PGTABLE
[    0.000000] BRK [0x01fe3000, 0x01fe3fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x9db73000-0x9db73fff]
[    0.000000]  [mem 0x9db73000-0x9db73fff] page 4k
[    0.000000] init_memory_mapping: [mem 0x9dbb6000-0x9dd24fff]
[    0.000000]  [mem 0x9dbb6000-0x9dd24fff] page 4k
[    0.000000] init_memory_mapping: [mem 0x9dffa000-0x9dffffff]
[    0.000000]  [mem 0x9dffa000-0x9dffffff] page 4k
[    0.000000] RAMDISK: [mem 0x358e0000-0x36c67fff]
[    0.000000] ACPI: RSDP 00000000000f04a0 000024 (v02 ALASKA)
[    0.000000] ACPI: XSDT 000000009d70a078 000074 (v01 ALASKA   A M I  01072009 AMI  00010013)
[    0.000000] ACPI: FACP 000000009d712d10 00010C (v05 ALASKA   A M I  01072009 AMI  00010013)
[    0.000000] ACPI: DSDT 000000009d70a180 008B8D (v02 ALASKA   A M I  01072009 INTL 20120913)
[    0.000000] ACPI: FACS 000000009d858f80 000040
[    0.000000] ACPI: APIC 000000009d712e20 000084 (v03 ALASKA   A M I  01072009 AMI  00010013)
[    0.000000] ACPI: FPDT 000000009d712ea8 000044 (v01 ALASKA   A M I  01072009 AMI  00010013)
[    0.000000] ACPI: MCFG 000000009d712ef0 00003C (v01 ALASKA   A M I  01072009 MSFT 00000097)
[    0.000000] ACPI: LPIT 000000009d712f30 000104 (v01 ALASKA   A M I  00000003 VLV2 0100000D)
[    0.000000] ACPI: HPET 000000009d713038 000038 (v01 ALASKA   A M I  01072009 AMI. 00000005)
[    0.000000] ACPI: SSDT 000000009d713070 000763 (v01  PmRef    CpuPm 00003000 INTL 20061109)
[    0.000000] ACPI: SSDT 000000009d7137d8 000290 (v01  PmRef  Cpu0Tst 00003000 INTL 20061109)
[    0.000000] ACPI: SSDT 000000009d713a68 00017A (v01  PmRef    ApTst 00003000 INTL 20061109)
[    0.000000] ACPI: UEFI 000000009d713be8 000042 (v01 ALASKA   A M I  00000000      00000000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000013fffffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x13fffffff]
[    0.000000]   NODE_DATA [mem 0x13fff6000-0x13fffafff]
[    0.000000]  [ffffea0000000000-ffffea0004ffffff] PMD -> [ffff88013be00000-ffff88013f5fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x13fffffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0008cfff]
[    0.000000]   node   0: [mem 0x00100000-0x1fffffff]
[    0.000000]   node   0: [mem 0x20100000-0x9d6d3fff]
[    0.000000]   node   0: [mem 0x9db73000-0x9db73fff]
[    0.000000]   node   0: [mem 0x9dbb6000-0x9dd24fff]
[    0.000000]   node   0: [mem 0x9dffa000-0x9dffffff]
[    0.000000]   node   0: [mem 0x100000000-0x13fffffff]
[    0.000000] On node 0 totalpages: 906966
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3980 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 10014 pages used for memmap
[    0.000000]   DMA32 zone: 640842 pages, LIFO batch:31
[    0.000000]   Normal zone: 4096 pages used for memmap
[    0.000000]   Normal zone: 262144 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x0])
[    0.000000] ACPI: NMI not connected to LINT 1!
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x0])
[    0.000000] ACPI: NMI not connected to LINT 1!
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x0])
[    0.000000] ACPI: NMI not connected to LINT 1!
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] dfl dfl lint[0x0])
[    0.000000] ACPI: NMI not connected to LINT 1!
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-86
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] smpboot: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 103
[    0.000000] PM: Registered nosave memory: [mem 0x0008d000-0x0008dfff]
[    0.000000] PM: Registered nosave memory: [mem 0x0008e000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x20000000-0x200fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x9d6d4000-0x9d703fff]
[    0.000000] PM: Registered nosave memory: [mem 0x9d704000-0x9d713fff]
[    0.000000] PM: Registered nosave memory: [mem 0x9d714000-0x9d858fff]
[    0.000000] PM: Registered nosave memory: [mem 0x9d859000-0x9db72fff]
[    0.000000] PM: Registered nosave memory: [mem 0x9db74000-0x9dbb5fff]
[    0.000000] PM: Registered nosave memory: [mem 0x9dd25000-0x9dff9fff]
[    0.000000] PM: Registered nosave memory: [mem 0x9e000000-0x9effffff]
[    0.000000] PM: Registered nosave memory: [mem 0x9f000000-0xbeffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xbf000000-0xe00f7fff]
[    0.000000] PM: Registered nosave memory: [mem 0xe00f8000-0xe00f8fff]
[    0.000000] PM: Registered nosave memory: [mem 0xe00f9000-0xfed00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed01000-0xfed01fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed02000-0xffafffff]
[    0.000000] PM: Registered nosave memory: [mem 0xffb00000-0xffffffff]
[    0.000000] e820: [mem 0xbf000000-0xe00f7fff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 29 pages/cpu @ffff88013fc00000 s86336 r8192 d24256 u524288
[    0.000000] pcpu-alloc: s86336 r8192 d24256 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 892771
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-3.13.0-30-generic root=/dev/mapper/stripe-root ro quiet splash nomdmonddf nomdmonisw nomdmonddf nomdmonisw
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 3467356K/3627864K available (7356K kernel code, 1142K rwdata, 3396K rodata, 1332K init, 1440K bss, 160508K reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
[    0.000000] 	Offload RCU callbacks from all CPUs
[    0.000000] 	Offload RCU callbacks from CPUs: 0-3.
[    0.000000] NR_IRQS:16640 nr_irqs:1024 16
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 14680064 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.004000] tsc: Detected 2000.081 MHz processor
[    0.000004] Calibrating delay loop (skipped), value calculated using timer frequency.. 4000.16 BogoMIPS (lpj=8000324)
[    0.000010] pid_max: default: 32768 minimum: 301
[    0.000054] Security Framework initialized
[    0.000081] AppArmor: AppArmor initialized
[    0.000084] Yama: becoming mindful.
[    0.000650] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.002542] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.003383] Mount-cache hash table entries: 8192 (order: 4, 65536 bytes)
[    0.003400] Mountpoint-cache hash table entries: 8192 (order: 4, 65536 bytes)
[    0.003743] Initializing cgroup subsys memory
[    0.003756] Initializing cgroup subsys devices
[    0.003760] Initializing cgroup subsys freezer
[    0.003764] Initializing cgroup subsys blkio
[    0.003767] Initializing cgroup subsys perf_event
[    0.003772] Initializing cgroup subsys hugetlb
[    0.003801] CPU: Physical Processor ID: 0
[    0.003804] CPU: Processor Core ID: 0
[    0.003810] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.003810] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.008588] mce: CPU supports 6 MCE banks
[    0.008600] CPU0: Thermal monitoring enabled (TM1)
[    0.008609] Last level iTLB entries: 4KB 0, 2MB 0, 4MB 0
[    0.008609] Last level dTLB entries: 4KB 128, 2MB 0, 4MB 0
[    0.008609] tlb_flushall_shift: 6
[    0.008751] Freeing SMP alternatives memory: 32K (ffffffff81e6c000 - ffffffff81e74000)
[    0.010075] ACPI: Core revision 20131115
[    0.020911] ACPI: All ACPI Tables successfully acquired
[    0.021046] ftrace: allocating 28465 entries in 112 pages
[    0.037686] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=0 pin2=0
[    0.077378] smpboot: CPU0: Intel(R) Celeron(R) CPU  J1900  @ 1.99GHz (fam: 06, model: 37, stepping: 03)
[    0.077391] TSC deadline timer enabled
[    0.079390] Performance Events: PEBS fmt2+, 8-deep LBR, Silvermont events, full-width counters, Intel PMU driver.
[    0.079402] ... version:                3
[    0.079405] ... bit width:              40
[    0.079407] ... generic registers:      2
[    0.079410] ... value mask:             000000ffffffffff
[    0.079412] ... max period:             000000ffffffffff
[    0.079414] ... fixed-purpose events:   3
[    0.079416] ... event mask:             0000000700000003
[    0.082552] x86: Booting SMP configuration:
[    0.100418] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.082558] .... node  #0, CPUs:      #1 #2 #3
[    0.136507] x86: Booted up 1 node, 4 CPUs
[    0.136512] smpboot: Total of 4 processors activated (16000.64 BogoMIPS)
[    0.137519] devtmpfs: initialized
[    0.144378] EVM: security.selinux
[    0.144381] EVM: security.SMACK64
[    0.144384] EVM: security.ima
[    0.144386] EVM: security.capability
[    0.144500] PM: Registering ACPI NVS region [mem 0x9d714000-0x9d858fff] (1331200 bytes)
[    0.146306] pinctrl core: initialized pinctrl subsystem
[    0.146433] regulator-dummy: no parameters
[    0.146472] RTC time:  7:16:34, date: 07/10/14
[    0.146559] NET: Registered protocol family 16
[    0.146799] cpuidle: using governor ladder
[    0.146803] cpuidle: using governor menu
[    0.146917] ACPI: bus type PCI registered
[    0.146921] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.147020] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.147026] PCI: not using MMCONFIG
[    0.147029] PCI: Using configuration type 1 for base access
[    0.148979] bio: create slab <bio-0> at 0
[    0.149318] ACPI: Added _OSI(Module Device)
[    0.149323] ACPI: Added _OSI(Processor Device)
[    0.149326] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.149328] ACPI: Added _OSI(Processor Aggregator Device)
[    0.163374] ACPI: SSDT 000000009d6fcc18 0003D7 (v01  PmRef  Cpu0Ist 00003000 INTL 20061109)
[    0.164125] ACPI: Dynamic OEM Table Load:
[    0.164130] ACPI: SSDT           (null) 0003D7 (v01  PmRef  Cpu0Ist 00003000 INTL 20061109)
[    0.164333] ACPI: SSDT 000000009d6fb918 000433 (v01  PmRef  Cpu0Cst 00003001 INTL 20061109)
[    0.165070] ACPI: Dynamic OEM Table Load:
[    0.165075] ACPI: SSDT           (null) 000433 (v01  PmRef  Cpu0Cst 00003001 INTL 20061109)
[    0.170996] ACPI: SSDT 000000009d6fde18 00015F (v01  PmRef    ApIst 00003000 INTL 20061109)
[    0.171775] ACPI: Dynamic OEM Table Load:
[    0.171780] ACPI: SSDT           (null) 00015F (v01  PmRef    ApIst 00003000 INTL 20061109)
[    0.174689] ACPI: SSDT 000000009d6fef18 00008D (v01  PmRef    ApCst 00003000 INTL 20061109)
[    0.175431] ACPI: Dynamic OEM Table Load:
[    0.175436] ACPI: SSDT           (null) 00008D (v01  PmRef    ApCst 00003000 INTL 20061109)
[    0.179810] ACPI: Interpreter enabled
[    0.179822] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20131115/hwxface-580)
[    0.179832] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)
[    0.179860] ACPI: (supports S0 S3 S4 S5)
[    0.179863] ACPI: Using IOAPIC for interrupt routing
[    0.179907] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.180787] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.208812] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.209141] ACPI: No dock devices found.
[    0.828278] ACPI: Power Resource [USBC] (on)
[    0.828681] ACPI: Power Resource [FN00] (off)
[    0.829748] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.829759] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.830033] \_SB_.PCI0:_OSC invalid UUID
[    0.830037] _OSC request data:1 1f 0 
[    0.830046] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM
[    0.831001] PCI host bridge to bus 0000:00
[    0.831008] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.831013] pci_bus 0000:00: root bus resource [io  0x0000-0x006f]
[    0.831017] pci_bus 0000:00: root bus resource [io  0x0078-0x0cf7]
[    0.831021] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.831025] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.831029] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000dffff]
[    0.831033] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000fffff]
[    0.831037] pci_bus 0000:00: root bus resource [mem 0xc0000000-0xd0716ffe]
[    0.831049] pci 0000:00:00.0: [8086:0f00] type 00 class 0x060000
[    0.831235] pci 0000:00:02.0: [8086:0f31] type 00 class 0x030000
[    0.831253] pci 0000:00:02.0: reg 0x10: [mem 0xd0000000-0xd03fffff]
[    0.831266] pci 0000:00:02.0: reg 0x18: [mem 0xc0000000-0xcfffffff pref]
[    0.831279] pci 0000:00:02.0: reg 0x20: [io  0xf080-0xf087]
[    0.831475] pci 0000:00:13.0: [8086:0f23] type 00 class 0x010601
[    0.831498] pci 0000:00:13.0: reg 0x10: [io  0xf070-0xf077]
[    0.831510] pci 0000:00:13.0: reg 0x14: [io  0xf060-0xf063]
[    0.831521] pci 0000:00:13.0: reg 0x18: [io  0xf050-0xf057]
[    0.831532] pci 0000:00:13.0: reg 0x1c: [io  0xf040-0xf043]
[    0.831544] pci 0000:00:13.0: reg 0x20: [io  0xf020-0xf03f]
[    0.831555] pci 0000:00:13.0: reg 0x24: [mem 0xd0716000-0xd07167ff]
[    0.831605] pci 0000:00:13.0: PME# supported from D3hot
[    0.831765] pci 0000:00:14.0: [8086:0f35] type 00 class 0x0c0330
[    0.831788] pci 0000:00:14.0: reg 0x10: [mem 0xd0700000-0xd070ffff 64bit]
[    0.831851] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    0.831983] pci 0000:00:14.0: System wakeup disabled by ACPI
[    0.832052] pci 0000:00:1a.0: [8086:0f18] type 00 class 0x108000
[    0.832082] pci 0000:00:1a.0: reg 0x10: [mem 0xd0500000-0xd05fffff]
[    0.832097] pci 0000:00:1a.0: reg 0x14: [mem 0xd0400000-0xd04fffff]
[    0.832204] pci 0000:00:1a.0: PME# supported from D0 D3hot
[    0.832365] pci 0000:00:1b.0: [8086:0f04] type 00 class 0x040300
[    0.832391] pci 0000:00:1b.0: reg 0x10: [mem 0xd0710000-0xd0713fff 64bit]
[    0.832466] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.832620] pci 0000:00:1c.0: [8086:0f48] type 01 class 0x060400
[    0.832685] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.832840] pci 0000:00:1c.1: [8086:0f4a] type 01 class 0x060400
[    0.832904] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.833062] pci 0000:00:1c.2: [8086:0f4c] type 01 class 0x060400
[    0.833126] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.833282] pci 0000:00:1c.3: [8086:0f4e] type 01 class 0x060400
[    0.833346] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.833508] pci 0000:00:1f.0: [8086:0f1c] type 00 class 0x060100
[    0.833736] pci 0000:00:1f.3: [8086:0f12] type 00 class 0x0c0500
[    0.833775] pci 0000:00:1f.3: reg 0x10: [mem 0xd0714000-0xd071401f]
[    0.833849] pci 0000:00:1f.3: reg 0x20: [io  0xf000-0xf01f]
[    0.834177] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    0.834278] pci 0000:00:1c.1: PCI bridge to [bus 02]
[    0.834403] pci 0000:03:00.0: [10ec:8168] type 00 class 0x020000
[    0.834424] pci 0000:03:00.0: reg 0x10: [io  0xe000-0xe0ff]
[    0.834455] pci 0000:03:00.0: reg 0x18: [mem 0xd0604000-0xd0604fff 64bit]
[    0.834475] pci 0000:03:00.0: reg 0x20: [mem 0xd0600000-0xd0603fff 64bit pref]
[    0.834551] pci 0000:03:00.0: supports D1 D2
[    0.834555] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.834605] pci 0000:03:00.0: System wakeup disabled by ACPI
[    0.839002] pci 0000:00:1c.2: PCI bridge to [bus 03]
[    0.839009] pci 0000:00:1c.2:   bridge window [io  0xe000-0xefff]
[    0.839015] pci 0000:00:1c.2:   bridge window [mem 0xd0600000-0xd06fffff]
[    0.839113] pci 0000:00:1c.3: PCI bridge to [bus 04]
[    1.043643] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 *11 12 14 15)
[    1.043780] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 *4 5 6 10 11 12 14 15)
[    1.043911] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 10 *11 12 14 15)
[    1.044039] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 *10 11 12 14 15)
[    1.044168] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 10 11 12 14 15)
[    1.044296] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    1.044426] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 5 6 10 11 12 14 15)
[    1.044555] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *10 11 12 14 15)
[    1.045195] ACPI: Enabled 6 GPEs in block 00 to 3F
[    1.045212] ACPI: \_SB_.PCI0: notify handler is installed
[    1.045313] Found 1 acpi root devices
[    1.045549] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    1.045559] vgaarb: loaded
[    1.045562] vgaarb: bridge control possible 0000:00:02.0
[    1.045929] SCSI subsystem initialized
[    1.046032] libata version 3.00 loaded.
[    1.046070] ACPI: bus type USB registered
[    1.046103] usbcore: registered new interface driver usbfs
[    1.046124] usbcore: registered new interface driver hub
[    1.046176] usbcore: registered new device driver usb
[    1.046394] PCI: Using ACPI for IRQ routing
[    1.052392] PCI: pci_cache_line_size set to 64 bytes
[    1.052439] e820: reserve RAM buffer [mem 0x0008d800-0x0008ffff]
[    1.052443] e820: reserve RAM buffer [mem 0x9d6d4000-0x9fffffff]
[    1.052447] e820: reserve RAM buffer [mem 0x9db74000-0x9fffffff]
[    1.052450] e820: reserve RAM buffer [mem 0x9dd25000-0x9fffffff]
[    1.052453] e820: reserve RAM buffer [mem 0x9e000000-0x9fffffff]
[    1.052600] NetLabel: Initializing
[    1.052603] NetLabel:  domain hash size = 128
[    1.052605] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.052626] NetLabel:  unlabeled traffic allowed by default
[    1.052758] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    1.052766] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    1.054816] Switched to clocksource hpet
[    1.063346] AppArmor: AppArmor Filesystem Enabled
[    1.063399] pnp: PnP ACPI init
[    1.063423] ACPI: bus type PNP registered
[    1.063502] pnp 00:00: Plug and Play ACPI device, IDs PNP0b00 (active)
[    1.063615] pnp 00:01: Plug and Play ACPI device, IDs PNP0103 (active)
[    1.063805] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
[    1.063896] system 00:03: [io  0x0680-0x069f] has been reserved
[    1.063902] system 00:03: [io  0x0400-0x047f] has been reserved
[    1.063907] system 00:03: [io  0x0500-0x05fe] has been reserved
[    1.063911] system 00:03: [io  0x0600-0x061f] has been reserved
[    1.063917] system 00:03: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.064155] system 00:04: [io  0x0a00-0x0a0f] has been reserved
[    1.064161] system 00:04: [io  0x0a10-0x0a1f] has been reserved
[    1.064167] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.064485] pnp 00:05: Plug and Play ACPI device, IDs PNP0303 (active)
[    1.064581] pnp 00:06: Plug and Play ACPI device, IDs PNP0f13 (active)
[    1.267255] system 00:07: [mem 0xe0000000-0xefffffff] could not be reserved
[    1.267261] system 00:07: [mem 0xfed01000-0xfed01fff] has been reserved
[    1.267270] system 00:07: [mem 0xfed03000-0xfed03fff] has been reserved
[    1.267274] system 00:07: [mem 0xfed04000-0xfed04fff] has been reserved
[    1.267279] system 00:07: [mem 0xfed0c000-0xfed0ffff] has been reserved
[    1.267283] system 00:07: [mem 0xfed08000-0xfed08fff] has been reserved
[    1.267288] system 00:07: [mem 0xfed1c000-0xfed1cfff] has been reserved
[    1.267292] system 00:07: [mem 0xfee00000-0xfeefffff] has been reserved
[    1.267297] system 00:07: [mem 0xfef00000-0xfeffffff] has been reserved
[    1.267303] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.267694] pnp: PnP ACPI: found 8 devices
[    1.267698] ACPI: bus type PNP unregistered
[    1.276144] pci 0000:00:1c.0: bridge window [io  0x1000-0x0fff] to [bus 01] add_size 1000
[    1.276152] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 01] add_size 200000
[    1.276158] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff] to [bus 01] add_size 200000
[    1.276168] pci 0000:00:1c.1: bridge window [io  0x1000-0x0fff] to [bus 02] add_size 1000
[    1.276173] pci 0000:00:1c.1: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 02] add_size 200000
[    1.276178] pci 0000:00:1c.1: bridge window [mem 0x00100000-0x000fffff] to [bus 02] add_size 200000
[    1.276189] pci 0000:00:1c.2: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 03] add_size 200000
[    1.276198] pci 0000:00:1c.3: bridge window [io  0x1000-0x0fff] to [bus 04] add_size 1000
[    1.276203] pci 0000:00:1c.3: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 04] add_size 200000
[    1.276208] pci 0000:00:1c.3: bridge window [mem 0x00100000-0x000fffff] to [bus 04] add_size 200000
[    1.276224] pci 0000:00:1c.0: res[14]=[mem 0x00100000-0x000fffff] get_res_add_size add_size 200000
[    1.276229] pci 0000:00:1c.0: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    1.276233] pci 0000:00:1c.1: res[14]=[mem 0x00100000-0x000fffff] get_res_add_size add_size 200000
[    1.276237] pci 0000:00:1c.1: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    1.276242] pci 0000:00:1c.2: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    1.276246] pci 0000:00:1c.3: res[14]=[mem 0x00100000-0x000fffff] get_res_add_size add_size 200000
[    1.276251] pci 0000:00:1c.3: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    1.276255] pci 0000:00:1c.0: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    1.276259] pci 0000:00:1c.1: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    1.276263] pci 0000:00:1c.3: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    1.276272] pci 0000:00:1c.0: BAR 14: can't assign mem (size 0x200000)
[    1.276278] pci 0000:00:1c.0: BAR 15: can't assign mem pref (size 0x200000)
[    1.276284] pci 0000:00:1c.1: BAR 14: can't assign mem (size 0x200000)
[    1.276289] pci 0000:00:1c.1: BAR 15: can't assign mem pref (size 0x200000)
[    1.276295] pci 0000:00:1c.2: BAR 15: can't assign mem pref (size 0x200000)
[    1.276300] pci 0000:00:1c.3: BAR 14: can't assign mem (size 0x200000)
[    1.276306] pci 0000:00:1c.3: BAR 15: can't assign mem pref (size 0x200000)
[    1.276312] pci 0000:00:1c.0: BAR 13: assigned [io  0x1000-0x1fff]
[    1.276317] pci 0000:00:1c.1: BAR 13: assigned [io  0x2000-0x2fff]
[    1.276323] pci 0000:00:1c.3: BAR 13: assigned [io  0x3000-0x3fff]
[    1.276331] pci 0000:00:1c.3: BAR 14: can't assign mem (size 0x200000)
[    1.276336] pci 0000:00:1c.3: BAR 15: can't assign mem pref (size 0x200000)
[    1.276342] pci 0000:00:1c.2: BAR 15: can't assign mem pref (size 0x200000)
[    1.276348] pci 0000:00:1c.1: BAR 14: can't assign mem (size 0x200000)
[    1.276353] pci 0000:00:1c.1: BAR 15: can't assign mem pref (size 0x200000)
[    1.276358] pci 0000:00:1c.0: BAR 14: can't assign mem (size 0x200000)
[    1.276364] pci 0000:00:1c.0: BAR 15: can't assign mem pref (size 0x200000)
[    1.276369] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    1.276374] pci 0000:00:1c.0:   bridge window [io  0x1000-0x1fff]
[    1.276386] pci 0000:00:1c.1: PCI bridge to [bus 02]
[    1.276390] pci 0000:00:1c.1:   bridge window [io  0x2000-0x2fff]
[    1.276402] pci 0000:00:1c.2: PCI bridge to [bus 03]
[    1.276406] pci 0000:00:1c.2:   bridge window [io  0xe000-0xefff]
[    1.276412] pci 0000:00:1c.2:   bridge window [mem 0xd0600000-0xd06fffff]
[    1.276421] pci 0000:00:1c.3: PCI bridge to [bus 04]
[    1.276425] pci 0000:00:1c.3:   bridge window [io  0x3000-0x3fff]
[    1.276437] pci_bus 0000:00: resource 4 [io  0x0000-0x006f]
[    1.276441] pci_bus 0000:00: resource 5 [io  0x0078-0x0cf7]
[    1.276445] pci_bus 0000:00: resource 6 [io  0x0d00-0xffff]
[    1.276449] pci_bus 0000:00: resource 7 [mem 0x000a0000-0x000bffff]
[    1.276452] pci_bus 0000:00: resource 8 [mem 0x000c0000-0x000dffff]
[    1.276456] pci_bus 0000:00: resource 9 [mem 0x000e0000-0x000fffff]
[    1.276460] pci_bus 0000:00: resource 10 [mem 0xc0000000-0xd0716ffe]
[    1.276464] pci_bus 0000:01: resource 0 [io  0x1000-0x1fff]
[    1.276468] pci_bus 0000:02: resource 0 [io  0x2000-0x2fff]
[    1.276472] pci_bus 0000:03: resource 0 [io  0xe000-0xefff]
[    1.276476] pci_bus 0000:03: resource 1 [mem 0xd0600000-0xd06fffff]
[    1.276480] pci_bus 0000:04: resource 0 [io  0x3000-0x3fff]
[    1.276534] NET: Registered protocol family 2
[    1.276823] TCP established hash table entries: 32768 (order: 6, 262144 bytes)
[    1.276977] TCP bind hash table entries: 32768 (order: 7, 524288 bytes)
[    1.277136] TCP: Hash tables configured (established 32768 bind 32768)
[    1.277184] TCP: reno registered
[    1.277204] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    1.277247] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    1.277391] NET: Registered protocol family 1
[    1.277416] pci 0000:00:02.0: Boot video device
[    1.277734] PCI: CLS 64 bytes, default 64
[    1.277857] Trying to unpack rootfs image as initramfs...
[    1.799278] Freeing initrd memory: 20000K (ffff8800358e0000 - ffff880036c68000)
[    1.799287] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    1.799291] software IO TLB [mem 0x996d4000-0x9d6d4000] (64MB) mapped at [ffff8800996d4000-ffff88009d6d3fff]
[    1.799679] microcode: CPU0 sig=0x30673, pf=0x4, revision=0x320
[    1.799691] microcode: CPU1 sig=0x30673, pf=0x4, revision=0x320
[    1.799700] microcode: CPU2 sig=0x30673, pf=0x4, revision=0x320
[    1.799711] microcode: CPU3 sig=0x30673, pf=0x4, revision=0x320
[    1.799803] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.799807] Scanning for low memory corruption every 60 seconds
[    1.800297] Initialise system trusted keyring
[    1.800374] audit: initializing netlink socket (disabled)
[    1.800391] type=2000 audit(1404976595.796:1): initialized
[    1.843257] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.845461] zbud: loaded
[    1.845686] VFS: Disk quotas dquot_6.5.2
[    1.845766] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.846649] fuse init (API version 7.22)
[    1.846801] msgmni has been set to 6811
[    1.846909] Key type big_key registered
[    1.847803] Key type asymmetric registered
[    1.847808] Asymmetric key parser 'x509' registered
[    1.847866] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    1.847939] io scheduler noop registered
[    1.847943] io scheduler deadline registered (default)
[    1.847990] io scheduler cfq registered
[    1.848738] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.848765] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.848844] efifb: probing for efifb
[    1.848852] efifb: framebuffer at 0xa0000, mapped to 0xffff8800000a0000, using 64k, total 64k
[    1.848855] efifb: mode is 640x480x1, linelength=80, pages=1
[    1.848857] efifb: scrolling: redraw
[    1.848861] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    1.851546] Console: switching to colour frame buffer device 80x30
[    1.854099] fb0: EFI VGA frame buffer device
[    1.854121] intel_idle: does not run on family 6 model 55
[    1.854133] ipmi message handler version 39.2
[    1.854252] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    1.854261] ACPI: Power Button [PWRB]
[    1.854325] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    1.854331] ACPI: Sleep Button [SLPB]
[    1.854393] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    1.854398] ACPI: Power Button [PWRF]
[    1.854504] ACPI: Fan [FAN0] (off)
[    1.856805] Monitor-Mwait will be used to enter C-1 state
[    1.859454] thermal LNXTHERM:00: registered as thermal_zone0
[    1.859460] ACPI: Thermal Zone [TZ01] (27 C)
[    1.859497] GHES: HEST is not enabled!
[    1.859657] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.862278] Linux agpgart interface v0.103
[    1.864934] brd: module loaded
[    1.866334] loop: module loaded
[    1.867053] libphy: Fixed MDIO Bus: probed
[    1.867224] tun: Universal TUN/TAP device driver, 1.6
[    1.867228] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.867313] PPP generic driver version 2.4.2
[    1.867385] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.867394] ehci-pci: EHCI PCI platform driver
[    1.867417] ehci-platform: EHCI generic platform driver
[    1.867430] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.867433] ohci-pci: OHCI PCI platform driver
[    1.867447] ohci-platform: OHCI generic platform driver
[    1.867459] uhci_hcd: USB Universal Host Controller Interface driver
[    1.867668] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    1.867679] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 1
[    1.868077] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    1.868112] xhci_hcd 0000:00:14.0: irq 103 for MSI/MSI-X
[    1.868242] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.868247] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.868251] usb usb1: Product: xHCI Host Controller
[    1.868254] usb usb1: Manufacturer: Linux 3.13.0-30-generic xhci_hcd
[    1.868258] usb usb1: SerialNumber: 0000:00:14.0
[    1.868454] hub 1-0:1.0: USB hub found
[    1.868474] hub 1-0:1.0: 6 ports detected
[    1.869247] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    1.869255] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 2
[    1.869341] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003
[    1.869346] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.869349] usb usb2: Product: xHCI Host Controller
[    1.869353] usb usb2: Manufacturer: Linux 3.13.0-30-generic xhci_hcd
[    1.869356] usb usb2: SerialNumber: 0000:00:14.0
[    1.869538] hub 2-0:1.0: USB hub found
[    1.869556] hub 2-0:1.0: 1 port detected
[    1.874961] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.875402] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.875412] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.875574] mousedev: PS/2 mouse device common for all mice
[    1.875906] rtc_cmos 00:00: RTC can wake from S4
[    1.876068] rtc_cmos 00:00: rtc core: registered rtc_cmos as rtc0
[    1.876101] rtc_cmos 00:00: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.876218] device-mapper: uevent: version 1.0.3
[    1.876332] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
[    1.876343] ledtrig-cpu: registered to indicate activity on CPUs
[    1.876512] TCP: cubic registered
[    1.876673] NET: Registered protocol family 10
[    1.876959] NET: Registered protocol family 17
[    1.876982] Key type dns_resolver registered
[    1.877487] Loading compiled-in X.509 certificates
[    1.879408] Loaded X.509 cert 'Magrathea: Glacier signing key: 094b30964ee6ceb2c567d252226b47712cfd8af6'
[    1.879430] registered taskstats version 1
[    1.884537] Key type trusted registered
[    1.889096] Key type encrypted registered
[    1.893629] AppArmor: AppArmor sha1 policy hashing enabled
[    1.893634] IMA: No TPM chip found, activating TPM-bypass!
[    1.893951] regulator-dummy: disabling
[    1.894038]   Magic number: 6:217:268
[    1.894158] rtc_cmos 00:00: setting system clock to 2014-07-10 07:16:36 UTC (1404976596)
[    1.895317] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.895320] EDD information not available.
[    1.895406] PM: Hibernation image not present or could not be loaded.
[    1.897155] Freeing unused kernel memory: 1332K (ffffffff81d1f000 - ffffffff81e6c000)
[    1.897161] Write protecting the kernel read-only data: 12288k
[    1.900951] Freeing unused kernel memory: 824K (ffff880001732000 - ffff880001800000)
[    1.903976] Freeing unused kernel memory: 700K (ffff880001b51000 - ffff880001c00000)
[    1.927456] systemd-udevd[114]: starting version 204
[    1.961864] md: linear personality registered for level -1
[    1.967154] md: multipath personality registered for level -4
[    1.972759] md: raid0 personality registered for level 0
[    1.973234] ahci 0000:00:13.0: version 3.0
[    1.973414] ahci 0000:00:13.0: irq 104 for MSI/MSI-X
[    1.976813] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.976830] r8169 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[    1.978544] md: raid1 personality registered for level 1
[    1.983238] r8169 0000:03:00.0: irq 105 for MSI/MSI-X
[    1.983478] r8169 0000:03:00.0 eth0: RTL8168g/8111g at 0xffffc9000063a000, 44:8a:5b:8e:7d:ab, XID 0c000800 IRQ 105
[    1.983483] r8169 0000:03:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    1.986877] ahci 0000:00:13.0: AHCI 0001.0300 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[    1.986885] ahci 0000:00:13.0: flags: 64bit ncq pm led clo pio slum part deso sadm sds 
[    1.987342] scsi0 : ahci
[    1.987479] scsi1 : ahci
[    1.987546] ata1: SATA max UDMA/133 abar m2048@0xd0716000 port 0xd0716100 irq 104
[    1.987550] ata2: SATA max UDMA/133 abar m2048@0xd0716000 port 0xd0716180 irq 104
[    2.050897] raid6: sse2x1     606 MB/s
[    2.118890] raid6: sse2x2     741 MB/s
[    2.178855] usb 1-1: new low-speed USB device number 2 using xhci_hcd
[    2.186847] raid6: sse2x4    1271 MB/s
[    2.186850] raid6: using algorithm sse2x4 (1271 MB/s)
[    2.186852] raid6: using ssse3x2 recovery algorithm
[    2.188934] xor: measuring software checksum speed
[    2.200365] usb 1-1: New USB device found, idVendor=1997, idProduct=0409
[    2.200369] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.200373] usb 1-1: Product: Micro Keyboard
[    2.200375] usb 1-1: Manufacturer: Riitek
[    2.200510] usb 1-1: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[    2.200519] usb 1-1: ep 0x82 - rounding interval to 64 microframes, ep desc says 80 microframes
[    2.206056] hidraw: raw HID events driver (C) Jiri Kosina
[    2.214205] usbcore: registered new interface driver usbhid
[    2.214210] usbhid: USB HID core driver
[    2.216761] input: Riitek Micro Keyboard as /devices/pci0000:00/0000:00:14.0/usb1/1-1/1-1:1.0/input/input6
[    2.216925] hid-generic 0003:1997:0409.0001: input,hidraw0: USB HID v1.11 Keyboard [Riitek Micro Keyboard] on usb-0000:00:14.0-1/input0
[    2.217177] input: Riitek Micro Keyboard as /devices/pci0000:00/0000:00:14.0/usb1/1-1/1-1:1.1/input/input7
[    2.217373] hid-generic 0003:1997:0409.0002: input,hidraw1: USB HID v1.11 Mouse [Riitek Micro Keyboard] on usb-0000:00:14.0-1/input1
[    2.226823]    prefetch64-sse:  8245.000 MB/sec
[    2.266821]    generic_sse:  7416.000 MB/sec
[    2.266824] xor: using function: prefetch64-sse (8245.000 MB/sec)
[    2.268734] async_tx: api initialized (async)
[    2.280632] md: raid6 personality registered for level 6
[    2.280638] md: raid5 personality registered for level 5
[    2.280640] md: raid4 personality registered for level 4
[    2.287146] systemd-udevd[119]: renamed network interface eth0 to p2p1
[    2.292578] md: raid10 personality registered for level 10
[    2.314844] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.318838] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.319446] ata2.00: ATA-9: ST2000DM001-1CH164, CC27, max UDMA/133
[    2.319452] ata2.00: 3907029168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    2.319999] ata2.00: configured for UDMA/133
[    2.321276] ata1.00: ATA-9: ST2000DM001-1CH164, CC27, max UDMA/133
[    2.321279] ata1.00: 3907029168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.321896] ata1.00: configured for UDMA/133
[    2.322092] scsi 0:0:0:0: Direct-Access     ATA      ST2000DM001-1CH1 CC27 PQ: 0 ANSI: 5
[    2.322354] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.322388] sd 0:0:0:0: [sda] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    2.322393] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    2.322535] sd 0:0:0:0: [sda] Write Protect is off
[    2.322539] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.322593] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.322610] scsi 1:0:0:0: Direct-Access     ATA      ST2000DM001-1CH1 CC27 PQ: 0 ANSI: 5
[    2.323065] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    2.323078] sd 1:0:0:0: [sdb] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    2.323083] sd 1:0:0:0: [sdb] 4096-byte physical blocks
[    2.323241] sd 1:0:0:0: [sdb] Write Protect is off
[    2.323246] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.323309] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.337366]  sda: sda1 sda2 sda3 sda4
[    2.338015] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.366867] usb 1-2: new high-speed USB device number 3 using xhci_hcd
[    2.382984] usb 1-2: New USB device found, idVendor=0409, idProduct=005a
[    2.382989] usb 1-2: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.383305] hub 1-2:1.0: USB hub found
[    2.383337] hub 1-2:1.0: 2 ports detected
[    2.494850] usb 1-3: new full-speed USB device number 4 using xhci_hcd
[    2.514778] usb 1-3: New USB device found, idVendor=0e6f, idProduct=0113
[    2.514783] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.514786] usb 1-3: Product: Afterglow Gamepad for Xbox 360
[    2.514789] usb 1-3: Manufacturer: Performance Designed Products
[    2.514792] usb 1-3: SerialNumber: 0000FC38
[    2.682856] usb 1-4: new full-speed USB device number 5 using xhci_hcd
[    2.702713] usb 1-4: New USB device found, idVendor=0e6f, idProduct=0113
[    2.702718] usb 1-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.702721] usb 1-4: Product: Afterglow Gamepad for Xbox 360
[    2.702724] usb 1-4: Manufacturer: Performance Designed Products
[    2.702727] usb 1-4: SerialNumber: 0000DA9D
[    2.798847] tsc: Refined TSC clocksource calibration: 1999.999 MHz
[    3.086861] usb 1-2.2: new low-speed USB device number 6 using xhci_hcd
[    3.107646] usb 1-2.2: New USB device found, idVendor=04f3, idProduct=0110
[    3.107650] usb 1-2.2: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    3.107782] usb 1-2.2: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[    3.107792] usb 1-2.2: ep 0x82 - rounding interval to 64 microframes, ep desc says 80 microframes
[    3.111298] input: HID 04f3:0110 as /devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2.2/1-2.2:1.0/input/input8
[    3.111456] hid-generic 0003:04F3:0110.0003: input,hidraw2: USB HID v1.10 Keyboard [HID 04f3:0110] on usb-0000:00:14.0-2.2/input0
[    3.116825] input: HID 04f3:0110 as /devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2.2/1-2.2:1.1/input/input9
[    3.117031] hid-generic 0003:04F3:0110.0004: input,hidraw3: USB HID v1.10 Mouse [HID 04f3:0110] on usb-0000:00:14.0-2.2/input1
[    3.798959] Switched to clocksource tsc
[    7.224521]  sdb: sdb1 sdb2 sdb3 sdb4
[    7.225113] sd 1:0:0:0: [sdb] Attached SCSI disk
[    7.332477] md: bind<sda3>
[    7.340107] md: bind<sdb2>
[    7.363057] md: bind<sda4>
[    7.368755] md: bind<sda2>
[    7.371804] md/raid1:md0: not clean -- starting background reconstruction
[    7.371809] md/raid1:md0: active with 2 out of 2 mirrors
[    7.371839] md0: detected capacity change from 0 to 200081408
[    7.374651] md: resync of RAID array md0
[    7.374657] md: minimum _guaranteed_  speed: 1000 KB/sec/disk.
[    7.374659] md: using maximum available idle IO bandwidth (but not more than 200000 KB/sec) for resync.
[    7.374663] md: using 128k window, over a total of 195392k.
[    7.375168]  md0: unknown partition table
[    7.376355] md: bind<sdb3>
[    7.379468] md/raid0:md1: md_size is 62498816 sectors.
[    7.379473] md: RAID0 configuration for md1 - 1 zone
[    7.379475] md: zone0=[sda3/sdb3]
[    7.379481]       zone-offset=         0KB, device-offset=         0KB, size=  31249408KB
[    7.379483] 
[    7.379495] md1: detected capacity change from 0 to 31999393792
[    7.382532]  md1: unknown partition table
[    7.382693] md: bind<sdb4>
[    7.385596] md/raid1:md2: not clean -- starting background reconstruction
[    7.385602] md/raid1:md2: active with 2 out of 2 mirrors
[    7.385633] md2: detected capacity change from 0 to 1983063588864
[    7.385721] md: delaying resync of md2 until md0 has finished (they share one or more physical units)
[    7.430851] random: lvm urandom read with 53 bits of entropy available
[    7.468191]  md2: unknown partition table
[    7.719293] bio: create slab <bio-1> at 1
[    7.898586] EXT4-fs (dm-1): INFO: recovery required on readonly filesystem
[    7.898592] EXT4-fs (dm-1): write access will be enabled during recovery
[    8.001099] random: nonblocking pool is initialized
[    8.906148] EXT4-fs (dm-1): recovery complete
[    8.939313] EXT4-fs (dm-1): mounted filesystem with ordered data mode. Opts: (null)
[    9.974640] init: plymouth-upstart-bridge main process (249) terminated with status 1
[    9.974669] init: plymouth-upstart-bridge main process ended, respawning
[    9.979004] init: plymouth-upstart-bridge main process (260) terminated with status 1
[    9.979032] init: plymouth-upstart-bridge main process ended, respawning
[    9.982677] init: plymouth-upstart-bridge main process (262) terminated with status 1
[    9.982705] init: plymouth-upstart-bridge main process ended, respawning
[    9.987107] init: plymouth-upstart-bridge main process (264) terminated with status 1
[    9.987134] init: plymouth-upstart-bridge main process ended, respawning
[    9.992007] init: plymouth-upstart-bridge main process (266) terminated with status 1
[    9.992035] init: plymouth-upstart-bridge main process ended, respawning
[   12.732340] Adding 975868k swap on /dev/sda1.  Priority:-1 extents:1 across:975868k FS
[   12.752396] Adding 975868k swap on /dev/sdb1.  Priority:-2 extents:1 across:975868k FS
[   12.779872] IPv6: ADDRCONF(NETDEV_UP): p2p1: link is not ready
[   12.850419] systemd-udevd[387]: starting version 204
[   12.945042] lp: driver loaded but no devices found
[   12.967780] wmi: Mapper loaded
[   12.979290] [drm] Initialized drm 1.1.0 20060810
[   13.020769] [drm] Memory usable by graphics device = 2048M
[   13.020776] checking generic (a0000 10000) vs hw (c0000000 10000000)
[   13.020779] fb: conflicting fb hw usage inteldrmfb vs EFI VGA - removing generic driver
[   13.020804] Console: switching to colour dummy device 80x25
[   13.075105] i915 0000:00:02.0: irq 106 for MSI/MSI-X
[   13.075121] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[   13.075124] [drm] Driver supports precise vblank timestamp query.
[   13.075216] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   13.095777] type=1400 audit(1404976607.698:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=433 comm="apparmor_parser"
[   13.095789] type=1400 audit(1404976607.698:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=433 comm="apparmor_parser"
[   13.095796] type=1400 audit(1404976607.698:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=433 comm="apparmor_parser"
[   13.096744] type=1400 audit(1404976607.698:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=433 comm="apparmor_parser"
[   13.096756] type=1400 audit(1404976607.698:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=433 comm="apparmor_parser"
[   13.097241] type=1400 audit(1404976607.698:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=433 comm="apparmor_parser"
[   13.321871] fbcon: inteldrmfb (fb0) is primary device
[   13.432881] r8169 0000:03:00.0 p2p1: link down
[   13.432916] r8169 0000:03:00.0 p2p1: link down
[   13.432966] IPv6: ADDRCONF(NETDEV_UP): p2p1: link is not ready
[   13.734953] Console: switching to colour frame buffer device 240x67
[   13.746036] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   13.746038] i915 0000:00:02.0: registered panic notifier
[   13.749517] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   13.751181] acpi device:0a: registered as cooling_device5
[   13.755679] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input10
[   13.760224] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   13.764397] snd_hda_intel 0000:00:1b.0: irq 107 for MSI/MSI-X
[   13.767009] EXT4-fs (dm-1): re-mounted. Opts: errors=remount-ro
[   13.820294] SKU: Nid=0x1d sku_cfg=0x4025c603
[   13.820295] SKU: port_connectivity=0x1
[   13.820296] SKU: enable_pcbeep=0x0
[   13.820297] SKU: check_sum=0x00000005
[   13.820297] SKU: customization=0x000000c6
[   13.820298] SKU: external_amp=0x0
[   13.820298] SKU: platform_type=0x0
[   13.820299] SKU: swap=0x1
[   13.820299] SKU: override=0x1
[   13.823464] autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:line
[   13.823466]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   13.823467]    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[   13.823468]    mono: mono_out=0x0
[   13.823468]    inputs:
[   13.823470]      Front Mic=0x19
[   13.823472]      Rear Mic=0x18
[   13.823473]      Line=0x1a
[   13.823474] realtek: No valid SSID, checking pincfg 0x4025c603 for NID 0x1d
[   13.823475] realtek: Enabling init ASM_ID=0xc603 CODEC_ID=10ec0887
[   13.901415] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input16
[   13.901556] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
[   13.901673] input: HDA Intel PCH Line Out as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[   13.901783] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   13.901896] input: HDA Intel PCH Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   13.902005] input: HDA Intel PCH Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   14.782853] [drm] Enabling RC6 states: RC6 off, RC6p off, RC6pp off
[   15.241248] r8169 0000:03:00.0 p2p1: link up
[   15.241261] IPv6: ADDRCONF(NETDEV_CHANGE): p2p1: link becomes ready
[   16.618515] EXT4-fs (md0): mounting ext2 file system using the ext4 subsystem
[   16.660688] EXT4-fs (md0): mounted filesystem without journal. Opts: (null)
[   50.614102] EXT4-fs (dm-0): mounted filesystem with ordered data mode. Opts: (null)
[   51.524061] init: failsafe main process (922) killed by TERM signal
[   51.727060] input: Xbox Gamepad (userspace driver) as /devices/virtual/input/input17
[   51.728533] input: Xbox Gamepad (userspace driver) #2 as /devices/virtual/input/input18
[   51.731153] input: Xbox Gamepad (userspace driver) #3 as /devices/virtual/input/input19
[   51.731333] input: Xbox Gamepad (userspace driver) #4 as /devices/virtual/input/input20
[   51.780134] type=1400 audit(1404976646.841:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/tcpdump" pid=1060 comm="apparmor_parser"
[   51.786281] type=1400 audit(1404976646.845:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=1057 comm="apparmor_parser"
[   51.786299] type=1400 audit(1404976646.845:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1057 comm="apparmor_parser"
[   51.786307] type=1400 audit(1404976646.845:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1057 comm="apparmor_parser"
[   51.787374] type=1400 audit(1404976646.849:12): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1057 comm="apparmor_parser"
[   51.787386] type=1400 audit(1404976646.849:13): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1057 comm="apparmor_parser"
[   51.787641] type=1400 audit(1404976646.849:14): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=1056 comm="apparmor_parser"
[   51.787653] type=1400 audit(1404976646.849:15): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=1056 comm="apparmor_parser"
[   51.787874] type=1400 audit(1404976646.849:16): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1057 comm="apparmor_parser"
[   51.788232] type=1400 audit(1404976646.849:17): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="chromium" pid=1056 comm="apparmor_parser"
[   51.815390] init: avahi-cups-reload main process (1063) terminated with status 1
[   51.951114] init: samba-ad-dc main process (1081) terminated with status 1
[   52.331717] init: powerwaked main process (1254) terminated with status 1
[   53.126813] init: plymouth-upstart-bridge main process ended, respawning
[   56.347719] WARNING! power/level is deprecated; use power/control instead
[   59.164780] Bluetooth: Core ver 2.17
[   59.164830] NET: Registered protocol family 31
[   59.164833] Bluetooth: HCI device and connection manager initialized
[   59.164845] Bluetooth: HCI socket layer initialized
[   59.164850] Bluetooth: L2CAP socket layer initialized
[   59.164858] Bluetooth: SCO socket layer initialized
[   59.174506] Bluetooth: RFCOMM TTY layer initialized
[   59.174523] Bluetooth: RFCOMM socket layer initialized
[   59.174534] Bluetooth: RFCOMM ver 1.11
[   85.085861] init: anacron main process (1201) killed by TERM signal
[  123.167922] md: md0: resync done.
[  123.174198] md: resync of RAID array md2
[  123.174208] md: minimum _guaranteed_  speed: 1000 KB/sec/disk.
[  123.174213] md: using maximum available idle IO bandwidth (but not more than 200000 KB/sec) for resync.
[  123.174220] md: using 128k window, over a total of 1936585536k.
[  123.258413] RAID1 conf printout:
[  123.258448]  --- wd:2 rd:2
[  123.258455]  disk 0, wo:0, o:1, dev:sda2
[  123.258460]  disk 1, wo:0, o:1, dev:sdb2
[  251.390612] init: powernap main process (1299) killed by KILL signal
[ 4573.218656] perf samples too long (2502 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
[12970.867695] md: md2: resync done.
[12971.100249] RAID1 conf printout:
[12971.100257]  --- wd:2 rd:2
[12971.100260]  disk 0, wo:0, o:1, dev:sda4
[12971.100263]  disk 1, wo:0, o:1, dev:sdb4

```


[B]/proc/cmdline
[/B]BOOT_IMAGE=/vmlinuz-3.13.0-30-generic root=/dev/mapper/stripe-root ro quiet splash nomdmonddf nomdmonisw nomdmonddf nomdmonisw
[B]
/etc/initramfs-tools/conf.d/resume
[/B]RESUME=UUID=a06ceb3d-7b09-41b7-b52d-9f37bd14e5c3


**The crash log from /var/crash/susres.2014...crash reads**
```
ProblemType: KernelOopsAnnotation: This occured during a previous suspend and prevented it from resuming properly.
Architecture: amd64
Date: Thu Jul 10 08:17:27 2014
DistroRelease: Ubuntu 14.04
ExecutablePath: /usr/share/apport/apportcheckresume
ExecutableTimestamp: 1400281919
Failure: suspend/resume
InterpreterPath: /usr/bin/python3.4
Package: linux-image-3.13.0-30-generic 3.13.0-30.55
ProcCmdline: /usr/bin/python3 /usr/share/apport/apportcheckresume
ProcCwd: /
ProcEnviron:
 TERM=linux
 PATH=(custom, no user)
ProcMaps:
 00400000-00754000 r-xp 00000000 fc:01 1439211                            /usr/bin/python3.4
 00953000-00954000 r--p 00353000 fc:01 1439211                            /usr/bin/python3.4
 00954000-009e0000 rw-p 00354000 fc:01 1439211                            /usr/bin/python3.4
 009e0000-009fc000 rw-p 00000000 00:00 0 
 01809000-01ad6000 rw-p 00000000 00:00 0                                  [heap]
 7f7c52383000-7f7c52403000 rw-p 00000000 00:00 0 
 7f7c52403000-7f7c52424000 r-xp 00000000 fc:01 1569997                    /lib/x86_64-linux-gnu/liblzma.so.5.0.0
 7f7c52424000-7f7c52623000 ---p 00021000 fc:01 1569997                    /lib/x86_64-linux-gnu/liblzma.so.5.0.0
 7f7c52623000-7f7c52624000 r--p 00020000 fc:01 1569997                    /lib/x86_64-linux-gnu/liblzma.so.5.0.0
 7f7c52624000-7f7c52625000 rw-p 00021000 fc:01 1569997                    /lib/x86_64-linux-gnu/liblzma.so.5.0.0
 7f7c52625000-7f7c5263b000 r-xp 00000000 fc:01 1569984                    /lib/x86_64-linux-gnu/libgcc_s.so.1
 7f7c5263b000-7f7c5283a000 ---p 00016000 fc:01 1569984                    /lib/x86_64-linux-gnu/libgcc_s.so.1
 7f7c5283a000-7f7c5283b000 rw-p 00015000 fc:01 1569984                    /lib/x86_64-linux-gnu/libgcc_s.so.1
 7f7c5283b000-7f7c52921000 r-xp 00000000 fc:01 1441848                    /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.19
 7f7c52921000-7f7c52b20000 ---p 000e6000 fc:01 1441848                    /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.19
 7f7c52b20000-7f7c52b28000 r--p 000e5000 fc:01 1441848                    /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.19
 7f7c52b28000-7f7c52b2a000 rw-p 000ed000 fc:01 1441848                    /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.19
 7f7c52b2a000-7f7c52b3f000 rw-p 00000000 00:00 0 
 7f7c52b3f000-7f7c52c83000 r-xp 00000000 fc:01 1439028                    /usr/lib/x86_64-linux-gnu/libapt-pkg.so.4.12.0
 7f7c52c83000-7f7c52e83000 ---p 00144000 fc:01 1439028                    /usr/lib/x86_64-linux-gnu/libapt-pkg.so.4.12.0
 7f7c52e83000-7f7c52e87000 r--p 00144000 fc:01 1439028                    /usr/lib/x86_64-linux-gnu/libapt-pkg.so.4.12.0
 7f7c52e87000-7f7c52e88000 rw-p 00148000 fc:01 1439028                    /usr/lib/x86_64-linux-gnu/libapt-pkg.so.4.12.0
 7f7c52e88000-7f7c52e89000 rw-p 00000000 00:00 0 
 7f7c52e89000-7f7c52ecf000 r-xp 00000000 fc:01 1449902                    /usr/lib/python3/dist-packages/apt_pkg.cpython-34m-x86_64-linux-gnu.so
 7f7c52ecf000-7f7c530ce000 ---p 00046000 fc:01 1449902                    /usr/lib/python3/dist-packages/apt_pkg.cpython-34m-x86_64-linux-gnu.so
 7f7c530ce000-7f7c530d0000 r--p 00045000 fc:01 1449902                    /usr/lib/python3/dist-packages/apt_pkg.cpython-34m-x86_64-linux-gnu.so
 7f7c530d0000-7f7c530d8000 rw-p 00047000 fc:01 1449902                    /usr/lib/python3/dist-packages/apt_pkg.cpython-34m-x86_64-linux-gnu.so
 7f7c530d8000-7f7c53118000 rw-p 00000000 00:00 0 
 7f7c53118000-7f7c5316c000 r-xp 00000000 fc:01 1591145                    /lib/x86_64-linux-gnu/libssl.so.1.0.0
 7f7c5316c000-7f7c5336c000 ---p 00054000 fc:01 1591145                    /lib/x86_64-linux-gnu/libssl.so.1.0.0
 7f7c5336c000-7f7c5336f000 r--p 00054000 fc:01 1591145                    /lib/x86_64-linux-gnu/libssl.so.1.0.0
 7f7c5336f000-7f7c53375000 rw-p 00057000 fc:01 1591145                    /lib/x86_64-linux-gnu/libssl.so.1.0.0
 7f7c53375000-7f7c53376000 rw-p 00000000 00:00 0 
 7f7c53376000-7f7c53389000 r-xp 00000000 fc:01 1440969                    /usr/lib/python3.4/lib-dynload/_ssl.cpython-34m-x86_64-linux-gnu.so
 7f7c53389000-7f7c53588000 ---p 00013000 fc:01 1440969                    /usr/lib/python3.4/lib-dynload/_ssl.cpython-34m-x86_64-linux-gnu.so
 7f7c53588000-7f7c53589000 r--p 00012000 fc:01 1440969                    /usr/lib/python3.4/lib-dynload/_ssl.cpython-34m-x86_64-linux-gnu.so
 7f7c53589000-7f7c5358d000 rw-p 00013000 fc:01 1440969                    /usr/lib/python3.4/lib-dynload/_ssl.cpython-34m-x86_64-linux-gnu.so
 7f7c5358d000-7f7c5370d000 rw-p 00000000 00:00 0 
 7f7c5370d000-7f7c538be000 r-xp 00000000 fc:01 1591249                    /lib/x86_64-linux-gnu/libcrypto.so.1.0.0
 7f7c538be000-7f7c53abd000 ---p 001b1000 fc:01 1591249                    /lib/x86_64-linux-gnu/libcrypto.so.1.0.0
 7f7c53abd000-7f7c53ad8000 r--p 001b0000 fc:01 1591249                    /lib/x86_64-linux-gnu/libcrypto.so.1.0.0
 7f7c53ad8000-7f7c53ae3000 rw-p 001cb000 fc:01 1591249                    /lib/x86_64-linux-gnu/libcrypto.so.1.0.0
 7f7c53ae3000-7f7c53ae7000 rw-p 00000000 00:00 0 
 7f7c53ae7000-7f7c53aec000 r-xp 00000000 fc:01 1440961                    /usr/lib/python3.4/lib-dynload/_hashlib.cpython-34m-x86_64-linux-gnu.so
 7f7c53aec000-7f7c53ceb000 ---p 00005000 fc:01 1440961                    /usr/lib/python3.4/lib-dynload/_hashlib.cpython-34m-x86_64-linux-gnu.so
 7f7c53ceb000-7f7c53cec000 r--p 00004000 fc:01 1440961                    /usr/lib/python3.4/lib-dynload/_hashlib.cpython-34m-x86_64-linux-gnu.so
 7f7c53cec000-7f7c53ced000 rw-p 00005000 fc:01 1440961                    /usr/lib/python3.4/lib-dynload/_hashlib.cpython-34m-x86_64-linux-gnu.so
 7f7c53ced000-7f7c53d2d000 rw-p 00000000 00:00 0 
 7f7c53d2d000-7f7c53d3c000 r-xp 00000000 fc:01 1569959                    /lib/x86_64-linux-gnu/libbz2.so.1.0.4
 7f7c53d3c000-7f7c53f3b000 ---p 0000f000 fc:01 1569959                    /lib/x86_64-linux-gnu/libbz2.so.1.0.4
 7f7c53f3b000-7f7c53f3c000 r--p 0000e000 fc:01 1569959                    /lib/x86_64-linux-gnu/libbz2.so.1.0.4
 7f7c53f3c000-7f7c53f3d000 rw-p 0000f000 fc:01 1569959                    /lib/x86_64-linux-gnu/libbz2.so.1.0.4
 7f7c53f3d000-7f7c53f40000 r-xp 00000000 fc:01 1440946                    /usr/lib/python3.4/lib-dynload/_bz2.cpython-34m-x86_64-linux-gnu.so
 7f7c53f40000-7f7c5413f000 ---p 00003000 fc:01 1440946                    /usr/lib/python3.4/lib-dynload/_bz2.cpython-34m-x86_64-linux-gnu.so
 7f7c5413f000-7f7c54140000 r--p 00002000 fc:01 1440946                    /usr/lib/python3.4/lib-dynload/_bz2.cpython-34m-x86_64-linux-gnu.so
 7f7c54140000-7f7c54141000 rw-p 00003000 fc:01 1440946                    /usr/lib/python3.4/lib-dynload/_bz2.cpython-34m-x86_64-linux-gnu.so
 7f7c54141000-7f7c542e2000 rw-p 00000000 00:00 0 
 7f7c542e2000-7f7c542ed000 r-xp 00000000 fc:01 1570019                    /lib/x86_64-linux-gnu/libnss_files-2.19.so
 7f7c542ed000-7f7c544ec000 ---p 0000b000 fc:01 1570019                    /lib/x86_64-linux-gnu/libnss_files-2.19.so
 7f7c544ec000-7f7c544ed000 r--p 0000a000 fc:01 1570019                    /lib/x86_64-linux-gnu/libnss_files-2.19.so
 7f7c544ed000-7f7c544ee000 rw-p 0000b000 fc:01 1570019                    /lib/x86_64-linux-gnu/libnss_files-2.19.so
 7f7c544ee000-7f7c544f9000 r-xp 00000000 fc:01 1570023                    /lib/x86_64-linux-gnu/libnss_nis-2.19.so
 7f7c544f9000-7f7c546f8000 ---p 0000b000 fc:01 1570023                    /lib/x86_64-linux-gnu/libnss_nis-2.19.so
 7f7c546f8000-7f7c546f9000 r--p 0000a000 fc:01 1570023                    /lib/x86_64-linux-gnu/libnss_nis-2.19.so
 7f7c546f9000-7f7c546fa000 rw-p 0000b000 fc:01 1570023                    /lib/x86_64-linux-gnu/libnss_nis-2.19.so
 7f7c546fa000-7f7c54711000 r-xp 00000000 fc:01 1570013                    /lib/x86_64-linux-gnu/libnsl-2.19.so
 7f7c54711000-7f7c54910000 ---p 00017000 fc:01 1570013                    /lib/x86_64-linux-gnu/libnsl-2.19.so
 7f7c54910000-7f7c54911000 r--p 00016000 fc:01 1570013                    /lib/x86_64-linux-gnu/libnsl-2.19.so
 7f7c54911000-7f7c54912000 rw-p 00017000 fc:01 1570013                    /lib/x86_64-linux-gnu/libnsl-2.19.so
 7f7c54912000-7f7c54914000 rw-p 00000000 00:00 0 
 7f7c54914000-7f7c5491d000 r-xp 00000000 fc:01 1570015                    /lib/x86_64-linux-gnu/libnss_compat-2.19.so
 7f7c5491d000-7f7c54b1c000 ---p 00009000 fc:01 1570015                    /lib/x86_64-linux-gnu/libnss_compat-2.19.so
 7f7c54b1c000-7f7c54b1d000 r--p 00008000 fc:01 1570015                    /lib/x86_64-linux-gnu/libnss_compat-2.19.so
 7f7c54b1d000-7f7c54b1e000 rw-p 00009000 fc:01 1570015                    /lib/x86_64-linux-gnu/libnss_compat-2.19.so
 7f7c54b1e000-7f7c54c23000 r-xp 00000000 fc:01 1569998                    /lib/x86_64-linux-gnu/libm-2.19.so
 7f7c54c23000-7f7c54e22000 ---p 00105000 fc:01 1569998                    /lib/x86_64-linux-gnu/libm-2.19.so
 7f7c54e22000-7f7c54e23000 r--p 00104000 fc:01 1569998                    /lib/x86_64-linux-gnu/libm-2.19.so
 7f7c54e23000-7f7c54e24000 rw-p 00105000 fc:01 1569998                    /lib/x86_64-linux-gnu/libm-2.19.so
 7f7c54e24000-7f7c54e3c000 r-xp 00000000 fc:01 1570078                    /lib/x86_64-linux-gnu/libz.so.1.2.8
 7f7c54e3c000-7f7c5503b000 ---p 00018000 fc:01 1570078                    /lib/x86_64-linux-gnu/libz.so.1.2.8
 7f7c5503b000-7f7c5503c000 r--p 00017000 fc:01 1570078                    /lib/x86_64-linux-gnu/libz.so.1.2.8
 7f7c5503c000-7f7c5503d000 rw-p 00018000 fc:01 1570078                    /lib/x86_64-linux-gnu/libz.so.1.2.8
 7f7c5503d000-7f7c55064000 r-xp 00000000 fc:01 1569981                    /lib/x86_64-linux-gnu/libexpat.so.1.6.0
 7f7c55064000-7f7c55264000 ---p 00027000 fc:01 1569981                    /lib/x86_64-linux-gnu/libexpat.so.1.6.0
 7f7c55264000-7f7c55266000 r--p 00027000 fc:01 1569981                    /lib/x86_64-linux-gnu/libexpat.so.1.6.0
 7f7c55266000-7f7c55267000 rw-p 00029000 fc:01 1569981                    /lib/x86_64-linux-gnu/libexpat.so.1.6.0
 7f7c55267000-7f7c55269000 r-xp 00000000 fc:01 1570073                    /lib/x86_64-linux-gnu/libutil-2.19.so
 7f7c55269000-7f7c55468000 ---p 00002000 fc:01 1570073                    /lib/x86_64-linux-gnu/libutil-2.19.so
 7f7c55468000-7f7c55469000 r--p 00001000 fc:01 1570073                    /lib/x86_64-linux-gnu/libutil-2.19.so
 7f7c55469000-7f7c5546a000 rw-p 00002000 fc:01 1570073                    /lib/x86_64-linux-gnu/libutil-2.19.so
 7f7c5546a000-7f7c5546d000 r-xp 00000000 fc:01 1569976                    /lib/x86_64-linux-gnu/libdl-2.19.so
 7f7c5546d000-7f7c5566c000 ---p 00003000 fc:01 1569976                    /lib/x86_64-linux-gnu/libdl-2.19.so
 7f7c5566c000-7f7c5566d000 r--p 00002000 fc:01 1569976                    /lib/x86_64-linux-gnu/libdl-2.19.so
 7f7c5566d000-7f7c5566e000 rw-p 00003000 fc:01 1569976                    /lib/x86_64-linux-gnu/libdl-2.19.so
 7f7c5566e000-7f7c5582a000 r-xp 00000000 fc:01 1569960                    /lib/x86_64-linux-gnu/libc-2.19.so
 7f7c5582a000-7f7c55a29000 ---p 001bc000 fc:01 1569960                    /lib/x86_64-linux-gnu/libc-2.19.so
 7f7c55a29000-7f7c55a2d000 r--p 001bb000 fc:01 1569960                    /lib/x86_64-linux-gnu/libc-2.19.so
 7f7c55a2d000-7f7c55a2f000 rw-p 001bf000 fc:01 1569960                    /lib/x86_64-linux-gnu/libc-2.19.so
 7f7c55a2f000-7f7c55a34000 rw-p 00000000 00:00 0 
 7f7c55a34000-7f7c55a4d000 r-xp 00000000 fc:01 1570050                    /lib/x86_64-linux-gnu/libpthread-2.19.so
 7f7c55a4d000-7f7c55c4c000 ---p 00019000 fc:01 1570050                    /lib/x86_64-linux-gnu/libpthread-2.19.so
 7f7c55c4c000-7f7c55c4d000 r--p 00018000 fc:01 1570050                    /lib/x86_64-linux-gnu/libpthread-2.19.so
 7f7c55c4d000-7f7c55c4e000 rw-p 00019000 fc:01 1570050                    /lib/x86_64-linux-gnu/libpthread-2.19.so
 7f7c55c4e000-7f7c55c52000 rw-p 00000000 00:00 0 
 7f7c55c52000-7f7c55c75000 r-xp 00000000 fc:01 1569940                    /lib/x86_64-linux-gnu/ld-2.19.so
 7f7c55cae000-7f7c55cee000 rw-p 00000000 00:00 0 
 7f7c55d1f000-7f7c55e64000 rw-p 00000000 00:00 0 
 7f7c55e72000-7f7c55e74000 rw-p 00000000 00:00 0 
 7f7c55e74000-7f7c55e75000 r--p 00022000 fc:01 1569940                    /lib/x86_64-linux-gnu/ld-2.19.so
 7f7c55e75000-7f7c55e76000 rw-p 00023000 fc:01 1569940                    /lib/x86_64-linux-gnu/ld-2.19.so
 7f7c55e76000-7f7c55e77000 rw-p 00000000 00:00 0 
 7fff368ce000-7fff368ef000 rw-p 00000000 00:00 0                          [stack]
 7fff369fe000-7fff36a00000 r-xp 00000000 00:00 0                          [vdso]
 ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vsyscall]
ProcStatus:
 Name:	apportcheckresu
 State:	R (running)
 Tgid:	1326
 Ngid:	0
 Pid:	1326
 PPid:	1143
 TracerPid:	0
 Uid:	0	0	0	0
 Gid:	0	0	0	0
 FDSize:	64
 Groups:	0 
 VmPeak:	   66984 kB
 VmSize:	   66984 kB
 VmLck:	       0 kB
 VmPin:	       0 kB
 VmHWM:	   14692 kB
 VmRSS:	   14692 kB
 VmData:	    8936 kB
 VmStk:	     136 kB
 VmExe:	    3408 kB
 VmLib:	    8500 kB
 VmPTE:	     140 kB
 VmSwap:	       0 kB
 Threads:	1
 SigQ:	0/27088
 SigPnd:	0000000000000000
 ShdPnd:	0000000000000000
 SigBlk:	0000000000000000
 SigIgn:	0000000001001000
 SigCgt:	0000000180000002
 CapInh:	0000000000000000
 CapPrm:	0000001fffffffff
 CapEff:	0000001fffffffff
 CapBnd:	0000001fffffffff
 Seccomp:	0
 Cpus_allowed:	f
 Cpus_allowed_list:	0-3
 Mems_allowed:	00000000,00000001
 Mems_allowed_list:	0
 voluntary_ctxt_switches:	3
 nonvoluntary_ctxt_switches:	28
SleepLog:
 Initial commandline parameters: 
 Thu Jul  3 22:17:31 BST 2014: Running hooks for suspend.
 Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
 /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
 /usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
 Linux mediapc 3.13.0-30-generic #54-Ubuntu SMP Mon Jun 9 22:45:01 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
 Module                  Size  Used by
 rfcomm                 69160  0 
 bluetooth             395423  3 rfcomm
 snd_hda_codec_realtek    61438  1 
 snd_hda_intel          52355  0 
 snd_hda_codec         192906  2 snd_hda_codec_realtek,snd_hda_intel
 snd_hwdep              13602  1 snd_hda_codec
 snd_pcm               102099  2 snd_hda_codec,snd_hda_intel
 snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
 snd_seq_midi           13324  0 
 snd_seq_midi_event     14899  1 snd_seq_midi
 snd_rawmidi            30144  1 snd_seq_midi
 snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
 snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
 snd_timer              29482  2 snd_pcm,snd_seq
 kvm                   451511  0 
 radeon               1514165  6 
 ttm                    85115  1 radeon
 snd                    69238  10 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
 drm_kms_helper         53081  1 radeon
 drm                   303102  8 ttm,drm_kms_helper,radeon
 edac_core              62291  0 
 i2c_algo_bit           13413  1 radeon
 sp5100_tco             13979  0 
 k10temp                13126  0 
 joydev                 17381  0 
 soundcore              12680  1 snd
 serio_raw              13462  0 
 lp                     17759  0 
 edac_mce_amd           22617  0 
 shpchp                 37032  0 
 parport                42348  1 lp
 mac_hid                13205  0 
 wmi                    19177  0 
 i2c_piix4              22155  0 
 hid_generic            12548  0 
 usbhid                 52570  0 
 hid                   106148  2 hid_generic,usbhid
 pata_acpi              13038  0 
 raid10                 48128  0 
 raid456                86484  0 
 async_raid6_recov      12984  1 raid456
 async_memcpy           12762  1 raid456
 async_pq               13365  1 raid456
 async_xor              13160  2 async_pq,raid456
 async_tx               13509  5 async_pq,raid456,async_xor,async_memcpy,async_raid6_recov
 xor                    21411  1 async_xor
 raid6_pq               97812  2 async_pq,async_raid6_recov
 raid1                  35530  2 
 raid0                  17842  1 
 psmouse               102222  0 
 multipath              13145  0 
 linear                 12894  0 
 r8169                  67581  0 
 ahci                   25819  8 
 libahci                32168  1 ahci
 mii                    13934  1 r8169
 pata_atiixp            13271  0 
              total       used       free     shared    buffers     cached
 Mem:       1788692    1659144     129548      11148     106548    1174756
 -/+ buffers/cache:     377840    1410852
 Swap:      1951736          0    1951736
 /usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
 /usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
 /etc/pm/sleep.d/10_grub-common suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
 /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
 /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
 Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
 /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
 /usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
 /usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
 /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
 stop: Unknown instance: 
 /usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
 /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
 /usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
 Kernel modesetting video driver detected, not using quirks.
 /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
 kernel.acpi_video_flags = 0
 /usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
 /etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
 
 Thu Jul  3 22:17:32 BST 2014: performing suspend
 Fri Jul  4 00:00:55 BST 2014: Awake.
 Fri Jul  4 00:00:55 BST 2014: Running hooks for resume
 Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
 /etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
 /usr/lib/pm-utils/sleep.d/99video resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
 /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
 /usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:
 
 /dev/sda:
  setting Advanced Power Management level to 0xfe (254)
  APM_level	= 254
 
 /dev/sdb:
  setting Advanced Power Management level to 0xfe (254)
  APM_level	= 254
 /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
 /usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
 /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
 /usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
 Reloaded unloaded modules.
 /usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
 Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
 /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
 /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.
 
 Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
 /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
 
 Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
 /etc/pm/sleep.d/10_grub-common resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
 /usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
 /usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
 /usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
 /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
 
 Fri Jul  4 00:00:56 BST 2014: Finished.
 Initial commandline parameters: 
 Fri Jul  4 00:08:43 BST 2014: Running hooks for suspend.
 Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
 /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
 /usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
 Linux mediapc 3.13.0-30-generic #54-Ubuntu SMP Mon Jun 9 22:45:01 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
 Module                  Size  Used by
 rfcomm                 69160  0 
 bluetooth             395423  3 rfcomm
 snd_hda_codec_realtek    61438  1 
 snd_hda_intel          52355  0 
 snd_hda_codec         192906  2 snd_hda_codec_realtek,snd_hda_intel
 snd_hwdep              13602  1 snd_hda_codec
 snd_pcm               102099  2 snd_hda_codec,snd_hda_intel
 snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
 snd_seq_midi           13324  0 
 snd_seq_midi_event     14899  1 snd_seq_midi
 snd_rawmidi            30144  1 snd_seq_midi
 snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
 snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
 snd_timer              29482  2 snd_pcm,snd_seq
 kvm                   451511  0 
 radeon               1514165  6 
 ttm                    85115  1 radeon
 snd                    69238  10 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
 drm_kms_helper         53081  1 radeon
 drm                   303102  8 ttm,drm_kms_helper,radeon
 edac_core              62291  0 
 i2c_algo_bit           13413  1 radeon
 sp5100_tco             13979  0 
 k10temp                13126  0 
 joydev                 17381  0 
 soundcore              12680  1 snd
 serio_raw              13462  0 
 lp                     17759  0 
 edac_mce_amd           22617  0 
 shpchp                 37032  0 
 parport                42348  1 lp
 mac_hid                13205  0 
 wmi                    19177  0 
 i2c_piix4              22155  0 
 hid_generic            12548  0 
 usbhid                 52570  0 
 hid                   106148  2 hid_generic,usbhid
 pata_acpi              13038  0 
 raid10                 48128  0 
 raid456                86484  0 
 async_raid6_recov      12984  1 raid456
 async_memcpy           12762  1 raid456
 async_pq               13365  1 raid456
 async_xor              13160  2 async_pq,raid456
 async_tx               13509  5 async_pq,raid456,async_xor,async_memcpy,async_raid6_recov
 xor                    21411  1 async_xor
 raid6_pq               97812  2 async_pq,async_raid6_recov
 raid1                  35530  2 
 raid0                  17842  1 
 psmouse               102222  0 
 multipath              13145  0 
 linear                 12894  0 
 r8169                  67581  0 
 ahci                   25819  8 
 libahci                32168  1 ahci
 mii                    13934  1 r8169
 pata_atiixp            13271  0 
              total       used       free     shared    buffers     cached
 Mem:       1788692    1643988     144704      11148     107540    1159396
 -/+ buffers/cache:     377052    1411640
 Swap:      1951736          0    1951736
 /usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
 /usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
 /etc/pm/sleep.d/10_grub-common suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
 /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
 /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
 Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
 /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
 /usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
 /usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
 /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
 /usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
 /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
 /usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
 Kernel modesetting video driver detected, not using quirks.
 /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
 kernel.acpi_video_flags = 0
 /usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
 /etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
 
 Fri Jul  4 00:08:44 BST 2014: performing suspend
 Fri Jul  4 21:31:54 BST 2014: Awake.
 Fri Jul  4 21:31:54 BST 2014: Running hooks for resume
 Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
 /etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
 /usr/lib/pm-utils/sleep.d/99video resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
 /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
 /usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:
 
 /dev/sda:
  setting Advanced Power Management level to 0xfe (254)
  APM_level	= 254
 
 /dev/sdb:
  setting Advanced Power Management level to 0xfe (254)
  APM_level	= 254
 /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
 /usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
 /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
 /usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
 Reloaded unloaded modules.
 /usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
 Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
 /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
 /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.
 
 Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
 /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
 
 Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
 /etc/pm/sleep.d/10_grub-common resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
 /usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
 /usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
 /usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
 /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
 
 Fri Jul  4 21:31:55 BST 2014: Finished.
 Initial commandline parameters: 
 Fri Jul  4 23:19:31 BST 2014: Running hooks for suspend.
 Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
 /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
 /usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
 Linux mediapc 3.13.0-30-generic #54-Ubuntu SMP Mon Jun 9 22:45:01 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
 Module                  Size  Used by
 rfcomm                 69160  0 
 bluetooth             395423  3 rfcomm
 snd_hda_codec_realtek    61438  1 
 snd_hda_intel          52355  0 
 snd_hda_codec         192906  2 snd_hda_codec_realtek,snd_hda_intel
 snd_hwdep              13602  1 snd_hda_codec
 snd_pcm               102099  2 snd_hda_codec,snd_hda_intel
 snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
 snd_seq_midi           13324  0 
 snd_seq_midi_event     14899  1 snd_seq_midi
 snd_rawmidi            30144  1 snd_seq_midi
 snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
 snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
 radeon               1514165  5 
 snd_timer              29482  2 snd_pcm,snd_seq
 ttm                    85115  1 radeon
 kvm                   451511  0 
 snd                    69238  10 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
 k10temp                13126  0 
 edac_core              62291  0 
 drm_kms_helper         53081  1 radeon
 sp5100_tco             13979  0 
 edac_mce_amd           22617  0 
 soundcore              12680  1 snd
 lp                     17759  0 
 serio_raw              13462  0 
 joydev                 17381  0 
 i2c_piix4              22155  0 
 drm                   303102  7 ttm,drm_kms_helper,radeon
 i2c_algo_bit           13413  1 radeon
 mac_hid                13205  0 
 shpchp                 37032  0 
 wmi                    19177  0 
 parport                42348  1 lp
 hid_generic            12548  0 
 usbhid                 52570  0 
 hid                   106148  2 hid_generic,usbhid
 pata_acpi              13038  0 
 raid10                 48128  0 
 raid456                86484  0 
 async_raid6_recov      12984  1 raid456
 async_memcpy           12762  1 raid456
 async_pq               13365  1 raid456
 async_xor              13160  2 async_pq,raid456
 async_tx               13509  5 async_pq,raid456,async_xor,async_memcpy,async_raid6_recov
 xor                    21411  1 async_xor
 psmouse               102222  0 
 raid6_pq               97812  2 async_pq,async_raid6_recov
 raid1                  35530  2 
 raid0                  17842  1 
 multipath              13145  0 
 pata_atiixp            13271  0 
 ahci                   25819  8 
 linear                 12894  0 
 libahci                32168  1 ahci
 r8169                  67581  0 
 mii                    13934  1 r8169
              total       used       free     shared    buffers     cached
 Mem:       1788692     671372    1117320      10520      85896     324088
 -/+ buffers/cache:     261388    1527304
 Swap:      1951736          0    1951736
 /usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
 /usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
 /etc/pm/sleep.d/10_grub-common suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
 /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
 /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
 Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
 /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
 /usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
 /usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
 /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
 /usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
 /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
 /usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
 Kernel modesetting video driver detected, not using quirks.
 /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
 kernel.acpi_video_flags = 0
 /usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
 /etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
 
 Fri Jul  4 23:19:32 BST 2014: performing suspend
 Sat Jul  5 00:00:55 BST 2014: Awake.
 Sat Jul  5 00:00:55 BST 2014: Running hooks for resume
 Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
 /etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
 /usr/lib/pm-utils/sleep.d/99video resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
 /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
 /usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:
 
 /dev/sda:
  setting Advanced Power Management level to 0xfe (254)
  APM_level	= 254
 
 /dev/sdb:
  setting Advanced Power Management level to 0xfe (254)
  APM_level	= 254
 /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
 /usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
 /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
 /usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
 Reloaded unloaded modules.
 /usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
 Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
 /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
 /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.
 
 Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
 /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
 
 Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
 /etc/pm/sleep.d/10_grub-common resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
 /usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
 /usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
 /usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
 /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
 
 Sat Jul  5 00:00:56 BST 2014: Finished.
 Initial commandline parameters: 
 Sat Jul  5 08:02:30 BST 2014: Running hooks for suspend.
 Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
 /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
 /usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
 Linux mediapc 3.13.0-30-generic #54-Ubuntu SMP Mon Jun 9 22:45:01 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
 Module                  Size  Used by
 rfcomm                 69160  0 
 bluetooth             395423  3 rfcomm
 snd_hda_codec_realtek    61438  1 
 snd_hda_intel          52355  0 
 snd_hda_codec         192906  2 snd_hda_codec_realtek,snd_hda_intel
 snd_hwdep              13602  1 snd_hda_codec
 snd_pcm               102099  2 snd_hda_codec,snd_hda_intel
 snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
 snd_seq_midi           13324  0 
 snd_seq_midi_event     14899  1 snd_seq_midi
 snd_rawmidi            30144  1 snd_seq_midi
 snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
 snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
 radeon               1514165  5 
 snd_timer              29482  2 snd_pcm,snd_seq
 ttm                    85115  1 radeon
 kvm                   451511  0 
 snd                    69238  10 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
 k10temp                13126  0 
 edac_core              62291  0 
 drm_kms_helper         53081  1 radeon
 sp5100_tco             13979  0 
 edac_mce_amd           22617  0 
 soundcore              12680  1 snd
 lp                     17759  0 
 serio_raw              13462  0 
 joydev                 17381  0 
 i2c_piix4              22155  0 
 drm                   303102  7 ttm,drm_kms_helper,radeon
 i2c_algo_bit           13413  1 radeon
 mac_hid                13205  0 
 shpchp                 37032  0 
 wmi                    19177  0 
 parport                42348  1 lp
 hid_generic            12548  0 
 usbhid                 52570  0 
 hid                   106148  2 hid_generic,usbhid
 pata_acpi              13038  0 
 raid10                 48128  0 
 raid456                86484  0 
 async_raid6_recov      12984  1 raid456
 async_memcpy           12762  1 raid456
 async_pq               13365  1 raid456
 async_xor              13160  2 async_pq,raid456
 async_tx               13509  5 async_pq,raid456,async_xor,async_memcpy,async_raid6_recov
 xor                    21411  1 async_xor
 psmouse               102222  0 
 raid6_pq               97812  2 async_pq,async_raid6_recov
 raid1                  35530  2 
 raid0                  17842  1 
 multipath              13145  0 
 pata_atiixp            13271  0 
 ahci                   25819  8 
 linear                 12894  0 
 libahci                32168  1 ahci
 r8169                  67581  0 
 mii                    13934  1 r8169
              total       used       free     shared    buffers     cached
 Mem:       1788692    1084800     703892      10576     169560     522652
 -/+ buffers/cache:     392588    1396104
 Swap:      1951736          0    1951736
 /usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
 /usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
 /etc/pm/sleep.d/10_grub-common suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
 /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
 /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
 Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
 /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
 /usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
 /usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
 /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
 stop: Unknown instance: 
 /usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
 /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
 /usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
 Kernel modesetting video driver detected, not using quirks.
 /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
 kernel.acpi_video_flags = 0
 /usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
 /etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
 
 Sat Jul  5 08:02:31 BST 2014: performing suspend
 Sat Jul  5 22:46:27 BST 2014: Awake.
 Sat Jul  5 22:46:27 BST 2014: Running hooks for resume
 Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
 /etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
 /usr/lib/pm-utils/sleep.d/99video resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
 /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
 /usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:
 
 /dev/sda:
  setting Advanced Power Management level to 0xfe (254)
  APM_level	= 254
 
 /dev/sdb:
  setting Advanced Power Management level to 0xfe (254)
  APM_level	= 254
 /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
 /usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
 /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
 /usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
 Reloaded unloaded modules.
 /usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
 Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
 /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
 /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.
 
 Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
 /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
 
 Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
 /etc/pm/sleep.d/10_grub-common resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
 /usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
 /usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
 /usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
 /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
 
 Sat Jul  5 22:46:28 BST 2014: Finished.
 Initial commandline parameters: 
 Sat Jul  5 23:31:29 BST 2014: Running hooks for suspend.
 Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
 /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
 /usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
 Linux mediapc 3.13.0-30-generic #54-Ubuntu SMP Mon Jun 9 22:45:01 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
 Module                  Size  Used by
 rfcomm                 69160  0 
 bluetooth             395423  3 rfcomm
 snd_hda_codec_realtek    61438  1 
 snd_hda_intel          52355  0 
 snd_hda_codec         192906  2 snd_hda_codec_realtek,snd_hda_intel
 snd_hwdep              13602  1 snd_hda_codec
 snd_pcm               102099  2 snd_hda_codec,snd_hda_intel
 snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
 snd_seq_midi           13324  0 
 snd_seq_midi_event     14899  1 snd_seq_midi
 snd_rawmidi            30144  1 snd_seq_midi
 snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
 snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
 radeon               1514165  7 
 snd_timer              29482  2 snd_pcm,snd_seq
 ttm                    85115  1 radeon
 kvm                   451511  0 
 drm_kms_helper         53081  1 radeon
 drm                   303102  9 ttm,drm_kms_helper,radeon
 snd                    69238  10 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
 sp5100_tco             13979  0 
 serio_raw              13462  0 
 k10temp                13126  0 
 joydev                 17381  0 
 i2c_algo_bit           13413  1 radeon
 edac_core              62291  0 
 i2c_piix4              22155  0 
 mac_hid                13205  0 
 edac_mce_amd           22617  0 
 soundcore              12680  1 snd
 lp                     17759  0 
 wmi                    19177  0 
 shpchp                 37032  0 
 parport                42348  1 lp
 hid_generic            12548  0 
 usbhid                 52570  0 
 hid                   106148  2 hid_generic,usbhid
 pata_acpi              13038  0 
 raid10                 48128  0 
 raid456                86484  0 
 async_raid6_recov      12984  1 raid456
 async_memcpy           12762  1 raid456
 async_pq               13365  1 raid456
 async_xor              13160  2 async_pq,raid456
 async_tx               13509  5 async_pq,raid456,async_xor,async_memcpy,async_raid6_recov
 xor                    21411  1 async_xor
 psmouse               102222  0 
 raid6_pq               97812  2 async_pq,async_raid6_recov
 raid1                  35530  2 
 raid0                  17842  1 
 multipath              13145  0 
 linear                 12894  0 
 r8169                  67581  0 
 mii                    13934  1 r8169
 ahci                   25819  8 
 libahci                32168  1 ahci
 pata_atiixp            13271  0 
              total       used       free     shared    buffers     cached
 Mem:       1788692    1365780     422912      10520      99728     925796
 -/+ buffers/cache:     340256    1448436
 Swap:      1951736          0    1951736
 /usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
 /usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
 /etc/pm/sleep.d/10_grub-common suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
 /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
 /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
 Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
 /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
 /usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
 /usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
 /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
 stop: Unknown instance: 
 /usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
 /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
 /usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
 Kernel modesetting video driver detected, not using quirks.
 /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
 kernel.acpi_video_flags = 0
 /usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
 /etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
 
 Sat Jul  5 23:31:31 BST 2014: performing suspend
 Tue Jul  8 00:00:52 BST 2014: Awake.
 Tue Jul  8 00:00:52 BST 2014: Running hooks for resume
 Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
 /etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
 /usr/lib/pm-utils/sleep.d/99video resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
 /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
 /usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:
 
 /dev/sda:
  setting Advanced Power Management level to 0xfe (254)
  APM_level	= 254
 
 /dev/sdb:
  setting Advanced Power Management level to 0xfe (254)
  APM_level	= 254
 /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
 /usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
 /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
 /usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
 Reloaded unloaded modules.
 /usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
 Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
 /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
 /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.
 
 Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
 /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
 
 Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
 /etc/pm/sleep.d/10_grub-common resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
 /usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
 /usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
 /usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
 /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
 
 Tue Jul  8 00:00:53 BST 2014: Finished.
 Initial commandline parameters: 
 Tue Jul  8 00:09:56 BST 2014: Running hooks for suspend.
 Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
 /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
 /usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
 Linux mediapc 3.13.0-30-generic #54-Ubuntu SMP Mon Jun 9 22:45:01 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
 Module                  Size  Used by
 rfcomm                 69160  0 
 bluetooth             395423  3 rfcomm
 snd_hda_codec_realtek    61438  1 
 snd_hda_intel          52355  0 
 snd_hda_codec         192906  2 snd_hda_codec_realtek,snd_hda_intel
 snd_hwdep              13602  1 snd_hda_codec
 snd_pcm               102099  2 snd_hda_codec,snd_hda_intel
 snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
 snd_seq_midi           13324  0 
 snd_seq_midi_event     14899  1 snd_seq_midi
 snd_rawmidi            30144  1 snd_seq_midi
 snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
 snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
 radeon               1514165  7 
 snd_timer              29482  2 snd_pcm,snd_seq
 ttm                    85115  1 radeon
 kvm                   451511  0 
 drm_kms_helper         53081  1 radeon
 drm                   303102  9 ttm,drm_kms_helper,radeon
 snd                    69238  10 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
 sp5100_tco             13979  0 
 serio_raw              13462  0 
 k10temp                13126  0 
 joydev                 17381  0 
 i2c_algo_bit           13413  1 radeon
 edac_core              62291  0 
 i2c_piix4              22155  0 
 mac_hid                13205  0 
 edac_mce_amd           22617  0 
 soundcore              12680  1 snd
 lp                     17759  0 
 wmi                    19177  0 
 shpchp                 37032  0 
 parport                42348  1 lp
 hid_generic            12548  0 
 usbhid                 52570  0 
 hid                   106148  2 hid_generic,usbhid
 pata_acpi              13038  0 
 raid10                 48128  0 
 raid456                86484  0 
 async_raid6_recov      12984  1 raid456
 async_memcpy           12762  1 raid456
 async_pq               13365  1 raid456
 async_xor              13160  2 async_pq,raid456
 async_tx               13509  5 async_pq,raid456,async_xor,async_memcpy,async_raid6_recov
 xor                    21411  1 async_xor
 psmouse               102222  0 
 raid6_pq               97812  2 async_pq,async_raid6_recov
 raid1                  35530  2 
 raid0                  17842  1 
 multipath              13145  0 
 linear                 12894  0 
 r8169                  67581  0 
 mii                    13934  1 r8169
 ahci                   25819  8 
 libahci                32168  1 ahci
 pata_atiixp            13271  0 
              total       used       free     shared    buffers     cached
 Mem:       1788692    1382480     406212      10540     107236     928564
 -/+ buffers/cache:     346680    1442012
 Swap:      1951736          0    1951736
 /usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
 /usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
 /etc/pm/sleep.d/10_grub-common suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
 /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
 /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
 Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
 /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
 /usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
 /usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
 /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
 /usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
 /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
 /usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
 Kernel modesetting video driver detected, not using quirks.
 /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
 kernel.acpi_video_flags = 0
 /usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
 /etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
 
 Tue Jul  8 00:09:57 BST 2014: performing suspend
 Wed Jul  9 00:00:52 BST 2014: Awake.
 Wed Jul  9 00:00:52 BST 2014: Running hooks for resume
 Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
 /etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
 /usr/lib/pm-utils/sleep.d/99video resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
 /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
 /usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:
 
 /dev/sda:
  setting Advanced Power Management level to 0xfe (254)
  APM_level	= 254
 
 /dev/sdb:
  setting Advanced Power Management level to 0xfe (254)
  APM_level	= 254
 /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
 /usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
 /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
 /usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
 Reloaded unloaded modules.
 /usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
 Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
 /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
 /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.
 
 Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
 /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
 
 Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
 /etc/pm/sleep.d/10_grub-common resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
 /usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
 /usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
 /usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
 /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
 
 Wed Jul  9 00:00:52 BST 2014: Finished.
 Initial commandline parameters: 
 Wed Jul  9 00:08:40 BST 2014: Running hooks for suspend.
 Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
 /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
 /usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
 Linux mediapc 3.13.0-30-generic #54-Ubuntu SMP Mon Jun 9 22:45:01 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
 Module                  Size  Used by
 rfcomm                 69160  0 
 bluetooth             395423  3 rfcomm
 snd_hda_codec_realtek    61438  1 
 snd_hda_intel          52355  0 
 snd_hda_codec         192906  2 snd_hda_codec_realtek,snd_hda_intel
 snd_hwdep              13602  1 snd_hda_codec
 snd_pcm               102099  2 snd_hda_codec,snd_hda_intel
 snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
 snd_seq_midi           13324  0 
 snd_seq_midi_event     14899  1 snd_seq_midi
 snd_rawmidi            30144  1 snd_seq_midi
 snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
 snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
 radeon               1514165  7 
 snd_timer              29482  2 snd_pcm,snd_seq
 ttm                    85115  1 radeon
 kvm                   451511  0 
 drm_kms_helper         53081  1 radeon
 drm                   303102  9 ttm,drm_kms_helper,radeon
 snd                    69238  10 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
 sp5100_tco             13979  0 
 serio_raw              13462  0 
 k10temp                13126  0 
 joydev                 17381  0 
 i2c_algo_bit           13413  1 radeon
 edac_core              62291  0 
 i2c_piix4              22155  0 
 mac_hid                13205  0 
 edac_mce_amd           22617  0 
 soundcore              12680  1 snd
 lp                     17759  0 
 wmi                    19177  0 
 shpchp                 37032  0 
 parport                42348  1 lp
 hid_generic            12548  0 
 usbhid                 52570  0 
 hid                   106148  2 hid_generic,usbhid
 pata_acpi              13038  0 
 raid10                 48128  0 
 raid456                86484  0 
 async_raid6_recov      12984  1 raid456
 async_memcpy           12762  1 raid456
 async_pq               13365  1 raid456
 async_xor              13160  2 async_pq,raid456
 async_tx               13509  5 async_pq,raid456,async_xor,async_memcpy,async_raid6_recov
 xor                    21411  1 async_xor
 psmouse               102222  0 
 raid6_pq               97812  2 async_pq,async_raid6_recov
 raid1                  35530  2 
 raid0                  17842  1 
 multipath              13145  0 
 linear                 12894  0 
 r8169                  67581  0 
 mii                    13934  1 r8169
 ahci                   25819  8 
 libahci                32168  1 ahci
 pata_atiixp            13271  0 
              total       used       free     shared    buffers     cached
 Mem:       1788692    1398792     389900      10500     115656     949252
 -/+ buffers/cache:     333884    1454808
 Swap:      1951736          0    1951736
 /usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
 /usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
 /etc/pm/sleep.d/10_grub-common suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
 /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
 /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
 Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
 /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
 /usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
 /usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
 /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
 /usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
 /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
 /usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
 Kernel modesetting video driver detected, not using quirks.
 /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
 kernel.acpi_video_flags = 0
 /usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
 /etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
 
 Wed Jul  9 00:08:41 BST 2014: performing suspend
 Wed Jul  9 08:07:08 BST 2014: Awake.
 Wed Jul  9 08:07:08 BST 2014: Running hooks for resume
 Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
 /etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
 /usr/lib/pm-utils/sleep.d/99video resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
 /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
 /usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:
 
 /dev/sda:
  setting Advanced Power Management level to 0xfe (254)
  APM_level	= 254
 
 /dev/sdb:
  setting Advanced Power Management level to 0xfe (254)
  APM_level	= 254
 /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
 /usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
 /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
 /usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
 Reloaded unloaded modules.
 /usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
 Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
 /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
 /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.
 
 Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
 /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
 
 Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
 /etc/pm/sleep.d/10_grub-common resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
 /usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
 /usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
 /usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
 /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
 
 Wed Jul  9 08:07:09 BST 2014: Finished.
 Initial commandline parameters: 
 Wed Jul  9 17:20:40 BST 2014: Running hooks for suspend.
 Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
 /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
 /usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
 Linux mediapc 3.13.0-30-generic #54-Ubuntu SMP Mon Jun 9 22:45:01 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
 Module                  Size  Used by
 rfcomm                 69160  0 
 bluetooth             395423  3 rfcomm
 snd_hda_codec_hdmi     46207  1 
 snd_hda_codec_realtek    61438  1 
 snd_hda_intel          52355  0 
 snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
 snd_hwdep              13602  1 snd_hda_codec
 snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
 snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
 snd_seq_midi           13324  0 
 snd_seq_midi_event     14899  1 snd_seq_midi
 intel_rapl             18773  0 
 snd_rawmidi            30144  1 snd_seq_midi
 snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
 snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
 i915                  783703  5 
 coretemp               13435  0 
 snd_timer              29482  2 snd_pcm,snd_seq
 kvm_intel             143060  0 
 drm_kms_helper         53081  1 i915
 snd                    69238  11 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
 drm                   303102  6 i915,drm_kms_helper
 kvm                   451511  1 kvm_intel
 wmi                    19177  0 
 i2c_algo_bit           13413  1 i915
 soundcore              12680  1 snd
 crct10dif_pclmul       14289  0 
 lp                     17759  0 
 crc32_pclmul           13113  0 
 ghash_clmulni_intel    13216  0 
 joydev                 17381  0 
 serio_raw              13462  0 
 cryptd                 20359  1 ghash_clmulni_intel
 mac_hid                13205  0 
 video                  19476  1 i915
 parport                42348  1 lp
 hid_generic            12548  0 
 usbhid                 52570  0 
 hid                   106148  2 hid_generic,usbhid
 raid10                 48128  0 
 raid456                86484  0 
 async_raid6_recov      12984  1 raid456
 async_memcpy           12762  1 raid456
 async_pq               13365  1 raid456
 async_xor              13160  2 async_pq,raid456
 async_tx               13509  5 async_pq,raid456,async_xor,async_memcpy,async_raid6_recov
 xor                    21411  1 async_xor
 raid6_pq               97812  2 async_pq,async_raid6_recov
 psmouse               102222  0 
 r8169                  67581  0 
 raid1                  35530  2 
 mii                    13934  1 r8169
 ahci                   25819  8 
 raid0                  17842  1 
 libahci                32168  1 ahci
 multipath              13145  0 
 linear                 12894  0 
              total       used       free     shared    buffers     cached
 Mem:       3490244     737344    2752900      97624      85724     389836
 -/+ buffers/cache:     261784    3228460
 Swap:      1951736          0    1951736
 /usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
 /usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
 /etc/pm/sleep.d/10_grub-common suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
 /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
 /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
 Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
 /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
 /usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
 /usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
 /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
 /usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
 /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
 /usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
 Kernel modesetting video driver detected, not using quirks.
 /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
 kernel.acpi_video_flags = 0
 /usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
 /etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
 
 Wed Jul  9 17:20:40 BST 2014: performing suspend
 Initial commandline parameters: 
 Wed Jul  9 13:21:30 BST 2014: Running hooks for suspend.
 Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
 /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
 /usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
 Linux mediapc 3.13.0-30-generic #55-Ubuntu SMP Fri Jul 4 21:40:53 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
 Module                  Size  Used by
 rfcomm                 69160  0 
 bluetooth             395423  3 rfcomm
 snd_hda_codec_hdmi     46207  1 
 snd_hda_codec_realtek    61438  1 
 intel_rapl             18773  0 
 coretemp               13435  0 
 snd_hda_intel          52355  0 
 snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
 snd_hwdep              13602  1 snd_hda_codec
 snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
 snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
 snd_seq_midi           13324  0 
 snd_seq_midi_event     14899  1 snd_seq_midi
 snd_rawmidi            30144  1 snd_seq_midi
 snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
 snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
 snd_timer              29482  2 snd_pcm,snd_seq
 kvm_intel             143060  0 
 kvm                   451511  1 kvm_intel
 snd                    69238  11 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
 crct10dif_pclmul       14289  0 
 crc32_pclmul           13113  0 
 ghash_clmulni_intel    13216  0 
 soundcore              12680  1 snd
 i915                  783703  5 
 cryptd                 20359  1 ghash_clmulni_intel
 drm_kms_helper         53081  1 i915
 drm                   303102  6 i915,drm_kms_helper
 i2c_algo_bit           13413  1 i915
 joydev                 17381  0 
 mac_hid                13205  0 
 wmi                    19177  0 
 serio_raw              13462  0 
 video                  19476  1 i915
 lp                     17759  0 
 parport                42348  1 lp
 hid_generic            12548  0 
 usbhid                 52570  0 
 hid                   106148  2 hid_generic,usbhid
 raid10                 48128  0 
 raid456                86484  0 
 async_raid6_recov      12984  1 raid456
 async_memcpy           12762  1 raid456
 async_pq               13365  1 raid456
 async_xor              13160  2 async_pq,raid456
 async_tx               13509  5 async_pq,raid456,async_xor,async_memcpy,async_raid6_recov
 xor                    21411  1 async_xor
 raid6_pq               97812  2 async_pq,async_raid6_recov
 psmouse               102222  0 
 r8169                  67581  0 
 raid1                  35530  2 
 mii                    13934  1 r8169
 ahci                   25819  8 
 raid0                  17842  1 
 libahci                32168  1 ahci
 multipath              13145  0 
 linear                 12894  0 
              total       used       free     shared    buffers     cached
 Mem:       3490244     705960    2784284      97392      33992     376768
 -/+ buffers/cache:     295200    3195044
 Swap:      1951736          0    1951736
 /usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
 /usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
 /etc/pm/sleep.d/10_grub-common suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
 /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
 /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
 Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
 /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
 /usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
 /usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
 /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
 stop: Unknown instance: 
 /usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
 /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
 /usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
 Kernel modesetting video driver detected, not using quirks.
 /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
 kernel.acpi_video_flags = 0
 /usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
 /etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
 
 Wed Jul  9 13:21:30 BST 2014: performing suspend
 Wed Jul  9 13:22:01 BST 2014: Awake.
 Wed Jul  9 13:22:01 BST 2014: Running hooks for resume
 Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
 /etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
 /usr/lib/pm-utils/sleep.d/99video resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
 /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
 /usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:
 
 /dev/sda:
  setting Advanced Power Management level to 0xfe (254)
  APM_level	= 254
 
 /dev/sdb:
  setting Advanced Power Management level to 0xfe (254)
  APM_level	= 254
 /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
 /usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
 /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
 /usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
 Reloaded unloaded modules.
 /usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
 Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
 /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
 /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.
 
 Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
 /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
 
 Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
 /etc/pm/sleep.d/10_grub-common resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
 /usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
 /usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
 /usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
 /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
 
 Wed Jul  9 13:22:02 BST 2014: Finished.
 Initial commandline parameters: 
 Wed Jul  9 13:22:16 BST 2014: Running hooks for suspend.
 Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
 /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
 /usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
 Linux mediapc 3.13.0-30-generic #55-Ubuntu SMP Fri Jul 4 21:40:53 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
 Module                  Size  Used by
 rfcomm                 69160  0 
 bluetooth             395423  3 rfcomm
 snd_hda_codec_hdmi     46207  1 
 snd_hda_codec_realtek    61438  1 
 intel_rapl             18773  0 
 coretemp               13435  0 
 snd_hda_intel          52355  0 
 snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
 snd_hwdep              13602  1 snd_hda_codec
 snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
 snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
 snd_seq_midi           13324  0 
 snd_seq_midi_event     14899  1 snd_seq_midi
 snd_rawmidi            30144  1 snd_seq_midi
 snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
 snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
 snd_timer              29482  2 snd_pcm,snd_seq
 kvm_intel             143060  0 
 kvm                   451511  1 kvm_intel
 snd                    69238  11 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
 crct10dif_pclmul       14289  0 
 crc32_pclmul           13113  0 
 ghash_clmulni_intel    13216  0 
 soundcore              12680  1 snd
 i915                  783703  5 
 cryptd                 20359  1 ghash_clmulni_intel
 drm_kms_helper         53081  1 i915
 drm                   303102  6 i915,drm_kms_helper
 i2c_algo_bit           13413  1 i915
 joydev                 17381  0 
 mac_hid                13205  0 
 wmi                    19177  0 
 serio_raw              13462  0 
 video                  19476  1 i915
 lp                     17759  0 
 parport                42348  1 lp
 hid_generic            12548  0 
 usbhid                 52570  0 
 hid                   106148  2 hid_generic,usbhid
 raid10                 48128  0 
 raid456                86484  0 
 async_raid6_recov      12984  1 raid456
 async_memcpy           12762  1 raid456
 async_pq               13365  1 raid456
 async_xor              13160  2 async_pq,raid456
 async_tx               13509  5 async_pq,raid456,async_xor,async_memcpy,async_raid6_recov
 xor                    21411  1 async_xor
 raid6_pq               97812  2 async_pq,async_raid6_recov
 psmouse               102222  0 
 r8169                  67581  0 
 raid1                  35530  2 
 mii                    13934  1 r8169
 ahci                   25819  8 
 raid0                  17842  1 
 libahci                32168  1 ahci
 multipath              13145  0 
 linear                 12894  0 
              total       used       free     shared    buffers     cached
 Mem:       3490244     709816    2780428     104996      34032     384580
 -/+ buffers/cache:     291204    3199040
 Swap:      1951736          0    1951736
 /usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
 /usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
 /etc/pm/sleep.d/10_grub-common suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
 /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
 /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
 Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
 /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
 /usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
 /usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
 /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
 stop: Unknown instance: 
 /usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
 /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
 /usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
 Kernel modesetting video driver detected, not using quirks.
 /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
 kernel.acpi_video_flags = 0
 /usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
 /etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
 
 Wed Jul  9 13:22:17 BST 2014: performing suspend
 Wed Jul  9 13:22:33 BST 2014: Awake.
 Wed Jul  9 13:22:33 BST 2014: Running hooks for resume
 Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
 /etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
 /usr/lib/pm-utils/sleep.d/99video resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
 /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
 /usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:
 
 /dev/sda:
  setting Advanced Power Management level to 0xfe (254)
  APM_level	= 254
 
 /dev/sdb:
  setting Advanced Power Management level to 0xfe (254)
  APM_level	= 254
 /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
 /usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
 /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
 /usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
 Reloaded unloaded modules.
 /usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
 Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
 /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
 /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.
 
 Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
 /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
 
 Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
 /etc/pm/sleep.d/10_grub-common resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
 /usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
 /usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
 /usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
 /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
 
 Wed Jul  9 13:22:34 BST 2014: Finished.
 Initial commandline parameters: 
 Wed Jul  9 13:22:50 BST 2014: Running hooks for suspend.
 Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
 /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
 /usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
 Linux mediapc 3.13.0-30-generic #55-Ubuntu SMP Fri Jul 4 21:40:53 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
 Module                  Size  Used by
 rfcomm                 69160  0 
 bluetooth             395423  3 rfcomm
 snd_hda_codec_hdmi     46207  1 
 snd_hda_codec_realtek    61438  1 
 intel_rapl             18773  0 
 coretemp               13435  0 
 snd_hda_intel          52355  0 
 snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
 snd_hwdep              13602  1 snd_hda_codec
 snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
 snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
 snd_seq_midi           13324  0 
 snd_seq_midi_event     14899  1 snd_seq_midi
 snd_rawmidi            30144  1 snd_seq_midi
 snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
 snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
 snd_timer              29482  2 snd_pcm,snd_seq
 kvm_intel             143060  0 
 kvm                   451511  1 kvm_intel
 snd                    69238  11 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
 crct10dif_pclmul       14289  0 
 crc32_pclmul           13113  0 
 ghash_clmulni_intel    13216  0 
 soundcore              12680  1 snd
 i915                  783703  5 
 cryptd                 20359  1 ghash_clmulni_intel
 drm_kms_helper         53081  1 i915
 drm                   303102  6 i915,drm_kms_helper
 i2c_algo_bit           13413  1 i915
 joydev                 17381  0 
 mac_hid                13205  0 
 wmi                    19177  0 
 serio_raw              13462  0 
 video                  19476  1 i915
 lp                     17759  0 
 parport                42348  1 lp
 hid_generic            12548  0 
 usbhid                 52570  0 
 hid                   106148  2 hid_generic,usbhid
 raid10                 48128  0 
 raid456                86484  0 
 async_raid6_recov      12984  1 raid456
 async_memcpy           12762  1 raid456
 async_pq               13365  1 raid456
 async_xor              13160  2 async_pq,raid456
 async_tx               13509  5 async_pq,raid456,async_xor,async_memcpy,async_raid6_recov
 xor                    21411  1 async_xor
 raid6_pq               97812  2 async_pq,async_raid6_recov
 psmouse               102222  0 
 r8169                  67581  0 
 raid1                  35530  2 
 mii                    13934  1 r8169
 ahci                   25819  8 
 raid0                  17842  1 
 libahci                32168  1 ahci
 multipath              13145  0 
 linear                 12894  0 
              total       used       free     shared    buffers     cached
 Mem:       3490244     725932    2764312     105704      34088     385316
 -/+ buffers/cache:     306528    3183716
 Swap:      1951736          0    1951736
 /usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
 /usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
 /etc/pm/sleep.d/10_grub-common suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
 /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
 /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
 Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
 /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
 /usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
 /usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
 /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
 stop: Unknown instance: 
 /usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
 /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
 /usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
 Kernel modesetting video driver detected, not using quirks.
 /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
 kernel.acpi_video_flags = 0
 /usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
 /etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
 
 Wed Jul  9 13:22:50 BST 2014: performing suspend
 Wed Jul  9 13:23:05 BST 2014: Awake.
 Wed Jul  9 13:23:05 BST 2014: Running hooks for resume
 Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
 /etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
 /usr/lib/pm-utils/sleep.d/99video resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
 /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
 /usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:
 
 /dev/sda:
  setting Advanced Power Management level to 0xfe (254)
  APM_level	= 254
 
 /dev/sdb:
  setting Advanced Power Management level to 0xfe (254)
  APM_level	= 254
 /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
 /usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
 /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
 /usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
 Reloaded unloaded modules.
 /usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
 Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
 /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
 /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.
 
 Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
 /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
 
 Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
 /etc/pm/sleep.d/10_grub-common resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
 /usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
 /usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
 /usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
 /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
 
 Wed Jul  9 13:23:06 BST 2014: Finished.
 Initial commandline parameters: 
 Wed Jul  9 14:33:49 BST 2014: Running hooks for suspend.
 Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
 /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
 /usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
 Linux mediapc 3.13.0-30-generic #55-Ubuntu SMP Fri Jul 4 21:40:53 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
 Module                  Size  Used by
 rfcomm                 69160  0 
 bluetooth             395423  3 rfcomm
 snd_hda_codec_hdmi     46207  1 
 snd_hda_codec_realtek    61438  1 
 intel_rapl             18773  0 
 coretemp               13435  0 
 snd_hda_intel          52355  0 
 snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
 snd_hwdep              13602  1 snd_hda_codec
 snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
 snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
 snd_seq_midi           13324  0 
 snd_seq_midi_event     14899  1 snd_seq_midi
 snd_rawmidi            30144  1 snd_seq_midi
 snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
 snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
 snd_timer              29482  2 snd_pcm,snd_seq
 kvm_intel             143060  0 
 kvm                   451511  1 kvm_intel
 snd                    69238  11 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
 crct10dif_pclmul       14289  0 
 crc32_pclmul           13113  0 
 ghash_clmulni_intel    13216  0 
 soundcore              12680  1 snd
 i915                  783703  5 
 cryptd                 20359  1 ghash_clmulni_intel
 drm_kms_helper         53081  1 i915
 drm                   303102  6 i915,drm_kms_helper
 i2c_algo_bit           13413  1 i915
 joydev                 17381  0 
 mac_hid                13205  0 
 wmi                    19177  0 
 serio_raw              13462  0 
 video                  19476  1 i915
 lp                     17759  0 
 parport                42348  1 lp
 hid_generic            12548  0 
 usbhid                 52570  0 
 hid                   106148  2 hid_generic,usbhid
 raid10                 48128  0 
 raid456                86484  0 
 async_raid6_recov      12984  1 raid456
 async_memcpy           12762  1 raid456
 async_pq               13365  1 raid456
 async_xor              13160  2 async_pq,raid456
 async_tx               13509  5 async_pq,raid456,async_xor,async_memcpy,async_raid6_recov
 xor                    21411  1 async_xor
 raid6_pq               97812  2 async_pq,async_raid6_recov
 psmouse               102222  0 
 r8169                  67581  0 
 raid1                  35530  2 
 mii                    13934  1 r8169
 ahci                   25819  8 
 raid0                  17842  1 
 libahci                32168  1 ahci
 multipath              13145  0 
 linear                 12894  0 
              total       used       free     shared    buffers     cached
 Mem:       3490244     921724    2568520      99876      44556     560752
 -/+ buffers/cache:     316416    3173828
 Swap:      1951736          0    1951736
 /usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
 /usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
 /etc/pm/sleep.d/10_grub-common suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
 /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
 /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
 Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
 /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
 /usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
 /usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
 /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
 stop: Unknown instance: 
 /usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
 /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
 /usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
 Kernel modesetting video driver detected, not using quirks.
 /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
 kernel.acpi_video_flags = 0
 /usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
 /etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/xboxdrv suspend suspend:
 xboxdrv stop/waiting
 /etc/pm/sleep.d/xboxdrv suspend suspend: success.
 
 Wed Jul  9 14:33:50 BST 2014: performing suspend
 Wed Jul  9 18:16:11 BST 2014: Awake.
 Wed Jul  9 18:16:11 BST 2014: Running hooks for resume
 Running hook /etc/pm/sleep.d/xboxdrv resume suspend:
 stop: Unknown instance: 
 xboxdrv start/running, process 26423
 /etc/pm/sleep.d/xboxdrv resume suspend: success.
 
 Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
 /etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
 /usr/lib/pm-utils/sleep.d/99video resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
 /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
 /usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:
 
 /dev/sda:
  setting Advanced Power Management level to 0xfe (254)
  APM_level	= 254
 
 /dev/sdb:
  setting Advanced Power Management level to 0xfe (254)
  APM_level	= 254
 /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
 /usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
 /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
 /usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
 Reloaded unloaded modules.
 /usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
 Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
 /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
 /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.
 
 Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
 /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
 
 Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
 /etc/pm/sleep.d/10_grub-common resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
 /usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
 /usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
 /usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
 /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
 
 Wed Jul  9 18:16:12 BST 2014: Finished.
 Initial commandline parameters: 
 Wed Jul  9 18:16:39 BST 2014: Running hooks for suspend.
 Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
 /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
 /usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
 Linux mediapc 3.13.0-30-generic #55-Ubuntu SMP Fri Jul 4 21:40:53 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
 Module                  Size  Used by
 rfcomm                 69160  0 
 bluetooth             395423  3 rfcomm
 snd_hda_codec_hdmi     46207  1 
 snd_hda_codec_realtek    61438  1 
 intel_rapl             18773  0 
 coretemp               13435  0 
 snd_hda_intel          52355  0 
 snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
 snd_hwdep              13602  1 snd_hda_codec
 snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
 snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
 snd_seq_midi           13324  0 
 snd_seq_midi_event     14899  1 snd_seq_midi
 snd_rawmidi            30144  1 snd_seq_midi
 snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
 snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
 snd_timer              29482  2 snd_pcm,snd_seq
 kvm_intel             143060  0 
 kvm                   451511  1 kvm_intel
 snd                    69238  11 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
 crct10dif_pclmul       14289  0 
 crc32_pclmul           13113  0 
 ghash_clmulni_intel    13216  0 
 soundcore              12680  1 snd
 i915                  783703  5 
 cryptd                 20359  1 ghash_clmulni_intel
 drm_kms_helper         53081  1 i915
 drm                   303102  6 i915,drm_kms_helper
 i2c_algo_bit           13413  1 i915
 joydev                 17381  0 
 mac_hid                13205  0 
 wmi                    19177  0 
 serio_raw              13462  0 
 video                  19476  1 i915
 lp                     17759  0 
 parport                42348  1 lp
 hid_generic            12548  0 
 usbhid                 52570  0 
 hid                   106148  2 hid_generic,usbhid
 raid10                 48128  0 
 raid456                86484  0 
 async_raid6_recov      12984  1 raid456
 async_memcpy           12762  1 raid456
 async_pq               13365  1 raid456
 async_xor              13160  2 async_pq,raid456
 async_tx               13509  5 async_pq,raid456,async_xor,async_memcpy,async_raid6_recov
 xor                    21411  1 async_xor
 raid6_pq               97812  2 async_pq,async_raid6_recov
 psmouse               102222  0 
 r8169                  67581  0 
 raid1                  35530  2 
 mii                    13934  1 r8169
 ahci                   25819  8 
 raid0                  17842  1 
 libahci                32168  1 ahci
 multipath              13145  0 
 linear                 12894  0 
              total       used       free     shared    buffers     cached
 Mem:       3490244     941440    2548804     107608      45756     575624
 -/+ buffers/cache:     320060    3170184
 Swap:      1951736          0    1951736
 /usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
 /usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
 /etc/pm/sleep.d/10_grub-common suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
 /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
 /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
 Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
 /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
 /usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
 /usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
 /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
 stop: Unknown instance: 
 /usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
 /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
 /usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
 Kernel modesetting video driver detected, not using quirks.
 /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
 kernel.acpi_video_flags = 0
 /usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
 /etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/xboxdrv suspend suspend:
 xboxdrv stop/waiting
 /etc/pm/sleep.d/xboxdrv suspend suspend: success.
 
 Wed Jul  9 18:16:39 BST 2014: performing suspend
 Wed Jul  9 18:16:57 BST 2014: Awake.
 Wed Jul  9 18:16:57 BST 2014: Running hooks for resume
 Running hook /etc/pm/sleep.d/xboxdrv resume suspend:
 stop: Unknown instance: 
 xboxdrv start/running, process 27361
 /etc/pm/sleep.d/xboxdrv resume suspend: success.
 
 Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
 /etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
 /usr/lib/pm-utils/sleep.d/99video resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
 /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
 /usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:
 
 /dev/sda:
  setting Advanced Power Management level to 0xfe (254)
  APM_level	= 254
 
 /dev/sdb:
  setting Advanced Power Management level to 0xfe (254)
  APM_level	= 254
 /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
 /usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
 /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
 /usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
 Reloaded unloaded modules.
 /usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
 Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
 /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
 /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.
 
 Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
 /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
 
 Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
 /etc/pm/sleep.d/10_grub-common resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
 /usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
 /usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
 /usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
 /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
 
 Wed Jul  9 18:16:58 BST 2014: Finished.
 Initial commandline parameters: 
 Wed Jul  9 18:17:05 BST 2014: Running hooks for suspend.
 Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
 /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
 /usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
 Linux mediapc 3.13.0-30-generic #55-Ubuntu SMP Fri Jul 4 21:40:53 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
 Module                  Size  Used by
 rfcomm                 69160  0 
 bluetooth             395423  3 rfcomm
 snd_hda_codec_hdmi     46207  1 
 snd_hda_codec_realtek    61438  1 
 intel_rapl             18773  0 
 coretemp               13435  0 
 snd_hda_intel          52355  0 
 snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
 snd_hwdep              13602  1 snd_hda_codec
 snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
 snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
 snd_seq_midi           13324  0 
 snd_seq_midi_event     14899  1 snd_seq_midi
 snd_rawmidi            30144  1 snd_seq_midi
 snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
 snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
 snd_timer              29482  2 snd_pcm,snd_seq
 kvm_intel             143060  0 
 kvm                   451511  1 kvm_intel
 snd                    69238  11 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
 crct10dif_pclmul       14289  0 
 crc32_pclmul           13113  0 
 ghash_clmulni_intel    13216  0 
 soundcore              12680  1 snd
 i915                  783703  5 
 cryptd                 20359  1 ghash_clmulni_intel
 drm_kms_helper         53081  1 i915
 drm                   303102  6 i915,drm_kms_helper
 i2c_algo_bit           13413  1 i915
 joydev                 17381  0 
 mac_hid                13205  0 
 wmi                    19177  0 
 serio_raw              13462  0 
 video                  19476  1 i915
 lp                     17759  0 
 parport                42348  1 lp
 hid_generic            12548  0 
 usbhid                 52570  0 
 hid                   106148  2 hid_generic,usbhid
 raid10                 48128  0 
 raid456                86484  0 
 async_raid6_recov      12984  1 raid456
 async_memcpy           12762  1 raid456
 async_pq               13365  1 raid456
 async_xor              13160  2 async_pq,raid456
 async_tx               13509  5 async_pq,raid456,async_xor,async_memcpy,async_raid6_recov
 xor                    21411  1 async_xor
 raid6_pq               97812  2 async_pq,async_raid6_recov
 psmouse               102222  0 
 r8169                  67581  0 
 raid1                  35530  2 
 mii                    13934  1 r8169
 ahci                   25819  8 
 raid0                  17842  1 
 libahci                32168  1 ahci
 multipath              13145  0 
 linear                 12894  0 
              total       used       free     shared    buffers     cached
 Mem:       3490244     948664    2541580     107932      45804     575980
 -/+ buffers/cache:     326880    3163364
 Swap:      1951736          0    1951736
 /usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
 /usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
 /etc/pm/sleep.d/10_grub-common suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
 /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
 /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
 Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
 /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
 /usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
 /usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
 /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
 stop: Unknown instance: 
 /usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
 /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
 /usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
 Kernel modesetting video driver detected, not using quirks.
 /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
 kernel.acpi_video_flags = 0
 /usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
 /etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/xboxdrv suspend suspend:
 xboxdrv stop/waiting
 /etc/pm/sleep.d/xboxdrv suspend suspend: success.
 
 Wed Jul  9 18:17:05 BST 2014: performing suspend
 Initial commandline parameters: 
 Wed Jul  9 18:25:39 BST 2014: Running hooks for suspend.
 Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
 /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
 /usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
 Linux mediapc 3.13.0-30-generic #55-Ubuntu SMP Fri Jul 4 21:40:53 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
 Module                  Size  Used by
 rfcomm                 69160  0 
 bluetooth             395423  3 rfcomm
 snd_hda_codec_hdmi     46207  1 
 snd_hda_codec_realtek    61438  1 
 intel_rapl             18773  0 
 coretemp               13435  0 
 snd_hda_intel          52355  0 
 snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
 snd_hwdep              13602  1 snd_hda_codec
 snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
 snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
 kvm_intel             143060  0 
 snd_seq_midi           13324  0 
 snd_seq_midi_event     14899  1 snd_seq_midi
 kvm                   451511  1 kvm_intel
 snd_rawmidi            30144  1 snd_seq_midi
 snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
 crct10dif_pclmul       14289  0 
 crc32_pclmul           13113  0 
 ghash_clmulni_intel    13216  0 
 snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
 i915                  783703  8 
 snd_timer              29482  2 snd_pcm,snd_seq
 cryptd                 20359  1 ghash_clmulni_intel
 snd                    69238  11 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
 wmi                    19177  0 
 drm_kms_helper         53081  1 i915
 drm                   303102  9 i915,drm_kms_helper
 soundcore              12680  1 snd
 joydev                 17381  0 
 serio_raw              13462  0 
 i2c_algo_bit           13413  1 i915
 mac_hid                13205  0 
 video                  19476  1 i915
 lp                     17759  0 
 parport                42348  1 lp
 hid_generic            12548  0 
 usbhid                 52570  0 
 hid                   106148  2 hid_generic,usbhid
 raid10                 48128  0 
 raid456                86484  0 
 async_raid6_recov      12984  1 raid456
 async_memcpy           12762  1 raid456
 async_pq               13365  1 raid456
 async_xor              13160  2 async_pq,raid456
 async_tx               13509  5 async_pq,raid456,async_xor,async_memcpy,async_raid6_recov
 xor                    21411  1 async_xor
 raid6_pq               97812  2 async_pq,async_raid6_recov
 psmouse               102222  0 
 raid1                  35530  2 
 r8169                  67581  0 
 ahci                   25819  8 
 mii                    13934  1 r8169
 libahci                32168  1 ahci
 raid0                  17842  1 
 multipath              13145  0 
 linear                 12894  0 
              total       used       free     shared    buffers     cached
 Mem:       3490244     806244    2684000     109904      53336     456780
 -/+ buffers/cache:     296128    3194116
 Swap:      1951736          0    1951736
 /usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
 /usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
 /etc/pm/sleep.d/10_grub-common suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
 /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
 /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
 Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
 /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
 /usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
 /usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
 /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
 stop: Unknown instance: 
 /usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
 /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
 /usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
 Kernel modesetting video driver detected, not using quirks.
 /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
 kernel.acpi_video_flags = 0
 /usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
 /etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/xboxdrv suspend suspend:
 xboxdrv stop/waiting
 /etc/pm/sleep.d/xboxdrv suspend suspend: success.
 
 Wed Jul  9 18:25:40 BST 2014: performing suspend
 Wed Jul  9 18:25:57 BST 2014: Awake.
 Wed Jul  9 18:25:57 BST 2014: Running hooks for resume
 Running hook /etc/pm/sleep.d/xboxdrv resume suspend:
 stop: Unknown instance: 
 xboxdrv start/running, process 3747
 /etc/pm/sleep.d/xboxdrv resume suspend: success.
 
 Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
 /etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
 /usr/lib/pm-utils/sleep.d/99video resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
 /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
 /usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:
 
 /dev/sda:
  setting Advanced Power Management level to 0xfe (254)
  APM_level	= 254
 
 /dev/sdb:
  setting Advanced Power Management level to 0xfe (254)
  APM_level	= 254
 /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
 /usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
 /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
 /usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
 Reloaded unloaded modules.
 /usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
 Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
 /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
 /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.
 
 Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
 /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
 
 Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
 /etc/pm/sleep.d/10_grub-common resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
 /usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
 /usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
 /usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
 /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
 
 Wed Jul  9 18:25:58 BST 2014: Finished.
 Initial commandline parameters: 
 Wed Jul  9 18:32:25 BST 2014: Running hooks for suspend.
 Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
 /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
 /usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
 Linux mediapc 3.13.0-30-generic #55-Ubuntu SMP Fri Jul 4 21:40:53 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
 Module                  Size  Used by
 rfcomm                 69160  0 
 bluetooth             395423  3 rfcomm
 snd_hda_codec_hdmi     46207  1 
 snd_hda_codec_realtek    61438  1 
 intel_rapl             18773  0 
 coretemp               13435  0 
 snd_hda_intel          52355  0 
 snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
 snd_hwdep              13602  1 snd_hda_codec
 snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
 snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
 kvm_intel             143060  0 
 snd_seq_midi           13324  0 
 snd_seq_midi_event     14899  1 snd_seq_midi
 kvm                   451511  1 kvm_intel
 snd_rawmidi            30144  1 snd_seq_midi
 snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
 crct10dif_pclmul       14289  0 
 crc32_pclmul           13113  0 
 ghash_clmulni_intel    13216  0 
 snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
 i915                  783703  8 
 snd_timer              29482  2 snd_pcm,snd_seq
 cryptd                 20359  1 ghash_clmulni_intel
 snd                    69238  11 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
 wmi                    19177  0 
 drm_kms_helper         53081  1 i915
 drm                   303102  9 i915,drm_kms_helper
 soundcore              12680  1 snd
 joydev                 17381  0 
 serio_raw              13462  0 
 i2c_algo_bit           13413  1 i915
 mac_hid                13205  0 
 video                  19476  1 i915
 lp                     17759  0 
 parport                42348  1 lp
 hid_generic            12548  0 
 usbhid                 52570  0 
 hid                   106148  2 hid_generic,usbhid
 raid10                 48128  0 
 raid456                86484  0 
 async_raid6_recov      12984  1 raid456
 async_memcpy           12762  1 raid456
 async_pq               13365  1 raid456
 async_xor              13160  2 async_pq,raid456
 async_tx               13509  5 async_pq,raid456,async_xor,async_memcpy,async_raid6_recov
 xor                    21411  1 async_xor
 raid6_pq               97812  2 async_pq,async_raid6_recov
 psmouse               102222  0 
 raid1                  35530  2 
 r8169                  67581  0 
 ahci                   25819  8 
 mii                    13934  1 r8169
 libahci                32168  1 ahci
 raid0                  17842  1 
 multipath              13145  0 
 linear                 12894  0 
              total       used       free     shared    buffers     cached
 Mem:       3490244     805492    2684752     108244      53408     455928
 -/+ buffers/cache:     296156    3194088
 Swap:      1951736          0    1951736
 /usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
 /usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
 /etc/pm/sleep.d/10_grub-common suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
 /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
 /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
 Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
 /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
 /usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
 /usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
 /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
 stop: Unknown instance: 
 /usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
 /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
 /usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
 Kernel modesetting video driver detected, not using quirks.
 /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
 kernel.acpi_video_flags = 0
 /usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
 /etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/xboxdrv suspend suspend:
 xboxdrv stop/waiting
 /etc/pm/sleep.d/xboxdrv suspend suspend: success.
 
 Wed Jul  9 18:32:25 BST 2014: performing suspend
 Initial commandline parameters: 
 Wed Jul  9 23:54:40 BST 2014: Running hooks for suspend.
 Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
 /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
 /usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
 Linux mediapc 3.13.0-30-generic #55-Ubuntu SMP Fri Jul 4 21:40:53 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
 Module                  Size  Used by
 rfcomm                 69160  0 
 bluetooth             395423  3 rfcomm
 snd_hda_codec_hdmi     46207  1 
 snd_hda_codec_realtek    61438  1 
 snd_hda_intel          52355  0 
 snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
 snd_hwdep              13602  1 snd_hda_codec
 snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
 snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
 snd_seq_midi           13324  0 
 snd_seq_midi_event     14899  1 snd_seq_midi
 snd_rawmidi            30144  1 snd_seq_midi
 intel_rapl             18773  0 
 coretemp               13435  0 
 snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
 kvm_intel             143060  0 
 kvm                   451511  1 kvm_intel
 crct10dif_pclmul       14289  0 
 crc32_pclmul           13113  0 
 i915                  783703  5 
 ghash_clmulni_intel    13216  0 
 cryptd                 20359  1 ghash_clmulni_intel
 snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
 snd_timer              29482  2 snd_pcm,snd_seq
 serio_raw              13462  0 
 drm_kms_helper         53081  1 i915
 snd                    69238  11 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
 joydev                 17381  0 
 soundcore              12680  1 snd
 drm                   303102  6 i915,drm_kms_helper
 i2c_algo_bit           13413  1 i915
 wmi                    19177  0 
 video                  19476  1 i915
 mac_hid                13205  0 
 lp                     17759  0 
 parport                42348  1 lp
 hid_generic            12548  0 
 usbhid                 52570  0 
 hid                   106148  2 hid_generic,usbhid
 raid10                 48128  0 
 raid456                86484  0 
 async_raid6_recov      12984  1 raid456
 async_memcpy           12762  1 raid456
 async_pq               13365  1 raid456
 async_xor              13160  2 async_pq,raid456
 async_tx               13509  5 async_pq,raid456,async_xor,async_memcpy,async_raid6_recov
 xor                    21411  1 async_xor
 psmouse               102222  0 
 raid6_pq               97812  2 async_pq,async_raid6_recov
 r8169                  67581  0 
 raid1                  35530  2 
 mii                    13934  1 r8169
 ahci                   25819  8 
 raid0                  17842  1 
 libahci                32168  1 ahci
 multipath              13145  0 
 linear                 12894  0 
              total       used       free     shared    buffers     cached
 Mem:       3490244     786936    2703308      98440      95256     393676
 -/+ buffers/cache:     298004    3192240
 Swap:      1951736          0    1951736
 /usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
 /usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
 /etc/pm/sleep.d/10_grub-common suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
 /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
 /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
 /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
 /usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
 /usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
 /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
 stop: Unknown instance: 
 /usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
 /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
 /usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
 Kernel modesetting video driver detected, not using quirks.
 /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
 kernel.acpi_video_flags = 0
 /usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
 /etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/xboxdrv suspend suspend:
 xboxdrv stop/waiting
 /etc/pm/sleep.d/xboxdrv suspend suspend: success.
 
 Wed Jul  9 23:54:41 BST 2014: performing suspend
Tags: resume suspend
Uname: Linux 3.13.0-30-generic x86_64
UserGroups: 

```

I'm using powernap to automatically suspend when the system is idle. I've added the [patch to detect when RAID is rebuilding and prevent suspend.]("https://bugs.launchpad.net/powernap/+bug/1280507")
[B]/etc/powernap/config
[/B]```
[powernap]
# This is the configuration file for PowerNap.
# See powernap(1) for more information.


# This file is Python syntax, and will be sourced by the powernap daemon
# on start. To enact changes to this configuration, restart the daemon.
# Example:
#   sudo service powernap restart


# The ACTION_METHOD variable determines what action to take.
# The possible actions are:
# 0 - powersave
# 1 - suspend
# 2 - hibernate
# 3 - poweroff
# 4 - best-effort
# The default mode of operation is powersave. This method will use the
# "pm-powersave" command and will execute hooks locate in "/etc/pm/power.d" and
# "/usr/lib/pm-utils/power.d".
# The best-effort method, witll first, it will try a user-defined script
# at "/etc/powernap/action", or suspend, hibernate, poweroff.
ACTION_METHOD = 0


# Number of seconds that all monitors must have no activity or must be absent.
# The default is an absence period of 30 seconds.
# Example:
#   ABSENT_SECONDS = 30
ABSENT_SECONDS = 30


# Grace period, after (ABSENT_SECONDS - GRACE_SECONDS) have elapsed with all of
# the Monitors with absent activity, the system will send a Wall message for an
# administrator to warn that the system will perform the "/usr/sbin/powernap"
# action in GRACE_SECONDS.
# The default grace period is 6 seconds.
# Example:
#   GRACE_SECONDS = 6
GRACE_SECONDS = 6


# The powernap daemon will wake every INTERVAL_SECONDS and check for activity
# to all of the monitors.  Lower values of INTERVAL_SECONDS will provide
# more detailed process monitoring but will consume more system resources.
# Higher values of INTERVAL_SECONDS will consume less system resources, but
# might miss activity that execute for less than INTERVAL_SECONDS.
# The minimum runtime of any monitor should not be less than INTERVAL_SECONDS.
# The default interval is 1 second.
# Example:
#   INTERVAL_SECONDS = 1
INTERVAL_SECONDS = 1


# The powernap daemon will issue a warning message to the console whenever it
# has entered into GRACE period. This warning message will warn the user that
# it is about to perform an ACTION.
# This warning message is done using the "wall" command, notifying all the
# users connected to a console.
# The default is set to 'yes' to WARN the user. It can be disabled by setting
# the option to 'n' or 'no', or can simply be commented.
# Example
#   WARN = y
#   WARN = n
WARN = y


# The powernap daemon logs errors to /var/log/powernap.err, and some basic
# information to /var/log/powernap.log.  To change the verbosity of this
# logging, set DEBUG to 0, 1, 2, or 3:
# The default debug level is 0.
#    DEBUG = 1
#    DEBUG = 2
DEBUG = 0


# The powernap daemon can watch for changes in the configuration file in
# /etc/powernap directory without having to restart it.
# The default value is n.
#    WATCH_CONFIG = y
#    WATCH_CONFIG = n
WATCH_CONFIG = n


# Kernel Modules that are to be disabled when running PowerNap on Powersave
# mode
#KERN_MODULES = btusb sco tfcomm bnep


# Network Services that are to be disabled when running PowerNap on
# PowerSave mode
#SERVICES = postgresql-8.4 apache2 ntp network-manager


############################################################################
####                        STAGE2 ACTION                               ####
############################################################################
[powernap-stage2]
# Number of seconds that all monitors must have no activity or must be absent
# while running in PowerSave mode to perform the STAGE2_ACTION_METHOD.
# The default value is to be disabled by default. If you wish to enable the
# Second Stage Action method, set the STAGE2_ABSENT_SECONDS and ensure that
# STAGE2_ACTION_METHOD is set correctly.
# Example:
#   STAGE2_ABSENT_SECONDS = 500
STAGE2_ABSENT_SECONDS = 300


# The STAGE2_ACTION_METHOD variable determines what action should be taken
# after a period on inactivity while under PowerSave Mode (See ACTION_METHOD
# above).
# The possible actions are:
# 1 - suspend
# 2 - hibernate
# 3 - poweroff
# 4 - best-effort
# The default mode of operation is best-effort. This method will try to
# user-defined script  at "/etc/powernap/action", or suspend, hibernate,
# or poweroff the machine.
STAGE2_ACTION_METHOD = 4


############################################################################
####                          MONITORS                                  ####
############################################################################


# The [WoLMonitor] section lists all ports on which the WoL Monitor will be
# listening for WoL Packets for any of the network interfaces.
# Once a WoL Packet is received, the WoLMonitor will compare the data received
# with all the network interfaces (eth's) to determine wether it is destined
# for any of the network interfaces.
# The default is to monitor ports 7 and 9 for WoL data packets. It can also be
# set to any other port on which the machine is receiving WoL packets
# Example:
#  wol1052 = 1052
[WoLMonitor]
wol7 = 7
wol9 = 9


# The [ConsoleMonitor] section enables or disables  monitoring of activity
# in the Console (tty), also tracking activity from any locally connected
# mouse and keyboard (PS2 Only).
# The default is enabled, set to 'y'. It can be disabled by setting it to 'n'.
# Examples:
#  console = y
#  console = n
[ConsoleMonitor]
ptmx = y


# The [ProcessMonitor] section lists all the processes to Monitor by using
# regular expressions.
# Each item listed will be compared against the output of "ps -eo args".
# The default is to monitor /sbin/init, which should always be running.
# Examples:
#  mplayer = "mplayer "
#  sshd = "sshd: .*\[priv\]$"
#  kvm = "kvm "
[ProcessMonitor]
#init = "^/sbin/init"
ssh = "ssh "
rdiff = "rdiff-backup "
mupen = "mupen64plus "


# The [LoadMonitor] section defines the load threshold.  When the system load
# according to /proc/loadavg is above this value, then system will be deemed
# 'active' and will not powernap.  If the system is already powernapping, then
# the system will awake out of the powernap mode if the load raises above the
# threshold.
# If the threshold is set to "n" (which is default), threshold is automatically
# calculated to be the number of online processors, as determined by:
#   getconf _NPROCESSORS_ONLN
# Example:
#   threshold = 1.5
#   threshold = 9999
#   threshold = 0
#   threshold = n
[LoadMonitor]
threshold = n


# The [TCPMonitor] section lists all the TCP ports on which to watch for
# established connections using netstat(8). It supports both, single TCP
# as well as port ranges.
# There is no default TCP Monitor.
# Examples:
#  ssh = 22
#  http = 80
#  https = 443
#  other = 64500-65000
[TCPMonitor]
ssh = 22
transmission-rpc = 9091
transmission-data = 56155
smbd = 445
# The [UDPMonitor] section lists all the UDP ports on which to listen
# for data.
# Each item listed will BIND a UDP port and listen to any data. Keep
# in mind that this port will be bined and no other application will
# be able to use this port.
# There is no default UDP Monitor.
# Examples:
#  udp-1 = 1025
#  udp-2 = 2048
[UDPMonitor]
#udp-1025 = 1025


# The [IOMonitor] section lists all the processes to Monitor for IO
# activity. A regular expressions is used to find the processes PIDs, which
# are later used to monitor IO.
# There is no default IO Monitor.
# Examples:
#  kvm-io = "kvm"
#  mysqld-io = "mysql"
[IOMonitor]
#kvm-io = "kvm"
#mysqld-io = "mysql"


# The [InputMonitor] section lists the USB Input devices for which to track
# events. Currently, only two types of devices are supported, mouse and keyboard.
# Both InputMonitor's are enabled by default. In the case there are no USB
# devices connected, PowerNap will ignore these settings.
# To disable, set them to "n" or "no", or simply comment them.
# Examples:
#  keyboard = n
#  keyboard = y
[InputMonitor]
keyboard = y
mouse = y


# The [DiskMonitor] section lists the disk devices for which to track
# standby/sleep status.  If any of the devices are active/idle the
# system will be deemed 'active' and will not powernap. Generally useful
# for monitoring data drives (e.g. NAS), but will not typically work to
# monitor the root drive. Note also that this plugin only reacts to the
# state of the drive and does not modify the behavior of the drive
# directly. Therefore it only makes sense to monitor a drive that has
# already been configured to standby or sleep.
# To disable checking specific drives, set them to "n" or "no",
# or simply comment them.
# Examples:
#  sda = y
#  sdb = n
[DiskMonitor]
#sda = y


# The [RAIDMonitor] section lists the arrays for which to track maintenance
# tasks. If any of the arrays are performing checks, repairs, rebuilds or
# resyncs, the system will be deemed 'active' and will not powernap.
# To disable checking specific arrays, set them to "n" or "no",
# or simply comment them.
# Examples:
#  md0 = n
#  md1 = y
[RAIDMonitor]
md0 = y
#md1 = y
md2 = y

```

I've set this to "best effort" which runs /etc/powernap/action when it thinks the system is idle, this runs a script using python-xbmc to check if XBMC is also idle and suspend from within xbmc using xbmc.System.Suspend()
**/etc/powernap/action**
```
#!/usr/bin/python
#
# I wrote this script for Powernap, to sleep my Xbmc box if nobody is using it.
#
# I've got my Harmony remote setup to send PwrToggle when I switch to Xbmc which 
# wakes up my Xbmc box if it is sleeping (suspended).
#
# Just cat this into /etc/powernap/action && chmod +x /etc/powernap/action
# If you have Powernap's ACTION_METHOD set to 4 "best-effort" it will run this 
# script when it believes that your system is idle.
#
# You'll also need to edit line 19 to match the url of your Xbmc box
#
# Requirements: python-xbmc - https://github.com/jcsaaddupuy/python-xbmc
#
 
from xbmcjson import XBMC
 
xbmc = XBMC('http://localhost:8080/jsonrpc')
 
screenActive = xbmc.xbmc.GetInfoBooleans({'booleans':['System.ScreenSaverActive']})
playerActive = xbmc.Player.GetActivePlayers()
 
if not playerActive['result'] and screenActive['result']['System.ScreenSaverActive']:
  xbmc.System.Suspend()



```

---

### Post by rikki2 on 2014-08-11
Submitted as bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1354410](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1354410).

---

