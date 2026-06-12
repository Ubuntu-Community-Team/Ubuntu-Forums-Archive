---
title: "Sudden slow boot time caused by swap?"
date: 2013-08-15
forum: General Help
---

### Post by Sly14Cat on 2013-08-15
Hello,
Recently on my 2 week old Ubuntu install my boot time has dropped from 19s to a staggering 30-40s. Then only thing I've really installed is the Emerald WM and Xubuntu desktop. But even then I'm having this problem a few days after installing these. I really don't feel like reinstalling the OS AGAIN. I've gotten rid of every unnecessary start-up program I know of and the only problem I seem to be able to find is this odd looking line in my dmesg.

[    2.387940] usb 2-1.5: New USB device strings: Mfr=0, Product=0, SerialNumber=0
**[   21.780725] Adding 8259580k swap on /dev/sda5.  Priority:-1 extents:1 across:8259580k FS**
[   22.018611] EXT4-fs (sda4): re-mounted. Opts: errors=remount-ro

It seems that the swap is taking 20 seconds to mount. And I have no devices plugged in so it couldn't be USB problems.

**Specs**:
*Distro:* Ubuntu 13.04 x64
*Kernel*: 3.10.6-031006-generic
I'd be glad to add more information as you need it.

Please help me restore my boot time,
~ Sly

**EDIT:**
After removing the swap line from my fstab, I'm left with the same boot time. I believe it may be a USB problem and I'm investigating further and any input is appreciated.

---

### Post by Sly14Cat on 2013-08-15
Anything guys?

---

### Post by ian-weisser on 2013-08-15
Please post the entire first 60 seconds of dmesg, inside code tags.

---

### Post by Sly14Cat on 2013-08-15
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.10.6-031006-generic (apw@gomeisa) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #201308112316 SMP Mon Aug 12 03:17:33 UTC 2013
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.10.6-031006-generic root=UUID=c3ffd383-3363-4e96-9f4a-67cf1e78929d ro quiet splash acpi_backlight=vendor vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009d3ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009d400-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000001fffffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000020000000-0x00000000201fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000020200000-0x0000000040003fff] usable
[    0.000000] BIOS-e820: [mem 0x0000000040004000-0x0000000040004fff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000040005000-0x000000009ffaffff] usable
[    0.000000] BIOS-e820: [mem 0x000000009ffb0000-0x00000000a13affff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000a13b0000-0x00000000aa3befff] usable
[    0.000000] BIOS-e820: [mem 0x00000000aa3bf000-0x00000000aaebefff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000aaebf000-0x00000000aafbefff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000aafbf000-0x00000000aaffefff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000aafff000-0x00000000aaffffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000ab000000-0x00000000af9fffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000feb00000-0x00000000feb03fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed10000-0x00000000fed19fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffb80000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000024f5fffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.7 present.
[    0.000000] DMI: Dell Inc. Inspiron 5520/04G65K, BIOS A14 05/13/2013
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x24f600 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-E7FFF write-protect
[    0.000000]   E8000-EFFFF write-combining
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FE0000000 write-back
[    0.000000]   2 base 0A0000000 mask FF8000000 write-back
[    0.000000]   3 base 0A8000000 mask FFE000000 write-back
[    0.000000]   4 base 0AA000000 mask FFF000000 write-back
[    0.000000]   5 base 0FFA00000 mask FFFE00000 write-protect
[    0.000000]   6 base 0FFC00000 mask FFFC00000 write-protect
[    0.000000]   7 base 100000000 mask F00000000 write-back
[    0.000000]   8 base 200000000 mask F80000000 write-back
[    0.000000]   9 base 24F600000 mask FFFE00000 uncachable
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820: last_pfn = 0xab000 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000fe1b0-0x000fe1bf] mapped at [ffff8800000fe1b0]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000097000] 97000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01fca000, 0x01fcafff] PGTABLE
[    0.000000] BRK [0x01fcb000, 0x01fcbfff] PGTABLE
[    0.000000] BRK [0x01fcc000, 0x01fccfff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x24f400000-0x24f5fffff]
[    0.000000]  [mem 0x24f400000-0x24f5fffff] page 2M
[    0.000000] BRK [0x01fcd000, 0x01fcdfff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x24c000000-0x24f3fffff]
[    0.000000]  [mem 0x24c000000-0x24f3fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x200000000-0x24bffffff]
[    0.000000]  [mem 0x200000000-0x24bffffff] page 2M
[    0.000000] BRK [0x01fce000, 0x01fcefff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x00100000-0x1fffffff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x1fffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x20200000-0x40003fff]
[    0.000000]  [mem 0x20200000-0x3fffffff] page 2M
[    0.000000]  [mem 0x40000000-0x40003fff] page 4k
[    0.000000] init_memory_mapping: [mem 0x40005000-0x9ffaffff]
[    0.000000]  [mem 0x40005000-0x401fffff] page 4k
[    0.000000]  [mem 0x40200000-0x9fdfffff] page 2M
[    0.000000]  [mem 0x9fe00000-0x9ffaffff] page 4k
[    0.000000] init_memory_mapping: [mem 0xa13b0000-0xaa3befff]
[    0.000000]  [mem 0xa13b0000-0xa13fffff] page 4k
[    0.000000]  [mem 0xa1400000-0xaa1fffff] page 2M
[    0.000000]  [mem 0xaa200000-0xaa3befff] page 4k
[    0.000000] init_memory_mapping: [mem 0xaafff000-0xaaffffff]
[    0.000000]  [mem 0xaafff000-0xaaffffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x100000000-0x1ffffffff]
[    0.000000]  [mem 0x100000000-0x1ffffffff] page 2M
[    0.000000] RAMDISK: [mem 0x36168000-0x370abfff]
[    0.000000] ACPI: RSDP 00000000000fe020 00024 (v02 DELL  )
[    0.000000] ACPI: XSDT 00000000aaffe210 0009C (v01 DELL    CL09    00000001      01000013)
[    0.000000] ACPI: FACP 00000000aaffa000 0010C (v05 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: DSDT 00000000aafee000 08F82 (v01 DELL    CL09    00000000 ASL  00040000)
[    0.000000] ACPI: FACS 00000000aafb9000 00040
[    0.000000] ACPI: SLIC 00000000aaffd000 00176 (v01 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: UEFI 00000000aaffc000 00236 (v01 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: ASF! 00000000aaffb000 000A5 (v32 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: HPET 00000000aaff9000 00038 (v01 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: APIC 00000000aaff8000 0008C (v03 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: MCFG 00000000aaff7000 0003C (v01 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: SLIC 00000000aafed000 00176 (v01 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: SSDT 00000000aafec000 006FE (v01 COMPAL CRV ORB  00001000 ACPI 00040000)
[    0.000000] ACPI: BOOT 00000000aafea000 00028 (v01 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: ASPT 00000000aafe8000 00034 (v07 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: DBGP 00000000aafe7000 00034 (v01 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: FPDT 00000000aafe5000 00044 (v01 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: SSDT 00000000aafe4000 00968 (v01 COMPAL CRV ORB  00003000 ACPI 00040000)
[    0.000000] ACPI: SSDT 00000000aafe3000 00A92 (v01 COMPAL CRV ORB  00003000 ACPI 00040000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000024f5fffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x24f5fffff]
[    0.000000]   NODE_DATA [mem 0x24f5f0000-0x24f5f4fff]
[    0.000000]  [ffffea0000000000-ffffea00093fffff] PMD -> [ffff880246c00000-ffff88024ebfffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x24f5fffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009cfff]
[    0.000000]   node   0: [mem 0x00100000-0x1fffffff]
[    0.000000]   node   0: [mem 0x20200000-0x40003fff]
[    0.000000]   node   0: [mem 0x40005000-0x9ffaffff]
[    0.000000]   node   0: [mem 0xa13b0000-0xaa3befff]
[    0.000000]   node   0: [mem 0xaafff000-0xaaffffff]
[    0.000000]   node   0: [mem 0x100000000-0x24f5fffff]
[    0.000000] On node 0 totalpages: 2065243
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3996 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 10743 pages used for memmap
[    0.000000]   DMA32 zone: 687551 pages, LIFO batch:31
[    0.000000]   Normal zone: 21464 pages used for memmap
[    0.000000]   Normal zone: 1373696 pages, LIFO batch:31
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
[    0.000000] ACPI: IOAPIC (id[0x00] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 0, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] smpboot: Allowing 8 CPUs, 4 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000020200000
[    0.000000] PM: Registered nosave memory: 0000000040004000 - 0000000040005000
[    0.000000] PM: Registered nosave memory: 000000009ffb0000 - 00000000a13b0000
[    0.000000] PM: Registered nosave memory: 00000000aa3bf000 - 00000000aaebf000
[    0.000000] PM: Registered nosave memory: 00000000aaebf000 - 00000000aafbf000
[    0.000000] PM: Registered nosave memory: 00000000aafbf000 - 00000000aafff000
[    0.000000] PM: Registered nosave memory: 00000000ab000000 - 00000000afa00000
[    0.000000] PM: Registered nosave memory: 00000000afa00000 - 00000000e0000000
[    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
[    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000feb00000
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
[    0.000000] e820: [mem 0xafa00000-0xdfffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 29 pages/cpu @ffff88024f200000 s86336 r8192 d24256 u262144
[    0.000000] pcpu-alloc: s86336 r8192 d24256 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2032951
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.10.6-031006-generic root=UUID=c3ffd383-3363-4e96-9f4a-67cf1e78929d ro quiet splash acpi_backlight=vendor vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 8030700k/9689088k available (7246k kernel code, 1428116k absent, 230272k reserved, 6045k data, 1360k init)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000]     Experimental no-CBs for all CPUs
[    0.000000]     Experimental no-CBs CPUs: 0-255.
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 33554432 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.004000] tsc: Detected 2494.117 MHz processor
[    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 4988.23 BogoMIPS (lpj=9976468)
[    0.000004] pid_max: default: 32768 minimum: 301
[    0.000024] Security Framework initialized
[    0.000034] AppArmor: AppArmor initialized
[    0.000035] Yama: becoming mindful.
[    0.000489] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.002436] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.003297] Mount-cache hash table entries: 256
[    0.003451] Initializing cgroup subsys memory
[    0.003458] Initializing cgroup subsys devices
[    0.003460] Initializing cgroup subsys freezer
[    0.003461] Initializing cgroup subsys blkio
[    0.003462] Initializing cgroup subsys perf_event
[    0.003465] Initializing cgroup subsys hugetlb
[    0.003486] CPU: Physical Processor ID: 0
[    0.003487] CPU: Processor Core ID: 0
[    0.003492] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.003492] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.003848] mce: CPU supports 7 MCE banks
[    0.003858] CPU0: Thermal monitoring enabled (TM1)
[    0.003867] Last level iTLB entries: 4KB 512, 2MB 0, 4MB 0
[    0.003867] Last level dTLB entries: 4KB 512, 2MB 32, 4MB 32
[    0.003867] tlb_flushall_shift: 1
[    0.003975] Freeing SMP alternatives: 24k freed
[    0.005989] ACPI: Core revision 20130328
[    0.010501] ACPI: All ACPI Tables successfully acquired
[    0.023615] ftrace: allocating 30176 entries in 118 pages
[    0.037513] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.077240] smpboot: CPU0: Intel(R) Core(TM) i5-3210M CPU @ 2.50GHz (fam: 06, model: 3a, stepping: 09)
[    0.077248] TSC deadline timer enabled
[    0.077258] Performance Events: PEBS fmt1+, 16-deep LBR, IvyBridge events, Intel PMU driver.
[    0.077265] ... version:                3
[    0.077266] ... bit width:              48
[    0.077266] ... generic registers:      4
[    0.077267] ... value mask:             0000ffffffffffff
[    0.077268] ... max period:             000000007fffffff
[    0.077269] ... fixed-purpose events:   3
[    0.077270] ... event mask:             000000070000000f
[    0.091852] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.078328] smpboot: Booting Node   0, Processors  #1 #2 #3
[    0.118934] Brought up 4 CPUs
[    0.118938] smpboot: Total of 4 processors activated (19952.93 BogoMIPS)
[    0.122283] devtmpfs: initialized
[    0.123182] EVM: security.selinux
[    0.123183] EVM: security.SMACK64
[    0.123184] EVM: security.capability
[    0.123233] PM: Registering ACPI NVS region [mem 0xaaebf000-0xaafbefff] (1048576 bytes)
[    0.123981] regulator-dummy: no parameters
[    0.124020] NET: Registered protocol family 16
[    0.124142] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.124143] ACPI: bus type PCI registered
[    0.124145] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.124195] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.124198] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.147888] PCI: Using configuration type 1 for base access
[    0.147894] dmi type 0xB1 record - unknown flag
[    0.148669] bio: create slab <bio-0> at 0
[    0.148792] ACPI: Added _OSI(Module Device)
[    0.148794] ACPI: Added _OSI(Processor Device)
[    0.148795] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.148796] ACPI: Added _OSI(Processor Aggregator Device)
[    0.149974] ACPI: EC: Look up EC in DSDT
[    0.151163] ACPI: Executed 1 blocks of module-level executable AML code
[    0.163380] ACPI: SSDT 00000000aae17018 0083B (v01  PmRef  Cpu0Cst 00003001 INTL 20121220)
[    0.163683] ACPI: Dynamic OEM Table Load:
[    0.163684] ACPI: SSDT           (null) 0083B (v01  PmRef  Cpu0Cst 00003001 INTL 20121220)
[    0.171224] ACPI: SSDT 00000000aae18a98 00303 (v01  PmRef    ApIst 00003000 INTL 20121220)
[    0.171553] ACPI: Dynamic OEM Table Load:
[    0.171554] ACPI: SSDT           (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20121220)
[    0.179113] ACPI: SSDT 00000000aae16d98 00119 (v01  PmRef    ApCst 00003000 INTL 20121220)
[    0.179408] ACPI: Dynamic OEM Table Load:
[    0.179409] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20121220)
[    0.187615] ACPI: Interpreter enabled
[    0.187620] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20130328/hwxface-568)
[    0.187624] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20130328/hwxface-568)
[    0.187637] ACPI: (supports S0 S3 S4 S5)
[    0.187638] ACPI: Using IOAPIC for interrupt routing
[    0.187659] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.187745] ACPI: No dock devices found.
[    0.377397] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[    0.377507] \_SB_.PCI0:_OSC invalid UUID
[    0.377509] _OSC request data:1 8 0 
[    0.378025] PCI host bridge to bus 0000:00
[    0.378028] pci_bus 0000:00: root bus resource [bus 00-fe]
[    0.378030] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.378032] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.378033] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.378035] pci_bus 0000:00: root bus resource [mem 0xafa00000-0xfeafffff]
[    0.378042] pci 0000:00:00.0: [8086:0154] type 00 class 0x060000
[    0.378112] pci 0000:00:02.0: [8086:0166] type 00 class 0x030000
[    0.378123] pci 0000:00:02.0: reg 10: [mem 0xc0000000-0xc03fffff 64bit]
[    0.378129] pci 0000:00:02.0: reg 18: [mem 0xb0000000-0xbfffffff 64bit pref]
[    0.378134] pci 0000:00:02.0: reg 20: [io  0x3000-0x303f]
[    0.378220] pci 0000:00:14.0: [8086:1e31] type 00 class 0x0c0330
[    0.378242] pci 0000:00:14.0: reg 10: [mem 0xc0600000-0xc060ffff 64bit]
[    0.378313] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    0.378343] pci 0000:00:14.0: System wakeup disabled by ACPI
[    0.378376] pci 0000:00:16.0: [8086:1e3a] type 00 class 0x078000
[    0.378400] pci 0000:00:16.0: reg 10: [mem 0xc0614000-0xc061400f 64bit]
[    0.378477] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.378546] pci 0000:00:1a.0: [8086:1e2d] type 00 class 0x0c0320
[    0.378567] pci 0000:00:1a.0: reg 10: [mem 0xc0619000-0xc06193ff]
[    0.378659] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.378709] pci 0000:00:1b.0: [8086:1e20] type 00 class 0x040300
[    0.378723] pci 0000:00:1b.0: reg 10: [mem 0xc0610000-0xc0613fff 64bit]
[    0.378791] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.378840] pci 0000:00:1c.0: [8086:1e10] type 01 class 0x060400
[    0.378919] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.378953] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.378980] pci 0000:00:1c.1: [8086:1e12] type 01 class 0x060400
[    0.379059] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.379088] pci 0000:00:1c.1: System wakeup disabled by ACPI
[    0.379124] pci 0000:00:1d.0: [8086:1e26] type 00 class 0x0c0320
[    0.379145] pci 0000:00:1d.0: reg 10: [mem 0xc0618000-0xc06183ff]
[    0.379237] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.379268] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.379298] pci 0000:00:1f.0: [8086:1e57] type 00 class 0x060100
[    0.379445] pci 0000:00:1f.2: [8086:1e03] type 00 class 0x010601
[    0.379463] pci 0000:00:1f.2: reg 10: [io  0x3088-0x308f]
[    0.379471] pci 0000:00:1f.2: reg 14: [io  0x3094-0x3097]
[    0.379479] pci 0000:00:1f.2: reg 18: [io  0x3080-0x3087]
[    0.379487] pci 0000:00:1f.2: reg 1c: [io  0x3090-0x3093]
[    0.379495] pci 0000:00:1f.2: reg 20: [io  0x3060-0x307f]
[    0.379503] pci 0000:00:1f.2: reg 24: [mem 0xc0617000-0xc06177ff]
[    0.379550] pci 0000:00:1f.2: PME# supported from D3hot
[    0.379596] pci 0000:00:1f.3: [8086:1e22] type 00 class 0x0c0500
[    0.379610] pci 0000:00:1f.3: reg 10: [mem 0xc0615000-0xc06150ff 64bit]
[    0.379631] pci 0000:00:1f.3: reg 20: [io  0x3040-0x305f]
[    0.379821] pci 0000:01:00.0: [10ec:8136] type 00 class 0x020000
[    0.379889] pci 0000:01:00.0: reg 10: [io  0x2000-0x20ff]
[    0.380003] pci 0000:01:00.0: reg 18: [mem 0xc0404000-0xc0404fff 64bit pref]
[    0.380077] pci 0000:01:00.0: reg 20: [mem 0xc0400000-0xc0403fff 64bit pref]
[    0.380412] pci 0000:01:00.0: supports D1 D2
[    0.380413] pci 0000:01:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.387430] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    0.387435] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.387443] pci 0000:00:1c.0:   bridge window [mem 0xc0400000-0xc04fffff 64bit pref]
[    0.387564] pci 0000:02:00.0: [8086:0887] type 00 class 0x028000
[    0.387611] pci 0000:02:00.0: reg 10: [mem 0xc0500000-0xc0501fff 64bit]
[    0.387841] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
[    0.395456] pci 0000:00:1c.1: PCI bridge to [bus 02]
[    0.395463] pci 0000:00:1c.1:   bridge window [mem 0xc0500000-0xc05fffff]
[    0.395527] \_SB_.PCI0:_OSC invalid UUID
[    0.395528] _OSC request data:1 1f 0 
[    0.395531] acpi PNP0A08:00: ACPI _OSC support notification failed, disabling PCIe ASPM
[    0.395533] acpi PNP0A08:00: Unable to request _OSC control (_OSC support mask: 0x08)
[    0.455740] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 10 11 12 14 15) *7
[    0.455789] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 10 *11 12 14 15)
[    0.455835] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.455882] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 *10 11 12 14 15)
[    0.455927] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.455972] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 10 11 12 14 15) *7
[    0.456018] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 *10 11 12 14 15)
[    0.456064] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 10 *11 12 14 15)
[    0.456275] ACPI: Enabled 5 GPEs in block 00 to 3F
[    0.456281] acpi root: \_SB_.PCI0 notify handler is installed
[    0.456320] Found 1 acpi root devices
[    0.456349] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.456457] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.456460] vgaarb: loaded
[    0.456461] vgaarb: bridge control possible 0000:00:02.0
[    0.456586] SCSI subsystem initialized
[    0.456588] ACPI: bus type ATA registered
[    0.456622] libata version 3.00 loaded.
[    0.456635] ACPI: bus type USB registered
[    0.456647] usbcore: registered new interface driver usbfs
[    0.456653] usbcore: registered new interface driver hub
[    0.456686] usbcore: registered new device driver usb
[    0.456779] PCI: Using ACPI for IRQ routing
[    0.463307] PCI: pci_cache_line_size set to 64 bytes
[    0.463396] e820: reserve RAM buffer [mem 0x0009d400-0x0009ffff]
[    0.463398] e820: reserve RAM buffer [mem 0x40004000-0x43ffffff]
[    0.463399] e820: reserve RAM buffer [mem 0x9ffb0000-0x9fffffff]
[    0.463400] e820: reserve RAM buffer [mem 0xaa3bf000-0xabffffff]
[    0.463401] e820: reserve RAM buffer [mem 0xab000000-0xabffffff]
[    0.463403] e820: reserve RAM buffer [mem 0x24f600000-0x24fffffff]
[    0.463470] NetLabel: Initializing
[    0.463472] NetLabel:  domain hash size = 128
[    0.463472] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.463485] NetLabel:  unlabeled traffic allowed by default
[    0.463534] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.463539] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.465551] Switching to clocksource hpet
[    0.469393] AppArmor: AppArmor Filesystem Enabled
[    0.469414] pnp: PnP ACPI init
[    0.469424] ACPI: bus type PNP registered
[    0.469452] pnp 00:00: [dma 4]
[    0.469467] pnp 00:00: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.469484] pnp 00:01: Plug and Play ACPI device, IDs INT0800 (active)
[    0.469581] pnp 00:02: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.469606] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.469641] system 00:04: [io  0x0680-0x069f] has been reserved
[    0.469643] system 00:04: [io  0x1000-0x100f] has been reserved
[    0.469644] system 00:04: [io  0xffff] has been reserved
[    0.469646] system 00:04: [io  0xffff] has been reserved
[    0.469648] system 00:04: [io  0x0400-0x0453] has been reserved
[    0.469649] system 00:04: [io  0x0458-0x047f] has been reserved
[    0.469651] system 00:04: [io  0x0500-0x057f] has been reserved
[    0.469653] system 00:04: [io  0x164e-0x164f] has been reserved
[    0.469654] system 00:04: [io  0xfd60-0xfd63] has been reserved
[    0.469657] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.469676] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.469714] system 00:06: [io  0x0454-0x0457] has been reserved
[    0.469716] system 00:06: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.469748] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.469772] pnp 00:08: Plug and Play ACPI device, IDs DLL0569 PNP0f13 (active)
[    0.529784] system 00:09: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.529787] system 00:09: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.529788] system 00:09: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.529790] system 00:09: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.529792] system 00:09: [mem 0xe0000000-0xefffffff] has been reserved
[    0.529794] system 00:09: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.529795] system 00:09: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.529797] system 00:09: [mem 0xff000000-0xff000fff] has been reserved
[    0.529799] system 00:09: [mem 0xff010000-0xffffffff] could not be reserved
[    0.529801] system 00:09: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.529803] system 00:09: [mem 0xafa00000-0xafa00fff] has been reserved
[    0.529805] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.530036] system 00:0a: [mem 0x20000000-0x201fffff] has been reserved
[    0.530037] system 00:0a: [mem 0x40004000-0x40004fff] has been reserved
[    0.530040] system 00:0a: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.530053] pnp: PnP ACPI: found 11 devices
[    0.530054] ACPI: bus type PNP unregistered
[    0.536079] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    0.536083] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.536091] pci 0000:00:1c.0:   bridge window [mem 0xc0400000-0xc04fffff 64bit pref]
[    0.536098] pci 0000:00:1c.1: PCI bridge to [bus 02]
[    0.536102] pci 0000:00:1c.1:   bridge window [mem 0xc0500000-0xc05fffff]
[    0.536246] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.536248] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.536250] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.536251] pci_bus 0000:00: resource 7 [mem 0xafa00000-0xfeafffff]
[    0.536253] pci_bus 0000:01: resource 0 [io  0x2000-0x2fff]
[    0.536255] pci_bus 0000:01: resource 2 [mem 0xc0400000-0xc04fffff 64bit pref]
[    0.536257] pci_bus 0000:02: resource 1 [mem 0xc0500000-0xc05fffff]
[    0.536279] NET: Registered protocol family 2
[    0.536441] TCP established hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.536608] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.536721] TCP: Hash tables configured (established 65536 bind 65536)
[    0.536740] TCP: reno registered
[    0.536750] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.536776] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.536840] NET: Registered protocol family 1
[    0.536850] pci 0000:00:02.0: Boot video device
[    0.569826] PCI: CLS 64 bytes, default 64
[    0.569863] Trying to unpack rootfs image as initramfs...
[    0.810311] Freeing initrd memory: 15632k freed
[    0.812029] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.812034] software IO TLB [mem 0xa63bf000-0xaa3bf000] (64MB) mapped at [ffff8800a63bf000-ffff8800aa3befff]
[    0.812075] Simple Boot Flag at 0x44 set to 0x1
[    0.812235] Scanning for low memory corruption every 60 seconds
[    0.812405] Initialise module verification
[    0.812439] audit: initializing netlink socket (disabled)
[    0.812447] type=2000 audit(1376606546.800:1): initialized
[    0.837685] bounce pool size: 64 pages
[    0.837697] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.838873] VFS: Disk quotas dquot_6.5.2
[    0.838906] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.839273] fuse init (API version 7.22)
[    0.839335] msgmni has been set to 15715
[    0.839795] Key type asymmetric registered
[    0.839797] Asymmetric key parser 'x509' registered
[    0.839822] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.839860] io scheduler noop registered
[    0.839861] io scheduler deadline registered (default)
[    0.839882] io scheduler cfq registered
[    0.840027] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.840037] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.840065] intel_idle: MWAIT substates: 0x21120
[    0.840067] intel_idle: v0.4 model 0x3A
[    0.840067] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.840154] ACPI: AC Adapter [ACAD] (off-line)
[    0.840229] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/PNP0C0C:00/input/input0
[    0.840233] ACPI: Power Button [PWRB]
[    0.840265] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    0.840285] ACPI: Lid Switch [LID0]
[    0.840310] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.840312] ACPI: Power Button [PWRF]
[    0.840373] ACPI: Requesting acpi_cpufreq
[    0.899084] GHES: HEST is not enabled!
[    0.899166] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.110336] ACPI: Battery Slot [BAT1] (battery present)
[    1.110430] Linux agpgart interface v0.103
[    1.111382] brd: module loaded
[    1.111832] loop: module loaded
[    1.112071] libphy: Fixed MDIO Bus: probed
[    1.112128] tun: Universal TUN/TAP device driver, 1.6
[    1.112129] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.112167] PPP generic driver version 2.4.2
[    1.112200] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.112202] ehci-pci: EHCI PCI platform driver
[    1.112291] ehci-pci 0000:00:1a.0: setting latency timer to 64
[    1.112299] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    1.112304] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.112317] ehci-pci 0000:00:1a.0: debug port 2
[    1.116211] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    1.116226] ehci-pci 0000:00:1a.0: irq 16, io mem 0xc0619000
[    1.126325] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.126341] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.126342] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.126344] usb usb1: Product: EHCI Host Controller
[    1.126346] usb usb1: Manufacturer: Linux 3.10.6-031006-generic ehci_hcd
[    1.126347] usb usb1: SerialNumber: 0000:00:1a.0
[    1.126435] hub 1-0:1.0: USB hub found
[    1.126439] hub 1-0:1.0: 2 ports detected
[    1.126580] ehci-pci 0000:00:1d.0: setting latency timer to 64
[    1.126585] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    1.126589] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.126601] ehci-pci 0000:00:1d.0: debug port 2
[    1.130507] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    1.130521] ehci-pci 0000:00:1d.0: irq 23, io mem 0xc0618000
[    1.142347] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.142357] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.142359] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.142361] usb usb2: Product: EHCI Host Controller
[    1.142362] usb usb2: Manufacturer: Linux 3.10.6-031006-generic ehci_hcd
[    1.142363] usb usb2: SerialNumber: 0000:00:1d.0
[    1.142437] hub 2-0:1.0: USB hub found
[    1.142440] hub 2-0:1.0: 2 ports detected
[    1.142496] ehci-platform: EHCI generic platform driver
[    1.142501] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.142510] uhci_hcd: USB Universal Host Controller Interface driver
[    1.142602] xhci_hcd 0000:00:14.0: setting latency timer to 64
[    1.142605] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    1.142609] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
[    1.142693] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    1.142714] xhci_hcd 0000:00:14.0: irq 40 for MSI/MSI-X
[    1.142755] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    1.142757] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.142758] usb usb3: Product: xHCI Host Controller
[    1.142760] usb usb3: Manufacturer: Linux 3.10.6-031006-generic xhci_hcd
[    1.142761] usb usb3: SerialNumber: 0000:00:14.0
[    1.142813] xHCI xhci_add_endpoint called for root hub
[    1.142815] xHCI xhci_check_bandwidth called for root hub
[    1.142829] hub 3-0:1.0: USB hub found
[    1.142836] hub 3-0:1.0: 4 ports detected
[    1.143065] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    1.143068] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 4
[    1.143085] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
[    1.143087] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.143088] usb usb4: Product: xHCI Host Controller
[    1.143090] usb usb4: Manufacturer: Linux 3.10.6-031006-generic xhci_hcd
[    1.143091] usb usb4: SerialNumber: 0000:00:14.0
[    1.143144] xHCI xhci_add_endpoint called for root hub
[    1.143146] xHCI xhci_check_bandwidth called for root hub
[    1.143158] hub 4-0:1.0: USB hub found
[    1.143164] hub 4-0:1.0: 4 ports detected
[    1.166419] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.186004] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.186009] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.186092] mousedev: PS/2 mouse device common for all mice
[    1.186323] rtc_cmos 00:05: RTC can wake from S4
[    1.186453] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.186481] rtc_cmos 00:05: alarms up to one month, 242 bytes nvram, hpet irqs
[    1.186530] device-mapper: uevent: version 1.0.3
[    1.186577] device-mapper: ioctl: 4.24.0-ioctl (2013-01-15) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    1.186582] Intel P-state driver initializing.
[    1.186591] Intel pstate controlling: cpu 0
[    1.186603] Intel pstate controlling: cpu 1
[    1.186613] Intel pstate controlling: cpu 2
[    1.186627] Intel pstate controlling: cpu 3
[    1.186716] cpuidle: using governor ladder
[    1.186815] cpuidle: using governor menu
[    1.186826] ledtrig-cpu: registered to indicate activity on CPUs
[    1.186934] ashmem: initialized
[    1.187047] TCP: cubic registered
[    1.187113] NET: Registered protocol family 10
[    1.187265] NET: Registered protocol family 17
[    1.187273] Key type dns_resolver registered
[    1.187458] Loading module verification certificates
[    1.188222] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: 173af51c13a897b03fd2598caf85d0407708e9b7'
[    1.188231] registered taskstats version 1
[    1.190436] Key type trusted registered
[    1.192392] Key type encrypted registered
[    1.194695] rtc_cmos 00:05: setting system clock to 2013-08-15 22:42:27 UTC (1376606547)
[    1.194895] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.194897] EDD information not available.
[    1.195781] Freeing unused kernel memory: 1360k freed
[    1.195932] Write protecting the kernel read-only data: 12288k
[    1.197558] Freeing unused kernel memory: 936k freed
[    1.199137] Freeing unused kernel memory: 868k freed
[    1.206793] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.212083] udevd[123]: starting version 175
[    1.243762] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.243997] r8169 0000:01:00.0: irq 41 for MSI/MSI-X
[    1.244167] r8169 0000:01:00.0 eth0: RTL8105e at 0xffffc90000c3c000, d4:be:d9:26:30:8e, XID 00c00000 IRQ 41
[    1.245971] ahci 0000:00:1f.2: version 3.0
[    1.246086] ahci 0000:00:1f.2: irq 42 for MSI/MSI-X
[    1.258509] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x5 impl SATA mode
[    1.258515] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part ems apst 
[    1.258522] ahci 0000:00:1f.2: setting latency timer to 64
[    1.270530] scsi0 : ahci
[    1.270631] scsi1 : ahci
[    1.270705] scsi2 : ahci
[    1.270937] scsi3 : ahci
[    1.271010] scsi4 : ahci
[    1.271061] scsi5 : ahci
[    1.271112] ata1: SATA max UDMA/133 abar m2048@0xc0617000 port 0xc0617100 irq 42
[    1.271114] ata2: DUMMY
[    1.271118] ata3: SATA max UDMA/133 abar m2048@0xc0617000 port 0xc0617200 irq 42
[    1.271119] ata4: DUMMY
[    1.271121] ata5: DUMMY
[    1.271122] ata6: DUMMY
[    1.438726] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.571355] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
[    1.571360] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.571732] hub 1-1:1.0: USB hub found
[    1.571809] hub 1-1:1.0: 6 ports detected
[    1.590926] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.596765] ata3.00: ATAPI: TSSTcorp DVD+/-RW SN-208BB, D300, max UDMA/100
[    1.598920] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.603595] ata3.00: configured for UDMA/100
[    1.613762] ata1.00: ATA-8: WDC WD10JPVT-75A1YT0, 01.01A01, max UDMA/133
[    1.613767] ata1.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    1.615247] ata1.00: configured for UDMA/133
[    1.615543] scsi 0:0:0:0: Direct-Access     ATA      WDC WD10JPVT-75A 01.0 PQ: 0 ANSI: 5
[    1.615779] sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.615783] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    1.615789] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.615862] sd 0:0:0:0: [sda] Write Protect is off
[    1.615865] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.615898] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.618446] scsi 2:0:0:0: CD-ROM            TSSTcorp DVD+-RW SN-208BB D300 PQ: 0 ANSI: 5
[    1.626795] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.626800] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.627019] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    1.627137] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    1.651215]  sda: sda1 sda2 sda3 < sda5 > sda4
[    1.652078] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.682979] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    1.811167] tsc: Refined TSC clocksource calibration: 2494.335 MHz
[    1.811174] Switching to clocksource tsc
[    1.815622] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
[    1.815626] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.816009] hub 2-1:1.0: USB hub found
[    1.816078] hub 2-1:1.0: 8 ports detected
[    1.887283] usb 1-1.3: new high-speed USB device number 3 using ehci-pci
[    1.980255] usb 1-1.3: New USB device found, idVendor=0bda, idProduct=0129
[    1.980275] usb 1-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.980278] usb 1-1.3: Product: USB2.0-CRW
[    1.980281] usb 1-1.3: Manufacturer: Generic
[    1.980283] usb 1-1.3: SerialNumber: 20100201396000000
[    2.051639] usb 1-1.5: new high-speed USB device number 4 using ehci-pci
[    2.214326] usb 1-1.5: New USB device found, idVendor=064e, idProduct=8125
[    2.214332] usb 1-1.5: New USB device strings: Mfr=2, Product=1, SerialNumber=0
[    2.214336] usb 1-1.5: Product: Laptop_Integrated_Webcam_HD
[    2.214338] usb 1-1.5: Manufacturer: SuYin
[    2.291911] usb 2-1.5: new full-speed USB device number 3 using ehci-pci
[    2.388113] usb 2-1.5: New USB device found, idVendor=0a12, idProduct=0001
[    2.388118] usb 2-1.5: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.438879] EXT4-fs (sda4): mounted filesystem with ordered data mode. Opts: (null)
[    3.710674] init: ureadahead main process (297) terminated with status 5
[    4.757519] Adding 8259580k swap on /dev/sda5.  Priority:-1 extents:1 across:8259580k FS
[    8.075453] EXT4-fs (sda4): re-mounted. Opts: errors=remount-ro
[    8.124334] udevd[514]: starting version 175
[    9.365946] cfg80211: Calling CRDA to update world regulatory domain
[    9.420674] wmi: Mapper loaded
[    9.466233] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[    9.482088] microcode: CPU0 sig=0x306a9, pf=0x10, revision=0x15
[    9.674342] microcode: CPU1 sig=0x306a9, pf=0x10, revision=0x15
[    9.675373] microcode: CPU2 sig=0x306a9, pf=0x10, revision=0x15
[    9.676350] microcode: CPU3 sig=0x306a9, pf=0x10, revision=0x15
[    9.677398] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    9.973919] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20130328/utaddress-251)
[    9.973927] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    9.973932] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20130328/utaddress-251)
[    9.973935] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    9.973937] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 1 (20130328/utaddress-251)
[    9.973940] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    9.973941] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   10.019369] input: Dell WMI hotkeys as /devices/virtual/input/input4
[   10.221968] lp: driver loaded but no devices found
[   10.319683] Bluetooth: Core ver 2.16
[   10.319699] NET: Registered protocol family 31
[   10.319701] Bluetooth: HCI device and connection manager initialized
[   10.319708] Bluetooth: HCI socket layer initialized
[   10.319711] Bluetooth: L2CAP socket layer initialized
[   10.319717] Bluetooth: SCO socket layer initialized
[   10.337321] rts5139: module is from the staging directory, the quality is unknown, you have been warned.
[   10.340506] scsi6 : SCSI emulation for RTS5139 USB card reader
[   10.340598] usbcore: registered new interface driver rts5139
[   10.340633] scsi 6:0:0:0: Direct-Access     Generic- xD/SD/M.S.       1.00 PQ: 0 ANSI: 0 CCS
[   10.340986] sd 6:0:0:0: Attached scsi generic sg2 type 0
[   10.344000] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[   10.351627] [drm] Initialized drm 1.1.0 20060810
[   10.361978] Linux video capture interface: v2.00
[   10.367239] Intel(R) Wireless WiFi driver for Linux, in-tree:
[   10.367241] Copyright(c) 2003-2013 Intel Corporation
[   10.367453] iwlwifi 0000:02:00.0: irq 43 for MSI/MSI-X
[   10.417474] mei_me 0000:00:16.0: setting latency timer to 64
[   10.417511] mei_me 0000:00:16.0: irq 44 for MSI/MSI-X
[   10.490879] [drm] Memory usable by graphics device = 2048M
[   10.490885] i915 0000:00:02.0: setting latency timer to 64
[   10.514102] i915 0000:00:02.0: irq 45 for MSI/MSI-X
[   10.514109] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   10.514110] [drm] Driver supports precise vblank timestamp query.
[   10.514186] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   10.530639] usbcore: registered new interface driver btusb
[   10.539728] iwlwifi 0000:02:00.0: loaded firmware version 18.168.6.1 op_mode iwldvm
[   10.550724] fbcon: inteldrmfb (fb0) is primary device
[   10.884309] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   10.884310] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   10.884311] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   10.884320] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEVICE_TESTMODE enabled
[   10.884321] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_P2P disabled
[   10.884322] iwlwifi 0000:02:00.0: Detected Intel(R) Centrino(R) Wireless-N 2230 BGN, REV=0xC8
[   10.884372] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[   10.931148] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   10.945068] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_HD (064e:8125)
[   10.971104] input: Laptop_Integrated_Webcam_HD as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.0/input/input5
[   10.971178] usbcore: registered new interface driver uvcvideo
[   10.971179] USB Video Class driver (1.1.1)
[   11.018681] ip_tables: (C) 2000-2006 Netfilter Core Team
[   11.168159] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   11.226005] Console: switching to colour frame buffer device 170x48
[   11.228910] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   11.228913] i915 0000:00:02.0: registered panic notifier
[   11.229986] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   11.230052] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6
[   11.230148] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   11.230288] snd_hda_intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[   11.286609] psmouse serio1: elantech: assuming hardware version 3 (with firmware version 0x450f02)
[   11.315895] psmouse serio1: elantech: Synaptics capabilities query result 0x79, 0x17, 0x0c.
[   11.366439] hda_codec: CX20590: BIOS auto-probing.
[   11.366875] autoconfig: line_outs=1 (0x1f/0x0/0x0/0x0/0x0) type:speaker
[   11.366877]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   11.366878]    hp_outs=1 (0x19/0x0/0x0/0x0/0x0)
[   11.366878]    mono: mono_out=0x0
[   11.366879]    inputs:
[   11.366881]      Internal Mic=0x23
[   11.366882]      Mic=0x1a
[   11.367726] hda_codec: Enable sync_write for stable communication
[   11.395791] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   11.395865] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   11.395921] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   11.448488] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio1/input/input10
[   11.645095] cfg80211: World regulatory domain updated:
[   11.645098] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   11.645100] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.645102] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   11.645103] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   11.645104] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.645105] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.721120] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   11.838922] [drm] Enabling RC6 states: RC6 on, RC6p on, RC6pp off
[   12.169134] type=1400 audit(1376620958.456:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=907 comm="apparmor_parser"
[   12.169218] type=1400 audit(1376620958.456:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=798 comm="apparmor_parser"
[   12.169226] type=1400 audit(1376620958.456:4): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=803 comm="apparmor_parser"
[   12.169475] type=1400 audit(1376620958.456:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=907 comm="apparmor_parser"
[   12.169662] type=1400 audit(1376620958.456:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=907 comm="apparmor_parser"
[   12.169752] type=1400 audit(1376620958.456:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=798 comm="apparmor_parser"
[   12.169758] type=1400 audit(1376620958.456:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=803 comm="apparmor_parser"
[   12.170043] type=1400 audit(1376620958.456:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=798 comm="apparmor_parser"
[   12.170054] type=1400 audit(1376620958.456:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=803 comm="apparmor_parser"
[   14.192663] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   14.192666] Bluetooth: BNEP filters: protocol multicast
[   14.192676] Bluetooth: BNEP socket layer initialized
[   14.217534] init: avahi-cups-reload main process (1046) terminated with status 1
[   14.232339] Bluetooth: RFCOMM TTY layer initialized
[   14.232352] Bluetooth: RFCOMM socket layer initialized
[   14.232353] Bluetooth: RFCOMM ver 1.11
[   14.460960] ppdev: user-space parallel port driver
[   14.927671] type=1400 audit(1376620961.212:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1087 comm="apparmor_parser"
[   15.066818] init: failsafe main process (1057) killed by TERM signal
[   18.941732] r8169 0000:01:00.0 eth0: link down
[   18.941779] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.011053] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[   19.018702] iwlwifi 0000:02:00.0: Radio type=0x2-0x0-0x0
[   19.370594] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[   19.378252] iwlwifi 0000:02:00.0: Radio type=0x2-0x0-0x0
[   19.565491] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.193325] wlan0: authenticate with e8:40:f2:88:d7:5c
[   21.207492] wlan0: send auth to e8:40:f2:88:d7:5c (try 1/3)
[   21.210603] wlan0: authenticated
[   21.210731] iwlwifi 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   21.210735] iwlwifi 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   21.213298] wlan0: associate with e8:40:f2:88:d7:5c (try 1/3)
[   21.215729] wlan0: RX AssocResp from e8:40:f2:88:d7:5c (capab=0x411 status=0 aid=3)
[   21.222393] wlan0: associated
[   21.222416] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

```

Just to add my two cents what I find odd is that although it takes 30-40 seconds to boot but dmesg only records the first 21s. So I'm guessing it may be a Xorg problem. Anyways removing Unity didn't help, you guys probably know what's going on here better than what I do.
 
EDIT:
That's odd, it seems to be all evenly spaced out now, but still, I don't understand the long gap after dmesg stops recording and LightDM starts up.
Just thought I'd add this in; does anyone know how to get rid of bluetooth

Thanks,
Sly

---

### Post by ian-weisser on 2013-08-16
21 seconds to a mounted, connected system is not bad.

However, this section shows a ureadahead failure (which lengthens boot), and a slow remount of sda.
```
[    2.388118] usb 2-1.5: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[COLOR=#0000ff][    2.438879] EXT4-fs (sda4): mounted filesystem with ordered data mode. Opts: (null)[/COLOR]
[COLOR=#ffd700][    3.710674] init: ureadahead main process (297) terminated with status 5[/COLOR]
[    4.757519] Adding 8259580k swap on /dev/sda5.  Priority:-1 extents:1 across:8259580k FS
[COLOR=#0000ff][    8.075453] EXT4-fs (sda4): re-mounted. Opts: errors=remount-ro[/COLOR]
[    8.124334] udevd[514]: starting version 175

```

Slow remounts may be due to many possible factors...including a dying hard drive, lots of partitions, errors in the partition table, exotic formats, etc. I'm NOT saying to run out and buy a new hard drive, or to repartition or reformat the existing drive. Merely keep an eye on it.

ureadahead is a tiny application that speeds up boot from 45-60 seconds down to 15-20. It does this by reading whole sectors of the hard drive in physical order instead of in the system's read order. Moving the drive's physical r/w head all over the place is -by far- the slowest part of the process, and ureadahead tries to eliminate all unnecessary head movement during boot.

Ureadahead error 5 is very specific. It usually happens when ureadahead cannot find /var (for example, if /var is on a different partition), or cannot otherwise create the pack file full of data that it just read from the disk.

Try reinstalling ureadahead
```
sudo apr-get install --reinstall ureadahead
```

If that doesn't fix the problem, then see [http://ubuntuforums.org/showthread.php?t=1434502](http://ubuntuforums.org/showthread.php?t=1434502) to learn how to get ureadahead debug information, and open a bug report. The developer did not intend ureadahead to fail.

---

### Post by Sly14Cat on 2013-08-17
Reinstalling ureadahead has not helped anything and I'm stilling getting error 5. I find the idea of my HDD failing odd considering this laptop is only 1 year old as of last week.
I've been worrying about a failing HDD for months now but it seems to be a Linux only problem for me and I have NO IDEA why.

For example I dual boot Windows and Linux and here's what I get,
When Ubuntu was taking 40s to boot a few months ago I was scared my HDD was failing. But when I boot into Windows 7 it took 15s to get to the desktop.
Again a month or so ago when Linux Mint was taking 40s to boot and I was scared my HDD was failing, I boot into Windows 7 and there's my 15s.
Today I'm scared my HDD is failing with my 40s boot time in Ubuntu but I boot into Windows 8 in 8-10 seconds flat.

This whole slow boot garbage seems to be a Linux only thing, and as much as I love Linux, the fact that I have a slow boot and can't do anything about it really annoys me.

---

### Post by ian-weisser on 2013-08-17
> **Sly14Cat said:**
> Today I'm scared my HDD is failing with my 40s boot time in Ubuntu but I boot into Windows 8 in 8-10 seconds flat.

This whole slow boot garbage seems to be a Linux only thing, and as much as I love Linux, the fact that I have a slow boot and can't do anything about it really annoys me.

You discovered a bug in ureadahead. Open a bug report. That's how "garbage" gets fixed.
My earlier post includes a link showing you how to gather bug information the developer needs.

Everyone is frustrated when they discover a problem. We report them. They get fixed.

---

### Post by Sly14Cat on 2013-08-17
Sorry about my rant, I just never thought I'd stumble upon a bug and all this time I've just borked my system beyond repair.

I'll be filing a bug report soon and ill but hang out on debian or something until they can work this out.

Thanks,
Sly

---

