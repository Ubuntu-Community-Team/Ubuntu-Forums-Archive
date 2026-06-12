---
title: "Ubuntu 14.04 - Computer sometimes does not boot"
date: 2014-05-02
forum: General Help
---

### Post by MirkoCe on 2014-05-02
Hello,

I have a weird problem with my system. I start noticing random black screens and no possibility to open any tty terminal when trying to boot into my OS after having upgraded to Ubuntu 14.04. This occurs really randomly but frequently as soon as the grub menu should appear. A black screen is all I can see, nothing happens. If then I press letters on my keyboard they appear with a blinking cursor.
 After trying different solutions I have noticed that this occurs only with

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

as my setting. If I change it to "quiet" or "" the system boots perfectly everytime. 

Now, I would like to use plymouth but I seriously cannot understand what is the problem. My computer is a Lenovo U310 and I never noticed those problems in ubuntu 13.10. Could anybody helpe me? Sorry if no further information is provided at the moment, but I have no idea what could help.

Again, sorry for any mistake I am not a native speaker.

---

### Post by slooksterpsv on 2014-05-03
Wonderful english, you did very well! =D

When it fails to boot if you could get us a copy of the dmesg logs and put them on pastebin, we could look and see whats happening.

Here's a clip of my dmesg
```

dmesg | tail

[14168.176713] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[14169.493002] wlan0: authenticate with 08:86:3b:dc:5d:44
[14169.511898] wlan0: send auth to 08:86:3b:dc:5d:44 (try 1/3)
[14169.517920] wlan0: authenticated
[14169.518728] wlan0: associate with 08:86:3b:dc:5d:44 (try 1/3)
[14169.522215] wlan0: RX AssocResp from 08:86:3b:dc:5d:44 (capab=0x411 status=0 aid=7)
[14169.522367] wlan0: associated
[14549.950022] perf samples too long (5002 > 5000), lowering kernel.perf_event_max_sample_rate to 25000
[16780.883650] <3>[fglrx:firegl_lock_free] *ERROR* lock was not held by 25! (*lock=0x80000007)
[16780.883663] <3>[fglrx:firegl_unlock] *ERROR* firegl_lock_free failed!
[17799.016928] <3>[fglrx:firegl_lock_free] *ERROR* lock was not held by 25! (*lock=0x80000007)
[17799.016939] <3>[fglrx:firegl_unlock] *ERROR* firegl_lock_free failed!
[19830.549272] wlan0: Connection to AP 08:86:3b:dc:5d:44 lost


```

---

### Post by MirkoCe on 2014-05-05
Thank you so much!
At the moment I am FORTUNATELLY unable to reproduce the problem, I really hope it got fixed with the latest updates. I am starting to think that maybe it's the classic old story: when you want to show something to somebody else it never works (though this time it actually *does* work :D)
 Anyway, I will test it for a couple of day and I hope you can still help me if needed. :D

---

### Post by MirkoCe on 2014-05-14
Ok, after more than a week it happened again -.-
Here is my dmseg

```
 [    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.13.0-24-generic (buildd@batsu) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #47-Ubuntu SMP Fri May 2 23:30:00 UTC 2014 (Ubuntu 3.13.0-24.47-generic 3.13.9)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic root=UUID=6350cd06-e3d5-4207-b62c-ed03ac476452 ro quiet splash
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
[    0.000000] BIOS-e820: [mem 0x0000000040005000-0x00000000c5e9cfff] usable
[    0.000000] BIOS-e820: [mem 0x00000000c5e9d000-0x00000000c609efff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000c609f000-0x00000000d8385fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000d8386000-0x00000000daeeefff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000daeef000-0x00000000daf9efff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000daf9f000-0x00000000daffefff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000dafff000-0x00000000daffffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000db000000-0x00000000df9fffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed08000-0x00000000fed08fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed10000-0x00000000fed19fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff980000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000011f5fffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.7 present.
[    0.000000] DMI: LENOVO IdeaPad U310    /Lenovo          , BIOS 65CN15WW 06/05/2012
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x11f600 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0FF800000 mask FFF800000 write-protect
[    0.000000]   1 base 000000000 mask F80000000 write-back
[    0.000000]   2 base 080000000 mask FC0000000 write-back
[    0.000000]   3 base 0C0000000 mask FE0000000 write-back
[    0.000000]   4 base 0DC000000 mask FFC000000 uncachable
[    0.000000]   5 base 0DB000000 mask FFF000000 uncachable
[    0.000000]   6 base 100000000 mask FE0000000 write-back
[    0.000000]   7 base 11F800000 mask FFF800000 uncachable
[    0.000000]   8 base 11F600000 mask FFFE00000 uncachable
[    0.000000]   9 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820: last_pfn = 0xdb000 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000f0130-0x000f013f] mapped at [ffff8800000f0130]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000097000] 97000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01fdd000, 0x01fddfff] PGTABLE
[    0.000000] BRK [0x01fde000, 0x01fdefff] PGTABLE
[    0.000000] BRK [0x01fdf000, 0x01fdffff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x11f400000-0x11f5fffff]
[    0.000000]  [mem 0x11f400000-0x11f5fffff] page 2M
[    0.000000] BRK [0x01fe0000, 0x01fe0fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x11c000000-0x11f3fffff]
[    0.000000]  [mem 0x11c000000-0x11f3fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x100000000-0x11bffffff]
[    0.000000]  [mem 0x100000000-0x11bffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0x1fffffff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x1fffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x20200000-0x40003fff]
[    0.000000]  [mem 0x20200000-0x3fffffff] page 2M
[    0.000000]  [mem 0x40000000-0x40003fff] page 4k
[    0.000000] BRK [0x01fe1000, 0x01fe1fff] PGTABLE
[    0.000000] BRK [0x01fe2000, 0x01fe2fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x40005000-0xc5e9cfff]
[    0.000000]  [mem 0x40005000-0x401fffff] page 4k
[    0.000000]  [mem 0x40200000-0xc5dfffff] page 2M
[    0.000000]  [mem 0xc5e00000-0xc5e9cfff] page 4k
[    0.000000] init_memory_mapping: [mem 0xc609f000-0xd8385fff]
[    0.000000]  [mem 0xc609f000-0xc61fffff] page 4k
[    0.000000]  [mem 0xc6200000-0xd81fffff] page 2M
[    0.000000]  [mem 0xd8200000-0xd8385fff] page 4k
[    0.000000] init_memory_mapping: [mem 0xdafff000-0xdaffffff]
[    0.000000]  [mem 0xdafff000-0xdaffffff] page 4k
[    0.000000] RAMDISK: [mem 0x35b82000-0x36db8fff]
[    0.000000] ACPI: RSDP 00000000000f0150 000024 (v02 LENOVO)
[    0.000000] ACPI: XSDT 00000000daffe170 000094 (v01 LENOVO CB-01    06040000  LTP 00000000)
[    0.000000] ACPI: FACP 00000000dafee000 0000F4 (v03 LENOVO CB-01    06040000  LTP 00000000)
[    0.000000] ACPI: DSDT 00000000daff1000 00AD64 (v02 LENOVO  IVB-CPT 00000000 INTL 20061109)
[    0.000000] ACPI: FACS 00000000daf78000 000040
[    0.000000] ACPI: SLIC 00000000daffd000 000176 (v01 LENOVO CB-01    06040000  LTP 00000000)
[    0.000000] ACPI: SSDT 00000000daffc000 00052F (v01 LENOVO PtidDevc 00001000 INTL 20061109)
[    0.000000] ACPI: ASF! 00000000daff0000 0000A5 (v32 LENOVO CB-01    06040000  LTP 00000000)
[    0.000000] ACPI: HPET 00000000dafed000 000038 (v01 LENOVO CB-01    06040000  LTP 00000000)
[    0.000000] ACPI: APIC 00000000dafec000 000098 (v01 LENOVO CB-01    06040000  LTP 00000000)
[    0.000000] ACPI: MCFG 00000000dafeb000 00003C (v01 LENOVO CB-01    06040000  LTP 00000000)
[    0.000000] ACPI: FPDT 00000000dafea000 000064 (v01 LENOVO CB-01    06040000  LTP 00000000)
[    0.000000] ACPI: SSDT 00000000dafe9000 0008E4 (v01  PmRef  Cpu0Ist 00003000 INTL 20061109)
[    0.000000] ACPI: SSDT 00000000dafe8000 000A92 (v01  PmRef    CpuPm 00003000 INTL 20061109)
[    0.000000] ACPI: UEFI 00000000dafe7000 00003E (v01 LENOVO CB-01    06040000  LTP 00000000)
[    0.000000] ACPI: UEFI 00000000dafe6000 000042 (v01 PTL      COMBUF 00000001 PTL  00000001)
[    0.000000] ACPI: POAT 00000000dafe5000 000055 (v03 LENOVO CB-01    06040000  LTP 00000000)
[    0.000000] ACPI: UEFI 00000000dafe4000 0002E2 (v01 LENOVO CB-01    06040000  LTP 00000000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000011f5fffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x11f5fffff]
[    0.000000]   NODE_DATA [mem 0x11f5f5000-0x11f5f9fff]
[    0.000000]  [ffffea0000000000-ffffea00047fffff] PMD -> [ffff88011ac00000-ffff88011ebfffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x11f5fffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009cfff]
[    0.000000]   node   0: [mem 0x00100000-0x1fffffff]
[    0.000000]   node   0: [mem 0x20200000-0x40003fff]
[    0.000000]   node   0: [mem 0x40005000-0xc5e9cfff]
[    0.000000]   node   0: [mem 0xc609f000-0xd8385fff]
[    0.000000]   node   0: [mem 0xdafff000-0xdaffffff]
[    0.000000]   node   0: [mem 0x100000000-0x11f5fffff]
[    0.000000] On node 0 totalpages: 1013024
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3996 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 13759 pages used for memmap
[    0.000000]   DMA32 zone: 880516 pages, LIFO batch:31
[    0.000000]   Normal zone: 2008 pages used for memmap
[    0.000000]   Normal zone: 128512 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a301 base: 0xfed00000
[    0.000000] smpboot: Allowing 8 CPUs, 4 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: [mem 0x0009d000-0x0009dfff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x20000000-0x201fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x40004000-0x40004fff]
[    0.000000] PM: Registered nosave memory: [mem 0xc5e9d000-0xc609efff]
[    0.000000] PM: Registered nosave memory: [mem 0xd8386000-0xdaeeefff]
[    0.000000] PM: Registered nosave memory: [mem 0xdaeef000-0xdaf9efff]
[    0.000000] PM: Registered nosave memory: [mem 0xdaf9f000-0xdaffefff]
[    0.000000] PM: Registered nosave memory: [mem 0xdb000000-0xdf9fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xdfa00000-0xf7ffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf8000000-0xfbffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfc000000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfed07fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed08000-0xfed08fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed09000-0xfed0ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed10000-0xfed19fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1a000-0xfed1bfff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xff97ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xff980000-0xffffffff]
[    0.000000] e820: [mem 0xdfa00000-0xf7ffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 29 pages/cpu @ffff88011f200000 s86336 r8192 d24256 u262144
[    0.000000] pcpu-alloc: s86336 r8192 d24256 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 997172
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic root=UUID=6350cd06-e3d5-4207-b62c-ed03ac476452 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 3884280K/4052096K available (7338K kernel code, 1138K rwdata, 3388K rodata, 1332K init, 1440K bss, 167816K reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000]     Offload RCU callbacks from all CPUs
[    0.000000]     Offload RCU callbacks from CPUs: 0-7.
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 16777216 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.004000] tsc: Detected 1795.834 MHz processor
[    0.000003] Calibrating delay loop (skipped), value calculated using timer frequency.. 3591.66 BogoMIPS (lpj=7183336)
[    0.000006] pid_max: default: 32768 minimum: 301
[    0.000034] Security Framework initialized
[    0.000056] AppArmor: AppArmor initialized
[    0.000057] Yama: becoming mindful.
[    0.000469] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.001926] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.002573] Mount-cache hash table entries: 8192 (order: 4, 65536 bytes)
[    0.002581] Mountpoint-cache hash table entries: 8192 (order: 4, 65536 bytes)
[    0.002819] Initializing cgroup subsys memory
[    0.002826] Initializing cgroup subsys devices
[    0.002827] Initializing cgroup subsys freezer
[    0.002829] Initializing cgroup subsys blkio
[    0.002831] Initializing cgroup subsys perf_event
[    0.002834] Initializing cgroup subsys hugetlb
[    0.002864] CPU: Physical Processor ID: 0
[    0.002865] CPU: Processor Core ID: 0
[    0.002871] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.002871] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.002875] mce: CPU supports 7 MCE banks
[    0.002889] CPU0: Thermal monitoring enabled (TM1)
[    0.002900] Last level iTLB entries: 4KB 512, 2MB 0, 4MB 0
[    0.002900] Last level dTLB entries: 4KB 512, 2MB 32, 4MB 32
[    0.002900] tlb_flushall_shift: 2
[    0.003058] Freeing SMP alternatives memory: 32K (ffffffff81e6b000 - ffffffff81e73000)
[    0.004642] ACPI: Core revision 20131115
[    0.013525] ACPI: All ACPI Tables successfully acquired
[    0.013869] ftrace: allocating 28408 entries in 111 pages
[    0.032453] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.072126] smpboot: CPU0: Intel(R) Core(TM) i3-3217U CPU @ 1.80GHz (fam: 06, model: 3a, stepping: 09)
[    0.072135] TSC deadline timer enabled
[    0.075251] Performance Events: PEBS fmt1+, 16-deep LBR, IvyBridge events, full-width counters, Intel PMU driver.
[    0.075260] ... version:                3
[    0.075262] ... bit width:              48
[    0.075263] ... generic registers:      4
[    0.075264] ... value mask:             0000ffffffffffff
[    0.075266] ... max period:             0000ffffffffffff
[    0.075267] ... fixed-purpose events:   3
[    0.075268] ... event mask:             000000070000000f
[    0.077444] x86: Booting SMP configuration:
[    0.090710] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.077446] .... node  #0, CPUs:      #1 #2 #3
[    0.117231] x86: Booted up 1 node, 4 CPUs
[    0.117235] smpboot: Total of 4 processors activated (14366.67 BogoMIPS)
[    0.121541] devtmpfs: initialized
[    0.124774] EVM: security.selinux
[    0.124776] EVM: security.SMACK64
[    0.124777] EVM: security.ima
[    0.124779] EVM: security.capability
[    0.124835] PM: Registering ACPI NVS region [mem 0xdaeef000-0xdaf9efff] (720896 bytes)
[    0.125868] pinctrl core: initialized pinctrl subsystem
[    0.125933] regulator-dummy: no parameters
[    0.125968] RTC time: 14:06:08, date: 05/14/14
[    0.126009] NET: Registered protocol family 16
[    0.126121] cpuidle: using governor ladder
[    0.126123] cpuidle: using governor menu
[    0.126163] ACPI: bus type PCI registered
[    0.126165] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.126237] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.126240] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.135084] PCI: Using configuration type 1 for base access
[    0.135263] mtrr: your CPUs had inconsistent variable MTRR settings
[    0.135265] mtrr: probably your BIOS does not setup all CPUs.
[    0.135266] mtrr: corrected configuration.
[    0.136162] bio: create slab <bio-0> at 0
[    0.136348] ACPI: Added _OSI(Module Device)
[    0.136351] ACPI: Added _OSI(Processor Device)
[    0.136352] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.136354] ACPI: Added _OSI(Processor Aggregator Device)
[    0.145349] ACPI: Executed 2 blocks of module-level executable AML code
[    0.149227] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.149732] ACPI: SSDT 00000000dae8e018 00083B (v01  PmRef  Cpu0Cst 00003001 INTL 20061109)
[    0.150403] ACPI: Dynamic OEM Table Load:
[    0.150406] ACPI: SSDT           (null) 00083B (v01  PmRef  Cpu0Cst 00003001 INTL 20061109)
[    0.153591] ACPI: SSDT 00000000dae8fa98 000303 (v01  PmRef    ApIst 00003000 INTL 20061109)
[    0.154301] ACPI: Dynamic OEM Table Load:
[    0.154303] ACPI: SSDT           (null) 000303 (v01  PmRef    ApIst 00003000 INTL 20061109)
[    0.157421] ACPI: SSDT 00000000dae8dd98 000119 (v01  PmRef    ApCst 00003000 INTL 20061109)
[    0.158091] ACPI: Dynamic OEM Table Load:
[    0.158094] ACPI: SSDT           (null) 000119 (v01  PmRef    ApCst 00003000 INTL 20061109)
[    0.593648] ACPI: Interpreter enabled
[    0.593663] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)
[    0.593684] ACPI: (supports S0 S1 S3 S4 S5)
[    0.593686] ACPI: Using IOAPIC for interrupt routing
[    0.593721] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.593935] ACPI: No dock devices found.
[    0.603891] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    0.603898] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.604054] \_SB_.PCI0:_OSC invalid UUID
[    0.604056] _OSC request data:1 1f 0 
[    0.604061] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM
[    0.604753] PCI host bridge to bus 0000:00
[    0.604757] pci_bus 0000:00: root bus resource [bus 00-3e]
[    0.604759] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.604762] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.604764] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.604766] pci_bus 0000:00: root bus resource [mem 0xdfa00000-0xfeafffff]
[    0.604769] pci_bus 0000:00: root bus resource [mem 0xfed40000-0xfed44fff]
[    0.604779] pci 0000:00:00.0: [8086:0154] type 00 class 0x060000
[    0.604888] pci 0000:00:02.0: [8086:0166] type 00 class 0x030000
[    0.604903] pci 0000:00:02.0: reg 0x10: [mem 0xf0000000-0xf03fffff 64bit]
[    0.604912] pci 0000:00:02.0: reg 0x18: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.604918] pci 0000:00:02.0: reg 0x20: [io  0x3000-0x303f]
[    0.605060] pci 0000:00:14.0: [8086:1e31] type 00 class 0x0c0330
[    0.605092] pci 0000:00:14.0: reg 0x10: [mem 0xf0600000-0xf060ffff 64bit]
[    0.605188] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    0.605246] pci 0000:00:14.0: System wakeup disabled by ACPI
[    0.605288] pci 0000:00:16.0: [8086:1e3a] type 00 class 0x078000
[    0.605318] pci 0000:00:16.0: reg 0x10: [mem 0xf0615000-0xf061500f 64bit]
[    0.605417] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.605537] pci 0000:00:1a.0: [8086:1e2d] type 00 class 0x0c0320
[    0.605570] pci 0000:00:1a.0: reg 0x10: [mem 0xf0619000-0xf06193ff]
[    0.605691] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.605771] pci 0000:00:1a.0: System wakeup disabled by ACPI
[    0.605814] pci 0000:00:1b.0: [8086:1e20] type 00 class 0x040300
[    0.605836] pci 0000:00:1b.0: reg 0x10: [mem 0xf0610000-0xf0613fff 64bit]
[    0.605930] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.605991] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    0.606027] pci 0000:00:1c.0: [8086:1e10] type 01 class 0x060400
[    0.606133] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.606195] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.606232] pci 0000:00:1c.1: [8086:1e12] type 01 class 0x060400
[    0.606334] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.606394] pci 0000:00:1c.1: System wakeup disabled by ACPI
[    0.606429] pci 0000:00:1c.2: [8086:1e14] type 01 class 0x060400
[    0.606529] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.606591] pci 0000:00:1c.2: System wakeup disabled by ACPI
[    0.606642] pci 0000:00:1d.0: [8086:1e26] type 00 class 0x0c0320
[    0.606670] pci 0000:00:1d.0: reg 0x10: [mem 0xf0618000-0xf06183ff]
[    0.606783] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.606857] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.606897] pci 0000:00:1f.0: [8086:1e57] type 00 class 0x060100
[    0.607109] pci 0000:00:1f.2: [8086:1e03] type 00 class 0x010601
[    0.607136] pci 0000:00:1f.2: reg 0x10: [io  0x3088-0x308f]
[    0.607146] pci 0000:00:1f.2: reg 0x14: [io  0x3094-0x3097]
[    0.607157] pci 0000:00:1f.2: reg 0x18: [io  0x3080-0x3087]
[    0.607169] pci 0000:00:1f.2: reg 0x1c: [io  0x3090-0x3093]
[    0.607179] pci 0000:00:1f.2: reg 0x20: [io  0x3060-0x307f]
[    0.607190] pci 0000:00:1f.2: reg 0x24: [mem 0xf0617000-0xf06177ff]
[    0.607253] pci 0000:00:1f.2: PME# supported from D3hot
[    0.607336] pci 0000:00:1f.3: [8086:1e22] type 00 class 0x0c0500
[    0.607362] pci 0000:00:1f.3: reg 0x10: [mem 0xf0614000-0xf06140ff 64bit]
[    0.607394] pci 0000:00:1f.3: reg 0x20: [io  0xefa0-0xefbf]
[    0.607578] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    0.607756] pci 0000:02:00.0: [10ec:8136] type 00 class 0x020000
[    0.607829] pci 0000:02:00.0: reg 0x10: [io  0x2000-0x20ff]
[    0.607959] pci 0000:02:00.0: reg 0x18: [mem 0xf0404000-0xf0404fff 64bit pref]
[    0.608037] pci 0000:02:00.0: reg 0x20: [mem 0xf0400000-0xf0403fff 64bit pref]
[    0.608390] pci 0000:02:00.0: supports D1 D2
[    0.608392] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.608517] pci 0000:02:00.0: System wakeup disabled by ACPI
[    0.617588] pci 0000:00:1c.1: PCI bridge to [bus 02]
[    0.617593] pci 0000:00:1c.1:   bridge window [io  0x2000-0x2fff]
[    0.617604] pci 0000:00:1c.1:   bridge window [mem 0xf0400000-0xf04fffff 64bit pref]
[    0.617713] pci 0000:03:00.0: [168c:002b] type 00 class 0x028000
[    0.617747] pci 0000:03:00.0: reg 0x10: [mem 0xf0500000-0xf050ffff 64bit]
[    0.617900] pci 0000:03:00.0: supports D1
[    0.617902] pci 0000:03:00.0: PME# supported from D0 D1 D3hot
[    0.617941] pci 0000:03:00.0: System wakeup disabled by ACPI
[    0.629547] pci 0000:00:1c.2: PCI bridge to [bus 03]
[    0.629555] pci 0000:00:1c.2:   bridge window [mem 0xf0500000-0xf05fffff]
[    0.630391] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 10 *11 12 14 15)
[    0.630460] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 *10 11 12 14 15)
[    0.630526] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 10 11 12 14 15) *7
[    0.630590] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 10 11 12 14 15) *7
[    0.630655] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.630719] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.630787] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 *10 11 12 14 15)
[    0.630852] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 10 *11 12 14 15)
[    0.631567] ACPI: Enabled 4 GPEs in block 00 to 3F
[    0.631576] ACPI: \_SB_.PCI0: notify handler is installed
[    0.631661] Found 1 acpi root devices
[    0.631705] ACPI : EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.631816] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.631820] vgaarb: loaded
[    0.631822] vgaarb: bridge control possible 0000:00:02.0
[    0.632001] SCSI subsystem initialized
[    0.632061] libata version 3.00 loaded.
[    0.632081] ACPI: bus type USB registered
[    0.632100] usbcore: registered new interface driver usbfs
[    0.632109] usbcore: registered new interface driver hub
[    0.632136] usbcore: registered new device driver usb
[    0.632261] PCI: Using ACPI for IRQ routing
[    0.634089] PCI: pci_cache_line_size set to 64 bytes
[    0.634155] e820: reserve RAM buffer [mem 0x0009d800-0x0009ffff]
[    0.634158] e820: reserve RAM buffer [mem 0x40004000-0x43ffffff]
[    0.634160] e820: reserve RAM buffer [mem 0xc5e9d000-0xc7ffffff]
[    0.634161] e820: reserve RAM buffer [mem 0xd8386000-0xdbffffff]
[    0.634164] e820: reserve RAM buffer [mem 0xdb000000-0xdbffffff]
[    0.634165] e820: reserve RAM buffer [mem 0x11f600000-0x11fffffff]
[    0.634255] NetLabel: Initializing
[    0.634257] NetLabel:  domain hash size = 128
[    0.634258] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.634276] NetLabel:  unlabeled traffic allowed by default
[    0.634336] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.634343] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.636377] Switched to clocksource hpet
[    0.642125] AppArmor: AppArmor Filesystem Enabled
[    0.642154] pnp: PnP ACPI init
[    0.642168] ACPI: bus type PNP registered
[    0.642206] pnp 00:00: [dma 4]
[    0.642232] pnp 00:00: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.642257] pnp 00:01: Plug and Play ACPI device, IDs INT0800 (active)
[    0.642375] pnp 00:02: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.642410] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.642460] system 00:04: [io  0x0680-0x069f] has been reserved
[    0.642463] system 00:04: [io  0x1000-0x100f] has been reserved
[    0.642466] system 00:04: [io  0xffff] has been reserved
[    0.642468] system 00:04: [io  0xffff] has been reserved
[    0.642471] system 00:04: [io  0x0400-0x0453] could not be reserved
[    0.642474] system 00:04: [io  0x0458-0x047f] has been reserved
[    0.642476] system 00:04: [io  0x0500-0x057f] has been reserved
[    0.642479] system 00:04: [io  0x164e-0x164f] has been reserved
[    0.642482] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.642509] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.642564] system 00:06: [io  0x0454-0x0457] has been reserved
[    0.642568] system 00:06: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.642595] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.642661] pnp 00:08: Plug and Play ACPI device, IDs SYN1050 SYN1000 SYN0002 PNP0f13 (active)
[    0.642897] system 00:09: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.642900] system 00:09: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.642902] system 00:09: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.642905] system 00:09: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.642907] system 00:09: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.642910] system 00:09: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.642913] system 00:09: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.642915] system 00:09: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.642921] system 00:09: [mem 0xff000000-0xffffffff] could not be reserved
[    0.642924] system 00:09: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.642926] system 00:09: [mem 0xfffff000-0xffffffff] has been reserved
[    0.642929] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.643453] pnp: PnP ACPI: found 10 devices
[    0.643455] ACPI: bus type PNP unregistered
[    0.650068] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    0.650087] pci 0000:00:1c.1: PCI bridge to [bus 02]
[    0.650091] pci 0000:00:1c.1:   bridge window [io  0x2000-0x2fff]
[    0.650101] pci 0000:00:1c.1:   bridge window [mem 0xf0400000-0xf04fffff 64bit pref]
[    0.650110] pci 0000:00:1c.2: PCI bridge to [bus 03]
[    0.650116] pci 0000:00:1c.2:   bridge window [mem 0xf0500000-0xf05fffff]
[    0.650128] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.650130] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.650132] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.650135] pci_bus 0000:00: resource 7 [mem 0xdfa00000-0xfeafffff]
[    0.650137] pci_bus 0000:00: resource 8 [mem 0xfed40000-0xfed44fff]
[    0.650140] pci_bus 0000:02: resource 0 [io  0x2000-0x2fff]
[    0.650142] pci_bus 0000:02: resource 2 [mem 0xf0400000-0xf04fffff 64bit pref]
[    0.650145] pci_bus 0000:03: resource 1 [mem 0xf0500000-0xf05fffff]
[    0.650179] NET: Registered protocol family 2
[    0.650366] TCP established hash table entries: 32768 (order: 6, 262144 bytes)
[    0.650472] TCP bind hash table entries: 32768 (order: 7, 524288 bytes)
[    0.650557] TCP: Hash tables configured (established 32768 bind 32768)
[    0.650577] TCP: reno registered
[    0.650587] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.650607] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.650679] NET: Registered protocol family 1
[    0.650692] pci 0000:00:02.0: Boot video device
[    0.651317] PCI: CLS 64 bytes, default 64
[    0.651389] Trying to unpack rootfs image as initramfs...
[    1.051789] Freeing initrd memory: 18652K (ffff880035b82000 - ffff880036db9000)
[    1.051795] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    1.051798] software IO TLB [mem 0xd4386000-0xd8386000] (64MB) mapped at [ffff8800d4386000-ffff8800d8385fff]
[    1.052052] microcode: CPU0 sig=0x306a9, pf=0x10, revision=0x12
[    1.052059] microcode: CPU1 sig=0x306a9, pf=0x10, revision=0x12
[    1.052068] microcode: CPU2 sig=0x306a9, pf=0x10, revision=0x12
[    1.052078] microcode: CPU3 sig=0x306a9, pf=0x10, revision=0x12
[    1.052142] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.052144] Scanning for low memory corruption every 60 seconds
[    1.052491] Initialise system trusted keyring
[    1.052543] audit: initializing netlink socket (disabled)
[    1.052553] type=2000 audit(1400076369.044:1): initialized
[    1.089102] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.090473] VFS: Disk quotas dquot_6.5.2
[    1.090519] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.090976] fuse init (API version 7.22)
[    1.091054] msgmni has been set to 7622
[    1.091110] Key type big_key registered
[    1.091606] Key type asymmetric registered
[    1.091608] Asymmetric key parser 'x509' registered
[    1.091639] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    1.091681] io scheduler noop registered
[    1.091684] io scheduler deadline registered (default)
[    1.091709] io scheduler cfq registered
[    1.092264] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.092281] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.092328] intel_idle: MWAIT substates: 0x21120
[    1.092330] intel_idle: v0.4 model 0x3A
[    1.092331] intel_idle: lapic_timer_reliable_states 0xffffffff
[    1.092448] ipmi message handler version 39.2
[    1.093016] ACPI: AC Adapter [ACAD] (off-line)
[    1.093107] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    1.093986] ACPI: Lid Switch [LID0]
[    1.094029] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.094033] ACPI: Power Button [PWRB]
[    1.094067] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    1.094070] ACPI: Power Button [PWRF]
[    1.097118] thermal LNXTHERM:00: registered as thermal_zone0
[    1.097123] ACPI: Thermal Zone [TZ00] (35 C)
[    1.097171] GHES: HEST is not enabled!
[    1.097366] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.099706] Linux agpgart interface v0.103
[    1.101266] brd: module loaded
[    1.102007] loop: module loaded
[    1.102423] libphy: Fixed MDIO Bus: probed
[    1.102512] tun: Universal TUN/TAP device driver, 1.6
[    1.102514] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.102554] PPP generic driver version 2.4.2
[    1.102599] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.102606] ehci-pci: EHCI PCI platform driver
[    1.102763] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    1.102771] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.102789] ehci-pci 0000:00:1a.0: debug port 2
[    1.106685] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    1.106715] ehci-pci 0000:00:1a.0: irq 16, io mem 0xf0619000
[    1.116246] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.116327] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.116330] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.116332] usb usb1: Product: EHCI Host Controller
[    1.116334] usb usb1: Manufacturer: Linux 3.13.0-24-generic ehci_hcd
[    1.116336] usb usb1: SerialNumber: 0000:00:1a.0
[    1.116479] hub 1-0:1.0: USB hub found
[    1.116488] hub 1-0:1.0: 3 ports detected
[    1.116768] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    1.116774] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.116792] ehci-pci 0000:00:1d.0: debug port 2
[    1.120720] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    1.120737] ehci-pci 0000:00:1d.0: irq 23, io mem 0xf0618000
[    1.132309] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.132398] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.132401] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.132404] usb usb2: Product: EHCI Host Controller
[    1.132406] usb usb2: Manufacturer: Linux 3.13.0-24-generic ehci_hcd
[    1.132408] usb usb2: SerialNumber: 0000:00:1d.0
[    1.132602] hub 2-0:1.0: USB hub found
[    1.132615] hub 2-0:1.0: 3 ports detected
[    1.132815] ehci-platform: EHCI generic platform driver
[    1.132829] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.132831] ohci-pci: OHCI PCI platform driver
[    1.132842] ohci-platform: OHCI generic platform driver
[    1.132849] uhci_hcd: USB Universal Host Controller Interface driver
[    1.133029] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    1.133037] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
[    1.133150] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    1.133184] xhci_hcd 0000:00:14.0: irq 40 for MSI/MSI-X
[    1.133278] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    1.133281] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.133283] usb usb3: Product: xHCI Host Controller
[    1.133285] usb usb3: Manufacturer: Linux 3.13.0-24-generic xhci_hcd
[    1.133287] usb usb3: SerialNumber: 0000:00:14.0
[    1.133430] hub 3-0:1.0: USB hub found
[    1.133442] hub 3-0:1.0: 4 ports detected
[    1.133834] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    1.133839] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 4
[    1.133889] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
[    1.133891] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.133893] usb usb4: Product: xHCI Host Controller
[    1.133895] usb usb4: Manufacturer: Linux 3.13.0-24-generic xhci_hcd
[    1.133897] usb usb4: SerialNumber: 0000:00:14.0
[    1.134018] hub 4-0:1.0: USB hub found
[    1.134031] hub 4-0:1.0: 4 ports detected
[    1.144417] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2A] at 0x60,0x64 irq 1,12
[    1.147646] i8042: Detected active multiplexing controller, rev 1.1
[    1.148334] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.148341] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.148354] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.148357] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.148361] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.148511] mousedev: PS/2 mouse device common for all mice
[    1.148893] rtc_cmos 00:05: RTC can wake from S4
[    1.149113] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.149148] rtc_cmos 00:05: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.149226] device-mapper: uevent: version 1.0.3
[    1.149347] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
[    1.149357] ledtrig-cpu: registered to indicate activity on CPUs
[    1.149474] TCP: cubic registered
[    1.149564] NET: Registered protocol family 10
[    1.149747] NET: Registered protocol family 17
[    1.149755] Key type dns_resolver registered
[    1.150216] Loading compiled-in X.509 certificates
[    1.151408] Loaded X.509 cert 'Magrathea: Glacier signing key: 69b0d0a79b85d90621706e8d06604d730b359fc0'
[    1.151427] registered taskstats version 1
[    1.154535] Key type trusted registered
[    1.157172] Key type encrypted registered
[    1.159652] AppArmor: AppArmor sha1 policy hashing enabled
[    1.159657] IMA: No TPM chip found, activating TPM-bypass!
[    1.159946] regulator-dummy: disabling
[    1.160006]   Magic number: 14:593:131
[    1.160048] acpi device:06: hash matches
[    1.160100] rtc_cmos 00:05: setting system clock to 2014-05-14 14:06:09 UTC (1400076369)
[    1.160917] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.160919] EDD information not available.
[    1.160969] PM: Hibernation image not present or could not be loaded.
[    1.189901] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.428257] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.560557] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
[    1.560562] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.560978] hub 1-1:1.0: USB hub found
[    1.561216] hub 1-1:1.0: 6 ports detected
[    1.624536] ACPI: Battery Slot [BAT1] (battery present)
[    1.625720] Freeing unused kernel memory: 1332K (ffffffff81d1e000 - ffffffff81e6b000)
[    1.625724] Write protecting the kernel read-only data: 12288k
[    1.628546] Freeing unused kernel memory: 844K (ffff88000172d000 - ffff880001800000)
[    1.630822] Freeing unused kernel memory: 708K (ffff880001b4f000 - ffff880001c00000)
[    1.647094] systemd-udevd[123]: starting version 204
[    1.672090] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    1.680325] ahci 0000:00:1f.2: version 3.0
[    1.680533] ahci 0000:00:1f.2: irq 41 for MSI/MSI-X
[    1.680609] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x3 impl SATA mode
[    1.680614] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part ems apst 
[    1.681552] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.681566] r8169 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
[    1.681820] r8169 0000:02:00.0: irq 42 for MSI/MSI-X
[    1.682046] r8169 0000:02:00.0 eth0: RTL8105e at 0xffffc90000660000, 08:9e:01:15:19:d5, XID 00c00000 IRQ 42
[    1.688928] scsi0 : ahci
[    1.689062] scsi1 : ahci
[    1.689165] scsi2 : ahci
[    1.689263] scsi3 : ahci
[    1.689367] scsi4 : ahci
[    1.689668] scsi5 : ahci
[    1.689858] ata1: SATA max UDMA/133 abar m2048@0xf0617000 port 0xf0617100 irq 41
[    1.689864] ata2: SATA max UDMA/133 abar m2048@0xf0617000 port 0xf0617180 irq 41
[    1.689867] ata3: DUMMY
[    1.689869] ata4: DUMMY
[    1.689871] ata5: DUMMY
[    1.689873] ata6: DUMMY
[    1.804421] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
[    1.804427] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.804744] hub 2-1:1.0: USB hub found
[    1.804955] hub 2-1:1.0: 8 ports detected
[    1.972097] usb 3-3: new high-speed USB device number 2 using xhci_hcd
[    1.997287] usb 3-3: New USB device found, idVendor=5986, idProduct=0295
[    1.997292] usb 3-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.997295] usb 3-3: Product: Lenovo EasyCamera
[    1.997297] usb 3-3: Manufacturer: Vimicro corp.
[    2.008001] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.008025] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    2.008728] ata1.00: ATA-8: SAMSUNG MZMPC032HBCD-000L1, CXM12L1Q, max UDMA/133
[    2.008732] ata1.00: 62533296 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.009240] ata1.00: configured for UDMA/133
[    2.009459] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG MZMPC032 CXM1 PQ: 0 ANSI: 5
[    2.009621] sd 0:0:0:0: [sda] 62533296 512-byte logical blocks: (32.0 GB/29.8 GiB)
[    2.009653] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.009804] sd 0:0:0:0: [sda] Write Protect is off
[    2.009808] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.009920] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.010468]  sda: sda1
[    2.010900] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.011893] ata2.00: ATA-8: ST500LT012-9WS142, 0001LVM1, max UDMA/133
[    2.011896] ata2.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.012654] ata2.00: configured for UDMA/133
[    2.012877] scsi 1:0:0:0: Direct-Access     ATA      ST500LT012-9WS14 0001 PQ: 0 ANSI: 5
[    2.013043] sd 1:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    2.013046] sd 1:0:0:0: [sdb] 4096-byte physical blocks
[    2.013062] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    2.013173] sd 1:0:0:0: [sdb] Write Protect is off
[    2.013177] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.013248] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.047964] tsc: Refined TSC clocksource calibration: 1795.920 MHz
[    2.108889]  sdb: sdb1 sdb2 < sdb5 >
[    2.109754] sd 1:0:0:0: [sdb] Attached SCSI disk
[    2.163986] usb 3-4: new full-speed USB device number 3 using xhci_hcd
[    2.180890] usb 3-4: New USB device found, idVendor=0cf3, idProduct=3002
[    2.180894] usb 3-4: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.696081] psmouse serio4: synaptics: Touchpad model: 1, fw: 8.1, id: 0x1e2b1, caps: 0xd00123/0x840300/0x123c00, board id: 1800, fw id: 1087391
[    2.736886] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input11
[    3.047850] Switched to clocksource tsc
[    3.161144] random: nonblocking pool is initialized
[    3.238887] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    3.372205] init: plymouth-upstart-bridge main process (192) terminated with status 1
[    3.372229] init: plymouth-upstart-bridge main process ended, respawning
[    3.378877] init: plymouth-upstart-bridge main process (202) terminated with status 1
[    3.378899] init: plymouth-upstart-bridge main process ended, respawning
[    3.381999] init: plymouth-upstart-bridge main process (205) terminated with status 1
[    3.382014] init: plymouth-upstart-bridge main process ended, respawning
[    3.385711] init: plymouth-upstart-bridge main process (206) terminated with status 1
[    3.385733] init: plymouth-upstart-bridge main process ended, respawning
[    3.388784] init: plymouth-upstart-bridge main process (208) terminated with status 1
[    3.388799] init: plymouth-upstart-bridge main process ended, respawning
[    3.392403] init: plymouth-upstart-bridge main process (209) terminated with status 1
[    3.392425] init: plymouth-upstart-bridge main process ended, respawning
[    3.395385] init: plymouth-upstart-bridge main process (211) terminated with status 1
[    3.395399] init: plymouth-upstart-bridge main process ended, respawning
[    3.399140] init: plymouth-upstart-bridge main process (212) terminated with status 1
[    3.399162] init: plymouth-upstart-bridge main process ended, respawning
[    3.402198] init: plymouth-upstart-bridge main process (214) terminated with status 1
[    3.402213] init: plymouth-upstart-bridge main process ended, respawning
[    3.407111] init: plymouth-upstart-bridge main process (215) terminated with status 1
[    3.407127] init: plymouth-upstart-bridge main process ended, respawning
[    3.411293] init: plymouth-upstart-bridge main process (217) terminated with status 1
[    3.411308] init: plymouth-upstart-bridge respawning too fast, stopped
[    3.539040] Adding 3997692k swap on /dev/sdb5.  Priority:-1 extents:1 across:3997692k FS
[    3.630866] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[    3.681771] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    3.728330] systemd-udevd[357]: starting version 204
[    3.795338] lp: driver loaded but no devices found
[    3.810869] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[    3.816735] ppdev: user-space parallel port driver
[    3.839083] mei_me 0000:00:16.0: irq 43 for MSI/MSI-X
[    3.854570] [drm] Initialized drm 1.1.0 20060810
[    3.890360] cfg80211: Calling CRDA to update world regulatory domain
[    3.906281] [drm] Memory usable by graphics device = 2048M
[    3.913072] input: Ideapad extra buttons as /devices/platform/VPC2004:00/input/input12
[    3.974834] wmi: Mapper loaded
[    3.984691] i915 0000:00:02.0: irq 44 for MSI/MSI-X
[    3.984707] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    3.984709] [drm] Driver supports precise vblank timestamp query.
[    3.985036] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    3.989705] Linux video capture interface: v2.00
[    4.008283] uvcvideo: Found UVC 1.00 device Lenovo EasyCamera (5986:0295)
[    4.008288] uvcvideo: Forcing device quirks to 0x100 by module parameter for testing purpose.
[    4.008290] uvcvideo: Please report required quirks to the linux-uvc-devel mailing list.
[    4.010691] Bluetooth: Core ver 2.17
[    4.010716] NET: Registered protocol family 31
[    4.010718] Bluetooth: HCI device and connection manager initialized
[    4.010727] Bluetooth: HCI socket layer initialized
[    4.010730] Bluetooth: L2CAP socket layer initialized
[    4.010736] Bluetooth: SCO socket layer initialized
[    4.025263] usbcore: registered new interface driver btusb
[    4.030017] input: Lenovo EasyCamera as /devices/pci0000:00/0000:00:14.0/usb3/3-3/3-3:1.0/input/input13
[    4.031154] usbcore: registered new interface driver uvcvideo
[    4.031159] USB Video Class driver (1.1.1)
[    4.091731] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    4.091735] Bluetooth: BNEP filters: protocol multicast
[    4.091744] Bluetooth: BNEP socket layer initialized
[    4.096089] Bluetooth: RFCOMM TTY layer initialized
[    4.096104] Bluetooth: RFCOMM socket layer initialized
[    4.096113] Bluetooth: RFCOMM ver 1.11
[    4.122406] ath: phy0: ASPM enabled: 0x42
[    4.122414] ath: EEPROM regdomain: 0x65
[    4.122417] ath: EEPROM indicates we should expect a direct regpair map
[    4.122422] ath: Country alpha2 being used: 00
[    4.122424] ath: Regpair used: 0x65
[    4.127310] type=1400 audit(1400076372.467:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=553 comm="apparmor_parser"
[    4.127322] type=1400 audit(1400076372.467:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=553 comm="apparmor_parser"
[    4.127331] type=1400 audit(1400076372.467:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=553 comm="apparmor_parser"
[    4.128083] type=1400 audit(1400076372.467:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=553 comm="apparmor_parser"
[    4.128095] type=1400 audit(1400076372.467:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=553 comm="apparmor_parser"
[    4.128504] type=1400 audit(1400076372.467:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=553 comm="apparmor_parser"
[    4.131956] type=1400 audit(1400076372.471:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=554 comm="apparmor_parser"
[    4.131968] type=1400 audit(1400076372.471:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=554 comm="apparmor_parser"
[    4.132581] type=1400 audit(1400076372.471:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=554 comm="apparmor_parser"
[    4.135507] [drm] GMBUS [i915 gmbus vga] timed out, falling back to bit banging on pin 2
[    4.151435] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[    4.152098] ieee80211 phy0: Atheros AR9285 Rev:2 mem=0xffffc900047c0000, irq=18
[    4.154996] fbcon: inteldrmfb (fb0) is primary device
[    4.205296] init: cups main process (572) killed by HUP signal
[    4.205316] init: cups main process ended, respawning
[    4.232367] kvm: disabled by bios
[    4.279395] kvm: disabled by bios
[    4.340509] usbcore: registered new interface driver ath3k
[    4.356818] usb 3-4: USB disconnect, device number 3
[    4.365638] cfg80211: World regulatory domain updated:
[    4.365639] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    4.365641] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    4.365642] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    4.365643] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    4.365644] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    4.365645] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    4.411215] intel_rapl: domain uncore energy ctr 2454:2454 not working, skip
[    4.858505] Console: switching to colour frame buffer device 170x48
[    4.861857] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[    4.861859] i915 0000:00:02.0: registered panic notifier
[    4.869121] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    4.876706] acpi device:46: registered as cooling_device5
[    4.876839] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input14
[    4.876962] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    4.877076] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20131115/utaddress-251)
[    4.877077] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    4.877084] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
[    4.877085] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    4.877089] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
[    4.877090] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    4.877091] lpc_ich: Resource conflict(s) found affecting gpio_ich
[    4.877484] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[    4.898742] hda_codec: CX20590: BIOS auto-probing.
[    4.899394] autoconfig: line_outs=1 (0x1f/0x0/0x0/0x0/0x0) type:speaker
[    4.899399]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    4.899402]    hp_outs=1 (0x19/0x0/0x0/0x0/0x0)
[    4.899404]    mono: mono_out=0x0
[    4.899406]    inputs:
[    4.899408]      Internal Mic=0x23
[    4.899411]      Mic=0x1a
[    4.900401] hda_codec: Enable sync_write for stable communication
[    4.913125] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input17
[    4.915274] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input16
[    4.915857] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
[    4.935150] usb 3-4: new full-speed USB device number 4 using xhci_hcd
[    4.952009] usb 3-4: New USB device found, idVendor=0cf3, idProduct=3005
[    4.952017] usb 3-4: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    5.004234] init: failsafe main process (659) killed by TERM signal
[    5.042459] init: udev-fallback-graphics main process (736) terminated with status 1
[    5.593822] r8169 0000:02:00.0 eth0: link down
[    5.593868] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    5.594299] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    5.611466] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    5.614656] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    5.811948] [drm] Enabling RC6 states: RC6 on, RC6p on, RC6pp off


```

---

### Post by MirkoCe on 2014-05-18
Nobody? :(

---

### Post by slooksterpsv on 2014-05-19
I'd remove quiet and splash and wait for it to happen again, I'm not seeing anything out of the ordinary with the dmesg logs. Whats the specs of your machine? And do you have proprietary drivers installed?

EDIT:
```

[    4.869121] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    4.876706] acpi device:46: registered as cooling_device5
[    4.876839] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input14
[    4.876962] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    4.877076] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20131115/utaddress-251)
[    4.877077] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    4.877084] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
[    4.877085] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    4.877089] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
[    4.877090] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver

```
Hmm... that looks odd. Wonder if it's an ACPI issue now. You can add acpi=off to the boot params see if that fixes anything.

---

### Post by MirkoCe on 2014-05-20
With no plymouth it seems ok, I've tested for some days and nothing happened. As soon as I enable plymouth something stops it, but really seldom not always!  There is no proprietary driver to be installed anyway.

I'm running ubuntu on an Ideapad Lenovo u310.

---

### Post by MirkoCe on 2014-05-20
Sorry to bother you again, but I think I at least managed to get rid of those ACPI warnings. As I am not an expert, could you confirm that there is nothing weird at the moment?

```
 [    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.13.0-24-generic (buildd@batsu) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #47-Ubuntu SMP Fri May 2 23:30:00 UTC 2014 (Ubuntu 3.13.0-24.47-generic 3.13.9)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic root=UUID=6350cd06-e3d5-4207-b62c-ed03ac476452 ro quiet splash vt.handoff=7
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
[    0.000000] BIOS-e820: [mem 0x0000000040005000-0x00000000c5e9cfff] usable
[    0.000000] BIOS-e820: [mem 0x00000000c5e9d000-0x00000000c609efff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000c609f000-0x00000000d8385fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000d8386000-0x00000000daeeefff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000daeef000-0x00000000daf9efff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000daf9f000-0x00000000daffefff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000dafff000-0x00000000daffffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000db000000-0x00000000df9fffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed08000-0x00000000fed08fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed10000-0x00000000fed19fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff980000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000011f5fffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.7 present.
[    0.000000] DMI: LENOVO IdeaPad U310    /Lenovo          , BIOS 65CN15WW 06/05/2012
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x11f600 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0FF800000 mask FFF800000 write-protect
[    0.000000]   1 base 000000000 mask F80000000 write-back
[    0.000000]   2 base 080000000 mask FC0000000 write-back
[    0.000000]   3 base 0C0000000 mask FE0000000 write-back
[    0.000000]   4 base 0DC000000 mask FFC000000 uncachable
[    0.000000]   5 base 0DB000000 mask FFF000000 uncachable
[    0.000000]   6 base 100000000 mask FE0000000 write-back
[    0.000000]   7 base 11F800000 mask FFF800000 uncachable
[    0.000000]   8 base 11F600000 mask FFFE00000 uncachable
[    0.000000]   9 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820: last_pfn = 0xdb000 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000f0130-0x000f013f] mapped at [ffff8800000f0130]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000097000] 97000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01fdd000, 0x01fddfff] PGTABLE
[    0.000000] BRK [0x01fde000, 0x01fdefff] PGTABLE
[    0.000000] BRK [0x01fdf000, 0x01fdffff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x11f400000-0x11f5fffff]
[    0.000000]  [mem 0x11f400000-0x11f5fffff] page 2M
[    0.000000] BRK [0x01fe0000, 0x01fe0fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x11c000000-0x11f3fffff]
[    0.000000]  [mem 0x11c000000-0x11f3fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x100000000-0x11bffffff]
[    0.000000]  [mem 0x100000000-0x11bffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0x1fffffff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x1fffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x20200000-0x40003fff]
[    0.000000]  [mem 0x20200000-0x3fffffff] page 2M
[    0.000000]  [mem 0x40000000-0x40003fff] page 4k
[    0.000000] BRK [0x01fe1000, 0x01fe1fff] PGTABLE
[    0.000000] BRK [0x01fe2000, 0x01fe2fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x40005000-0xc5e9cfff]
[    0.000000]  [mem 0x40005000-0x401fffff] page 4k
[    0.000000]  [mem 0x40200000-0xc5dfffff] page 2M
[    0.000000]  [mem 0xc5e00000-0xc5e9cfff] page 4k
[    0.000000] init_memory_mapping: [mem 0xc609f000-0xd8385fff]
[    0.000000]  [mem 0xc609f000-0xc61fffff] page 4k
[    0.000000]  [mem 0xc6200000-0xd81fffff] page 2M
[    0.000000]  [mem 0xd8200000-0xd8385fff] page 4k
[    0.000000] init_memory_mapping: [mem 0xdafff000-0xdaffffff]
[    0.000000]  [mem 0xdafff000-0xdaffffff] page 4k
[    0.000000] RAMDISK: [mem 0x35b84000-0x36db9fff]
[    0.000000] ACPI: RSDP 00000000000f0150 000024 (v02 LENOVO)
[    0.000000] ACPI: XSDT 00000000daffe170 000094 (v01 LENOVO CB-01    06040000  LTP 00000000)
[    0.000000] ACPI: FACP 00000000dafee000 0000F4 (v03 LENOVO CB-01    06040000  LTP 00000000)
[    0.000000] ACPI: DSDT 00000000daff1000 00AD64 (v02 LENOVO  IVB-CPT 00000000 INTL 20061109)
[    0.000000] ACPI: FACS 00000000daf78000 000040
[    0.000000] ACPI: SLIC 00000000daffd000 000176 (v01 LENOVO CB-01    06040000  LTP 00000000)
[    0.000000] ACPI: SSDT 00000000daffc000 00052F (v01 LENOVO PtidDevc 00001000 INTL 20061109)
[    0.000000] ACPI: ASF! 00000000daff0000 0000A5 (v32 LENOVO CB-01    06040000  LTP 00000000)
[    0.000000] ACPI: HPET 00000000dafed000 000038 (v01 LENOVO CB-01    06040000  LTP 00000000)
[    0.000000] ACPI: APIC 00000000dafec000 000098 (v01 LENOVO CB-01    06040000  LTP 00000000)
[    0.000000] ACPI: MCFG 00000000dafeb000 00003C (v01 LENOVO CB-01    06040000  LTP 00000000)
[    0.000000] ACPI: FPDT 00000000dafea000 000064 (v01 LENOVO CB-01    06040000  LTP 00000000)
[    0.000000] ACPI: SSDT 00000000dafe9000 0008E4 (v01  PmRef  Cpu0Ist 00003000 INTL 20061109)
[    0.000000] ACPI: SSDT 00000000dafe8000 000A92 (v01  PmRef    CpuPm 00003000 INTL 20061109)
[    0.000000] ACPI: UEFI 00000000dafe7000 00003E (v01 LENOVO CB-01    06040000  LTP 00000000)
[    0.000000] ACPI: UEFI 00000000dafe6000 000042 (v01 PTL      COMBUF 00000001 PTL  00000001)
[    0.000000] ACPI: POAT 00000000dafe5000 000055 (v03 LENOVO CB-01    06040000  LTP 00000000)
[    0.000000] ACPI: UEFI 00000000dafe4000 0002E2 (v01 LENOVO CB-01    06040000  LTP 00000000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000011f5fffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x11f5fffff]
[    0.000000]   NODE_DATA [mem 0x11f5f5000-0x11f5f9fff]
[    0.000000]  [ffffea0000000000-ffffea00047fffff] PMD -> [ffff88011ac00000-ffff88011ebfffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x11f5fffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009cfff]
[    0.000000]   node   0: [mem 0x00100000-0x1fffffff]
[    0.000000]   node   0: [mem 0x20200000-0x40003fff]
[    0.000000]   node   0: [mem 0x40005000-0xc5e9cfff]
[    0.000000]   node   0: [mem 0xc609f000-0xd8385fff]
[    0.000000]   node   0: [mem 0xdafff000-0xdaffffff]
[    0.000000]   node   0: [mem 0x100000000-0x11f5fffff]
[    0.000000] On node 0 totalpages: 1013024
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3996 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 13759 pages used for memmap
[    0.000000]   DMA32 zone: 880516 pages, LIFO batch:31
[    0.000000]   Normal zone: 2008 pages used for memmap
[    0.000000]   Normal zone: 128512 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a301 base: 0xfed00000
[    0.000000] smpboot: Allowing 8 CPUs, 4 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: [mem 0x0009d000-0x0009dfff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x20000000-0x201fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x40004000-0x40004fff]
[    0.000000] PM: Registered nosave memory: [mem 0xc5e9d000-0xc609efff]
[    0.000000] PM: Registered nosave memory: [mem 0xd8386000-0xdaeeefff]
[    0.000000] PM: Registered nosave memory: [mem 0xdaeef000-0xdaf9efff]
[    0.000000] PM: Registered nosave memory: [mem 0xdaf9f000-0xdaffefff]
[    0.000000] PM: Registered nosave memory: [mem 0xdb000000-0xdf9fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xdfa00000-0xf7ffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf8000000-0xfbffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfc000000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfed07fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed08000-0xfed08fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed09000-0xfed0ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed10000-0xfed19fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1a000-0xfed1bfff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xff97ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xff980000-0xffffffff]
[    0.000000] e820: [mem 0xdfa00000-0xf7ffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 29 pages/cpu @ffff88011f200000 s86336 r8192 d24256 u262144
[    0.000000] pcpu-alloc: s86336 r8192 d24256 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 997172
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic root=UUID=6350cd06-e3d5-4207-b62c-ed03ac476452 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 3884284K/4052096K available (7338K kernel code, 1138K rwdata, 3388K rodata, 1332K init, 1440K bss, 167812K reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000]     Offload RCU callbacks from all CPUs
[    0.000000]     Offload RCU callbacks from CPUs: 0-7.
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 16777216 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.004000] tsc: Detected 1795.842 MHz processor
[    0.000003] Calibrating delay loop (skipped), value calculated using timer frequency.. 3591.68 BogoMIPS (lpj=7183368)
[    0.000007] pid_max: default: 32768 minimum: 301
[    0.000034] Security Framework initialized
[    0.000056] AppArmor: AppArmor initialized
[    0.000057] Yama: becoming mindful.
[    0.000468] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.001919] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.002562] Mount-cache hash table entries: 8192 (order: 4, 65536 bytes)
[    0.002569] Mountpoint-cache hash table entries: 8192 (order: 4, 65536 bytes)
[    0.002807] Initializing cgroup subsys memory
[    0.002813] Initializing cgroup subsys devices
[    0.002815] Initializing cgroup subsys freezer
[    0.002817] Initializing cgroup subsys blkio
[    0.002819] Initializing cgroup subsys perf_event
[    0.002822] Initializing cgroup subsys hugetlb
[    0.002852] CPU: Physical Processor ID: 0
[    0.002853] CPU: Processor Core ID: 0
[    0.002859] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.002859] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.002863] mce: CPU supports 7 MCE banks
[    0.002877] CPU0: Thermal monitoring enabled (TM1)
[    0.002888] Last level iTLB entries: 4KB 512, 2MB 0, 4MB 0
[    0.002888] Last level dTLB entries: 4KB 512, 2MB 32, 4MB 32
[    0.002888] tlb_flushall_shift: 2
[    0.003047] Freeing SMP alternatives memory: 32K (ffffffff81e6b000 - ffffffff81e73000)
[    0.004627] ACPI: Core revision 20131115
[    0.013507] ACPI: All ACPI Tables successfully acquired
[    0.013831] ftrace: allocating 28408 entries in 111 pages
[    0.032436] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.072109] smpboot: CPU0: Intel(R) Core(TM) i3-3217U CPU @ 1.80GHz (fam: 06, model: 3a, stepping: 09)
[    0.072118] TSC deadline timer enabled
[    0.075234] Performance Events: PEBS fmt1+, 16-deep LBR, IvyBridge events, full-width counters, Intel PMU driver.
[    0.075243] ... version:                3
[    0.075244] ... bit width:              48
[    0.075245] ... generic registers:      4
[    0.075247] ... value mask:             0000ffffffffffff
[    0.075248] ... max period:             0000ffffffffffff
[    0.075249] ... fixed-purpose events:   3
[    0.075251] ... event mask:             000000070000000f
[    0.077428] x86: Booting SMP configuration:
[    0.090709] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.077430] .... node  #0, CPUs:      #1 #2 #3
[    0.117229] x86: Booted up 1 node, 4 CPUs
[    0.117233] smpboot: Total of 4 processors activated (14366.73 BogoMIPS)
[    0.121547] devtmpfs: initialized
[    0.124783] EVM: security.selinux
[    0.124785] EVM: security.SMACK64
[    0.124787] EVM: security.ima
[    0.124788] EVM: security.capability
[    0.124849] PM: Registering ACPI NVS region [mem 0xdaeef000-0xdaf9efff] (720896 bytes)
[    0.125883] pinctrl core: initialized pinctrl subsystem
[    0.125948] regulator-dummy: no parameters
[    0.125982] RTC time: 17:23:52, date: 05/20/14
[    0.126022] NET: Registered protocol family 16
[    0.126140] cpuidle: using governor ladder
[    0.126142] cpuidle: using governor menu
[    0.126187] ACPI: bus type PCI registered
[    0.126189] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.126261] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.126263] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.135112] PCI: Using configuration type 1 for base access
[    0.135295] mtrr: your CPUs had inconsistent variable MTRR settings
[    0.135297] mtrr: probably your BIOS does not setup all CPUs.
[    0.135298] mtrr: corrected configuration.
[    0.136194] bio: create slab <bio-0> at 0
[    0.136382] ACPI: Added _OSI(Module Device)
[    0.136384] ACPI: Added _OSI(Processor Device)
[    0.136386] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.136388] ACPI: Added _OSI(Processor Aggregator Device)
[    0.145354] ACPI: Executed 2 blocks of module-level executable AML code
[    0.149228] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.149733] ACPI: SSDT 00000000dae8e018 00083B (v01  PmRef  Cpu0Cst 00003001 INTL 20061109)
[    0.150406] ACPI: Dynamic OEM Table Load:
[    0.150409] ACPI: SSDT           (null) 00083B (v01  PmRef  Cpu0Cst 00003001 INTL 20061109)
[    0.153593] ACPI: SSDT 00000000dae8fa98 000303 (v01  PmRef    ApIst 00003000 INTL 20061109)
[    0.154302] ACPI: Dynamic OEM Table Load:
[    0.154304] ACPI: SSDT           (null) 000303 (v01  PmRef    ApIst 00003000 INTL 20061109)
[    0.157429] ACPI: SSDT 00000000dae8dd98 000119 (v01  PmRef    ApCst 00003000 INTL 20061109)
[    0.158099] ACPI: Dynamic OEM Table Load:
[    0.158102] ACPI: SSDT           (null) 000119 (v01  PmRef    ApCst 00003000 INTL 20061109)
[    0.589691] ACPI: Interpreter enabled
[    0.589706] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)
[    0.589726] ACPI: (supports S0 S1 S3 S4 S5)
[    0.589728] ACPI: Using IOAPIC for interrupt routing
[    0.589763] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.589977] ACPI: No dock devices found.
[    0.603349] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    0.603356] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.603512] \_SB_.PCI0:_OSC invalid UUID
[    0.603513] _OSC request data:1 1f 0 
[    0.603519] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM
[    0.604211] PCI host bridge to bus 0000:00
[    0.604215] pci_bus 0000:00: root bus resource [bus 00-3e]
[    0.604218] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.604220] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.604223] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.604225] pci_bus 0000:00: root bus resource [mem 0xdfa00000-0xfeafffff]
[    0.604227] pci_bus 0000:00: root bus resource [mem 0xfed40000-0xfed44fff]
[    0.604237] pci 0000:00:00.0: [8086:0154] type 00 class 0x060000
[    0.604347] pci 0000:00:02.0: [8086:0166] type 00 class 0x030000
[    0.604362] pci 0000:00:02.0: reg 0x10: [mem 0xf0000000-0xf03fffff 64bit]
[    0.604370] pci 0000:00:02.0: reg 0x18: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.604376] pci 0000:00:02.0: reg 0x20: [io  0x3000-0x303f]
[    0.604522] pci 0000:00:14.0: [8086:1e31] type 00 class 0x0c0330
[    0.604553] pci 0000:00:14.0: reg 0x10: [mem 0xf0600000-0xf060ffff 64bit]
[    0.604645] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    0.604702] pci 0000:00:14.0: System wakeup disabled by ACPI
[    0.604745] pci 0000:00:16.0: [8086:1e3a] type 00 class 0x078000
[    0.604775] pci 0000:00:16.0: reg 0x10: [mem 0xf0615000-0xf061500f 64bit]
[    0.604871] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.604983] pci 0000:00:1a.0: [8086:1e2d] type 00 class 0x0c0320
[    0.605011] pci 0000:00:1a.0: reg 0x10: [mem 0xf0619000-0xf06193ff]
[    0.605126] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.605204] pci 0000:00:1a.0: System wakeup disabled by ACPI
[    0.605247] pci 0000:00:1b.0: [8086:1e20] type 00 class 0x040300
[    0.605271] pci 0000:00:1b.0: reg 0x10: [mem 0xf0610000-0xf0613fff 64bit]
[    0.605357] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.605415] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    0.605452] pci 0000:00:1c.0: [8086:1e10] type 01 class 0x060400
[    0.605565] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.605629] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.605666] pci 0000:00:1c.1: [8086:1e12] type 01 class 0x060400
[    0.605770] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.605831] pci 0000:00:1c.1: System wakeup disabled by ACPI
[    0.605867] pci 0000:00:1c.2: [8086:1e14] type 01 class 0x060400
[    0.605972] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.606034] pci 0000:00:1c.2: System wakeup disabled by ACPI
[    0.606085] pci 0000:00:1d.0: [8086:1e26] type 00 class 0x0c0320
[    0.606112] pci 0000:00:1d.0: reg 0x10: [mem 0xf0618000-0xf06183ff]
[    0.606226] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.606298] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.606336] pci 0000:00:1f.0: [8086:1e57] type 00 class 0x060100
[    0.606549] pci 0000:00:1f.2: [8086:1e03] type 00 class 0x010601
[    0.606576] pci 0000:00:1f.2: reg 0x10: [io  0x3088-0x308f]
[    0.606588] pci 0000:00:1f.2: reg 0x14: [io  0x3094-0x3097]
[    0.606599] pci 0000:00:1f.2: reg 0x18: [io  0x3080-0x3087]
[    0.606610] pci 0000:00:1f.2: reg 0x1c: [io  0x3090-0x3093]
[    0.606621] pci 0000:00:1f.2: reg 0x20: [io  0x3060-0x307f]
[    0.606632] pci 0000:00:1f.2: reg 0x24: [mem 0xf0617000-0xf06177ff]
[    0.606700] pci 0000:00:1f.2: PME# supported from D3hot
[    0.606786] pci 0000:00:1f.3: [8086:1e22] type 00 class 0x0c0500
[    0.606810] pci 0000:00:1f.3: reg 0x10: [mem 0xf0614000-0xf06140ff 64bit]
[    0.606843] pci 0000:00:1f.3: reg 0x20: [io  0xefa0-0xefbf]
[    0.607026] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    0.607208] pci 0000:02:00.0: [10ec:8136] type 00 class 0x020000
[    0.607282] pci 0000:02:00.0: reg 0x10: [io  0x2000-0x20ff]
[    0.607413] pci 0000:02:00.0: reg 0x18: [mem 0xf0404000-0xf0404fff 64bit pref]
[    0.607493] pci 0000:02:00.0: reg 0x20: [mem 0xf0400000-0xf0403fff 64bit pref]
[    0.607845] pci 0000:02:00.0: supports D1 D2
[    0.607847] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.607970] pci 0000:02:00.0: System wakeup disabled by ACPI
[    0.613631] pci 0000:00:1c.1: PCI bridge to [bus 02]
[    0.613637] pci 0000:00:1c.1:   bridge window [io  0x2000-0x2fff]
[    0.613647] pci 0000:00:1c.1:   bridge window [mem 0xf0400000-0xf04fffff 64bit pref]
[    0.613755] pci 0000:03:00.0: [168c:002b] type 00 class 0x028000
[    0.613788] pci 0000:03:00.0: reg 0x10: [mem 0xf0500000-0xf050ffff 64bit]
[    0.613942] pci 0000:03:00.0: supports D1
[    0.613944] pci 0000:03:00.0: PME# supported from D0 D1 D3hot
[    0.613983] pci 0000:03:00.0: System wakeup disabled by ACPI
[    0.621592] pci 0000:00:1c.2: PCI bridge to [bus 03]
[    0.621600] pci 0000:00:1c.2:   bridge window [mem 0xf0500000-0xf05fffff]
[    0.622429] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 10 *11 12 14 15)
[    0.622498] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 *10 11 12 14 15)
[    0.622563] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 10 11 12 14 15) *7
[    0.622628] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 10 11 12 14 15) *7
[    0.622693] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.622758] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.622825] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 *10 11 12 14 15)
[    0.622892] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 10 *11 12 14 15)
[    0.623599] ACPI: Enabled 4 GPEs in block 00 to 3F
[    0.623608] ACPI: \_SB_.PCI0: notify handler is installed
[    0.623693] Found 1 acpi root devices
[    0.623736] ACPI : EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.623848] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.623852] vgaarb: loaded
[    0.623853] vgaarb: bridge control possible 0000:00:02.0
[    0.624031] SCSI subsystem initialized
[    0.624092] libata version 3.00 loaded.
[    0.624113] ACPI: bus type USB registered
[    0.624132] usbcore: registered new interface driver usbfs
[    0.624141] usbcore: registered new interface driver hub
[    0.624168] usbcore: registered new device driver usb
[    0.624295] PCI: Using ACPI for IRQ routing
[    0.626125] PCI: pci_cache_line_size set to 64 bytes
[    0.626192] e820: reserve RAM buffer [mem 0x0009d800-0x0009ffff]
[    0.626195] e820: reserve RAM buffer [mem 0x40004000-0x43ffffff]
[    0.626196] e820: reserve RAM buffer [mem 0xc5e9d000-0xc7ffffff]
[    0.626198] e820: reserve RAM buffer [mem 0xd8386000-0xdbffffff]
[    0.626200] e820: reserve RAM buffer [mem 0xdb000000-0xdbffffff]
[    0.626202] e820: reserve RAM buffer [mem 0x11f600000-0x11fffffff]
[    0.626293] NetLabel: Initializing
[    0.626295] NetLabel:  domain hash size = 128
[    0.626296] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.626314] NetLabel:  unlabeled traffic allowed by default
[    0.626379] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.626387] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.628421] Switched to clocksource hpet
[    0.634162] AppArmor: AppArmor Filesystem Enabled
[    0.634191] pnp: PnP ACPI init
[    0.634204] ACPI: bus type PNP registered
[    0.634243] pnp 00:00: [dma 4]
[    0.634270] pnp 00:00: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.634295] pnp 00:01: Plug and Play ACPI device, IDs INT0800 (active)
[    0.634412] pnp 00:02: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.634447] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.634497] system 00:04: [io  0x0680-0x069f] has been reserved
[    0.634500] system 00:04: [io  0x1000-0x100f] has been reserved
[    0.634502] system 00:04: [io  0xffff] has been reserved
[    0.634505] system 00:04: [io  0xffff] has been reserved
[    0.634508] system 00:04: [io  0x0400-0x0453] could not be reserved
[    0.634510] system 00:04: [io  0x0458-0x047f] has been reserved
[    0.634512] system 00:04: [io  0x0500-0x057f] has been reserved
[    0.634515] system 00:04: [io  0x164e-0x164f] has been reserved
[    0.634518] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.634544] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.634599] system 00:06: [io  0x0454-0x0457] has been reserved
[    0.634603] system 00:06: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.634631] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.634696] pnp 00:08: Plug and Play ACPI device, IDs SYN1050 SYN1000 SYN0002 PNP0f13 (active)
[    0.634932] system 00:09: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.634935] system 00:09: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.634938] system 00:09: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.634940] system 00:09: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.634943] system 00:09: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.634945] system 00:09: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.634948] system 00:09: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.634950] system 00:09: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.634956] system 00:09: [mem 0xff000000-0xffffffff] could not be reserved
[    0.634959] system 00:09: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.634961] system 00:09: [mem 0xfffff000-0xffffffff] has been reserved
[    0.634964] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.635487] pnp: PnP ACPI: found 10 devices
[    0.635489] ACPI: bus type PNP unregistered
[    0.642095] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    0.642115] pci 0000:00:1c.1: PCI bridge to [bus 02]
[    0.642119] pci 0000:00:1c.1:   bridge window [io  0x2000-0x2fff]
[    0.642130] pci 0000:00:1c.1:   bridge window [mem 0xf0400000-0xf04fffff 64bit pref]
[    0.642138] pci 0000:00:1c.2: PCI bridge to [bus 03]
[    0.642144] pci 0000:00:1c.2:   bridge window [mem 0xf0500000-0xf05fffff]
[    0.642158] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.642160] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.642163] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.642165] pci_bus 0000:00: resource 7 [mem 0xdfa00000-0xfeafffff]
[    0.642167] pci_bus 0000:00: resource 8 [mem 0xfed40000-0xfed44fff]
[    0.642170] pci_bus 0000:02: resource 0 [io  0x2000-0x2fff]
[    0.642173] pci_bus 0000:02: resource 2 [mem 0xf0400000-0xf04fffff 64bit pref]
[    0.642175] pci_bus 0000:03: resource 1 [mem 0xf0500000-0xf05fffff]
[    0.642210] NET: Registered protocol family 2
[    0.642396] TCP established hash table entries: 32768 (order: 6, 262144 bytes)
[    0.642501] TCP bind hash table entries: 32768 (order: 7, 524288 bytes)
[    0.642588] TCP: Hash tables configured (established 32768 bind 32768)
[    0.642607] TCP: reno registered
[    0.642618] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.642637] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.642709] NET: Registered protocol family 1
[    0.642721] pci 0000:00:02.0: Boot video device
[    0.643348] PCI: CLS 64 bytes, default 64
[    0.643420] Trying to unpack rootfs image as initramfs...
[    1.043568] Freeing initrd memory: 18648K (ffff880035b84000 - ffff880036dba000)
[    1.043575] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    1.043578] software IO TLB [mem 0xd4386000-0xd8386000] (64MB) mapped at [ffff8800d4386000-ffff8800d8385fff]
[    1.043835] microcode: CPU0 sig=0x306a9, pf=0x10, revision=0x12
[    1.043843] microcode: CPU1 sig=0x306a9, pf=0x10, revision=0x12
[    1.043852] microcode: CPU2 sig=0x306a9, pf=0x10, revision=0x12
[    1.043862] microcode: CPU3 sig=0x306a9, pf=0x10, revision=0x12
[    1.043927] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.043930] Scanning for low memory corruption every 60 seconds
[    1.044246] Initialise system trusted keyring
[    1.044318] audit: initializing netlink socket (disabled)
[    1.044329] type=2000 audit(1400606633.040:1): initialized
[    1.080841] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.082204] VFS: Disk quotas dquot_6.5.2
[    1.082251] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.082705] fuse init (API version 7.22)
[    1.082782] msgmni has been set to 7622
[    1.082839] Key type big_key registered
[    1.083295] Key type asymmetric registered
[    1.083299] Asymmetric key parser 'x509' registered
[    1.083333] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    1.083375] io scheduler noop registered
[    1.083378] io scheduler deadline registered (default)
[    1.083404] io scheduler cfq registered
[    1.083938] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.083955] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.083993] vesafb: mode is 1366x768x32, linelength=5504, pages=0
[    1.083995] vesafb: scrolling: redraw
[    1.083997] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    1.084615] vesafb: framebuffer at 0xe0000000, mapped to 0xffffc90004780000, using 4160k, total 4160k
[    1.180313] Console: switching to colour frame buffer device 170x48
[    1.275673] fb0: VESA VGA frame buffer device
[    1.275692] intel_idle: MWAIT substates: 0x21120
[    1.275694] intel_idle: v0.4 model 0x3A
[    1.275695] intel_idle: lapic_timer_reliable_states 0xffffffff
[    1.275810] ipmi message handler version 39.2
[    1.276435] ACPI: AC Adapter [ACAD] (off-line)
[    1.276529] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    1.277437] ACPI: Lid Switch [LID0]
[    1.277489] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.277494] ACPI: Power Button [PWRB]
[    1.277531] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    1.277534] ACPI: Power Button [PWRF]
[    1.279087] thermal LNXTHERM:00: registered as thermal_zone0
[    1.279090] ACPI: Thermal Zone [TZ00] (48 C)
[    1.279120] GHES: HEST is not enabled!
[    1.279248] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.281043] Linux agpgart interface v0.103
[    1.282464] brd: module loaded
[    1.283252] loop: module loaded
[    1.283794] libphy: Fixed MDIO Bus: probed
[    1.283921] tun: Universal TUN/TAP device driver, 1.6
[    1.283923] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.284011] PPP generic driver version 2.4.2
[    1.284099] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.284122] ehci-pci: EHCI PCI platform driver
[    1.284377] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    1.284386] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.284404] ehci-pci 0000:00:1a.0: debug port 2
[    1.288299] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    1.288321] ehci-pci 0000:00:1a.0: irq 16, io mem 0xf0619000
[    1.300240] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.300310] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.300314] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.300318] usb usb1: Product: EHCI Host Controller
[    1.300337] usb usb1: Manufacturer: Linux 3.13.0-24-generic ehci_hcd
[    1.300339] usb usb1: SerialNumber: 0000:00:1a.0
[    1.300502] hub 1-0:1.0: USB hub found
[    1.300512] hub 1-0:1.0: 3 ports detected
[    1.300819] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    1.300825] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.300841] ehci-pci 0000:00:1d.0: debug port 2
[    1.304743] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    1.304774] ehci-pci 0000:00:1d.0: irq 23, io mem 0xf0618000
[    1.309052] ACPI: Battery Slot [BAT1] (battery present)
[    1.316297] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.316389] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.316393] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.316396] usb usb2: Product: EHCI Host Controller
[    1.316398] usb usb2: Manufacturer: Linux 3.13.0-24-generic ehci_hcd
[    1.316400] usb usb2: SerialNumber: 0000:00:1d.0
[    1.316658] hub 2-0:1.0: USB hub found
[    1.316672] hub 2-0:1.0: 3 ports detected
[    1.316872] ehci-platform: EHCI generic platform driver
[    1.316886] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.316888] ohci-pci: OHCI PCI platform driver
[    1.316900] ohci-platform: OHCI generic platform driver
[    1.316908] uhci_hcd: USB Universal Host Controller Interface driver
[    1.317086] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    1.317097] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
[    1.317213] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    1.317248] xhci_hcd 0000:00:14.0: irq 40 for MSI/MSI-X
[    1.317346] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    1.317349] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.317351] usb usb3: Product: xHCI Host Controller
[    1.317353] usb usb3: Manufacturer: Linux 3.13.0-24-generic xhci_hcd
[    1.317355] usb usb3: SerialNumber: 0000:00:14.0
[    1.317564] hub 3-0:1.0: USB hub found
[    1.317579] hub 3-0:1.0: 4 ports detected
[    1.317984] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    1.317989] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 4
[    1.318040] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
[    1.318042] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.318045] usb usb4: Product: xHCI Host Controller
[    1.318047] usb usb4: Manufacturer: Linux 3.13.0-24-generic xhci_hcd
[    1.318049] usb usb4: SerialNumber: 0000:00:14.0
[    1.318233] hub 4-0:1.0: USB hub found
[    1.318248] hub 4-0:1.0: 4 ports detected
[    1.324407] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2A] at 0x60,0x64 irq 1,12
[    1.326917] i8042: Detected active multiplexing controller, rev 1.1
[    1.327755] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.327769] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.327801] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.327822] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.327840] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.328007] mousedev: PS/2 mouse device common for all mice
[    1.328342] rtc_cmos 00:05: RTC can wake from S4
[    1.328517] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.328550] rtc_cmos 00:05: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.328618] device-mapper: uevent: version 1.0.3
[    1.328723] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
[    1.328732] ledtrig-cpu: registered to indicate activity on CPUs
[    1.328848] TCP: cubic registered
[    1.328936] NET: Registered protocol family 10
[    1.329119] NET: Registered protocol family 17
[    1.329128] Key type dns_resolver registered
[    1.329473] Loading compiled-in X.509 certificates
[    1.330657] Loaded X.509 cert 'Magrathea: Glacier signing key: 69b0d0a79b85d90621706e8d06604d730b359fc0'
[    1.330679] registered taskstats version 1
[    1.333986] Key type trusted registered
[    1.336665] Key type encrypted registered
[    1.339190] AppArmor: AppArmor sha1 policy hashing enabled
[    1.339194] IMA: No TPM chip found, activating TPM-bypass!
[    1.339494] regulator-dummy: disabling
[    1.339589]   Magic number: 14:123:391
[    1.339596] hub 3-0:1.0: hash matches
[    1.339692] rtc_cmos 00:05: setting system clock to 2014-05-20 17:23:53 UTC (1400606633)
[    1.340521] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.340523] EDD information not available.
[    1.340573] PM: Hibernation image not present or could not be loaded.
[    1.341626] Freeing unused kernel memory: 1332K (ffffffff81d1e000 - ffffffff81e6b000)
[    1.341628] Write protecting the kernel read-only data: 12288k
[    1.344315] Freeing unused kernel memory: 844K (ffff88000172d000 - ffff880001800000)
[    1.346559] Freeing unused kernel memory: 708K (ffff880001b4f000 - ffff880001c00000)
[    1.362241] systemd-udevd[122]: starting version 204
[    1.370916] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.393098] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.393111] r8169 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
[    1.393353] r8169 0000:02:00.0: irq 41 for MSI/MSI-X
[    1.393526] r8169 0000:02:00.0 eth0: RTL8105e at 0xffffc90000640000, 08:9e:01:15:19:d5, XID 00c00000 IRQ 41
[    1.394077] ahci 0000:00:1f.2: version 3.0
[    1.394256] ahci 0000:00:1f.2: irq 42 for MSI/MSI-X
[    1.394315] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x3 impl SATA mode
[    1.394319] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part ems apst 
[    1.402376] scsi0 : ahci
[    1.402498] scsi1 : ahci
[    1.402594] scsi2 : ahci
[    1.402691] scsi3 : ahci
[    1.402786] scsi4 : ahci
[    1.402881] scsi5 : ahci
[    1.402948] ata1: SATA max UDMA/133 abar m2048@0xf0617000 port 0xf0617100 irq 42
[    1.402953] ata2: SATA max UDMA/133 abar m2048@0xf0617000 port 0xf0617180 irq 42
[    1.402956] ata3: DUMMY
[    1.402958] ata4: DUMMY
[    1.402960] ata5: DUMMY
[    1.402962] ata6: DUMMY
[    1.612239] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.720128] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.720155] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.720763] ata1.00: ATA-8: SAMSUNG MZMPC032HBCD-000L1, CXM12L1Q, max UDMA/133
[    1.720768] ata1.00: 62533296 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.720799] ata2.00: ATA-8: ST500LT012-9WS142, 0001LVM1, max UDMA/133
[    1.720803] ata2.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.721215] ata1.00: configured for UDMA/133
[    1.721449] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG MZMPC032 CXM1 PQ: 0 ANSI: 5
[    1.721665] ata2.00: configured for UDMA/133
[    1.721737] sd 0:0:0:0: [sda] 62533296 512-byte logical blocks: (32.0 GB/29.8 GiB)
[    1.721817] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.722048] sd 0:0:0:0: [sda] Write Protect is off
[    1.722053] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.722099] scsi 1:0:0:0: Direct-Access     ATA      ST500LT012-9WS14 0001 PQ: 0 ANSI: 5
[    1.722108] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.722249] sd 1:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.722253] sd 1:0:0:0: [sdb] 4096-byte physical blocks
[    1.722323] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    1.722445] sd 1:0:0:0: [sdb] Write Protect is off
[    1.722450] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.722493] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.722800]  sda: sda1
[    1.723122] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.744550] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
[    1.744555] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.744959] hub 1-1:1.0: USB hub found
[    1.745119] hub 1-1:1.0: 6 ports detected
[    1.765448]  sdb: sdb1 sdb2 < sdb5 >
[    1.766480] sd 1:0:0:0: [sdb] Attached SCSI disk
[    1.856150] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    1.988631] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
[    1.988635] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.989005] hub 2-1:1.0: USB hub found
[    1.989166] hub 2-1:1.0: 8 ports detected
[    2.040072] tsc: Refined TSC clocksource calibration: 1795.920 MHz
[    2.156089] usb 3-3: new high-speed USB device number 2 using xhci_hcd
[    2.180777] usb 3-3: New USB device found, idVendor=5986, idProduct=0295
[    2.180785] usb 3-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.180791] usb 3-3: Product: Lenovo EasyCamera
[    2.180794] usb 3-3: Manufacturer: Vimicro corp.
[    2.347991] usb 3-4: new full-speed USB device number 3 using xhci_hcd
[    2.365299] usb 3-4: New USB device found, idVendor=0cf3, idProduct=3005
[    2.365304] usb 3-4: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.550920] psmouse serio4: synaptics: Touchpad model: 1, fw: 8.1, id: 0x1e2b1, caps: 0xd00123/0x840300/0x123c00, board id: 1800, fw id: 1087391
[    2.594716] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input11
[    2.784909] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    2.800426] random: nonblocking pool is initialized
[    2.896732] init: plymouth-upstart-bridge main process (192) terminated with status 1
[    2.896749] init: plymouth-upstart-bridge main process ended, respawning
[    2.905916] init: plymouth-upstart-bridge main process (202) terminated with status 1
[    2.905935] init: plymouth-upstart-bridge main process ended, respawning
[    2.912064] init: plymouth-upstart-bridge main process (205) terminated with status 1
[    2.912080] init: plymouth-upstart-bridge main process ended, respawning
[    2.917297] init: plymouth-upstart-bridge main process (208) terminated with status 1
[    2.917322] init: plymouth-upstart-bridge main process ended, respawning
[    3.039759] Switched to clocksource tsc
[    3.042669] Adding 3997692k swap on /dev/sdb5.  Priority:-1 extents:1 across:3997692k FS
[    3.078881] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    3.155961] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[    3.173984] systemd-udevd[328]: starting version 204
[    3.273012] [drm] Initialized drm 1.1.0 20060810
[    3.273988] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[    3.306750] lp: driver loaded but no devices found
[    3.322876] [drm] Memory usable by graphics device = 2048M
[    3.322883] checking generic (e0000000 410000) vs hw (e0000000 10000000)
[    3.322887] fb: conflicting fb hw usage inteldrmfb vs VESA VGA - removing generic driver
[    3.322911] Console: switching to colour dummy device 80x25
[    3.324643] ppdev: user-space parallel port driver
[    3.357524] input: Ideapad extra buttons as /devices/platform/VPC2004:00/input/input12
[    3.385382] wmi: Mapper loaded
[    3.395888] i915 0000:00:02.0: irq 43 for MSI/MSI-X
[    3.395904] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    3.395906] [drm] Driver supports precise vblank timestamp query.
[    3.395986] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    3.561450] cfg80211: Calling CRDA to update world regulatory domain
[    3.587546] [drm] GMBUS [i915 gmbus vga] timed out, falling back to bit banging on pin 2
[    3.613249] fbcon: inteldrmfb (fb0) is primary device
[    3.738605] type=1400 audit(1400606635.892:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=529 comm="apparmor_parser"
[    3.738613] type=1400 audit(1400606635.892:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=529 comm="apparmor_parser"
[    3.738620] type=1400 audit(1400606635.892:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=529 comm="apparmor_parser"
[    3.739423] type=1400 audit(1400606635.892:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=529 comm="apparmor_parser"
[    3.739444] type=1400 audit(1400606635.892:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=529 comm="apparmor_parser"
[    3.739824] type=1400 audit(1400606635.896:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=529 comm="apparmor_parser"
[    3.740453] type=1400 audit(1400606635.896:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=530 comm="apparmor_parser"
[    3.740461] type=1400 audit(1400606635.896:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=530 comm="apparmor_parser"
[    3.740467] type=1400 audit(1400606635.896:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=530 comm="apparmor_parser"
[    3.797106] Bluetooth: Core ver 2.17
[    3.797168] NET: Registered protocol family 31
[    3.797169] Bluetooth: HCI device and connection manager initialized
[    3.797190] Bluetooth: HCI socket layer initialized
[    3.797199] Bluetooth: L2CAP socket layer initialized
[    3.797211] Bluetooth: SCO socket layer initialized
[    3.814114] ath: phy0: ASPM enabled: 0x42
[    3.814117] ath: EEPROM regdomain: 0x65
[    3.814118] ath: EEPROM indicates we should expect a direct regpair map
[    3.814120] ath: Country alpha2 being used: 00
[    3.814120] ath: Regpair used: 0x65
[    3.834643] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    3.834644] Bluetooth: BNEP filters: protocol multicast
[    3.834653] Bluetooth: BNEP socket layer initialized
[    3.837291] kvm: disabled by bios
[    3.852432] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[    3.853006] ieee80211 phy0: Atheros AR9285 Rev:2 mem=0xffffc90004800000, irq=18
[    4.026737] intel_rapl: domain uncore energy ctr 3351:3351 not working, skip
[    4.126520] cfg80211: World regulatory domain updated:
[    4.126521] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    4.126523] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    4.126524] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    4.126525] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    4.126526] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    4.126527] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    4.339316] Console: switching to colour frame buffer device 170x48
[    4.342654] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[    4.342656] i915 0000:00:02.0: registered panic notifier
[    4.346571] Bluetooth: RFCOMM TTY layer initialized
[    4.346584] Bluetooth: RFCOMM socket layer initialized
[    4.346589] Bluetooth: RFCOMM ver 1.11
[    4.358058] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    4.360040] acpi device:46: registered as cooling_device5
[    4.360223] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input13
[    4.360543] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    4.364441] mei_me 0000:00:16.0: irq 44 for MSI/MSI-X
[    4.378557] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[    4.382095] init: avahi-cups-reload main process (573) terminated with status 1
[    4.407199] hda_codec: CX20590: BIOS auto-probing.
[    4.407992] autoconfig: line_outs=1 (0x1f/0x0/0x0/0x0/0x0) type:speaker
[    4.407997]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    4.408000]    hp_outs=1 (0x19/0x0/0x0/0x0/0x0)
[    4.408002]    mono: mono_out=0x0
[    4.408003]    inputs:
[    4.408006]      Internal Mic=0x23
[    4.408008]      Mic=0x1a
[    4.409812] hda_codec: Enable sync_write for stable communication
[    4.429008] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input16
[    4.429242] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
[    4.429446] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[    4.503360] usbcore: registered new interface driver btusb
[    4.533138] Linux video capture interface: v2.00
[    4.536686] init: failsafe main process (672) killed by TERM signal
[    4.548291] uvcvideo: Found UVC 1.00 device Lenovo EasyCamera (5986:0295)
[    4.548297] uvcvideo: Forcing device quirks to 0x100 by module parameter for testing purpose.
[    4.548299] uvcvideo: Please report required quirks to the linux-uvc-devel mailing list.
[    4.548921] input: Lenovo EasyCamera as /devices/pci0000:00/0000:00:14.0/usb3/3-3/3-3:1.0/input/input17
[    4.549490] usbcore: registered new interface driver uvcvideo
[    4.549494] USB Video Class driver (1.1.1)
[    4.820161] [drm] Enabling RC6 states: RC6 on, RC6p on, RC6pp off
[    5.110027] r8169 0000:02:00.0 eth0: link down
[    5.110067] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    5.110582] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    5.127405] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    5.130502] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready


```


EDIT: OK, apparently it has nothing to do with plymouth. For the first time this morning it also occured with plymouth disabled.

---

### Post by slooksterpsv on 2014-05-21
Did that occur with acpi=off or no? The above looks normal to me.

---

### Post by MirkoCe on 2014-05-21
Ok, thanks. I modified the title as it seems not to be related to plymouth.

 No, I haven't disabled acpi (I wanna do that as my last chance)...
I have updated my drivers and I am gonna test another bit :/ I really don't understand, it happens really randomly so I can't really figure it out.

---

### Post by slooksterpsv on 2014-05-22
It's all good, I'm hoping someone else who's seen this issue will hop in and give their knowledge. I'm not to experienced with failure to boot, mine just works. I'm dealing with sound issues at the moment.

---

### Post by MirkoCe on 2014-05-22
I really appreciate your time and help. I will keep this thread up to date in case other users might find it useful or somebody could help me investigate.

---

### Post by andzep on 2014-11-21
Hi, I thought of sharing my story, as I had the same problems with a dell laptop and a new installation of linux mint. (GPU is ati radeon hd 6520g)

The laptop had win7 before, and started having some blue-screen problems and was also full of viruses. So I convinced the owners of the laptop, friends of mine, to install linux instead and try it for a while. As Windows had to be wiped off anyway. So they were happy to try and so I started, what I thought would be a fast and painless installation. From the beginning, the liveCD didn't want to boot (had GPU problems) so I started on recovery mode, installed linux and then (after starting again in recovery mode) the fglrx propietary drivers.... and everything worked fine! 

And that's when the booting-russian-roulette started. First I thought it was a driver problem, as the liveCD had problems with the native driver. But as it was only happening sometimes, and after one reboot it always worked, we thought it was not so bad to leave it like that. But then it started to happen a lot more... so I installed the fglrx repository together with amd catalyst, etc. etc. Tried the fglrx-updates, and well, lots of things. But nothing changed. It worked great -- when it did boot, but the booting problems remained and became really bad. Somtimes had to try about 10 times to get a succesfull boot. My friends were getting very esceptical about linux at this point :)  So, in a last attempt to solve the issue, I installed the latest driver from the amd site. Then I had about (almost) 10 successfull boots without a single bad one!!!... I thought the problem was solved, of course. And then, the day afterwards... nothing. Tried about 20 times or more and it didn't boot once. Not even on recovery mode.

So, that's when I started thinking, it could be a hardware problem instead of a driver problem. That's why the blue screens started appearing in Win7. And that also explained why it happened randomly, and getting worse and worse. So I read A LOT, and decided to do a reflow (on the oven) to see if that might solve any GPU issues. Talked to my friends (which gave me a green light), and I did it. 

And well, it might start happening again. Who knows. But until now, I really think it's fixed. 2nd day now and absolutely no boot-problems anymore.  So, if you tried everything with the fglrx drivers like me, and nothing else helps, and you're confident in doing a reflow to your laptop... well it might solve things for you too.

If the laptop starts failing again, I'll post an edit here of course. And if everything runs fine... well, I'll try to remember to post the good news here also :)

---

### Post by i-noph8 on 2015-03-20
Hello!
I have the same problem. And I am new to Linux, so I can't hardly help someone powerful advice. But perhaps the following information will help someone:
I used Kubuntu 14.10 and 14.04LTS and on both affected by this problem. My laptop is Dell N5110 with Intel HD3000 and Nvidia 525M. I tried to use different versions of proprietary drivers and I tried to disable splashscreen. It does not help. I have checked the memory for errors: everything is clean.This problem prevents me much, but I do not know how to approach it.
I had not any problem when I used Win8/Win8.1 x64 on my laptop.
The last strings in dmesg is
> [    5.885763] init: cups main process (2000) killed by HUP signal[    5.885776] init: cups main process ended, respawning


And according to tradition of this topic: [COLOR=#000000]sorry for any mistake I am not a native speaker. =)[/COLOR]

---

