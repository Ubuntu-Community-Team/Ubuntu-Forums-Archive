---
title: "Very slow boot"
date: 2013-04-09
forum: General Help
---

### Post by erik1001 on 2013-04-09
Hello all.


I'm going to reinstall my Ubuntu with the new 13.04 release soon so I want to ask you which is the best option to recreate my partition scheme. My system boots really slow and I blame the hard drive for this. I'm running Ubuntu 12.10 64bit with Unity on:
8 logical cores i7
8 GB 1666 MHz RAM
1 TB 5400 rpm hard drive
When I say slow, I mean really slow - 60 seconds for OS itself and other 30 seconds for DE.


My current partition scheme is:
```
user@pc:~$ sudo fdisk -l
[sudo] password for user: 


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000a88d6


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      718847      358400    7  HPFS/NTFS/exFAT
/dev/sda2          718848   614402047   306841600    7  HPFS/NTFS/exFAT
/dev/sda3       614404094  1952293427   668944667    5  Extended
Partition 3 does not start on physical sector boundary.
/dev/sda5       614404096   682761517    34178711   83  Linux
/dev/sda6       682764288   692527103     4881408   82  Linux swap / Solaris
/dev/sda7       692529152   790183935    48827392   83  Linux
/dev/sda8       790185984  1931812863   570813440   83  Linux
/dev/sda9      1931814912  1952293427    10239258   83  Linux

```
sda7 is my /var
sda8 is my /home
sda9 does not mount at all and it is for testing some stuff

I think to change it to:
    /dev/sda1 - 370MB
    /dev/sda2 - 315GB - ntfs (Windows partition)
    /dev/sda3 - 685GB - extended (Linux partitions)
    /dev/sda4 - 35GB - ext4 - /
    /dev/sda5 - 4GB - swap
    /dev/sda6 - 646GB - ext4 - /home

Would this improve my boot speed?

Also, I've checked my log and I saw some huge delays in it:
```
[    0.000000] Initializing cgroup subsys cpuset[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.5.0-26-generic (buildd@lamiak) (gcc version 4.7.2 (Ubuntu/Linaro 4.7.2-2ubuntu1) ) #42-Ubuntu SMP Fri Mar 8 23:18:20 UTC 2013 (Ubuntu 3.5.0-26.42-generic 3.5.7.6)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-26-generic root=UUID=ea7728c0-d5fe-4914-a93a-5e089ca7ea1d ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009d7ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009d800-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000001fffffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000020000000-0x00000000201fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000020200000-0x0000000040003fff] usable
[    0.000000] BIOS-e820: [mem 0x0000000040004000-0x0000000040004fff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000040005000-0x00000000baabefff] usable
[    0.000000] BIOS-e820: [mem 0x00000000baabf000-0x00000000baebefff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000baebf000-0x00000000bafbefff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bafbf000-0x00000000baffefff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000bafff000-0x00000000baffffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bb000000-0x00000000bf9fffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000f0000000-0x00000000f3ffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000feb00000-0x00000000feb03fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed10000-0x00000000fed19fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffb80000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000023f5fffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.7 present.
[    0.000000] DMI: LENOVO 20150/Product Name, BIOS 5ECN39WW(V3.05) 09/11/2012
[    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x23f600 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-E7FFF write-protect
[    0.000000]   E8000-EFFFF write-combining
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FC0000000 write-back
[    0.000000]   2 base 0BB000000 mask FFF000000 uncachable
[    0.000000]   3 base 0BC000000 mask FFC000000 uncachable
[    0.000000]   4 base 0FFC00000 mask FFFC00000 write-protect
[    0.000000]   5 base 100000000 mask F00000000 write-back
[    0.000000]   6 base 200000000 mask FC0000000 write-back
[    0.000000]   7 base 23F600000 mask FFFE00000 uncachable
[    0.000000]   8 base 23F800000 mask FFF800000 uncachable
[    0.000000]   9 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820: last_pfn = 0xbb000 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000fe1b0-0x000fe1bf] mapped at [ffff8800000fe1b0]
[    0.000000] initial memory mapped: [mem 0x00000000-0x1fffffff]
[    0.000000] Base memory trampoline at [ffff880000097000] 97000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0xbaffffff]
[    0.000000]  [mem 0x00000000-0xbaffffff] page 2M
[    0.000000] kernel direct mapping tables up to 0xbaffffff @ [mem 0x1fffc000-0x1fffffff]
[    0.000000] init_memory_mapping: [mem 0x100000000-0x23f5fffff]
[    0.000000]  [mem 0x100000000-0x23f5fffff] page 2M
[    0.000000] kernel direct mapping tables up to 0x23f5fffff @ [mem 0xbaab9000-0xbaabefff]
[    0.000000] RAMDISK: [mem 0x355d6000-0x36ae2fff]
[    0.000000] ACPI: RSDP 00000000000fe020 00024 (v02 LENOVO)
[    0.000000] ACPI: XSDT 00000000baffe210 00094 (v01 LENOVO CB-01    00000001      01000013)
[    0.000000] ACPI: FACP 00000000baffb000 000F4 (v04 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: DSDT 00000000bafee000 09846 (v01 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: FACS 00000000bafbb000 00040
[    0.000000] ACPI: UEFI 00000000baffd000 00236 (v01 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: ASF! 00000000baffc000 000A5 (v32 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: HPET 00000000baffa000 00038 (v01 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: APIC 00000000baff9000 0008C (v02 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: MCFG 00000000baff8000 0003C (v01 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: SLIC 00000000bafed000 00176 (v01 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: SSDT 00000000bafec000 006FE (v01 LENOVO CB-01    00001000 ACPI 00040000)
[    0.000000] ACPI: BOOT 00000000bafea000 00028 (v01 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: ASPT 00000000bafe5000 00034 (v07 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: FPDT 00000000bafe3000 00044 (v01 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: SSDT 00000000bafe2000 008A2 (v01 LENOVO CB-01    00003000 ACPI 00040000)
[    0.000000] ACPI: SSDT 00000000bafe1000 00A92 (v01 LENOVO CB-01    00003000 ACPI 00040000)
[    0.000000] ACPI: SSDT 00000000bafdf000 01EDD (v01 LENOVO CB-01    00001000 ACPI 00040000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000023f5fffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x23f5fffff]
[    0.000000]   NODE_DATA [mem 0x23f5fc000-0x23f5fffff]
[    0.000000]  [ffffea0000000000-ffffea0008ffffff] PMD -> [ffff880236c00000-ffff88023ebfffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00010000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x23f5fffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00010000-0x0009cfff]
[    0.000000]   node   0: [mem 0x00100000-0x1fffffff]
[    0.000000]   node   0: [mem 0x20200000-0x40003fff]
[    0.000000]   node   0: [mem 0x40005000-0xbaabefff]
[    0.000000]   node   0: [mem 0xbafff000-0xbaffffff]
[    0.000000]   node   0: [mem 0x100000000-0x23f5fffff]
[    0.000000] On node 0 totalpages: 2072140
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 6 pages reserved
[    0.000000]   DMA zone: 3911 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 16320 pages used for memmap
[    0.000000]   DMA32 zone: 743679 pages, LIFO batch:31
[    0.000000]   Normal zone: 20440 pages used for memmap
[    0.000000]   Normal zone: 1287720 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] enabled)
[    0.000000] ACPI: IOAPIC (id[0x00] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 0, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 8 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000020200000
[    0.000000] PM: Registered nosave memory: 0000000040004000 - 0000000040005000
[    0.000000] PM: Registered nosave memory: 00000000baabf000 - 00000000baebf000
[    0.000000] PM: Registered nosave memory: 00000000baebf000 - 00000000bafbf000
[    0.000000] PM: Registered nosave memory: 00000000bafbf000 - 00000000bafff000
[    0.000000] PM: Registered nosave memory: 00000000bb000000 - 00000000bfa00000
[    0.000000] PM: Registered nosave memory: 00000000bfa00000 - 00000000f0000000
[    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000f4000000
[    0.000000] PM: Registered nosave memory: 00000000f4000000 - 00000000feb00000
[    0.000000] PM: Registered nosave memory: 00000000feb00000 - 00000000feb04000
[    0.000000] PM: Registered nosave memory: 00000000feb04000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
[    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fed10000
[    0.000000] PM: Registered nosave memory: 00000000fed10000 - 00000000fed1a000
[    0.000000] PM: Registered nosave memory: 00000000fed1a000 - 00000000fed1c000
[    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
[    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffb80000
[    0.000000] PM: Registered nosave memory: 00000000ffb80000 - 0000000100000000
[    0.000000] e820: [mem 0xbfa00000-0xefffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88023f200000 s83584 r8192 d22912 u262144
[    0.000000] pcpu-alloc: s83584 r8192 d22912 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2035310
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-26-generic root=UUID=ea7728c0-d5fe-4914-a93a-5e089ca7ea1d ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] __ex_table already sorted, skipping sort
[    0.000000] xsave/xrstor: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 8053116k/9426944k available (6708k kernel code, 1138384k absent, 235444k reserved, 6458k data, 932k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 33554432 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.004000] Detected 2195.213 MHz processor.
[    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 4390.42 BogoMIPS (lpj=8780852)
[    0.000005] pid_max: default: 32768 minimum: 301
[    0.000027] Security Framework initialized
[    0.000039] AppArmor: AppArmor initialized
[    0.000040] Yama: becoming mindful.
[    0.000560] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.002747] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.003714] Mount-cache hash table entries: 256
[    0.003875] Initializing cgroup subsys cpuacct
[    0.003877] Initializing cgroup subsys memory
[    0.003885] Initializing cgroup subsys devices
[    0.003886] Initializing cgroup subsys freezer
[    0.003887] Initializing cgroup subsys blkio
[    0.003889] Initializing cgroup subsys perf_event
[    0.003915] CPU: Physical Processor ID: 0
[    0.003916] CPU: Processor Core ID: 0
[    0.003920] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.003920] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.004326] mce: CPU supports 9 MCE banks
[    0.004340] CPU0: Thermal monitoring enabled (TM1)
[    0.004348] using mwait in idle threads.
[    0.006554] ACPI: Core revision 20120320
[    0.026073] ftrace: allocating 25098 entries in 99 pages
[    0.043867] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.083512] CPU0: Intel(R) Core(TM) i7-3632QM CPU @ 2.20GHz stepping 09
[    0.188370] Performance Events: PEBS fmt1+, 16-deep LBR, SandyBridge events, Intel PMU driver.
[    0.188376] ... version:                3
[    0.188377] ... bit width:              48
[    0.188378] ... generic registers:      4
[    0.188379] ... value mask:             0000ffffffffffff
[    0.188380] ... max period:             000000007fffffff
[    0.188381] ... fixed-purpose events:   3
[    0.188382] ... event mask:             000000070000000f
[    0.188518] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.188598] Booting Node   0, Processors  #1 #2 #3 #4 #5 #6 #7 Ok.
[    0.283798] Brought up 8 CPUs
[    0.283802] Total of 8 processors activated (35123.40 BogoMIPS).
[    0.291479] devtmpfs: initialized
[    0.292543] EVM: security.selinux
[    0.292544] EVM: security.SMACK64
[    0.292545] EVM: security.capability
[    0.292583] PM: Registering ACPI NVS region [mem 0xbaebf000-0xbafbefff] (1048576 bytes)
[    0.293309] dummy: 
[    0.293341] RTC time: 22:33:53, date: 04/08/13
[    0.293374] NET: Registered protocol family 16
[    0.293457] Trying to unpack rootfs image as initramfs...
[    0.293513] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.293515] ACPI: bus type pci registered
[    0.293582] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf0000000-0xf3ffffff] (base 0xf0000000)
[    0.293584] PCI: MMCONFIG at [mem 0xf0000000-0xf3ffffff] reserved in E820
[    0.300360] PCI: Using configuration type 1 for base access
[    0.300598] mtrr: your CPUs had inconsistent variable MTRR settings
[    0.300599] mtrr: probably your BIOS does not setup all CPUs.
[    0.300600] mtrr: corrected configuration.
[    0.301208] bio: create slab <bio-0> at 0
[    0.301276] ACPI: Added _OSI(Module Device)
[    0.301278] ACPI: Added _OSI(Processor Device)
[    0.301279] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.301281] ACPI: Added _OSI(Processor Aggregator Device)
[    0.302899] ACPI: EC: Look up EC in DSDT
[    0.304545] ACPI: Executed 1 blocks of module-level executable AML code
[    0.356306] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.357438] ACPI: SSDT 00000000badf8018 0083B (v01  PmRef  Cpu0Cst 00003001 INTL 20100121)
[    0.357851] ACPI: Dynamic OEM Table Load:
[    0.357853] ACPI: SSDT           (null) 0083B (v01  PmRef  Cpu0Cst 00003001 INTL 20100121)
[    0.384383] ACPI: SSDT 00000000badf9a98 00303 (v01  PmRef    ApIst 00003000 INTL 20100121)
[    0.384823] ACPI: Dynamic OEM Table Load:
[    0.384825] ACPI: SSDT           (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20100121)
[    0.412222] ACPI: SSDT 00000000badf7d98 00119 (v01  PmRef    ApCst 00003000 INTL 20100121)
[    0.412635] ACPI: Dynamic OEM Table Load:
[    0.412637] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20100121)
[    0.433633] ACPI: Interpreter enabled
[    0.433637] ACPI: (supports S0 S3 S4 S5)
[    0.433659] ACPI: Using IOAPIC for interrupt routing
[    0.555034] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.555210] ACPI: No dock devices found.
[    0.555214] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.555510] \_SB_.PCI0:_OSC invalid UUID
[    0.555511] _OSC request data:1 8 1f 
[    0.555515] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    0.555976] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.555978] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.555980] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.555983] pci_root PNP0A08:00: host bridge window [mem 0xbfa00000-0xfeafffff]
[    0.556008] PCI host bridge to bus 0000:00
[    0.556010] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.556012] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.556014] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.556016] pci_bus 0000:00: root bus resource [mem 0xbfa00000-0xfeafffff]
[    0.556024] pci 0000:00:00.0: [8086:0154] type 00 class 0x060000
[    0.556061] pci 0000:00:01.0: [8086:0151] type 01 class 0x060400
[    0.556094] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.556114] pci 0000:00:02.0: [8086:0166] type 00 class 0x030000
[    0.556125] pci 0000:00:02.0: reg 10: [mem 0xd3400000-0xd37fffff 64bit]
[    0.556132] pci 0000:00:02.0: reg 18: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.556138] pci 0000:00:02.0: reg 20: [io  0x4000-0x403f]
[    0.556192] pci 0000:00:14.0: [8086:1e31] type 00 class 0x0c0330
[    0.556216] pci 0000:00:14.0: reg 10: [mem 0xd3a00000-0xd3a0ffff 64bit]
[    0.556290] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    0.556315] pci 0000:00:16.0: [8086:1e3a] type 00 class 0x078000
[    0.556340] pci 0000:00:16.0: reg 10: [mem 0xd3a14000-0xd3a1400f 64bit]
[    0.556419] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.556456] pci 0000:00:1a.0: [8086:1e2d] type 00 class 0x0c0320
[    0.556727] pci 0000:00:1a.0: reg 10: [mem 0xd3a19000-0xd3a193ff]
[    0.558247] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.558276] pci 0000:00:1b.0: [8086:1e20] type 00 class 0x040300
[    0.558292] pci 0000:00:1b.0: reg 10: [mem 0xd3a10000-0xd3a13fff 64bit]
[    0.558363] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.558388] pci 0000:00:1c.0: [8086:1e10] type 01 class 0x060400
[    0.558471] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.558497] pci 0000:00:1c.1: [8086:1e12] type 01 class 0x060400
[    0.558579] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.558616] pci 0000:00:1d.0: [8086:1e26] type 00 class 0x0c0320
[    0.558877] pci 0000:00:1d.0: reg 10: [mem 0xd3a18000-0xd3a183ff]
[    0.560411] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.560439] pci 0000:00:1f.0: [8086:1e59] type 00 class 0x060100
[    0.560567] pci 0000:00:1f.2: [8086:1e03] type 00 class 0x010601
[    0.560588] pci 0000:00:1f.2: reg 10: [io  0x4088-0x408f]
[    0.560596] pci 0000:00:1f.2: reg 14: [io  0x4094-0x4097]
[    0.560605] pci 0000:00:1f.2: reg 18: [io  0x4080-0x4087]
[    0.560614] pci 0000:00:1f.2: reg 1c: [io  0x4090-0x4093]
[    0.560623] pci 0000:00:1f.2: reg 20: [io  0x4060-0x407f]
[    0.560631] pci 0000:00:1f.2: reg 24: [mem 0xd3a17000-0xd3a177ff]
[    0.560679] pci 0000:00:1f.2: PME# supported from D3hot
[    0.560699] pci 0000:00:1f.3: [8086:1e22] type 00 class 0x0c0500
[    0.560715] pci 0000:00:1f.3: reg 10: [mem 0xd3a15000-0xd3a150ff 64bit]
[    0.560738] pci 0000:00:1f.3: reg 20: [io  0x4040-0x405f]
[    0.560802] pci 0000:01:00.0: [10de:0de3] type 00 class 0x030000
[    0.560813] pci 0000:01:00.0: reg 10: [mem 0xd2000000-0xd2ffffff]
[    0.560825] pci 0000:01:00.0: reg 14: [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.560836] pci 0000:01:00.0: reg 1c: [mem 0xd0000000-0xd1ffffff 64bit pref]
[    0.560844] pci 0000:01:00.0: reg 24: [io  0x3000-0x307f]
[    0.560852] pci 0000:01:00.0: reg 30: [mem 0xfff80000-0xffffffff pref]
[    0.567945] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.567948] pci 0000:00:01.0:   bridge window [io  0x3000-0x3fff]
[    0.567951] pci 0000:00:01.0:   bridge window [mem 0xd2000000-0xd30fffff]
[    0.567955] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xd1ffffff 64bit pref]
[    0.568069] pci 0000:02:00.0: [1969:1090] type 00 class 0x020000
[    0.568170] pci 0000:02:00.0: reg 10: [mem 0xd3900000-0xd393ffff 64bit]
[    0.568219] pci 0000:02:00.0: reg 18: [io  0x2000-0x207f]
[    0.568695] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.575964] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.575969] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.575973] pci 0000:00:1c.0:   bridge window [mem 0xd3900000-0xd39fffff]
[    0.576083] pci 0000:03:00.0: [14e4:4727] type 00 class 0x028000
[    0.576118] pci 0000:03:00.0: reg 10: [mem 0xd3800000-0xd3803fff 64bit]
[    0.576282] pci 0000:03:00.0: supports D1 D2
[    0.576284] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[    0.583962] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    0.583969] pci 0000:00:1c.1:   bridge window [mem 0xd3800000-0xd38fffff]
[    0.583991] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.584113] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.584140] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.584180] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEG0._PRT]
[    0.584261] \_SB_.PCI0:_OSC invalid UUID
[    0.584263] _OSC request data:1 1f 1f 
[    0.584267]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.584304] \_SB_.PCI0:_OSC invalid UUID
[    0.584305] _OSC request data:1 0 1d 
[    0.584309]  pci0000:00: ACPI _OSC request failed (AE_ERROR), returned control mask: 0x1d
[    0.584310] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.586820] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 10 *11 12 14 15)
[    0.586862] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 *10 11 12 14 15)
[    0.586901] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.586941] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 *10 11 12 14 15)
[    0.586978] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.587017] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 10 11 12 14 15) *7
[    0.587055] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 10 11 12 14 15) *7
[    0.587094] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 10 *11 12 14 15)
[    0.587170] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.587176] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=none,locks=none
[    0.587178] vgaarb: loaded
[    0.587179] vgaarb: bridge control possible 0000:01:00.0
[    0.587180] vgaarb: no bridge control possible 0000:00:02.0
[    0.587308] SCSI subsystem initialized
[    0.587342] libata version 3.00 loaded.
[    0.587357] ACPI: bus type usb registered
[    0.587373] usbcore: registered new interface driver usbfs
[    0.587379] usbcore: registered new interface driver hub
[    0.587394] usbcore: registered new device driver usb
[    0.587446] PCI: Using ACPI for IRQ routing
[    0.589072] PCI: pci_cache_line_size set to 64 bytes
[    0.589179] e820: reserve RAM buffer [mem 0x0009d800-0x0009ffff]
[    0.589181] e820: reserve RAM buffer [mem 0x40004000-0x43ffffff]
[    0.589182] e820: reserve RAM buffer [mem 0xbaabf000-0xbbffffff]
[    0.589184] e820: reserve RAM buffer [mem 0xbb000000-0xbbffffff]
[    0.589185] e820: reserve RAM buffer [mem 0x23f600000-0x23fffffff]
[    0.589256] NetLabel: Initializing
[    0.589258] NetLabel:  domain hash size = 128
[    0.589259] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.589267] NetLabel:  unlabeled traffic allowed by default
[    0.589311] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.589316] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.591326] Switching to clocksource hpet
[    0.596347] AppArmor: AppArmor Filesystem Enabled
[    0.596367] pnp: PnP ACPI init
[    0.596378] ACPI: bus type pnp registered
[    0.596649] pnp 00:00: [bus 00-3e]
[    0.596653] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.596655] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.596657] pnp 00:00: [io  0x0d00-0xffff window]
[    0.596659] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.596660] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    0.596662] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    0.596664] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    0.596665] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    0.596667] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    0.596668] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    0.596670] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    0.596671] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    0.596673] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    0.596675] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    0.596676] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    0.596678] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    0.596679] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    0.596681] pnp 00:00: [mem 0xbfa00000-0xfeafffff window]
[    0.596683] pnp 00:00: [mem 0x00010000-0x0001ffff window]
[    0.596739] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.596750] pnp 00:01: [io  0x0000-0x001f]
[    0.596752] pnp 00:01: [io  0x0081-0x0091]
[    0.596753] pnp 00:01: [io  0x0093-0x009f]
[    0.596755] pnp 00:01: [io  0x00c0-0x00df]
[    0.596757] pnp 00:01: [dma 4]
[    0.596773] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.596780] pnp 00:02: [mem 0xff010000-0xffffffff]
[    0.596794] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
[    0.596857] pnp 00:03: [mem 0xfed00000-0xfed003ff]
[    0.596874] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.596882] pnp 00:04: [io  0x00f0]
[    0.596891] pnp 00:04: [irq 13]
[    0.596906] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.596914] pnp 00:05: [io  0x002e-0x002f]
[    0.596916] pnp 00:05: [io  0x004e-0x004f]
[    0.596917] pnp 00:05: [io  0x0061]
[    0.596919] pnp 00:05: [io  0x0063]
[    0.596920] pnp 00:05: [io  0x0065]
[    0.596922] pnp 00:05: [io  0x0067]
[    0.596923] pnp 00:05: [io  0x0070]
[    0.596924] pnp 00:05: [io  0x0080]
[    0.596926] pnp 00:05: [io  0x0092]
[    0.596927] pnp 00:05: [io  0x00b2-0x00b3]
[    0.596929] pnp 00:05: [io  0x0680-0x069f]
[    0.596930] pnp 00:05: [io  0x1000-0x100f]
[    0.596932] pnp 00:05: [io  0xffff]
[    0.596933] pnp 00:05: [io  0xffff]
[    0.596936] pnp 00:05: [io  0x0400-0x0453]
[    0.596937] pnp 00:05: [io  0x0458-0x047f]
[    0.596939] pnp 00:05: [io  0x0500-0x057f]
[    0.596940] pnp 00:05: [io  0x164e-0x164f]
[    0.596942] pnp 00:05: [io  0xfd60-0xfd63]
[    0.596975] system 00:05: [io  0x0680-0x069f] has been reserved
[    0.596978] system 00:05: [io  0x1000-0x100f] has been reserved
[    0.596979] system 00:05: [io  0xffff] has been reserved
[    0.596981] system 00:05: [io  0xffff] has been reserved
[    0.596983] system 00:05: [io  0x0400-0x0453] has been reserved
[    0.596985] system 00:05: [io  0x0458-0x047f] has been reserved
[    0.596987] system 00:05: [io  0x0500-0x057f] has been reserved
[    0.596988] system 00:05: [io  0x164e-0x164f] has been reserved
[    0.596990] system 00:05: [io  0xfd60-0xfd63] has been reserved
[    0.596993] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.597000] pnp 00:06: [io  0x0070-0x0077]
[    0.597005] pnp 00:06: [irq 8]
[    0.597020] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.597042] pnp 00:07: [io  0x0454-0x0457]
[    0.597068] system 00:07: [io  0x0454-0x0457] has been reserved
[    0.597070] system 00:07: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.597079] pnp 00:08: [io  0x0060]
[    0.597081] pnp 00:08: [io  0x0064]
[    0.597086] pnp 00:08: [irq 1]
[    0.597102] pnp 00:08: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.597152] pnp 00:09: [irq 12]
[    0.597172] pnp 00:09: Plug and Play ACPI device, IDs ETD0613 ETD0001 PNP0f13 (active)
[    0.639146] Freeing initrd memory: 21556k freed
[    0.655547] pnp 00:0a: [mem 0xfed1c000-0xfed1ffff]
[    0.655550] pnp 00:0a: [mem 0xfed10000-0xfed17fff]
[    0.655552] pnp 00:0a: [mem 0xfed18000-0xfed18fff]
[    0.655553] pnp 00:0a: [mem 0xfed19000-0xfed19fff]
[    0.655555] pnp 00:0a: [mem 0xf0000000-0xf3ffffff]
[    0.655556] pnp 00:0a: [mem 0xfed20000-0xfed3ffff]
[    0.655558] pnp 00:0a: [mem 0xfed90000-0xfed93fff]
[    0.655559] pnp 00:0a: [mem 0xff000000-0xff000fff]
[    0.655561] pnp 00:0a: [mem 0xff010000-0xffffffff]
[    0.655562] pnp 00:0a: [mem 0xfee00000-0xfeefffff]
[    0.655564] pnp 00:0a: [mem 0xbfa00000-0xbfa00fff]
[    0.655618] system 00:0a: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.655620] system 00:0a: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.655622] system 00:0a: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.655624] system 00:0a: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.655626] system 00:0a: [mem 0xf0000000-0xf3ffffff] has been reserved
[    0.655628] system 00:0a: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.655630] system 00:0a: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.655632] system 00:0a: [mem 0xff000000-0xff000fff] has been reserved
[    0.655634] system 00:0a: [mem 0xff010000-0xffffffff] could not be reserved
[    0.655636] system 00:0a: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.655638] system 00:0a: [mem 0xbfa00000-0xbfa00fff] has been reserved
[    0.655641] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.655941] pnp 00:0b: [mem 0x20000000-0x201fffff]
[    0.655943] pnp 00:0b: [mem 0x40004000-0x40004fff]
[    0.655994] system 00:0b: [mem 0x20000000-0x201fffff] has been reserved
[    0.655996] system 00:0b: [mem 0x40004000-0x40004fff] has been reserved
[    0.655999] system 00:0b: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.656015] pnp: PnP ACPI: found 12 devices
[    0.656016] ACPI: ACPI bus type pnp unregistered
[    0.662072] pci 0000:01:00.0: no compatible bridge window for [mem 0xfff80000-0xffffffff pref]
[    0.662105] pci 0000:01:00.0: BAR 6: assigned [mem 0xd3000000-0xd307ffff pref]
[    0.662108] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.662110] pci 0000:00:01.0:   bridge window [io  0x3000-0x3fff]
[    0.662113] pci 0000:00:01.0:   bridge window [mem 0xd2000000-0xd30fffff]
[    0.662116] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xd1ffffff 64bit pref]
[    0.662120] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.662123] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.662129] pci 0000:00:1c.0:   bridge window [mem 0xd3900000-0xd39fffff]
[    0.662137] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    0.662142] pci 0000:00:1c.1:   bridge window [mem 0xd3800000-0xd38fffff]
[    0.662179] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.662181] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.662182] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.662184] pci_bus 0000:00: resource 7 [mem 0xbfa00000-0xfeafffff]
[    0.662186] pci_bus 0000:01: resource 0 [io  0x3000-0x3fff]
[    0.662188] pci_bus 0000:01: resource 1 [mem 0xd2000000-0xd30fffff]
[    0.662190] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xd1ffffff 64bit pref]
[    0.662192] pci_bus 0000:02: resource 0 [io  0x2000-0x2fff]
[    0.662193] pci_bus 0000:02: resource 1 [mem 0xd3900000-0xd39fffff]
[    0.662195] pci_bus 0000:03: resource 1 [mem 0xd3800000-0xd38fffff]
[    0.662222] NET: Registered protocol family 2
[    0.662379] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.663006] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.664105] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.664231] TCP: Hash tables configured (established 524288 bind 65536)
[    0.664232] TCP: reno registered
[    0.664244] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.664270] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.664348] NET: Registered protocol family 1
[    0.664362] pci 0000:00:02.0: Boot video device
[    0.695454] PCI: CLS 64 bytes, default 64
[    0.695456] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.695458] software IO TLB [mem 0xb6ab9000-0xbaab8fff] (64MB) mapped at [ffff8800b6ab9000-ffff8800baab8fff]
[    0.695490] Simple Boot Flag at 0x44 set to 0x1
[    0.695986] audit: initializing netlink socket (disabled)
[    0.695993] type=2000 audit(1365460433.572:1): initialized
[    0.717455] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.718875] VFS: Disk quotas dquot_6.5.2
[    0.718912] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.719287] fuse init (API version 7.19)
[    0.719367] msgmni has been set to 15770
[    0.719660] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.719684] io scheduler noop registered
[    0.719685] io scheduler deadline registered (default)
[    0.719705] io scheduler cfq registered
[    0.719785] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.719915] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.719926] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.719957] intel_idle: MWAIT substates: 0x21120
[    0.719958] intel_idle: v0.4 model 0x3A
[    0.719959] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.720042] ACPI: AC Adapter [ACAD] (on-line)
[    0.720120] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0C:00/input/input0
[    0.720124] ACPI: Power Button [PWRB]
[    0.720151] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0E:00/input/input1
[    0.720153] ACPI: Sleep Button [SLPB]
[    0.720185] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input2
[    0.720206] ACPI: Lid Switch [LID0]
[    0.720232] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.720234] ACPI: Power Button [PWRF]
[    0.720297] ACPI: Requesting acpi_cpufreq
[    0.841669] thermal LNXTHERM:00: registered as thermal_zone0
[    0.841671] ACPI: Thermal Zone [TZ00] (54 C)
[    0.841685] ACPI: Battery Slot [BAT1] (battery present)
[    0.841704] GHES: HEST is not enabled!
[    0.841753] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.842763] Linux agpgart interface v0.103
[    0.843803] brd: module loaded
[    0.844408] loop: module loaded
[    0.844646] Fixed MDIO Bus: probed
[    0.844675] tun: Universal TUN/TAP device driver, 1.6
[    0.844677] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.844710] PPP generic driver version 2.4.2
[    0.844747] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.844788] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.844791] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    0.844798] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    0.844822] ehci_hcd 0000:00:1a.0: debug port 2
[    0.848695] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    0.848709] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xd3a19000
[    0.859185] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    0.859222] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.859224] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.859226] usb usb1: Product: EHCI Host Controller
[    0.859228] usb usb1: Manufacturer: Linux 3.5.0-26-generic ehci_hcd
[    0.859229] usb usb1: SerialNumber: 0000:00:1a.0
[    0.859312] hub 1-0:1.0: USB hub found
[    0.859316] hub 1-0:1.0: 2 ports detected
[    0.859370] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.859373] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    0.859377] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.859397] ehci_hcd 0000:00:1d.0: debug port 2
[    0.863265] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    0.863277] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xd3a18000
[    0.875169] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    0.875201] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    0.875202] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.875204] usb usb2: Product: EHCI Host Controller
[    0.875206] usb usb2: Manufacturer: Linux 3.5.0-26-generic ehci_hcd
[    0.875207] usb usb2: SerialNumber: 0000:00:1d.0
[    0.875285] hub 2-0:1.0: USB hub found
[    0.875288] hub 2-0:1.0: 2 ports detected
[    0.875328] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.875340] uhci_hcd: USB Universal Host Controller Interface driver
[    0.875379] xhci_hcd 0000:00:14.0: setting latency timer to 64
[    0.875382] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.875385] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
[    0.875471] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    0.875483] xhci_hcd 0000:00:14.0: irq 21, io mem 0xd3a00000
[    0.875529] xhci_hcd 0000:00:14.0: irq 41 for MSI/MSI-X
[    0.875572] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    0.875574] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.875575] usb usb3: Product: xHCI Host Controller
[    0.875577] usb usb3: Manufacturer: Linux 3.5.0-26-generic xhci_hcd
[    0.875578] usb usb3: SerialNumber: 0000:00:14.0
[    0.875635] xHCI xhci_add_endpoint called for root hub
[    0.875637] xHCI xhci_check_bandwidth called for root hub
[    0.875654] hub 3-0:1.0: USB hub found
[    0.875661] hub 3-0:1.0: 4 ports detected
[    0.875704] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.875707] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 4
[    0.875725] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
[    0.875726] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.875728] usb usb4: Product: xHCI Host Controller
[    0.875729] usb usb4: Manufacturer: Linux 3.5.0-26-generic xhci_hcd
[    0.875731] usb usb4: SerialNumber: 0000:00:14.0
[    0.875783] xHCI xhci_add_endpoint called for root hub
[    0.875785] xHCI xhci_check_bandwidth called for root hub
[    0.875799] hub 4-0:1.0: USB hub found
[    0.875806] hub 4-0:1.0: 4 ports detected
[    0.875907] usbcore: registered new interface driver libusual
[    0.875934] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:MSS4] at 0x60,0x64 irq 1,12
[    0.890043] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.890047] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.890127] mousedev: PS/2 mouse device common for all mice
[    0.891991] rtc_cmos 00:06: RTC can wake from S4
[    0.892104] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.892133] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    0.892187] device-mapper: uevent: version 1.0.3
[    0.892239] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    0.892356] cpuidle: using governor ladder
[    0.892514] cpuidle: using governor menu
[    0.892515] EFI Variables Facility v0.08 2004-May-17
[    0.892687] ashmem: initialized
[    0.892782] TCP: cubic registered
[    0.892859] NET: Registered protocol family 10
[    0.893010] NET: Registered protocol family 17
[    0.893019] Key type dns_resolver registered
[    0.893180] PM: Hibernation image not present or could not be loaded.
[    0.893188] registered taskstats version 1
[    0.895706] Key type trusted registered
[    0.897975] Key type encrypted registered
[    0.900639]   Magic number: 9:950:602
[    0.900753] rtc_cmos 00:06: setting system clock to 2013-04-08 22:33:54 UTC (1365460434)
[    0.902025] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.902027] EDD information not available.
[    0.904785] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.039078] ACPI: Battery Slot [BAT1] (battery present)
[    1.040155] Freeing unused kernel memory: 932k freed
[    1.040233] Write protecting the kernel read-only data: 12288k
[    1.043210] Freeing unused kernel memory: 1472k freed
[    1.045608] Freeing unused kernel memory: 1136k freed
[    1.059188] udevd[119]: starting version 175
[    1.071302] [drm] Initialized drm 1.1.0 20060810
[    1.074393] i915 0000:00:02.0: setting latency timer to 64
[    1.074815] pci 0000:00:00.0: Intel Ivybridge Chipset
[    1.074868] pci 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    1.076008] pci 0000:00:00.0: detected 65536K stolen memory
[    1.101990] i915 0000:00:02.0: irq 42 for MSI/MSI-X
[    1.101998] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    1.101999] [drm] Driver supports precise vblank timestamp query.
[    1.102572] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=none:owns=io+mem
[    1.102573] vgaarb: transferring owner from PCI:0000:00:02.0 to PCI:0000:01:00.0
[    1.170919] usb 1-1: new high-speed USB device number 2 using ehci_hcd
[    1.303173] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
[    1.303180] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.303556] hub 1-1:1.0: USB hub found
[    1.303636] hub 1-1:1.0: 6 ports detected
[    1.414593] usb 2-1: new high-speed USB device number 2 using ehci_hcd
[    1.546902] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
[    1.546909] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.547292] hub 2-1:1.0: USB hub found
[    1.547362] hub 2-1:1.0: 6 ports detected
[    1.618614] usb 1-1.2: new full-speed USB device number 3 using ehci_hcd
[    1.657823] [drm] Enabling RC6 states: RC6 on, RC6p on, RC6pp off
[    1.694319] Refined TSC clocksource calibration: 2195.013 MHz.
[    1.694328] Switching to clocksource tsc
[    1.712480] usb 1-1.2: New USB device found, idVendor=09da, idProduct=054f
[    1.712487] usb 1-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.712491] usb 1-1.2: Product: USB Device
[    1.712494] usb 1-1.2: Manufacturer: A4TECH
[    1.717478] usbcore: registered new interface driver usbhid
[    1.717492] usbhid: USB HID core driver
[    1.718978] input: A4TECH USB Device as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input5
[    1.719217] hid-generic 0003:09DA:054F.0001: input,hiddev0,hidraw0: USB HID v1.11 Keyboard [A4TECH USB Device] on usb-0000:00:1a.0-1.2/input0
[    1.719324] input: A4TECH USB Device as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.1/input/input6
[    1.719439] hid-generic 0003:09DA:054F.0002: input,hidraw1: USB HID v1.11 Mouse [A4TECH USB Device] on usb-0000:00:1a.0-1.2/input1
[    1.782405] usb 1-1.3: new full-speed USB device number 4 using ehci_hcd
[    1.840744] fbcon: inteldrmfb (fb0) is primary device
[    1.840779] Console: switching to colour frame buffer device 170x48
[    1.840793] fb0: inteldrmfb frame buffer device
[    1.840794] drm: registered panic notifier
[    1.840953] [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS
[    1.842277] acpi device:37: registered as cooling_device8
[    1.842363] ACPI: Video Device [PEGP] (multi-head: yes  rom: yes  post: no)
[    1.842395] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:35/LNXVIDEO:00/input/input7
[    1.847661] acpi device:43: registered as cooling_device9
[    1.847775] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    1.847830] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input8
[    1.847949] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    1.847973] ahci 0000:00:1f.2: version 3.0
[    1.848052] ahci 0000:00:1f.2: irq 43 for MSI/MSI-X
[    1.848085] ahci: SSS flag set, parallel bus scan disabled
[    1.862194] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x5 impl SATA mode
[    1.862198] ahci 0000:00:1f.2: flags: 64bit ncq stag pm led clo pio slum part ems apst 
[    1.862202] ahci 0000:00:1f.2: setting latency timer to 64
[    1.870561] scsi0 : ahci
[    1.870739] scsi1 : ahci
[    1.870874] scsi2 : ahci
[    1.871003] scsi3 : ahci
[    1.871158] scsi4 : ahci
[    1.871313] scsi5 : ahci
[    1.871394] ata1: SATA max UDMA/133 abar m2048@0xd3a17000 port 0xd3a17100 irq 43
[    1.871395] ata2: DUMMY
[    1.871398] ata3: SATA max UDMA/133 abar m2048@0xd3a17000 port 0xd3a17200 irq 43
[    1.871399] ata4: DUMMY
[    1.871399] ata5: DUMMY
[    1.871400] ata6: DUMMY
[    1.877789] usb 1-1.3: New USB device found, idVendor=0489, idProduct=e032
[    1.877796] usb 1-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.877799] usb 1-1.3: Product: BCM20702A0
[    1.877802] usb 1-1.3: Manufacturer: Broadcom Corp
[    1.877805] usb 1-1.3: SerialNumber: C0143DD3CA80
[    1.950356] usb 1-1.4: new high-speed USB device number 5 using ehci_hcd
[    2.042852] usb 1-1.4: New USB device found, idVendor=0bda, idProduct=0129
[    2.042859] usb 1-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.042863] usb 1-1.4: Product: USB2.0-CRW
[    2.042866] usb 1-1.4: Manufacturer: Generic
[    2.042869] usb 1-1.4: SerialNumber: 20100201396000000
[    2.114027] usb 2-1.6: new high-speed USB device number 3 using ehci_hcd
[    2.189789] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.196368] ata1.00: failed to enable AA (error_mask=0x1)
[    2.196377] ata1.00: ATA-8: ST1000LM024 HN-M101MBB, 2AR10001, max UDMA/100
[    2.196381] ata1.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    2.202977] ata1.00: failed to enable AA (error_mask=0x1)
[    2.202990] ata1.00: configured for UDMA/100
[    2.210000] scsi 0:0:0:0: Direct-Access     ATA      ST1000LM024 HN-M 2AR1 PQ: 0 ANSI: 5
[    2.210164] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.210168] sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    2.210170] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    2.210379] sd 0:0:0:0: [sda] Write Protect is off
[    2.210382] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.210494] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.214820] usb 2-1.6: New USB device found, idVendor=04f2, idProduct=b2e1
[    2.214827] usb 2-1.6: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.214831] usb 2-1.6: Product: Lenovo EasyCamera
[    2.214834] usb 2-1.6: Manufacturer: Vimicro Corp.
[    2.483938]  sda: sda1 sda2 sda3 < sda5 sda6 sda7 sda8 sda9 >
[    2.485172] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.529409] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.532569] ata3.00: ATAPI: PLDS DVD-RW DS8A8SH, KL31, max UDMA/100
[    2.533525] ata3.00: configured for UDMA/100
[    2.541543] scsi 2:0:0:0: CD-ROM            PLDS     DVD-RW DS8A8SH   KL31 PQ: 0 ANSI: 5
[    2.550930] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.550937] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.551111] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    2.551270] sr 2:0:0:0: Attached scsi generic sg1 type 5
[   11.093214] EXT4-fs (sda5): INFO: recovery required on readonly filesystem
[   11.093217] EXT4-fs (sda5): write access will be enabled during recovery
[   13.686923] EXT4-fs (sda5): orphan cleanup on readonly fs
[   13.686930] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1183159
[   13.686977] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1183076
[   13.702781] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1180456
[   13.702864] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1180455
[   13.702872] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1180443
[   13.702876] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1180441
[   13.702880] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1180386
[   13.702884] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1180385
[   13.702888] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1180384
[   13.702892] EXT4-fs (sda5): 9 orphan inodes deleted
[   13.702893] EXT4-fs (sda5): recovery complete
[   13.885889] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[   15.370480] init: ureadahead main process (368) terminated with status 5
[   17.113272] Adding 4881404k swap on /dev/sda6.  Priority:-1 extents:1 across:4881404k 
[   19.903408] udevd[442]: starting version 175
[   21.590807] lp: driver loaded but no devices found
[   21.949391] acpi_handle_hack: Setting new ACPI handle for discrete video card
[   22.905080] ACPI Warning: 0x0000000000000460-0x000000000000047f SystemIO conflicts with Region \PMIO 1 (20120320/utaddress-251)
[   22.905086] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   22.905096] lpc_ich: Resource conflict(s) found affecting iTCO_wdt
[   22.905099] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20120320/utaddress-251)
[   22.905101] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   22.905104] ACPI Warning: 0x0000000000000500-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20120320/utaddress-251)
[   22.905106] ACPI Warning: 0x0000000000000500-0x000000000000053f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 2 (20120320/utaddress-251)
[   22.905117] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   22.905118] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   23.034417] lib80211: common routines for IEEE802.11 drivers
[   23.034420] lib80211_crypt: registered algorithm 'NULL'
[   23.069649] mei 0000:00:16.0: setting latency timer to 64
[   23.069702] mei 0000:00:16.0: irq 44 for MSI/MSI-X
[   23.074782] mei 0000:00:16.0: wd: failed to find the client
[   23.237617] input: Ideapad extra buttons as /devices/platform/ideapad/input/input9
[   23.270370] microcode: CPU0 sig=0x306a9, pf=0x10, revision=0x13
[   23.285353] Qualcomm Atheros(R) AR816x/AR817x PCI-E Ethernet Network Driver
[   23.296315] alx 0000:02:00.0: alx(b8:88:e3:94:bf:12): Qualcomm Atheros Ethernet Network Connection
[   23.436298] wl: module license 'MIXED/Proprietary' taints kernel.
[   23.436302] Disabling lock debugging due to kernel taint
[   23.636859] microcode: CPU1 sig=0x306a9, pf=0x10, revision=0x13
[   23.637796] microcode: CPU2 sig=0x306a9, pf=0x10, revision=0x13
[   23.638680] microcode: CPU3 sig=0x306a9, pf=0x10, revision=0x13
[   23.639525] microcode: CPU4 sig=0x306a9, pf=0x10, revision=0x13
[   23.640305] microcode: CPU5 sig=0x306a9, pf=0x10, revision=0x13
[   23.641068] microcode: CPU6 sig=0x306a9, pf=0x10, revision=0x13
[   23.641861] microcode: CPU7 sig=0x306a9, pf=0x10, revision=0x13
[   23.642675] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   24.060961] psmouse serio1: elantech: assuming hardware version 3 (with firmware version 0x450f02)
[   24.083814] psmouse serio1: elantech: Synaptics capabilities query result 0x78, 0x17, 0x0b.
[   24.203600] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio1/input/input10
[   24.253590] lib80211_crypt: registered algorithm 'TKIP'
[   24.395253] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 5.100.82.112
[   24.475785] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   25.176261] hda_codec: CX20590: BIOS auto-probing.
[   25.200581] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   25.200721] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   25.200758] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   25.369776] type=1400 audit(1365449658.993:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=703 comm="apparmor_parser"
[   25.369808] type=1400 audit(1365449658.993:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=642 comm="apparmor_parser"
[   25.369823] type=1400 audit(1365449658.993:4): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=700 comm="apparmor_parser"
[   25.370045] type=1400 audit(1365449658.993:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=703 comm="apparmor_parser"
[   25.370075] type=1400 audit(1365449658.993:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=642 comm="apparmor_parser"
[   25.370090] type=1400 audit(1365449658.993:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=700 comm="apparmor_parser"
[   25.370196] type=1400 audit(1365449658.993:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=703 comm="apparmor_parser"
[   25.370226] type=1400 audit(1365449658.993:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=642 comm="apparmor_parser"
[   25.370241] type=1400 audit(1365449658.993:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=700 comm="apparmor_parser"
[   25.671664] Bluetooth: Core ver 2.16
[   25.671678] NET: Registered protocol family 31
[   25.671679] Bluetooth: HCI device and connection manager initialized
[   25.671680] Bluetooth: HCI socket layer initialized
[   25.671681] Bluetooth: L2CAP socket layer initialized
[   25.671684] Bluetooth: SCO socket layer initialized
[   25.838833] usbcore: registered new interface driver btusb
[   25.880678] Bluetooth: can't load firmware, may not work correctly
[   25.896842] rts5139: module is from the staging directory, the quality is unknown, you have been warned.
[   25.900404] scsi6 : SCSI emulation for RTS5139 USB card reader
[   25.900528] usbcore: registered new interface driver rts5139
[   25.900583] scsi 6:0:0:0: Direct-Access     Generic- xD/SD/M.S.       1.00 PQ: 0 ANSI: 0 CCS
[   25.901105] sd 6:0:0:0: Attached scsi generic sg2 type 0
[   25.902307] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[   25.908170] Linux video capture interface: v2.00
[   26.061503] uvcvideo: Found UVC 1.00 device Lenovo EasyCamera (04f2:b2e1)
[   26.062519] input: Lenovo EasyCamera as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/input/input14
[   26.062586] usbcore: registered new interface driver uvcvideo
[   26.062587] USB Video Class driver (1.1.1)
[   29.144295] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   37.385722] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
[   49.801134] EXT4-fs (sda8): mounted filesystem with ordered data mode. Opts: (null)
[   50.101560] init: failsafe main process (954) killed by TERM signal
[   51.538663] type=1400 audit(1365449685.189:11): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1053 comm="apparmor_parser"
[   51.538937] type=1400 audit(1365449685.189:12): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1053 comm="apparmor_parser"
[   51.539088] type=1400 audit(1365449685.189:13): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1053 comm="apparmor_parser"
[   51.702519] type=1400 audit(1365449685.353:14): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1060 comm="apparmor_parser"
[   51.712034] type=1400 audit(1365449685.365:15): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1050 comm="apparmor_parser"
[   51.712249] type=1400 audit(1365449685.365:16): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=1050 comm="apparmor_parser"
[   51.731349] type=1400 audit(1365449685.385:17): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=1056 comm="apparmor_parser"
[   51.731679] type=1400 audit(1365449685.385:18): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=1056 comm="apparmor_parser"
[   51.732156] type=1400 audit(1365449685.385:19): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*//sanitized_helper" pid=1056 comm="apparmor_parser"
[   51.737698] type=1400 audit(1365449685.389:20): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1057 comm="apparmor_parser"
[   53.681722] ppdev: user-space parallel port driver
```

Is it possible to speed it up?

---

### Post by zero2xiii on 2013-04-11
Hay,

With a 5400rpm drive. I HIGHLY doubt it. Maybe try adding a SSD, or a small 7200rpm drive atleast to host the / partition. On my i7 similar spec laptop also with a 5400 drive I get similar boot times. On i7 desktop with 7200 host drive I get about 45-60 for a full boot to desktop. Including my time to type password. Both laptop and desktop has similar specs. (only more ram in desktop, but 32GB vs 16GB should not affect boot time that much).

Cheers

---

### Post by erik1001 on 2013-04-11
Thank you. At least I know I'm not the only one. I'll remove my 5400rpm hard drive soon and reduce number of partitions and I hope it will boot faster than now. Sadly, I don't have options to add SSD so 7200 rpm is the only way to get things better.

---

### Post by zero2xiii on 2013-04-13
Hay,

All good :).

Also note SATA2 vs SATA3 drives.
2 = 3Gb/s
3 = 6Gb/s transfer speed.

The SATA3 drives will also boot a slight bit faster if your mainboard supports SATA3

Cheers

---

