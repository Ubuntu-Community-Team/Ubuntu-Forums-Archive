---
title: "Ubuntu 15.10 slow boot with dmesg results"
date: 2016-03-01
forum: General Help
---

### Post by Lijun on 2016-03-01
Hi,

Can some one be so kind to help me to find out what is causing the slow boot of my Ubuntu 15.10? I am dual-booting with Windows 10. After selecting Ubuntu in the grub page, the computer waits for quite a while before the Ubuntu logo screen shows up. So I am not quite sure what is causing this delay, grub? or ubuntu itself?

**Here is the output of systemd-analyze:**
```
The time after the unit is active or started is printed after the "@" character.
The time the unit takes to start is printed after the "+" character.
graphical.target @30.557s
&#9492;&#9472;multi-user.target @30.557s
  &#9492;&#9472;getty.target @30.557s
    &#9492;&#9472;getty@tty1.service @30.557s
      &#9492;&#9472;[1;31mrc-local.service @27.890s +24ms[0m
        &#9492;&#9472;network-online.target @27.889s
          &#9492;&#9472;network.target @17.545s
            &#9492;&#9472;[1;31mwpa_supplicant.service @19.451s +271ms[0m
              &#9492;&#9472;basic.target @11.707s
                &#9492;&#9472;paths.target @11.707s
                  &#9492;&#9472;systemd-networkd-resolvconf-update.path @11.707s
                    &#9492;&#9472;sysinit.target @11.609s
                      &#9492;&#9472;[1;31mnetworking.service @11.408s +200ms[0m
                        &#9492;&#9472;[1;31mapparmor.service @9.297s +2.110s[0m
                          &#9492;&#9472;local-fs.target @9.295s
                            &#9492;&#9472;[1;31mhome.mount @9.074s +220ms[0m
                              &#9492;&#9472;[1;31msystemd-fsck@dev-disk-by\x2duuid-49868bae\x2d5e9c\x2d4eca\x2da837\x2d132e11384431.service @8.001s +1.054s[0m
                                &#9492;&#9472;dev-disk-by\x2duuid-49868bae\x2d5e9c\x2d4eca\x2da837\x2d132e11384431.device @8.001s
```

**And here is the output of dmesg:**
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 4.2.0-30-generic (buildd@lgw01-60) (gcc version 5.2.1 20151010 (Ubuntu 5.2.1-22ubuntu2) ) #36-Ubuntu SMP Fri Feb 26 00:58:07 UTC 2016 (Ubuntu 4.2.0-30.36-generic 4.2.8-ckt3)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.2.0-30-generic root=UUID=19148037-ae66-4628-8dfa-cb8c6efc5a8e ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] x86/fpu: xstate_offset[2]: 0240, xstate_sizes[2]: 0100
[    0.000000] x86/fpu: Supporting XSAVE feature 0x01: 'x87 floating point registers'
[    0.000000] x86/fpu: Supporting XSAVE feature 0x02: 'SSE registers'
[    0.000000] x86/fpu: Supporting XSAVE feature 0x04: 'AVX registers'
[    0.000000] x86/fpu: Enabled xstate features 0x7, context size is 0x340 bytes, using 'standard' format.
[    0.000000] x86/fpu: Using 'eager' FPU context switches.
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009d7ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009d800-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000001fffffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000020000000-0x00000000201fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000020200000-0x0000000040003fff] usable
[    0.000000] BIOS-e820: [mem 0x0000000040004000-0x0000000040004fff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000040005000-0x00000000d067ffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000d0680000-0x00000000dae9efff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000dae9f000-0x00000000daf9efff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000daf9f000-0x00000000daffefff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000dafff000-0x00000000df9fffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed08000-0x00000000fed08fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed10000-0x00000000fed19fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffc00000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000021e5fffff] usable
[    0.000000] BIOS-e820: [mem 0x000000021e600000-0x000000021e7fffff] reserved
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.7 present.
[    0.000000] DMI: LENOVO 343545G/343545G, BIOS GCET21WW (1.10 ) 07/25/2012
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0x21e600 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0FFC00000 mask FFFC00000 write-protect
[    0.000000]   1 base 000000000 mask F80000000 write-back
[    0.000000]   2 base 080000000 mask FC0000000 write-back
[    0.000000]   3 base 0C0000000 mask FE0000000 write-back
[    0.000000]   4 base 0DC000000 mask FFC000000 uncachable
[    0.000000]   5 base 0DB000000 mask FFF000000 uncachable
[    0.000000]   6 base 100000000 mask F00000000 write-back
[    0.000000]   7 base 200000000 mask FE0000000 write-back
[    0.000000]   8 base 21F000000 mask FFF000000 uncachable
[    0.000000]   9 base 21E800000 mask FFF800000 uncachable
[    0.000000] x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- WT  
[    0.000000] e820: last_pfn = 0xd0680 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000f0100-0x000f010f] mapped at [ffff8800000f0100]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000097000] 97000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01ff1000, 0x01ff1fff] PGTABLE
[    0.000000] BRK [0x01ff2000, 0x01ff2fff] PGTABLE
[    0.000000] BRK [0x01ff3000, 0x01ff3fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x21e400000-0x21e5fffff]
[    0.000000]  [mem 0x21e400000-0x21e5fffff] page 2M
[    0.000000] BRK [0x01ff4000, 0x01ff4fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x200000000-0x21e3fffff]
[    0.000000]  [mem 0x200000000-0x21e3fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x1e0000000-0x1ffffffff]
[    0.000000]  [mem 0x1e0000000-0x1ffffffff] page 2M
[    0.000000] BRK [0x01ff5000, 0x01ff5fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x00100000-0x1fffffff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x1fffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x20200000-0x40003fff]
[    0.000000]  [mem 0x20200000-0x3fffffff] page 2M
[    0.000000]  [mem 0x40000000-0x40003fff] page 4k
[    0.000000] BRK [0x01ff6000, 0x01ff6fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x40005000-0xd067ffff]
[    0.000000]  [mem 0x40005000-0x401fffff] page 4k
[    0.000000]  [mem 0x40200000-0xd05fffff] page 2M
[    0.000000]  [mem 0xd0600000-0xd067ffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x100000000-0x1dfffffff]
[    0.000000]  [mem 0x100000000-0x1dfffffff] page 2M
[    0.000000] RAMDISK: [mem 0x33fd8000-0x35fe3fff]
[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x00000000000F0120 000024 (v02 LENOVO)
[    0.000000] ACPI: XSDT 0x00000000DAFFE170 0000BC (v01 LENOVO TP-GC    00001100 PTL  00000002)
[    0.000000] ACPI: FACP 0x00000000DAFE5000 0000F4 (v04 LENOVO TP-GC    00001100 PTL  00000002)
[    0.000000] ACPI: DSDT 0x00000000DAFE8000 0105A2 (v01 LENOVO TP-GC    00001100 INTL 20061109)
[    0.000000] ACPI: FACS 0x00000000DAF5A000 000040
[    0.000000] ACPI: FACS 0x00000000DAF5A000 000040
[    0.000000] ACPI: SLIC 0x00000000DAFFD000 000176 (v01 LENOVO TP-GC    00001100 PTL  00000001)
[    0.000000] ACPI: TCPA 0x00000000DAFFC000 000032 (v02 PTL    LENOVO   06040000 LNVO 00000001)
[    0.000000] ACPI: SSDT 0x00000000DAFFB000 000249 (v01 LENOVO TP-SSDT2 00000200 INTL 20061109)
[    0.000000] ACPI: SSDT 0x00000000DAFFA000 000033 (v01 LENOVO TP-SSDT1 00000100 INTL 20061109)
[    0.000000] ACPI: SSDT 0x00000000DAFF9000 0007A8 (v01 LENOVO SataAhci 00001000 INTL 20061109)
[    0.000000] ACPI: HPET 0x00000000DAFE4000 000038 (v01 LENOVO TP-GC    00001100 PTL  00000002)
[    0.000000] ACPI: APIC 0x00000000DAFE3000 000098 (v01 LENOVO TP-GC    00001100 PTL  00000002)
[    0.000000] ACPI: MCFG 0x00000000DAFE2000 00003C (v01 LENOVO TP-GC    00001100 PTL  00000002)
[    0.000000] ACPI: ECDT 0x00000000DAFE1000 000052 (v01 LENOVO TP-GC    00001100 PTL  00000002)
[    0.000000] ACPI: FPDT 0x00000000DAFE0000 000054 (v01 LENOVO TP-GC    00001100 PTL  00000002)
[    0.000000] ACPI: ASF! 0x00000000DAFE7000 0000A5 (v32 LENOVO TP-GC    00001100 PTL  00000002)
[    0.000000] ACPI: UEFI 0x00000000DAFDF000 00003E (v01 LENOVO TP-GC    00001100 PTL  00000002)
[    0.000000] ACPI: UEFI 0x00000000DAFDE000 000042 (v01 PTL    COMBUF   00000001 PTL  00000001)
[    0.000000] ACPI: POAT 0x00000000DAFDD000 000055 (v03 LENOVO TP-GC    00001100 PTL  00000002)
[    0.000000] ACPI: SSDT 0x00000000DAFDC000 000C79 (v01 PmRef  Cpu0Ist  00003000 INTL 20061109)
[    0.000000] ACPI: SSDT 0x00000000DAFDB000 000A7E (v01 PmRef  CpuPm    00003000 INTL 20061109)
[    0.000000] ACPI: DMAR 0x00000000DAFDA000 0000B8 (v01 INTEL  SNB      00000001 INTL 00000001)
[    0.000000] ACPI: UEFI 0x00000000DAFD9000 0002A6 (v01 LENOVO TP-GC    00001100 PTL  00000002)
[    0.000000] ACPI: DMI detected: Lenovo ThinkPad X230
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000021e5fffff]
[    0.000000] NODE_DATA(0) allocated [mem 0x21e5f4000-0x21e5f8fff]
[    0.000000]  [ffffea0000000000-ffffea00087fffff] PMD -> [ffff880215e00000-ffff88021dbfffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x0000000000001000-0x0000000000ffffff]
[    0.000000]   DMA32    [mem 0x0000000001000000-0x00000000ffffffff]
[    0.000000]   Normal   [mem 0x0000000100000000-0x000000021e5fffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x0000000000001000-0x000000000009cfff]
[    0.000000]   node   0: [mem 0x0000000000100000-0x000000001fffffff]
[    0.000000]   node   0: [mem 0x0000000020200000-0x0000000040003fff]
[    0.000000]   node   0: [mem 0x0000000040005000-0x00000000d067ffff]
[    0.000000]   node   0: [mem 0x0000000100000000-0x000000021e5fffff]
[    0.000000] Initmem setup node 0 [mem 0x0000000000001000-0x000000021e5fffff]
[    0.000000] On node 0 totalpages: 2026011
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3996 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 13266 pages used for memmap
[    0.000000]   DMA32 zone: 849023 pages, LIFO batch:31
[    0.000000]   Normal zone: 18328 pages used for memmap
[    0.000000]   Normal zone: 1172992 pages, LIFO batch:31
[    0.000000] Reserving Intel graphics stolen memory at 0xdba00000-0xdf9fffff
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a301 base: 0xfed00000
[    0.000000] smpboot: Allowing 8 CPUs, 4 hotplug CPUs
[    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009d000-0x0009dfff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x20000000-0x201fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x40004000-0x40004fff]
[    0.000000] PM: Registered nosave memory: [mem 0xd0680000-0xdae9efff]
[    0.000000] PM: Registered nosave memory: [mem 0xdae9f000-0xdaf9efff]
[    0.000000] PM: Registered nosave memory: [mem 0xdaf9f000-0xdaffefff]
[    0.000000] PM: Registered nosave memory: [mem 0xdafff000-0xdf9fffff]
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
[    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xffbfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xffc00000-0xffffffff]
[    0.000000] e820: [mem 0xdfa00000-0xf7ffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] clocksource: refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645519600211568 ns
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 33 pages/cpu @ffff88021e200000 s96728 r8192 d30248 u262144
[    0.000000] pcpu-alloc: s96728 r8192 d30248 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1994332
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.2.0-30-generic root=UUID=19148037-ae66-4628-8dfa-cb8c6efc5a8e ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 7858364K/8104044K available (8158K kernel code, 1238K rwdata, 3804K rodata, 1464K init, 1292K bss, 245680K reserved, 0K cma-reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     Build-time adjustment of leaf fanout to 64.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=64, nr_cpu_ids=8
[    0.000000] NR_IRQS:16640 nr_irqs:488 16
[    0.000000]     Offload RCU callbacks from all CPUs
[    0.000000]     Offload RCU callbacks from CPUs: 0-7.
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] clocksource: hpet: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 133484882848 ns
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 2893.337 MHz processor
[    0.000029] Calibrating delay loop (skipped), value calculated using timer frequency.. 5786.67 BogoMIPS (lpj=11573348)
[    0.000032] pid_max: default: 32768 minimum: 301
[    0.000036] ACPI: Core revision 20150619
[    0.009922] ACPI: All ACPI Tables successfully acquired
[    0.009938] Security Framework initialized
[    0.009947] AppArmor: AppArmor initialized
[    0.009947] Yama: becoming mindful.
[    0.010365] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.012051] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.012798] Mount-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.012806] Mountpoint-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.012974] Initializing cgroup subsys blkio
[    0.012976] Initializing cgroup subsys memory
[    0.012982] Initializing cgroup subsys devices
[    0.012984] Initializing cgroup subsys freezer
[    0.012985] Initializing cgroup subsys net_cls
[    0.012987] Initializing cgroup subsys perf_event
[    0.012989] Initializing cgroup subsys net_prio
[    0.012990] Initializing cgroup subsys hugetlb
[    0.013009] CPU: Physical Processor ID: 0
[    0.013010] CPU: Processor Core ID: 0
[    0.013014] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.013015] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.013340] mce: CPU supports 7 MCE banks
[    0.013350] CPU0: Thermal monitoring enabled (TM1)
[    0.013355] process: using mwait in idle threads
[    0.013357] Last level iTLB entries: 4KB 512, 2MB 8, 4MB 8
[    0.013358] Last level dTLB entries: 4KB 512, 2MB 32, 4MB 32, 1GB 0
[    0.013722] Freeing SMP alternatives memory: 28K (ffffffff81ea5000 - ffffffff81eac000)
[    0.016372] ftrace: allocating 30940 entries in 121 pages
[    0.028701] DMAR: Host address width 36
[    0.028704] DMAR: DRHD base: 0x000000fed90000 flags: 0x0
[    0.028708] DMAR: dmar0: reg_base_addr fed90000 ver 1:0 cap c0000020e60262 ecap f0101a
[    0.028709] DMAR: DRHD base: 0x000000fed91000 flags: 0x1
[    0.028712] DMAR: dmar1: reg_base_addr fed91000 ver 1:0 cap c9008020660262 ecap f0105a
[    0.028713] DMAR: RMRR base: 0x000000da2f0000 end: 0x000000da306fff
[    0.028714] DMAR: RMRR base: 0x000000db800000 end: 0x000000df9fffff
[    0.028716] DMAR-IR: IOAPIC id 2 under DRHD base  0xfed91000 IOMMU 1
[    0.028717] DMAR-IR: HPET id 0 under DRHD base 0xfed91000
[    0.028718] DMAR-IR: Queued invalidation will be enabled to support x2apic and Intr-remapping.
[    0.028968] DMAR-IR: Enabled IRQ remapping in x2apic mode
[    0.028969] x2apic enabled
[    0.028975] Switched APIC routing to cluster x2apic.
[    0.029438] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.069138] TSC deadline timer enabled
[    0.069142] smpboot: CPU0: Intel(R) Core(TM) i7-3520M CPU @ 2.90GHz (fam: 06, model: 3a, stepping: 09)
[    0.069163] Performance Events: PEBS fmt1+, 16-deep LBR, IvyBridge events, full-width counters, Intel PMU driver.
[    0.069180] ... version:                3
[    0.069181] ... bit width:              48
[    0.069181] ... generic registers:      4
[    0.069182] ... value mask:             0000ffffffffffff
[    0.069183] ... max period:             0000ffffffffffff
[    0.069184] ... fixed-purpose events:   3
[    0.069184] ... event mask:             000000070000000f
[    0.069854] x86: Booting SMP configuration:
[    0.069855] .... node  #0, CPUs:      #1
[    0.073378] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.073463]  #2 #3
[    0.080397] x86: Booted up 1 node, 4 CPUs
[    0.080400] smpboot: Total of 4 processors activated (23146.69 BogoMIPS)
[    0.083733] devtmpfs: initialized
[    0.085881] evm: security.selinux
[    0.085882] evm: security.SMACK64
[    0.085883] evm: security.SMACK64EXEC
[    0.085883] evm: security.SMACK64TRANSMUTE
[    0.085884] evm: security.SMACK64MMAP
[    0.085885] evm: security.ima
[    0.085886] evm: security.capability
[    0.085932] PM: Registering ACPI NVS region [mem 0xdae9f000-0xdaf9efff] (1048576 bytes)
[    0.086008] clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
[    0.086073] pinctrl core: initialized pinctrl subsystem
[    0.086170] RTC time: 19:41:08, date: 03/01/16
[    0.086259] NET: Registered protocol family 16
[    0.091588] cpuidle: using governor ladder
[    0.095591] cpuidle: using governor menu
[    0.095674] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.095676] ACPI: bus type PCI registered
[    0.095677] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.095860] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.095862] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.095867] PCI: Using configuration type 1 for base access
[    0.096056] perf_event_intel: PMU erratum BJ122, BV98, HSD29 worked around, HT is on
[    0.099887] ACPI: Added _OSI(Module Device)
[    0.099888] ACPI: Added _OSI(Processor Device)
[    0.099889] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.099890] ACPI: Added _OSI(Processor Aggregator Device)
[    0.099891] ACPI: Deleted _OSI(Windows 2012)
[    0.101016] ACPI : EC: EC description table is found, configuring boot EC
[    0.101028] ACPI : EC: EC started
[    0.104016] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.106421] ACPI: Dynamic OEM Table Load:
[    0.106430] ACPI: SSDT 0xFFFF880214130000 000A01 (v01 PmRef  Cpu0Cst  00003001 INTL 20061109)
[    0.106859] ACPI: Dynamic OEM Table Load:
[    0.106866] ACPI: SSDT 0xFFFF880214120C00 000303 (v01 PmRef  ApIst    00003000 INTL 20061109)
[    0.107241] ACPI: Dynamic OEM Table Load:
[    0.107247] ACPI: SSDT 0xFFFF880214138000 000119 (v01 PmRef  ApCst    00003000 INTL 20061109)
[    0.107957] ACPI: Interpreter enabled
[    0.107962] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20150619/hwxface-580)
[    0.107965] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20150619/hwxface-580)
[    0.107975] ACPI: (supports S0 S3 S4 S5)
[    0.107976] ACPI: Using IOAPIC for interrupt routing
[    0.107994] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.110370] ACPI: Power Resource [PUBS] (on)
[    0.111081] acpi PNP0C0A:01: ACPI dock station (docks/bays count: 1)
[    0.111819] acpi LNXIOBAY:00: ACPI dock station (docks/bays count: 2)
[    0.113942] acpi IBM0079:00: ACPI dock station (docks/bays count: 3)
[    0.114267] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11)
[    0.114333] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11)
[    0.114394] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 *7 9 10 11)
[    0.114457] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 *7 9 10 11)
[    0.114519] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11)
[    0.114580] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11)
[    0.114642] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 *10 11)
[    0.114704] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11)
[    0.114772] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3f])
[    0.114775] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.114854] acpi PNP0A08:00: _OSC: platform does not support [PCIeCapability]
[    0.114888] acpi PNP0A08:00: _OSC: not requesting control; platform does not support [PCIeCapability]
[    0.114890] acpi PNP0A08:00: _OSC: OS requested [PCIeHotplug PME AER PCIeCapability]
[    0.114892] acpi PNP0A08:00: _OSC: platform willing to grant [PCIeHotplug PME AER]
[    0.114893] acpi PNP0A08:00: _OSC failed (AE_SUPPORT); disabling ASPM
[    0.115012] PCI host bridge to bus 0000:00
[    0.115014] pci_bus 0000:00: root bus resource [bus 00-3f]
[    0.115016] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7 window]
[    0.115017] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff window]
[    0.115019] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff window]
[    0.115020] pci_bus 0000:00: root bus resource [mem 0xdfa00000-0xfebfffff window]
[    0.115021] pci_bus 0000:00: root bus resource [mem 0xfed40000-0xfed4bfff window]
[    0.115027] pci 0000:00:00.0: [8086:0154] type 00 class 0x060000
[    0.115091] pci 0000:00:02.0: [8086:0166] type 00 class 0x030000
[    0.115100] pci 0000:00:02.0: reg 0x10: [mem 0xf0000000-0xf03fffff 64bit]
[    0.115106] pci 0000:00:02.0: reg 0x18: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.115110] pci 0000:00:02.0: reg 0x20: [io  0x5000-0x503f]
[    0.115186] pci 0000:00:14.0: [8086:1e31] type 00 class 0x0c0330
[    0.115205] pci 0000:00:14.0: reg 0x10: [mem 0xf2520000-0xf252ffff 64bit]
[    0.115267] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    0.115290] pci 0000:00:14.0: System wakeup disabled by ACPI
[    0.115326] pci 0000:00:16.0: [8086:1e3a] type 00 class 0x078000
[    0.115346] pci 0000:00:16.0: reg 0x10: [mem 0xf2535000-0xf253500f 64bit]
[    0.115413] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.115466] pci 0000:00:16.3: [8086:1e3d] type 00 class 0x070002
[    0.115482] pci 0000:00:16.3: reg 0x10: [io  0x50b0-0x50b7]
[    0.115490] pci 0000:00:16.3: reg 0x14: [mem 0xf253c000-0xf253cfff]
[    0.115604] pci 0000:00:19.0: [8086:1502] type 00 class 0x020000
[    0.115619] pci 0000:00:19.0: reg 0x10: [mem 0xf2500000-0xf251ffff]
[    0.115627] pci 0000:00:19.0: reg 0x14: [mem 0xf253b000-0xf253bfff]
[    0.115636] pci 0000:00:19.0: reg 0x18: [io  0x5080-0x509f]
[    0.115688] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.115711] pci 0000:00:19.0: System wakeup disabled by ACPI
[    0.115745] pci 0000:00:1a.0: [8086:1e2d] type 00 class 0x0c0320
[    0.115762] pci 0000:00:1a.0: reg 0x10: [mem 0xf253a000-0xf253a3ff]
[    0.115837] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.115860] pci 0000:00:1a.0: System wakeup disabled by ACPI
[    0.115895] pci 0000:00:1b.0: [8086:1e20] type 00 class 0x040300
[    0.115910] pci 0000:00:1b.0: reg 0x10: [mem 0xf2530000-0xf2533fff 64bit]
[    0.115974] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.116001] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    0.116038] pci 0000:00:1c.0: [8086:1e10] type 01 class 0x060400
[    0.116150] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.116216] pci 0000:00:1c.1: [8086:1e12] type 01 class 0x060400
[    0.116329] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.116395] pci 0000:00:1c.2: [8086:1e14] type 01 class 0x060400
[    0.116508] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.116538] pci 0000:00:1c.2: System wakeup disabled by ACPI
[    0.116578] pci 0000:00:1d.0: [8086:1e26] type 00 class 0x0c0320
[    0.116595] pci 0000:00:1d.0: reg 0x10: [mem 0xf2539000-0xf25393ff]
[    0.116670] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.116693] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.116727] pci 0000:00:1f.0: [8086:1e55] type 00 class 0x060100
[    0.116866] pci 0000:00:1f.2: [8086:1e03] type 00 class 0x010601
[    0.116879] pci 0000:00:1f.2: reg 0x10: [io  0x50a8-0x50af]
[    0.116886] pci 0000:00:1f.2: reg 0x14: [io  0x50bc-0x50bf]
[    0.116894] pci 0000:00:1f.2: reg 0x18: [io  0x50a0-0x50a7]
[    0.116902] pci 0000:00:1f.2: reg 0x1c: [io  0x50b8-0x50bb]
[    0.116909] pci 0000:00:1f.2: reg 0x20: [io  0x5060-0x507f]
[    0.116917] pci 0000:00:1f.2: reg 0x24: [mem 0xf2538000-0xf25387ff]
[    0.116950] pci 0000:00:1f.2: PME# supported from D3hot
[    0.116996] pci 0000:00:1f.3: [8086:1e22] type 00 class 0x0c0500
[    0.117010] pci 0000:00:1f.3: reg 0x10: [mem 0xf2534000-0xf25340ff 64bit]
[    0.117030] pci 0000:00:1f.3: reg 0x20: [io  0xefa0-0xefbf]
[    0.117211] pci 0000:02:00.0: [1180:e822] type 00 class 0x088001
[    0.117232] pci 0000:02:00.0: MMC controller base frequency changed to 50Mhz.
[    0.117260] pci 0000:02:00.0: reg 0x10: [mem 0xf1d00000-0xf1d000ff]
[    0.117447] pci 0000:02:00.0: supports D1 D2
[    0.117449] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.127853] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.127857] pci 0000:00:1c.0:   bridge window [io  0x4000-0x4fff]
[    0.127861] pci 0000:00:1c.0:   bridge window [mem 0xf1d00000-0xf24fffff]
[    0.127870] pci 0000:00:1c.0:   bridge window [mem 0xf0400000-0xf0bfffff 64bit pref]
[    0.128060] pci 0000:03:00.0: [8086:0085] type 00 class 0x028000
[    0.128228] pci 0000:03:00.0: reg 0x10: [mem 0xf1c00000-0xf1c01fff 64bit]
[    0.128909] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[    0.139727] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    0.139736] pci 0000:00:1c.1:   bridge window [mem 0xf1c00000-0xf1cfffff]
[    0.139822] acpiphp: Slot [1] registered
[    0.139830] pci 0000:00:1c.2: PCI bridge to [bus 04-0b]
[    0.139835] pci 0000:00:1c.2:   bridge window [io  0x3000-0x3fff]
[    0.139839] pci 0000:00:1c.2:   bridge window [mem 0xf1400000-0xf1bfffff]
[    0.139848] pci 0000:00:1c.2:   bridge window [mem 0xf0c00000-0xf13fffff 64bit pref]
[    0.140753] ACPI: Enabled 4 GPEs in block 00 to 3F
[    0.140803] ACPI : EC: GPE = 0x11, I/O: command/status = 0x66, data = 0x62
[    0.140887] vgaarb: setting as boot device: PCI:0000:00:02.0
[    0.140889] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.140891] vgaarb: loaded
[    0.140892] vgaarb: bridge control possible 0000:00:02.0
[    0.141062] SCSI subsystem initialized
[    0.141096] libata version 3.00 loaded.
[    0.141114] ACPI: bus type USB registered
[    0.141128] usbcore: registered new interface driver usbfs
[    0.141134] usbcore: registered new interface driver hub
[    0.141148] usbcore: registered new device driver usb
[    0.141260] PCI: Using ACPI for IRQ routing
[    0.142946] PCI: pci_cache_line_size set to 64 bytes
[    0.143316] e820: reserve RAM buffer [mem 0x0009d800-0x0009ffff]
[    0.143318] e820: reserve RAM buffer [mem 0x40004000-0x43ffffff]
[    0.143319] e820: reserve RAM buffer [mem 0xd0680000-0xd3ffffff]
[    0.143320] e820: reserve RAM buffer [mem 0x21e600000-0x21fffffff]
[    0.143410] NetLabel: Initializing
[    0.143411] NetLabel:  domain hash size = 128
[    0.143412] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.143421] NetLabel:  unlabeled traffic allowed by default
[    0.143481] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.143485] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.146518] clocksource: Switched to clocksource hpet
[    0.151064] AppArmor: AppArmor Filesystem Enabled
[    0.151126] pnp: PnP ACPI init
[    0.151442] system 00:00: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.151444] system 00:00: [mem 0x000c0000-0x000c3fff] could not be reserved
[    0.151446] system 00:00: [mem 0x000c4000-0x000c7fff] could not be reserved
[    0.151447] system 00:00: [mem 0x000c8000-0x000cbfff] has been reserved
[    0.151448] system 00:00: [mem 0x000cc000-0x000cffff] has been reserved
[    0.151450] system 00:00: [mem 0x000d0000-0x000d3fff] has been reserved
[    0.151451] system 00:00: [mem 0x000d4000-0x000d7fff] has been reserved
[    0.151452] system 00:00: [mem 0x000d8000-0x000dbfff] has been reserved
[    0.151454] system 00:00: [mem 0x000dc000-0x000dffff] has been reserved
[    0.151455] system 00:00: [mem 0x000e0000-0x000e3fff] could not be reserved
[    0.151457] system 00:00: [mem 0x000e4000-0x000e7fff] could not be reserved
[    0.151458] system 00:00: [mem 0x000e8000-0x000ebfff] could not be reserved
[    0.151459] system 00:00: [mem 0x000ec000-0x000effff] could not be reserved
[    0.151461] system 00:00: [mem 0x000f0000-0x000fffff] could not be reserved
[    0.151462] system 00:00: [mem 0x00100000-0xdf9fffff] could not be reserved
[    0.151464] system 00:00: [mem 0xfec00000-0xfed3ffff] could not be reserved
[    0.151465] system 00:00: [mem 0xfed4c000-0xffffffff] could not be reserved
[    0.151468] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.151533] pnp 00:01: [Firmware Bug]: PNP resource [mem 0xfed10000-0xfed13fff] covers only part of 0000:00:00.0 Intel MCH; extending to [mem 0xfed10000-0xfed17fff]
[    0.151550] system 00:01: [io  0x0400-0x047f] could not be reserved
[    0.151552] system 00:01: [io  0x0500-0x057f] has been reserved
[    0.151553] system 00:01: [io  0x0800-0x080f] has been reserved
[    0.151555] system 00:01: [io  0x15e0-0x15ef] has been reserved
[    0.151556] system 00:01: [io  0x1600-0x167f] has been reserved
[    0.151559] system 00:01: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.151560] system 00:01: [mem 0xfffff000-0xffffffff] has been reserved
[    0.151562] system 00:01: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.151563] system 00:01: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.151565] system 00:01: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.151566] system 00:01: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.151568] system 00:01: [mem 0xfed45000-0xfed4bfff] has been reserved
[    0.151570] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.151607] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.151625] pnp 00:03: Plug and Play ACPI device, IDs LEN0070 PNP0303 (active)
[    0.151642] pnp 00:04: Plug and Play ACPI device, IDs LEN0020 PNP0f13 (active)
[    0.151677] pnp 00:05: Plug and Play ACPI device, IDs SMO1200 PNP0c31 (active)
[    0.152110] pnp: PnP ACPI: found 6 devices
[    0.158316] clocksource: acpi_pm: mask: 0xffffff max_cycles: 0xffffff, max_idle_ns: 2085701024 ns
[    0.158358] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.158363] pci 0000:00:1c.0:   bridge window [io  0x4000-0x4fff]
[    0.158369] pci 0000:00:1c.0:   bridge window [mem 0xf1d00000-0xf24fffff]
[    0.158375] pci 0000:00:1c.0:   bridge window [mem 0xf0400000-0xf0bfffff 64bit pref]
[    0.158383] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    0.158389] pci 0000:00:1c.1:   bridge window [mem 0xf1c00000-0xf1cfffff]
[    0.158401] pci 0000:00:1c.2: PCI bridge to [bus 04-0b]
[    0.158404] pci 0000:00:1c.2:   bridge window [io  0x3000-0x3fff]
[    0.158410] pci 0000:00:1c.2:   bridge window [mem 0xf1400000-0xf1bfffff]
[    0.158415] pci 0000:00:1c.2:   bridge window [mem 0xf0c00000-0xf13fffff 64bit pref]
[    0.158424] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7 window]
[    0.158425] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff window]
[    0.158427] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff window]
[    0.158428] pci_bus 0000:00: resource 7 [mem 0xdfa00000-0xfebfffff window]
[    0.158429] pci_bus 0000:00: resource 8 [mem 0xfed40000-0xfed4bfff window]
[    0.158431] pci_bus 0000:02: resource 0 [io  0x4000-0x4fff]
[    0.158432] pci_bus 0000:02: resource 1 [mem 0xf1d00000-0xf24fffff]
[    0.158434] pci_bus 0000:02: resource 2 [mem 0xf0400000-0xf0bfffff 64bit pref]
[    0.158435] pci_bus 0000:03: resource 1 [mem 0xf1c00000-0xf1cfffff]
[    0.158437] pci_bus 0000:04: resource 0 [io  0x3000-0x3fff]
[    0.158438] pci_bus 0000:04: resource 1 [mem 0xf1400000-0xf1bfffff]
[    0.158439] pci_bus 0000:04: resource 2 [mem 0xf0c00000-0xf13fffff 64bit pref]
[    0.158464] NET: Registered protocol family 2
[    0.158603] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
[    0.158721] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.158824] TCP: Hash tables configured (established 65536 bind 65536)
[    0.158843] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.158865] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.158911] NET: Registered protocol family 1
[    0.158925] pci 0000:00:02.0: Video device with shadowed ROM
[    0.159445] PCI: CLS 64 bytes, default 64
[    0.159487] Trying to unpack rootfs image as initramfs...
[    0.582463] Freeing initrd memory: 32816K (ffff880033fd8000 - ffff880035fe4000)
[    0.582485] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.582487] software IO TLB [mem 0xcc680000-0xd0680000] (64MB) mapped at [ffff8800cc680000-ffff8800d067ffff]
[    0.582560] RAPL PMU detected, API unit is 2^-32 Joules, 3 fixed counters 163840 ms ovfl timer
[    0.582561] hw unit of domain pp0-core 2^-16 Joules
[    0.582562] hw unit of domain package 2^-16 Joules
[    0.582563] hw unit of domain pp1-gpu 2^-16 Joules
[    0.582694] microcode: CPU0 sig=0x306a9, pf=0x10, revision=0x12
[    0.582703] microcode: CPU1 sig=0x306a9, pf=0x10, revision=0x12
[    0.582712] microcode: CPU2 sig=0x306a9, pf=0x10, revision=0x12
[    0.582719] microcode: CPU3 sig=0x306a9, pf=0x10, revision=0x12
[    0.582766] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.582833] Scanning for low memory corruption every 60 seconds
[    0.583146] futex hash table entries: 2048 (order: 5, 131072 bytes)
[    0.583167] Initialise system trusted keyring
[    0.583188] audit: initializing netlink subsys (disabled)
[    0.583201] audit: type=2000 audit(1456861268.580:1): initialized
[    0.583541] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.584668] zpool: loaded
[    0.584670] zbud: loaded
[    0.584820] VFS: Disk quotas dquot_6.6.0
[    0.584848] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.585214] fuse init (API version 7.23)
[    0.585330] Key type big_key registered
[    0.585610] Key type asymmetric registered
[    0.585612] Asymmetric key parser 'x509' registered
[    0.585623] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 249)
[    0.585652] io scheduler noop registered
[    0.585654] io scheduler deadline registered (default)
[    0.585677] io scheduler cfq registered
[    0.586098] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.586104] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.586128] vesafb: mode is 1366x768x32, linelength=5504, pages=0
[    0.586129] vesafb: scrolling: redraw
[    0.586131] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    0.586138] vesafb: framebuffer at 0xe0000000, mapped to 0xffffc90001000000, using 4160k, total 4160k
[    0.586218] Console: switching to colour frame buffer device 170x48
[    0.586233] fb0: VESA VGA frame buffer device
[    0.586247] intel_idle: MWAIT substates: 0x21120
[    0.586248] intel_idle: v0.4 model 0x3A
[    0.586249] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.586514] ACPI: AC Adapter [AC] (on-line)
[    0.586563] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.586666] ACPI: Lid Switch [LID]
[    0.586695] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.586698] ACPI: Sleep Button [SLPB]
[    0.586729] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.586731] ACPI: Power Button [PWRF]
[    0.587815] thermal LNXTHERM:00: registered as thermal_zone0
[    0.587817] ACPI: Thermal Zone [THM0] (61 C)
[    0.587841] GHES: HEST is not enabled!
[    0.587921] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.596237] ACPI: Battery Slot [BAT0] (battery present)
[    0.610129] 0000:00:16.3: ttyS4 at I/O 0x50b0 (irq = 19, base_baud = 115200) is a 16550A
[    0.610346] Linux agpgart interface v0.103
[    0.630741] tpm_tis 00:05: 1.2 TPM (device-id 0x0, rev-id 78)
[    0.717466] brd: module loaded
[    0.718154] loop: module loaded
[    0.718315] libphy: Fixed MDIO Bus: probed
[    0.718318] tun: Universal TUN/TAP device driver, 1.6
[    0.718319] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.718361] PPP generic driver version 2.4.2
[    0.718488] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.718493] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 1
[    0.719573] xhci_hcd 0000:00:14.0: hcc params 0x20007181 hci version 0x100 quirks 0x0000b930
[    0.719580] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    0.719663] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.719665] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.719666] usb usb1: Product: xHCI Host Controller
[    0.719668] usb usb1: Manufacturer: Linux 4.2.0-30-generic xhci-hcd
[    0.719669] usb usb1: SerialNumber: 0000:00:14.0
[    0.719759] hub 1-0:1.0: USB hub found
[    0.719770] hub 1-0:1.0: 4 ports detected
[    0.720071] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.720075] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 2
[    0.720104] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003
[    0.720105] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.720107] usb usb2: Product: xHCI Host Controller
[    0.720108] usb usb2: Manufacturer: Linux 4.2.0-30-generic xhci-hcd
[    0.720109] usb usb2: SerialNumber: 0000:00:14.0
[    0.720187] hub 2-0:1.0: USB hub found
[    0.720197] hub 2-0:1.0: 4 ports detected
[    0.720337] usb: failed to peer usb2-port2 and usb1-port1 by location (usb2-port2:none) (usb1-port1:usb2-port1)
[    0.720338] usb usb2-port2: failed to peer to usb1-port1 (-16)
[    0.720339] usb: port power management may be unreliable
[    0.720404] usb: failed to peer usb2-port3 and usb1-port1 by location (usb2-port3:none) (usb1-port1:usb2-port1)
[    0.720405] usb usb2-port3: failed to peer to usb1-port1 (-16)
[    0.720467] usb: failed to peer usb2-port4 and usb1-port1 by location (usb2-port4:none) (usb1-port1:usb2-port1)
[    0.720468] usb usb2-port4: failed to peer to usb1-port1 (-16)
[    0.720529] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.720533] ehci-pci: EHCI PCI platform driver
[    0.720597] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    0.720601] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.720615] ehci-pci 0000:00:1a.0: debug port 2
[    0.724523] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    0.724535] ehci-pci 0000:00:1a.0: irq 16, io mem 0xf253a000
[    0.734731] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    0.734767] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    0.734769] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.734770] usb usb3: Product: EHCI Host Controller
[    0.734771] usb usb3: Manufacturer: Linux 4.2.0-30-generic ehci_hcd
[    0.734772] usb usb3: SerialNumber: 0000:00:1a.0
[    0.734926] hub 3-0:1.0: USB hub found
[    0.734935] hub 3-0:1.0: 3 ports detected
[    0.735102] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    0.735106] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 4
[    0.735119] ehci-pci 0000:00:1d.0: debug port 2
[    0.739021] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    0.739033] ehci-pci 0000:00:1d.0: irq 23, io mem 0xf2539000
[    0.750734] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    0.750770] usb usb4: New USB device found, idVendor=1d6b, idProduct=0002
[    0.750772] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.750773] usb usb4: Product: EHCI Host Controller
[    0.750774] usb usb4: Manufacturer: Linux 4.2.0-30-generic ehci_hcd
[    0.750776] usb usb4: SerialNumber: 0000:00:1d.0
[    0.750933] hub 4-0:1.0: USB hub found
[    0.750939] hub 4-0:1.0: 3 ports detected
[    0.751053] ehci-platform: EHCI generic platform driver
[    0.751062] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.751066] ohci-pci: OHCI PCI platform driver
[    0.751074] ohci-platform: OHCI generic platform driver
[    0.751080] uhci_hcd: USB Universal Host Controller Interface driver
[    0.751121] i8042: PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    0.755217] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.755221] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.755448] mousedev: PS/2 mouse device common for all mice
[    0.755843] rtc_cmos 00:02: RTC can wake from S4
[    0.756040] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.756085] rtc_cmos 00:02: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.756092] i2c /dev entries driver
[    0.756150] device-mapper: uevent: version 1.0.3
[    0.756209] device-mapper: ioctl: 4.33.0-ioctl (2015-8-18) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    0.756237] Intel P-state driver initializing.
[    0.756427] ledtrig-cpu: registered to indicate activity on CPUs
[    0.756736] PCCT header not found.
[    0.757145] NET: Registered protocol family 10
[    0.757302] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.757500] NET: Registered protocol family 17
[    0.757528] Key type dns_resolver registered
[    0.758123] Loading compiled-in X.509 certificates
[    0.759908] Loaded X.509 cert 'Build time autogenerated kernel key: aa46912a20e4e17b1e4a6ccc08bd3c70d4d8f464'
[    0.759932] registered taskstats version 1
[    0.759972] zswap: loading zswap
[    0.759975] zswap: using zbud pool
[    0.759983] zswap: using lzo compressor
[    0.764290] Key type trusted registered
[    0.766676] Key type encrypted registered
[    0.766688] AppArmor: AppArmor sha1 policy hashing enabled
[    1.030914] evm: HMAC attrs: 0x1
[    1.031406]   Magic number: 8:204:697
[    1.031529] rtc_cmos 00:02: setting system clock to 2016-03-01 19:41:09 UTC (1456861269)
[    1.031588] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.031589] EDD information not available.
[    1.031644] PM: Hibernation image not present or could not be loaded.
[    1.031885] Freeing unused kernel memory: 1464K (ffffffff81d37000 - ffffffff81ea5000)
[    1.031886] Write protecting the kernel read-only data: 12288k
[    1.031988] Freeing unused kernel memory: 20K (ffff8800017fb000 - ffff880001800000)
[    1.032057] Freeing unused kernel memory: 292K (ffff880001bb7000 - ffff880001c00000)
[    1.046782] usb 3-1: new high-speed USB device number 2 using ehci-pci
[    1.047816] random: systemd-udevd urandom read with 8 bits of entropy available
[    1.062783] usb 4-1: new high-speed USB device number 2 using ehci-pci
[    1.073687] wmi: Mapper loaded
[    1.077388] sdhci: Secure Digital Host Controller Interface driver
[    1.077390] sdhci: Copyright(c) Pierre Ossman
[    1.079033] sdhci-pci 0000:02:00.0: SDHCI controller found [1180:e822] (rev 7)
[    1.079274] ahci 0000:00:1f.2: version 3.0
[    1.079520] sdhci-pci 0000:02:00.0: No vmmc regulator found
[    1.079522] sdhci-pci 0000:02:00.0: No vqmmc regulator found
[    1.079604] ahci 0000:00:1f.2: SSS flag set, parallel bus scan disabled
[    1.080283] pps_core: LinuxPPS API ver. 1 registered
[    1.080285] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
[    1.081113] [drm] Initialized drm 1.1.0 20060810
[    1.081564] PTP clock support registered
[    1.084092] mmc0: SDHCI controller on PCI [0000:02:00.0] using DMA
[    1.086078] e1000e: Intel(R) PRO/1000 Network Driver - 3.2.5-k
[    1.086080] e1000e: Copyright(c) 1999 - 2015 Intel Corporation.
[    1.094811] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x13 impl SATA mode
[    1.094815] ahci 0000:00:1f.2: flags: 64bit ncq stag pm led clo pio slum part ems sxs apst 
[    1.111493] scsi host0: ahci
[    1.111660] scsi host1: ahci
[    1.111765] scsi host2: ahci
[    1.111864] scsi host3: ahci
[    1.111960] scsi host4: ahci
[    1.112057] scsi host5: ahci
[    1.112109] ata1: SATA max UDMA/133 abar m2048@0xf2538000 port 0xf2538100 irq 27
[    1.112112] ata2: SATA max UDMA/133 abar m2048@0xf2538000 port 0xf2538180 irq 27
[    1.112113] ata3: DUMMY
[    1.112115] ata4: DUMMY
[    1.112119] ata5: SATA max UDMA/133 abar m2048@0xf2538000 port 0xf2538300 irq 27
[    1.112121] ata6: DUMMY
[    1.112278] e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    1.179633] usb 3-1: New USB device found, idVendor=8087, idProduct=0024
[    1.179636] usb 3-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.180109] hub 3-1:1.0: USB hub found
[    1.180369] hub 3-1:1.0: 6 ports detected
[    1.195234] usb 4-1: New USB device found, idVendor=8087, idProduct=0024
[    1.195236] usb 4-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.195516] hub 4-1:1.0: USB hub found
[    1.195604] hub 4-1:1.0: 8 ports detected
[    1.304803] e1000e 0000:00:19.0 eth0: registered PHC clock
[    1.304807] e1000e 0000:00:19.0 eth0: (PCI Express:2.5GT/s:Width x1) 3c:97:0e:26:71:d5
[    1.304809] e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
[    1.304869] e1000e 0000:00:19.0 eth0: MAC: 10, PHY: 11, PBA No: 1000FF-0FF
[    1.305862] [drm] Memory usable by graphics device = 2048M
[    1.305865] checking generic (e0000000 410000) vs hw (e0000000 10000000)
[    1.305866] fb: switching to inteldrmfb from VESA VGA
[    1.305885] Console: switching to colour dummy device 80x25
[    1.305969] [drm] Replacing VGA console driver
[    1.312664] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    1.312666] [drm] Driver supports precise vblank timestamp query.
[    1.312758] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    1.344662] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[    1.345351] acpi device:00: registered as cooling_device4
[    1.345401] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input6
[    1.345480] [drm] Initialized i915 1.6.0 20150522 for 0000:00:02.0 on minor 0
[    1.410985] [drm] GMBUS [i915 gmbus dpb] timed out, falling back to bit banging on pin 5
[    1.427840] fbcon: inteldrmfb (fb0) is primary device
[    1.427893] Console: switching to colour frame buffer device 170x48
[    1.427908] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[    1.427909] i915 0000:00:02.0: registered panic notifier
[    1.430980] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.432098] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[    1.432113] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    1.433146] ata1.00: ATA-8: HITACHI HTS725050A7E630, GH2ZB390, max UDMA/133
[    1.433154] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.434328] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[    1.434338] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    1.435297] ata1.00: configured for UDMA/133
[    1.435486] scsi 0:0:0:0: Direct-Access     ATA      HITACHI HTS72505 B390 PQ: 0 ANSI: 5
[    1.435744] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.435747] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    1.435783] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.435803] sd 0:0:0:0: [sda] Write Protect is off
[    1.435807] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.435833] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.450968] usb 3-1.3: new full-speed USB device number 3 using ehci-pci
[    1.482964] usb 4-1.5: new full-speed USB device number 3 using ehci-pci
[    1.508815]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 sda7 >
[    1.509819] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.545127] usb 3-1.3: New USB device found, idVendor=147e, idProduct=2020
[    1.545130] usb 3-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.545131] usb 3-1.3: Product: Biometric Coprocessor
[    1.545132] usb 3-1.3: Manufacturer: Auth
[    1.578178] usb 4-1.5: New USB device found, idVendor=056a, idProduct=00e6
[    1.578186] usb 4-1.5: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.578198] usb 4-1.5: Product: ISD-V4
[    1.578199] usb 4-1.5: Manufacturer: Tablet
[    1.578919] tsc: Refined TSC clocksource calibration: 2893.438 MHz
[    1.578922] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x29b50c41951, max_idle_ns: 440795259070 ns
[    1.582264] hidraw: raw HID events driver (C) Jiri Kosina
[    1.593334] usbcore: registered new interface driver usbhid
[    1.593338] usbhid: USB HID core driver
[    1.596255] input: Wacom ISDv4 E6 Pen as /devices/pci0000:00/0000:00:1d.0/usb4/4-1/4-1.5/4-1.5:1.0/0003:056A:00E6.0001/input/input7
[    1.596358] wacom 0003:056A:00E6.0001: hidraw0: USB HID v1.11 Device [Tablet ISD-V4] on usb-0000:00:1d.0-1.5/input0
[    1.596554] input: Wacom ISDv4 E6 Finger as /devices/pci0000:00/0000:00:1d.0/usb4/4-1/4-1.5/4-1.5:1.1/0003:056A:00E6.0002/input/input11
[    1.596630] wacom 0003:056A:00E6.0002: hidraw1: USB HID v1.11 Mouse [Tablet ISD-V4] on usb-0000:00:1d.0-1.5/input1
[    1.615015] usb 3-1.4: new full-speed USB device number 4 using ehci-pci
[    1.712472] usb 3-1.4: New USB device found, idVendor=0a5c, idProduct=21e6
[    1.712475] usb 3-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.712476] usb 3-1.4: Product: BCM20702A0
[    1.712477] usb 3-1.4: Manufacturer: Broadcom Corp
[    1.712478] usb 3-1.4: SerialNumber: E006E6BBD5F4
[    1.755057] ata2: SATA link down (SStatus 0 SControl 300)
[    1.783039] usb 3-1.6: new high-speed USB device number 5 using ehci-pci
[    1.884355] usb 3-1.6: New USB device found, idVendor=04f2, idProduct=b2ea
[    1.884358] usb 3-1.6: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.884360] usb 3-1.6: Product: Integrated Camera
[    1.884361] usb 3-1.6: Manufacturer: Chicony Electronics Co., Ltd.
[    1.977620] psmouse serio1: synaptics: queried max coordinates: x [..5768], y [..5062]
[    2.017453] psmouse serio1: synaptics: queried min coordinates: x [1174..], y [790..]
[    2.083157] ata5: SATA link down (SStatus 0 SControl 300)
[    2.094293] psmouse serio1: synaptics: Touchpad model: 1, fw: 8.1, id: 0x1e2b1, caps: 0xd002a3/0x940300/0x123800/0x0, board id: 1611, fw id: 1099905
[    2.094300] psmouse serio1: synaptics: serio: Synaptics pass-through port at isa0060/serio1/input0
[    2.143256] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input5
[    2.579258] clocksource: Switched to clocksource tsc
[    2.827057] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[    3.315514] random: nonblocking pool is initialized
[    3.368055] systemd[1]: RTC configured in localtime, applying delta of 120 minutes to system time.
[    3.587885] systemd[1]: Failed to insert module 'kdbus': Function not implemented
[    3.659793] systemd[1]: systemd 225 running in system mode. (+PAM +AUDIT +SELINUX +IMA +APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT +GNUTLS +ACL +XZ -LZ4 +SECCOMP +BLKID -ELFUTILS +KMOD -IDN)
[    3.659921] systemd[1]: Detected architecture x86-64.
[    3.684613] systemd[1]: Set hostname to <X230>.
[    5.491842] systemd[1]: Reached target Encrypted Volumes.
[    5.491903] systemd[1]: Reached target Remote File Systems (Pre).
[    5.491929] systemd[1]: Started Forward Password Requests to Wall Directory Watch.
[    5.491952] systemd[1]: Reached target User and Group Name Lookups.
[    5.491994] systemd[1]: Created slice Root Slice.
[    5.492074] systemd[1]: Created slice System Slice.
[    5.492443] systemd[1]: Starting Increase datagram queue length...
[    5.492506] systemd[1]: Created slice system-systemd\x2dfsck.slice.
[    5.492596] systemd[1]: Listening on Journal Audit Socket.
[    5.492623] systemd[1]: Listening on fsck to fsckd communication Socket.
[    5.492654] systemd[1]: Listening on /dev/initctl Compatibility Named Pipe.
[    5.492681] systemd[1]: Listening on udev Control Socket.
[    5.492713] systemd[1]: Listening on Journal Socket.
[    5.493042] systemd[1]: Mounting Huge Pages File System...
[    5.493426] systemd[1]: Starting Create list of required static device nodes for the current kernel...
[    5.493903] systemd[1]: Starting Setup Virtual Console...
[    5.571950] systemd[1]: Starting Load Kernel Modules...
[    5.572371] systemd[1]: Started Braille Device Support.
[    5.572852] systemd[1]: Starting Uncomplicated firewall...
[    5.573207] systemd[1]: Started Read required files in advance.
[    5.573613] systemd[1]: Mounting POSIX Message Queue File System...
[    5.573959] systemd[1]: Starting LSB: controls configuration of serial ports...
[    5.574510] systemd[1]: Mounting Debug File System...
[    5.574556] systemd[1]: Listening on udev Kernel Socket.
[    5.574912] systemd[1]: Starting udev Coldplug all Devices...
[    5.574956] systemd[1]: Listening on Journal Socket (/dev/log).
[    5.575028] systemd[1]: Created slice User and Session Slice.
[    5.575037] systemd[1]: Reached target Slices.
[    5.575137] systemd[1]: Set up automount Arbitrary Executable File Formats File System Automount Point.
[    5.620323] systemd[1]: Started Setup Virtual Console.
[    5.632176] systemd[1]: Started Create list of required static device nodes for the current kernel.
[    5.632598] systemd[1]: Starting Create Static Device Nodes in /dev...
[    5.686858] systemd[1]: Mounted POSIX Message Queue File System.
[    5.686880] systemd[1]: Mounted Debug File System.
[    5.686891] systemd[1]: Mounted Huge Pages File System.
[    5.687024] systemd[1]: Started Increase datagram queue length.
[    5.687234] systemd[1]: Listening on Syslog Socket.
[    5.687588] systemd[1]: Starting Journal Service...
[    5.980148] systemd[1]: Started Uncomplicated firewall.
[    6.129698] systemd[1]: Started udev Coldplug all Devices.
[    6.193226] lp: driver loaded but no devices found
[    6.203859] ppdev: user-space parallel port driver
[    6.260491] systemd[1]: Started Load Kernel Modules.
[    6.261005] systemd[1]: Mounting FUSE Control File System...
[    6.261395] systemd[1]: Starting Apply Kernel Variables...
[    6.262546] systemd[1]: Mounted FUSE Control File System.
[    6.296961] systemd[1]: Started Journal Service.
[    7.104242] psmouse serio2: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3
[    7.353458] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/serio2/input/input13
[    8.074493] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[    8.337974] systemd-journald[256]: Received request to flush runtime journal from PID 1
[    8.486000] ACPI Warning: SystemIO range 0x0000000000000428-0x000000000000042F conflicts with OpRegion 0x0000000000000400-0x000000000000047F (\_SB_.PCI0.LPC_.PMIO) (20150619/utaddress-254)
[    8.486005] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    8.486008] ACPI Warning: SystemIO range 0x0000000000000540-0x000000000000054F conflicts with OpRegion 0x0000000000000500-0x000000000000057F (\_SB_.PCI0.LPC_.LPIO) (20150619/utaddress-254)
[    8.486010] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    8.486011] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053F conflicts with OpRegion 0x0000000000000500-0x000000000000057F (\_SB_.PCI0.LPC_.LPIO) (20150619/utaddress-254)
[    8.486013] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    8.486014] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052F conflicts with OpRegion 0x0000000000000500-0x000000000000057F (\_SB_.PCI0.LPC_.LPIO) (20150619/utaddress-254)
[    8.486016] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    8.486016] lpc_ich: Resource conflict(s) found affecting gpio_ich
[    8.494804] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    8.982956] Non-volatile memory driver v1.3
[    9.010094] thinkpad_acpi: ThinkPad ACPI Extras v0.25
[    9.010097] thinkpad_acpi: [http://ibm-acpi.sf.net/](http://ibm-acpi.sf.net/)
[    9.010098] thinkpad_acpi: ThinkPad BIOS GCET21WW (1.10 ), EC unknown
[    9.010100] thinkpad_acpi: Lenovo ThinkPad X230 Tablet, model 343545G
[    9.010479] thinkpad_acpi: detected a 16-level brightness capable ThinkPad
[    9.010586] thinkpad_acpi: radio switch found; radios are enabled
[    9.010669] thinkpad_acpi: possible tablet mode switch found; ThinkPad in laptop mode
[    9.010679] thinkpad_acpi: This ThinkPad has standard ACPI backlight brightness control, supported by the ACPI video driver
[    9.010680] thinkpad_acpi: Disabling thinkpad-acpi brightness events by default...
[    9.011661] thinkpad_acpi: rfkill switch tpacpi_bluetooth_sw: radio is unblocked
[    9.011967] thinkpad_acpi: Standard ACPI backlight interface available, not loading native one
[    9.018983] input: ThinkPad Extra Buttons as /devices/platform/thinkpad_acpi/input/input14
[    9.029659] Intel(R) Wireless WiFi driver for Linux
[    9.029662] Copyright(c) 2003- 2015 Intel Corporation
[    9.029840] iwlwifi 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[    9.056581] AVX version of gcm_enc/dec engaged.
[    9.056584] AES CTR mode by8 optimization enabled
[    9.485646] snd_hda_codec_realtek hdaudioC0D0: autoconfig for ALC269VC: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[    9.485650] snd_hda_codec_realtek hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    9.485653] snd_hda_codec_realtek hdaudioC0D0:    hp_outs=2 (0x15/0x1b/0x0/0x0/0x0)
[    9.485655] snd_hda_codec_realtek hdaudioC0D0:    mono: mono_out=0x0
[    9.485656] snd_hda_codec_realtek hdaudioC0D0:    inputs:
[    9.485659] snd_hda_codec_realtek hdaudioC0D0:      Mic=0x18
[    9.485660] snd_hda_codec_realtek hdaudioC0D0:      Dock Mic=0x19
[    9.485662] snd_hda_codec_realtek hdaudioC0D0:      Internal Mic=0x12
[    9.490174] iwlwifi 0000:03:00.0: loaded firmware version 18.168.6.1 op_mode iwldvm
[    9.502901] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
[    9.502969] input: HDA Intel PCH Dock Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input16
[    9.503035] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input17
[    9.503093] input: HDA Intel PCH Dock Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input18
[    9.503151] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input19
[    9.503209] input: HDA Intel PCH HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input20
[    9.830390] intel_rapl: Found RAPL domain package
[    9.830393] intel_rapl: Found RAPL domain core
[    9.830395] intel_rapl: Found RAPL domain uncore
[    9.830399] intel_rapl: RAPL package 0 domain package locked by BIOS
[    9.858842] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUG disabled
[    9.858845] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[    9.858846] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[    9.858847] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Advanced-N 6205 AGN, REV=0xB0
[    9.859010] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[    9.905705] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   10.074240] cfg80211: World regulatory domain updated:
[   10.074243] cfg80211:  DFS Master region: unset
[   10.074244] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[   10.074246] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[   10.074247] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[   10.074248] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
[   10.074249] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
[   10.074250] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
[   10.074251] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
[   10.074252] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
[   10.074253] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
[   10.259103] Adding 3774460k swap on /dev/sda5.  Priority:-1 extents:1 across:3774460k FS
[   11.540209] media: Linux media interface: v0.10
[   11.559976] Linux video capture interface: v2.00
[   11.641729] Bluetooth: Core ver 2.20
[   11.641741] NET: Registered protocol family 31
[   11.641742] Bluetooth: HCI device and connection manager initialized
[   11.641744] Bluetooth: HCI socket layer initialized
[   11.641746] Bluetooth: L2CAP socket layer initialized
[   11.641750] Bluetooth: SCO socket layer initialized
[   11.717670] usbcore: registered new interface driver btusb
[   11.722865] Bluetooth: hci0: BCM: chip id 63
[   11.723782] Bluetooth: hci0: BCM20702A1 (001.002.014) build 0000
[   11.735716] bluetooth hci0: Direct firmware load for brcm/BCM20702A1-0a5c-21e6.hcd failed with error -2
[   11.735724] Bluetooth: hci0: BCM: Patch brcm/BCM20702A1-0a5c-21e6.hcd not found
[   11.774307] uvcvideo: Found UVC 1.00 device Integrated Camera (04f2:b2ea)
[   11.776675] input: Integrated Camera as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.6/3-1.6:1.0/input/input21
[   11.776716] usbcore: registered new interface driver uvcvideo
[   11.776718] USB Video Class driver (1.1.1)
[   12.635824] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
[   13.982238] audit: type=1400 audit(1456854082.439:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=732 comm="apparmor_parser"
[   13.982243] audit: type=1400 audit(1456854082.439:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=732 comm="apparmor_parser"
[   14.084811] audit: type=1400 audit(1456854082.543:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=732 comm="apparmor_parser"
[   14.084830] audit: type=1400 audit(1456854082.543:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=732 comm="apparmor_parser"
[   14.084833] audit: type=1400 audit(1456854082.543:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=732 comm="apparmor_parser"
[   14.084836] audit: type=1400 audit(1456854082.543:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=732 comm="apparmor_parser"
[   14.338533] audit: type=1400 audit(1456854082.799:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince" pid=732 comm="apparmor_parser"
[   14.338540] audit: type=1400 audit(1456854082.799:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=732 comm="apparmor_parser"
[   14.338552] audit: type=1400 audit(1456854082.799:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince-previewer" pid=732 comm="apparmor_parser"
[   14.338555] audit: type=1400 audit(1456854082.799:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=732 comm="apparmor_parser"
[   18.458743] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   18.458747] Bluetooth: BNEP filters: protocol multicast
[   18.458751] Bluetooth: BNEP socket layer initialized
[   19.229317] [drm:intel_set_pch_fifo_underrun_reporting [i915]] *ERROR* uncleared pch fifo underrun on pch transcoder A
[   19.229355] [drm:intel_pch_fifo_underrun_irq_handler [i915]] *ERROR* PCH transcoder A FIFO underrun
[   22.155817] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.155999] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[   22.162972] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[   22.433837] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[   22.440795] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[   22.525800] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.527350] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   22.756963] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   23.256269] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   27.455521] wlan0: authenticate with 20:0c:c8:1a:6c:5b
[   27.462101] wlan0: send auth to 20:0c:c8:1a:6c:5b (try 1/3)
[   27.467492] wlan0: authenticated
[   27.467603] wlan0: waiting for beacon from 20:0c:c8:1a:6c:5b
[   27.541953] wlan0: associate with 20:0c:c8:1a:6c:5b (try 1/3)
[   27.545440] wlan0: RX AssocResp from 20:0c:c8:1a:6c:5b (capab=0x411 status=0 aid=5)
[   27.567233] wlan0: associated
[   27.567270] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   31.446285] vboxdrv: module verification failed: signature and/or required key missing - tainting kernel
[   31.448650] vboxdrv: Found 4 processor cores
[   31.471271] vboxdrv: TSC mode is Invariant, tentative frequency 2893436326 Hz
[   31.471274] vboxdrv: Successfully loaded version 5.0.14_Ubuntu (interface 0x00240000)
[   31.474478] VBoxNetFlt: Successfully started.
[   31.477544] VBoxNetAdp: Successfully started.
[   31.480587] VBoxPciLinuxInit
[   31.482097] vboxpci: IOMMU not found (not registered)
[   33.986365] thinkpad_ec: thinkpad_ec_request_row: arg0 rejected: (0x01:0x00)->0x00
[   33.986368] thinkpad_ec: thinkpad_ec_read_row: failed requesting row: (0x01:0x00)->0xfffffffb
[   33.986369] thinkpad_ec: initial ec test failed
[   34.071291] thinkpad_ec: thinkpad_ec_request_row: arg0 rejected: (0x01:0x00)->0x00
[   34.071294] thinkpad_ec: thinkpad_ec_read_row: failed requesting row: (0x01:0x00)->0xfffffffb
[   34.071295] thinkpad_ec: initial ec test failed
[   38.246399] Bluetooth: RFCOMM TTY layer initialized
[   38.246405] Bluetooth: RFCOMM socket layer initialized
[   38.246410] Bluetooth: RFCOMM ver 1.11
```


Thank you very much for your time and kindness to read through this. Please advise what is possibly wrong.

---

