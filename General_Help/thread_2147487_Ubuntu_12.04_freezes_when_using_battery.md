---
title: "Ubuntu 12.04 freezes when using battery"
date: 2013-05-22
forum: General Help
---

### Post by Silent Hill on 2013-05-22
Hello!
I know there are already many posts dealing with this problem but they have not helped me up to now.
I have installed ubuntu 12.04 32 bit in a sony vaio sve1513q1es(64 bit) and I've been having freezing system problems since then.
I thought the problem was wifi device so every time I boot I perform "sudo iwconfig wlan0 power off".
Then I learnt that also google chrome can freeze the system, so I'm avoiding using it.

Finally, I see that when there's no battery, using mozilla firefoz, setting power manager off and not using pae kernel (41 42 43...generic)...with all this everything goes fine. There's no block.
But this morning I used it with battery and then it freezed again.

How can I solve this?

here's the log

```

4.6.3-1ubuntu5) ) #66-Ubuntu SMP Thu Apr 25 03:28:09 UTC 2013 (Ubuntu 3.2.0-41.66-generic 3.2.42)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] KERNEL supported cpus:
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]   Intel GenuineIntel
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]   AMD AuthenticAMD
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]   NSC Geode by NSC
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]   Cyrix CyrixInstead
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]   Centaur CentaurHauls
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]   Transmeta GenuineTMx86
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]   Transmeta TransmetaCPU
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]   UMC UMC UMC UMC
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] BIOS-provided physical RAM map:
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d400 (usable)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]  BIOS-e820: 000000000009d400 - 00000000000a0000 (reserved)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 0000000020000000 (usable)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]  BIOS-e820: 0000000020000000 - 0000000020200000 (reserved)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]  BIOS-e820: 0000000020200000 - 0000000040004000 (usable)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]  BIOS-e820: 0000000040004000 - 0000000040005000 (reserved)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]  BIOS-e820: 0000000040005000 - 00000000a4db0000 (usable)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]  BIOS-e820: 00000000a4db0000 - 00000000a61b0000 (reserved)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]  BIOS-e820: 00000000a61b0000 - 00000000aaabf000 (usable)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]  BIOS-e820: 00000000aaabf000 - 00000000aaebf000 (reserved)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]  BIOS-e820: 00000000aaebf000 - 00000000aafbf000 (ACPI NVS)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]  BIOS-e820: 00000000aafbf000 - 00000000aafff000 (ACPI data)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]  BIOS-e820: 00000000aafff000 - 00000000ab000000 (usable)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]  BIOS-e820: 00000000ab000000 - 00000000afa00000 (reserved)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]  BIOS-e820: 00000000feb00000 - 00000000feb04000 (reserved)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]  BIOS-e820: 00000000fed10000 - 00000000fed1a000 (reserved)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]  BIOS-e820: 00000000ffd00000 - 0000000100000000 (reserved)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 000000014f600000 (usable)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] SMBIOS 2.7 present.
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] DMI: Sony Corporation SVE1513Q1ESI/VAIO, BIOS R0170D5 11/14/2012
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] last_pfn = 0xab000 max_arch_pfn = 0x100000
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] MTRR default type: uncachable
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] MTRR fixed ranges enabled:
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]   00000-9FFFF write-back
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]   A0000-BFFFF uncachable
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]   C0000-E7FFF write-protect
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]   E8000-EFFFF write-combining
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]   F0000-FFFFF write-protect
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] MTRR variable ranges enabled:
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]   0 base 000000000 mask F80000000 write-back
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]   1 base 080000000 mask FE0000000 write-back
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]   2 base 0A0000000 mask FF8000000 write-back
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]   3 base 0A8000000 mask FFE000000 write-back
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]   4 base 0AA000000 mask FFF000000 write-back
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]   5 base 0FFC00000 mask FFFC00000 write-protect
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]   6 base 100000000 mask F80000000 write-back
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]   7 base 14F600000 mask FFFE00000 uncachable
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]   8 base 14F800000 mask FFF800000 uncachable
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]   9 base 150000000 mask FF0000000 uncachable
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] found SMP MP-table at [c00fe1b0] fe1b0
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] initial memory mapped : 0 - 01c00000
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] Base memory trampoline at [c0099000] 99000 size 16384
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]  0000000000 - 0000400000 page 4k
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]  0000400000 - 0037400000 page 2M
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]  0037400000 - 00377fe000 page 4k
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfa000-1c00000
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] RAMDISK: 364e0000 - 37268000
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] ACPI: RSDP 000fe020 00024 (v02   Sony)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] ACPI: XSDT aaffe210 00094 (v01   Sony     VAIO 20121030      01000013)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] ACPI: FACP aaffb000 0010C (v05   Sony     VAIO 20121030 INTL 20100121)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] ACPI Warning: FADT (revision 5) is longer than ACPI 2.0 version, truncating length 268 to 244 (20110623/tbfadt-288)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] ACPI: DSDT aafee000 09122 (v02   Sony     VAIO 20121030 INTL 20100121)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] ACPI: FACS aafbb000 00040
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] ACPI: UEFI aaffd000 00236 (v01   Sony     VAIO 20121030 INTL 20100121)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] ACPI: ASF! aaffc000 000A5 (v32   Sony     VAIO 20121030 INTL 20100121)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] ACPI: HPET aaffa000 00038 (v01   Sony     VAIO 20121030 INTL 20100121)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] ACPI: APIC aaff9000 0008C (v03   Sony     VAIO 20121030 INTL 20100121)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] ACPI: MCFG aaff8000 0003C (v01   Sony     VAIO 20121030 INTL 20100121)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] ACPI: WDAT aafec000 00224 (v01   Sony     VAIO 20121030 INTL 20100121)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] ACPI: BOOT aafea000 00028 (v01   Sony     VAIO 20121030 INTL 20100121)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] ACPI: ASPT aafe9000 00034 (v07   Sony     VAIO 20121030 INTL 20100121)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] ACPI: DBGP aafe8000 00034 (v01   Sony     VAIO 20121030 INTL 20100121)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] ACPI: FPDT aafe6000 00044 (v01   Sony     VAIO 20121030 INTL 20100121)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] ACPI: MSDM aafe5000 00055 (v03   Sony     VAIO 20121030 INTL 20100121)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] ACPI: SSDT aafe4000 009AA (v01   Sony     VAIO 20121030 INTL 20100121)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] ACPI: SSDT aafe3000 00A92 (v01   Sony     VAIO 20121030 INTL 20100121)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] 1848MB HIGHMEM available.
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] 887MB LOWMEM available.
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]   mapped low ram: 0 - 377fe000
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]   low ram: 0 - 377fe000
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] Zone PFN ranges:
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]   Normal   0x00001000 -> 0x000377fe
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]   HighMem  0x000377fe -> 0x000ab000
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] Movable zone start PFN for each node
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] early_node_map[6] active PFN ranges
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]     0: 0x00000010 -> 0x0000009d
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]     0: 0x00000100 -> 0x00020000
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]     0: 0x00020200 -> 0x00040004
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]     0: 0x00040005 -> 0x000a4db0
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]     0: 0x000a61b0 -> 0x000aaabf
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]     0: 0x000aafff -> 0x000ab000
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] On node 0 totalpages: 693324
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] free_area_init_node: node 0, pgdat c1829c40, node_mem_map f4f80200
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]   DMA zone: 32 pages used for memmap
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]   DMA zone: 0 pages reserved
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]   DMA zone: 3949 pages, LIFO batch:0
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]   Normal zone: 1744 pages used for memmap
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]   Normal zone: 220974 pages, LIFO batch:31
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]   HighMem zone: 3697 pages used for memmap
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]   HighMem zone: 462928 pages, LIFO batch:31
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] Using APIC driver default
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x00] disabled)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x00] disabled)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x00] disabled)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x00] disabled)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] ACPI: IOAPIC (id[0x00] address[0xfec00000] gsi_base[0])
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] IOAPIC[0]: apic_id 0, version 32, address 0xfec00000, GSI 0-23
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] ACPI: IRQ0 used by override.
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] ACPI: IRQ2 used by override.
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] ACPI: IRQ9 used by override.
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] SMP: Allowing 8 CPUs, 4 hotplug CPUs
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] nr_irqs_gsi: 40
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000020200000
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] Allocating PCI resources starting at afa00000 (gap: afa00000:40600000)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:8 nr_node_ids:1
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] PERCPU: Embedded 13 pages/cpu @f7789000 s31616 r0 d21632 u53248
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] pcpu-alloc: s31616 r0 d21632 u53248 alloc=13*4096
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] pcpu-alloc: [0] 0 [0] 1 [0] 2 [0] 3 [0] 4 [0] 5 [0] 6 [0] 7 
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 687851
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-41-generic root=UUID=99fb38b9-e3d3-4c85-b54f-0ddbe5bb5588 ro quiet splash vt.handoff=7
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] Initializing CPU#0
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] xsave/xrstor: enabled xstate_bv 0x7, cntxt size 0x340
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] allocated 11206400 bytes of page_cgroup
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] Initializing HighMem for node 0 (000377fe:000ab000)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] Memory: 2715296k/2801664k available (5630k kernel code, 58000k reserved, 2778k data, 712k init, 1866500k highmem)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] virtual kernel memory layout:
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]       .init : 0xc1837000 - 0xc18e9000   ( 712 kB)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]       .data : 0xc157f8c4 - 0xc1836380   (2778 kB)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]       .text : 0xc1000000 - 0xc157f8c4   (5630 kB)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] Hierarchical RCU implementation.
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] NR_IRQS:2304 nr_irqs:744 16
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] CPU 0 irqstacks, hard=f400a000 soft=f400c000
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] vt handoff: transparent VT on vt#7
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] Console: colour dummy device 80x25
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] console [tty0] enabled
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] hpet clockevent registered
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000000] Fast TSC calibration using PIT
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.004000] Detected 2594.234 MHz processor.
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000001] Calibrating delay loop (skipped), value calculated using timer frequency.. 5188.46 BogoMIPS (lpj=10376936)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000004] pid_max: default: 32768 minimum: 301
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000021] Security Framework initialized
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000031] AppArmor: AppArmor initialized
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000032] Yama: becoming mindful.
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000069] Mount-cache hash table entries: 512
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000150] Initializing cgroup subsys cpuacct
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000154] Initializing cgroup subsys memory
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000159] Initializing cgroup subsys devices
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000160] Initializing cgroup subsys freezer
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000162] Initializing cgroup subsys blkio
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000165] Initializing cgroup subsys perf_event
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000185] CPU: Physical Processor ID: 0
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000186] CPU: Processor Core ID: 0
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000190] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000191] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000869] mce: CPU supports 7 MCE banks
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000879] CPU0: Thermal monitoring enabled (TM1)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.000885] using mwait in idle threads.
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.002806] ACPI: Core revision 20110623
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.017058] ftrace: allocating 25500 entries in 50 pages
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.024396] Enabling APIC mode:  Flat.  Using 1 I/O APICs
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.024811] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.064422] CPU0: Intel(R) Core(TM) i5-3230M CPU @ 2.60GHz stepping 09
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.168693] Performance Events: PEBS fmt1+, generic architected perfmon, Intel PMU driver.
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.168698] ... version:                3
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.168699] ... bit width:              48
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.168700] ... generic registers:      4
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.168702] ... value mask:             0000ffffffffffff
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.168703] ... max period:             000000007fffffff
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.168704] ... fixed-purpose events:   3
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.168705] ... event mask:             000000070000000f
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.168832] NMI watchdog enabled, takes one hw-pmu counter.
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.168895] CPU 1 irqstacks, hard=f4160000 soft=f4162000
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.168897] Booting Node   0, Processors  #1
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.168899] smpboot cpu 1: start_ip = 99000
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.179148] Initializing CPU#1
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.277287] NMI watchdog enabled, takes one hw-pmu counter.
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.277348] CPU 2 irqstacks, hard=f416e000 soft=f4170000
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.277349]  #2
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.277350] smpboot cpu 2: start_ip = 99000
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.287564] Initializing CPU#2
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.385033] NMI watchdog enabled, takes one hw-pmu counter.
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.385094] CPU 3 irqstacks, hard=f4184000 soft=f4186000
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.385095]  #3
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.385096] smpboot cpu 3: start_ip = 99000
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.395309] Initializing CPU#3
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.492876] NMI watchdog enabled, takes one hw-pmu counter.
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.492896] Brought up 4 CPUs
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.492898] Total of 4 processors activated (20752.38 BogoMIPS).
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.496111] devtmpfs: initialized
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.496194] EVM: security.selinux
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.496196] EVM: security.SMACK64
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.496197] EVM: security.capability
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.496216] PM: Registering ACPI NVS region at aaebf000 (1048576 bytes)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.496977] print_constraints: dummy: 
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.497005] RTC time: 10:06:06, date: 05/22/13
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.497031] NET: Registered protocol family 16
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.497103] EISA bus registered
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.497104] Trying to unpack rootfs image as initramfs...
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.497121] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.497123] ACPI: bus type pci registered
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.497174] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf0000000-0xf3ffffff] (base 0xf0000000)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.497176] PCI: MMCONFIG at [mem 0xf0000000-0xf3ffffff] reserved in E820
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.497178] PCI: Using MMCONFIG for extended config space
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.497179] PCI: Using configuration type 1 for base access
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.497888] bio: create slab <bio-0> at 0
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.497942] ACPI: Added _OSI(Module Device)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.497943] ACPI: Added _OSI(Processor Device)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.497945] ACPI: Added _OSI(3.0 _SCP Extensions)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.497946] ACPI: Added _OSI(Processor Aggregator Device)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.499197] ACPI: EC: Look up EC in DSDT
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.500386] ACPI: Executed 1 blocks of module-level executable AML code
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.536334] ACPI: SSDT aae19018 0083B (v01  PmRef  Cpu0Cst 00003001 INTL 20111123)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.536659] ACPI: Dynamic OEM Table Load:
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.536661] ACPI: SSDT   (null) 0083B (v01  PmRef  Cpu0Cst 00003001 INTL 20111123)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.568111] ACPI: SSDT aae5ba98 00303 (v01  PmRef    ApIst 00003000 INTL 20111123)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.568463] ACPI: Dynamic OEM Table Load:
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.568465] ACPI: SSDT   (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20111123)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.579971] ACPI: SSDT aae18d98 00119 (v01  PmRef    ApCst 00003000 INTL 20111123)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.580293] ACPI: Dynamic OEM Table Load:
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.580295] ACPI: SSDT   (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20111123)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    0.724663] Freeing initrd memory: 13856k freed
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.015940] ACPI: Interpreter enabled
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.015950] ACPI: (supports S0 S3 S4 S5)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.015969] ACPI: Using IOAPIC for interrupt routing
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.019043] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.019180] ACPI: No dock devices found.
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.019182] HEST: Table not found.
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.019186] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.019441] \_SB_.PCI0:_OSC invalid UUID
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.019442] _OSC request data:1 8 1f 
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.019446] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.019858] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.019860] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.019862] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.019864] pci_root PNP0A08:00: host bridge window [mem 0xafa00000-0xfeafffff]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.019875] pci 0000:00:00.0: [8086:0154] type 0 class 0x000600
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.019911] pci 0000:00:02.0: [8086:0166] type 0 class 0x000300
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.019922] pci 0000:00:02.0: reg 10: [mem 0xc0000000-0xc03fffff 64bit]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.019929] pci 0000:00:02.0: reg 18: [mem 0xb0000000-0xbfffffff 64bit pref]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.019934] pci 0000:00:02.0: reg 20: [io  0x3000-0x303f]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.019986] pci 0000:00:14.0: [8086:1e31] type 0 class 0x000c03
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.020009] pci 0000:00:14.0: reg 10: [mem 0xc0700000-0xc070ffff 64bit]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.020082] pci 0000:00:14.0: PME# supported from D3hot D3cold
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.020086] pci 0000:00:14.0: PME# disabled
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.020109] pci 0000:00:16.0: [8086:1e3a] type 0 class 0x000780
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.020132] pci 0000:00:16.0: reg 10: [mem 0xc0714000-0xc071400f 64bit]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.020210] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.020214] pci 0000:00:16.0: PME# disabled
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.020247] pci 0000:00:1a.0: [8086:1e2d] type 0 class 0x000c03
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.020268] pci 0000:00:1a.0: reg 10: [mem 0xc0719000-0xc07193ff]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.020360] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.020365] pci 0000:00:1a.0: PME# disabled
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.020389] pci 0000:00:1b.0: [8086:1e20] type 0 class 0x000403
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.020404] pci 0000:00:1b.0: reg 10: [mem 0xc0710000-0xc0713fff 64bit]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.020474] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.020478] pci 0000:00:1b.0: PME# disabled
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.020501] pci 0000:00:1c.0: [8086:1e10] type 1 class 0x000604
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.020582] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.020586] pci 0000:00:1c.0: PME# disabled
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.020610] pci 0000:00:1c.1: [8086:1e12] type 1 class 0x000604
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.020690] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.020695] pci 0000:00:1c.1: PME# disabled
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.020718] pci 0000:00:1c.2: [8086:1e14] type 1 class 0x000604
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.020799] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.020803] pci 0000:00:1c.2: PME# disabled
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.020836] pci 0000:00:1d.0: [8086:1e26] type 0 class 0x000c03
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.020857] pci 0000:00:1d.0: reg 10: [mem 0xc0718000-0xc07183ff]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.020949] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.020954] pci 0000:00:1d.0: PME# disabled
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.020978] pci 0000:00:1f.0: [8086:1e59] type 0 class 0x000601
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.021103] pci 0000:00:1f.2: [8086:1e03] type 0 class 0x000106
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.021122] pci 0000:00:1f.2: reg 10: [io  0x3088-0x308f]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.021131] pci 0000:00:1f.2: reg 14: [io  0x3094-0x3097]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.021139] pci 0000:00:1f.2: reg 18: [io  0x3080-0x3087]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.021148] pci 0000:00:1f.2: reg 1c: [io  0x3090-0x3093]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.021156] pci 0000:00:1f.2: reg 20: [io  0x3060-0x307f]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.021165] pci 0000:00:1f.2: reg 24: [mem 0xc0717000-0xc07177ff]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.021210] pci 0000:00:1f.2: PME# supported from D3hot
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.021214] pci 0000:00:1f.2: PME# disabled
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.021231] pci 0000:00:1f.3: [8086:1e22] type 0 class 0x000c05
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.021246] pci 0000:00:1f.3: reg 10: [mem 0xc0715000-0xc07150ff 64bit]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.021268] pci 0000:00:1f.3: reg 20: [io  0x3040-0x305f]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.021361] pci 0000:01:00.0: [168c:0032] type 0 class 0x000280
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.021389] pci 0000:01:00.0: reg 10: [mem 0xc0600000-0xc067ffff 64bit]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.021453] pci 0000:01:00.0: reg 30: [mem 0xffff0000-0xffffffff pref]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.021520] pci 0000:01:00.0: supports D1 D2
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.021522] pci 0000:01:00.0: PME# supported from D0 D1 D2 D3hot D3cold
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.021527] pci 0000:01:00.0: PME# disabled
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.027855] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.027867] pci 0000:00:1c.0:   bridge window [mem 0xc0600000-0xc06fffff]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.028013] pci 0000:02:00.0: [10ec:5209] type 0 class 0x00ff00
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.028079] pci 0000:02:00.0: reg 10: [mem 0xc0500000-0xc0500fff]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.028569] pci 0000:02:00.0: supports D1 D2
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.028571] pci 0000:02:00.0: PME# supported from D1 D2 D3hot
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.028586] pci 0000:02:00.0: PME# disabled
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.035888] pci 0000:00:1c.1: PCI bridge to [bus 02-02]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.035895] pci 0000:00:1c.1:   bridge window [mem 0xc0500000-0xc05fffff]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.035967] pci 0000:03:00.0: [10ec:8168] type 0 class 0x000200
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.035987] pci 0000:03:00.0: reg 10: [io  0x2000-0x20ff]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.036022] pci 0000:03:00.0: reg 18: [mem 0xc0404000-0xc0404fff 64bit pref]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.036044] pci 0000:03:00.0: reg 20: [mem 0xc0400000-0xc0403fff 64bit pref]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.036137] pci 0000:03:00.0: supports D1 D2
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.036138] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.036144] pci 0000:03:00.0: PME# disabled
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.043822] pci 0000:00:1c.2: PCI bridge to [bus 03-03]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.043830] pci 0000:00:1c.2:   bridge window [io  0x2000-0x2fff]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.043860] pci 0000:00:1c.2:   bridge window [mem 0xc0400000-0xc04fffff 64bit pref]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.043877] pci_bus 0000:00: on NUMA node 0
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.043879] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.044007] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.044034] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.044058] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.044131] \_SB_.PCI0:_OSC invalid UUID
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.044132] _OSC request data:1 1f 1f 
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.044136]  pci0000:00: Requesting ACPI _OSC control (0x1d)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.044167] \_SB_.PCI0:_OSC invalid UUID
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.044169] _OSC request data:1 0 1d 
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.044172]  pci0000:00: ACPI _OSC request failed (AE_ERROR), returned control mask: 0x1d
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.044173] ACPI _OSC control for PCIe not granted, disabling ASPM
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.046085] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 10 11 12 14 15) *7
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.046124] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 10 *11 12 14 15)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.046159] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 10 *11 12 14 15)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.046193] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 *10 11 12 14 15)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.046227] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.046262] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 *10 11 12 14 15)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.046297] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 *10 11 12 14 15)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.046331] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 10 11 12 14 15) *7
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.046402] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.046408] vgaarb: loaded
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.046409] vgaarb: bridge control possible 0000:00:02.0
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.046482] i2c-core: driver [aat2870] using legacy suspend method
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.046483] i2c-core: driver [aat2870] using legacy resume method
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.046545] SCSI subsystem initialized
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.046587] libata version 3.00 loaded.
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.046621] usbcore: registered new interface driver usbfs
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.046628] usbcore: registered new interface driver hub
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.046646] usbcore: registered new device driver usb
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.046710] PCI: Using ACPI for IRQ routing
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.048259] PCI: pci_cache_line_size set to 64 bytes
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.048335] reserve RAM buffer: 000000000009d400 - 000000000009ffff 
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.048337] reserve RAM buffer: 0000000040004000 - 0000000043ffffff 
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.048338] reserve RAM buffer: 00000000a4db0000 - 00000000a7ffffff 
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.048340] reserve RAM buffer: 00000000aaabf000 - 00000000abffffff 
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.048342] reserve RAM buffer: 00000000ab000000 - 00000000abffffff 
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.048418] NetLabel: Initializing
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.048420] NetLabel:  domain hash size = 128
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.048421] NetLabel:  protocols = UNLABELED CIPSOv4
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.048428] NetLabel:  unlabeled traffic allowed by default
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.048470] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.048476] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.050485] Switching to clocksource hpet
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.055833] AppArmor: AppArmor Filesystem Enabled
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.055846] pnp: PnP ACPI init
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.055855] ACPI: bus type pnp registered
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056083] pnp 00:00: [bus 00-3e]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056085] pnp 00:00: [io  0x0000-0x0cf7 window]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056087] pnp 00:00: [io  0x0cf8-0x0cff]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056089] pnp 00:00: [io  0x0d00-0xffff window]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056090] pnp 00:00: [mem 0x000a0000-0x000bffff window]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056092] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056094] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056095] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056097] pnp 00:00: [mem 0x000cc000-0x000cffff window]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056098] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056100] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056102] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056103] pnp 00:00: [mem 0x000dc000-0x000dffff window]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056105] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056107] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056108] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056110] pnp 00:00: [mem 0x000ec000-0x000effff window]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056111] pnp 00:00: [mem 0x000f0000-0x000fffff window]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056113] pnp 00:00: [mem 0xafa00000-0xfeafffff window]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056115] pnp 00:00: [mem 0x00010000-0x0001ffff window]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056156] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056169] pnp 00:01: [io  0x0000-0x001f]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056170] pnp 00:01: [io  0x0081-0x0091]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056172] pnp 00:01: [io  0x0093-0x009f]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056173] pnp 00:01: [io  0x00c0-0x00df]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056175] pnp 00:01: [dma 4]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056193] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056199] pnp 00:02: [mem 0xff000000-0xffffffff]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056215] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056265] pnp 00:03: [mem 0xfed00000-0xfed003ff]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056282] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056289] pnp 00:04: [io  0x00f0]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056297] pnp 00:04: [irq 13]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056315] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056323] pnp 00:05: [io  0x002e-0x002f]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056324] pnp 00:05: [io  0x004e-0x004f]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056326] pnp 00:05: [io  0x0061]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056327] pnp 00:05: [io  0x0063]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056328] pnp 00:05: [io  0x0065]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056330] pnp 00:05: [io  0x0067]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056331] pnp 00:05: [io  0x0070]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056332] pnp 00:05: [io  0x0080]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056333] pnp 00:05: [io  0x0092]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056335] pnp 00:05: [io  0x00b2-0x00b3]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056336] pnp 00:05: [io  0x0680-0x069f]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056338] pnp 00:05: [io  0x1000-0x100f]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056339] pnp 00:05: [io  0xffff]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056340] pnp 00:05: [io  0xffff]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056342] pnp 00:05: [io  0x0400-0x0453]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056343] pnp 00:05: [io  0x0458-0x047f]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056345] pnp 00:05: [io  0x0500-0x057f]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056346] pnp 00:05: [io  0x164e-0x164f]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056376] system 00:05: [io  0x0680-0x069f] has been reserved
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056378] system 00:05: [io  0x1000-0x100f] has been reserved
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056380] system 00:05: [io  0xffff] has been reserved
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056382] system 00:05: [io  0xffff] has been reserved
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056384] system 00:05: [io  0x0400-0x0453] has been reserved
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056386] system 00:05: [io  0x0458-0x047f] has been reserved
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056387] system 00:05: [io  0x0500-0x057f] has been reserved
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056389] system 00:05: [io  0x164e-0x164f] has been reserved
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056392] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056398] pnp 00:06: [io  0x0070-0x0077]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056402] pnp 00:06: [irq 8]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056419] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056437] pnp 00:07: [io  0x0454-0x0457]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056464] system 00:07: [io  0x0454-0x0457] has been reserved
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056467] system 00:07: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056487] pnp 00:08: [io  0x0060]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056488] pnp 00:08: [io  0x0064]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056493] pnp 00:08: [irq 1]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056511] pnp 00:08: Plug and Play ACPI device, IDs SNYa009 PNP030b (active)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056523] pnp 00:09: [irq 12]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056544] pnp 00:09: Plug and Play ACPI device, IDs SYN2704 SYN2700 SYN0002 PNP0f13 (active)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056615] pnp 00:0a: [mem 0xfed1c000-0xfed1ffff]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056616] pnp 00:0a: [mem 0xfed10000-0xfed17fff]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056618] pnp 00:0a: [mem 0xfed18000-0xfed18fff]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056620] pnp 00:0a: [mem 0xfed19000-0xfed19fff]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056621] pnp 00:0a: [mem 0xf0000000-0xf3ffffff]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056623] pnp 00:0a: [mem 0xfed20000-0xfed3ffff]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056624] pnp 00:0a: [mem 0xfed90000-0xfed93fff]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056626] pnp 00:0a: [mem 0xff000000-0xffffffff]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056627] pnp 00:0a: [mem 0xfee00000-0xfeefffff]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056629] pnp 00:0a: [mem 0xafa00000-0xafa00fff]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056659] system 00:0a: [mem 0xfed1c000-0xfed1ffff] has been reserved
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056661] system 00:0a: [mem 0xfed10000-0xfed17fff] has been reserved
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056663] system 00:0a: [mem 0xfed18000-0xfed18fff] has been reserved
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056665] system 00:0a: [mem 0xfed19000-0xfed19fff] has been reserved
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056667] system 00:0a: [mem 0xf0000000-0xf3ffffff] has been reserved
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056669] system 00:0a: [mem 0xfed20000-0xfed3ffff] has been reserved
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056671] system 00:0a: [mem 0xfed90000-0xfed93fff] has been reserved
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056673] system 00:0a: [mem 0xff000000-0xffffffff] could not be reserved
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056675] system 00:0a: [mem 0xfee00000-0xfeefffff] could not be reserved
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056677] system 00:0a: [mem 0xafa00000-0xafa00fff] has been reserved
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056680] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056849] pnp 00:0b: [mem 0x20000000-0x201fffff]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056850] pnp 00:0b: [mem 0x40004000-0x40004fff]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056893] system 00:0b: [mem 0x20000000-0x201fffff] has been reserved
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056895] system 00:0b: [mem 0x40004000-0x40004fff] has been reserved
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056897] system 00:0b: Plug and Play ACPI device, IDs PNP0c01 (active)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056905] pnp: PnP ACPI: found 12 devices
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056906] ACPI: ACPI bus type pnp unregistered
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.056909] PnPBIOS: Disabled by ACPI PNP
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.093012] pci 0000:01:00.0: no compatible bridge window for [mem 0xffff0000-0xffffffff pref]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.093015] PCI: max bus depth: 1 pci_try_num: 2
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.093044] pci 0000:00:1c.0: BAR 15: assigned [mem 0xafb00000-0xafbfffff pref]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.093047] pci 0000:01:00.0: BAR 6: assigned [mem 0xafb00000-0xafb0ffff pref]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.093049] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.093055] pci 0000:00:1c.0:   bridge window [mem 0xc0600000-0xc06fffff]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.093059] pci 0000:00:1c.0:   bridge window [mem 0xafb00000-0xafbfffff pref]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.093065] pci 0000:00:1c.1: PCI bridge to [bus 02-02]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.093071] pci 0000:00:1c.1:   bridge window [mem 0xc0500000-0xc05fffff]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.093080] pci 0000:00:1c.2: PCI bridge to [bus 03-03]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.093083] pci 0000:00:1c.2:   bridge window [io  0x2000-0x2fff]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.093091] pci 0000:00:1c.2:   bridge window [mem 0xc0400000-0xc04fffff 64bit pref]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.093108] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.093113] pci 0000:00:1c.0: setting latency timer to 64
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.093123] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.093127] pci 0000:00:1c.1: setting latency timer to 64
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.093136] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.093140] pci 0000:00:1c.2: setting latency timer to 64
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.093144] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.093146] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.093148] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.093150] pci_bus 0000:00: resource 7 [mem 0xafa00000-0xfeafffff]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.093152] pci_bus 0000:01: resource 1 [mem 0xc0600000-0xc06fffff]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.093154] pci_bus 0000:01: resource 2 [mem 0xafb00000-0xafbfffff pref]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.093155] pci_bus 0000:02: resource 1 [mem 0xc0500000-0xc05fffff]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.093157] pci_bus 0000:03: resource 0 [io  0x2000-0x2fff]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.093159] pci_bus 0000:03: resource 2 [mem 0xc0400000-0xc04fffff 64bit pref]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.093181] NET: Registered protocol family 2
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.093220] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.093335] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.093518] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.093608] TCP: Hash tables configured (established 131072 bind 65536)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.093610] TCP reno registered
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.093612] UDP hash table entries: 512 (order: 2, 16384 bytes)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.093617] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.093661] NET: Registered protocol family 1
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.093669] pci 0000:00:02.0: Boot video device
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.093680] pci 0000:00:14.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.094885] pci 0000:00:14.0: PCI INT A disabled
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.094895] pci 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.110360] pci 0000:00:1a.0: PCI INT A disabled
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.110396] pci 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.126323] pci 0000:00:1d.0: PCI INT A disabled
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.126361] PCI: CLS 64 bytes, default 64
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.126366] Simple Boot Flag at 0x44 set to 0x1
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.126734] audit: initializing netlink socket (disabled)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.126739] type=2000 audit(1369217166.964:1): initialized
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.144853] highmem bounce pool size: 64 pages
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.144856] HugeTLB registered 4 MB page size, pre-allocated 0 pages
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.146103] VFS: Disk quotas dquot_6.5.2
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.146144] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.146513] fuse init (API version 7.17)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.146577] msgmni has been set to 1684
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.146877] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.146903] io scheduler noop registered
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.146904] io scheduler deadline registered
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.146909] io scheduler cfq registered (default)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.147114] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.147127] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.147172] intel_idle: MWAIT substates: 0x21120
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.147173] intel_idle: v0.4 model 0x3A
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.147174] intel_idle: lapic_timer_reliable_states 0xffffffff
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.147442] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.147681] ACPI: AC Adapter [ACAD] (off-line)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.147752] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.147765] ACPI: Power Button [PWRB]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.147794] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.148112] ACPI: Lid Switch [LID0]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.148148] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.148151] ACPI: Power Button [PWRF]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.149610] thermal LNXTHERM:00: registered as thermal_zone0
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.149612] ACPI: Thermal Zone [THRM] (59 C)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.149629] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.149635] ACPI: Battery Slot [BAT1] (battery present)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.149651] ERST: Table is not found!
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.149652] GHES: HEST is not enabled!
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.149699] isapnp: Scanning for PnP cards...
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.149707] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.236992] ACPI: Battery Slot [BAT1] (battery present)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.503003] isapnp: No Plug & Play device found
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.529956] Linux agpgart interface v0.103
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.530030] agpgart-intel 0000:00:00.0: Intel Ivybridge Chipset
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.530082] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.530896] agpgart-intel 0000:00:00.0: detected 65536K stolen memory
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.530988] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xb0000000
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.532006] brd: module loaded
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.532514] loop: module loaded
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.532587] ahci 0000:00:1f.2: version 3.0
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.532605] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.532642] ahci 0000:00:1f.2: irq 40 for MSI/MSI-X
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.532666] ahci: SSS flag set, parallel bus scan disabled
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.545563] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x11 impl SATA mode
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.545566] ahci 0000:00:1f.2: flags: 64bit ncq stag pm led clo pio slum part ems apst 
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.545570] ahci 0000:00:1f.2: setting latency timer to 64
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.553873] scsi0 : ahci
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.553944] scsi1 : ahci
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.554000] scsi2 : ahci
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.554054] scsi3 : ahci
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.554110] scsi4 : ahci
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.554161] scsi5 : ahci
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.554261] ata1: SATA max UDMA/133 abar m2048@0xc0717000 port 0xc0717100 irq 40
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.554263] ata2: DUMMY
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.554264] ata3: DUMMY
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.554265] ata4: DUMMY
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.554268] ata5: SATA max UDMA/133 abar m2048@0xc0717000 port 0xc0717300 irq 40
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.554270] ata6: DUMMY
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.554532] Fixed MDIO Bus: probed
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.554545] tun: Universal TUN/TAP device driver, 1.6
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.554546] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.554583] PPP generic driver version 2.4.2
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.554651] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.554664] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.554676] ehci_hcd 0000:00:1a.0: setting latency timer to 64
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.554679] ehci_hcd 0000:00:1a.0: EHCI Host Controller
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.554712] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.554733] ehci_hcd 0000:00:1a.0: debug port 2
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.558625] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.558638] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xc0719000
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.573478] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.573595] hub 1-0:1.0: USB hub found
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.573598] hub 1-0:1.0: 2 ports detected
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.573642] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.573652] ehci_hcd 0000:00:1d.0: setting latency timer to 64
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.573655] ehci_hcd 0000:00:1d.0: EHCI Host Controller
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.573687] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.573705] ehci_hcd 0000:00:1d.0: debug port 2
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.577571] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.577583] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xc0718000
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.593441] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.593540] hub 2-0:1.0: USB hub found
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.593542] hub 2-0:1.0: 2 ports detected
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.593581] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.593590] uhci_hcd: USB Universal Host Controller Interface driver
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.593610] xhci_hcd 0000:00:14.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.593626] xhci_hcd 0000:00:14.0: setting latency timer to 64
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.593629] xhci_hcd 0000:00:14.0: xHCI Host Controller
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.593663] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.593747] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.593788] xhci_hcd 0000:00:14.0: irq 41 for MSI/MSI-X
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.593877] xHCI xhci_add_endpoint called for root hub
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.593879] xHCI xhci_check_bandwidth called for root hub
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.593895] hub 3-0:1.0: USB hub found
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.593902] hub 3-0:1.0: 4 ports detected
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.593943] xhci_hcd 0000:00:14.0: xHCI Host Controller
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.593971] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 4
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.594030] xHCI xhci_add_endpoint called for root hub
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.594031] xHCI xhci_check_bandwidth called for root hub
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.594047] hub 4-0:1.0: USB hub found
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.594054] hub 4-0:1.0: 4 ports detected
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.625440] usbcore: registered new interface driver libusual
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.625477] i8042: PNP: PS/2 Controller [PNP030b:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.627258] serio: i8042 KBD port at 0x60,0x64 irq 1
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.627263] serio: i8042 AUX port at 0x60,0x64 irq 12
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.627351] mousedev: PS/2 mouse device common for all mice
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.627481] rtc_cmos 00:06: RTC can wake from S4
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.627574] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.627602] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.627650] device-mapper: uevent: version 1.0.3
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.627703] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.627723] EISA: Probing bus 0 at eisa.0
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.627724] EISA: Cannot allocate resource for mainboard
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.627726] Cannot allocate resource for EISA slot 1
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.627727] Cannot allocate resource for EISA slot 2
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.627728] Cannot allocate resource for EISA slot 3
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.627730] Cannot allocate resource for EISA slot 4
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.627731] Cannot allocate resource for EISA slot 5
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.627732] Cannot allocate resource for EISA slot 6
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.627733] Cannot allocate resource for EISA slot 7
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.627735] Cannot allocate resource for EISA slot 8
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.627736] EISA: Detected 0 cards.
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.627742] cpufreq-nforce2: No nForce2 chipset.
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.627834] cpuidle: using governor ladder
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.627984] cpuidle: using governor menu
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.627986] EFI Variables Facility v0.08 2004-May-17
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.628135] TCP cubic registered
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.628213] NET: Registered protocol family 10
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.628550] NET: Registered protocol family 17
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.628553] Registering the dns_resolver key type
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.628568] Using IPI No-Shortcut mode
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.628653] PM: Hibernation image not present or could not be loaded.
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.628660] registered taskstats version 1
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.634688]   Magic number: 13:769:123
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.634711] acpi LNXSYBUS:01: hash matches
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.634761] rtc_cmos 00:06: setting system clock to 2013-05-22 10:06:07 UTC (1369217167)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.635294] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.635295] EDD information not available.
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.641768] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.872948] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.884922] usb 1-1: new high-speed USB device number 2 using ehci_hcd
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.926337] ata1.00: ATA-8: TOSHIBA MQ01ABD075, AX0A3H, max UDMA/100
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.926344] ata1.00: 1465149168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.928176] ata1.00: configured for UDMA/100
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.928455] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MQ01ABD0 AX0A PQ: 0 ANSI: 5
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.928574] sd 0:0:0:0: Attached scsi generic sg0 type 0
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.928578] sd 0:0:0:0: [sda] 1465149168 512-byte logical blocks: (750 GB/698 GiB)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.928581] sd 0:0:0:0: [sda] 4096-byte physical blocks
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.928619] sd 0:0:0:0: [sda] Write Protect is off
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.928621] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    1.928631] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    2.017554] hub 1-1:1.0: USB hub found
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    2.017739] hub 1-1:1.0: 6 ports detected
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    2.055901]  sda: sda1 sda2 sda3 < sda5 sda6 >
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    2.056459] sd 0:0:0:0: [sda] Attached SCSI disk
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    2.124464] Refined TSC clocksource calibration: 2594.108 MHz.
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    2.124472] Switching to clocksource tsc
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    2.128448] usb 2-1: new high-speed USB device number 2 using ehci_hcd
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    2.244236] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    2.246897] ata5.00: ATAPI: HL-DT-ST DVDRAM GT80N, SV02, max UDMA/133
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    2.249045] ata5.00: configured for UDMA/133
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    2.253271] scsi 4:0:0:0: CD-ROM            HL-DT-ST DVDRAM GT80N     SV02 PQ: 0 ANSI: 5
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    2.257621] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    2.257627] cdrom: Uniform CD-ROM driver Revision: 3.20
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    2.257825] sr 4:0:0:0: Attached scsi CD-ROM sr0
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    2.257926] sr 4:0:0:0: Attached scsi generic sg1 type 5
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    2.258197] Freeing unused kernel memory: 712k freed
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    2.258350] Write protecting the kernel text: 5632k
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    2.258419] Write protecting the kernel read-only data: 2332k
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    2.260645] hub 2-1:1.0: USB hub found
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    2.260754] hub 2-1:1.0: 6 ports detected
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    2.286242] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    2.286264] r8169 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    2.286304] r8169 0000:03:00.0: setting latency timer to 64
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    2.286391] r8169 0000:03:00.0: irq 42 for MSI/MSI-X
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    2.291391] r8169 0000:03:00.0: eth0: RTL8168evl/8111evl at 0xf803c000, 30:f9:ed:d6:63:da, XID 0c900800 IRQ 42
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    2.291395] r8169 0000:03:00.0: eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    2.427893] usb 3-4: new low-speed USB device number 2 using xhci_hcd
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    2.447230] usb 3-4: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    2.450828] input: USB Optical Mouse as /devices/pci0000:00/0000:00:14.0/usb3/3-4/3-4:1.0/input/input4
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    2.450980] generic-usb 0003:192F:0416.0001: input,hidraw0: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:14.0-4/input0
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    2.450996] usbcore: registered new interface driver usbhid
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    2.450998] usbhid: USB HID core driver
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    2.519764] usb 1-1.2: new full-speed USB device number 3 using ehci_hcd
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    2.687451] usb 1-1.3: new high-speed USB device number 4 using ehci_hcd
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    2.792820] EXT3-fs (sda5): recovery required on readonly filesystem
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    2.792823] EXT3-fs (sda5): write access will be enabled during recovery
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    9.661240] kjournald starting.  Commit interval 5 seconds
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    9.661465] EXT3-fs (sda5): orphan cleanup on readonly fs
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    9.661469] ext3_orphan_cleanup: deleting unreferenced inode 22890246
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    9.661489] ext3_orphan_cleanup: deleting unreferenced inode 22890085
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    9.661497] ext3_orphan_cleanup: deleting unreferenced inode 22890143
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    9.661502] ext3_orphan_cleanup: deleting unreferenced inode 22890175
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    9.661507] ext3_orphan_cleanup: deleting unreferenced inode 22890083
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    9.661512] ext3_orphan_cleanup: deleting unreferenced inode 22890067
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    9.661518] ext3_orphan_cleanup: deleting unreferenced inode 22888603
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    9.661523] ext3_orphan_cleanup: deleting unreferenced inode 22888672
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    9.661527] ext3_orphan_cleanup: deleting unreferenced inode 22888664
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    9.661533] ext3_orphan_cleanup: deleting unreferenced inode 22888645
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    9.661540] ext3_orphan_cleanup: deleting unreferenced inode 17924101
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    9.661544] ext3_orphan_cleanup: deleting unreferenced inode 17924100
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    9.661549] ext3_orphan_cleanup: deleting unreferenced inode 22888623
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    9.661554] ext3_orphan_cleanup: deleting unreferenced inode 22888558
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    9.661559] ext3_orphan_cleanup: deleting unreferenced inode 22890149
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    9.661564] ext3_orphan_cleanup: deleting unreferenced inode 22890139
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    9.661569] EXT3-fs (sda5): 16 orphan inodes deleted
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    9.661570] EXT3-fs (sda5): recovery complete
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [    9.872856] EXT3-fs (sda5): mounted filesystem with ordered data mode
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.001525] Adding 5116664k swap on /dev/sda6.  Priority:-1 extents:1 across:5116664k 
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.005916] ADDRCONF(NETDEV_UP): eth0: link is not ready
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.076659] [drm] Initialized drm 1.1.0 20060810
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.077024] lp: driver loaded but no devices found
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.079328] cfg80211: Calling CRDA to update world regulatory domain
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.080262] rts_pstor: module is from the staging directory, the quality is unknown, you have been warned.
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.081028] Initializing Realtek PCIE storage driver...
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.081058] rts_pstor 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.081478] mei: module is from the staging directory, the quality is unknown, you have been warned.
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.081920] mei 0000:00:16.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.081928] mei 0000:00:16.0: setting latency timer to 64
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.081981] mei 0000:00:16.0: irq 43 for MSI/MSI-X
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.083858] Resource length: 0x1000
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.083870] Original address: 0xc0500000, remapped address: 0xf8054000
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.083873] pci->irq = 17
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.083874] rtsx_acquire_irq: chip->msi_en = 0, pci->irq = 17
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.083901] rts_pstor 0000:02:00.0: setting latency timer to 64
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.088596] Bluetooth: Core ver 2.16
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.088611] NET: Registered protocol family 31
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.088613] Bluetooth: HCI device and connection manager initialized
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.088615] Bluetooth: HCI socket layer initialized
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.088617] Bluetooth: L2CAP socket layer initialized
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.088621] Bluetooth: SCO socket layer initialized
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.089621] Linux video capture interface: v2.00
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.089739] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.089743] i915 0000:00:02.0: setting latency timer to 64
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.099948] ath9k 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.099961] ath9k 0000:01:00.0: setting latency timer to 64
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.104087] usbcore: registered new interface driver btusb
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.109908] ath: EEPROM regdomain: 0x65
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.109910] ath: EEPROM indicates we should expect a direct regpair map
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.109913] ath: Country alpha2 being used: 00
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.109915] ath: Regpair used: 0x65
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.110450] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.110454] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.110456] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.110459] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.110461] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.110463] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.110465] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.110469] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.110471] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.110474] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.110476] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.110478] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.110480] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.110483] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.110485] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.110487] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.110489] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.110492] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.110503] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.110506] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.110508] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.110511] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.110513] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.110516] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.110518] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.110520] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.110523] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.111137] mtrr: no more MTRRs available
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.111140] [drm] MTRR allocation failed.  Graphics performance may suffer.
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.111530] type=1400 audit(1369209991.017:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=473 comm="apparmor_parser"
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.111848] i915 0000:00:02.0: irq 44 for MSI/MSI-X
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.111853] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.111855] [drm] Driver supports precise vblank timestamp query.
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.111921] [drm:intel_dsm_platform_mux_info] *ERROR* MUX INFO call failed
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.111933] type=1400 audit(1369209991.017:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=473 comm="apparmor_parser"
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.112124] type=1400 audit(1369209991.017:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=473 comm="apparmor_parser"
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.112518] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.113276] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.122239] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.122753] Registered led device: ath9k-phy0
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.122761] ieee80211 phy0: Atheros AR9485 Rev:1 mem=0xf8d00000, irq=16
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.136699] uvcvideo: Found UVC 1.00 device USB2.0 Camera (05ca:18c3)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.140339] input: USB2.0 Camera as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.0/input/input5
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.140402] usbcore: registered new interface driver uvcvideo
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.140404] USB Video Class driver (1.1.1)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.199180] sony_laptop: Sony Notebook Control Driver v0.6
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.204435] input: Sony Vaio Keys as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/SNY5001:00/input/input6
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.204524] input: Sony Vaio Jogdial as /devices/virtual/input/input7
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.204661] sony_laptop: brightness ignored, must be controlled by ACPI video driver
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.225869] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.225873] cfg80211: World regulatory domain updated:
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.225875] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.225878] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.225880] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.225883] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.225885] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.225887] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.285185] scsi6 : SCSI emulation for PCI-Express Mass Storage devices
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.285319] rts_pstor: waiting for device to settle before scanning
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.518129] EXT3-fs (sda5): using internal journal
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.547383] init: failsafe main process (768) killed by TERM signal
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.709565] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.709568] Bluetooth: BNEP filters: protocol multicast
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.712525] Bluetooth: RFCOMM TTY layer initialized
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.712530] Bluetooth: RFCOMM socket layer initialized
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.712531] Bluetooth: RFCOMM ver 1.11
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.752315] type=1400 audit(1369209991.661:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=858 comm="apparmor_parser"
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.754682] type=1400 audit(1369209991.661:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=863 comm="apparmor_parser"
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.755170] type=1400 audit(1369209991.661:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=863 comm="apparmor_parser"
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.756663] type=1400 audit(1369209991.665:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=864 comm="apparmor_parser"
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.757135] type=1400 audit(1369209991.665:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=864 comm="apparmor_parser"
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.758645] type=1400 audit(1369209991.665:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=860 comm="apparmor_parser"
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.759101] type=1400 audit(1369209991.665:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=866 comm="apparmor_parser"
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.767459] ppdev: user-space parallel port driver
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.772442] fbcon: inteldrmfb (fb0) is primary device
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.772517] Console: switching to colour frame buffer device 170x48
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.772545] fb0: inteldrmfb frame buffer device
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.772546] drm: registered panic notifier
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.773716] acpi device:35: registered as cooling_device4
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.774003] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input8
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.774083] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.774435] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.774473] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.774527] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.774927] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.850507] psmouse serio1: synaptics: Touchpad model: 1, fw: 8.1, id: 0x1e2b1, caps: 0xd00123/0x840300/0x127c00
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.883497] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
May 22 10:06:31 lory-SVE1513Q1ESI kernel: [   25.986904] ADDRCONF(NETDEV_UP): wlan0: link is not ready
May 22 10:06:32 lory-SVE1513Q1ESI kernel: [   26.132280] r8169 0000:03:00.0: eth0: link down
May 22 10:06:32 lory-SVE1513Q1ESI kernel: [   26.132287] r8169 0000:03:00.0: eth0: link down
May 22 10:06:32 lory-SVE1513Q1ESI kernel: [   26.132428] ADDRCONF(NETDEV_UP): eth0: link is not ready
May 22 10:06:32 lory-SVE1513Q1ESI kernel: [   26.132835] ADDRCONF(NETDEV_UP): eth0: link is not ready
May 22 10:06:32 lory-SVE1513Q1ESI kernel: [   26.160556] init: alsa-restore main process (933) terminated with status 19
May 22 10:06:32 lory-SVE1513Q1ESI kernel: [   26.283171] rts_pstor: device scan complete
May 22 10:06:32 lory-SVE1513Q1ESI kernel: [   26.283355] scsi 6:0:0:0: Direct-Access     Generic- SD/MMC           1.00 PQ: 0 ANSI: 0 CCS
May 22 10:06:32 lory-SVE1513Q1ESI kernel: [   26.283482] scsi 6:0:0:1: Direct-Access     Generic- MemoryStick      1.00 PQ: 0 ANSI: 0 CCS
May 22 10:06:32 lory-SVE1513Q1ESI kernel: [   26.283547] Bad LUN (0:2)
May 22 10:06:32 lory-SVE1513Q1ESI kernel: [   26.283667] Bad target number (1:0)
May 22 10:06:32 lory-SVE1513Q1ESI kernel: [   26.283784] Bad target number (2:0)
May 22 10:06:32 lory-SVE1513Q1ESI kernel: [   26.283879] Bad target number (3:0)
May 22 10:06:32 lory-SVE1513Q1ESI kernel: [   26.283983] Bad target number (4:0)
May 22 10:06:32 lory-SVE1513Q1ESI kernel: [   26.284015] Bad target number (5:0)
May 22 10:06:32 lory-SVE1513Q1ESI kernel: [   26.284048] Bad target number (6:0)
May 22 10:06:32 lory-SVE1513Q1ESI kernel: [   26.284114] Bad target number (7:0)
May 22 10:06:32 lory-SVE1513Q1ESI kernel: [   26.284385] sd 6:0:0:0: [sdb] Attached SCSI removable disk
May 22 10:06:32 lory-SVE1513Q1ESI kernel: [   26.284579] sd 6:0:0:0: Attached scsi generic sg2 type 0
May 22 10:06:32 lory-SVE1513Q1ESI kernel: [   26.286360] sd 6:0:0:1: Attached scsi generic sg3 type 0
May 22 10:06:32 lory-SVE1513Q1ESI kernel: [   26.286777] sd 6:0:0:1: [sdc] Attached SCSI removable disk
May 22 10:06:32 lory-SVE1513Q1ESI kernel: [   26.326138] HDMI status: Codec=3 Pin=5 Presence_Detect=0 ELD_Valid=0
May 22 10:06:32 lory-SVE1513Q1ESI kernel: [   26.326196] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
May 22 10:06:32 lory-SVE1513Q1ESI kernel: [   26.326267] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
May 22 10:06:32 lory-SVE1513Q1ESI kernel: [   26.326327] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
May 22 10:06:32 lory-SVE1513Q1ESI kernel: [   26.591604] init: anacron main process (964) killed by TERM signal
May 22 10:06:32 lory-SVE1513Q1ESI kernel: [   26.655379] [drm:gen6_sanitize_pm] *ERROR* Power management discrepancy: GEN6_RP_INTERRUPT_LIMITS expected 16000000, was 12060000
May 22 10:06:33 lory-SVE1513Q1ESI kernel: [   27.259539] init: plymouth-stop pre-start process (1273) terminated with status 1
May 22 10:06:34 lory-SVE1513Q1ESI kernel: [   28.420238] r8169 0000:03:00.0: eth0: link up
May 22 10:06:34 lory-SVE1513Q1ESI kernel: [   28.420350] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
May 22 10:06:41 lory-SVE1513Q1ESI kernel: [   35.302606] [drm:gen6_sanitize_pm] *ERROR* Power management discrepancy: GEN6_RP_INTERRUPT_LIMITS expected 16070000, was 16000000
May 22 10:06:47 lory-SVE1513Q1ESI kernel: [   40.580130] eth0: no IPv6 routers present


```


thanks for you attention!

---

