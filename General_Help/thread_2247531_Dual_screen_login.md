---
title: "Dual screen login?"
date: 2014-10-08
forum: General Help
---

### Post by d4m1r on 2014-10-08
Hey guys, something changed within the past month and partially screwed up my dual monitor setup...There was a 100+ package update pushed about a month back that I picked up and this has been happened every time at boot since.

The problem? I no longer get the login password prompt on BOTH my monitors. Only on my primary one (laptop) and not on my external Samsung monitor. Before, I would get the password prompt on both, log in, and Ubuntu would correctly remember that I want my laptop screen disabled and picture only shown on my external monitor. Now, at the LightDM login screen, I get a weird rendered purple screen that only even completes rendering (refreshes and displays correctly) when I move my mouse within my external monitor. And even then, it just shows the default wallpaper with an Ubuntu icon in the background and NO password prompt.

This is very annoying because I can't see what I am typing and have to look at my laptop screen while typing my password, and it is not directly beside my external monitor so....This work previously for 1+ years before being broken in the recent update...Has this happened to anyone else recently? Known issue?

---

### Post by d4m1r on 2014-10-09
Any ideas/suggestions guys? :(

---

### Post by mastablasta on 2014-10-09
graphics card? graphics drivers?  what drivers are now installed?

---

### Post by d4m1r on 2014-10-09
GPU = Intel 4000 HD

Default drivers for that gpu were automatically detected and installed by Ubuntu. Haven't manually touched anything....You think this could be related to my gpu driver installed?

---

### Post by mastablasta on 2014-10-09
ok so the only drivers are the ones provided in kernel since intel has opensource drivers for (most) of their chips. and the ones provided by kernel should be ok.

it does seem like some change in kernel could have caused this. you could try searching for any bugs reported relating to intel GPU. it could also be a lightdm bug. hard to say.

anything in dmesg log? anything in any of the logs? any possible errors on boot or similar?

---

### Post by d4m1r on 2014-10-09
Thanks for the reply. Find 3 short logs below so take a look and let me know for sure but there does seem to be some funny business going on with LightDM....


dmesg
```
[    0.000000] Initializing cgroup subsys cpuset 
[    0.000000] Initializing cgroup subsys cpu 
[    0.000000] Initializing cgroup subsys cpuacct 
[    0.000000] Linux version 3.13.0-36-generic (buildd@kissel) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #63~precise1-Ubuntu SMP Thu Sep 4 22:28:20 UTC 2014 (Ubuntu 3.13.0-36.63~precise1-generic 3.13.11.6) 
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-36-generic root=UUID=ff870fab-18e7-4850-bd2b-d73ad107be8c ro quiet splash vt.handoff=7 
[    0.000000] KERNEL supported cpus: 
[    0.000000]   Intel GenuineIntel 
[    0.000000]   AMD AuthenticAMD 
[    0.000000]   Centaur CentaurHauls 
[    0.000000] e820: BIOS-provided physical RAM map: 
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000008dfff] usable 
[    0.000000] BIOS-e820: [mem 0x000000000008e000-0x000000000008ffff] reserved 
[    0.000000] BIOS-e820: [mem 0x0000000000090000-0x000000000009fbff] usable 
[    0.000000] BIOS-e820: [mem 0x000000000009fc00-0x00000000000bffff] reserved 
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved 
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000001fffffff] usable 
[    0.000000] BIOS-e820: [mem 0x0000000020000000-0x00000000201fffff] reserved 
[    0.000000] BIOS-e820: [mem 0x0000000020200000-0x0000000040003fff] usable 
[    0.000000] BIOS-e820: [mem 0x0000000040004000-0x0000000040004fff] reserved 
[    0.000000] BIOS-e820: [mem 0x0000000040005000-0x000000008ad13fff] usable 
[    0.000000] BIOS-e820: [mem 0x000000008ad14000-0x000000008ad52fff] ACPI NVS 
[    0.000000] BIOS-e820: [mem 0x000000008ad53000-0x000000008ad68fff] usable 
[    0.000000] BIOS-e820: [mem 0x000000008ad69000-0x000000008ad8efff] ACPI data 
[    0.000000] BIOS-e820: [mem 0x000000008ad8f000-0x000000008af8ffff] usable 
[    0.000000] BIOS-e820: [mem 0x000000008af90000-0x000000008affefff] reserved 
[    0.000000] BIOS-e820: [mem 0x000000008afff000-0x000000008affffff] usable 
[    0.000000] BIOS-e820: [mem 0x000000008b000000-0x000000008f9fffff] reserved 
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved 
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved 
[    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed03fff] reserved 
[    0.000000] BIOS-e820: [mem 0x00000000fed10000-0x00000000fed13fff] reserved 
[    0.000000] BIOS-e820: [mem 0x00000000fed18000-0x00000000fed19fff] reserved 
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved 
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved 
[    0.000000] BIOS-e820: [mem 0x00000000ff800000-0x00000000ffffffff] reserved 
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000026f5fffff] usable 
[    0.000000] NX (Execute Disable) protection: active 
[    0.000000] SMBIOS 2.4 present. 
[    0.000000] DMI: Apple Inc. MacBookPro9,2/Mac-6F01561E16C75D06, BIOS MBP91.88Z.00D3.B08.1208081132 08/08/2012 
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved 
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable 
[    0.000000] No AGP bridge found 
[    0.000000] e820: last_pfn = 0x26f600 max_arch_pfn = 0x400000000 
[    0.000000] MTRR default type: write-back 
[    0.000000] MTRR fixed ranges enabled: 
[    0.000000]   00000-9FFFF write-back 
[    0.000000]   A0000-BFFFF uncachable 
[    0.000000]   C0000-DFFFF write-protect 
[    0.000000]   E0000-FFFFF uncachable 
[    0.000000] MTRR variable ranges enabled: 
[    0.000000]   0 base 0C0000000 mask FC0000000 uncachable 
[    0.000000]   1 base 0A0000000 mask FE0000000 uncachable 
[    0.000000]   2 base 090000000 mask FF0000000 uncachable 
[    0.000000]   3 base 08C000000 mask FFC000000 uncachable 
[    0.000000]   4 base 08B000000 mask FFF000000 uncachable 
[    0.000000]   5 disabled 
[    0.000000]   6 disabled 
[    0.000000]   7 disabled 
[    0.000000]   8 disabled 
[    0.000000]   9 disabled 
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106 
[    0.000000] e820: last_pfn = 0x8b000 max_arch_pfn = 0x400000000 
[    0.000000] Scanning 1 areas for low memory corruption 
[    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 24576 
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff] 
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k 
[    0.000000] BRK [0x01fe4000, 0x01fe4fff] PGTABLE 
[    0.000000] BRK [0x01fe5000, 0x01fe5fff] PGTABLE 
[    0.000000] BRK [0x01fe6000, 0x01fe6fff] PGTABLE 
[    0.000000] init_memory_mapping: [mem 0x26f400000-0x26f5fffff] 
[    0.000000]  [mem 0x26f400000-0x26f5fffff] page 2M 
[    0.000000] BRK [0x01fe7000, 0x01fe7fff] PGTABLE 
[    0.000000] init_memory_mapping: [mem 0x26c000000-0x26f3fffff] 
[    0.000000]  [mem 0x26c000000-0x26f3fffff] page 2M 
[    0.000000] init_memory_mapping: [mem 0x200000000-0x26bffffff] 
[    0.000000]  [mem 0x200000000-0x26bffffff] page 2M 
[    0.000000] BRK [0x01fe8000, 0x01fe8fff] PGTABLE 
[    0.000000] init_memory_mapping: [mem 0x00100000-0x1fffffff] 
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k 
[    0.000000]  [mem 0x00200000-0x1fffffff] page 2M 
[    0.000000] init_memory_mapping: [mem 0x20200000-0x40003fff] 
[    0.000000]  [mem 0x20200000-0x3fffffff] page 2M 
[    0.000000]  [mem 0x40000000-0x40003fff] page 4k 
[    0.000000] BRK [0x01fe9000, 0x01fe9fff] PGTABLE 
[    0.000000] init_memory_mapping: [mem 0x40005000-0x8ad13fff] 
[    0.000000]  [mem 0x40005000-0x401fffff] page 4k 
[    0.000000]  [mem 0x40200000-0x8abfffff] page 2M 
[    0.000000]  [mem 0x8ac00000-0x8ad13fff] page 4k 
[    0.000000] init_memory_mapping: [mem 0x8ad53000-0x8ad68fff] 
[    0.000000]  [mem 0x8ad53000-0x8ad68fff] page 4k 
[    0.000000] init_memory_mapping: [mem 0x8ad8f000-0x8af8ffff] 
[    0.000000]  [mem 0x8ad8f000-0x8af8ffff] page 4k 
[    0.000000] init_memory_mapping: [mem 0x8afff000-0x8affffff] 
[    0.000000]  [mem 0x8afff000-0x8affffff] page 4k 
[    0.000000] init_memory_mapping: [mem 0x100000000-0x1ffffffff] 
[    0.000000]  [mem 0x100000000-0x1ffffffff] page 2M 
[    0.000000] RAMDISK: [mem 0x35bde000-0x36de6fff] 
[    0.000000] ACPI: RSDP 00000000000fe020 000024 (v02 APPLE ) 
[    0.000000] ACPI: XSDT 000000008ad8e1c0 0000B4 (v01 APPLE   Apple00 00000000      01000013) 
[    0.000000] ACPI: FACP 000000008ad8c000 0000F4 (v04 APPLE   Apple00 00000000 Loki 0000005F) 
[    0.000000] ACPI: DSDT 000000008ad82000 004D53 (v01 APPLE  MacBookP 00090001 INTL 20100915) 
[    0.000000] ACPI: FACS 000000008ad1e000 000040 
[    0.000000] ACPI: HPET 000000008ad8b000 000038 (v01 APPLE   Apple00 00000001 Loki 0000005F) 
[    0.000000] ACPI: APIC 000000008ad8a000 0000BC (v02 APPLE   Apple00 00000001 Loki 0000005F) 
[    0.000000] ACPI: SBST 000000008ad88000 000030 (v01 APPLE   Apple00 00000001 Loki 0000005F) 
[    0.000000] ACPI: ECDT 000000008ad87000 000053 (v01 APPLE   Apple00 00000001 Loki 0000005F) 
[    0.000000] ACPI: SSDT 000000008ad7f000 0002E0 (v01 APPLE  SataAhci 00001000 INTL 20100915) 
[    0.000000] ACPI: SSDT 000000008ad7e000 000024 (v01 APPLE   SmcDppt 00001000 INTL 20100915) 
[    0.000000] ACPI: SSDT 000000008ad79000 000D20 (v01 APPLE    UsbPpt 00001000 INTL 20100915) 
[    0.000000] ACPI: SSDT 000000008ad77000 000159 (v02 APPLE     IGHda 00001000 INTL 20100915) 
[    0.000000] ACPI: SSDT 000000008ad75000 000032 (v01 APPLE    SsdtS3 00001000 INTL 20100915) 
[    0.000000] ACPI: SSDT 000000008ad73000 0015EB (v02 APPLE  SsdtIGPU 00001000 INTL 20100915) 
[    0.000000] ACPI: SSDT 000000008ad70000 000AE6 (v01 APPLE  TbtPEG10 00001000 INTL 20100915) 
[    0.000000] ACPI: SSDT 000000008ad6d000 000615 (v01  PmRef  Cpu0Ist 00003000 INTL 20100915) 
[    0.000000] ACPI: SSDT 000000008ad6c000 000B3D (v01  PmRef    CpuPm 00003000 INTL 20100915) 
[    0.000000] ACPI: SSDT 000000008ad6b000 000315 (v01  PmRef  Cpu0Tst 00003000 INTL 20100915) 
[    0.000000] ACPI: SSDT 000000008ad6a000 00037A (v01  PmRef    ApTst 00003000 INTL 20100915) 
[    0.000000] ACPI: DMAR 000000008ad69000 000088 (v01 APPLE      IVB  00000001 AAPL 00000001) 
[    0.000000] ACPI: MCFG 000000008ad89000 00003C (v01 APPLE   Apple00 00000001 Loki 0000005F) 
[    0.000000] ACPI: Local APIC address 0xfee00000 
[    0.000000] No NUMA configuration found 
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000026f5fffff] 
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x26f5fffff] 
[    0.000000]   NODE_DATA [mem 0x26f5f3000-0x26f5f7fff] 
[    0.000000]  [ffffea0000000000-ffffea0009bfffff] PMD -> [ffff880266c00000-ffff88026ebfffff] on node 0 
[    0.000000] Zone ranges: 
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff] 
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff] 
[    0.000000]   Normal   [mem 0x100000000-0x26f5fffff] 
[    0.000000] Movable zone start for each node 
[    0.000000] Early memory node ranges 
[    0.000000]   node   0: [mem 0x00001000-0x0008dfff] 
[    0.000000]   node   0: [mem 0x00090000-0x0009efff] 
[    0.000000]   node   0: [mem 0x00100000-0x1fffffff] 
[    0.000000]   node   0: [mem 0x20200000-0x40003fff] 
[    0.000000]   node   0: [mem 0x40005000-0x8ad13fff] 
[    0.000000]   node   0: [mem 0x8ad53000-0x8ad68fff] 
[    0.000000]   node   0: [mem 0x8ad8f000-0x8af8ffff] 
[    0.000000]   node   0: [mem 0x8afff000-0x8affffff] 
[    0.000000]   node   0: [mem 0x100000000-0x26f5fffff] 
[    0.000000] On node 0 totalpages: 2073287 
[    0.000000]   DMA zone: 64 pages used for memmap 
[    0.000000]   DMA zone: 21 pages reserved 
[    0.000000]   DMA zone: 3996 pages, LIFO batch:0 
[    0.000000]   DMA32 zone: 8821 pages used for memmap 
[    0.000000]   DMA32 zone: 564523 pages, LIFO batch:31 
[    0.000000]   Normal zone: 23512 pages used for memmap 
[    0.000000]   Normal zone: 1504768 pages, LIFO batch:31 
[    0.000000] ACPI: PM-Timer IO Port: 0x408 
[    0.000000] ACPI: Local APIC address 0xfee00000 
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled) 
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled) 
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] enabled) 
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled) 
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0xff] disabled) 
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0xff] disabled) 
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0xff] disabled) 
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0xff] disabled) 
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1]) 
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1]) 
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1]) 
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] high edge lint[0x1]) 
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x05] high edge lint[0x1]) 
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x06] high edge lint[0x1]) 
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x07] high edge lint[0x1]) 
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x08] high edge lint[0x1]) 
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0]) 
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23 
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl) 
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level) 
[    0.000000] ACPI: IRQ0 used by override. 
[    0.000000] ACPI: IRQ2 used by override. 
[    0.000000] ACPI: IRQ9 used by override. 
[    0.000000] Using ACPI (MADT) for SMP configuration information 
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000 
[    0.000000] smpboot: Allowing 8 CPUs, 4 hotplug CPUs 
[    0.000000] nr_irqs_gsi: 40 
[    0.000000] PM: Registered nosave memory: [mem 0x0008e000-0x0008ffff] 
[    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff] 
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000bffff] 
[    0.000000] PM: Registered nosave memory: [mem 0x000c0000-0x000dffff] 
[    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff] 
[    0.000000] PM: Registered nosave memory: [mem 0x20000000-0x201fffff] 
[    0.000000] PM: Registered nosave memory: [mem 0x40004000-0x40004fff] 
[    0.000000] PM: Registered nosave memory: [mem 0x8ad14000-0x8ad52fff] 
[    0.000000] PM: Registered nosave memory: [mem 0x8ad69000-0x8ad8efff] 
[    0.000000] PM: Registered nosave memory: [mem 0x8af90000-0x8affefff] 
[    0.000000] PM: Registered nosave memory: [mem 0x8b000000-0x8f9fffff] 
[    0.000000] PM: Registered nosave memory: [mem 0x8fa00000-0xdfffffff] 
[    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff] 
[    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfebfffff] 
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff] 
[    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfecfffff] 
[    0.000000] PM: Registered nosave memory: [mem 0xfed00000-0xfed03fff] 
[    0.000000] PM: Registered nosave memory: [mem 0xfed04000-0xfed0ffff] 
[    0.000000] PM: Registered nosave memory: [mem 0xfed10000-0xfed13fff] 
[    0.000000] PM: Registered nosave memory: [mem 0xfed14000-0xfed17fff] 
[    0.000000] PM: Registered nosave memory: [mem 0xfed18000-0xfed19fff] 
[    0.000000] PM: Registered nosave memory: [mem 0xfed1a000-0xfed1bfff] 
[    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff] 
[    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff] 
[    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff] 
[    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xff7fffff] 
[    0.000000] PM: Registered nosave memory: [mem 0xff800000-0xffffffff] 
[    0.000000] e820: [mem 0x8fa00000-0xdfffffff] available for PCI devices 
[    0.000000] Booting paravirtualized kernel on bare hardware 
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1 
[    0.000000] PERCPU: Embedded 29 pages/cpu @ffff88026f200000 s86336 r8192 d24256 u262144 
[    0.000000] pcpu-alloc: s86336 r8192 d24256 u262144 alloc=1*2097152 
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7  
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2040869 
[    0.000000] Policy zone: Normal 
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-36-generic root=UUID=ff870fab-18e7-4850-bd2b-d73ad107be8c ro quiet splash vt.handoff=7 
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes) 
[    0.000000] xsave: enabled xstate_bv 0x7, cntxt size 0x340 
[    0.000000] Checking aperture... 
[    0.000000] No AGP bridge found 
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area 
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing! 
[    0.000000] Memory: 8059944K/8293148K available (7613K kernel code, 1138K rwdata, 3488K rodata, 1360K init, 1440K bss, 233204K reserved) 
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1 
[    0.000000] Hierarchical RCU implementation. 
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled. 
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8. 
[    0.000000]     Offload RCU callbacks from all CPUs 
[    0.000000]     Offload RCU callbacks from CPUs: 0-7. 
[    0.000000] NR_IRQS:16640 nr_irqs:744 16 
[    0.000000] Console: colour dummy device 80x25 
[    0.000000] console [tty0] enabled 
[    0.000000] allocated 33554432 bytes of page_cgroup 
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups 
[    0.000000] hpet clockevent registered 
[    0.000000] tsc: Fast TSC calibration using PIT 
[    0.004000] tsc: Detected 2494.301 MHz processor 
[    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 4988.60 BogoMIPS (lpj=9977204) 
[    0.000005] pid_max: default: 32768 minimum: 301 
[    0.000024] Security Framework initialized 
[    0.000040] AppArmor: AppArmor initialized 
[    0.000041] Yama: becoming mindful. 
[    0.000584] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes) 
[    0.002570] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes) 
[    0.003439] Mount-cache hash table entries: 16384 (order: 5, 131072 bytes) 
[    0.003450] Mountpoint-cache hash table entries: 16384 (order: 5, 131072 bytes) 
[    0.003637] Initializing cgroup subsys memory 
[    0.003642] Initializing cgroup subsys devices 
[    0.003643] Initializing cgroup subsys freezer 
[    0.003645] Initializing cgroup subsys blkio 
[    0.003646] Initializing cgroup subsys perf_event 
[    0.003648] Initializing cgroup subsys hugetlb 
[    0.003668] CPU: Physical Processor ID: 0 
[    0.003669] CPU: Processor Core ID: 0 
[    0.004031] mce: CPU supports 7 MCE banks 
[    0.004041] CPU0: Thermal monitoring enabled (TM1) 
[    0.004048] Last level iTLB entries: 4KB 512, 2MB 0, 4MB 0 
[    0.004048] Last level dTLB entries: 4KB 512, 2MB 32, 4MB 32 
[    0.004048] tlb_flushall_shift: 2 
[    0.004161] Freeing SMP alternatives memory: 32K (ffffffff81e72000 - ffffffff81e7a000) 
[    0.005299] ACPI: Core revision 20131115 
[    0.010956] ACPI: All ACPI Tables successfully acquired 
[    0.011164] ftrace: allocating 31488 entries in 124 pages 
[    0.025124] dmar: Host address width 36 
[    0.025126] dmar: DRHD base: 0x000000fed90000 flags: 0x0 
[    0.025133] dmar: IOMMU 0: reg_base_addr fed90000 ver 1:0 cap c0000020e60262 ecap f0101a 
[    0.025135] dmar: DRHD base: 0x000000fed91000 flags: 0x1 
[    0.025139] dmar: IOMMU 1: reg_base_addr fed91000 ver 1:0 cap c9008020660262 ecap f0105a 
[    0.025140] dmar: RMRR base: 0x0000008b800000 end: 0x0000008f9fffff 
[    0.025211] IOAPIC id 0 under DRHD base  0xfed91000 IOMMU 1 
[    0.025212] HPET id 0 under DRHD base 0xfed91000 
[    0.025213] [Firmware Bug]: ioapic 2 has no mapping iommu, interrupt remapping will be disabled 
[    0.025214] Not enable interrupt remapping 
[    0.025215] Failed to enable irq remapping.  You are vulnerable to irq-injection attacks. 
[    0.025670] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1 
[    0.065399] smpboot: CPU0: Intel(R) Core(TM) i5-3210M CPU @ 2.50GHz (fam: 06, model: 3a, stepping: 09) 
[    0.065406] TSC deadline timer enabled 
[    0.065416] Performance Events: PEBS fmt1+, 16-deep LBR, IvyBridge events, full-width counters, Intel PMU driver. 
[    0.065423] ... version:                3 
[    0.065424] ... bit width:              48 
[    0.065424] ... generic registers:      4 
[    0.065425] ... value mask:             0000ffffffffffff 
[    0.065426] ... max period:             0000ffffffffffff 
[    0.065427] ... fixed-purpose events:   3 
[    0.065428] ... event mask:             000000070000000f 
[    0.066926] x86: Booting SMP configuration: 
[    0.080542] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter. 
[    0.066928] .... node  #0, CPUs:      #1 #2 #3 
[    0.107728] x86: Booted up 1 node, 4 CPUs 
[    0.107732] smpboot: Total of 4 processors activated (19954.40 BogoMIPS) 
[    0.111113] devtmpfs: initialized 
[    0.115677] EVM: security.selinux 
[    0.115679] EVM: security.SMACK64 
[    0.115679] EVM: security.ima 
[    0.115680] EVM: security.capability 
[    0.115725] PM: Registering ACPI NVS region [mem 0x8ad14000-0x8ad52fff] (258048 bytes) 
[    0.116422] pinctrl core: initialized pinctrl subsystem 
[    0.116473] regulator-dummy: no parameters 
[    0.116503] RTC time: 18:23:55, date: 10/09/14 
[    0.116532] NET: Registered protocol family 16 
[    0.116627] cpuidle: using governor ladder 
[    0.116628] cpuidle: using governor menu 
[    0.116662] ACPI: bus type PCI registered 
[    0.116663] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5 
[    0.116718] PCI: MMCONFIG for domain 0000 [bus 00-9a] at [mem 0xe0000000-0xe9afffff] (base 0xe0000000) 
[    0.116721] PCI: MMCONFIG at [mem 0xe0000000-0xe9afffff] reserved in E820 
[    0.134530] PCI: Using configuration type 1 for base access 
[    0.135341] bio: create slab <bio-0> at 0 
[    0.135483] ACPI: Added _OSI(Module Device) 
[    0.135484] ACPI: Added _OSI(Processor Device) 
[    0.135486] ACPI: Added _OSI(3.0 _SCP Extensions) 
[    0.135487] ACPI: Added _OSI(Processor Aggregator Device) 
[    0.136577] ACPI : EC: EC description table is found, configuring boot EC 
[    0.140436] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored 
[    2.149979] ACPI: SSDT 000000008ad19190 0008AD (v01  PmRef  Cpu0Cst 00003001 INTL 20100915) 
[    2.150261] ACPI: Dynamic OEM Table Load: 
[    2.150263] ACPI: SSDT           (null) 0008AD (v01  PmRef  Cpu0Cst 00003001 INTL 20100915) 
[    2.151430] ACPI: SSDT 000000008ad1a710 0003A4 (v01  PmRef    ApIst 00003000 INTL 20100915) 
[    2.151743] ACPI: Dynamic OEM Table Load: 
[    2.151745] ACPI: SSDT           (null) 0003A4 (v01  PmRef    ApIst 00003000 INTL 20100915) 
[    2.155321] ACPI: SSDT 000000008ad18d90 000119 (v01  PmRef    ApCst 00003000 INTL 20100915) 
[    2.155594] ACPI: Dynamic OEM Table Load: 
[    2.155596] ACPI: SSDT           (null) 000119 (v01  PmRef    ApCst 00003000 INTL 20100915) 
[    2.159687] ACPI: Interpreter enabled 
[    2.159692] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20131115/hwxface-580) 
[    2.159696] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580) 
[    2.159706] ACPI: (supports S0 S3 S4 S5) 
[    2.159708] ACPI: Using IOAPIC for interrupt routing 
[    2.159731] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug 
[    2.159853] ACPI: No dock devices found. 
[    2.167005] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff]) 
[    2.167010] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI] 
[    2.167139] acpi PNP0A08:00: _OSC: OS now controls [PCIeHotplug PME AER PCIeCapability] 
[    2.167536] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-9a] only partially covers this bridge 
[    2.167645] PCI host bridge to bus 0000:00 
[    2.167647] pci_bus 0000:00: root bus resource [bus 00-ff] 
[    2.167649] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7] 
[    2.167650] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff] 
[    2.167652] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff] 
[    2.167653] pci_bus 0000:00: root bus resource [mem 0x8fa00000-0xfeafffff] 
[    2.167655] pci_bus 0000:00: root bus resource [mem 0xfed40000-0xfed44fff] 
[    2.167662] pci 0000:00:00.0: [8086:0154] type 00 class 0x060000 
[    2.167738] pci 0000:00:01.0: [8086:0151] type 01 class 0x060400 
[    2.167817] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold 
[    2.167853] pci 0000:00:01.0: System wakeup disabled by ACPI 
[    2.167883] pci 0000:00:02.0: [8086:0166] type 00 class 0x030000 
[    2.167893] pci 0000:00:02.0: reg 0x10: [mem 0xa0000000-0xa03fffff 64bit] 
[    2.167899] pci 0000:00:02.0: reg 0x18: [mem 0x90000000-0x9fffffff 64bit pref] 
[    2.167903] pci 0000:00:02.0: reg 0x20: [io  0x2000-0x203f] 
[    2.167983] pci 0000:00:14.0: [8086:1e31] type 00 class 0x0c0330 
[    2.168005] pci 0000:00:14.0: reg 0x10: [mem 0xa0800000-0xa080ffff 64bit] 
[    2.168076] pci 0000:00:14.0: PME# supported from D3hot D3cold 
[    2.168105] pci 0000:00:14.0: System wakeup disabled by ACPI 
[    2.168137] pci 0000:00:16.0: [8086:1e3a] type 00 class 0x078000 
[    2.168160] pci 0000:00:16.0: reg 0x10: [mem 0xa0817100-0xa081710f 64bit] 
[    2.168236] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold 
[    2.168302] pci 0000:00:1a.0: [8086:1e2d] type 00 class 0x0c0320 
[    2.168323] pci 0000:00:1a.0: reg 0x10: [mem 0xa0816c00-0xa0816fff] 
[    2.168414] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold 
[    2.168445] pci 0000:00:1a.0: System wakeup disabled by ACPI 
[    2.168475] pci 0000:00:1b.0: [8086:1e20] type 00 class 0x040300 
[    2.168491] pci 0000:00:1b.0: reg 0x10: [mem 0xa0810000-0xa0813fff 64bit] 
[    2.168558] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold 
[    2.168589] pci 0000:00:1b.0: System wakeup disabled by ACPI 
[    2.168617] pci 0000:00:1c.0: [8086:1e10] type 01 class 0x060400 
[    2.168695] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold 
[    2.168728] pci 0000:00:1c.0: System wakeup disabled by ACPI 
[    2.168755] pci 0000:00:1c.1: [8086:1e12] type 01 class 0x060400 
[    2.168832] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold 
[    2.168866] pci 0000:00:1c.1: System wakeup disabled by ACPI 
[    2.168895] pci 0000:00:1c.2: [8086:1e14] type 01 class 0x060400 
[    2.168973] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold 
[    2.169007] pci 0000:00:1c.2: System wakeup disabled by ACPI 
[    2.169043] pci 0000:00:1d.0: [8086:1e26] type 00 class 0x0c0320 
[    2.169064] pci 0000:00:1d.0: reg 0x10: [mem 0xa0816800-0xa0816bff] 
[    2.169153] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold 
[    2.169185] pci 0000:00:1d.0: System wakeup disabled by ACPI 
[    2.169215] pci 0000:00:1f.0: [8086:1e57] type 00 class 0x060100 
[    2.169369] pci 0000:00:1f.2: [8086:1e03] type 00 class 0x010601 
[    2.169386] pci 0000:00:1f.2: reg 0x10: [io  0x2098-0x209f] 
[    2.169395] pci 0000:00:1f.2: reg 0x14: [io  0x20bc-0x20bf] 
[    2.169403] pci 0000:00:1f.2: reg 0x18: [io  0x2090-0x2097] 
[    2.169411] pci 0000:00:1f.2: reg 0x1c: [io  0x20b8-0x20bb] 
[    2.169419] pci 0000:00:1f.2: reg 0x20: [io  0x2060-0x207f] 
[    2.169427] pci 0000:00:1f.2: reg 0x24: [mem 0xa0816000-0xa08167ff] 
[    2.169472] pci 0000:00:1f.2: PME# supported from D3hot 
[    2.169524] pci 0000:00:1f.3: [8086:1e22] type 00 class 0x0c0500 
[    2.169539] pci 0000:00:1f.3: reg 0x10: [mem 0xa0817000-0xa08170ff 64bit] 
[    2.169564] pci 0000:00:1f.3: reg 0x20: [io  0xefa0-0xefbf] 
[    2.169682] pci 0000:00:01.0: PCI bridge to [bus 04-9a] 
[    2.169686] pci 0000:00:01.0:   bridge window [io  0x3000-0x5fff] 
[    2.169689] pci 0000:00:01.0:   bridge window [mem 0xa0900000-0xacbfffff] 
[    2.169695] pci 0000:00:01.0:   bridge window [mem 0xacc00000-0xb8bfffff 64bit pref] 
[    2.169832] pci 0000:01:00.0: [14e4:16b4] type 00 class 0x020000 
[    2.169868] pci 0000:01:00.0: reg 0x10: [mem 0xa0400000-0xa040ffff 64bit pref] 
[    2.169897] pci 0000:01:00.0: reg 0x18: [mem 0xa0410000-0xa041ffff 64bit pref] 
[    2.170058] pci 0000:01:00.0: PME# supported from D0 D3hot D3cold 
[    2.170117] pci 0000:01:00.0: System wakeup disabled by ACPI 
[    2.170198] pci 0000:01:00.1: [14e4:16bc] type 00 class 0x080501 
[    2.170234] pci 0000:01:00.1: reg 0x10: [mem 0xa0420000-0xa042ffff 64bit pref] 
[    2.170412] pci 0000:01:00.1: PME# supported from D0 D3hot D3cold 
[    2.170452] pci 0000:01:00.1: System wakeup disabled by ACPI 
[    2.177662] pci 0000:00:1c.0: PCI bridge to [bus 01] 
[    2.177669] pci 0000:00:1c.0:   bridge window [mem 0xa0700000-0xa07fffff] 
[    2.177675] pci 0000:00:1c.0:   bridge window [mem 0xa0400000-0xa04fffff 64bit pref] 
[    2.177790] pci 0000:02:00.0: [14e4:4331] type 00 class 0x028000 
[    2.177819] pci 0000:02:00.0: reg 0x10: [mem 0xa0600000-0xa0603fff 64bit] 
[    2.177975] pci 0000:02:00.0: supports D1 D2 
[    2.177977] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold 
[    2.178016] pci 0000:02:00.0: System wakeup disabled by ACPI 
[    2.185620] pci 0000:00:1c.1: PCI bridge to [bus 02] 
[    2.185638] pci 0000:00:1c.1:   bridge window [mem 0xa0600000-0xa06fffff] 
[    2.185739] pci 0000:03:00.0: [11c1:5901] type 00 class 0x0c0010 
[    2.185777] pci 0000:03:00.0: reg 0x10: [mem 0xa0500000-0xa0500fff 64bit] 
[    2.185963] pci 0000:03:00.0: supports D1 D2 
[    2.185965] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold 
[    2.193612] pci 0000:00:1c.2: PCI bridge to [bus 03] 
[    2.193624] pci 0000:00:1c.2:   bridge window [mem 0xa0500000-0xa05fffff] 
[    2.194091] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11 
[    2.194136] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15) 
[    2.194178] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled. 
[    2.194220] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 *11 12 14 15) 
[    2.194261] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled. 
[    2.194303] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled. 
[    2.194344] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15) 
[    2.194385] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15) 
[    2.195517] ACPI: Enabled 4 GPEs in block 00 to 3F 
[    2.195525] ACPI: \_SB_.PCI0: notify handler is installed 
[    2.195584] Found 1 acpi root devices 
[    2.195617] ACPI : EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62 
[    2.195697] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none 
[    2.195700] vgaarb: loaded 
[    2.195701] vgaarb: bridge control possible 0000:00:02.0 
[    2.195830] SCSI subsystem initialized 
[    2.195873] libata version 3.00 loaded. 
[    2.195903] ACPI: bus type USB registered 
[    2.195918] usbcore: registered new interface driver usbfs 
[    2.195924] usbcore: registered new interface driver hub 
[    2.195948] usbcore: registered new device driver usb 
[    2.196039] PCI: Using ACPI for IRQ routing 
[    2.200586] PCI: pci_cache_line_size set to 64 bytes 
[    2.200727] e820: reserve RAM buffer [mem 0x0008e000-0x0008ffff] 
[    2.200728] e820: reserve RAM buffer [mem 0x0009fc00-0x0009ffff] 
[    2.200730] e820: reserve RAM buffer [mem 0x40004000-0x43ffffff] 
[    2.200731] e820: reserve RAM buffer [mem 0x8ad14000-0x8bffffff] 
[    2.200732] e820: reserve RAM buffer [mem 0x8ad69000-0x8bffffff] 
[    2.200734] e820: reserve RAM buffer [mem 0x8af90000-0x8bffffff] 
[    2.200735] e820: reserve RAM buffer [mem 0x8b000000-0x8bffffff] 
[    2.200736] e820: reserve RAM buffer [mem 0x26f600000-0x26fffffff] 
[    2.200809] NetLabel: Initializing 
[    2.200810] NetLabel:  domain hash size = 128 
[    2.200811] NetLabel:  protocols = UNLABELED CIPSOv4 
[    2.200822] NetLabel:  unlabeled traffic allowed by default 
[    2.200876] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0 
[    2.200881] hpet0: 8 comparators, 64-bit 14.318180 MHz counter 
[    2.202914] Switched to clocksource hpet 
[    2.206676] AppArmor: AppArmor Filesystem Enabled 
[    2.206697] pnp: PnP ACPI init 
[    2.206709] ACPI: bus type PNP registered 
[    2.206800] pnp 00:00: [dma 4] 
[    2.206822] pnp 00:00: Plug and Play ACPI device, IDs PNP0200 (active) 
[    2.206842] pnp 00:01: Plug and Play ACPI device, IDs INT0800 (active) 
[    2.206973] system 00:02: [mem 0xfed00000-0xfed003ff] has been reserved 
[    2.206976] system 00:02: Plug and Play ACPI device, IDs PNP0103 PNP0c01 (active) 
[    2.207001] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active) 
[    2.207031] system 00:04: [io  0x1000-0x100f] has been reserved 
[    2.207033] system 00:04: [io  0x0400-0x047f] could not be reserved 
[    2.207035] system 00:04: [io  0x0500-0x057f] has been reserved 
[    2.207037] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active) 
[    2.207056] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active) 
[    2.207079] pnp 00:06: Plug and Play ACPI device, IDs APP0001 (active) 
[    2.207133] pnp 00:07: Plug and Play ACPI device, IDs APP000b (active) 
[    2.207265] system 00:08: [mem 0xfed1c000-0xfed1ffff] has been reserved 
[    2.207267] system 00:08: [mem 0xfed10000-0xfed17fff] could not be reserved 
[    2.207269] system 00:08: [mem 0xfed18000-0xfed18fff] has been reserved 
[    2.207270] system 00:08: [mem 0xfed19000-0xfed19fff] has been reserved 
[    2.207272] system 00:08: [mem 0xe0000000-0xefffffff] has been reserved 
[    2.207274] system 00:08: [mem 0xfed20000-0xfed3ffff] has been reserved 
[    2.207276] system 00:08: [mem 0xfed90000-0xfed93fff] could not be reserved 
[    2.207277] system 00:08: [mem 0xfed45000-0xfed8ffff] has been reserved 
[    2.207279] system 00:08: [mem 0xff000000-0xffffffff] could not be reserved 
[    2.207281] system 00:08: [mem 0xfee00000-0xfeefffff] could not be reserved 
[    2.207283] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active) 
[    2.209411] system 00:09: [mem 0x20000000-0x201fffff] has been reserved 
[    2.209413] system 00:09: [mem 0x40000000-0x401fffff] could not be reserved 
[    2.209416] system 00:09: Plug and Play ACPI device, IDs PNP0c01 (active) 
[    2.209425] pnp: PnP ACPI: found 10 devices 
[    2.209426] ACPI: bus type PNP unregistered 
[    2.215638] pci 0000:00:01.0: PCI bridge to [bus 04-9a] 
[    2.215642] pci 0000:00:01.0:   bridge window [io  0x3000-0x5fff] 
[    2.215646] pci 0000:00:01.0:   bridge window [mem 0xa0900000-0xacbfffff] 
[    2.215650] pci 0000:00:01.0:   bridge window [mem 0xacc00000-0xb8bfffff 64bit pref] 
[    2.215656] pci 0000:00:1c.0: PCI bridge to [bus 01] 
[    2.215661] pci 0000:00:1c.0:   bridge window [mem 0xa0700000-0xa07fffff] 
[    2.215666] pci 0000:00:1c.0:   bridge window [mem 0xa0400000-0xa04fffff 64bit pref] 
[    2.215671] pci 0000:00:1c.1: PCI bridge to [bus 02] 
[    2.215676] pci 0000:00:1c.1:   bridge window [mem 0xa0600000-0xa06fffff] 
[    2.215685] pci 0000:00:1c.2: PCI bridge to [bus 03] 
[    2.215690] pci 0000:00:1c.2:   bridge window [mem 0xa0500000-0xa05fffff] 
[    2.215699] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7] 
[    2.215701] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff] 
[    2.215702] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff] 
[    2.215704] pci_bus 0000:00: resource 7 [mem 0x8fa00000-0xfeafffff] 
[    2.215706] pci_bus 0000:00: resource 8 [mem 0xfed40000-0xfed44fff] 
[    2.215707] pci_bus 0000:04: resource 0 [io  0x3000-0x5fff] 
[    2.215709] pci_bus 0000:04: resource 1 [mem 0xa0900000-0xacbfffff] 
[    2.215710] pci_bus 0000:04: resource 2 [mem 0xacc00000-0xb8bfffff 64bit pref] 
[    2.215712] pci_bus 0000:01: resource 1 [mem 0xa0700000-0xa07fffff] 
[    2.215714] pci_bus 0000:01: resource 2 [mem 0xa0400000-0xa04fffff 64bit pref] 
[    2.215715] pci_bus 0000:02: resource 1 [mem 0xa0600000-0xa06fffff] 
[    2.215717] pci_bus 0000:03: resource 1 [mem 0xa0500000-0xa05fffff] 
[    2.215745] NET: Registered protocol family 2 
[    2.215886] TCP established hash table entries: 65536 (order: 7, 524288 bytes) 
[    2.216029] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes) 
[    2.216136] TCP: Hash tables configured (established 65536 bind 65536) 
[    2.216152] TCP: reno registered 
[    2.216162] UDP hash table entries: 4096 (order: 5, 131072 bytes) 
[    2.216188] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes) 
[    2.216251] NET: Registered protocol family 1 
[    2.216263] pci 0000:00:02.0: Boot video device 
[    2.216329] pci 0000:00:14.0: can't derive routing for PCI INT A 
[    2.216331] pci 0000:00:14.0: PCI INT A: no GSI 
[    2.216422] pci 0000:00:14.0: can't derive routing for PCI INT A 
[    2.216929] PCI: CLS 256 bytes, default 64 
[    2.216984] Trying to unpack rootfs image as initramfs... 
[    2.487926] Freeing initrd memory: 18468K (ffff880035bde000 - ffff880036de7000) 
[    2.487966] PCI-DMA: Using software bounce buffering for IO (SWIOTLB) 
[    2.487968] software IO TLB [mem 0x86d14000-0x8ad14000] (64MB) mapped at [ffff880086d14000-ffff88008ad13fff] 
[    2.488159] microcode: CPU0 sig=0x306a9, pf=0x10, revision=0x15 
[    2.488169] microcode: CPU1 sig=0x306a9, pf=0x10, revision=0x15 
[    2.488173] microcode: CPU2 sig=0x306a9, pf=0x10, revision=0x15 
[    2.488178] microcode: CPU3 sig=0x306a9, pf=0x10, revision=0x15 
[    2.488224] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba 
[    2.488226] Scanning for low memory corruption every 60 seconds 
[    2.488468] Initialise system trusted keyring 
[    2.488504] audit: initializing netlink socket (disabled) 
[    2.488513] type=2000 audit(1412879037.480:1): initialized 
[    2.515342] HugeTLB registered 2 MB page size, pre-allocated 0 pages 
[    2.516281] zbud: loaded 
[    2.516400] VFS: Disk quotas dquot_6.5.2 
[    2.516431] Dquot-cache hash table entries: 512 (order 0, 4096 bytes) 
[    2.516771] fuse init (API version 7.22) 
[    2.516833] msgmni has been set to 15778 
[    2.516877] Key type big_key registered 
[    2.517296] Key type asymmetric registered 
[    2.517299] Asymmetric key parser 'x509' registered 
[    2.517324] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252) 
[    2.517360] io scheduler noop registered 
[    2.517363] io scheduler deadline registered (default) 
[    2.517383] io scheduler cfq registered 
[    2.517541] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X 
[    2.517689] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X 
[    2.517818] pcieport 0000:00:1c.1: irq 42 for MSI/MSI-X 
[    2.517940] pcieport 0000:00:1c.2: irq 43 for MSI/MSI-X 
[    2.518017] pcieport 0000:00:01.0: Signaling PME through PCIe PME interrupt 
[    2.518021] pcie_pme 0000:00:01.0:pcie01: service driver pcie_pme loaded 
[    2.518038] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt 
[    2.518039] pci 0000:01:00.0: Signaling PME through PCIe PME interrupt 
[    2.518041] pci 0000:01:00.1: Signaling PME through PCIe PME interrupt 
[    2.518045] pcie_pme 0000:00:1c.0:pcie01: service driver pcie_pme loaded 
[    2.518062] pcieport 0000:00:1c.1: Signaling PME through PCIe PME interrupt 
[    2.518064] pci 0000:02:00.0: Signaling PME through PCIe PME interrupt 
[    2.518068] pcie_pme 0000:00:1c.1:pcie01: service driver pcie_pme loaded 
[    2.518084] pcieport 0000:00:1c.2: Signaling PME through PCIe PME interrupt 
[    2.518086] pci 0000:03:00.0: Signaling PME through PCIe PME interrupt 
[    2.518090] pcie_pme 0000:00:1c.2:pcie01: service driver pcie_pme loaded 
[    2.518101] pci_hotplug: PCI Hot Plug PCI Core version: 0.5 
[    2.518113] pciehp: PCI Express Hot Plug Controller Driver version: 0.4 
[    2.518147] efifb: probing for efifb 
[    2.518148] efifb: cannot reserve video memory at 0xa6d60 
[    2.518152] efifb: framebuffer at 0xa6d60, mapped to 0xffff8800000a6d60, using 56k, total 64k 
[    2.518153] efifb: mode is 640x350x1, linelength=80, pages=1 
[    2.518154] efifb: scrolling: redraw 
[    2.518155] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0 
[    2.519441] Console: switching to colour frame buffer device 80x43 
[    2.520634] fb0: EFI VGA frame buffer device 
[    2.520643] intel_idle: MWAIT substates: 0x21120 
[    2.520645] intel_idle: v0.4 model 0x3A 
[    2.520646] intel_idle: lapic_timer_reliable_states 0xffffffff 
[    2.520734] ipmi message handler version 39.2 
[    2.520766] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared 
[    2.520803] ACPI: AC Adapter [ADP1] (on-line) 
[    2.520883] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0 
[    2.520897] ACPI: Lid Switch [LID0] 
[    2.520923] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1 
[    2.520926] ACPI: Power Button [PWRB] 
[    2.520950] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2 
[    2.520952] ACPI: Sleep Button [SLPB] 
[    2.520976] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3 
[    2.520978] ACPI: Power Button [PWRF] 
[    2.522308] GHES: HEST is not enabled! 
[    2.522383] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled 
[    2.524162] Linux agpgart interface v0.103 
[    2.525232] brd: module loaded 
[    2.525771] loop: module loaded 
[    2.526038] libphy: Fixed MDIO Bus: probed 
[    2.526103] tun: Universal TUN/TAP device driver, 1.6 
[    2.526104] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com> 
[    2.526139] PPP generic driver version 2.4.2 
[    2.526172] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver 
[    2.526175] ehci-pci: EHCI PCI platform driver 
[    2.526266] ehci-pci 0000:00:1a.0: EHCI Host Controller 
[    2.526271] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1 
[    2.526284] ehci-pci 0000:00:1a.0: debug port 2 
[    2.530191] ehci-pci 0000:00:1a.0: cache line size of 256 is not supported 
[    2.530215] ehci-pci 0000:00:1a.0: irq 23, io mem 0xa0816c00 
[    2.539396] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00 
[    2.539488] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002 
[    2.539492] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1 
[    2.539494] usb usb1: Product: EHCI Host Controller 
[    2.539495] usb usb1: Manufacturer: Linux 3.13.0-36-generic ehci_hcd 
[    2.539497] usb usb1: SerialNumber: 0000:00:1a.0 
[    2.539709] hub 1-0:1.0: USB hub found 
[    2.539728] hub 1-0:1.0: 2 ports detected 
[    2.540065] ehci-pci 0000:00:1d.0: EHCI Host Controller 
[    2.540077] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2 
[    2.540100] ehci-pci 0000:00:1d.0: debug port 2 
[    2.544035] ehci-pci 0000:00:1d.0: cache line size of 256 is not supported 
[    2.544065] ehci-pci 0000:00:1d.0: irq 22, io mem 0xa0816800 
[    2.555354] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00 
[    2.555426] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002 
[    2.555429] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1 
[    2.555431] usb usb2: Product: EHCI Host Controller 
[    2.555432] usb usb2: Manufacturer: Linux 3.13.0-36-generic ehci_hcd 
[    2.555434] usb usb2: SerialNumber: 0000:00:1d.0 
[    2.555586] hub 2-0:1.0: USB hub found 
[    2.555592] hub 2-0:1.0: 2 ports detected 
[    2.555708] ehci-platform: EHCI generic platform driver 
[    2.555720] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver 
[    2.555721] ohci-pci: OHCI PCI platform driver 
[    2.555732] ohci-platform: OHCI generic platform driver 
[    2.555739] uhci_hcd: USB Universal Host Controller Interface driver 
[    2.555820] xhci_hcd 0000:00:14.0: can't derive routing for PCI INT A 
[    2.555822] xhci_hcd 0000:00:14.0: PCI INT A: no GSI 
[    2.555851] xhci_hcd 0000:00:14.0: xHCI Host Controller 
[    2.555855] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3 
[    2.555972] xhci_hcd 0000:00:14.0: cache line size of 256 is not supported 
[    2.556001] xhci_hcd 0000:00:14.0: irq 44 for MSI/MSI-X 
[    2.556069] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002 
[    2.556071] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1 
[    2.556073] usb usb3: Product: xHCI Host Controller 
[    2.556074] usb usb3: Manufacturer: Linux 3.13.0-36-generic xhci_hcd 
[    2.556075] usb usb3: SerialNumber: 0000:00:14.0 
[    2.556190] hub 3-0:1.0: USB hub found 
[    2.556202] hub 3-0:1.0: 4 ports detected 
[    2.556356] xhci_hcd 0000:00:14.0: xHCI Host Controller 
[    2.556360] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 4 
[    2.556402] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003 
[    2.556404] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1 
[    2.556405] usb usb4: Product: xHCI Host Controller 
[    2.556406] usb usb4: Manufacturer: Linux 3.13.0-36-generic xhci_hcd 
[    2.556408] usb usb4: SerialNumber: 0000:00:14.0 
[    2.556490] hub 4-0:1.0: USB hub found 
[    2.556503] hub 4-0:1.0: 4 ports detected 
[    2.571414] i8042: PNP: No PS/2 controller found. Probing ports directly. 
[    2.851686] usb 1-1: new high-speed USB device number 2 using ehci-pci 
[    2.984170] usb 1-1: New USB device found, idVendor=8087, idProduct=0024 
[    2.984174] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0 
[    2.984326] hub 1-1:1.0: USB hub found 
[    2.984419] hub 1-1:1.0: 6 ports detected 
[    3.164091] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared 
[    3.164096] ACPI: Battery Slot [BAT0] (battery present) 
[    3.256204] usb 1-1.1: new high-speed USB device number 3 using ehci-pci 
[    3.361949] usb 1-1.1: New USB device found, idVendor=05ac, idProduct=8509 
[    3.361952] usb 1-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=3 
[    3.361954] usb 1-1.1: Product: FaceTime HD Camera (Built-in) 
[    3.361956] usb 1-1.1: Manufacturer: Apple Inc. 
[    3.361959] usb 1-1.1: SerialNumber: CC2CAT03CKDG6LL0 
[    3.488393] tsc: Refined TSC clocksource calibration: 2494.334 MHz 
[    3.608459] i8042: No controller found 
[    3.608602] mousedev: PS/2 mouse device common for all mice 
[    3.608950] rtc_cmos 00:05: RTC can wake from S4 
[    3.609106] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0 
[    3.609139] rtc_cmos 00:05: alarms up to one month, y3k, 242 bytes nvram, hpet irqs 
[    3.609209] device-mapper: uevent: version 1.0.3 
[    3.609277] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com 
[    3.609285] ledtrig-cpu: registered to indicate activity on CPUs 
[    3.609379] TCP: cubic registered 
[    3.609448] NET: Registered protocol family 10 
[    3.609582] NET: Registered protocol family 17 
[    3.609590] Key type dns_resolver registered 
[    3.609840] Loading compiled-in X.509 certificates 
[    3.610607] Loaded X.509 cert 'Magrathea: Glacier signing key: b034ba75c415b5d2034baf5402f924e68b580549' 
[    3.610621] registered taskstats version 1 
[    3.612535] Key type trusted registered 
[    3.614044] Key type encrypted registered 
[    3.615481] AppArmor: AppArmor sha1 policy hashing enabled 
[    3.615485] IMA: No TPM chip found, activating TPM-bypass! 
[    3.616002] regulator-dummy: disabling 
[    3.616050]   Magic number: 2:433:392 
[    3.616080] button PNP0C0D:00: hash matches 
[    3.616137] rtc_cmos 00:05: setting system clock to 2014-10-09 18:23:58 UTC (1412879038) 
[    3.616588] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found 
[    3.616589] EDD information not available. 
[    3.616628] PM: Hibernation image not present or could not be loaded. 
[    3.617472] Freeing unused kernel memory: 1360K (ffffffff81d1e000 - ffffffff81e72000) 
[    3.617474] Write protecting the kernel read-only data: 12288k 
[    3.618546] Freeing unused kernel memory: 568K (ffff880001772000 - ffff880001800000) 
[    3.619588] Freeing unused kernel memory: 608K (ffff880001b68000 - ffff880001c00000) 
[    3.630725] udevd[125]: starting version 175 
[    3.652478] pps_core: LinuxPPS API ver. 1 registered 
[    3.652481] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it> 
[    3.654179] PTP clock support registered 
[    3.657878] tg3.c:v3.134 (Sep 16, 2013) 
[    3.658919] ahci 0000:00:1f.2: version 3.0 
[    3.659051] ahci 0000:00:1f.2: irq 45 for MSI/MSI-X 
[    3.659105] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x3 impl SATA mode 
[    3.659109] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part ems apst  
[    3.663355] firewire_ohci 0000:03:00.0: irq 46 for MSI/MSI-X 
[    3.664523] sdhci: Secure Digital Host Controller Interface driver 
[    3.664525] sdhci: Copyright(c) Pierre Ossman 
[    3.667535] scsi0 : ahci 
[    3.672013] scsi1 : ahci 
[    3.674631] scsi2 : ahci 
[    3.674916] tg3 0000:01:00.0 eth0: Tigon3 [partno(BCM957765) rev 57785100] (PCI Express) MAC address a8:20:66:3e:c6:ef 
[    3.674920] tg3 0000:01:00.0 eth0: attached PHY is 57765 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[1]) 
[    3.674923] tg3 0000:01:00.0 eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1] 
[    3.674925] tg3 0000:01:00.0 eth0: dma_rwctrl[00000001] dma_mask[64-bit] 
[    3.675063] sdhci-pci 0000:01:00.1: SDHCI controller found [14e4:16bc] (rev 10) 
[    3.675267] sdhci-pci 0000:01:00.1: dummy supplies not allowed 
[    3.675269] mmc0: no vqmmc regulator found 
[    3.675271] sdhci-pci 0000:01:00.1: dummy supplies not allowed 
[    3.675273] mmc0: no vmmc regulator found 
[    3.675427] mmc0: SDHCI controller on PCI [0000:01:00.1] using ADMA 
[    3.675723] scsi3 : ahci 
[    3.675805] scsi4 : ahci 
[    3.675871] scsi5 : ahci 
[    3.675915] ata1: SATA max UDMA/133 abar m2048@0xa0816000 port 0xa0816100 irq 45 
[    3.675919] ata2: SATA max UDMA/133 abar m2048@0xa0816000 port 0xa0816180 irq 45 
[    3.675921] ata3: DUMMY 
[    3.675922] ata4: DUMMY 
[    3.675924] ata5: DUMMY 
[    3.675925] ata6: DUMMY 
[    3.716815] firewire_ohci 0000:03:00.0: added OHCI v1.10 device as card 0, 8 IR + 8 IT contexts, quirks 0x0 
[    3.820892] usb 2-1: new high-speed USB device number 2 using ehci-pci 
[    3.953692] usb 2-1: New USB device found, idVendor=8087, idProduct=0024 
[    3.953700] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0 
[    3.954131] hub 2-1:1.0: USB hub found 
[    3.954288] hub 2-1:1.0: 8 ports detected 
[    3.993062] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300) 
[    3.993086] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300) 
[    3.993483] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out 
[    3.993615] ata1.00: ATA-9: M4-CT128M4SSD2, 070H, max UDMA/100 
[    3.993618] ata1.00: 250069680 sectors, multi 16: LBA48 NCQ (depth 31/32), AA 
[    3.994089] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out 
[    3.994233] ata1.00: configured for UDMA/100 
[    3.994486] scsi 0:0:0:0: Direct-Access     ATA      M4-CT128M4SSD2   070H PQ: 0 ANSI: 5 
[    3.994654] sd 0:0:0:0: Attached scsi generic sg0 type 0 
[    3.994658] sd 0:0:0:0: [sda] 250069680 512-byte logical blocks: (128 GB/119 GiB) 
[    3.994780] sd 0:0:0:0: [sda] Write Protect is off 
[    3.994783] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00 
[    3.994889] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[    3.995018] ata2.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out 
[    3.995022] ata2.00: ATAPI: MATSHITADVD-R   UJ-8A8, HB14, max UDMA/100 
[    3.996530]  sda: sda1 sda2 sda3 sda4 sda5 
[    3.997034] sd 0:0:0:0: [sda] Attached SCSI disk 
[    3.997576] ata2.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out 
[    3.997580] ata2.00: configured for UDMA/100 
[    4.007890] scsi 1:0:0:0: CD-ROM            MATSHITA DVD-R   UJ-8A8   HB14 PQ: 0 ANSI: 5 
[    4.011128] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray 
[    4.011132] cdrom: Uniform CD-ROM driver Revision: 3.20 
[    4.011316] sr 1:0:0:0: Attached scsi CD-ROM sr0 
[    4.011429] sr 1:0:0:0: Attached scsi generic sg1 type 5 
[    4.045265] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null) 
[    4.096137] random: init urandom read with 51 bits of entropy available 
[    4.121142] usb 3-2: new high-speed USB device number 2 using xhci_hcd 
[    4.133652] init: ureadahead main process (319) terminated with status 5 
[    4.138080] usb 3-2: New USB device found, idVendor=2109, idProduct=3431 
[    4.138082] usb 3-2: New USB device strings: Mfr=0, Product=1, SerialNumber=0 
[    4.138084] usb 3-2: Product: USB2.0 Hub 
[    4.138436] hub 3-2:1.0: USB hub found 
[    4.138712] hub 3-2:1.0: 4 ports detected 
[    4.186884] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro 
[    4.217713] firewire_core 0000:03:00.0: created device fw0: GUID a82066fffeaf1218, S800 
[    4.217723] firewire_core 0000:03:00.0: phy config: new root=ffc0, gap_count=63 
[    4.219888] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready 
[    4.238611] udevd[424]: starting version 175 
[    4.271615] lp: driver loaded but no devices found 
[    4.326510] ppdev: user-space parallel port driver 
[    4.352281] Bluetooth: Core ver 2.17 
[    4.352383] NET: Registered protocol family 31 
[    4.352385] Bluetooth: HCI device and connection manager initialized 
[    4.352398] Bluetooth: HCI socket layer initialized 
[    4.352401] Bluetooth: L2CAP socket layer initialized 
[    4.352413] Bluetooth: SCO socket layer initialized 
[    4.358687] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20131115/utaddress-251) 
[    4.358695] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver 
[    4.358699] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251) 
[    4.358703] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver 
[    4.358704] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251) 
[    4.358707] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver 
[    4.358709] lpc_ich: Resource conflict(s) found affecting gpio_ich 
[    4.361872] Bluetooth: RFCOMM TTY layer initialized 
[    4.361882] Bluetooth: RFCOMM socket layer initialized 
[    4.361887] Bluetooth: RFCOMM ver 1.11 
[    4.363528] lib80211: common routines for IEEE802.11 drivers 
[    4.363531] lib80211_crypt: registered algorithm 'NULL' 
[    4.369696] Bluetooth: BNEP (Ethernet Emulation) ver 1.3 
[    4.369700] Bluetooth: BNEP filters: protocol multicast 
[    4.369707] Bluetooth: BNEP socket layer initialized 
[    4.391247] type=1400 audit(1412871839.271:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=611 comm="apparmor_parser" 
[    4.391255] type=1400 audit(1412871839.271:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=611 comm="apparmor_parser" 
[    4.391828] type=1400 audit(1412871839.271:4): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=611 comm="apparmor_parser" 
[    4.411084] mei_me 0000:00:16.0: irq 47 for MSI/MSI-X 
[    4.444409] apple_gmux: gmux device not present 
[    4.448431] [drm] Initialized drm 1.1.0 20060810 
[    4.476921] type=1400 audit(1412871839.355:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=861 comm="apparmor_parser" 
[    4.476929] type=1400 audit(1412871839.355:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=861 comm="apparmor_parser" 
[    4.476934] type=1400 audit(1412871839.355:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=861 comm="apparmor_parser" 
[    4.477441] type=1400 audit(1412871839.355:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=861 comm="apparmor_parser" 
[    4.477449] type=1400 audit(1412871839.355:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=861 comm="apparmor_parser" 
[    4.477719] type=1400 audit(1412871839.359:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=861 comm="apparmor_parser" 
[    4.490363] Switched to clocksource tsc 
[    4.491951] cfg80211: Calling CRDA to update world regulatory domain 
[    4.502689] random: nonblocking pool is initialized 
[    4.536828] wl: module license 'MIXED/Proprietary' taints kernel. 
[    4.536832] Disabling lock debugging due to kernel taint 
[    4.538136] wl: module verification failed: signature and/or  required key missing - tainting kernel 
[    4.541887] [drm] Memory usable by graphics device = 2048M 
[    4.541891] checking generic (a6d60 e000) vs hw (90000000 10000000) 
[    4.651886] INFO @wl_cfg80211_attach : Registered CFG80211 phy 
[    4.660799] lib80211_crypt: registered algorithm 'TKIP' 
[    4.669900] i915 0000:00:02.0: irq 48 for MSI/MSI-X 
[    4.669934] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013). 
[    4.669936] [drm] Driver supports precise vblank timestamp query. 
[    4.670042] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem 
[    4.694596] applesmc: key=374 fan=1 temp=22 index=21 acc=1 lux=2 kbd=1 
[    4.703053] input: applesmc as /devices/platform/applesmc.768/input/input4 
[    4.797913] [drm] GMBUS [i915 gmbus vga] timed out, falling back to bit banging on pin 2 
[    4.821627] eth1: Broadcom BCM4331 802.11 Hybrid Wireless Controller 6.20.155.1 (r326264) 
[    4.845003] init: failsafe main process (1012) killed by TERM signal 
[    4.855906] cfg80211: World regulatory domain updated: 
[    4.855910] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp) 
[    4.855912] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
[    4.855914] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm) 
[    4.855916] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm) 
[    4.855917] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
[    4.855919] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
[    4.885155] usb 4-2: new SuperSpeed USB device number 2 using xhci_hcd 
[    4.900814] usb 4-2: New USB device found, idVendor=2109, idProduct=8110 
[    4.900819] usb 4-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0 
[    4.900821] usb 4-2: Product: 4-Port USB 3.0 Hub 
[    4.900823] usb 4-2: Manufacturer: VIA Labs, Inc. 
[    4.903807] hub 4-2:1.0: USB hub found 
[    4.903905] hub 4-2:1.0: 4 ports detected 
[    4.908273] checking generic (a6d60 e000) vs hw (90000000 10000000) 
[    4.908376] fbcon: inteldrmfb (fb1) is primary device 
[    4.908377] fbcon: Remapping primary device, fb1, to tty 1-63 
[    4.940593] Linux video capture interface: v2.00 
[    4.950837] uvcvideo: Found UVC 1.00 device FaceTime HD Camera (Built-in) (05ac:8509) 
[    4.956077] tg3 0000:01:00.0: irq 49 for MSI/MSI-X 
[    4.956082] tg3 0000:01:00.0: irq 50 for MSI/MSI-X 
[    4.956086] tg3 0000:01:00.0: irq 51 for MSI/MSI-X 
[    4.956089] tg3 0000:01:00.0: irq 52 for MSI/MSI-X 
[    4.956093] tg3 0000:01:00.0: irq 53 for MSI/MSI-X 
[    4.957915] input: FaceTime HD Camera (Built-in) as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.0/input/input5 
[    4.958086] usbcore: registered new interface driver uvcvideo 
[    4.958087] USB Video Class driver (1.1.1) 
[    4.978199] usb 2-1.8: new high-speed USB device number 3 using ehci-pci 
[    5.070711] usb 2-1.8: New USB device found, idVendor=0424, idProduct=2513 
[    5.070712] usb 2-1.8: New USB device strings: Mfr=0, Product=0, SerialNumber=0 
[    5.070931] hub 2-1.8:1.0: USB hub found 
[    5.071115] hub 2-1.8:1.0: 3 ports detected 
[    5.142483] usb 3-2.1: new full-speed USB device number 3 using xhci_hcd 
[    5.163210] usb 3-2.1: New USB device found, idVendor=ffc0, idProduct=001f 
[    5.163212] usb 3-2.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0 
[    5.163213] usb 3-2.1: Product: Gaming II 
[    5.163213] usb 3-2.1: Manufacturer: Areson 
[    5.234545] usb 3-2.2: new full-speed USB device number 4 using xhci_hcd 
[    5.252645] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready 
[    5.252868] usb 3-2.2: New USB device found, idVendor=046d, idProduct=c223 
[    5.252870] usb 3-2.2: New USB device strings: Mfr=0, Product=2, SerialNumber=0 
[    5.252872] usb 3-2.2: Product: G15 Keyboard Hub 
[    5.252892] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready 
[    5.252967] usb 3-2.2: ep 0x81 - rounding interval to 1024 microframes, ep desc says 2040 microframes 
[    5.253187] hub 3-2.2:1.0: USB hub found 
[    5.253502] hub 3-2.2:1.0: 4 ports detected 
[    5.254133] IPv6: ADDRCONF(NETDEV_UP): eth2: link is not ready 
[    5.326613] usb 3-2.4: new high-speed USB device number 5 using xhci_hcd 
[    5.343746] usb 3-2.4: New USB device found, idVendor=05e3, idProduct=0608 
[    5.343747] usb 3-2.4: New USB device strings: Mfr=0, Product=1, SerialNumber=0 
[    5.343749] usb 3-2.4: Product: USB2.0 Hub 
[    5.344156] hub 3-2.4:1.0: USB hub found 
[    5.344388] hub 3-2.4:1.0: 4 ports detected 
[    5.377218] i915 0000:00:02.0: fb1: inteldrmfb frame buffer device 
[    5.377219] i915 0000:00:02.0: registered panic notifier 
[    5.391136] ACPI: Video Device [IGPU] (multi-head: yes  rom: no  post: no) 
[    5.391439] acpi device:0e: registered as cooling_device4 
[    5.391518] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6 
[    5.391599] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0 
[    5.391759] snd_hda_intel 0000:00:1b.0: irq 54 for MSI/MSI-X 
[    5.418105] autoconfig: line_outs=2 (0xb/0xa/0x0/0x0/0x0) type:speaker 
[    5.418108]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0) 
[    5.418110]    hp_outs=1 (0x9/0x0/0x0/0x0/0x0) 
[    5.418111]    mono: mono_out=0x0 
[    5.418112]    dig-out=0x10/0x0 
[    5.418113]    inputs: 
[    5.418114]      Mic=0xd 
[    5.425231] input: HDA Intel PCH HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10 
[    5.425317] input: HDA Intel PCH HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9 
[    5.425368] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8 
[    5.425412] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7 
[    5.430681] usb 2-1.8.1: new full-speed USB device number 4 using ehci-pci
```

lightdm.log
```
[+0.00s] DEBUG: Logging to /var/log/lightdm/lightdm.log 
[+0.00s] DEBUG: Starting Light Display Manager 1.2.3, UID=0 PID=2032 
[+0.00s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf 
[+0.00s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager 
[+0.00s] DEBUG: Registered seat module xlocal 
[+0.00s] DEBUG: Registered seat module xremote 
[+0.00s] DEBUG: Adding default seat 
[+0.00s] DEBUG: Starting seat 
[+0.00s] DEBUG: Starting new display for greeter 
[+0.00s] DEBUG: Starting local X display 
[+0.01s] DEBUG: X server :0 will replace Plymouth 
[+0.03s] DEBUG: Using VT 7 
[+0.03s] DEBUG: Activating VT 7 
[+0.03s] DEBUG: Logging to /var/log/lightdm/x-0.log 
[+0.03s] DEBUG: Writing X server authority to /var/run/lightdm/root/:0 
[+0.03s] DEBUG: Launching X Server 
[+0.03s] DEBUG: Launching process 2088: /usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch -background none 
[+0.03s] DEBUG: Waiting for ready signal from X server :0 
[+0.03s] DEBUG: Acquired bus name org.freedesktop.DisplayManager 
[+0.03s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0 
[+0.16s] DEBUG: Got signal 10 from process 2088 
[+0.16s] DEBUG: Got signal from X server :0 
[+0.16s] DEBUG: Stopping Plymouth, X server is ready 
[+0.18s] DEBUG: Connecting to XServer :0 
[+0.18s] DEBUG: Starting greeter 
[+0.18s] DEBUG: Started session 2381 with service 'lightdm', username 'lightdm' 
[+0.34s] DEBUG: Session 2381 authentication complete with return value 0: Success 
[+0.34s] DEBUG: Greeter authorized 
[+0.34s] DEBUG: Logging to /var/log/lightdm/x-0-greeter.log 
[+0.34s] DEBUG: Session 2381 running command /usr/lib/lightdm/lightdm-greeter-session /usr/sbin/unity-greeter 
[+1.05s] DEBUG: Greeter connected version=1.2.3 
[+1.05s] DEBUG: Greeter connected, display is ready 
[+1.05s] DEBUG: New display ready, switching to it 
[+1.05s] DEBUG: Activating VT 7 
[+1.93s] DEBUG: Greeter start authentication for damir 
[+1.93s] DEBUG: Started session 3593 with service 'lightdm', username 'damir' 
[+1.94s] DEBUG: Session 3593 got 1 message(s) from PAM 
[+1.94s] DEBUG: Prompt greeter with 1 message(s) 
[+150.45s] DEBUG: Continue authentication 
[+150.47s] DEBUG: Session 3593 authentication complete with return value 0: Success 
[+150.47s] DEBUG: Authenticate result for user damir: Success 
[+150.48s] DEBUG: User damir authorized 
[+150.48s] DEBUG: Greeter requests session ubuntu 
[+150.48s] DEBUG: Using session ubuntu 
[+150.48s] DEBUG: Stopping greeter 
[+150.48s] DEBUG: Session 2381: Sending SIGTERM 
[+150.50s] DEBUG: Greeter closed communication channel 
[+150.50s] DEBUG: Session 2381 exited with return value 0 
[+150.50s] DEBUG: Greeter quit 
[+150.51s] DEBUG: Dropping privileges to uid 1000 
[+150.51s] DEBUG: Restoring privileges 
[+150.52s] DEBUG: Dropping privileges to uid 1000 
[+150.52s] DEBUG: Writing /home/damir/.dmrc 
[+150.53s] DEBUG: Restoring privileges 
[+150.54s] DEBUG: Starting session ubuntu as user damir 
[+150.54s] DEBUG: Session 3593 running command /usr/sbin/lightdm-session gnome-session --session=ubuntu 
[+150.55s] DEBUG: Registering session with bus path /org/freedesktop/DisplayManager/Session0
```

auth.log
```
Oct  8 21:17:01 damir-macbook CRON[6079]: pam_unix(cron:session): session opened for user root by (uid=0) 
Oct  8 21:17:01 damir-macbook CRON[6079]: pam_unix(cron:session): session closed for user root 
Oct  8 22:17:01 damir-macbook CRON[7579]: pam_unix(cron:session): session opened for user root by (uid=0) 
Oct  8 22:17:01 damir-macbook CRON[7579]: pam_unix(cron:session): session closed for user root 
Oct  8 23:17:01 damir-macbook CRON[7603]: pam_unix(cron:session): session opened for user root by (uid=0) 
Oct  8 23:17:01 damir-macbook CRON[7603]: pam_unix(cron:session): session closed for user root 
Oct  9 00:15:17 damir-macbook polkitd(authority=local): Unregistered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session2 (system bus name :1.52, object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_CA.UTF-8) (disconnected from bus) 
Oct  9 18:07:14 damir-macbook lightdm: pam_unix(lightdm:session): session opened for user lightdm by (uid=0) 
Oct  9 18:07:14 damir-macbook lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :0 
Oct  9 18:07:16 damir-macbook lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "damir" 
Oct  9 18:07:16 damir-macbook dbus[576]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.24" (uid=104 pid=3549 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.13" (uid=0 pid=2137 comm="/usr/sbin/console-kit-daemon --no-daemon ") 
Oct  9 18:17:01 damir-macbook CRON[3818]: pam_unix(cron:session): session opened for user root by (uid=0) 
Oct  9 18:17:01 damir-macbook CRON[3818]: pam_unix(cron:session): session closed for user root 
Oct  9 18:24:00 damir-macbook lightdm: pam_unix(lightdm:session): session opened for user lightdm by (uid=0) 
Oct  9 18:24:00 damir-macbook lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :0 
Oct  9 18:24:02 damir-macbook lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "damir" 
Oct  9 18:24:02 damir-macbook dbus[506]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.25" (uid=104 pid=3623 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.13" (uid=0 pid=2151 comm="/usr/sbin/console-kit-daemon --no-daemon ") 
Oct  9 18:26:30 damir-macbook lightdm: pam_unix(lightdm:session): session closed for user lightdm 
Oct  9 18:26:30 damir-macbook lightdm: pam_unix(lightdm:session): session opened for user damir by (uid=0) 
Oct  9 18:26:30 damir-macbook lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :0 
Oct  9 18:26:32 damir-macbook polkitd(authority=local): Registered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session2 (system bus name :1.44 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_CA.UTF-8) 
Oct  9 18:26:34 damir-macbook dbus[506]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.57" (uid=1000 pid=4220 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.13" (uid=0 pid=2151 comm="/usr/sbin/console-kit-daemon --no-daemon ") 
Oct  9 18:59:42 damir-macbook sudo:    damir : TTY=pts/1 ; PWD=/home/damir ; USER=root ; COMMAND=/usr/bin/nautilus 
Oct  9 18:59:42 damir-macbook sudo: pam_unix(sudo:session): session opened for user root by damir(uid=1000)
```

---

### Post by d4m1r on 2014-10-10
Anyone? :(

---

### Post by d4m1r on 2014-10-14
Nobody? Still having this problem every time booting up Ubuntu...

---

