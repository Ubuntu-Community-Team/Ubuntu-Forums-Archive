---
title: "Ubuntu stucks at shutdown-screen"
date: 2013-06-29
forum: General Help
---

### Post by LinuxWillWin on 2013-06-29
Hi Ubuntu fans,

I have just installed e4rat (a program to make your boot time faster) and setted it up. Now the boot time is much faster, but when I want to shutdown or reboot my machine stucks at the shutdown-screen. When I press ESC the last message on the screen is:
```
spamassasin mail filter daemon: disabled: see /etc/default/spamassasin 
```

...here is the output of /var/log/kern.log:
```
Jun 30 15:56:59 my-pc kernel: imklog 5.8.11, log source = /proc/kmsg started.Jun 30 15:56:59 my-pc kernel: [    0.000000] Initializing cgroup subsys cpuset
Jun 30 15:56:59 my-pc kernel: [    0.000000] Initializing cgroup subsys cpu
Jun 30 15:56:59 my-pc kernel: [    0.000000] Linux version 3.8.0-26-generic (buildd@panlong) (gcc version 4.7.3 (Ubuntu/Linaro 4.7.3-1ubuntu1) ) #38-Ubuntu SMP Mon Jun 17 21:43:33 UTC 2013 (Ubuntu 3.8.0-26.38-generic 3.8.13.2)
Jun 30 15:56:59 my-pc kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-26-generic root=UUID=17e528d4-9821-4ba1-9d59-b684a2125f43 ro init=/sbin/e4rat-preload quiet splash vt.handoff=7
Jun 30 15:56:59 my-pc kernel: [    0.000000] KERNEL supported cpus:
Jun 30 15:56:59 my-pc kernel: [    0.000000]   Intel GenuineIntel
Jun 30 15:56:59 my-pc kernel: [    0.000000]   AMD AuthenticAMD
Jun 30 15:56:59 my-pc kernel: [    0.000000]   Centaur CentaurHauls
Jun 30 15:56:59 my-pc kernel: [    0.000000] e820: BIOS-provided physical RAM map:
Jun 30 15:56:59 my-pc kernel: [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009f7ff] usable
Jun 30 15:56:59 my-pc kernel: [    0.000000] BIOS-e820: [mem 0x000000000009f800-0x000000000009ffff] reserved
Jun 30 15:56:59 my-pc kernel: [    0.000000] BIOS-e820: [mem 0x00000000000f0000-0x00000000000fffff] reserved
Jun 30 15:56:59 my-pc kernel: [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000cfdeffff] usable
Jun 30 15:56:59 my-pc kernel: [    0.000000] BIOS-e820: [mem 0x00000000cfdf0000-0x00000000cfdf2fff] ACPI NVS
Jun 30 15:56:59 my-pc kernel: [    0.000000] BIOS-e820: [mem 0x00000000cfdf3000-0x00000000cfdfffff] ACPI data
Jun 30 15:56:59 my-pc kernel: [    0.000000] BIOS-e820: [mem 0x00000000cfe00000-0x00000000cfefffff] reserved
Jun 30 15:56:59 my-pc kernel: [    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
Jun 30 15:56:59 my-pc kernel: [    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000ffffffff] reserved
Jun 30 15:56:59 my-pc kernel: [    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000010fffffff] usable
Jun 30 15:56:59 my-pc kernel: [    0.000000] NX (Execute Disable) protection: active
Jun 30 15:56:59 my-pc kernel: [    0.000000] SMBIOS 2.4 present.
Jun 30 15:56:59 my-pc kernel: [    0.000000] DMI: Gigabyte Technology Co., Ltd. GA-78LMT-USB3/GA-78LMT-USB3, BIOS F4 10/19/2012
Jun 30 15:56:59 my-pc kernel: [    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
Jun 30 15:56:59 my-pc kernel: [    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
Jun 30 15:56:59 my-pc kernel: [    0.000000] No AGP bridge found
Jun 30 15:56:59 my-pc kernel: [    0.000000] e820: last_pfn = 0x110000 max_arch_pfn = 0x400000000
Jun 30 15:56:59 my-pc kernel: [    0.000000] MTRR default type: uncachable
Jun 30 15:56:59 my-pc kernel: [    0.000000] MTRR fixed ranges enabled:
Jun 30 15:56:59 my-pc kernel: [    0.000000]   00000-9FFFF write-back
Jun 30 15:56:59 my-pc kernel: [    0.000000]   A0000-BFFFF uncachable
Jun 30 15:56:59 my-pc kernel: [    0.000000]   C0000-C7FFF write-protect
Jun 30 15:56:59 my-pc kernel: [    0.000000]   C8000-FFFFF uncachable
Jun 30 15:56:59 my-pc kernel: [    0.000000] MTRR variable ranges enabled:
Jun 30 15:56:59 my-pc kernel: [    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
Jun 30 15:56:59 my-pc kernel: [    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
Jun 30 15:56:59 my-pc kernel: [    0.000000]   2 base 0000C0000000 mask FFFFF0000000 write-back
Jun 30 15:56:59 my-pc kernel: [    0.000000]   3 base 0000CFE00000 mask FFFFFFE00000 uncachable
Jun 30 15:56:59 my-pc kernel: [    0.000000]   4 disabled
Jun 30 15:56:59 my-pc kernel: [    0.000000]   5 disabled
Jun 30 15:56:59 my-pc kernel: [    0.000000]   6 disabled
Jun 30 15:56:59 my-pc kernel: [    0.000000]   7 disabled
Jun 30 15:56:59 my-pc kernel: [    0.000000] TOM2: 0000000130000000 aka 4864M
Jun 30 15:56:59 my-pc kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Jun 30 15:56:59 my-pc kernel: [    0.000000] original variable MTRRs
Jun 30 15:56:59 my-pc kernel: [    0.000000] reg 0, base: 0GB, range: 2GB, type WB
Jun 30 15:56:59 my-pc kernel: [    0.000000] reg 1, base: 2GB, range: 1GB, type WB
Jun 30 15:56:59 my-pc kernel: [    0.000000] reg 2, base: 3GB, range: 256MB, type WB
Jun 30 15:56:59 my-pc kernel: [    0.000000] reg 3, base: 3326MB, range: 2MB, type UC
Jun 30 15:56:59 my-pc kernel: [    0.000000] total RAM covered: 3326M
Jun 30 15:56:59 my-pc kernel: [    0.000000] Found optimal setting for mtrr clean up
Jun 30 15:56:59 my-pc kernel: [    0.000000]  gran_size: 64K     chunk_size: 4M     num_reg: 4      lose cover RAM: 0G
Jun 30 15:56:59 my-pc kernel: [    0.000000] New variable MTRRs
Jun 30 15:56:59 my-pc kernel: [    0.000000] reg 0, base: 0GB, range: 2GB, type WB
Jun 30 15:56:59 my-pc kernel: [    0.000000] reg 1, base: 2GB, range: 1GB, type WB
Jun 30 15:56:59 my-pc kernel: [    0.000000] reg 2, base: 3GB, range: 256MB, type WB
Jun 30 15:56:59 my-pc kernel: [    0.000000] reg 3, base: 3326MB, range: 2MB, type UC
Jun 30 15:56:59 my-pc kernel: [    0.000000] e820: update [mem 0xcfe00000-0xffffffff] usable ==> reserved
Jun 30 15:56:59 my-pc kernel: [    0.000000] e820: last_pfn = 0xcfdf0 max_arch_pfn = 0x400000000
Jun 30 15:56:59 my-pc kernel: [    0.000000] found SMP MP-table at [mem 0x000f5e40-0x000f5e4f] mapped at [ffff8800000f5e40]
Jun 30 15:56:59 my-pc kernel: [    0.000000] initial memory mapped: [mem 0x00000000-0x1fffffff]
Jun 30 15:56:59 my-pc kernel: [    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 24576
Jun 30 15:56:59 my-pc kernel: [    0.000000] Using GB pages for direct mapping
Jun 30 15:56:59 my-pc kernel: [    0.000000] init_memory_mapping: [mem 0x00000000-0xcfdeffff]
Jun 30 15:56:59 my-pc kernel: [    0.000000]  [mem 0x00000000-0xbfffffff] page 1G
Jun 30 15:56:59 my-pc kernel: [    0.000000]  [mem 0xc0000000-0xcfbfffff] page 2M
Jun 30 15:56:59 my-pc kernel: [    0.000000]  [mem 0xcfc00000-0xcfdeffff] page 4k
Jun 30 15:56:59 my-pc kernel: [    0.000000] kernel direct mapping tables up to 0xcfdeffff @ [mem 0x1fffd000-0x1fffffff]
Jun 30 15:56:59 my-pc kernel: [    0.000000] init_memory_mapping: [mem 0x100000000-0x10fffffff]
Jun 30 15:56:59 my-pc kernel: [    0.000000]  [mem 0x100000000-0x10fffffff] page 2M
Jun 30 15:56:59 my-pc kernel: [    0.000000] kernel direct mapping tables up to 0x10fffffff @ [mem 0xcfdee000-0xcfdeffff]
Jun 30 15:56:59 my-pc kernel: [    0.000000] RAMDISK: [mem 0x3433c000-0x36195fff]
Jun 30 15:56:59 my-pc kernel: [    0.000000] ACPI: RSDP 00000000000f7870 00014 (v00 GBT   )
Jun 30 15:56:59 my-pc kernel: [    0.000000] ACPI: RSDT 00000000cfdf3000 0003C (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Jun 30 15:56:59 my-pc kernel: [    0.000000] ACPI: FACP 00000000cfdf3080 00074 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Jun 30 15:56:59 my-pc kernel: [    0.000000] ACPI: DSDT 00000000cfdf3100 0683B (v01 GBT    GBTUACPI 00001000 MSFT 03000000)
Jun 30 15:56:59 my-pc kernel: [    0.000000] ACPI: FACS 00000000cfdf0000 00040
Jun 30 15:56:59 my-pc kernel: [    0.000000] ACPI: MSDM 00000000cfdf9a00 00055 (v03 GBT    GBTUACPI 42302E31 GBTU 01010101)
Jun 30 15:56:59 my-pc kernel: [    0.000000] ACPI: HPET 00000000cfdf9a80 00038 (v01 GBT    GBTUACPI 42302E31 GBTU 00000098)
Jun 30 15:56:59 my-pc kernel: [    0.000000] ACPI: MCFG 00000000cfdf9ac0 0003C (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Jun 30 15:56:59 my-pc kernel: [    0.000000] ACPI: TAMG 00000000cfdf9b00 00022 (v01 GBT    GBT   B0 5455312E BG?? 00000101)
Jun 30 15:56:59 my-pc kernel: [    0.000000] ACPI: APIC 00000000cfdf9940 000BC (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Jun 30 15:56:59 my-pc kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jun 30 15:56:59 my-pc kernel: [    0.000000] No NUMA configuration found
Jun 30 15:56:59 my-pc kernel: [    0.000000] Faking a node at [mem 0x0000000000000000-0x000000010fffffff]
Jun 30 15:56:59 my-pc kernel: [    0.000000] Initmem setup node 0 [mem 0x00000000-0x10fffffff]
Jun 30 15:56:59 my-pc kernel: [    0.000000]   NODE_DATA [mem 0x10fffb000-0x10fffffff]
Jun 30 15:56:59 my-pc kernel: [    0.000000]  [ffffea0000000000-ffffea00043fffff] PMD -> [ffff88010be00000-ffff88010f5fffff] on node 0
Jun 30 15:56:59 my-pc kernel: [    0.000000] Zone ranges:
Jun 30 15:56:59 my-pc kernel: [    0.000000]   DMA      [mem 0x00010000-0x00ffffff]
Jun 30 15:56:59 my-pc kernel: [    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
Jun 30 15:56:59 my-pc kernel: [    0.000000]   Normal   [mem 0x100000000-0x10fffffff]
Jun 30 15:56:59 my-pc kernel: [    0.000000] Movable zone start for each node
Jun 30 15:56:59 my-pc kernel: [    0.000000] Early memory node ranges
Jun 30 15:56:59 my-pc kernel: [    0.000000]   node   0: [mem 0x00010000-0x0009efff]
Jun 30 15:56:59 my-pc kernel: [    0.000000]   node   0: [mem 0x00100000-0xcfdeffff]
Jun 30 15:56:59 my-pc kernel: [    0.000000]   node   0: [mem 0x100000000-0x10fffffff]
Jun 30 15:56:59 my-pc kernel: [    0.000000] On node 0 totalpages: 916863
Jun 30 15:56:59 my-pc kernel: [    0.000000]   DMA zone: 64 pages used for memmap
Jun 30 15:56:59 my-pc kernel: [    0.000000]   DMA zone: 6 pages reserved
Jun 30 15:56:59 my-pc kernel: [    0.000000]   DMA zone: 3913 pages, LIFO batch:0
Jun 30 15:56:59 my-pc kernel: [    0.000000]   DMA32 zone: 13240 pages used for memmap
Jun 30 15:56:59 my-pc kernel: [    0.000000]   DMA32 zone: 834104 pages, LIFO batch:31
Jun 30 15:56:59 my-pc kernel: [    0.000000]   Normal zone: 1024 pages used for memmap
Jun 30 15:56:59 my-pc kernel: [    0.000000]   Normal zone: 64512 pages, LIFO batch:15
Jun 30 15:56:59 my-pc kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x4008
Jun 30 15:56:59 my-pc kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jun 30 15:56:59 my-pc kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jun 30 15:56:59 my-pc kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Jun 30 15:56:59 my-pc kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
Jun 30 15:56:59 my-pc kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] enabled)
Jun 30 15:56:59 my-pc kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x04] enabled)
Jun 30 15:56:59 my-pc kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x05] enabled)
Jun 30 15:56:59 my-pc kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x06] disabled)
Jun 30 15:56:59 my-pc kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x07] disabled)
Jun 30 15:56:59 my-pc kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
Jun 30 15:56:59 my-pc kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
Jun 30 15:56:59 my-pc kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
Jun 30 15:56:59 my-pc kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
Jun 30 15:56:59 my-pc kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] dfl dfl lint[0x1])
Jun 30 15:56:59 my-pc kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x05] dfl dfl lint[0x1])
Jun 30 15:56:59 my-pc kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x06] dfl dfl lint[0x1])
Jun 30 15:56:59 my-pc kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x07] dfl dfl lint[0x1])
Jun 30 15:56:59 my-pc kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Jun 30 15:56:59 my-pc kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
Jun 30 15:56:59 my-pc kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jun 30 15:56:59 my-pc kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Jun 30 15:56:59 my-pc kernel: [    0.000000] ACPI: IRQ0 used by override.
Jun 30 15:56:59 my-pc kernel: [    0.000000] ACPI: IRQ2 used by override.
Jun 30 15:56:59 my-pc kernel: [    0.000000] ACPI: IRQ9 used by override.
Jun 30 15:56:59 my-pc kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jun 30 15:56:59 my-pc kernel: [    0.000000] ACPI: HPET id: 0x10b9a201 base: 0xfed00000
Jun 30 15:56:59 my-pc kernel: [    0.000000] smpboot: Allowing 8 CPUs, 2 hotplug CPUs
Jun 30 15:56:59 my-pc kernel: [    0.000000] nr_irqs_gsi: 40
Jun 30 15:56:59 my-pc kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jun 30 15:56:59 my-pc kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Jun 30 15:56:59 my-pc kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Jun 30 15:56:59 my-pc kernel: [    0.000000] PM: Registered nosave memory: 00000000cfdf0000 - 00000000cfdf3000
Jun 30 15:56:59 my-pc kernel: [    0.000000] PM: Registered nosave memory: 00000000cfdf3000 - 00000000cfe00000
Jun 30 15:56:59 my-pc kernel: [    0.000000] PM: Registered nosave memory: 00000000cfe00000 - 00000000cff00000
Jun 30 15:56:59 my-pc kernel: [    0.000000] PM: Registered nosave memory: 00000000cff00000 - 00000000e0000000
Jun 30 15:56:59 my-pc kernel: [    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
Jun 30 15:56:59 my-pc kernel: [    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000fec00000
Jun 30 15:56:59 my-pc kernel: [    0.000000] PM: Registered nosave memory: 00000000fec00000 - 0000000100000000
Jun 30 15:56:59 my-pc kernel: [    0.000000] e820: [mem 0xcff00000-0xdfffffff] available for PCI devices
Jun 30 15:56:59 my-pc kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Jun 30 15:56:59 my-pc kernel: [    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
Jun 30 15:56:59 my-pc kernel: [    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88010fc00000 s85056 r8192 d21440 u262144
Jun 30 15:56:59 my-pc kernel: [    0.000000] pcpu-alloc: s85056 r8192 d21440 u262144 alloc=1*2097152
Jun 30 15:56:59 my-pc kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
Jun 30 15:56:59 my-pc kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 902529
Jun 30 15:56:59 my-pc kernel: [    0.000000] Policy zone: Normal
Jun 30 15:56:59 my-pc kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-26-generic root=UUID=17e528d4-9821-4ba1-9d59-b684a2125f43 ro init=/sbin/e4rat-preload quiet splash vt.handoff=7
Jun 30 15:56:59 my-pc kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Jun 30 15:56:59 my-pc kernel: [    0.000000] __ex_table already sorted, skipping sort
Jun 30 15:56:59 my-pc kernel: [    0.000000] xsave: enabled xstate_bv 0x7, cntxt size 0x340
Jun 30 15:56:59 my-pc kernel: [    0.000000] Checking aperture...
Jun 30 15:56:59 my-pc kernel: [    0.000000] No AGP bridge found
Jun 30 15:56:59 my-pc kernel: [    0.000000] Node 0: aperture @ bdf2000000 size 32 MB
Jun 30 15:56:59 my-pc kernel: [    0.000000] Aperture beyond 4GB. Ignoring.
Jun 30 15:56:59 my-pc kernel: [    0.000000] Your BIOS doesn't leave a aperture memory hole
Jun 30 15:56:59 my-pc kernel: [    0.000000] Please enable the IOMMU option in the BIOS setup
Jun 30 15:56:59 my-pc kernel: [    0.000000] This costs you 64 MB of RAM
Jun 30 15:56:59 my-pc kernel: [    0.000000] Mapping aperture over 65536 KB of RAM @ c4000000
Jun 30 15:56:59 my-pc kernel: [    0.000000] PM: Registered nosave memory: 00000000c4000000 - 00000000c8000000
Jun 30 15:56:59 my-pc kernel: [    0.000000] Memory: 3430720k/4456448k available (7010k kernel code, 788996k absent, 236732k reserved, 6232k data, 996k init)
Jun 30 15:56:59 my-pc kernel: [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
Jun 30 15:56:59 my-pc kernel: [    0.000000] Hierarchical RCU implementation.
Jun 30 15:56:59 my-pc kernel: [    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
Jun 30 15:56:59 my-pc kernel: [    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
Jun 30 15:56:59 my-pc kernel: [    0.000000] NR_IRQS:16640 nr_irqs:744 16
Jun 30 15:56:59 my-pc kernel: [    0.000000] spurious 8259A interrupt: IRQ7.
Jun 30 15:56:59 my-pc kernel: [    0.000000] Console: colour dummy device 80x25
Jun 30 15:56:59 my-pc kernel: [    0.000000] console [tty0] enabled
Jun 30 15:56:59 my-pc kernel: [    0.000000] allocated 14680064 bytes of page_cgroup
Jun 30 15:56:59 my-pc kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Jun 30 15:56:59 my-pc kernel: [    0.000000] hpet clockevent registered
Jun 30 15:56:59 my-pc kernel: [    0.004000] tsc: Fast TSC calibration using PIT
Jun 30 15:56:59 my-pc kernel: [    0.008000] tsc: Detected 3515.189 MHz processor
Jun 30 15:56:59 my-pc kernel: [    0.000003] Calibrating delay loop (skipped), value calculated using timer frequency.. 7030.37 BogoMIPS (lpj=14060756)
Jun 30 15:56:59 my-pc kernel: [    0.000006] pid_max: default: 32768 minimum: 301
Jun 30 15:56:59 my-pc kernel: [    0.000029] Security Framework initialized
Jun 30 15:56:59 my-pc kernel: [    0.000041] AppArmor: AppArmor initialized
Jun 30 15:56:59 my-pc kernel: [    0.000041] Yama: becoming mindful.
Jun 30 15:56:59 my-pc kernel: [    0.000303] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
Jun 30 15:56:59 my-pc kernel: [    0.001633] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
Jun 30 15:56:59 my-pc kernel: [    0.002261] Mount-cache hash table entries: 256
Jun 30 15:56:59 my-pc kernel: [    0.002417] Initializing cgroup subsys cpuacct
Jun 30 15:56:59 my-pc kernel: [    0.002419] Initializing cgroup subsys memory
Jun 30 15:56:59 my-pc kernel: [    0.002427] Initializing cgroup subsys devices
Jun 30 15:56:59 my-pc kernel: [    0.002428] Initializing cgroup subsys freezer
Jun 30 15:56:59 my-pc kernel: [    0.002429] Initializing cgroup subsys blkio
Jun 30 15:56:59 my-pc kernel: [    0.002430] Initializing cgroup subsys perf_event
Jun 30 15:56:59 my-pc kernel: [    0.002432] Initializing cgroup subsys hugetlb
Jun 30 15:56:59 my-pc kernel: [    0.002453] tseg: 00cff00000
Jun 30 15:56:59 my-pc kernel: [    0.002455] CPU: Physical Processor ID: 0
Jun 30 15:56:59 my-pc kernel: [    0.002456] CPU: Processor Core ID: 0
Jun 30 15:56:59 my-pc kernel: [    0.002457] mce: CPU supports 7 MCE banks
Jun 30 15:56:59 my-pc kernel: [    0.002463] LVT offset 1 assigned for vector 0xf9
Jun 30 15:56:59 my-pc kernel: [    0.002469] Last level iTLB entries: 4KB 512, 2MB 1024, 4MB 512
Jun 30 15:56:59 my-pc kernel: [    0.002469] Last level dTLB entries: 4KB 1024, 2MB 1024, 4MB 512
Jun 30 15:56:59 my-pc kernel: [    0.002469] tlb_flushall_shift: 5
Jun 30 15:56:59 my-pc kernel: [    0.002559] Freeing SMP alternatives: 24k freed
Jun 30 15:56:59 my-pc kernel: [    0.003932] ACPI: Core revision 20121018
Jun 30 15:56:59 my-pc kernel: [    0.068307] ftrace: allocating 26697 entries in 105 pages
Jun 30 15:56:59 my-pc kernel: [    0.076672] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Jun 30 15:56:59 my-pc kernel: [    0.116316] smpboot: CPU0: AMD FX(tm)-6300 Six-Core Processor (fam: 15, model: 02, stepping: 00)
Jun 30 15:56:59 my-pc kernel: [    0.222727] Performance Events: 
Jun 30 15:56:59 my-pc kernel: [    0.222728] perf: AMD core performance counters detected
Jun 30 15:56:59 my-pc kernel: [    0.222730] AMD PMU driver.
Jun 30 15:56:59 my-pc kernel: [    0.222732] ... version:                0
Jun 30 15:56:59 my-pc kernel: [    0.222733] ... bit width:              48
Jun 30 15:56:59 my-pc kernel: [    0.222734] ... generic registers:      6
Jun 30 15:56:59 my-pc kernel: [    0.222734] ... value mask:             0000ffffffffffff
Jun 30 15:56:59 my-pc kernel: [    0.222735] ... max period:             00007fffffffffff
Jun 30 15:56:59 my-pc kernel: [    0.222736] ... fixed-purpose events:   0
Jun 30 15:56:59 my-pc kernel: [    0.222737] ... event mask:             000000000000003f
Jun 30 15:56:59 my-pc kernel: [    0.223613] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
Jun 30 15:56:59 my-pc kernel: [    0.223675] smpboot: Booting Node   0, Processors  #1 #2 #3 #4 #5
Jun 30 15:56:59 my-pc kernel: [    0.289517] Brought up 6 CPUs
Jun 30 15:56:59 my-pc kernel: [    0.289520] smpboot: Total of 6 processors activated (42182.26 BogoMIPS)
Jun 30 15:56:59 my-pc kernel: [    0.297363] devtmpfs: initialized
Jun 30 15:56:59 my-pc kernel: [    0.298381] EVM: security.selinux
Jun 30 15:56:59 my-pc kernel: [    0.298382] EVM: security.SMACK64
Jun 30 15:56:59 my-pc kernel: [    0.298384] EVM: security.capability
Jun 30 15:56:59 my-pc kernel: [    0.298447] PM: Registering ACPI NVS region [mem 0xcfdf0000-0xcfdf2fff] (12288 bytes)
Jun 30 15:56:59 my-pc kernel: [    0.299112] regulator-dummy: no parameters
Jun 30 15:56:59 my-pc kernel: [    0.299154] NET: Registered protocol family 16
Jun 30 15:56:59 my-pc kernel: [    0.299343] ACPI: bus type pci registered
Jun 30 15:56:59 my-pc kernel: [    0.299387] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Jun 30 15:56:59 my-pc kernel: [    0.299390] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
Jun 30 15:56:59 my-pc kernel: [    0.311809] PCI: Using configuration type 1 for base access
Jun 30 15:56:59 my-pc kernel: [    0.312786] bio: create slab <bio-0> at 0
Jun 30 15:56:59 my-pc kernel: [    0.312874] ACPI: Added _OSI(Module Device)
Jun 30 15:56:59 my-pc kernel: [    0.312878] ACPI: Added _OSI(Processor Device)
Jun 30 15:56:59 my-pc kernel: [    0.312879] ACPI: Added _OSI(3.0 _SCP Extensions)
Jun 30 15:56:59 my-pc kernel: [    0.312880] ACPI: Added _OSI(Processor Aggregator Device)
Jun 30 15:56:59 my-pc kernel: [    0.313742] ACPI: EC: Look up EC in DSDT
Jun 30 15:56:59 my-pc kernel: [    0.320344] ACPI: Interpreter enabled
Jun 30 15:56:59 my-pc kernel: [    0.320349] ACPI: (supports S0 S3 S4 S5)
Jun 30 15:56:59 my-pc kernel: [    0.320369] ACPI: Using IOAPIC for interrupt routing
Jun 30 15:56:59 my-pc kernel: [    0.334795] ACPI: No dock devices found.
Jun 30 15:56:59 my-pc kernel: [    0.334799] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Jun 30 15:56:59 my-pc kernel: [    0.334860] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Jun 30 15:56:59 my-pc kernel: [    0.334862] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Jun 30 15:56:59 my-pc kernel: [    0.335160] PCI host bridge to bus 0000:00
Jun 30 15:56:59 my-pc kernel: [    0.335163] pci_bus 0000:00: root bus resource [bus 00-ff]
Jun 30 15:56:59 my-pc kernel: [    0.335165] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
Jun 30 15:56:59 my-pc kernel: [    0.335167] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
Jun 30 15:56:59 my-pc kernel: [    0.335169] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
Jun 30 15:56:59 my-pc kernel: [    0.335170] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000dffff]
Jun 30 15:56:59 my-pc kernel: [    0.335172] pci_bus 0000:00: root bus resource [mem 0xd0000000-0xfebfffff]
Jun 30 15:56:59 my-pc kernel: [    0.335183] pci 0000:00:00.0: [1022:9600] type 00 class 0x060000
Jun 30 15:56:59 my-pc kernel: [    0.335194] pci 0000:00:00.0: reg 1c: [mem 0xe0000000-0xffffffff 64bit]
Jun 30 15:56:59 my-pc kernel: [    0.335235] pci 0000:00:01.0: [1022:9602] type 01 class 0x060400
Jun 30 15:56:59 my-pc kernel: [    0.335272] pci 0000:00:04.0: [1022:9604] type 01 class 0x060400
Jun 30 15:56:59 my-pc kernel: [    0.335306] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
Jun 30 15:56:59 my-pc kernel: [    0.335320] pci 0000:00:06.0: [1022:9606] type 01 class 0x060400
Jun 30 15:56:59 my-pc kernel: [    0.335353] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
Jun 30 15:56:59 my-pc kernel: [    0.335366] pci 0000:00:07.0: [1022:9607] type 01 class 0x060400
Jun 30 15:56:59 my-pc kernel: [    0.335399] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
Jun 30 15:56:59 my-pc kernel: [    0.335429] pci 0000:00:11.0: [1002:4390] type 00 class 0x01018f
Jun 30 15:56:59 my-pc kernel: [    0.335448] pci 0000:00:11.0: reg 10: [io  0xff00-0xff07]
Jun 30 15:56:59 my-pc kernel: [    0.335457] pci 0000:00:11.0: reg 14: [io  0xfe00-0xfe03]
Jun 30 15:56:59 my-pc kernel: [    0.335466] pci 0000:00:11.0: reg 18: [io  0xfd00-0xfd07]
Jun 30 15:56:59 my-pc kernel: [    0.335475] pci 0000:00:11.0: reg 1c: [io  0xfc00-0xfc03]
Jun 30 15:56:59 my-pc kernel: [    0.335483] pci 0000:00:11.0: reg 20: [io  0xfb00-0xfb0f]
Jun 30 15:56:59 my-pc kernel: [    0.335493] pci 0000:00:11.0: reg 24: [mem 0xfe02f000-0xfe02f3ff]
Jun 30 15:56:59 my-pc kernel: [    0.335512] pci 0000:00:11.0: set SATA to AHCI mode
Jun 30 15:56:59 my-pc kernel: [    0.335558] pci 0000:00:12.0: [1002:4397] type 00 class 0x0c0310
Jun 30 15:56:59 my-pc kernel: [    0.335571] pci 0000:00:12.0: reg 10: [mem 0xfe02e000-0xfe02efff]
Jun 30 15:56:59 my-pc kernel: [    0.335634] pci 0000:00:12.1: [1002:4398] type 00 class 0x0c0310
Jun 30 15:56:59 my-pc kernel: [    0.335647] pci 0000:00:12.1: reg 10: [mem 0xfe02d000-0xfe02dfff]
Jun 30 15:56:59 my-pc kernel: [    0.335717] pci 0000:00:12.2: [1002:4396] type 00 class 0x0c0320
Jun 30 15:56:59 my-pc kernel: [    0.335735] pci 0000:00:12.2: reg 10: [mem 0xfe02c000-0xfe02c0ff]
Jun 30 15:56:59 my-pc kernel: [    0.335816] pci 0000:00:12.2: supports D1 D2
Jun 30 15:56:59 my-pc kernel: [    0.335818] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
Jun 30 15:56:59 my-pc kernel: [    0.335840] pci 0000:00:13.0: [1002:4397] type 00 class 0x0c0310
Jun 30 15:56:59 my-pc kernel: [    0.335853] pci 0000:00:13.0: reg 10: [mem 0xfe02b000-0xfe02bfff]
Jun 30 15:56:59 my-pc kernel: [    0.335916] pci 0000:00:13.1: [1002:4398] type 00 class 0x0c0310
Jun 30 15:56:59 my-pc kernel: [    0.335929] pci 0000:00:13.1: reg 10: [mem 0xfe02a000-0xfe02afff]
Jun 30 15:56:59 my-pc kernel: [    0.335997] pci 0000:00:13.2: [1002:4396] type 00 class 0x0c0320
Jun 30 15:56:59 my-pc kernel: [    0.336015] pci 0000:00:13.2: reg 10: [mem 0xfe029000-0xfe0290ff]
Jun 30 15:56:59 my-pc kernel: [    0.336096] pci 0000:00:13.2: supports D1 D2
Jun 30 15:56:59 my-pc kernel: [    0.336098] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
Jun 30 15:56:59 my-pc kernel: [    0.336123] pci 0000:00:14.0: [1002:4385] type 00 class 0x0c0500
Jun 30 15:56:59 my-pc kernel: [    0.336221] pci 0000:00:14.1: [1002:439c] type 00 class 0x01018a
Jun 30 15:56:59 my-pc kernel: [    0.336237] pci 0000:00:14.1: reg 10: [io  0x0000-0x0007]
Jun 30 15:56:59 my-pc kernel: [    0.336245] pci 0000:00:14.1: reg 14: [io  0x0000-0x0003]
Jun 30 15:56:59 my-pc kernel: [    0.336254] pci 0000:00:14.1: reg 18: [io  0x0000-0x0007]
Jun 30 15:56:59 my-pc kernel: [    0.336263] pci 0000:00:14.1: reg 1c: [io  0x0000-0x0003]
Jun 30 15:56:59 my-pc kernel: [    0.336272] pci 0000:00:14.1: reg 20: [io  0xfa00-0xfa0f]
Jun 30 15:56:59 my-pc kernel: [    0.336329] pci 0000:00:14.2: [1002:4383] type 00 class 0x040300
Jun 30 15:56:59 my-pc kernel: [    0.336349] pci 0000:00:14.2: reg 10: [mem 0xfe024000-0xfe027fff 64bit]
Jun 30 15:56:59 my-pc kernel: [    0.336418] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
Jun 30 15:56:59 my-pc kernel: [    0.336432] pci 0000:00:14.3: [1002:439d] type 00 class 0x060100
Jun 30 15:56:59 my-pc kernel: [    0.336507] pci 0000:00:14.4: [1002:4384] type 01 class 0x060401
Jun 30 15:56:59 my-pc kernel: [    0.336548] pci 0000:00:14.5: [1002:4399] type 00 class 0x0c0310
Jun 30 15:56:59 my-pc kernel: [    0.336561] pci 0000:00:14.5: reg 10: [mem 0xfe028000-0xfe028fff]
Jun 30 15:56:59 my-pc kernel: [    0.336628] pci 0000:00:18.0: [1022:1600] type 00 class 0x060000
Jun 30 15:56:59 my-pc kernel: [    0.336646] pci 0000:00:18.1: [1022:1601] type 00 class 0x060000
Jun 30 15:56:59 my-pc kernel: [    0.336661] pci 0000:00:18.2: [1022:1602] type 00 class 0x060000
Jun 30 15:56:59 my-pc kernel: [    0.336675] pci 0000:00:18.3: [1022:1603] type 00 class 0x060000
Jun 30 15:56:59 my-pc kernel: [    0.336693] pci 0000:00:18.4: [1022:1604] type 00 class 0x060000
Jun 30 15:56:59 my-pc kernel: [    0.336707] pci 0000:00:18.5: [1022:1605] type 00 class 0x060000
Jun 30 15:56:59 my-pc kernel: [    0.336753] pci 0000:01:05.0: [1002:9616] type 00 class 0x030000
Jun 30 15:56:59 my-pc kernel: [    0.336761] pci 0000:01:05.0: reg 10: [mem 0xd0000000-0xdfffffff pref]
Jun 30 15:56:59 my-pc kernel: [    0.336766] pci 0000:01:05.0: reg 14: [io  0xce00-0xceff]
Jun 30 15:56:59 my-pc kernel: [    0.336770] pci 0000:01:05.0: reg 18: [mem 0xfdae0000-0xfdaeffff]
Jun 30 15:56:59 my-pc kernel: [    0.336780] pci 0000:01:05.0: reg 24: [mem 0xfd900000-0xfd9fffff]
Jun 30 15:56:59 my-pc kernel: [    0.336798] pci 0000:01:05.0: supports D1 D2
Jun 30 15:56:59 my-pc kernel: [    0.336807] pci 0000:01:05.1: [1002:960f] type 00 class 0x040300
Jun 30 15:56:59 my-pc kernel: [    0.336815] pci 0000:01:05.1: reg 10: [mem 0xfdafc000-0xfdafffff]
Jun 30 15:56:59 my-pc kernel: [    0.336847] pci 0000:01:05.1: supports D1 D2
Jun 30 15:56:59 my-pc kernel: [    0.336884] pci 0000:00:01.0: PCI bridge to [bus 01]
Jun 30 15:56:59 my-pc kernel: [    0.336887] pci 0000:00:01.0:   bridge window [io  0xc000-0xcfff]
Jun 30 15:56:59 my-pc kernel: [    0.336889] pci 0000:00:01.0:   bridge window [mem 0xfd900000-0xfdafffff]
Jun 30 15:56:59 my-pc kernel: [    0.336892] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
Jun 30 15:56:59 my-pc kernel: [    0.336926] pci 0000:02:00.0: [1b6f:7023] type 00 class 0x0c0330
Jun 30 15:56:59 my-pc kernel: [    0.336941] pci 0000:02:00.0: reg 10: [mem 0xfd6f8000-0xfd6fffff 64bit]
Jun 30 15:56:59 my-pc kernel: [    0.337008] pci 0000:02:00.0: supports D1 D2
Jun 30 15:56:59 my-pc kernel: [    0.337010] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Jun 30 15:56:59 my-pc kernel: [    0.345712] pci 0000:00:04.0: PCI bridge to [bus 02]
Jun 30 15:56:59 my-pc kernel: [    0.345716] pci 0000:00:04.0:   bridge window [io  0xb000-0xbfff]
Jun 30 15:56:59 my-pc kernel: [    0.345718] pci 0000:00:04.0:   bridge window [mem 0xfd600000-0xfd6fffff]
Jun 30 15:56:59 my-pc kernel: [    0.345721] pci 0000:00:04.0:   bridge window [mem 0xfdf00000-0xfdffffff 64bit pref]
Jun 30 15:56:59 my-pc kernel: [    0.345758] pci 0000:03:00.0: [10ec:8168] type 00 class 0x020000
Jun 30 15:56:59 my-pc kernel: [    0.345770] pci 0000:03:00.0: reg 10: [io  0xee00-0xeeff]
Jun 30 15:56:59 my-pc kernel: [    0.345790] pci 0000:03:00.0: reg 18: [mem 0xfddff000-0xfddfffff 64bit pref]
Jun 30 15:56:59 my-pc kernel: [    0.345803] pci 0000:03:00.0: reg 20: [mem 0xfddf8000-0xfddfbfff 64bit pref]
Jun 30 15:56:59 my-pc kernel: [    0.345858] pci 0000:03:00.0: supports D1 D2
Jun 30 15:56:59 my-pc kernel: [    0.345860] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Jun 30 15:56:59 my-pc kernel: [    0.353703] pci 0000:00:06.0: PCI bridge to [bus 03]
Jun 30 15:56:59 my-pc kernel: [    0.353706] pci 0000:00:06.0:   bridge window [io  0xe000-0xefff]
Jun 30 15:56:59 my-pc kernel: [    0.353709] pci 0000:00:06.0:   bridge window [mem 0xfde00000-0xfdefffff]
Jun 30 15:56:59 my-pc kernel: [    0.353712] pci 0000:00:06.0:   bridge window [mem 0xfdd00000-0xfddfffff 64bit pref]
Jun 30 15:56:59 my-pc kernel: [    0.353746] pci 0000:04:00.0: [1b6f:7023] type 00 class 0x0c0330
Jun 30 15:56:59 my-pc kernel: [    0.353761] pci 0000:04:00.0: reg 10: [mem 0xfdcf8000-0xfdcfffff 64bit]
Jun 30 15:56:59 my-pc kernel: [    0.353829] pci 0000:04:00.0: supports D1 D2
Jun 30 15:56:59 my-pc kernel: [    0.353831] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Jun 30 15:56:59 my-pc kernel: [    0.361694] pci 0000:00:07.0: PCI bridge to [bus 04]
Jun 30 15:56:59 my-pc kernel: [    0.361698] pci 0000:00:07.0:   bridge window [io  0xd000-0xdfff]
Jun 30 15:56:59 my-pc kernel: [    0.361700] pci 0000:00:07.0:   bridge window [mem 0xfdc00000-0xfdcfffff]
Jun 30 15:56:59 my-pc kernel: [    0.361703] pci 0000:00:07.0:   bridge window [mem 0xfdb00000-0xfdbfffff 64bit pref]
Jun 30 15:56:59 my-pc kernel: [    0.361763] pci 0000:00:14.4: PCI bridge to [bus 05] (subtractive decode)
Jun 30 15:56:59 my-pc kernel: [    0.361767] pci 0000:00:14.4:   bridge window [io  0xa000-0xafff]
Jun 30 15:56:59 my-pc kernel: [    0.361771] pci 0000:00:14.4:   bridge window [mem 0xfd800000-0xfd8fffff]
Jun 30 15:56:59 my-pc kernel: [    0.361774] pci 0000:00:14.4:   bridge window [mem 0xfd700000-0xfd7fffff pref]
Jun 30 15:56:59 my-pc kernel: [    0.361776] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
Jun 30 15:56:59 my-pc kernel: [    0.361778] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
Jun 30 15:56:59 my-pc kernel: [    0.361779] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
Jun 30 15:56:59 my-pc kernel: [    0.361781] pci 0000:00:14.4:   bridge window [mem 0x000c0000-0x000dffff] (subtractive decode)
Jun 30 15:56:59 my-pc kernel: [    0.361782] pci 0000:00:14.4:   bridge window [mem 0xd0000000-0xfebfffff] (subtractive decode)
Jun 30 15:56:59 my-pc kernel: [    0.361837] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
Jun 30 15:56:59 my-pc kernel: [    0.361878] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE4._PRT]
Jun 30 15:56:59 my-pc kernel: [    0.361909] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE6._PRT]
Jun 30 15:56:59 my-pc kernel: [    0.361938] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE7._PRT]
Jun 30 15:56:59 my-pc kernel: [    0.361973] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
Jun 30 15:56:59 my-pc kernel: [    0.362005]  pci0000:00: ACPI _OSC support notification failed, disabling PCIe ASPM
Jun 30 15:56:59 my-pc kernel: [    0.362007]  pci0000:00: Unable to request _OSC control (_OSC support mask: 0x08)
Jun 30 15:56:59 my-pc kernel: [    0.363077] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jun 30 15:56:59 my-pc kernel: [    0.363115] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jun 30 15:56:59 my-pc kernel: [    0.363152] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jun 30 15:56:59 my-pc kernel: [    0.363189] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jun 30 15:56:59 my-pc kernel: [    0.363225] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jun 30 15:56:59 my-pc kernel: [    0.363261] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jun 30 15:56:59 my-pc kernel: [    0.363296] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jun 30 15:56:59 my-pc kernel: [    0.363332] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jun 30 15:56:59 my-pc kernel: [    0.363422] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
Jun 30 15:56:59 my-pc kernel: [    0.363424] vgaarb: loaded
Jun 30 15:56:59 my-pc kernel: [    0.363425] vgaarb: bridge control possible 0000:01:05.0
Jun 30 15:56:59 my-pc kernel: [    0.363585] SCSI subsystem initialized
Jun 30 15:56:59 my-pc kernel: [    0.363587] ACPI: bus type scsi registered
Jun 30 15:56:59 my-pc kernel: [    0.363633] libata version 3.00 loaded.
Jun 30 15:56:59 my-pc kernel: [    0.363647] ACPI: bus type usb registered
Jun 30 15:56:59 my-pc kernel: [    0.363661] usbcore: registered new interface driver usbfs
Jun 30 15:56:59 my-pc kernel: [    0.363669] usbcore: registered new interface driver hub
Jun 30 15:56:59 my-pc kernel: [    0.363691] usbcore: registered new device driver usb
Jun 30 15:56:59 my-pc kernel: [    0.363771] PCI: Using ACPI for IRQ routing
Jun 30 15:56:59 my-pc kernel: [    0.372257] PCI: pci_cache_line_size set to 64 bytes
Jun 30 15:56:59 my-pc kernel: [    0.372264] pci 0000:00:00.0: no compatible bridge window for [mem 0xe0000000-0xffffffff 64bit]
Jun 30 15:56:59 my-pc kernel: [    0.372324] e820: reserve RAM buffer [mem 0x0009f800-0x0009ffff]
Jun 30 15:56:59 my-pc kernel: [    0.372326] e820: reserve RAM buffer [mem 0xcfdf0000-0xcfffffff]
Jun 30 15:56:59 my-pc kernel: [    0.372400] NetLabel: Initializing
Jun 30 15:56:59 my-pc kernel: [    0.372401] NetLabel:  domain hash size = 128
Jun 30 15:56:59 my-pc kernel: [    0.372402] NetLabel:  protocols = UNLABELED CIPSOv4
Jun 30 15:56:59 my-pc kernel: [    0.372410] NetLabel:  unlabeled traffic allowed by default
Jun 30 15:56:59 my-pc kernel: [    0.372465] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
Jun 30 15:56:59 my-pc kernel: [    0.372468] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
Jun 30 15:56:59 my-pc kernel: [    0.374493] Switching to clocksource hpet
Jun 30 15:56:59 my-pc kernel: [    0.379749] AppArmor: AppArmor Filesystem Enabled
Jun 30 15:56:59 my-pc kernel: [    0.379762] pnp: PnP ACPI init
Jun 30 15:56:59 my-pc kernel: [    0.379769] ACPI: bus type pnp registered
Jun 30 15:56:59 my-pc kernel: [    0.379829] system 00:00: [io  0x04d0-0x04d1] has been reserved
Jun 30 15:56:59 my-pc kernel: [    0.379832] system 00:00: [io  0x0220-0x0225] has been reserved
Jun 30 15:56:59 my-pc kernel: [    0.379834] system 00:00: [io  0x0290-0x0294] has been reserved
Jun 30 15:56:59 my-pc kernel: [    0.379836] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
Jun 30 15:56:59 my-pc kernel: [    0.380338] pnp 00:01: disabling [mem 0x00000000-0x00000fff window] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
Jun 30 15:56:59 my-pc kernel: [    0.380387] system 00:01: [io  0x4100-0x411f] has been reserved
Jun 30 15:56:59 my-pc kernel: [    0.380390] system 00:01: [io  0x0228-0x022f] has been reserved
Jun 30 15:56:59 my-pc kernel: [    0.380392] system 00:01: [io  0x040b] has been reserved
Jun 30 15:56:59 my-pc kernel: [    0.380393] system 00:01: [io  0x04d6] has been reserved
Jun 30 15:56:59 my-pc kernel: [    0.380395] system 00:01: [io  0x0c00-0x0c01] has been reserved
Jun 30 15:56:59 my-pc kernel: [    0.380397] system 00:01: [io  0x0c14] has been reserved
Jun 30 15:56:59 my-pc kernel: [    0.380399] system 00:01: [io  0x0c50-0x0c52] has been reserved
Jun 30 15:56:59 my-pc kernel: [    0.380401] system 00:01: [io  0x0c6c-0x0c6d] has been reserved
Jun 30 15:56:59 my-pc kernel: [    0.380402] system 00:01: [io  0x0c6f] has been reserved
Jun 30 15:56:59 my-pc kernel: [    0.380404] system 00:01: [io  0x0cd0-0x0cd1] has been reserved
Jun 30 15:56:59 my-pc kernel: [    0.380406] system 00:01: [io  0x0cd2-0x0cd3] has been reserved
Jun 30 15:56:59 my-pc kernel: [    0.380407] system 00:01: [io  0x0cd4-0x0cdf] has been reserved
Jun 30 15:56:59 my-pc kernel: [    0.380409] system 00:01: [io  0x4000-0x40fe] has been reserved
Jun 30 15:56:59 my-pc kernel: [    0.380411] system 00:01: [io  0x4210-0x4217] has been reserved
Jun 30 15:56:59 my-pc kernel: [    0.380412] system 00:01: [io  0x0b00-0x0b0f] has been reserved
Jun 30 15:56:59 my-pc kernel: [    0.380414] system 00:01: [io  0x0b10-0x0b1f] has been reserved
Jun 30 15:56:59 my-pc kernel: [    0.380416] system 00:01: [io  0x0b20-0x0b3f] has been reserved
Jun 30 15:56:59 my-pc kernel: [    0.380419] system 00:01: [mem 0xfee00400-0xfee00fff window] has been reserved
Jun 30 15:56:59 my-pc kernel: [    0.380422] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
Jun 30 15:56:59 my-pc kernel: [    0.380512] pnp 00:02: [dma 4]
Jun 30 15:56:59 my-pc kernel: [    0.380526] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
Jun 30 15:56:59 my-pc kernel: [    0.380593] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
Jun 30 15:56:59 my-pc kernel: [    0.380631] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
Jun 30 15:56:59 my-pc kernel: [    0.380649] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
Jun 30 15:56:59 my-pc kernel: [    0.380674] pnp 00:06: Plug and Play ACPI device, IDs PNP0c04 (active)
Jun 30 15:56:59 my-pc kernel: [    0.380819] pnp 00:07: [dma 2]
Jun 30 15:56:59 my-pc kernel: [    0.380842] pnp 00:07: Plug and Play ACPI device, IDs PNP0700 (active)
Jun 30 15:56:59 my-pc kernel: [    0.381050] pnp 00:08: Plug and Play ACPI device, IDs PNP0501 (active)
Jun 30 15:56:59 my-pc kernel: [    0.381271] pnp 00:09: Plug and Play ACPI device, IDs PNP0400 (active)
Jun 30 15:56:59 my-pc kernel: [    0.381411] system 00:0a: [mem 0xe0000000-0xefffffff] has been reserved
Jun 30 15:56:59 my-pc kernel: [    0.381413] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
Jun 30 15:56:59 my-pc kernel: [    0.381574] pnp 00:0b: disabling [mem 0x000cec00-0x000cffff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
Jun 30 15:56:59 my-pc kernel: [    0.381577] pnp 00:0b: disabling [mem 0x000f0000-0x000f7fff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
Jun 30 15:56:59 my-pc kernel: [    0.381579] pnp 00:0b: disabling [mem 0x000f8000-0x000fbfff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
Jun 30 15:56:59 my-pc kernel: [    0.381581] pnp 00:0b: disabling [mem 0x000fc000-0x000fffff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
Jun 30 15:56:59 my-pc kernel: [    0.381583] pnp 00:0b: disabling [mem 0x00000000-0x0009ffff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
Jun 30 15:56:59 my-pc kernel: [    0.381585] pnp 00:0b: disabling [mem 0x00100000-0xcfdeffff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
Jun 30 15:56:59 my-pc kernel: [    0.381607] pnp 00:0b: [Firmware Bug]: [mem 0x00000000-0xffffffffffffffff disabled] covers only part of AMD MMCONFIG area [mem 0xe0000000-0xe00fffff]; adding more reservations
Jun 30 15:56:59 my-pc kernel: [    0.381624] system 00:0b: [mem 0xcfdf0000-0xcfdfffff] could not be reserved
Jun 30 15:56:59 my-pc kernel: [    0.381626] system 00:0b: [mem 0xffff0000-0xffffffff] has been reserved
Jun 30 15:56:59 my-pc kernel: [    0.381628] system 00:0b: [mem 0xcfe00000-0xcfefffff] has been reserved
Jun 30 15:56:59 my-pc kernel: [    0.381630] system 00:0b: [mem 0xcff00000-0xcfffffff] could not be reserved
Jun 30 15:56:59 my-pc kernel: [    0.381632] system 00:0b: [mem 0xfec00000-0xfec00fff] could not be reserved
Jun 30 15:56:59 my-pc kernel: [    0.381634] system 00:0b: [mem 0xfee00000-0xfee00fff] could not be reserved
Jun 30 15:56:59 my-pc kernel: [    0.381635] system 00:0b: [mem 0xfff80000-0xfffeffff] has been reserved
Jun 30 15:56:59 my-pc kernel: [    0.381637] system 00:0b: Plug and Play ACPI device, IDs PNP0c01 (active)
Jun 30 15:56:59 my-pc kernel: [    0.381654] pnp: PnP ACPI: found 12 devices
Jun 30 15:56:59 my-pc kernel: [    0.381655] ACPI: ACPI bus type pnp unregistered
Jun 30 15:56:59 my-pc kernel: [    0.387979] pci 0000:00:01.0: PCI bridge to [bus 01]
Jun 30 15:56:59 my-pc kernel: [    0.387982] pci 0000:00:01.0:   bridge window [io  0xc000-0xcfff]
Jun 30 15:56:59 my-pc kernel: [    0.387985] pci 0000:00:01.0:   bridge window [mem 0xfd900000-0xfdafffff]
Jun 30 15:56:59 my-pc kernel: [    0.387987] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
Jun 30 15:56:59 my-pc kernel: [    0.387991] pci 0000:00:04.0: PCI bridge to [bus 02]
Jun 30 15:56:59 my-pc kernel: [    0.387992] pci 0000:00:04.0:   bridge window [io  0xb000-0xbfff]
Jun 30 15:56:59 my-pc kernel: [    0.387995] pci 0000:00:04.0:   bridge window [mem 0xfd600000-0xfd6fffff]
Jun 30 15:56:59 my-pc kernel: [    0.387997] pci 0000:00:04.0:   bridge window [mem 0xfdf00000-0xfdffffff 64bit pref]
Jun 30 15:56:59 my-pc kernel: [    0.388000] pci 0000:00:06.0: PCI bridge to [bus 03]
Jun 30 15:56:59 my-pc kernel: [    0.388002] pci 0000:00:06.0:   bridge window [io  0xe000-0xefff]
Jun 30 15:56:59 my-pc kernel: [    0.388005] pci 0000:00:06.0:   bridge window [mem 0xfde00000-0xfdefffff]
Jun 30 15:56:59 my-pc kernel: [    0.388007] pci 0000:00:06.0:   bridge window [mem 0xfdd00000-0xfddfffff 64bit pref]
Jun 30 15:56:59 my-pc kernel: [    0.388010] pci 0000:00:07.0: PCI bridge to [bus 04]
Jun 30 15:56:59 my-pc kernel: [    0.388011] pci 0000:00:07.0:   bridge window [io  0xd000-0xdfff]
Jun 30 15:56:59 my-pc kernel: [    0.388014] pci 0000:00:07.0:   bridge window [mem 0xfdc00000-0xfdcfffff]
Jun 30 15:56:59 my-pc kernel: [    0.388016] pci 0000:00:07.0:   bridge window [mem 0xfdb00000-0xfdbfffff 64bit pref]
Jun 30 15:56:59 my-pc kernel: [    0.388019] pci 0000:00:14.4: PCI bridge to [bus 05]
Jun 30 15:56:59 my-pc kernel: [    0.388021] pci 0000:00:14.4:   bridge window [io  0xa000-0xafff]
Jun 30 15:56:59 my-pc kernel: [    0.388026] pci 0000:00:14.4:   bridge window [mem 0xfd800000-0xfd8fffff]
Jun 30 15:56:59 my-pc kernel: [    0.388030] pci 0000:00:14.4:   bridge window [mem 0xfd700000-0xfd7fffff pref]
Jun 30 15:56:59 my-pc kernel: [    0.388067] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
Jun 30 15:56:59 my-pc kernel: [    0.388069] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
Jun 30 15:56:59 my-pc kernel: [    0.388071] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
Jun 30 15:56:59 my-pc kernel: [    0.388072] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000dffff]
Jun 30 15:56:59 my-pc kernel: [    0.388074] pci_bus 0000:00: resource 8 [mem 0xd0000000-0xfebfffff]
Jun 30 15:56:59 my-pc kernel: [    0.388075] pci_bus 0000:01: resource 0 [io  0xc000-0xcfff]
Jun 30 15:56:59 my-pc kernel: [    0.388077] pci_bus 0000:01: resource 1 [mem 0xfd900000-0xfdafffff]
Jun 30 15:56:59 my-pc kernel: [    0.388078] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
Jun 30 15:56:59 my-pc kernel: [    0.388080] pci_bus 0000:02: resource 0 [io  0xb000-0xbfff]
Jun 30 15:56:59 my-pc kernel: [    0.388081] pci_bus 0000:02: resource 1 [mem 0xfd600000-0xfd6fffff]
Jun 30 15:56:59 my-pc kernel: [    0.388083] pci_bus 0000:02: resource 2 [mem 0xfdf00000-0xfdffffff 64bit pref]
Jun 30 15:56:59 my-pc kernel: [    0.388084] pci_bus 0000:03: resource 0 [io  0xe000-0xefff]
Jun 30 15:56:59 my-pc kernel: [    0.388086] pci_bus 0000:03: resource 1 [mem 0xfde00000-0xfdefffff]
Jun 30 15:56:59 my-pc kernel: [    0.388087] pci_bus 0000:03: resource 2 [mem 0xfdd00000-0xfddfffff 64bit pref]
Jun 30 15:56:59 my-pc kernel: [    0.388089] pci_bus 0000:04: resource 0 [io  0xd000-0xdfff]
Jun 30 15:56:59 my-pc kernel: [    0.388090] pci_bus 0000:04: resource 1 [mem 0xfdc00000-0xfdcfffff]
Jun 30 15:56:59 my-pc kernel: [    0.388092] pci_bus 0000:04: resource 2 [mem 0xfdb00000-0xfdbfffff 64bit pref]
Jun 30 15:56:59 my-pc kernel: [    0.388093] pci_bus 0000:05: resource 0 [io  0xa000-0xafff]
Jun 30 15:56:59 my-pc kernel: [    0.388095] pci_bus 0000:05: resource 1 [mem 0xfd800000-0xfd8fffff]
Jun 30 15:56:59 my-pc kernel: [    0.388096] pci_bus 0000:05: resource 2 [mem 0xfd700000-0xfd7fffff pref]
Jun 30 15:56:59 my-pc kernel: [    0.388098] pci_bus 0000:05: resource 4 [io  0x0000-0x0cf7]
Jun 30 15:56:59 my-pc kernel: [    0.388099] pci_bus 0000:05: resource 5 [io  0x0d00-0xffff]
Jun 30 15:56:59 my-pc kernel: [    0.388101] pci_bus 0000:05: resource 6 [mem 0x000a0000-0x000bffff]
Jun 30 15:56:59 my-pc kernel: [    0.388102] pci_bus 0000:05: resource 7 [mem 0x000c0000-0x000dffff]
Jun 30 15:56:59 my-pc kernel: [    0.388104] pci_bus 0000:05: resource 8 [mem 0xd0000000-0xfebfffff]
Jun 30 15:56:59 my-pc kernel: [    0.388128] NET: Registered protocol family 2
Jun 30 15:56:59 my-pc kernel: [    0.388255] TCP established hash table entries: 32768 (order: 7, 524288 bytes)
Jun 30 15:56:59 my-pc kernel: [    0.388367] TCP bind hash table entries: 32768 (order: 7, 524288 bytes)
Jun 30 15:56:59 my-pc kernel: [    0.388450] TCP: Hash tables configured (established 32768 bind 32768)
Jun 30 15:56:59 my-pc kernel: [    0.388472] TCP: reno registered
Jun 30 15:56:59 my-pc kernel: [    0.388480] UDP hash table entries: 2048 (order: 4, 65536 bytes)
Jun 30 15:56:59 my-pc kernel: [    0.388496] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
Jun 30 15:56:59 my-pc kernel: [    0.388550] NET: Registered protocol family 1
Jun 30 15:56:59 my-pc kernel: [    0.388556] pci 0000:00:01.0: MSI quirk detected; subordinate MSI disabled
Jun 30 15:56:59 my-pc kernel: [    0.750206] pci 0000:01:05.0: Boot video device
Jun 30 15:56:59 my-pc kernel: [    0.750287] PCI: CLS 64 bytes, default 64
Jun 30 15:56:59 my-pc kernel: [    0.750333] Trying to unpack rootfs image as initramfs...
Jun 30 15:56:59 my-pc kernel: [    1.156745] Freeing initrd memory: 31080k freed
Jun 30 15:56:59 my-pc kernel: [    1.166361] PCI-DMA: Disabling AGP.
Jun 30 15:56:59 my-pc kernel: [    1.166455] PCI-DMA: aperture base @ c4000000 size 65536 KB
Jun 30 15:56:59 my-pc kernel: [    1.166456] PCI-DMA: using GART IOMMU.
Jun 30 15:56:59 my-pc kernel: [    1.166460] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
Jun 30 15:56:59 my-pc kernel: [    1.171702] LVT offset 0 assigned for vector 0x400
Jun 30 15:56:59 my-pc kernel: [    1.171733] perf: AMD IBS detected (0x000000ff)
Jun 30 15:56:59 my-pc kernel: [    1.171978] Initialise module verification
Jun 30 15:56:59 my-pc kernel: [    1.172018] audit: initializing netlink socket (disabled)
Jun 30 15:56:59 my-pc kernel: [    1.172028] type=2000 audit(1372600580.004:1): initialized
Jun 30 15:56:59 my-pc kernel: [    1.193659] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Jun 30 15:56:59 my-pc kernel: [    1.195000] VFS: Disk quotas dquot_6.5.2
Jun 30 15:56:59 my-pc kernel: [    1.195034] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Jun 30 15:56:59 my-pc kernel: [    1.195465] fuse init (API version 7.20)
Jun 30 15:56:59 my-pc kernel: [    1.195533] msgmni has been set to 6890
Jun 30 15:56:59 my-pc kernel: [    1.196048] Key type asymmetric registered
Jun 30 15:56:59 my-pc kernel: [    1.196051] Asymmetric key parser 'x509' registered
Jun 30 15:56:59 my-pc kernel: [    1.196078] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
Jun 30 15:56:59 my-pc kernel: [    1.196105] io scheduler noop registered
Jun 30 15:56:59 my-pc kernel: [    1.196107] io scheduler deadline registered (default)
Jun 30 15:56:59 my-pc kernel: [    1.196113] io scheduler cfq registered
Jun 30 15:56:59 my-pc kernel: [    1.196223] pcieport 0000:00:04.0: irq 40 for MSI/MSI-X
Jun 30 15:56:59 my-pc kernel: [    1.196277] pcieport 0000:00:06.0: irq 41 for MSI/MSI-X
Jun 30 15:56:59 my-pc kernel: [    1.196330] pcieport 0000:00:07.0: irq 42 for MSI/MSI-X
Jun 30 15:56:59 my-pc kernel: [    1.196379] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jun 30 15:56:59 my-pc kernel: [    1.196391] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Jun 30 15:56:59 my-pc kernel: [    1.196476] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
Jun 30 15:56:59 my-pc kernel: [    1.196480] ACPI: Power Button [PWRB]
Jun 30 15:56:59 my-pc kernel: [    1.196514] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Jun 30 15:56:59 my-pc kernel: [    1.196516] ACPI: Power Button [PWRF]
Jun 30 15:56:59 my-pc kernel: [    1.202675] GHES: HEST is not enabled!
Jun 30 15:56:59 my-pc kernel: [    1.202750] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Jun 30 15:56:59 my-pc kernel: [    1.223185] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jun 30 15:56:59 my-pc kernel: [    1.224368] Linux agpgart interface v0.103
Jun 30 15:56:59 my-pc kernel: [    1.225440] brd: module loaded
Jun 30 15:56:59 my-pc kernel: [    1.226035] loop: module loaded
Jun 30 15:56:59 my-pc kernel: [    1.226303] libphy: Fixed MDIO Bus: probed
Jun 30 15:56:59 my-pc kernel: [    1.226352] tun: Universal TUN/TAP device driver, 1.6
Jun 30 15:56:59 my-pc kernel: [    1.226353] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Jun 30 15:56:59 my-pc kernel: [    1.226392] PPP generic driver version 2.4.2
Jun 30 15:56:59 my-pc kernel: [    1.226434] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Jun 30 15:56:59 my-pc kernel: [    1.226435] ehci-pci: EHCI PCI platform driver
Jun 30 15:56:59 my-pc kernel: [    1.226468] ehci-pci 0000:00:12.2: EHCI Host Controller
Jun 30 15:56:59 my-pc kernel: [    1.226473] ehci-pci 0000:00:12.2: new USB bus registered, assigned bus number 1
Jun 30 15:56:59 my-pc kernel: [    1.226478] ehci-pci 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
Jun 30 15:56:59 my-pc kernel: [    1.226489] ehci-pci 0000:00:12.2: debug port 1
Jun 30 15:56:59 my-pc kernel: [    1.226527] ehci-pci 0000:00:12.2: irq 17, io mem 0xfe02c000
Jun 30 15:56:59 my-pc kernel: [    1.237723] ehci-pci 0000:00:12.2: USB 2.0 started, EHCI 1.00
Jun 30 15:56:59 my-pc kernel: [    1.237738] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
Jun 30 15:56:59 my-pc kernel: [    1.237740] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jun 30 15:56:59 my-pc kernel: [    1.237742] usb usb1: Product: EHCI Host Controller
Jun 30 15:56:59 my-pc kernel: [    1.237743] usb usb1: Manufacturer: Linux 3.8.0-26-generic ehci_hcd
Jun 30 15:56:59 my-pc kernel: [    1.237745] usb usb1: SerialNumber: 0000:00:12.2
Jun 30 15:56:59 my-pc kernel: [    1.237827] hub 1-0:1.0: USB hub found
Jun 30 15:56:59 my-pc kernel: [    1.237830] hub 1-0:1.0: 6 ports detected
Jun 30 15:56:59 my-pc kernel: [    1.237928] ehci-pci 0000:00:13.2: EHCI Host Controller
Jun 30 15:56:59 my-pc kernel: [    1.237932] ehci-pci 0000:00:13.2: new USB bus registered, assigned bus number 2
Jun 30 15:56:59 my-pc kernel: [    1.237934] ehci-pci 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
Jun 30 15:56:59 my-pc kernel: [    1.237946] ehci-pci 0000:00:13.2: debug port 1
Jun 30 15:56:59 my-pc kernel: [    1.237978] ehci-pci 0000:00:13.2: irq 19, io mem 0xfe029000
Jun 30 15:56:59 my-pc kernel: [    1.249720] ehci-pci 0000:00:13.2: USB 2.0 started, EHCI 1.00
Jun 30 15:56:59 my-pc kernel: [    1.249732] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
Jun 30 15:56:59 my-pc kernel: [    1.249734] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jun 30 15:56:59 my-pc kernel: [    1.249735] usb usb2: Product: EHCI Host Controller
Jun 30 15:56:59 my-pc kernel: [    1.249737] usb usb2: Manufacturer: Linux 3.8.0-26-generic ehci_hcd
Jun 30 15:56:59 my-pc kernel: [    1.249738] usb usb2: SerialNumber: 0000:00:13.2
Jun 30 15:56:59 my-pc kernel: [    1.249807] hub 2-0:1.0: USB hub found
Jun 30 15:56:59 my-pc kernel: [    1.249810] hub 2-0:1.0: 6 ports detected
Jun 30 15:56:59 my-pc kernel: [    1.249895] ehci-platform: EHCI generic platform driver
Jun 30 15:56:59 my-pc kernel: [    1.249901] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Jun 30 15:56:59 my-pc kernel: [    1.249923] ohci_hcd 0000:00:12.0: OHCI Host Controller
Jun 30 15:56:59 my-pc kernel: [    1.249927] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
Jun 30 15:56:59 my-pc kernel: [    1.249950] ohci_hcd 0000:00:12.0: irq 16, io mem 0xfe02e000
Jun 30 15:56:59 my-pc kernel: [    1.309642] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
Jun 30 15:56:59 my-pc kernel: [    1.309643] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jun 30 15:56:59 my-pc kernel: [    1.309645] usb usb3: Product: OHCI Host Controller
Jun 30 15:56:59 my-pc kernel: [    1.309646] usb usb3: Manufacturer: Linux 3.8.0-26-generic ohci_hcd
Jun 30 15:56:59 my-pc kernel: [    1.309648] usb usb3: SerialNumber: 0000:00:12.0
Jun 30 15:56:59 my-pc kernel: [    1.309723] hub 3-0:1.0: USB hub found
Jun 30 15:56:59 my-pc kernel: [    1.309729] hub 3-0:1.0: 3 ports detected
Jun 30 15:56:59 my-pc kernel: [    1.309803] ohci_hcd 0000:00:12.1: OHCI Host Controller
Jun 30 15:56:59 my-pc kernel: [    1.309807] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
Jun 30 15:56:59 my-pc kernel: [    1.309818] ohci_hcd 0000:00:12.1: irq 16, io mem 0xfe02d000
Jun 30 15:56:59 my-pc kernel: [    1.369584] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
Jun 30 15:56:59 my-pc kernel: [    1.369586] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jun 30 15:56:59 my-pc kernel: [    1.369588] usb usb4: Product: OHCI Host Controller
Jun 30 15:56:59 my-pc kernel: [    1.369589] usb usb4: Manufacturer: Linux 3.8.0-26-generic ohci_hcd
Jun 30 15:56:59 my-pc kernel: [    1.369590] usb usb4: SerialNumber: 0000:00:12.1
Jun 30 15:56:59 my-pc kernel: [    1.369666] hub 4-0:1.0: USB hub found
Jun 30 15:56:59 my-pc kernel: [    1.369672] hub 4-0:1.0: 3 ports detected
Jun 30 15:56:59 my-pc kernel: [    1.369741] ohci_hcd 0000:00:13.0: OHCI Host Controller
Jun 30 15:56:59 my-pc kernel: [    1.369744] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
Jun 30 15:56:59 my-pc kernel: [    1.369768] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfe02b000
Jun 30 15:56:59 my-pc kernel: [    1.429527] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
Jun 30 15:56:59 my-pc kernel: [    1.429529] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jun 30 15:56:59 my-pc kernel: [    1.429530] usb usb5: Product: OHCI Host Controller
Jun 30 15:56:59 my-pc kernel: [    1.429532] usb usb5: Manufacturer: Linux 3.8.0-26-generic ohci_hcd
Jun 30 15:56:59 my-pc kernel: [    1.429533] usb usb5: SerialNumber: 0000:00:13.0
Jun 30 15:56:59 my-pc kernel: [    1.429607] hub 5-0:1.0: USB hub found
Jun 30 15:56:59 my-pc kernel: [    1.429612] hub 5-0:1.0: 3 ports detected
Jun 30 15:56:59 my-pc kernel: [    1.429681] ohci_hcd 0000:00:13.1: OHCI Host Controller
Jun 30 15:56:59 my-pc kernel: [    1.429685] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
Jun 30 15:56:59 my-pc kernel: [    1.429698] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfe02a000
Jun 30 15:56:59 my-pc kernel: [    1.489471] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
Jun 30 15:56:59 my-pc kernel: [    1.489473] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jun 30 15:56:59 my-pc kernel: [    1.489474] usb usb6: Product: OHCI Host Controller
Jun 30 15:56:59 my-pc kernel: [    1.489476] usb usb6: Manufacturer: Linux 3.8.0-26-generic ohci_hcd
Jun 30 15:56:59 my-pc kernel: [    1.489477] usb usb6: SerialNumber: 0000:00:13.1
Jun 30 15:56:59 my-pc kernel: [    1.489550] hub 6-0:1.0: USB hub found
Jun 30 15:56:59 my-pc kernel: [    1.489555] hub 6-0:1.0: 3 ports detected
Jun 30 15:56:59 my-pc kernel: [    1.489624] ohci_hcd 0000:00:14.5: OHCI Host Controller
Jun 30 15:56:59 my-pc kernel: [    1.489628] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
Jun 30 15:56:59 my-pc kernel: [    1.489639] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfe028000
Jun 30 15:56:59 my-pc kernel: [    1.549415] usb usb7: New USB device found, idVendor=1d6b, idProduct=0001
Jun 30 15:56:59 my-pc kernel: [    1.549417] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jun 30 15:56:59 my-pc kernel: [    1.549419] usb usb7: Product: OHCI Host Controller
Jun 30 15:56:59 my-pc kernel: [    1.549420] usb usb7: Manufacturer: Linux 3.8.0-26-generic ohci_hcd
Jun 30 15:56:59 my-pc kernel: [    1.549421] usb usb7: SerialNumber: 0000:00:14.5
Jun 30 15:56:59 my-pc kernel: [    1.549492] hub 7-0:1.0: USB hub found
Jun 30 15:56:59 my-pc kernel: [    1.549497] hub 7-0:1.0: 2 ports detected
Jun 30 15:56:59 my-pc kernel: [    1.549551] uhci_hcd: USB Universal Host Controller Interface driver
Jun 30 15:56:59 my-pc kernel: [    1.549582] xhci_hcd 0000:02:00.0: xHCI Host Controller
Jun 30 15:56:59 my-pc kernel: [    1.549585] xhci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 8
Jun 30 15:56:59 my-pc kernel: [    1.549689] xhci_hcd 0000:02:00.0: irq 43 for MSI/MSI-X
Jun 30 15:56:59 my-pc kernel: [    1.549728] usb usb8: New USB device found, idVendor=1d6b, idProduct=0002
Jun 30 15:56:59 my-pc kernel: [    1.549730] usb usb8: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jun 30 15:56:59 my-pc kernel: [    1.549731] usb usb8: Product: xHCI Host Controller
Jun 30 15:56:59 my-pc kernel: [    1.549732] usb usb8: Manufacturer: Linux 3.8.0-26-generic xhci_hcd
Jun 30 15:56:59 my-pc kernel: [    1.549734] usb usb8: SerialNumber: 0000:02:00.0
Jun 30 15:56:59 my-pc kernel: [    1.549786] xHCI xhci_add_endpoint called for root hub
Jun 30 15:56:59 my-pc kernel: [    1.549787] xHCI xhci_check_bandwidth called for root hub
Jun 30 15:56:59 my-pc kernel: [    1.549801] hub 8-0:1.0: USB hub found
Jun 30 15:56:59 my-pc kernel: [    1.549806] hub 8-0:1.0: 2 ports detected
Jun 30 15:56:59 my-pc kernel: [    1.549851] xhci_hcd 0000:02:00.0: xHCI Host Controller
Jun 30 15:56:59 my-pc kernel: [    1.549854] xhci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 9
Jun 30 15:56:59 my-pc kernel: [    1.549870] usb usb9: New USB device found, idVendor=1d6b, idProduct=0003
Jun 30 15:56:59 my-pc kernel: [    1.549872] usb usb9: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jun 30 15:56:59 my-pc kernel: [    1.549873] usb usb9: Product: xHCI Host Controller
Jun 30 15:56:59 my-pc kernel: [    1.549874] usb usb9: Manufacturer: Linux 3.8.0-26-generic xhci_hcd
Jun 30 15:56:59 my-pc kernel: [    1.549875] usb usb9: SerialNumber: 0000:02:00.0
Jun 30 15:56:59 my-pc kernel: [    1.549922] xHCI xhci_add_endpoint called for root hub
Jun 30 15:56:59 my-pc kernel: [    1.549923] xHCI xhci_check_bandwidth called for root hub
Jun 30 15:56:59 my-pc kernel: [    1.549937] hub 9-0:1.0: USB hub found
Jun 30 15:56:59 my-pc kernel: [    1.549941] hub 9-0:1.0: 2 ports detected
Jun 30 15:56:59 my-pc kernel: [    1.550053] xhci_hcd 0000:04:00.0: xHCI Host Controller
Jun 30 15:56:59 my-pc kernel: [    1.550059] xhci_hcd 0000:04:00.0: new USB bus registered, assigned bus number 10
Jun 30 15:56:59 my-pc kernel: [    1.550168] xhci_hcd 0000:04:00.0: irq 44 for MSI/MSI-X
Jun 30 15:56:59 my-pc kernel: [    1.550211] usb usb10: New USB device found, idVendor=1d6b, idProduct=0002
Jun 30 15:56:59 my-pc kernel: [    1.550213] usb usb10: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jun 30 15:56:59 my-pc kernel: [    1.550214] usb usb10: Product: xHCI Host Controller
Jun 30 15:56:59 my-pc kernel: [    1.550216] usb usb10: Manufacturer: Linux 3.8.0-26-generic xhci_hcd
Jun 30 15:56:59 my-pc kernel: [    1.550217] usb usb10: SerialNumber: 0000:04:00.0
Jun 30 15:56:59 my-pc kernel: [    1.550287] xHCI xhci_add_endpoint called for root hub
Jun 30 15:56:59 my-pc kernel: [    1.550288] xHCI xhci_check_bandwidth called for root hub
Jun 30 15:56:59 my-pc kernel: [    1.550305] hub 10-0:1.0: USB hub found
Jun 30 15:56:59 my-pc kernel: [    1.550311] hub 10-0:1.0: 2 ports detected
Jun 30 15:56:59 my-pc kernel: [    1.550365] xhci_hcd 0000:04:00.0: xHCI Host Controller
Jun 30 15:56:59 my-pc kernel: [    1.550367] xhci_hcd 0000:04:00.0: new USB bus registered, assigned bus number 11
Jun 30 15:56:59 my-pc kernel: [    1.550396] usb usb11: New USB device found, idVendor=1d6b, idProduct=0003
Jun 30 15:56:59 my-pc kernel: [    1.550398] usb usb11: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jun 30 15:56:59 my-pc kernel: [    1.550399] usb usb11: Product: xHCI Host Controller
Jun 30 15:56:59 my-pc kernel: [    1.550401] usb usb11: Manufacturer: Linux 3.8.0-26-generic xhci_hcd
Jun 30 15:56:59 my-pc kernel: [    1.550402] usb usb11: SerialNumber: 0000:04:00.0
Jun 30 15:56:59 my-pc kernel: [    1.550448] xHCI xhci_add_endpoint called for root hub
Jun 30 15:56:59 my-pc kernel: [    1.550449] xHCI xhci_check_bandwidth called for root hub
Jun 30 15:56:59 my-pc kernel: [    1.550462] hub 11-0:1.0: USB hub found
Jun 30 15:56:59 my-pc kernel: [    1.550466] hub 11-0:1.0: 2 ports detected
Jun 30 15:56:59 my-pc kernel: [    1.553500] i8042: PNP: No PS/2 controller found. Probing ports directly.
Jun 30 15:56:59 my-pc kernel: [    1.586769] i8042: Failed to disable AUX port, but continuing anyway... Is this a SiS?
Jun 30 15:56:59 my-pc kernel: [    1.586770] i8042: If AUX port is really absent please use the 'i8042.noaux' option
Jun 30 15:56:59 my-pc kernel: [    1.837229] serio: i8042 KBD port at 0x60,0x64 irq 1
Jun 30 15:56:59 my-pc kernel: [    1.837332] mousedev: PS/2 mouse device common for all mice
Jun 30 15:56:59 my-pc kernel: [    1.837447] rtc_cmos 00:04: RTC can wake from S4
Jun 30 15:56:59 my-pc kernel: [    1.837547] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
Jun 30 15:56:59 my-pc kernel: [    1.837578] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
Jun 30 15:56:59 my-pc kernel: [    1.837643] device-mapper: uevent: version 1.0.3
Jun 30 15:56:59 my-pc kernel: [    1.837694] device-mapper: ioctl: 4.23.1-ioctl (2012-12-18) initialised: dm-devel@redhat.com
Jun 30 15:56:59 my-pc kernel: [    1.837701] cpuidle: using governor ladder
Jun 30 15:56:59 my-pc kernel: [    1.837702] cpuidle: using governor menu
Jun 30 15:56:59 my-pc kernel: [    1.837706] ledtrig-cpu: registered to indicate activity on CPUs
Jun 30 15:56:59 my-pc kernel: [    1.837707] EFI Variables Facility v0.08 2004-May-17
Jun 30 15:56:59 my-pc kernel: [    1.837846] ashmem: initialized
Jun 30 15:56:59 my-pc kernel: [    1.837931] TCP: cubic registered
Jun 30 15:56:59 my-pc kernel: [    1.838004] NET: Registered protocol family 10
Jun 30 15:56:59 my-pc kernel: [    1.838131] NET: Registered protocol family 17
Jun 30 15:56:59 my-pc kernel: [    1.838137] Key type dns_resolver registered
Jun 30 15:56:59 my-pc kernel: [    1.838492] Loading module verification certificates
Jun 30 15:56:59 my-pc kernel: [    1.839238] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: 28bf685926cf24167b29d0d66d07256be256431c'
Jun 30 15:56:59 my-pc kernel: [    1.839245] registered taskstats version 1
Jun 30 15:56:59 my-pc kernel: [    1.841398] Key type trusted registered
Jun 30 15:56:59 my-pc kernel: [    1.842951] Key type encrypted registered
Jun 30 15:56:59 my-pc kernel: [    1.844698] rtc_cmos 00:04: setting system clock to 2013-06-30 13:56:20 UTC (1372600580)
Jun 30 15:56:59 my-pc kernel: [    1.844730] powernow-k8: this CPU is not supported anymore, using acpi-cpufreq instead.
Jun 30 15:56:59 my-pc kernel: [    1.845550] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jun 30 15:56:59 my-pc kernel: [    1.845551] EDD information not available.
Jun 30 15:56:59 my-pc kernel: [    1.847795] Freeing unused kernel memory: 996k freed
Jun 30 15:56:59 my-pc kernel: [    1.847995] Write protecting the kernel read-only data: 12288k
Jun 30 15:56:59 my-pc kernel: [    1.852995] Freeing unused kernel memory: 1172k freed
Jun 30 15:56:59 my-pc kernel: [    1.857461] Freeing unused kernel memory: 1080k freed
Jun 30 15:56:59 my-pc kernel: [    1.888877] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Jun 30 15:56:59 my-pc kernel: [    1.889171] r8169 0000:03:00.0: irq 45 for MSI/MSI-X
Jun 30 15:56:59 my-pc kernel: [    1.889557] r8169 0000:03:00.0 eth0: RTL8168evl/8111evl at 0xffffc90000644000, 94:de:80:28:d2:1d, XID 0c900800 IRQ 45
Jun 30 15:56:59 my-pc kernel: [    1.889560] r8169 0000:03:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
Jun 30 15:56:59 my-pc kernel: [    1.893787] Disabling lock debugging due to kernel taint
Jun 30 15:56:59 my-pc kernel: [    1.893861] scsi0 : pata_atiixp
Jun 30 15:56:59 my-pc kernel: [    1.893928] wmi: Mapper loaded
Jun 30 15:56:59 my-pc kernel: [    1.894264] scsi1 : pata_atiixp
Jun 30 15:56:59 my-pc kernel: [    1.894640] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfa00 irq 14
Jun 30 15:56:59 my-pc kernel: [    1.894642] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfa08 irq 15
Jun 30 15:56:59 my-pc kernel: [    1.894970] ahci 0000:00:11.0: version 3.0
Jun 30 15:56:59 my-pc kernel: [    1.895177] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
Jun 30 15:56:59 my-pc kernel: [    1.895182] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc 
Jun 30 15:56:59 my-pc kernel: [    1.895774] scsi2 : ahci
Jun 30 15:56:59 my-pc kernel: [    1.895831] scsi3 : ahci
Jun 30 15:56:59 my-pc kernel: [    1.895884] scsi4 : ahci
Jun 30 15:56:59 my-pc kernel: [    1.895934] scsi5 : ahci
Jun 30 15:56:59 my-pc kernel: [    1.895963] ata3: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f100 irq 22
Jun 30 15:56:59 my-pc kernel: [    1.895965] ata4: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f180 irq 22
Jun 30 15:56:59 my-pc kernel: [    1.895967] ata5: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f200 irq 22
Jun 30 15:56:59 my-pc kernel: [    1.895970] ata6: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f280 irq 22
Jun 30 15:56:59 my-pc kernel: [    1.897484] [drm] Initialized drm 1.1.0 20060810
Jun 30 15:56:59 my-pc kernel: [    1.908552] Floppy drive(s): fd0 is unknown type 13 (usb?)
Jun 30 15:56:59 my-pc kernel: [    1.918886] [drm] radeon defaulting to kernel modesetting.
Jun 30 15:56:59 my-pc kernel: [    1.918888] [drm] radeon kernel modesetting enabled.
Jun 30 15:56:59 my-pc kernel: [    1.919113] [drm] initializing kernel modesetting (RS780 0x1002:0x9616 0x1458:0xD000).
Jun 30 15:56:59 my-pc kernel: [    1.919128] [drm] register mmio base: 0xFDAE0000
Jun 30 15:56:59 my-pc kernel: [    1.919129] [drm] register mmio size: 65536
Jun 30 15:56:59 my-pc kernel: [    1.919465] ATOM BIOS: B27732
Jun 30 15:56:59 my-pc kernel: [    1.919484] radeon 0000:01:05.0: VRAM: 512M 0x00000000C0000000 - 0x00000000DFFFFFFF (512M used)
Jun 30 15:56:59 my-pc kernel: [    1.919486] radeon 0000:01:05.0: GTT: 512M 0x00000000A0000000 - 0x00000000BFFFFFFF
Jun 30 15:56:59 my-pc kernel: [    1.928682] [drm] Detected VRAM RAM=512M, BAR=256M
Jun 30 15:56:59 my-pc kernel: [    1.928686] [drm] RAM width 32bits DDR
Jun 30 15:56:59 my-pc kernel: [    1.928743] [TTM] Zone  kernel: Available graphics memory: 1765512 kiB
Jun 30 15:56:59 my-pc kernel: [    1.928745] [TTM] Initializing pool allocator
Jun 30 15:56:59 my-pc kernel: [    1.928749] [TTM] Initializing DMA pool allocator
Jun 30 15:56:59 my-pc kernel: [    1.928769] [drm] radeon: 512M of VRAM memory ready
Jun 30 15:56:59 my-pc kernel: [    1.928770] [drm] radeon: 512M of GTT memory ready.
Jun 30 15:56:59 my-pc kernel: [    1.928780] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
Jun 30 15:56:59 my-pc kernel: [    1.928782] [drm] Driver supports precise vblank timestamp query.
Jun 30 15:56:59 my-pc kernel: [    1.928796] [drm] radeon: irq initialized.
Jun 30 15:56:59 my-pc kernel: [    1.928800] [drm] GART: num cpu pages 131072, num gpu pages 131072
Jun 30 15:56:59 my-pc kernel: [    1.929481] [drm] Loading RS780 Microcode
Jun 30 15:56:59 my-pc kernel: [    1.931983] FDC 0 is a post-1991 82077
Jun 30 15:56:59 my-pc kernel: [    1.936344] [drm] PCIE GART of 512M enabled (table at 0x00000000C0040000).
Jun 30 15:56:59 my-pc kernel: [    1.936375] radeon 0000:01:05.0: WB enabled
Jun 30 15:56:59 my-pc kernel: [    1.936378] radeon 0000:01:05.0: fence driver on ring 0 use gpu addr 0x00000000a0000c00 and cpu addr 0xffff880103974c00
Jun 30 15:56:59 my-pc kernel: [    1.936380] radeon 0000:01:05.0: fence driver on ring 3 use gpu addr 0x00000000a0000c0c and cpu addr 0xffff880103974c0c
Jun 30 15:56:59 my-pc kernel: [    1.936444] radeon 0000:01:05.0: setting latency timer to 64
Jun 30 15:56:59 my-pc kernel: [    1.967440] [drm] ring test on 0 succeeded in 1 usecs
Jun 30 15:56:59 my-pc kernel: [    1.967496] [drm] ring test on 3 succeeded in 1 usecs
Jun 30 15:56:59 my-pc kernel: [    1.967635] [drm] ib test on ring 0 succeeded in 0 usecs
Jun 30 15:56:59 my-pc kernel: [    2.068923] usb 4-1: new low-speed USB device number 2 using ohci_hcd
Jun 30 15:56:59 my-pc kernel: [    2.073588] ata1.00: ATAPI: PHILIPS DVDR824DP, P3.0, max UDMA/33
Jun 30 15:56:59 my-pc kernel: [    2.073717] ata1.01: ATA-7: SAMSUNG SP0802N, TK100-24, max UDMA/133
Jun 30 15:56:59 my-pc kernel: [    2.073719] ata1.01: 156368016 sectors, multi 16: LBA48 
Jun 30 15:56:59 my-pc kernel: [    2.073722] ata1.01: limited to UDMA/33 due to 40-wire cable
Jun 30 15:56:59 my-pc kernel: [    2.089616] ata1.00: configured for UDMA/33
Jun 30 15:56:59 my-pc kernel: [    2.097389] ata1.01: configured for UDMA/33
Jun 30 15:56:59 my-pc kernel: [    2.101834] scsi 0:0:0:0: CD-ROM            PHILIPS  DVDR824DP        P3.0 PQ: 0 ANSI: 5
Jun 30 15:56:59 my-pc kernel: [    2.105572] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
Jun 30 15:56:59 my-pc kernel: [    2.105574] cdrom: Uniform CD-ROM driver Revision: 3.20
Jun 30 15:56:59 my-pc kernel: [    2.105674] sr 0:0:0:0: Attached scsi CD-ROM sr0
Jun 30 15:56:59 my-pc kernel: [    2.105762] sr 0:0:0:0: Attached scsi generic sg0 type 5
Jun 30 15:56:59 my-pc kernel: [    2.115926] scsi 0:0:1:0: Direct-Access     ATA      SAMSUNG SP0802N  TK10 PQ: 0 ANSI: 5
Jun 30 15:56:59 my-pc kernel: [    2.116047] sd 0:0:1:0: [sda] 156368016 512-byte logical blocks: (80.0 GB/74.5 GiB)
Jun 30 15:56:59 my-pc kernel: [    2.116050] sd 0:0:1:0: Attached scsi generic sg1 type 0
Jun 30 15:56:59 my-pc kernel: [    2.116118] sd 0:0:1:0: [sda] Write Protect is off
Jun 30 15:56:59 my-pc kernel: [    2.116121] sd 0:0:1:0: [sda] Mode Sense: 00 3a 00 00
Jun 30 15:56:59 my-pc kernel: [    2.116153] sd 0:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 30 15:56:59 my-pc kernel: [    2.157981]  sda: sda1 sda2 < sda5 >
Jun 30 15:56:59 my-pc kernel: [    2.158301] sd 0:0:1:0: [sda] Attached SCSI disk
Jun 30 15:56:59 my-pc kernel: [    2.168826] tsc: Refined TSC clocksource calibration: 3515.549 MHz
Jun 30 15:56:59 my-pc kernel: [    2.168830] Switching to clocksource tsc
Jun 30 15:56:59 my-pc kernel: [    2.212800] ata3: SATA link down (SStatus 0 SControl 300)
Jun 30 15:56:59 my-pc kernel: [    2.212830] ata6: SATA link down (SStatus 0 SControl 300)
Jun 30 15:56:59 my-pc kernel: [    2.212859] ata5: SATA link down (SStatus 0 SControl 300)
Jun 30 15:56:59 my-pc kernel: [    2.212885] ata4: SATA link down (SStatus 0 SControl 300)
Jun 30 15:56:59 my-pc kernel: [    2.235784] usb 4-1: New USB device found, idVendor=04f3, idProduct=0210
Jun 30 15:56:59 my-pc kernel: [    2.235787] usb 4-1: New USB device strings: Mfr=0, Product=2, SerialNumber=0
Jun 30 15:56:59 my-pc kernel: [    2.235789] usb 4-1: Product: PS/2+USB Mouse
Jun 30 15:56:59 my-pc kernel: [    2.246841] usbcore: registered new interface driver usbhid
Jun 30 15:56:59 my-pc kernel: [    2.246844] usbhid: USB HID core driver
Jun 30 15:56:59 my-pc kernel: [    2.249595] input: PS/2+USB Mouse as /devices/pci0000:00/0000:00:12.1/usb4/4-1/4-1:1.0/input/input2
Jun 30 15:56:59 my-pc kernel: [    2.249704] hid-generic 0003:04F3:0210.0001: input,hidraw0: USB HID v1.11 Mouse [PS/2+USB Mouse] on usb-0000:00:12.1-1/input0
Jun 30 15:56:59 my-pc kernel: [    2.372630] usb 3-3: new low-speed USB device number 2 using ohci_hcd
Jun 30 15:56:59 my-pc kernel: [    2.416591] [drm] ib test on ring 3 succeeded in 0 usecs
Jun 30 15:56:59 my-pc kernel: [    2.416759] [drm] Radeon Display Connectors
Jun 30 15:56:59 my-pc kernel: [    2.416761] [drm] Connector 0:
Jun 30 15:56:59 my-pc kernel: [    2.416762] [drm]   VGA-1
Jun 30 15:56:59 my-pc kernel: [    2.416764] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
Jun 30 15:56:59 my-pc kernel: [    2.416764] [drm]   Encoders:
Jun 30 15:56:59 my-pc kernel: [    2.416765] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
Jun 30 15:56:59 my-pc kernel: [    2.416766] [drm] Connector 1:
Jun 30 15:56:59 my-pc kernel: [    2.416767] [drm]   DVI-D-1
Jun 30 15:56:59 my-pc kernel: [    2.416768] [drm]   HPD1
Jun 30 15:56:59 my-pc kernel: [    2.416769] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
Jun 30 15:56:59 my-pc kernel: [    2.416770] [drm]   Encoders:
Jun 30 15:56:59 my-pc kernel: [    2.416771] [drm]     DFP1: INTERNAL_KLDSCP_LVTMA
Jun 30 15:56:59 my-pc kernel: [    2.416789] [drm] radeon: power management initialized
Jun 30 15:56:59 my-pc kernel: [    2.449440] [drm] fb mappable at 0xD0142000
Jun 30 15:56:59 my-pc kernel: [    2.449441] [drm] vram apper at 0xD0000000
Jun 30 15:56:59 my-pc kernel: [    2.449442] [drm] size 8294400
Jun 30 15:56:59 my-pc kernel: [    2.449443] [drm] fb depth is 24
Jun 30 15:56:59 my-pc kernel: [    2.449444] [drm]    pitch is 7680
Jun 30 15:56:59 my-pc kernel: [    2.449507] fbcon: radeondrmfb (fb0) is primary device
Jun 30 15:56:59 my-pc kernel: [    2.464650] Console: switching to colour frame buffer device 240x67
Jun 30 15:56:59 my-pc kernel: [    2.468495] radeon 0000:01:05.0: fb0: radeondrmfb frame buffer device
Jun 30 15:56:59 my-pc kernel: [    2.468497] radeon 0000:01:05.0: registered panic notifier
Jun 30 15:56:59 my-pc kernel: [    2.468502] [drm] Initialized radeon 2.29.0 20080528 for 0000:01:05.0 on minor 0
Jun 30 15:56:59 my-pc kernel: [    2.540493] usb 3-3: New USB device found, idVendor=0461, idProduct=0010
Jun 30 15:56:59 my-pc kernel: [    2.540496] usb 3-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Jun 30 15:56:59 my-pc kernel: [    2.540498] usb 3-3: Product: USB Keyboard
Jun 30 15:56:59 my-pc kernel: [    2.540500] usb 3-3: Manufacturer: NOVATEK
Jun 30 15:56:59 my-pc kernel: [    2.547754] input: NOVATEK USB Keyboard as /devices/pci0000:00/0000:00:12.0/usb3/3-3/3-3:1.0/input/input3
Jun 30 15:56:59 my-pc kernel: [    2.547818] hid-generic 0003:0461:0010.0002: input,hidraw1: USB HID v1.10 Keyboard [NOVATEK USB Keyboard] on usb-0000:00:12.0-3/input0
Jun 30 15:56:59 my-pc kernel: [    2.557512] input: NOVATEK USB Keyboard as /devices/pci0000:00/0000:00:12.0/usb3/3-3/3-3:1.1/input/input4
Jun 30 15:56:59 my-pc kernel: [    2.557583] hid-generic 0003:0461:0010.0003: input,hidraw2: USB HID v1.10 Device [NOVATEK USB Keyboard] on usb-0000:00:12.0-3/input1
Jun 30 15:56:59 my-pc kernel: [    2.668359] usb 10-1: new high-speed USB device number 2 using xhci_hcd
Jun 30 15:56:59 my-pc kernel: [    2.687660] usb 10-1: New USB device found, idVendor=0ace, idProduct=1211
Jun 30 15:56:59 my-pc kernel: [    2.687663] usb 10-1: New USB device strings: Mfr=16, Product=32, SerialNumber=0
Jun 30 15:56:59 my-pc kernel: [    2.687665] usb 10-1: Product: USB2.0 WLAN
Jun 30 15:56:59 my-pc kernel: [    2.687667] usb 10-1: Manufacturer: ZyDAS
Jun 30 15:56:59 my-pc kernel: [    2.796275] usb 10-2: new high-speed USB device number 3 using xhci_hcd
Jun 30 15:56:59 my-pc kernel: [    2.822647] usb 10-2: New USB device found, idVendor=058f, idProduct=6387
Jun 30 15:56:59 my-pc kernel: [    2.822650] usb 10-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Jun 30 15:56:59 my-pc kernel: [    2.822652] usb 10-2: Product: Intenso Alu Line
Jun 30 15:56:59 my-pc kernel: [    2.822653] usb 10-2: Manufacturer: Alcor Tech
Jun 30 15:56:59 my-pc kernel: [    2.822655] usb 10-2: SerialNumber: 13012300003512
Jun 30 15:56:59 my-pc kernel: [    2.824490] Initializing USB Mass Storage driver...
Jun 30 15:56:59 my-pc kernel: [    2.824639] scsi6 : usb-storage 10-2:1.0
Jun 30 15:56:59 my-pc kernel: [    2.824695] usbcore: registered new interface driver usb-storage
Jun 30 15:56:59 my-pc kernel: [    2.824697] USB Mass Storage support registered.
Jun 30 15:56:59 my-pc kernel: [    3.427693] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
Jun 30 15:56:59 my-pc kernel: [    3.427697] EXT4-fs (sda1): write access will be enabled during recovery
Jun 30 15:56:59 my-pc kernel: [    3.824936] scsi 6:0:0:0: Direct-Access     Intenso  Alu Line         8.07 PQ: 0 ANSI: 4
Jun 30 15:56:59 my-pc kernel: [    3.825341] sd 6:0:0:0: Attached scsi generic sg2 type 0
Jun 30 15:56:59 my-pc kernel: [    3.825985] sd 6:0:0:0: [sdb] 7680000 512-byte logical blocks: (3.93 GB/3.66 GiB)
Jun 30 15:56:59 my-pc kernel: [    3.826618] sd 6:0:0:0: [sdb] Write Protect is off
Jun 30 15:56:59 my-pc kernel: [    3.826621] sd 6:0:0:0: [sdb] Mode Sense: 23 00 00 00
Jun 30 15:56:59 my-pc kernel: [    3.827262] sd 6:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Jun 30 15:56:59 my-pc kernel: [    3.830474]  sdb: sdb1
Jun 30 15:56:59 my-pc kernel: [    3.832320] sd 6:0:0:0: [sdb] Attached SCSI removable disk
Jun 30 15:56:59 my-pc kernel: [    5.984817] EXT4-fs (sda1): recovery complete
Jun 30 15:56:59 my-pc kernel: [    5.993001] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Jun 30 15:56:59 my-pc kernel: [   39.735202] Adding 3665916k swap on /dev/sda5.  Priority:-1 extents:1 across:3665916k 
Jun 30 15:56:59 my-pc kernel: [   39.741250] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 30 15:56:59 my-pc kernel: [   39.850018] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jun 30 15:56:59 my-pc kernel: [   39.852567] ACPI Warning: 0x0000000000000b00-0x0000000000000b07 SystemIO conflicts with Region \SOR1 1 (20121018/utaddress-251)
Jun 30 15:56:59 my-pc kernel: [   39.852574] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Jun 30 15:56:59 my-pc kernel: [   39.853774] sp5100_tco: SP5100/SB800 TCO WatchDog Timer Driver v0.05
Jun 30 15:56:59 my-pc kernel: [   39.853830] sp5100_tco: PCI Revision ID: 0x3c
Jun 30 15:56:59 my-pc kernel: [   39.853848] sp5100_tco: failed to find MMIO address, giving up.
Jun 30 15:56:59 my-pc kernel: [   39.855223] lp: driver loaded but no devices found
Jun 30 15:56:59 my-pc kernel: [   39.855565] MCE: In-kernel MCE decoding enabled.
Jun 30 15:56:59 my-pc kernel: [   39.857888] EDAC MC: Ver: 3.0.0
Jun 30 15:56:59 my-pc kernel: [   39.860800] it87: Found IT8728F chip at 0x228, revision 1
Jun 30 15:56:59 my-pc kernel: [   39.860818] it87: Beeping is supported
Jun 30 15:56:59 my-pc kernel: [   39.861579] AMD64 EDAC driver v3.4.0
Jun 30 15:56:59 my-pc kernel: [   39.861616] EDAC amd64: DRAM ECC disabled.
Jun 30 15:56:59 my-pc kernel: [   39.861628] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
Jun 30 15:56:59 my-pc kernel: [   39.861628]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
Jun 30 15:56:59 my-pc kernel: [   39.861628]  (Note that use of the override may cause unknown side effects.)
Jun 30 15:56:59 my-pc kernel: [   39.874091] parport_pc 00:09: reported by Plug and Play ACPI
Jun 30 15:56:59 my-pc kernel: [   39.874144] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Jun 30 15:56:59 my-pc kernel: [   39.916977] cfg80211: Calling CRDA to update world regulatory domain
Jun 30 15:56:59 my-pc kernel: [   39.920141] microcode: CPU0: patch_level=0x0600081c
Jun 30 15:56:59 my-pc kernel: [   39.937748] input: HDA ATI SB Line as /devices/pci0000:00/0000:00:14.2/sound/card0/input5
Jun 30 15:56:59 my-pc kernel: [   39.937891] input: HDA ATI SB Front Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input6
Jun 30 15:56:59 my-pc kernel: [   39.937973] input: HDA ATI SB Rear Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input7
Jun 30 15:56:59 my-pc kernel: [   39.938035] input: HDA ATI SB Front Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input8
Jun 30 15:56:59 my-pc kernel: [   39.938093] input: HDA ATI SB Line Out as /devices/pci0000:00/0000:00:14.2/sound/card0/input9
Jun 30 15:56:59 my-pc kernel: [   39.938382] snd_hda_intel 0000:01:05.1: setting latency timer to 64
Jun 30 15:56:59 my-pc kernel: [   39.948031] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:05.1/sound/card1/input10
Jun 30 15:56:59 my-pc kernel: [   39.968919] lp0: using parport0 (interrupt-driven).
Jun 30 15:56:59 my-pc kernel: [   39.971941] ppdev: user-space parallel port driver
Jun 30 15:56:59 my-pc kernel: [   39.978642] cfg80211: World regulatory domain updated:
Jun 30 15:56:59 my-pc kernel: [   39.978645] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jun 30 15:56:59 my-pc kernel: [   39.978648] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 30 15:56:59 my-pc kernel: [   39.978649] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jun 30 15:56:59 my-pc kernel: [   39.978651] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jun 30 15:56:59 my-pc kernel: [   39.978653] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 30 15:56:59 my-pc kernel: [   39.978655] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 30 15:56:59 my-pc kernel: [   40.044741] usb 10-1: reset high-speed USB device number 2 using xhci_hcd
Jun 30 15:56:59 my-pc kernel: [   40.062067] xhci_hcd 0000:04:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff8801047c6200
Jun 30 15:56:59 my-pc kernel: [   40.062070] xhci_hcd 0000:04:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff8801047c6240
Jun 30 15:56:59 my-pc kernel: [   40.062072] xhci_hcd 0000:04:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff8801047c6280
Jun 30 15:56:59 my-pc kernel: [   40.062074] xhci_hcd 0000:04:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff8801047c62c0
Jun 30 15:56:59 my-pc kernel: [   40.065019] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
Jun 30 15:56:59 my-pc kernel: [   40.065162] zd1211rw 10-1:1.0: phy0
Jun 30 15:56:59 my-pc kernel: [   40.065184] usbcore: registered new interface driver zd1211rw
Jun 30 15:56:59 my-pc kernel: [   40.189755] microcode: CPU1: patch_level=0x0600081c
Jun 30 15:56:59 my-pc kernel: [   40.189770] microcode: CPU2: patch_level=0x0600081c
Jun 30 15:56:59 my-pc kernel: [   40.189778] microcode: CPU3: patch_level=0x0600081c
Jun 30 15:56:59 my-pc kernel: [   40.189787] microcode: CPU4: patch_level=0x0600081c
Jun 30 15:56:59 my-pc kernel: [   40.189795] microcode: CPU5: patch_level=0x0600081c
Jun 30 15:56:59 my-pc kernel: [   40.189845] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
Jun 30 15:56:59 my-pc kernel: [   40.201039] kvm: Nested Virtualization enabled
Jun 30 15:56:59 my-pc kernel: [   40.201045] kvm: Nested Paging enabled
Jun 30 15:56:59 my-pc kernel: [   40.474209] type=1400 audit(1372600619.165:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=709 comm="apparmor_parser"
Jun 30 15:56:59 my-pc kernel: [   40.474341] type=1400 audit(1372600619.165:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=750 comm="apparmor_parser"
Jun 30 15:56:59 my-pc kernel: [   40.474348] type=1400 audit(1372600619.165:4): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=825 comm="apparmor_parser"
Jun 30 15:56:59 my-pc kernel: [   40.474471] type=1400 audit(1372600619.165:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=709 comm="apparmor_parser"
Jun 30 15:56:59 my-pc kernel: [   40.474615] type=1400 audit(1372600619.165:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=709 comm="apparmor_parser"
Jun 30 15:56:59 my-pc kernel: [   40.474748] type=1400 audit(1372600619.165:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=750 comm="apparmor_parser"
Jun 30 15:56:59 my-pc kernel: [   40.474753] type=1400 audit(1372600619.165:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=825 comm="apparmor_parser"
Jun 30 15:56:59 my-pc kernel: [   40.474968] type=1400 audit(1372600619.165:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=750 comm="apparmor_parser"
Jun 30 15:56:59 my-pc kernel: [   40.474972] type=1400 audit(1372600619.165:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=825 comm="apparmor_parser"
Jun 30 15:56:59 my-pc kernel: [   40.476391] type=1400 audit(1372600619.165:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/ntpd" pid=891 comm="apparmor_parser"
Jun 30 15:56:59 my-pc kernel: [   41.019470] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Jun 30 15:56:59 my-pc kernel: [   41.218099] Bluetooth: Core ver 2.16
Jun 30 15:56:59 my-pc kernel: [   41.218119] NET: Registered protocol family 31
Jun 30 15:56:59 my-pc kernel: [   41.218121] Bluetooth: HCI device and connection manager initialized
Jun 30 15:56:59 my-pc kernel: [   41.218347] Bluetooth: HCI socket layer initialized
Jun 30 15:56:59 my-pc kernel: [   41.218351] Bluetooth: L2CAP socket layer initialized
Jun 30 15:56:59 my-pc kernel: [   41.218357] Bluetooth: SCO socket layer initialized
Jun 30 15:56:59 my-pc kernel: [   41.222770] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Jun 30 15:56:59 my-pc kernel: [   41.222773] Bluetooth: BNEP filters: protocol multicast
Jun 30 15:56:59 my-pc kernel: [   41.222780] Bluetooth: BNEP socket layer initialized
Jun 30 15:56:59 my-pc kernel: [   41.223909] Bluetooth: RFCOMM TTY layer initialized
Jun 30 15:56:59 my-pc kernel: [   41.223917] Bluetooth: RFCOMM socket layer initialized
Jun 30 15:56:59 my-pc kernel: [   41.223919] Bluetooth: RFCOMM ver 1.11
Jun 30 15:57:00 my-pc kernel: [   41.517359] r8169 0000:03:00.0 eth0: link down
Jun 30 15:57:00 my-pc kernel: [   41.517374] r8169 0000:03:00.0 eth0: link down
Jun 30 15:57:00 my-pc kernel: [   41.517407] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 30 15:57:00 my-pc kernel: [   41.517713] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 30 15:57:00 my-pc kernel: [   41.940857] zd1211rw 10-1:1.0: firmware version 4605
Jun 30 15:57:00 my-pc kernel: [   41.945853] zd1211rw 10-1:1.0: zd1211 chip 0ace:1211 v4330 high 00-30-95 RF2959_RF pa0 -----
Jun 30 15:57:00 my-pc kernel: [   41.946242] cfg80211: Calling CRDA for country: DE
Jun 30 15:57:00 my-pc kernel: [   41.949000] cfg80211: Regulatory domain changed to country: DE
Jun 30 15:57:00 my-pc kernel: [   41.949003] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jun 30 15:57:00 my-pc kernel: [   41.949004] cfg80211:   (2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A, 2000 mBm)
Jun 30 15:57:00 my-pc kernel: [   41.949006] cfg80211:   (5150000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Jun 30 15:57:00 my-pc kernel: [   41.949007] cfg80211:   (5250000 KHz - 5350000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Jun 30 15:57:00 my-pc kernel: [   41.949008] cfg80211:   (5470000 KHz - 5725000 KHz @ 40000 KHz), (N/A, 2698 mBm)
Jun 30 15:57:00 my-pc kernel: [   41.962375] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 30 15:57:00 my-pc kernel: [   41.962624] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 30 15:57:00 my-pc kernel: [   42.198279] Unsafe core_pattern used with suid_dumpable=2. Pipe handler or fully qualified core dump path required.
Jun 30 15:57:01 my-pc kernel: [   43.167819] r8169 0000:03:00.0 eth0: link up
Jun 30 15:57:01 my-pc kernel: [   43.167827] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Jun 30 15:57:01 my-pc kernel: [   43.182946] vboxdrv: Found 6 processor cores.
Jun 30 15:57:01 my-pc kernel: [   43.183136] vboxdrv: fAsync=0 offMin=0x571 offMax=0x2713
Jun 30 15:57:01 my-pc kernel: [   43.183216] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
Jun 30 15:57:01 my-pc kernel: [   43.183218] vboxdrv: Successfully loaded version 4.2.10_Ubuntu (interface 0x001a0004).
Jun 30 15:57:01 my-pc kernel: [   43.204773] vboxpci: IOMMU not found (not registered)
Jun 30 15:57:06 my-pc kernel: [   47.387439] audit_printk_skb: 86 callbacks suppressed
Jun 30 15:57:06 my-pc kernel: [   47.387443] type=1400 audit(1372600626.080:40): apparmor="DENIED" operation="open" parent=1230 profile="/sbin/dhclient" name="/var/lib/NetworkManager/dhclient6-eth0.conf" pid=2222 comm="dhclient" requested_mask="r" denied_mask="r" fsuid=0 ouid=0

```

What can I do to prevent the stuck on the bootscreen?

Thanks for your help!

---

### Post by LinuxWillWin on 2013-06-30
´

---

### Post by LinuxWillWin on 2013-07-03
´

---

### Post by LinuxWillWin on 2013-07-04
Every suggestion is welcome! :D

---

