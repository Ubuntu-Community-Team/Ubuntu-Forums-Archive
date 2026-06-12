---
title: "Ubuntu 14.10 stalls on boot"
date: 2015-01-10
forum: General Help
---

### Post by gold14-q on 2015-01-10
I recently installed Ubuntu 14.10 on my HP 2000 laptop alongside the Windows 10 technical preview. I originally tried to install from USB, but my laptop wouldn't boot from USB (I checked my BIOS settings - nothing was amis), soI installed from a DVD. The installation process went smoothly, then I booted into Ubuntu. After a while, it was time to go to bed, so I told Ubuntu to shutdown using the button in the Unity GUI. My laptop mostly shut down, but it displayed a black screen but still had power for quite some time. Tiring of that screen, I held down the power button and my computer turned off.

The next time I tried to boot into Ubuntu, I was shown the purple Ubuntu screen with the Ubuntu logo and the five dots underneath. That screen stayed for probably five minutes before I became impatient and shut down my laptop by holding down the power button. Since then, every time I try to boot into Ubuntu, I get the same result.

I've booted from my Ubuntu 14.10 live CD, and am using that now. The contents of my /var/log/dmesg can be found at [http://pastebin.com/F0QJCMkS](http://pastebin.com/F0QJCMkS)

Mod Note: They have been copied below.

```

[LIST=1]
[*][COLOR=#000000][    0.000000] Initializing cgroup subsys cpuset[/COLOR]
[*][COLOR=#000000][    0.000000] Initializing cgroup subsys cpu[/COLOR]
[*][COLOR=#000000][    0.000000] Initializing cgroup subsys cpuacct[/COLOR]
[*][COLOR=#000000][    0.000000] Linux version 3.16.0-23-generic (buildd@phianna) (gcc version 4.9.1 (Ubuntu 4.9.1-16ubuntu6) ) #31-Ubuntu SMP Tue Oct 21 17:56:17 UTC 2014 (Ubuntu 3.16.0-23.31-generic 3.16.4)[/COLOR]
[*][COLOR=#000000][    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.16.0-23-generic root=UUID=ed568bf2-afe1-4317-900a-e15d74216072 ro quiet splash vt.handoff=7[/COLOR]
[*][COLOR=#000000][    0.000000] KERNEL supported cpus:[/COLOR]
[*][COLOR=#000000][    0.000000]   Intel GenuineIntel[/COLOR]
[*][COLOR=#000000][    0.000000]   AMD AuthenticAMD[/COLOR]
[*][COLOR=#000000][    0.000000]   Centaur CentaurHauls[/COLOR]
[*][COLOR=#000000][    0.000000] e820: BIOS-provided physical RAM map:[/COLOR]
[*][COLOR=#000000][    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009cbff] usable[/COLOR]
[*][COLOR=#000000][    0.000000] BIOS-e820: [mem 0x000000000009cc00-0x000000000009ffff] reserved[/COLOR]
[*][COLOR=#000000][    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved[/COLOR]
[*][COLOR=#000000][    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000bb63efff] usable[/COLOR]
[*][COLOR=#000000][    0.000000] BIOS-e820: [mem 0x00000000bb63f000-0x00000000bb6befff] reserved[/COLOR]
[*][COLOR=#000000][    0.000000] BIOS-e820: [mem 0x00000000bb6bf000-0x00000000bb7befff] ACPI NVS[/COLOR]
[*][COLOR=#000000][    0.000000] BIOS-e820: [mem 0x00000000bb7bf000-0x00000000bb7fefff] ACPI data[/COLOR]
[*][COLOR=#000000][    0.000000] BIOS-e820: [mem 0x00000000bb7ff000-0x00000000bb7fffff] usable[/COLOR]
[*][COLOR=#000000][    0.000000] BIOS-e820: [mem 0x00000000bb800000-0x00000000bfffffff] reserved[/COLOR]
[*][COLOR=#000000][    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved[/COLOR]
[*][COLOR=#000000][    0.000000] BIOS-e820: [mem 0x00000000feb00000-0x00000000feb03fff] reserved[/COLOR]
[*][COLOR=#000000][    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved[/COLOR]
[*][COLOR=#000000][    0.000000] BIOS-e820: [mem 0x00000000fed10000-0x00000000fed13fff] reserved[/COLOR]
[*][COLOR=#000000][    0.000000] BIOS-e820: [mem 0x00000000fed18000-0x00000000fed19fff] reserved[/COLOR]
[*][COLOR=#000000][    0.000000] BIOS-e820: [mem 0x00000000fed1b000-0x00000000fed1ffff] reserved[/COLOR]
[*][COLOR=#000000][    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved[/COLOR]
[*][COLOR=#000000][    0.000000] BIOS-e820: [mem 0x00000000ffe00000-0x00000000ffffffff] reserved[/COLOR]
[*][COLOR=#000000][    0.000000] BIOS-e820: [mem 0x0000000100000000-0x0000000137ffffff] usable[/COLOR]
[*][COLOR=#000000][    0.000000] NX (Execute Disable) protection: active[/COLOR]
[*][COLOR=#000000][    0.000000] SMBIOS 2.6 present.[/COLOR]
[*][COLOR=#000000][    0.000000] DMI: Hewlett-Packard HP 2000 Notebook PC             /3674, BIOS F.24 09/22/2011[/COLOR]
[*][COLOR=#000000][    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved[/COLOR]
[*][COLOR=#000000][    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable[/COLOR]
[*][COLOR=#000000][    0.000000] AGP: No AGP bridge found[/COLOR]
[*][COLOR=#000000][    0.000000] e820: last_pfn = 0x138000 max_arch_pfn = 0x400000000[/COLOR]
[*][COLOR=#000000][    0.000000] MTRR default type: uncachable[/COLOR]
[*][COLOR=#000000][    0.000000] MTRR fixed ranges enabled:[/COLOR]
[*][COLOR=#000000][    0.000000]   00000-9FFFF write-back[/COLOR]
[*][COLOR=#000000][    0.000000]   A0000-BFFFF uncachable[/COLOR]
[*][COLOR=#000000][    0.000000]   C0000-EFFFF write-through[/COLOR]
[*][COLOR=#000000][    0.000000]   F0000-FFFFF write-combining[/COLOR]
[*][COLOR=#000000][    0.000000] MTRR variable ranges enabled:[/COLOR]
[*][COLOR=#000000][    0.000000]   0 base 000000000 mask F80000000 write-back[/COLOR]
[*][COLOR=#000000][    0.000000]   1 base 0FFE00000 mask FFFE00000 write-protect[/COLOR]
[*][COLOR=#000000][    0.000000]   2 base 080000000 mask FC0000000 write-back[/COLOR]
[*][COLOR=#000000][    0.000000]   3 base 0BC000000 mask FFC000000 uncachable[/COLOR]
[*][COLOR=#000000][    0.000000]   4 base 0BB800000 mask FFF800000 uncachable[/COLOR]
[*][COLOR=#000000][    0.000000]   5 base 100000000 mask FC0000000 write-back[/COLOR]
[*][COLOR=#000000][    0.000000]   6 base 138000000 mask FF8000000 uncachable[/COLOR]
[*][COLOR=#000000][    0.000000]   7 disabled[/COLOR]
[*][COLOR=#000000][    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106[/COLOR]
[*][COLOR=#000000][    0.000000] e820: last_pfn = 0xbb800 max_arch_pfn = 0x400000000[/COLOR]
[*][COLOR=#000000][    0.000000] Scanning 1 areas for low memory corruption[/COLOR]
[*][COLOR=#000000][    0.000000] Base memory trampoline at [ffff880000096000] 96000 size 24576[/COLOR]
[*][COLOR=#000000][    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff][/COLOR]
[*][COLOR=#000000][    0.000000]  [mem 0x00000000-0x000fffff] page 4k[/COLOR]
[*][COLOR=#000000][    0.000000] BRK [0x01fd3000, 0x01fd3fff] PGTABLE[/COLOR]
[*][COLOR=#000000][    0.000000] BRK [0x01fd4000, 0x01fd4fff] PGTABLE[/COLOR]
[*][COLOR=#000000][    0.000000] BRK [0x01fd5000, 0x01fd5fff] PGTABLE[/COLOR]
[*][COLOR=#000000][    0.000000] init_memory_mapping: [mem 0x137e00000-0x137ffffff][/COLOR]
[*][COLOR=#000000][    0.000000]  [mem 0x137e00000-0x137ffffff] page 2M[/COLOR]
[*][COLOR=#000000][    0.000000] BRK [0x01fd6000, 0x01fd6fff] PGTABLE[/COLOR]
[*][COLOR=#000000][    0.000000] init_memory_mapping: [mem 0x134000000-0x137dfffff][/COLOR]
[*][COLOR=#000000][    0.000000]  [mem 0x134000000-0x137dfffff] page 2M[/COLOR]
[*][COLOR=#000000][    0.000000] init_memory_mapping: [mem 0x100000000-0x133ffffff][/COLOR]
[*][COLOR=#000000][    0.000000]  [mem 0x100000000-0x133ffffff] page 2M[/COLOR]
[*][COLOR=#000000][    0.000000] init_memory_mapping: [mem 0x00100000-0xbb63efff][/COLOR]
[*][COLOR=#000000][    0.000000]  [mem 0x00100000-0x001fffff] page 4k[/COLOR]
[*][COLOR=#000000][    0.000000]  [mem 0x00200000-0xbb5fffff] page 2M[/COLOR]
[*][COLOR=#000000][    0.000000]  [mem 0xbb600000-0xbb63efff] page 4k[/COLOR]
[*][COLOR=#000000][    0.000000] init_memory_mapping: [mem 0xbb7ff000-0xbb7fffff][/COLOR]
[*][COLOR=#000000][    0.000000]  [mem 0xbb7ff000-0xbb7fffff] page 4k[/COLOR]
[*][COLOR=#000000][    0.000000] RAMDISK: [mem 0x35904000-0x36c79fff][/COLOR]
[*][COLOR=#000000][    0.000000] ACPI: Early table checksum verification disabled[/COLOR]
[*][COLOR=#000000][    0.000000] ACPI: RSDP 0x00000000000FE020 000024 (v02 HPQOEM)[/COLOR]
[*][COLOR=#000000][    0.000000] ACPI: XSDT 0x00000000BB7FE120 000074 (v01 HPQOEM SLIC-MPC 00000001      01000013)[/COLOR]
[*][COLOR=#000000][    0.000000] ACPI: FACP 0x00000000BB7FC000 0000F4 (v04 HPQOEM SLIC-MPC 00000001 MSFT 01000013)[/COLOR]
[*][COLOR=#000000][    0.000000] ACPI: DSDT 0x00000000BB7ED000 00BEC7 (v02 HP     INSYDE   00000001 MSFT 01000013)[/COLOR]
[*][COLOR=#000000][    0.000000] ACPI: FACS 0x00000000BB76D000 000040[/COLOR]
[*][COLOR=#000000][    0.000000] ACPI: ASF! 0x00000000BB7FD000 0000A5 (v32 HP     INSYDE   00000001 MSFT 01000013)[/COLOR]
[*][COLOR=#000000][    0.000000] ACPI: HPET 0x00000000BB7FB000 000038 (v01 HP     INSYDE   00000001 MSFT 01000013)[/COLOR]
[*][COLOR=#000000][    0.000000] ACPI: APIC 0x00000000BB7FA000 00008C (v02 HP     INSYDE   00000001 MSFT 01000013)[/COLOR]
[*][COLOR=#000000][    0.000000] ACPI: MCFG 0x00000000BB7F9000 00003C (v01 HP     INSYDE   00000001 MSFT 01000013)[/COLOR]
[*][COLOR=#000000][    0.000000] ACPI: SLIC 0x00000000BB7EC000 000176 (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)[/COLOR]
[*][COLOR=#000000][    0.000000] ACPI: BOOT 0x00000000BB7E8000 000028 (v01 HP     INSYDE   00000001 MSFT 01000013)[/COLOR]
[*][COLOR=#000000][    0.000000] ACPI: ASPT 0x00000000BB7E5000 000034 (v04 HP     INSYDE   00000001 MSFT 01000013)[/COLOR]
[*][COLOR=#000000][    0.000000] ACPI: WDAT 0x00000000BB7E4000 000224 (v01 HP     INSYDE   00000001 MSFT 01000013)[/COLOR]
[*][COLOR=#000000][    0.000000] ACPI: SSDT 0x00000000BB7E3000 0009F1 (v01 PmRef  CpuPm    00003000 INTL 20051117)[/COLOR]
[*][COLOR=#000000][    0.000000] ACPI: Local APIC address 0xfee00000[/COLOR]
[*][COLOR=#000000][    0.000000] No NUMA configuration found[/COLOR]
[*][COLOR=#000000][    0.000000] Faking a node at [mem 0x0000000000000000-0x0000000137ffffff][/COLOR]
[*][COLOR=#000000][    0.000000] Initmem setup node 0 [mem 0x00000000-0x137ffffff][/COLOR]
[*][COLOR=#000000][    0.000000]   NODE_DATA [mem 0x137ff8000-0x137ffcfff][/COLOR]
[*][COLOR=#000000][    0.000000]  [ffffea0000000000-ffffea0004dfffff] PMD -> [ffff880133800000-ffff8801375fffff] on node 0[/COLOR]
[*][COLOR=#000000][    0.000000] Zone ranges:[/COLOR]
[*][COLOR=#000000][    0.000000]   DMA      [mem 0x00001000-0x00ffffff][/COLOR]
[*][COLOR=#000000][    0.000000]   DMA32    [mem 0x01000000-0xffffffff][/COLOR]
[*][COLOR=#000000][    0.000000]   Normal   [mem 0x100000000-0x137ffffff][/COLOR]
[*][COLOR=#000000][    0.000000] Movable zone start for each node[/COLOR]
[*][COLOR=#000000][    0.000000] Early memory node ranges[/COLOR]
[*][COLOR=#000000][    0.000000]   node   0: [mem 0x00001000-0x0009bfff][/COLOR]
[*][COLOR=#000000][    0.000000]   node   0: [mem 0x00100000-0xbb63efff][/COLOR]
[*][COLOR=#000000][    0.000000]   node   0: [mem 0xbb7ff000-0xbb7fffff][/COLOR]
[*][COLOR=#000000][    0.000000]   node   0: [mem 0x100000000-0x137ffffff][/COLOR]
[*][COLOR=#000000][    0.000000] On node 0 totalpages: 996827[/COLOR]
[*][COLOR=#000000][    0.000000]   DMA zone: 64 pages used for memmap[/COLOR]
[*][COLOR=#000000][    0.000000]   DMA zone: 21 pages reserved[/COLOR]
[*][COLOR=#000000][    0.000000]   DMA zone: 3995 pages, LIFO batch:0[/COLOR]
[*][COLOR=#000000][    0.000000]   DMA32 zone: 11929 pages used for memmap[/COLOR]
[*][COLOR=#000000][    0.000000]   DMA32 zone: 763456 pages, LIFO batch:31[/COLOR]
[*][COLOR=#000000][    0.000000]   Normal zone: 3584 pages used for memmap[/COLOR]
[*][COLOR=#000000][    0.000000]   Normal zone: 229376 pages, LIFO batch:31[/COLOR]
[*][COLOR=#000000][    0.000000] Reserving Intel graphics stolen memory at 0xbe000000-0xbfffffff[/COLOR]
[*][COLOR=#000000][    0.000000] ACPI: PM-Timer IO Port: 0x408[/COLOR]
[*][COLOR=#000000][    0.000000] ACPI: Local APIC address 0xfee00000[/COLOR]
[*][COLOR=#000000][    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)[/COLOR]
[*][COLOR=#000000][    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)[/COLOR]
[*][COLOR=#000000][    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)[/COLOR]
[*][COLOR=#000000][    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x05] enabled)[/COLOR]
[*][COLOR=#000000][    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x00] disabled)[/COLOR]
[*][COLOR=#000000][    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x00] disabled)[/COLOR]
[*][COLOR=#000000][    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x00] disabled)[/COLOR]
[*][COLOR=#000000][    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x00] disabled)[/COLOR]
[*][COLOR=#000000][    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])[/COLOR]
[*][COLOR=#000000][    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23[/COLOR]
[*][COLOR=#000000][    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)[/COLOR]
[*][COLOR=#000000][    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)[/COLOR]
[*][COLOR=#000000][    0.000000] ACPI: IRQ0 used by override.[/COLOR]
[*][COLOR=#000000][    0.000000] ACPI: IRQ2 used by override.[/COLOR]
[*][COLOR=#000000][    0.000000] ACPI: IRQ9 used by override.[/COLOR]
[*][COLOR=#000000][    0.000000] Using ACPI (MADT) for SMP configuration information[/COLOR]
[*][COLOR=#000000][    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000[/COLOR]
[*][COLOR=#000000][    0.000000] smpboot: Allowing 8 CPUs, 4 hotplug CPUs[/COLOR]
[*][COLOR=#000000][    0.000000] nr_irqs_gsi: 40[/COLOR]
[*][COLOR=#000000][    0.000000] PM: Registered nosave memory: [mem 0x0009c000-0x0009cfff][/COLOR]
[*][COLOR=#000000][    0.000000] PM: Registered nosave memory: [mem 0x0009d000-0x0009ffff][/COLOR]
[*][COLOR=#000000][    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff][/COLOR]
[*][COLOR=#000000][    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff][/COLOR]
[*][COLOR=#000000][    0.000000] PM: Registered nosave memory: [mem 0xbb63f000-0xbb6befff][/COLOR]
[*][COLOR=#000000][    0.000000] PM: Registered nosave memory: [mem 0xbb6bf000-0xbb7befff][/COLOR]
[*][COLOR=#000000][    0.000000] PM: Registered nosave memory: [mem 0xbb7bf000-0xbb7fefff][/COLOR]
[*][COLOR=#000000][    0.000000] PM: Registered nosave memory: [mem 0xbb800000-0xbfffffff][/COLOR]
[*][COLOR=#000000][    0.000000] PM: Registered nosave memory: [mem 0xc0000000-0xdfffffff][/COLOR]
[*][COLOR=#000000][    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff][/COLOR]
[*][COLOR=#000000][    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfeafffff][/COLOR]
[*][COLOR=#000000][    0.000000] PM: Registered nosave memory: [mem 0xfeb00000-0xfeb03fff][/COLOR]
[*][COLOR=#000000][    0.000000] PM: Registered nosave memory: [mem 0xfeb04000-0xfebfffff][/COLOR]
[*][COLOR=#000000][    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff][/COLOR]
[*][COLOR=#000000][    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfed0ffff][/COLOR]
[*][COLOR=#000000][    0.000000] PM: Registered nosave memory: [mem 0xfed10000-0xfed13fff][/COLOR]
[*][COLOR=#000000][    0.000000] PM: Registered nosave memory: [mem 0xfed14000-0xfed17fff][/COLOR]
[*][COLOR=#000000][    0.000000] PM: Registered nosave memory: [mem 0xfed18000-0xfed19fff][/COLOR]
[*][COLOR=#000000][    0.000000] PM: Registered nosave memory: [mem 0xfed1a000-0xfed1afff][/COLOR]
[*][COLOR=#000000][    0.000000] PM: Registered nosave memory: [mem 0xfed1b000-0xfed1ffff][/COLOR]
[*][COLOR=#000000][    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff][/COLOR]
[*][COLOR=#000000][    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff][/COLOR]
[*][COLOR=#000000][    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xffdfffff][/COLOR]
[*][COLOR=#000000][    0.000000] PM: Registered nosave memory: [mem 0xffe00000-0xffffffff][/COLOR]
[*][COLOR=#000000][    0.000000] e820: [mem 0xc0000000-0xdfffffff] available for PCI devices[/COLOR]
[*][COLOR=#000000][    0.000000] Booting paravirtualized kernel on bare hardware[/COLOR]
[*][COLOR=#000000][    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1[/COLOR]
[*][COLOR=#000000][    0.000000] PERCPU: Embedded 29 pages/cpu @ffff880137c00000 s87360 r8192 d23232 u262144[/COLOR]
[*][COLOR=#000000][    0.000000] pcpu-alloc: s87360 r8192 d23232 u262144 alloc=1*2097152[/COLOR]
[*][COLOR=#000000][    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7[/COLOR]
[*][COLOR=#000000][    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 981229[/COLOR]
[*][COLOR=#000000][    0.000000] Policy zone: Normal[/COLOR]
[*][COLOR=#000000][    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.16.0-23-generic root=UUID=ed568bf2-afe1-4317-900a-e15d74216072 ro quiet splash vt.handoff=7[/COLOR]
[*][COLOR=#000000][    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)[/COLOR]
[*][COLOR=#000000][    0.000000] AGP: Checking aperture...[/COLOR]
[*][COLOR=#000000][    0.000000] AGP: No AGP bridge found[/COLOR]
[*][COLOR=#000000][    0.000000] Calgary: detecting Calgary via BIOS EBDA area[/COLOR]
[*][COLOR=#000000][    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing![/COLOR]
[*][COLOR=#000000][    0.000000] Memory: 3820316K/3987308K available (7731K kernel code, 1200K rwdata, 3608K rodata, 1360K init, 1308K bss, 166992K reserved)[/COLOR]
[*][COLOR=#000000][    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1[/COLOR]
[*][COLOR=#000000][    0.000000] Hierarchical RCU implementation.[/COLOR]
[*][COLOR=#000000][    0.000000]  RCU dyntick-idle grace-period acceleration is enabled.[/COLOR]
[*][COLOR=#000000][    0.000000]  RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.[/COLOR]
[*][COLOR=#000000][    0.000000]  Offload RCU callbacks from all CPUs[/COLOR]
[*][COLOR=#000000][    0.000000]  Offload RCU callbacks from CPUs: 0-7.[/COLOR]
[*][COLOR=#000000][    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=16, nr_cpu_ids=8[/COLOR]
[*][COLOR=#000000][    0.000000] NR_IRQS:16640 nr_irqs:744 16[/COLOR]
[*][COLOR=#000000][    0.000000] vt handoff: transparent VT on vt#7[/COLOR]
[*][COLOR=#000000][    0.000000] Console: colour dummy device 80x25[/COLOR]
[*][COLOR=#000000][    0.000000] console [tty0] enabled[/COLOR]
[*][COLOR=#000000][    0.000000] allocated 16252928 bytes of page_cgroup[/COLOR]
[*][COLOR=#000000][    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups[/COLOR]
[*][COLOR=#000000][    0.000000] hpet clockevent registered[/COLOR]
[*][COLOR=#000000][    0.000000] tsc: Fast TSC calibration using PIT[/COLOR]
[*][COLOR=#000000][    0.000000] tsc: Detected 2393.787 MHz processor[/COLOR]
[*][COLOR=#000000][    0.000037] Calibrating delay loop (skipped), value calculated using timer frequency.. 4787.57 BogoMIPS (lpj=9575148)[/COLOR]
[*][COLOR=#000000][    0.000041] pid_max: default: 32768 minimum: 301[/COLOR]
[*][COLOR=#000000][    0.000050] ACPI: Core revision 20140424[/COLOR]
[*][COLOR=#000000][    0.012894] ACPI: All ACPI Tables successfully acquired[/COLOR]
[*][COLOR=#000000][    0.043863] Security Framework initialized[/COLOR]
[*][COLOR=#000000][    0.043889] AppArmor: AppArmor initialized[/COLOR]
[*][COLOR=#000000][    0.043890] Yama: becoming mindful.[/COLOR]
[*][COLOR=#000000][    0.044214] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)[/COLOR]
[*][COLOR=#000000][    0.045528] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)[/COLOR]
[*][COLOR=#000000][    0.046116] Mount-cache hash table entries: 8192 (order: 4, 65536 bytes)[/COLOR]
[*][COLOR=#000000][    0.046122] Mountpoint-cache hash table entries: 8192 (order: 4, 65536 bytes)[/COLOR]
[*][COLOR=#000000][    0.046402] Initializing cgroup subsys memory[/COLOR]
[*][COLOR=#000000][    0.046429] Initializing cgroup subsys devices[/COLOR]
[*][COLOR=#000000][    0.046436] Initializing cgroup subsys freezer[/COLOR]
[*][COLOR=#000000][    0.046439] Initializing cgroup subsys net_cls[/COLOR]
[*][COLOR=#000000][    0.046444] Initializing cgroup subsys blkio[/COLOR]
[*][COLOR=#000000][    0.046448] Initializing cgroup subsys perf_event[/COLOR]
[*][COLOR=#000000][    0.046451] Initializing cgroup subsys net_prio[/COLOR]
[*][COLOR=#000000][    0.046458] Initializing cgroup subsys hugetlb[/COLOR]
[*][COLOR=#000000][    0.046482] CPU: Physical Processor ID: 0[/COLOR]
[*][COLOR=#000000][    0.046483] CPU: Processor Core ID: 0[/COLOR]
[*][COLOR=#000000][    0.046490] mce: CPU supports 9 MCE banks[/COLOR]
[*][COLOR=#000000][    0.046499] CPU0: Thermal monitoring handled by SMI[/COLOR]
[*][COLOR=#000000][    0.046510] Last level iTLB entries: 4KB 512, 2MB 7, 4MB 7[/COLOR]
[*][COLOR=#000000]Last level dTLB entries: 4KB 512, 2MB 32, 4MB 32, 1GB 0[/COLOR]
[*][COLOR=#000000]tlb_flushall_shift: 6[/COLOR]
[*][COLOR=#000000][    0.046634] Freeing SMP alternatives memory: 32K (ffffffff81e82000 - ffffffff81e8a000)[/COLOR]
[*][COLOR=#000000][    0.047932] ftrace: allocating 29288 entries in 115 pages[/COLOR]
[*][COLOR=#000000][    0.064432] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1[/COLOR]
[*][COLOR=#000000][    0.104140] smpboot: CPU0: Intel(R) Core(TM) i3 CPU       M 370  @ 2.40GHz (fam: 06, model: 25, stepping: 05)[/COLOR]
[*][COLOR=#000000][    0.211719] Performance Events: PEBS fmt1+, 16-deep LBR, Westmere events, Intel PMU driver.[/COLOR]
[*][COLOR=#000000][    0.211739] perf_event_intel: CPUID marked event: 'bus cycles' unavailable[/COLOR]
[*][COLOR=#000000][    0.211742] ... version:                3[/COLOR]
[*][COLOR=#000000][    0.211743] ... bit width:              48[/COLOR]
[*][COLOR=#000000][    0.211743] ... generic registers:      4[/COLOR]
[*][COLOR=#000000][    0.211744] ... value mask:             0000ffffffffffff[/COLOR]
[*][COLOR=#000000][    0.211745] ... max period:             000000007fffffff[/COLOR]
[*][COLOR=#000000][    0.211746] ... fixed-purpose events:   3[/COLOR]
[*][COLOR=#000000][    0.211747] ... event mask:             000000070000000f[/COLOR]
[*][COLOR=#000000][    0.213740] x86: Booting SMP configuration:[/COLOR]
[*][COLOR=#000000][    0.213743] .... node  #0, CPUs:      #1[/COLOR]
[*][COLOR=#000000][    0.224804] CPU1: Thermal monitoring handled by SMI[/COLOR]
[*][COLOR=#000000][    0.227020] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.[/COLOR]
[*][COLOR=#000000][    0.227135]  #2[/COLOR]
[*][COLOR=#000000][    0.238192] CPU2: Thermal monitoring handled by SMI[/COLOR]
[*][COLOR=#000000][    0.240412]  #3[/COLOR]
[*][COLOR=#000000][    0.251470] CPU3: Thermal monitoring handled by SMI[/COLOR]
[*][COLOR=#000000][    0.253591] x86: Booted up 1 node, 4 CPUs[/COLOR]
[*][COLOR=#000000][    0.253596] smpboot: Total of 4 processors activated (19150.29 BogoMIPS)[/COLOR]
[*][COLOR=#000000][    0.256231] devtmpfs: initialized[/COLOR]
[*][COLOR=#000000][    0.258772] evm: security.selinux[/COLOR]
[*][COLOR=#000000][    0.258774] evm: security.SMACK64[/COLOR]
[*][COLOR=#000000][    0.258774] evm: security.SMACK64EXEC[/COLOR]
[*][COLOR=#000000][    0.258775] evm: security.SMACK64TRANSMUTE[/COLOR]
[*][COLOR=#000000][    0.258776] evm: security.SMACK64MMAP[/COLOR]
[*][COLOR=#000000][    0.258777] evm: security.ima[/COLOR]
[*][COLOR=#000000][    0.258778] evm: security.capability[/COLOR]
[*][COLOR=#000000][    0.258846] PM: Registering ACPI NVS region [mem 0xbb6bf000-0xbb7befff] (1048576 bytes)[/COLOR]
[*][COLOR=#000000][    0.259940] pinctrl core: initialized pinctrl subsystem[/COLOR]
[*][COLOR=#000000][    0.260024] regulator-dummy: no parameters[/COLOR]
[*][COLOR=#000000][    0.260064] RTC time: 11:08:43, date: 01/02/15[/COLOR]
[*][COLOR=#000000][    0.260119] NET: Registered protocol family 16[/COLOR]
[*][COLOR=#000000][    0.260280] cpuidle: using governor ladder[/COLOR]
[*][COLOR=#000000][    0.260283] cpuidle: using governor menu[/COLOR]
[*][COLOR=#000000][    0.260335] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it[/COLOR]
[*][COLOR=#000000][    0.260337] ACPI: bus type PCI registered[/COLOR]
[*][COLOR=#000000][    0.260339] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5[/COLOR]
[*][COLOR=#000000][    0.260423] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)[/COLOR]
[*][COLOR=#000000][    0.260426] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820[/COLOR]
[*][COLOR=#000000][    0.260968] PCI: Using configuration type 1 for base access[/COLOR]
[*][COLOR=#000000][    0.261151] mtrr: your CPUs had inconsistent variable MTRR settings[/COLOR]
[*][COLOR=#000000][    0.261153] mtrr: probably your BIOS does not setup all CPUs.[/COLOR]
[*][COLOR=#000000][    0.261153] mtrr: corrected configuration.[/COLOR]
[*][COLOR=#000000][    0.264265] ACPI: Added _OSI(Module Device)[/COLOR]
[*][COLOR=#000000][    0.264268] ACPI: Added _OSI(Processor Device)[/COLOR]
[*][COLOR=#000000][    0.264269] ACPI: Added _OSI(3.0 _SCP Extensions)[/COLOR]
[*][COLOR=#000000][    0.264270] ACPI: Added _OSI(Processor Aggregator Device)[/COLOR]
[*][COLOR=#000000][    0.267354] ACPI: Executed 1 blocks of module-level executable AML code[/COLOR]
[*][COLOR=#000000][    0.275793] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored[/COLOR]
[*][COLOR=#000000][    0.276192] ACPI: Dynamic OEM Table Load:[/COLOR]
[*][COLOR=#000000][    0.276200] ACPI: SSDT 0xFFFF880131B21000 000432 (v01 PmRef  Cpu0Ist  00003000 INTL 20051117)[/COLOR]
[*][COLOR=#000000][    0.276747] ACPI: Dynamic OEM Table Load:[/COLOR]
[*][COLOR=#000000][    0.276754] ACPI: SSDT 0xFFFF880131B1C000 000891 (v01 PmRef  Cpu0Cst  00003001 INTL 20051117)[/COLOR]
[*][COLOR=#000000][    0.284042] ACPI: Dynamic OEM Table Load:[/COLOR]
[*][COLOR=#000000][    0.284049] ACPI: SSDT 0xFFFF880131AF9C00 000303 (v01 PmRef  ApIst    00003000 INTL 20051117)[/COLOR]
[*][COLOR=#000000][    0.287906] ACPI: Dynamic OEM Table Load:[/COLOR]
[*][COLOR=#000000][    0.287912] ACPI: SSDT 0xFFFF880131A47600 000119 (v01 PmRef  ApCst    00003000 INTL 20051117)[/COLOR]
[*][COLOR=#000000][    0.725051] ACPI: Interpreter enabled[/COLOR]
[*][COLOR=#000000][    0.725062] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20140424/hwxface-580)[/COLOR]
[*][COLOR=#000000][    0.725069] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20140424/hwxface-580)[/COLOR]
[*][COLOR=#000000][    0.725091] ACPI: (supports S0 S3 S4 S5)[/COLOR]
[*][COLOR=#000000][    0.725093] ACPI: Using IOAPIC for interrupt routing[/COLOR]
[*][COLOR=#000000][    0.725134] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug[/COLOR]
[*][COLOR=#000000][    0.778235] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])[/COLOR]
[*][COLOR=#000000][    0.778242] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI][/COLOR]
[*][COLOR=#000000][    0.778275] \_SB_.PCI0:_OSC invalid UUID[/COLOR]
[*][COLOR=#000000][    0.778276] _OSC request data:1 1f 0[/COLOR]
[*][COLOR=#000000][    0.778280] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM[/COLOR]
[*][COLOR=#000000][    0.778981] PCI host bridge to bus 0000:00[/COLOR]
[*][COLOR=#000000][    0.778985] pci_bus 0000:00: root bus resource [bus 00-fe][/COLOR]
[*][COLOR=#000000][    0.778987] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7][/COLOR]
[*][COLOR=#000000][    0.778989] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff][/COLOR]
[*][COLOR=#000000][    0.778991] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff][/COLOR]
[*][COLOR=#000000][    0.778993] pci_bus 0000:00: root bus resource [mem 0xc0000000-0xfeafffff][/COLOR]
[*][COLOR=#000000][    0.779001] pci 0000:00:00.0: [8086:0044] type 00 class 0x060000[/COLOR]
[*][COLOR=#000000][    0.779020] DMAR: Disabling batched IOTLB flush on Ironlake[/COLOR]
[*][COLOR=#000000][    0.779093] pci 0000:00:02.0: [8086:0046] type 00 class 0x030000[/COLOR]
[*][COLOR=#000000][    0.779105] pci 0000:00:02.0: reg 0x10: [mem 0xd0000000-0xd03fffff 64bit][/COLOR]
[*][COLOR=#000000][    0.779111] pci 0000:00:02.0: reg 0x18: [mem 0xc0000000-0xcfffffff 64bit pref][/COLOR]
[*][COLOR=#000000][    0.779116] pci 0000:00:02.0: reg 0x20: [io  0x4050-0x4057][/COLOR]
[*][COLOR=#000000][    0.779238] pci 0000:00:16.0: [8086:3b64] type 00 class 0x078000[/COLOR]
[*][COLOR=#000000][    0.779270] pci 0000:00:16.0: reg 0x10: [mem 0xd6404000-0xd640400f 64bit][/COLOR]
[*][COLOR=#000000][    0.779365] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold[/COLOR]
[*][COLOR=#000000][    0.779461] pci 0000:00:1a.0: [8086:3b3c] type 00 class 0x0c0320[/COLOR]
[*][COLOR=#000000][    0.779927] pci 0000:00:1a.0: reg 0x10: [mem 0xd640a000-0xd640a3ff][/COLOR]
[*][COLOR=#000000][    0.782596] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold[/COLOR]
[*][COLOR=#000000][    0.782657] pci 0000:00:1a.0: System wakeup disabled by ACPI[/COLOR]
[*][COLOR=#000000][    0.782709] pci 0000:00:1b.0: [8086:3b56] type 00 class 0x040300[/COLOR]
[*][COLOR=#000000][    0.782733] pci 0000:00:1b.0: reg 0x10: [mem 0xd6400000-0xd6403fff 64bit][/COLOR]
[*][COLOR=#000000][    0.782843] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold[/COLOR]
[*][COLOR=#000000][    0.782889] pci 0000:00:1b.0: System wakeup disabled by ACPI[/COLOR]
[*][COLOR=#000000][    0.782933] pci 0000:00:1c.0: [8086:3b42] type 01 class 0x060400[/COLOR]
[*][COLOR=#000000][    0.783039] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold[/COLOR]
[*][COLOR=#000000][    0.783085] pci 0000:00:1c.0: System wakeup disabled by ACPI[/COLOR]
[*][COLOR=#000000][    0.783129] pci 0000:00:1c.2: [8086:3b46] type 01 class 0x060400[/COLOR]
[*][COLOR=#000000][    0.783238] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold[/COLOR]
[*][COLOR=#000000][    0.783284] pci 0000:00:1c.2: System wakeup disabled by ACPI[/COLOR]
[*][COLOR=#000000][    0.783328] pci 0000:00:1c.4: [8086:3b4a] type 01 class 0x060400[/COLOR]
[*][COLOR=#000000][    0.783434] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold[/COLOR]
[*][COLOR=#000000][    0.783480] pci 0000:00:1c.4: System wakeup disabled by ACPI[/COLOR]
[*][COLOR=#000000][    0.783532] pci 0000:00:1d.0: [8086:3b34] type 00 class 0x0c0320[/COLOR]
[*][COLOR=#000000][    0.783990] pci 0000:00:1d.0: reg 0x10: [mem 0xd6409000-0xd64093ff][/COLOR]
[*][COLOR=#000000][    0.786653] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold[/COLOR]
[*][COLOR=#000000][    0.786712] pci 0000:00:1d.0: System wakeup disabled by ACPI[/COLOR]
[*][COLOR=#000000][    0.786758] pci 0000:00:1e.0: [8086:2448] type 01 class 0x060401[/COLOR]
[*][COLOR=#000000][    0.786865] pci 0000:00:1e.0: System wakeup disabled by ACPI[/COLOR]
[*][COLOR=#000000][    0.786906] pci 0000:00:1f.0: [8086:3b09] type 00 class 0x060100[/COLOR]
[*][COLOR=#000000][    0.787087] pci 0000:00:1f.2: [8086:3b29] type 00 class 0x010601[/COLOR]
[*][COLOR=#000000][    0.787114] pci 0000:00:1f.2: reg 0x10: [io  0x4048-0x404f][/COLOR]
[*][COLOR=#000000][    0.787125] pci 0000:00:1f.2: reg 0x14: [io  0x405c-0x405f][/COLOR]
[*][COLOR=#000000][    0.787136] pci 0000:00:1f.2: reg 0x18: [io  0x4040-0x4047][/COLOR]
[*][COLOR=#000000][    0.787147] pci 0000:00:1f.2: reg 0x1c: [io  0x4058-0x405b][/COLOR]
[*][COLOR=#000000][    0.787158] pci 0000:00:1f.2: reg 0x20: [io  0x4020-0x403f][/COLOR]
[*][COLOR=#000000][    0.787169] pci 0000:00:1f.2: reg 0x24: [mem 0xd6408000-0xd64087ff][/COLOR]
[*][COLOR=#000000][    0.787241] pci 0000:00:1f.2: PME# supported from D3hot[/COLOR]
[*][COLOR=#000000][    0.787318] pci 0000:00:1f.3: [8086:3b30] type 00 class 0x0c0500[/COLOR]
[*][COLOR=#000000][    0.787340] pci 0000:00:1f.3: reg 0x10: [mem 0xd6406000-0xd64060ff 64bit][/COLOR]
[*][COLOR=#000000][    0.787370] pci 0000:00:1f.3: reg 0x20: [io  0x4000-0x401f][/COLOR]
[*][COLOR=#000000][    0.787611] pci 0000:01:00.0: [10ec:8136] type 00 class 0x020000[/COLOR]
[*][COLOR=#000000][    0.787689] pci 0000:01:00.0: reg 0x10: [io  0x3000-0x30ff][/COLOR]
[*][COLOR=#000000][    0.787803] pci 0000:01:00.0: reg 0x18: [mem 0xd0404000-0xd0404fff 64bit pref][/COLOR]
[*][COLOR=#000000][    0.787873] pci 0000:01:00.0: reg 0x20: [mem 0xd0400000-0xd0403fff 64bit pref][/COLOR]
[*][COLOR=#000000][    0.788242] pci 0000:01:00.0: supports D1 D2[/COLOR]
[*][COLOR=#000000][    0.788244] pci 0000:01:00.0: PME# supported from D0 D1 D2 D3hot D3cold[/COLOR]
[*][COLOR=#000000][    0.789267] pci 0000:01:00.0: System wakeup disabled by ACPI[/COLOR]
[*][COLOR=#000000][    0.789404] pci 0000:00:1c.0: PCI bridge to [bus 01][/COLOR]
[*][COLOR=#000000][    0.789410] pci 0000:00:1c.0:   bridge window [io  0x3000-0x3fff][/COLOR]
[*][COLOR=#000000][    0.789415] pci 0000:00:1c.0:   bridge window [mem 0xd5400000-0xd63fffff][/COLOR]
[*][COLOR=#000000][    0.789423] pci 0000:00:1c.0:   bridge window [mem 0xd0400000-0xd13fffff 64bit pref][/COLOR]
[*][COLOR=#000000][    0.789530] pci 0000:02:00.0: [168c:0032] type 00 class 0x028000[/COLOR]
[*][COLOR=#000000][    0.789570] pci 0000:02:00.0: reg 0x10: [mem 0xd4400000-0xd447ffff 64bit][/COLOR]
[*][COLOR=#000000][    0.789644] pci 0000:02:00.0: reg 0x30: [mem 0xffff0000-0xffffffff pref][/COLOR]
[*][COLOR=#000000][    0.789736] pci 0000:02:00.0: supports D1 D2[/COLOR]
[*][COLOR=#000000][    0.789738] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold[/COLOR]
[*][COLOR=#000000][    0.789798] pci 0000:02:00.0: System wakeup disabled by ACPI[/COLOR]
[*][COLOR=#000000][    0.796653] pci 0000:00:1c.2: PCI bridge to [bus 02][/COLOR]
[*][COLOR=#000000][    0.796664] pci 0000:00:1c.2:   bridge window [io  0x2000-0x2fff][/COLOR]
[*][COLOR=#000000][    0.796673] pci 0000:00:1c.2:   bridge window [mem 0xd4400000-0xd53fffff][/COLOR]
[*][COLOR=#000000][    0.796686] pci 0000:00:1c.2:   bridge window [mem 0xd1400000-0xd23fffff 64bit pref][/COLOR]
[*][COLOR=#000000][    0.796861] pci 0000:03:00.0: [10ec:5209] type 00 class 0xff0000[/COLOR]
[*][COLOR=#000000][    0.796944] pci 0000:03:00.0: reg 0x10: [mem 0xd3400000-0xd3400fff][/COLOR]
[*][COLOR=#000000][    0.797494] pci 0000:03:00.0: supports D1 D2[/COLOR]
[*][COLOR=#000000][    0.797495] pci 0000:03:00.0: PME# supported from D1 D2 D3hot[/COLOR]
[*][COLOR=#000000][    0.797581] pci 0000:03:00.0: System wakeup disabled by ACPI[/COLOR]
[*][COLOR=#000000][    0.797688] pci 0000:00:1c.4: PCI bridge to [bus 03][/COLOR]
[*][COLOR=#000000][    0.797693] pci 0000:00:1c.4:   bridge window [io  0x1000-0x1fff][/COLOR]
[*][COLOR=#000000][    0.797698] pci 0000:00:1c.4:   bridge window [mem 0xd3400000-0xd43fffff][/COLOR]
[*][COLOR=#000000][    0.797706] pci 0000:00:1c.4:   bridge window [mem 0xd2400000-0xd33fffff 64bit pref][/COLOR]
[*][COLOR=#000000][    0.797790] pci 0000:00:1e.0: PCI bridge to [bus 04] (subtractive decode)[/COLOR]
[*][COLOR=#000000][    0.797803] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)[/COLOR]
[*][COLOR=#000000][    0.797805] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)[/COLOR]
[*][COLOR=#000000][    0.797807] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)[/COLOR]
[*][COLOR=#000000][    0.797809] pci 0000:00:1e.0:   bridge window [mem 0xc0000000-0xfeafffff] (subtractive decode)[/COLOR]
[*][COLOR=#000000][    0.798278] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 *10 12 14 15)[/COLOR]
[*][COLOR=#000000][    0.798329] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)[/COLOR]
[*][COLOR=#000000][    0.798379] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11[/COLOR]
[*][COLOR=#000000][    0.798428] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 *11 12 14 15)[/COLOR]
[*][COLOR=#000000][    0.798477] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.[/COLOR]
[*][COLOR=#000000][    0.798526] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *10[/COLOR]
[*][COLOR=#000000][    0.798575] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)[/COLOR]
[*][COLOR=#000000][    0.798624] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *10[/COLOR]
[*][COLOR=#000000][    0.821658] ACPI: PCI Root Bridge [CPBG] (domain 0000 [bus ff])[/COLOR]
[*][COLOR=#000000][    0.821663] acpi PNP0A03:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI][/COLOR]
[*][COLOR=#000000][    0.821667] acpi PNP0A03:00: _OSC failed (AE_NOT_FOUND); disabling ASPM[/COLOR]
[*][COLOR=#000000][    0.821738] PCI host bridge to bus 0000:ff[/COLOR]
[*][COLOR=#000000][    0.821741] pci_bus 0000:ff: root bus resource [bus ff][/COLOR]
[*][COLOR=#000000][    0.821746] pci 0000:ff:00.0: [8086:2c62] type 00 class 0x060000[/COLOR]
[*][COLOR=#000000][    0.821794] pci 0000:ff:00.1: [8086:2d01] type 00 class 0x060000[/COLOR]
[*][COLOR=#000000][    0.821842] pci 0000:ff:02.0: [8086:2d10] type 00 class 0x060000[/COLOR]
[*][COLOR=#000000][    0.821887] pci 0000:ff:02.1: [8086:2d11] type 00 class 0x060000[/COLOR]
[*][COLOR=#000000][    0.821930] pci 0000:ff:02.2: [8086:2d12] type 00 class 0x060000[/COLOR]
[*][COLOR=#000000][    0.821973] pci 0000:ff:02.3: [8086:2d13] type 00 class 0x060000[/COLOR]
[*][COLOR=#000000][    0.822084] ACPI: Enabled 6 GPEs in block 00 to 3F[/COLOR]
[*][COLOR=#000000][    0.822144] ACPI : EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62[/COLOR]
[*][COLOR=#000000][    0.822259] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none[/COLOR]
[*][COLOR=#000000][    0.822263] vgaarb: loaded[/COLOR]
[*][COLOR=#000000][    0.822264] vgaarb: bridge control possible 0000:00:02.0[/COLOR]
[*][COLOR=#000000][    0.822544] SCSI subsystem initialized[/COLOR]
[*][COLOR=#000000][    0.822594] libata version 3.00 loaded.[/COLOR]
[*][COLOR=#000000][    0.822623] ACPI: bus type USB registered[/COLOR]
[*][COLOR=#000000][    0.822644] usbcore: registered new interface driver usbfs[/COLOR]
[*][COLOR=#000000][    0.822653] usbcore: registered new interface driver hub[/COLOR]
[*][COLOR=#000000][    0.822677] usbcore: registered new device driver usb[/COLOR]
[*][COLOR=#000000][    0.822821] PCI: Using ACPI for IRQ routing[/COLOR]
[*][COLOR=#000000][    0.832703] PCI: pci_cache_line_size set to 64 bytes[/COLOR]
[*][COLOR=#000000][    0.832767] e820: reserve RAM buffer [mem 0x0009cc00-0x0009ffff][/COLOR]
[*][COLOR=#000000][    0.832768] e820: reserve RAM buffer [mem 0xbb63f000-0xbbffffff][/COLOR]
[*][COLOR=#000000][    0.832770] e820: reserve RAM buffer [mem 0xbb800000-0xbbffffff][/COLOR]
[*][COLOR=#000000][    0.832893] NetLabel: Initializing[/COLOR]
[*][COLOR=#000000][    0.832895] NetLabel:  domain hash size = 128[/COLOR]
[*][COLOR=#000000][    0.832895] NetLabel:  protocols = UNLABELED CIPSOv4[/COLOR]
[*][COLOR=#000000][    0.832910] NetLabel:  unlabeled traffic allowed by default[/COLOR]
[*][COLOR=#000000][    0.832995] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0[/COLOR]
[*][COLOR=#000000][    0.833001] hpet0: 8 comparators, 64-bit 14.318180 MHz counter[/COLOR]
[*][COLOR=#000000][    0.835049] Switched to clocksource hpet[/COLOR]
[*][COLOR=#000000][    0.841684] AppArmor: AppArmor Filesystem Enabled[/COLOR]
[*][COLOR=#000000][    0.841730] pnp: PnP ACPI init[/COLOR]
[*][COLOR=#000000][    0.841751] ACPI: bus type PNP registered[/COLOR]
[*][COLOR=#000000][    0.841901] pnp 00:00: disabling [io  0x164e-0x164f] because it overlaps 0000:00:1c.4 BAR 13 [io  0x1000-0x1fff][/COLOR]
[*][COLOR=#000000][    0.841957] system 00:00: [io  0x0680-0x069f] has been reserved[/COLOR]
[*][COLOR=#000000][    0.841959] system 00:00: [io  0x0800-0x080f] has been reserved[/COLOR]
[*][COLOR=#000000][    0.841961] system 00:00: [io  0x0810-0x0813] has been reserved[/COLOR]
[*][COLOR=#000000][    0.841964] system 00:00: [io  0xffff] has been reserved[/COLOR]
[*][COLOR=#000000][    0.841966] system 00:00: [io  0x0400-0x047f] could not be reserved[/COLOR]
[*][COLOR=#000000][    0.841968] system 00:00: [io  0x0500-0x057f] has been reserved[/COLOR]
[*][COLOR=#000000][    0.841973] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)[/COLOR]
[*][COLOR=#000000][    0.842011] pnp 00:01: Plug and Play ACPI device, IDs PNP0b00 (active)[/COLOR]
[*][COLOR=#000000][    0.842043] pnp 00:02: Plug and Play ACPI device, IDs PNP0303 (active)[/COLOR]
[*][COLOR=#000000][    0.842072] pnp 00:03: Plug and Play ACPI device, IDs SYN1e4b SYN1e00 SYN0002 PNP0f13 (active)[/COLOR]
[*][COLOR=#000000][    0.842347] system 00:04: [mem 0xfed1c000-0xfed1ffff] has been reserved[/COLOR]
[*][COLOR=#000000][    0.842350] system 00:04: [mem 0xfed10000-0xfed13fff] has been reserved[/COLOR]
[*][COLOR=#000000][    0.842352] system 00:04: [mem 0xfed18000-0xfed18fff] has been reserved[/COLOR]
[*][COLOR=#000000][    0.842354] system 00:04: [mem 0xfed19000-0xfed19fff] has been reserved[/COLOR]
[*][COLOR=#000000][    0.842356] system 00:04: [mem 0xe0000000-0xefffffff] has been reserved[/COLOR]
[*][COLOR=#000000][    0.842358] system 00:04: [mem 0xfed20000-0xfed3ffff] has been reserved[/COLOR]
[*][COLOR=#000000][    0.842361] system 00:04: [mem 0xff000000-0xffffffff] could not be reserved[/COLOR]
[*][COLOR=#000000][    0.842363] system 00:04: [mem 0xfee00000-0xfeefffff] could not be reserved[/COLOR]
[*][COLOR=#000000][    0.842366] system 00:04: [mem 0xd6500000-0xd6500fff] has been reserved[/COLOR]
[*][COLOR=#000000][    0.842368] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)[/COLOR]
[*][COLOR=#000000][    0.863772] pnp: PnP ACPI: found 5 devices[/COLOR]
[*][COLOR=#000000][    0.863774] ACPI: bus type PNP unregistered[/COLOR]
[*][COLOR=#000000][    0.871100] pci 0000:02:00.0: can't claim BAR 6 [mem 0xffff0000-0xffffffff pref]: no compatible bridge window[/COLOR]
[*][COLOR=#000000][    0.871145] pci 0000:00:1c.0: PCI bridge to [bus 01][/COLOR]
[*][COLOR=#000000][    0.871149] pci 0000:00:1c.0:   bridge window [io  0x3000-0x3fff][/COLOR]
[*][COLOR=#000000][    0.871156] pci 0000:00:1c.0:   bridge window [mem 0xd5400000-0xd63fffff][/COLOR]
[*][COLOR=#000000][    0.871161] pci 0000:00:1c.0:   bridge window [mem 0xd0400000-0xd13fffff 64bit pref][/COLOR]
[*][COLOR=#000000][    0.871172] pci 0000:02:00.0: BAR 6: assigned [mem 0xd4480000-0xd448ffff pref][/COLOR]
[*][COLOR=#000000][    0.871174] pci 0000:00:1c.2: PCI bridge to [bus 02][/COLOR]
[*][COLOR=#000000][    0.871178] pci 0000:00:1c.2:   bridge window [io  0x2000-0x2fff][/COLOR]
[*][COLOR=#000000][    0.871184] pci 0000:00:1c.2:   bridge window [mem 0xd4400000-0xd53fffff][/COLOR]
[*][COLOR=#000000][    0.871189] pci 0000:00:1c.2:   bridge window [mem 0xd1400000-0xd23fffff 64bit pref][/COLOR]
[*][COLOR=#000000][    0.871196] pci 0000:00:1c.4: PCI bridge to [bus 03][/COLOR]
[*][COLOR=#000000][    0.871200] pci 0000:00:1c.4:   bridge window [io  0x1000-0x1fff][/COLOR]
[*][COLOR=#000000][    0.871206] pci 0000:00:1c.4:   bridge window [mem 0xd3400000-0xd43fffff][/COLOR]
[*][COLOR=#000000][    0.871211] pci 0000:00:1c.4:   bridge window [mem 0xd2400000-0xd33fffff 64bit pref][/COLOR]
[*][COLOR=#000000][    0.871220] pci 0000:00:1e.0: PCI bridge to [bus 04][/COLOR]
[*][COLOR=#000000][    0.871235] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7][/COLOR]
[*][COLOR=#000000][    0.871237] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff][/COLOR]
[*][COLOR=#000000][    0.871239] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff][/COLOR]
[*][COLOR=#000000][    0.871240] pci_bus 0000:00: resource 7 [mem 0xc0000000-0xfeafffff][/COLOR]
[*][COLOR=#000000][    0.871243] pci_bus 0000:01: resource 0 [io  0x3000-0x3fff][/COLOR]
[*][COLOR=#000000][    0.871244] pci_bus 0000:01: resource 1 [mem 0xd5400000-0xd63fffff][/COLOR]
[*][COLOR=#000000][    0.871246] pci_bus 0000:01: resource 2 [mem 0xd0400000-0xd13fffff 64bit pref][/COLOR]
[*][COLOR=#000000][    0.871249] pci_bus 0000:02: resource 0 [io  0x2000-0x2fff][/COLOR]
[*][COLOR=#000000][    0.871250] pci_bus 0000:02: resource 1 [mem 0xd4400000-0xd53fffff][/COLOR]
[*][COLOR=#000000][    0.871252] pci_bus 0000:02: resource 2 [mem 0xd1400000-0xd23fffff 64bit pref][/COLOR]
[*][COLOR=#000000][    0.871254] pci_bus 0000:03: resource 0 [io  0x1000-0x1fff][/COLOR]
[*][COLOR=#000000][    0.871256] pci_bus 0000:03: resource 1 [mem 0xd3400000-0xd43fffff][/COLOR]
[*][COLOR=#000000][    0.871258] pci_bus 0000:03: resource 2 [mem 0xd2400000-0xd33fffff 64bit pref][/COLOR]
[*][COLOR=#000000][    0.871261] pci_bus 0000:04: resource 4 [io  0x0000-0x0cf7][/COLOR]
[*][COLOR=#000000][    0.871262] pci_bus 0000:04: resource 5 [io  0x0d00-0xffff][/COLOR]
[*][COLOR=#000000][    0.871264] pci_bus 0000:04: resource 6 [mem 0x000a0000-0x000bffff][/COLOR]
[*][COLOR=#000000][    0.871266] pci_bus 0000:04: resource 7 [mem 0xc0000000-0xfeafffff][/COLOR]
[*][COLOR=#000000][    0.871300] NET: Registered protocol family 2[/COLOR]
[*][COLOR=#000000][    0.871511] TCP established hash table entries: 32768 (order: 6, 262144 bytes)[/COLOR]
[*][COLOR=#000000][    0.871616] TCP bind hash table entries: 32768 (order: 7, 524288 bytes)[/COLOR]
[*][COLOR=#000000][    0.871761] TCP: Hash tables configured (established 32768 bind 32768)[/COLOR]
[*][COLOR=#000000][    0.871791] TCP: reno registered[/COLOR]
[*][COLOR=#000000][    0.871799] UDP hash table entries: 2048 (order: 4, 65536 bytes)[/COLOR]
[*][COLOR=#000000][    0.871821] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)[/COLOR]
[*][COLOR=#000000][    0.871893] NET: Registered protocol family 1[/COLOR]
[*][COLOR=#000000][    0.871910] pci 0000:00:02.0: Boot video device[/COLOR]
[*][COLOR=#000000][    0.903268] PCI: CLS 64 bytes, default 64[/COLOR]
[*][COLOR=#000000][    0.903338] Trying to unpack rootfs image as initramfs...[/COLOR]
[*][COLOR=#000000][    1.249650] Freeing initrd memory: 19928K (ffff880035904000 - ffff880036c7a000)[/COLOR]
[*][COLOR=#000000][    1.249702] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)[/COLOR]
[*][COLOR=#000000][    1.249705] software IO TLB [mem 0xb763f000-0xbb63f000] (64MB) mapped at [ffff8800b763f000-ffff8800bb63efff][/COLOR]
[*][COLOR=#000000][    1.249773] Simple Boot Flag at 0x44 set to 0x1[/COLOR]
[*][COLOR=#000000][    1.250004] microcode: CPU0 sig=0x20655, pf=0x10, revision=0x2[/COLOR]
[*][COLOR=#000000][    1.250011] microcode: CPU1 sig=0x20655, pf=0x10, revision=0x2[/COLOR]
[*][COLOR=#000000][    1.250015] microcode: CPU2 sig=0x20655, pf=0x10, revision=0x2[/COLOR]
[*][COLOR=#000000][    1.250022] microcode: CPU3 sig=0x20655, pf=0x10, revision=0x2[/COLOR]
[*][COLOR=#000000][    1.250098] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba[/COLOR]
[*][COLOR=#000000][    1.250125] Scanning for low memory corruption every 60 seconds[/COLOR]
[*][COLOR=#000000][    1.250536] futex hash table entries: 2048 (order: 5, 131072 bytes)[/COLOR]
[*][COLOR=#000000][    1.250586] Initialise system trusted keyring[/COLOR]
[*][COLOR=#000000][    1.250612] audit: initializing netlink subsys (disabled)[/COLOR]
[*][COLOR=#000000][    1.250631] audit: type=2000 audit(1420196924.108:1): initialized[/COLOR]
[*][COLOR=#000000][    1.251034] HugeTLB registered 2 MB page size, pre-allocated 0 pages[/COLOR]
[*][COLOR=#000000][    1.252564] zpool: loaded[/COLOR]
[*][COLOR=#000000][    1.252567] zbud: loaded[/COLOR]
[*][COLOR=#000000][    1.252755] VFS: Disk quotas dquot_6.5.2[/COLOR]
[*][COLOR=#000000][    1.252795] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)[/COLOR]
[*][COLOR=#000000][    1.253313] fuse init (API version 7.23)[/COLOR]
[*][COLOR=#000000][    1.253413] msgmni has been set to 7500[/COLOR]
[*][COLOR=#000000][    1.253481] Key type big_key registered[/COLOR]
[*][COLOR=#000000][    1.254017] Key type asymmetric registered[/COLOR]
[*][COLOR=#000000][    1.254022] Asymmetric key parser 'x509' registered[/COLOR]
[*][COLOR=#000000][    1.254064] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)[/COLOR]
[*][COLOR=#000000][    1.254121] io scheduler noop registered[/COLOR]
[*][COLOR=#000000][    1.254125] io scheduler deadline registered (default)[/COLOR]
[*][COLOR=#000000][    1.254177] io scheduler cfq registered[/COLOR]
[*][COLOR=#000000][    1.254752] pci_hotplug: PCI Hot Plug PCI Core version: 0.5[/COLOR]
[*][COLOR=#000000][    1.254771] pciehp: PCI Express Hot Plug Controller Driver version: 0.4[/COLOR]
[*][COLOR=#000000][    1.254821] vesafb: mode is 1024x768x32, linelength=4096, pages=0[/COLOR]
[*][COLOR=#000000][    1.254822] vesafb: scrolling: redraw[/COLOR]
[*][COLOR=#000000][    1.254824] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0[/COLOR]
[*][COLOR=#000000][    1.254843] vesafb: framebuffer at 0xc0000000, mapped to 0xffffc90010780000, using 3072k, total 3072k[/COLOR]
[*][COLOR=#000000][    1.254948] Console: switching to colour frame buffer device 128x48[/COLOR]
[*][COLOR=#000000][    1.254972] fb0: VESA VGA frame buffer device[/COLOR]
[*][COLOR=#000000][    1.254996] intel_idle: MWAIT substates: 0x1120[/COLOR]
[*][COLOR=#000000][    1.254997] intel_idle: v0.4 model 0x25[/COLOR]
[*][COLOR=#000000][    1.254999] intel_idle: lapic_timer_reliable_states 0xffffffff[/COLOR]
[*][COLOR=#000000][    1.267365] ACPI: AC Adapter [AC] (on-line)[/COLOR]
[*][COLOR=#000000][    1.267472] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0[/COLOR]
[*][COLOR=#000000][    1.283547] ACPI: Lid Switch [LID][/COLOR]
[*][COLOR=#000000][    1.283626] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1[/COLOR]
[*][COLOR=#000000][    1.283632] ACPI: Power Button [PWRB][/COLOR]
[*][COLOR=#000000][    1.283694] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2[/COLOR]
[*][COLOR=#000000][    1.283698] ACPI: Power Button [PWRF][/COLOR]
[*][COLOR=#000000][    1.363528] thermal LNXTHERM:00: registered as thermal_zone0[/COLOR]
[*][COLOR=#000000][    1.363533] ACPI: Thermal Zone [TSZ0] (56 C)[/COLOR]
[*][COLOR=#000000][    1.435567] thermal LNXTHERM:01: registered as thermal_zone1[/COLOR]
[*][COLOR=#000000][    1.435572] ACPI: Thermal Zone [TSZ1] (55 C)[/COLOR]
[*][COLOR=#000000][    1.435618] GHES: HEST is not enabled![/COLOR]
[*][COLOR=#000000][    1.435770] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled[/COLOR]
[*][COLOR=#000000][    1.438031] Linux agpgart interface v0.103[/COLOR]
[*][COLOR=#000000][    1.438093] agpgart-intel 0000:00:00.0: Intel HD Graphics Chipset[/COLOR]
[*][COLOR=#000000][    1.438113] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable[/COLOR]
[*][COLOR=#000000][    1.438687] agpgart-intel 0000:00:00.0: detected 32768K stolen memory[/COLOR]
[*][COLOR=#000000][    1.438866] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000[/COLOR]
[*][COLOR=#000000][    1.440472] brd: module loaded[/COLOR]
[*][COLOR=#000000][    1.441300] loop: module loaded[/COLOR]
[*][COLOR=#000000][    1.441547] libphy: Fixed MDIO Bus: probed[/COLOR]
[*][COLOR=#000000][    1.441550] tun: Universal TUN/TAP device driver, 1.6[/COLOR]
[*][COLOR=#000000][    1.441551] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>[/COLOR]
[*][COLOR=#000000][    1.441619] PPP generic driver version 2.4.2[/COLOR]
[*][COLOR=#000000][    1.441680] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver[/COLOR]
[*][COLOR=#000000][    1.441686] ehci-pci: EHCI PCI platform driver[/COLOR]
[*][COLOR=#000000][    1.441858] ehci-pci 0000:00:1a.0: EHCI Host Controller[/COLOR]
[*][COLOR=#000000][    1.441865] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1[/COLOR]
[*][COLOR=#000000][    1.441882] ehci-pci 0000:00:1a.0: debug port 2[/COLOR]
[*][COLOR=#000000][    1.445851] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported[/COLOR]
[*][COLOR=#000000][    1.445875] ehci-pci 0000:00:1a.0: irq 16, io mem 0xd640a000[/COLOR]
[*][COLOR=#000000][    1.455451] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00[/COLOR]
[*][COLOR=#000000][    1.455493] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002[/COLOR]
[*][COLOR=#000000][    1.455495] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1[/COLOR]
[*][COLOR=#000000][    1.455497] usb usb1: Product: EHCI Host Controller[/COLOR]
[*][COLOR=#000000][    1.455499] usb usb1: Manufacturer: Linux 3.16.0-23-generic ehci_hcd[/COLOR]
[*][COLOR=#000000][    1.455501] usb usb1: SerialNumber: 0000:00:1a.0[/COLOR]
[*][COLOR=#000000][    1.455643] hub 1-0:1.0: USB hub found[/COLOR]
[*][COLOR=#000000][    1.455651] hub 1-0:1.0: 3 ports detected[/COLOR]
[*][COLOR=#000000][    1.455873] ehci-pci 0000:00:1d.0: EHCI Host Controller[/COLOR]
[*][COLOR=#000000][    1.455881] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2[/COLOR]
[*][COLOR=#000000][    1.455895] ehci-pci 0000:00:1d.0: debug port 2[/COLOR]
[*][COLOR=#000000][    1.459849] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported[/COLOR]
[*][COLOR=#000000][    1.459868] ehci-pci 0000:00:1d.0: irq 23, io mem 0xd6409000[/COLOR]
[*][COLOR=#000000][    1.471459] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00[/COLOR]
[*][COLOR=#000000][    1.471494] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002[/COLOR]
[*][COLOR=#000000][    1.471496] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1[/COLOR]
[*][COLOR=#000000][    1.471498] usb usb2: Product: EHCI Host Controller[/COLOR]
[*][COLOR=#000000][    1.471500] usb usb2: Manufacturer: Linux 3.16.0-23-generic ehci_hcd[/COLOR]
[*][COLOR=#000000][    1.471502] usb usb2: SerialNumber: 0000:00:1d.0[/COLOR]
[*][COLOR=#000000][    1.471720] hub 2-0:1.0: USB hub found[/COLOR]
[*][COLOR=#000000][    1.471727] hub 2-0:1.0: 3 ports detected[/COLOR]
[*][COLOR=#000000][    1.471846] ehci-platform: EHCI generic platform driver[/COLOR]
[*][COLOR=#000000][    1.471856] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver[/COLOR]
[*][COLOR=#000000][    1.471861] ohci-pci: OHCI PCI platform driver[/COLOR]
[*][COLOR=#000000][    1.471872] ohci-platform: OHCI generic platform driver[/COLOR]
[*][COLOR=#000000][    1.471880] uhci_hcd: USB Universal Host Controller Interface driver[/COLOR]
[*][COLOR=#000000][    1.471947] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12[/COLOR]
[*][COLOR=#000000][    1.484366] serio: i8042 KBD port at 0x60,0x64 irq 1[/COLOR]
[*][COLOR=#000000][    1.484371] serio: i8042 AUX port at 0x60,0x64 irq 12[/COLOR]
[*][COLOR=#000000][    1.484611] mousedev: PS/2 mouse device common for all mice[/COLOR]
[*][COLOR=#000000][    1.484960] rtc_cmos 00:01: RTC can wake from S4[/COLOR]
[*][COLOR=#000000][    1.485105] rtc_cmos 00:01: rtc core: registered rtc_cmos as rtc0[/COLOR]
[*][COLOR=#000000][    1.485139] rtc_cmos 00:01: alarms up to one month, 242 bytes nvram, hpet irqs[/COLOR]
[*][COLOR=#000000][    1.485211] device-mapper: uevent: version 1.0.3[/COLOR]
[*][COLOR=#000000][    1.485293] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com[/COLOR]
[*][COLOR=#000000][    1.485367] ledtrig-cpu: registered to indicate activity on CPUs[/COLOR]
[*][COLOR=#000000][    1.485477] TCP: cubic registered[/COLOR]
[*][COLOR=#000000][    1.485597] NET: Registered protocol family 10[/COLOR]
[*][COLOR=#000000][    1.485903] NET: Registered protocol family 17[/COLOR]
[*][COLOR=#000000][    1.485916] Key type dns_resolver registered[/COLOR]
[*][COLOR=#000000][    1.486284] Loading compiled-in X.509 certificates[/COLOR]
[*][COLOR=#000000][    1.487392] Loaded X.509 cert 'Magrathea: Glacier signing key: d120c47c14beb62ead6703d41712cc110575d297'[/COLOR]
[*][COLOR=#000000][    1.487410] registered taskstats version 1[/COLOR]
[*][COLOR=#000000][    1.489820] Key type trusted registered[/COLOR]
[*][COLOR=#000000][    1.491364] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3[/COLOR]
[*][COLOR=#000000][    1.491560] Key type encrypted registered[/COLOR]
[*][COLOR=#000000][    1.493213] AppArmor: AppArmor sha1 policy hashing enabled[/COLOR]
[*][COLOR=#000000][    1.493219] ima: No TPM chip found, activating TPM-bypass![/COLOR]
[*][COLOR=#000000][    1.493246] evm: HMAC attrs: 0x1[/COLOR]
[*][COLOR=#000000][    1.493667]   Magic number: 15:347:124[/COLOR]
[*][COLOR=#000000][    1.493813] rtc_cmos 00:01: setting system clock to 2015-01-02 11:08:44 UTC (1420196924)[/COLOR]
[*][COLOR=#000000][    1.494862] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found[/COLOR]
[*][COLOR=#000000][    1.494864] EDD information not available.[/COLOR]
[*][COLOR=#000000][    1.494939] PM: Hibernation image not present or could not be loaded.[/COLOR]
[*][COLOR=#000000][    1.651727] ACPI: Battery Slot [BAT0] (battery present)[/COLOR]
[*][COLOR=#000000][    1.653296] Freeing unused kernel memory: 1360K (ffffffff81d2e000 - ffffffff81e82000)[/COLOR]
[*][COLOR=#000000][    1.653300] Write protecting the kernel read-only data: 12288k[/COLOR]
[*][COLOR=#000000][    1.654634] Freeing unused kernel memory: 448K (ffff880001790000 - ffff880001800000)[/COLOR]
[*][COLOR=#000000][    1.655906] Freeing unused kernel memory: 488K (ffff880001b86000 - ffff880001c00000)[/COLOR]
[*][COLOR=#000000][    1.671162] systemd-udevd[124]: starting version 208[/COLOR]
[*][COLOR=#000000][    1.671705] random: systemd-udevd urandom read with 8 bits of entropy available[/COLOR]
[*][COLOR=#000000][    1.709420] rtsx_pci 0000:03:00.0: irq 40 for MSI/MSI-X[/COLOR]
[*][COLOR=#000000][    1.709437] rtsx_pci 0000:03:00.0: rtsx_pci_acquire_irq: pcr->msi_en = 1, pci->irq = 40[/COLOR]
[*][COLOR=#000000][    1.712524] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded[/COLOR]
[*][COLOR=#000000][    1.712536] r8169 0000:01:00.0: can't disable ASPM; OS doesn't have ASPM control[/COLOR]
[*][COLOR=#000000][    1.712758] r8169 0000:01:00.0: irq 41 for MSI/MSI-X[/COLOR]
[*][COLOR=#000000][    1.712993] r8169 0000:01:00.0 eth0: RTL8105e at 0xffffc9000067e000, e4:11:5b:fc:b9:be, XID 00a00000 IRQ 41[/COLOR]
[*][COLOR=#000000][    1.714043] ahci 0000:00:1f.2: version 3.0[/COLOR]
[*][COLOR=#000000][    1.714190] ahci 0000:00:1f.2: irq 42 for MSI/MSI-X[/COLOR]
[*][COLOR=#000000][    1.714259] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 4 ports 3 Gbps 0x3 impl SATA mode[/COLOR]
[*][COLOR=#000000][    1.714262] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck pm led clo pio slum part ems apst[/COLOR]
[*][COLOR=#000000][    1.720602] scsi0 : ahci[/COLOR]
[*][COLOR=#000000][    1.723950] scsi1 : ahci[/COLOR]
[*][COLOR=#000000][    1.727469] scsi2 : ahci[/COLOR]
[*][COLOR=#000000][    1.733052] scsi3 : ahci[/COLOR]
[*][COLOR=#000000][    1.733169] ata1: SATA max UDMA/133 abar m2048@0xd6408000 port 0xd6408100 irq 42[/COLOR]
[*][COLOR=#000000][    1.733174] ata2: SATA max UDMA/133 abar m2048@0xd6408000 port 0xd6408180 irq 42[/COLOR]
[*][COLOR=#000000][    1.733176] ata3: DUMMY[/COLOR]
[*][COLOR=#000000][    1.733178] ata4: DUMMY[/COLOR]
[*][COLOR=#000000][    1.767883] usb 1-1: new high-speed USB device number 2 using ehci-pci[/COLOR]
[*][COLOR=#000000][    1.900533] usb 1-1: New USB device found, idVendor=8087, idProduct=0020[/COLOR]
[*][COLOR=#000000][    1.900539] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0[/COLOR]
[*][COLOR=#000000][    1.901132] hub 1-1:1.0: USB hub found[/COLOR]
[*][COLOR=#000000][    1.901312] hub 1-1:1.0: 6 ports detected[/COLOR]
[*][COLOR=#000000][    2.011899] usb 2-1: new high-speed USB device number 2 using ehci-pci[/COLOR]
[*][COLOR=#000000][    2.051916] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)[/COLOR]
[*][COLOR=#000000][    2.051956] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)[/COLOR]
[*][COLOR=#000000][    2.052335] ata1.00: supports DRM functions and may not be fully accessible[/COLOR]
[*][COLOR=#000000][    2.055299] ata1.00: disabling queued TRIM support[/COLOR]
[*][COLOR=#000000][    2.055304] ata1.00: ATA-9: Crucial_CT240M500SSD1, MU03, max UDMA/133[/COLOR]
[*][COLOR=#000000][    2.055308] ata1.00: 468862128 sectors, multi 16: LBA48 NCQ (depth 31/32), AA[/COLOR]
[*][COLOR=#000000][    2.055415] ata2.00: ATAPI: hp       CDDVDW TS-L633R, 0400, max UDMA/100[/COLOR]
[*][COLOR=#000000][    2.059042] ata1.00: supports DRM functions and may not be fully accessible[/COLOR]
[*][COLOR=#000000][    2.060093] ata2.00: configured for UDMA/100[/COLOR]
[*][COLOR=#000000][    2.062004] ata1.00: disabling queued TRIM support[/COLOR]
[*][COLOR=#000000][    2.065280] ata1.00: configured for UDMA/133[/COLOR]
[*][COLOR=#000000][    2.065529] scsi 0:0:0:0: Direct-Access     ATA      Crucial_CT240M50 MU03 PQ: 0 ANSI: 5[/COLOR]
[*][COLOR=#000000][    2.066028] sd 0:0:0:0: Attached scsi generic sg0 type 0[/COLOR]
[*][COLOR=#000000][    2.066044] sd 0:0:0:0: [sda] 468862128 512-byte logical blocks: (240 GB/223 GiB)[/COLOR]
[*][COLOR=#000000][    2.066048] sd 0:0:0:0: [sda] 4096-byte physical blocks[/COLOR]
[*][COLOR=#000000][    2.066249] sd 0:0:0:0: [sda] Write Protect is off[/COLOR]
[*][COLOR=#000000][    2.066253] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00[/COLOR]
[*][COLOR=#000000][    2.066350] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA[/COLOR]
[*][COLOR=#000000][    2.067135]  sda: sda1 sda2 sda3 sda4 < sda5 >[/COLOR]
[*][COLOR=#000000][    2.067703] sd 0:0:0:0: [sda] Attached SCSI disk[/COLOR]
[*][COLOR=#000000][    2.069211] scsi 1:0:0:0: CD-ROM            hp       CDDVDW TS-L633R  0400 PQ: 0 ANSI: 5[/COLOR]
[*][COLOR=#000000][    2.096942] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray[/COLOR]
[*][COLOR=#000000][    2.096947] cdrom: Uniform CD-ROM driver Revision: 3.20[/COLOR]
[*][COLOR=#000000][    2.097120] sr 1:0:0:0: Attached scsi CD-ROM sr0[/COLOR]
[*][COLOR=#000000][    2.097189] sr 1:0:0:0: Attached scsi generic sg1 type 5[/COLOR]
[*][COLOR=#000000][    2.136483] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)[/COLOR]
[*][COLOR=#000000][    2.144587] usb 2-1: New USB device found, idVendor=8087, idProduct=0020[/COLOR]
[*][COLOR=#000000][    2.144596] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0[/COLOR]
[*][COLOR=#000000][    2.145013] hub 2-1:1.0: USB hub found[/COLOR]
[*][COLOR=#000000][    2.145171] hub 2-1:1.0: 8 ports detected[/COLOR]
[*][COLOR=#000000][    2.224074] usb 1-1.2: new full-speed USB device number 3 using ehci-pci[/COLOR]
[*][COLOR=#000000][    2.247951] tsc: Refined TSC clocksource calibration: 2393.998 MHz[/COLOR]
[*][COLOR=#000000][    2.265746] init: plymouth-upstart-bridge main process (193) terminated with status 1[/COLOR]
[*][COLOR=#000000][    2.265766] init: plymouth-upstart-bridge main process ended, respawning[/COLOR]
[*][COLOR=#000000][    2.320848] usb 1-1.2: New USB device found, idVendor=1532, idProduct=011a[/COLOR]
[*][COLOR=#000000][    2.320854] usb 1-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0[/COLOR]
[*][COLOR=#000000][    2.320857] usb 1-1.2: Product: Razer BlackWidow Ultimate[/COLOR]
[*][COLOR=#000000][    2.320860] usb 1-1.2: Manufacturer: Razer[/COLOR]
[*][COLOR=#000000][    2.383002] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro[/COLOR]
[*][COLOR=#000000][    2.396162] usb 1-1.3: new high-speed USB device number 4 using ehci-pci[/COLOR]
[*][COLOR=#000000][    2.490841] systemd-udevd[352]: starting version 208[/COLOR]
[*][COLOR=#000000][    2.534240] usb 1-1.3: New USB device found, idVendor=05c8, idProduct=021e[/COLOR]
[*][COLOR=#000000][    2.534246] usb 1-1.3: New USB device strings: Mfr=2, Product=1, SerialNumber=3[/COLOR]
[*][COLOR=#000000][    2.534249] usb 1-1.3: Product: HP Webcam-101[/COLOR]
[*][COLOR=#000000][    2.534252] usb 1-1.3: Manufacturer: HP Webcam-101[/COLOR]
[*][COLOR=#000000][    2.534255] usb 1-1.3: SerialNumber: HP Webcam-101[/COLOR]
[*][COLOR=#000000][    2.577232] lp: driver loaded but no devices found[/COLOR]
[*][COLOR=#000000][    2.600710] ppdev: user-space parallel port driver[/COLOR]
[*][COLOR=#000000][    2.612394] usb 1-1.4: new full-speed USB device number 5 using ehci-pci[/COLOR]
[*][COLOR=#000000][    2.627202] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4[/COLOR]
[*][COLOR=#000000][    2.662423] [drm] Initialized drm 1.1.0 20060810[/COLOR]
[*][COLOR=#000000][    2.670811] ACPI Warning: SystemIO range 0x0000000000000428-0x000000000000042f conflicts with OpRegion 0x0000000000000400-0x000000000000047f (\PMIO) (20140424/utaddress-258)[/COLOR]
[*][COLOR=#000000][    2.670821] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver[/COLOR]
[*][COLOR=#000000][    2.670826] ACPI Warning: SystemIO range 0x0000000000000540-0x000000000000054f conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20140424/utaddress-258)[/COLOR]
[*][COLOR=#000000][    2.670831] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver[/COLOR]
[*][COLOR=#000000][    2.670834] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053f conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20140424/utaddress-258)[/COLOR]
[*][COLOR=#000000][    2.670839] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver[/COLOR]
[*][COLOR=#000000][    2.670840] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052f conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20140424/utaddress-258)[/COLOR]
[*][COLOR=#000000][    2.670845] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver[/COLOR]
[*][COLOR=#000000][    2.670846] lpc_ich: Resource conflict(s) found affecting gpio_ich[/COLOR]
[*][COLOR=#000000][    2.699071] media: Linux media interface: v0.10[/COLOR]
[*][COLOR=#000000][    2.701080] wmi: Mapper loaded[/COLOR]
[*][COLOR=#000000][    2.703791] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.5, id: 0x1e0b1, caps: 0xd00073/0x240000/0xa0400, board id: 1680, fw id: 706145[/COLOR]
[*][COLOR=#000000][    2.706335] usb 1-1.4: New USB device found, idVendor=0cf3, idProduct=311d[/COLOR]
[*][COLOR=#000000][    2.706339] usb 1-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=3[/COLOR]
[*][COLOR=#000000][    2.706342] usb 1-1.4: Product: Bluetooth USB Host Controller[/COLOR]
[*][COLOR=#000000][    2.706346] usb 1-1.4: Manufacturer: Atheros Communications[/COLOR]
[*][COLOR=#000000][    2.706348] usb 1-1.4: SerialNumber: Alaska Day 2006[/COLOR]
[*][COLOR=#000000][    2.708391] Linux video capture interface: v2.00[/COLOR]
[*][COLOR=#000000][    2.722599] mei_me 0000:00:16.0: irq 43 for MSI/MSI-X[/COLOR]
[*][COLOR=#000000][    2.746731] uvcvideo: Found UVC 1.00 device HP Webcam-101 (05c8:021e)[/COLOR]
[*][COLOR=#000000][    2.756411] [drm] Memory usable by graphics device = 2048M[/COLOR]
[*][COLOR=#000000][    2.756415] [drm] Replacing VGA console driver[/COLOR]
[*][COLOR=#000000][    2.756421] checking generic (c0000000 300000) vs hw (c0000000 10000000)[/COLOR]
[*][COLOR=#000000][    2.756423] fb: switching to inteldrmfb from VESA VGA[/COLOR]
[*][COLOR=#000000][    2.756562] Console: switching to colour dummy device 80x25[/COLOR]
[*][COLOR=#000000][    2.764084] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input5[/COLOR]
[*][COLOR=#000000][    2.766134] input: HP Webcam-101 as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.0/input/input6[/COLOR]
[*][COLOR=#000000][    2.766299] usbcore: registered new interface driver uvcvideo[/COLOR]
[*][COLOR=#000000][    2.766301] USB Video Class driver (1.1.1)[/COLOR]
[*][COLOR=#000000][    2.776383] usb 2-1.1: new full-speed USB device number 3 using ehci-pci[/COLOR]
[*][COLOR=#000000][    2.788376] i915 0000:00:02.0: irq 44 for MSI/MSI-X[/COLOR]
[*][COLOR=#000000][    2.788394] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).[/COLOR]
[*][COLOR=#000000][    2.788396] [drm] Driver supports precise vblank timestamp query.[/COLOR]
[*][COLOR=#000000][    2.788524] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem[/COLOR]
[*][COLOR=#000000][    2.789492] Bluetooth: Core ver 2.19[/COLOR]
[*][COLOR=#000000][    2.789522] NET: Registered protocol family 31[/COLOR]
[*][COLOR=#000000][    2.789524] Bluetooth: HCI device and connection manager initialized[/COLOR]
[*][COLOR=#000000][    2.789533] Bluetooth: HCI socket layer initialized[/COLOR]
[*][COLOR=#000000][    2.789536] Bluetooth: L2CAP socket layer initialized[/COLOR]
[*][COLOR=#000000][    2.789549] Bluetooth: SCO socket layer initialized[/COLOR]
[*][COLOR=#000000][    2.799940] Bluetooth: BNEP (Ethernet Emulation) ver 1.3[/COLOR]
[*][COLOR=#000000][    2.799944] Bluetooth: BNEP filters: protocol multicast[/COLOR]
[*][COLOR=#000000][    2.799956] Bluetooth: BNEP socket layer initialized[/COLOR]
[*][COLOR=#000000][    2.800171] Bluetooth: RFCOMM TTY layer initialized[/COLOR]
[*][COLOR=#000000][    2.800180] Bluetooth: RFCOMM socket layer initialized[/COLOR]
[*][COLOR=#000000][    2.800187] Bluetooth: RFCOMM ver 1.11[/COLOR]
[*][COLOR=#000000][    2.831257] audit: type=1400 audit(1420214925.829:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=470 comm="apparmor_parser"[/COLOR]
[*][COLOR=#000000][    2.831269] audit: type=1400 audit(1420214925.829:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=470 comm="apparmor_parser"[/COLOR]
[*][COLOR=#000000][    2.831275] audit: type=1400 audit(1420214925.829:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="third_party" pid=470 comm="apparmor_parser"[/COLOR]
[*][COLOR=#000000][    2.831823] init: avahi-cups-reload main process (479) terminated with status 1[/COLOR]
[*][COLOR=#000000][    2.875310] usb 2-1.1: New USB device found, idVendor=1532, idProduct=0037[/COLOR]
[*][COLOR=#000000][    2.875316] usb 2-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0[/COLOR]
[*][COLOR=#000000][    2.875319] usb 2-1.1: Product: Razer DeathAdder 2013[/COLOR]
[*][COLOR=#000000][    2.875322] usb 2-1.1: Manufacturer: Razer[/COLOR]
[*][COLOR=#000000][    2.892093] cfg80211: Calling CRDA to update world regulatory domain[/COLOR]
[*][COLOR=#000000][    2.919283] fbcon: inteldrmfb (fb0) is primary device[/COLOR]
[*][COLOR=#000000][    2.919325] Console: switching to colour frame buffer device 170x48[/COLOR]
[*][COLOR=#000000][    2.919377] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device[/COLOR]
[*][COLOR=#000000][    2.919380] i915 0000:00:02.0: registered panic notifier[/COLOR]
[*][COLOR=#000000][    2.922334] audit: type=1400 audit(1420214925.921:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=496 comm="apparmor_parser"[/COLOR]
[*][COLOR=#000000][    2.922346] audit: type=1400 audit(1420214925.921:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=496 comm="apparmor_parser"[/COLOR]
[*][COLOR=#000000][    2.922352] audit: type=1400 audit(1420214925.921:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=496 comm="apparmor_parser"[/COLOR]
[*][COLOR=#000000][    2.997610] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)[/COLOR]
[*][COLOR=#000000][    3.009229] hidraw: raw HID events driver (C) Jiri Kosina[/COLOR]
[*][COLOR=#000000][    3.016575] ath: phy0: ASPM enabled: 0x43[/COLOR]
[*][COLOR=#000000][    3.016580] ath: EEPROM regdomain: 0x60[/COLOR]
[*][COLOR=#000000][    3.016581] ath: EEPROM indicates we should expect a direct regpair map[/COLOR]
[*][COLOR=#000000][    3.016583] ath: Country alpha2 being used: 00[/COLOR]
[*][COLOR=#000000][    3.016584] ath: Regpair used: 0x60[/COLOR]
[*][COLOR=#000000][    3.020719] acpi device:01: registered as cooling_device4[/COLOR]
[*][COLOR=#000000][    3.020873] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input7[/COLOR]
[*][COLOR=#000000][    3.021157] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0[/COLOR]
[*][COLOR=#000000][    3.021727] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X[/COLOR]
[*][COLOR=#000000][    3.023664] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'[/COLOR]
[*][COLOR=#000000][    3.024094] ieee80211 phy0: Atheros AR9485 Rev:1 mem=0xffffc90011000000, irq=18[/COLOR]
[*][COLOR=#000000][    3.035361] usbcore: registered new interface driver usbhid[/COLOR]
[*][COLOR=#000000][    3.035366] usbhid: USB HID core driver[/COLOR]
[*][COLOR=#000000][    3.046958] sound hdaudioC0D0: autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker[/COLOR]
[*][COLOR=#000000][    3.046965] sound hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)[/COLOR]
[*][COLOR=#000000][    3.046968] sound hdaudioC0D0:    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)[/COLOR]
[*][COLOR=#000000][    3.046971] sound hdaudioC0D0:    mono: mono_out=0x0[/COLOR]
[*][COLOR=#000000][    3.046974] sound hdaudioC0D0:    inputs:[/COLOR]
[*][COLOR=#000000][    3.046977] sound hdaudioC0D0:      Mic=0x18[/COLOR]
[*][COLOR=#000000][    3.046980] sound hdaudioC0D0:      Internal Mic=0x12[/COLOR]
[*][COLOR=#000000][    3.052635] input: HDA Intel MID Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8[/COLOR]
[*][COLOR=#000000][    3.052774] input: HDA Intel MID Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9[/COLOR]
[*][COLOR=#000000][    3.082981] kvm: disabled by bios[/COLOR]
[*][COLOR=#000000][    3.232286] random: nonblocking pool is initialized[/COLOR]
[*][COLOR=#000000][    3.255154] Switched to clocksource tsc[/COLOR]
[*][COLOR=#000000][    3.270181] init: failsafe main process (552) killed by TERM signal[/COLOR]
[*][COLOR=#000000][    3.328967] input: HP WMI hotkeys as /devices/virtual/input/input10[/COLOR]
[*][COLOR=#000000][    3.370359] usbcore: registered new interface driver btusb[/COLOR]
[*][COLOR=#000000][    3.374797] usbcore: registered new interface driver ath3k[/COLOR]
[*][COLOR=#000000][    3.393879] cfg80211: World regulatory domain updated:[/COLOR]
[*][COLOR=#000000][    3.393885] cfg80211:  DFS Master region: unset[/COLOR]
[*][COLOR=#000000][    3.393888] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)[/COLOR]
[*][COLOR=#000000][    3.393892] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)[/COLOR]
[*][COLOR=#000000][    3.393895] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)[/COLOR]
[*][COLOR=#000000][    3.393898] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)[/COLOR]
[*][COLOR=#000000][    3.393901] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)[/COLOR]
[*][COLOR=#000000][    3.393904] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)[/COLOR]
[*][COLOR=#000000][    3.402915] input: Razer Razer BlackWidow Ultimate as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/0003:1532:011A.0001/input/input11[/COLOR]
[*][COLOR=#000000][    3.405177] hid-generic 0003:1532:011A.0001: input,hidraw0: USB HID v1.11 Keyboard [Razer Razer BlackWidow Ultimate] on usb-0000:00:1a.0-1.2/input0[/COLOR]
[*][COLOR=#000000][    3.407481] input: Razer Razer BlackWidow Ultimate as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.1/0003:1532:011A.0002/input/input12[/COLOR]
[*][COLOR=#000000][    3.407680] hid-generic 0003:1532:011A.0002: input,hidraw1: USB HID v1.11 Keyboard [Razer Razer BlackWidow Ultimate] on usb-0000:00:1a.0-1.2/input1[/COLOR]
[*][COLOR=#000000][    3.408910] input: Razer Razer BlackWidow Ultimate as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.2/0003:1532:011A.0003/input/input13[/COLOR]
[*][COLOR=#000000][    3.409068] hid-generic 0003:1532:011A.0003: input,hidraw2: USB HID v1.11 Mouse [Razer Razer BlackWidow Ultimate] on usb-0000:00:1a.0-1.2/input2[/COLOR]
[*][COLOR=#000000][    3.409276] input: Razer Razer DeathAdder 2013 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.0/0003:1532:0037.0004/input/input14[/COLOR]
[*][COLOR=#000000][    3.409431] hid-generic 0003:1532:0037.0004: input,hidraw3: USB HID v1.11 Mouse [Razer Razer DeathAdder 2013] on usb-0000:00:1d.0-1.1/input0[/COLOR]
[*][COLOR=#000000][    3.413188] input: Razer Razer DeathAdder 2013 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.1/0003:1532:0037.0005/input/input15[/COLOR]
[*][COLOR=#000000][    3.415599] hid-generic 0003:1532:0037.0005: input,hidraw4: USB HID v1.11 Keyboard [Razer Razer DeathAdder 2013] on usb-0000:00:1d.0-1.1/input1[/COLOR]
[*][COLOR=#000000][    3.415807] input: Razer Razer DeathAdder 2013 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.2/0003:1532:0037.0006/input/input16[/COLOR]
[*][COLOR=#000000][    3.415925] hid-generic 0003:1532:0037.0006: input,hidraw5: USB HID v1.11 Keyboard [Razer Razer DeathAdder 2013] on usb-0000:00:1d.0-1.1/input2[/COLOR]
[*][COLOR=#000000][    3.424056] ACPI Error: Field [B128] at 1152 exceeds Buffer [NULL] size 160 (bits) (20140424/dsopcode-236)[/COLOR]
[*][COLOR=#000000][    3.424066] ACPI Error: Method parse/execution failed [\_SB_.WMID.HWCD] (Node ffff88013343de88), AE_AML_BUFFER_LIMIT (20140424/psparse-536)[/COLOR]
[*][COLOR=#000000][    3.424079] ACPI Error: Method parse/execution failed [\_SB_.WMID.WMAD] (Node ffff88013343e4b0), AE_AML_BUFFER_LIMIT (20140424/psparse-536)[/COLOR]
[*][COLOR=#000000][    3.448977] ACPI Error: Field [B128] at 1152 exceeds Buffer [NULL] size 160 (bits) (20140424/dsopcode-236)[/COLOR]
[*][COLOR=#000000][    3.448988] ACPI Error: Method parse/execution failed [\_SB_.WMID.HWCD] (Node ffff88013343de88), AE_AML_BUFFER_LIMIT (20140424/psparse-536)[/COLOR]
[*][COLOR=#000000][    3.449002] ACPI Error: Method parse/execution failed [\_SB_.WMID.WMAD] (Node ffff88013343e4b0), AE_AML_BUFFER_LIMIT (20140424/psparse-536)[/COLOR]
[*][COLOR=#000000][    3.543415] audit: type=1400 audit(1420214926.544:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cups-browsed" pid=743 comm="apparmor_parser"[/COLOR]
[*][COLOR=#000000][    3.575084] audit: type=1400 audit(1420214926.576:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=756 comm="apparmor_parser"[/COLOR]
[*][COLOR=#000000][    3.575095] audit: type=1400 audit(1420214926.576:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=756 comm="apparmor_parser"[/COLOR]
[*][COLOR=#000000][    3.682283] systemd-logind[763]: New seat seat0.[/COLOR]
[*][COLOR=#000000][    3.689155] systemd-logind[763]: Watching system buttons on /dev/input/event2 (Power Button)[/COLOR]
[*][COLOR=#000000][    3.689259] systemd-logind[763]: Watching system buttons on /dev/input/event6 (Video Bus)[/COLOR]
[*][COLOR=#000000][    3.689366] systemd-logind[763]: Watching system buttons on /dev/input/event1 (Power Button)[/COLOR]
[*][COLOR=#000000][    3.689469] systemd-logind[763]: Watching system buttons on /dev/input/event0 (Lid Switch)[/COLOR]
[*][COLOR=#000000][    3.892085] r8169 0000:01:00.0 eth0: link down[/COLOR]
[*][COLOR=#000000][    3.892180] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready[/COLOR]
[*][COLOR=#000000][    3.916766] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready[/COLOR]
[/LIST]

```















Raw Paste Data

```
[    0.000000] Initializing cgroup subsys cpuset[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.16.0-23-generic (buildd@phianna) (gcc version 4.9.1 (Ubuntu 4.9.1-16ubuntu6) ) #31-Ubuntu SMP Tue Oct 21 17:56:17 UTC 2014 (Ubuntu 3.16.0-23.31-generic 3.16.4)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.16.0-23-generic root=UUID=ed568bf2-afe1-4317-900a-e15d74216072 ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009cbff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009cc00-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000bb63efff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bb63f000-0x00000000bb6befff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000bb6bf000-0x00000000bb7befff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bb7bf000-0x00000000bb7fefff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000bb7ff000-0x00000000bb7fffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bb800000-0x00000000bfffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000feb00000-0x00000000feb03fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed10000-0x00000000fed13fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed18000-0x00000000fed19fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1b000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffe00000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x0000000137ffffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.6 present.
[    0.000000] DMI: Hewlett-Packard HP 2000 Notebook PC             /3674, BIOS F.24 09/22/2011
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] AGP: No AGP bridge found
[    0.000000] e820: last_pfn = 0x138000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-combining
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 0FFE00000 mask FFFE00000 write-protect
[    0.000000]   2 base 080000000 mask FC0000000 write-back
[    0.000000]   3 base 0BC000000 mask FFC000000 uncachable
[    0.000000]   4 base 0BB800000 mask FFF800000 uncachable
[    0.000000]   5 base 100000000 mask FC0000000 write-back
[    0.000000]   6 base 138000000 mask FF8000000 uncachable
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820: last_pfn = 0xbb800 max_arch_pfn = 0x400000000
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000096000] 96000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01fd3000, 0x01fd3fff] PGTABLE
[    0.000000] BRK [0x01fd4000, 0x01fd4fff] PGTABLE
[    0.000000] BRK [0x01fd5000, 0x01fd5fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x137e00000-0x137ffffff]
[    0.000000]  [mem 0x137e00000-0x137ffffff] page 2M
[    0.000000] BRK [0x01fd6000, 0x01fd6fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x134000000-0x137dfffff]
[    0.000000]  [mem 0x134000000-0x137dfffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x100000000-0x133ffffff]
[    0.000000]  [mem 0x100000000-0x133ffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0xbb63efff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0xbb5fffff] page 2M
[    0.000000]  [mem 0xbb600000-0xbb63efff] page 4k
[    0.000000] init_memory_mapping: [mem 0xbb7ff000-0xbb7fffff]
[    0.000000]  [mem 0xbb7ff000-0xbb7fffff] page 4k
[    0.000000] RAMDISK: [mem 0x35904000-0x36c79fff]
[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x00000000000FE020 000024 (v02 HPQOEM)
[    0.000000] ACPI: XSDT 0x00000000BB7FE120 000074 (v01 HPQOEM SLIC-MPC 00000001      01000013)
[    0.000000] ACPI: FACP 0x00000000BB7FC000 0000F4 (v04 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: DSDT 0x00000000BB7ED000 00BEC7 (v02 HP     INSYDE   00000001 MSFT 01000013)
[    0.000000] ACPI: FACS 0x00000000BB76D000 000040
[    0.000000] ACPI: ASF! 0x00000000BB7FD000 0000A5 (v32 HP     INSYDE   00000001 MSFT 01000013)
[    0.000000] ACPI: HPET 0x00000000BB7FB000 000038 (v01 HP     INSYDE   00000001 MSFT 01000013)
[    0.000000] ACPI: APIC 0x00000000BB7FA000 00008C (v02 HP     INSYDE   00000001 MSFT 01000013)
[    0.000000] ACPI: MCFG 0x00000000BB7F9000 00003C (v01 HP     INSYDE   00000001 MSFT 01000013)
[    0.000000] ACPI: SLIC 0x00000000BB7EC000 000176 (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: BOOT 0x00000000BB7E8000 000028 (v01 HP     INSYDE   00000001 MSFT 01000013)
[    0.000000] ACPI: ASPT 0x00000000BB7E5000 000034 (v04 HP     INSYDE   00000001 MSFT 01000013)
[    0.000000] ACPI: WDAT 0x00000000BB7E4000 000224 (v01 HP     INSYDE   00000001 MSFT 01000013)
[    0.000000] ACPI: SSDT 0x00000000BB7E3000 0009F1 (v01 PmRef  CpuPm    00003000 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x0000000137ffffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x137ffffff]
[    0.000000]   NODE_DATA [mem 0x137ff8000-0x137ffcfff]
[    0.000000]  [ffffea0000000000-ffffea0004dfffff] PMD -> [ffff880133800000-ffff8801375fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x137ffffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009bfff]
[    0.000000]   node   0: [mem 0x00100000-0xbb63efff]
[    0.000000]   node   0: [mem 0xbb7ff000-0xbb7fffff]
[    0.000000]   node   0: [mem 0x100000000-0x137ffffff]
[    0.000000] On node 0 totalpages: 996827
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3995 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 11929 pages used for memmap
[    0.000000]   DMA32 zone: 763456 pages, LIFO batch:31
[    0.000000]   Normal zone: 3584 pages used for memmap
[    0.000000]   Normal zone: 229376 pages, LIFO batch:31
[    0.000000] Reserving Intel graphics stolen memory at 0xbe000000-0xbfffffff
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x00] disabled)
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
[    0.000000] PM: Registered nosave memory: [mem 0x0009c000-0x0009cfff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009d000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xbb63f000-0xbb6befff]
[    0.000000] PM: Registered nosave memory: [mem 0xbb6bf000-0xbb7befff]
[    0.000000] PM: Registered nosave memory: [mem 0xbb7bf000-0xbb7fefff]
[    0.000000] PM: Registered nosave memory: [mem 0xbb800000-0xbfffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xc0000000-0xdfffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfeafffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfeb00000-0xfeb03fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfeb04000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfed0ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed10000-0xfed13fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed14000-0xfed17fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed18000-0xfed19fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1a000-0xfed1afff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1b000-0xfed1ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xffdfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xffe00000-0xffffffff]
[    0.000000] e820: [mem 0xc0000000-0xdfffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 29 pages/cpu @ffff880137c00000 s87360 r8192 d23232 u262144
[    0.000000] pcpu-alloc: s87360 r8192 d23232 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 981229
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.16.0-23-generic root=UUID=ed568bf2-afe1-4317-900a-e15d74216072 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] AGP: Checking aperture...
[    0.000000] AGP: No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 3820316K/3987308K available (7731K kernel code, 1200K rwdata, 3608K rodata, 1360K init, 1308K bss, 166992K reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000]     Offload RCU callbacks from all CPUs
[    0.000000]     Offload RCU callbacks from CPUs: 0-7.
[    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=16, nr_cpu_ids=8
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 16252928 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 2393.787 MHz processor
[    0.000037] Calibrating delay loop (skipped), value calculated using timer frequency.. 4787.57 BogoMIPS (lpj=9575148)
[    0.000041] pid_max: default: 32768 minimum: 301
[    0.000050] ACPI: Core revision 20140424
[    0.012894] ACPI: All ACPI Tables successfully acquired
[    0.043863] Security Framework initialized
[    0.043889] AppArmor: AppArmor initialized
[    0.043890] Yama: becoming mindful.
[    0.044214] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.045528] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.046116] Mount-cache hash table entries: 8192 (order: 4, 65536 bytes)
[    0.046122] Mountpoint-cache hash table entries: 8192 (order: 4, 65536 bytes)
[    0.046402] Initializing cgroup subsys memory
[    0.046429] Initializing cgroup subsys devices
[    0.046436] Initializing cgroup subsys freezer
[    0.046439] Initializing cgroup subsys net_cls
[    0.046444] Initializing cgroup subsys blkio
[    0.046448] Initializing cgroup subsys perf_event
[    0.046451] Initializing cgroup subsys net_prio
[    0.046458] Initializing cgroup subsys hugetlb
[    0.046482] CPU: Physical Processor ID: 0
[    0.046483] CPU: Processor Core ID: 0
[    0.046490] mce: CPU supports 9 MCE banks
[    0.046499] CPU0: Thermal monitoring handled by SMI
[    0.046510] Last level iTLB entries: 4KB 512, 2MB 7, 4MB 7
Last level dTLB entries: 4KB 512, 2MB 32, 4MB 32, 1GB 0
tlb_flushall_shift: 6
[    0.046634] Freeing SMP alternatives memory: 32K (ffffffff81e82000 - ffffffff81e8a000)
[    0.047932] ftrace: allocating 29288 entries in 115 pages
[    0.064432] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.104140] smpboot: CPU0: Intel(R) Core(TM) i3 CPU       M 370  @ 2.40GHz (fam: 06, model: 25, stepping: 05)
[    0.211719] Performance Events: PEBS fmt1+, 16-deep LBR, Westmere events, Intel PMU driver.
[    0.211739] perf_event_intel: CPUID marked event: 'bus cycles' unavailable
[    0.211742] ... version:                3
[    0.211743] ... bit width:              48
[    0.211743] ... generic registers:      4
[    0.211744] ... value mask:             0000ffffffffffff
[    0.211745] ... max period:             000000007fffffff
[    0.211746] ... fixed-purpose events:   3
[    0.211747] ... event mask:             000000070000000f
[    0.213740] x86: Booting SMP configuration:
[    0.213743] .... node  #0, CPUs:      #1
[    0.224804] CPU1: Thermal monitoring handled by SMI
[    0.227020] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.227135]  #2
[    0.238192] CPU2: Thermal monitoring handled by SMI
[    0.240412]  #3
[    0.251470] CPU3: Thermal monitoring handled by SMI
[    0.253591] x86: Booted up 1 node, 4 CPUs
[    0.253596] smpboot: Total of 4 processors activated (19150.29 BogoMIPS)
[    0.256231] devtmpfs: initialized
[    0.258772] evm: security.selinux
[    0.258774] evm: security.SMACK64
[    0.258774] evm: security.SMACK64EXEC
[    0.258775] evm: security.SMACK64TRANSMUTE
[    0.258776] evm: security.SMACK64MMAP
[    0.258777] evm: security.ima
[    0.258778] evm: security.capability
[    0.258846] PM: Registering ACPI NVS region [mem 0xbb6bf000-0xbb7befff] (1048576 bytes)
[    0.259940] pinctrl core: initialized pinctrl subsystem
[    0.260024] regulator-dummy: no parameters
[    0.260064] RTC time: 11:08:43, date: 01/02/15
[    0.260119] NET: Registered protocol family 16
[    0.260280] cpuidle: using governor ladder
[    0.260283] cpuidle: using governor menu
[    0.260335] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.260337] ACPI: bus type PCI registered
[    0.260339] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.260423] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.260426] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.260968] PCI: Using configuration type 1 for base access
[    0.261151] mtrr: your CPUs had inconsistent variable MTRR settings
[    0.261153] mtrr: probably your BIOS does not setup all CPUs.
[    0.261153] mtrr: corrected configuration.
[    0.264265] ACPI: Added _OSI(Module Device)
[    0.264268] ACPI: Added _OSI(Processor Device)
[    0.264269] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.264270] ACPI: Added _OSI(Processor Aggregator Device)
[    0.267354] ACPI: Executed 1 blocks of module-level executable AML code
[    0.275793] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.276192] ACPI: Dynamic OEM Table Load:
[    0.276200] ACPI: SSDT 0xFFFF880131B21000 000432 (v01 PmRef  Cpu0Ist  00003000 INTL 20051117)
[    0.276747] ACPI: Dynamic OEM Table Load:
[    0.276754] ACPI: SSDT 0xFFFF880131B1C000 000891 (v01 PmRef  Cpu0Cst  00003001 INTL 20051117)
[    0.284042] ACPI: Dynamic OEM Table Load:
[    0.284049] ACPI: SSDT 0xFFFF880131AF9C00 000303 (v01 PmRef  ApIst    00003000 INTL 20051117)
[    0.287906] ACPI: Dynamic OEM Table Load:
[    0.287912] ACPI: SSDT 0xFFFF880131A47600 000119 (v01 PmRef  ApCst    00003000 INTL 20051117)
[    0.725051] ACPI: Interpreter enabled
[    0.725062] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20140424/hwxface-580)
[    0.725069] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20140424/hwxface-580)
[    0.725091] ACPI: (supports S0 S3 S4 S5)
[    0.725093] ACPI: Using IOAPIC for interrupt routing
[    0.725134] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.778235] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[    0.778242] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.778275] \_SB_.PCI0:_OSC invalid UUID
[    0.778276] _OSC request data:1 1f 0 
[    0.778280] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM
[    0.778981] PCI host bridge to bus 0000:00
[    0.778985] pci_bus 0000:00: root bus resource [bus 00-fe]
[    0.778987] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.778989] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.778991] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.778993] pci_bus 0000:00: root bus resource [mem 0xc0000000-0xfeafffff]
[    0.779001] pci 0000:00:00.0: [8086:0044] type 00 class 0x060000
[    0.779020] DMAR: Disabling batched IOTLB flush on Ironlake
[    0.779093] pci 0000:00:02.0: [8086:0046] type 00 class 0x030000
[    0.779105] pci 0000:00:02.0: reg 0x10: [mem 0xd0000000-0xd03fffff 64bit]
[    0.779111] pci 0000:00:02.0: reg 0x18: [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.779116] pci 0000:00:02.0: reg 0x20: [io  0x4050-0x4057]
[    0.779238] pci 0000:00:16.0: [8086:3b64] type 00 class 0x078000
[    0.779270] pci 0000:00:16.0: reg 0x10: [mem 0xd6404000-0xd640400f 64bit]
[    0.779365] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.779461] pci 0000:00:1a.0: [8086:3b3c] type 00 class 0x0c0320
[    0.779927] pci 0000:00:1a.0: reg 0x10: [mem 0xd640a000-0xd640a3ff]
[    0.782596] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.782657] pci 0000:00:1a.0: System wakeup disabled by ACPI
[    0.782709] pci 0000:00:1b.0: [8086:3b56] type 00 class 0x040300
[    0.782733] pci 0000:00:1b.0: reg 0x10: [mem 0xd6400000-0xd6403fff 64bit]
[    0.782843] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.782889] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    0.782933] pci 0000:00:1c.0: [8086:3b42] type 01 class 0x060400
[    0.783039] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.783085] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.783129] pci 0000:00:1c.2: [8086:3b46] type 01 class 0x060400
[    0.783238] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.783284] pci 0000:00:1c.2: System wakeup disabled by ACPI
[    0.783328] pci 0000:00:1c.4: [8086:3b4a] type 01 class 0x060400
[    0.783434] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.783480] pci 0000:00:1c.4: System wakeup disabled by ACPI
[    0.783532] pci 0000:00:1d.0: [8086:3b34] type 00 class 0x0c0320
[    0.783990] pci 0000:00:1d.0: reg 0x10: [mem 0xd6409000-0xd64093ff]
[    0.786653] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.786712] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.786758] pci 0000:00:1e.0: [8086:2448] type 01 class 0x060401
[    0.786865] pci 0000:00:1e.0: System wakeup disabled by ACPI
[    0.786906] pci 0000:00:1f.0: [8086:3b09] type 00 class 0x060100
[    0.787087] pci 0000:00:1f.2: [8086:3b29] type 00 class 0x010601
[    0.787114] pci 0000:00:1f.2: reg 0x10: [io  0x4048-0x404f]
[    0.787125] pci 0000:00:1f.2: reg 0x14: [io  0x405c-0x405f]
[    0.787136] pci 0000:00:1f.2: reg 0x18: [io  0x4040-0x4047]
[    0.787147] pci 0000:00:1f.2: reg 0x1c: [io  0x4058-0x405b]
[    0.787158] pci 0000:00:1f.2: reg 0x20: [io  0x4020-0x403f]
[    0.787169] pci 0000:00:1f.2: reg 0x24: [mem 0xd6408000-0xd64087ff]
[    0.787241] pci 0000:00:1f.2: PME# supported from D3hot
[    0.787318] pci 0000:00:1f.3: [8086:3b30] type 00 class 0x0c0500
[    0.787340] pci 0000:00:1f.3: reg 0x10: [mem 0xd6406000-0xd64060ff 64bit]
[    0.787370] pci 0000:00:1f.3: reg 0x20: [io  0x4000-0x401f]
[    0.787611] pci 0000:01:00.0: [10ec:8136] type 00 class 0x020000
[    0.787689] pci 0000:01:00.0: reg 0x10: [io  0x3000-0x30ff]
[    0.787803] pci 0000:01:00.0: reg 0x18: [mem 0xd0404000-0xd0404fff 64bit pref]
[    0.787873] pci 0000:01:00.0: reg 0x20: [mem 0xd0400000-0xd0403fff 64bit pref]
[    0.788242] pci 0000:01:00.0: supports D1 D2
[    0.788244] pci 0000:01:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.789267] pci 0000:01:00.0: System wakeup disabled by ACPI
[    0.789404] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    0.789410] pci 0000:00:1c.0:   bridge window [io  0x3000-0x3fff]
[    0.789415] pci 0000:00:1c.0:   bridge window [mem 0xd5400000-0xd63fffff]
[    0.789423] pci 0000:00:1c.0:   bridge window [mem 0xd0400000-0xd13fffff 64bit pref]
[    0.789530] pci 0000:02:00.0: [168c:0032] type 00 class 0x028000
[    0.789570] pci 0000:02:00.0: reg 0x10: [mem 0xd4400000-0xd447ffff 64bit]
[    0.789644] pci 0000:02:00.0: reg 0x30: [mem 0xffff0000-0xffffffff pref]
[    0.789736] pci 0000:02:00.0: supports D1 D2
[    0.789738] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.789798] pci 0000:02:00.0: System wakeup disabled by ACPI
[    0.796653] pci 0000:00:1c.2: PCI bridge to [bus 02]
[    0.796664] pci 0000:00:1c.2:   bridge window [io  0x2000-0x2fff]
[    0.796673] pci 0000:00:1c.2:   bridge window [mem 0xd4400000-0xd53fffff]
[    0.796686] pci 0000:00:1c.2:   bridge window [mem 0xd1400000-0xd23fffff 64bit pref]
[    0.796861] pci 0000:03:00.0: [10ec:5209] type 00 class 0xff0000
[    0.796944] pci 0000:03:00.0: reg 0x10: [mem 0xd3400000-0xd3400fff]
[    0.797494] pci 0000:03:00.0: supports D1 D2
[    0.797495] pci 0000:03:00.0: PME# supported from D1 D2 D3hot
[    0.797581] pci 0000:03:00.0: System wakeup disabled by ACPI
[    0.797688] pci 0000:00:1c.4: PCI bridge to [bus 03]
[    0.797693] pci 0000:00:1c.4:   bridge window [io  0x1000-0x1fff]
[    0.797698] pci 0000:00:1c.4:   bridge window [mem 0xd3400000-0xd43fffff]
[    0.797706] pci 0000:00:1c.4:   bridge window [mem 0xd2400000-0xd33fffff 64bit pref]
[    0.797790] pci 0000:00:1e.0: PCI bridge to [bus 04] (subtractive decode)
[    0.797803] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.797805] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.797807] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.797809] pci 0000:00:1e.0:   bridge window [mem 0xc0000000-0xfeafffff] (subtractive decode)
[    0.798278] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.798329] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.798379] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.798428] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.798477] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.798526] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.798575] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.798624] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.821658] ACPI: PCI Root Bridge [CPBG] (domain 0000 [bus ff])
[    0.821663] acpi PNP0A03:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.821667] acpi PNP0A03:00: _OSC failed (AE_NOT_FOUND); disabling ASPM
[    0.821738] PCI host bridge to bus 0000:ff
[    0.821741] pci_bus 0000:ff: root bus resource [bus ff]
[    0.821746] pci 0000:ff:00.0: [8086:2c62] type 00 class 0x060000
[    0.821794] pci 0000:ff:00.1: [8086:2d01] type 00 class 0x060000
[    0.821842] pci 0000:ff:02.0: [8086:2d10] type 00 class 0x060000
[    0.821887] pci 0000:ff:02.1: [8086:2d11] type 00 class 0x060000
[    0.821930] pci 0000:ff:02.2: [8086:2d12] type 00 class 0x060000
[    0.821973] pci 0000:ff:02.3: [8086:2d13] type 00 class 0x060000
[    0.822084] ACPI: Enabled 6 GPEs in block 00 to 3F
[    0.822144] ACPI : EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.822259] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.822263] vgaarb: loaded
[    0.822264] vgaarb: bridge control possible 0000:00:02.0
[    0.822544] SCSI subsystem initialized
[    0.822594] libata version 3.00 loaded.
[    0.822623] ACPI: bus type USB registered
[    0.822644] usbcore: registered new interface driver usbfs
[    0.822653] usbcore: registered new interface driver hub
[    0.822677] usbcore: registered new device driver usb
[    0.822821] PCI: Using ACPI for IRQ routing
[    0.832703] PCI: pci_cache_line_size set to 64 bytes
[    0.832767] e820: reserve RAM buffer [mem 0x0009cc00-0x0009ffff]
[    0.832768] e820: reserve RAM buffer [mem 0xbb63f000-0xbbffffff]
[    0.832770] e820: reserve RAM buffer [mem 0xbb800000-0xbbffffff]
[    0.832893] NetLabel: Initializing
[    0.832895] NetLabel:  domain hash size = 128
[    0.832895] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.832910] NetLabel:  unlabeled traffic allowed by default
[    0.832995] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.833001] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.835049] Switched to clocksource hpet
[    0.841684] AppArmor: AppArmor Filesystem Enabled
[    0.841730] pnp: PnP ACPI init
[    0.841751] ACPI: bus type PNP registered
[    0.841901] pnp 00:00: disabling [io  0x164e-0x164f] because it overlaps 0000:00:1c.4 BAR 13 [io  0x1000-0x1fff]
[    0.841957] system 00:00: [io  0x0680-0x069f] has been reserved
[    0.841959] system 00:00: [io  0x0800-0x080f] has been reserved
[    0.841961] system 00:00: [io  0x0810-0x0813] has been reserved
[    0.841964] system 00:00: [io  0xffff] has been reserved
[    0.841966] system 00:00: [io  0x0400-0x047f] could not be reserved
[    0.841968] system 00:00: [io  0x0500-0x057f] has been reserved
[    0.841973] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.842011] pnp 00:01: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.842043] pnp 00:02: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.842072] pnp 00:03: Plug and Play ACPI device, IDs SYN1e4b SYN1e00 SYN0002 PNP0f13 (active)
[    0.842347] system 00:04: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.842350] system 00:04: [mem 0xfed10000-0xfed13fff] has been reserved
[    0.842352] system 00:04: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.842354] system 00:04: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.842356] system 00:04: [mem 0xe0000000-0xefffffff] has been reserved
[    0.842358] system 00:04: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.842361] system 00:04: [mem 0xff000000-0xffffffff] could not be reserved
[    0.842363] system 00:04: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.842366] system 00:04: [mem 0xd6500000-0xd6500fff] has been reserved
[    0.842368] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.863772] pnp: PnP ACPI: found 5 devices
[    0.863774] ACPI: bus type PNP unregistered
[    0.871100] pci 0000:02:00.0: can't claim BAR 6 [mem 0xffff0000-0xffffffff pref]: no compatible bridge window
[    0.871145] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    0.871149] pci 0000:00:1c.0:   bridge window [io  0x3000-0x3fff]
[    0.871156] pci 0000:00:1c.0:   bridge window [mem 0xd5400000-0xd63fffff]
[    0.871161] pci 0000:00:1c.0:   bridge window [mem 0xd0400000-0xd13fffff 64bit pref]
[    0.871172] pci 0000:02:00.0: BAR 6: assigned [mem 0xd4480000-0xd448ffff pref]
[    0.871174] pci 0000:00:1c.2: PCI bridge to [bus 02]
[    0.871178] pci 0000:00:1c.2:   bridge window [io  0x2000-0x2fff]
[    0.871184] pci 0000:00:1c.2:   bridge window [mem 0xd4400000-0xd53fffff]
[    0.871189] pci 0000:00:1c.2:   bridge window [mem 0xd1400000-0xd23fffff 64bit pref]
[    0.871196] pci 0000:00:1c.4: PCI bridge to [bus 03]
[    0.871200] pci 0000:00:1c.4:   bridge window [io  0x1000-0x1fff]
[    0.871206] pci 0000:00:1c.4:   bridge window [mem 0xd3400000-0xd43fffff]
[    0.871211] pci 0000:00:1c.4:   bridge window [mem 0xd2400000-0xd33fffff 64bit pref]
[    0.871220] pci 0000:00:1e.0: PCI bridge to [bus 04]
[    0.871235] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.871237] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.871239] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.871240] pci_bus 0000:00: resource 7 [mem 0xc0000000-0xfeafffff]
[    0.871243] pci_bus 0000:01: resource 0 [io  0x3000-0x3fff]
[    0.871244] pci_bus 0000:01: resource 1 [mem 0xd5400000-0xd63fffff]
[    0.871246] pci_bus 0000:01: resource 2 [mem 0xd0400000-0xd13fffff 64bit pref]
[    0.871249] pci_bus 0000:02: resource 0 [io  0x2000-0x2fff]
[    0.871250] pci_bus 0000:02: resource 1 [mem 0xd4400000-0xd53fffff]
[    0.871252] pci_bus 0000:02: resource 2 [mem 0xd1400000-0xd23fffff 64bit pref]
[    0.871254] pci_bus 0000:03: resource 0 [io  0x1000-0x1fff]
[    0.871256] pci_bus 0000:03: resource 1 [mem 0xd3400000-0xd43fffff]
[    0.871258] pci_bus 0000:03: resource 2 [mem 0xd2400000-0xd33fffff 64bit pref]
[    0.871261] pci_bus 0000:04: resource 4 [io  0x0000-0x0cf7]
[    0.871262] pci_bus 0000:04: resource 5 [io  0x0d00-0xffff]
[    0.871264] pci_bus 0000:04: resource 6 [mem 0x000a0000-0x000bffff]
[    0.871266] pci_bus 0000:04: resource 7 [mem 0xc0000000-0xfeafffff]
[    0.871300] NET: Registered protocol family 2
[    0.871511] TCP established hash table entries: 32768 (order: 6, 262144 bytes)
[    0.871616] TCP bind hash table entries: 32768 (order: 7, 524288 bytes)
[    0.871761] TCP: Hash tables configured (established 32768 bind 32768)
[    0.871791] TCP: reno registered
[    0.871799] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.871821] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.871893] NET: Registered protocol family 1
[    0.871910] pci 0000:00:02.0: Boot video device
[    0.903268] PCI: CLS 64 bytes, default 64
[    0.903338] Trying to unpack rootfs image as initramfs...
[    1.249650] Freeing initrd memory: 19928K (ffff880035904000 - ffff880036c7a000)
[    1.249702] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    1.249705] software IO TLB [mem 0xb763f000-0xbb63f000] (64MB) mapped at [ffff8800b763f000-ffff8800bb63efff]
[    1.249773] Simple Boot Flag at 0x44 set to 0x1
[    1.250004] microcode: CPU0 sig=0x20655, pf=0x10, revision=0x2
[    1.250011] microcode: CPU1 sig=0x20655, pf=0x10, revision=0x2
[    1.250015] microcode: CPU2 sig=0x20655, pf=0x10, revision=0x2
[    1.250022] microcode: CPU3 sig=0x20655, pf=0x10, revision=0x2
[    1.250098] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.250125] Scanning for low memory corruption every 60 seconds
[    1.250536] futex hash table entries: 2048 (order: 5, 131072 bytes)
[    1.250586] Initialise system trusted keyring
[    1.250612] audit: initializing netlink subsys (disabled)
[    1.250631] audit: type=2000 audit(1420196924.108:1): initialized
[    1.251034] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.252564] zpool: loaded
[    1.252567] zbud: loaded
[    1.252755] VFS: Disk quotas dquot_6.5.2
[    1.252795] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.253313] fuse init (API version 7.23)
[    1.253413] msgmni has been set to 7500
[    1.253481] Key type big_key registered
[    1.254017] Key type asymmetric registered
[    1.254022] Asymmetric key parser 'x509' registered
[    1.254064] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    1.254121] io scheduler noop registered
[    1.254125] io scheduler deadline registered (default)
[    1.254177] io scheduler cfq registered
[    1.254752] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.254771] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.254821] vesafb: mode is 1024x768x32, linelength=4096, pages=0
[    1.254822] vesafb: scrolling: redraw
[    1.254824] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    1.254843] vesafb: framebuffer at 0xc0000000, mapped to 0xffffc90010780000, using 3072k, total 3072k
[    1.254948] Console: switching to colour frame buffer device 128x48
[    1.254972] fb0: VESA VGA frame buffer device
[    1.254996] intel_idle: MWAIT substates: 0x1120
[    1.254997] intel_idle: v0.4 model 0x25
[    1.254999] intel_idle: lapic_timer_reliable_states 0xffffffff
[    1.267365] ACPI: AC Adapter [AC] (on-line)
[    1.267472] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    1.283547] ACPI: Lid Switch [LID]
[    1.283626] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    1.283632] ACPI: Power Button [PWRB]
[    1.283694] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    1.283698] ACPI: Power Button [PWRF]
[    1.363528] thermal LNXTHERM:00: registered as thermal_zone0
[    1.363533] ACPI: Thermal Zone [TSZ0] (56 C)
[    1.435567] thermal LNXTHERM:01: registered as thermal_zone1
[    1.435572] ACPI: Thermal Zone [TSZ1] (55 C)
[    1.435618] GHES: HEST is not enabled!
[    1.435770] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.438031] Linux agpgart interface v0.103
[    1.438093] agpgart-intel 0000:00:00.0: Intel HD Graphics Chipset
[    1.438113] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    1.438687] agpgart-intel 0000:00:00.0: detected 32768K stolen memory
[    1.438866] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[    1.440472] brd: module loaded
[    1.441300] loop: module loaded
[    1.441547] libphy: Fixed MDIO Bus: probed
[    1.441550] tun: Universal TUN/TAP device driver, 1.6
[    1.441551] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.441619] PPP generic driver version 2.4.2
[    1.441680] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.441686] ehci-pci: EHCI PCI platform driver
[    1.441858] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    1.441865] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.441882] ehci-pci 0000:00:1a.0: debug port 2
[    1.445851] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    1.445875] ehci-pci 0000:00:1a.0: irq 16, io mem 0xd640a000
[    1.455451] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.455493] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.455495] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.455497] usb usb1: Product: EHCI Host Controller
[    1.455499] usb usb1: Manufacturer: Linux 3.16.0-23-generic ehci_hcd
[    1.455501] usb usb1: SerialNumber: 0000:00:1a.0
[    1.455643] hub 1-0:1.0: USB hub found
[    1.455651] hub 1-0:1.0: 3 ports detected
[    1.455873] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    1.455881] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.455895] ehci-pci 0000:00:1d.0: debug port 2
[    1.459849] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    1.459868] ehci-pci 0000:00:1d.0: irq 23, io mem 0xd6409000
[    1.471459] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.471494] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.471496] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.471498] usb usb2: Product: EHCI Host Controller
[    1.471500] usb usb2: Manufacturer: Linux 3.16.0-23-generic ehci_hcd
[    1.471502] usb usb2: SerialNumber: 0000:00:1d.0
[    1.471720] hub 2-0:1.0: USB hub found
[    1.471727] hub 2-0:1.0: 3 ports detected
[    1.471846] ehci-platform: EHCI generic platform driver
[    1.471856] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.471861] ohci-pci: OHCI PCI platform driver
[    1.471872] ohci-platform: OHCI generic platform driver
[    1.471880] uhci_hcd: USB Universal Host Controller Interface driver
[    1.471947] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.484366] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.484371] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.484611] mousedev: PS/2 mouse device common for all mice
[    1.484960] rtc_cmos 00:01: RTC can wake from S4
[    1.485105] rtc_cmos 00:01: rtc core: registered rtc_cmos as rtc0
[    1.485139] rtc_cmos 00:01: alarms up to one month, 242 bytes nvram, hpet irqs
[    1.485211] device-mapper: uevent: version 1.0.3
[    1.485293] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
[    1.485367] ledtrig-cpu: registered to indicate activity on CPUs
[    1.485477] TCP: cubic registered
[    1.485597] NET: Registered protocol family 10
[    1.485903] NET: Registered protocol family 17
[    1.485916] Key type dns_resolver registered
[    1.486284] Loading compiled-in X.509 certificates
[    1.487392] Loaded X.509 cert 'Magrathea: Glacier signing key: d120c47c14beb62ead6703d41712cc110575d297'
[    1.487410] registered taskstats version 1
[    1.489820] Key type trusted registered
[    1.491364] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.491560] Key type encrypted registered
[    1.493213] AppArmor: AppArmor sha1 policy hashing enabled
[    1.493219] ima: No TPM chip found, activating TPM-bypass!
[    1.493246] evm: HMAC attrs: 0x1
[    1.493667]   Magic number: 15:347:124
[    1.493813] rtc_cmos 00:01: setting system clock to 2015-01-02 11:08:44 UTC (1420196924)
[    1.494862] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.494864] EDD information not available.
[    1.494939] PM: Hibernation image not present or could not be loaded.
[    1.651727] ACPI: Battery Slot [BAT0] (battery present)
[    1.653296] Freeing unused kernel memory: 1360K (ffffffff81d2e000 - ffffffff81e82000)
[    1.653300] Write protecting the kernel read-only data: 12288k
[    1.654634] Freeing unused kernel memory: 448K (ffff880001790000 - ffff880001800000)
[    1.655906] Freeing unused kernel memory: 488K (ffff880001b86000 - ffff880001c00000)
[    1.671162] systemd-udevd[124]: starting version 208
[    1.671705] random: systemd-udevd urandom read with 8 bits of entropy available
[    1.709420] rtsx_pci 0000:03:00.0: irq 40 for MSI/MSI-X
[    1.709437] rtsx_pci 0000:03:00.0: rtsx_pci_acquire_irq: pcr->msi_en = 1, pci->irq = 40
[    1.712524] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.712536] r8169 0000:01:00.0: can't disable ASPM; OS doesn't have ASPM control
[    1.712758] r8169 0000:01:00.0: irq 41 for MSI/MSI-X
[    1.712993] r8169 0000:01:00.0 eth0: RTL8105e at 0xffffc9000067e000, e4:11:5b:fc:b9:be, XID 00a00000 IRQ 41
[    1.714043] ahci 0000:00:1f.2: version 3.0
[    1.714190] ahci 0000:00:1f.2: irq 42 for MSI/MSI-X
[    1.714259] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 4 ports 3 Gbps 0x3 impl SATA mode
[    1.714262] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck pm led clo pio slum part ems apst 
[    1.720602] scsi0 : ahci
[    1.723950] scsi1 : ahci
[    1.727469] scsi2 : ahci
[    1.733052] scsi3 : ahci
[    1.733169] ata1: SATA max UDMA/133 abar m2048@0xd6408000 port 0xd6408100 irq 42
[    1.733174] ata2: SATA max UDMA/133 abar m2048@0xd6408000 port 0xd6408180 irq 42
[    1.733176] ata3: DUMMY
[    1.733178] ata4: DUMMY
[    1.767883] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.900533] usb 1-1: New USB device found, idVendor=8087, idProduct=0020
[    1.900539] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.901132] hub 1-1:1.0: USB hub found
[    1.901312] hub 1-1:1.0: 6 ports detected
[    2.011899] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    2.051916] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.051956] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.052335] ata1.00: supports DRM functions and may not be fully accessible
[    2.055299] ata1.00: disabling queued TRIM support
[    2.055304] ata1.00: ATA-9: Crucial_CT240M500SSD1, MU03, max UDMA/133
[    2.055308] ata1.00: 468862128 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.055415] ata2.00: ATAPI: hp       CDDVDW TS-L633R, 0400, max UDMA/100
[    2.059042] ata1.00: supports DRM functions and may not be fully accessible
[    2.060093] ata2.00: configured for UDMA/100
[    2.062004] ata1.00: disabling queued TRIM support
[    2.065280] ata1.00: configured for UDMA/133
[    2.065529] scsi 0:0:0:0: Direct-Access     ATA      Crucial_CT240M50 MU03 PQ: 0 ANSI: 5
[    2.066028] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.066044] sd 0:0:0:0: [sda] 468862128 512-byte logical blocks: (240 GB/223 GiB)
[    2.066048] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    2.066249] sd 0:0:0:0: [sda] Write Protect is off
[    2.066253] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.066350] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.067135]  sda: sda1 sda2 sda3 sda4 < sda5 >
[    2.067703] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.069211] scsi 1:0:0:0: CD-ROM            hp       CDDVDW TS-L633R  0400 PQ: 0 ANSI: 5
[    2.096942] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.096947] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.097120] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.097189] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.136483] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[    2.144587] usb 2-1: New USB device found, idVendor=8087, idProduct=0020
[    2.144596] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.145013] hub 2-1:1.0: USB hub found
[    2.145171] hub 2-1:1.0: 8 ports detected
[    2.224074] usb 1-1.2: new full-speed USB device number 3 using ehci-pci
[    2.247951] tsc: Refined TSC clocksource calibration: 2393.998 MHz
[    2.265746] init: plymouth-upstart-bridge main process (193) terminated with status 1
[    2.265766] init: plymouth-upstart-bridge main process ended, respawning
[    2.320848] usb 1-1.2: New USB device found, idVendor=1532, idProduct=011a
[    2.320854] usb 1-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.320857] usb 1-1.2: Product: Razer BlackWidow Ultimate
[    2.320860] usb 1-1.2: Manufacturer: Razer
[    2.383002] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[    2.396162] usb 1-1.3: new high-speed USB device number 4 using ehci-pci
[    2.490841] systemd-udevd[352]: starting version 208
[    2.534240] usb 1-1.3: New USB device found, idVendor=05c8, idProduct=021e
[    2.534246] usb 1-1.3: New USB device strings: Mfr=2, Product=1, SerialNumber=3
[    2.534249] usb 1-1.3: Product: HP Webcam-101
[    2.534252] usb 1-1.3: Manufacturer: HP Webcam-101
[    2.534255] usb 1-1.3: SerialNumber: HP Webcam-101
[    2.577232] lp: driver loaded but no devices found
[    2.600710] ppdev: user-space parallel port driver
[    2.612394] usb 1-1.4: new full-speed USB device number 5 using ehci-pci
[    2.627202] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    2.662423] [drm] Initialized drm 1.1.0 20060810
[    2.670811] ACPI Warning: SystemIO range 0x0000000000000428-0x000000000000042f conflicts with OpRegion 0x0000000000000400-0x000000000000047f (\PMIO) (20140424/utaddress-258)
[    2.670821] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    2.670826] ACPI Warning: SystemIO range 0x0000000000000540-0x000000000000054f conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20140424/utaddress-258)
[    2.670831] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    2.670834] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053f conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20140424/utaddress-258)
[    2.670839] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    2.670840] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052f conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20140424/utaddress-258)
[    2.670845] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    2.670846] lpc_ich: Resource conflict(s) found affecting gpio_ich
[    2.699071] media: Linux media interface: v0.10
[    2.701080] wmi: Mapper loaded
[    2.703791] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.5, id: 0x1e0b1, caps: 0xd00073/0x240000/0xa0400, board id: 1680, fw id: 706145
[    2.706335] usb 1-1.4: New USB device found, idVendor=0cf3, idProduct=311d
[    2.706339] usb 1-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.706342] usb 1-1.4: Product: Bluetooth USB Host Controller
[    2.706346] usb 1-1.4: Manufacturer: Atheros Communications
[    2.706348] usb 1-1.4: SerialNumber: Alaska Day 2006
[    2.708391] Linux video capture interface: v2.00
[    2.722599] mei_me 0000:00:16.0: irq 43 for MSI/MSI-X
[    2.746731] uvcvideo: Found UVC 1.00 device HP Webcam-101 (05c8:021e)
[    2.756411] [drm] Memory usable by graphics device = 2048M
[    2.756415] [drm] Replacing VGA console driver
[    2.756421] checking generic (c0000000 300000) vs hw (c0000000 10000000)
[    2.756423] fb: switching to inteldrmfb from VESA VGA
[    2.756562] Console: switching to colour dummy device 80x25
[    2.764084] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input5
[    2.766134] input: HP Webcam-101 as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.0/input/input6
[    2.766299] usbcore: registered new interface driver uvcvideo
[    2.766301] USB Video Class driver (1.1.1)
[    2.776383] usb 2-1.1: new full-speed USB device number 3 using ehci-pci
[    2.788376] i915 0000:00:02.0: irq 44 for MSI/MSI-X
[    2.788394] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    2.788396] [drm] Driver supports precise vblank timestamp query.
[    2.788524] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    2.789492] Bluetooth: Core ver 2.19
[    2.789522] NET: Registered protocol family 31
[    2.789524] Bluetooth: HCI device and connection manager initialized
[    2.789533] Bluetooth: HCI socket layer initialized
[    2.789536] Bluetooth: L2CAP socket layer initialized
[    2.789549] Bluetooth: SCO socket layer initialized
[    2.799940] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    2.799944] Bluetooth: BNEP filters: protocol multicast
[    2.799956] Bluetooth: BNEP socket layer initialized
[    2.800171] Bluetooth: RFCOMM TTY layer initialized
[    2.800180] Bluetooth: RFCOMM socket layer initialized
[    2.800187] Bluetooth: RFCOMM ver 1.11
[    2.831257] audit: type=1400 audit(1420214925.829:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=470 comm="apparmor_parser"
[    2.831269] audit: type=1400 audit(1420214925.829:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=470 comm="apparmor_parser"
[    2.831275] audit: type=1400 audit(1420214925.829:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="third_party" pid=470 comm="apparmor_parser"
[    2.831823] init: avahi-cups-reload main process (479) terminated with status 1
[    2.875310] usb 2-1.1: New USB device found, idVendor=1532, idProduct=0037
[    2.875316] usb 2-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.875319] usb 2-1.1: Product: Razer DeathAdder 2013
[    2.875322] usb 2-1.1: Manufacturer: Razer
[    2.892093] cfg80211: Calling CRDA to update world regulatory domain
[    2.919283] fbcon: inteldrmfb (fb0) is primary device
[    2.919325] Console: switching to colour frame buffer device 170x48
[    2.919377] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[    2.919380] i915 0000:00:02.0: registered panic notifier
[    2.922334] audit: type=1400 audit(1420214925.921:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=496 comm="apparmor_parser"
[    2.922346] audit: type=1400 audit(1420214925.921:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=496 comm="apparmor_parser"
[    2.922352] audit: type=1400 audit(1420214925.921:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=496 comm="apparmor_parser"
[    2.997610] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    3.009229] hidraw: raw HID events driver (C) Jiri Kosina
[    3.016575] ath: phy0: ASPM enabled: 0x43
[    3.016580] ath: EEPROM regdomain: 0x60
[    3.016581] ath: EEPROM indicates we should expect a direct regpair map
[    3.016583] ath: Country alpha2 being used: 00
[    3.016584] ath: Regpair used: 0x60
[    3.020719] acpi device:01: registered as cooling_device4
[    3.020873] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input7
[    3.021157] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    3.021727] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[    3.023664] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[    3.024094] ieee80211 phy0: Atheros AR9485 Rev:1 mem=0xffffc90011000000, irq=18
[    3.035361] usbcore: registered new interface driver usbhid
[    3.035366] usbhid: USB HID core driver
[    3.046958] sound hdaudioC0D0: autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[    3.046965] sound hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    3.046968] sound hdaudioC0D0:    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
[    3.046971] sound hdaudioC0D0:    mono: mono_out=0x0
[    3.046974] sound hdaudioC0D0:    inputs:
[    3.046977] sound hdaudioC0D0:      Mic=0x18
[    3.046980] sound hdaudioC0D0:      Internal Mic=0x12
[    3.052635] input: HDA Intel MID Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[    3.052774] input: HDA Intel MID Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[    3.082981] kvm: disabled by bios
[    3.232286] random: nonblocking pool is initialized
[    3.255154] Switched to clocksource tsc
[    3.270181] init: failsafe main process (552) killed by TERM signal
[    3.328967] input: HP WMI hotkeys as /devices/virtual/input/input10
[    3.370359] usbcore: registered new interface driver btusb
[    3.374797] usbcore: registered new interface driver ath3k
[    3.393879] cfg80211: World regulatory domain updated:
[    3.393885] cfg80211:  DFS Master region: unset
[    3.393888] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[    3.393892] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[    3.393895] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[    3.393898] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
[    3.393901] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[    3.393904] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[    3.402915] input: Razer Razer BlackWidow Ultimate as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/0003:1532:011A.0001/input/input11
[    3.405177] hid-generic 0003:1532:011A.0001: input,hidraw0: USB HID v1.11 Keyboard [Razer Razer BlackWidow Ultimate] on usb-0000:00:1a.0-1.2/input0
[    3.407481] input: Razer Razer BlackWidow Ultimate as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.1/0003:1532:011A.0002/input/input12
[    3.407680] hid-generic 0003:1532:011A.0002: input,hidraw1: USB HID v1.11 Keyboard [Razer Razer BlackWidow Ultimate] on usb-0000:00:1a.0-1.2/input1
[    3.408910] input: Razer Razer BlackWidow Ultimate as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.2/0003:1532:011A.0003/input/input13
[    3.409068] hid-generic 0003:1532:011A.0003: input,hidraw2: USB HID v1.11 Mouse [Razer Razer BlackWidow Ultimate] on usb-0000:00:1a.0-1.2/input2
[    3.409276] input: Razer Razer DeathAdder 2013 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.0/0003:1532:0037.0004/input/input14
[    3.409431] hid-generic 0003:1532:0037.0004: input,hidraw3: USB HID v1.11 Mouse [Razer Razer DeathAdder 2013] on usb-0000:00:1d.0-1.1/input0
[    3.413188] input: Razer Razer DeathAdder 2013 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.1/0003:1532:0037.0005/input/input15
[    3.415599] hid-generic 0003:1532:0037.0005: input,hidraw4: USB HID v1.11 Keyboard [Razer Razer DeathAdder 2013] on usb-0000:00:1d.0-1.1/input1
[    3.415807] input: Razer Razer DeathAdder 2013 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.2/0003:1532:0037.0006/input/input16
[    3.415925] hid-generic 0003:1532:0037.0006: input,hidraw5: USB HID v1.11 Keyboard [Razer Razer DeathAdder 2013] on usb-0000:00:1d.0-1.1/input2
[    3.424056] ACPI Error: Field [B128] at 1152 exceeds Buffer [NULL] size 160 (bits) (20140424/dsopcode-236)
[    3.424066] ACPI Error: Method parse/execution failed [\_SB_.WMID.HWCD] (Node ffff88013343de88), AE_AML_BUFFER_LIMIT (20140424/psparse-536)
[    3.424079] ACPI Error: Method parse/execution failed [\_SB_.WMID.WMAD] (Node ffff88013343e4b0), AE_AML_BUFFER_LIMIT (20140424/psparse-536)
[    3.448977] ACPI Error: Field [B128] at 1152 exceeds Buffer [NULL] size 160 (bits) (20140424/dsopcode-236)
[    3.448988] ACPI Error: Method parse/execution failed [\_SB_.WMID.HWCD] (Node ffff88013343de88), AE_AML_BUFFER_LIMIT (20140424/psparse-536)
[    3.449002] ACPI Error: Method parse/execution failed [\_SB_.WMID.WMAD] (Node ffff88013343e4b0), AE_AML_BUFFER_LIMIT (20140424/psparse-536)
[    3.543415] audit: type=1400 audit(1420214926.544:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cups-browsed" pid=743 comm="apparmor_parser"
[    3.575084] audit: type=1400 audit(1420214926.576:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=756 comm="apparmor_parser"
[    3.575095] audit: type=1400 audit(1420214926.576:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=756 comm="apparmor_parser"
[    3.682283] systemd-logind[763]: New seat seat0.
[    3.689155] systemd-logind[763]: Watching system buttons on /dev/input/event2 (Power Button)
[    3.689259] systemd-logind[763]: Watching system buttons on /dev/input/event6 (Video Bus)
[    3.689366] systemd-logind[763]: Watching system buttons on /dev/input/event1 (Power Button)
[    3.689469] systemd-logind[763]: Watching system buttons on /dev/input/event0 (Lid Switch)
[    3.892085] r8169 0000:01:00.0 eth0: link down
[    3.892180] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    3.916766] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

---

### Post by sudodus on 2015-01-10
Welcome to the Ubuntu Forums :-)

The way to shut down Ubuntu is often called hard shutdown, and it can damage some open file or even the file system and cause problems. Sometimes it can be repaired with tools, that repair the file system (and run from the Ubuntu live CD.

There is a better way to reboot, soft reboot, that often works even in emergency situations, when there is no response to the mouse and keyboard:
[I][B]
SysRq R E I S U B[/B][/I]

and soft shutdown

***SysRq R E I S U O***

according to this link 

Often SysRq is on the PrintScreen key, and you activate it with ***alt + PrintScreen***. Press it all the time while pressing of the keys R E I S U B one after another.

Sometimes it is even referred to ***alt + SysRq + R E I S U B***

[https://en.wikipedia.org/wiki/Magic_SysRq_key](https://en.wikipedia.org/wiki/Magic_SysRq_key)

-o-

When the system is damaged right after installation, it is often easier to re-install than to debug it and repair it.

There may be a few reasons why it did not want to shutdown properly, maybe problems with the ACPI, the graphics card or the wifi card. That is easier to look for and try to fix in a fresh installed system.

Often it helps to use one or several boot options. You can start with ACPI and nomodeset. See this link

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

-o-

Please specify your computer details

- Brand name and model - *HP 2000* - is this link correct? - [http://h10025.www1.hp.com/ewfrf/wc/document?cc=se&lc=sv&dlc=sv&docname=c03499287](http://h10025.www1.hp.com/ewfrf/wc/document?cc=se&lc=sv&dlc=sv&docname=c03499287)
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

It will make it easier for us to help.

If that link to the computer specs is correct, ***Xubuntu*** might work better than Ubuntu, because of Xubuntu's lighter desktop environment, but there might be the same problems at shutdown.

---

